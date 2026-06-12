---
title: "D-Link DWA-140 B3 and Ubuntu 11.10"
date: 2012-01-24
forum: Networking &amp; Wireless
---

### Post by hmln-dk on 2012-01-24
Hi All,

I'm quite new to Ubuntu :???:  and having problems with my new hardware a D-Link DWA-140 B3.
It works fine on Win 7.

I hope you can help me getting the adapter working - The B3 version of the adapter seems to be quite difficult getting to work with the Ubuntu 11.10.

I've downloaded the driver from Ralink -  rt5370sta according to: 
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)

But I need an easy step by step guide.

I have tried looking for help - but it seems that the B3 version needs special skills.

An update from lsusb:

anonym@anonym:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1058:0910 Western Digital Technologies, Inc. MyBook Essential External HDD
Bus 004 Device 002: ID 0763:2012 Midiman M-Audio Fast Track Pro
Bus 004 Device 003: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 005 Device 002: ID 046d:c30f Logitech, Inc. Logicool HID-Compliant Keyboard (106 key)
Bus 001 Device 005: ID 2001:3c15 D-Link Corp.

And iwconfig:

anonym@anonym:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

Thanks for you help!

Kind regards

Hans

---

### Post by chili555 on 2012-01-24
> I've downloaded the driver from Ralink - rt5370sta according to: Which version? I have version 2.5.0.2 and it doesn't support your device:> chili@LAPTOP60:~$ modinfo Desktop/Forum/ubuntu_stuff/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V**2.5.0.2**_DPO/os/linux/rt5370sta.ko | grep [COLOR="Red"]3C15[/COLOR]
chili@LAPTOP60:~$ Which is to say, no match. Did you download a later version?

I have a few ideas that may or may not work.> Bus 001 Device 005: ID 2001:[COLOR="Red"]3c15[/COLOR] D-Link Corp.

---

### Post by hmln-dk on 2012-01-25
I have downloaded this version:
2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO
But I don't know what to do then...

---

### Post by chili555 on 2012-01-25
> **hmln-dk said:**
> I have downloaded this version:
2011_0225_RT5370_RT5372_Linux_STA_V[COLOR="Red"]**2.5.0.1**[/COLOR]_DPO
But I don't know what to do then...That version isn't going to support your device either. I could teach you to compile it and it would do nothing.

If you are ready to step off into experimental territory, let's get started with the special skills. Remove the device and in a terminal, do:```

sudo gedit /etc/udev/rules.d/network_drivers.rules
```Add one long line:```

ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="2001", ATTR{idProduct}=="3c15", RUN+="/sbin/modprobe -qba rt2800usb"
```Caps, brackets, punctuation, etc. are crucial. Proofread twice, save and close gedit.```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Add one long single line:```

install rt2800usb /sbin/modprobe --ignore-install rt2800usb $CMDLINE_OPTS; /bin/echo "2001 3c15" > /sys/bus/usb/drivers/rt2800/new_id
```
Proofread twice, save and close gedit. 

