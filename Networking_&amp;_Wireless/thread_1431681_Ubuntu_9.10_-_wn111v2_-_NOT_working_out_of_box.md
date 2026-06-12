---
title: "Ubuntu 9.10 - wn111v2 - NOT working out of box"
date: 2010-03-16
forum: Networking &amp; Wireless
---

### Post by sublimewb on 2010-03-16
Thank you ahead of time for all the help.  Using Ubuntu 9.10 (Kernel 2.6.31-20-generic i686) on Sun's VirtualBox and attaching the NetGear Rangemax adapter (wn111v2) as a USB device.  It is the Atheros AR9001U flavor.  It is recognized in ubuntu as being attached via USB but that is it.  Not seen in ifconfig/iwconfig.  Any help would be appreciated..I have read everywhere on this and nobody seems to have the same problem I do.  BTW, ndiswrapper is NOT an option, I want to use the native drivers which I know are included with 9.10.  Here are some output snippets:

**lsusb**
```
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0846:9001 NetGear, Inc. WN111(v2) RangeMax Next Wireless [Atheros AR9001U-(2)NG]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


**ifconfig -a**
```
eth0      Link encap:Ethernet  HWaddr 08:00:27:b2:62:97                                              
          inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:feb2:6297/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1656 (1.6 KB)  TX bytes:5359 (5.3 KB)
          Interrupt:10 Base address:0xd020

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
```


**lsmod** *(You can see pieces of it here!)*
```
Module                  Size  Used by
vboxvideo               2044  2      
drm                   160032  3 vboxvideo
agpgart                34988  1 drm      
binfmt_misc             8356  1          
vboxvfs                34952  0          
snd_intel8x0           30168  2          
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0               
snd_mixer_oss          16028  1 snd_pcm_oss   
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0                                        
snd_seq_oss            28576  0                                        
snd_seq_midi            6464  0                                        
snd_rawmidi            22176  1 snd_seq_midi                           
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi               
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iptable_filter          3100  0                                                          
ip_tables              11692  1 iptable_filter                                           
x_tables               16544  1 ip_tables                                                
ppdev                   6688  0                                                          
snd_timer              22276  2 snd_pcm,snd_seq                                          
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ar9170usb              46240  0
mac80211              181140  1 ar9170usb
led_class               4096  1 ar9170usb
ath                     8060  1 ar9170usb
cfg80211               93052  3 ar9170usb,mac80211,ath
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                56500  0
serio_raw               5280  0
i2c_piix4               9932  0
vboxguest             148104  8 vboxvfs
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
parport_pc             31940  0
lp                      8964  0
parport                35340  3 ppdev,parport_pc,lp
pcnet32                32644  0
mii                     5212  1 pcnet32
```


**dmesg**
*(Edited down to interesting part, maybe someone knows what this means for me.)*
*(Error code -110?)*
```
[    0.977654] usbcore: registered new interface driver usbfs                                                                                    
[    0.978184] usbcore: registered new interface driver hub                                                                                      
[    0.978384] usbcore: registered new device driver usb                                                                                                                                          
[    2.021222] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver                                                                        
[    2.023961] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10                                                                                 
[    2.023991] PCI: setting IRQ 10 as level-triggered                                                                                            
[    2.024017] ehci_hcd 0000:00:0b.0: PCI INT A -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10                                                   
[    2.024210] ehci_hcd 0000:00:0b.0: setting latency timer to 64                                                                                
[    2.024273] ehci_hcd 0000:00:0b.0: EHCI Host Controller                                                                                       
[    2.024599] ehci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1                                                              
[    2.039701] ehci_hcd 0000:00:0b.0: irq 10, io mem 0xf0805000                                                                                  
[    2.051768] ehci_hcd 0000:00:0b.0: USB 2.0 started, EHCI 1.00                                                                                 
[    2.065518] usb usb1: configuration #1 chosen from 1 choice                                                                                   
[    2.069848] hub 1-0:1.0: USB hub found                                                                                                        
[    2.073660] hub 1-0:1.0: 8 ports detected                                                                                                     
[    2.074422] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver                                                                            
[    2.075362] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11                                                                                 
[    2.075442] PCI: setting IRQ 11 as level-triggered                                                                                            
[    2.075511] ohci_hcd 0000:00:06.0: PCI INT A -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11                                                   
[    2.075680] ohci_hcd 0000:00:06.0: setting latency timer to 64                                                                                
[    2.075728] ohci_hcd 0000:00:06.0: OHCI Host Controller                                                                                       
[    2.075917] ohci_hcd 0000:00:06.0: new USB bus registered, assigned bus number 2                                                              
[    2.076604] ohci_hcd 0000:00:06.0: irq 11, io mem 0xf0804000                                                                                  
[    2.136363] usb usb2: configuration #1 chosen from 1 choice                                                                                   
[    2.136442] hub 2-0:1.0: USB hub found                                                                                                        
[    2.139318] hub 2-0:1.0: 8 ports detected                                                                                                     
[    2.146556] uhci_hcd: USB Universal Host Controller Interface driver                                                                                                                                                                     
[    2.406228] usb 1-1: new high speed USB device using ehci_hcd and address 2                                                                                                                     
[    3.139662] usb 1-1: configuration #1 chosen from 1 choice                                                                                                            
[   14.205256] usb 1-1: reset high speed USB device using ehci_hcd and address 2                                                                 
[   17.191046] usb 1-1: firmware: requesting ar9170.fw
[   18.373958] usb 1-1: USB setup failed (-110).
[   18.388540] ar9170usb: probe of 1-1:1.0 failed with error -110
[   18.388786] usbcore: registered new interface driver ar9170usb
```


**sudo lshw -C network** - This only shows the ethernet NIC.

Thanks again everyone.  Beginner to Linux in general so I only know the basics and a few sneaky tricks, but any more info I can provide let me know.

---

### Post by sublimewb on 2010-03-16
**Update:** After reading my own post I see under dmesg that it looks like it is trying to load the following:

**[   17.191046] usb 1-1: firmware: requesting ar9170.fw**

But my wn111v2 is the Atheros 9001U? Does that matter? Does that firmware work for both wn111v2's?

Another thought, is this a vendor ID problem?

I'm so lost.

---

### Post by sublimewb on 2010-03-17
bump...Nobody has any ideas? I see this forum is inundated with requests. :(  Any help would be appreciated.  Possibly a VirtualBox USB emulation problem?  Thanks folks....

---

### Post by chili555 on 2010-03-17
> ID [COLOR="Blue"]0846:9001[/COLOR] NetGear, Inc. WN111(v2)> $ modinfo ar9170usb | grep 9001
alias:          usb:v[COLOR="Blue"]0846[/COLOR]p[COLOR="Blue"]9001[/COLOR]d*dc*dsc*dp*ic*isc*ip*The module ar9170usb is correct for your device. It requires firmware, as you have learned. If you can connect the computer to an ethernet cable and get a connection, please do:```
sudo apt-get install linux-firmware
```Detach the ethernet cable. Unplug the Netgear, wait just a few moments and plug it back in. Enjoy your new wireless!

---

### Post by sublimewb on 2010-03-18
Thank you for the response, unfortunately that didn't do it.  I am using Ubuntu 9.10 so I already have the ar9170.fw installed. (I tried your suggestion anyhow and it just said:

```
linux-firmware is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
```

I'm back to square one. :(  What is the following from dmesg mean?

```
usb 1-1: firmware: requesting ar9170.fw
usb 1-1: USB setup failed (-110).
ar9170usb: probe of 1-1:1.0 failed with error -110
usbcore: registered new interface driver ar9170usb
```

It seems to be the error that is killing me perhaps.

---

### Post by sublimewb on 2010-03-18
some more info for any Linux Wireless sleuths out there ready to help me :)

Doing a [B]cat /var/log/messages | grep ar9170
[/B] turns up this tidbit...

```
usb 1-1: firmware: requesting ar9170.fw
ar9170usb: probe of 1-1:1.0 failed with error -110
usbcore: registered new interface driver ar9170usb

