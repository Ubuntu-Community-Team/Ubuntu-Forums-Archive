---
title: "WLAN Problem after installing pulseaudio and pavumeter"
date: 2011-07-30
forum: Networking &amp; Wireless
---

### Post by Shadowrain on 2011-07-30
[FONT=Calibri]Hello,[/FONT]
  [FONT=Calibri]yesterday I installed pulseaudio and pavumeter. This morning I couldn't connect to the internet anymore. I checked the settings but couldn't see any changes.[/FONT]
  [FONT=Calibri]I read the post at [[COLOR=blue]http://ubuntuforums.org/showthread.php?t=370108[/COLOR]]("http://ubuntuforums.org/showthread.php?t=370108") and I'm going to post the outcome of the instructions here:[/FONT]
  
  [FONT=Calibri]1.) My Notebook is a Sony Vaio[/FONT]
  
  [FONT=Calibri]2.) Wireless brand, model and chipset:[/FONT]
  [FONT=Calibri]```
ubuntu@ubuntu:~$ lspci -nn | grep Atheros
```[/FONT]```

  [FONT=Calibri]02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01) [/FONT]
```
  
  [FONT=Calibri]3.) Check interface:[/FONT]
  [FONT=Calibri]```
ubuntu@ubuntu:~$ ifconfig
```[/FONT]```

  [FONT=Calibri]eth0      Link encap:Ethernet  HWaddr f0:bf:97:13:10:ed [/FONT]
  [FONT=Calibri]          UP BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT]
  [FONT=Calibri]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT]
  [FONT=Calibri]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
  [FONT=Calibri]          collisions:0 txqueuelen:1000[/FONT]
  [FONT=Calibri]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT]
  [FONT=Calibri]          Interrupt:18[/FONT]
  
  [FONT=Calibri]lo        Link encap:Local Loopback [/FONT]
  [FONT=Calibri]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT]
  [FONT=Calibri]          inet6 addr: ::1/128 Scope:Host[/FONT]
  [FONT=Calibri]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/FONT]
  [FONT=Calibri]          RX packets:51 errors:0 dropped:0 overruns:0 frame:0[/FONT]
  [FONT=Calibri]          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
  [FONT=Calibri]          collisions:0 txqueuelen:0[/FONT]
  [FONT=Calibri]          RX bytes:2567 (2.5 KB)  TX bytes:2567 (2.5 KB)[/FONT]
  
  [FONT=Calibri]wlan0     Link encap:Ethernet  HWaddr 4c:0f:6e:f7:75:f8 [/FONT]
  [FONT=Calibri]          UP BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT]
  [FONT=Calibri]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT]
  [FONT=Calibri]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
  [FONT=Calibri]          collisions:0 txqueuelen:1000[/FONT]
  [FONT=Calibri]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT]
  
  [FONT=Calibri]ubuntu@ubuntu:~$ iwconfig wlan0[/FONT]
  [FONT=Calibri]wlan0     IEEE 802.11bgn  ESSID:off/any [/FONT]
  [FONT=Calibri]          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm  [/FONT]
  [FONT=Calibri]          Retry  long limit:7   RTS thr:off   Fragment thr:off[/FONT]
  [FONT=Calibri]          Power Management:on[/FONT]
  
  
```
  
  [FONT=Calibri]4.) Check for modules. I found two, which might be the right ones, but I'm not sure:[/FONT]
  ```

  [FONT=Calibri]ath9k                 329117  0[/FONT]
  [FONT=Calibri]ath                     9723  1 ath9k[/FONT]
  
```
5.) Kernel configuration. When I called dmegs I got:
```

[    0.861703] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.861932] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.862054] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.862186] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.862337] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.862456] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]

[    2.182417] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    2.183240] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    2.184961] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    2.185230] TCP: Hash tables configured (established 524288 bind 65536)
[    2.185294] TCP reno registered

[    6.367253] TCP cubic registered

[   28.223145] ath9k 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   28.223157] ath9k 0000:02:00.0: setting latency timer to 64

[   28.274138] ath: EEPROM regdomain: 0x65
[   28.274141] ath: EEPROM indicates we should expect a direct regpair map
[   28.274144] ath: Country alpha2 being used: 00
[   28.274145] ath: Regpair used: 0x65

[   28.641320] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```
6.) Network configuration
```

ubuntu@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 4c:0f:6e:f7:75:f8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:f4a00000-f4a0ffff
  *-network
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 11
       serial: f0:bf:97:13:10:ed
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:35 memory:f2220000-f2223fff ioport:a000(size=256) memory:f2200000-f221ffff(prefetchable)


```
7.) Scan for networks:
```

ubuntu@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.


```
8.) Ubuntu version:
```

ubuntu@ubuntu:~$ lsb_release -d
Description:    Ubuntu 10.04.2 LTS


```
9.) Kernel/architecture:
```

[FONT=Calibri]ubuntu@ubuntu:~$ uname -mr
2.6.32-28-generic x86_64[/FONT]


```
10.) Restarting the network:
```

ubuntu@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...  [ OK ]

```


