---
title: "Alright, again."
date: 2007-01-25
forum: Multimedia &amp; Video
---

### Post by RyanOmailley on 2007-01-25
I really don't see what the linux fuss is about as I can't get ANYTHING to work!

The first time I tried to install it it froze at 86% everytime. Also, I had to go into windows and change me screen resolution, refresh rate, and run in 16bits for it to even go into the Live option.

Now, after burning a new DVD and doing a text install, I have managed to install the OS sucessfully, however I am getting the bouncing "Input not supported" box and the rest of the screen is black.

I am using an ATI AIW x600

---

### Post by Garyu on 2007-01-25
First of all, welcome to the Ubuntu community. I hope you will find your time here as rewarding and fun as most of us regular visitors do.

Let me begin by adressing your post. When you choose a title for your post, try to make it as informative as possible. "Alright, again" will not tell people anything about your problem, and so people who are sitting on the solution to your problem might miss your post. A better title would have been something on the lines of "Can't get ATI video to work on install" or something similar.

Also, I understand that you are frustrated, but beginning your post with a complaint about linux in general will not make people motivated to answer your post. Linux is very popular for several good reasons. Each user have their own reasons for making the switch from other operating systems to Linux, and I hope you will find your own reasons to do this. The fact that you have noticed that there is "a big fuss about linux" should give you a hint that there is actually something good to be found here, even if you happen to have some problems with your particular hardware.

Now, to adress your problem. I am not familiar with ATI cards, so I'm not sure if your card is supported or not (I always use nvidia and I have never experienced any problems). A good place to start is this wiki page: [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)
There you will be able to see if your particular hardware is supported. Also, you should check this list before you buy any new hardware to make sure it will work when you plug it in. I checked for your ATI video card, and it is not in the list. There is, however, an entry for the x700 model, which might be similar to yours. A tip from that page:
> if X server does not start with driver "Ati" (first boot) change it to "vesa" and then follow the instructions on BinaryDriverHowto. On some manufacturer's cards (I think Abit, a red card) openGL doesn't work, gdb says crash happens in the driver.
So it seems you might be more successful if you specify your card as a VESA card.

I would actually always recommend a text install since I find that to be more reliable. But when you describe your process to start a graphical install with the Live option, you mention changing video options in Windows? You should try to boot from the CD, rather than starting it from your existing Windows installation.

EDIT: 
oh, right, if you don't know how to change driver to VESA... Try running this command in a terminal:
```
sudo dpkg-reconfigure xserver-xorg
```

EDIT2:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
You should also visit this page to make sure you've got the binary driver for your ATI card running. The link was on the previously mentioned hardware wiki page, but the link was not copied to this message.

---

### Post by RyanOmailley on 2007-01-25
Thank you for the help.

> if X server does not start with driver "Ati" (first boot) change it to "vesa" and then follow the instructions on BinaryDriverHowto. On some manufacturer's cards (I think Abit, a red card) openGL doesn't work, gdb says crash happens in the driver.

I don't know what how to do this or check anything.

> I would actually always recommend a text install since I find that to be more reliable. But when you describe your process to start a graphical install with the Live option, you mention changing video options in Windows? You should try to boot from the CD, rather than starting it from your existing Windows installation.

I'm not sure what you mean here. I did do a text install.

And, I don't know what the terminal is or how to access it.

---

### Post by Garyu on 2007-01-25
> **RyanOmailley said:**
> I don't know what how to do this or check anything.

Sorry, there are two ways for you to access the terminal if you get a black screen when booting.

1) Press Ctrl-Alt-F1 when the screen goes black and everything is loaded. This should bring up a text-mode screen where you can login. Then run the command I stated above:
"sudo dpkg-reconfigure xserver-xorg"

2) When the GRUB bootloader shows up, go down one step using the arrow keys to "Recovery mode". This should give you the same terminal with a login. Then run the above command.

If you want to reboot your computer from terminal mode, just write in the terminal:
```
sudo reboot
```

---

