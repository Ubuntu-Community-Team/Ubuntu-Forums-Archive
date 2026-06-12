---
title: "No network interface on old laptop"
date: 2011-10-05
forum: Networking &amp; Wireless
---

### Post by stevenocchipinti on 2011-10-05
Hi,

I have installed Ubuntu Server 10.04.3 LTS on an *old* laptop that has a PCMCIA ethernet card.
During that installation, the installer configured my network card, and I had internet connectivity.
Now that it is all installed, i can't see any network interfaces and am not very familiar with how to install network drivers as I've always taken that for granted.
Basically I just need to enable the drivers like the installer did, but I am having a hard time finding how to do this.

I would paste the output of [FONT=Courier New]dmesg[/FONT], etc. but without network I can't really copy and paste it :P
I also tried using a USB drive, but [FONT=Courier New]fdisk -l[/FONT] shows nothing and so I'm not sure how to mount that either... obviously not having much luck :(

I can tell you that all of the below commands return nothing:
```
lspci | grep ethernet
lspci | grep network
dmesg | ethernet
dmesg | network
lshw -C network
```and [FONT=Courier New]ifconfig -a[/FONT] only lists the loopback interface.

I know this is possible because the installer did it... please help :confused:

P.S. Once I get this working, I actually have a PCMCIA wifi card that I would like to use, so I'm hoping the method for installing these drivers will also help with that later down the track - but that's not important right now, I just need internet!


Thanks in advance.

---

### Post by WasMeHere on 2011-10-05
Since you had ethernet during the live sesssion, you should have it also after installation.

Try the following command
```
sudo lshw |grep eth
```
and post your output!

---

### Post by stevenocchipinti on 2011-10-05
> **Olle Wiklund said:**
> Since you had ethernet during the live sesssion, you should have it also after installation.

I would have thought so too! :)
It's worth noting, that as its Ubuntu server, I only get the step-by-step, non-x installer. But there is a step in that installer that configures my network interface, and when I switch to another console with alt+ctrl+F2, I can successfully ping google (during the install process)
But now that it's installed... nothing, no interface at all.

> **Olle Wiklund said:**
>  Try the following command
```
sudo lshw |grep eth
```and post your output!

That command produces nothing aswell.

As this Ubuntu Server install is fairly minumal, I'm guessing I would need to enable some modules/drivers or something before the PCMCIA card is recognised... any ideas?

Thanks for your help BTW :)

---

### Post by WasMeHere on 2011-10-05
Obviously Ubuntu Server behaves differently from what I am used to using several of the desktop versions. Ubuntu Studio also has that kind of installer, but I had no issues with ethernet installing it.

I agree that you try to install a PCMCIA card driver, or if no success: Have you  tried to install vanilla Ubuntu? That version should install with a working ethernet connection. If so you may install the server software needed afterwards (sshd, smbd ...).

But if you really want the server version, [COLOR="Red"]let us call for help from someone with experience of server installations[/COLOR]!

Good luck
Olle

Edit: Would it possibly disturb the configuration to enter another console and ping google?

---

### Post by stevenocchipinti on 2011-10-05
> **Olle Wiklund said:**
> Obviously Ubuntu Server behaves differently from what I am used to using several of the desktop versions. Ubuntu Studio also has that kind of installer, but I had no issues with ethernet installing it.

Me too! I've always taken network access for granted in the other variants.

> **Olle Wiklund said:**
>  I suggest that you try to install a PCMCIA card driver.

I'm not sure how to do this? 
The installer must have done something like this automatically for the install process, but I don't know how to do that myself.

> **Olle Wiklund said:**
> Have you  tried to install vanilla Ubuntu. That version may install with a working ethernet connection. If so you may install the server software needed afterwards (sshd, smbd ...).

I havent tried vanilla Ubuntu on this, thats because this laptop is really old!
It only has 128mb ram, so I doubt it would be able to run the standard Ubuntu.
As it is, ubuntu server just about uses all the ram now, fully fledged Ubuntu desktop would most likely crumble.
I'm open to other suggestions, but this hardware is not very "modern".

Another alternative is to try a less-memory intensive OS, like Arch linux, but I chose Ubuntu because I thought it would have more hardware support... which is not working for me too well right now :P

> **Olle Wiklund said:**
> But if you really want the server version, [COLOR=Red]let us call for help from someone with experience of server installations[/COLOR]!

That would be great :)
Thanks

---

### Post by WasMeHere on 2011-10-06
It's that old, and the RAM is that small! You are right, vanilla Ubuntu is a no-go. Possibly Lubuntu would work, but maybe you can have fun with some very small linux version. Your mentioned Arch, but you can find several other versions with a small foot-print. Simply browse the internet for 'small footprint linux' or 'text mode linux with internet'

I have run DSL on old computers.

---

### Post by stevenocchipinti on 2011-10-11
I have now decided against using this machine in favour of a newer one.
Thanks for the help ether way

---

### Post by robvas on 2011-10-11
You will have to start the PC Card service to use a PC card NIC

---

### Post by stevenocchipinti on 2011-10-11
Thanks, but now that I've swapped to a (slightly) newer machine, the default installation of Ubuntu server simply works with this PCMCIA NIC.

Thanks anyway

---

