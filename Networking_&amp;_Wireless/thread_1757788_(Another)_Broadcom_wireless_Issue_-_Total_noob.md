---
title: "(Another?) Broadcom wireless Issue - Total noob"
date: 2011-05-13
forum: Networking &amp; Wireless
---

### Post by Panacco on 2011-05-13
Let me first off apologize for making yet another of these posts. You would think I would find my solution among the million of other posts about similar issues, however I have not, or rather I have not quite understood some of the solutions.

At the very begging of my ubuntu experience (2 days ago) I was able to check the "Enable Wireless" bar up in the top right corner, but I was unable to connect any wireless networks, cause none would show on the list.
Using nm-tool i get this info:

> NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        C8:0A:A9:98:D5:C6

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         85.224.196.57
    Prefix:          22 (255.255.252.0)
    Gateway:         85.224.196.1

    DNS:             195.54.122.199
    DNS:             195.54.122.204


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             unavailable
  Default:           no
  HW Address:        78:E4:00:DD:06:E8

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points The thing is: I have not used Linux for the past 7 years, and basically nothing is the same (cept for the terminal). People write stuff like System > settings, and I honestly have no idea how or where to find this "system"?
So the reason why I am making this post is due to the fact that I am unable to even attempt some of the solutions and guides out there.

Now this is what I've gathered sofar is:

lshw -class network

>   *-network               
       description: Ethernet interface
       product: AR8151 v1.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: c8:0a:a9:98:d5:c6
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=85.224.196.57 latency=0 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:d3400000-d343ffff ioport:2000(size=128)
  *-network DISABLED
       description: Wireless interface
       product: BCM43225 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 78:e4:00:dd:06:e8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:d2400000-d2403fffI also (finally) figured out how to install the damn drivers and hoped that would solve the issue, however it did not. (the propertary drivers that is).

Acer aspire timelinex 4820T
With a Broadcom (BCM43225) - According to the "Additional Drivers" my drivers are installed and working correctly.
Ubuntu 11.04 installed via Wubi. (Windows 7 Home Premium 64-bit)

---

### Post by Panacco on 2011-05-13
Oh and connecting via cable seems to be working with no issues (thats how ive typed all of this!)

---

