---
title: "Network manager does not show my wireless connection"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by jason44 on 2009-03-30
I recently bought a Compaq Presario Laptop, Model CQ60-211DX, that came with wireless B+G networking. The laptop came preloaded with Vista and I was able to connect to my wireless router with no problem. However, when I installed Ubuntu 8.10 and went to the Network Manager it could not find any wireless connections. I am wondering if the driver for the wireless is not supported or if I am doing something wrong. I had to switch back to Vista for the wireless connection but would love to figure out how to fix my wireless connection in Ubuntu so I can switch back. Any help would be great.

---

### Post by atomizer on 2009-03-30
Please do ```
sudo lshw -C network
``` in a terminal and give us the output, so we know what wireless card you are talking about.
There are many different tweaks for different wireless cards.

---

### Post by jason44 on 2009-03-30
here is the results:

*-Network 

Desc: Ethernet Interface
Prod: RTL810E/RTL8102E PCI Express Fast Ethernet Controller
Vend: Realtek Semiconductor Co., Ltd.
Physical ID: 0
Logical Name: eth0
Serial: 00:1f:16:6e:b3:d8
Size: 1GB/s
Capacity: 1GB/s
Width: 64 Bits
Clock: 33 MHz

*-Network Unclaimed

Desc: Ethernet Controller
Prod: AR242x 802.11abg Wireless PCI Express Adapter
Vend: Atheros Communications Inc.
Phys ID: 0
Bus Info: pci0000:02:00:0
Width: 64 Bits
Clock: 33MHz

*-Network Disabled

Desc: Ethernet Interface
Phys. ID: 1
Logical Name: pan0
Serial: 5a:82:ea:2d:54:92

---

### Post by golliwog on 2009-03-30
> **jason44 said:**
> here is the results:

*-Network Disabled



I was getting this error when I first installed 8.10, although it recognized my card.  I had to use a ethernet cable to get to the net, then run the auto-updates and restart the computer.  When Ubuntu came back up it updated the driver automatically.  

*Note* I have a different Wireless card than you.

-g

---

### Post by atomizer on 2009-03-31
I see you have the same wireless as me

solution is fairly simple:

1) if you have the atheros restricted drivers enabled, disable them.

2) install linux-backports-modules-intrepid

3) reboot


and voila: the wireless should work now

---

### Post by pro003 on 2009-03-31
Open the terminal and type:

```
ifconfig -a
```

and if you see ath0 or wifi0 you should get it up by typing command:

```
ifconfig ath0 up
```


you can also try to install madwifi atheros drivers as well, if they aren't already installed of course.

hope it helps

---

### Post by jason44 on 2009-04-02
Thanks Atomizer for the info. Could you do one better and explain a little more in depth about the first 2 steps. I am real green to Linux and some of the lingo. Quite frankly, I don't know where to go to do those steps. I would appreciate your patience to guide me through.

---

### Post by atomizer on 2009-04-02
Who hasn't been a green with linux :P:P


It's been a while since I  have used the Gnome desktop so I have to do it by head:

1) the restricted drivers are found in system ==> administration (?) ==> restricted drivers. the little icon looks like a pci card.

there you can (un)choose the restricted atheros driver (and mostly the restricted ati or nvidia driver for your 3d acc.)


2) you can install linux-backports-modules-intrepid with synaptic, your package manager. Make shure you have selected all repositories in settings ==> reposetories (and do an "reload" after you checked all possebilities)

you should find linux-backports-modules-intrepid with the search function.

mark for install and press apply.

3) reboot :P:P:P

---

