---
title: "wireless problem on an acer travelmate 2700, Inprocomm IPN2220 not working"
date: 2013-08-11
forum: Networking &amp; Wireless
---

### Post by ramon71 on 2013-08-11
Hi guys, 
i installed xubuntu 13.04 on an acer travelmate 2700 (P4 1gb), while the wired ethernet works perfectly i am not able to make the wireless interface work (it is a inprocomm IPN2220), it's not even shown in the ifconfig command output wich shows only eth0 interface (the wired ethernet), i installed ndiswrapper via synaptic package manager and the windows drivers for the cars, additionally, ndisgtk tells me the hardware is recognized, any suggestion?

---

### Post by varunendra on 2013-08-11
Please follow the "Wireless Script" link in my signature, follow the instructions in the linked post to download and run the script, and post back the "wireless-info.txt" file or its contents in your next post. Thanks !

---

### Post by ramon71 on 2013-08-11
thanks for the attention, here's the output for the commands you requested

---

### Post by chili555 on 2013-08-11
I don't know how late it is in Varun's home, but I think he'll want to draw your attention to:> ndiswrapper (check_nt_hdr:147): [COLOR="#FF0000"]kernel is 32-bit, but Windows driver is not 32-bit;bad magic[/COLOR]: 020BHe'll ask where you got the .inf and .sys files.

---

### Post by varunendra on 2013-08-11
> **chili555 said:**
> I don't know how late it is in Varun's home

9:53 pm only :) , but I have to prepare for a class in the morning (temporarily working as a "fill-in" teacher for a few days). So.. thread's all yours doc ! :)

---

### Post by praseodym on 2013-08-11
Please check the attached 64bit driver with ndiswrapper.

---

### Post by chili555 on 2013-08-11
> **praseodym said:**
> Please check the attached 64bit driver with ndiswrapper.Oooops!! He actually needs the 32-bit.> kernel is 32-bit, 

---

### Post by praseodym on 2013-08-11
32bit is also included ;)

---

### Post by ramon71 on 2013-08-11
thanks guys, il look for the 32 bit version, my fault, please consider i'm quite noob ;)

---

### Post by ramon71 on 2013-08-11
PS: i hate that windows stuff ;)

---

### Post by ramon71 on 2013-08-11
thanks praseodym for the correct drivers, il close the topic if it works

---

### Post by chili555 on 2013-08-11
> **ramon71 said:**
> thanks guys, il look for the 32 bit version, my fault, please consider i'm quite noob ;)Look in post #6 above. Our experts have attached just for you!

---

### Post by ramon71 on 2013-08-11
and obviously meanwhile thanks to varunendra and all who replied this post[SIZE=4][COLOR=#dd4814] [/COLOR][/SIZE]

---

### Post by varunendra on 2013-08-11
You're most welcome !

I'm glad the 'real experts' joined us in time, and I'm sure the problem has no place to hide now in their presence.. :)

---

### Post by ramon71 on 2013-08-12
still not working, it keeps asking for auth, the device is now correctly detected, i'll post updated results from your script asap (i'm away from home now and i do not have access to my machines)

---

### Post by ramon71 on 2013-08-12
here's the new output from the wireless script, again thanks in advance for the time spent:

---

### Post by praseodym on 2013-08-12
Unplug the cable and run the script again. Please show additionally
```

ndiswrapper -l
cat /etc/modprobe.d/ndiswrapper.conf
```

---

### Post by ramon71 on 2013-08-12
```

ndiswrapper -l

ipn2220_x32ntw2000_mod : driver installed
    device (17FE:2220) present

cat /etc/modprobe.d/ndiswrapper.conf

alias pci:v000017FEd00002220sv00000305sd00001468bc*sc*i* ndiswrapper
alias pci:v000017FEd00002220sv00000310sd00001468bc*sc*i* ndiswrapper
alias pci:v000017FEd00002220sv00002220sd000017FEbc*sc*i* ndiswrapper
alias pci:v000017FEd00002220sv*sd*bc*sc*i* ndiswrapper

```

and here's the output from the script, executed with the cable unplugged, thanks for the attention praseodym

---

### Post by praseodym on 2013-08-12
There are no nameservers in your /etc/resolv.conf:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo /etc/init.d/networking restart
sudo service network-manager restart
```
Check:
```

iwconfig
ifconfig -a
route -n
sudo iwlist scan
iwlist chan
dmesg | grep ndis
```
In that driver package there is another 32 bit driver (2 for 32 and 64bit, respectively)

---

### Post by ramon71 on 2013-08-12
here's the output for the commands you requested, after trying with little success to add manually google DNS to resolv.conf (wich btw was followed a quite immediate crash of the network manager) anyway, restarting the machine and executing the commands with the cable unplugged i got these results:

```

el@nemesis:~$ iwconfig
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:0 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

el@nemesis:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:5f:70:51  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:580 errors:0 dropped:0 overruns:0 frame:0
          TX packets:599 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:564129 (564.1 KB)  TX bytes:97647 (97.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:230 errors:0 dropped:0 overruns:0 frame:0
          TX packets:230 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20857 (20.8 KB)  TX bytes:20857 (20.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0e:9b:9e:85:e4  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Memory:e8200000-e8200800 

el@nemesis:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
el@nemesis:~$ sudo iwlist scan
wlan0     No scan results

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

el@nemesis:~$ iwlist chan
wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Channel:0

lo        no frequency information.

eth0      no frequency information.

el@nemesis:~$ dmesg | grep ndis
[   15.262253] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[   16.209089] ndiswrapper: driver ipn2220_x32ntw2000_mod (INPROCOMM,02/24/2005,3.07.02.2005) loaded
[   16.244843] ndiswrapper: using IRQ 18
[   16.444953] usbcore: registered new interface driver ndiswrapper
[   23.848329] ndiswrapper (iw_set_ap_address:677): setting AP mac address failed (C0010015)
[  216.037438] ndiswrapper (iw_set_ap_address:677): setting AP mac address failed (C0010015)


```

i believe i'll try again both drivers included in the package you attached earlier...

---

### Post by ramon71 on 2013-08-13
tried even th 98/me driver i was previously using the NT one, but no progress, i'm starting to think it's an hw problem, never tried windows so i cant tell if it works under windows, will try using a Mint installation i have on the side of the main xubuntu, suggestions are still welcome

---

