---
title: "Problems connecting to Asus RT-N56U wifi AP using Lenovo X220 Tablet PC"
date: 2011-07-28
forum: Networking &amp; Wireless
---

### Post by jdefoe on 2011-07-28
I'm having a strange problem on my new Lenovo X220 Tablet PC with Ubuntu 11.04 64-bit.  At work, my wireless connects fine.  At home, it's a different story.

I have an Asus RT-N56U router which supports dual-band connections, as does the laptop.  The wireless card is the Intel Advanced-N 6205, which also supports dual-band.  My machine is a dual boot with Windows 7 and in Windows everything works fine, so I know it isn't a hardware issue.  In Linux the wireless card uses the iwlagn kernel module.

The problem is that every time I reboot the machine, my wireless doesn't work right.  It sees the router and tells me I'm connected to the network (I get assigned an IP address), but no web pages will load, and I cannot even ping machines on the local subnet.  I downloaded the compat-wireless tarball and followed the installation instructions, which worked perfectly: after installing the updated driver, things worked great again. But upon reboot, the wireless fails in the same way; I have to do the following to get it working:

- go to the directory where I untarred compat-wireless
- sudo make unload
- sudo make install
- sudo modprobe iwlagn
- sudo modprobe bnep
- sudo modprobe btusb
- sudo modprobe rfcomm
- sudo modprobe sco

Then the wireless will work fine until I restart again.  It's like this change isn't permanent, even though it should be.  How can I make it so I don't have to follow these annoying steps every time I restart to get wireless working?

Any guidance would be greatly appreciated!

---

### Post by lkjoel on 2011-07-28
> **jdefoe said:**
> I'm having a strange problem on my new Lenovo X220 Tablet PC with Ubuntu 11.04 64-bit.  At work, my wireless connects fine.  At home, it's a different story.

I have an Asus RT-N56U router which supports dual-band connections, as does the laptop.  The wireless card is the Intel Advanced-N 6205, which also supports dual-band.  My machine is a dual boot with Windows 7 and in Windows everything works fine, so I know it isn't a hardware issue.  In Linux the wireless card uses the iwlagn kernel module.

The problem is that every time I reboot the machine, my wireless doesn't work right.  It sees the router and tells me I'm connected to the network (I get assigned an IP address), but no web pages will load, and I cannot even ping machines on the local subnet.  I downloaded the compat-wireless tarball and followed the installation instructions, which worked perfectly: after installing the updated driver, things worked great again. But upon reboot, the wireless fails in the same way; I have to do the following to get it working:

- go to the directory where I untarred compat-wireless
- sudo make unload
- sudo make install
- sudo modprobe iwlagn
- sudo modprobe bnep
- sudo modprobe btusb
- sudo modprobe rfcomm
- sudo modprobe sco

Then the wireless will work fine until I restart again.  It's like this change isn't permanent, even though it should be.  How can I make it so I don't have to follow these annoying steps every time I restart to get wireless working?

Any guidance would be greatly appreciated!
Try this in a Terminal window:
```
cat << EOF | sudo tee /etc/init.d/compat-wireless-fix
cd *PATH/TO/UNTARRED/COMPAT-WIRELESS*
make unload
make install
modprobe iwlagn
modprobe bnep
modprobe btusb
modprobe rfcomm
modprobe sco
EOF
```
Then restart

---

### Post by jdefoe on 2011-07-29
Hi,

Thanks for the quick reply!  So I generated the script you suggested, though as-is it doesn't work, because even once I've added a

#! /bin/bash

line at the start and make the script executable, it still doesn't automatically run on startup just because it's on the /etc/init.d folder -- I need to do something else to make it auto-start. How do I do that?

If I manually run this script after logging in when the wireless isn't working, it fixes it.

Also, this isn't really a fix, just a way of automating the workaround I've found. It has the drawback of significantly increasing the boot-up time; in addition, wireless will also fail after waking from suspend and this solution doesn't take care of that. There must be a more elegant way to make this work!

It's like the kernel isn't loading the updated module, even though /etc/depmod.d/ubuntu.conf contains:

search updates ubuntu built-in

which as I understand it means that it should load modules in "updates" (where compat-wireless installs) rather than the built-in ones (yet this doesn't seem to be happening -- or maybe it does and for some reason the networking still just doesn't work until the modules are re-loaded... how would I check that?).

