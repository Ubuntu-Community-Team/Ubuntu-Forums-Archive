---
title: "Problem with 5.1 sound"
date: 2010-10-12
forum: Multimedia Software
---

### Post by raxsix on 2010-10-12
Hi, 

i installed new ubuntu 10.10
I had another Linux installed but there where so many problems especially with the sound. So i think i try new Ubuntu. When the installation were finished. i immediately checked the sound. I was surprised there where a options to choose 5.1 sound, i thought nice. i chose that and test the sound, it worked. 
Now u think where is the problem then ??!!
I tell you...
When i listen to some music and the next song comes then the 5.1 sound turn off and only 2 speaker play the sound. Same thing happens when i restart the PC. Every time i must go to sound preferences and change the option ( click something else than 5.1 and then click back 5.1, then the sound comes back in 5.1) until next song :( drives me crazy.........



*-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:c000(size=256) ioport:c400(size=64) memory

---

### Post by Mugsy323 on 2010-10-12
Unfortunately, I don't have an answer for you.

I'm writing to say I am having the same (?) problem. And it seems new to 10.10.

I have a 5.1 speaker setup. All the way up to Ubuntu 10.04, when I set my sound preferences to "Analog Surround 5.1 Output" ("Hardware" tab, Profile drop-down), all my speakers worked.

I did a fresh full install (w/format) of 10.10 this morning, and I'm only getting stereo output no matter what I set my hardware too. I'm using the correct "device" for output ("Internal Audio"), but when I "Test Speakers", only my front two produce sound.

As I noted, they worked just fine in 10.04, and they work fine in Windows (XP), but something changed in 10.10.

---

### Post by Buttink on 2010-10-12
I cant even get that far. I get a weird buzzing noise on my 5.1 but only that X.1.

---

### Post by Mugsy323 on 2010-10-12
> **raxsix said:**
> When i listen to some music and the next song comes then the 5.1 sound turn off and only 2 speaker play the sound.
I may have discovered something.

What installation of Ubuntu 10.10 did you install? My problem is with the 64bit version.

I just installed 32bit Ubu 10.10 on another drive (I put 32bit Ubu on a Flash drive I can take with me to use on other computers, and use 64bit Ubu at home), and 5.1 Surround Sound works perfectly on the 32bit installation!

Something has changed in the way 32bit & 64bit Ubu handles sound. Must be a (flakey) 64bit sound driver.

Until they produce a fix, if you *absolutely* my have Surround Sound, try installing the 32bit version.

---

### Post by raxsix on 2010-10-13
I installed 32-bit version


uname -m command give me a answer i686, then it should be 32-bit

---

### Post by Mugsy323 on 2010-10-13
> **raxsix said:**
> I installed 32-bit version


uname -m command give me a answer i686, then it should be 32-bit
Yes, installing the 32bit version on a 64bit processor reports "i686" (32bit cpu's report "1386".) 64bit Ubu reports "x86_64".

Comparing my two installations, I found the default settings between my two installations were slightly different. On my 32bit install, by default, it had an INPUT audio device (in my case my "USB WinTV" device) set to "Enabled", and the "Fade" setting was (properly) centered, where as it was well off on my 64bit install.

By making those changes (enabling the "Input" device... which Ubu doesn't even use... and centering the "Fade" slider), 5.1 sound now works properly under both of my Ubuntu installations.

---

### Post by raxsix on 2010-10-13
Does not work for me, dunno then...

---

### Post by michalstaporek on 2010-10-14
hello, i have resolved my problem, just type alsamixer in the terminal and adjust your master front volume
hope it helps

---

### Post by esorensen on 2010-10-17
Just did a fresh 64 bit install (10.10) and I couldn't set surround either. I'm not willing to reinstall as 32, so I guess I'll keep trying and waiting til a solution...

---

### Post by esorensen on 2010-10-17
> **Mugsy323 said:**
> Yes, installing the 32bit version on a 64bit processor reports "i686" (32bit cpu's report "1386".) 64bit Ubu reports "x86_64".

Comparing my two installations, I found the default settings between my two installations were slightly different. On my 32bit install, by default, it had an INPUT audio device (in my case my "USB WinTV" device) set to "Enabled", and the "Fade" setting was (properly) centered, where as it was well off on my 64bit install.

By making those changes (enabling the "Input" device... which Ubu doesn't even use... and centering the "Fade" slider), 5.1 sound now works properly under both of my Ubuntu installations.

Hi Mugsy, where did you do these changes? I looked for it and couldn't find it... I'm hoping to fix it quickly!!

---

### Post by Mugsy323 on 2010-10-17
> **esorensen said:**
> Hi Mugsy, where did you do these changes?
If you left-click on the speaker icon in the tray, you can access Sound Properties.

Make sure "Fade" is balanced and... if you have any other Multimedia hardware... it is "enabled" even if Ubu doesn't use it (to avoid conflicts).

Are you using on-board AC97 audio?

---

### Post by esorensen on 2010-10-17
I guess this is why... using HDA Intel (ALC888).

---

### Post by Mugsy323 on 2010-10-17
> **esorensen said:**
> I guess this is why... using HDA Intel (ALC888).
Are you using SPDIF?

I hate taking shortcuts, but a "quick & dirty" solution might be to blow $15 on a cheap sound card (you're probably not picky about sound since you are already using the on-board ALC888).

You're getting stereo but not Surround Sound?

This might help: [http://www.uluga.ubuntuforums.org/showthread.php?t=674437](http://www.uluga.ubuntuforums.org/showthread.php?t=674437)

---

### Post by raxsix on 2010-12-03
Still no solution found...

---

### Post by Mugsy323 on 2010-12-03
> **raxsix said:**
> Still no solution found...
If 5.1 sound works *after* you change the setting back after boot, then either *something* in your startup settings is changing it back, or your system is detecting your audio device as only being capable of stereo.

You mentioned using the "AC'97 Audio Controller", meaning on-board audio, not a separate card.

You might find some helpful info [here]("https://help.ubuntu.com/community/SoundTroubleshooting").

I'll do some more research and see what I find.

---

