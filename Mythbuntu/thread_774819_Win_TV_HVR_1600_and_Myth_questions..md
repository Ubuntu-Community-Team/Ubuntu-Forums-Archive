---
title: "Win TV HVR 1600 and Myth questions."
date: 2008-04-29
forum: Mythbuntu
---

### Post by Midwest-Linux on 2008-04-29
Hauppauge Win TV HVR 1600 and Myth questions

I bought this unit, I read different posts that Linux doesn't support this unit...but there is a Beta driver and it is Linux supported.

 Then some posts say the remote is not supported, but the remote works only for Vista. I would just use the 1600 with Windows, but really want to go with Linux, also I would like the ability to burn DVDs of what I recorded if that is easily done.

 I also have a 950 stick model too.

 So should I return this unit and look for a model 150? The stores don't seem to carry it, but seems E-bay has several for sale.

 Is there a much simpler way to make Mythbuntu work strictly as a Video recorder? I have a set top box from a U.S. satellite company called Direct TV and plan to use Mythtv with the set top box set for output for one channel. I can use the set top box to switch channels.

 So how do I set up Mythbuntu with out all the extra menus and server setups? Is there a Mythbuntu Lite? 

 Is there a tutorial for setting up a Mythbuntu or any Linux based video recorder..especially a simple video capture that I can play back on my TV? 

 Can I set up some kind of Mythbuntu on a spare computer Pentium III with 256 MB of ram or do I need a 2 Ghz unit with 1 Gb of memory.

Thanks in advance for any answers you may have.

---

### Post by Midwest-Linux on 2008-04-30
Anyone ??

---

### Post by msrinath80 on 2008-05-03
I own a HVR-950 and I can tell you that it works without any problems (out of the box) on Fedora 9. It does not work on Hardy for me, so I will be switching to Fedora.

All you need is to do in Fedora is copy the firmware file (xc3028-v27.fw) to /lib/firmware and you're all set to watch TV. Absolutely no compiling, kernel configuration etc.

---

### Post by superm1 on 2008-05-04
> **msrinath80 said:**
> I own a HVR-950 and I can tell you that it works without any problems (out of the box) on Fedora 9. It does not work on Hardy for me, so I will be switching to Fedora.

All you need is to do in Fedora is copy the firmware file (xc3028-v27.fw) to /lib/firmware and you're all set to watch TV. Absolutely no compiling, kernel configuration etc.
What driver is the 950 supported by?

---

### Post by msrinath80 on 2008-05-04
em28xx driver.

---

### Post by pigphish on 2008-05-29
> **msrinath80 said:**
> I own a HVR-950 and I can tell you that it works without any problems (out of the box) on Fedora 9. It does not work on Hardy for me, so I will be switching to Fedora.

All you need is to do in Fedora is copy the firmware file (xc3028-v27.fw) to /lib/firmware and you're all set to watch TV. Absolutely no compiling, kernel configuration etc.

Could you explain where we can get this file, xc3028-v27.fw, and how did you configure myth or other tv program.

---

### Post by bronson on 2008-09-26
Here's how to get that firmware file.  Hopefully you found the answer months ago but, if not...

cd /tmp
wget [http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip](http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip)
unzip -j HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip
perl extract_xc3028.pl
cp xc3028-v27.fw /lib/firmware/`uname -r`

I put some more notes on how to set it up a related device here: [http://u32.net/MythTV/WinTV-HVR-950/index.html](http://u32.net/MythTV/WinTV-HVR-950/index.html)

---

### Post by nmahini on 2008-09-26
Hi all,

I desperately need help. I'm running ubuntu 8.04 on a machine with following configuration:

MB: M3A78-EM
CPU: AMD
Ram: 2 gb
Tuner: Hauppauge HVR-1600

I installed and configured the mythtv and I'm running an S-Video cable from my Directv H21 setup box to the Hauppauge.

The problem that I ran to is that once I start mythtv and I chose the "Watch TV" option, I only couple of frames per second, so instead of being able to get anything out of what it's being showed, I just get pictures being refreshed every 3 seconds.

I tried installing an update for my video card( which is by the way on the MB) and I got an error sayin the version was incorrect. Now the driver was downloaded from Asus website and I'm assuming that it's the latest.

Any thoughts regarding the problem?? Any solutions you guys might've think of??


Thanks

---

