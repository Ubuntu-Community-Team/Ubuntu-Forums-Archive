---
title: "Password Corrupts for Connect to Hidden Network"
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by Ed934 on 2009-07-10
I've just installed Ubunto 9.04 on my Asus eeePC Netbook using the Wubi version. I am able to jump onto my neighbor's wireless network but not my own! So, I assume my card is working all right. The problem I'm having is that the password always seems to become corrupted every time I enter it. I have all of the SSID feature properly selected, but the password gets corrupted every time.

I've done a system check pasted below and an lshw -C network. I don't much about this really, but read these were helpful in other posts:

System Testing report
RT2860
Property    Value
info.subsystem    pci
info.product    RT2860
info.vendor    RaLink
info.parent    /org/freedesktop/Hal/devices/pci_8086_27d6
info.linux.driver    rt2860
info.udi    /org/freedesktop/Hal/devices/pci_1814_781
pci.product    RT2860
pci.vendor_id    6164
pci.vendor    RaLink
pci.product_id    1921
pci.device_protocol    0
pci.subsys_vendor    RaLink
pci.device_subclass    128
pci.subsys_vendor_id    6164
pci.device_class    2
pci.subsys_product_id    10128
pci.linux.sysfs_path    /sys/devices/pci0000:00/0000:00:1c.3/0000:01:00.0



 lshw -C network

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: L1e Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:24:8c:a7:ba:13
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 module=atl1e multicast=yes
  *-network
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: ra0
       version: 00
       serial: 00:22:43:96:46:9b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 ip=192.168.1.100 latency=0 module=rt2860sta multicast=yes wireless=RT2860 Wireless
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 6e:1c:76:c1:21:72
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
main3@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:8c:a7:ba:13  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

ra0       Link encap:Ethernet  HWaddr 00:22:43:96:46:9b  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:43ff:fe96:469b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20223 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3680 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4918888 (4.9 MB)  TX bytes:477947 (477.9 KB)
          Interrupt:19 


Any suggestions for getting MY OWN wireless card connecting to my own router would be much appreciated.

Ed

---

### Post by Ed934 on 2009-07-10
Maybe I should add too that I do not have any bars on the wireless icon on the panel. 

So I choose >Connect to Hidden wireless network>

I wonder if the "Allow access" popup window option, "Allow application access to keyring?" is part of the problem?

It reads, "The application 'NetworkManager Applet' (/usr/bin/nm-applet) wants to access the password for 'network secret for Wireless connection 1/802-11-wireless-security/psk' in the default keyring"
deny allow once always allow"

Not knowing what to click, I've always clicked "always allow," assuming that's the right one, since I want to ALWAYS get on the Internet!!

"Connect Automatically" is checked. I enter my SSID, Mode: Infrastruture, go to Wireless tab, select Security WPA & WPA2 Personal, enter my password, click show password to make sure it's right, then OK.

The wireless icon whirrs and whirrs but never connects. When I right click and check it > edit, show the password, I get a long string like this, three or four times longer than my password:

1d6050107dddd7aeb296473ded4e41f7ee577f7e4931b751d582bccc5faa9dd9

Any ideas?

Ed

---

### Post by stuckdoingwork on 2009-07-10
I recall having the same issue, both on my EEE and a Dell Latitude both running Jaunty.

The password is not getting corrupted, I believe that's the encrypted hash.  I honestly don't recall exactly how I fixed it, but I spent a good afternoon repeatedly hitting 'connect.'  I don't think it matters whether you have the hash or plaintext password, but I could be mistaken.  You can try reducing the security (temporarily) to WEP or NONE (on the router too!) just to ensure that the card and router are working correctly.

I don't know if this was part of the solution, but I ended up resetting the password on my router a few times as well.  One of my problems I think was having too simple a passphrase and it wasn't getting saved/applied correctly, so I may have autogenerated a passkey.

You were right to click 'always allow' and be sure to type in your (ubuntu) password correctly if it prompted you then.

---

### Post by Ed934 on 2009-07-10
> **stuckdoingwork said:**
> 
I don't think it matters whether you have the hash or plaintext password, but I could be mistaken.  You can try reducing the security (temporarily) to WEP or NONE (on the router too!) just to ensure that the card and router are working correctly.

I don't know if this was part of the solution, but I ended up resetting the password on my router a few times as well.  One of my problems I think was having too simple a passphrase and it wasn't getting saved/applied correctly, so I may have autogenerated a passkey.

You were right to click 'always allow' and be sure to type in your (ubuntu) password correctly if it prompted you then.


With five laptops in the house, I really want to avoid resetting the router password.... I do have a fairly long auto generate password. I've never had any trouble with my other laptops, so I'm not too hasty to head for the router. I appreciate the suggestion, but I've been there before. 

Thanks for mentioning "always allow" is okay. I thought maybe that was the problem. I'm assuming the correct password which I enter is somehow saved in the Keyring? So maybe when it times out, the seemingly random lettering under password is just coded or "hash." After a week of playing with this already, I don't know what else to try.... 

Ed

---

### Post by ecujak on 2009-07-29
> **Ed934 said:**
> I really want to avoid resetting the router password.... I do have a fairly long auto generate password.

Ed

first you have know isolate the issue

---

### Post by Ed934 on 2009-08-07
> **ecujak said:**
> first you have know isolate the issue


How? I'm open to suggestions. I still haven't been able to get the wireless to work.

Ed

---

### Post by Ed934 on 2009-08-07
Here's my setup which is beyond me:
 

sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: L1e Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:24:8c:a7:ba:13
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.1.109 latency=0 link=yes module=atl1e multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: ra0
       version: 00
       serial: 00:22:43:96:46:9b
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=0 module=rt2860sta multicast=yes wireless=RT2860 Wireless
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 1a:df:c0:76:d3:58
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by stuckdoingwork on 2009-10-14
My EEE started acting up again...  this time I think I found a concrete workaround.

I changed my wireless settings (on the router) from 

WPA-PSK [TKIP] + WPA2-PSK [AES] 

to

WPA2-PSK [AES]

I guess the EEE gets confused with the two options :?

And everything worked flawlessly (most of my laptops automatically updated to the configuration; one Vista machine I had to change some preference from 'TKIP' to 'AES' but this was pretty easy)

---

