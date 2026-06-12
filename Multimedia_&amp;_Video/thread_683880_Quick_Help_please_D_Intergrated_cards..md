---
title: "Quick Help please :D Intergrated cards."
date: 2008-01-31
forum: Multimedia &amp; Video
---

### Post by lestatxxx on 2008-01-31
Hmm i've somehow lost the command under 

(initramfs)

so that it will be able to open my /etc/modprobe.d/blacklist      file

I've looked in varius forums, but I only get the sudo gedit command to open it via a GUI. I've booted with Break=Bottom so that I may modify and blacklist my onboard video display and use my PCI card.'



If anyone remembers what I must do first to be able to access /etc/modprobe.d/blacklist it will be of much help, thanks in advance.

PS

I'm currently at the Initramfs prompt.

---

### Post by Skerit on 2008-01-31
The initramfs prompt? 

If you want to edit a file in the shell you can always use nano (my favorite) or vi (don't like it, but let's not get into that age-old discussion, lol)

---

### Post by lestatxxx on 2008-01-31
hmm I think its Vi or Vim now that you mention it, I've tried nano and it tells me that it isnt a command under (initramfs) prompt.


Meh tried vi also, but still says Invalid mode: vi or vim, same as nano. <--Edit


I know it involves chroot or chmod, but I can't really get the full command to execute ><.

---

### Post by lestatxxx on 2008-01-31
Update -

I'm able to open the file now, somehow I was able to log in as root, but now when I sudo nano /etc/modprobe.d/blacklist 
I get a read-only error ><

---

### Post by lestatxxx on 2008-01-31
Bump*

No one knows? 

Damn I should've copied it down on a notebook lol, now I'm stuck and forgot where I got the info from last time ><...


Sry for the post after post, but trying to renew to see if someone knows the solution.

---

### Post by Yellow Pasque on 2008-01-31
Your root filesystem probably got mounted as read-only. You need to remount with rw option (and the -n argument), so:
```
mount -n -o remount,rw /
```

---

### Post by lestatxxx on 2008-01-31
Now under I get this


(initramfs) nano : not found
 " " " " " "   sudo : not found


and when I try to /root to gain root permission, it says

/bin/sh: /root: permission denied 

wah this is getting worst everytime lol.


I do remember though, that the command was underthe (initramfs) shell, ( the command to let me edit my /etc/modprobe.d/blacklist file )



**Edit** also I can do a    

cat /etc/modprobe.d/blacklist to view the currently blacklisted files, but if I try to edit the file, I'd get a read only error.

---

### Post by Yellow Pasque on 2008-01-31
I'm kind of lost as to why you're at the initramfs prompt. What happens when you try to boot normally?
Regardless, you should be able to log in as root, remount the / filesystem with the command I gave above, and then vim the file you need to. When you first open vim, press 'i' to put it into normal editing mode. When you're done making changes, press 'Esc' and then type ':x[Enter]' to write the file.

Also, can you not just disable the onboard video in the BIOS?

---

### Post by lestatxxx on 2008-01-31
Well lol, my motherboard doesn't allow me to turn off onboard, although I can choose which is the primary display, but ubuntu tends to detect the onboard first and not my agp/pci card and thus resulting in the so famous freeze splash screen at startup.

When I boot,  I choose ubuntu then hit esc, then I edit the kernel from silent splash to  break=bottom; so that I can boot to the initramfs which will allow me to edit my /etc/modprobe.d/blacklist and black list agpgart and intel_agp, which controlls the onboard device.

It has been solved already,  but I've been looking like a madman and haven't been fortunate enough to find the forum or post  in which the solution was in ><


Also I can't recall how to log in with root permissions after I'm at the (initramfs) shell prompt.

---

### Post by Yellow Pasque on 2008-01-31
You can't boot into a normal "recovery mode" terminal?

> Also I can't recall how to log in with root permissions after I'm at the (initramfs) shell prompt.Try: ```
su
```

Also, wouldn't this be easier to do with a LiveCD?

---

### Post by lestatxxx on 2008-01-31
Normal recovery will hang, just like the splash screen, the screen freezes and  also freezes my other devices ei; keyboard, mouse, cd rom, and the only way to get back is by force reboot.

When I su  in the (inintramfs) prompt I get

sh: su: not found

same for sudo, and nano. Its really weird, I might have to try and reinstall the OS.

---

### Post by Yellow Pasque on 2008-01-31
Yeah, your issues seem to run deeper than video drivers. Hopefully, you have a separate home partition. THat should make reinstalling a lot easier.

---

### Post by lestatxxx on 2008-01-31
Yeah, as it turns out windows can be useful at times for certain things like these XD. Anyways, thanks alot dude, I'm going to reinstall ubuntu studio and see how it goes.

---

### Post by Yellow Pasque on 2008-01-31
> **lestatxxx said:**
> Yeah, as it turns out windows can be useful at times for certain things like these XD. Anyways, thanks alot dude, I'm going to reinstall ubuntu studio and see how it goes.
Np. Good luck.

---

