---
title: "Hauppage WinTV-HVR 950Q Analog"
date: 2009-11-28
forum: Multimedia Software
---

### Post by iaguy2 on 2009-11-28
Trying to get analog signal on my 950q.  I'm running an upgraded 9.10 ubuntu.  I was able to capture digital cable to MPG's with mencoder and it looks good.  When I try analog on the tv or composite input I get a flicker.  This happens on players tvtime, vlc, mplayer.  I assume that it is the driver?  

Any suggestions would be appreciated.

---

### Post by glennric on 2009-12-08
How did you get tvtime and vlc to work at all?  I can play video with these programs, but can't seem to get sound.

I just figured out how to get mplayer to play analog input from composite video, although the sound and video do not match up that well.  The following did the trick:
```
mplayer -tv driver=v4l2:input=1:device=/dev/video1:norm=NTSC:chanlist=us-bcast:channel=3:alsa=1:adevice=hw.2:audiorate=48000:immediatemode=0:amode=1 tv://1
```
Of course you will have to change your video device and alsa device appropriately.

---

### Post by fogNL on 2009-12-08
I'm after trying everything with this card, I can't seem to get analog working with it at all.

---

### Post by glennric on 2009-12-08
Ok, I finally got vlc to work.  It was really the new format for alsa devices that was throwing me.  Why can't mplayer and vlc pick a command line format and stick with it.  They change their formats every release.  It is really annoying.

Anyway the vlc command that worked for me is:
```
cvlc v4l2:///dev/video1  --input-slave alsa://hw:2 --v4l2-standard 3 --v4l2-input 1 --v4l2-caching 300
```

I should point out that I am using the composite input for these commands, hence the option "--v4l2-input 1". If you are using the cable-tv input you won't need that option.  You will also need to change your sound device from alsa://hw:2 to whatever your device number is on your computer.

---

### Post by fogNL on 2009-12-09
I actually had a little more success after my previous post.  I stumbled across an app called "ktv" ([http://jerous.thimhallan.org/ktv/](http://jerous.thimhallan.org/ktv/)) that is a 'front-end' for mplayer to play tv.

The options i used to get it working were:

> channel-list=us-cable
video-device=/dev/video0
Norm=ntsc
Audio device= hw.1
Additional tv arguments:  audiorate=48000:immediatemode=0:amode=1
Additional arguments:  -vf pp=lb -cache 6144

The channel scanning does not work, as far as I can tell from the source code, it uses mplayer's -tvscan option, which I can't get going manually anyways.  It always says it can't detect a signal, even if i set the threshold to 1.  I think i remember hearing about this issue before.  I can create a stationlist.xml using tvtime, but have no idea how to import it.  I've sent the author an email for ideas.

---

### Post by nacho32 on 2009-12-09
I had that same card and returned it because I thought it ran to hot and the remote looked like it came out of a gum-ball machine Then it fried after 4 days of purchase, Xp-windows 7 wintv7 freeze .Under ubuntu 9.10 I found Kaffeine to be my favourite on my new hauppauge 1600 model 1199 this card preforms so much better, no crash no heat issues faster channel render. just my 2 cents

---

### Post by glennric on 2009-12-09
So now I have mplayer and vlc working with sound and video (as mentioned above), but I have the flicker problem mentioned by iaguy2 in the initial post from this thread.  Any ideas on how to resolve this?  I also still have not managed to get sound to work with tvtime.

---

### Post by fogNL on 2009-12-09
> **glennric said:**
> So now I have mplayer and vlc working with sound and video (as mentioned above), but I have the flicker problem mentioned by iaguy2 in the initial post from this thread.  Any ideas on how to resolve this?  I also still have not managed to get sound to work with tvtime.

You won't get sound working with tvtime alone.  This is due to the fact that TVtime renders sound differently.  TVtime was designed to get sound from a dedicated cable connected to the sound card, which obviously these USB devices do not have.  The only way TVtime will get sound is by running aplay or sox in the background to pipe the audio.  Each time I have tried this method, the sound has been out of sync with video.  There was one sox command i found last night that supposivly gave it no-lag audio, but I can't find it here now cause i'm at work.  When I get home, i'll check my .bash_history and edit the post.  The command didn't work for me because it said /dev/dsp was in use, which is probably due to PulseAudio.

---

### Post by glennric on 2009-12-09
Yeah, I am not sure it is worth it to get tvtime working.  I am not sure it is worth it to keep this device.  I am thinking that Nacho32 may be right.  Even in Windows 7 this device seems to get crappy video.  I think it was better yesterday, but today it seems to get choppy video from the composite input.  Also in linux I have to keep using modprobe to remove the kernel modules every once in a while or I don't get any sound or video at all.  It is possible that the linux drivers are corrupting the device.

---

### Post by glennric on 2009-12-09
Ah ha.  It turns out that it was my front panel usb port that was causing all of my problems.  I tried a back panel usb port and got much better video, and the problems that were occurring that were making me have to remove the kernel modules every once in a while stopped.

---

### Post by markackerman8@gmail.com on 2010-04-15
Hello everyone,

I am exhausting my search for a solution to watch and record analog cable tv with my HVR-950Q, I have tried everything (I hope not actually), including 
MythTV, 
MythBuntu, 
XBMC w MythTV, 
XBMC w tvheadenf, 
Kaffeine, 
vlc.......

........please a functional pvr media center for linux???? :confused:

---

### Post by WinterRain on 2010-04-15
You should maybe think about buying a linux compatible tv tuner card. The Hauppauge HVR 1600 works well. Or any of the Hauppauge PVR series. (150/250/350) Good luck.

---

### Post by markackerman8@gmail.com on 2010-04-19
Well Winterrain,I took your advice, and was able to find a second hand winTV-PVR-USB2 (ONLY ANALOG SUPPORT - HEH PERFECT FOR ME), AND after 5-10 "hoops" over 2 days it is working, and with MythTV - coool!

Not giving up on my HVR-950Q, or pcmcia hvr1500Q for analog and MythTV....
.... IF anyone gets either of these to work , PLEASE let me know!

Thanks in advance and Iwill monitor for another year..haha!

---

### Post by mlord on 2010-11-16
There's a trick (or several) to getting analog audio from the HVR-950Q in MythTV, probably required due to bugs in the latter.

The rest of this post assumes you have already figured out how to get the video part of analog recordings to work *(720x480 in all profiles, 48000 audio, RTJPEG at max quality, and create a single recording group to hold both the analog and digital halves of the 950Q)*.

MythTV seems to only work properly with audio recording when the OSS ("Open Sound System") audio driver interface is used.  It fails miserably and randomly when attempting to use the newer ALSA ("Advanced Linux Sound Architecture") driver interfaces.

So.. if your distro provides /dev/dsp1 (from OSS), then use that as the audio input device when configuring the HVR-950Q as a capture card.

If it does not provide it, then do **modprobe snd-pcm-oss** and check for /dev/dsp* again.  If the **modprobe** command fails, then you will have to reconfigure/rebuild the Linux kernel to get that missing feature.

The **snd-pcm-oss** module is simply a glue layer, so that old-style OSS interfaces can be used (by MythTV) with the newer ALSA drivers underneath.  This is the only method I've found that works for analog audio capture from the 950Q in MythTV.  Other apps work fine, of course.

Cheers

---

