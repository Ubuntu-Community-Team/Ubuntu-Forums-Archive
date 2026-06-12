---
title: "onboard atheros AR8151 driver atl1c problem"
date: 2011-12-03
forum: Networking &amp; Wireless
---

### Post by ledzgio on 2011-12-03
Hi all,

I have installed ubuntu 11.10 ant everythink works like a charm except for ethernet driver. It disconnect when I download with deluge torrent at high speed and thus I have to restart network-manager service to get it working again.

The ethernet card is onboard Atheros AR8151, the motherboard is ASRock HS1M-GS.

lspci -nnk | grep -iA2 net output is:

02:00.0 Ethernet controller [0200]: Atheros Communications AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
	Subsystem: ASRock Incorporation Device [1849:1083]
	Kernel driver in use: atl1c

uname -a output:

Linux scantinato-desktop 3.0.0-14-generic-pae #23-Ubuntu SMP Mon Nov 21 22:07:10 UTC 2011 i686 i686 i386 GNU/Linux

It appears to be working well most of the times but It gets disconnected and in dmesg I can get the attached error when the network get disconnected.

Any ideas? 


thank you very much

---

### Post by waxillium on 2011-12-05
I'm having the same problem in Ubuntu Server 11.10 with an AR8132 on an EeePC 1005HA. I did not have any issues in 11.04. For now I'm using a cron that does "ifdown eth0 && ifup eth0" (restarts the network connection) every 15 minutes, which is horrible, but I can't find any proper solution.

lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Atheros Communications AR8132 Fast Ethernet [1969:1062] (rev c0)
        Subsystem: ASUSTeK Computer Inc. Device [1043:838a]
        Kernel driver in use: atl1c

uname -a
Linux TerribleTerror 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:25:36 UTC 2011 i686 i686 i386 GNU/Linux

---

### Post by waxillium on 2011-12-05
I think I actually found a solution. I've installed the 3.1 kernel and the problem seems to go away. Check out

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.1-oneiric/")

for the .deb files and

