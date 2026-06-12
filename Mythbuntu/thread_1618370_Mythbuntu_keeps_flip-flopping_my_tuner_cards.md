---
title: "Mythbuntu keeps flip-flopping my tuner cards"
date: 2010-11-10
forum: Mythbuntu
---

### Post by kyphos on 2010-11-10
Brand-new Mythbuntu 10.04 install.
I have two tuner cards: a PVR-150 and an Asus 7135.
The system will not retain the configurations for these two cards.

Using the Capture Card section of backend setup, I first added the PVR-150, since it's the preferred device for recording video from my analog cable feed.
I specify Card type = IVTV MPEG-2.
Video device = /dev/video0
After many seconds, the Probed info field displays **Hauppauge WinTV PVR-150**.

Next, I added the Asus card.
Card type = Analog V4L capture card
Video Device = /dev/video1
Probed info displays **Asus TV-FM 7135 [saa7134]**
Parenthetically, I've learned (painfully) that I had to set Audio Device for this card to be /dev/dsp2.  Using the default that was offered (Alsa) doesn't result in any audio being captured.

After configuring the two cards, I then define the Video Sources, Connections, etc.
This resulted in a working MythTV system. I've recorded shows (two channels at one, played back recorded shows, watched LiveTV, etc).

But **sometimes** after a reboot, I find the two capture cards have changed their stripes and no longer function.
- The MPEG card (Tuner 1) is still shown at dev/video0, but Probed info = Asus.
- The Asus card (Tuner 2) is still at dev/video1, but Probed info = PVR-150.

I have to go through the entire backend config again. I've had to do this 5 times since installing 10.04 last week. This entails 'Deleting all capture cards' and starting over, as I don't know how to force the configure screen to change the probed information field so as to accurately depict the type of card. On occasion, I find if I change from /video0 to /video1, the IVTV card will then change from the Asus to the PVR-150 (and vice versa).  But this doesn't stick.

Don't know if this is relevant, but when selecting a card from the list of the two configured cards (the **Capture Card** screen), my display goes blank for 10 to 20 seconds before the **Capture Card Setup** screen for that card appears.  

What do I need to do to make my capture card configurations permanent?  

Thanks

---

### Post by tgm4883 on 2010-11-10
You will need to write some udev rules so they are always mapped to the same location 

