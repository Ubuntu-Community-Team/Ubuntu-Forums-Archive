---
title: "Remote sound with X"
date: 2008-09-18
forum: Multimedia Software
---

### Post by timandjulz on 2008-09-18
I am using xvfb to run a headless box.  I want to be able to hear sound (listen to music, hear alerts, etc.) when remoting into my virtual desktop.

My understanding is that X does not support sound.  Is there some other method I can use to get the full desktop experience over the wire?

Thanks,
Tim

---

### Post by huwnet on 2008-09-18
Pulseaudio will work as a network sound server :).

[Here](http://blog.paulbetts.org/index.php/2007/04/15/pulseaudio-in-ubuntu-feisty-play-sound-over-the-network/) is an Ubuntu article about this, although I don't know if it will still work in 8.04

---

### Post by timandjulz on 2008-09-18
Thanks huwnet.  I'll do some checking on this.

It appears that vmware does not like alsa/pulseaudio.  But I may be able to get it working well enough.

I was hoping to avoid wiring up my own solution.  The Linux community is in desperate need of a remote desktop solution like what Windows has.  Exposing local hardware to the machine running the applications, and without having to install/configure multiple tools, would be very useful.

---

### Post by HDave on 2009-04-16
Where did this end up?  I have the same situation as the OP and was just wondering....thanks.

---

### Post by Chris Musampa on 2009-04-16
I just use ssh x forwarding from my laptop to run amarok on my desktop (which has speakers and subwoofer)

ssh username@desktop -X amarok

I have set up publikey authentication for ssh and have the above command in a launcher icon on the laptop, works like a dream.

---

### Post by HDave on 2009-04-16
> **Chris Musampa said:**
> I just use ssh x forwarding from my laptop to run amarok on my desktop (which has speakers and subwoofer)

Wow -- good to know it "just works."  Now I feel stupid for not "just trying it."  Guess I outsmarted myself....

---

### Post by Chris Musampa on 2009-04-17
Note to self: Read threads properly rather than when running out the door :frown:

I've had Freenx forward sound (with gnome) in the past.

---

