---
title: "HDMI out video nvida"
date: 2010-11-03
forum: Multimedia Software
---

### Post by Gamicon on 2010-11-03
I have an HP laptopwith nvidia geforce (8600 I believe) with HDMI out. I have a Toshiba flatscreen I picked up last xmas. 

For a long time I was running wubi dual boot with windows until linux somehow erased itself. 

Anyways, back then I knew how to set the second monitor (IE my tv) to scale down th screen to fit, instead of just epanding beyond the edges zoomed into the center of the screen.

Now that I am running Ubuntu 10.10 by itself as a stand alone os on my laptop I can seem to get the settings correct for this anymore.

Can anyone help me out with this?

---

### Post by tommcd on 2010-11-03
It is good that you got away from Wubi and did a real Ubuntu install to a dedicated linux partition on your hard drive.

To verify what nvidia card you have, post the output of this from the terminal:
```
lspci | grep -i vga
```
Did you install the nvidia driver and nvidia-settings?
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
You want to use the *nvidia-current* driver for your card.
You should be able to use (I think!) nvidia-settings to adjust the second monitor.

How did you setup the Toshiba TV before?

And welcome to the Ubuntu forums!

---

