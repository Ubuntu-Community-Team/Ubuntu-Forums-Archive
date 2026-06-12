---
title: "Dell Inspiron 1545 Wireless disabled on boot"
date: 2010-08-04
forum: Networking &amp; Wireless
---

### Post by kage52124 on 2010-08-04
Drivers are installed and work properly when the wireless is not disabled, however if the wireless button is not pressed at the logon screen or very soon afterwards, the network icon with say it is active, but will fail to find a connection.  If the button is never pressed, the network icon says wireless is disabled.

How do I make the computer boot with the wireless enabled?  Could it have something to do with the keyboard, as the function keys and F keys are reversed?  With this computer, what would normally be F2 is the wireless radio button, and pressing Function and that key will result in F2.  I hope that makes sense.

---

### Post by JoshDN on 2010-08-05
I have the same laptop and same problem, but to matter when i press the wireless key, my wireless is still disabled. I installed the propreitary Broadcom STA driver. After the installation it says it is activated and in use - network manager says wireless disabled. After a reboot the driver is activated but not in use - network manager doesn't have wireless options at all. If I right click on the network manager there is no option to "enable wireless".
 
I've even tried the Ndiswrapper package to install the windows driver for my wireless card - still no success.
 
It seems like the driver is installed properly but there is just no good way to turn the wireless on - since it is done from the keyboard as kage52124 described.
 
Interesting fact: I have 3 laptops all together with ubuntu 10.04 or 9.10. NONE of them are able to use the wireless card. I also have the latest version of Puppy Linux that I boot from a USB drive - and ALL of them are able to run wirless using "Barry's Simple Network Wizard". How can puppy linux have such an edge over ubuntu??? somebody should talk to Barry!
 
Using Dell Inspiron 1545 with Ubuntu 10.04 WUBI.

---

### Post by dyltman on 2010-08-06
I have the same issue here but I am on inspiron 15n

---

### Post by kage52124 on 2010-08-11
Bump...desperate for this to get fixed...

---

### Post by dyltman on 2010-08-11
> **kage52124 said:**
> Bump...desperate for this to get fixed...

try pressing f2 with diffrent key combination like alt+f2 etc.

it's a dumb button that deactivates your internet

---

### Post by kage52124 on 2010-08-12
@ Dyltman

Thank you but I think you misunderstand.  If I press the key, it will change the dialog from "Wireless is disabled" to "Not connected", so that won't help.

I've been trying to figure how to automatically start the wireless radio, but to no avail.

---

### Post by ptha on 2010-08-13
> **dyltman said:**
> try pressing f2 with different key combination like alt+f2 etc.

it's a dumb button that deactivates your internet

This happened to me (also using Inspiron 1545 and Ubuntu 10.04), I had mistakenly pressed Alt-F2 to try to get the run dialog and had unbeknownst to myself turned off the wireless. I was pressing the blue Fn button plus F2 and nothing was happening (on reboot still turned off). Pressing Alt-F2 or even Ctrl-F2 turned it back on again.
P

---

### Post by JoshDN on 2010-08-20
kage52124, did this work for you? I'm still dead in the water. 
 
Anyone else have ideas?

---

### Post by Freeman-sr on 2010-08-20
Dell Inspiron 1720 here.

I remember googling and downloading sort of drivers that apparently worked. Cool. I removed them from where I kept them. Just a day later, Ubuntu asked me whether I want to stop using drivers that might not be appropriate. Since I thought they were graphic card drivers, I agreed to that, but poof -- I just happened to have no wireless internet connectivity again and of course I didn't remember what I did to get it before.

Now, isn't there a solution to this? Why everything works fine with 8.10 while 10.04 keeps bugging us?

---

### Post by kage52124 on 2010-08-23
No I'm dead in the water too...

---

### Post by JoshDN on 2010-08-24
I came across this thread today, but I won't be able to try it till later this afternoon. Maybe you can give it a shot?
 
[http://ubuntuforums.org/showthread.php?t=1559025](http://ubuntuforums.org/showthread.php?t=1559025)

---

### Post by kage52124 on 2010-09-02
Will try that method today...I'll post results...

---

### Post by kage52124 on 2010-09-07
No luck, couldn't compile the downloaded drivers...sigh.

---

### Post by kage52124 on 2010-09-11
Seems solved by updating to 10.10 beta...will mark as solved after a few days in case it was just luck.

EDIT: Looks good to me, so I'm marking as solved.

---

