---
title: "Lynksys WUSB54GSC Present on USB list but not operating"
date: 2010-12-29
forum: Networking &amp; Wireless
---

### Post by lavallie on 2010-12-29
I just installed the latest version of Ubuntu Desktop.  When I do a "lsusb" I can see the device present but the light is not on and I cannot see the wireless router.

Amazing that I can be at version 11.04 and it still doesn't see a wireless device and install it.

So, my guess is that I have to root around about 5 different places and gather up a bunch of files so I can get this running.

Any help would be appreciated...Tks

---

### Post by Bucky Ball on 2010-12-29
That is your issue probably. There is no 11.04. You are using 10.10 Maverick Meerkat I think. There has been a bug with that on some machines.

What computer are you using? Did this happen after an update?

You might want to try 10.04. Little more stable and long term support release so supported for another year beyond 10.10.

There is currently a thread to report this issue here:

[http://ubuntuforums.org/showthread.php?t=1653568](http://ubuntuforums.org/showthread.php?t=1653568)

---

### Post by lavallie on 2010-12-29
Bucky, thanks for your reply.  Now I am even less impressed.  That is the version that I get when I go to the information about the newly downloaded version.  I went to the Ubuntu site and downloaded directly from there.

Are you telling me that they are feeding me a "buggy" version??  Wow!!! Amazing!!!

This is an ACER Pentium Dual Core system.  About a year old.

Thanks for your response.... very enlightening.

---

### Post by Bucky Ball on 2010-12-29
Hey, it is only happening on a few machines. I am using the very same kernel and it is problem free on a Toshiba Satellite Pro L510. Have a read of the link I posted and add your experiences. That will help the developers work it out. This is an extremely rare occurrence so don't let it put you off.

As I say, try 10.04. Bit more stable and a long term support release. (10.04 = April, 2010: 10.10 = October, 2010 - 10.04 been around a bit longer and will be around a bit longer). :)

---

### Post by Shibblet on 2010-12-29
> **lavallie said:**
> Are you telling me that they are feeding me a "buggy" version??  Wow!!! Amazing!!!

11.04 is a pre-alpha at this point.  I'm not sure you went to the right site to download Ubuntu.

Go to [www.ubuntu.com](www.ubuntu.com) and click on the big orange button that says "Download Ubuntu" from there you can choose the x86 or x86_64 version of Ubuntu 10.10 (Maverick) or 10.04 (Lucid)

---

### Post by lavallie on 2010-12-29
> **Shibblet said:**
> 11.04 is a pre-alpha at this point.  I'm not sure you went to the right site to download Ubuntu.

Go to [www.ubuntu.com](www.ubuntu.com) and click on the big orange button that says "Download Ubuntu" from there you can choose the x86 or x86_64 version of Ubuntu 10.10 (Maverick) or 10.04 (Lucid)

OK here is the issue. I did go to the exact web site to download.  And clicked on the Download button.  But the box listed version 10.10 (current version) then the second choice was the 10.04LTS.  

Now the average person like me would say, yea current version, that sounds good.. besides what the hell is LTS????  So I downloaded it.

Once installed I find that I am at version 11.04. 
(You are using Ubuntu 11.04 - the Natty Narwhal - released in April 2011 and supported until October 2012) 

Just makes no sense to me.

Why do they do this???  I wasted hours screwing around with this version and the problem with the wireless.

Why do they put a "not for prime time version" up one the main page of the web site???

---

### Post by bkratz on 2010-12-29
> **lavallie said:**
> OK here is the issue. I did go to the exact web site to download.  And clicked on the Download button.  But the box listed version 10.10 (current version) then the second choice was the 10.04LTS.  

Now the average person like me would say, yea current version, that sounds good.. besides what the hell is LTS????  So I downloaded it.

Once installed I find that I am at version 11.04. 
(You are using Ubuntu 11.04 - the Natty Narwhal - released in April 2011 and supported until October 2012) 

Just makes no sense to me.

Why do they do this???  I wasted hours screwing around with this version and the problem with the wireless.

Why do they put a "not for prime time version" up one the main page of the web site???



You did not do anything wrong. Recently with some hardware it is indicating 11.04, but it is hopefully just a temporary event. The 10.04 LTS (which is what I run) stands for long-term-support. So updates will be provided for a longer time period.

---

### Post by lavallie on 2010-12-29
Thanks Bkratz... just frustrates me when stuff like this happens.

---

### Post by PatchesTheCaveman on 2010-12-29
Go to Applications > Accessories > Terminal and type the following command and press Enter:
```
uname -r
```

If that outputs *2.6.35-24-generic*, you are running an broken version of the Linux kernel Canonical recently released.  We've discovered that that version seems to break tons and tons of USB and network devices.  It can be fixed simply by downgrading to the previous version of the kernel.

I haven't seen this, but apparently this broken kernel also makes 10.10 Maverick Meerkat appear to be 11.04 Natty Narwhal even though it obviously isn't that version.

We've been discussing this issue in [this thread]("http://ubuntuforums.org/showthread.php?t=1653568") and there are instructions on how to downgrade your kernel in the [last two posts]("http://ubuntuforums.org/showthread.php?t=1653568&page=2").

---

### Post by Bucky Ball on 2010-12-29
> **PatchesTheCaveman said:**
> Go to Applications > Accessories > Terminal and type the following command and press Enter:
```
uname -r
```If that outputs *2.6.35-24-generic*, you are running an broken version of the Linux kernel Canonical recently released. 

One more time people: This is a bug-reported, known issue affecting a small number of machines, particular brands and models, NOT EVERY MACHINE ACROSS THE BOARD!!!

Many of us are running this kernel problem-free.

---

