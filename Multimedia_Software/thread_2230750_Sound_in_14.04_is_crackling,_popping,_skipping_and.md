---
title: "Sound in 14.04 is crackling, popping, skipping and echoing"
date: 2014-06-20
forum: Multimedia Software
---

### Post by ClayJ on 2014-06-20
Hello,

I've posted this in launchpad already, but I'm hoping to get some help here. I installed 14.04 over an old install of ubuntu (formating the partition) and kept the /home folders that were on a different drive. The audio has not worked properly since installation, including system sounds. The audio seems to echo and skip with crackles and pops. I've tried the adding tsched=0 to /etc/pulse/default.pa, which did not work. During boot there is a message displayed saying snd_hda_codec/snd_hda_intel has bad taint, and something about trace events, but the computer does boot. I do dual boot with Windows 8.1, but it is on another hard drive. My motherboard is an asus gryphon z97 with a Realtek ALC892 audio chipset.

I posted my alsa info here: [http://www.alsa-project.org/db/?f=cd36934e5bb672e54b2e0f6895c3b85a165b8fb7](http://www.alsa-project.org/db/?f=cd36934e5bb672e54b2e0f6895c3b85a165b8fb7)

Thanks

---

### Post by matthayllar on 2014-06-21
I feel your pain.  My sound crackles and sounds sort of like what a bad analog connection might sound like if someone were twisting the connector.  I thought I had a cable problem until I realized it does it through SPDIF, 3.5mm, and HDMI outputs, and this is the ONLY OS it happens in.  I too have screwed with the files in the /etc/pulse/ directory more than anyone ever should ever have to.  I managed to lessen the problem, but it just caused side effects in other areas.  Bad sound is a deal breaker.  PulseAudio and ALSA are both junk, and they're smearing crap on what is otherwise a great OS.  Take the amount of time I've spent screwing with the sound, convert that into money, and I could have bought 10 Windows licenses by now.  Windows may be stupid, ugly, and boring, but at least she puts out.

---

### Post by paul146 on 2014-06-23
Mine does something similar, but it only does it when i switch to headphones. It went away one while watching youtube. I have tried both front and rear jacks and 2 diff headphones. they work fine on my cell phone and other computer that runs windows. The sound is fine thru my HDMI cable to my moniter.

hopefully our issues are related.

---

### Post by ngujay on 2014-06-23
I'm also having the same issue with my Asus Z97-A board that's using the Realtek ALC892 codec as well. 

I've been testing around to see when it happens. I've only messed around and tested for around 2-3 hours. From my experience it happens usually when buffering and playing media at the same time: e.g. Watching a YouTube video. When i migrate into different tabs, while audio is still playing in one (or more) tab(s), the audio will crackle and become very distorted. I find that the audio will just progressively get worse. I'll extensively check out the Windows side of things tomorrow because I dual-boot.

---

### Post by Yellow Pasque on 2014-06-23
@ngujay: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1321421](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1321421)

---

### Post by ClayJ on 2014-06-24
Thank you Temujin,

The following worked for me, as per your link.

sudo gedit /etc/modprobe.d/alsa-base.conf

and added the following line to the bottom:

options snd-hda-intel vid=8086 pid=8ca0 snoop=0

Sound works fine now. Your link says it is something that is being patched in kernel 3.15, so the above may only need to be a temporary fix. :)

---

### Post by ngujay on 2014-06-26
> **ClayJ said:**
> Thank you Temujin,

The following worked for me, as per your link.

sudo gedit /etc/modprobe.d/alsa-base.conf

and added the following line to the bottom:

options snd-hda-intel vid=8086 pid=8ca0 snoop=0

Sound works fine now. Your link says it is something that is being patched in kernel 3.15, so the above may only need to be a temporary fix. :)

This also worked for me.

Thanks Temujin

---

### Post by Yellow Pasque on 2014-06-26
You're welcome. The fix should land in Ubuntu 14.04.1 and 14.10.

---

