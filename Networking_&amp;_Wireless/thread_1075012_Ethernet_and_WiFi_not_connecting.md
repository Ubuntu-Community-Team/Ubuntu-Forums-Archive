---
title: "Ethernet and WiFi not connecting"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by Nny on 2009-02-19
I'm new to Linux and Ubuntu so I apologize if I am not detailed enough.  Please let me know if any more information will help.  I had just installed Ubuntu 8.10 and was installing updates and software on and off yesterday so I don't precisely remember at what point I lost my ethernet and wifi but it happened immediately after a restart.  This is being run on an Acer Aspire One 1.6Ghz, 160Gb HDD.  

I've tried:
'sudo shutdown -r now' no change
Some helpful people on IRC #ubuntu suggested trying 'sudo /etc/init.d/networking restart' this caused no change even after a restart
I don't know if it is related or helps but I had to use this guide to originally get my WiFi working. [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne).  After installing the WiFi it worked beautifully for about 6 hours before this happened.  Once this problem started though I lost both WiFi and ethernet.

```
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz
sudo apt-get install build-essential linux-headers-$(uname -r)
tar -xzf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6*/
make
sudo make install
sudo modprobe ath_pci
```

If need be I'm prepared to reinstall and start over but I'd like to avoid that if possible.  here are the most recent ifconfig results.

```
ath0      Link encap:Ethernet  HWaddr 00:24:2b:27:84:2b  
          inet6 addr: fe80::224:2bff:fe27:842b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:23:8b:5c:8c:e1  
          inet6 addr: fe80::223:8bff:fe5c:8ce1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:2231369595 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6472 (6.4 KB)  TX bytes:6472 (6.4 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-24-2B-27-84-2B-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:209 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:0 (0.0 B)  TX bytes:9614 (9.6 KB)
          Interrupt:18 

```

---

### Post by Nny on 2009-02-20
I don't mean to bump my own thread, but just to update I did a full erase and install.  Ran the instructions for wifi here [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) and then ran software updates.  Same issue occurs.  Am I looking at yet another install or does anyone have any suggestions or ideas?  

Here are the copied instructions from the above link.

```
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz
sudo apt-get install build-essential linux-headers-$(uname -r)
tar -xzf madwifi-hal-0.10.5.6-current.tar.gz
cd madwifi-hal-0.10.5.6*/
make
sudo make install
sudo modprobe ath_pci
```

One last thing.  After doing this last install every time I open the computer it asks me which option I want to boot from.  They are all variations of 'Ubuntu 8.10, kernel 2.6.27-11-generic' some are (recovery mode).  Is there a way to have this boot to the same one every time without asking me or will I always have to choose?

---