Now download the newer firmware file I've attached to your desktop. Right-click it and select *Extract Here*. Now, back to the terminal and do:```
sudo mv /lib/firmware/rt2870.bin /lib/firmware/rt2870.old
sudo cp Desktop/RT2870_Firmware_V22/rt2870.bin /lib/firmware
```

Insert the device. If it doesn't start immediately, you might have to do:```
sudo modprobe rt2800usb
```Please post back with your report.

---

### Post by hmln-dk on 2012-01-25
Hello again,

Thanks for your help! 

Before trying  your guidelines - I've found a newer driver!!!
2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO

It's working :D - but sometimes disconnects to my network - Would you suggest that I follow your advice anyway? Or could you cure the "disconnect-sickness" ?

Enclosed details:

anonym@anonym:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 2001:3c15 D-Link Corp. 
Bus 002 Device 002: ID 1058:0910 Western Digital Technologies, Inc. MyBook Essential External HDD
Bus 004 Device 002: ID 0763:2012 Midiman M-Audio Fast Track Pro
Bus 004 Device 003: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 005 Device 002: ID 046d:c30f Logitech, Inc. Logicool HID-Compliant Keyboard (106 key)
anonym@anonym:~$ sudo ifconfig
[sudo] password for anonym: 
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:0c:d8:1f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:1d:7d:0c:c2:ff  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8813 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8813 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:361240 (361.2 KB)  TX bytes:361240 (361.2 KB)

ra0       Link encap:Ethernet  HWaddr b8:a3:86:00:f6:21  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::baa3:86ff:fe00:f621/64 Scope:Link
          UP BROADCAST NOTRAILERS RUNNING PROMISC ALLMULTI  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:709929044 (709.9 MB)  TX bytes:18789135 (18.7 MB)

anonym@anonym:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

ra0       Ralink STA  ESSID:"ingen adgang"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:19:70:66:F1:23   
          Bit Rate=130 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=73/100  Signal level:-68 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

anonym@anonym:~$ 

Kind regards

Hans

---

### Post by chili555 on 2012-01-25
> Would you suggest that I follow your advice anyway?Not yet. If you have a working driver, and at N speeds, I'd try to refine it first. Are there any clues here?```
dmesg | grep -e ra0 -e rt5
sudo cat /var/log/syslog | grep etwork | tail -n20
```We will get the best information if you run these right after a disconnect.

---

### Post by hmln-dk on 2012-01-25
Hi again,

I hope the enclosed make any sense to you - Thanks in advance.

anonym@anonym:~$ dmesg | grep -e ra0 -e rt5
[   42.600014] ra0: no IPv6 routers present
[  507.800013] ra0: no IPv6 routers present
[  692.816012] ra0: no IPv6 routers present
[ 2247.648013] ra0: no IPv6 routers present

anonym@anonym:~$ sudo cat /var/log/syslog | grep etwork | tail -n20
Jan 25 23:31:09 anonym NetworkManager[992]: <info> Activation (ra0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan 25 23:31:09 anonym NetworkManager[992]: <info> dhclient started with pid 5983
Jan 25 23:31:09 anonym NetworkManager[992]: <info> Activation (ra0) Beginning IP6 addrconf.
Jan 25 23:31:09 anonym NetworkManager[992]: <info> Activation (ra0) Stage 3 of 5 (IP Configure Start) complete.
Jan 25 23:31:09 anonym NetworkManager[992]: <info> (ra0): DHCPv4 state changed nbi -> preinit
Jan 25 23:31:09 anonym NetworkManager[992]: <info> (ra0): DHCPv4 state changed preinit -> reboot
Jan 25 23:31:09 anonym NetworkManager[992]: <info> Activation (ra0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan 25 23:31:09 anonym NetworkManager[992]: <info> Activation (ra0) Stage 4 of 5 (IP4 Configure Get) started...
Jan 25 23:31:09 anonym NetworkManager[992]: <info>   address 192.168.1.11
Jan 25 23:31:09 anonym NetworkManager[992]: <info>   prefix 24 (255.255.255.0)
Jan 25 23:31:09 anonym NetworkManager[992]: <info>   gateway 192.168.1.1
Jan 25 23:31:09 anonym NetworkManager[992]: <info>   hostname 'anonym'
Jan 25 23:31:09 anonym NetworkManager[992]: <info>   nameserver '192.168.1.1'
Jan 25 23:31:09 anonym NetworkManager[992]: <info>   domain name 'home'
Jan 25 23:31:09 anonym NetworkManager[992]: <info> Activation (ra0) Stage 5 of 5 (IP Configure Commit) started...
Jan 25 23:31:10 anonym NetworkManager[992]: <info> (ra0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jan 25 23:31:10 anonym NetworkManager[992]: <info> Policy set 'ingen adgang' (ra0) as default for IPv4 routing and DNS.
Jan 25 23:31:10 anonym NetworkManager[992]: <info> Activation (ra0) successful, device activated.
Jan 25 23:31:10 anonym NetworkManager[992]: <info> Activation (ra0) Stage 5 of 5 (IP Configure Commit) complete.
Jan 25 23:31:10 anonym NetworkManager[992]: <info> Activation (ra0) Stage 4 of 5 (IP4 Configure Get) complete.
anonym@anonym:~$ sudo cat /var/log/syslog | grep etwork | tail -n20
Jan 25 23:31:09 anonym NetworkManager[992]: <info> dhclient started with pid 5983
Jan 25 23:31:09 anonym NetworkManager[992]: <info> Activation (ra0) Beginning IP6 addrconf.
Jan 25 23:31:09 anonym NetworkManager[992]: <info> Activation (ra0) Stage 3 of 5 (IP Configure Start) complete.
Jan 25 23:31:09 anonym NetworkManager[992]: <info> (ra0): DHCPv4 state changed nbi -> preinit
Jan 25 23:31:09 anonym NetworkManager[992]: <info> (ra0): DHCPv4 state changed preinit -> reboot
Jan 25 23:31:09 anonym NetworkManager[992]: <info> Activation (ra0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan 25 23:31:09 anonym NetworkManager[992]: <info> Activation (ra0) Stage 4 of 5 (IP4 Configure Get) started...
Jan 25 23:31:09 anonym NetworkManager[992]: <info>   address 192.168.1.11
Jan 25 23:31:09 anonym NetworkManager[992]: <info>   prefix 24 (255.255.255.0)
Jan 25 23:31:09 anonym NetworkManager[992]: <info>   gateway 192.168.1.1
Jan 25 23:31:09 anonym NetworkManager[992]: <info>   hostname 'anonym'
Jan 25 23:31:09 anonym NetworkManager[992]: <info>   nameserver '192.168.1.1'
Jan 25 23:31:09 anonym NetworkManager[992]: <info>   domain name 'home'
Jan 25 23:31:09 anonym NetworkManager[992]: <info> Activation (ra0) Stage 5 of 5 (IP Configure Commit) started...
Jan 25 23:31:10 anonym NetworkManager[992]: <info> (ra0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jan 25 23:31:10 anonym NetworkManager[992]: <info> Policy set 'ingen adgang' (ra0) as default for IPv4 routing and DNS.
Jan 25 23:31:10 anonym NetworkManager[992]: <info> Activation (ra0) successful, device activated.
Jan 25 23:31:10 anonym NetworkManager[992]: <info> Activation (ra0) Stage 5 of 5 (IP Configure Commit) complete.
Jan 25 23:31:10 anonym NetworkManager[992]: <info> Activation (ra0) Stage 4 of 5 (IP4 Configure Get) complete.
Jan 25 23:31:11 anonym NetworkManager[992]: <info> wpa_supplicant die count reset
anonym@anonym:~$

---

### Post by hmln-dk on 2012-01-25
> **hmln-dk said:**
> Hi again,

I hope the enclosed make any sense to you - Thanks in advance.

anonym@anonym:~$ dmesg | grep -e ra0 -e rt5
[   42.600014] ra0: no IPv6 routers present
[  507.800013] ra0: no IPv6 routers present
[  692.816012] ra0: no IPv6 routers present
[ 2247.648013] ra0: no IPv6 routers present

anonym@anonym:~$ sudo cat /var/log/syslog | grep etwork | tail -n20
Jan 25 23:31:09 anonym NetworkManager[992]: <info> Activation (ra0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan 25 23:31:09 anonym NetworkManager[992]: <info> dhclient started with pid 5983
Jan 25 23:31:09 anonym NetworkManager[992]: <info> Activation (ra0) Beginning IP6 addrconf.
Jan 25 23:31:09 anonym NetworkManager[992]: <info> Activation (ra0) Stage 3 of 5 (IP Configure Start) complete.
Jan 25 23:31:09 anonym NetworkManager[992]: <info> (ra0): DHCPv4 state changed nbi -> preinit
Jan 25 23:31:09 anonym NetworkManager[992]: <info> (ra0): DHCPv4 state changed preinit -> reboot
Jan 25 23:31:09 anonym NetworkManager[992]: <info> Activation (ra0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan 25 23:31:09 anonym NetworkManager[992]: <info> Activation (ra0) Stage 4 of 5 (IP4 Configure Get) started...
Jan 25 23:31:09 anonym NetworkManager[992]: <info>   address 192.168.1.11
Jan 25 23:31:09 anonym NetworkManager[992]: <info>   prefix 24 (255.255.255.0)
Jan 25 23:31:09 anonym NetworkManager[992]: <info>   gateway 192.168.1.1
Jan 25 23:31:09 anonym NetworkManager[992]: <info>   hostname 'anonym'
Jan 25 23:31:09 anonym NetworkManager[992]: <info>   nameserver '192.168.1.1'
Jan 25 23:31:09 anonym NetworkManager[992]: <info>   domain name 'home'
Jan 25 23:31:09 anonym NetworkManager[992]: <info> Activation (ra0) Stage 5 of 5 (IP Configure Commit) started...
Jan 25 23:31:10 anonym NetworkManager[992]: <info> (ra0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jan 25 23:31:10 anonym NetworkManager[992]: <info> Policy set 'ingen adgang' (ra0) as default for IPv4 routing and DNS.
Jan 25 23:31:10 anonym NetworkManager[992]: <info> Activation (ra0) successful, device activated.
Jan 25 23:31:10 anonym NetworkManager[992]: <info> Activation (ra0) Stage 5 of 5 (IP Configure Commit) complete.
Jan 25 23:31:10 anonym NetworkManager[992]: <info> Activation (ra0) Stage 4 of 5 (IP4 Configure Get) complete.
anonym@anonym:~$ sudo cat /var/log/syslog | grep etwork | tail -n20
Jan 25 23:31:09 anonym NetworkManager[992]: <info> dhclient started with pid 5983
Jan 25 23:31:09 anonym NetworkManager[992]: <info> Activation (ra0) Beginning IP6 addrconf.
Jan 25 23:31:09 anonym NetworkManager[992]: <info> Activation (ra0) Stage 3 of 5 (IP Configure Start) complete.
Jan 25 23:31:09 anonym NetworkManager[992]: <info> (ra0): DHCPv4 state changed nbi -> preinit
Jan 25 23:31:09 anonym NetworkManager[992]: <info> (ra0): DHCPv4 state changed preinit -> reboot
Jan 25 23:31:09 anonym NetworkManager[992]: <info> Activation (ra0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan 25 23:31:09 anonym NetworkManager[992]: <info> Activation (ra0) Stage 4 of 5 (IP4 Configure Get) started...
Jan 25 23:31:09 anonym NetworkManager[992]: <info>   address 192.168.1.11
Jan 25 23:31:09 anonym NetworkManager[992]: <info>   prefix 24 (255.255.255.0)
Jan 25 23:31:09 anonym NetworkManager[992]: <info>   gateway 192.168.1.1
Jan 25 23:31:09 anonym NetworkManager[992]: <info>   hostname 'anonym'
Jan 25 23:31:09 anonym NetworkManager[992]: <info>   nameserver '192.168.1.1'
Jan 25 23:31:09 anonym NetworkManager[992]: <info>   domain name 'home'
Jan 25 23:31:09 anonym NetworkManager[992]: <info> Activation (ra0) Stage 5 of 5 (IP Configure Commit) started...
Jan 25 23:31:10 anonym NetworkManager[992]: <info> (ra0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jan 25 23:31:10 anonym NetworkManager[992]: <info> Policy set 'ingen adgang' (ra0) as default for IPv4 routing and DNS.
Jan 25 23:31:10 anonym NetworkManager[992]: <info> Activation (ra0) successful, device activated.
Jan 25 23:31:10 anonym NetworkManager[992]: <info> Activation (ra0) Stage 5 of 5 (IP Configure Commit) complete.
Jan 25 23:31:10 anonym NetworkManager[992]: <info> Activation (ra0) Stage 4 of 5 (IP4 Configure Get) complete.
Jan 25 23:31:11 anonym NetworkManager[992]: <info> wpa_supplicant die count reset
anonym@anonym:~$

**And another drop-out-info:**

anonym@anonym:~$ dmesg | grep -e ra0 -e rt5
[   42.600014] ra0: no IPv6 routers present
[  507.800013] ra0: no IPv6 routers present
[  692.816012] ra0: no IPv6 routers present
[ 2247.648013] ra0: no IPv6 routers present
[ 2563.040017] ra0: no IPv6 routers present
[ 3370.616012] ra0: no IPv6 routers present
anonym@anonym:~$ sudo cat /var/log/syslog | grep etwork | tail -n20
[sudo] password for anonym: 
Jan 25 23:44:37 anonym NetworkManager[992]: <info> Activation (ra0) Stage 4 of 5 (IP4 Configure Get) started...
Jan 25 23:44:37 anonym NetworkManager[992]: <info>   address 192.168.1.11
Jan 25 23:44:37 anonym NetworkManager[992]: <info>   prefix 24 (255.255.255.0)
Jan 25 23:44:37 anonym NetworkManager[992]: <info>   gateway 192.168.1.1
Jan 25 23:44:37 anonym NetworkManager[992]: <info>   hostname 'anonym'
Jan 25 23:44:37 anonym NetworkManager[992]: <info>   nameserver '192.168.1.1'
Jan 25 23:44:37 anonym NetworkManager[992]: <info>   domain name 'home'
Jan 25 23:44:37 anonym NetworkManager[992]: <info> Activation (ra0) Stage 5 of 5 (IP Configure Commit) started...
Jan 25 23:44:38 anonym NetworkManager[992]: <info> (ra0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jan 25 23:44:38 anonym NetworkManager[992]: <info> Policy set 'ingen adgang' (ra0) as default for IPv4 routing and DNS.
Jan 25 23:44:38 anonym NetworkManager[992]: <info> Activation (ra0) successful, device activated.
Jan 25 23:44:38 anonym NetworkManager[992]: <info> Activation (ra0) Stage 5 of 5 (IP Configure Commit) complete.
Jan 25 23:44:38 anonym NetworkManager[992]: <info> Activation (ra0) Stage 4 of 5 (IP4 Configure Get) complete.
Jan 25 23:44:41 anonym NetworkManager[992]: <info> wpa_supplicant die count reset
Jan 25 23:44:57 anonym NetworkManager[992]: <info> (ra0): IP6 addrconf timed out or failed.
Jan 25 23:44:57 anonym NetworkManager[992]: <info> Activation (ra0) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Jan 25 23:44:57 anonym NetworkManager[992]: <info> Activation (ra0) Stage 4 of 5 (IP6 Configure Timeout) started...
Jan 25 23:44:57 anonym NetworkManager[992]: <info> Activation (ra0) Stage 5 of 5 (IP Configure Commit) started...
Jan 25 23:44:57 anonym NetworkManager[992]: <info> Activation (ra0) Stage 5 of 5 (IP Configure Commit) complete.
Jan 25 23:44:57 anonym NetworkManager[992]: <info> Activation (ra0) Stage 4 of 5 (IP6 Configure Timeout) complete.
anonym@anonym:~$

---

### Post by chili555 on 2012-01-26
> Jan 25 23:44:57 anonym NetworkManager[992]: <info> (ra0): [COLOR="Red"]IP6 addrconf timed out or failed.[/COLOR]
Jan 25 23:44:57 anonym NetworkManager[992]: <info> Activation (ra0) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Jan 25 23:44:57 anonym NetworkManager[992]: <info> Activation (ra0) Stage 4 of 5 (IP6 Configure Timeout) started...I'm not sure that IPv6 has much to do with this, but let's see. Please right-click the Network Manager icon and select Edit Connections. Select Wireless and then IPv6 Settings. Change Method to Ignore. Save and close. Are the disconnects solved? Reduced? Or...?

---

### Post by hmln-dk on 2012-01-26
> **chili555 said:**
> I'm not sure that IPv6 has much to do with this, but let's see. Please right-click the Network Manager icon and select Edit Connections. Select Wireless and then IPv6 Settings. Change Method to Ignore. Save and close. Are the disconnects solved? Reduced? Or...?

Hello again,

Tried your advice - however i'm still having drop-outs - and there seems to be another problem - Ubuntu won't shut down - so I think that my driver-adventure has failed- I will try again following your advice from yesterday.

"I'll be back" [IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG]

Kind regards

Hans

---

### Post by hmln-dk on 2012-01-26
> **hmln-dk said:**
> Hello again,

Tried your advice - however i'm still having drop-outs - and there seems to be another problem - Ubuntu won't shut down - so I think that my driver-adventure has failed- I will try again following your advice from yesterday.

"I'll be back" [IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG]

Kind regards

Hans

New status - Clean "dual boot" updated install

No adapter mounted

downloaded:
RT8070 /RT3070 /RT3370 /RT5370 /RT5372 USB
from [http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)

next: Sudo make and sudo make install 
- connected the adapter - and it works!

Do I have do do anything more?

Kind regards

Hans

---

### Post by chili555 on 2012-01-26
> and it works!

Do I have do do anything more?Just one thing; use Thread Tools at the top and Mark Solved....oh, and enjoy!! Glad it's working.

---

### Post by Nichlee on 2012-04-09
> **hmln-dk said:**
> New status - Clean "dual boot" updated install

No adapter mounted

downloaded:
RT8070 /RT3070 /RT3370 /RT5370 /RT5372 USB
from [http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)

next: Sudo make and sudo make install 
- connected the adapter - and it works!

Do I have do do anything more?

Kind regards

Hans

Hi, could you give me an step by step way to install that driver you have downloaded ? Have used linux a while, but not to good with the installing part of bz2, tar and so on files :P 

Thanks

Yours faithfully
Lee

---

### Post by chili555 on 2012-04-09
Lee, before we give you the magic of compiling, tell us about your device. Please open a terminal and run and post:```
lsusb
```Also, what version are you running?```
lsb_release -r
```Are you able to get an ethernet connection temporarily?

---

### Post by Nichlee on 2012-04-09
> **chili555 said:**
> Lee, before we give you the magic of compiling, tell us about your device. Please open a terminal and run and post:```
lsusb
```Also, what version are you running?```
lsb_release -r
```Are you able to get an ethernet connection temporarily?
Not using ubuntu at the moment, but its for ubuntu 11.10 and its the  same wireless usb. Should I go ahead and install ubuntu again and then let you help me? ^^

Yours faithfully
Lee

---

### Post by chili555 on 2012-04-09
Can you get those details running the live CD? If you are running any other Linux distribution, the *lsusb* will be the same.

---

### Post by Nichlee on 2012-04-09
> **chili555 said:**
> Lee, before we give you the magic of compiling, tell us about your device. Please open a terminal and run and post:```
lsusb
```Also, what version are you running?```
lsb_release -r
```Are you able to get an ethernet connection temporarily?
Did an reinstall, using ubuntu 11.10 now

lsusb:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 003: ID 2001:3c15 D-Link Corp. 

Yes, using the ethernet connection now

---

### Post by chili555 on 2012-04-09
Alrighty then, let's rock! Download the file referenced above to your desktop. Right-click the package and select *Extract Here*. Another compressed package will be extracted. Right-click it and select *Rename*. Rename it 5370 with no extension. Right-click the package and select *Extract Here*. Whew!

Now open the folder and drill down to os/linux/config.mk. Open config.mk with Text Editor. Change these lines.```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=[COLOR="Red"]y[/COLOR]


# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=[COLOR="Red"]y[/COLOR]
```Proofread carefully, save and close the text editor. Now open the terminal and do:```
sudo apt-get install linux-headers-generic build-essential
cd Desktop/2011
```Press Tab and the remainder of the long name will fill in automagically. Press Enter. Now do:```
sudo su
make
make install
modprobe rt5370sta
exit
```Is it working?

---

### Post by Nichlee on 2012-04-09
> 
cd Desktop/2011[/CODE]Press Tab and the remainder of the long name will fill in automagically. Press Enter. Now do:```
sudo su
make
make install
modprobe rt5370sta
exit
```Is it working?

the install was succesfull. But when i do cd desktop/2011 and press tab or copy/paste the folder name I only get No such file or directory. Have also tried with skrivebord/2011 and tab but no luck.

My ubuntu is on norwegian, so i tried with skrivebord wich is desktop on english

Edit: No worries, found out of it !
And its working, thanks alot!

---

### Post by chili555 on 2012-04-09
> Edit: No worries, found out of it !
And its working, thanks alot!Awesome! Glad it's working.

Whenever a newer kernel version, or linux-image as it's called in Ubuntu, is released and installed by Update Manager, you'll need to rebuild the module for the newer kernel:```
sudo su
[COLOR="Red"]make clean[/COLOR]
make
make install
modprobe rt5370sta
exit
```Please make a note of this so you are ready when the inevitable updates are installed.

Congratulations; now you are among the few who are experienced and successful with compiling!

---

### Post by Nichlee on 2012-04-09
> **chili555 said:**
> Awesome! Glad it's working.

Whenever a newer kernel version, or linux-image as it's called in Ubuntu, is released and installed by Update Manager, you'll need to rebuild the module for the newer kernel:```
sudo su
[COLOR="Red"]make clean[/COLOR]
make
make install
modprobe rt5370sta
exit
```Please make a note of this so you are ready when the inevitable updates are installed.

Congratulations; now you are among the few who are experienced and successful with compiling!
Haha, already done a print screen, cause I did an update and needed to do it again ;P But thanks again, have tried out ubuntu over a few years. But have been on and off But just got my System76 machine from USA soo..now am I going to stick with ubuntu ^^, 
But ofc, Win7 on my other gaming machine...ashamed:oops:

---

### Post by MichaelMaier on 2012-04-14
> **chili555 said:**
> Alrighty then, let's rock! Download the file referenced above to your desktop. Right-click the package and select *Extract Here*. Another compressed package will be extracted. Right-click it and select *Rename*. Rename it 5370 with no extension. Right-click the package and select *Extract Here*. Whew!

Now open the folder and drill down to os/linux/config.mk. Open config.mk with Text Editor. Change these lines.```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=[COLOR="Red"]y[/COLOR]


# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=[COLOR="Red"]y[/COLOR]
```Proofread carefully, save and close the text editor. Now open the terminal and do:```
sudo apt-get install linux-headers-generic build-essential
cd Desktop/2011
```Press Tab and the remainder of the long name will fill in automagically. Press Enter. Now do:```
sudo su
make
make install
modprobe rt5370sta
exit
```Is it working?
Just tried it and it's working great. Thank you so much.

Regards,
Michael

---

### Post by R.A. on 2012-05-20
> **chili555 said:**
> Alrighty then, let's rock! [...]Is it working?

Thank you for the tutorial, and yes, it works for me too!

---

### Post by Redcougar27 on 2012-06-13
To Chili555,

I had the same problem with a d-link DWA140B3 (not working with xubuntu 12.04). Your solution was rather easy to apply and it's working. Thanks a lot.

---

### Post by Redcougar27 on 2012-06-19
Dear Chil555,

It's a pity, but after an upgrade of the linux kernel, the D-link DWA140B3 is NOT working anymore. Several attemps (following your advices) were unsuccessful. I am crying...
Best regards.

---

### Post by wildmanne39 on 2012-06-19
Hi Redcougar27, please see post 20.
Thanks

---

### Post by s.v.z on 2012-10-04
Great topic! Really helped me out. You guys rock! :guitar:

---