[FONT=Calibri]Has someone any ideas what I can do?
[/FONT]

---

### Post by wildmanne39 on 2011-07-30
Hi, click on the zip file it is a script that fixes wireless issue created by lkjoel.

Copy it to your desktop then do this.
```
cd ~/Desktop
chmod +x wirelessGUI.sh
./wirelessGUI.sh &
```
then just answer the questions and it will most likely fix your problem. 
You will need to enter you password every time it asks for it.
Thank you

---

### Post by Shadowrain on 2011-07-31
Thank you for your reply.  But the script won't work. It tries to connect, but then nothing happens and I have to abort it after a while.
Moreover, sometimes when I boot my system I have an internet connection and sometimes not, but it doesn't seem to follow a specific pattern.


I found out, why nothing happens with the script after a while: I have a Kubuntu and the script uses gksu. Gksu is a library that provides a Gtk+ frontend to su and sudo. But I have KDE and now the question is, if I should edit the script and if I can use kdesu instead of gksu.

---

### Post by wildmanne39 on 2011-07-31
Hi, you probably can, I want to ask the person who created the script before you do. I will have him take a look at your thread.

---

### Post by wildmanne39 on 2011-07-31
Hi, here is a kubuntu version of that script, I am sorry I did not realize you needed a different script.

I imagine you will need to use these commands.
```
cd ~/Desktop
chmod +x wirelessGUIKDE.sh
./wirelessGUIKDE.sh & 
```

---

### Post by Shadowrain on 2011-08-01
Thank you for the script. Unfortunately I got error messages, when I executed it. 

The command line said
```

ubuntu@ubuntu:~/Desktop$ ./wirelessGUIKDE.sh &
[1] 4278
ubuntu@ubuntu:~/Desktop$ QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/ubuntu/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/ubuntu/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon

```And the log file told me
```

===sudo ifconfig wlan0 down===
===sudo dhclient -r wlan0===
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/4c:0f:6e:f7:75:f8
Sending on   LPF/wlan0/4c:0f:6e:f7:75:f8
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
===sudo ifconfig wlan0 up===
===sudo iwconfig wlan0 essid "TnH"===
===sudo iwconfig wlan0 mode Managed===
===sudo dhclient wlan0===
There is already a pid file /var/run/dhclient.pid with pid 4327
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/4c:0f:6e:f7:75:f8
Sending on   LPF/wlan0/4c:0f:6e:f7:75:f8
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
It is really strange, because yesterday evening I could connect to the internet (without script I mean) and this morning I don't. Sometimes the internet works and sometimes not, but under Windows 7 it always does!

---

### Post by lkjoel on 2011-08-01
Yeah, that GUI script is sometimes buggy.

The script in my attachment usually works fine.
The commands for this script is:
```
cd ~/Desktop
chmod +x wireless.sh
wireless.sh wlan0 TnH
```

---

### Post by Shadowrain on 2011-08-01
Thank you for the script. I executed it and it finished, but still I had no internet connection.

This said the log file:

```

