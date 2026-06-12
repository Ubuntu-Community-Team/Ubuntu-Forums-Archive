---
title: "Can't get 1280x1024 with x300 in 7.04"
date: 2007-07-13
forum: Multimedia &amp; Video
---

### Post by Synth3t1c on 2007-07-13
I've been looking for quite a while, and can't get my ATI Radeon x300 to work with 7.04.

Can someone tell me what to do?

---

### Post by Synth3t1c on 2007-07-14
bump please, any help is appreciated

---

### Post by patrickjlbyrne on 2007-07-23
You have my sympathy. I also have an X300 and can't set 1440x900 with the open-source (radeon) driver. The LCD monitor reports it is being driven at 1152x864. Something is skew-whif, presumably the driver. If I find a solution I will post it here!

PS I have gotten 1440x900 working with the restricted (ATI) driver, though that doesn't support compositing/desktop effects.

Ho hum.


-P

---

### Post by fredj on 2007-07-24
I had a similar problem with the nvida driver, it would only work at 800x600 instead of 1240x1024.
Here is how I fixed it. First you need to get your monitor specs. In particular you need to know the range
of vertical refresh rates it will accept (this is specified in kHz and is usually something like 30-80.
You also need to know the range of vertical refresh rates it will accept usually something like 60-75 (this
is specified in Hz).
Then I edited the xorg.conf file with 'sudo gedit xorg.conf' (back it up first)
I added these two lines to the Monitor Section (before the End Section line)
HorizSync 30 - 80
VertRefresh 60 - 75
Then make sure that the display size you want is at the front of every mode line i.e add "1240x1024" at the
beginning of every mode line if its not already there.

---

