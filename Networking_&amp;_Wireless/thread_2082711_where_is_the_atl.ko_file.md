---
title: "where is the atl.ko file ?"
date: 2012-11-10
forum: Networking &amp; Wireless
---

### Post by Rudra G on 2012-11-10
I've an Asus P5GC-MX/1333 motherboard with 32bit Intel Core 2 duo. Atheros L2 & Realtek drivers are not working. I had downloaded attansicl2.tgz file & tried to move that file to /lib/modules/3.5.0-17-generic/kernel/drivers/net/atl.ko, however I found no **_atl.ko_** files in that directory. Please help. I am completely new to any linux OS

---

### Post by Abhinav Kumar on 2012-11-11
> **Rudra G said:**
> I've an Asus P5GC-MX/1333 motherboard with 32bit Intel Core 2 duo. Atheros L2 & Realtek drivers are not working. I had downloaded attansicl2.tgz file & tried to move that file to /lib/modules/3.5.0-17-generic/kernel/drivers/net/atl.ko, however I found no **_atl.ko_** files in that directory. Please help. I am completely new to any linux OS
Hi,

I think you need to first  extract the file to a proper location and then you have to move the file. Say you extracted the tgz in a folder say sampleFolder inside your home directory. Note that the atl.ko is the file and not a directory. 

Then, do the following code
```

sudo cp ~/sampleFolder/atl.ko /lib/modules/3.5.0-17-generic/kernel/drivers/net/

```
Now to see the contents of the folder
```

ls /lib/modules/3.5.0-17-generic/kernel/drivers/net/

```

:)

Regards,
Abhinav

---

### Post by chili555 on 2012-11-11
However, you won't have an atl.ko in that directory until you compile the package for your running kernel. If you can provide us with some details, we will be glad to help. Open a terminal and run and post:```
lspci -nn | grep 0200
lsb_release -d
```Can you give us a link to the file you downloaded? Maybe there is a newer file or a better way.

---

### Post by Rudra G on 2012-11-12
> **Abhinav Kumar said:**
> Hi,

I think you need to first  extract the file to a proper location and then you have to move the file. Say you extracted the tgz in a folder say sampleFolder inside your home directory. Note that the atl.ko is the file and not a directory. 

Then, do the following code
```

sudo cp ~/sampleFolder/atl.ko /lib/modules/3.5.0-17-generic/kernel/drivers/net/

```
Now to see the contents of the folder
```

ls /lib/modules/3.5.0-17-generic/kernel/drivers/net/

