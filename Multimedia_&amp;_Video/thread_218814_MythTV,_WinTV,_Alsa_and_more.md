---
title: "MythTV, WinTV, Alsa and more"
date: 2006-07-19
forum: Multimedia &amp; Video
---

### Post by ubtpenguin on 2006-07-19
It was enjoyable two weeks with MythTV with lots of pain.

Bottom line. It works. Yeah sort of.

However I start this thread since I believe this may help somebody and solve my minor problems too. 

I.System Specification
CPU: Pentium 4 3.2GHz
Video: Geforce 6600GT
Sound: AC97' From ATI chipset.
TV Tuner: WinTV (I don't know exact model since I got only the Tuner board from my friend but it is using bt878 and it has FM radio) 

II.Sound Setup
	my esd is on since I figured out the it doesn't matter if esd is on or not
	I didn't change any sound set up from dapper upgrade except libesd-alsa0 installation

Devices detected
From volume control on desktop I could see three difference audio devices
ATI IXP (alsa mixer)
Brooktree BT878 (alsa mixer)
Realtek ALC650F (OSS mixer)

Connection 
Audio Cable is connected from Line-out of TV tuner to Line-in of On-board sound card
Note: I heard that BT878 has it's own sound chip so I don't need to connect line out to line -in but if I disconnect it I can not hear any sound. Do you guys know the reason? 	 
III.MythTV installation
Package installation was done by synaptic package manager. Other setting was followed pretty much by other well known how-tos.
In mythfronend, I set audio output device as ALSA:default and mixer as default.
 
IV.Result
It is recording and playing live TV.

V.Problems
At first, I thought there was feedback problem since sound was static and I wasted almost one week to figure out. I figured out some solution while I was playing around on ATI IXP from mixer.  Capture tap on mixer has Line-in,  CD, Microphone, and Capture. Capture was in sync with mythTV video and Line-in was not. And interestingly, when MythTV frontend starts, it turns both Line-in and Capture and when frontend exits, it leaves Line-in on. Therefore I could hear TV sound even after I exit from MythTV. Furthermore when I use TVtime to watch TV, It only uses Line-in and it turns on and off as it starts and exits.
I came to conclusion that MythTV is not using Line-in at all to record TV. That make sense, even if I muted Line-in, I could watch both live and recorded TV. Now this is the mystery. If then, it should still work fine if I disconnect cable from line-in. However, as soon as I disconnect line-in cable, I lose audio. What on earth is happening hear. Capture and Line-in was actually the same thing? Then logical conclusion is Line-in audio comes first and capture audio follows and makes audio static. And why mythTV does not turn off line-in?? 
I heard stories about audio and video is not in sync. if you have a trouble, some of you may have a simple problem like this. MythTV turns on both Line-in and Capture and Line-in goes to speaker and capture captures audio and send it back to speaker that makes audio static or if you muted capture, you would get asynchronous sound watching Live TV and no sound on recording.
I have other minor video problems but I am still digging up, I might have to update document again later.
Please share your thoughts. Thank you guys

](*,)

---

### Post by ubtpenguin on 2006-07-19
Okay this is my little bit of update

Sound problem is somewhat solved.

In mythtv-setup, I chose sound device as /dev/dsp1. previously, it was /dev/dsp.

I realized that snd_bt87x module created dsp1. and dsp is oss driver for my on-board sound card.

I can now record and watch TV without line-in cable.

But I still don't know how to use alsa capture devices.

/dev/dsp1 is still oss driver for bt87x. I can control audio input volume by using oss mixer in volume control. bt878 alsa mixer doesn't do anything.

I checked device manager and I found out that bt878 audio created /dev/snd/pcmC1D1c and /dev/snd/pcmC1D0c devices (and I believe these are controlled by alsamixer) if I remember correctly.

How can I use this devices in mythTV? 

Still digging up

P.S.

Something is wrong with the forum, I can not log in easily.

---

### Post by ubtpenguin on 2006-07-20
Another problem I met is BadMatch X error.

But I figured out that nVidia is not supporting overlay anymore.

If you guys get this error but mythTV still works fine, I believe you can ignore it.

By the way, I didn't know I was using mythTV 0.18.1 version in ubuntu. It is more than a year old version. 

No wonder there was compatibility issue with mySQL 5.0 regard of mythfilldatabase.

I decide to build from the source with latest bug fix release 0.19.1. 

I believe I am going to be busy this weekend.

---

### Post by tbonius on 2006-08-29
Which Capture card are you using?  Are you able to successfully use /dev/dsp1 as a digital audio capture device without runing cables out of your capture card and into your sound card?  When I attempt this I get ssslllooowwww (mis-sampled) audio.  I finally found that the analog in device created by snd_bt87x is /dev/adsp1.. but I cannot get any sound out of it when I attempt to grab audio from the device.  Any recommendations?

---

### Post by HiFiJive on 2007-09-05
ubtpenguin: You have a very similar setup as me. I have 1.6 intel dualcore with onboard sound, nvidia 6200 / 2gb 800mhz ram / WinTV NTSC tuner with fm radio. Ubuntu Feisty installs it as bt878. 

My question do you think you could somewhat explain how you go mythtv working? I was able to get tvtime to display correctly. But when I run through the Myth backend setup it does not work. Was there any specific tweaks you had to install?

video: /dev/video0  *(i did ln -s /dev/video0 /dev/video)

I have dish tv and would love to have this record my programs. any help would be GREATLY appreciated. :mrgreen:

---

