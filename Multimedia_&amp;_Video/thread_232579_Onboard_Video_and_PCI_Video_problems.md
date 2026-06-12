---
title: "Onboard Video and PCI Video problems"
date: 2006-08-08
forum: Multimedia &amp; Video
---

### Post by skattman83 on 2006-08-08
I am trying to set up ubuntu on an older machine using the Intel i810 chipset.  The onboard video can be set as secondary, but not disabled.  I want to use my geforce 6200 pci card to pull the strain off of the cpu and system memory.  The problem I am having is I don't know how to make this work.  When I tried to boot up using the PCI card, it works until about halfway through the initialization process for Ubuntu.  It gives me a black screen with a cursor in the upper left corner.  If I remove the PCI card and use the onboard, it works fine, which is how I got it installed.

So thats the situation.  Basically, I have a computer with linux on it, and now I want to see if I can't trick it into using the pci card over the onboard graphics.  I was thinking that I could install the drivers and such for the pci card, and edit out the onboard stuff from the xorg.conf file.  Would this work, or is there somewhere else that checks to see if there is a display adapter?

---

### Post by Dr. Nick on 2006-08-08
is your 6200 a pci?

I know it can be done if you edit your xorg.conf file, namely the BusID section. I know how to do this if the 2 cards are differnt interfaces, but not if they are both pci

---

### Post by computergroove on 2006-08-09
onboard video is typically defined internally as AGP. Can you find your bus ID's? type lspci -X in the terminal and manually edit the xorg.conf file but dont erase the lines you want to delete - just give them a # prefix to comment them out until you know they work. Good Luck

---

### Post by skattman83 on 2006-08-09
The 6200 is PCI, and the onboard is listed in the bios as AGP.

---

### Post by tseliot on 2006-08-09
Try this guide:
[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)

---

### Post by skattman83 on 2006-08-09
Thanks for the tutorial!  I was close with what I was going to try, but I was unaware of the blacklist file.  I'll give it a try tonight and post my results.

---

### Post by skattman83 on 2006-08-09
when I run lspci i get two lines of interest:

1. 0000:00:01.0 VGA compatible controller: Intel Corporation 82810 CGC [Chipset Graphics Controller] (rev 03)

2. 0000:01:0b.0 VGA compatible controller: nVidia Corporation GeForce 6200 (rev a1)

In my xorg.conf file I have my display adapter listed as 0.1.0.  Would that mean that I need to change it to 1.b.0 to make use of the nvidia card?

---

### Post by tseliot on 2006-08-09
> **skattman83 said:**
> when I run lspci i get two lines of interest:

1. 0000:00:01.0 VGA compatible controller: Intel Corporation 82810 CGC [Chipset Graphics Controller] (rev 03)

2. 0000:01:0b.0 VGA compatible controller: nVidia Corporation GeForce 6200 (rev a1)

In my xorg.conf file I have my display adapter listed as 0.1.0.  Would that mean that I need to change it to 1.b.0 to make use of the nvidia card?

Did you follow EVERY step of that guide?

---

### Post by skattman83 on 2006-08-09
Yeah, now that I think about it...when I commented out that line, it probably doesn't matter *what* i put in there, does it? :oops:

Anyway, I followed that guide, and it worked like a charm!  Thanks again for your help.

---

### Post by tseliot on 2006-08-09
> **skattman83 said:**
> Yeah, now that I think about it...when I commented out that line, it probably doesn't matter *what* i put in there, does it? :oops:
it doesn't.

> **skattman83 said:**
> Anyway, I followed that guide, and it worked like a charm!  Thanks again for your help.

I'm glad it worked for you ;)

---

