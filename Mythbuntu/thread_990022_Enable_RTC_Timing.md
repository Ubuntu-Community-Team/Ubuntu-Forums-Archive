---
title: "Enable RTC Timing?"
date: 2008-11-22
forum: Mythbuntu
---

### Post by uncle hammy on 2008-11-22
Hi,

I have enabled the RTC hack on my backend machine running Hardy because I can't install 8.10 yet because of this [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271070](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271070)  


On my stand alone frontend, running 8.10, I can't enable the RTC hack because of this [https://bugs.launchpad.net/mythbuntu/+bug/290439](https://bugs.launchpad.net/mythbuntu/+bug/290439)

When this frontend was running 8.04, I was able to manually set the hack by adding dev.rtc.max-user-freq = 1024 to /etc/sysctl.conf.  I confirmed it worked using mythfrontend -v playback and found thd the "using timing method RTC" part in the output.

However, now that I am running 8.10 on this frontend, when I add the line to /etc/sysctl.conf it doesn't have any effect.  When I so sysctl -p, I shows an error of...

error: "dev.rtc.max-user-freq" is an unknown key

Can anyone please help me get RTC timing enabled on this frontend?  I seemed to have a little better video quality when I did.

---

### Post by ian dobson on 2008-11-22
Hi

Why not try setting the S option in chmod for nythfrontend.real (chmod +s /usr/bin/mythfrontend.real)?

On my box when I do that I see:-
2008-11-22 15:55:06.201 Using realtime priority.

and playback seems to abit smoother on my system.

Regards
Ian Dobson

---

### Post by uncle hammy on 2008-11-22
I have never enabled realtime threads that way.  I have always added to my /etc/security/limits.conf as per [http://www.mythtv.org/docs/mythtv-HOWTO-5.html#ss5.4](http://www.mythtv.org/docs/mythtv-HOWTO-5.html#ss5.4)

*                -       rtprio          0
*                -       nice            0
@audio           -       rtprio          50
@audio           -       nice            0

Which has always results in pretty bad system lockups for me.  However, I tried your suggestion, adding the above to limits.conf, and both.  None of them seem to work on this 8.10 installation.  No matter what I try, I get...

realtime priority would require suid as root

---

### Post by ian dobson on 2008-11-22
Hi,

The flag s just sets the "root user permissions" for the executable, when mythtv "sees" that it has the correct permissions to set realtime priority then it sets it.

It's a bit of a hack and some might say it's a security risk.

Have a look here:- [http://www.extremetech.com/article2/0,2845,2055103,00.asp](http://www.extremetech.com/article2/0,2845,2055103,00.asp)
Regards
Ian Dobson

---

