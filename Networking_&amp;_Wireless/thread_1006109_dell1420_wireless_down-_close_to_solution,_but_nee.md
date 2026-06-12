---
title: "dell1420 wireless down- close to solution, but need help"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by DaviswhoisDavis on 2008-12-09
Hello,

My wireless went down after my last upgrade.  I have an intel3945 wireless card.  After some looking around I have found a page which describes what is going on. 

[https://help.ubuntu.com/community/WifiDocs/Driver/iwlwifi_Intel_3945_4965/gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/iwlwifi_Intel_3945_4965/gutsy)

It tells me to delete a couple of lines of code in one place and add others in another, and then use some sudo commands.  

I don't know how to delete or install lines of code, so I'm stuck.

I'll keep searching for answers on the reticulum, but if anybody can help I'd appreciate it.  Thanks.

Davis

---

### Post by Tilex on 2008-12-09
> I don't know how to delete or install lines of code, so I'm stuck.


If you're in Gnome, you can type in:
```
sudo gedit filename.txt
```

If you're in KDE, it'd be:
```
sudo kate filename.txt
```

---

### Post by DaviswhoisDavis on 2008-12-09
That's a good start, Thanks.  I typed in

sudo gedit /etc/udev/rules.d/70-persistent-net.rules.txt

a blank window opened up, I searched for the lines that need to go with no result.  A step by step would be helpful if anybody is willing.

Thanks

---

### Post by Tilex on 2008-12-09
> a blank window opened up, I searched for the lines that need to go with no result. A step by step would be helpful if anybody is willing.

Usually when a blank file pops up is because there is no such file on your system, so it opens up a new (blank) file with the name you provided (70.persistent-net.rules.txt in your case).

Are you sure this file exists on your system?  Make sure you typed it correctly.  You could naviguate to that particular folder by:

```

cd /etc/udev/rules.d/
ls -l

```

and see if the file 70-persistent-net.rules.txt is there.  If the file exists, then the window shouldn't be blank and you would see the lines they're refering to.

---

### Post by DaviswhoisDavis on 2008-12-09
Thanks for that.

I believe I have made some forward progress.

I found the files, deleted what I was supposed to, added what I was supposed to.  Ran the commands and one came back.  This is what it looked like, plus sudo lshw -C network and ifconfig

davis@dell:~$ sudo modprobe -r ipw3945
sh: /sbin/ipw3945d-2.6.22-16-rt: not found

davis@dell:~$ sudo modprobe -r ieee80211
davis@dell:~$ sudo modprobe -r ieee80211_crypt_tkip
davis@dell:~$ sudo modprobe -r ieee80211_crypt_ccmp
davis@dell:~$ sudo modprobe -r ieee80211_crypt_wep
davis@dell:~$ sudo modprobe -r ieee80211_crypt
davis@dell:~$ sudo modprobe -r mac80211
davis@dell:~$ sudo modprobe iwlwifi_mac80211
davis@dell:~$ sudo modprobe iwl3945
davis@dell:~$ sudo modprobe -r ipw3945
sh: /sbin/ipw3945d-2.6.22-16-rt: not found
davis@dell:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:d1:2b:3f
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:a0:ff:6b:04
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 duplex=full ip=192.168.1.108 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
davis@dell:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

It looks like I have a wireless network called wlan0 now, but a wireless option is not showing up in my wireless manager, nor network connection

I shall continue to try follow the directions on the page.  

Thanks

---

### Post by DaviswhoisDavis on 2008-12-09
Success!!!!!!!

The wireless is up and running.  It isn't configured the same way I am used to but it is good for now.  I am travelling in Southeast Asia and this has been plaguing me for days.

---

### Post by Tilex on 2008-12-09
Well awsome then!  Have a good trip!

---

