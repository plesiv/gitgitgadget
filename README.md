# Contributing Git patches via GitHub PRs

This project's goal is to make contributions to the Git project almost as easy as opening a GitHub PR. The idea is for users to open a pull request at [](https://github.com/gitgitgadget/git) with a good description of their patch series. Then a "/submit" comment on that PR tells GitGitGadget to send the patches as a mail thread to [the Git mailing list](mailto:git@vger.kernel.org), using the pull request description as the cover letter.

As usual, reviewers on the Git mailing list will probably ask for changes. These should be folded into the respective commits (or added as standalone commits at an appropriate place in the patch series) via `git rebase -i`, followed by a force-push. Once everything is in good shape, update the description to summarize the changes relative to the latest iteration, and another "/submit" comment will ask GitGitGadget to send a new iteration of the patch series.

All relevant information—such as the current iteration of the patch series, the Message-IDs of the sent mails, and so on—is stored in Git notes under `refs/notes/gitgitgadget`.

GitGitGadget will Cc the original authors when sending patches on their behalf, as well as people mentioned in the `Cc:` footer of the pull request description.

Furthermore, for every iteration of a patch series except the first, GitGitGadget will append a machine-generated representation of what changed between revisions, replying to the cover letter of the previous iteration. This patch-revision diff can be suppressed by adding a `Range-Diff: false` footer in the pull request description, which is useful when the diff would be too large or irrelevant.

For the convenience of reviewers, GitGitGadget will generate tags for each iteration it sends and push them to [](https://github.com/gitgitgadget/git). Links to those tags will be included in the cover letter.
