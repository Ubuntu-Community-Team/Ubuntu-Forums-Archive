---
title: "Why is A2DP in Ubuntu such a difficult thing to do?"
date: 2009-02-05
forum: Multimedia Software
---

### Post by lavadisco on 2009-02-05
I've been trying for about 1.5 years now to get my laptop, currently running Intrepid, to send bluetooth audio (A2DP) to a little bluetooth receiver hooked up to my stereo. I have read and tried multiple tutorials and solutions (all very convoluted and non-intuitive) on this website that have worked for others, but nothing has worked for me. I can browse the files on my cell phone via bluetooth no problem, so I know the hardware is working.

I am really only writing here because I'm surprised that more attention hasn't been paid to this issue by the kind folks who program the OS. Is this a fringe usage for bluetooth, and thus not worthy of their attention? Do you think I can expect this issue to be resolved in Jaunty? How can I find that out?

---

### Post by markbuntu on 2009-02-05
You can talk to the people at bluez.org since they are the ones developing the bluetooth drivers.

---

### Post by Aqualung on 2009-04-03
> **lavadisco said:**
> I've been trying for about 1.5 years now to get my laptop, currently running Intrepid, to send bluetooth audio (A2DP) to a little bluetooth receiver hooked up to my stereo. I have read and tried multiple tutorials and solutions (all very convoluted and non-intuitive) on this website that have worked for others, but nothing has worked for me. I can browse the files on my cell phone via bluetooth no problem, so I know the hardware is working.

I am really only writing here because I'm surprised that more attention hasn't been paid to this issue by the kind folks who program the OS. Is this a fringe usage for bluetooth, and thus not worthy of their attention? Do you think I can expect this issue to be resolved in Jaunty? How can I find that out?I hear ya brother, I've been complaining about this for aeons. Let's make a little noise, perhaps we'll start making some waves, who knows!

---

### Post by doudou4978 on 2009-04-20
Markbuntu, I don't know if you're right.
The bluez stack is used in Maemo (linux for Nokia internet tablet). It runs fine for all protocols. It means there is a lack of support to open the power of this software on the desktop distros.
The lack of fresh informations (tutos, howto etc.) is very disturbing. We are always directed to wiki which are one, two or three years old.
I understand the question:
Why is A2DP in Ubuntu such a difficult thing to do?

---

### Post by markbuntu on 2009-04-20
It is not, now, if you use a 2.6.29 kernel and alsa 1.0.19 and pulseaudio 0.9.15 and bluez 4.35 or later and gnome bluetooth 2.27.4 your A2DP should work with just a few mouse clicks. 

In Ubuntu this should all be in the Koala release in September though I think you can find ppas in Launchpad for all that which will work in Jaunty now. I believe all of this is in Mandriva 2009 now and in Fedora in the rawhide repository.

It is pretty easy to tweak a distro for one particular set of hardware (Mac OSx, Nokia tablets, etc) but to make that stuff work generally for a zillion different machines requires a lot of widescale plumbing changes.

It just took a while to get it all together.

---

