---
title: "Modlues not loading ath9k Driver"
date: 2009-08-04
forum: Networking &amp; Wireless
---

### Post by MadHatter21 on 2009-08-04
Hello,

I have a gateway netbook running a atheros wifi card. I have installed Compat-Wireless-2.6.30 and have sucessfuly connected to my ap and browsed the net using the ath9k driver. After some restarts and shutdowns, now the light for the wireless led on my netbook is not on and the driver only sometimes loads, due to unknown cause. I am not sure why it only loads sometimes and was hoping someone could help me resolve this issue. 

Thanks 
MadHatter21

---

### Post by Crafty Kisses on 2009-08-04
Have you tried manually loading the module by running the following?
```
modprobe ath9k
```

---

### Post by MadHatter21 on 2009-08-04
Yes i have tried to load the driver manually but does not change anything. I think it might not be that the driver isnt loading but something else.

---

### Post by Crafty Kisses on 2009-08-04
So just to clarify this, the issue is sometimes your wireless works and other times it doesn't upon numerous reboots?

---

### Post by MadHatter21 on 2009-08-04
So at first it was working fine, after a few reboots and update manager it doesnt work.

---

### Post by Crafty Kisses on 2009-08-04
Hmmm, so it must have been an update you ran, was there any kernel updates in there?

---

### Post by MadHatter21 on 2009-08-04
I am not sure, dont remember. Is there a way to check? If that is the problem then how would i get it to work.

---

### Post by Crafty Kisses on 2009-08-04
Well here's what I would do, you should have earlier kernels you can boot into via GRUB. Are you able to boot into any earlier kernels when you first boot up your computer?

---

### Post by MadHatter21 on 2009-08-04
Booting into 2.6.28-14 generic kernel now instead of 2.6.28-15 generic and it is working. Why is that? The led for the wifi card is on and everything. Could it be that i have installed the kernel for the 2.6.28-14 and then upgraded to the 2.6.28-15 and the same thing will not work? Reinstall on 2.6.28-15 generic?

---

### Post by Crafty Kisses on 2009-08-04
Hah! I knew it, must have been a kernel update, or some update that is conflicting with the wireless card. I would file a bug report with Launchpad, and hopefully in the next update, it will fix your card, but for now use the older kernel.

---

### Post by MadHatter21 on 2009-08-04
Hey your good man. How would i set the default boot to go straight off of the older kernel then the newer stuff? Instead of waiting for the next update, do you know of any other way to get the atheros ar5b95 card working with the current kernel?

Thanks for the help, and you arnt good, your great!:KS

MadHatter21

---

### Post by Crafty Kisses on 2009-08-04
Hey there, so now I'm not sure about this, are you saying how would I take out the selections I want? For example this is my GRUB menu list:

```


title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		21ff3c0c-8816-4f03-beb1-8aa5dfcf7b59
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=21ff3c0c-8816-4f03-beb1-8aa5dfcf7b59 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		21ff3c0c-8816-4f03-beb1-8aa5dfcf7b59
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=21ff3c0c-8816-4f03-beb1-8aa5dfcf7b59 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		21ff3c0c-8816-4f03-beb1-8aa5dfcf7b59
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=21ff3c0c-8816-4f03-beb1-8aa5dfcf7b59 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		21ff3c0c-8816-4f03-beb1-8aa5dfcf7b59
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=21ff3c0c-8816-4f03-beb1-8aa5dfcf7b59 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		21ff3c0c-8816-4f03-beb1-8aa5dfcf7b59
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=21ff3c0c-8816-4f03-beb1-8aa5dfcf7b59 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		21ff3c0c-8816-4f03-beb1-8aa5dfcf7b59
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=21ff3c0c-8816-4f03-beb1-8aa5dfcf7b59 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		21ff3c0c-8816-4f03-beb1-8aa5dfcf7b59
kernel		/boot/memtest86+.bin
quiet
```
Now for example, if I want to remove an older kernel/newer kernel I would just remove the one I wanted. So for example, I have the following line in my GRUB menu:
```
title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		21ff3c0c-8816-4f03-beb1-8aa5dfcf7b59
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=21ff3c0c-8816-4f03-beb1-8aa5dfcf7b59 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet
```
Now if I wanted to remove that selection, I would just simply highlight it, and remove it. So now in order for you to do this, just run in the terminal **(Applications->Accessories->Terminal)**:
```
sudo gedit /boot/grub/menu.lst
```
Then follow my instructions, alternatively you can simply run as root:
```
apt-get remove kernelname
```
That might work too, I've hoped I helped. Don't thank me for helping, I'm so glad I could help you, it's been a pleasure my good friend!