[http://askubuntu.com/questions/72714/how-can-i-upgrade-kernel-to-3-1](http://askubuntu.com/questions/72714/how-can-i-upgrade-kernel-to-3-1)

for the installation steps.

Another possible solution might be downgrading to the 2.6 kernel: [http://askubuntu.com/questions/71139/how-to-downgrade-the-kernel-on-11-10](http://askubuntu.com/questions/71139/how-to-downgrade-the-kernel-on-11-10)

---

### Post by ledzgio on 2011-12-05
> **waxillium said:**
> I think I actually found a solution. I've installed the 3.1 kernel and the problem seems to go away. Check out

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.1-oneiric/")

for the .deb files and

[http://askubuntu.com/questions/72714/how-can-i-upgrade-kernel-to-3-1](http://askubuntu.com/questions/72714/how-can-i-upgrade-kernel-to-3-1)

for the installation steps.

Another possible solution might be downgrading to the 2.6 kernel: [http://askubuntu.com/questions/71139/how-to-downgrade-the-kernel-on-11-10](http://askubuntu.com/questions/71139/how-to-downgrade-the-kernel-on-11-10)

Ok perfect, I hope this will fix mine too, I'll check it out after work and I'll let you know.

thanks

---

### Post by ledzgio on 2011-12-05
Nothing, same problem. 

I have tried kernel 3.1 and also 3.2-rc4 but the bugs is still present. I have noticed that the driver seems to crash after loads of data, when the speed is very high and that with the experimental kernels I have tried, it seems to crash less frequent than before.

---

### Post by kio_http on 2011-12-05
> **ledzgio said:**
> Nothing, same problem. 

I have tried kernel 3.1 and also 3.2-rc4 but the bugs is still present. I have noticed that the driver seems to crash after loads of data, when the speed is very high and that with the experimental kernels I have tried, it seems to crash less frequent than before.

For me I had the same issue but then when I set KDE's auto connect in network settings the problem went away

---

### Post by ledzgio on 2011-12-05
> **kio_http said:**
> For me I had the same issue but then when I set KDE's auto connect in network settings the problem went away

Isn't it enabled by defaul? Which is the equivalent in Ubuntu 11.10?

---

### Post by kio_http on 2011-12-06
> **ledzgio said:**
> Isn't it enabled by defaul? Which is the equivalent in Ubuntu 11.10?

Sorry no idea about that. For me I manually created a network profile and checked auto connect for the adapter. Normally on other adapters, they just work without touching settings (assuming DHCP is running on the router).

---

### Post by ledzgio on 2011-12-06
I think in Ubuntu 11.10 autoconnect is enabled by default.


waxillium can you confirm that your solutions is actually working for you?

---

### Post by kio_http on 2011-12-06
> **ledzgio said:**
> I think in Ubuntu 11.10 autoconnect is enabled by default.


waxillium can you confirm that your solutions is actually working for you?

It is enabled as I said but for some reason on this adapter, I have to manually delete the current network profile then create a new one and set auto connect on.

---

### Post by waxillium on 2011-12-06
It seems I've spoken too soon. Indeed, the network connection fails less frequently with 3.1, but it still does. Now I'm trying kernel 2.6.38-12 (the one from Natty). I'll see how it goes and get back to you tomorrow.

---

### Post by ledzgio on 2011-12-07
> **waxillium said:**
> It seems I've spoken too soon. Indeed, the network connection fails less frequently with 3.1, but it still does. Now I'm trying kernel 2.6.38-12 (the one from Natty). I'll see how it goes and get back to you tomorrow.

Ok let me know if you are lucky with that.

In the meanwhile, I have found a patch that seems to fix our bug but I don't have the sources to apply the patch to and I don't know where I can download it. If someone know how to proceed it could be very useful.

[http://patchwork.ozlabs.org/patch/125198/](http://patchwork.ozlabs.org/patch/125198/)

---

### Post by waxillium on 2011-12-07
> **ledzgio said:**
> Ok let me know if you are lucky with that.

In the meanwhile, I have found a patch that seems to fix our bug but I don't have the sources to apply the patch to and I don't know where I can download it. If someone know how to proceed it could be very useful.

[http://patchwork.ozlabs.org/patch/125198/](http://patchwork.ozlabs.org/patch/125198/)

Fantastic. Neither of the kernels 2.6.38-12-generic (the one left from Natty) or 2.6.38-10-generic (one I've downloaded) solve the bug. I've never recompiled a kernel before but it seems a little tedious. Also, since the old 2.6 kernel which worked in Natty doesn't work in Oneiric, I'm not sure if this patch will solve anything.

I'm thinking of trying Debian Squeeze on another partition to see if the bug is present there too.

---

### Post by ledzgio on 2011-12-07
> **waxillium said:**
> Fantastic. Neither of the kernels 2.6.38-12-generic (the one left from Natty) or 2.6.38-10-generic (one I've downloaded) solve the bug. I've never recompiled a kernel before but it seems a little tedious. Also, since the old 2.6 kernel which worked in Natty doesn't work in Oneiric, I'm not sure if this patch will solve anything.

I'm thinking of trying Debian Squeeze on another partition to see if the bug is present there too.

Yes, very bad news. However I don't think you need to recompile the kernel but just the driver..the only things you need are the sources of the driver and the kernel-headers installed.
The problem is that I don't have the sources and I don't know where to find it.

Which is the last kernel that worked with this ethernet card?


p.s. I will also try to run some debian based distribution to understand if the bug is present there too.

---

### Post by jamesthenail on 2011-12-27
Hi, all:

I've got the same problem with Atheros AR8151 on Ubuntu 10.04 LTS which simply doesn't recognize the onboard lan card (Atheros AR8151 on Asus' P5G41T-M LX3). I tried versions later than 10.04LTS, they worked pretty well. But I can't do without Ubuntu 10.04. Is it a good idea to get the driver and have it installed for AR8151? Where? How? I feel like a blind cat smelling a delicious rat playing with its tail. Someone could help? 

Thanks.

---

