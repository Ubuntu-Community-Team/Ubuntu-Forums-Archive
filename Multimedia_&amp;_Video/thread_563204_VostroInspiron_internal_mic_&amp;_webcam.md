---
title: "Vostro/Inspiron internal mic &amp; webcam"
date: 2007-09-29
forum: Multimedia &amp; Video
---

### Post by irwjager on 2007-09-29
Hi all,

Has anyone been able to get their internal microphone working on a Dell Vostro 1400/1500/1700 or Inspiron 1420/1520/1720?

I'm thinking the webcam (in my case Bus 003 Device 002: ID 05a9:2640 OmniVision Technologies, Inc.) should probably provide a generic usb audio device, but it doesn't :(

[   31.028646] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 1
2 14:12:24 PDT 2007
[   31.126181] Linux video capture interface: v2.00
[   31.242182] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:26
40)
[   31.243047] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   31.244095] usbcore: registered new interface driver uvcvideo
[   31.244100] USB Video Class driver (v0.1.0)
[   31.395995] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 21

As you can see, there's nothing at all in dmesg that points to an internal mic, and the internal soundcard ( Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog])  doesn't record anything when i try the all the sources (Mic, Front Mic and Line In). I can hear it switch turning up everything to MAX; each source produces distinct background noise when amplified, so everything seems to work fine.

The webcam only works with luvcview, but not with any other apps. Has anyone had any success with other apps?

I've tried a lot of things; compiling latest ALSA drivers (10.15.rc3), latest kernel (2.6.23-rc8 ), but to no avail. Any pointers?

Thanks!

Ivo

---

### Post by ankursmart on 2007-10-22
No luck.....I tried the same thing, audio/speakers work...but the microphone (internal) doesn't work.

Upgraded to gutsy, still no luck. Haven't tried any plugged-in microphone. 

Anyone any idea?

---

### Post by delino on 2007-10-23
No idea!

I have the same issue,  Audio/speaker works but nothing with my built in webcam.

I have just installed Ubunto 7.04 on my inspiron 1420. (I hope I don't have to go backto vista!!!) 

Any help would be more then appreciate!

thanks

---

### Post by daageep on 2007-11-18
I would like some more information also. My vostro 1400 is running like a champ except for the internal mic. 

since the skype beta is out. i need the mic working =)

---

### Post by chauster on 2007-11-24
I also have this problem.  I can't seem to get internal mic on my Inspiron 1420 to work in the Sound Recorder.  Everything else seems to be working great, haven't tested the webcam though.  Has anyone found a fix for this?

---

### Post by flowbot on 2007-11-24
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153963](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153963) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				First of all, you need to enable the **gutsy-proposed** repository in synaptic, then reload the repos. You should now have an upgradeable **linux-backports-modules** which you need to install. Once installed, reboot, then launch **alsamixer**.

In the playback channels, scroll across to **Digital Input Source** and ensure that **Digital Mic 1** is selected:

[img]http://i188.photobucket.com/albums/z30/gnuworld/screenshots/Screenshot.png[/img]

Then hit **F4** to go to capture channels, go across to first **Capture** channel and hit the spacebar to enable capture. Then go to the **Digital** channel and turn it right up:

[img]http://i188.photobucket.com/albums/z30/gnuworld/screenshots/Screenshot-1.png[/img]

Your webcam mic should now be working.

However - i think a bit of work needs to be done, as the capture volume on this mic is pretty low ... test it out in Skype or something and add your reports to the launchpad bug referenced at the top of  this post.

---

### Post by adithyu85 on 2007-11-25
hey,

has this been tested positively on Vostro 1400? because I tried goofing around once with backports etc, which screwed even internal speakers.

I had to reinstall Ubuntu after that.

Would be glad to hear some good news.

---

### Post by flowbot on 2007-11-25
not sure about vostro 1400 ... i have insprion 1420 with STAC9228 audio chip. if vostro has same audio chip, it should work.

---

### Post by mushroomcloudwarrior on 2007-11-30
Same problem with the microphone, on my vostro 1500.

