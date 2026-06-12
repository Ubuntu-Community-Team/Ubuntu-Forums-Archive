---
title: "I am about to bin this Linux stuff...."
date: 2006-07-15
forum: Networking &amp; Wireless
---

### Post by FooAtari on 2006-07-15
I'm just lost...

I now have a DWL G510C (rt61 chip) and as with last card every guide I try goes tits up somewhere and i have little clue whats going wrong and finding it hard to find useful info...

I am using [this]("http://www.ubuntuforums.org/showthread.php?p=1260529#post1260529") guide

When i get to here (under section 3):

**make all #this will install the drivers as a module**

i get this:

[B]root@Desktop:/home/allie/Desktop/RT61_Linux_STA_Drv1.0.4.0/Modules# make all
make -C /lib/modules/2.6.15-26-386/build SUBDIRS=/home/allie/Desktop/RT61_Linux_STA_Drv1.0.4.0/Modules modules
make: *** /lib/modules/2.6.15-26-386/build: No such file or directory.  Stop.
make: *** [all] Error 2[/B]

Why??

After nearly a week and two different cards I am about ready to give up.  It's hard going from a competent user in one OS to a total newbie in another.  I need to get this working as my connection from PC needs to be wireless or else I will have to give up on Linux :(

Any help GREATLY appreciated.

Thanks :D

---

### Post by southerngrey on 2006-07-15
Stick at it man.  I have all sorts of problems getting my ACX-111 wireless card to work with a new kernel and it took me three days.  In the end it was just a bug concerning a broken shortcut. took 2 seconds to fix. Did your card go ok with the default kernel and have you tried ndiswrapper?

Also I seem to recall that there is some issue to do with blacklisting the default driver for this chipset once the new one is installed.

---

### Post by jpkotta on 2006-07-15
Did you install linux-headers?

---

### Post by FooAtari on 2006-07-15
Havent tried Ndiswrapper yet southerngrey as didnt think it was required if i was able to get through the guide I linked too.

well jpkotta, i think so....  I installed what was mentioned but the kernel-heders were a different version to the kernel version I have...

I have updated to the most recent kernel from the updater but the kernel on package manager was different, should the versions be the same (i think so)

So it's probably what's cuasing the problem, but i dont know how to get around it.

---

### Post by jpkotta on 2006-07-15
```
sudo apt-get install linux-headers-$(uname -r)
```
will install the headers for the kernel that's running.

---

### Post by Evan John on 2006-07-16
I would like to echo the same sentiment - less than happy. I looked up the list of well-supported cards and chose a dud. Well, I would still like to persevere, however my error is different:

root@ubuntu:~/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module# make all
make -C /lib/modules/2.6.15-26-386/build SUBDIRS=/home/evanj/Desktop/RT61_Linux_ STA_Drv1.0.4.0/Module modules
make[1]: Entering directory `/lib/modules/2.6.15-26-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.15-26-386/build'
make: *** [all] Error 2
root@ubuntu:~/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module#

If I try to make any individual objects, I get thousands of error messages. I have installed all the packages mentioned in this and other discussion threads. On my version of Dapper only the kernel-package was provided, not kernel-sources and kernel-headers. I assume that was equivalent.

Coultn't I just cheat a bit, by getting someone else's copy of rt61.ko?

---

### Post by jpkotta on 2006-07-16
> **Evan John said:**
> I would like to echo the same sentiment - less than happy. I looked up the list of well-supported cards and chose a dud. Well, I would still like to persevere, however my error is different:

root@ubuntu:~/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module# make all
make -C /lib/modules/2.6.15-26-386/build SUBDIRS=/home/evanj/Desktop/RT61_Linux_ STA_Drv1.0.4.0/Module modules
make[1]: Entering directory `/lib/modules/2.6.15-26-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.15-26-386/build'
make: *** [all] Error 2
root@ubuntu:~/Desktop/RT61_Linux_STA_Drv1.0.4.0/Module#

If I try to make any individual objects, I get thousands of error messages. I have installed all the packages mentioned in this and other discussion threads. On my version of Dapper only the kernel-package was provided, not kernel-sources and kernel-headers. I assume that was equivalent.