### Post by DrJohn999 on 2014-06-27
Same problem here on Asus Z97-A: [http://ubuntuforums.org/showthread.php?t=2229310](http://ubuntuforums.org/showthread.php?t=2229310) 

Switching to HDMI audio thru the monitor works fine. Have to give it a try over Bluetooth phones at some point.

---

### Post by jh71 on 2014-06-27
[FONT=arial]As the others, I added the line 
 [/FONT][COLOR=#000000][I][FONT=arial]options snd-hda-intel vid=8086 pid=8ca0 snoop=0
to alsa-base.conf, and this solved the bad noise.
But now my wireless usb adapter disconnects regularly (every 5 minutes or so), and this is very annoying.
I have the same problem with 2 different wireless adapters.
For the moment, I have written a small script to restart network-manager automatically.
[/FONT]I tried to install linux 3.15 kernel, but then I only get a blank screen.

Any idea what can be wrong with the wireless ?
It is related to this line in alsa-base.conf, because I do not get these disconnects when I comment it out, but then the crackling noise returns.

[/I][/COLOR]

---

### Post by mrojas73-l on 2014-07-11
Thanks a bunch, fixed the issue on my brand new system!

---

### Post by nerdylicious on 2014-07-17
> **jh71 said:**
> [FONT=arial]As the others, I added the line 
 [/FONT][COLOR=#000000][I][FONT=arial]options snd-hda-intel vid=8086 pid=8ca0 snoop=0
to alsa-base.conf, and this solved the bad noise.
But now my wireless usb adapter disconnects regularly (every 5 minutes or so), and this is very annoying.
I have the same problem with 2 different wireless adapters.
For the moment, I have written a small script to restart network-manager automatically.
[/FONT]I tried to install linux 3.15 kernel, but then I only get a blank screen.

Any idea what can be wrong with the wireless ?
It is related to this line in alsa-base.conf, because I do not get these disconnects when I comment it out, but then the crackling noise returns.

[/I][/COLOR]

Installing the latest linux kernel (3.16) solved the sound distortion for me on an ASUS Z97-Pro.  Using Ubuntu on a Z97 build also revealed other hardware compatibility  issues (which is apparently common when you're a Linux user and you're  on the bleeding edge of things). I documented some of these other fixes  here: [https://github.com/Nerdylicious/How_...ntel_Z97_Build]("https://github.com/Nerdylicious/How_To_Fix_Ubuntu_Compatibility_On_Intel_Z97_Build")

I also had an issue with my USB wireless adapter disconnecting every few minutes. I was able to solve this issue by installing the Broadcom STA Driver (after having to make a few changes to the driver source code in order to support linux kernel versions of 3.15 and above). Here are the instructions that I followed: [https://github.com/Nerdylicious/How_To_Fix_Ubuntu_Compatibility_On_Intel_Z97_Build#install-broadcom-wireless-driver](https://github.com/Nerdylicious/How_To_Fix_Ubuntu_Compatibility_On_Intel_Z97_Build#install-broadcom-wireless-driver)

---

### Post by dark-sylinc on 2014-12-25
Hi, I just got a similar MB (ASUS Z97-P) and noticed that:

1. The rear audio sounds fine.
2. The front panel audio sounds choppy, with pops, very noisy. Almost unbearable.

There is a quick fix for the lazy ones that doesn't involve Kernel upgrades.

Enter the BIOS, go to Advanced->Onboard Devices Configuration->De-Pop. Set it to "Disabled". All problems gone.

When you plug the headphones, the rear audio stops playing. This is supposedly "a feature" which happens on Windows too. You can disable this in two ways:
[LIST=1]
[*]BIOS: Advanced->Onboard Devices Configuration->Front Panel Type. Set it to AC97. The audio card will now be no longer be able to tell whether you plugged the headphones/microphone in the jack or not and will power all jacks all the time.
[*]Software: Open alsamixer from a terminal. Hit F6 to select "HDA Intel PCH" (if not already selected). Find the option that says "Auto-Mute"; hit Z to disable it. Press Esc to quit. Now type "sudo alsactl store" to keep this setting forever.
[/LIST]

---

