---
title: "[SOLVED] Can't log into ubuntu after filling my hard drive"
date: 2007-07-18
forum: Multimedia &amp; Video
---

### Post by Peregrine88 on 2007-07-18
So I'm pretty new to Ubuntu but finally got the dvd::rip working the other night. I set a bunch of files to start transcoding overnight and accidentally filled my entire drive. I thought I had enough space, I had been deleting .vob files to make room.

I'm not able to log in anymore, I get an error message something to the effect "Cannot log you in, cannot write authorization file." I'm assuming I'm getting this error because my entire drive is full.

My two questions- Does ubuntu keep files on the drive in some sort of trash file? If so and even not, can I use the live cd (which I'm using now to write this) to go in and empty the trash or delete some files that I choose? I tried deleting something already but I don't have the right permissions. Please help, I want to keep learning new things and not being able to log in hinders that process.

---

### Post by phidia on 2007-07-18
First if you want to remove files in the CLI (command line interface) you want to type > sudo rm <filename> <enter> 
That command will ask for your password and you should have no problems removing what you want.
If you want to use the livecd you could do it that way too. If you needed a root gui interface in the livecd you would type > gksudo nautilus

---

### Post by meierfra on 2007-07-18
You might try booting in recovery mode (press Esc during boot up to get to the grub boot  menu)

---

### Post by Peregrine88 on 2007-07-20
Thank you, I went in with the terminal and deleted a file and now I'm back in. :guitar:

---

