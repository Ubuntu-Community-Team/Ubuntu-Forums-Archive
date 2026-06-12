---
title: "iPhone!"
date: 2009-07-07
forum: Multimedia Software
---

### Post by philcamlin on 2009-07-07
hey guys i got my iphone 1st gen yesterday off ebay and i had a touch

question: how od i sync it with ubuntu 

if i cant well il going to have to leave ubuntu :| and then reinstall to dualboot :(

i really dont want to leave but i might have npo other choice 

can someone point me how to do this 

2.2.1 unlocked if anyone needs details :popcorn:

and the guide everyone says to looik at doesnt seem to work 

****

when i get to the command thats liek this i get an error :(

phil@phil-desktop:~$ none /proc/bus/usb usbfs devgid=123,devmode=664 0 0 
bash: none: command not found
phil@phil-desktop:~$ 


can someone help PLEASE! im desperate :D

---

### Post by Ratscallion on 2009-07-07
I choose not to use Ubuntu for iPod syncing, i use my dual boot of Vista (I know, I know) and use iTunes to sync. You could, however, get a virtual machine, shove windows in there, and try it that way?

---

### Post by philcamlin on 2009-07-07
yeah sadly thats where my issue falls in 

i have 1 80 gig hdd 

with ubuntu only :)

can i partition it without screwing anything up and dualboot and then all i do is reinstall GRUB?

---

### Post by philcamlin on 2009-07-07
well it looks like im going ot format with xp then reinstall in partiton 

ill see you guys later :)

when i get all my ubuntu stuff straight :popcorn::popcorn:

i really dont want to leave :(

---

### Post by Ratscallion on 2009-07-07
I suggest just going ahead with partitioning. No need to format or change GRUB really. I do, however, suggest backing up ALL data before partitioning, even though there is a small chance of errors, the chance is still there.

---

### Post by AnimeOmega on 2009-07-07
You don't need to dualboot! Just install Virtual Box ([http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)), not the open source edition (OSE) you'll need USB support. Create a dynamically expanding virtual hard drive and install Windows XP + iTunes. Install guest additions and enable USB support in the options. Add your user to vboxusers. You wont need Wine and youll be able to sync your iphone/itouch, it will use up about 2GB. 

More detailed instructions in [http://www.google.com.pr/search?hl=es&ei=HqdTSuTED4OytwfqzsCdCA&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=ubuntu+virtualbox+sync+iphone&spell=1](http://www.google.com.pr/search?hl=es&ei=HqdTSuTED4OytwfqzsCdCA&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=ubuntu+virtualbox+sync+iphone&spell=1)

or [http://www.samlesher.com/ubuntu/virtualbox-with-usb-support-on-ubuntu](http://www.samlesher.com/ubuntu/virtualbox-with-usb-support-on-ubuntu)

(URL tags are not working?)

---

### Post by teh'p3nsi0n3r on 2009-07-22
for those who wish to use virtualbox as AnimeOmega suggested.

[http://ubuntuforums.org/showthread.php?t=1208906&highlight=iphone](http://ubuntuforums.org/showthread.php?t=1208906&highlight=iphone)

---

### Post by not2slo128 on 2009-08-07
Hi everyone.  I'm looking for a solution for the Iphone 3g S.  I'm very new to the iPHone, relatively new to Ununtu (running 9.04 btw) and have a little Linux experience.

I've read about WINE, the Virtual Box, and about some bluetooth method, all of which dont appeal that much to me.

Optimally, would like to sync via USB.  Is it do-able?  If not, what are my options?

TIA

---

