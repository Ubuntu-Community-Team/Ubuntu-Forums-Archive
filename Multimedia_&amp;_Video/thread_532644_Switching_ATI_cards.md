---
title: "Switching ATI cards"
date: 2007-08-23
forum: Multimedia &amp; Video
---

### Post by Dubbayoo on 2007-08-23
I have been using an ATI Radeon 8500 with the free 'ati' driver on Feisty. I just got a Radeon X1300 Pro. I want to use the ATI closed driver with this card. Both cards are AGP. 

I installed the new card and the ATI driver from the repository, but now I can't get into X. It appears that I haven't told X that the card is now different. How do I reconfigure X so it replaces the old card configuration with the new? What command do I run?

TIA

---

### Post by RomeReactor on 2007-08-23
Hi. When you get dropped to the command line enter this:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
when it asks you which driver to use, select **fglrx** (I think; I don't have an ATI card).
if after that you don't get to see your desktop, enter this:
```
start x
```
If you are still unable to get a display, repeat the steps, but choose the **ati** driver this time.

---

### Post by Dubbayoo on 2007-08-23
I got it to work by adding some things from another configuration here. The only left is my resolutions. I only have options for 1152, 1024, 800 and 600 even though my xorg.conf file is configured for 1400 (my preferred), 1280, 1152 and 1024.

Also, what does **phigh** signify in your response?

---

### Post by RomeReactor on 2007-08-23
The **-phigh** is the priority level of the questions you get asked during the reconfigure; I'm not certain about this, but I take it's meaning as "only high priority questions will be asked during reconfigure; other questions will not be asked and will be set to their defaults".

As for the resolution issue, try installing **fglrx-control**. Look for it in Synaptic, or to install from the terminal:
```
sudo apt-get install fglrx-control
```
I don't have an ati card, but this sounds like the **nvidia-settings** we have for Nvidia cards, which let you manipulate the card's settings through a graphical interface. Hopefully someone who actually has used this program can comment on this.

---

### Post by eye208 on 2007-08-23
> **Dubbayoo said:**
> How do I reconfigure X so it replaces the old card configuration with the new? What command do I run?
```
sudo aticonfig --initial --ovt Xv
```
That's all. The fglrx driver will automatically detect which resolutions are supported by your display and pick the highest one.

In order to use direct rendering, you will have to add these lines to your xorg.conf:
```
Section "Extensions"
    Option "NoComposite"
EndSection
```

Things could have been even easier if you had just used Feisty's restricted drivers manager instead of adding and configuring stuff by hand.

---

### Post by Dubbayoo on 2007-08-26
> **eye208 said:**
> 
Things could have been even easier if you had just used Feisty's restricted drivers manager instead of adding and configuring stuff by hand.
Wrong.

I couldn't get into X after switching the card, hence negating the opportunity to access restricted driver manager. RDM wouldn't activate the driver with the old card still in because the 8500 isn't supported by the driver.

---

### Post by eye208 on 2007-08-27
So the free Radeon driver does not work with X1xxx cards?

I would have expected it to work in 2D mode at least ... :-k

It's probably best practice to switch X to vesa before switching cards.

---