```

:)

Regards,
Abhinav
Thnx for reply . I've downloaded that tgz file to my USB drive using my Windows XP & have extracted on the same drive. The link is [http://vitriol.ntbti.com/wp-content/...attansicl2.tgz](http://vitriol.ntbti.com/wp-content/...attansicl2.tgz)  from where I've  had downloaded.

---

### Post by Rudra G on 2012-11-12
Tanx for reply. The link is [http://vitriol.ntbti.com/wp-content/...attansicl2.tgz](http://vitriol.ntbti.com/wp-content/...attansicl2.tgz) from where I've had downloaded. I was using Windows XP to download onto my USB drive & I've had it extracted over there. And I've to use windows XP to gain access to internet. I hope you can understand my words

---

### Post by chili555 on 2012-11-12
The file included, atl2.ko was built in 2007 for who knows what kernel. It isn't going to work...*no way, no how*...in your shiny new 12.10 kernel. Moreover, your shiny new 12.10 kernel already includes atl2:```
chili@LAPTOP410:~$ modinfo atl2
filename:       /lib/modules/3.5.0-18-generic/kernel/drivers/net/ethernet/atheros/atlx/[COLOR="Red"]atl2.ko[/COLOR]
version:        2.2.3
license:        GPL
description:    Atheros Fast Ethernet Network Driver
author:         Atheros Corporation <xiong.huang@atheros.com>, Chris Snook <csnook@redhat.com>
<snip>
```Now, if you'd like to provide the requested information, we can start to troubleshoot your ethernet:```
lspci -nn | grep 0200
lsb_release -d
```> I hope you can understand my wordsPerfectly well, thank you.

---

### Post by Rudra G on 2012-11-18
All right then, I did what you have ask.
*~$* *lspci -nn | grep 0200* gave this : 
02:00.0 Ethernet Controller [**0200**]:Atheros Communications Inc. L2 Fast Ethernet [1969:2048] (rev a0)
*~$ lsb_release -d* gave this :
ubuntu 12.10
What do I need to do next ?

---

### Post by chili555 on 2012-11-18
Your device is covered by the driver atl2 which is already present in 12.10:> $ modinfo atl2
filename:       /lib/modules/3.5.0-18-generic/kernel/drivers/net/ethernet/atheros/atlx/atl2.ko
version:        2.2.3
license:        GPL
description:    Atheros Fast Ethernet Network Driver
author:         Atheros Corporation <xiong.huang@atheros.com>, Chris Snook <csnook@redhat.com>
srcversion:     D49F69D2C70096F9D27B745
alias:          pci:v0000[COLOR="Red"]1969[/COLOR]d0000[COLOR="Red"]2048[/COLOR]sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.5.0-18-generic SMP mod_unload modversions 
parm:           TxMemSize:Bytes of Transmit Memory (array of int)
parm:           RxMemBlock:Number of receive memory block (array of int)
parm:           MediaType:MediaType Select (array of int)
parm:           IntModTimer:Interrupt Moderator Timer (array of int)
parm:           FlashVendor:SPI Flash Vendor (array of int)I expect the driver is already loaded; let's check:```
lsmod | grep atl2
```If it is not driving your device correctly, there is a reason. Let's check:```
nm-tool
dmesg | grep atl2
```

---

### Post by Rudra G on 2012-11-19
All right then,
*lsmod | grep atl2* gave the following
**atl2**     27628   0
*nm-tool *gave my HW address & IPv4 settings.
Carrier detect:yes
Carrier : on
Device : eth 0 [wired coonnection 1]
Driver : atl2
state : connected
default : yes
 
although the list goes on & not in the same order as it appeared on terminal screen
 
*dmesg | grep atl2 *gave the following
[12.591272]atl2 0000:02:00.0>irq 43 for MSI/MSI-X
[12.591396]atl2 : eth0 NIC Link is up <100 Mbps Full duplex>

---

### Post by chili555 on 2012-11-19
> state : connectedThat sounds pretty hopeful.> nm-tool gave my HW address & IPv4 settings.That's exactly what we wanted to see, aside from the hardware address. Any chance we can see them??

---

### Post by Rudra G on 2012-11-19
Sure, I will just give the IPv4 settings
Address: 192.168.1.2
Prefix: 24 (255.255.255.0)
Gateway: 192.168.1.1
DNS: 192.168.1.1

---

### Post by chili555 on 2012-11-19
Did you put those in yourself? I hope not. If Network Manager put them in, then you are well and truly connected. What is the result of:```
ping -c3 192.168.1.1
ping -c3 8.8.8.8
ping -c3 www.google.com
```You don't have to tell us all the details, just whether you got ping returns or not and, if not, what the error was.

---

### Post by Rudra G on 2012-11-19
OK.
*ping -c3 192.168.1.1*
3 packets recieved 3 packets sent 0% loss
 
*ping -c3 8.8.8.8*
destination net unreachable
 
*ping -c3 [www.google.com]("http://www.google.com")*
ping unkown host [www.google.com]("http://www.google.com")

---

### Post by chili555 on 2012-11-19
You are connected to the router but not beyond. Do other computers attached to the same router connect to the internet? What do their settings look like? IP address? Gateway? DNS nameservers?

---

### Post by Rudra G on 2012-11-20
Well I am using the same connection while writing this to you (using my Windows XP). Moreover this is the only computer that I have. The problem seems to persist only with Ubuntu. One more thing is that I have not run the *$ sudo pppoeconfig* on the terminal yet.

---

### Post by chili555 on 2012-11-20
> **Rudra G said:**
> Well I am using the same connection while writing this to you (using my Windows XP). Moreover this is the only computer that I have. The problem seems to persist only with Ubuntu. One more thing is that I have not run the *$ sudo pppoeconfig* on the terminal yet.Well, then no wonder you are not connected! You may have better luck by right-clicking the Network Manager icon and selecting 'Edit Connections' and the complete the DSL section. I would also suggest the username and password would be better placed in the router. Please see attached.

---

