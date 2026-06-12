---
title: "Rewriting titles in e-mails"
date: 2009-10-13
forum: Networking &amp; Wireless
---

### Post by PypeBros on 2009-10-13
Hello all,

I was wondering if there is some existing mechanism i could use to batch the rewriting of titles of e-mails. E.g. I receive lots of mails with titles such as "[Pr0jectList-Developers] <actual subject>" that makes readability of the inbox a nightmare. I'd love some feature that would let me say "on folder Inbox, move mails with "[Pr0jectList-(.*)] (.*)" into folder "Pr0ject" with title "[$shortname{$1}] $2".

Obviously, message filters of Thunderbird already handles the first part, but it doesn't seem to provide the "titles rewriting" itself. Before i start trying to add a PERL engine into a mozilla application, i was curious if any of you knows an existing tool that could help me. A google search and a scan through thunderbird extensions didn't provide anything useful.

Ideally, the solution wouldn't require to modify the mail server and would fit with a pop3 -> thunderbird setup, but if "Mail reader Xyz does it that way ..." or "imap handle this as ..." is the solution, i could live happily with it.

---

