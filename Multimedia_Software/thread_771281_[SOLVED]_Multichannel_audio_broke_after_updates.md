---
title: "[SOLVED] Multichannel audio broke after updates"
date: 2008-04-27
forum: Multimedia Software
---

### Post by volkswagner on 2008-04-27
I am running mythbuntu 7.10AMD64.  I had working spdif passthrough prior to updates included with mythtv .21.  I have tried several changes.  I went through comprehensive sound guide.  Uninstalled and reinstalled alsa, etc.  I when I enable passthrough in VLC and Mythtv I get no sound from multi channel media.  No sound in DVD's unless I select no passthrough or 2ch max.

If I try to play multichannel audio without passthrough enabled, I get "WriteAudio: buffer underrun" errors every half second or so. 

I am using onboard sound. Gigabyte GA-MA69GM-S2H with Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller, Audio device: ATI Technologies Inc SBx00 Azalia. 

```
List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 0: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0 
``` 

```

aplay -L
front:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, ALC882 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
iec958:CARD=HDMI,DEV=0
    HDA ATI HDMI
    IEC958 (S/PDIF) Digital Audio Output 
```

Here is a portion of amixer -c0 contents , I am not sure what all the numbers mean. When I had the 5.1 working, passthrough device in myth was listed as "ALSA:iec958:(AESO 0x02)". I have tried other combinations here but not all. 

```
numid=27,iface=MIXER,name='IEC958 Playback Con Mask'
  ; type=IEC958,access=r-------,values=1
  : values=[AES0=0x0f AES1=0xff AES2=0x00 AES3=0x00]
numid=28,iface=MIXER,name='IEC958 Playback Pro Mask'
  ; type=IEC958,access=r-------,values=1
  : values=[AES0=0x0f AES1=0x00 AES2=0x00 AES3=0x00]
numid=29,iface=MIXER,name='IEC958 Playback Default'
  ; type=IEC958,access=rw------,values=1
  : values=[AES0=0x04 AES1=0x82 AES2=0x00 AES3=0x02]
numid=30,iface=MIXER,name='IEC958 Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=32,iface=MIXER,name='IEC958 Capture Default'
  ; type=IEC958,access=r-------,values=1
  : values=[AES0=0x04 AES1=0x00 AES2=0x00 AES3=0x00]
numid=31,iface=MIXER,name='IEC958 Capture Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=off 
```

frontend.log while playing 2ch recording.
```

2008-04-27 15:02:27.960 TV: Attempting to change from None to WatchingPreRecorded
2008-04-27 15:02:28.179 AFD: Opened codec 0x985e8e0, id(MPEG2VIDEO) type(Video)
2008-04-27 15:02:28.179 AFD: codec MP2 has 2 channels
2008-04-27 15:02:28.179 AFD: Opened codec 0x1bb1bc0, id(MP2) type(Audio)
2008-04-27 15:02:28.180 Opening audio device 'default'. ch 6(2) sr 48000
2008-04-27 15:02:28.180 Opening ALSA audio device 'default'.
2008-04-27 15:02:28.197 Mixer unable to find control Master
2008-04-27 15:02:28.197 Mixer unable to find control Master 
```

Here is log when playing AC3 recording via firewire

```
2008-04-27 15:10:07.211 TV: Attempting to change from None to WatchingPreRecorded
2008-04-27 15:10:07.618 AFD: Opened codec 0x98ff070, id(MPEG2VIDEO) type(Video)
2008-04-27 15:10:07.618 AFD: codec AC3 has 6 channels
No accelerated IMDCT transform found
2008-04-27 15:10:07.618 AFD: Opened codec 0x985e8e0, id(AC3) type(Audio)
2008-04-27 15:10:07.619 Opening audio device 'default'. ch 6(2) sr 48000
2008-04-27 15:10:07.619 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2008-04-27 15:10:07.620 AudioOutput Error: Channels count (6) not available: Invalid argument
2008-04-27 15:10:07.620 AudioOutput Error: Unable to set ALSA parameters
2008-04-27 15:10:07.631 NVP: Disabling Audio, reason is: Unable to set ALSA parameters 
```