Just got the sound working, and headphone jack works muting the external speakers. Now if only i can get my mic to work!

---

### Post by mushroomcloudwarrior on 2007-11-30
and my alsa mixer just looks like this, doesn't have most of the options you have there;

[IMG]http://i36.photobucket.com/albums/e37/mushroomcloudwarrior/snapshot8.png[/IMG]

(i'm using kubuntu 7.10 if it makes a difference.

---

### Post by hasher on 2007-12-04
It kind of works and I suspect this is the right track. For the last poter, there is nothing wrong with your ALSAMIXER, just go to where it says PCM and use the right arrow key untill it show  "Digital Input Source" and then follow the tutorial posted above.

---

### Post by luisasolarf on 2007-12-09
Hi, it seems that no one knows a solution to get working the integrated mic. I have a 1420 with web cam working on skype, amsn, and ekiga, even a few other programs to capture pictures and videos. But I haven't could enable the integrated mic. I have conected a wired external mic and it works perfectly, that's the only way to have a nice skype conversation. THe beta 2.0 of skype works well for video but compiz activated I can see the video, but the receptor does receive the video. 
Please if someone have a way to make the integrated mic to work please!!! POst it!

---

### Post by malagutista on 2007-12-26
Has anyone tried the new 2.6.24-Kernel? Any results with it? 

I read that the hardy 8.04 rc2 has come out with that Kernel, so maybe this issue gets resolved with that...

---

### Post by chokas on 2008-01-25
Hi all, I have a VOSTRO 1500

My lshw gets the following for the audio device

```
 *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
```

And lsusb shows the following for my webcam
```

Bus 007 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. 
```

At first with a fresh installation of gutsy I didn't get the audio to work, so I had to update the kernel and that did the trick. I posted this in another thread so here's the link..

[http://ubuntuforums.org/showpost.php?p=4109859&postcount=37](http://ubuntuforums.org/showpost.php?p=4109859&postcount=37)

And I got the webcam to work finally today following this easy steps from the gentoo wiki

[http://gentoo-wiki.com/HARDWARE_Dell_Inspiron_1520](http://gentoo-wiki.com/HARDWARE_Dell_Inspiron_1520)

You have to do the following:

 Download svn trunk

```
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
```

      Insert the id product in uvc_driver.c

/* after line 1661 */
/* OmniVision OEM Dell Notebook */
	{ .match_flags		= USB_DEVICE_ID_MATCH_DEVICE
				| USB_DEVICE_ID_MATCH_INT_INFO,
	  .idVendor		= 0x05a9,
	  .idProduct		= 0x2640,
	  .bInterfaceClass	= USB_CLASS_VIDEO,
	  .bInterfaceSubClass	= 1,
	  .bInterfaceProtocol	= 0,
	  .driver_info		= UVC_QUIRK_PROBE_MINMAX },

 Compile and install

```

make
make install
```

 Load driver

```
modprobe uvcvideo
```

AND NOW TEST IT WITH gstreamer-properties or with amsn, Ready for webcam calls :guitar: !!

amsn gave me some bugs, and a black image, but I adjusted the settings within a chat window changing my display picture and clicking on "webcam snapshot" ;), hope this helps.

---

### Post by Termina on 2008-02-05
> **malagutista said:**
> Has anyone tried the new 2.6.24-Kernel? Any results with it? 

I read that the hardy 8.04 rc2 has come out with that Kernel, so maybe this issue gets resolved with that...

I tried, no luck. Both with dist-upgrade, and an actual 8.04 alpha CD.

Vostro 1400 without webcam, with mic.

---

### Post by Termina on 2008-02-05
While I see a 'Digital' field in Playback, there is no way to change/selecet any text in that. It seems to be empty.

Is there something I can do about this? I am using, in /etc/modprobe.d/alsa-base
options snd_hda_intel model=5stack

---

### Post by Janus23 on 2008-07-11
I am having this problem on an Inspiron 1420n.  I am using 7.10.  Alsamixer doesn't show me the digital here - instead it shows "Analog L" and information says analog loopback off.  Can anyone tell me how to toggle this to digital?

---

