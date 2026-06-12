---
title: "No desktop effects after upgrading to 9.10"
date: 2009-10-30
forum: Multimedia Software
---

### Post by Jerfo on 2009-10-30
Well, no matter how much I search I can't seem to find an answer. It's as simple as that, once I updated to 9.10 I can't have anything but "no desktop effects" because should I choose anything else I get a black background with no icons, even though the effects seem to work fine. It was all working perfectly with 9.04.

---

### Post by beastrace91 on 2009-10-31
What video card and what driver version (if any) do you have installed?

~Jeff

---

### Post by Jerfo on 2009-11-01
Radeon 9200 and as far as I know it's using whatever drivers it automatically installs because so far I've been unable to get any drivers working reading the various guides I've found :s

---

### Post by jheylin on 2009-11-01
After the upgrade I too can't find desktop effects. I have an NVIDIA GeForce 8600M GT in my Dell M1530 laptop and have the Accelerated driver version 185 activated. I tried switching back to driver version 173 but it still didn't pop up on the menu.

Really wishing I could get my spinning block back after the update.

---

### Post by lazycamel on 2009-11-01
Same problem. I haven't been able to run desktop effects since 8.04, where I got the nvidia drivers working perfectly after extensive research and work and doing a whole new xorg.conf by hand.

Starting up first time after a clean install of 9.04 and the graphics was all skewed again, did the same thing with X again, got the full range of screen resolutions at least, but no way no how would compiz work.

Smooth upgrade to 9.10, which looks and feels great, but more graphics weirdness. Every time it starts up it makes the desktop bigger than the screen, so you have to scroll it up and down with the mouse to see the edges. Using the display configurations to change the resolution away from and back to the right resolution fixes the problem.

No apparent reasons for any of this. I'm using GeForce FX 5200. It has been suggested there's a hardware problem of some sort (blacklisted PCIID), but it worked fine under 8.04, and I can't see what's different now.

---

### Post by psidrum on 2009-11-01
i got the same problem, i have a Radeon X1600

---

### Post by epek on 2009-11-01
My old Ati Radeon 9200 had a similar issue right after the upgrade.
First compiz was disabled, afterwards program windows where black, but the menu would pop up.

In my case I opened a terminal and tried to compiz --replace or compiz.real --replace, that did not solve the problem but I enabled my to switch back to the menu. (That resolved the black-background-problem for me on an old nforce2 board with Radeon 9200)

Afterwards I switched the desktop effect settings from it´s system control icon. First: Disable/Ok, than Normal/Ok, than Extended/Ok.

That solved the issue for me.

Possible other ideas:
* You might have an entry in your modules blacklist in order to disable an ancient, now updated framebuffer kernel module.
* You have a wrong graphics card driver - go to a console using alt+f1, log in, and give us the output of lspci and send us the contents of /etc/X11/xorg.conf, if possible. Especially the radeons have multiple drivers.
* Intel graphics should be "stable" again in this release. Maybe you have the wrong platform kernel. Try the generic flavour on AMD processor machines or the 386-flavour (with is also for x64, afaik) on an intel platform.

---

### Post by tuvelijn on 2009-11-01
My old ATI radeon 9000 card gives black desktop after upgrading to Ubuntu 9.10; all application windows on maximum size are black. 
The previous release did not support 1400x1050 out of the box. Adjusted configuration and all worked well. But now on the right screen resolution the desktop/windows are black. Are there solutions??

Solution found: switched from normal to no visual effects and the desktop reappeared.

---

### Post by Jerfo on 2009-11-02
Actually, I do not have a xorg.conf file anymore, I don't remember how I got my card working when I first installed Ubuntu about a year ago but I remember it did take some effort and some xorg.conf editing, so at first I followed the instructions I found and assumed it'd get the problem solved but I kept getting this error because no such file as xorg.conf existed so I went on to create one and ended killing my graphic interface, had it not been because I logged in using the livecd and deleted the file manually (I can't use the purely text interface, people, I just don't know that much!) I'd be stuck with no graphics at all.

So no, adding lines to xorg.conf did deffinitely no good to me this time!

---

### Post by TUOggy on 2009-11-22
Were you able to get this working?  I'm experiencing a similar problem, and can't get the Visual Effects working.

I have a Radeon 9200.

---

### Post by cuppieinc on 2009-11-23
Hi,

I had the exact same problem after upgrading to 9.10. In 9.04 my Radeon X1650 could display the desktop effects, but after upgrading to 9.10 I got the error that desktop effect could not be enabled.

After searching around and playing with my xorg.conf I found the solution for my problem at [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver).

Basically, the fglrx driver needs to be removed and the original libgli1-mesa need to be re-installed. After doing this and rebooting the system I could enable the desktop effects again.

regards,

Cuppieinc.

---

### Post by mist4u on 2009-11-24
I upgraded my Ubuntu from 9.04 to 9.10

I get a message "Desktop effects could not be enabled" when I click on the System>>Preferences>>Appearance Visual Effects and then Normal or Extra

What should I do to enable these effects?

Thanks,
mist

---

### Post by mist4u on 2009-11-24
**_$lspci_**
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)


_**xorg.conf contains:**_
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

---

### Post by TUOggy on 2009-11-25
> **cuppieinc said:**
> 
After searching around and playing with my xorg.conf I found the solution for my problem at [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver).


Thanks for the reply Cuppie, I tried this, but couldn't find anything on the RadeonDriver page that actually helped.

```

$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200] [1002:5961] (rev 01)

```

When I try to follow the steps under the RadeonDriver, X wont start at all...

This is getting very frustrating for something that worked fine in 9.04...

---

### Post by TUOggy on 2009-11-29
So nobody has any idea how to get the Visual Effects working with an ATI Radeon 9200?

---

### Post by rockdj on 2009-11-30
> **jheylin said:**
> After the upgrade I too can't find desktop effects. I have an NVIDIA GeForce 8600M GT in my Dell M1530 laptop and have the Accelerated driver version 185 activated. I tried switching back to driver version 173 but it still didn't pop up on the menu.

Really wishing I could get my spinning block back after the update.

Same here with the same model laptop and gfx card.  Nothing's helped and even the latest nvidia drivers (192.xx) didn't help at all.  The drivers are apparently activated (as mentioned) but no luck. :icon_frown:

---

### Post by TUOggy on 2009-12-01
I am still having the same problems.  I can't seem to find any answers for it.

Here is just one of the issues I am having because of this issue:

[IMG]http://i53.photobucket.com/albums/g52/tuoggy/Screenshot.png[/IMG]
Yes, this happens both with and without using OpenGL


Now I'm regretting ever attempting to upgrade from 9.04.

It was so much better...

---

