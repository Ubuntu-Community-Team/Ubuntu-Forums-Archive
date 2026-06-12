---
title: "System freezes at random for no apparent reason..."
date: 2010-09-11
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by exploder on 2010-09-11
I have a fresh install of Maverick fully updated and the system will freeze at random for no apparent reason. I am using the open source nvidea drivers, nvidea GT 220, ati mainboard with onboard everything. Pretty common hardware.

The system logs are not showing a thing.... The mouse will still move when this happens but the system is completely unresponsive. Is anyone else having this problem? Is there a bug report I can add to?

---

### Post by JimBuntu on 2010-09-11
I had this problem with an older version of Ubuntu. I have a custom built computer. It's an AMD 64 with nvidia 8600gt Abit an9 board and 2 gigs of ram. I installed Ubuntu 64bit and it would crash randomly. Sometimes within 20 min. and sometimes it took a few hours. I could never find the cause but once i installed the 32 bit version it never crashed. However, I have since got the latest bios chip for my mobo and now have 64 bit Ubu running with no problems at all. I don't know what the original problem was, but think it may have had something to do with the bios?? I'm not sure. I would try a new download of Ubuntu and reinstalling it. If that don't work, try 32 bit and see if it still crashes. It may be that your hardware is not working well with Ubu 64 bit. I just realized you never said you were using 64 bit... Oh well. That's my best guess.

---

### Post by mc4man on 2010-09-11
> The system logs are not showing a thing...
After one of these freezes  grep for syslog for a few of these words, if found then open the syslog and search to put in context

```
cat  /var/log/syslog |grep Dazed
```
 ```
cat  /var/log/syslog |grep Uhhuh
```

---

### Post by Slug71 on 2010-09-11
I get similar random freezes except i cant move the mouse. 

Im thinking its hardware related but not sure.
Have 512mb ram, Athlon XP1800+, Soltek board and nVidia AGP 6600 256mb.

I get it on Lucid every now and again too but far more common on Maverick.

---

### Post by Longinus00 on 2010-09-11
> **mc4man said:**
> After one of these freezes  grep for syslog for a few of these words, if found then open the syslog and search to put in context

```
cat  /var/log/syslog |grep Dazed
```
 ```
cat  /var/log/syslog |grep Uhhuh
```

You don't need to pipe a file's contents to grep, grep can take a file as an argument.

```
grep PATTERN /path/to/file
```

---

### Post by VMC on 2010-09-11
> **Longinus00 said:**
> You don't need to pipe a file's contents to grep, grep can take a file as an argument.

```
grep PATTERN /path/to/file
```
I think he meant some sarcasm there.

---

### Post by exploder on 2010-09-11
I have had this freezing problem in 32 and 64 bit, currently I am running 32 bit. Also, this happens on two computers, the only thing they have in common is NVidea graphics.

I have tested the RAM on both computers, tried proprietary graphics drivers and the open source drivers. The RAM on both machines tests good and graphics drivers do not seem to have anything to do with the problem.

The system logs on both computers contain no clue to what the problem is and there is no specific task that I am aware of triggering this problem.

At the moment it would not do much good to file a bug report because I do not have any real information to provide. Sometimes the computer will work fine all day and sometimes it won't. Both systems are duel core AMD processors and both have lots of RAM installed. I am stumped on this one....

---

### Post by Slug71 on 2010-09-11
> **exploder said:**
> I have had this freezing problem in 32 and 64 bit, currently I am running 32 bit. Also, this happens on two computers, the only thing they have in common is NVidea graphics.

I have tested the RAM on both computers, tried proprietary graphics drivers and the open source drivers. The RAM on both machines tests good and graphics drivers do not seem to have anything to do with the problem.

The system logs on both computers contain no clue to what the problem is and there is no specific task that I am aware of triggering this problem.

At the moment it would not do much good to file a bug report because I do not have any real information to provide. Sometimes the computer will work fine all day and sometimes it won't. Both systems are duel core AMD processors and both have lots of RAM installed. I am stumped on this one....

