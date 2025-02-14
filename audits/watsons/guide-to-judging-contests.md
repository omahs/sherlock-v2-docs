---
description: So you want to be a Sherlock judge...
---

# Guide to Judging Contests

## What's in it for you?

5% of the value of the audit contest pot will be up for grabs in each judging contest. If an audit has a $50k pot, then the “judging pot” will be $2,500.

## When do judging contests start?

Immediately after an audit contest ends, the 3-day judging contest will begin.

Example: If an audit contest goes from January 1st to January 14th, the judging contest will start on January 14th and run until January 17th.

## How to join a judging contest

1. Go to [https://app.sherlock.xyz/audits/contests](https://app.sherlock.xyz/audits/contests)
2. Sign up as a Watson if you haven't already.
3. Find active contests in the `JUDGING CONTESTS` section of the [Contests page](https://app.sherlock.xyz/audits/contests), or find upcoming ones by looking for a "Judge Contest" button on a protocol's detailed contest page
4.  Click on that contest then click the "Judge Contest" button on the lower right side.\
    \


    <figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>
5. A new private repo will be created for you in GitHub.
6. The repo will contain a Markdown (.md) file with each submitted issue and two folders ("low" and "false"). Your job is to sort the Markdown files. See the next section.

## How to judge issues

{% hint style="danger" %}
**DONT's**

* Change file content
* Remove files (only move between folders)
* Rename files (has a single exception)
* Create folders that are not formatted either ###-M or ###-H

\### stands for any number, we would suggest to start with 001 and increase sequentially (002, 003, 004)

By default every {number}.md file in the root of the repo is considered an unjudged issue.
{% endhint %}

You've already completed the steps above and now you're ready to start judging:

For each Markdown (.md) file, you will:

1\. Decide the severity (High/Medium/Low/False)

* If High, create a new folder with a 3 digit number and an “-H” (ex. 001-H) and put the corresponding .md file in the folder
* If Medium, create a new folder with a 3 digit number and an “-M” (ex. 001-M) and put the corresponding .md file in the folder
* If Low/False, put the .md file in either the “low” or “false” folder

An example High severity issue might look like this:

```
Individual issue

001-H/
  - 003.md
```

2\. Decide if the issue is a duplicate or not

* If it’s a duplicate, put it in the same folder as an issue that it’s a duplicate of
* If it’s not a duplicate, it will live in its own folder (if it’s a High or Medium)

A family of duplicate High issues might look like:

```
Family of issues

001-H/
  - 003.md
  - 007.md
  - 049.md
```

3\. If there are duplicates, pick the “best” issue out of the bunch (the issue that describes the vulnerability best)

For example, if 7.md was the “best” issue, you would rename it like so:

```
Family of issues (with best issue labeled)

001-H/
  - 003.md
  - 007-best.md
  - 049.md
```

Once you’ve gone through all of the issues, every issue should be in a folder. The top-level folder structure might look like:

```
001-H/
002-H/
001-M/
002-M/
003-M/
low/
false/
```

This would mean that there are 2 High severity vulnerabilities, and 3 Medium severity vulnerabilities.\
\
If you were to open up all the folders above, it might look like this:

```
001-H/
  - 003.md
  - 005-best.md
  - 012.md
002-H/
  - 006.md
001-M/
  - 007.md
  - 013-best.md
002-M/
  - 011-best.md
  - 016.md
003-M/
  - 014.md 
low/
  - 002.md
  - 004.md
  - 008.md
  - 009.md
false/
  - 001.md
  - 010.md
  - 015.md
```

This structure still means that there are 2 High severity vulnerabilities, and 3 Medium severity vulnerabilities (just like the top-level folder structure above).&#x20;

{% hint style="info" %}
"-best" only needs to be added when there is more than 1 .md file in a folder. "low" and "false" folders will not have "-best" because those issues will not be considered.&#x20;
{% endhint %}

Once the issues have been sorted into folders and "best" reports labeled, you are done!

## How to earn USDC from judging

In order to become eligible for a payout, your judging must be >=40% accurate. Each issue has 3 points:

1. Severity (Medium/High/else) = 1 point
2. Duplication (Is it in a folder with at least 1 correct duplicate issue? Or correctly put in a solo folder?) = 1 point
3. Best issue (Was the best issue of the duplicate family correctly chosen?) = 1 point

If there were 100 issues in a repo, and each issue is worth 3 points, then a contestant would need to get at least 120 points (120 correct / 300 possible = 40% score) in order to become eligible for a payout.

{% hint style="info" %}
Why is >=40% accuracy required for a payout? If only 5% accuracy received a payout, then audit contest participants could just judge their own submissions and get paid for it, which is not fair.
{% endhint %}

## How are USDC payouts calculated in a judging contest:

The formula for payouts is very similar to the sybil-resistant formula for audit contests.

{% hint style="info" %}
Remember that in an audit contest, you get paid way more if you find an issue that no one else finds. The dynamic is the same in a judging contest.
{% endhint %}

In the judging contest, you get paid way more if you get something correct that no one else gets correct. And you get paid less if 4 people get it correct vs. 2 people get it correct, etc.

There’s also a twist:

1. Correct "Severity" judgments are worth 10x
2. Correct "Duplicate" judgments are worth 5x
3. Correct “Best Report” judgments are worth 1x

And the judging contest uses an even stricter sybil formula, which means getting a “solo correct” issue is worth A LOT more than getting an issue correct alongside 3 other people. Sherlock hopes this will reimburse judges who spend the time to understand the most difficult issues in the judging contest.

The sybil-resistant formula is:

```
question_weight / 2.01 ^ (X - 1)
```

Where question\_weight is the multiplier for the question type (Severity, Duplication, Best), and X represents the number of judges who got the question correct.

After this, each judge will receive an individual score for their performance. And based on the individual\_score / total\_score, a proportional percentage of the contest pot will be awarded.

For example, if the contest pot is $2,500 and a judge receives 50% of all the points, then that judge will receive $1,250.
