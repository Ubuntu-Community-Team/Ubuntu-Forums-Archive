---
title: "Dell Very Annoying Driver Problem (Inspiron 1545, Broadcom 4312)"
date: 2011-06-25
forum: Networking &amp; Wireless
---

### Post by adro947 on 2011-06-25
Have had Ubuntu 10.04 64-bit on my laptop for months and it's great. It's a Dell Inspiron 1545. It has a Broadcom 4312 wireless card. Now I can get the wireless working, but not without driving myself mad every time I turn the laptop on. (For that reason, I think this is different to the sticky above.) :mad:

So anyway, when I boot up it doesn't even detect a wireless network card. So, as you might expect I go to System --> Administration --> Hardware Drivers. When I open that, it says that the "Broadcom STA Wireless Driver" is activated. So what I've found is, when I remove it and activate it again, the wireless starts working.

Now this is slowly driving me insane. I'd rather not have to go through this very annoying procedure when I start Ubuntu. It makes both Windows Vista and Windows XP which I also have on here much more attractive. Anyone have any solutions? Also, in case this affects anything with conflicts or whatever...If I go to System --> Administration --> Windows Wireless Drivers, then It also says it has a driver for the Broadcom card. I removed that driver however, and everything happens exactly the same as before so I don't believe it's an issue.

Any help would be very much appreciated!

---

### Post by chili555 on 2011-06-25
Please try an experiment. Turn off your computer completely. Start it and run in the terminal:```
lsmod > adrobefore.txt
```Activate the maddening wireless and then run:```
lsmod > adroafter.txt
```Post the two text files to your reply using the paperclip tool at the top of the reply box. My suspicion is that the driver module is not loading automatically and we'll see what's missing from before to after. Then we'll load the module automatically on boot and life will be good!

---

### Post by adro947 on 2011-06-25
> **chili555 said:**
> Please try an experiment. Turn off your computer completely. Start it and run in the terminal:```
lsmod > adrobefore.txt
```Activate the maddening wireless and then run:```
lsmod > adroafter.txt
```Post the two text files to your reply using the paperclip tool at the top of the reply box. My suspicion is that the driver module is not loading automatically and we'll see what's missing from before to after. Then we'll load the module automatically on boot and life will be good!

Ok, here are the files...

Thanks :)

---

### Post by chili555 on 2011-06-25
*before*, we see that ndiswrapper is loaded; *after*, we see that ndiswrapper is not loaded and wl and dkms *are* loaded. Let's see:```
ndiswrapper -l
```That's a lower-case L there, not a one. Since ndiswrapper conflicts with wl, we're probably going to remove ndiswrapper and load wl on boot. Before we warm up the bone saw, let's see the result I asked for above.

---

### Post by adro947 on 2011-06-25
> **chili555 said:**
> *before*, we see that ndiswrapper is loaded; *after*, we see that ndiswrapper is not loaded and wl and dkms *are* loaded. Let's see:```
ndiswrapper -l
```That's a lower-case L there, not a one. Since ndiswrapper conflicts with wl, we're probably going to remove ndiswrapper and load wl on boot. Before we warm up the bone saw, let's see the result I asked for above.

> adrian@adrian-laptop:~$ ndiswrapper -l
yk60x64 : invalid driver!


The "yk60x64" there represents the Marvell Yukon ethernet port. That works fine and I have no issues with that. No wireless drivers are listed. As said above, I removed them.

---

### Post by chili555 on 2011-06-25
May we see:```
cat /etc/modprobe.d/ndiswrapper
cat /etc/modprobe.d/ndiswrapper.conf
```If you have such a file, we can probably just delete it and be freed of ndiswrapper. Also:```
ls /etc/ndiswrapper
```Let's load wl automatically:```
sudo su
echo wl >> /etc/modules
exit
```Your wireless should start on boot now, but let's clean up ndiswrapper.

---

### Post by nerdy_kid on 2011-06-25
you may need to run 
```

sudo update-initramfs -u

```
after adding wl to /etc/modules AFAIK

---

### Post by adro947 on 2011-06-25
Excellent. The wireless works perfectly now :) Superb. :)

For information, I didn't have to run update-initramfs -u.

So I should remove ndiswrapper yes?

Anyway, as requested:

> adrian@adrian-laptop:~$ cat /etc/modprobe.d/ndiswrapper
alias pci:v000014E4d00004311sv00000007sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00000007sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00000008sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv00000008sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004311sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00000007sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00000007sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00000008sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv00000008sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004312sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004315sv0000000Bsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004315sv0000000Bsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004315sv0000000Csd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004315sv0000000Csd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004315sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004315sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv00000005sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv00000005sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv00000006sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv00000006sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004318sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv00000005sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv00000005sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv00000006sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv00000006sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004319sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000001sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000001sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000002sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000002sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000003sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000003sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000004sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv00000004sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004320sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv00000001sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv00000001sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv00000002sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv00000002sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv00000003sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv00000003sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv00000004sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv00000004sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004324sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv00000009sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv00000009sd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv0000000Asd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv0000000Asd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d00004328sv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d0000432Bsv0000000Dsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000432Bsv0000000Dsd00001028bc*sc*i* ndiswrapper
alias pci:v000014E4d0000432Bsv*sd*bc*sc*i* ndiswrapper
alias pci:v000014E4d0000432Bsv*sd*bc*sc*i* ndiswrapper

/etc/modprobe.d/ndiswrapper.conf doesn't exist apparently...

> adrian@adrian-laptop:~$ cat /etc/modprobe.d/ndiswrapper.conf
cat: /etc/modprobe.d/ndiswrapper.conf: No such file or directory


> adrian@adrian-laptop:~$ ls /etc/ndiswrapper
yk60x64


---

### Post by chili555 on 2011-06-25
> So I should remove ndiswrapper yes?Yes, please; it's not needed:```
sudo ndiswrapper -e yk60x64 
sudo rm /etc/modprobe.d/ndiswrapper
```You should be all set. You may wish to use the thread tools at the top and mark the thread Solved.

---

### Post by adro947 on 2011-06-25
> **chili555 said:**
> Yes, please; it's not needed:```
sudo ndiswrapper -e yk60x64 
sudo rm /etc/modprobe.d/ndiswrapper
```You should be all set. You may wish to use the thread tools at the top and mark the thread Solved.

Done! Will do.

---

