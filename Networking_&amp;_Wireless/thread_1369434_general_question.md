---
title: "general question"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by t1mb3rl1n3 on 2010-01-01
greetings
I have not posted much here and I am sorry for that
because I do like Unix and especially Ubuntu very much
but I am used to ascertaining answers on my own
this is, though, a puzzler
and so I reach to you folks for help
I may not check back here
so if you know or want to discuss this it might be better to mail me @ <snip>

the question I have is thus:

is there a way via command line to suspend, pause, stop, or otherwise inhibit local TCP or UDP ports specified by port number?

to date, the best solution I have found to this is a program that runs under Wine called Cports
but I noticed today that it does not override some programs running in the shell
thus, it is a vulnerability as much as it is an anonymizer
because if I can't close down specific ports that it opens
at whim
they can be used to reach to me

so my curiosity is aroused

do any of you have an answer to this?

---

### Post by t1mb3rl1n3 on 2010-01-16
bump

so far the best I have found to do is shut with cports

_or_

source down running process with ps -A | less and sudo kill it by trial and error

---

