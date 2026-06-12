---
title: "Sound &quot;Clicks&quot; when playing audio after update (12.04.1 x64)"
date: 2013-02-05
forum: Multimedia Software
---

### Post by redroserade on 2013-02-05
Greetings everyone.

I recently installed Ubuntu 12.04.1 on my laptop after switching the HDD, and I was glad that everything was working fine (sound, wireless, etc., which were problematic in previous versions of Ubuntu).

Previous versions of Ubuntu always developed a problem (it was usually after a system update), where sound playback would often produce audio "pops" and "clicks".

When Ubuntu was installed (installed it yesterday) there were no problems;
Installing the proprietary nvidia drivers and rebooting didn't cause the problem;
Updating packages and rebooting broke audio quality.

This issue seems well documented, there are bugs on such issues, like [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201"), and people said that the workaound is to disable power saving.

I did such things, rebooted and so on, but the issue persists, although it isn't as pronounced as it was before (instead of clicking every half-second or so, it only clicks about every half-minute, but it seems more pronounced under heavier system loads).

I now leave you with some information about the laptop (ask me if you need more):
lspci -vnvn output: [http://pastebin.com/zeXhMdrL](http://pastebin.com/zeXhMdrL)
aplay -l output: [http://pastebin.com/mxuLuekN](http://pastebin.com/mxuLuekN)
alsa-info.sh output: [http://www.alsa-project.org/db/?f=dc2959fab329f2bb9280010bf73bb449771b196f](http://www.alsa-project.org/db/?f=dc2959fab329f2bb9280010bf73bb449771b196f)

---

