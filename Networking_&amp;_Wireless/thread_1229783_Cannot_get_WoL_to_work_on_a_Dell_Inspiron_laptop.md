---
title: "Cannot get WoL to work on a Dell Inspiron laptop"
date: 2009-08-02
forum: Networking &amp; Wireless
---

### Post by Gustavo Narea on 2009-08-02
Hello, everyone.

I have a Dell Inspiron 6400 laptop powered by Ubuntu 9.04 and I'm having trouble to get Wake-on-LAN (WoL) to work.

The hardware is as follows:
[LIST]
[*]NIC: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02).
[*]Motherboard: ```
  *-core                                                                                 
       description: Motherboard                                                          
       product: 0KD882                                                                   
       vendor: Dell Inc.                                                                 
       physical id: 0                                                                    
       serial: .H15QMB1.CN486436787979.                                                  
     *-firmware                                                                          
          description: BIOS                                                              
          vendor: Dell Inc.                                                              
          physical id: 0                                                                 
          version: A06 (06/09/2006)                                                      
          size: 64KiB                                                                    
          capacity: 512KiB                                                               
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
```
[/LIST]

In the BIOS there's nothing about WoL, but according to ethtool, it IS supported. I have an script that enables WoL on startup and according to the following output, it's certainly enabled:
```
gustavo@paris:~$ sudo ethtool eth0
Settings for eth0:                
        Supported ports: [ MII ]  
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes                      
        Advertised link modes:  10baseT/Half 10baseT/Full   
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes                    
        Speed: 100Mb/s                                      
        Duplex: Full                                        
        Port: Twisted Pair                                  
        PHYAD: 1                                            
        Transceiver: internal                               
        Auto-negotiation: on                                
        Supports Wake-on: g                                 
        Wake-on: g                                          
        Current message level: 0x000000ff (255)             
        Link detected: yes
```

But no matter how I shut down the computer (e.g., "echo mem > /sys/power/state", "sudo halt", "sudo halt -p", "sudo halt -f -p", "sudo pm-suspend", "sudo pm-hibernate"), it never wakes when I run any of the following commands from another computer in the same home network:
[LIST]
[*]wakeonlan 00:15:c5:a7:f0:19
[*]wakeonlan -p 7 00:15:c5:a7:f0:19
[*]wakeonlan -i 192.168.1.128 00:15:c5:a7:f0:19
[*]wakeonlan -p 7 -i 192.168.1.128 00:15:c5:a7:f0:19
[/LIST]

What else can I try to make Wake-on-LAN work on this computer?

Thanks in advance!

---

### Post by Gustavo Narea on 2009-08-03
OK, I've made some progress: Now at least WoL works on suspend (ACPI mode S3).

Here's what I did:
[LIST=1]
[*]Find the devices that can resume the computer:
```
gustavo@paris:~$ cat /proc/acpi/wakeup
Device  S-state   Status   Sysfs node 
LID       S3    *enabled              
PBTN      S4    *enabled              
PCI0      S3     disabled  no-bus:pci0000:00
USB0      S0     disabled  pci:0000:00:1d.0 
USB1      S0     disabled  pci:0000:00:1d.1 
USB2      S0     disabled  pci:0000:00:1d.2 
USB3      S0     disabled  pci:0000:00:1d.3 
EHCI      S0     disabled  pci:0000:00:1d.7 
AZAL      S3     disabled  pci:0000:00:1b.0 
PCIE      S4     disabled  pci:0000:00:1e.0 
RP01      S4     disabled  pci:0000:00:1c.0 
RP02      S3     disabled                   
RP03      S3     disabled                   
RP04      S3     disabled  pci:0000:00:1c.3 
RP05      S3     disabled                   
RP06      S3     disabled
```
[*]Find which of those devices is my Ethernet card:
```
gustavo@paris:~$ lspci -tv
-[0000:00]-+-00.0  Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
           +-02.0  Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller    
           +-02.1  Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
           +-1b.0  Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller                  
           +-1c.0-[0000:0b]----00.0  Broadcom Corporation BCM4311 802.11b/g WLAN                            
           +-1c.3-[0000:0c-0d]--                                                                            
           +-1d.0  Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1                            
           +-1d.1  Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2                            
           +-1d.2  Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3                            
           +-1d.3  Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4                            
           +-1d.7  Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller                              
           **+-1e.0-[0000:03]--+-00.0  Broadcom Corporation BCM4401-B0 100Base-TX**                             
           |                 +-01.0  Ricoh Co Ltd R5C832 IEEE 1394 Controller                               
           |                 +-01.1  Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter                  
           |                 +-01.2  Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter                      
           |                 \-01.3  Ricoh Co Ltd xD-Picture Card Controller                                
           +-1f.0  Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge                                 
           +-1f.2  Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller                         
           \-1f.3  Intel Corporation 82801G (ICH7 Family) SMBus Controller
```
[*]Enable it for WoL (it is "PCIE" in my case):
```
sudo sh -c "echo PCIE > /proc/acpi/wakeup"
```
[/LIST]

Then it should be enabled for WoL:
```
gustavo@paris:~$ cat /proc/acpi/wakeup
Device  S-state   Status   Sysfs node
LID       S3    *enabled
PBTN      S4    *enabled
PCI0      S3     enabled   no-bus:pci0000:00
USB0      S0     disabled  pci:0000:00:1d.0
USB1      S0     disabled  pci:0000:00:1d.1
USB2      S0     disabled  pci:0000:00:1d.2
USB3      S0     disabled  pci:0000:00:1d.3
EHCI      S0     disabled  pci:0000:00:1d.7
AZAL      S3     disabled  pci:0000:00:1b.0
**PCIE      S4     enabled   pci:0000:00:1e.0**
RP01      S4     disabled  pci:0000:00:1c.0
RP02      S3     disabled
RP03      S3     disabled
RP04      S3     disabled  pci:0000:00:1c.3
RP05      S3     disabled
RP06      S3     disabled
```

Finally, suspend it:
```
sudo pm-suspend
```

And "wake" it from another device on your network:
```
wakeonlan -i *[COLOR="DarkOrange"]$IP-Address-Of-Your-Suspended-Computer[/COLOR]* *[COLOR="Navy"]$MAC-Address-Of-Your-NIC[/COLOR]*
```

Now [the challenge is to make it work with hibernation and soft off]("http://ubuntuforums.org/showthread.php?t=1229783").

HTH.

---

### Post by megamania on 2009-08-03
> **Gustavo Narea said:**
> Hello, everyone.

I have a Dell Inspiron 6400 laptop powered by Ubuntu 9.04 and I'm having trouble to get Wake-on-LAN (WoL) to work.

I know very little about wake on lan, but I was looking into it (want to set it up myself) and as far as I know, you should:

run "ethtool -s eth0 wol g" to enable the wake-on-magic-packet on the computer that you want to wake up remotely.

run "etherwake [macaddress]" from another computer to wake the computer.

I also think you have to run "ethtool -s eth0 wol g" every time you turn on your computer, otherwise it will only wake up once (in other words that setting is volatile).

As I said, this can be inaccurate because I just started looking into it myself. However, I hope it can help somehow.

EDIT: seen you're making progress... never mind

---

