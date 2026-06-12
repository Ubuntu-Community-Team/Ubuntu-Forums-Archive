---
title: "Can't connect to wireless networks"
date: 2011-09-11
forum: Networking &amp; Wireless
---

### Post by Groescht on 2011-09-11
I have a Dell Inspiron 1545 laptop.  I had to hard shutdown my computer because it froze.  When it had restarted I am unable to connect to my wireless networks.  "enable wireless" is greyed out.  And it says "wireless networks are disabled by hardware switch".  There is a button that turns on and off accessing wireless networks. I have pushed it to no avail.  Any help would be GREATLY appreciated.

---

### Post by Groescht on 2011-09-11
bump

---

### Post by Groescht on 2011-09-11
Trolled forums.  Tried a bunch of stuff and got it fixed. If anyone else has this problem I recommend going here: [http://ubuntuforums.org/showthread.php?t=1559025](http://ubuntuforums.org/showthread.php?t=1559025)

---

### Post by fdrake on 2011-09-11
do you have a switcher  that lets you turn off/on the wifi antenna somwhere? it may be a combination of keys too. make sure you check the txt on the hardware first. if that does not work run these command sin the terminal:
```

iwconfig
sudo lshw -c Network
rfkill list all

```

---

### Post by akshaypande1989 on 2011-09-12
Hi fdrake,

I am facing a similar problem:

I am using Ubuntu 10.4 AMD64 on an ASUS EEE PC 1201T, I do not have other operating systems. Linux can detect my wireless hardware as shown by the output of lshw -C network

```
PCI (sysfs) 
  *-network DISABLED     
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 48:5d:60:b1:10:50
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.32-34-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:fbef0000-fbefffff
```

I've downloaded the needed driver from this URL [https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285](https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285) but my network is still disabled.

My computer is up to date already (I've checked in Update Manager). 

My wireless switch is Fn+F2 but it isn't working.

Do help!

Warmly
Akshay Pande

---

### Post by fdrake on 2011-09-12
can u post the results for the commands in post #4(especially the last one)

---

### Post by akshaypande1989 on 2011-09-12
iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

sudo lshw -C network
```

 *-network DISABLED      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 48:5d:60:b1:10:50
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.32-34-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:fbef0000-fbefffff
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: bc:ae:c5:42:06:0b
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI duplex=full firmware=N/A ip=10.156.0.228 latency=0 link=yes multicast=yes port=twisted pair speed=10MB/s
       resources: irq:26 memory:fbfc0000-fbffffff ioport:ec00(size=128)

```

rfkill list all

```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```

---

### Post by fdrake on 2011-09-12
```

0: phy0: Wireless LAN
    Soft blocked: no
   [COLOR="Red"]**_ Hard blocked: yes_**[/COLOR]

```

your switch is OFF you have to change it to ON.
Try to changed it and run the command "rfkill list all" untill you see "Hard blocked: no". Try to do it several times. There is nothing wrong with the driver/os.
try also this:studdown the laptop, unplugging the power AC, take out the battery for 1 min and put everything back and restart.

---

### Post by akshaypande1989 on 2011-09-12
Dear fdrake,

I followed your advice and tried switching my wireless on during an Ubuntu session and also during the BIOS page on startup, but it isn't switching on. When I right click the network icon, the "Enable Wireless" checkbox option is greyed out and not clickable.

On Windows I could have switched it on but I don't have Windows anymore and neither can install it.

Is there something else I could try? Maybe something BIOS related?

Warmly
Akshay Pande

---

### Post by akshaypande1989 on 2011-09-12
PROBLEM SOLVED!!

I went to my BIOS settings on Startup, chose the **Advanced **tab and then went to **Onboard devices configuration. **I saw there that the wireless and bluetooth were disabled. So I enabled them!

Now the light is on and **rfkill list all** says
```

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

Thank you so much!! Your advice inspired me to go to the BIOS settings because I had a BIOS related problem earlier where I was advised to do what you said - i.e. disconnect all peripherals and let everything cool down.

---

### Post by fdrake on 2011-09-12
congrats I am happy for you!:popcorn:

---

### Post by davenlin19 on 2013-03-14
Hello fdrake,
I typed rfkill list all, and it displayed:
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

I can't find wireless or smt like that, but i have already installed broadcom :(
Please help me.

---

### Post by wildmanne39 on 2013-03-14
Old thread closed! Please start a new thread.
Thanks

---

