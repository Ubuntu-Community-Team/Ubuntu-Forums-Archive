---
title: "Problems starting Ubuntu"
date: 2006-07-17
forum: Multimedia &amp; Video
---

### Post by khdx on 2006-07-17
Hello

I have looked around this forum and posted a couple of weeks ago, but no one replyed or had an answer for my problem.

I have a Dimension 2350 with onboard video, but I have disabled it and I'm using a FX5200 vid card.  I installed xp and it works correctly.  I then installed ubuntu for a duel boot.  It installed fine.  When I go to startup ubuntu, it freezes at the the bootable GUI at "Loading hardware devices".  When I try to start it up in the terminal mode (safe mode?) it gives me a kernal panic error, then freezes.  

I then enabled the onboard video, reinstalled and it works fine.  I tried to disable the onboard and reconfigure the xorg, same thing as above happened.  I tried the live CD and the live CD did the same thing as noted above when I had the onboard disabled.

I am sorta new to linux, but have gotten ubuntu installed on my laptop.  Now I just want to install it on my desktop since I really like this distro.  Can anyone help me with my problem?

Thanks
Kevin

---

### Post by khdx on 2006-07-18
Can anyone help?

---

### Post by tseliot on 2006-07-18
1) Plug the card in and connect your monitor to it.

2) Boot in Recovery Mode (you can boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer)

3) type:
```
lspci | grep VGA
```

and write down the output on a piece of paper (there's no need to post it right now).

OR (if you don't want to use a piece of paper)
```
lspci | grep VGA > /home/your_username/videolist.txt
```

OF COURSE replace "your_username" with your username.

You will find the output of that command in /home/your_username/videolist.txt

You might need that output later

4) Type: 
```
sudo nano -w /etc/X11/xorg.conf
```

Put a # before the BUSID in the section Device
Set the driver to "vesa"

CTRL+X to exit

5) reboot:
```
sudo reboot
```

and boot as usual.

If that doesn't work (explain me what happens) please post the output you got in step 4

---

### Post by khdx on 2006-07-18
I selected recovery mode in the grub boot.  It booted text wise.  When it got to loading hardware drivers, it gave me this:

Kernel panic - not syncing: Fatel exception in interrupt

Then it froze.  If I enable the onboard, it will boot right back up.

---

### Post by khdx on 2006-07-19
bump

---

### Post by tseliot on 2006-07-19
You might try upgrading the BIOS of your motherboard

---

### Post by khdx on 2006-07-19
Its has the current version for the dimension 2350 (which is A02).

---

### Post by exautt on 2006-07-20
I've got a VERY similar problem to KHDX, only i have an older dell (L667r) and am using a Geforce 4000MX PCI. I found that when i use my onboard card, Ubuntu Live CD boots right up, but when using my PCI Geforce, it locks up just as the GUI tries to start. Normally this wouldnt be a big deal for me, but I use the PCI Geforce for its S-Video output to go to a TV. Like KHDX I am also kinda new to the whole linux scene. any help would be appreciated.
     UPDATE (5 mins after i posted original) // I tried booting into safe graphics mode and it spit back an error message.
[Go here to see it.]("http://www.box.net/public/q25o4z9ho6")

---

### Post by BigJerm on 2006-07-20
I have the exact same problem, except for system specs. I have a Radeon 9200 SE PCI, and it freezes when it gets to the *loading hardware drivers*. The freeze does not occur when I use my onboard graphics card. I cannot for the life of me figure out this problem, and I have approached the problem many different ways. All of which have failed. Me and a friend, cannot figure this out. I would imagine it might be a option in the BIOS that is conflicting with Linux, or could be straight out the graphics card. I am currently using Phoenix BIOS. Any help is greatly appreciated.

---

### Post by khdx on 2006-07-24
It seems like this is a problem with multiple people, yet no fix?

---

### Post by khdx on 2006-07-31
I'm still having problems with this, anyone know of a fix?

---

### Post by nmanglani on 2006-08-03
I have a similar problem with my laptop (Dell Precision M60). It will stall at "loading hardware drivers" if I do no have my power chord plugged in. With the power chord it boots just fine. I'm not exactly sure but it's possible that this issue began after installing my wireless card and net manager.

---

