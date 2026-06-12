---
title: "Wireless down after using Aircrack"
date: 2011-10-08
forum: Networking &amp; Wireless
---

### Post by trunk on 2011-10-08
Hey so Ive been toying around with programs such as caine & able, wireshark, WEPcracker, and aircrack-ng recently. I tried to run WEPcracker and aircrack-ng synonymously when my wireless connection cut out. After looking at aircrack's website I realized my wireless card, which is an Ralink 5390, wasn't supported for airdump, I'm not sure whether this is what caused the problem but it seems too coincidental. I tried to reinstall the wireless driver to see if that would do anything but to no avail. Any help would be greatly appreciated since it seems that I'm in over my head on this one! :)
 
EDIT: I just reinstalled the OS and drivers so now it works.

---

### Post by Dangertux on 2011-10-08
Your wireless card is probably still in monitor mode. You should put it back in managed mode using the following command

```

sudo iwconfig wlan0 mode managed

```

Where wlan0 = your wireless interface.

hope that thelps.

---

### Post by trunk on 2011-10-09
[U]K lemme try that thanks :)
[/U]

---

### Post by trunk on 2011-10-09
Mmm it didn't seem to do anything

---

### Post by Dangertux on 2011-10-09
Can you post the output of the following commands please.

```

rfkill list

```

```

iwconfig

```

```

ifconfig

```

```

lscpi

```

Thanks

---

### Post by trunk on 2011-10-09
[B]rfkill list:
[/B]there was no output

[B]iwconfig:
[/B]lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr: off   Fragment thr: off
          Encryption key: off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[B]

ifconfig:
[/B]eth0      Link encap:Ethernet  HWaddr 10:1f:74:0b:43:e9  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::121f:74ff:fe0b:43e9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:226725 errors:0 dropped:0 overruns:0 frame:0
          TX packets:121742 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:326422952 (326.4 MB)  TX bytes:10528596 (10.5 MB)
          Interrupt:40 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:208 errors:0 dropped:0 overruns:0 frame:0
          TX packets:208 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15456 (15.4 KB)  TX bytes:15456 (15.4 KB)

ra0       Link encap:Ethernet  HWaddr 38:59:f9:3a:b5:bd  
          inet6 addr: fe80::3a59:f9ff:fe3a:b5bd/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 
[B]
lscpi:
[/B]No command 'lscpi' found, did you mean:
 Command 'lscpu' from package 'util-linux' (main)
 Command 'lscp' from package 'nilfs-tools' (universe)
 Command 'lspci' from package 'pciutils' (main)
lscpi: command not found

---

### Post by Dangertux on 2011-10-09
Sorry that last command should have been lspci not lscpi, it's late here :-P

It seems that your card is not associated with the access point. Have you tried reconnecting via network manager or wicd? 

Also did you kill network manager? You can try restarting network manager by doing the following

```

sudo /etc/init.d/network-manager restart

```

That might help. I will be back around to this post tomorrow morning, but I have to go to bed. Hopefully you can find your answer before then.

---

### Post by trunk on 2011-10-09
I have tried to reconnect through network manager but it doesnt even give me the option too and after restarting it recognized my ethernet connection but not my wifi card :( Thanks for all the help so far though :)

---

