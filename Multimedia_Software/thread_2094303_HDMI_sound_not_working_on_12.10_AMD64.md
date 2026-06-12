---
title: "HDMI sound not working on 12.10 AMD64"
date: 2012-12-13
forum: Multimedia Software
---

### Post by checoimg on 2012-12-13
Hi I'm tryin to watch movies on my TV. The TV is recognized and video works but I don't find the ubuntu studio audio controls to get the HDMI to work.

I have two options in the output tab of the Sound configuration tool "Speakers" and "Digital Audio (S/PDIF)"
The second one doesn't get HDMI audio to work.

---

### Post by dannyboy79 on 2012-12-13
whats listed under the devices tab? also, what graphics card are you using?

---

### Post by N00b-un-2 on 2012-12-13
I've used this in the past to fix problems with HDMI audio.  [http://crunchbang.org/forums/viewtopic.php?id=2310]("http://crunchbang.org/forums/viewtopic.php?id=2310")

---

### Post by checoimg on 2012-12-13
> **dannyboy79 said:**
> whats listed under the devices tab? also, what graphics card are you using?
Thank you for your response dannyboy79
  I'm using a "Intel HD Graphics" as says in the sticker outside and the driver says "unknown" experience standard ( System Details ). 
Where is that Device Tab ?

---

### Post by dannyboy79 on 2012-12-13
have you tried installing pavucontrol? It allows for much more control over pulseaudio and your audio devices. I believe the devices tab is the second tab within pavucontrol 

Also, did you check out the link the other person posted?

---

### Post by checoimg on 2012-12-13
> **N00b-un-2 said:**
> I've used this in the past to fix problems with HDMI audio.  [http://crunchbang.org/forums/viewtopic.php?id=2310](http://crunchbang.org/forums/viewtopic.php?id=2310)
  Ok so I did "aplay -l" and got:

card 0: Intel [HDA Intel], device 0: ALC271X Analog [ALC271X Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC271X Digital [ALC271X Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

That tells me HDMI is on Card 0

so then I did "sudo alsamixer -c 0"

Used the arrows to red-select S/PDIF and hit "m" to unmute.
Then back to Sound preferences by entering "Sound" on Dash home search; The HDMI device was there and everything worked fine when selected.

---

### Post by checoimg on 2012-12-13
Thank you dannyboy79 and N00b-un-2 for your time.

---

### Post by dannyboy79 on 2012-12-13
> **checoimg said:**
> Thank you dannyboy79 and N00b-un-2 for your time.awesome you got it working. use the thread tools to mark it solved.

---

### Post by N00b-un-2 on 2012-12-17
I'm glad I was able to help.

---