---

### Post by MadHatter21 on 2009-08-04
Thanks yes that would work. But is there a way to get the ath9k driver working on my newer kernel that you know of?

Still thanks a million,
MadHatter21

---

### Post by Crafty Kisses on 2009-08-04
Actually, on your newer kernel install, try running the following:
```

echo 0 > /sys/devices/platform/asus-laptop/bluetooth # disable bluetooth
echo 1 > /sys/devices/platform/asus-laptop/wlan # enable wireless
```
See if that gets your wireless card up and running, now to my knowledge the newer kernel your running is:
```
2.6.28-15
```
Now that fix was by, I can't remember, but where it says "asus-laptop" that might change, not sure you can always run:
```
/sys/devices/platform
```
Then press TAB, and see your options, hope this helps.

---

### Post by Crafty Kisses on 2009-08-04
To confirm what kernel you're using, you can run the following command:
```
uname -r
```

---

### Post by MadHatter21 on 2009-08-05
There is no asus laptop directory.

---

### Post by Crafty Kisses on 2009-08-05
Run the following in terminal:
```
/sys/devices/platform
```
Then press TAB twice, what are the results, just copy and paste.

---

### Post by MadHatter21 on 2009-08-05
Do you want the ls command with 8 options or the double tab with a few thousand?

---

### Post by Crafty Kisses on 2009-08-05
8 options. ;-)

---

### Post by MadHatter21 on 2009-08-05
eisa.0
Fixed MDIO bus.0
i8042
pcspkr
power
regulatory.0
serial8250
uevent

There you go. And of course there is the . and .. as well.

Mad Hatter 21

---

### Post by Crafty Kisses on 2009-08-05
Hmmm, what are the contents of this file:
```
cd /sys/devices/platform/eisa.0
```
Once you're in the directory, type:
```
ls
```
Copy and paste the results to me.

---

### Post by MadHatter21 on 2009-08-05
> **Codename said:**
> Hmmm, what are the contents of this file:
```
cd /sys/devices/platform/eisa.0
```
Once you're in the directory, type:
```
ls
```
Copy and paste the results to me.

Although i am a noob to linux i do understand common commands like ls. ha and the contents of the directory are

modalias
power
subsystem
uevent

MadHatter21

---

### Post by Crafty Kisses on 2009-08-05
Hmmm, I'm not too sure I don't see anything that corresponds for what I'm looking for obviously since your using a Gateway netbook, I mean I'm not too sure what you could do right now to get it working, my suggestion to you is uninstall and reinstall the driver, try that and get back to me.

---

### Post by MadHatter21 on 2009-08-05
> **Codename said:**
> Hmmm, I'm not too sure I don't see anything that corresponds for what I'm looking for obviously since your using a Gateway netbook, I mean I'm not too sure what you could do right now to get it working, my suggestion to you is uninstall and reinstall the driver, try that and get back to me.

I will pm you the results tmro. good night

---

### Post by MadHatter21 on 2009-08-05
Reinstalled and it works, thanks for all of the help.

---

### Post by Crafty Kisses on 2009-08-05
No problem man anytime! I'm thrilled I could help you!

---

