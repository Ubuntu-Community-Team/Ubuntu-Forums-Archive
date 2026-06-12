---
title: "Frozen: Dell Dimension 2400 Intel 82845G/GL/GE Chipset"
date: 2010-04-06
forum: Multimedia Software
---

### Post by abpriest on 2010-04-06
I've seen a bit about the display being frozen on intel integrated displays, but I do not see the answer anywhere. Does anyone know how to fix this problem:

Ubuntu 9.10 boots and runs just fine for 10, 20 or even 30 minutes performing variety of tasks. Then, without warning the display is frozen. The mouse can move the pointer just fine, but I cannot interact with the desktop and the machine must be shutdown by holding the power button. 

I've observed this while playing a Kpatience game, general surfing of the internet, and view youtube videos. One time it happened when the display powers off after being idle, but this is not consistently the case. I have tried to make the freeze happen, but am unable to do so (so it seems, anyway). What is happening here?:confused:


Here are the details of my system:

Dell Dimension 2400 Desktop
Output from lshw:
        *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e8000000-efffffff(prefetchable) memory:feb80000-febffff

---

### Post by abpriest on 2010-04-07
Update: I turned off the screen saver at 10:30 last night and it is still working great (no freezes) at 7:00 am ( I left it on all night and let power management turn off the monitor).
But this doesn't feel like the problem or a solution.

---

### Post by wavesailor on 2010-04-08
Abpriest - Can you confirm the your freezes have disappeared? 

I have that same setup as you (Dell Dimension 2400 Intel 82845G/GL/GE Chipset) and I am experiencing the same freezes as you.

Googling it seems a lot of people are experiencing the same issues and the best option seems to revert to the [Jaunty Xorg intel driver to 2.4]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4")

Can you or anyone confirm this?

-jj

---

### Post by Johnzw on 2010-04-20
I also have exactly the same problem with that integrated graphics chip.

The system in question is constructed mainly from spare parts, however. Here is lspci -nn

```

00:00.0 Host bridge [0600]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface [8086:2560] (rev 01)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge [8086:24c0] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DB (ICH4) IDE Controller [8086:24cb] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
01:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller [8086:1039] (rev 81)

```and output of lshw is attached

EDIT:

Also, I've already tried reverting the X driver, didn't work. I've tried the Jaunty graphics thing, didn't work. 