Yeh thats why i havent filed a bug.

Seems like an nVidia or Kernel issue judging by the posts.

---

### Post by exploder on 2010-09-11
Thanks Slug71! I was beginning to think I was the only one with this problem. I also wonder about the kernel, seems like the problem started showing up again after the last kernel update. Other than the occasional lock ups Maverick looks and runs great.

---

### Post by Slug71 on 2010-09-11
> **exploder said:**
> Thanks Slug71! I was beginning to think I was the only one with this problem. I also wonder about the kernel, seems like the problem started showing up again after the last kernel update. Other than the occasional lock ups Maverick looks and runs great.

Im glad to see others are experiencing this too. Not sure how to track it though.
But yeh other than that it does run great.

Anyone have any suggestions as to how to track this sucker?

---

### Post by mc4man on 2010-09-11
> I think he meant some sarcasm there. I thought it was an informative post, if so (sarcasm), it was wasted on me.
Actually use both ways - saw a grep command in my history and used that.
Overall not too concerned here about the path taken if the result is what was desired. (barring unintended consequences, none here that I see.

edit: something else that may show in syslog just prior to freeze
 NVRM: [COLOR="Red"]os_pci_init_handle[/COLOR]: invalid context!

search, grep, whatever, for red

---

### Post by exploder on 2010-09-11
I would like to add to the bug report if someone has a link to it.

---

### Post by cariboo on 2010-09-11
Those of you having lockup/freezing problems may want to have a look at [this]("https://wiki.ubuntu.com/X/Troubleshooting/Freeze") wiki page, it may help diagnose the problem.

---

### Post by VMC on 2010-09-11
I'd be curious for those that have freeze problems, what x driver are you using. I have installed nvidia 256.33 and no issues. Also, just installed todays iso with default x driver and no lockups.

I was having problems with jockey installs, but that wasn't a lockup it was GDM in contention with nvidia.

---

### Post by 23meg on 2010-09-11
> **cariboo907 said:**
> Those of you having lockup/freezing problems may want to have a look at [this]("https://wiki.ubuntu.com/X/Troubleshooting/Freeze") wiki page, it may help diagnose the problem.

And [this]("https://help.ubuntu.com/community/DebuggingSystemCrash") one.

---

### Post by exploder on 2010-09-11
I ran memtest on both effected computers. The system I am on today is using the open source drivers, the other system is using the 256.33 drivers. There is absolutely nothing in the system logs that indicates where the problem might be. I submitted a bug report.

[https://bugs.launchpad.net/ubuntu/+bug/636094](https://bugs.launchpad.net/ubuntu/+bug/636094)

Possibly the developers can provide some insight on this.

---

### Post by 23meg on 2010-09-11
> **exploder said:**
>  I submitted a bug report.

[https://bugs.launchpad.net/ubuntu/+bug/636094](https://bugs.launchpad.net/ubuntu/+bug/636094)

Possibly the developers can provide some insight on this.

You've filed it without a package, and there's no debugging information, so the chances of that happening are very slim.

If the mouse pointer is moving, that's not a system freeze; the kernel and possibly xorg are probably partially alive and you can get a stack trace dump, or ssh into the machine for further debugging. Read the community doc page I linked to above for instructions, and see if helps you obtain some information.

---

### Post by Slug71 on 2010-09-11
> **cariboo907 said:**
> Those of you having lockup/freezing problems may want to have a look at [this]("https://wiki.ubuntu.com/X/Troubleshooting/Freeze") wiki page, it may help diagnose the problem.

> **23meg said:**
> And [this]("https://help.ubuntu.com/community/DebuggingSystemCrash") one.

Thanks for the links. Will go through tomorrow but it seems they have plenty of info!

P.S. Using the open source drivers here.

---

### Post by exploder on 2010-09-11
One of the links mentioned the BIOS. I looked all through my settings and found a couple of setting were not right. I made some changes and will wait and see if that was the problem.

---

### Post by ktp on 2010-09-11
> **23meg said:**
> If the mouse pointer is moving, that's not a system freeze; the kernel and possibly xorg are probably partially alive and you can get a stack trace dump, or ssh into the machine for further debugging. Read the community doc page I linked to above for instructions, and see if helps you obtain some information.

I had similar issue during 9.04 days and that is why I have sshd installed.  ssh had shown it was gdm hanging so I would, if your system is still some what response, ssh into it and dig around.

---

### Post by Cenotaph on 2010-09-11
my maverick freezes everytime i boot after a long time shutdown, the last time even before the panels appeared on the desktop. but after i reboot (which i have to, because nothing works) it never freezes. Its pretty awkward.

---

### Post by VMC on 2010-09-11
Freeze means to me that no input/ouput is happening. If Ctrl+Alt+F? brings a VT then it isn't frozen ,just not responding. X may have stopped. If I can get a response with Alt+SysRq+b then at least I know the keyboard is responding.

I wonder if those having "freeze" problems are unrelated, or having separate issues. 

I was wondering if I just haven't left Maverick running long enough or not putting enough strain on the system to freeze. I now have several programs running, including Rhythmbox(a usual suspect.) I have no indication what so ever. Everything is running smoothly.

I believe the ssh idea is the best idea if your system is really frozen.

---

### Post by Ancanus on 2010-09-12
I have a similar issue. Mouse works, but clicking does nothing. My keyboard is fully functional though. I am able to pop up a terminal, sudo pkill gdm, and when my X comes back the mouse is working again.

---

### Post by exploder on 2010-09-12
I seem to have the problem fixed on one of my machines. I changed a couple of settings that were wrong in the BIOS and so far no problems today.

---

### Post by 23meg on 2010-09-12
> **exploder said:**
> I seem to have the problem fixed on one of my machines. I changed a couple of settings that were wrong in the BIOS and so far no problems today.

It might help others isolate the issue on their end if you mention what those settings are.

---

### Post by exploder on 2010-09-12
> It might help others isolate the issue on their end if you mention what those settings are.

I disabled every feature relating to floppy drives. There is no floppy drive on this machine. The settings for the system time were off by a mile, not sure how this happened but I corrected it. I turned off some odd power management feature that was enabled.

The computer has been on for 14 and a half hours with no problems so far. exploder keeps fingers crossed. :D

Edit: If you are having problems it is worth the time to look at all of the setting in the BIOS.

---

### Post by Jonners59 on 2010-09-13
> **Slug71 said:**
> 
Quote:
Originally Posted by **cariboo907** [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9834691#post9834691") 
*Those of you having lockup/freezing problems may want to have a look at [[COLOR=#000000]this[/COLOR]]("https://wiki.ubuntu.com/X/Troubleshooting/Freeze") wiki page, it may help diagnose the problem.*

Quote:
Originally Posted by **23meg** [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9834718#post9834718") 
*And [[COLOR=#000000]this[/COLOR]]("https://help.ubuntu.com/community/DebuggingSystemCrash") one.*

I have the same problem on one of my PCs.  It is a home build with nVIDIA and AMD 64.  I am running 10.4   It freezes, I have no mouse or keyboard and have to do a hard restart.  Yesterday I was in Skype and during this call I had to reboot 3 times before we gave up.  Interestingly, the sound played the last few fractions of a second over and over.
 
I am not at home on the machine to give more system info or run tests but I was interested to read the threads below and how many have nVidia cards.
 
I will try these links when I get in.

---

### Post by scottmuz on 2010-09-13
The solution is really simple, stick to a 32 bit kernel.

I had lots of issues with AMD64 and nVidia across several Ubuntu versions.

Finally I gave up and installed Lucid 32 bit.

Things just work so much better on 32 bit. Obviously for some
workloads 64 bit is needed but for desktop computing just save yourself
a lot lot of bother and stick to 32 bit.

---

### Post by Claus7 on 2010-09-13
Hello,

I think that this should become a sticky (or something similar), since there are many users facing that problem. It is really sad that is happening also on maverick. Hope it can become trivial soon.

Regards!

---

### Post by Cenotaph on 2010-09-13
as strange as it may seem i have determined that my maverick only freezes if the last OS i used was Windows. Im dual booting this test computer with Windows 7 64-bit and Maverick 64-bit, and whenever i go to windows the next time i boot maverick it ALWAYS freezes not long after booting X. there's nothing in the syslog and i really can't do anything with the mouse or keyboard.

Does this make sense?

---

### Post by arpanaut on 2010-09-13
> Does this make sense?

NO, but come to think of it, last week I booted windows to do some updates & maintance and when I came back to Ubuntu, I had freeze-ups in both lucid and maverick. I haven't since. 

Strange???

---

### Post by Slug71 on 2010-09-13
> **scottmuz said:**
> The solution is really simple, stick to a 32 bit kernel.

I had lots of issues with AMD64 and nVidia across several Ubuntu versions.

Finally I gave up and installed Lucid 32 bit.

Things just work so much better on 32 bit. Obviously for some
workloads 64 bit is needed but for desktop computing just save yourself
a lot lot of bother and stick to 32 bit.

I'm using 32bit.

> **Cenotaph said:**
> as strange as it may seem i have determined that my maverick only freezes if the last OS i used was Windows. Im dual booting this test computer with Windows 7 64-bit and Maverick 64-bit, and whenever i go to windows the next time i boot maverick it ALWAYS freezes not long after booting X. there's nothing in the syslog and i really can't do anything with the mouse or keyboard.

Does this make sense?

I use Ubuntu exclusively.

---

### Post by Slug71 on 2010-09-13
Anyway, i made some changes to the BIOS and will see how it goes. I probably should have made less changes though.
My card is 256mb and it was set to 64mb. Changed that to 256mb.
Disabled ACPI and made a couple other changes. Will edit this post on my next reboot to say what else i did.

---

### Post by ranch hand on 2010-09-13
The freeze up after using MS may make some sense.

I know that before I installed 8.04 I was using the LiveCD and then installed on another drive.  In both cases I was trying to get dialup working on Ubuntu.

When configuring the modem I was, of course, changing things in the cards memory.

When I would boot to MS it would always recognise the card as new hardware and configure it.

This may be happening with one or more of your cards when switching from MS to Ubuntu.

Then again this is just speculation on my part.

---

### Post by Slug71 on 2010-09-13
Well still no freeze here. Heading out shortly and will leave the computer on and see if anything happens while i was away.

The only thing that i changed which might be a bug(?) would be the ACPI thing.
Would that be a bug?(If it was that)

---

### Post by Slug71 on 2010-09-13
> **Slug71 said:**
> Anyway, i made some changes to the BIOS and will see how it goes. I probably should have made less changes though.
My card is 256mb and it was set to 64mb. Changed that to 256mb.
Disabled ACPI and made a couple other changes. Will edit this post on my next reboot to say what else i did.

Just rebooted to check what i changed earlier.

Changed the graphics ram from 64mb to 256mb.
Disabled ACPI
Changed DRAM Clock from 'by spd' to 133Mhz.(FSB and DRAM frequency is 133Mhz.)
Enabled 'System BIOS cacheable'
Enabled 'Video RAM cacheable.'

If i dont get a Freeze today with these changes i'll start reverting one by one until the freeze happens again. But as earlier stated, the only thing that would and might actually be a bug is the ACPI setting.

---

### Post by Ancanus on 2010-09-13
Is it really plausible that some BIOS settings are causing Maverick's X to freeze but not Lucid's?

---

### Post by ranch hand on 2010-09-13
Yes, 10.04 is a stable release. 10.10 is not.  The interaction between the OS an the hardware is different.

Beyond that we have a completely different x version than 10.04.

---

### Post by 23meg on 2010-09-13
> **ranch hand said:**
> Yes, 10.04 is a stable release. 10.10 is not.  The interaction between the OS an the hardware is different.

While you can expect a BIOS setting that caused a crash in one release not to cause one in another (if that's actually the case here), the best explanation at this point is not the inherent difference between stable releases and development snapshots. Maverick is pretty close to a stable release in terms of the number and significance of moving parts it has at the moment (past Feature Freeze and approaching Final Freeze).

---

### Post by 23meg on 2010-09-13
> **exploder said:**
>  I turned off some odd power management feature that was enabled.

Again, which specific settings? It might not be reasonable to expect them to be disabled; that you aren't having the crash doesn't mean the underlying problem isn't there. 

If you want to venture beyond troubleshooting and into testing, it would be helpful to cite more specifics and try to enable/disable things one at a time so that you can pinpoint the source of the problem.

---

### Post by Jonners59 on 2010-09-13
> **scottmuz said:**
> The solution is really simple, stick to a 32 bit kernel.

I had lots of issues with AMD64 and nVidia across several Ubuntu versions.

Finally I gave up and installed Lucid 32 bit.

Things just work so much better on 32 bit. Obviously for some
workloads 64 bit is needed but for desktop computing just save yourself
a lot lot of bother and stick to 32 bit.

Mine is 32, so that's not the answer

---

### Post by Slug71 on 2010-09-13
> **Ancanus said:**
> Is it really plausible that some BIOS settings are causing Maverick's X to freeze but not Lucid's?

I was getting freezes on Lucid too but not nearly as often as on Maverick.

Still no freeze so far.

---

### Post by exploder on 2010-09-13
> Again, which specific settings? It might not be reasonable to expect them to be disabled; that you aren't having the crash doesn't mean the underlying problem isn't there.

If you want to venture beyond troubleshooting and into testing, it would be helpful to cite more specifics and try to enable/disable things one at a time so that you can pinpoint the source of the problem.

The settings were simply the normal BIOS settings I thought were in place. It is likely my youngest son (a toddler) messed with the computer when I was at work. Also, BIOS setting vary by board manufacturer, if someone is looking for specifics, it is best to check the manual for their specific board. There is a huge difference in settings between my Biostar and Foxconn boards for example.

---

### Post by nanog on 2010-09-13
this is still a bug. if the kernel or x fail with particular bios settings it should be reported.

---

### Post by exploder on 2010-09-13
> this is still a bug. if the kernel or x fail with particular bios settings it should be reported.

Not necessarily, the idea to check the BIOS came strait from official Ubuntu documentation.

---

### Post by Slug71 on 2010-09-15
Well i had a freeze on both Maverick and Lucid. 
I re-enabled ACPI and enabled PNP O/S.

---

### Post by crjackson on 2010-09-15
> **ranch hand said:**
> The freeze up after using MS may make some sense.

I know that before I installed 8.04 I was using the LiveCD and then installed on another drive.  In both cases I was trying to get dialup working on Ubuntu.

When configuring the modem I was, of course, changing things in the cards memory.

When I would boot to MS it would always recognise the card as new hardware and configure it.

This may be happening with one or more of your cards when switching from MS to Ubuntu.

Then again this is just speculation on my part.

I have had similar experiences with wireless cards and webcams, except that I could boot into windows and activate either of them and it seems to reset the device in question.  then it WILL work in Ubuntu where it previously wouldn't.

---

### Post by Slug71 on 2010-09-16
> **Slug71 said:**
> Well i had a freeze on both Maverick and Lucid. 
I re-enabled ACPI and enabled PNP O/S.

PNP O/S did not work either. 
Dont really see any other settings that it could be.

Will read through those docs again and keep searching. Thinking something to do with the compositor and graphics now.

---

### Post by mc4man on 2010-09-16
I've resolved the 'freeze' and or X 'crash', (somewhat hard to always differentiate) here. 
Because it was random in nature - once or twice an hr. to 4+ days there were several 'red herrings', some changes appeared to fix but ultimately it always returned.

In my case memtest showed a bad address, the built-in (dell) preboot mem tests revealed a couple more.
After a mobo and ram replacement last week have had no issues as of yet though several more days should be conclusive. 
(even so can't say it was just the ram, the mobo connectors or the gpu chipset may also have been factors

Here's a rather large thread that at best shows the scenarios vary greatly and the solutions, **if any**, just as much.
[http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787)

---

### Post by Slug71 on 2010-09-21
Well, turned off compositing and quit docky to see if anything comes of that and still got a freeze.

Ran memtest and no errors.

:mad:

---

### Post by Slug71 on 2010-09-22
Well i just had 4 freezes back to back pretty much at 10:12, 10:14, 10:17 and 10:19.
I posted the output from var/log/sys.log and kern.log from around those times to the bug report and then then looked at user.log and found what ive posted below. Looks like it might be my sound card. 
But i only had Firefox open at each crash and wasnt using any sound which makes it really strange to me. Especially since it happens randomly and has happened when the system has been at idle. Ive also never had a problem with sound.

> Sep 22 10:13:25 jj pulseaudio[1351]: module-alsa-card.c: Failed to find a working profile.
Sep 22 10:13:25 jj pulseaudio[1351]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Sep 22 10:16:41 jj pulseaudio[1358]: module-alsa-card.c: Failed to find a working profile.
Sep 22 10:16:41 jj pulseaudio[1358]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Sep 22 10:18:27 jj pulseaudio[1367]: module-alsa-card.c: Failed to find a working profile.
Sep 22 10:18:27 jj pulseaudio[1367]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Sep 22 10:20:34 jj pulseaudio[1351]: module-alsa-card.c: Failed to find a working profile.
Sep 22 10:20:34 jj pulseaudio[1351]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="1" card_name="alsa_card.1" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.

:confused::confused:

---

### Post by kmas on 2010-10-01
i'm having a different issue, but i think it could be taken in same context

my touchpad right click doesn't work. I have a button on my key board for right click, but doesn't right click on items mouse pointer hovers. I also went into synaptic and found an annoying work around, i enable right click with long click, so basically after 2 seconds left clicking right click menu context shows up, any one on what to do to troubleshoot this?

here's a complete report of my hard info: [http://dl.dropbox.com/u/1567633/hardinfo_report.html](http://dl.dropbox.com/u/1567633/hardinfo_report.html)forgot to mention the most important part, i'm on maverick RC AMD 64

ruling out the possibility of it failing because of something i installed, this is a fresh install, ruling out hardware issue, mouse works well under windows. for troubleshooting sake, switched from right handed to left handed, the right click (select) works fine, but the left click (menu) wouldn't bring menu up. I know it has to do with the touchpad configuration on my laptop because USB mouse works. 

cross referencing posts in which i posted this comment: [http://ubuntuforums.org/showpost.php?p=9911694&postcount=5](http://ubuntuforums.org/showpost.php?p=9911694&postcount=5) just in case someone gets mad for duplicates.

---

### Post by mullens101 on 2010-10-01
I had a similar issue (I admit, didn't read this whole thread).  My system would randomly completely freeze, occassionally there'd be screen corruption in the lower right corner.  I did learn that I could still SSH inti the box and restart it cleanly, though restarting GDM or killing X did nothing.

After some research, I disabled x11vnc and the problem's completely gone.  I'm now trying to determine what's wrong with the combo of x11vnc and Maverick.

---

### Post by wilbur.harvey on 2010-10-05
I am having a similar problem.
Dell Studio 15, i7, 8GB ram, ATI graphics with fglrx driver, 240GB Vertex II SSD.
This was a fresh install of maverick and has all updates.
The root file system is btrfs.
I get random complete system freezes when logging in. No mouse, power button doesn't do anything (until held in for about 15 seconds), ctrl-alt-del doesn't do anything.
After last nights updates they seem much worse.
They seem to be associated with the network manager connecting to the wireless network, but no proof of that.
Previously it seemed to only occur when resuming from suspend, but this morning it locked up when the login screen came up.
I hope this helps.
Wilbur

---

### Post by krunge on 2010-10-05
> **wilbur.harvey said:**
> I am having a similar problem.
Dell Studio 15, i7, 8GB ram, ATI graphics with fglrx driver, 240GB Vertex II SSD.
This was a fresh install of maverick and has all updates.
The root file system is btrfs.
I get random complete system freezes when logging in. No mouse, power button doesn't do anything (until held in for about 15 seconds), ctrl-alt-del doesn't do anything.
After last nights updates they seem much worse.
They seem to be associated with the network manager connecting to the wireless network, but no proof of that.
Previously it seemed to only occur when resuming from suspend, but this morning it locked up when the login screen came up.

So you are not running x11vnc?

---

### Post by krunge on 2010-10-06
The freezing problem reported in this thread might be due to this Xorg X server bug:

[INDENT][https://bugs.freedesktop.org/show_bug.cgi?id=30032](https://bugs.freedesktop.org/show_bug.cgi?id=30032)[/INDENT]

Until they fix that one can add the "-noxrecord" x11vnc option as a workaround.

Another workaround is to disable the RECORD extension in the X server (via xorg.conf I guess.)

Please report back here if either one fixes the system freezing problem or not.

---

### Post by Jonners59 on 2010-10-08
> **krunge said:**
> The freezing problem reported in this thread might be due to this Xorg X server bug:
[INDENT][https://bugs.freedesktop.org/show_bug.cgi?id=30032](https://bugs.freedesktop.org/show_bug.cgi?id=30032)[/INDENT]Until they fix that one can add the "-noxrecord" x11vnc option as a workaround.

Another workaround is to disable the RECORD extension in the X server (via xorg.conf I guess.)

Please report back here if either one fixes the system freezing problem or not.
Sorry, but could you give me a terminal cmd that I can run this, please.  I am not sure, otherwise how to do what you are suggesting...

---

### Post by krunge on 2010-10-09
> **Jonners59 said:**
> Sorry, but could you give me a terminal cmd that I can run this, please.  I am not sure, otherwise how to do what you are suggesting...
How is x11vnc being started for you?  Are you running it in a terminal, or is something else starting it? You just add "-noxrecord" to the other cmdline options.

---

### Post by hibit on 2010-10-09
I'm using up to date maverick packages and I think I am experiencing similar issues. Apparently at random (say after five or ten minutes logged in) the left mouse button stops working! Bizarre, as the right button and keyboard still work and Gnome is fine except for this issue. I tend to go to Ctrl+F1 to a terminal and kill gnome-session.

Anyone else got a similar issue? Any ideas how to fix it?

This is an AMD64 machine, nvidia graphics. Has been running previous version of ubuntu fine for a long time. I reckon this issue started happening about a month back (guess). Am happy to help anyone with any diagnostics.

Should I log this as a bug, and if so under which package?

---

### Post by hibit on 2010-10-09
> **Ancanus said:**
> I have a similar issue. Mouse works, but clicking does nothing. My keyboard is fully functional though. I am able to pop up a terminal, sudo pkill gdm, and when my X comes back the mouse is working again.

Aha! This would appear to be very close to what I am seeing. It would help to read all the thread. Is this resolved somehow?

---

### Post by caecusum on 2010-10-09
It is possible that you are experiencing freezes related to [this Nouveau bug]("http://bugs.freedesktop.org/show_bug.cgi?id=26980").  If you have Nvidia hardware but wish to use Nouveau, please try adding nouveau.noaccel=1 to your boot options as mentioned in that bug report.

---

### Post by Jonners59 on 2010-10-10
> **krunge said:**
> How is x11vnc being started for you?  Are you running it in a terminal, or is something else starting it? You just add "-noxrecord" to the other cmdline options.

I don't know???  I certainly do not run anything in cmd line (unless told to).  I use Ubuntu Tweak to do my fine tuning since I discovered it.  Brilliant for noddies like me.  If you can tell me what to look for or make some suggestions I could feed back.

---

### Post by spoon_ on 2010-10-10
Having the same periodic freezing problem on a fresh install of Maverick.

AMD64, Nvidia card, with drivers downloaded from nvidia.com. Problem didn't exist in Lucid.

---

