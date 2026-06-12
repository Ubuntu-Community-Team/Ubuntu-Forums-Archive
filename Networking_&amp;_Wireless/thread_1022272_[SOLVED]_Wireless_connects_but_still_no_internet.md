---
title: "[SOLVED] Wireless connects but still no internet"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by benthegreat on 2008-12-26
This has really confused me!!

I recently acquired a dell latitude D400. I'm dual booting XP and ubuntu. Nothing unusual there... I'm using a wireless dongle (onboard is not an option); a netgear WG111 (v3). It works fine, with windows and (once at least) with ubuntu.

I have used this setup on a bthome hub firstly, using WEP encryption. All was good! I then bring the laptop home, where I'm using WPA 2. Windows still works fine and shows no sign of change. Ubuntu did work fine for a bit, but recently (and i really have no idea what changed) I lost internet access. I can still see my network, I can still connect to my network and ethernet still works fine. All the connection details check out aswell. The laptop apears as it should on the router's dhcp table.

For some reason I cannot find any webpages. I have tried disabling IPV6 and tried to recieve emails. Both the no avail. Windows still works (I'm as shocked as you are!).

It is possible I've forgotten something, any suggestions are welcome.

---

### Post by lsutiger on 2008-12-26
Can you ping successfully inside and outside your network?

---

### Post by benthegreat on 2008-12-26
Thanks for the reply

Last time I tried, I couldn't ping my router.

---

### Post by benthegreat on 2008-12-26
Heres something interesting... While trying to get a ping to my router, I descovered that there is a breif period while I am connecting to the network, where I can comunicate with the router. Once fully connected I cannot ping or connect to anything.

I hope this helps...

---

### Post by lsutiger on 2008-12-26
I am really at a loss here. I am leaning toward a driver issue. Have you had a driver update? What brand is the wireless dongle? And is it USB?
Do you have an IP?

And to add to my ignorance, I did not know that WPA2 was supported yet...

I will try to help you!

---

### Post by kevdog on 2008-12-26
Getting an IP address but inability to see the internet usually indicated either a dhcp problem or route problem.  If you can ping an external IP address by number then its a dhcp problem.  If you can ping the router but not any external ip address then its possibly a route problem.

---

### Post by benthegreat on 2008-12-27
The dongle has worked in ubuntu on different networks, and works fine in XP. It connects fine briefly, I can ping and even browse for a short period of time [about 3seconds] (if I get it right).

To see it helps, i've made that dongle's mac address static to one IP, it makes no difference (it can't hurt).

I can't ping anything once "fully" connected. But I do appear on the dhcp table.

---

### Post by benthegreat on 2008-12-28
Further testing...

I reset my router's settings today...

LAN Ethernet stuff is fine, but I now can't see the network at all in ubuntu. More twiddling is in order...

---

### Post by benthegreat on 2008-12-28
Breakthourgh!!!

I switched channel selection off, and set it to channel 6 (its the norm i believe) and it worked....

I'm going to try building security back up, hopefully ill break it again so we can see exactly what was stopping it before...

---

### Post by benthegreat on 2008-12-28
I'v had a thought... It tends to work in certain places, where (I think) the wireless signal is strongest (like directly underneath the transmitter). Could it be (and this is just a hunch), that the drivers for the netgear dongle arn't sending strong enough authentication signals, seeing as I can always connect, but not always access the network. Any thoughts anyone?

---

### Post by benthegreat on 2008-12-28
After much starting and stalling (does it work, no.. yes...no...) I think I've cracked it. I'm not going to say definitely just in case.

I discovered that, for some reason, the default driver in linux decides that any signal strength under about 50% is deemed unworthy of access! And only when your constantly over 50% (about) does it play ball. This is a bit of a problem in my household, seeing as the female powers that be state that our router has to be "tucked away", not good for optimum range...

So, as lsutiger suggested, it looks like the linux driver can use the adapter, but is somewhat unsuited to it, and is therefore inefficient in usage.

I'm now running it happily with ndiswrapper, the windows drivers are very ndiswrapper friendly.

This reply is being writen from the furthest point possible from the router (my room). It remains to be seen whether the setup "holds" after more usage, but for now, problem solved.

---

### Post by mahasmb on 2008-12-28
> **benthegreat said:**
> 

I discovered that, for some reason, the default driver in linux decides that any signal strength under **_*about 50%*_** is deemed unworthy of access! And only when your constantly over 50% (about) does it play ball. This is a bit of a problem in my household, seeing as the female powers that be state that our router has to be "tucked away", not good for optimum range...


Please tell me that's not true. It's ridiculous. I'm having the same problem and if Windows XP can surf the web just fine I should be able to do so on my Ubuntu partition as well!

---

### Post by Lostin60's on 2008-12-28
> **mahasmb said:**
> Please tell me that's not true. It's ridiculous. I'm having the same problem and if Windows XP can surf the web just fine I should be able to do so on my Ubuntu partition as well!

Having just had the internet connection fight myself I will add my minuscule knowledge. Assuming you are using ndiswrapper, open a terminal and run this command:
 
ndiswrapper -l
If you get a message like this:
netwg111 : driver installed device (0846:4240) present (alternate driver: p54usb) 
then your driver is installed. next, run this command:

sudo lshw -c network
You will an output like this
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:0b:02.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:ae:dd:bb
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:0b:03.0
       logical name: wlan0
       version: 03
       serial: 00:14:a5:14:76:70
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes [COLOR="Red"]driver=ndiswrapper+bcmwl5[/COLOR] driverversion=1.53+Broadcom,12/17/2005, 4.10.4 ip=192.168.2.2 latency=64 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: aa:b9:5f:a2:fe:b3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

The output in red is what you will be looking for. If this does not match the windows driver you installed, you can blacklist the driver listed there (probably b43) and ssb.  Reboot and you you should connect.

---

### Post by mahasmb on 2008-12-28
I'm not using ndiswrapper. After doing a fresh install of Intrepid, I only just replaced network-manager with WICD. It was working fine then for a few days and now I can connect to my network, but I've still got no internet access. My connectivity is at about 30%, which allowed me to surf the web just fine before this mysterious problem.

---

### Post by benthegreat on 2008-12-28
> Please tell me that's not true. It's ridiculous. I'm having the same problem and if Windows XP can surf the web just fine I should be able to do so on my Ubuntu partition as well!

It's a simple matter or the basic generic driver not being adapted properly to some dongles. The ndiswrapper thing is incredibly useful, most of the time the windows driver can be used as the ubuntu one!!

I just followed this:[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper"). It works a treat. I actually ended up not blacklisting the old drivers, that tended to break it more!

Look at this way; the hardest part is done, you at least know what the problem is...

---

### Post by Dazed &amp; Confused on 2008-12-29
Benthegreat, you're a hero. Thanks for pointing a linux newbie to the channel issue. It's brought sense and network detection to a lowly Dell Latitude d600 which otherwise only connected to the net by wire.

Now to tackle a desktop without a wire. hmmm

---

### Post by mahasmb on 2008-12-30
Okay, I can get reliable internet now after installing ndiswrapper, but I for some reason need to reinstall the drivers every startup.

It's annoying. And a huge pain.

---

### Post by lsutiger on 2008-12-31
Happy you got it solved! Happy Ubuntuing!

> **benthegreat said:**
> After much starting and stalling (does it work, no.. yes...no...) I think I've cracked it. I'm not going to say definitely just in case.

I discovered that, for some reason, the default driver in linux decides that any signal strength under about 50% is deemed unworthy of access! And only when your constantly over 50% (about) does it play ball. This is a bit of a problem in my household, seeing as the female powers that be state that our router has to be "tucked away", not good for optimum range...

So, as lsutiger suggested, it looks like the linux driver can use the adapter, but is somewhat unsuited to it, and is therefore inefficient in usage.

I'm now running it happily with ndiswrapper, the windows drivers are very ndiswrapper friendly.

This reply is being writen from the furthest point possible from the router (my room). It remains to be seen whether the setup "holds" after more usage, but for now, problem solved.

---

