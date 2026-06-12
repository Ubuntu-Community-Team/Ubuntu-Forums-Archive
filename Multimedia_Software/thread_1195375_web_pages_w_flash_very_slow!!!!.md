---
title: "web pages w/ flash very slow!!!!"
date: 2009-06-23
forum: Multimedia Software
---

### Post by HH60Gunner on 2009-06-23
It hadn't always been this way.  I used to use ubuntu some time ago then switched to try a few other distros of linux only to make my way back to ubuntu recently.  I'm very happy with it except for this one thing.  Any web pages that have flash on it are sooooo sloowwwww it's almost unbearable.  For now I just use flashblocker so that normal browsing isn't slow.  If this was fixed and I found a solution to stream video to my xbox 360 I'd be a very happy man.  After all it's hard to try and talk up linux to my friends when something so simple as flash makes it look like a pinto when browsing online and thier windblows boxes are blowing it out of the water w/ flash enabled.  Any idea on what could be causing this or is this a known problem?

---

### Post by kerry_s on 2009-06-23
i just keep flash disabled in the tools> add-ons
and turn it on when i want to use it on a site. most of the time i don't even need to turn it on, i have the "unplug" add on and can copy the link to watch in gnome-mplayer. i prefer to use external so i can close firefox.

it looks like this->

---

### Post by HH60Gunner on 2009-06-23
meh, I just find that to be an extra hassle when I'm just doing some quick browsing.  So is this the common theme then or is there a fix to the problem?

---

### Post by kerry_s on 2009-06-23
yes, it's a common problem in linux.
no, theres no fix.

i'm running on 450mhz 256mb ram, so for me, i have to work around the limitations of my rig.

it's funny though, flash plays perfect outside the browser, but in the browser i get everything from stuttering, skipping, to full on freezes.
i so wish flash would just die, any other media format works like a champ.

---

