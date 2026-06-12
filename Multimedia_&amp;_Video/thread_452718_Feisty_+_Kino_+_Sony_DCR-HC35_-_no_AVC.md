---
title: "Feisty + Kino + Sony DCR-HC35 - no AV/C"
date: 2007-05-23
forum: Multimedia &amp; Video
---

### Post by ahickey on 2007-05-23
Hi,

I am running Kino on Feisty and I'm capturing video.
It all appears to work perfectly except that I cannot control the camera from within Kino.

If I start to play from the camera it wll do the capture, but I was hoping to control it all from inside Kino.

Under Preferences in Kino in the 1394 tab there is no device listed  in the AV/C device list and my camera is listed under dv1394 devices '/dev/dv1394/0'

I know the camera can be controlled from softwares as I did it under Windows using Ulead Video Studio.  
This is a completely different system, so the 1394 card is new.

Any thoughts or assistance greatly appreciated.

Thanks,
Albert.

---

### Post by SammyBoy247 on 2007-07-19
Same problem.  Have had several long sessions trying to fix this but no luck.

---

### Post by Unterseeboot_234 on 2007-07-21
If you take the time and the total pain to build Kino from source AFTER you build ieee1394 with all its dependencies, you would set the option for the kino build to --with-dv1394 option

**[recent online kino docBook page]("http://www.kinodv.org/docbook/")**

In that doc they say this option to control camera with dv1394 will be deprecated in favor of making it part of the linux core (whatever that means).

At one time, I had the buttons "alive" in the Capture Panel in an AMD-64 built kino I did. That feature hangs kino if you shuttle the tape back and forth too much. Lately, I've been using the downloaded Synaptic version and it works with the camera on Play. Then I go back and edit the bulk capture later. Any stills, I use the captured dv, not the camera. That's one big difference over a stand-alone capture card which could only make a still from the  camera's dv tape.

---

### Post by TheJunklizard on 2007-09-09
I have the same trouble with my Canon HV20, and also Kino doesn't seem to support High Def. 
However if I log in as root, the AV/C works fine. I've changed ownership of  dev/dv1394/0 but didn't help. Not sure what I'm missing here?!? Give root a try and see

---

### Post by canakas on 2007-09-18
Hi guys,

I had the same problem

This worked for me:
take a gksudo nautilus window, and set group permission on the file /dev/raw1394 to a group you are member of... for instance video (check your group memberships by typing groups in terminal)

then restart kino... av/c is alive and the playback starts and stops. .no winding it seems

hope this helps.

oh and my camera is a canon DM-200iE

---

