---
title: "Ubuntu 8.04 Sound Problem"
date: 2008-06-17
forum: Multimedia Software
---

### Post by blaze_d on 2008-06-17
Well, here is my problem: after upgrading from 7.10 to 8.04 my sound is ... well, awfull. it sounds like scrached CD in old CD player. The fun part is, it's only with the audio files, don't have the problem with video files. Soundcard is Realtek integrated in MB Gigabyte M61SME-S2L. Can anyone help?
P.S. Sorry for the bad english... :oops:

---

### Post by ajgreeny on 2008-06-17
Which sound server are you using, pulse or alsa?  Go to System>>Preferences>>Sound and see what the five drop down boxes show.  Pulse is good, but I know some people are having problems with it, though not usually of the sort you mention.

---

### Post by blaze_d on 2008-06-17
Well, it doesn't matter wich one i am using, because it's the same on both - just tryed. Any other ideas?

---

### Post by Yellow Pasque on 2008-06-17
Try OSS4 (link in signature).

---

### Post by gramnemo on 2008-06-17
> **Temüjin said:**
> Try OSS4 (link in signature).


 Thanks !

---

### Post by blaze_d on 2008-06-17
well, tryed but ... it's now without any sound. Time to go big! Time to try Debian ...

---

### Post by markbuntu on 2008-06-17
Try this, it will get you back to a pure alsa setup

1. Stop pulseaudio or oss or any other sound manager from loading at boot with Boot Up Manager (bum, available with Synaptic, you will find it in System/Administration/ after it installs). 

2. Put etc/asoundrc in the trash.

3. Edit etc/libao.conf to say: 

default_driver=alsa

4. Make sure alsa-utils runs at boot (System/Admin../Services)

5. Check with Synaptic that these are all installed:

aconnectgui  (ALSA MIDI connection utility)
alsa-oss  (alsa wrapper for OSS apps)
alsaplayer-alsa  (PCM player for alsa)
alsa-utils  (command line utilities)
asoundconf-gtk  (choose default alsa sound card)
gnome-alsamixer (GUI alsa mixer for Gnome)
gstreamer0.10-alsa (gstreamer plugin)
xmms2-plugin-alsa (xmms2 plugin)
libasound2-plugins (jack, OSS, pulseaudio)
libesd-alsa0 Enlightened Sound Demon (allows  multiple audio streams on one device)

6. System/Preferences/Default Sound Card, choose the sound card hardware. 

7. Sys../Pref.../Mutimedia Systems Selector/Audio, set plugin to alsa and Device to Default for both input and output.

8. Sys../Pref.../Sound, set all to ALSA. Default mixer tracks to "your sound card" (i.e. ATI IXP, Realtec, etc) (Alsa )mixer).

9. Reboot. If you are having trouble changing settings in Multimedia Systems Selector or Sound, reboot and then make the changes.

10. Open alsamixer, alsamixergui, or gnome-alsamixer, to configure the mixer. Turn stuff on and put up the sliders. check mix, capture, cd, mic, etc, unmute, mute, blah blah blah... If you have a usb mic or headphones turn them on and test them in the gnome-alsa mixer USB section. Open the volume control and set it to master.

11. Test with Rythmbox, vlc, totem, xine, gstreamer, ekiga etc. configure all preferences to alsa if available/possible.

12. Test Sound Recorder. set capture/mix level, enable record, turn on mic, unmute, mute etc, etc... fool with mixer until it works right

good luck and let us know how this works out for you.

---

### Post by blaze_d on 2008-06-18
Okay, here's the result: no soundcard detected ;( I did almost everything (xmms2-plugin-alsa - not installed, 7. Sys../Pref.../Mutimedia Systems Selector/Audio - don't have anything like that in the menu). Set my Default SC to NVIDIA (well, it was only nvidia and pulse audio), made everything in Sounds to ALSA, puted the Device to NVIDIA again and after rebooting - no audio driver. Cannot start Deafult Sound Card. Some help, please?

---

### Post by blaze_d on 2008-06-18
Update:
```
tunay@ubuntu:~$ aplay -l
aplay: device_list:205: no soundcards found...
```
;(

---

### Post by blaze_d on 2008-06-18
Update: New installed ubuntu (got enough tryin' to fix the errors).  The same problem accured. But now it was after double installed ubuntu restricted modules. First - installed the nvidia VGA driver when ubuntu asked. Then i typed:
```

sudo apt-get install linux-restricted-modules-server

```
After that ubuntu asked for reboot. After the reboot - no sound cards ... Well i got really enough of it.
P.S. When booted from LiveCD, there is nothin' wrong with the sound, everything's perfect, but after installation - even login sound event is "cutted". Now I'm going to try without installing the code above...

---

### Post by snatchy on 2008-06-18
Hi can anyone help me?I have no sound in ubuntu 8.04 hardy 
Any one who knows how to fix it?


I have an acer aspire 6920
Mobile Intel ® PM965 Express Chipset 
card HDA intel
Chip:Realtek ALC889

---

### Post by blaze_d on 2008-06-18
@snatchy - look at the sticky's, i think there you can find ur problem
@ everyone, who tried to help me - THANK you ;) i tried lots of things, but in the end ... well, i just turned down the volume, arround 50-60% and it's ok now... i wonder why... whatever.
@modz & adminz - please, lock or remove ;)

---

