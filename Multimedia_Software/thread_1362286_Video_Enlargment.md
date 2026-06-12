---
title: "Video Enlargment"
date: 2009-12-22
forum: Multimedia Software
---

### Post by solaralchemy on 2009-12-22
I have had a recent problems with videos. When I play back videos in either VLC or Totem. The videos can only play in small format. When I enlarge them I lose the video, however the audio is still there.  Sometimes I will have half the video image with blocks of it missing which is really weird.
This didn't happen until the last few weeks before that video played fine I havn't really done anything that I can recall that might effect any of the packages.
Anybody have some possible troubleshooting tips?

---

### Post by lavinog on 2009-12-23
First thing i would do is disable desktop effects.

What video card do you have, and have you enabled a proprietary driver for it?

---

### Post by solaralchemy on 2009-12-23
When Desktop effects are turned off video plays normaly. When I switch compiz with the cube and awn dock back on however I get video performance issues again. My computer is an older Acer laptop is there something I can run from the comand line to find out what the video card is? Maybe I will have to reduce my desktop effects to get full screen video.
thanks for the help though its a start in the right dirrection.

---

### Post by lavinog on 2009-12-23
```

lshw -c video

```

---

### Post by solaralchemy on 2009-12-23
ok this is what I got

 description: VGA compatible controller
       product: Radeon RV250 [Mobility FireGL 9000]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=66 mingnt=8

---

### Post by lavinog on 2009-12-23
Ok that card isn't supported by ati's fglrx driver anymore so the open source drivers are your only option.

What version of ubuntu are you using?  The open source drivers in karmic are supposed to have better 3d support.

---

### Post by solaralchemy on 2010-01-06
Actually im ussing Mint 7 though the issue should not be a big issue since I recently got a new Dell Vostro with Ubuntu on it I imagine that it will not have any graphic problems....im happy I didn't have to pay the windows tax.

---