```


Doing a **modprobe -l *9170*** returns this...

```
kernel/drivers/net/wireless/ath/ar9170/ar9170usb.ko
```


So my driver is loaded, the firmware is found... Doing a modinfo of the driver displays the device id for my dongle that matches the lsusb id. But yet ifconfig and iwconfig return nothing.  This is baffling.  I know one of you wizards out there will solve this in a split second.  I am just waiting for you to arrive on the scene. :)


Thanks again anyone.......any help much appreciated.

---

### Post by chili555 on 2010-03-18
Ubuntu is the guest OS in a virtual machine? If I have misunderstood, I apologize. I saw this:  [http://communities.vmware.com/thread/244964](http://communities.vmware.com/thread/244964)> Something that doesn't make sense to me is why you are installing a driver for a host-side network adapter inside a guest OS. (Mainly because the USB stuff has caused people nothing but issues such as the one you're experiencing. Personally, I limit the USB functionality in VMware Workstation to only attaching external USB drives to a guest. A communications device is best left at the host layer.)

Don't even bother connecting it to the guest as a USB device. You should be able to get network access on your guest working through a virtual NIC that uses that same adapter, but on the host side as opposed to inside the guest, without the need to do what you're doing (assuming that I'm understanding correctly what it is that you're doing.)If I am misunderstanding, please help me.

---

### Post by sublimewb on 2010-03-18
Yes, I am in VirtualBox.  I have the shared networking from the host OS working fine, but that isn't the goal.  One, I want to eventually do a hard install onto my laptop but not if the wireless dongle isn't going to work, and two, I want to play with some of the more powerful features of the linux Atheros drivers that cannot be found under Windows.

I have never been one to give up on a tough technology problem and take an easier road if that easier road doesn't give me *exactly* the features I am looking for. :)  Besides, from what I have found poking around, a lot of people seem to have USB dongles working in VirtualBox so it shouldn't be a problem.  I'm not convinced the emulator is causing the problem either.

---

### Post by chili555 on 2010-03-19
> I want to eventually do a hard install onto my laptop but not if the wireless dongle isn't going to work, Have you tried a live CD?

---

### Post by sublimewb on 2010-03-19
Yes didn't work.

I just formatted my Inspiron 4150 laptop and am going to do a real install on that instead of the VirtualBox install.  I guess that will eliminate quite a few variables with trying to get this driver working.  If it works on the laptop after a hard install, then I'll know it is *probably* the virtual machine.  But I do want to get it working on my desktop pc on that virtual machine still.  I guess I'll have to just focus on VirtualBox's USB support and see if anyone has run into any problems.

Any VirtualBox users out there who have had any positive or negative experiences getting wireless dongles working in Linux (or Ubuntu in particular)?

---

### Post by LaJuan on 2010-09-09
I having a different issue with 10.04 on my Dell Inspiron 4150. The wireless work fine in Windows XP but, when I try to use wireless in Ubuntu 10.04, the option to even use wireless is turned off or I can pick it in my connection menu. Any suggestion on what I am doing wrong?

Thanks,

LaJuan

---

### Post by dmalsbury on 2011-06-24
my installation of natty 11.04 does not reliably recognise/connect to new wn111v2 usb adapter.
wired works great.

any help would be appreciated.

---

### Post by ether3al on 2011-08-25
I am experiencing same issue here with a Win7 host, Ubuntu 11.04 & BT5 guest machines using a Ubiquiti SR71USB. The drivers are clearly loaded but still the interface is unavailable. 

This type of install should work as I have seen it done with the Alpha wireless USB card and the SR71 works fine on a dedicated install of Ubuntu.

---

### Post by bigwillaye on 2012-03-20
> **dmalsbury said:**
> my installation of natty 11.04 does not reliably recognise/connect to new wn111v2 usb adapter.
wired works great.

any help would be appreciated.

> **ether3al said:**
> I am experiencing same issue here with a Win7 host, Ubuntu 11.04 & BT5 guest machines using a Ubiquiti SR71USB. The drivers are clearly loaded but still the interface is unavailable. 

This type of install should work as I have seen it done with the Alpha wireless USB card and the SR71 works fine on a dedicated install of Ubuntu.


Same issue - natty 11.04, drivers loaded and fine, interface unavailable. Any ideas??

---