Anyway, if I could get this script to actually automatically run at boot, it would at least be a "hands-off" workaround for now, until a solution to the real problem can be found.

---

### Post by lkjoel on 2011-07-29
> **jdefoe said:**
> Hi,

Thanks for the quick reply!  So I generated the script you suggested, though as-is it doesn't work, because even once I've added a

#! /bin/bash

line at the start and make the script executable, it still doesn't automatically run on startup just because it's on the /etc/init.d folder -- I need to do something else to make it auto-start. How do I do that?

If I manually run this script after logging in when the wireless isn't working, it fixes it.

Also, this isn't really a fix, just a way of automating the workaround I've found. It has the drawback of significantly increasing the boot-up time; in addition, wireless will also fail after waking from suspend and this solution doesn't take care of that. There must be a more elegant way to make this work!

It's like the kernel isn't loading the updated module, even though /etc/depmod.d/ubuntu.conf contains:

search updates ubuntu built-in

which as I understand it means that it should load modules in "updates" (where compat-wireless installs) rather than the built-in ones (yet this doesn't seem to be happening -- or maybe it does and for some reason the networking still just doesn't work until the modules are re-loaded... how would I check that?).

Anyway, if I could get this script to actually automatically run at boot, it would at least be a "hands-off" workaround for now, until a solution to the real problem can be found.
Type in the Terminal window:
```
sudo chmod -R 0755 /etc/init.d/compat-wireless-fix
```

---

### Post by jdefoe on 2011-07-29
Hi, thanks.

That just made the script executable -- but it already was.  The problem is the boot-up sequence doesn't know to execute this script.

Thank you for all your help, though.

Hopefully I can eventually get a permanent fix for this problem.

---

### Post by Samsicle on 2011-08-16
Hey guys,

any success on this?

I have the same router and problem with almost the same hardware. I have a x201 tablet (has the intel advanced-N 6200 AGN network adapter). Appears to connect to wireless network but cannot ping the router or load web pages, no problems on wired network or from windows boot.

I haven't tried the compat-wireless-fix described because it doesn't sound like the best solution, maybe I'll give it a shot tomorrow.

Anyway, any help would be awesome

---

### Post by jdefoe on 2011-08-16
Hi,

I haven't found a real solution yet, but I have narrowed down the problem and identified a workaround to improve the situation. All the steps I was doing with re-installing compat-wireless over and over was not the right way to go about things.  Instead, here's the solution I've found that works pretty well:

1) DO install compat-wireless (once!) ... the updated driver seems to make some difference

2) TURN OFF the 5.0 GHz radio on the Asus RT-N56U and connect to the 2.4 GHz network instead (you might be able to leave the radio on and just tell Ubuntu to connect to the 2.4 GHz network instead)

These two steps result in me having working wireless about 90% of the time.  When it doesn't work, disabling wireless via the HARDWARE SWITCH on the laptop, leaving it off for about 5 seconds, and then turning it back on generally gets me up and running.

Obviously this isn't an ideal solution for several reasons:

a) it only works 90% of the time
b) you're not taking full advantage of the capabilities of the router

....but at least it alleviates most of the frustration!

Hopefully this helps.

---

### Post by Samsicle on 2011-08-16
Thanks for the help jdefoe,

I did try installing compat-wireless but then it took a really long time to connect to a wireless network at work. Perhaps i did something wrong, either way I uninstalled it. When I got home I simply tried turning the hardware switch off for a few seconds then back on again. All seems to be well and I'm connected to the 5GHz band without issue so far (a little more than the length of time it took to write this post).

Hopefully all is well and Thanks for the help again.

---

### Post by jdefoe on 2011-08-30
Thanks for the tip about using the hardware wireless switch. This seems to fix the problem MOST of the time for me -- but occasionally it's stubborn and I need to unload and reload the kernel modules to get it to work again.  Hopefully in October when the next version of Ubuntu comes out this will be fixed!

---

### Post by awonglk on 2012-06-21
I have Lenono T410 and experienced this same issue as well, i.e. only an issue if I connect to the 5GHz network.

What fixed it for me, is if I just fixed a few settings on the router itself. Namely, I fixed the channel bandwidth to 40MHz, instead of the default 20/40Mhz. And also fixed my channel to 40, instead of the default 'Auto'.

I've been able to connect on the 5GHz network without any issues since. Hope this helps for others.

---

