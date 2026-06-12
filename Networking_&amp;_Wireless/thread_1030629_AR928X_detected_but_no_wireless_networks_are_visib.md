---
title: "AR928X detected but no wireless networks are visible?"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by Zerimas on 2009-01-04
The Ubuntu hardware tester claims my wireless card (Atheros AR928X) exists, as does lspci 
```
03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

```

and lshw -c Network ```
 *-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:15:af:cd:ed:33
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn

```

However I cannot see my university's wireless networks (which are not hidden)

```
dan@Syndev:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

```

I've tried the "echo" on/off fix seen _[here]("http://ubuntuforums.org/showthread.php?t=930667")_ to no avail.  What is the last step in getting my wireless card to work? My network manager is WICD, by the way.

---

### Post by Zerimas on 2009-01-04
Bump.

---

### Post by Foxbat250 on 2009-01-05
hi
I also have exactly the same problem!!!!!
if somebody can help us!!!

---

### Post by Zerimas on 2009-01-08
Bump. :(

---

### Post by kevdog on 2009-01-09
Can you post 

ifconfig
iwlist scan

---

### Post by Nopposan on 2009-01-10
I'm having what appears to be the same problem with the same card.

Here's the output of my ifconfig:
```
user-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:72:7c:57:51  
          inet addr:192.168.1.13  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:72ff:fe7c:5751/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1689 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1202 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2297913 (2.2 MB)  TX bytes:119929 (119.9 KB)
          Interrupt:253 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:23:4d:3c:e3:3a  
          inet6 addr: fe80::223:4dff:fe3c:e33a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2376 (2.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-23-4D-3C-E3-3A-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Does this help?

Also, here's iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Tx-Power=23 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

So, wlan0 looks promising, but I have no idea how to tap it's potential.

'Hope someone can help me out or point me in the right direction.

Cheers.

---

### Post by Zerimas on 2009-01-14
It appears as if Nopposan and I are having the same problem. :(  Why is my laptop not functioning as it should? :'(

ifconfig: 
```
eth0      Link encap:Ethernet  HWaddr 00:22:15:60:e2:aa  
          inet addr:129.97.241.231  Bcast:129.97.241.255  Mask:255.255.255.0
          inet6 addr: fec0::9:222:15ff:fe60:e2aa/64 Scope:Site
          inet6 addr: 2002:8161:f15e:9:222:15ff:fe60:e2aa/64 Scope:Global
          inet6 addr: 2002:8161:d1b0:9:222:15ff:fe60:e2aa/64 Scope:Global
          inet6 addr: 2002:8161:f122:a:222:15ff:fe60:e2aa/64 Scope:Global
          inet6 addr: 2002:8161:f16d:b:222:15ff:fe60:e2aa/64 Scope:Global
          inet6 addr: fec0::b:222:15ff:fe60:e2aa/64 Scope:Site
          inet6 addr: 2002:8161:f166:b:222:15ff:fe60:e2aa/64 Scope:Global
          inet6 addr: fe80::222:15ff:fe60:e2aa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4884 errors:0 dropped:56146191344 overruns:0 frame:0
          TX packets:2500 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2474057 (2.4 MB)  TX bytes:393348 (393.3 KB)
          Interrupt:247 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:cd:ed:33  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-AF-CD-ED-33-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

iwlist scan:
```
dan@Syndev:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

```

---

### Post by Gwasanaethau on 2009-01-26
Finally, I found a thread that matches the problems I'm having! I too have an AR928X wireless adapter on my laptop, and it too refuses to connect. On the odd occasion, however, it will find wireless networks (including my own), but when I ask it to connect it just sits there, doing nothing. It seems to be going through the motions - it asks for a password if there's an encryption protocol on the network, and then it appears to attempt a connection. I've figured out that it doesn't actually send a DHCP request to the router, though the software seems to think it does and waits patiently for an IP address to be returned.

I've tried without encryption, with WEP and WPA; I've tried compiling the latest [ath9k]("http://wireless.kernel.org/en/users/Download") drivers, and the latest 2.6.28 kernel from [kernel.org]("http://www.kernel.org"); I've tried 32bit and 64bit versions of Arch Linux; and various different network controllers (I even worked from the command line without X running) just to try and get this to work; all ended up at the very same impasse.

It's frustrating because it's almost there!

P.S. my outputs are pretty much identical to those already posted.

---

### Post by HuaiDan on 2009-01-26
Guys, do a search on these forums for atheros backports fix. There's a package you install that zips this right up, assuming you haven't messed up your system too much already by trying to get the damn thing to work.

I should know, I went through it all a few weeks ago, now using atheros wireless like a champ. A little buggy at first, but when you get the hang of enabling and re-enabling the wireless (by right-clicking on the network manager icon , located on the right side of the upper panel by default), then you'll be up and running.

---

### Post by HuaiDan on 2009-01-26
Ok, did the footwork here. COMPLETELY uninstall and ban the restricted drivers that Ubuntu tries to install. 
Then run this:
sudo aptitude install linux-backports-modules-intrepid-generic


After some cleaning up of prior user damage, it came right up.

---

### Post by DarKm4773r on 2009-01-26
It looks like your wireless card isn't relaying with the station that you're connected to.  I'm guessing that it's most likely the driver that you're using.  I have a Broadcom and the sucker wouldn't work until I found a user-created driver when I was using Hardy.  Try to Google "AR928X Linux driver".  I hope this helps a bit and that you get that bug worked out.:D

---

### Post by Gwasanaethau on 2009-01-26
> **HuaiDan said:**
> Ok, did the footwork here. COMPLETELY uninstall and ban the restricted drivers that Ubuntu tries to install. 
Then run this:
sudo aptitude install linux-backports-modules-intrepid-generic


After some cleaning up of prior user damage, it came right up.

Thanks for the advice. Unfortunately, I'm running Hardy, so Intrepid updates will probably conflict along the way. In any case, that package doesn't appear to exist in the Ubuntu repositories anywhere - is it a standard Ubuntu package?

> **DarKm4773r said:**
> It looks like your wireless card isn't relaying with the station that you're connected to.  I'm guessing that it's most likely the driver that you're using.  I have a Broadcom and the sucker wouldn't work until I found a user-created driver when I was using Hardy.  Try to Google "AR928X Linux driver".  I hope this helps a bit and that you get that bug worked out.:D

That's exactly it. If I knew more about drivers, I could try and hack the ath9k drivers to attempt to get it to work, but my knowledge in this area is non-existant! I'll keep searching to see if something comes up, but NDISwrapper seems to hate my Windows drivers. Unless…

---

### Post by Gwasanaethau on 2009-01-26
Okie dokie - some progress; well, at least in Arch. I tried to sort things out in Ubuntu but I ended up with a kernel panic when trying to unload and then reload the ath9k drivers. Probably not a good thing! :(

Anyway, I thought I'd post my Arch sequence here in case it helps any of the rest of you along the way. No guarantees this will work - it might even break stuff, but, as with anything you see in these fora, if it does, you get to keep both pieces!

**[color="navy"]--- Preparation ---[/color]**
First things first - Arch comes without any kind of GUI interface - thus no 'network-manager' and no 'wicd', so it might be wise to disable and even uninstall them (at least until you get a connection working). Also, currently I can _*only*_ get it to work if WPA-PSK encryption is activated - I can't even get an open connection to work, but I've listed the commands you should use anyway to see if you can figure it out. Also, as I was working as 'root' in Arch, some of the commands below might need raised privileges - if this is the case, just type ```
sudo !!
``` to repeat the last command as the superuser. You should also do this without your Ethernet connection connected - I recommend unplugging it and rebooting if you've already started up with Ethernet active - I've found that some of the commands are sent via the Ethernet if it's active instead of straight to the wireless card.

**[color="navy"]--- 1: Kernel Modules ---[/color]**
The first thing I did with regards to setting up the system was I made sure that ndiswrapper was not active (I had been messing with it) and ensured that ath9k *was* active. This you can do by:
```
lsmod | grep ndiswrapper
lsmod | grep ath9k
```
If ndiswrapper shows up, do:
```
modprobe -r ndiswrapper
```
and if ath9k doesn't show up:
```
modprobe ath9k
```

EDIT:
It seems the ath9k module support for kernels older than 2.6.27 has gone. You used to need to compile the ath9k module yourself as it's not built-in to these kernels. I'll leave the links for the download and instruction sites here in case they come back ([wireless.kernel.org]("http://wireless.kernel.org/en/users/Download")), but it looks like Hardy users might have to either switch to Intrepid or compile their own kernel ([instructions]("http://www.howtoforge.com/kernel_compilation_ubuntu_p2")). I'm currently in the middle of compiling 2.6.28.2, so I'll let you know in due course if this is the way to go.

FURTHER EDIT:
Just finished compiling 2.6.28.2 and it broke a load of stuff - so I definitely don't recommend that! Looks like it's not going to be so easy to get AR928X working with Hardy.

**[color="navy"]--- 2: Interface Activation ---[/color]**
Next, use:
```
iwconfig
```
and:
```
ifconfig
```
to determine whether your card is active and what designation it has been given. If it is present in 'iwconfig' but not in 'ifconfig', then it is recognised but disabled. To enable it use:
```
ifconfig <INTERFACE> up
```
replacing <INTERFACE> with the name of card in 'iwconfig'. Now wait a few seconds for the card to initialise, and then scan for local networks using:
```
iwlist <INTERFACE> scan
```
If it comes up with:
> no scan results
try disabling your wireless card using:
```
ifconfig <INTERFACE> down
```
and then shutting down and restarting the ath9k module
```
modprobe -r ath9k; modprobe ath9k
```

**[color="orange"]WARNING: this caused a kernel panic on my Ubuntu system - not sure why as it was fine in Arch. If anyone can give any insight into this, please let us know![/color]**

**[color="navy"]--- 3: Network Assignment ---[/color]**
Next you need to assign a network to your wireless interface. If you're using an open (unencrypted) connection or using WPA-PSK, use command #1 below - for WEP use command #2:
```
#1: iwconfig <INTERFACE> essid <ESSID>
#2: iwconfig <INTERFACE> essid <ESSID> key <HEX KEY>
```
where <ESSID> is the name of your network and <HEX KEY> is the hexadecimal key string (NB: will be visible in your terminal as you type). <ESSID> should match one of the cells (yours!) listed in the output of 'iwlist <INTERFACE> scan' done earlier. If using an unencrypted connection or WEP, go to step 5.

**[color="navy"]--- 4: WPA-PSK Encryption ---[/color]**
If you're using WPA-PSK, you'll need to set up your encryption scheme. If you don't have it already, install 'wpa_supplicant' via your usual method. You then need to create a config file for it (backing up the old one first, of course):
```
sudo mv /etc/wpa_supplicant.conf{,.bak}
echo "ctrl_interface=DIR=/var/run/wpa_supplcant GROUP=$USERNAME" | sudo tee /etc/wpa_supplcant.conf
wpa_passphrase '<ESSID>' '<PSK>' | sudo tee -a /etc/wpa_supplcant.conf
```
where <PSK> is your connection password (NB: will be visible as you type). Please note the single quotes. As the new file contains your key in plaintext, you should change the access privileges of the file so that only root can read it:
```
sudo chmod 0600 /etc/wpa_supplicant.conf
```
Now you need to activate the encryption by using:
```
wpa_supplicant -B -Dwext -i <INTERFACE> -c /etc/wpa_supplicant.conf
```
Adding '-d' or '-dd' will give you more verbose output.

**[color="navy"]--- 5: IP Address Assignment ---[/color]**
Now, no matter which type of connection you have (unencrypted, WEP or WPA-PSK), you should wait a little while before getting or assigning an IP address (I would wait at least 30 seconds) as the wireless card needs time to get itself up and running. Once it's ready, you can get an address via DHCP using either of the commands below:
```
dhcpcd <INTERFACE>
dhclient <INTERFACE>
```

Fingers crossed! I'll keep hacking away to try and give you more concise instructions; I still need to figure out a few more things myself! :P

---

### Post by HuaiDan on 2009-01-29
> **Gwasanaethau said:**
> Thanks for the advice. Unfortunately, I'm running Hardy, so Intrepid updates will probably conflict along the way. In any case, that package doesn't appear to exist in the Ubuntu repositories anywhere - is it a standard Ubuntu package?




I'm guessing that would be in unsupported updates (intrepid backports)in intrepid, IIRC older releases were mentioned in the fix. I would only have to assume there's a Hardy backports repo as well.

---

### Post by robere.it on 2009-02-18
I'm having the exact same trouble. Acer Extensa 4630z with wireless Atheros ar928x chipset. I can connect to unencrypted, wpa and wep encrypted, but not wpa-enterprise networks (like the one at my university). Some help would definitely be appreciated.

---

### Post by Ketara on 2009-02-18
It seems like several different people here are having several different problems all with the same card. Aren't Atheros cards just amazing.

Just a couple threads that might be able to help:

[http://ubuntuforums.org/showthread.php?t=1072051](http://ubuntuforums.org/showthread.php?t=1072051)

and

[http://ubuntuforums.org/showthread.php?t=1072685](http://ubuntuforums.org/showthread.php?t=1072685)

I don't know how much help those will be, but it's a possibility.

---

### Post by networkproblems on 2009-08-03
> **HuaiDan said:**
> Ok, did the footwork here. COMPLETELY uninstall and ban the restricted drivers that Ubuntu tries to install. 
Then run this:
sudo aptitude install linux-backports-modules-intrepid-generic


After some cleaning up of prior user damage, it came right up.

Thanks. This worked for me. I just replaced "intrepid" with "jaunty" for it to work with my 9.04. No more slow to connect or dropped connections.

---

