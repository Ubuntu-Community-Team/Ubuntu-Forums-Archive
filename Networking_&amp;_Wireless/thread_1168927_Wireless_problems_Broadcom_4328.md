---
title: "Wireless problems Broadcom 4328"
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by email2mickey on 2009-05-24
Hi completely new to ubuntu and just downloaded 9.04 on an Inspiron 1721 running Vista. Wired connection works fine but wireless does not (dont see my network as being recognized). Wireless works fine with Vista. Can someone help pls. Thx.

---

### Post by Idefix82 on 2009-05-24
Try this: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")

Actually, the instructions are not so easy to follow if you are completely new to Ubuntu. If you stay online for half an hour, I would be willing to guide you through it. Start by typing in the terminal
```
lspci | grep Bro
```
and paste the output here. Then we'll take it from there.

---

### Post by email2mickey on 2009-05-24
Thx a lot for your help. You are right, tried to follow but got lost.

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0b:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

---

### Post by Idefix82 on 2009-05-24
OK. You will need a tool called ndiswrapper, which is used to run Windows wireless drivers under Linux. Most of the work will be in the terminal, because that's easiest to explain (instead of 'go to the menu, click the second pixel from the right,...). So, in the terminal, please run
```
sudo apt-get install ndiswrapper-utils-1.9
```
to install ndiswrapper. You will be prompted for your login password before the download begins. Let me know when you are done.

---

### Post by email2mickey on 2009-05-24
yes done. Thx

---

