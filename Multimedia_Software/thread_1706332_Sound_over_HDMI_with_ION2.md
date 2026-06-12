---
title: "Sound over HDMI with ION2"
date: 2011-03-13
forum: Multimedia Software
---

### Post by domovoi on 2011-03-13
Greetings,

I have a Giada Slim-N20 running XBMC-Live 10.1 (Ubuntu v.10.04.1).  It is hooked up by HDMI to my two-speaker TV.  I don't think XBMC is my problem, however.  Out of the box, XBMC supports sound over HDMI (if you tell it to use it), but when I try to run ZSNES, I only get sound through the headphone jack on the side.

Now, the one problem with XBMC is that menu sounds go through the default device (i.e. the headphone jack) rather than the device selected in its settings (in my case, the HDMI port).  In order to fix that problem, my .asoundrc looks like this:
```
pcm.!default {
        type plug
        slave {
            pcm "hw:1,3"
        }
}
```

Unfortunately, this does not fix ZSNES for some reason.  Even worse, I no longer get sound through the headphone jack.

What does fix ZSNES, however, is this strange hack that has been making the rounds on the XBMC forums.  First, you download a modified version of HDA-Intel.conf found [here](http://pastebin.com/f2e38265).  It appears to route everything through pcm.!remap-surround71.

Then, you use this asound.conf:
```
pcm.!hdmi-remap {
type asym
playback.pcm {
type plug
slave.pcm "remap-surround71"
}
}

pcm.!remap-surround71 {
  type route
  slave.pcm "hw:1,3"
  ttable {
    0.0= 1
    1.1= 1
    2.4= 1
    3.5= 1
    4.2= 1
    5.3= 1
    6.6= 1
    7.7= 1
  }
}
```
Finally, you use this .asoundrc:
```
pcm.dmixer {
type dmix
ipc_key 1024
ipc_key_add_uid false
ipc_perm 0660
slave {
pcm "hw:1,3"
rate 48000
channels 2
period_time 0
period_size 1024
buffer_time 0
buffer_size 4096
}
}

pcm.!default {
type plug
slave.pcm "dmixer"
}
```
This almost fixes everything.  Unfortunately, when I try playing a video with AC3/Dolby Digital, I get a screechy, garbled mess.  Videos with mp3 and DTS work fine, however.

The ALSA wiki is thoroughly unhelpful.  I honestly have very little idea what the asound files or the modified HDA-Intel.conf are trying to do.  My guess is that something with the 7.1 mapping is screwing up AC3.  And my hunch is that such a hack is way too complicated just to tell ZSNES to use the HDMI port.

And, yes, ZSNES is instructed to use SDL or ALSA (neither appears to make a difference).

Does anyone have any insight on this?  Or can point to some sort of ALSA tutorial so I can try figuring it out myself?

---

### Post by domovoi on 2011-03-13
Never mind I figured it out.  Interesting how typing out my problem clarified certain things for me.

---

### Post by rubylaser on 2011-03-13
You could post your fix in here for others in the future that my experience similar problems.  I ended up going with Openelec.tv on my Shuttle XS35GTs and I couldn't be happier.  They come with the .asoundrc for all popular ION devices baked right in.

---

### Post by Macragge on 2011-04-23
I'm running Linux XBMCLive 2.6.32-29-generic #58-Ubuntu on a Shuttle XG35GT, and I had the same problem mentioned above where sound worked fine in XBMC over HDMI, but the menu noises and Zsnes played through the default device.  

aplay -l
```
root@XBMCLive:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

As you can see, the default device is the Intel sound card.  I was able to specify which sound card to use by creating /etc/asound.conf

```
root@XBMCLive:~# cat /etc/asound.conf
pcm.!default {
    type hw
    card NVidia
    device 3
}
ctl.!default {
    type hw
    card NVidia
    device 3
}

```

Note: I used "card NVidia" in case the kernel detects the devices in a different order, or a future kernel update screws with something.  

So thats it, there was no need for the funky hack mentioned above.  I haven't noticed any problems with AC3/Dolby Digital either.  I hopefully someone finds this helpful down the road.

---

