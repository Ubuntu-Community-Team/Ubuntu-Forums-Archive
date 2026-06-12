---
title: "Can't keep internet connected on Compaq Evo N800c"
date: 2010-08-17
forum: Networking &amp; Wireless
---

### Post by redneckred on 2010-08-17
I am a newbie to Ubuntu and Linux, so please excuse my ignorance.  I loaded Ubuntu 10.04 on my Compaq Evo N800c as a single operating system.  I cannot get my wireless connection to work which is the Compaq w200.  I tried connecting the internet through a wired connection and the computer shows it tries to connect and does for all of 3-5 seconds.  I then get a internet disconnected message at the top of the screen.  As I said, I am a newbie to Ubuntu/Linux, so please, be gentle.  Any and all help is GREATLY appreciated.

---

### Post by Iowan on 2010-08-17
[Here]("http://ubuntuforums.org/showthread.php?t=1156441") is a problem/fix I had with Jaunty - though it hasn't helped any recent problems ( the symptoms sound similar).

---

### Post by redneckred on 2010-08-18
If anyone can help me get the ethernet working, I could download the files and get the wirless working.  I have tried deleting the autoether1 and rebooting as well as creating my own and trying that, but that's not working.  Any help would be greatly appreciated.
:confused:

---

### Post by Iowan on 2010-08-18
If you know your router's address, you might be able to configure a manual (static) address to connect to it.

---

### Post by redneckred on 2010-08-19
I do know it, but as I said earlier, am ignorant in Linux/Ubuntu.  I would appreciate you pointing me in the right direction of creating this link.

---

### Post by redneckred on 2010-08-19
I have managed to change some settings using the network manager provided by UBUNTU and have managed to establish a connection with the router, I think.  I now show a connected message, however, I have no connection with the internet.  Any help with this would be appreciated.

---

### Post by varunendra on 2010-08-19
To connect to router, you need a valid IP address & subnet. I guess you've already managed it since you are connected.

To connect to Internet, you need to define a gateway and DNS servers.

[LIST]
[*]Gateway is most often your router's IP.
[/LIST]

