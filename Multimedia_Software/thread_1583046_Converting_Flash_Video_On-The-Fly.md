---
title: "Converting Flash Video On-The-Fly?"
date: 2010-09-27
forum: Multimedia Software
---

### Post by fogNL on 2010-09-27
I know I'm going out on a limb asking this here, but I don't know where else to ask.

Its no secret that flash video performance is sub-par in Ubuntu.  I have a Zotac Mag HD ND01 that I have connected to my 40" LCD tv and have a minimal Ubuntu 9.10 installed running openbox and firefox/boxee/xbmc

My primary use for running a web browser is so I could watch live streaming hockey games in HD.  However, thanks to Flash's performance (and yes, i've tried the latest versions, even the 091510 version in labs) in full screen mode, watching hockey is not possible because its way too choppy.

Now, on my desktop computer in my office, I can watch the same stream without issue.  So, my question is, is there any way to take this live stream (which is using Flowplayer), and re-encode it on-the-fly so I can stream it to my htpc in a format it likes (such as MKV i guess, it can play 720p/1080p mkv files without issue)?

My desktop is a Core i7 920 overclocked to 4.2Ghz with 6GB DDR3 ram, so I would hope its powerful enough for the cause.  Also, the desktop is running Windows 7 64bit and Ubuntu 10.04 64bit on a dual boot, so a method in either is fine.

Is this possible?

---

### Post by SeijiSensei on 2010-09-27
Perhaps your office has more Internet bandwidth than you do at home?  What if you use the same player at home?

---

### Post by fogNL on 2010-09-27
> **SeijiSensei said:**
> Perhaps your office has more Internet bandwidth than you do at home?  What if you use the same player at home?

Sorry, I worded that wrong, my "office" meaning my office in my house.  Both computers are utilizing the same network connection.  The problem is definitely with the flash player because I can play any other hd media on the HTPC computer without issues.

---

### Post by lovinglinux on 2010-09-28
See [Flash Optimization](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html). Not a miracle maker, but can help.

---

### Post by Linuxforall on 2010-09-28
The x64 version of latest Adobe Flash under Linux runs brilliantly, on nvidia cards it uses the GPU and full screen videos hardly takes CPU %age like before.

---

### Post by lovinglinux on 2010-09-28
> **Linuxforall said:**
> The x64 version of latest Adobe Flash under Linux runs brilliantly, on nvidia cards it uses the GPU and full screen videos hardly takes CPU %age like before.

I have just released FLASH-AID 1.0.14, which supports the installation of flash 64bit square preview 2.

[https://addons.mozilla.org/en-US/firefox/addon/161939/versions/](https://addons.mozilla.org/en-US/firefox/addon/161939/versions/)
[http://github.com/lovinglinux/flash-aid/downloads](http://github.com/lovinglinux/flash-aid/downloads)

---

