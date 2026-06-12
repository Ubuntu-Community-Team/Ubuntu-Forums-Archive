---
title: "No picture with pvr-150."
date: 2012-02-01
forum: Mythbuntu
---

### Post by robgue on 2012-02-01
Hi. Thanks for looking. I can't figure this one out. I've been happily using mythtv .24.x (mythbuntu repo) with my HDHomerun. I just added a Hauppauge pvr 150. It's recognized. Thought I installed it correctly. IVT in mythsetup. Using Schedules Direct. I can change channels from the command line and I'm assuming from FE. (see below)

When I try to view a channel in FE all I get is a black screen and no sound??
FE starts with one of the HDHOMERUN channels but when I change it to one of the analog pvr 150 channels I get nothing but the channel info from the pvr 150 and of course a black screen with no sound.

I can run mplayer /dev/video0 and I get the channel I changed it to using FE and of course video. I'm controlling a Directv D12-100 with a serial to usb adapter. Using the s-video output/input and rca audio to a 3.5 line in. Also hardware wise I'm using intel E8500, 8 gb ram and an onboard nvidia 9300 (VDPAU). Running Ubuntu 64 bit 11.10.

I've posted an abridged version of my logs here: [http://pastebin.com/fueARSpJ](http://pastebin.com/fueARSpJ)
If needed I can post more, run some commands, anything to get it going.
Again thanks for looking.;)

---

### Post by Moozillaaa on 2012-02-01
It's kind of hard to tell exactly what you DO have working here, besides that your card is properly recognized...

I use a Haup pvr 500 (same chip as your 150; only there's 2 tuners). Run these commands, and see what the return is:

```
sudo aptitude install scantv 

v4l2-ctl -i 0

ivtv-tune -c73

vlc pvr:// :pvr-device="/dev/video0" :pvr-radio-device="/dev/radio0" :pvr-norm=0 :pvr-frequency=-1 :pvr-bitrate=-1 

```-c73 = the channel output of my settop box (satellite receiver). Return for this command should be device / frequency / detection of signal

Last command opens up VLC with the audio + vids from the sat receiver...
***[COLOR=Red](ed.: the screenshot of my pc, with the screenshot of the signal is SATELLITE signal detection by the satellite receiver, NOT receiver detection by the Haup tuner)[/COLOR]***

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=211842&d=1328156646[/IMG]

---

### Post by robgue on 2012-02-01
here's the command line output:

```
laptop@ubuntu-server:~$ v4l2-ctl -i 0
Video input set to 0 (Tuner 1)
laptop@ubuntu-server:~$ ivtv-tune -c73
/dev/video0: 517.250 MHz
laptop@ubuntu-server:~$ vlc pvr:// :pvr-device="/dev/video0" :pvr-radio-device="/dev/radio0" :pvr-norm=0 :pvr-frequency=-1 :pvr-bitrate=-1
VLC media player 1.1.12 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x141f120] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to setlocale(6, "")

(process:13794): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
```


Vlc does not show anything. Just black sceen fuzz. I'm not using the coax tuner.
If I run "v4l2-ctl -i 1" and then the vlc command I do get the svideo video.

---

### Post by Moozillaaa on 2012-02-02
Is your set top box (or whatever device is feeding signal TO the Haup card, set to OUTput on channel 73 ???)

I ask, because the return for that particular command, as I said in my other post, should say **'Signal Detected'**. 

Re-read my post carefully. And also note what I posted on the screenshot.

Then, AFTER YOU DO THAT, check to see on what channel the signal is being outputted, on your device - the Directv D12-100, I presume.

Most devices output by default on channel 3.

So try to change the command syntax from -c73 to -c3 . Then, again, note what the return is for that command, as I noted in my other post...

---

### Post by robgue on 2012-02-02
Thank you for your help. It did not return (Signal Detected) with v4l2-ctl -i 0. 
If I run v4l2-ctl -i 1 it spits out the following.

```
laptop@ubuntu-server:~$ ivtv-tune -c73
/dev/video0: 517.250 MHz  (Signal Detected)
laptop@ubuntu-server:~$ ivtv-tune -c3
/dev/video0: 61.250 MHz  (Signal Detected)
```

I have not tried the coax tuner. Isn't ivtv-tune command for tuners? I'm using the s-video. Maybe I'm confused. The sat box is just on channel 7.

---

### Post by Moozillaaa on 2012-02-02
Sorry - I missed that you are bringing signal in on S-video. I don't know if this changes the appropriate syntax or not, or if ivtv-tune command is only for the coax input.

Since a signal IS now detected however, withOUT a coax input connected, I am guessing that the ivtv-tune command in NOT only for coax input, but also for S-video signal too.

So...

try again the vlc command, with the same values as before:
[HTML]vlc pvr:// :pvr-device="/dev/video0" :pvr-radio-device="/dev/radio0" :pvr-norm=0 :pvr-frequency=-1 :pvr-bitrate=-1[/HTML]

You did install scantv - correct?

---

### Post by robgue on 2012-02-02
Well there is a signal since it is receiving a feed. I already confirmed that. And if I run that above I do get video from the sat box. But that was fine before also. 
ivtv-tune is for the (coax) analog tuner not s-video. Think it was used for old analog cable.

---

### Post by Moozillaaa on 2012-02-02
I looked at your event log. I don't see where the problem is...

I suggest importing the signal into the coax input, instead of the S-video. If the coax is going to your tv already, then switch S-video -> TV, and coax -> computer / Haup card.

I've transcoded 600 videos through my Haup 500, and the recordings are equal quality to my satellite DVR recordings in standard definition, even when linked BACK to the TV.

In case you do do it that way, and you're recording the video into the computer, the additional syntax to record is:

[HTML]vlc pvr:// :pvr-device="/dev/video0" :pvr-radio-device="/dev/radio0"  :pvr-norm=0 :pvr-frequency=-1 :pvr-bitrate=-1 --sout  '#duplicate{dst=display,dst=std{access=file,mux=ts  ,dst="/home/robgue/Video_Title.mpg"}}'[/HTML]

---

### Post by robgue on 2012-02-02
I'd really would like to get the s-video going. Any other suggestions? Maybe anybody else have a similiar set-up?

---

### Post by Moozillaaa on 2012-02-03
Alright - 1 last observation here, and it might or might not apply to importing an S-video signal, and then again, it might bring to mind a factor to condsider.

You said that you could change channels by command line. Which channels? On which device? Keep in mind for a moment that 'channel' has different meanings, and here's what I mean in my case (I think yours is probably the same too (respective again to coax signals) ). Maybe you know this, maybe not. So lets call the 2 types of channels *viewing* channels, and *device* channels.

The satellite receiver OUTputs every different viewing channel (01 - 999) on 1 'device' channel (usually channel 3, or sometimes 4, **or**, when the D12-100 is like mine - a Dish network 625, with 2 different tuners for 2 televisions, the first tuner is on channel 3, and the second is on 73).

The **device** channel on the OUTputting device, AND on the INputting device must stay the same. Then and only then, can the **viewing** channel be changed, ON THE OUTPUTTING DEVICE.

So, maybe confirm that these factors apply to importing S-video signal, as well as to importing coax signal...

edit..........

---

