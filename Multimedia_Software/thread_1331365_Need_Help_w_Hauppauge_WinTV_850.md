---
title: "Need Help w/ Hauppauge WinTV 850"
date: 2009-11-19
forum: Multimedia Software
---

### Post by kblonder on 2009-11-19
I'm a complete beginner with Ubuntu and I'm trying to get my Hauppauge WinTV 850 digital TV tuner installed and working.  What I think I need is driver downloads and TV program software.  Please assume I know nothing.  Thanks!

---

### Post by laceration on 2009-11-19
take a look at this page:
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-850](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-850)

the drivers are already built in to Linux, but you need to install some firmware. Instrucs are on the page.

As for software...
I was in your position a while back and found the TV software in Linux unsatisfactory.  Eventually I wrote my own program, OSTV.  Of course I am biased but I think it is the best program available and easiest to set up.  However it is new, does not have many users or a track record.

Setting a TV system for a beginner will be challenging but is doable.  At this point it is easier to do in Windows.

Since I am interested in people trying out OSTV, I'll subscribe to this thread if you want to try it and be available to help/answer questions.

---

### Post by HappyFeet on 2009-11-19
Thanks for that laceration. I use vlc and mythtv for watching tv with no problems, but I will give OSTV a try, and let you know how it goes. Can I schedule recordings with it?

---

### Post by laceration on 2009-11-19
> **HappyFeet said:**
> Thanks for that laceration. I use vlc and mythtv for watching tv with no problems, but I will give OSTV a try, and let you know how it goes. Can I schedule recordings with it?

Cool!  Yes, OSTV schedules TV recordings and also bittorrent downloads.

---

### Post by kblonder on 2009-11-20
That all sounds great.  Thanks!  I'll try it out and let you know how it goes.

---

### Post by kblonder on 2009-11-20
So, like I said, I'm a beginner with this stuff.  I went to the website and wasn't able to do anything with the firmware download:

[http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip](http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip)
I downloaded it but wasn't sure which file to run (tried running the .exe file but got an error).

Also, this appears to apply only to analog and I think I need digital (connected to cable TV).

Don't know what to do.  Any help would be greatly appreciated.  Thanks.

---

### Post by steefjeqv on 2009-11-21
Hi,

You need to copy the firmware file to /lib/firmware. But before you do this, check your dmesg output (it may not be necessary to install extra firmware or drivers). In fact, your tuner should work out of the box (if you're using Karmic). Use your terminal with following command :

sudo dmesg | grep firmware

and

sudo dmesg | grep Firmware

If there's a firmware problem there should be an error message.

You can also use Kaffeine to test if your tuner is recognised (you can watch digital TV with Kaffeine too).

If you're interested in turning your Ubuntu in a full digital TV settopbox you might want to give VDR a try (it supports ATSC and DVB). There's a nice ppa put together by the VDR-Team :

[https://launchpad.net/~the-vdr-team/+archive/vdr-ubuntu-karmic]("https://launchpad.net/~the-vdr-team/+archive/vdr-ubuntu-karmic")

[https://launchpad.net/~the-vdr-team]("https://launchpad.net/~the-vdr-team")

Greetings,
Steven

---

### Post by laceration on 2009-11-21
kblonder,

I thought you might be asking a question like this;).

The instructions on the page are meant to typed into(or copied + pasted) into the infamous Linux command line terminal, aka the cli or terminal.

Go to the mainmenu->Accessories->Terminal

Type, or copy and paste in these commands one at a time followed by your Enter key.  The "$" represents the prompt -- don't type that in.

```

$ wget http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip
$ wget http://www.steventoth.net/linux/xc5000/extract.sh
$ sh extract.sh
$ cp dvb-fe-xc5000-1.1.fw /lib/firmware

```
An explanation of these commands: wget downloads, sh runs the script that you downloaded and cp copies the file to the right place.

This is for digital.  And .exe files do not do anything in Linux--a common noob mistake.

Also, before you get started on this, you do realize that the only cable you can get through your computer is the basic tier?  The premium channels are encrypted.  This is same in Windows, Linux or Apple.

---

