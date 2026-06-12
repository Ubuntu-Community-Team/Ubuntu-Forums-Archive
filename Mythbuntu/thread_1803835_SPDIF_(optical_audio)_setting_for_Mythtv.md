---
title: "SPDIF (optical audio) setting for Mythtv"
date: 2011-07-13
forum: Mythbuntu
---

### Post by davidstoll on 2011-07-13
I can get audio via my HDMI, but can't get it to ouput optical in MythTV.  Optical works with other programs just fine also (without an asound file).

Basically, I need to figure out what I put in the UTILITIES/SETTINGS->GENERAL->page3->"Audio output device" and also the "Digital output device"....and if I NEED an /etc/asound.conf or ~/.asound .  I assume if I have a correctly configured asound file, then I can just use ALSA:default and Default (respectively) for the two devices in the MythTV settings...?

Not 100% sure about this, but I would use this with ALSA:default in the MythTV sound settings...if it is correct.
```
$ cat /etc/asound.conf
pcm.!default {
type plug
slave.pcm {
type hw
card 0
device 1
}
}
```


```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```



```
$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
front:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC888 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Direct sample mixing device
dmix:CARD=Intel,DEV=1
    HDA Intel, ALC888 Digital
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Direct sample snooping device
dsnoop:CARD=Intel,DEV=1
    HDA Intel, ALC888 Digital
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=1
    HDA Intel, ALC888 Digital
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, ALC888 Analog
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=1
    HDA Intel, ALC888 Digital
    Hardware device with all software conversions
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dmix:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dmix:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=9
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
```

---

### Post by nickrout on 2011-07-14
Have you scanned for audio devices in mythtv settings? What options does it then offer?

---

### Post by matthias.rieber on 2011-07-14
Have a similar problem (and the same HW ? asrock ION 3D ? aplay -L looks identical)
 
Got s/pdif running with entry "ALSA:plughw:0,1" (it is the intel digital sound using s/pdif) in section:
"mythfrontend-configuration-general-<page3 or 4> (audio settings) very top line under the "scan for audio devices"
 
the "asound.conf"-files will not work on my installation, too....
 
but setting s/pdif to default output, then hdmi audio will not longer work.........
only if I change this line back to "ALSA:plughw:1,7"
 
direct througput will not work at all....
 
and on some films i just here horrible noise (dts sound, working on a win PC and on WD-TV live box)

---

### Post by davidstoll on 2011-07-14
> **nickrout said:**
> Have you scanned for audio devices in mythtv settings? What options does it then offer?

Oh, sorry, I forgot to say, I'm running 10.10, so I don't have that option.  I could run a live disk of 11.04, but I had issues booting to that...but I can try again.  I even tried DVD and CD....hmmmm

---

### Post by davidstoll on 2011-07-14
> **matthias.rieber said:**
> on some films i just here horrible noise

I can get a loud choppy static sound, but that's the best I can do.

---

### Post by nickrout on 2011-07-14
> **davidstoll said:**
> Oh, sorry, I forgot to say, I'm running 10.10, so I don't have that option.  I could run a live disk of 11.04, but I had issues booting to that...but I can try again.  I even tried DVD and CD....hmmmm

you need to update to 0.24-fixes to et any help around here. Use mythbuntu-repo

---

### Post by davidstoll on 2011-07-14
> **nickrout said:**
> you need to update to 0.24-fixes to et any help around here. Use mythbuntu-repo

The device line should still be the same....what would it be for .24?  I would like to give that a try first if you don't mind.

---

### Post by nickrout on 2011-07-15
Dunno, I rely on the scanner. That's what it's there for. That's why they have mythbuntu-repos.

---

### Post by davidstoll on 2011-07-16
What did people do before the scanner?  The scanner is new with 11.04 in the official builds.  So, it's not like it's been around in the official releases with MythBuntu for a long time.

I'm not talking about something from years ago...it's only been like 3 months since 11.04 came out.

I tried to boot to 11.04 32 and 64bit and I get a kernel panic attack, so that isn't an option.

I understand there are repos, but I don't want to run into other issues like I have before.  I'd rather stick with my current build...only 3 months "old".

Is there nobody who can possibly help me with what I'm running now?

---

### Post by nickrout on 2011-07-17
> **davidstoll said:**
> What did people do before the scanner?  The scanner is new with 11.04 in the official builds.  So, it's not like it's been around in the official releases with MythBuntu for a long time.

I'm not talking about something from years ago...it's only been like 3 months since 11.04 came out.

I tried to boot to 11.04 32 and 64bit and I get a kernel panic attack, so that isn't an option.

I understand there are repos, but I don't want to run into other issues like I have before.  I'd rather stick with my current build...only 3 months "old".

Is there nobody who can possibly help me with what I'm running now?

Nobody said anything about 11.04.

---

### Post by davidstoll on 2011-07-17
> **nickrout said:**
> Nobody said anything about 11.04.

I did.  11.04 is the first official distribution (that has the version of mythtv) with the scanner.

I can't get 11.04 up and running.  I've tried, but can't.  Yes, I could go down that path of solving that issue, but that seems like a much larger hill to climb.  I've seen 11.04 (which has .24 in it) and I had other issues too, so I've reverted back to 10.10 (.23+fixes) and everything seems basically fine except I can't get optical audio.

Now, yes, I could get other releases of just .24+ through repos, but I've had other issues with doing this in the past....certain things (like 3rd party programs) didn't work for me and it is a lot of work to bring it back to a version where things work.

I just want help with figuring out my audio settings.  When people have audio problems, they typically are asked to post certain things, which I did from the beginning in hopes that that would get the ball rolling.

I still would like to get help with my audio.  I certainly didn't want to start some kind of argument about what version I should try.

---

### Post by nickrout on 2011-07-17
> **davidstoll said:**
> I did.  11.04 is the first official distribution (that has the version of mythtv) with the scanner.

wrong, 0.24-fixes is available for 10.04 at least. The repos are official. Please don't confuse mythbuntu versions (10.04, 11.04 etc) with mythtv versions (0.23, 0.24-fixes etc) > 

I can't get 11.04 up and running.  I've tried, but can't.  Yes, I could go down that path of solving that issue, but that seems like a much larger hill to climb.  I've seen 11.04 (which has .24 in it) and I had other issues too, so I've reverted back to 10.10 (.23+fixes) and everything seems basically fine except I can't get optical audio.

Now, yes, I could get other releases of just .24+ through repos, but I've had other issues with doing this in the past....certain things (like 3rd party programs) didn't work for me and it is a lot of work to bring it back to a version where things work.

I just want help with figuring out my audio settings.  When people have audio problems, they typically are asked to post certain things, which I did from the beginning in hopes that that would get the ball rolling.

I still would like to get help with my audio.  I certainly didn't want to start some kind of argument about what version I should try.

I'll try and help but honestly audio in mythtv has had a lot of changes and improvements between 0.23 and 0.24, and the scanner does work well. But if you are determined to use an unsupported version, I'll do my best to help.

Lets start with the output of ```
ls -l /proc/asound
```

---

### Post by davidstoll on 2011-07-17
$ ls -l /proc/asound
total 0
dr-xr-xr-x 7 root root 0 2011-07-17 03:43 card0
dr-xr-xr-x 6 root root 0 2011-07-17 03:43 card1
-r--r--r-- 1 root root 0 2011-07-17 03:43 cards
-r--r--r-- 1 root root 0 2011-07-17 03:43 devices
-r--r--r-- 1 root root 0 2011-07-17 03:43 hwdep
lrwxrwxrwx 1 root root 5 2011-07-17 03:43 Intel -> card0
-r--r--r-- 1 root root 0 2011-07-17 03:43 modules
lrwxrwxrwx 1 root root 5 2011-07-17 03:43 NVidia -> card1
-r--r--r-- 1 root root 0 2011-07-17 03:43 pcm
dr-xr-xr-x 2 root root 0 2011-07-17 03:43 seq
-r--r--r-- 1 root root 0 2011-07-17 03:43 timers
-r--r--r-- 1 root root 0 2011-07-17 03:43 version