### Post by josephmills on 2011-05-13
please see post number 44 thanks [http://ubuntuforums.org/showthread.php?t=1748245&page=5](http://ubuntuforums.org/showthread.php?t=1748245&page=5)

---

### Post by Panacco on 2011-05-14
```
nicholas@ubuntu:~$ rfkill list
0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```


this is where I get stuck it seems, nicholas@ubuntu:~$ lsmod | grep b43 simply jumps to the next line with nothing being shown :(

---

### Post by bkratz on 2011-05-14
> **Panacco said:**
> ```
nicholas@ubuntu:~$ rfkill list
0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```


this is where I get stuck it seems, nicholas@ubuntu:~$ lsmod | grep b43 simply jumps to the next line with nothing being shown :(

The reason you are seeing no output for that command is that you are using  the STA driver (wl) rather than b43.

From above
configuration: broadcast=yes [COLOR="Red"]driver=wl0 driverversion=5.100.82.38[/COLOR] latency=0 multicast=yes wireless=IEEE 802.11

---

### Post by irv on 2011-05-14
With any Broadcom 43xx card if you do these four simple steps it will work.

A fix for the Broadcom BCM43xx driver in 11.04.

1. I uninstalled “bcm-kernel-source” package,

```
sudo apt-get remove bcm-kernel-source
```


2. I installed “firmware-b43-installer” package

```
sudo apt-get install firmware-b43-installer
```

3. I installed “b43-fwcutter” packager

```
sudo apt-get install b43-fwcutter
```

4. I typed into the terminal:

```
 cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl| lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3 |rt6|rt7|witch|wl'
```

---

### Post by josephmills on 2011-05-14
> **Panacco said:**
> ```
nicholas@ubuntu:~$ rfkill list
0: acer-wireless: Wireless LAN
    Soft blocked: **yes**
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```


this is where I get stuck it seems, nicholas@ubuntu:~$ lsmod | grep b43 simply jumps to the next line with nothing being shown :(

the part in bold  is the trouble please try 
```
rfkill unblock all 
```

---

### Post by josephmills on 2011-05-14
> **irv said:**
> With any Broadcom 43xx card if you do these four simple steps it will work.

A fix for the Broadcom BCM43xx driver in 11.04.

1. I uninstalled “bcm-kernel-source” package,

```
sudo apt-get remove bcm-kernel-source
```


2. I installed “firmware-b43-installer” package

```
sudo apt-get install firmware-b43-installer
```

3. I installed “b43-fwcutter” packager

```
sudo apt-get install b43-fwcutter
```

4. I typed into the terminal:

```
 cat /etc/modprobe.d/* | '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl| lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3 |rt6|rt7|witch|wl'
```

what if  the person needs the sta driver and not the fwcutter? also I like the cat modprobe part. is that a list of all the mods that the kernel is having trouble with? Thats what it looks like to me. I could be wrong

---

### Post by Panacco on 2011-05-14
> **josephmills said:**
> the part in bold  is the trouble please try 
```
rfkill unblock all 
```

i did that, still says 'yes'

Im gonna attempt the 4 step suggestion =/

EDIT: The 4 step suggestion ended with a new line coming up, but no info?

---

### Post by Panacco on 2011-05-14
I read somewhere that there seems to be some kind of issue between wubi+ battery power saving functions in windows, apparently ubuntu cant access the wireless cause windows shuts it down when restarting. Ive only found the XP version solutions but not the windows 7 ones. Could that be it?

---

### Post by Panacco on 2011-05-26
well thats it for my ubuntu expirience, it wont work through wubi so i wont even bother trying dualbooting.

---

### Post by nm_geo on 2011-05-26
> **josephmills said:**
> what if the person needs the sta driver and not the fwcutter? also I like the cat modprobe part. is that a list of all the mods that the kernel is having trouble with? Thats what it looks like to me. I could be wrong
 
You are absolutely right Joseph. I built that line from a launchpad help ticket to show people what wireless drivers might be blacklisted. It resolves nothing on it's on. I wish more users with Broadcom drivers would pay attention to your advice. NOT ALL BCM43XXX chipsets use the same driver as you well know.

---

### Post by TBABill on 2011-05-26
> **Panacco said:**
> i did that, still says 'yes'
 
Im gonna attempt the 4 step suggestion =/
 
EDIT: The 4 step suggestion ended with a new line coming up, but no info?
 
That should be done as ```
sudo rfkill unblock all
``` Does that improve things? You will not see an actual output in terminal after you perform that action, just a new line. That's normal. But, you can do a ```
sudo rfkill list 
``` to see if you are still soft blocked or not.

---

### Post by chili555 on 2011-05-26
> NOT ALL BCM43XXX chipsets use the same driver as you well know.Correct! Almost all use either b43/ssb or wl. They are not interchangeable. You can't get your wireless to work if it's claimed by b43/ssb by blacklisting them and installing wl. It just doesn't work that way!!!

Compare the pci.id aliases with modinfo, for example:```
chili@LAPTOP40:~$ modinfo wl | grep 4727
alias:          pci:v000014E4d0000[COLOR="Red"]4727[/COLOR]sv*sd*bc*sc*i*
chili@LAPTOP40:~$ modinfo ssb | grep 4727
chili@LAPTOP40:~$ 

```Hit on wl; no joy on ssb.

I don't know the original poster's pci.id; no one asked for it:```
lspci -nn
```I strongly suspect wl is correct. I also suspect that this will cure his soft-blocked ills:```
sudo rmmod -f acer-wmi
sudo rfkill unblock all
```Is it currently loaded?```
lsmod | grep acer
```

---

### Post by josephmills on 2011-05-26
> **chili555 said:**
> Correct! Almost all use either b43/ssb or wl. They are not interchangeable. You can't get your wireless to work if it's claimed by b43/ssb by blacklisting them and installing wl. It just doesn't work that way!!!

Compare the pci.id aliases with modinfo, for example:```
chili@LAPTOP40:~$ modinfo wl | grep 4727
alias:          pci:v000014E4d0000[COLOR="Red"]4727[/COLOR]sv*sd*bc*sc*i*
chili@LAPTOP40:~$ modinfo ssb | grep 4727
chili@LAPTOP40:~$ 

```Hit on wl; no joy on ssb.

I don't know the original poster's pci.id; no one asked for it:```
lspci -nn
```I strongly suspect wl is correct. I also suspect that this will cure his soft-blocked ills:```
sudo rmmod -f acer-wmi
sudo rfkill unblock all
```Is it currently loaded?```
lsmod | grep acer
```

So what you are saying here is that the acer_wmi is blocking it thats why rfkill unblock is getting us nowhere fast? So it needs to be softblocked so that it can not get in the way anymore. I am 100% with you on the wl part. thanks am  I right?

---

### Post by chili555 on 2011-05-26
> So what you are saying here is that the acer_wmi is blocking it thats why rfkill unblock is getting us nowhere fast? So it needs to be softblocked so that it can not get in the way anymore. I am 100% with you on the wl part. thanks am I right?I am saying that his wireless *MAY* be soft blocked because acer-wmi is not doing its job correctly:> nicholas@ubuntu:~$ rfkill list
0: **acer-wireless**: Wireless LAN
    **Soft blocked: yes**
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: noThere is one quick and easy way to find out, remove the module and try to unblock it. If it kicks the wireless to life, blacklist acer-wmi and add rfkill unblock all to rc.local. If it doesn't work, probe elsewhere for a reason it's soft-blocked.

See how easy this stuff is? Only 9,000 tries and you're home free!

---

### Post by Panacco on 2011-09-04
I'm gonna have another go at this. I'll let you know if it works.

Cheers!

---

### Post by irv on 2011-09-05
> **Panacco said:**
> I'm gonna have another go at this. I'll let you know if it works.

Cheers!

I got frustrated with it the first time I tried Linux but I finely got it going and I am very glad I did. First, I do not like Wubi. Let me make a suggestion. Try the live CD and make sure everything works. Like your Network connection. Then back up all your data from your Windows install before installing Ubuntu. Next. do an Install to your Hard drive and just take the default setting and do a dual boot with Windows and Ubuntu. You will be able to get at all your files in a NTFS partition, and it should not destroy any of your files. I always like to back up in case something goes wrong, and sometimes it does.

I am taking for granted that you have enough room on your hard drive to do this.

---

