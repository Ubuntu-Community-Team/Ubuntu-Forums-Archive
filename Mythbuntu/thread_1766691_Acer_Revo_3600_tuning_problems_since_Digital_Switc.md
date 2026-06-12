---
title: "Acer Revo 3600 tuning problems since Digital Switch Over"
date: 2011-05-24
forum: Mythbuntu
---

### Post by Vargster on 2011-05-24
Hi all,

I've got serious issues with my MythBuntu install since the Digital Switchover in my area of the UK (Sandy Heath).

I installed MB nearly a year ago, using the Lucid 10.04 LTS version, on an Acer Revo 3600 using a K-World 399U USB DVB-T twin tuner and an old MCE remote, over HDMI to my TV. It all worked, first time, out of the box with no messing about.

In nearly a year of daily use I've only have one minor issue with it, in that occasionally when the back button on the remote is pressed to stop viewing a recording and jump back to the menu, the Front End crashes and the desktop is visible, annoying but not really a showstopper.

All this stopped when it came to retune for the Digital Switchover. I closed the FrontEnd, started Myth Setup and rescanned the muxes.

It didn't find any, which was odd as my TV found them all. I replaced the TV antenna that night, which seemed to help, Myth found most of the channels, everything seemed to be OK. Then the chaos started, at random points during the day or night, it would stop recording programmes correctly. They would show in the recorded programmes list, but pressing play gave and error saying the "file can not not be found". Then I noticed that the orange light on the K-World 399U, that had been on for nearly a year, was off. It was on when the box was restarted and everything worked until something happened and the light went off and no more recordings. 

Ah, just a coincidence I though! I bought another matching K-World 399U tuner and swapped them over. This tuner did the same thing.

The Mythbox was now being restarted two/three times and day, yet was still missing several programmes a day.

I thought the only thing to do would be to reinstall MythBuntu (maybe an update killed it?), this took a while as most of the guides about restoring the database don't seem to work on Lucid, but using phpmyadmin it was sorted. Sadly the reinstall didn't help, the recording was the same as before, and MythWeb just brought back a blank page and the HDMI sound didn't work. I upgraded the dvb firmware to version 5.1, still no use. I updated the OS (I'd been trying not to incase it caused the problem) as now I was running out of options, still no use. I found a webpage with script to upgrade V4L (I think) specifically for Lucid but that not longer works as the repo had been removed.

I wiped it and tried again with Maverick, but the MCE remote drivers appear to be broken, most button presses are ignored.

So I moved onto Natty. The remote now works fine, but the sound over HDMI didn't. After much googling I found it needed a manual tweak to one of the config files. However, now the second tuner doesn't appear to work. Myth knows it there, but when it tries to record something on tuner 2 it just sits there 'Tuning' for the length of the show, so nothing is recorded. The listing still shows up on the recorded shows list, but if you attempt to watch it, you get the dreaded 'file cannot be found' error. And then after some time the first tuner drops out and no longer records. I've tried a signal booster, I've tried all the Afatech firmwares, but nothing seems to help.

I'm at my wits end. Is anyone else having these issues or is it just me? I don't understand what's happened to such a stable system.

Is anyone else running a Revo recording Freeview? What version of MythBuntu? What tuners are you using? Are you experiencing any issues with them? 

Argh! Any help much appriciated!

PS. I'm running  2:0.24.0+fixes.20110416.9ba3ece-0ubuntu1, I'm getting a small section of the logs together now.

---

### Post by ian dobson on 2011-05-25
Hi,

Have you tried deleting all channels/input sources, recreating them and doing a new scan. I've seen afew times that MythTV gets really confused if channels move.

Regards
Ian Dobson

---

### Post by Vargster on 2011-05-25
Ian,

That certainly helped at the very begining when I was having issues finding the channels, and I've done it several times on each of the different installs/versions, but it's not had any effect on the problem with the tuners tuning or dropping out.

Cheers,
V.

---

### Post by Vargster on 2011-06-09
After much reading and head scratching, I gave up in disgust. :(
Unlike me, but there's only so long the family can be without TV and we were well past that deadline.

I bought a new Hauppauge WinTV Nova TD USB dual DVB-T (freeview) tuner and replaced the K-World 399U dual tuner. It was recognised out-of-the-box (no manual work required at all). After a quick delete of the old tuners and addition of the new tuners, all seems OK. It's been recording solidly for two weeks now. 

Result!
:popcorn:

---

### Post by zorro07 on 2011-06-09
Hi, the afatech tuners work well once installed properly except they need to be cold booted.  Restarting the myth box will cause the tuners not to work properly, continually trying to tune channels and never recording of allowing lock on a channel. 

So number 1 tip - never, never reboot a system with an afatech chip set.  Always shutdown and cold boot the system.  All will work well if you have the right drivers installed.

Tip 2 - install the latest V4L drivers.  V4L now uses git to distribute rather than mercurial.
Check out the V4L wiki for details of installing the drivers.  It's really easy.
Btw V4L is now in version 2.  

It's a pain that the driver is so unstable but that's the current state of play.  Works ok if you cold boot the system.

Cheers
Paul

---

