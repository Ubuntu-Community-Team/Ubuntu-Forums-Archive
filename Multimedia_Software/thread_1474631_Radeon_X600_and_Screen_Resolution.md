---
title: "Radeon X600 and Screen Resolution"
date: 2010-05-06
forum: Multimedia Software
---

### Post by rslater on 2010-05-06
Although not a complete newby to Ubuntu, I am struggling to find a solution to this:
 
I have a dual core P4 and a Radeon X600 video card. I am running Jaunty and I do not seem to be able to set the screen resolution higher than 1024x768. I have a 19" monitor and I am getting frustrated that I cannot select a higher resolution. I have tried to follow several online solutions reference changing the video drivers, but to date I have had no luck.
 
What I really need if anyone can help is a simple to follow, step by step solution. Thanks in advance.

---

### Post by Mark Phelps on 2010-05-06
Ignore what people are telling you about changing video drivers.  The card you have does not have ATI fglrx drivers that work for it anymore, so if you force an ATI driver installation, you will only corrupt your display and have to reinstall the drivers you already have.

Sorry, but the resolution you're getting may be the highest one the open source drivers provide for your card.

---

### Post by Yellow Pasque on 2010-05-06
Note that you may have partially installed drivers interfering with your current driver. Follow this to restore the stock driver: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

After that, log out to restart the Xserver. Log back in and post or pastebin your /var/log/Xorg.0.log file

> Sorry, but the resolution you're getting may be the highest one the open source drivers provide for your card.
I got 1680x1050 from an X300SE through the VGA/analog output using open-source drivers. I don't think the driver is the issue.

---

### Post by rslater on 2010-05-06
Thanks for your help everyone. :-D

---

### Post by Yellow Pasque on 2010-05-06
> **rslater said:**
> Thanks for your help everyone. :-D
Does this mean the issue is resolved?

---

