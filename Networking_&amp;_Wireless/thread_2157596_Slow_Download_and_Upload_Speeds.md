---
title: "Slow Download and Upload Speeds"
date: 2013-06-26
forum: Networking &amp; Wireless
---

### Post by phosphide on 2013-06-26
[IMG]http://www.speedtest.net/result/2797504313.png[/IMG]

Recently, I was having some terrible download and upload speeds. AT&T came out and gave me a new router and every device in my house from phones, tablets, and my Windows based PC's are now getting close to the 12 Mbps Download Speed and 1.5 Mbps Upload Speed via our Uverse. Undoubtedly, I have tried everything up until this point to figure out why I am getting such slow speeds on my Ubuntu machine.

Here is some helpful information.

```
name@box:~$ sudo lshw -C Network
[sudo] password for name: 
    *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 09
       serial: 60:a4:4c:56:c2:b3
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168f-1_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:77 ioport:d000(size=256) memory:fa104000-fa104fff memory:fa100000-fa103fff
  *-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 60:a4:4c:44:45:44
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.5.0-34-generic firmware=N/A ip=192.168.1.72 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:48 ioport:c000(size=256) memory:fe100000-fe103fff

```

```
name@box:~$ lspci | grep -i netw
04:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)

```

```
name@box:~$ sudo ifconfig -s
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0       1500 0         0      0      0 0             0      0      0      0 BMU
lo        16436 0      1020      0      0 0          1020      0      0      0 LRU
wlan0      1500 0     17877      0      0 0         13392      0      0      0 BMRU

```

```
name@box:~$ ping -c 4 www.google.com
PING www.google.com (74.125.225.243) 56(84) bytes of data.
64 bytes from dfw06s26-in-f19.1e100.net (74.125.225.243): icmp_req=1 ttl=55 time=32.9 ms
64 bytes from dfw06s26-in-f19.1e100.net (74.125.225.243): icmp_req=2 ttl=55 time=25.5 ms
64 bytes from dfw06s26-in-f19.1e100.net (74.125.225.243): icmp_req=3 ttl=55 time=28.9 ms
64 bytes from dfw06s26-in-f19.1e100.net (74.125.225.243): icmp_req=4 ttl=55 time=26.7 ms

--- www.google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms
rtt min/avg/max/mdev = 25.522/28.529/32.943/2.821 ms

```

I was hoping someone could shed some light on this issue. Downloading things, especially through the software center, takes a very long time. Apt-get seems to work alright, but still should be substantially faster than what I am getting. Lastly, here are the system specs:
```
name@box:~$ uname -a
Linux box 3.5.0-34-generic #55~precise1-Ubuntu SMP Fri Jun 7 16:25:50 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

AMD FX-4170 Quad Core (4.2 ghz)
8 gb Patriot Memory (2 x 4)
Asus M5A97 LE R2.0 Motherboard
GeForce GT 620 (Dual DVI, Mini hdmi)
1 TB Seagate Hard Drive (7200)
Asus Wireless-N 300 Mbps PCI
```

Any help would be appreciated, thanks.

---

### Post by sanderj on 2013-06-26
You use wifi? If so, what if you use fixed ethernet?

---

### Post by varunendra on 2013-06-26
Please answer what sanderj asked above. If it is wireless, please follow the "Wireless Script" link in my signature and post back the result as mentioned in the linked post.

---

### Post by phosphide on 2013-06-26
Undoutedly I do not have the ability to connect via ethernet. Here is the output from the script you provided.

