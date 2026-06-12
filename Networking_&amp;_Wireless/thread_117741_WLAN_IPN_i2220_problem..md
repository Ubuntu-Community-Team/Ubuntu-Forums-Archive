---
title: "WLAN IPN i2220 problem."
date: 2006-01-15
forum: Networking &amp; Wireless
---

### Post by Omaha on 2006-01-15
Hi there,

I'm trying to get my WLAN to work on my Laptop but I'm having some problems. I followed this guide : [http://users.skynet.be/ostaquet/aceraspire1360/](http://users.skynet.be/ostaquet/aceraspire1360/) but it doesn't detect my WLAN :/

ndiswrapper -l gives me the following line :

Installed ndis drivers:
neti2220        driver present, hardware present

Help me plz ;)

Greetings

---

### Post by Rollmops on 2006-01-15
Have you tried the ipw2200 driver from [http://ipw2200.sf.net?](http://ipw2200.sf.net?)

---

### Post by Omaha on 2006-01-15
I'll give it a shot.

---

### Post by Omaha on 2006-01-19
They don't work. 

It's kinda strange that ndiswrapper says my driver (the one in my post) is present and the harware also is, but still it doesn't see my wlan :(

---

### Post by Lambert on 2006-01-19
breezy comes with the ipw2200 driver installed so it's possible that both drivers are loading and causing a conflict.

Post the output of this command

```
sudo lshw -C network
```

---

### Post by Omaha on 2006-01-20
```

*-network:0
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth0
       version: 10
       serial: 00:0c:76:f9:3f:7b
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.1.102 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:e800-e8ff iomemory:fbfffc00-fbfffcff irq:18
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
       vendor: Linksys, A Division of Cisco Systems
       physical id: 9
       bus info: pci@02:09.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: ioport:e400-e41f iomemory:fbfff800-fbfff81f iomemory:fbffe800-fbffefff irq:5

```

---

### Post by Omaha on 2006-01-21
No one who knows what the problem seems to be ? I'm wasting my time in windows atm since I don't have internet with ubuntu :(

---

### Post by Lambert on 2006-01-21
It doesn't look like ndiswrapper is loaded.

Check with this command

```
lsmod | grep ndis
```

If you get no output, just a new prompt then run this command.

```
sudo modprobe ndiswrapper
```

Check again with lsmod command.

When running the lshw command you should get a line like this under your wireless device.

 configuration: broadcast=yes driver=ndiswrapper 

Then from here you need to configure.

---

### Post by Omaha on 2006-01-21
lsmod | grep ndis gives me :

```

ndiswrapper           148692  0

```

lshw gives me this :

```

*-network:1 UNCLAIMED
                description: Ethernet controller
                product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
                vendor: Linksys, A Division of Cisco Systems
                physical id: 9
                bus info: pci@02:09.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                resources: ioport:e400-e41f iomemory:fbfff800-fbfff81f iomemory:fbffe800-fbffefff irq:5

```

so it seems nothing has changed.

---

### Post by Omaha on 2006-01-25
Still no internet :( Tried some other drivers, but they also didn't work :(

---

### Post by patrickfromspain on 2006-01-25
mmm Stop there. Don't confuse the IPN 2220 with the IPW 2200, that's the first thing.

Second: this card works fine with ndiswrapper. My laptop has the same card and works. It's a toshiba L10, I used the drivers that came with the laptop CD's.

After having loaded the windows drivers, you do modprobe ndiswrapper. And then what's the problem? If you go to System -> administration -> network it doesn't see your card??

---

### Post by Omaha on 2006-01-25
Yup, that's the problem. It only shows eth0 and modemconnection.

---

### Post by patrickfromspain on 2006-01-25
mm you could try the drivers from the toshiba site. Maybe...

---

### Post by Omaha on 2006-01-25
I've tried the drivers from the toshiba site. Still nothing.

First I removed the old driver with ndiswrapper -e command, then copied the driver folder to /opt/ (as told in the link in the beginning of this thread) and then installed it with ndiswrapper. After this I did 'ndiswrapper -m' and the terminal said this : "modprobe config already contains alias directive". Then I did 'modprobe ndiswrapper' and went to System -> Administration -> Network. It started searching I think, my mousepointer changed into the round-thingie, but then just showed me my eth0 and modem.

---

### Post by patrickfromspain on 2006-01-25
mm then I don't know what's happening. Are you using the 32bit or the 64bit breezy??

I just copied the driver to my home and then, sudo ndiswrapper -i driver.inf, sudo ndiswrapper -l, sudo ndiswrapper - and sudo modprobe ndiswrapper.. after that, my wlan0 appeared, and worked ok.

If you do iwlist scanning do you get something??

---

### Post by Omaha on 2006-01-25
I have 64-bit breezy. Will post my iwlist later.

---

### Post by patrickfromspain on 2006-01-25
aaaah ok then. I'm not sure if it will work, but you need the winxp 64 bit drivers... With a 64 bit breezy you need 64bit drivers.

---

### Post by patrickfromspain on 2006-01-25
[http://www.planetamd64.com/index.php?act=Attach&type=post&id=435](http://www.planetamd64.com/index.php?act=Attach&type=post&id=435)

you can get the drivers here.

---

### Post by apt on 2006-05-01
How did you manager to get WiFI working|. I've tried everything to get this working on my L10 , I've managed to get the windows wifi driver installed using ndiswrapper and it is recognised by the hardware but everytime I try and load the driver is gives me an error in the log something about not being able to load the driver. I'm using 32bit Dapper beta (should I try Breezy?)

Ay suggestions?

Regards

Adrian

---

### Post by michael71034 on 2006-05-01
I solved a similar problem by switching the WLAN channel from 12 to 6 and adding the channel info with iwconfig eth1 channel 6.

I know it sounds funny...

---