prior to the upgrade to Karmic X often hung when switching VTs or after a user logged out. Interestingly, this manifested with the X cursor in the center of the screen over a black and white dots-pattern background at a very low resolution (I'd guess 800x600 or lower). This no longer happens, now the hangs happen seemingly randomly.

---

### Post by purgatori on 2010-04-25
This problem is well-known, and there is a patch being developed that will probably make it into Lucid-backports, or 10.04.1.

I wish I could give you a sure-fire fix for the problem in the meantime, but sadly, I don't know of one... if I did, then my own problems would be resolved, and I'd be a lot happier.

Apparently, though, running this command (to blacklist KMS) has worked for some:

```
echo options i915 modeset=0 > /etc/modprobe.d/i915-kms.conf

```

---

### Post by Johnzw on 2010-04-25
> **purgatori said:**
> This problem is well-known, and there is a patch being developed that will probably make it into Lucid-backports, or 10.04.1.

I wish I could give you a sure-fire fix for the problem in the meantime, but sadly, I don't know of one... if I did, then my own problems would be resolved, and I'd be a lot happier.

Apparently, though, running this command (to blacklist KMS) has worked for some:

```
echo options i915 modeset=0 > /etc/modprobe.d/i915-kms.conf

```
Will attempt that and post what happens.

---

### Post by Johnzw on 2010-04-26
That appears to have worked. Uptime is 1 day 1:38. The freezes had been happening no less than every five hours. I'll keep monitoring.

---

### Post by Johnzw on 2010-04-28
Well, that sorta worked. Got to the 2 day 4 hour mark then tried a switch user and it went to black and locked. Upon reboot it did the characteristic freeze within minutes.

---

### Post by purgatori on 2010-05-02
Yeah, upon some boots I'll get a good run that can go for days, but if I have to power cycle the system for some reason, then the crashing comes back... I hope someone comes up with a way to squash this enigmatic bug.

---

### Post by Johnzw on 2010-05-02
Well, now we're back to freezes every 3-4 hours n average. 

Anyone know if this is fixed in lucid?

---

### Post by henjj on 2010-05-02
I don't think it is fixed in Lucid.  I had the same problem using Karmic so I followed the thread on how to revert back to the Jaunty Xorg intel driver to 2.4 ([https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)).  It workd with my system when I had Karmic on it.  Then I upgraded to Lucid and the problem is back and now when I try to follow the instructions on [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4) , I get the following message:   

The following packages have unmet dependencies:
  xserver-xorg-video-intel-2.4: Depends: xserver-xorg-core (>= 2:1.5.99.901) but it is not going to be installed
E: Broken packages

I then try and install xserver-xorg-core and I get the message:

xserver-xorg-core is already the newest version.

I'm not sure what to try now.

---

### Post by purgatori on 2010-05-03
> **Johnzw said:**
> Well, now we're back to freezes every 3-4 hours n average. 

Anyone know if this is fixed in lucid?

Lucid is what I've been using, so no: it's not fixed :P

Here are some potential fixes for those using Lucid: [Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes).

If I can add another one to those suggestions, I recently added 'xforcevesa' after 'ro' in the kernel line of menu.lst, and I haven't had a crash since... but nor have I rebooted my machine since then, so it could be a matter of this just being one of the 'good' boots, and have nothing to do with using xforcevesa. I'll report back any changes. 

Ultimately though, I'm hoping they get a fix through the backports sooner rather than later.

---

### Post by the-rosbif on 2010-05-03
Had exactly the same problems as you guys with Ubuntu 9.10 and the same setup. I couldn't even get mine to start with the screen on after a while. I had no end of problems with the thing - FreeNAS wouldn't recognise the network card, I could never get webcams working properly. I just dont think the machine is capable of running ubuntu properly..

---

### Post by style23 on 2010-05-03
> **henjj said:**
> I don't think it is fixed in Lucid.  I had the same problem using Karmic so I followed the thread on how to revert back to the Jaunty Xorg intel driver to 2.4 ([https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)).  It workd with my system when I had Karmic on it.  Then I upgraded to Lucid and the problem is back and now when I try to follow the instructions on [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4) , I get the following message:   

The following packages have unmet dependencies:
  xserver-xorg-video-intel-2.4: Depends: xserver-xorg-core (>= 2:1.5.99.901) but it is not going to be installed
E: Broken packages

I then try and install xserver-xorg-core and I get the message:

xserver-xorg-core is already the newest version.

I'm not sure what to try now.

henjj - I'm going through the same problems and tried the same exact steps, the only way I was able to boot into Lucid was by removing the intel_drv.so driver - found in /usr/lib/xorg/modules/drivers. Now i'm left with the highest screen resolution of 1024x768 and I don't know what to do. If you find any other suggestions please post them here.

---

### Post by Johnzw on 2010-05-04
I just personally watched the system in question do this 4 times in ten minutes... my users are getting kind of pissed off. 

Later this week I'll try the X/Bugs/Lucidi8xxFreezes things and report back what happens. I desire to avoid switching to VESA as this box is very low on memory anyway so it needs all the help it can get, but I seem to recall that a long time ago (like several releases ago) there was some kind of annoying graphics problem that meant that only VESA could be used.

Apparrently Linux and Intel video cards don't play nice.

---

### Post by Rasa1111 on 2010-05-04
> **Johnzw said:**
> Well, now we're back to freezes every 3-4 hours n average. 

Anyone know if this is fixed in lucid?


hey, I have a dell dimension 2350 and Karmic did that to me to, 
not quite as often, but enough to be annoying, 
[i had to learn reisub to avoid manual 'power button' shutdowns]

however.. Lucid is on it now..
and it has not done that once!!  :KS

 it has actually 'restarted' on me a couple times on its own though. 

my CPU is 2.3 GHz and i have 1 GB ram, 
Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Control
ler/Host-Hub Interface 

other than that, Lucid is running soo good. 
and karmic ran really well, except for the occasional freeze up. lol
Lucid is running much better though.

 kind of amazing, really. :)

---

