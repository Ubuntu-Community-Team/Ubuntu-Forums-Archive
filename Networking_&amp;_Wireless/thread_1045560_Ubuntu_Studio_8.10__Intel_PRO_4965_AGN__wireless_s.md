---
title: "Ubuntu Studio 8.10 | Intel PRO 4965 AGN | wireless setup"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by bbr_505 on 2009-01-20
Hey all,

my setup is an HP dv6500 with a fairly standard (on these models at least) Intel PRO 4965 AGN wireless card, NVidia 8400 M GS graphics, 64bit architecture, 4GB RAM.
i had been running a few linux distros through vmware player before i decided what to stick with permanently, so i settled on Ubuntu Studio (as opposed to Ubuntu and gnome/KDE openSUSE).

my problem: wireless doesn't work out of the box. 
[FONT="Fixedsys"]sudo lshw -C network[/FONT] tells me all entries are DISABLED. the troubleshooting guide tells me that the wireless card needs to be on (ie via hardware switch) and it is. i tried the same command with the switch on and off and there is no difference in the output.
my understanding is that my card is supported out of the box, and i would rather not use ndiswrapper to get this working (i hope i dont have to)

the biggest annoyance right now is having to access the internet by rebooting into vista and then going back and trying whatever suggestions you may have, so ill try and get one of my roommates laptops and have them side by side.

let me know what else i should be posting to help solve this problem.

cheers

---

### Post by bbr_505 on 2009-01-20
[FONT="System"]02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
        Subsystem: Intel Corporation Device 1100
        Flags: fast devsel, IRQ 16
        Memory at f4000000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: iwlagn
        Kernel modules: iwlagn

bobo@fuzzies:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


bobo@fuzzies:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.
[/FONT]

Network Tools lists loopback interface as the only device.

---

### Post by bbr_505 on 2009-01-20
bump?

i also cant get an internet connection through a cable and thus no way to run the updates...any ideas?

---

### Post by bbr_505 on 2009-01-21
Managed to get wired working so i ran the updates. Wireless still a no go. 
lwlist scan returns no results.

---

### Post by bbr_505 on 2009-01-21
here is the output for iwconfig
```
bobo@fuzzies:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

here is the output for sudo lshw -C network

```
bobo@fuzzies:~$ sudo lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:f1:46:d1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:24:d2:54:ef
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.125 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 02:f1:72:76:81:bc
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

output for sudo iwlist scan
```

bobo@fuzzies:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

pan0      Interface doesn't support scanning.
```

my wireless card/bluetooth switch is on
i will check to see if there is a bios option for having the wireless card always on and post that soon.

this is making some progress especially because i dont have to reboot into vista to check the forums. thanks in advance to those who are keeping an eye on the thread and looking forward to suggestions.

---

### Post by floatingpoint on 2009-01-22
bump, similar problem with wireless on UbuStu 8.10. Network configuration isn't even listed in the menus.

---

### Post by skit on 2009-01-24
Same problem here.

---

### Post by thpc14 on 2009-02-15
I have the same problem too.

---

### Post by freddyspam on 2009-02-20
So this might work as a temp fix. I've had issues before the wireless card thinking the hardware switch is set to disabled no matter what I do. Doing this worked for my mini pci card. By taping over (insulating) pin #13 "silent rf", it tricks the laptop into thinking the wireless hardware switch is set to on.  
 
For mini pci express, it is pin #20, which is located on the underside, second pin from the notch toward the side with more pins.  
 
I haven't tried it for a pci express mini card, but I'd imagine it'd have the same effect. 

As I don't use the hardware switch, this was an acceptable mod for me.

---

### Post by urs4edal on 2009-04-03
> **bbr_505 said:**
> 

output for sudo iwlist scan
```

bobo@fuzzies:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

pan0      Interface doesn't support scanning.
```

my wireless card/bluetooth switch is on
i will check to see if there is a bios option for having the wireless card always on and post that soon.

this is making some progress especially because i dont have to reboot into vista to check the forums. thanks in advance to those who are keeping an eye on the thread and looking forward to suggestions.


I noticed that next to your wlan0 interface it says that Network is down.  You could try:

sudo ifconfig wlan0 up
sudo iwlist wlan0 scan

Not sure if this will help or not.

---

### Post by dasme on 2009-04-06
> **bbr_505 said:**
> Hey all,

my setup is an HP dv6500 with a fairly standard (on these models at least) Intel PRO 4965 AGN wireless card, NVidia 8400 M GS graphics, 64bit architecture, 4GB RAM.
i had been running a few linux distros through vmware player before i decided what to stick with permanently, so i settled on Ubuntu Studio (as opposed to Ubuntu and gnome/KDE openSUSE).

my problem: wireless doesn't work out of the box. 
[FONT="Fixedsys"]sudo lshw -C network[/FONT] tells me all entries are DISABLED. the troubleshooting guide tells me that the wireless card needs to be on (ie via hardware switch) and it is. i tried the same command with the switch on and off and there is no difference in the output.
my understanding is that my card is supported out of the box, and i would rather not use ndiswrapper to get this working (i hope i dont have to)

the biggest annoyance right now is having to access the internet by rebooting into vista and then going back and trying whatever suggestions you may have, so ill try and get one of my roommates laptops and have them side by side.

let me know what else i should be posting to help solve this problem.

cheers

Hi, same configuration here, But i didn't had any problem with wi-fi it was detected automatically after installation. But the driver performance is not that good. I checked broadband speed on speedbit.com and it gave me 0.8 MB/s but with ethernet it gives me 1.3MB/s. [COLOR="Red"](if any1 knows fix for this pls let me know)[/COLOR]

and one more thing the sound output is very low as compared to vista. (Realtek ALC268 ).

tc
Sa

---

### Post by DarkPi on 2009-04-25
Hey folks,

Just had the same problem 15 min ago, but after quick google found a solution:

I guess you all missing the driver for [FONT=Arial][SIZE=2]Intel® Wireless WiFi Link 4965AGN, so here you are - 

[http://www.intellinuxwireless.org/?p=iwlwifi](http://www.intellinuxwireless.org/?p=iwlwifi)

download a driver from the site mentioned above and install it by typing 

[FONT=Courier New]sudo cp iwlwifi-4965-2.ucode /lib/firmware[/FONT]
[/SIZE][/FONT]

---

