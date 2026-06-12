---
title: "NVIDIA driver broke my nvidia hdmi output"
date: 2012-04-22
forum: Multimedia Software
---

### Post by strask on 2012-04-22
Hi all.

I have a new clean install of ubuntu 11.10 on a notebook with NVIDIA graphics with an HDMI output that I connect to a large screen.

It seemed to be working fine for me until I tried to play some .mp3 files via banshee, and the audio came out of the notebook speakers rather than the (much better) display speakers. I tried selecting the hdmi audio output in the audio control panel, but then I got no sound at all.

So I read the sound troubleshooting sticky in this forum and found procedure Ae: Make NVIDIA HDMI Audio Work. That looked like exactly what I needed to do. It said to install the NVIDIA proprietary graphics driver, so I did, and when I rebooted...

1) My large display connected via hdmi is not detected at all.
2) My notebook display which was previously detected and identified in the display control panel is now listed as "unknown".

I tried un-installing the nvidia driver but that didn't fix my display problem. Not only that but the next steps in the sound troubleshooting guide don't work for me either (when the nvidia driver is installed) so I'm pretty completely lost now. 

Any help would be highly appreciated. At this point my priority is to get the large display working again, getting it to also provide audio would be nice but is not urgent.

---

### Post by strask on 2012-04-23
I would really like to get back at least to where I was before with both displays working, and it occurs to me that I might be able to do something like this:

1) Boot from the Ubuntu livecd (which correctly uses both displays)
2) Type some commands or look at some files to determine what video drivers it is using.
3) Boot back into my installed OS.
4) Type some commands or modify some files to match things up with step 2.
5) Reboot.

I just need help figuring out what needs to happen in steps 2 and 4. Anyone?

---

### Post by strask on 2012-04-23
Solved!

With the NVIDIA proprietary driver installed, I discovered a new application in the dash called "NVIDIA X Server Settings". Selecting "X Server Display Configuration" on the left-hand navigation tree showed me a layout panel with my larger display labeled as "Disabled". I've attached a screen shot of this window.

A few clicks later I was able to configure things the way I wanted them and when I hit "apply", my big display came on just as it should.

My audio is still not going through the HDMI like I want it to, but I can fiddle with that later.

---

### Post by houseworkshy on 2012-04-23
Sorry this isn't a fix but it looks like your thread needs a bump.  You could install "sysinfo", which is available in the repositories.   Running this, it puts a link in your Applications>System Tools, will get your hardware specs, that will let you search more accurately and it has an option to save an overview to file which you could attach to posts in the hope of getting specific advice.  Good luck.

---