### Post by purgatori on 2010-05-04
On subsequent reboots, it became apparent that the 'xforcevesa' option did nothing to help. Unfortunately I can't use vesa as an alternative to the Intel xorg driver because despite numerous alterations made to the xorg.conf file, I cannot achieve a resolution > 640x480. At the moment, I'm looking at backing up all my work, and getting rid of Ubuntu/Linux altogether, and moving to Windows XP or something. This is not a step I ever would have dreamed of taking, as someone who loves Linux (esp. the command-line functionality, which I don't know how I'll do without), but I have work that I need to use my computer for, and at the moment, this problem is far too disruptive to my work-flow.

---

### Post by erfahren on 2010-05-09
> **purgatori said:**
> Lucid is what I've been using, so no: it's not fixed :P

Here are some potential fixes for those using Lucid: [Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes).

...

I did a clean install of Lucid on my Dell 2400 (with the Intel 82845G/GL/GE Chipset)and it froze with a screen full of errors on the first restart.

I tried the "Workaround A: Re-enable KMS" on that Wiki page and it booted up ok but X crashed on me when I went to rename a file in Nautilus - so I'm going to try the "Workaround F: Use UXA Rendering" there as well.

I do have one question for anyone who understands all this better then me: - Would I need to apply that "Workaround A: Re-enable KMS" fix with every new kernel update? the guide doesn't mention that one way or another

I'll also update on this thread after I do the Workaround F 

- thanks

EDIT: tried some things to no avail - decided to revert back to 8.04 for time being - darnit anyway!

---

### Post by lathanial on 2010-05-11
I'm having similar problem with my Dell Dimension 2400 with Intel 82845G/GL/GE Chipset.After upgrading to Lucid Lynx I started getting very frequent crashes - black screen with a row of vertical white stripes flashing on top half of screen. I could reboot with alt+Sysreg+REISUB. I tried blacklisting KMS:

echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf

That helped out enough to make my system usable. Now I get occasional crashes(once or twice a day) with a completely black screen and have to do a hard reset. 

Misery loves company but not much help other than that.

lathanial

---

### Post by aust77 on 2010-05-24
In Lucid, I have finally found a working combo of fixes provided on the "Lucidi8xxFreezes" wiki page. They stop crashing on the following hardware:
```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

```

The fixes "A" (Enabling KMS) and "E" (Disable DRI) have stopped the crashes.

The wiki is unclear about fix A in the sense that you must modify the GRUB settings for fix A to work. If you simply execute the code given in a terminal, chances are you will be unable to boot into your OS. You have to add "i1915.modeset=1" to your GRUB settings (the instructions for this are found *below* the two fix A terminal commands, for no apparent good reason). Before you attempt this fix, ensure you have a non-USB keyboard, as editing the GRUB settings is impossible with a USB keyboard.

Hope I am clear enough.

aust77

---

### Post by Rasa1111 on 2010-05-25
> **aust77 said:**
> In Lucid, I have finally found a working combo of fixes provided on the "Lucidi8xxFreezes" wiki page. They stop crashing on the following hardware:
```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

```The fixes "A" (Enabling KMS) and "E" (Disable DRI) have stopped the crashes.

The wiki is unclear about fix A in the sense that you must modify the GRUB settings for fix A to work. If you simply execute the code given in a terminal, chances are you will be unable to boot into your OS. You have to add "i1915.modeset=1" to your GRUB settings (the instructions for this are found *below* the two fix A terminal commands, for no apparent good reason). Before you attempt this fix, ensure you have a non-USB keyboard, as editing the GRUB settings is impossible with a USB keyboard.

Hope I am clear enough.

aust77

  Hi aust77~
Thank you!