### Post by Idefix82 on 2009-05-24
Ok, now download this archive and unzip it into your home folder, say:
[http://myspamb8.googlepages.com/R151517-pruned.zip]("http://myspamb8.googlepages.com/R151517-pruned.zip")

In the terminal, change into the unzipped folder (to change folders use the cd command). Run
```
sudo ndiswrapper -i bcmwl5.inf
sudo rmmod ssb
sudo modprobe ndiswrapper
lshw -C network
```

and paste the output from the last command here.

---

### Post by email2mickey on 2009-05-24
Hi there was an error before that. Could be from one of the random fixes I was trying before.

email2mickey@ubuntu:~/Desktop$ sudo rmmod ssb
ERROR: Module ssb is in use by b44

---

### Post by Idefix82 on 2009-05-24
Ok. Can you first run
```
lshw -C network
```
and give me the output? Then try
```
sudo rmmod b44
sudo rmmod b43
sudo rmmod ssb
sudo modprobe ndiswrapper
```

and let me know if there were any errors. The chain of dependencies might be a bit longer, but don't worry, it will eventually terminate.

By the way, you also don't need to worry about breaking anything at the moment, because anything I am telling you to change now will be lost after the next reboot. Once we know what works, we will make it permanent.

---

### Post by email2mickey on 2009-05-24
email2mickey@ubuntu:~/Desktop$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:89:82:0b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.16 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2a:6c:0f:b6:40:f0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by Idefix82 on 2009-05-24
Thanks, this is important information. Now, do this, instead of what I told you at the end of the previous post:
```

sudo rmmod b44
sudo rmmod ssb
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44

```

---

### Post by email2mickey on 2009-05-24
Hi this is from another computer as the wired connection seemed to have been disabled after the sudo rmmod sequence of commands.

It gave me an error on b43 (module b43 does not exist in /proc/modules).

However in the netowork connection now I see my wireless network (havent enabled it as yet).

---

### Post by Idefix82 on 2009-05-24
Excellent! See my previous post. You now need to execute
```
sudo modprobe ssb
sudo modprobe b44
```
to bring back your wired connection. Sorry about that!

---

### Post by email2mickey on 2009-05-24
hi I had tried some of the rmmod commands from the previous post, but did the above sequence again. I do see my wireless now in the network box.

---

### Post by Idefix82 on 2009-05-24
Have you runt he last two commands I gave you? Did that bring the wired connection back?
What is the output from
```
lshw -C network
```
after running the above two commands?

---

### Post by email2mickey on 2009-05-24
Hi the wired network is back. I also see my wireless network but have not tried to connect to it as yet.

email2mickey@ubuntu:~/Desktop$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 03
       serial: 00:1c:26:2c:e0:4c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.53+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:89:82:0b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.16 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2a:6c:0f:b6:40:f0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by Idefix82 on 2009-05-24
Can you please try to connect to a wireless network and let me know how it goes? If it works (which I expect it should) then I will give you the commands to make the changes permanent.

---

### Post by email2mickey on 2009-05-24
Hi it took my passkey for the wireless network, but then seems to have a problem connecting (keeps on thinking).

---

### Post by Idefix82 on 2009-05-24
How long have you waited for? Can you connect to the wireless from other computers? What protocol is it, WEP or WPA?

---

### Post by email2mickey on 2009-05-24
It actually things for a while and then kicks me out. Other computer is working fine with the wireless. It is WPA Personal. TKIP encryption.

---

### Post by Idefix82 on 2009-05-24
I am currently looking whether there is an alternative windows driver that one can use. Can you give me the output from
```
uname -a
```
so I see whether you have an 64 bit or a 32 bit installation?

---

### Post by email2mickey on 2009-05-24
Linux ubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

---

### Post by Idefix82 on 2009-05-24
This is strange. I have not heard of this driver failing yet. I assume that you router is set to dhcp. Can you try configuring the router to use a static IP address and to configure your computer accordingly? You do that by right clicking onto the network icon and then "Edit connections..."

Before you do that, you can also try these commands from the tutorial:

```

sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant

```

I have to go to bed now, but meanwhile, this is how you make the settings permanent, so you can continue experimenting with the settings:

```

echo 'ndiswrapper' | sudo tee -a /etc/modules
modprobe -r b44 ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper

```

I will check up on you tomorrow.

---

### Post by email2mickey on 2009-05-24
Thanks a lot for your help. I will continue experimenting. Good night.

---

### Post by email2mickey on 2009-05-24
Hi Idefix82, still no luck but I tried below as you said:

echo 'ndiswrapper' | sudo tee -a /etc/modules
modprobe -r b44 ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper
However the second line below does not seem to work (get a > prompt after that).
Thx again.

---

### Post by Idefix82 on 2009-05-25
I'm sorry, the last line should have read
```

echo -e 'modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper

```

You don't need to repeat the previous line, only this one. For this boot, to bring up wireless, do
```

sudo rmmod b44
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44

```

---

### Post by Idefix82 on 2009-05-25
I just searched the forums a bit and it looks like this particular card together with ndiswrapper doesn't support WPA/TKIP, which is rather annoying.

There are a few things we can try. First, you can try switching your router to WEP. Admittedly, that's less secure and you might not like it as a long term solution.

We can also try a different driver. You can try running
```
sudo rmmod ndiswrapper
sudo rmmod b44
sudo rmmod ssb
sudo modprobe wl
sudo modprobe ssb
sudo modprobe b44
```

I don't have any experience with the wl driver, which is a native Linux driver, rather than a Windows driver under Linux, but some people report that it worked for them.

---

### Post by email2mickey on 2009-05-25
Hi Idefix82 the wireless works now! Unfortunately, not sure how. I tried your code sequence from yesterday. In addition (from other posts) I disabled the Broadcom wireless STA driver System/Preferences and then activated it again. Also, things seem to be working fine after boot, so I guess all the changes are permanent now. Thx again.

---

### Post by Idefix82 on 2009-05-25
Glad to hear it! I am curious though, how exactly it works. Can you give me the output from
```
lshw -C network
```
for the last time? And does there exist a file named /etc/modprobe.d/ndiswrapper and what is its content?

Enjoy surfing!

---

### Post by email2mickey on 2009-05-25
email2mickey@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 03
       serial: 00:1c:26:2c:e0:4c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 ip=192.168.1.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:89:82:0b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: c2:b0:9b:c0:44:58
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
email2mickey@ubuntu:~$ 

Think these are the contents of the file:
email2mickey@ubuntu:~$ cat /etc/modprobe.d/ndiswrapper
alias wlan0 ndiswrapper

---

### Post by Idefix82 on 2009-05-25
Nice, so the wl driver solved the problem. Good to know.

---