[http://www.mythtv.org/wiki/Device_Filenames_and_udev](http://www.mythtv.org/wiki/Device_Filenames_and_udev)

---

### Post by kyphos on 2010-11-10
> **tgm4883 said:**
> You will need to write some udev rules so they are always mapped to the same location 

[http://www.mythtv.org/wiki/Device_Filenames_and_udev](http://www.mythtv.org/wiki/Device_Filenames_and_udev)

@tgm,
Thanks for the hint. I'll go educate myself on udev.

Is there anything particular about /video0 vs video1?   IE is the assignment between video* and a particular tuner card entirely arbitrary, or should I worry about any particular mapping?

Thanks.

---

### Post by tgm4883 on 2010-11-10
> **kyphos said:**
> @tgm,
Thanks for the hint. I'll go educate myself on udev.

Is there anything particular about /video0 vs video1?   IE is the assignment between video* and a particular tuner card entirely arbitrary, or should I worry about any particular mapping?

Thanks.

Basically the way it works is the rules detect the card based on some criteria when they are loaded. The issue right now is when you boot sometimes one loads first, sometimes the other loads first. With the udev rules, you would basically say, when the PVR-150 loads, map it to /dev/pvr150-1 (instead of /dev/video1). You will no longer bother with /dev/videoX. Then you would use /dev/pvr150-1 in mythtv instead. It won't matter what you call it in the end (/dev/pvr150-1, /dev/pvr, /dev/myfavoritetuner).

---

### Post by kyphos on 2010-11-10
@tgm,
Thanks for the info re naming video devices.  Your explanation sheds much needed light...

The udev wiki article you pointed me at is way over my head, but I will persevere and see if I can figure out how to write the required rules for my two tuners. I had hoped that the Mythbuntu package would make it relatively easy for a neophyte to get this all working - but a week later, I've learned that's not the case.

---

### Post by kyphos on 2010-11-10
@tgm,
If you're still following this thread, could I ask you a question about this udev stuff.

I followed the directions in the udev wiki article and used udevadm to probe my existing devices. I found four.
- video0 is my Asus saa7133 card.
- video1, video25 and video 33 all refer to the Hauppauge PVR-150. All of their attributes are the same except for ATTR{name}.  The first one is "ivtv0 encoder MPG". The second is "ivtv0 encoder PCM". The third is "ivtv0 encoder YUV".

Presumably, this means that the PVR-150 has three different types of encoders on-board?

Do I need to create udev rules for all three? I assume the important one (used by myth) is the MPG device.  Does Myth make use of the PCM and/or YUV devices or can I safely ignore them?

And what's the difference between MPG, PCM and YUV?  My guess:  the PCM device delivers the audio PCM stream.  And YUV is the analog (not MPEG-2 encoded) video stream. 

[http://encyclopedia2.thefreedictionary.com/YUV](http://encyclopedia2.thefreedictionary.com/YUV)

Thanks.

---

### Post by nickrout on 2010-11-10
> **kyphos said:**
> @tgm,
If you're still following this thread, could I ask you a question about this udev stuff.

I followed the directions in the udev wiki article and used udevadm to probe my existing devices. I found four.
- video0 is my Asus saa7133 card.
- video1, video25 and video 33 all refer to the Hauppauge PVR-150. All of their attributes are the same except for ATTR{name}.  The first one is "ivtv0 encoder MPG". The second is "ivtv0 encoder PCM". The third is "ivtv0 encoder YUV".

Presumably, this means that the PVR-150 has three different types of encoders on-board?

Do I need to create udev rules for all three? I assume the important one (used by myth) is the MPG device.  Does Myth make use of the PCM and/or YUV devices or can I safely ignore them?

And what's the difference between MPG, PCM and YUV?  My guess:  the PCM device delivers the audio PCM stream.  And YUV is the analog (not MPEG-2 encoded) video stream. 

[http://encyclopedia2.thefreedictionary.com/YUV](http://encyclopedia2.thefreedictionary.com/YUV)

Thanks.

No you don't need to create rules for each of those devices. If the mpeg encoder is /dev/videoN then the others will be automatically numbered relative to N.

There was a readme that came with driver before it got merged into the kernel proper, there seems to be a copy here:

[http://ivtvdriver.org/svn/ivtv/trunk/doc/README.devices](http://ivtvdriver.org/svn/ivtv/trunk/doc/README.devices)

---

### Post by AKADAP on 2010-11-11
I've never gotten udev rules to work properly.
I have /etc/udev/rules.d/video-devices.rules:
```
#An attempt to get fixed names for video devices
KERNEL=="video*", ATTR{name}=="cx88[0] video (ATI HDTV Wonder)", SYMLINK+="AnalogTuner"
KERNEL=="video*", ATTRS{idVendor}=="045e", ATTRS{idProduct}=="075d", SYMLINK+="WebCam"

```

Excerpts of relevant data:
```
$ udevadm info -a -p $(udevadm info -q path -n /dev/video1)

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1e.0/0000:07:01.0/video4linux/video1':
    KERNEL=="video1"
    SUBSYSTEM=="video4linux"
    DRIVER==""
    ATTR{name}=="cx88[0] video (ATI HDTV Wonder)"
    ATTR{index}=="0"

```
```
$ udevadm info -a -p $(udevadm info -q path -n /dev/video0)

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.3/2-1.3:1.0/video4linux/video0':
    KERNEL=="video0"
    SUBSYSTEM=="video4linux"
    DRIVER==""
    ATTR{index}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.3/2-1.3:1.0':
    KERNELS=="2-1.3:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="uvcvideo"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="01"
    ATTRS{bInterfaceClass}=="0e"
    ATTRS{bInterfaceSubClass}=="01"
    ATTRS{bInterfaceProtocol}=="00"
    ATTRS{modalias}=="usb:v045Ep075Dd0105dcEFdsc02dp01ic0Eisc01ip00"
    ATTRS{supports_autosuspend}=="1"
    ATTRS{iad_bFirstInterface}=="00"
    ATTRS{iad_bInterfaceCount}=="02"
    ATTRS{iad_bFunctionClass}=="0e"
    ATTRS{iad_bFunctionSubClass}=="03"
    ATTRS{iad_bFunctionProtocol}=="00"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.3':
    KERNELS=="2-1.3"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 4"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}=="500mA"
    ATTRS{urbnum}=="7047"
    ATTRS{idVendor}=="045e"
    ATTRS{idProduct}=="075d"
    ATTRS{bcdDevice}=="0105"
    ATTRS{bDeviceClass}=="ef"
    ATTRS{bDeviceSubClass}=="02"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="5"
    ATTRS{devpath}=="1.3"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Microsoft"

```
and the results:
```
$ ls /dev
autofs           dvd       fd0u1920  log                 null     ram15   sda       stdin   tty2   tty33  tty47  tty60    usbmon0  vcs4         WebCam
block            dvdrw     fd0u360   loop0               oldmem   ram2    sda1      stdout  tty20  tty34  tty48  tty61    usbmon1  vcs5         zero
bsg              ecryptfs  fd0u720   loop1               pktcdvd  ram3    sda2      tty     tty21  tty35  tty49  tty62    usbmon2  vcs6
btrfs-control    fb0       fd0u800   loop2               port     ram4    sda5      tty0    tty22  tty36  tty5   tty63    usbmon3  vcs7
bus              fd        fd0u820   loop3               ppp      ram5    sdb       tty1    tty23  tty37  tty50  tty7     usbmon4  vcsa
cdrom            fd0       fd0u830   loop4               psaux    ram6    sdc       tty10   tty24  tty38  tty51  tty8     usbmon5  vcsa1
cdrw             fd0u1040  full      loop5               ptmx     ram7    sg0       tty11   tty25  tty39  tty52  tty9     usbmon6  vcsa2
char             fd0u1120  fuse      loop6               pts      ram8    sg1       tty12   tty26  tty4   tty53  ttyS0    usbmon7  vcsa3
console          fd0u1440  fw0       loop7               ram0     ram9    sg2       tty13   tty27  tty40  tty54  ttyS1    usbmon8  vcsa4
core             fd0u1600  hidraw0   mapper              ram1     random  sg3       tty14   tty28  tty41  tty55  ttyS2    v4l      vcsa5
cpu              fd0u1680  hidraw1   mcelog              ram10    rfkill  shm       tty15   tty29  tty42  tty56  ttyS3    vbi0     vcsa6
cpu_dma_latency  fd0u1722  hidraw2   mem                 ram11    root    snapshot  tty16   tty3   tty43  tty57  uinput   vcs      vcsa7
disk             fd0u1743  hpet      net                 ram12    rtc     snd       tty17   tty30  tty44  tty58  urandom  vcs1     vga_arbiter
dri              fd0u1760  input     network_latency     ram13    rtc0    sr0       tty18   tty31  tty45  tty59  usb      vcs2     video0
dvb              fd0u1840  kmsg      network_throughput  ram14    scd0    stderr    tty19   tty32  tty46  tty6   usblp0   vcs3     video1

```

Note that while the "WebCam" link was created, the "AnalogTuner" was not.
This result manages to be 100% completely useless. While MythTV will allow one to specify an arbitrary device name, the one it needs "AnalogTuner" does not get created.
So far, I have yet to find any software that lets one specify an arbitrary device name for a web cam. So I can't even use the udev rule created link that worked.

---

### Post by nickrout on 2010-11-11
Take a careful look at the wiki entry pointed to. The problem may be in the spaces in the ATTR{name}. Try:

KERNEL=="video*", ATTR{name}=="cx88*", SYMLINK+="AnalogTuner"

Also the wiki suggests the first part should be KERNEL=="video[0-9]*" but I don't know if that will make a difference.

---

### Post by kyphos on 2010-11-11
@AKADAP,
I've been successful getting udev rules to uniquely specify my two video tuner cards (and am grateful to nickrout and tgm for showing me the way).

Here is an idea regarding your problems, with the caveat that I am a newcomer to Linux, and have all of 30 minutes experience with udev.

Re your Analog Tuner rule:
I read a posting yestreday that the udev pattern matching can be problematic when underscore characters are involved.  Perhaps the same is true when trying to match square brackets. Try changing your rule to:

ATTR{name}=="cx88*"
or perhaps
ATTR{name}=="*ATI HDTV Wonder)"

Either form should uniquely specify your ATI device. Try one of these alternative strings and see if the /AnalogTuner device gets created.

 

[FONT=Verdana][/FONT]

---

### Post by kyphos on 2010-11-11
> **nickrout said:**
> Take a careful look at the wiki entry pointed to. The problem may be in the spaces in the ATTR{name}. Try:

KERNEL=="video*", ATTR{name}=="cx88*", SYMLINK+="AnalogTuner"

Also the wiki suggests the first part should be KERNEL=="video[0-9]*" but I don't know if that will make a difference.

@nickrout,

We seem to have posted our previous suggestions simultaneously!

My rule for one of my video cards is:
KERNEL=="video*", ATTR{name}=="ivtv0 encoder MPG", SYMLINK+="video-PVR150"

It works, so I think this indicates that spaces are OK as part of the matching pattern. However, underscores, square brackets and such may be the source of the problem.

Note also that I did not use the **video[0-9]*** form,  just** video***. 
My rule would match things like video, videocrap, videokilledtheradiostar, etc.  Unlikely to occur, I think. However, the ATTR{name} element adds sufficient constraints such that I'm assured a unique match to the required interface on my PVR-150 tuner card.  The **video[0-9]*** pattern used in the wiki article is more precise, and requires a numeric digit to follow the word "video".

---

### Post by AKADAP on 2010-11-12
After reading that wiki and man udev I found this in man udev:
>        Most of the fields support a shell style pattern matching. The following pattern characters are supported:

       *
           Matches zero, or any number of characters.

       ?
           Matches any single character.

       []
           Matches any single character specified within the brackets. For example, the pattern string 'tty[SR]' would match either 'ttyS' or 'ttyR'. Ranges are also
           supported within this match with the '-' character. For example, to match on the range of all digits, the pattern [0-9] would be used. If the first character
           following the '[' is a '!', any characters not enclosed are matched.

It does not say anything about spaces, but the brackets are certainly going to be a problem. Since I want my match to be as unique as possible, and there are many devices supported by the cx88?? drivers, I changed my /etc/udev/rules.d/video-devices.rules file to contain the following:
```
#An attempt to get fixed names for video devices
KERNEL=="video*", ATTR{name}=="cx88?0??video?(ATI?HDTV?Wonder)", SYMLINK+="AnalogTuner"
KERNEL=="video*", ATTRS{idVendor}=="045e", ATTRS{idProduct}=="075d", SYMLINK+="WebCam"

```

This works, so half the problem is solved. Thanks to kyphos and nickrout for pointing out the error of my ways.

The other half, WebCam applications not allowing arbitrary device names, is still a problem. It is especially a problem with the microphone since randomly the system switches between the webcam microphone and the sound card for sound input. It is really annoying to both parties to make a call with Skype and the other party can't hear you.

---

### Post by kyphos on 2010-11-12
@AKADAP,
Re your webcam rule that doesn't work:
I may be way off base, but I think the ATTRS parameters you are matching on ( the vendor and product IDs)   come from the parent device (i.e. the USB hub and/or controller) that is upstream from your USB webcam. It seems odd that there are no device-specific parameters pertaining to your webcam in the device portion of the data retrieved by udevadm.

Your webcam was plugged in when you did the udevadm scan, right?

So if your webcam is devoid of identifying information, you might be able to lock down a symlink by matching to the physical USB port it's plugged in to. I believe the port identification is hiding somewhere in the string of digits describing the first parent device:  usb2/2-1/2-1.3/2-1.3:1.0.

If so, perhaps you can match to the KERNELS string.
KERNELS=="2-1.3:1.0"
You could experiment with udevadm to see if you can reverse engineer the numbering plan for your USB ports. Plug your webcam into various ports and try to deduce a pattern to use for the udev matching.  Then just make sure your webcam is always plugged into the same USB port.

This is entirely conjecture on my part. (I only just learned about udev a couple days ago). If you make any headway, please post back and let us know if it works.

---

### Post by AKADAP on 2010-11-13
> **kyphos said:**
> @AKADAP,
Re your webcam rule that doesn't work:
I may be way off base, but I think the ATTRS parameters you are matching on ( the vendor and product IDs)   come from the parent device (i.e. the USB hub and/or controller) that is upstream from your USB webcam. It seems odd that there are no device-specific parameters pertaining to your webcam in the device portion of the data retrieved by udevadm.

Your webcam was plugged in when you did the udevadm scan, right?

So if your webcam is devoid of identifying information, you might be able to lock down a symlink by matching to the physical USB port it's plugged in to. I believe the port identification is hiding somewhere in the string of digits describing the first parent device:  usb2/2-1/2-1.3/2-1.3:1.0.

If so, perhaps you can match to the KERNELS string.
KERNELS=="2-1.3:1.0"
You could experiment with udevadm to see if you can reverse engineer the numbering plan for your USB ports. Plug your webcam into various ports and try to deduce a pattern to use for the udev matching.  Then just make sure your webcam is always plugged into the same USB port.

This is entirely conjecture on my part. (I only just learned about udev a couple days ago). If you make any headway, please post back and let us know if it works.

I'm afraid you misunderstood the issue. The udev rule for the web cam works fine, and the "WebCam" link gets created without any trouble.

The problem is that no application that uses web cams allows you to enter arbitrary device names, and will only allow you to select from a list that does not contain the WebCam link that is created by udev rules.

Also, the System->Preferences->Sound application that allows you to select the audio device used by the system, and therefore by Skype only allows you to select from a list. Which would be fine since the list shows the correct names of the devices, but quite often this selection gets changed for no apparent reason, and without warning.

---

### Post by nickrout on 2010-11-13
> **AKADAP said:**
> I'm afraid you misunderstood the issue. The udev rule for the web cam works fine, and the "WebCam" link gets created without any trouble.

The problem is that no application that uses web cams allows you to enter arbitrary device names, and will only allow you to select from a list that does not contain the WebCam link that is created by udev rules.

Also, the System->Preferences->Sound application that allows you to select the audio device used by the system, and therefore by Skype only allows you to select from a list. Which would be fine since the list shows the correct names of the devices, but quite often this selection gets changed for no apparent reason, and without warning.

Why not symlink the webcam to, say. /dev/video9. Unless you get 8 more video devices, /dev/video9 is never going to be auto allocated. You should be able to use /dev/video9 in your webcam app.

The sound thing is perhaps trickier.

---

### Post by kyphos on 2010-11-13
> **AKADAP said:**
> I'm afraid you misunderstood the issue. 



Quite right. 
Sorry I can't help on this problem - I have no experience with webcams.  

I too have an audio problem, but it's getting the audio out of my PVR150 tuner card.  Thanks the udev symlink, my problem with the device names flip-flopping has stopped, but there's something amiss with the sound capture.

Back to my good friend, Mr. Google.

---

### Post by nickrout on 2010-11-13
> **kyphos said:**
> Quite right. 
Sorry I can't help on this problem - I have no experience with webcams.  

I too have an audio problem, but it's getting the audio out of my PVR150 tuner card.  Thanks the udev symlink, my problem with the device names flip-flopping has stopped, but there's something amiss with the sound capture.

Back to my good friend, Mr. Google.

Are you capturing via the tuner as such or from an analogue source (like s-video out of a set top box)?

---

### Post by kyphos on 2010-11-13
> **nickrout said:**
> Are you capturing via the tuner as such or from an analogue source (like s-video out of a set top box)?

Hi Nickrout,

The answer is both. I have the coax input on my PVR-150 connected to my analog cable feed, and the S-video input (plus stereo audio) connected to the outputs from my digital cable box. Intent is to be able to record the occasional program being broadcast on a digital channel.

I have two Input Connections defined, one for the tuner input and another for the s-video input.  The former works just fine - video and audio are both captured and stored on my hard drive (MPEG encoded).  But if I record a program using the s-vid input,  I get the video of the channel being tuned by the STB (and very weak, distorted audio).

It's my understanding that the PVR-150 encodes the video and audio as it creates the MPEG stream. In other words, the audio never leaves the card on its own, doesn't go through alsa, etc.  Regardless, I've fiddled with the alas mixers, to no avail.

Any insights on this are most welcome!

---

### Post by nickrout on 2010-11-14
> **kyphos said:**
> Hi Nickrout,

The answer is both. I have the coax input on my PVR-150 connected to my analog cable feed, and the S-video input (plus stereo audio) connected to the outputs from my digital cable box. Intent is to be able to record the occasional program being broadcast on a digital channel.

I have two Input Connections defined, one for the tuner input and another for the s-video input.  The former works just fine - video and audio are both captured and stored on my hard drive (MPEG encoded).  But if I record a program using the s-vid input,  I get the video of the channel being tuned by the STB (and very weak, distorted audio).

It's my understanding that the PVR-150 encodes the video and audio as it creates the MPEG stream. In other words, the audio never leaves the card on its own, doesn't go through alsa, etc.  Regardless, I've fiddled with the alas mixers, to no avail.

Any insights on this are most welcome!

you are right on that. you perhaps have the wrong audio input setup, I am a little vague as I haven't used my pvr-150 for a long time. However the commandline control command is (IIRC) v4l2ctl. Have a play! You might need to add a channel change script to change the audio input when you change to an stb channel.

Also you can easily test the pvr-150 by using mplayer /dev/video0 or cat /dev/video0 > file.mpg . This gives you the ability to use v4l2ctl and see results straight away rather than continually trying sample recordings via myth.

---

### Post by kyphos on 2010-11-14
> **nickrout said:**
> you are right on that. you perhaps have the wrong audio input setup, I am a little vague as I haven't used my pvr-150 for a long time. However the commandline control command is (IIRC) v4l2ctl. Have a play! 


Nick,
Where do I find this v4l2ctl command?  This is what I get:
```
myth@myth-box:/etc$ v4l2ctl
No command 'v4l2ctl' found, did you mean:
 Command 'v4l2-ctl' from package 'ivtv-utils' (multiverse)
 Command 'v4l2ctrl' from package 'v4l2ucp' (universe)
 Command 'v4lctl' from package 'xawtv' (universe)
v4l2ctl: command not found
```
It seems I need to install something, but I'm not sure what to do. I suspect the ivtv-utils package is the most likely suspect.

Thanks.

---

### Post by nickrout on 2010-11-14
> **kyphos said:**
> Nick,
Where do I find this v4l2ctl command?  This is what I get:
```
myth@myth-box:/etc$ v4l2ctl
No command 'v4l2ctl' found, did you mean:
 Command 'v4l2-ctl' from package 'ivtv-utils' (multiverse)
 Command 'v4l2ctrl' from package 'v4l2ucp' (universe)
 Command 'v4lctl' from package 'xawtv' (universe)
v4l2ctl: command not found
```
It seems I need to install something, but I'm not sure what to do. I suspect the ivtv-utils package is the most likely suspect.

Thanks.

ivtv-utils it is.

---

### Post by kyphos on 2010-11-14
Nick,
Got it. Thanks!

Now to figure out what to do with it. And how to invoke it with a channel changing script, etc...

And thanks for the tip about using mplayer to monitor the media stream.  I would never have figured that out (Mythbuntu didn't come with mplayer installed).  Going back and forth into Myth was driving me nuts.

---