Would you be able to elaborate a bit on how to fix this?
It is happening more often than my nerves can handle lately.. ..
and Im really not sure what to do with the instructions here~[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

? 

 thanks man.

---

### Post by corcoram on 2010-05-25
I also have a Dimension 2400 with the Intel 82845G/GL/GE Chipset.  I had the same problem with Fedora, switched to Ubuntu 10.04 and the problem continued.  Turning off the screensaver made things better, but the display would continue to go away at the most inopportune times.  I finally broke down and purchased a geforce 9400gt (sparkle brand) and haven't had any problems since.

Warning: Look at the below post for details on getting the nvidia to work.  My guess is an ATI video card may provide for an easier setup, but I can't guarantee anything.

[http://ubuntuforums.org/search.php?searchid=73322793](http://ubuntuforums.org/search.php?searchid=73322793)

---

### Post by Rasa1111 on 2010-05-25
> **corcoram said:**
> I also have a Dimension 2400 with the Intel 82845G/GL/GE Chipset.  I had the same problem with Fedora, switched to Ubuntu 10.04 and the problem continued.  Turning off the screensaver made things better, but the display would continue to go away at the most inopportune times.  I finally broke down and purchased a geforce 9400gt (sparkle brand) and haven't had any problems since.

Warning: Look at the below post for details on getting the nvidia to work.  My guess is an ATI video card may provide for an easier setup, but I can't guarantee anything.

[http://ubuntuforums.org/search.php?searchid=73322793](http://ubuntuforums.org/search.php?searchid=73322793)

 good to know mate, thanks. 

So, If I buy this~ 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814187058](http://www.newegg.com/Product/Product.aspx?Item=N82E16814187058)
and put it into my Dell Dimension 2350, 
This problem will [or should] stop?

---

### Post by fishwebby on 2010-05-28
Hello,

after having the same problem and coming across this thread, I'm glad to see it's not just me!

I tried A + E as described above but it still likes to crash every so often (and Alt + SysReq + reisub doesn't work either) - I hope they come up with a fix for it soon. My problem is I can't work like this, and I can't do what I'm doing in Windows either (Rails development - couldn't get gems to work nicely in Windows). So my question is what is the last version of Ubuntu that worked nicely with the Intel graphics card? And can I reinstall that, even though more recent versions have a newer version of grub (my /home partition is separate)? I don't want to have to reinstall everything if I can avoid it, just the / partition.

Many thanks
Dave

---

### Post by Rasa1111 on 2010-05-28
hi Dave, 
Im not sure man, sorry. 

but, Ubuntu has recently "fixed itself" at my house..
im not quite sure how it happened...
but this is the 4th day I think..
and it hasnt happened once~ "The Crash". lol

thread here~
[http://ubuntuforums.org/showthread.php?t=1494141](http://ubuntuforums.org/showthread.php?t=1494141)

 Im wondering, anyone else whose PC was doing what i described in linked thread...
 has it stopped doing that for you also?
:confused:

it fixed itself that way~ but today my USB stopped opening my external drives. not sure whats up with that. lol

---

### Post by fishwebby on 2010-05-28
Hi Rasa,

great, lucky you! I've found that too - sometimes things just fix themselves (good Gremlins perhaps?). :-)

Alas the crashes on mine were getting more frequent, so I went ahead and went back to 9.04. So far no problems, apart from having to check out all my subversion repositories again as it seems there was a version clash. I'll upgrade to 10.04 if I ever read that the bug has been sorted!

Cheers
Dave

---

### Post by aust77 on 2010-05-28
> **Rasa1111 said:**
> Hi aust77~
Thank you!

Would you be able to elaborate a bit on how to fix this?
It is happening more often than my nerves can handle lately.. ..
and Im really not sure what to do with the instructions here~[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

? 

 thanks man.

Here are the instructions from the wiki page in the order they should be (thus meaning all credit goes to the wiki editors):

(Method A Instructions in Order)
**From an installation:**

 1) Hold down Shift while booting  to enter the GRUB menu. 
2) Press 'e'  to edit. 
3) Add "i915.modeset=1" after  "quiet splash". 
4) Ctrl+x to  boot. 
If adding "i915.modeset=1" to  your boot parameters allows you to boot successfully, you then need to  enter the command below into a terminal to make the changes permanent. 

-OR-

**From the LiveCD:**

 1) At the purple screen with a  keyboard and stickfigure, press Enter to get to the menu. 
2) Hit Enter to select your language, and then press F6  and then Esc. 
3) Add  "i915.modeset=1" after "quiet splash". 
4) Press  Enter to boot the LiveCD. 

-AFTER HAVING DONE ONE OF THE ABOVE, PASTE THE FOLLOWING IN A TERMINAL-