### Post by lovinglinux on 2009-06-23
You might get some improvements from my new tutorial [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). I still have issues with some flash videos, but I have manged to make it play YouTube HD without many hiccups. These are my [Peacekeeper](http://service.futuremark.com/peacekeeper/index.action) benchmark improvements since I installed Jaunty:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=118681&d=1245764692[/IMG]

---

### Post by kerry_s on 2009-06-24
interesting, i tried that peacekeeper and got an unresponsive javascript pop up, then the browser froze. :( i'll try again later, i'm doing a net install of debian on another machine, so it would have probably been slow.

what does the numbers mean? high good/bad, low good/bad?

---

### Post by lovinglinux on 2009-06-24
> **kerry_s said:**
> interesting, i tried that peacekeeper and got an unresponsive javascript pop up, then the browser froze. :( i'll try again later, i'm doing a net install of debian on another machine, so it would have probably been slow.

what does the numbers mean? high good/bad, low good/bad?

High is good. Just for comparison, the highest score of all users, which is 4521, is from Safari on an Intel Core i7 processor, while IE 8 scores only 1065. More statistics [here](http://service.futuremark.com/peacekeeper/browserStatistics.action).

My scores are very low because my processor is a P4 3.06Ghz HT.

---

### Post by kerry_s on 2009-06-24
> My scores are very low because my processor is a P4 3.06Ghz HT.

so then my 450mhz is probably going to make me cry. :lolflag:

---

### Post by lovinglinux on 2009-06-24
> **kerry_s said:**
> so then my 450mhz is probably going to make me cry. :lolflag:

:lolflag:

Please post your results if you try it. Would be interesting to know the difference between our machines. Who knows what you might get?

---

### Post by kerry_s on 2009-06-24
> **lovinglinux said:**
> :lolflag:

Please post your results if you try it. Would be interesting to know the difference between our machines. Who knows what you might get?

i'm still trying to get a debian install on my new computer. :(
it's a foxconn r10-s4 barebones i ordered from newegg, just came this evening, i threw in a 250gb sata i had in a usb enclosure & 512mb ram that i had lying around. i don't have a sata cd drive, so i'm using a usb thumb drive to do a debian testing net install, i can't seem to get a good net install, it looks like like somethings wrong with some packages on the debian testing repos.
i've tried i686 install, then the amd64, now i'm back to i686. this time i'm trying a base install only and i'm going to build it up from there.

anyways, looks like it's going to be awhile before i can mess around with that peacekeeper test.

---

### Post by kerry_s on 2009-06-24
oh my god! i probably got the lowest score ever recorded there. :lolflag:

---

### Post by lovinglinux on 2009-06-24
> **kerry_s said:**
> oh my god! i probably got the lowest score ever recorded there. :lolflag:

Wow. That is really low. But think positive, because it only can get better :)

---

### Post by kerry_s on 2009-06-24
> **lovinglinux said:**
> Wow. That is really low. But think positive, because it only can get better :)

as soon as i finish setting up my new computer, i'm going to try with that. it has a dual core atom 330 1.6mhz & 512mb ram.
i'm installing the gui part now, maybe in about 45min. :D

---

### Post by wojox on 2009-06-24
Yes it´s a problem and I don´t see any fixes coming soon. I've been a programmer for some years now and IMHO Flash is trash. It´s not true programming. To succeed in web programming your target audience has to be EVERYONE. Last I checked (many moons ago) you could not even view Flash on a dial up connection. Yes believe it or not people still use dial up. I keep mine disabled under plug-ins in Firefox.

---

### Post by kerry_s on 2009-06-24
hey even my brand new computers got a low score? am i suppose to use flash?

---

### Post by lovinglinux on 2009-06-24
> **kerry_s said:**
> hey even my brand new computers got a low score? am i suppose to use flash?

Mmmm, weird. My score was like yours when I first installed Jaunty and I don't have dual core. What's your graphics card? Do you have the proprietary driver enabled? Have you tried the tweaks from my tutorial?

No. You are not supposed to use flash.

---

### Post by kerry_s on 2009-06-24
> **lovinglinux said:**
> Mmmm, weird. My score was like yours when I first installed Jaunty and I don't have dual core. What's your graphics card? Do you have the proprietary driver enabled? Have you tried the tweaks from my tutorial?

No. You are not supposed to use flash.

its no big, it's just a junk intel, lspci:

```
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

```

i didn't expect much from this thing anyways, i just needed something on the cheap to replace my old computer that died.
i plan on maxing out the ram later, it can take 2gig, i only have 512mb in it now.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16856119012&Tpk=foxconn%20r10-s4](http://www.newegg.com/Product/Product.aspx?Item=N82E16856119012&Tpk=foxconn%20r10-s4)

---

### Post by lovinglinux on 2009-06-24
> **kerry_s said:**
> its no big, it's just a junk intel

Ah, that's the problem. Check [this thread](http://ubuntuforums.org/showthread.php?t=1130582).

---

### Post by kerry_s on 2009-06-24
> **lovinglinux said:**
> Ah, that's the problem. Check [this thread](http://ubuntuforums.org/showthread.php?t=1130582).

:lolflag: i still got exactly the same score, at least i know it's consistent. :D

---

### Post by raymondh on 2009-06-24
@ lovinlinux ... I scored 984.  Any reco's on improving it? Using an ATI HD 26ooXT and 4GB Ram.  Jaunty but still using 28.11 kernel

---

### Post by lovinglinux on 2009-06-24
> **raymondhenson said:**
> @ lovinlinux ... I scored 984.  Any reco's on improving it? Using an ATI HD 26ooXT and 4GB Ram.  Jaunty but still using 28.11 kernel

The only tweaks I know are in the [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567), but if there isn't any good reason to not update to the 28-13 kernel, I would do it. The last update I did, which included the kernel, xorg and compiz has improved my system performance considerably ([see discussion](http://ubuntuforums.org/showthread.php?t=1195028)).

---

### Post by plpinet on 2009-07-01
After a while I just realized that Ubuntu is using swfdec to read flash sites and it seems this version is buggy for some people.

sudo apt-get remove swfdec-mozilla

That did the trick for me, now everything in flash works perfectly fine. You might have to redownload flash10 from adobe.com.

---

### Post by gordintoronto on 2009-07-18
> **lovinglinux said:**
> :lolflag:

Please post your results if you try it. Would be interesting to know the difference between our machines. Who knows what you might get?

My CPU is an Athlon XP 2400+ (2 GHz) and video is an nVidia GeForce 2 MX 400, AGP 4x.  I have 512 MB of memory in this 6-year-old computer.

Running Firefox 3.0.12 with extensions, my score is 502.  I can play youtube videos in full screen with no problem.

Your machine should be around 50% faster, but it isn't.  I don't have either swfdec installed, do you?

---

### Post by lovinglinux on 2009-07-19
> **gordintoronto said:**
> My CPU is an Athlon XP 2400+ (2 GHz) and video is an nVidia GeForce 2 MX 400, AGP 4x.  I have 512 MB of memory in this 6-year-old computer.

Running Firefox 3.0.12 with extensions, my score is 502.  I can play youtube videos in full screen with no problem.

Your machine should be around 50% faster, but it isn't.  I don't have either swfdec installed, do you?

No, I haven't. Check [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567) to see what I have done to improve flash performance.

---

