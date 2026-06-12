---
title: "error logging"
date: 2009-05-26
forum: Mythbuntu
---

### Post by iitywygms on 2009-05-26
So I am using over the air signal now.  My mythfrontend.log is getting filled with this.
2009-05-21 21:21:58.079 [mpeg2video @ 0x7fc311d8ee70]slice mismatch
2009-05-21 21:21:58.079 [mpeg2video @ 0x7fc311d8ee70]ac-tex damaged at 1 4

I know this is because I have a weak signal on some channels and there is not much I can do about it.  Question is, can I stop this from being logged?
Every day my mythfrontend.log is filled with these error messages and it is huge! 106000 lines last time I checked.
Thanks

---

### Post by pebo on 2009-05-26
Try managing the log file with [logrotate]("http://manpages.ubuntu.com/manpages/hardy/man8/logrotate.8.html"). hth.

---

### Post by tgm4883 on 2009-05-26
> **pebo said:**
> Try managing the log file with [logrotate]("http://manpages.ubuntu.com/manpages/hardy/man8/logrotate.8.html"). hth.

That probably isn't going to work.  logrotate is already used to manage the log files.  Unfortunatly it is only run once a day, so your log files may be filling up faster than that.  I believe you can change the logging level, although I'm not sure what level you would need to go to so that doesn't get logged.

I'll do a little more research when I get home.

---

### Post by iitywygms on 2009-05-28
Thanks, I look forward to your response

---

### Post by ian dobson on 2009-05-28
Hi,

Maybe you could start mythfrontend with a command line option to reduce the logging level:-

&#8722;&#8722;verbose
increases verbosity of mythfrontend. valid options are: all quiet important record playback channel osd file schedule network commflag audio libav

Regards
Ian Dobson

---

### Post by tgm4883 on 2009-05-28
Yep, what Ian said should help.

---