Here is what I get when playing a 5.1DVD.
```

2008-04-27 15:18:52.437 AFD: Opened codec 0x24e7bb0, id(MPEG2VIDEO) type(Video)
2008-04-27 15:18:52.437 NVP: Disabling Audio, params(-1,-1,-1)
2008-04-27 15:18:52.437 NVP: Disabling Audio, params(0,-1,-1)
libGL error: drmGetMagic failed
libGL error: reverting to (slow) indirect rendering
2008-04-27 15:18:52.561 Failed to approve 'opengllinearblend' deinterlacer
2008-04-27 15:18:52.561 Couldn't load deinterlace filter
2008-04-27 15:18:52.562 OSD Theme Dimensions W: 640 H: 480
2008-04-27 15:18:52.732 TV: Changing from None to WatchingPreRecorded
2008-04-27 15:18:52.870 OpenGLVideoSync()
2008-04-27 15:18:52.870 ~OpenGLVideoSync() -- begin
2008-04-27 15:18:52.870 ~OpenGLVideoSync() -- middle
2008-04-27 15:18:52.870 ~OpenGLVideoSync() -- end
2008-04-27 15:18:52.870 Video timing method: USleep with busy wait
2008-04-27 15:18:52.919 AFD: Warning, video codec 0x24e7bb0 id(MPEG2VIDEO) type (Video) already open.
2008-04-27 15:18:52.994 AFD: codec AC3 has 0 channels
No accelerated IMDCT transform found
2008-04-27 15:18:52.995 AFD: Opened codec 0xa4ecde0, id(AC3) type(Audio)
2008-04-27 15:18:52.995 Opening audio device 'default'. ch 6(2) sr 48000
2008-04-27 15:18:52.996 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2008-04-27 15:18:52.996 AudioOutput Error: Channels count (6) not available: Invalid argument
2008-04-27 15:18:52.997 AudioOutput Error: Unable to set ALSA parameters
2008-04-27 15:18:53.004 NVP: Disabling Audio, reason is: Unable to set ALSA parameters
2008-04-27 15:19:13.058 NVP: Disabling Audio, params(-1,-1,-1)
2008-04-27 15:19:13.094 NVP: prebuffering pause
2008-04-27 15:19:13.157 NVP: Disabling Audio, params(0,-1,-1)
2008-04-27 15:19:13.169 AFD: Warning, video codec 0x24e7bb0 id(MPEG2VIDEO) type (Video) already open.
2008-04-27 15:19:13.193 NVP: prebuffering pause
2008-04-27 15:19:13.251 AFD: codec AC3 has 0 channels
No accelerated IMDCT transform found
2008-04-27 15:19:13.252 AFD: Opened codec 0x2aaacd03cb70, id(AC3) type(Audio)
2008-04-27 15:19:13.252 Opening audio device 'default'. ch 6(2) sr 48000
2008-04-27 15:19:13.252 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2008-04-27 15:19:13.253 AudioOutput Error: Channels count (6) not available: Invalid argument
2008-04-27 15:19:13.253 AudioOutput Error: Unable to set ALSA parameters
2008-04-27 15:19:13.261 NVP: Disabling Audio, reason is: Unable to set ALSA parameters
2008-04-27 15:19:50.343 NVP: Disabling Audio, params(-1,-1,-1)
2008-04-27 15:19:50.383 NVP: prebuffering pause
2008-04-27 15:19:50.438 NVP: Disabling Audio, params(0,-1,-1)
2008-04-27 15:19:50.446 AFD: Warning, video codec 0x24e7bb0 id(MPEG2VIDEO) type (Video) already open.
2008-04-27 15:19:50.510 AFD: codec AC3 has 0 channels
No accelerated IMDCT transform found
2008-04-27 15:19:50.510 AFD: Opened codec 0x2aaacd2c3aa0, id(AC3) type(Audio)
2008-04-27 15:19:50.512 Opening audio device 'default'. ch 6(2) sr 48000
2008-04-27 15:19:50.512 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2008-04-27 15:19:50.513 AudioOutput Error: Channels count (6) not available: Invalid argument
2008-04-27 15:19:50.513 AudioOutput Error: Unable to set ALSA parameters
2008-04-27 15:19:50.519 NVP: Disabling Audio, reason is: Unable to set ALSA parameters
```

---

### Post by volkswagner on 2008-04-28
Bump....Anyone, any ideas?  I am really banging my head.  I have months of configuration on these systems and my wife is ready to kill me.  If I have to start over, surely it will be alone in my new apartment!  :lolflag:

---

