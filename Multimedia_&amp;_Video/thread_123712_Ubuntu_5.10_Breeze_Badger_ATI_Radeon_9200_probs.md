---
title: "Ubuntu 5.10 Breeze Badger ATI Radeon 9200 probs"
date: 2006-01-30
forum: Multimedia &amp; Video
---

### Post by Mickey1 on 2006-01-30
Before anyone gives me any links on how to compile stuff...

I'm extremely new to linux and i mean exactly that
I know barely anything about it but i like it so i am willing to learn 

I have Ubuntu up and running but on my onboard graphics card 
I also have an ATI Radeon 9200 256 MB card in my pci slot

Whenever i go into bios and set my graphic selection to be the onboard source 
Ubuntu works fine , boots fine and functions fine

When i choose my graphics card selection to be pci (Radeon card) 
When ubuntu boots up and does all the checks it seems to constantly freeze when it comes to 
```

Starting hotplug subsystem

```

I've tried updating my drivers manually but i don't think i should be messing with this on my own 

I have posted this on several help forums but noone has been able to come up with a solution

Hope this will be the place :-)

Cheers,

---

### Post by Mickey1 on 2006-02-02
Any1?

---

### Post by Mickey1 on 2006-02-08
under lspci 
I get two listings for my card 
I reckon that one of those could be my tv-out?
It's listed as an unknown device
Could this be why the hotplug subsystem makes my system freeze on startup?

---

### Post by Mickey1 on 2006-02-08
I reckon i should actually give up on this 
as i posted this a wek ago with 69 views and no replies...
cheers anyway

---

### Post by Razorback on 2006-02-09
I have done the same thing you have as far as video except when I changed to the PCI card my pc hung and errored on the X driver.  I had to reconfigure the xserver-xorg file.  Try ctrl-alt-f1 when it hangs to get to the command line. Then type "sudo dpkg-reconfigure xserver-xorg" to reconfigure for the new graphics card.  You will be taken through questions about your hardware settings including video.  Complete all the answers and save then reboot.  You can do this by typing sudo reboot.  HTH

---

### Post by shuttleworthwannabe on 2006-02-09
You're right about posts just lying there. I have had some posts for weeks before someone actually responds. But,hey, we have to be patient, and just suck it up.

BTW: the wiki's are an excellent place to start: for my ATI fireGL mobility V5000, I followed this [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

it is works like a charm; Ubuntu is th efirst distro I tried that worked on thsi graphics card. Others (MEPIS, SUSE) I struggled with.

HTH

---

