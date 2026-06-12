---
title: "Can't connect my Dell E1505 to Wireless (don't know jack about command codes)"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by Ulysses1994XF04 on 2010-06-01
Hey, so I just installed Ubuntu as a desperate last resort after suffering several virus attacks on my Windows laptop. It's a Dell E1505. The installation seemed smooth, but I can't connect it to my Wireless network. My Wireless is working on every other computer in the house except my Ubuntu laptop. When I click in the little bars on the top tray, it says "device not ready." 
 
I'm totally baffled as to what to do. I searched a million forums about how to get Wireless working but they're so full of computer-code, and I don't know anything about programming. I tried to install something called "ndiswrapper" (by burning it on a CD on another computer and putting it in my Ubuntu laptop) but I try clicking on every single icon in the file and nothing happens. I don't know if the program ran or not.
 
What should I do? Please try to explain as simply as possible since I don't know anything about command codes or computer programming

---

### Post by pdc on 2010-06-01
I think you are likely to have a broadcom 4311 card;

from here

[http://bnmngcomputing.wordpress.com/2010/01/20/wireless-with-dell-e1505-and-ubuntu-9-10/](http://bnmngcomputing.wordpress.com/2010/01/20/wireless-with-dell-e1505-and-ubuntu-9-10/)

and other posts .......

you can check this by opening a terminal: system; accessories; terminal

and typing 

> lspci and amidst the information should be broadcom 4311

here is a guide to installing what you need: your 4311 is covered in the first entry: you need to read through it a couple of times and then do it

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

let us know how it goes

---

### Post by Ulysses1994XF04 on 2010-06-01
I typed "lspci" into "terminal." I read everything that showed up. I didn't see anything that said "Broadcom 4311" but I did find somethat that said 
 
>  03:00.0 Ethernet controller: Broadcom Corporation BCM401-B0 100Base-TX (rev2)
 
Is that what I'm looking for?

---

### Post by Ulysses1994XF04 on 2010-06-01
After typing "lspci" a whole bunch of times and reading through all the text that pops up, I can't find anything that says "Wireless card." Is the ethernet card the same thing? 
 
I DO know this laptop is wireless capable. I used wireless everyday on it when it had Windows.

---

### Post by drpjkurian on 2010-06-01
Hi 

See my snapshot of my terminal after typing the ```
lspci
```

You can see the second last line depicts of my wireless card

---

### Post by drpjkurian on 2010-06-01
HI 
Ethernet means wired network

---

### Post by Ulysses1994XF04 on 2010-06-01
Alright. I typed "lspci" and went to the bottom line. This is what I got.
> 0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (revi 01) 
 
Is THAT what I'm looking for?

---

### Post by Ulysses1994XF04 on 2010-06-01
> **pdc said:**
> I think you are likely to have a broadcom 4311 card;
 
from here
 
[http://bnmngcomputing.wordpress.com/2010/01/20/wireless-with-dell-e1505-and-ubuntu-9-10/](http://bnmngcomputing.wordpress.com/2010/01/20/wireless-with-dell-e1505-and-ubuntu-9-10/)
 
and other posts .......
 
you can check this by opening a terminal: system; accessories; terminal
 
and typing 
 
and amidst the information should be broadcom 4311
 
here is a guide to installing what you need: your 4311 is covered in the first entry: you need to read through it a couple of times and then do it
 
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)
 
let us know how it goes
 
 
Okay, so I went to that site you said. I put in the CD, clicked "Installable from CD-ROM/DVD, clicked "bcmwl-kernel-source" and preped it for installation. When I restarted Ubuntu, there was a new icon on the top bar by the clock saying "New Drivers to be installed" or something. I clicked on the two icons on the inside but they failed to install. I got an error message.
 
When I went through all that again to reinstall "bcmwl-kernel-source," I kept getting an error message and the download stops. :mad:
 
I'm kinda wishing I stuck with Windows right now.

---

### Post by pdc on 2010-06-01
don't you just hate it when it's hard?

so we are agreed you have the 4311 in your system

the instructions from here 

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

are

> **_IF WIRED CONNECTION DOES NOT WORK: _**     
    


> **1. From LiveCD** 
         1. Open Sytem -> Admin -> Synaptic Package Mgr


> 2. Ensure LiveCD is in the drive ........ *you installed from a liveC*D ????????/


> 3. In Synaptic Package Mgr, open **Settings** -> **Repositories **-> **Ubuntu Software**

> 4. Check "**Installable from CD-ROM/DVD**" and close

> 5. Reload (disregard connectivity errors)

> 6. Search for "bcmwl-kernel-source"

> 7. **Right-click** and **mark** for installation

> 8. **Apply** changes and reboot

> Repeat steps 1.3 thru 1.4.2

ie go to the section above; and do 

> After reboot, open System -> Admin -> Hardware Drivers

> Look for "Broadcom STA wireless driver";

   1. **IF DRIVER IS PRESENT AND ACTIVATED:**
         1. Remove network cable, toggle wireless button, and log into network.


> # IF DRIVER IS PRESENT **BUT NOT ACTIVATED**:

   1. Activate and reboot;
   2. After reboot, remove network cable, toggle wireless button, and log into network.


---

### Post by Ulysses1994XF04 on 2010-06-01
I've tried this several times already today. I go to "System" "Admin" and "Hardware Drivers." 
 
On the list of hardware drivers, it says "Broadcom B43 wireless driver" and "Broadcom STA wireless driver." I tried clicking "Activate" for both. But when I click on B43, it says
 
> Sorry, installation of this driver failed. Please have a look at the log file for details :/var/log/jockey.log
 
When I click on "Activate" for STA, it says > SystemError: installArchives () failed

---

### Post by pdc on 2010-06-01
sorry to hear this is being troublesome

I do not know if you have access to a wired connection; can you find some kind soul to let you plug this laptop into a router, and download via a wired connection?

that might allow you to try the first section again

---

### Post by Ulysses1994XF04 on 2010-06-01
> **pdc said:**
> sorry to hear this is being troublesome
 
I do not know if you have access to a wired connection; can you find some kind soul to let you plug this laptop into a router, and download via a wired connection?
 
that might allow you to try the first section again
 
I do have a wireless connection in my house. I'm typing right now from my brother's Windows laptop that is connected to the internet wirelessly. 
 
Will I be able to disconnect the cable from my WiFi Router and plug it into my Ubuntu laptop to connect to the internet?

---

### Post by pdc on 2010-06-01
not sure

some wireless routers have an ethernet port so one can go ethernet to ethernet

---

### Post by Ulysses1994XF04 on 2010-06-01
> **pdc said:**
> not sure

some wireless routers have an ethernet port so one can go ethernet to ethernet

Holy crap it worked! I plugged an ethernet cable from my Ubuntu laptop to my router and I was able to connect to the internet immediately (but through the wire). I clicked activate for my Broadcom drivers and they installed smoothly. When I unplugged the ethernet cable restarted my computer, I was able to logon to a wireless network automatically.

The problem is, it connected to my neighbor's wireless. I had to search in "Connect to Hidden Wireless Network" to find my wireless. When I restarted the computer for good measure, it still auto-connected to my neighbor's wireless. How can I set Ubuntu so that it automatically connects only to my wireless?

---

### Post by pdc on 2010-06-02
can you see your own wireless system? 

can you select it?

---

### Post by qwertyuio on 2010-06-09
HI guys I installed Ubuntu 10.04 on my dell Inspiron e1505 and now i don't have any internet at all. No wired or wireless. All this stuff about pulling up the mac add is fine , but no where in the term dose it say mac any thing . I copied and pasted it in to (Add) - in network connections,and it won't let me apply the setting? So please what exactly do I put into the MAC address line? The weired thing is after the install is finished and before I do the restart i have wired internet. I tried installing and activating new wireless drivers and every other setting i could think of in 4 reloads of software and nothing. How is it I have a working wired internet connection before the restart and not after. P.S. I have loaded 9.04 and wired connection works fine but not in 10.04 ?

---