[LIST]
[*]DNS server(s) can be sometimes same as gateway, or it is often provided by your ISP (you can verify it in your router's config.). Alternatively, you can search and choose any of the open DNS servers like [these]("http://www.dnsserverlist.org/").
[/LIST]
You have to fill in all this info via Network Manager for the selected interface, under IPv4 tab. It is recommended (but not necessary) to define two DNS servers separated by a comma (,).

Here's mine as an example:
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/Ubuntu-2010-08-14-02-40-43.png[/IMG]

---

### Post by redneckred on 2010-08-19
Not sure what is going on... I was frustrated so I wiped the hard drive, installed windows, installed Ubuntu beside windows, now when I run Ubuntu, works fine without doing anything (autoeth connection that is.)  I will try installing just Ubuntu and try it again to see.

---

### Post by redneckred on 2010-08-20
Ok, etho problem resolved, just having problems with the W200.  Tried following the install guide/instructions in the forums and ended up at the last 2 entries of modprobing and got mod not found error.  I tried repeatedly over and over the steps from the start with the same results.  Anyone got any ideas?

---

### Post by varunendra on 2010-08-21
Please post the link to the guide you followed and also the outputs of the following commands:

(open Applications>Accessories>Terminal and enter these commands)
```
ifconfig -a
```
```
iwconfig
```
```
sudo dhclient
```
```
route -n
```

To post the outputs, just copy the output text in the terminal, paste in your new post here, highlight (only) the pasted text and click on the "#" icon on the editing panel of the message box.

Make sure that your wireless adapter is switched on (if there is a manual switch for it) before doing any of the above.

One more thing- is your wireless connection secured (i.e., do you need a password to connect to it)?

---

### Post by redneckred on 2010-08-22
Ok, here's the guide I attempted to use (copy/paste) [https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200](https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200)

I did notice that there were errors while compiling and installing the driver 

make[2]: *** [/home/steve/usb/orinoco_usb.o] Error 1
make[1]: *** [_module_/home/steve/usb] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make: *** [modules] Error 2```

```

Here is the results you asked for...

ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:08:02:67:90:64  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:2ff:fe67:9064/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27415 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37927901 (37.9 MB)  TX bytes:1738703 (1.7 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)```

```

ifconfig

lo        no wireless extensions.

eth0      no wireless extensions.```

```

sudo dhclient


Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:08:02:67:90:64
Sending on   LPF/eth0/00:08:02:67:90:64
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER of 192.168.1.7 from 192.168.1.1
DHCPREQUEST of 192.168.1.7 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.7 from 192.168.1.1
bound to 192.168.1.7 -- renewal in 43133 seconds.```

```

route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0```

```

i don't know if it matters but the old header of 2.6.32-21-generic is beside the new one of 2.6.32-24-generic

Any help you can give me would help out because I am trying to fix this for the kids to use. I am new to linux, but it seems that the driver is failing to create.

---

### Post by varunendra on 2010-08-23
Due to some excessive workload, I'm unable to focus on all the aspects, so let's just try some quick possibilities for now.


[LIST=1]
[*]The second command I gave was **i[COLOR=Red]w[/COLOR]config**, not ifconfig (although it seems that you entered the right command in the terminal, it's only a typo in your post).
[*]Please post the output of ```
sudo lshw -C network
```
[*]Does the command ```
dmesg | grep wlan0
``` return something? If yes, please post the result.
[*]What is the output of ```
uname -r
```?
[/LIST]

I just glanced the guide you gave link of and suspect a possible mistake. In the second command on that page:
```
sudo apt-get install build-essential subversion linux-headers-[COLOR=Red]**`uname -r`**[/COLOR] gcc-3.4-base cpp-3.4 curl
``` **'uname -r'** is actually to be replaced by what is output of **uname -r** in the terminal. For example, mine is **2.6.31-14-generic**, so for me the command would be:
> sudo apt-get install build-essential subversion linux-headers-**2.6.31-14-generic** gcc-3.4-base cpp-3.4 curl

So, have you substituted 'uname -r' the same way?

Also, please try everything once more as per the guide, observe the outputs closely and mention here which exactly are the commands (in that guide) that return errors when you try them. If possible, please post the error messages also (you did it in the previous post, but knowing after which command those errors are produced would be more helpful).

---

### Post by redneckred on 2010-08-23
I did enter the name of uname -r and started gettting errors here :


steve@steve-laptop:~/usb$ make
make -C /usr/src/linux-headers-2.6.32-24-generic M=/home/steve/usb KERNELRELEASE=2.6.32-24-generic modules
sudomake[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /home/steve/usb/orinoco_usb.o
In file included from /home/steve/usb/orinoco_usb.c:70:
/home/steve/usb/orinoco.h: In function ‘orinoco_spin_unlock’:
/home/steve/usb/orinoco.h:188: warning: ‘__spin_unlock_irq’ is static but used in inline function ‘orinoco_spin_unlock’ which is not static
/home/steve/usb/orinoco_usb.c: In function ‘ezusb_request_out_callback’:
/home/steve/usb/orinoco_usb.c:568: error: implicit declaration of function ‘warn’
/home/steve/usb/orinoco_usb.c: In function ‘ezusb_probe’:
/home/steve/usb/orinoco_usb.c:1460: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/steve/usb/orinoco_usb.c:1535: warning: assignment discards qualifiers from pointer target type
make[2]: *** [/home/steve/usb/orinoco_usb.o] Error 1
make[1]: *** [_module_/home/steve/usb] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make: *** [modules] Error 2
steve@steve-laptop:~/usb$ sudo make install
make -C /usr/src/linux-headers-2.6.32-24-generic M=/home/steve/usb KERNELRELEASE=2.6.32-24-generic modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /home/steve/usb/orinoco_usb.o
In file included from /home/steve/usb/orinoco_usb.c:70:
/home/steve/usb/orinoco.h: In function ‘orinoco_spin_unlock’:
/home/steve/usb/orinoco.h:188: warning: ‘__spin_unlock_irq’ is static but used in inline function ‘orinoco_spin_unlock’ which is not static
/home/steve/usb/orinoco_usb.c: In function ‘ezusb_request_out_callback’:
/home/steve/usb/orinoco_usb.c:568: error: implicit declaration of function ‘warn’
/home/steve/usb/orinoco_usb.c: In function ‘ezusb_probe’:
/home/steve/usb/orinoco_usb.c:1460: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/steve/usb/orinoco_usb.c:1535: warning: assignment discards qualifiers from pointer target type
make[2]: *** [/home/steve/usb/orinoco_usb.o] Error 1
make[1]: *** [_module_/home/steve/usb] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make: *** [modules] Error 2
steve@steve-laptop:~/usb$ cd firmware
steve@steve-laptop:~/usb/firmware$ ./get
bash: ./get: No such file or directory
steve@steve-laptop:~/usb/firmware$ 
steve@steve-laptop:~/usb/firmware$ ./get_ezusb_fw
436+0 records in
436+0 records out
6976 bytes (7.0 kB) copied, 0.0501268 s, 139 kB/s

steve@steve-laptop:~/usb/firmware$ sudo modprobe -v orinoco_usb
FATAL: Module orinoco_usb not found.

The process craters from there and will not load the usb.

as for the other info you requested....

steve@steve-laptop:~$ uname -r
2.6.32-24-generic
steve@steve-laptop:~$ sudo lshw -C network
[sudo] password for steve: 
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:08:02:67:90:64
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.7 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:10 memory:40080000-40080fff ioport:2400(size=64)
steve@steve-laptop:~$ dmesg | grep wlan0
steve@steve-laptop:~$ 


is it possible that the guide will not work for the newer version of Ubuntu 10.04?  research also revealed a newer version of the driver (I think) here : [http://www.nongnu.org/orinoco/downloads/](http://www.nongnu.org/orinoco/downloads/)

Any help you can provide is greatly appreciated.:confused:

---

### Post by varunendra on 2010-08-24
> **redneckred said:**
> is it possible that the guide will not work for the newer version of Ubuntu 10.04?

With the outputs you provided, it looks like the case.

The new link you found was also last updated in 2006 (as evident by its documentation), so I'm afraid you have to try it by yourself since it is hardware specific and I can't try it myself on VMware. However, it contains a process-guide you may find helpful.

Sorry for no-optimistic comments but let me tell you this- you've already gone more advanced than me in sense that I've never tried to compile a driver into kernel module myself. I've tried independent sources but this one seems to have extra dependencies.

So just make sure to go through its documentation thoroughly, download its dependencies in advance if needed any, and it should go alright this time. Except for wrong version or unsatisfied dependencies, I can guess no other errors in your previous attempts.

---

### Post by redneckred on 2010-08-26
I don't know if anyone is still looking into this or not, but I did find this [http://www.oyamaphotography.com/linux/w200.htm](http://www.oyamaphotography.com/linux/w200.htm) , but it is talking about gentoo which is slightly different from Ubuntu from what I can see.  Is there a way to use this with Ubuntu commands?  Sorry about my ignorance, but as I said, I no nothing about linux and am trying to learn as much as I can, and working 2 jobs from 4 am to 10 pm doesn't leave much time.  Thanks for any help.

---

### Post by redneckred on 2010-08-27
I also found this, which looks to to be a newer update, but I really have no clue as to what it is I am looking at.  Anybody?

---

### Post by Iowan on 2010-08-27
> **redneckred said:**
> I also found this, which looks to to be a newer update, but I really have no clue as to what it is I am looking at.  Anybody? Missing the link - or are you referring to the _oyamaphotography_ (Gentoo) one? :)

---

### Post by redneckred on 2010-08-27
Sorry...I found these, but don't know if they are the update drivers for the 10.04 version of Ubuntu (or would work).  I don't even really know if what I am looking at is a compiled driver for the card, just guessing really.

[http://osdir.com/ml/linux-wireless/2009-07/msg00460.html](http://osdir.com/ml/linux-wireless/2009-07/msg00460.html)

[http://repo.or.cz/w/orinoco_usb.git](http://repo.or.cz/w/orinoco_usb.git)

On the second link, I was noticing the one's with the 2.6.32-usb's, or the first 2 in the short logs.

---

