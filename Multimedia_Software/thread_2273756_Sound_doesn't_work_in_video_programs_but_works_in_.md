---
title: "Sound doesn't work in video programs but works in browser"
date: 2015-04-15
forum: Multimedia Software
---

### Post by lion3 on 2015-04-15
Let me start by saying I'm VERY new to Ubuntu (v 14.04, I believe) so don't assume I know how to do pretty much anything. (LOL took me 15 minutes just to figure out how to find my tmp files.)

Last night I was watching a video on VLC media player. It worked just fine. I paused the video and started it again this morning, and now there's no sound.  I've tested several different videos, so it's not that particular video itself. I then tried the sound on whatever the standard media player is that came with Ubuntu. No sound there either.

However sound works just fine with streaming video on the web (hulu and youtube).

I've checked that Ubuntu recongnizes my video card - it does:

   **** List of PLAYBACK Hardware Devices **** 
 card 0: SB [HDA ATI SB], device 0: ALC887-VD Analog [ALC887-VD Analog] 
   Subdevices: 1/1 
   Subdevice #0: subdevice #0 
 card 0: SB [HDA ATI SB], device 1: ALC887-VD Digital [ALC887-VD Digital] 
   Subdevices: 1/1 
   Subdevice #0: subdevice #0 
 card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0] 
   Subdevices: 1/1 
   Subdevice #0: subdevice #0 
 

 Sound cards recognized by the system: 
 00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) [1002:4383] (rev 40) 
 01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Cedar HDMI Audio [Radeon HD 5400/6300 Series] [1002:aa68] 
 Sound cards recognized by ALSA: 
 00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) [1002:4383] (rev 40) 
 01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Cedar HDMI Audio [Radeon HD 5400/6300 Series] [1002:aa68] 
 Sound cards recognized by ALSA, and activated: 
 00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) [1002:4383] (rev 40) 
 01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Cedar HDMI Audio [Radeon HD 5400/6300 Series] [1002:aa68] 

I purged and reinstalled pulseaudio. No luck there.

I uninstalled and reinstalled VLC. No luck there.

Rebooting doesn't help either.

I tried using the sticky thread to troubleshoot, but got entirely lost. Also I couldn't find "procedure Ba" which seemed to be relevant.

Possibly related - Quite often when the computer sleeps, it freezes and I have to reboot to get it working again. (I haven't yet figured out how to fix this.) Also when Ubuntu boots, it tells me there are several errors. They zip past so fast that I can't read them, so if there's a way of capturing that info, it might help also. Notably, the system did NOT freeze in between the video sound working and it no longer working.

Thanks much for your help.

---

### Post by lion3 on 2015-04-16
Forgot to mention this is a dual system. Videos work just fine in Windows.

---

### Post by user_of_gnomes on 2015-04-16
Type [less /var/log/boot.log]("http://www.cyberciti.biz/faq/ubuntu-view-boot-log/") and see if you can find the errors you're speaking of.

---

### Post by lion3 on 2015-04-18
Yesterday when I booted, I didn't see any errors, but today there are some showing - and maybe this is weird, but yesterday's boot log was much longer.  Anyway, from just now:

ModemManager[715]: <info>  ModemManager (version 1.0.0) starting... 
  
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox 
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd 
 * Starting AppArmor profiles       [200G  [194G[ OK ] 
 * Setting sensors limits       [200G  [194G[ OK ] 
 * Setting up X socket directories...       [200G  [194G[ OK ] 
 * speech-dispatcher disabled; edit /etc/default/speech-dispatcher 
saned disabled; edit /etc/default/saned 
 * Restoring resolver state...       [200G  [194G[ OK ]

I note the "speech dispatcher" thing - could that be the problem?

---

### Post by user_of_gnomes on 2015-04-18
You can prevent it from starting up with the system by typing sudo update-rc.d -f speech-dispatcher remove, see if that makes a difference.

What device is your audio equipment hooked up to? Do you have any HDMI equipment?

---

### Post by Yellow Pasque on 2015-04-20
> I purged and reinstalled pulseaudio. No luck there.
If you purge a package, the user configuration will still remain.  Try this to delete the pulseaudio user config and generate fresh config files:
```
rm -r ~/.config/pulse*
```
Then log out/in.

---

### Post by lion3 on 2015-04-21
Woot! The last one worked. Thank you both!!!!!

---

### Post by lion3 on 2015-04-21
Oh and for the record, my only device was a headset.

---

