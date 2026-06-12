---
title: "Achilles heel of Ubuntu is the Xserver!"
date: 2007-10-30
forum: Multimedia &amp; Video
---

### Post by bwallum on 2007-10-30
Why is it not possible to get a stable Xserver? It crashes and bangs about, invents monitor frequencies, never seems to boot up the same way twice and is the thing that sucks up most of my maintenance time. I get 10 minutes of a dvd before it falls over because it can't seem to handle any longer time between getting its' mouse/keyboard event fix.

Does anybody have a sound xorg.conf file? Is there any way of stopping X from filling it with mush? 

I guess I have to become an X expert to get to the bottom of what should be taken for granted, i.e. having the screen work.

I'm not normally prone to ranting but this Xserver malarkey takes the biscuit.

Where can I find a manual on how to write a foolproof xorg.conf file please and encase it in titanium so that X can't fiddle with it?

Kind Regards
Bob

---

### Post by bwallum on 2007-11-01
errrhh...my Xserver has suddenly become a lot more stable following a nVidia driver update. I am feeling the full effect of about a dozen yolks running down my visage....:oops:

---

### Post by Rhapsody on 2007-11-01
Mine's not looks so good. I'm stuck at a 60Hz (which gives me serious headaches on this CRT) with no obvious way to get any other resolution. I've found changing the monitor driver can seriously mess up the display (to the point of it being unusable) and although installing the NVIDIA binary driver served as a partial fix previously, surely I don't need that just to change the refresh rate!

---

### Post by bwallum on 2007-11-01
Ah.. the best thing to start with is list your rig specs in your signature, There are quite a lot of permutations!. I have been around the houses on this, delighted to help out, but need to know what you are running on. The Linux boys will say open a terminal....I'm not quite that advanced! The upside is every post gets you noticed, possibly by somebody who can fix it.

---

### Post by Mcavity on 2007-11-01
you should be able to go into  etc>x11>xorg.conf and change the refresh rate.  though you will have to sudo it orlboot unbunto into root.

---

### Post by Rhapsody on 2007-11-01
> **Mcavity said:**
> you should be able to go into  etc>x11>xorg.conf and change the refresh rate.  though you will have to sudo it orlboot unbunto into root.
Yeah, problem is xorg.conf says I can [use 85Hz right now](http://ubuntuforums.org/showthread.php?t=599603). This PC has a habit of not making any sense.

---

### Post by bwallum on 2007-11-01
What is you rig please? Something like 32bit, you will know if you are 64bit-your graphics card, and...can't think of much else at the moment...lets get you sorted!

---

### Post by bwallum on 2007-11-01
well...cough man, cough...tell us.

---

### Post by Rhapsody on 2007-11-01
The video is a bit of a mystery, integrated stuff on an ASRock motherboard described as "GeForce 6-class". I know it's NVIDIA stuff (the NVIDIA drivers have worked before) and that it can output 1024x768@85Hz (it was doing it this morning), so that should be OK.

The monitor is a Samsung SyncMaster 793s, with 1024x768@85Hz being well within spec.

I don't have the NVIDIA restricted drivers installed, and I'm using the generic monitor driver (because using the specific driver listed cause the display to become completely unusable).

---

### Post by bwallum on 2007-11-01
What os are you running on now?

That is operating system, maybe Windows or Oubuntu or MAC(its a good 'un so include it)

---

### Post by Rhapsody on 2007-11-01
Kubuntu 7.10, I made a fresh install (formatted root, kept home) earlier today.

---

### Post by bwallum on 2007-11-01
What is your video card?

---

### Post by Rhapsody on 2007-11-01
I just stated that it's integrated on an ASRock motherboard (a K8NF6G-VSTA to be precise) and the manual states it to be "GeForce 6-class". That's everything I know about it.

---

### Post by bwallum on 2007-11-01
Ok , sorry to have missed the prompt.

I think you need the nvidia-glx-new driver.

go into System>Administration>Synaptic Package Manager and then search for nvidia-glx-new

If you do not have it (green sqaure) then install it.

Then open a terminal and do this cut and paste:-

```
sudo nvidia-xconfig
```

See how things are then report..I'm with you until we resolve this.

---

