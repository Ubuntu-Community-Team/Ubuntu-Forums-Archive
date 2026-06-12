---
title: "Wireless Card Drivers Compiling Help"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by JumpForJoy on 2010-01-24
Hi, I recently bought a new Sabrent Wireless-N PCI card.  It came with linux drivers on a mini-cd, but I'm having a lot of trouble getting them to work.  I think they want you to build your own driver, and the readme says:
> =======================================================================
Build Instructions:  
====================

1> $tar -xvzf DPB_RT2860_Linux_STA_x.x.x.x.tgz
    go to "./DPB_RT2860_Linux_STA_x.x.x.x" directory.
    
2> In Makefile
	 set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
	 define the linux kernel source include file path LINUX_SRC
	 modify to meet your need.

3> In os/linux/config.mk 
	define the GCC and LD of the target machine
	define the compiler flags CFLAGS
	modify to meet your need.
	** Build for being controlled by NetworkManager or wpa_supplicant wext functions
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
	   => #>cd wpa_supplicant-x.x
	   => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
	** Build for being controlled by WpaSupplicant with Ralink Driver
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
	   => #>cd wpa_supplicant-0.5.7
	   => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

4> $make			
	# compile driver source code
	# To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
	  => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c

5> $cp RT2860STA.dat  /etc/Wireless/RT2860STA/RT2860STA.dat       
    
6> load driver
    #[kernel 2.4]
    #    $/sbin/insmod rt2860sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt2860sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

7> unload driver    
    $/sbin/ifconfig ra0 down
	$/sbin/rmmod rt2860sta