[http://pastebin.ubuntu.com/5801472/](http://pastebin.ubuntu.com/5801472/)

---

### Post by varunendra on 2013-06-26
First and foremost, please change the encryption in the router to pure WPA2-PSK only, choosing AES instead of TKIP. Currently it is WPA/WPA2 mixed mode.

If that does not help, try -
```
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce swenc=1
```
This will be a temporary change and will be lost on reboot. If it seems to help, we can make it permanent.

If none of these help, we may have to compile the proprietary driver like mentioned here : [http://ubuntuforums.org/showthread.php?t=2156007&p=12700188#post12700188](http://ubuntuforums.org/showthread.php?t=2156007&p=12700188#post12700188)

But the encryption in the router should NOT be WPA/WPA2 mixed mode in any case. Do change it first as suggested above and leave it that way.

---

### Post by phosphide on 2013-06-26
Made the change to WPA2-PSK via AES. That was undoubtedly just the default, so I never messed with it. Retested my speed, no change.

Though, the changes made via the command line appear to have worked. I appreciate the helpful and timely response.

I'm assuming to make it permanent I could write a shell script and set it to default at boot? Or do you have another suggestion? Thanks!

---

### Post by varunendra on 2013-06-26
> **phosphide said:**
> Though, the changes made via the command line appear to have worked.

Actually there is a recommended easier way to make it permanent. In a terminal, just do -
```
echo "options rtl8192ce swenc=1" | sudo tee /etc/modprobe.d/rtl8192ce.conf
```

This will create a configuration file "rtl8192ce.conf" in the /etc/modprobe.d directory with the given setting for the driver. The name doesn't matter as long as its extension name is .conf.

Keep it on test bed for some time (or a couple of days if you wish) and let us know if the improvement is real or just coincidental. :)

If it seems to be a definite solution, please consider marking the thread as [SOLVED].

---

### Post by phosphide on 2013-06-28
Thanks for the help varunendra. Undoubtedly, I spoke too soon. I was getting the speeds that I needed but now, undoubtedly, am back down to where it was. I made the change via the command above as well.

---

### Post by varunendra on 2013-07-01
> **phosphide said:**
> Undoubtedly, I spoke too soon. I was getting the speeds that I needed but now, undoubtedly, am back down to where it was.

Did you try installing the proprietary driver then? Like mentioned here : [http://ubuntuforums.org/showthread.php?t=2156007&p=12700188#post12700188](http://ubuntuforums.org/showthread.php?t=2156007&p=12700188#post12700188)

---

### Post by phosphide on 2013-07-16
I downloaded the most recent driver from here: [http://www.service.asus.com/#!downloads/c1wax](http://www.service.asus.com/#!downloads/c1wax)

I extracted to the desktop and tried to run make. Got an error.

```
uname@comp:~/Desktop/Linux$ make
make -C /lib/modules/3.5.0-36-generic/build M=/home/uname/Desktop/Linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-36-generic'
  CC [M]  /home/uname/Desktop/Linux/base.o
/home/uname/Desktop/Linux/base.c: In function ‘_rtl_init_mac80211’:
/home/uname/Desktop/Linux/base.c:319:6: error: ‘IEEE80211_HW_BEACON_FILTER’ undeclared (first use in this function)
/home/uname/Desktop/Linux/base.c:319:6: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/home/uname/Desktop/Linux/base.o] Error 1
make[1]: *** [_module_/home/uname/Desktop/Linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-36-generic'
make: *** [all] Error 2
```

---

### Post by varunendra on 2013-07-16
> **phosphide said:**
> ```

/home/uname/Desktop/Linux/base.c:319:6: error:**[COLOR="#FF0000"] ‘IEEE80211_HW_BEACON_FILTER’ undeclared (first use in this function)[/COLOR]**
/home/uname/Desktop/Linux/base.c:319:6: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/home/uname/Desktop/Linux/base.o] Error 1
make[1]: *** [_module_/home/uname/Desktop/Linux] Error 2
```

You need to patch the driver. For reference : [http://ubuntuforums.org/showthread.php?t=2139074&p=12632851#post12632851](http://ubuntuforums.org/showthread.php?t=2139074&p=12632851#post12632851)

---

### Post by phosphide on 2013-07-16
Commented out the change and was able to run make no problem. Did sudo make install no problems as well. But now when it begins connecting to a wireless network, the entire OS freezes and forces a hard reset.

---

### Post by varunendra on 2013-07-16
That's another (probably very common) side effect, to which I have found no solutions yet.. :(

Maybe just try 12.04 (kernel 3.2x) instead, where the same driver compiles without patches, and works without problems.

---

### Post by phosphide on 2013-07-16
That's what I am currently running. Even did a fresh install.

---

### Post by varunendra on 2013-07-16
Then the only working solution I can suggest is to downgrade to kernel 3.2 series. I'm myself running on 3.2.0-36, 64 bit (didn't update because my connection is too slow and I'm too lazy). Of course this won't be called a good suggestion, but the that kernel version (the entire 3.2 series) is the only officially available option that has been tested ok in my experience.

A possibly better suggestion may be blacklisting or removing the proprietary driver and trying the latest compat drivers (newer versions of the native driver, hoping they'd perform well). But I haven't tested them. Let me know if you wish to try that (may take some experimenting to compile it, and the solution is experimental itself).

To see which versions of kernel are available and to install one, either use synaptic package manager (much easier), or in terminal -
```
apt-cache show linux-image-generic | grep -i version
```
..then to install a desired version -
```
sudo apt-get install linux-image-generic=<desired version obtained above>
```
I haven't tested above for installation of an older version of linux kernel, but works for normal application packages and I hope it should work the same way for kernel. Else we can just slightly change the package names based on what versions are available.

There are easier ways to install a particular kernel version, like downloading one from the ppa mainline, but I prefer to choose one that is present in the official repositories.

---

### Post by varunendra on 2013-07-17
> **ananthapriya said:**
> Thanks but Is there anyone else that has any ideas besides wiring it directly to the router? I don't want to have to be connected by a cable.

Hi ananthapriya, and welcome to the forums !

Wireless problems are very subjective. So even if they appear to be same, the reasons and solutions may often be very different. As such, I'd suggest you start a new thread of your own, with a suitable title and a detailed description of your problem.

It may be more helpful if you follow the "Wireless Script" link in my signature, follow the instructions there and post back the report generated by the script.

---

