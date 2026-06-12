---
title: "No internet at all"
date: 2009-11-17
forum: Networking &amp; Wireless
---

### Post by AHoFoSho on 2009-11-17
I am having the same problems that many are with the wireless card not being recognized on my compaq presario v2000 with a broadcom 4306 rev 3 wireless card. I have been attempting to follow the instructions on other threads. However, it seems as though my wired internet connection is not working either. I have the original cd with the drivers on it but am not sure how to use it to recognize the card. any help would be much appreciated!

---

### Post by coffeecat on 2009-11-17
The chances of you finding an ethernet network card that doesn't work in Ubuntu are somewhat slimmer than winning a National Lottery. You don't need the Windows drivers on the CD.

What exactly do you mean by the wired connection not working? What have you done to try to get it to connect?

Usually in Ubuntu (which mean 99% of times) you plug in an ethernet cable between your computer and the router and it just connects without you having to do anything at all.

---

### Post by AHoFoSho on 2009-11-17
Well i plugged the ethernet cord from my the router to my computer and it said wired connection disconnected and I could not figure out how to make it work. I am definitely an Ubuntu noob. I dont think I have ever been more lost with a computer in my life haha.  I trid this with an older version a few months ago and the wired connection had no problems but the wireless still didn't work. I gave up then and decided to give it another shot.

---

### Post by coffeecat on 2009-11-17
Try this, but I'm afraid that after I post this, I'll have to log off. It's late here.

Plug an ethernet cable between your router and the computer. If it doesn't autoconnect, click on the Network Manager icon towards the right of the upper panel. It's next to the sound icon. Does it show a line saying 'Auto Eth0'? If so, just click on that line and, hopefully, it will now connect.

If not, right-click on the Network Manager icon and untick the 'Enable Networking' tick box. Wait a couple of seconds and then tick it again. If it doesn't autoconnect, try clicking on  the 'auto eth0' line again.

If that none of that works, open a terminal and post the output of:

```
lspci | grep Ethernet
```We need to make sure your ethernet card is being seen by the system and that command should tell us that.

I'll check this thread out tomorrow but in the meantime hopefully someone else will help.

Good luck and welcome to the forum. :)

---

### Post by AHoFoSho on 2009-11-17
ha No worries I actually don't have anymore time today to mess with it anyways so we will work through this process slowly i guess haha. Thank you very much though.

---

### Post by Iowan on 2009-11-17
While you have the terminal window open...
Check **lshw -C network** - probably much the same information as **lspci**. 
Check **ifconfig -a** - should show interfaces. *Probably* won't have IP address for eth0. A 169.254.X.X address is an **avahi** address (which probably won't work).

---