### Post by volkswagner on 2008-04-29
Ok digging deep.  This is way over my head. 

According to my mobo spec at newegg, my onboard audio is Audio Chipset  	 Realtek ALC889A.

According to
```

 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


This is not what I get when...
```

 head -n 1 /proc/asound/card0/codec*
Codec: Realtek ALC885
```

Should these match?

From the following command I find no choice for ALC889A

```

zless /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz
```

 ```
ALC882/885
          3stack-dig    3-jack with SPDIF I/O
          6stack-dig    6-jack digital with SPDIF I/O
          arima         Arima W820Di1
          macpro        MacPro support
          w2jc          ASUS W2JC
          auto          auto-config reading BIOS (default)

        ALC883/888
          3stack-dig    3-jack with SPDIF I/O
          6stack-dig    6-jack digital with SPDIF I/O
          3stack-6ch    3-jack 6-channel
          3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
```

Followed this thread.

[http://ubuntuforums.org/showthread.php?t=588089&highlight=digital+sound]("http://ubuntuforums.org/showthread.php?t=588089&highlight=digital+sound")

I tried adding each of the following lines, reboot, none worked.

options snd-HDA-ATI model=6stack-dig
options snd-hda-intel model=6stack-dig
options snd-HDA-ATI-SB model=6stack-dig

 ```
cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe024000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfdffc000 irq 19
```

Still getting these errors.

 ```
AFD: Opened codec 0x1e391b0, id(AC3) type(Audio)
2008-04-29 18:06:47.482 Opening audio device 'default'. ch 6(2) sr 48000
2008-04-29 18:06:47.482 Opening ALSA audio device 'iec958:{AES0 0x02}'.
2008-04-29 18:06:47.523 AudioOutput Error: Channels count (6) not available: Invalid argument
2008-04-29 18:06:47.523 AudioOutput Error: Unable to set ALSA parameters
2008-04-29 18:06:47.528 NVP: Disabling Audio, reason is: Unable to set ALSA parameters

```

I think I need additional arguments in .asoundrc, the following used to work, but what can I add to give multi channel argument?


.asoundrc

```
pcm.!default {
        type plug
        slave {
                rate 48000
                pcm "spdif"
                format S16_LE
        }
}

```

---

### Post by volkswagner on 2008-04-30
Still no joy.  Does this mean anything.  Following advice on this thread.

[http://ubuntuforums.org/showthread.php?t=575653]("http://ubuntuforums.org/showthread.php?t=575653")



```
eric@FamilyRoom:~$ sudo m-a prepare
Getting source for kernel version: 2.6.22-14-generic
Kernel headers available in /usr/src/linux
Creating symlink...
Couldn't create the /usr/src/linux symlink!
apt-get install build-essential
```

---

### Post by volkswagner on 2008-05-04
Still plugging away at this.  Maybe someone can chime in here.  I am trying to get this to work in mplayer.  

Mplayer preferences= Audio>ALSA-0.9x-1.x audio output
                     >device hw=0,1
                     >mixer default
                     >mixer_channel Master
When I play a DVD with these settings I get two warnings
```

error opening/initializing the selected video_out (-vo) device.

[AO_ALSA] alsa-lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM hw:0,1,AESO=6
```

I click ok for each warning.  I loose picture, but I get dolby digital out to my receiver.  :)

Please tell me I am getting somewhere.  I feel I have messed with ALSA so much now it may be a problem.  I have followed the comprehensive guide to remove and reinstall but no luck.  Is my version of mplayer dated.  I just reinstalled it via synaptic because it was borked.  Reason I ask it seems it is set up for alsa pre-version .1.0.4.

Also within Mplayer I notice the following.  If I try to play the DVD directly from the menu I get the following.


OK, I messed with the video settings.  
When I select xv, I get the above scenario.

When I have any of the following, X11, gl, gl2, xvidix, I get the following.

```
Waring MVs not available
```

I do however get dolby sound out of spdif and video.  :)
Now it is back to mythtv.  Maybe someone can help sort out the above.

Also when I close Mplayer after using the few working video profiles, I get a Gnome screen saver warning.

---

### Post by volkswagner on 2008-08-03
Finally got it sorted.  See my last post here.

[http://ubuntuforums.org/showthread.php?p=5516332#post5516332]("http://ubuntuforums.org/showthread.php?p=5516332#post5516332")

---

