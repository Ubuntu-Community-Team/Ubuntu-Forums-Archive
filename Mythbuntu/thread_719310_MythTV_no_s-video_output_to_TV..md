---
title: "MythTV no s-video output to TV."
date: 2008-03-09
forum: Mythbuntu
---

### Post by jetsurgeon on 2008-03-09
Hello Folks,

New Ubuntu Linux user here, as well as MythTV user.  Just finished setting up Mythbuntu and everything works except one detail which I need some help with.

The problem is I get no video out to my 27" RCA (tube) television, once I boot into Gnome or MythTV.  

How to I enable MythTV to output to the TV?

Myth works just fine on the monitar which is hooked up to the box.

Also I noticed when I reboot the box, I get the computers POST and Ubuntu orange horizontal loading bar on the TV and Monitar, but after the horizontal bar goes away, the TV just goes blank, while the monitar always works.

The sound works just fine, output to the speakers.

I've got a NVidia Geforce 5500 video card as well as a Hoppauage WinTV-PVR 150.  The monitar s hooked up to the monitar port on the GeForce Card, and the S-VIDEO on the Geforce 5500 is hooked up the the TV input.

Is there hope???   Can you help me out with this problem?

Thanks in advance!!!!!!

Jeff

---

### Post by hardyn on 2008-03-09
its going to be more a function of the nvidia driver, and not mythtv.

i have never had a good go with it, it always too a big of editing of the xorg.conf file.
but you can rough it out using 'sudo nvidiaconfig'  (at least i think nvidiaconfig is right, im not on my ubuntu machine right now)

good luck.

---

### Post by jetsurgeon on 2008-03-10
Got it figured out, I had to run "nvidia-settings" and reconfigure both screen settings.

I had to reduce the monitar resolution to match the 27" tube tv, set both outputs to "twinview", and then set them both to mirror.

That fixed her up.  :KS

Now when I reboot, gnome and mythtv is mirrored on both the monitar and tv like it should.

Thanks!

---

### Post by rickyble on 2008-03-10
Two things

1-Can you tell exactly which driver you are using. 
2-Have you tried the DVI output?

I have the exact card and it will boot and find the tv on the svideo and function correctly.  If I boot on DVI it will find the tv on the connection but it display incorrectly.  If I pull up the NVIDIA config it does not show the tv as a monitor to configure.  Thanks

---