---

### Post by nickrout on 2011-07-17
Card=Intel Device=1 looks like it, I think it is formatted like

ALSA:CARD=Intel,DEV=1

or ALSA:iec958:Card=Intel,DEV=1

But this alsa stuff is very confusing! That's why the scanner is so good.

You seem to hae a lot of odd dmix etc devices, do you have an asound.conf or .asoundrc with lots of definitions? If so remove them (change the filename so you don't lose whats in there. You shouldn't need one at all these days.)

Good luck with your old and officially unsupported version. I'll keep an eye on this thread of course, but not sure how much I can do.

I would suggest the mailing list, but they are even more adamant about not supporting out of date versions.

---

### Post by davidstoll on 2011-07-18
One more quick question.  Is audio over HDMI possible in Mythtv.  It seems like I read a while back that it wasn't really very easy, so not really possible for the average user.  Is this still basically the case or should it work out-of-the-box...for the most part?  .23 and/or .24 and/or whatever.

Thanks again.

---

### Post by nickrout on 2011-07-18
> **davidstoll said:**
> One more quick question.  Is audio over HDMI possible in Mythtv.  It seems like I read a while back that it wasn't really very easy, so not really possible for the average user.  Is this still basically the case or should it work out-of-the-box...for the most part?  .23 and/or .24 and/or whatever.

Thanks again.

Yes it is possible, in fact it is quite common. In fact your first post said you had it working!

Again: easier with the 0.24 code.

Of course it depends which card you are using. It seems to work with nvidia cards out of the box, although for 4xx and 5xx series cards I think you need a newer version of alsa than is current in *buntu.

---

### Post by davidstoll on 2011-07-18
> **nickrout said:**
> Yes it is possible, in fact it is quite common. In fact your first post said you had it working!

Again: easier with the 0.24 code.

Of course it depends which card you are using. It seems to work with nvidia cards out of the box, although for 4xx and 5xx series cards I think you need a newer version of alsa than is current in *buntu.

Yeah HDMI audio works in the OS and some other 3rd party programs, but doesn't seem to work in MythTV...for me.  I seem to be able to get analog (via headphone plug) and coax, but I think that's about it for me in MythTV.

---

### Post by nickrout on 2011-07-18
> **davidstoll said:**
> Yeah HDMI audio works in the OS and some other 3rd party programs, but doesn't seem to work in MythTV...for me.  I seem to be able to get analog (via headphone plug) and coax, but I think that's about it for me in MythTV.

Did you even try the settings for spdif I posted?

did you try eliminating asound.conf and/or ~/.asoundrc from the equation?

---

### Post by davidstoll on 2011-07-19
> **nickrout said:**
> Did you even try the settings for spdif I posted?

did you try eliminating asound.conf and/or ~/.asoundrc from the equation?

Yes I did all these things.

...and I added the repo to get myself up to .24.  I have a few other issues now, but I'll deal with those later.

I did the scan and tried everything it found (scanning each time) and I am not able to get HDMI or optical audio out.

