---
title: "Wifi stopped working after install?!"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by VanceVEP72 on 2010-10-11
I'll try posting this here.

I have a laptop that was working fine with 10.04 LTS. Today, I did a full 10.10 install and now my wireless is not working. Thinking it had to do with 10.10, I did a full install back to 10.04 LTs. Wireless is still not working. I tried installing the driver for my laptop's internal wifi using ndiswrapper, but that didn't work either. I have another laptop that is identical to the non-working one, with the exception that it is running a Celeron processor and non-Nvidia graphics. Otherwise, they are identical with respect to the wifi adapter. The Celeron machine is giving me absolutely no problems. 

Someone has to have some idea how to get this working?! I'm a complete noob to Ubuntu so please keep that in mind when replying.

Thanks!

---

### Post by P4man on 2010-10-11
Have you tried the hardware killswitch? Make sure its set to on.
Also please provide the output of

```
lspci
```

and

```
lsusb
```

so we can see what hardware you have. 

(copy paste those commands in a terminal, applications > accessories > terminal, and paste the output here).

---

### Post by VanceVEP72 on 2010-10-11
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Processor Link Control
02:00.0 VGA compatible controller: nVidia Corporation C77 [GeForce 8200M G] (rev a2)
07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

---

### Post by VanceVEP72 on 2010-10-11
Bus 004 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by VanceVEP72 on 2010-10-11
...and how do you 'try the hardware kill switch?"

---

### Post by P4man on 2010-10-11
Most laptops have a switch to turn the wifi radio on or off. Ive seen ubuntu get confused about the state of the switch though, maybe you can try running these commands and report the output
```

sudo rfkill unblock all
rfkill list
```

---

### Post by VanceVEP72 on 2010-10-11
vance@AMDAthlonX2Laptop:~$ sudo rfkill unblock all
vance@AMDAthlonX2Laptop:~$ sudo rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by VanceVEP72 on 2010-10-11
OMG! After hours upon hours of Googling and re-installing Ubuntu your two simple command lines did the trick! After re-booting, my laptop found my wireless network and I am wireless again! (knock on wood). Hopefully, nothing will trigger Ubuntu to turn this off again! THANK YOU!!!

---

### Post by P4man on 2010-10-11
Just save that first command somewhere. If it happened once, its bound to happen again. But chances are you can solve it by toggeling the hardware switch or Fn+function key as well.

---

### Post by gialorga on 2010-10-12
Hello....
I have the same problem... I tried using 'ndiswrapper' and I installed the driver for my card (Realtek RTL 8187SE' and at the moment I don't have wireless... My 'eth0' connection works perfectly, but my 'wlan0' connection doesn't work... If I type 'rfkill list' nothing appears.... If I type 'iwconfig', I receive the next message:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Frequency=2.422 GHz  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

The last one is because I installed 'VirtualBox'.... I don't know what is the problem... Can you help me?.... Thanks in advance.....

---

### Post by VanceVEP72 on 2010-10-12
My understanding is that if you have messed around with your wireless configurations through the terminal, you need to undo all your steps and start over or it can cause further complications. I decided to just do a fresh install and then use the rfkill commands. I'm an Ubuntu noob though so I could be wrong.

---

### Post by gialorga on 2010-10-13
Well... I reinstall Ubuntu 10.10... Then I type in the terminal: 'sudo rfkill unblock all', then: 'rfkill list'... and nothing appear:
-------
gilberto@gilberto-ortiz:~$ sudo rfkill unblock all
gilberto@gilberto-ortiz:~$ rfkill list
gilberto@gilberto-ortiz:~$ 
-------

I don't know what to do.... If I type 'iwconfig':

gilberto@gilberto-ortiz:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Frequency=2.422 GHz  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I tried with 'ndiswrapper' but I couldn't connect my wireless...

Please, somebody help me...

---

### Post by VanceVEP72 on 2010-10-13
> Well... I reinstall Ubuntu 10.10... Then I type in the terminal: 'sudo rfkill unblock all', then: 'rfkill list'... and nothing appear:
 
 
Nothing will appear in the terminal after running those commands.

---

### Post by gialorga on 2010-10-13
So... what's the matter?... I don't have wireless.... Or my device (Realtek RTL8187SE) isn't supported yet?...  Help me....

---

### Post by VanceVEP72 on 2010-10-13
I would start by posting the results of > lspci and > lsusb here. Also, double-check that your wifi switch is turned on. You may have already checked it out, but this site may be of some help: [http://rtl-wifi.sourceforge.net/wiki/Main_Page](http://rtl-wifi.sourceforge.net/wiki/Main_Page)

---