===sudo ifconfig wlan0 down===
===sudo dhclient -r wlan0===
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/4c:0f:6e:f7:75:f8
Sending on   LPF/wlan0/4c:0f:6e:f7:75:f8
Sending on   Socket/fallback
===sudo ifconfig wlan0 up===
===sudo iwconfig wlan0 essid "TnH"===
===sudo iwconfig wlan0 mode Managed===
===sudo dhclient wlan0===
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/4c:0f:6e:f7:75:f8
Sending on   LPF/wlan0/4c:0f:6e:f7:75:f8
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```Any more ideas what I could try?

---

### Post by wildmanne39 on 2011-08-01
Hi, change your SSID to all lower case and see if you can connect then.

Also so please post the results of this.
```
cat /etc/network/interfaces
```
Thank you

---

### Post by Shadowrain on 2011-08-02
cat /etc/network/interfaces gives me
```

auto lo
iface lo inet loopback

```

What does it tell you?

---

### Post by wildmanne39 on 2011-08-02
Hi, that is what is suppose to be there if anything else was there we would delete it.Run this command please and post the resluts here.
```
lsmod | grep ath
```
```
modinfo ath
```
Thank you

---

### Post by Shadowrain on 2011-08-02
The results are:

```

ubuntu@ubuntu:~$ lsmod | grep ath
ath9k                 329117  0 
mac80211              238896  1 ath9k
ath                     9723  1 ath9k
cfg80211              148725  3 ath9k,mac80211,ath
led_class               3764  2 ath9k,sdhci

```

and

```

ubuntu@ubuntu:~$ modinfo ath
filename:       /lib/modules/2.6.32-28-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3DE1C06BB3A602076E2374D
depends:        cfg80211
vermagic:       2.6.32-28-generic SMP mod_unload modversions 

```

And thank you for trying so hard to help me!

---

### Post by wildmanne39 on 2011-08-02
Hi, run this command please.
```
modinfo ath9k | grep 02b
```

Did you change your settings to manage not master?

---

### Post by Shadowrain on 2011-08-02
When I run this command I get nothing back.
And I don't know what you mean by 'change your settings to manage to master'.

---

### Post by wildmanne39 on 2011-08-02
Hi, I am sorry the command should have been.
```
modinfo ath9k | grep 002b
```
Lets set it to managed.
```
sudo ifconfig wlan0 down
```
```
sudo iwconfig wlano0 mode Managed
```
```
sudo ifconfig wlan0 up
```
make sure you do not have your wired connection plugged in while we are trying to connect with your wireless.

---

### Post by Shadowrain on 2011-08-02
I did as you said, but I still got nothing from the command line.

---

### Post by wildmanne39 on 2011-08-02
Hi, make sure your router is set to b/g/n mode and not just n mode, then see if you can connect.

---

### Post by Shadowrain on 2011-08-02
I couldn't find any settings in my router to change any modes.
Do you think that is the last option I have? 
Because then I would try to purge pulseaudio from my system and hope that everything is back to normal. Otherwise I'm going to reinstall my Kubuntu. I means it's not that of a big deal, because it is almost fresh anyway (only ten days old).

---

### Post by wildmanne39 on 2011-08-02
Hi,to change your router setting you type something like this 168.192.0.1 into the address bar of firefox.

Lets try this
```
sudo ifconfig wlan0 down
```
```
sudo rmmod -f ath9k
```
```
sudo modprobe ath9k 11n_disable=1
```
```
sudo ifconfig wlan0 up
```
see if that works.

---

### Post by wildmanne39 on 2011-08-02
Hi, you can also try
```
sudo iwconfig wlan0 power off
```

---

### Post by Shadowrain on 2011-08-02
Sorry your last post came to late, I had to boot my Windows to write back.

```