There were at least 10 items it found when it scanned.  At least 4 were "HDMI" related.  No luck.  :(

I know the HDMI audio works because other 3rd party programs produce audio through HDMI...web browser, vlc, etc.

---

### Post by matthias.rieber on 2011-07-19
pls see my first post: I have the same "aplay" output (without asound-file).
I got hdmi working with either "plughw:1,7" or "dmix:Nvidia:Device=7" - not with the so called "hdmi-devices" found by mythtv scanner.
I got s/pdif working, too with "plughw:0,1" or "dmix:Intel:Device=1" - but no digital passthrough....
Every try to use any kind of asound-file failed....
And digital-passthrough-sound (working fine with vlc) will just give me noise/buzz on the speakers with mythtv.... you can look at this threat too: [[COLOR=#000000]Urgent help needed: errors in mythtranscode, mythwelcome and alsa[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1803451")  (no answers included)
 
Using vlc is no alternative - because gpu-support is not working (all videos larger 4 Gb are shuttering....)

---

### Post by nickrout on 2011-07-19
What video card do you have?

---

### Post by davidstoll on 2011-07-19
> **matthias.rieber said:**
> pls see my first post: I have the same "aplay" output (without asound-file).
I got hdmi working with either "plughw:1,7" or "dmix:Nvidia:Device=7" - not with the so called "hdmi-devices" found by mythtv scanner.
I got s/pdif working, too with "plughw:0,1" or "dmix:Intel:Device=1" - but no digital passthrough....
Every try to use any kind of asound-file failed....
And digital-passthrough-sound (working fine with vlc) will just give me noise/buzz on the speakers with mythtv.... you can look at this threat too: [[COLOR=#000000]Urgent help needed: errors in mythtranscode, mythwelcome and alsa[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1803451")  (no answers included)
 
Using vlc is no alternative - because gpu-support is not working (all videos larger 4 Gb are shuttering....)

I tried
plughw:1,7
dmix:Nvidia:Device=7
ALSA:dmix:Nvidia:Device=7     # this is what the scanner finds

Unfortunately, none worked.

---

### Post by davidstoll on 2011-07-19
> **nickrout said:**
> What video card do you have?

GeForce GT430

[http://www.amazon.com/gp/product/B0046HAW7Y](http://www.amazon.com/gp/product/B0046HAW7Y)

---

### Post by nickrout on 2011-07-20
> **davidstoll said:**
> GeForce GT430

[http://www.amazon.com/gp/product/B0046HAW7Y](http://www.amazon.com/gp/product/B0046HAW7Y)

Ahh perhaps you missed earlier in the thread where I said:

> Of course it depends which card you are using. It seems to work with nvidia cards out of the box, although for 4xx and 5xx series cards I think you need a newer version of alsa than is current in *buntu.

I believe you need alsa 1.0.24. I will try and find the mailing list thread that specifies how to get that on *buntu.

---

### Post by davidstoll on 2011-07-20
> **nickrout said:**
> Ahh perhaps you missed earlier in the thread where I said:

Of course it depends which card you are using. It seems to work with nvidia cards out of the box, although for 4xx and 5xx series cards I think you need a newer version of alsa than is current in *buntu.

I believe you need alsa 1.0.24. I will try and find the mailing list thread that specifies how to get that on *buntu.

I didn't think it was still valid if I can get HDMI audio in the OS and other 3rd party programs.  Logic kept pointing me to getting the correct setting in MythTV.  I guess there could be some kind of incompatibility between MythTV and some version of ALSA...but not with the OS or other programs....?

---

### Post by nickrout on 2011-07-20
I couldn't find the exact answer so I started a thread:

[http://www.gossamer-threads.com/lists/mythtv/users/486250#486250](http://www.gossamer-threads.com/lists/mythtv/users/486250#486250)

---

### Post by davidstoll on 2011-07-22
> **nickrout said:**
> I couldn't find the exact answer so I started a thread:

[http://www.gossamer-threads.com/lists/mythtv/users/486250#486250](http://www.gossamer-threads.com/lists/mythtv/users/486250#486250)

nickrout, what do you make of what they've said so far?  I'm not sure I see a path to take.

Is this:
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
or
[http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu) main
going to give me 1.0.24?

I'm not sure how to tell if it will or is even what I need.

---

### Post by ck102 on 2011-07-26
> **davidstoll said:**
> nickrout, what do you make of what they've said so far? I'm not sure I see a path to take.
 
Is this:
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
or
[http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu) main
going to give me 1.0.24?
 
I'm not sure how to tell if it will or is even what I need.
 
If you run the first line, you should then see the second line in your software sources.
 
You will then need to install [SIZE=1]linux-alsa-driver-modules to get 1.0.24.
[/SIZE]

---

### Post by davidstoll on 2011-07-27
> **ck102 said:**
> If you run the first line, you should then see the second line in your software sources.
 
You will then need to install [SIZE=1]linux-alsa-driver-modules to get 1.0.24.
[/SIZE]

First line seemed to be accepted ok, but nothing was added to /etc/apt/sources.list

I manually added the line above to sources list, but corrected to...
deb [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu) maverick main

Now I do:
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-alsa-driver-modules
```

---

### Post by ck102 on 2011-07-28
> **davidstoll said:**
> sudo apt-get install linux-alsa-driver-modules

 
You could try:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
 
Although that didn't work very well for me.  I found it easier to use synaptic and then searched for linux-alsa-driver-modules and then picked the one that matched my kernel.

---

### Post by davidstoll on 2011-07-28
> **ck102 said:**
> You could try:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
 
Although that didn't work very well for me.  I found it easier to use synaptic and then searched for linux-alsa-driver-modules and then picked the one that matched my kernel.

```
$uname -r
2.6.35-30-generic-pae

$sudo apt-get install linux-alsa-driver-modules-2.6.35-30-generic-pae
```

Successfully installed and even rebooted, but alsamixer still shows 1.0.23.

What else do I need to install?

---

### Post by ck102 on 2011-07-28
> **davidstoll said:**
> Successfully installed and even rebooted, but alsamixer still shows 1.0.23.
 
What else do I need to install?
 
[COLOR=black][FONT=Verdana]I don't recall having to install anything else.  After that I used the speaker-test and the scanner in mythtv and tested each of the hdmi aliases.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana]The aliases are listed with:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]```
aplay -L
```[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana]You can also test them using speaker-test or something similar to:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]```
aplay -D hdmi:CARD=NVidia_1,DEV=3 [some-wav-file]
```[/FONT][/COLOR]

---

### Post by davidstoll on 2011-07-28
> **ck102 said:**
> [COLOR=black][FONT=Verdana]I don't recall having to install anything else.  After that I used the speaker-test and the scanner in mythtv and tested each of the hdmi aliases.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana]The aliases are listed with:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]```
aplay -L
```[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana]You can also test them using speaker-test or something similar to:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]```
aplay -D hdmi:CARD=NVidia_1,DEV=3 [some-wav-file]
```[/FONT][/COLOR]

The aplay -L output was in my first post.  I'm a little confused with the "_1" portion on your aplay line.  I get an error if I try to use that kind of naming with aplay.  By the way, I always seem to find that aplay is very picky as to what format it will play.  Is there a generic sound file somewhere that every system has and is compatible with aplay?

Also, the speaker test is only in .25 if I understand correctly.  I'm now on .24, so I don't have the speaker test.

Also, the reason I am to this point is that I need (supposedly) 1.0.24 of alsa, which I still don't have for some reason.

So, doing the tests in myth (or even with aplay) put me back to where I was in the beginning.  I'd like to start with getting audio out of my HDMI.  Upgrading to Myth .24 didn't help (so far) and I have not been able to get 1.0.24 of alsa, which is also supposed to help.

---

### Post by ck102 on 2011-07-28
> **davidstoll said:**
> The aplay -L output was in my first post. I'm a little confused with the "_1" portion on your aplay line. I get an error if I try to use that kind of naming with aplay. By the way, I always seem to find that aplay is very picky as to what format it will play. Is there a generic sound file somewhere that every system has and is compatible with aplay?
 
Also, the speaker test is only in .25 if I understand correctly. I'm now on .24, so I don't have the speaker test.
 
Also, the reason I am to this point is that I need (supposedly) 1.0.24 of alsa, which I still don't have for some reason.
 
So, doing the tests in myth (or even with aplay) put me back to where I was in the beginning. I'd like to start with getting audio out of my HDMI. Upgrading to Myth .24 didn't help (so far) and I have not been able to get 1.0.24 of alsa, which is also supposed to help.
 
When I run the command aplay -L, one of the device aliases I get is hdmi:CARD=NVidia_1,DEV=3.  You will need to substitute your aliases for that one.
 
You are correct there is a speaker test in .25 of mythtv.  The speaker test I was talking about was the command "speaker-test"  
 
```
speaker-test -Dhdmi:CARD=NVidia,DEV=3
```
 
On my system it produced a staticy noise.  When I stopped the command the speakers were then silent.  It took me a while to figure out that was the noise I was suppose to hear.  Just make sure you change "hdmi:CARD=NVidia,DEV=3" to be one of the aliases your system provided in aplay -L.

---

### Post by davidstoll on 2011-07-29
> **ck102 said:**
> When I run the command aplay -L, one of the device aliases I get is hdmi:CARD=NVidia_1,DEV=3.  You will need to substitute your aliases for that one.
 
You are correct there is a speaker test in .25 of mythtv.  The speaker test I was talking about was the command "speaker-test"  
 
```
speaker-test -Dhdmi:CARD=NVidia,DEV=3
```
 
On my system it produced a staticy noise.  When I stopped the command the speakers were then silent.  It took me a while to figure out that was the noise I was suppose to hear.  Just make sure you change "hdmi:CARD=NVidia,DEV=3" to be one of the aliases your system provided in aplay -L.


I had to put a space after the "-D" in the speaker test, but here are my results...

These worked...but not what I'm looking for (analog, stereo, etc)
default:CARD=Intel
plughw:CARD=Intel,DEV=0
plughw:CARD=Intel,DEV=1

These looked like they were working, but I didn't get any sound...
plughw:CARD=NVidia,DEV=X
Where X was one of the valid numbers from aplay -L


Basically, the rest of them, I got this kind of error...
```
speaker-test 1.0.23

Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Channels count (1) not available for playbacks: Invalid argument
Setting of hwparams failed: Invalid argument
```

---

### Post by ck102 on 2011-07-31
Davidstoll,
After seeing the error message you were getting, I gave the commands a try on my system.  I am getting the same error message even with the hdmi setting I know is correct.  :(  Sorry for leading you down the wrong path.  I'm sure I used that command before.  I did manage to get this to work:
```
speaker-test -Dhdmi:CARD=NVidia_1,DEV=3 -c4 -l1 -twav
```

Please sub hdmi:CARD=NVidia_1,DEV=3 with something that is from aplay -L.

---

### Post by davidstoll on 2011-07-31
> **ck102 said:**
> Davidstoll,
After seeing the error message you were getting, I gave the commands a try on my system.  I am getting the same error message even with the hdmi setting I know is correct.  :(  Sorry for leading you down the wrong path.  I'm sure I used that command before.  I did manage to get this to work:
```
speaker-test -Dhdmi:CARD=NVidia_1,DEV=3 -c4 -l1 -twav
```

Please sub hdmi:CARD=NVidia_1,DEV=3 with something that is from aplay -L.

Hey, no problem.  I just appreciate being helped.  It's not easy to help someone remotely like this...

Several seem to work, but I get no sound....for instance...

```
$ speaker-test -Dhdmi:CARD=NVidia,DEV=0 -c4 -l1 -twav

speaker-test 1.0.23

Playback device is hdmi:CARD=NVidia,DEV=0
Stream parameters are 48000Hz, S16_LE, 4 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 32 to 8192
Period size range from 16 to 4096
Using max buffer size 8192
Periods = 4
was set period_size = 2048
was set buffer_size = 8192
 0 - Front Left
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
Time per period = 5.681310
```

I tried different cables...HDMI, optical, coax, etc. with each just to be sure.

---

### Post by ck102 on 2011-07-31
I'm not sure if this matters... but, which version of Nvidia drivers do you have?  I am currently on 270.29.

I'm sure you checked this and maybe even double checked... have you made sure the TV isn't muted or the alsa mixer?

---

### Post by davidstoll on 2011-08-01
> **ck102 said:**
> I'm not sure if this matters... but, which version of Nvidia drivers do you have?  I am currently on 270.29.

I'm sure you checked this and maybe even double checked... have you made sure the TV isn't muted or the alsa mixer?

Well, it looks like I'm on 260.19.06, so maybe I need to update?  Or not really?

Nothing is muted (aka MM) in alsamixer.

---

### Post by davidstoll on 2011-08-04
any other ideas?

---

### Post by ck102 on 2011-08-04
Hi,
I don't have anything else to try.

There is a discussion that is very similar to this, only for 11.04.  ([http://ubuntuforums.org/showthread.php?t=1811760](http://ubuntuforums.org/showthread.php?t=1811760))  You could try their ideas, or possibly try asking on the mythtv forum.

Chris.

---

### Post by nickrout on 2011-08-04
Where is this mythtv forum? The best resource is actually the mailing list. Details on mythtv.org.

---

### Post by ck102 on 2011-08-04
> **nickrout said:**
> Where is this mythtv forum? The best resource is actually the mailing list. Details on mythtv.org.

Thanks Nick for clarifying that.

---

### Post by BicyclerBoy on 2011-08-06
@OP
speaker-test -c 2 -r 48000 -D hw:1,3
speaker-test -c 2 -r 48000 -D hw:1,7
speaker-test -c 2 -r 48000 -D hw:1,8
speaker-test -c 2 -r 48000 -D hw:1,9

Have you got a probe_mask value for the snd-hda-intel module in any of the /etc/modprobe.d/*.conf files ?
I ask because there is lots of misleading info about the probe mask values & using any mask just makes debugging harder.

---

### Post by davidstoll on 2011-08-08
> **BicyclerBoy said:**
> Have you got a probe_mask value for the snd-hda-intel module in any of the /etc/modprobe.d/*.conf files ?
I ask because there is lots of misleading info about the probe mask values & using any mask just makes debugging harder.

$sudo grep "probe_mask" /etc/modprobe.d/*
and
$sudo grep "snd-hda-intel" /etc/modprobe.d/*

both returned nothing.

---

### Post by BicyclerBoy on 2011-08-08
Just noticed your alsa version is 1.0.23.
Are you wanting HDMI digital pass-thru' or just digital pass-thru' over S/PDIF ?

S/PDIF is not optical (Toslink) only but both optical & coaxial.
If the receiver does not have a reclocker then arguably coaxial is far superior.

The recommended version for HDMI audio is 1.0.24 for alsa base (userspace).
Can get 1.0.24 from iQuik audio ppa..

Test mobo soundcard S/PDIF ...
speaker-test -c6 -r 48000 iec958:CARD=Intel,DEV=0

Test HDMI version of "S/PDIF"
or try before/after alsa upgrade..
speaker-test -c2 -r 48000 -D hw:CARD=NVidia,DEV=3
speaker-test -c2 -r 48000 -D hw:CARD=NVidia,DEV=7
speaker-test -c2 -r 48000 -D hw:CARD=NVidia,DEV=8
speaker-test -c2 -r 48000 -D hw:CARD=NVidia,DEV=9

---

### Post by davidstoll on 2011-08-08
> **BicyclerBoy said:**
> Just noticed your alsa version is 1.0.23.
Are you wanting HDMI digital pass-thru' or just digital pass-thru' over S/PDIF ?

S/PDIF is not optical (Toslink) only but both optical & coaxial.
If the receiver does not have a reclocker then arguably coaxial is far superior.

The recommended version for HDMI audio is 1.0.24 for alsa base (userspace).
Can get 1.0.24 from iQuik audio ppa..

Test mobo soundcard S/PDIF ...
speaker-test -c6 -r 48000 iec958:CARD=Intel,DEV=0

Test HDMI version of "S/PDIF"
or try before/after alsa upgrade..
speaker-test -c2 -r 48000 -D hw:CARD=NVidia,DEV=3
speaker-test -c2 -r 48000 -D hw:CARD=NVidia,DEV=7
speaker-test -c2 -r 48000 -D hw:CARD=NVidia,DEV=8
speaker-test -c2 -r 48000 -D hw:CARD=NVidia,DEV=9

Someone suggested I install 1.0.24, which I thought I did.  When I run alsamixer, at the top it says AlsaMixer 1.0.23, but when I hit F2, it says...
```
/proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.24.
Compiled on Aug  4 2011 for kernel 2.6.35-30-generic-pae (SMP).

```

Also when I run VLC, I get sound with hw:0,1 but when I run...
```
speaker-test -c 6 -r 48000 -D hw:0,1
```
I don't get any sound.

---

### Post by BicyclerBoy on 2011-08-08
The version of the userspace driver can be different to the kernel space driver (lius-alsa-modules)

If speaker-test reports 1.0.24 you are okay (userspace)..

You only want mobo soundcard digital pass-thru' ??
I think you should not need any changes in asound.conf...The last time I remember it was required to be changed was Ubuntu 8.04 for S/PDIF or pass-thru' & rate 48000 was needed..

Did you try this ..?
speaker-test -c6 -r 48000 iec958:CARD=Intel,DEV=0
or
speaker-test -c 2 -r 48000 -D hw:0,1

---

### Post by nickrout on 2011-08-08
> **davidstoll said:**
> Someone suggested I install 1.0.24, which I thought I did.  When I run alsamixer, at the top it says AlsaMixer 1.0.23, but when I hit F2, it says...
```
/proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.24.
Compiled on Aug  4 2011 for kernel 2.6.35-30-generic-pae (SMP).

```

Also when I run VLC, I get sound with hw:0,1 but when I run...
```
speaker-test -c 6 -r 48000 -D hw:0,1
```
I don't get any sound.

sorry if this has been covered earlier, but what version of the nvidia drivers are you running? (I hope I remember right that this is audio through hdmi on an nvidia graphics card that you are after).

---

### Post by davidstoll on 2011-08-08
> **BicyclerBoy said:**
> The version of the userspace driver can be different to the kernel space driver (lius-alsa-modules)

If speaker-test reports 1.0.24 you are okay (userspace)..

You only want mobo soundcard digital pass-thru' ??
I think you should not need any changes in asound.conf...The last time I remember it was required to be changed was Ubuntu 8.04 for S/PDIF or pass-thru' & rate 48000 was needed..

Did you try this ..?
speaker-test -c6 -r 48000 iec958:CARD=Intel,DEV=0
or
speaker-test -c 2 -r 48000 -D hw:0,1

Basically I would like the option of optical and HDMI audio, but after going through this, I would settle for just HDMI.

Unfortunately, the speaker-test shows 1.0.23.

I get an error with both speaker-test's...

```
$ speaker-test -c6 -r 48000 iec958:CARD=Intel,DEV=0

speaker-test 1.0.23

Playback device is default
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
Playback open error: -16,Device or resource busy
```


```
$ speaker-test -c 6 -r 48000 -D hw:0,1

speaker-test 1.0.23

Playback device is hw:0,1
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Playback open error: -16,Device or resource busy
```

...and just to be complete...
```
$ speaker-test -c 6 -r 48000 -D hw:0.1

speaker-test 1.0.23

Playback device is hw:0.1
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
```

---

### Post by davidstoll on 2011-08-08
> **nickrout said:**
> sorry if this has been covered earlier, but what version of the nvidia drivers are you running? (I hope I remember right that this is audio through hdmi on an nvidia graphics card that you are after).

260
that is correct

[http://ubuntuforums.org/showpost.php?p=11107604&postcount=39](http://ubuntuforums.org/showpost.php?p=11107604&postcount=39)

---

### Post by nickrout on 2011-08-09
OK there is another thread running pretty parallel to this one that suggests updating the nvidia drivers may be the solution [http://ubuntuforums.org/showthread.php?t=1811760](http://ubuntuforums.org/showthread.php?t=1811760) - best you read the whole thread, but the stuff about the nvidia drivers is on page 5. Hope it helps.

---

### Post by BicyclerBoy on 2011-08-09
If you want to get your userspace alsa-base up to version 1.0.24 can use this ppa..
Very popular with XBMC Live as it is 10.04 based..
iQuik
[https://launchpad.net/~team-iquik/+archive/alsa]("https://launchpad.net/%7Eteam-iquik/+archive/alsa")


A note of warning about speaker-test...
You should close & re-open the terminal after every attempt to use it...especially if you <ctrl>+<c>  out of to terminate.. it does not exit cleanly..
This message can be an own goal..
Playback open error: -16,Device or resource busy

---

### Post by davidstoll on 2011-08-09
> **nickrout said:**
> OK there is another thread running pretty parallel to this one that suggests updating the nvidia drivers may be the solution [http://ubuntuforums.org/showthread.php?t=1811760](http://ubuntuforums.org/showthread.php?t=1811760) - best you read the whole thread, but the stuff about the nvidia drivers is on page 5. Hope it helps.

It says that it's better to install via a ppa than to just download strait from the nvidia web site.  While I understand a ppa will help me keep up to date, how can I know that the ppa I am adding is safe or even reliable?  Does Nvidia have a ppa?  The ppa they are talking about seems ok, but not official?

Don't deb's sometimes add a line to your source list to help keep you updated?

i.e.
[http://www.nvidia.com/object/linux-display-ia32-280.13-driver.html](http://www.nvidia.com/object/linux-display-ia32-280.13-driver.html)
vs
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

---

### Post by davidstoll on 2011-08-09
> **BicyclerBoy said:**
> If you want to get your userspace alsa-base up to version 1.0.24 can use this ppa..
Very popular with XBMC Live as it is 10.04 based..
iQuik
[https://launchpad.net/~team-iquik/+archive/alsa]("https://launchpad.net/%7Eteam-iquik/+archive/alsa")


A note of warning about speaker-test...
You should close & re-open the terminal after every attempt to use it...especially if you <ctrl>+<c>  out of to terminate.. it does not exit cleanly..
This message can be an own goal..
Playback open error: -16,Device or resource busy

Thanks for the tip on the terminal closing.

I added the iquik repo and here is what happened...not sure what to make of it.

```
$ sudo add-apt-repository ppa:team-iquik/alsa
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 1B05262E084BDE67358EF400210AE75EDC1FE094
gpg: requesting key DC1FE094 from hkp server keyserver.ubuntu.com
gpg: key DC1FE094: public key "Launchpad Addons PPA" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

$ sudo apt-get update
...
Err http://ppa.launchpad.net maverick/main Sources
  404  Not Found
Err http://ppa.launchpad.net maverick/main i386 Packages
  404  Not Found
Fetched 9,845B in 1s (6,473B/s)
W: Failed to fetch http://ppa.launchpad.net/team-iquik/alsa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/team-iquik/alsa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by nickrout on 2011-08-09
> **davidstoll said:**
> It says that it's better to install via a ppa than to just download strait from the nvidia web site.  While I understand a ppa will help me keep up to date, how can I know that the ppa I am adding is safe or even reliable?  Does Nvidia have a ppa?  The ppa they are talking about seems ok, but not official?

Don't deb's sometimes add a line to your source list to help keep you updated?

i.e.
[http://www.nvidia.com/object/linux-display-ia32-280.13-driver.html](http://www.nvidia.com/object/linux-display-ia32-280.13-driver.html)
vs
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

add-apt-repository adds a line to the source list.

your nvidia link shows the latest driver, which is the same one as available in the ppa..

No ppa is "official" but if you want to try the suggestion of the later drivers it is the best way to go.

---

### Post by davidstoll on 2011-08-09
> **nickrout said:**
> add-apt-repository adds a line to the source list.

your nvidia link shows the latest driver, which is the same one as available in the ppa..

No ppa is "official" but if you want to try the suggestion of the later drivers it is the best way to go.

That is strange that the in my previous message doesn't work...I just clicked it on a different computer and it worked.

I do have nvidia-current....i.e. sudo apt-get install nvidia-current.  Is that what you mean?

---

### Post by BicyclerBoy on 2011-08-09
I have just noticed that iQuik ppa does not have any maverick packages..
This is because XBMC Live is based on 10.04.

So this is not going to work until XBMC Live migrates to 10.10.

Sorry I have not found any other way to upgrade alsa except compile from source.
The dependencies for alsa are/were ridiculous (100MBs of xml cruft).
I don't know how to compile just the userspace components.

Compiling this & the nvidia driver just puts these packages outside of package management & kernel updates just break everything.

---

### Post by nickrout on 2011-08-09
Hey BicyclerBoy I see you are a Kiwi too! What part of the country are you in? I am in shakytown.

David, you should try adding the x-swat ppa and updating your nvidia drivers to 280.13.

---

### Post by davidstoll on 2011-08-09
> **nickrout said:**
> David, you should try adding the x-swat ppa and updating your nvidia drivers to 280.13.

Ok, I'm not running 280.13, but I am getting an error (the same for all 4 HDMI devices) when I use 6 channels.

```
$ speaker-test -c 6 -r 48000 -D hw:1,3

speaker-test 1.0.23

Playback device is hw:1,3
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 22 to 5461
Period size range from 11 to 2730
Using max buffer size 5460
Periods = 4
was set period_size = 1365
was set buffer_size = 5460
 0 - Front Left
Write error: -5,Input/output error
xrun_recovery failed: -5,Input/output error
Transfer failed: Operation not permitted
```

If I do 2 channels, it looks like it's working, but I don't get any sound.

If I do 6 channels on hw:0,1 , it looks like it works for all 6 channels, but I only get sound on 2 of them (front right and left).

---

### Post by nickrout on 2011-08-09
David, you should try adding the x-swat ppa and updating your nvidia drivers to 280.13.

---

### Post by davidstoll on 2011-08-09
> **nickrout said:**
> David, you should try adding the x-swat ppa and updating your nvidia drivers to 280.13.

Yes, I have 280.13 and x-swat ppa.

Even with the x-swat ppa, the speakertest still shows 1.0.23.

Again, when I run alsamixer, at the top it says alsamixer 1.0.23, but when I hit F2 and select driver version, it tells me I have 1.0.24...none of this information changed with the addition of the x-swat ppa (and apt-get update and apt-get upgrade and a reboot)...even though updates did get added.

---

### Post by nickrout on 2011-08-09
> **davidstoll said:**
> Ok, I'm not running 280.13> **davidstoll said:**
> Yes, I have 280.13 and x-swat ppa.

OK now you have me confused. Make up your mind.
> 
Even with the x-swat ppa, the speakertest still shows 1.0.23.

Again, when I run alsamixer, at the top it says alsamixer 1.0.23, but when I hit F2 and select driver version, it tells me I have 1.0.24...none of this information changed with the addition of the x-swat ppa (and apt-get update and apt-get upgrade and a reboot)...even though updates did get added.

the x-swat ppa does not provide alsa drivers or utilities.

If you read the other thread I pointed to you wil see that the up to date nvidia 280.13 driver enabled some posters to get audio over hdmi. That's why i suggested it.

---

### Post by davidstoll on 2011-08-09
> **nickrout said:**
> OK now you have me confused. Make up your mind.


the x-swat ppa does not provide alsa drivers or utilities.

If you read the other thread I pointed to you wil see that the up to date nvidia 280.13 driver enabled some posters to get audio over hdmi. That's why i suggested it.

ok, my mistake.  I thought the alsa driver update was also in the x-swat.

But the bottom line is that I have 280.13 and it doesn't seem to help my situation.

---

### Post by BicyclerBoy on 2011-08-10
I have found an alsa 1.0.24 user-space drivers ppa for 10.10 maverick.

[https://launchpad.net/~ricotz/+archive/unstable?field.series_filter=maverick]("https://launchpad.net/%7Ericotz/+archive/unstable?field.series_filter=maverick")
as long as the unstable bit does not bother you..

Sorry about the iQuik ppa ..they do not have any maverick packages.

To clarify..
The alsa kernel modules are in the normal ubuntu linux kernel. These can be updated by linux-alsa-modules packages or (more easily) by using a later kernel i.e. natty-backport-kernel package etc..
It is not likely you need to update this component.

Alsa 1.0.24 user-space updates avail from iQuik (10.04) or ricotz above (10.10).
Alsa 1.0.24 user-space (alsa-base libasound2 speaker-test etc) works fine with kernel alsa 1.0.23.
This update seems to help solve most HDMI problems.

The most reliable source of info is:
[http://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html]("ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html")

---

### Post by davidstoll on 2011-08-12
> **BicyclerBoy said:**
> I have found an alsa 1.0.24 user-space drivers ppa for 10.10 maverick.

[https://launchpad.net/~ricotz/+archive/unstable?field.series_filter=maverick]("https://launchpad.net/%7Ericotz/+archive/unstable?field.series_filter=maverick")
as long as the unstable bit does not bother you..

Sorry about the iQuik ppa ..they do not have any maverick packages.

To clarify..
The alsa kernel modules are in the normal ubuntu linux kernel. These can be updated by linux-alsa-modules packages or (more easily) by using a later kernel i.e. natty-backport-kernel package etc..
It is not likely you need to update this component.

Alsa 1.0.24 user-space updates avail from iQuik (10.04) or ricotz above (10.10).
Alsa 1.0.24 user-space (alsa-base libasound2 speaker-test etc) works fine with kernel alsa 1.0.23.
This update seems to help solve most HDMI problems.

The most reliable source of info is:
[http://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html]("ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html")

Ok, now I have alsa 1.0.24.2 and the speaker-test reflects that also.

Not much has changed though.  The only difference I can find (from post #60, [http://ubuntuforums.org/showpost.php?p=11135935&postcount=60](http://ubuntuforums.org/showpost.php?p=11135935&postcount=60)) is that now when I do a 6 speaker test on hw:0,1, I get this...and I do close/open a new terminal window with each test as suggested.  Whereas before, it looked like it worked, but I only got sound on the front 2 speakers...now, it errors out...

```
$ speaker-test -c 6 -r 48000 -D hw:0,1

speaker-test 1.0.24.2

Playback device is hw:0,1
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Channels count (6) not available for playbacks: Invalid argument
Setting of hwparams failed: Invalid argument
```

Specifically, I don't get any sound from any of the hdmi tests, but I don't get an error.  So, it looks like it's working, but nothing comes out.  As a reminder, I do get audio (as before) via my web browser, vlc, etc...

---

### Post by ck102 on 2011-08-12
> **davidstoll said:**
> 
Specifically, I don't get any sound from any of the hdmi tests, but I don't get an error. So, it looks like it's working, but nothing comes out. As a reminder, I do get audio (as before) via my web browser, vlc, etc...
 
Is the sound when using the web browser from the video card over the HDMI or from the on-board sound or sound card?
 
I vaguely recall a problem with my TV. If I left the stereo cable connected to the TV and the on-board sound, the TV wouldn't accept the sound over the HDMI.

---

### Post by davidstoll on 2011-08-18
Ok, so I have an update.  Sorry for the delay.

Unplugging the analog audio cable from the TV was a good idea, but it didn't seem to help.

I can get analog audio out of my headphone jack (speaker-test -c 2 -r 48000 -D hw:0,0) and my reciever does a half way decent job of trying to convert it to 5.1, but it's still not 5.1.  With the speaker test I can also run a 6 channels test without it erroring out, but it just puts sound to the front two.  The other channels show in the command line, but no sound.

I can get audio out of my coaxial port (speaker-test -c 2 -r 48000 -D hw:0,1), but it will only allow 2 channels.  I know it is my coaxial port because it cuts out when I unplug it.  I get an error that says X channels is not available on this device (where X = anything other than 2).

I can get audio out of my HDMI cable (speaker-test -c 2 -r 48000 -D hw:1,9), but it will also only allow 2 channels.  If it try to change it to 6 (or anything else) I get the same error regarding the number of channels not being available.  None of the other HDMI devices work (1,3 or 1,7 or 1,8).  I don't get errors running a speaker test with the other three HDMI devices, but I just don't get sound on the speaker test.

For the devices that would not work with a 6 channel speaker test, that followed through to MythTV.  I had to make sure if I chose that particular device, that I set it as stereo rather than 5.1.  This allowed for audio, but obviously just stereo.  This is probably why I was never able to get sound before in MythTV...because I always set it to 5.1.

So, the question is now:  How do I get 5.1 from my devices rather than just 2.0?

---

### Post by BicyclerBoy on 2011-08-19
The audio out headphones & coaxial s/pdif are working correctly..

Non HDA connection:
5.1 audio output is **only** possible with 6 analogue cables or matrix encoded AC3 or DTS via digital pass-thru'.
S/PDIF does **not** support 5.1 discrete PCM channels...stereo or matrix encoded only.
You need to output via digital pass-thru' an AC3 or DTS datastream.


HDA connection:
**If** the receiver has the capabilities (or you override) the HDMI allows:
stereo PCM
multi-channel LPCM
matrix encoded multi-channel AC3 DTS
lossless encoded multi-ch DTS-MA 

So now you need to find the capabilites of the receiver as reported by alsa (ELD)..
cat /proc/asound/card1/codec#9

Your connected TV may be changing the audio ELD reported from the HT Amp (AVR).
You are connected to AVR by HDMI ?

---

### Post by davidstoll on 2011-08-28
Hi, sorry it took me so long to get back.  I had a death in the family....anyway....

cat /proc/asound/card1/codec#9
gives me an error "No such file or directory"

I am connected via HDMI, but can also use S/PDIF.
I guess HDMI would be preferred, but I guess it would be good to have options for different setups...and to just have a better understanding, to get both working.

I basically understand what you are saying, in that certain types of connections support certain formats/encodings.  I just want to be able to record OTA HD TV and play it back via 5.1...preferably HDMI I guess.



> **BicyclerBoy said:**
> The audio out headphones & coaxial s/pdif are working correctly..

Non HDA connection:
5.1 audio output is **only** possible with 6 analogue cables or matrix encoded AC3 or DTS via digital pass-thru'.
S/PDIF does **not** support 5.1 discrete PCM channels...stereo or matrix encoded only.
You need to output via digital pass-thru' an AC3 or DTS datastream.


HDA connection:
**If** the receiver has the capabilities (or you override) the HDMI allows:
stereo PCM
multi-channel LPCM
matrix encoded multi-channel AC3 DTS
lossless encoded multi-ch DTS-MA 

So now you need to find the capabilites of the receiver as reported by alsa (ELD)..
cat /proc/asound/card1/codec#9

Your connected TV may be changing the audio ELD reported from the HT Amp (AVR).
You are connected to AVR by HDMI ?

---

### Post by nickrout on 2011-08-29
> **davidstoll said:**
> Hi, sorry it took me so long to get back.  I had a death in the family....anyway....

 Coincidence: same here. [http://www.youtube.com/watch?v=uS7WAHv3Ktk](http://www.youtube.com/watch?v=uS7WAHv3Ktk) - made entirely with linux! > cat /proc/asound/card1/codec#9
gives me an error "No such file or directory"

I am connected via HDMI, but can also use S/PDIF.
I guess HDMI would be preferred, but I guess it would be good to have options for different setups...and to just have a better understanding, to get both working.

I basically understand what you are saying, in that certain types of connections support certain formats/encodings.  I just want to be able to record OTA HD TV and play it back via 5.1...preferably HDMI I guess.

first and most obvious question is: does the audio stream from your HD TV broadcaster contain 5.1 audio?

Running mediainfo on a recorded file will tell you.

---

### Post by davidstoll on 2011-08-29
> **nickrout said:**
> Coincidence: same here. [http://www.youtube.com/watch?v=uS7WAHv3Ktk](http://www.youtube.com/watch?v=uS7WAHv3Ktk) - made entirely with linux! 


I would expect nothing less.  ;)
That's very nice.  I made a similar thing for our viewing, but not with the text/story...nice touch.

> **nickrout said:**
> 
first and most obvious question is: does the audio stream from your HD TV broadcaster contain 5.1 audio?

Running mediainfo on a recorded file will tell you.

Most (of my) HD recordings do, some don't (some SD with regular old stereo).

---

### Post by BicyclerBoy on 2011-08-29
My silly mistake..sorry.
The 3, 7, 8 & 9 physical map to the logical 0, 1 ,2 & 3..

So connect the HDMI receiver (TV) with it turned on..
cat /proc/asound/card1/codec#3

---

### Post by davidstoll on 2011-08-30
> **BicyclerBoy said:**
> My silly mistake..sorry.
The 3, 7, 8 & 9 physical map to the logical 0, 1 ,2 & 3..

So connect the HDMI receiver (TV) with it turned on..
cat /proc/asound/card1/codec#3

$ cat /proc/asound/card1/codec#3
Codec: Nvidia GPU 14 HDMI/DP
Address: 3
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x10de0014
Subsystem Id: 0x10de0101
Revision Id: 0x100100
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x04 [Audio Output] wcaps 0x72b1: 8-Channels Digital Stripe CP
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
Node 0x05 [Pin Complex] wcaps 0x407381: 8-Channels Digital CP
  Control: name="IEC958 Playback Con Mask", index=3, device=0
  Control: name="IEC958 Playback Pro Mask", index=3, device=0
  Control: name="IEC958 Playback Default", index=3, device=0
  Control: name="IEC958 Playback Switch", index=3, device=0
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=05, enabled=1
  Connection: 1
     0x04

---

### Post by BicyclerBoy on 2011-08-31
cat /proc/asound/card1/eld#3.0

---

### Post by davidstoll on 2011-08-31
> **BicyclerBoy said:**
> cat /proc/asound/card1/eld#3.0

$ cat /proc/asound/card1/eld#3.0
monitor_present		0
eld_valid		0

---

### Post by BicyclerBoy on 2011-08-31
That's bad..

1. Did you have the TV or HDMI receiver turned on ?
2. The TV is directly connected ?
3. No AVR HT amp involved ?
4. The nVidia X server gdm GUI was running ?
5. That command was not run from console ?

The nVidia driver only supports X screen output.

Maybe you should post your 
/var/log/Xorg.0.log

dmesg | grep HDMI

---

### Post by davidstoll on 2011-08-31
> **BicyclerBoy said:**
> That's bad..

1. Did you have the TV or HDMI receiver turned on ?
2. The TV is directly connected ?
3. No AVR HT amp involved ?
4. The nVidia X server gdm GUI was running ?
5. That command was not run from console ?

The nVidia driver only supports X screen output.

Maybe you should post your 
/var/log/Xorg.0.log

I'm connected directly to my multiple HDMI input amp and then out to the TV.

I guess I could do it the other way, but then I have to change 2 sets of inputs each time I want to view a different source.

I also have optical out from the TV that feeds back into the amp, so I can choose optical passed through from my TV or just use the HDMI before it passes to the TV.

Gui is running, it was run from a command line, TV and amp was turned on...I was in front of the tv/amp/computer when I ran it....not via ssh.

---

### Post by BicyclerBoy on 2011-08-31
When using HDMI input (multi-channel):
TVs will NOT output AC3 5.1 from S/PDIF output.

I suspect your AVR HT amp is the problem.
The HT amp should have its own ELD data.
This has been a recent problem with windows as well..only plagues some HT amps.

Please connect the HDMI video card direct to the TV & then re-post the ELD info..

With your TV pass-thru' soln:
How do you listen to music etc ?
Not from PC ?

---

### Post by davidstoll on 2011-08-31
> **BicyclerBoy said:**
> When using HDMI input (multi-channel):
TVs will NOT output AC3 5.1 from S/PDIF output.

I suspect your AVR HT amp is the problem.
The HT amp should have its own ELD data.
This has been a recent problem with windows as well..only plagues some HT amps.

Please connect the HDMI video card direct to the TV & then re-post the ELD info..

With your TV pass-thru' soln:
How do you listen to music etc ?
Not from PC ?

I don't really listen to music... :/

Ok, no amp, only a direct HDMI connection to the TV...

```
$ cat /proc/asound/card1/eld#3.0
monitor_present		1
eld_valid		1
monitor_name		SAMSUNG
     
connection_type		HDMI
eld_version		[0x2] CEA-861D or below
edid_version		[0x3] CEA-861-B, C or D
manufacture_id		0x2d4c
product_id		0x392
port_id			0x20000
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x1] FL/FR
sad_count		1
sad0_coding_type	[0x1] LPCM
sad0_channels		2
sad0_rates		[0xe0] 44100 48000 88200
sad0_bits		[0xe0000] 16 20 24
```

```
$ dmesg | grep HDMI
[869607.281713] HDMI hot plug event: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=0
[869607.292105] HDMI status: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=0
[869607.348763] HDMI hot plug event: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=1
[869607.357528] HDMI status: Codec=3 Pin=5 Presence_Detect=1 ELD_Valid=1
[869608.129512] HDMI: detected monitor SAMSUNG
[869608.129514]       at connection type HDMI
[869608.129518] HDMI: available speakers: FL/FR
[869608.129524] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200, bits = 16 20 24

```

---

### Post by BicyclerBoy on 2011-09-01
So now we know:
a. your AVR amp does not correctly support ELD
b. your amp works with 2 ch PCM over S/PDIF
c. your TV only accepts 2ch PCM at CD & 48KHz & 2xCD rates. NO AC3, NO 5.1 LPCM.
d. why only speaker-test -c 2 -r 48000 -D hw:1,9 works   (2 ch only)

What we do **not** know:
if your TV (if a digital tuner) may output AC3 (int. tuner only).
if your AVR amp accepts AC3 or DTS matrix encoded S/PDIF.

Further tests:
speaker-test can not test AC3 5.1 over S/PDIF, So see if you can find this test track...
www_lynnemusic_com_surround_test.ac3

Play it after launching VLC like this..
vlc --aout alsa --alsa-audio-device iec958

Other:
In MythTV 0.24+fixes, the audio code supports up-mixing to 5.1-AC3 to be output over S/PDIF digital pass-thru'. But if your audio gear does not accept or decode there is no point. Then your only multi-channel option is analogue 6 cables.

---

### Post by davidstoll on 2011-09-03
> **BicyclerBoy said:**
> So now we know:
a. your AVR amp does not correctly support ELD
b. your amp works with 2 ch PCM over S/PDIF
c. your TV only accepts 2ch PCM at CD & 48KHz & 2xCD rates. NO AC3, NO 5.1 LPCM.
d. why only speaker-test -c 2 -r 48000 -D hw:1,9 works   (2 ch only)

What we do **not** know:
if your TV (if a digital tuner) may output AC3 (int. tuner only).
if your AVR amp accepts AC3 or DTS matrix encoded S/PDIF.

Further tests:
speaker-test can not test AC3 5.1 over S/PDIF, So see if you can find this test track...
www_lynnemusic_com_surround_test.ac3

Play it after launching VLC like this..
vlc --aout alsa --alsa-audio-device iec958

Other:
In MythTV 0.24+fixes, the audio code supports up-mixing to 5.1-AC3 to be output over S/PDIF digital pass-thru'. But if your audio gear does not accept or decode there is no point. Then your only multi-channel option is analogue 6 cables.

Thanks for suggesting that test file.  It makes things much more clear.  Normally, I have to find some random show and sort of guess if it's 5.1.

Ok, so playing that sound file and launching VLC as you described, it clearly shows that I can get 5.1 via optical and coaxial.  I don't get anything via HDMI.

However, I do get audio via a Windows machine over HDMI into the same amp, but it is only stereo...not sure if it is outputting 5.1 and the amp is down grading to stereo or if the Windows machine is just outputting stereo.

My TV has an optical audio out.  Are you saying that if it got 5.1 via HDMI, that it cannot pass that to the amp?

It also sounds like I got what I paid for with regards to my amp...?

I might like to replace it.  So, I need to get one with ELD and 5.1 PCM support?  Any other specs I need to look for?

---

### Post by BicyclerBoy on 2011-09-03
Launching VLC as I described, & with your default audio setup, will only work with your alsa iec958 device  card0. It was a test of the HT amp over S/PDIF.
So this was not a test for HDMI AC3.
The ELD data shows that not possible:
- your TV does not accept AC3 5.1 or LPCM 5.1 over HDMI.
- your amp does not report any ELD.

So we now know the HT amp works with:
- 2 ch PCM S/PDIF
- matrix 5.1 AC3 S/PDIF digital pass-thru'.
You could test with windows & capture the ELD data to compare.. 

Most HT amps with HDMI have ELD/EDID management options because:
-  they have different audio capability to the display
-  can upscale video/resample audio for the display
-  could cache the display EDID/ELD so it can be left switched off.

Does your amp have any OSD setup? Any ELD settings ?
This OSD may only work on the analogue video jacks. 

Slight possibility:
The TV may output AC3 but only from a broadcast TV via internal tuner or playback from USB memory stick or DLNA server. These signals would have to have AC3 5.1 soundtrack, the TV will not transcode. Your TV HDMI input shows no AC3 or 5.1 LPCM support.

My idea of a good HT amp is that it is measured in kilograms..more the better.

---

### Post by nickrout on 2011-09-03
I have given up helping here as BicyclerBoy has more knowledge than me. However I have a question. My setup does not show any eld info at all. I have 195.36 nvidia drivers and alsa-utils 1.0.22 (all rather old but it works fine, I am just interested in why I don't have eld info). This is the first time I have read about eld, I have gleaned that it is gathered by the X driver and passed to the audio system, but can't find any documentation at all.

EDIT: Looking at the README for the latest nvidia drivers led me to this:

[ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html](ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html)

Wading through it now, but it answers the question why I have no ELD info:

> Early chipsets (ION an earlier) do not support PD or ELD information. In this case, the ALSA driver assumes that a monitor is always attached, and supports all audio features, including those which your monitor may not actually support. Newer chipsets and all GPUs support PD and ELD.

I have an ION :)

---

### Post by BicyclerBoy on 2011-09-03
Hi Nick,
Survived the latest shaking okay ?
How much earthquake wax does it take to stop a DFP TV falling to the floor ?

That nvidia readme popped up about 9 months ago & dispelled a lot of myths (no pun intended).
[http://http.download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html](http://http.download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html)
[http://ubuntuforums.org/showthread.php?t=1668737](http://ubuntuforums.org/showthread.php?t=1668737)

I thought it was posted to the mythtvnz mailing list..

The missing ELD data from OP's HT amp explains why he did not get error messages when outputting unsupported audio modes.
I guess, in some situations, this could be useful.
 
But I didn't think to quiz him earlier about the HDMI connection to TV.

---

### Post by nickrout on 2011-09-03
> **BicyclerBoy said:**
> Hi Nick,
Survived the latest shaking okay ?
How much earthquake wax does it take to stop a DFP TV falling to the floor ?

Yeah, quakes are chicken feed now, but I don't appreciate being woken at 3.30 am!

My Sony 46inch fell on the centre speaker on 22 Feb and the resulting hole in the panel was pretty unsighltly. Replaced it with the latest LG 55inch 3D job, very nice and uses cinema glasses which is sweet. Managed to find a 3D copy of Avatar online which shows it ff well. The wife enjoyed it more on the TV than in the cinema! 

But as a normal 2D panel it is also great, love it!

It is fixed firmly to the wall with a strong bracket. If the wall falls over, I have more problems than just the TV!

> That nvidia readme popped up about 9 months ago & dispelled a lot of myths (no pun intended).
[http://http.download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html](http://http.download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html)
[http://ubuntuforums.org/showthread.php?t=1668737](http://ubuntuforums.org/showthread.php?t=1668737)

I thought it was posted to the mythtvnz mailing list..

The missing ELD data from OP's HT amp explains why he did not get error messages when outputting unsupported audio modes.
I guess, in some situations, this could be useful.
 
But I didn't think to quiz him earlier about the HDMI connection to TV.

Maybe was posted to the NZ mailing list, I don't get to read it all :)

---

### Post by BicyclerBoy on 2011-09-03
I guess around the time that document surfaced you were rather preoccupied with other matters. !

Very sensible precautions with the bracket, we should all be doing the same thing.

---

### Post by davidstoll on 2011-09-04
> **BicyclerBoy said:**
> Launching VLC as I described, & with your default audio setup, will only work with your alsa iec958 device  card0. It was a test of the HT amp over S/PDIF.
So this was not a test for HDMI AC3.
The ELD data shows that not possible:
- your TV does not accept AC3 5.1 or LPCM 5.1 over HDMI.
- your amp does not report any ELD.

So we now know the HT amp works with:
- 2 ch PCM S/PDIF
- matrix 5.1 AC3 S/PDIF digital pass-thru'.
You could test with windows & capture the ELD data to compare.. 

Most HT amps with HDMI have ELD/EDID management options because:
-  they have different audio capability to the display
-  can upscale video/resample audio for the display
-  could cache the display EDID/ELD so it can be left switched off.

Does your amp have any OSD setup? Any ELD settings ?
This OSD may only work on the analogue video jacks. 

Slight possibility:
The TV may output AC3 but only from a broadcast TV via internal tuner or playback from USB memory stick or DLNA server. These signals would have to have AC3 5.1 soundtrack, the TV will not transcode. Your TV HDMI input shows no AC3 or 5.1 LPCM support.

My idea of a good HT amp is that it is measured in kilograms..more the better.

I don't see ELD or EDID anywhere in the setup.  If I were to look for a replacement amp (I like the way to measure the quality of an amp by the way), would it literally say ELD/EDID on the box or in the manual?

---

### Post by BicyclerBoy on 2011-09-04
I would hope that EDID management would be stated on the box.
It is possible that is covered off by hdmi compliance..

None of the big-brand consumer electronics manufacturers (TVs) make good audio gear.
But no point having HQ amp & rubbish speakers, so need to find a balance & it needs to suit the size of your room & wallet, the type of music/movies & how loud..
Movies are typically engineered to sound good on cheaper gear & anything is better than TV speakers.
The reasonably priced Wharfedale Diamond 9s have excellent performance so don't have to spend a fortune.
Made in Japan is a good thing but getting rare.
Marantz Yamaha Denon Pioneer Onkyo are good.
Sony does have a small ES range that can deserve respect.
I think all the brands have cheap models that under perform.

There are some very good midi/mini size systems, but they don't cost much less..

avsforums
audioreview

---

