---
title: "Waiting for network configuration 11.10"
date: 2012-10-14
forum: Networking &amp; Wireless
---

### Post by grey1beard on 2012-10-14
I've read several posts on this general problem, having just changed my laptop system from 11.04 to 11.10 via upgrade, and now faced with the same.

One thread advocates editing the  **failsafe.conf** by commenting out the sleep commands, and this seems perfectly logical as a minimum change.
Unfortunately a senior moment prevents me from remembering how to alter permissions for this particular "Read only" file.
Grateful for a guiding hand, and large cup of Matron's best.

John

---

### Post by grey1beard on 2012-10-15
While waiting for some help, and getting a good night's sleep, I've been exploring synaptic to see what wicd packages are installed.

This comes after I've opened the wicd network manager.
It says that "No networks detected" and at the bottom of the same window shows it's connected to my wireless network with 100% reception. Trying Refresh has no effect, still showing no network detected.

In synaptic, I see wicd,wicd-gtk, and wicd-daemon, but also python-wicd.
Is the python-wicd reduntant, and possibly its presence causing the problems I'm having?

---

### Post by mendieta on 2012-10-15
Hi, you can run an editor as superuser (please be careful):

sudo gedit 

Before doing this, you may want to check the contents of /etc/network/interfaces

Any "auto eth0" line there will make the boot procedure halt, waiting for an ethernet connection to be up.

Good luck!

---

### Post by grey1beard on 2012-10-16
Hi mendieta,
My network/interfaces has 
>  # The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid *********

Is it the auto eth1 entry that I should try commenting out ?

John

---

### Post by hawaiiman on 2012-10-16
If you comment out your auto eth1 that will prevent booting of the ethernet device. If you don't want to get on the internet through the ethernet, that may work. The error your getting usually implies a network connectivity issue. My limited understanding of the evolution of Ubuntu leads me to the idea that 11.10 was a sort of transition which led to 12.04. If it was me I'd consider going back.

---

### Post by grey1beard on 2012-10-16
> **hawaiiman said:**
> ..... My limited understanding of the evolution of Ubuntu leads me to the idea that 11.10 was a sort of transition which led to 12.04. If it was me I'd consider going back.

Hi hawaiiman,

Having slowly plodded on from 8.04, when I first discovered Ubuntu and started to see the pros and cons, I've got so used to seeing Update Manager pop up, that I'd feel a bit left behind if I didn't continue.:)

The learning curve has settled to a gentle slope, and apart from the odd senior moment, I can look back and be surprised just how much progress I've made.

I'm now seriously thinking of making the next move to 12.04, which being an LTS, will give me something of a breathing space before I need to repeat the process.
Not sure if I'll ever get used to Unity after the familiarity of Gnome, but that's a discussion for elsewhere.

Regards
John

---

### Post by grey1beard on 2012-10-16
With a little trepidation, I have commented out the auto eth1 line, and the restart ran perfectly, without any waiting.
Thanks all.
John

---

### Post by mendieta on 2012-10-16
> **grey1beard said:**
> With a little trepidation, I have commented out the auto eth1 line, and the restart ran perfectly, without any waiting.
Thanks all.
John

Yeah, sorry I didn't have time to look earlier. You did the right thing. More info here:
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/839595](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/839595)

Cheers!
Leo

---

### Post by grey1beard on 2012-10-17
Just a footnote.
The successful outcome of the above problem gave me confidence to move on one more step to 12.04.

During this, I opted to keep the same network config, and sure enough, 12.04 opened perfectly, all systems go.

John

---