I follow the instructions through, but I get errors when I make:
> zachary@zachary-desktop:~/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0$ make
make -C tools
make[1]: Entering directory `/home/zachary/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/zachary/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0/tools'
/home/zachary/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/zachary/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/Makefile
make  -C  /lib/modules/2.6.31-17-generic/build SUBDIRS=/home/zachary/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
  CC [M]  /home/zachary/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../common/rtmp_init.o
  CC [M]  /home/zachary/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../os/linux/rt_profile.o
/home/zachary/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../os/linux/rt_profile.c: In function ‘RTMPReadParametersHook’:
/home/zachary/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../os/linux/rt_profile.c:928: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/zachary/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../os/linux/rt_profile.c:929: error: ‘struct task_struct’ has no member named ‘fsgid’
/home/zachary/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../os/linux/rt_profile.c:930: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/zachary/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../os/linux/rt_profile.c:930: error: ‘struct task_struct’ has no member named ‘fsgid’
/home/zachary/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../os/linux/rt_profile.c:1554: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/zachary/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../os/linux/rt_profile.c:1555: error: ‘struct task_struct’ has no member named ‘fsgid’
make[2]: *** [/home/zachary/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux/../../os/linux/rt_profile.o] Error 1
make[1]: *** [_module_/home/zachary/Desktop/Linux/2008_0918_RT2860_Linux_STA_v1.8.0.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
make: *** [LINUX] Error 2

Is there a better/easier way to get the drivers for my card?  Or should I just try to figure out how to compile these?

Thanks for any help,
Jump For Joy

Also, I posted this under hardware before I saw the networking section, sorry.

---

### Post by darkod on 2010-01-24
Don't worry, compiling is peace of cake. Just make sure you follow the rest of the instructions carefully, like turning WPA Supplicant to =y (for Yes).

I guess that error is because you need to use sudo, even though they left it out in the instructions. For a task like driver compiling, you need to have root permissions.

But first, did you install the build-essential package? That is needed on ubuntu to compile drivers. If you didn't, just do in terminal:

sudo apt-get install build-essential

That will install all dependent packages too.

Then just instead of make, use:
sudo make

when needed.

---

### Post by chili555 on 2010-01-24
> [COLOR="Red"]2008_0918[/COLOR]_RT2860_Linux_STA_v1.8.0.0I believe this means the driver was built in September of 2008. I have doubts about whether it will successfully build in our current kernel version.

Before we go to the effort of trying to build our own, let's see what we might have on hand. Please do:```
sudo updatedb
```This will take a few moments, please be patient.```
locate rt2860sta.ko
```Do you have this?> /lib/modules/2.6.31-17-generic/kernel/drivers/staging/rt2860/rt2860sta.koIf so, can you get your card going with:```
sudo modprobe rt2860sta
```Post back and let us know.

---

### Post by JumpForJoy on 2010-01-24
Thanks for your help.

> **darkod said:**
> Just make sure you follow the rest of the instructions carefully, like turning WPA Supplicant to =y (for Yes)...
Yep, I made sure to do all of that.

> **darkod said:**
> I guess that error is because you need to use sudo...
I tried "sudo make", but got the same errors.

> **darkod said:**
> But first, did you install the build-essential package...
Yep, I did.


> **chili555 said:**
> I believe this means the driver was built in September of 2008. I have doubts about whether it will successfully build in our current kernel version.
That's correct, I was able to goto Ralink's website and find a 2009 source, but I'm still trying to use the 2008 source that came with the card.


> **chili555 said:**
> Before we go to the effort of trying to build our own, let's see what we might have on hand. Please do:```
sudo updatedb
```This will take a few moments, please be patient.```
locate rt2860sta.ko
```Do you have this?If so, can you get your card going with:```
sudo modprobe rt2860sta
```
I did infact see "/lib/modules/2.6.31-17-generic/kernel/drivers/staging/rt2860/rt2860sta.ko ", but even after I used "sudo modprobe rt2860sta" I still couldn't connect to the Internet.  I can now see a wireless section under my wireless connections area on the top right.  I can also see my network name :D, but when I try to connect to it, it says connection successfully but I can't load any web pages.  I'm also using WPA to secure my network if that matters.

I don't know if this will help, but I figured I should post it.
ifconfig:
> ra0       Link encap:Ethernet  HWaddr 00:0d:09:62:09:bc  
          inet addr:192.168.1.108  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:9ff:fe62:9bc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7658 errors:0 dropped:0 overruns:0 frame:0
          TX packets:634 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2045459 (2.0 MB)  TX bytes:3428 (3.4 KB)
          Interrupt:19 


iwconfig:
> ra0       RT2860 Wireless  ESSID:"linksysn"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:25:9C:68:5E:F1   
          Bit Rate=135 Mb/s   
          RTS thr: off   Fragment thr: off
          Link Quality=100/100  Signal level:-42 dBm  Noise level:-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Thanks for all your help,
Jump For Joy

---

### Post by chili555 on 2010-01-24
We're almost there! Please let us see:```
ping -c3 74.125.47.100
cat /etc/resolv.conf
```Thanks.> That's correct, I was able to goto Ralink's website and find a 2009 source, but I'm still trying to use the 2008 source that came with the card.In the world of Linux, newer is always better than older, unless, of course, you are running an older kernel for testing, development or embedded purposes.

---

### Post by JumpForJoy on 2010-01-24
```
ping -c3 74.125.47.100
```
> zachary@zachary-desktop:~$ ping -c3 74.125.47.100
PING 74.125.47.100 (74.125.47.100) 56(84) bytes of data.
64 bytes from 74.125.47.100: icmp_seq=1 ttl=54 time=33.3 ms
64 bytes from 74.125.47.100: icmp_seq=2 ttl=54 time=30.6 ms
64 bytes from 74.125.47.100: icmp_seq=3 ttl=54 time=30.8 ms

--- 74.125.47.100 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 30.671/31.618/33.308/1.206 ms

That's odd, so I can ping websites but not view them?

```
cat /etc/resolv.conf
```
> zachary@zachary-desktop:~$ cat /etc/resolv.conf
# Generated by NetworkManager
domain hr.cox.net
search hr.cox.net hr.cox.net
nameserver 192.168.1.1
nameserver 68.105.28.11
nameserver 68.105.29.11
# NOTE: the libc resolver may not support more than 3 nameservers.
# The nameservers listed below may not be recognized.
nameserver 192.168.1.1
nameserver 68.105.28.11
nameserver 68.105.29.11
This didn't allow me to view webpages, but I'm not really sure what this did :p

> Thanks.In the world of Linux, newer is always better than older, unless, of course, you are running an older kernel for testing, development or embedded purposes.
Ok, I'll remember that.  I just figured I should use the drivers that came with the card, just in case.

Thanks a bunch,
Jump For Joy

---

### Post by chili555 on 2010-01-24
Just for the moment, let's amend resolv to see if we can kick it to life.```
sudo gedit /etc/resolv.conf
```Add some bits to comment out some sections. Make it look like:```
# Generated by NetworkManager
domain hr.cox.net
search hr.cox.net hr.cox.net
#nameserver 192.168.1.1
nameserver 68.105.28.11
nameserver 68.105.29.11
# NOTE: the libc resolver may not support more than 3 nameservers.
# The nameservers listed below may not be recognized.
#nameserver 192.168.1.1
#nameserver 68.105.28.11
#nameserver 68.105.29.11 
```Proofread carefully, save and close gedit. Now do:```
ping -c3 www.google.com
```Are we golden?

---

### Post by JumpForJoy on 2010-01-24
Errm, I made a mistake there.  Two posts back:

I ran ```
ping -c3 74.125.47.100
``` while I was still connected with Ethernet.  When I run "ping -c3 74.125.47.100" using my wireless card, I get:> zachary@zachary-desktop:~$ ping -c3 74.125.47.100
PING 74.125.47.100 (74.125.47.100) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

--- 74.125.47.100 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2016ms

Which is a lot less fun looking.  Sorry for the trouble.

Sorry,
Jump For Joy

---

### Post by chili555 on 2010-01-24
> ping: sendmsg: Operation not permittedThis points to a firewall problem. Please see: [http://ubuntuforums.org/showthread.php?t=345251](http://ubuntuforums.org/showthread.php?t=345251) as well as [http://ubuntuforums.org/showthread.php?t=812644](http://ubuntuforums.org/showthread.php?t=812644)

---

### Post by JumpForJoy on 2010-01-24
Yep, your very right.  I used firestarted, and changed my internet interface to my new card, and everything works perfectly.

Thank you very much, and sorry for the trouble,
Jump For Joy

Edit: Thanks for those links, they were very helpful.

---

### Post by chili555 on 2010-01-24
Glad it's working! It was a lot easier than compiling.

---

### Post by JumpForJoy on 2010-01-24
Yep, that's for sure. :D

Thanks!
Jump For Joy

---

### Post by paxinos on 2010-02-08
I am getting the same error message when building using the latest source (Sept 2009) 009_0903_RT3090_Linux_STA_v2.2.0.1   and unfortunately the 2860 driver doesn't work with my wireless adapter.

Any guidance is greatly appreciated.



> **chili555 said:**
> I believe this means the driver was built in September of 2008. I have doubts about whether it will successfully build in our current kernel version.

Before we go to the effort of trying to build our own, let's see what we might have on hand. Please do:```
sudo updatedb
```This will take a few moments, please be patient.```
locate rt2860sta.ko
```Do you have this?If so, can you get your card going with:```
sudo modprobe rt2860sta
```Post back and let us know.

---

