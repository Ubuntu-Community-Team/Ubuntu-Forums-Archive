---
title: "There WAS sound.."
date: 2008-06-16
forum: Multimedia Software
---

### Post by Bizly on 2008-06-16
First off, i'd like to say hi to everyone, im new to both the Ubuntu forums and linux itself, and well I have a bit of a dilemma, when I first installed Ubuntu on my computer I had sound, and well, now I don't. 

And theres a speaker icon with a cross over it, and when I double click the icon I get 2 pop-up windows, one of which tells me:

**No volume control GStreamer plugins and/or devices found.**

and the other:

[B]
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.[/B]

I went and reinstalled the GStreamer plugins I had using Synaptic, but I still have the same thing, the only thing I remember doing prior to this problem was installing the NVIDIA drivers for my video card..

---

### Post by Erlander on 2008-06-17
When you boot up and see the message that GRUB is starting press the Esc key to see the GRUB menu and select one of the earlier kernels installed.  If that cures the problem it is the kernel you have been using.  You could then uninstall it in Synapatic if you wish.

Rob

---

### Post by GreenLantern33 on 2008-06-17
Did that work for you?  I have the same problem

---

### Post by bazookapenguin on 2008-06-17
Yeah, I have the same problem too. Did what Erlander say work?

---

