---
title: "Choppy Video...Low Resolution"
date: 2006-08-12
forum: Multimedia &amp; Video
---

### Post by sbjaved on 2006-08-12
I've just installed ubuntu (Hooray!) and i like it a lot. However there are some minor snags: 
(a) Video plays choppy...I'm using a Radeon 9200SE 128MB card which  is running on 'ati' driver supplied with ubuntu
(b) Low resolution...i am getting 800x600 res while my monitor and card can support 1028x764 and 32-bit colors instead of 24-bit
(c) Sound doesn't play continously during a song...like some sort of buffering is going on...(My soundcard is recognized by ubuntu)

The 'ati' drivers are probably for 2D acceleration...should i install "fglrx"? Would it work with my card? Plus what about the sound?

---

### Post by baldy1324 on 2006-08-12
here are the solution to the first two problems-
> 
(a) Video plays choppy...I'm using a Radeon 9200SE 128MB card which is running on 'ati' driver supplied with ubuntu
solution-use the flgrx driver-im not familiar with ati cards but if you install the linux-restricted-modules package for your kernel
run this command```
sudo apt-get install linux-restricted-modules-`uname -r`
``` (enter your password if it prompts)
this will install the restricted drivers for your kernel-then run ```
gdksudo gedit /etc/X11/xorg.conf
```
scroll down to the part where it says Driver "ati" in the Device section and replace it with flgrx.
then log out and press CTRL-ALT-BACKSPACE (this restarts the xserver)-that problem should be solved


> (b) Low resolution...i am getting 800x600 res while my monitor and card can support 1028x764 and 32-bit colors instead of 24-bit
go into your xorg.conf (gksudo gedit /etc/X11/xorg.conf) and go down to the Screen section. then at the last Subsection that says 24 depth and lists your resolution add 1024x764 before the other resolution. so it should looked something like this althought my monitor runs at 1280x1024.
```
SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection

```

and 32-bit colors is almost the same but it uses different encoding to get the pixels on the screen.

> (c) Sound doesn't play continously during a song...like some sort of buffering is going on...(My soundcard is recognized by ubuntu)

you can run sudo alsaconf and follow the instructions to reset your alsa (advanced linux sound architecture) configration. not sure but worth a try!!!

hope this helped

---

### Post by sbjaved on 2006-08-13
Thanks man, 
Resolution now 1024x768 :)
Sound Card working beautifully :))

However about that "fglrx" thingy...I use a dial-up and my Motorola SM56 Internal PCI Modem is still unrecognized and unconfigured...(Request to Linmodems sent) 

So is there anyway i can download 'fglrx' driver on windows and transfer it to Ubuntu...Also that question goes for "Easy Ubuntu"???

---

