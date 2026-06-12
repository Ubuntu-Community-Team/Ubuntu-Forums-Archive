---
title: "Cisco aironet 340 on Ubuntu 5.1"
date: 2006-02-22
forum: Networking &amp; Wireless
---

### Post by ymeng on 2006-02-22
I am a newbie. I have a Dell Latitude running Ubuntu 5.1. I plugged in Cisco aironet 340.  I use WEP on my router. I entered my system id and my key (hexadecimal) using "Network Settings", and selected DHCP.

I am pretty much lost after that. I don't have a connection, unless I plug in my network cable.

I ran a couple of commands and pasted results below, I couldn't tell what's wrong. Can someone tell me what I need to do?

Thanks.
================
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"mysid"
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:0F:66:C3:7D:E9
          Bit Rate:5.5 Mb/s   Tx-Power=15 dBm   Sensitivity=0/65535
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-40 dBm  Noise level=-100 dBm
          Rx invalid nwid:93  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:41   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:"mysid"
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:0F:66:C3:7D:E9
          Bit Rate:5.5 Mb/s   Tx-Power=15 dBm   Sensitivity=0/65535
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-40 dBm  Noise level=-100 dBm
          Rx invalid nwid:93  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:41   Missed beacon:0

================
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:03:8D:F0:01
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:3ff:fe8d:f001/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5327 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8294068 (7.9 MiB)  TX bytes:642818 (627.7 KiB)
          Interrupt:11 Base address:0xd400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:42064 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42064 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3142746 (2.9 MiB)  TX bytes:3142746 (2.9 MiB)

wifi0     Link encap:UNSPEC  HWaddr 00-40-96-2A-0A-9E-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:2312  Metric:1
          RX packets:22 errors:8 dropped:0 overruns:0 frame:8
          TX packets:0 errors:1 dropped:0 overruns:0 carrier:0
          collisions:16 txqueuelen:100
          RX bytes:1012 (1012.0 b)  TX bytes:954 (954.0 b)
          Interrupt:3 Base address:0x100

---

### Post by ymeng on 2006-02-22
I posted this one last night. I guess most people went to sleep.

I hope I can get some response during the day.

thanks for your help. 

[QUOTE=ymeng]I am a newbie. I have a Dell Latitude running Ubuntu 5.1. I plugged in Cisco aironet 340.  I use WEP on my router. I entered my system id and my key (hexadecimal) using "Network Settings", and selected DHCP.

I am pretty much lost after that. I don't have a connection, unless I plug in my network cable.

I ran a couple of commands and pasted results below, I couldn't tell what's wrong. Can someone tell me what I need to do?

Thanks.
================
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"mysid"
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:0F:66:C3:7D:E9
          Bit Rate:5.5 Mb/s   Tx-Power=15 dBm   Sensitivity=0/65535
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-40 dBm  Noise level=-100 dBm
          Rx invalid nwid:93  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:41   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:"mysid"
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:0F:66:C3:7D:E9
          Bit Rate:5.5 Mb/s   Tx-Power=15 dBm   Sensitivity=0/65535
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-40 dBm  Noise level=-100 dBm
          Rx invalid nwid:93  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:41   Missed beacon:0

================
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:03:8D:F0:01
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:3ff:fe8d:f001/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5327 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8294068 (7.9 MiB)  TX bytes:642818 (627.7 KiB)
          Interrupt:11 Base address:0xd400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:42064 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42064 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3142746 (2.9 MiB)  TX bytes:3142746 (2.9 MiB)

wifi0     Link encap:UNSPEC  HWaddr 00-40-96-2A-0A-9E-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:2312  Metric:1
          RX packets:22 errors:8 dropped:0 overruns:0 frame:8
          TX packets:0 errors:1 dropped:0 overruns:0 carrier:0
          collisions:16 txqueuelen:100
          RX bytes:1012 (1012.0 b)  TX bytes:954 (954.0 b)
          Interrupt:3 Base address:0x100[/QUOTE]

---

### Post by romdos on 2006-02-23
hmmm...
The first thing that you should try is to disable wep on your router and remove any wep keys on your local system and see if you can connect.
Wifi can be a little tricky, so it is good to eliminate sources of error so we can hone in  on the real problem.

If you can connect to your now open access point, your problem is your wep configuration, if not it is your wifi setup itself.

Try it and let us know what happend so we know which way to go...

---

### Post by ymeng on 2006-02-24
I got it working by "following" this guide: [https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide). Honest with you I couldn't really follow the guide:( , so I just started to try some of the commands.

The answer for me was really simple: I just ran sudo: dhclient.  That's it! But I have to do this each time after reboot :(

I stumbled on another problem right after I fixed the network connection. I wonder if anyone knows why:

I was following a how-to guide [http://makuchaku.info/amnesty/#scim](http://makuchaku.info/amnesty/#scim) to install scim, but it didn't work. Here is the screen dump:

ym@latitude:~$ sudo apt-get install scim
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package scim

So where should I find the scim package? How?

Any help is greatly appreciated.

---

### Post by romdos on 2006-02-24
scim is in the universe repository
to enable universe edit the text file /etc/apt/sources.list
uncomment the following lines ( remove the # from the beginning ):

```

# deb http://us.archive.ubuntu.com/ubuntu breezy universe
# deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

```

so now the lines should look like this:
```

 deb http://us.archive.ubuntu.com/ubuntu breezy universe
 deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

```

save the file,
now:

```

romdos@freekbox:~$ sudo apt-get update
romdos@freekbox:~$ sudo apt-get install scim

```

---

### Post by ymeng on 2006-02-27
Thanks for the reply.  

I managed to get it work through GUI without fully understood what I was doing. Now I think the GUI did  the same as you suggested. I checked "Community Mantained (Universe)" in Synaptic Package Manager. 

I appreciate your helpl. I always want to know what is under the hood, instead of blindly clicking on the GUI.

---