Coultn't I just cheat a bit, by getting someone else's copy of rt61.ko?

Please post /lib/modules/2.6.15-26-386/build/Makefile.  It is apparently broken.

You might be able to use someone else's .ko, *if* it was compiled for the exact same kernel (mine isn't, so I can't help you there).

---

### Post by mllr on 2006-07-16
I had this same problem when i was installing a webcam driver...

A friend told me about the kernel-headers but i didnt find the correct version for my kernel...

thanks jpkotta obout the command (sudo apt-get install linux-headers-$(uname -r)) but i had the same problem of the another guy:

```

mllr@mllr:~/Desktop/sn9$ sudo make install
make -C /lib/modules/`uname -r`/build M=/home/mllr/Desktop/sn9 modules_install
make[1]: Entrando no diretório `/usr/src/linux-headers-2.6.15-26-386'
make[1]: Saindo do diretório `/usr/src/linux-headers-2.6.15-26-386'
mllr@mllr:~/Desktop/sn9$

```

My Makefile is attached here ;)

thank you

---

### Post by FooAtari on 2006-07-16
Thanks jpkotta, keep it comming! :)

Now when I run make all i get

[B]root@Desktop:/home/allie/Desktop/RT61_Linux_STA_Drv1.0.4.0# make all
make: *** No rule to make target `all'.  Stop.[/B]

Would having installed the worng version kernel headers be causing problems?

---

### Post by Evan John on 2006-07-16
The make file is in my local directory - it came out of the TAR download from Ralink. Its main purpose is to compile rt61.ko I think.

As in the instructions, you copy Makefile.6 to Makefile. Here it is (I havbe also attached the file - renaming it to "Makefile6.txt"):
# Comment/uncomment the following line to enable/disable debugging

WFLAGS = -DAGGREGATION_SUPPORT -DWMM_SUPPORT -Wall -Wstrict-prototypes -Wno-trigraphs
#WFLAGS += -DRALINK_ATE
#WFLAGS += -DSINGLE_ADHOC_LINKUP 
#CFLAGS += -DDBG
CFLAGS+= $(WFLAGS)


obj-m := rt61.o

rt61-objs := rtmp_main.o mlme.o connect.o sync.o assoc.o auth.o auth_rsp.o rtmp_data.o rtmp_init.o sanity.o rtmp_wep.o rtmp_info.o eeprom.o rtmp_tkip.o wpa.o md5.o


all: 
	make -C /lib/modules/$(shell uname -r)/build SUBDIRS=$(shell pwd) modules
clean:
	rm -f *.o *~ .*.cmd *.ko *.mod.c
	
#make command :   make -C path/to/src SUBDIRS=$PWD modules
#example :        make -C /usr/src/linux-2.6.3-4mdk SUBDIRS=$PWD modules

---

### Post by FooAtari on 2006-07-16
Eh? :D 

Well you lost me there if that was a rpely to me previous post..

But I managed to get past that bit and get to the end of the guide, but still nothing....

I might give it one more go but i am getting tired of this.

It's that or I buy 30 meters of cable and run it around the walls, but then two doors will not close because of the wire!

I am quite keen to learn linux, but it's pretty useless to me without internet access.  And trying to setup this wireless seems to be jumping into the deep end and I am totally lost.  In Windows this took me 30 seconds, in Linux? Two PCI cards, 7 days and counting...

---

### Post by FooAtari on 2006-07-16
Progress!  I followed the guide [here]("http://www.ubuntuforums.org/showpost.php?p=750071&postcount=1") to the letter...

Ubuntu now seems to recognise the card but still no connection...

When I run iwconfig I get this:

[b]lo no wireless ext

eth0 no wireless ext

ra0 RT61 Wireless ESSID:'flat'
    Mode Managed Channel:6 Access Point XXXXXXX
    Bit Rate = 48Mb/s
    RTS thr: off  Fragment thr: off
    Link Quality = 69/70 Signal level: -72 dBm Noise level:-95dBm
    Rx Invalid nwid: 0 Rx Invalid crypt: 0 Rx Invalid frag: 0
    Tx excessive retries: 0  Invalid misc: 0  Missed beacon: 0

sit0 no wireless connection[/b]

I can ping the router.

It's a clean install, all I have done is follow the instructions listed for Ubuntu 6.06 as detailed towards the end of the guide.

What else should I have done?  I get the feeling it's something to do with the default gateway or dns...  But dont know where or how to set these up.  The guide stated not to use Networking as it can cause system to hang on start up

I think I am a few simple steps from wireless heaven, help! :D

---

### Post by jpkotta on 2006-07-16
> **mllr said:**
> I had this same problem when i was installing a webcam driver...

A friend told me about the kernel-headers but i didnt find the correct version for my kernel...

thanks jpkotta obout the command (sudo apt-get install linux-headers-$(uname -r)) but i had the same problem of the another guy:

```

