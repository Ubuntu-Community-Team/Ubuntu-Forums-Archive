---
title: "No wireless after suspend"
date: 2010-11-10
forum: Networking &amp; Wireless
---

### Post by nickav21 on 2010-11-10
Hi everyone, I tried searching but just couldn't find anything that dealt with my exact issue.  I have a Toshiba Satellite A215 and recently installed Ubuntu 10.10.  I haven't had any issues whatsoever with my wireless connection except one: when I power back up from being suspended I can no longer see my home wireless network.  However, if I shut down then start back up I connect to it 100% of the time.  This issue ONLY happens after I recover from suspend.  Does anyone know why this would be happening?  Thanks in advance for any help!!

Edit: forgot to mention I'm running 64-bit.  Not sure if it matters or not!

---

### Post by grahammechanical on 2010-11-11
I have been browsing this particular forum for a few months. I have noticed that many users have complained that wireless in Ubuntu does not work well or is broken, as they put it.

I suspect that the problems are caused by 1) having the wireless card switched off in hardware at boot time; 2) resuming from a suspend or hibernation.

This is just my impression. It is not based on any scientific evidence. As I understand it the OS loads up modules at boot time. If it detects a networking device, whether ethernet or wirless, it will load the modules. These modules will make some kind of connection to the networking devices. And we have networking.

What happens when you resume from hibernation? It seems to me, in my ignorance, that a different process takes place. The OS is coming back up but it is not making the same connections with the hardware as it does during booting. What does the suspend process do to prevent the battery draining down during the period of suspension ?

I experimented with hibernation on my desktop machine. I found that I lost data. I use the database program in OpenOffice. It saves new records to disc when you close the program. Up until then the saved records were kept in memory. By going into hibernation the new records were not being saved to disc because the program's shut down process was not being activated. And I lost that data.

I no longer experiment with hibernation. I no longer work for long periods with the database program. I will close the program to save my data and then reopen it or do some other work. I have learned to live with the situation.

I do not do not know what you are doing to live with your situation. Have you thought of disabling networking prior to suspending? Have you tried switching off the wireless hardware before suspending and then switching it back on after resuming and then enabling networking. These are things that I would experiment with if I had a laptop and wanted to use hibernation. I do not know if you have tried these things.

Regards.

---

### Post by sailor420 on 2010-11-11
I'm having the same issue. Started when I upgraded to 10.10 from 10.04.

Try running "sudo rfkill unblock wifi" in the terminal when the machine wakes up. This gets it working again for me. Not a solution, as there is something else wrong in 10.10--but it at least gets it working again without having to reboot.

---

### Post by pinku on 2010-12-09
I have the same, running 10.10 32-bit on ASUS PL30JT, using Atheros AR9285 Wireless Network Adapter.

Unfortunately upon resume rfkill says wifi is unblocked:
```
rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```so trying to unblock it again does not help much.

So no suspend, only reboot for me, for now :(

---

### Post by adityadeva on 2010-12-13
$sudo rfkill unblock wifi 

has helped me bring up my athreos 5007 card back to life.

---

