---
title: "Sigmatel 92xx STAC is not supported?"
date: 2008-08-02
forum: Multimedia Software
---

### Post by rosegarden78 on 2008-08-02
Dear Community:

I checked the ALSA homepage and Sigmatel was not listed as approved vendor.  However, Sigmatel sound seems to work fine in Inspiron 1200 laptop using 975X chip.  But the 92xx chips are missing key features in Linux:

Stereo mix (record what I hear)
Line in

I'm losing sleep over the best way to handle this.  I already know a couple things:

1) Using Rosegarden + JackD - I can record Qsynth 
2) Using PulseAudio wiki - I can record streams

But, I'm dismayed that "true stereo mix" is missing.  Can somebody give me a clear answer?

1.  Is the problem with the Sigmatel 92xx STAC chipset?
2.  Is there anyway to add stereo mix to the drivers / config?

The solution to this for Vista is: Download R171789.EXE from ftp.dell.com.  Install this in Compatibility Mode for SP2.  Go to Control Panel - Sound and right click the white space in Recording Devices to display hidden disabled device.

---

### Post by rosegarden78 on 2008-08-05
Okay, guys, I kinda knew what would happen but I called Dell Pro Support.  They, wow, didn't have that problem in their Internal Knowledge Base.  So if you got a new Dell Vostro or XPS recently with this chipset you may have this problem too.

While the Sigmatel website has always stated the same: Contact your vendor for drivers we do not make them - Dell asserts that drivers do indeed come from Sigmatel.  Dell claims they merely confirm that the new drivers function correctly.

Well, correctly and completely are entirely different.  You will likely encounter significant signal noise with this chipset and the R171789.exe driver while using a digital mic or analog input.  The line input has not been tested but has a higher STN ratio.

What this all means is: Sigmatel ultimately controls the release cycle of driver updates.  Neither Dell nor Intel hires programmers to make Sigmatel drivers.  You are at the mercy of Sigmatel whether or not your device will work.

I do have hope that Linux programmers (I want to get an AA in Computer Science) hack the Sigmatel STAC 92xx pretty soon.  My latency in ZynAddSubFx was at most 60 ms in Windows XP version, while I could configure Jack with ZynFX as low as 22 ms in Ubuntu Studio.

Oh, yeah, I almost forgot the reason for writing: If you want to make high quality sound recordings you need high quality equipment.  Tomorrow I'm going to Guitar Center to pickup a USB microphone and maybe a USB Mixer.  If the USB Mic provides a noise-free signal and low latency then I won't need analog mic input anymore.  The High-Def Audio output is noise-free and doesn't seem to have any problems.  Only the Digital Mic and Mic Input are affected by a humming static sound.

If you use Windows XP search ftp.dell.com for Knowles Acoustics Intellisonic Speech Enhancement.  This is real-time noise reduction for VOIP and speech programs.  I used it with Audacity and it does erase the signal noise.  You can get professional real-time noise reduction from ATC.com but it costs $1499 USD.  So while the Intellisonic skips and pops making it unsuitable for music, it could be used for clear narration and speech regognition.

If you want post-production ways to reduce noise try SoundSoap for Windows or just use Audacity.  It has a plugin that learns the noise and then removes it.  This does not work well on speech like Intellisonic - rather for vocals it works well.  While Audacity does not process noise in real-time it has features seen on expensive pro audio software.

---

### Post by CharlieFoxtrot on 2008-08-09
Thank you for your informative post.

I switched from The Other Operating System 10 months ago. I tried the Ubuntu live CD on my aging IBM desktop and found that although most everything worked well, I had audio problems. Because the IBM was due for replacement, and to avoid hardware compatibility problems, I purchased a Dell XPS410 (desktop) Ubuntu machine (sans speakers & monitor). I got it working well with my monitor but have never gotten audio working 100%. Although I have audio, I&#8217;ve never been able to get Audacity working well (not at all in Hardy) nor been able to record what you call &#8220;Stereo Mix&#8221;. I did manage to record &#8220;Line In&#8221; before Hardy.

My machine has on-board audio HDA Intel, SigmaTel STAC9227 chip. Your post reinforces my suspicion that my on-board audio will never do all of the few simple tasks I want it to. Not being an audiophile, I find all the audio options and layers in Ubuntu daunting. All I want to do just record &#8220;Stereo Mix&#8221; and get Audacity to work! I don&#8217;t need 127-channel surround sound and Nashville studio recording facilities.

My current line of thinking is that my simplest solution, especially since I&#8217;m still a Linux neophyte, is just to disable on-board audio and install a sound card. Any advice/recommendations?

---

### Post by rosegarden78 on 2008-09-12
Yeah I have another post related to this.  You'll want a professional audio sound card.  I went with an external USB model the M-Audio Fast Track Pro.  For even less money you can get an internal card from Guitar Center etc.  Frankly I would go back to Windows XP and check the torrents for thy desires.  :)

[http://ubuntuforums.org/showthread.php?t=769822](http://ubuntuforums.org/showthread.php?t=769822)

My reply at the bottom summarizes a few great articles.  Sadly getting "Stereo Mix" to work will need PulseAudio with padsp to launch your audio program.  Or just use QJack to patch your programs into Audacity.

---