mllr@mllr:~/Desktop/sn9$ sudo make install
make -C /lib/modules/`uname -r`/build M=/home/mllr/Desktop/sn9 modules_install
make[1]: Entrando no diretório `/usr/src/linux-headers-2.6.15-26-386'
make[1]: Saindo do diretório `/usr/src/linux-headers-2.6.15-26-386'
mllr@mllr:~/Desktop/sn9$

```

My Makefile is attached here ;)

thank you

Your makefile is identical to mine, except for the version number (which is expected).  I'm confused, because if you got that Makefile from /lib/modules/$(uname -r)/build/Makefile, then it should work, yet it says that directory doesn't even exist.

Let me explain how everything is working.  Then maybe it will be easier to solve the problems.  All of your modules are in /lib/modules/*kernel_version*.  When you install linux-headers, it installs the header files for the kernel to /usr/src, the canonical place for kernel source.  It also creates a symlink to the header directory in /lib/modules/*kernel_version*/build, and most things expect to find the headers there.  The command "uname -r" returns the version of the kernel that is running right now, and when you put something inside $(), it runs that as a command and returns the output.  So if you're running kernel version 2.6.x, then ```
ls /lib/modules/$(uname -r)
``` is the same as ```
ls /lib/modules/2.6.x
```.  Backticks (`) are equivalent to $().

Try removing linux-headers and reinstalling them.

---

### Post by jpkotta on 2006-07-16
> **FooAtari said:**
> Thanks jpkotta, keep it comming! :)

Now when I run make all i get

