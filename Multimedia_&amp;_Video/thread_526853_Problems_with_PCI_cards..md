---
title: "Problems with PCI cards."
date: 2007-08-16
forum: Multimedia &amp; Video
---

### Post by jso2897 on 2007-08-16
I have a couple of older machines that only have PCI expansion slots. i also have a couple of Nvidia PCI cards A Gforce 4000 and 5500. I cannot run the PCI cards with Fiesty on either machine. On one machine, Fiesty is running great with the onboard graphics, and on the other, a PCI card is running fine under XP. But on either machine, if I try to boot Fiesty with a PCI card in, it only goes until the loading bar stops, and then the screen goes black, and it locks up. This happens whether I boot from a HD or LiveCD. Does anybody know what I'm doing wrong? I've had no problems withe Fiesty with AGP or PCIe cards.:confused:

---

### Post by jso2897 on 2007-08-16
I'm gonna bump this one time in hopes somebody will recognize something familiar here. It's really driving me nuts. Both cards work fine right up until it tries to boot into X - then everything just dies. Both cards are supported - in fact, I have a n AGP version of one of them running in another machine right now. The BIOS recognizes the cards, and they are set as the primary display. Is there some trick with PCI cards?Anybody?:confused:

---

### Post by tseliot on 2007-08-16
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

### Post by jso2897 on 2007-08-16
TSEliot: Thanks - I'll give that a shot - will that work if I'm booting from a live CD?

---

### Post by jso2897 on 2007-08-16
Didn't work. Here's the deal. I already gave up on one machine, and sent the card back to Tigerdirect while there's still time to get full exchange. What I'm trying to do now is install Feisty on a WinXP machine with a Geforce 5200 PCI card in it. When I tried what you said, I got back:

00.01.0 VGA compatible controller: Intel Corporation CGC (chipset graphics controller) (rev 03)

01.0d.0 VGA compatible controller: nVidia Corporation NV34 (GeForce 5200) (rev a1)

When I go into XORG, it already says "VESA", and gives the PCI address as 0.1.0

I tried putting a # infront of that, but I don't think I did it right - and anyway, since I am booting from a live CD it was all for naught. As soon as I rebooted, the changes to the XORG were, of course, lost.
 So I don't know what the heck to do.:(

---

### Post by jso2897 on 2007-08-16
This is driving me nuts - I can't seem to find a way to get from editing XORG directly into X without rebooting and losing my changes.

OK - I solved that problem, but I tried several changes, but X wouldn't start, and the answer was always:

(WW)VESA: no matching device section for this instance (BUS ID PCI:0:1:0) found
(WW)VESA: no matching device section for this instance (BUS ID PCI:1:13:0) found

So, I don't know.  If I have to keep it as a Windows machine, so be it.

---

### Post by jso2897 on 2007-08-17
Still no solution. I don't think I have enough experience editing Xorg.conf. Does anybody know of a good guide?:confused:

---

### Post by orbeus on 2007-08-17
Hi 

I Just got back from the store with a new PCI graphics card. Had the same problem.
Followed the instructions from tseliot and was successful.

Thanks!
O

---

### Post by jso2897 on 2007-08-17
Maybe i'm not doing it right. where exactly does the "#" go in the line of text?:confused:

---

### Post by jso2897 on 2007-08-17
One last bump - hoping somebody sees it who knows the answer...:(

---