```
echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
sudo update-initramfs -u
```


Method "E" seems to be clear enough, so I'd just read the wiki page.

As I said before, USB keyboards do not function in the GRUB menu. I was using one but ended up having to switch to a "direct" keyboard (i.e. a keyboard plugged in to the special keyboard slot on the back of a PC) as it is the only type that works in the GRUB menu.

The reason I re-arranged the instructions is because when I pasted the two lines of code in the terminal (one by one, of course) my computer would not boot into Ubuntu. I later figured out I had to edit my kernel boot parameters BEFORE pasting the two lines of code into the terminal.

Crashing has virtually stopped for me except for the fact that my monitor is running at 85 Hz instead of what it should be running at; 75 Hz. This is why: [http://ubuntuforums.org/showthread.php?p=9370317#post9370317](http://ubuntuforums.org/showthread.php?p=9370317#post9370317)

Apologies for the late response, and I hope I have assisted you.



aust77

---

### Post by jhansonxi on 2010-06-02
I solved my 845 lock-up problems in 10.04 (Lucid Lynx) by adding the [X Retro repository]("https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-retro") and updating (effectively a downgrade) the xserver-xorg-video-intel driver.  I also added the "nomodesetting" to the GRUB_CMDLINE_LINUX_DEFAUT line in /etc/default/grub (and then running update-grub).  I'm not sure if the grub change affects the X problem but it solved VT corruption I was experiencing.  This didn't fix every crash but greatly reduced them.  I can play Chromium, Trigger, and Supertux but gCompris stalled and then X started hogging CPU until it crashed back to to the flashing black screen.

---

### Post by InTheSand on 2010-07-15
> **aust77 said:**
> Here are the instructions from the wiki page in the order they should be (thus meaning all credit goes to the wiki editors):
...

Crashing has virtually stopped for me except for the fact that my monitor is running at 85 Hz instead of what it should be running at; 75 Hz. This is why: [http://ubuntuforums.org/showthread.php?p=9370317#post9370317](http://ubuntuforums.org/showthread.php?p=9370317#post9370317)

Apologies for the late response, and I hope I have assisted you.

aust77

Just like to say a big THANKS to you on this! Have recently been given a Compaq Presario (2.6 Celery, WinXP, 512Mb, sloooooow) and decided to blow that away and install Lucid on it (as I run this on more modern machines and my netbook) - thanks to your clear steps above, the crashing has stopped and it's now a decent machine to give to the relatives!

---

### Post by erfahren on 2010-07-25
my update:

I went and found an older NVIDIA GeForce4 128MB PCI video card on eBay and just reinstalled Lucid (I had reverted back to 8.04 anyway) and then just installed the proprietary Nvidia driver through the "Hardware Drivers" app off the menu.

paid about $15(US) for the card (including shipping) and it seems to be running well & suspend works with no issues. :)

---

### Post by emackey3k on 2010-08-15
I have a Dell Dimension 2400 and have had this problem with a clean install.  I tried all the fixes in this thread and none seemed to work for me.  

I haven't had the problem with kernal 2.6.32-23.  Unfortunately I do have the problem with kernal 2.6.32-24.  So for now I am booting with kernal 2.6.32-23.

---

### Post by MyR on 2010-08-15
I gave up & installed debian.  it works.

---

### Post by Quezzy on 2010-09-12
Going to try a video card if I can find one tomorrow.

---

### Post by Rasa1111 on 2010-09-13
Ubuntu 10.10 doesnt have this problem. 
My lucid install stopped doing it eventually, 
but 10.10 has no graphics card problems at all for me.
[dell dimension 2350]
Everything works perfectly. 
Ill keep my lucid install for awhile,
but i think im going to switch fully to 10.10 in a couple months.. :D

---

### Post by lathanial on 2010-09-23
Possible fix - disable OpenOffice QuickStarter.

After putting up with this problem for a long time and learning to save and save often, my system has not crashed in over two weeks. I disabled Quick Starter because it was causing the gui shutdown (icon in the panel) to not work as well as making the update notifications window unresponsive. Since doing this I haven't crashed in over two weeks - down from 3+ crashes in a 8 hour day.

I don't have another 82845 machine to try this out on but I would like to here from anyone else who is still trying to use Lucid with the 845 chipset.

lathanial

---

### Post by lathanial on 2010-09-23
Possible fix - disable OpenOffice QuickStarter

I haven't crashed in over two weeks - down from 3+ in 8 hour day. I disabled QuickStarter because of other problems and haven't crashed since.

Is there anyone still dealing with this that could try to verify? I only have the one 845 chipset machine.

Let me know
lathanial

---

### Post by MLX on 2010-09-23
We have a Dell Dimension 2400 and have this issue. I am sorry to say that Open Office Quick starter is not enabled and we still have crashes. 
I have made a boot CD for Ubuntu 10.10 beta and ran from the CD. I did not see the problem but really need to let the system run longer to be sure. 
I would be very happy if 10.04 was fixed because I like to run the LTS versions.

---

### Post by Rasa1111 on 2010-09-23
> **MLX said:**
> We have a Dell Dimension 2400 and have this issue. I am sorry to say that Open Office Quick starter is not enabled and we still have crashes. 
I have made a boot CD for Ubuntu 10.10 beta and ran from the CD. I did not see the problem but really need to let the system run longer to be sure. 
I would be very happy if 10.04 was fixed because I like to run the LTS versions.

I would also be quite happy if 10.04 worked as it should. 

Even though my PC no longer freezes/crashes in 10.04..
the graphics problem still persists. 

 I still cannot use stellarium in 10.04,
and if i attempt to.. the PC *will* crash.
blacking out, white lines, etc. 

 Rather weak, as it is an LTS, which Id much rather use than an RC, but if i have to switch to 10.10 just so everything works properly, i will. 

wish I could use 10.04 though.
everything works, except the couple of things i use often. 
But that doesnt cut it i guess...

 though 10.10 does seem rather 'flawless'...

---

### Post by Creap on 2010-10-08
Is it confirmed that this bug is resolved in 10.10? I'm about to fix my sister's computer with this problem, but if it will be fixed in the 10.10 release in 2 days I'll wait before trying everything in the [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by MyR on 2010-11-06
Is this bug fixed in 10.10? Anyone?

---

### Post by bishopbutu on 2010-11-06
Hi, new to Ubuntu, and I have this video card and the same problems discussed here.

Have followed this thread, some things to add. Ubuntu 9.10, Ubuntu 10.10, Mint 8, Mint 9 have all given me problems I think because of incompatibilities with this Brookline card. 

Ubuntu 9.10, which I am running now on this Pentium IV with just under a gig of RAM, gives the least problem of the bunch. But it has problems too...

Three benchmarks have given clues to this problem for me: "the ant" (GL 3d bug screensaver), the playing of high def videos full screen, and random seemingly unexplainable lockups.

The main differences?

1.* 9.10 will let me not only see the GL ant screensaver, but also run it*. All of the others require a hard boot to break out of the lockup this causes, even sometimes just previewing.

2. *NONE OF THEM will consistently play hi def videos full screen without choppiness or lockups*. I have tried with MPlayer, Movie Player, Dragonplayer, KMPlayer, SMPlayer, and VLC player in some combination on these systems. The closest I can get to doing this successfully is using 9.10 and VLC, but then VLC does strange things also when transitioning between videos and exiting full screen. A couple of lesser players crashed the system first run. The only time the others succeed full screen is with low quality videos played singly.

3. *ALL OF THEM LOCK UP "RANDOMLY"*. I know they are not random.

Here are some more things. The lockups usually always occur when graphic-intensive and memory-hungry Firefox is running. I am thinking this is just enough at times to rob the system of what it needs to keep the desktop live.

When I ran the WinGates on this machine I had the same or better graphic and video quality at lower resolution. Meaning the screen I am seeing now at 1440x900 is not much sharper or different sizewise than when I was running 1024x768 with W...if that makes any sense.

I think the card is not made for the resolutions Linux is ascribing to it, no matter the driver, the metal and plastic just won't do. But I submit this to further the discussion, I really want to keep this system and put it on all my machines, and right now, stay up without having to reboot constantly.

So, I think 9.10 was closest to getting it right.

Oh, one more tidbit? In my CMOS I notice that this card is listed as a PCI card, when in fact is it an Onboard? I notice my .conf file is blank, and when I lspci I get no mention of any port...

:confused:

---

### Post by MyR on 2010-11-06
Well I've been running Debian and to my knowledge it has never crashed in the way that ubuntu crashes... So the problem does not lie with Linux in general, but probably something related to Ubuntu or the apps it comes with.

---

### Post by candtalan on 2010-11-21
Ubuntu 10.04.1 LTS fully updated.

Looks like the same problem I think, only with a Compaq Evo desktop 500MB ram, P4 2GHz

Reported random freeze, or more likely a weired graphic display - vertical black and white lines across the display in the upper third of the display.

When working, lspci gives
VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

There are two apparently identical machines, with same problem, I have worked on only one here.

I used stellarium app game to test the problem, it installed ok but I could never run it because of the problem. This was a very useful test, and I am very grateful for it being mentioned in at least one thread here.

I used 
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
I tried Workaround A first then B. Neither worked and after B, I got no graphic display at all so I used a live CD to re instate the xorg.conf-original which I had carefully created before  doing 'B'.

The next workaround which looked worth trying was workaround E.
=================
Workaround E: Disable DRI
Paste the following into /etc/X11/xorg.conf:

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
        Option          "DRI" "off"
EndSection
=================

I restarted the machine and it worked  - stellarium worked!

So it looks to me like the problem on this machine (I hope) is solved for the present time.

---

### Post by MyR on 2010-11-21
The problem is fixed in 10.10.

I've been using xubuntu on the 2400.  Works great!

---

### Post by candtalan on 2010-11-22
> **MyR said:**
> The problem is fixed in 10.10.
I've been using xubuntu on the 2400.  Works great!

Good to know, thanks. 

Any idea if 10.04 LTS will get further attention with this? 

Being LTS I have a number of people soon to be upgraded to it, and if you get caught, it is a significant problem. And bad publicity too - I have a relative trying 10.04 and his machine is affected. He runs a school IT facility and is very put off by this unfortunate problem, even though I have now belatedly found the fix (as my earlier post) for his same machine.

---

### Post by candtalan on 2010-11-22
> **candtalan said:**
> Good to know, thanks. 

Any idea if 10.04 LTS will get further attention with this? 

Being LTS I have a number of people soon to be upgraded to it, and if you get caught, it is a significant problem. And bad publicity too - I have a relative trying 10.04 and his machine is affected. He runs a school IT facility and is very put off by this unfortunate problem, even though I have now belatedly found the fix (as my earlier post) for his same machine.

Err - I perhaps spoke too soon.
I have been using the machine for the afternoon and evening, with mostly firefox web use this evening. On a particular Register site
[http://www.theregister.co.uk/2010/11/19/shell_centre_eels/](http://www.theregister.co.uk/2010/11/19/shell_centre_eels/)
the machine crashed out! I restarted, and same again, after a short time. I did again go back and did get to actually read the site but I am un nerved by such crashes. I need to hand this to an elderly non tech user.

I am wondering if I should upgrade  to Ubuntu 10.10 now??
any thoughts please

tia

---

### Post by MyR on 2010-11-22
> **candtalan said:**
> I am wondering if I should upgrade  to Ubuntu 10.10 now??
any thoughts please

tia

As you may already know, LTS releases are not necessarily more stable than regular releases.  This means that the length of support is the only difference between LTS and regular releases.  In my experience 10.10 has been more stable than 10.04, so I would recommend it.

Ubuntu 10.10 is supported until April 2012 as compared to April 2013 for 10.04 (desktop edition).

hth

---

### Post by candtalan on 2010-11-22
thanks,
I think I will upgrade

---

### Post by abpriest on 2011-02-18
Wow. I stopped checking this thread after going to opensuse 11.2 thinking it would solve my problem--it didn't and (sad to say) the opensuse community couldn't help me. I have learned that the ubuntu community has kept the issue alive. I am going to install ubuntu 10.10 today and I'll let you know how it works.

---

### Post by abpriest on 2011-02-27
SOLVED! Ubuntu 10.10 works great with my old Dimension 2400! Let it run for nearly a week (started it an restarted it, too) not one problem.

---