[B]root@Desktop:/home/allie/Desktop/RT61_Linux_STA_Drv1.0.4.0# make all
make: *** No rule to make target `all'.  Stop.[/B]

Would having installed the worng version kernel headers be causing problems?

You're in the wrong directory.

---

### Post by jpkotta on 2006-07-16
> **Evan John said:**
> The make file is in my local directory - it came out of the TAR download from Ralink. Its main purpose is to compile rt61.ko I think.

As in the instructions, you copy Makefile.6 to Makefile. Here it is (I havbe also attached the file - renaming it to "Makefile6.txt"):
# Comment/uncomment the following line to enable/disable debugging

WFLAGS = -DAGGREGATION_SUPPORT -DWMM_SUPPORT -Wall -Wstrict-prototypes -Wno-trigraphs
#WFLAGS += -DRALINK_ATE
#WFLAGS += -DSINGLE_ADHOC_LINKUP 
#CFLAGS += -DDBG
CFLAGS+= $(WFLAGS)


obj-m := rt61.o

rt61-objs := rtmp_main.o mlme.o connect.o sync.o assoc.o auth.o auth_rsp.o rtmp_data.o rtmp_init.o sanity.o rtmp_wep.o rtmp_info.o eeprom.o rtmp_tkip.o wpa.o md5.o


all: 
	make -C /lib/modules/$(shell uname -r)/build SUBDIRS=$(shell pwd) modules
clean:
	rm -f *.o *~ .*.cmd *.ko *.mod.c
	
#make command :   make -C path/to/src SUBDIRS=$PWD modules
#example :        make -C /usr/src/linux-2.6.3-4mdk SUBDIRS=$PWD modules

I meant the Makefile in /lib/modules/$(uname -r)/build.  That's where the error is coming from.

---

### Post by jpkotta on 2006-07-16
> **FooAtari said:**
> Progress!  I followed the guide [here]("http://www.ubuntuforums.org/showpost.php?p=750071&postcount=1") to the letter...

Ubuntu now seems to recognise the card but still no connection...

When I run iwconfig I get this:

[b]lo no wireless ext

eth0 no wireless ext

ra0 RT61 Wireless ESSID:'flat'
    Mode Managed Channel:6 Access Point XXXXXXX
    Bit Rate = 48Mb/s
    RTS thr: off  Fragment thr: off
    Link Quality = 69/70 Signal level: -72 dBm Noise level:-95dBm
    Rx Invalid nwid: 0 Rx Invalid crypt: 0 Rx Invalid frag: 0
    Tx excessive retries: 0  Invalid misc: 0  Missed beacon: 0

sit0 no wireless connection[/b]

I can ping the router.

It's a clean install, all I have done is follow the instructions listed for Ubuntu 6.06 as detailed towards the end of the guide.

What else should I have done?  I get the feeling it's something to do with the default gateway or dns...  But dont know where or how to set these up.  The guide stated not to use Networking as it can cause system to hang on start up

I think I am a few simple steps from wireless heaven, help! :D

Yeah, you're close, especially if you can ping the router (which I assume means ping 192.168.0.1 works).  Default gateway can be set in /etc/network/interfaces.  ```
man interfaces
``` for documentation.  Here's mine for reference.
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
auto eth0

# The primary network interface
iface eth0 inet static
address 192.168.0.5
netmask 255.255.255.0
gateway 192.168.0.1


---

### Post by FooAtari on 2006-07-16
I entered in the above, but still nothing.  Well I replaced eth0 with ra0.

Can still ping but nothing in Firefox.  I am using WEP, and have installed nothing extra apart from the two files required to setup wireless.  Clean instal from Ubuntu DVD

---

### Post by jpkotta on 2006-07-16
Turn off WEP.  It is insecure and not worth the hassle.  If you want a more secure connection, then use WPA, but wait for that until you get the thing working with no encryption at all.  

Personally, I never use wireless encryption.  Why?  I don't mind people using my connection (it's the neighborly thing to do), as long as it doesn't interfere with my usage.  I try to secure my computers so that it doesn't matter if someone is on my network.  And my laptop has to deal with insecure networks at school, so as I'm using it, why assume that the connection is secure?

Clearly, I haven't bothered to set up WPA, so I can't help you there.  Look in the wiki for a HowTo.

---

### Post by FooAtari on 2006-07-17
Well I do...

1.  Im paying for it, they are not

2.  They could be getting up to anything...

3.  I have peak time useage caps

How ever my SSID is hidden, and I also use MAC address filtering which is better nothing, so I will turn off WEP I think, at least until I get wireless working.

Thanks :D

---

### Post by FooAtari on 2006-07-17
I have disabled WEP but still, nothing! ARGH...

Same as before I can ping the router but am unable to get anything in firefox!

---

### Post by jpkotta on 2006-07-17
By "ping the router" I assume you mean that you can do something like
```

[jpkotta@euler FLCL](0)$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=250 time=0.663 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=250 time=0.679 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=250 time=0.694 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=250 time=0.665 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=250 time=0.665 ms

--- 192.168.0.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 807ms
rtt min/avg/max/mdev = 0.663/0.673/0.694/0.020 ms, ipg/ewma 201.950/0.667 ms
```

Can you reach the internet? ```
ping google.com
```
Or if DNS doesn't work, ```
ping 72.14.207.99
```
If DNS doesn't work, then does [http://72.14.207.99](http://72.14.207.99) at least work in Firefox?

Also, post the output of ```
ifconfig
```

---

### Post by jpkotta on 2006-07-20
Did you ever get it working?  There are a few more things to try if you didn't:

This is the built in network configuration tool.  You may find it easier than ifconfig, iwconfig, etc.
```
sudo network-admin
```

These are other tools that make wireless networking more automatic.  I haven't tried WiFi Radar.  I have tried Network Manager, and I didn't like it.
[http://www.linux.com/article.pl?sid=06/07/11/1354237](http://www.linux.com/article.pl?sid=06/07/11/1354237)
[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by FooAtari on 2006-07-22
Me?

Yes thanks, I did.  Problem with resolv.conf

---

