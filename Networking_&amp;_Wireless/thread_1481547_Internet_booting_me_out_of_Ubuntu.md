---
title: "Internet booting me out of Ubuntu"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by kemah201 on 2010-05-08
Hello folks,

I have been using Ubuntu for years and I've never had any problems. I now have a fresh install of 10.04 on my IBM T41 laptop. I was checking my email in firefox and I was automatically logged out and prompted to log back in. I ran the SMART test on the hard drive and everything tested healthy. As I've never had to troubleshoot any issues before, I do not know where to begin. Is it worth booting the live cd and tested the filesystem for errors? Are there any log files that I should inspect?

Thanks,
Happy Ubuntu user

---

### Post by bumanie on 2010-05-08
Could have been an issue with your isp, rather than ubuntu. Wouldn't worry unless it happens again, then it may be worth investigating.

---

### Post by kemah201 on 2010-05-12
hello folks,

this has happened twice now. I click on a link in firefox and get booted out to the login screen. Any advice? I am running ubuntu gnome 10.04 clean install.

thanks,
happy ubuntu user

---

### Post by kemah201 on 2010-05-14
I've posted twice previously because the internet is crashing ubuntu on me. What's up with this latest release. I've never had these issues going back 3 releases. This is supposed to be a LTS. So much for that. The previous release was more stable.

---

### Post by jerome1232 on 2010-05-14
This is a support thread?

Generalized statements based on one experince are annoying. It works fine for me, works fine for many others. It's not a wide spread common problem.

Make a real attempt at getting help. What's crashing, Firefox? When? like for example is it usually when you goto a site with flash on it? You using x86 or x86_64?

etc.. etc..

---

### Post by QIII on 2010-05-14
It is unfortunate that you are having problems.

I have been using Lucid as my primary since the first Beta and have not had any issues.

It might be more correct to say that it is unstable for you -- which is what we need to address as quickly as we can so you can get back to enjoying yourself!

Could you give a little more information such as the specifications of your machine and a little more detailed description of what behavior "crashing" is?

---

### Post by malangaman on 2010-05-14
It is very stable for me!
Please describe your problem in more detail.

---

### Post by mhgsys on 2010-05-14
stable here; 

check your /var/log/messages
dmesg 
etc.


edit; ohw .. your talking about internet crashing? Or ubuntu crashing on internet ?Or internet crashing ubuntu?

As suggested before; be more specific about the problem your running in to

---

### Post by (^_^)Smiley on 2010-05-14
I agree lucid has a tons of problems! I had many problems with lucid 64 bits version overheating and
some times on reboot it shows me a disk checking for errors. But after installing the 32 bits version
the laptop works better but still my laptop overheats.

---

### Post by jbiwer on 2010-05-14
I agree.  I have had *numerous* unsolicited system reboots with 10.04
[IBM ThinkPad R40].  I do not recall this happening with any previous versions.

I am however, using this laptop more often, longer periods of time, etc.
Is rebooting a heat related problem?  Other than rebooting, it works fine.

Thank you!

---

### Post by StuartN on 2010-05-14
There seem to be some serious instability problems that are extremely difficult to trace, because the log files are not written in a filesystem remounted readonly at the time of the freeze. Two active Launchpad bug reports contain more information at:

Repetitive massive filesystem corruption Bug #528981 [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/528981](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/528981)

resume from suspend does not work Bug #568711 [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711)

There are plenty more threads on the forum, with various workarounds that people have tried - it is worth noting that there are some issues with NVidia and Intel hardware that can be worked around:

Possible Sleep/Hibernation issues with 10.04? [http://ubuntuforums.org/showthread.php?t=1469167](http://ubuntuforums.org/showthread.php?t=1469167)

ubuntu 10.04 - Suspend, Hibernate not working [http://ubuntuforums.org/showthread.php](http://ubuntuforums.org/showthread.php)

[10.04] Ubuntu freeze because of Firefox? [http://ubuntuforums.org/showthread.php?t=1469650](http://ubuntuforums.org/showthread.php?t=1469650)

Lucid Freezes Randomly [http://ubuntuforums.org/showthread.php?t=1470452](http://ubuntuforums.org/showthread.php?t=1470452)

Hibernate & Suspend- can't wake up [http://ubuntuforums.org/showthread.php?t=1472860](http://ubuntuforums.org/showthread.php?t=1472860)

10.04 false I/O errors and random freezes [http://ubuntuforums.org/showthread.php?t=1473131](http://ubuntuforums.org/showthread.php?t=1473131)

Display Freezes - Fresh 10.04 install [http://ubuntuforums.org/showthread.php?t=1474730](http://ubuntuforums.org/showthread.php?t=1474730)

Sudden Read-Only File System?! [http://ubuntuforums.org/showthread.php?t=1475124](http://ubuntuforums.org/showthread.php?t=1475124)

Ubuntu 10.04 display freeze up [http://ubuntuforums.org/showthread.php?t=1476125](http://ubuntuforums.org/showthread.php?t=1476125)

---

### Post by lisati on 2010-05-14
Threads merged

---

### Post by QIII on 2010-05-14
> **(^_^)Smiley said:**
> I agree lucid has a tons of problems! I had many problems with lucid 64 bits version overheating and
some times on reboot it shows me a disk checking for errors. But after installing the 32 bits version
the laptop works better but still my laptop overheats.


Again -- "for you".  That doesn't make it any easier for you to take, I know, but you have to remember that there are likely millions of people using it that don't come here to ask for help because it is working fine.

We'd be happy to help you with those tons of problems, but one at a time!  ;)

---

### Post by QIII on 2010-05-14
> **StuartN said:**
> There seem to be some serious instability problems that are extremely difficult to trace...

Is that any more or fewer than the number of issues people were having with previous versions?

What number of people does that represent as a percentage of those using Lucid without problems?

We just don't know.

It may be horrendously large.  It may be fantastically small.

But you have to keep in mind that there are also Windows help forums aplenty, and I would be willing to bet the phones are ringing off the hook at Windows7HelpForum.org.

It's easy to just say something sucks.

Harder to help someone with a particular problem.

The latter is what we need to concentrate on.

---

### Post by utnubuuser on 2010-05-14
Let me guess..  ATI card?

7000 series card?

I've had the same prob with 10.04 and thinkpad/desktop with ATI.  Desktop was worse than thinkpad

what's the output of > lspci -v | grep ATI

If it is a network-manager issue, you could try switching to wicd instead.

---

### Post by kemah201 on 2010-05-25
Thank you for all the suggestions so far. I will try to better explain the original issue. I will click on a link in Firefox and I will get booted out to the login screen. So to eliminate Firefox as the culprit I switched to Chromium and I experienced a similar issue where I clicked on a link and the screen went black and froze with the cursor frozen on the screen. This very may well be an overheating issue. Is there a way to determine if this is the issue?  I am running an IBM T41.

Here is the answer to the question in the previous post:

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]

So yes, to answer the previous question, it is a 7000 series card. What does this mean?


Thanks much,

---

### Post by kemah201 on 2010-05-27
bump

---

### Post by Man_Beach on 2010-06-09
Ah, so that's my problem. I, too am having firefox throw me back to the login screen from certain sites. It's not repeatable - sometime it does, sometime it doesn't. But I too have a ATI Radeon 7000 series card (to be precise, I get 'ATI Radeon RV100 QZ [Radeon 7000/VE]'.

So, what's the solution - and why hasn't it happened with all of the other versions of Ubuntu which I've used in the past? Or is it just Ubuntu telling me that it's time to invest in a new computer (preferably without an ATI video card)?

---

