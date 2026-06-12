---
title: "USB DV Capture Issue"
date: 2009-04-26
forum: Multimedia Software
---

### Post by Anquietas on 2009-04-26
Hello,

I have a Panasonic DV Camcorder, using USB Connection and miniDV Tape... I want to extract some videos I recorded on the tape.

Can you recommend me a good program please ? I've searched for one, came up with Kino, but it doesn't support USB Capture...

What should I use to rip the movie from my DV Camcorder ?

---

### Post by MooseMagnet on 2009-05-02
You didn't get a reply. Hmmm. Not good news. I'm trying to do the same thing. I purchased a composite-to-USB cable along with software for 10 bucks, but it's XP not Ubuntu.

Anyone know of a linux app that will capture DV via USB.

---

### Post by liame on 2009-07-06
some problem here,
with a sony handycam. i think the problem is that *buntu doesn't recognize the cam as being connected to the usb,
i read on the kino site that kino only can capture by using firewire :(

---

### Post by PaulWhipp on 2010-01-17
I have the same problem with my panasonic NV-GS25 but I am making some progress with solving it and I can now dump my movies to the computer:

install dvgrab with synaptic.

Check what device your camera is appearing as (its probably /dev/video0) by watching what turns up in /dev when you plug in its USB cable.

Use the following command substituting your usb camera device and a filename base of your choice for lucas:
```

~/video/capture $ dvgrab -V -input /dev/video0 lucas

```

Press play on the camera.

When done you should have a lucas001.dv file.

The dvgrab function just sits there even after you finish but the file plays OK even though I killed it with ctrl C (which churns out lots of error stuff).

If anyone can point me at a guide for dvgrab I would be grateful. If not, I'll try to develop this into a decent howto as I work out more.

---

### Post by Jose Catre-Vandis on 2010-01-17
Hmmm...with my Sony Handycam I get an audio1 and a mixer1 created in /dev, but not video, and dvgrab doesn't like either of those!

```
dvgrab -V -input /dev/audio1 party
Error: v4l2reader.cc:70: In function "virtual bool v4l2Reader::Open()": "ioctl( VIDIOC_QUERYCAP, &cap )" evaluated to -1
v4l2reader.cc:70: errno: 22 (Invalid argument)terminate called without an active exception
Aborted

```

```
dvgrab -V -input /dev/mixer1 party
Error: v4l2reader.cc:71: In function "virtual bool v4l2Reader::Open()": condition "!( cap.capabilities & V4L2_CAP_VIDEO_CAPTURE )" is trueterminate called without an active exception
Aborted
```

Just "upgraded" to a new PC without firewire so have lost this option, which worked well.

---

### Post by edward2536 on 2010-01-17
Hi have had this running for quite a while now and have not received a reply. I have to download into XP. Now it will work IF i invest in a firewire card and fit that in my computer. How many people have firewire compared to USB ? not that  many unless you in to MAC. Panasonic make the software for Windows but nothing for MAC or Linux. I will try paulwhipp's suggestion and let you know what happens.

---

### Post by edward2536 on 2010-01-17
Hello
I have tried what paulwhipp said, but no luck. ubuntu did not recognize my Panasonic dv camera. Checked in dev as instucted and only viewed a ddr ? file. it did recognize my memory card which is in the camera. Will try anything as feed up with windows!

---

### Post by PaulWhipp on 2010-01-17
edward2536 - Just a possibility - Remove the card from your camcorder and try again. See if that leads to the ubuntu drivers creating a video device for you. It may be that they give up after creating the card device.

---

### Post by edward2536 on 2010-02-02
no did try with the card out ,but to no avail. will keep try ing  and in the death may have to go the fire wire way, thanks for trying it is appreciated.

---

### Post by PaulWhipp on 2010-02-02
Sorry I can't be more help edward2536. 

These issues are particularly hard for FOSS because there is so much varied hardware out there. Without the particular video camera I can't offer anything more.

Perhaps upgrading to 9.10 (it includes wider driver support I believe) but thats a big step.

Your other bet is to go to [_canonical support_]("http://www.ubuntu.com/support/services"). Its quite expensive but I've found it worth the money. They are very tenacious and the problems get fixed.

---

### Post by no2498 on 2010-02-05
with no card in the cam try this

open a terminal type ( gstreamer-properties ) click enter
click video
try v4l1 or v4l2
click the bottom test button
hope this helps

---

### Post by LintonHanes on 2010-02-25
Edward - just a thought - it seems right to put your cam in the 'pc' mode and then plug it in, but you have to put it in (video) 'play' mode then plug it in...

I'm a lucky one anyway, I have the gs25 and I used
ls /dev/sd*
ls /dev/vid*
ls /dev/d*
then plugged it in and repeated the above :: I got /dev/video1

..will be back soon also

Paul - ubuntugeek gets straight to the point - while introducing the planet's ugliest program -
[http://www.ubuntugeek.com/open-movie-editor-a-simple-non-linear-video-editor.html](http://www.ubuntugeek.com/open-movie-editor-a-simple-non-linear-video-editor.html)

---

### Post by PaulWhipp on 2010-02-25
Thanks for the link Linton.

After dvgrab, I've been using kino to make the movies and devede to compile them into a DVD with a menu.

Kino is easy to use so long as you are just cutting and splicing or adding simple fade ins etc.

Devede works fine but can only handle a simple menu/chapter structure - I did find myself wanting submenus for kids karate gradings and the like which it doesn't handle.

kino an devede are both in the standard ubuntu repositories.

Quality of the result is not great though - it looks better direct from the camera. I think it will be improved if I can stay with the DV format throughout.

I'll take a look at openmovieeditor next time I dump the tapes and burn more dvds.

---

### Post by G0lg0thaZA on 2010-02-27
Thanx for this. First time I'm trying this in Ubuntu. I used the following command after I figured out it was /dev/video0 as well for me.

Code:
```
 dvgrab --autosplit --format dv2 --size 0 --opendml -V -input /dev/video0 myVideoOutput 
```

Then just press play on the camcorder and watch the files being created. :-D

Awesome. Panasonic NV-GS35 with USB cable connection.

---

### Post by Timokl on 2011-03-30
> **PaulWhipp said:**
> Use the following command substituting your usb camera device and a filename base of your choice for lucas:
```

~/video/capture $ dvgrab -V -input /dev/video0 lucas

```

Press play on the camera.

When done you should have a lucas001.dv file.

This method worked fine for me. I used a Panasonic NV-GS75 camcorder with Ubuntu 10.10 and USB connection.

I could not capture directly into Kino, but for my purposes it's ok to rip the .dv files and load them into Kino manually.

---

