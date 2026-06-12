---
title: "new to ubuntu trying to activate nvidia graphics driver i get error."
date: 2008-11-21
forum: Multimedia Software
---

### Post by habelman on 2008-11-21
Hello, i am very new to ubuntu, was just told about it to. My windows decided to crash for no reason and would not re-install xp pro. So i decided to take a lil different route. I dont know much about linux but id like to give this a shot. Anyway this is the problem i am having as of now. when i first installed ubuntu i got the update manager and the hardware drivers tab poped up. So i decided to start both, the updates are currently installing but when i tried to active Nvidia accelerated graphics driver (version 177) [recommended] i get this error.

SystemError: Failed to lock /var/cache/apt/archives/lock

I was looking for a resolution on the forums befor i posted this but the ones i came across say to enter code to bypass the error. Well im not quite sure on how or where i need to enter the code? if anyone could help i would much  appreciate it.
I am using e-Geforce 8800gts graphics card aswell. its a pci-e

---

### Post by Vadi on 2008-11-21
Hi and welcome.

Try closing all other programs (except firefox, that shouldn't affect it) and then clicking the activate button. Does it work then?

---

### Post by habelman on 2008-11-21
No, Actualy i think i just got it. I downloaded the linux driver off nvidia's website. And luckly they explain how to use the terminal/command promt with linux. So i followed the codes that were mentiond in a diffrent post with a guy that was having a identicale problem and i think i got it goind.

---

### Post by Vadi on 2008-11-22
Well. Sort of. Drivers from the nvidia website will always work, however you will not be able to update them via the Update Manager when ubuntu updates their version of the drivers.

They're kinda a "last moment" type of thing when nothing else works :\.

But glad you got them working! Click on 'Thread Tools' and 'Mark Thread as Solved'

---

### Post by habelman on 2008-11-22
Well its not quite solved yet, i got the nvidia drivers installed, but now i cant get the resolution set to my westinghouse 22" lcd natives 1680x1020 res...  nvidia x server sets default at 1024x768 which leaves little over a inch on both sides of black. and the highest res the settings offer is 1360x768 which extends the windows to far. Im not quite sure how to get my native resolution any ideas?

---

### Post by Vadi on 2008-11-22
What are you using to set the resolution?

---

### Post by habelman on 2008-11-22
iv been trying to use the nvidia x server settings and iv also tried to use the screen resolution in the system > prefrences > screen resolution and if it matters im running a geforce 8800gts

---

### Post by Brandel Valico on 2008-11-22
I can't really help with the resolution issue. But I can explain the issue you had. When the update manager is running you can't use the hardware installer or install via terminal or add remove programs or synaptic. As they all use the same processes to install programs to your computer. So before you can use another installation program you need to let the running one finish. Trying to run two at the same time will always give you the error you got.

You might want to try actually using the built in driver to fix your resolution though. Just make sure update manager/Synaptic/and other such programs aren't running. Then goto System,Administrator,Hardware drivers. In the window that pops up click the driver for your card and see if it installs if it's not all ready activated.

---

### Post by habelman on 2008-11-22
the recommended nvidia 177 driver is installed and activated.

---

### Post by Vadi on 2008-11-23
I'd recommend posting on [http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14), the official nvidia linux forum.

Unfortunately I cannot help you as I never ran into this issue before. But when you find a solution, please repost here

---

### Post by habelman on 2008-11-23
alright thank you for the link, ill check it out and see what they have to say. ill let you know what i found out.

---

### Post by habelman on 2008-11-24
Alright the site you gave me to check it is being stuborn.. I tried to make a account so i could log into the forums and ask but they for some reason banned my e-mail when i was doing the register stuff.

---

### Post by Vadi on 2008-11-24
Try making a new gmail account? Some forums ban hotmail / temporary emails.

---

