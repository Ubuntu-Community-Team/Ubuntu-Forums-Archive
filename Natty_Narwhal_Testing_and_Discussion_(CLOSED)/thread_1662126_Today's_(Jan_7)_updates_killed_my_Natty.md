---
title: "Today's (Jan 7) updates killed my Natty"
date: 2011-01-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ratcheer on 2011-01-07
There were a lot (around 70) updates to install to Natty, this afternoon. I did not notice any errors when installing them. My Natty installation will no longer boot, either to normal or recovery mode. The screen goes black, plymouth never shows up. When trying to boot to recovery mode, messages are displayed, but none of them are obvious error messages.

I had already successfully updated to new kernel 2.6.37-12, yesterday, so that is not the problem.

I guess I will have to do a fresh install.

Tim

---

### Post by cgroza on 2011-01-07
That is the joy of an ALPHA tester.

---

### Post by ratcheer on 2011-01-07
> **cgroza said:**
> That is the joy of an ALPHA tester.

I understand. I am mainly fishing around to see if this happened to anyone else.

Tim

---

### Post by arpanaut on 2011-01-07
Thanks for the heads-up!

I haven't done any updates since last night late.
But I was about to go for it today.

Maybe I'll wait and see...

UPDATE:  3 hours later, 2 installs updated fully and no problems on either one.
Actually smoother than the updates last night, go figure?

---

### Post by cecilpierce on 2011-01-07
I have one install doing the same thing, but after about the forth try it started to work and then craped out again, but it boots once in awhile, keep cussing it :D

---