ubuntu@ubuntu:~/Desktop$ sudo modprobe ath9k 11n_disable=1
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
FATAL: Error inserting ath9k (/lib/modules/2.6.32-28-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko): Unknown symbol in module, or unknown parameter (see dmesg)

ubuntu@ubuntu:~/Desktop$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

```If I understand correctly, I have removed the kernel module for ath and now my Kubuntu has a missing driver?

---

### Post by wildmanne39 on 2011-08-02
Hi, did you run all the commands I gave you in my last post? If it caused more problems restart your computer and it will be reset to the way it was before you did the commands.

The driver is there but that one command I gave you did not show that your wireless device is being driven by the driver. I ask for chili555 to take a look when it has time.

---

### Post by Shadowrain on 2011-08-02
Yes I executed all the commands you gave me.

And thank you for your time.

---

### Post by chili555 on 2011-08-02
Wild Man made a slight error. The parameter he asked you to load is not correct for ath9k; please see here:> $ modinfo ath9k
filename:       /lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     A154806ADE78F5F924B0792
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,mac80211,cfg80211,ath9k_common,ath
vermagic:       2.6.38-10-generic SMP mod_unload modversions 686 
[COLOR="Red"]parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)[/COLOR]That's why the system said:> Unknown symbol in module, or unknown parameterIn effect, it said, 'I don't know what 11n_disable=1 means, so I'm not going to do it.'

Also, the command should have been:```
modinfo ath9k | grep 002E
```As you see above, the aliases are in upper-case; if you grep (look for a pattern) in lower-case, it will return no result.

Now I will go back and study your issue, maybe three heads are better than two.

---

### Post by chili555 on 2011-08-02
Does it connect sometimes? Other times, does it try and time out? What are your specific symptoms?

Your settings actually look very good.

---

### Post by Shadowrain on 2011-08-02
Yes, sometimes it connects and sometimes it doesn't. And I don't see, if it times out (where can I see this?). No more symptoms. It doesn't follow a pattern I'm aware of.

---

### Post by wildmanne39 on 2011-08-02
Hi, try this ```
kdesudo kate  /etc/modprobe.d/options.conf
```
and put
```
options ath9k nohwcrypt=1
```
press Enter so there is an end-of-line marker set in it then save it.
Then reboot.

---

### Post by chili555 on 2011-08-02
> **Shadowrain said:**
> Yes, sometimes it connects and sometimes it doesn't. And I don't see, if it times out (where can I see this?). No more symptoms. It doesn't follow a pattern I'm aware of.You would see the Network Manager swirl around endlessly, ask for your password again and again and finally say, "You are disconnected."> Hi, try this
Code:

kdesudo kate  /etc/modprobe.d/options.conf

and put
Code:

options ath9k nohwcrypt=1

in it and save it.
Then reboot. Perfect!

---

### Post by Shadowrain on 2011-08-02
I did as you told me. Up to this point everything seems to work fine, but I don't now if its due to the edited file. Is there a way to test it?

---

### Post by lkjoel on 2011-08-02
EDIT: Wrong post lol!

---

### Post by wildmanne39 on 2011-08-02
Hi, yes it is because of the file that should have fixed your issue,would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by lkjoel on 2011-08-02
> **Shadowrain said:**
> I did as you told me. Up to this point everything seems to work fine, but I don't now if its due to the edited file. Is there a way to test it?
Yes. Type in the Terminal window:
```
ping google.com

```
CTRL+C is to stop the pinging.
If you see 100% packet loss, then you are not connected.

---

### Post by Shadowrain on 2011-08-02
Thank you very much for all your effort and time!

---

### Post by wildmanne39 on 2011-08-02
Hi, your welcome and thank you chili555.

---