### Post by cecilpierce on 2011-01-07
Funny, one other install just crashed with blinking keyboard lights and locked up with a lot of text on the screen, pushed the reset and it booted OK the second time !!! :(

---

### Post by rburkartjo on 2011-01-07
most of the updates went okay got a lot of kernel panics(4 or 5) when installing the various updates
at least it didnt completely bork my system again.

---

### Post by mc4man on 2011-01-07
I've seen quite a number of hanged boots and or kernel panic's of late.
With the default lack of text output (nvidia), not sure if it's always a panic or if the hang is something else.
99% sure it's not hardware related (health-wise), though the cmos batteries may be questionable. (maverick on same machine is always fine.

Did manage to go from no boot possible this afternonn to 'seemingly' ok thru a few 'adjustments', a dozen or so restarts have gone fine. (kinda off the wall so probably not worth mentioning

---

### Post by nm_geo on 2011-01-07
I guess my question would be how did everyone do their upgrades today?  Anyone do a aptitude safe-upgrade?  I downloaded the current daily Natty iso at lunch with zsync and notice there the ISO had like a 30% change from yesterdays.  Believe that is the largest daily change I have noticed.

---

### Post by Quackers on 2011-01-07
I use synaptic all the time now. I'm up to date with updates at the moment.
Apart from the odd minor annoyance along the way (apart from the 2.6.37-6 to 2.6.37-7 fiasco, which wrecked everything) I seem to have escaped most of the serious problems - so far :-) On both Natty installs.

---

### Post by cariboo on 2011-01-07
I found with the updates, bcmwl-kernel-source, doesn't create the wl module, so no wireless. After some looking a round, I installed the b43 driver and firmware and I have wireless again, I'm still working on it as the device has changed from eth1 to wlan0 and Network-manager won't manage the device. I can get it to work on the command line.

---

### Post by ratcheer on 2011-01-07
> **nm_geo said:**
> I guess my question would be how did everyone do their upgrades today?  Anyone do a aptitude safe-upgrade?  I downloaded the current daily Natty iso at lunch with zsync and notice there the ISO had like a 30% change from yesterdays.  Believe that is the largest daily change I have noticed.

Yes, I used aptitude update, then aptitude safe-upgrade.

Tim

---

### Post by ronacc on 2011-01-07
I haven't been able to get any of the last 3 daily's to give me a working install , mostly ubiquity crashes at a random place , or if the install actually completes it won't boot .

---

### Post by nm_geo on 2011-01-07
Okay here we go I am determined to boink this one too...Man I hope I don't lose all 18 program Icons in my unity panel that I squashed the trash can with. ;)

ronacc I have been capturing a daily everyday since before Xmas just primarily to see how much the daily build changes.  Maybe I will need one soon.

---

### Post by ronacc on 2011-01-07
I keep the daily updated with zsync but usually just use a usb stick to check that it boots to destop , only occasionally actually install from it , the current ones boot to desktop ok it is ubiquity and the partitioner that are dying .

---

### Post by jerrylamos on 2011-01-07
> **cecilpierce said:**
> Funny, one other install just crashed with blinking keyboard lights and locked up with a lot of text on the screen, pushed the reset and it booted OK the second time !!! :(
I get those failed boots more often than not.  I think it helps to remove "quiet" from the boot line.

I don't know how to do a launchpad bug from this totally dead very early crash.

Any clue, anyone?

Jerry

---

### Post by MacUntu on 2011-01-07
-- deleted --

---

### Post by efflandt on 2011-01-07
After being on vacation for over a week, I started using **Update Manager** since it automatically appeared last night (Jan 6) after hitting the Reload icon in Synaptic before doing any updates.  Update Manager did throw an error, with the last thing in the log being the 2.6.37-12 kernel.  On reboot it did something unknown and rebooted again, but the 2.6.37-12 64-bit kernel booted fine.  I did remove the Afghanistan keyboard, so the keyboard applet went away (with just USA keyboard).

When I got home from work tonight around 6 PM Chicago time (-6:00) I used Update Manager again, which seemed to list many similar updates showed the night before.  It rebooted cleanly and everything seems to be working properly (for now).

---

### Post by Harry33 on 2011-01-08
My 64-bit desktop system (nvidia-current) is up to date and working fine.
For xserver, I use xorg-edgers version 1.9.2.901 instead of 1.9.0 in the repos.

I haven't found any problems with the 2.6.37-12 kernel nor with grub updates.

One odd thing yesterday was the package console-setup which now depends on keyboard-configuration.
On install it asked me to set the shortcut key for shifting between national and general keyboard setup.
The odd part here is that it suggested the Caps key to be used for that purpose!
Now, I need the Caps key for writing, so I set alt+Caps for shifting keyboard setup.
I haven't experienced this Afganistan key mess at all.
Oh, I use english (UK) language on my system and Finnish keyboard setup.

---

### Post by Gladk on 2011-01-08
> **cariboo907 said:**
> I found with the updates, bcmwl-kernel-source, doesn't create the wl module, so no wireless. After some looking a round, I installed the b43 driver and firmware and I have wireless again, I'm still working on it as the device has changed from eth1 to wlan0 and Network-manager won't manage the device. I can get it to work on the command line.

The same problem for me. How did you start the wireless with command line? 

There is a corresponding bug for that
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/699915](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/699915)

---

### Post by cariboo on 2011-01-08
> **Gladk said:**
> The same problem for me. How did you start the wireless with command line? 

There is a corresponding bug for that
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/699915](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/699915)

I used the following commands:

```
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>
```

---

### Post by Gladk on 2011-01-08
Thanks, cariboo907!

What do you think, is it better to wait till next update not doing this workaround?

---

### Post by ekjsim on 2011-01-08
Updates on Maverick seems fairly stable.

---

### Post by t1497f35 on 2011-01-08
Nobody leaves the building, a detective is on the way to investigate who killed Natty.. oh wait..

---

### Post by ratcheer on 2011-01-09
I have not exactly solved, but worked around the problem, whatever it was. I did a fresh install to the Jan 8 alternate iso image. I am glad I did because it fixed a bunch of nagging problems that had been building up in my 6-week old Natty installation. The downside is that I have to reinstall my software and reconfigure things - Java, ntp, Flash player, ALSA, etc, etc...

Tim

---

### Post by Amroozy on 2011-01-10
after last update i got "Error file not found" message while booting to natty but the funny thing is that natty boot after all..
i have no idea which file is not found or how is my system boots up with a missing file..

---

### Post by flomar on 2011-03-12
> after last update i got "Error file not found" message while booting to natty but the funny thing is that natty boot after all..
i have no idea which file is not found or how is my system boots up with a missing file..
I get the same error, natty continues to boot anyhow after ca. 15sec.

---

