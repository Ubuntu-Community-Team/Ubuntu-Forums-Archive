---
title: "Koala no longer Karmic on wireless internet - only vpn not greyed out."
date: 2010-08-20
forum: Networking &amp; Wireless
---

### Post by Lobstercat on 2010-08-20
I am having some issues with my wireless connection.  I recently upgraded to Karmic Koala, and everything still worked just fine - I had reliable wireless from both Ubuntu and Xubuntu.  I don't use Kubuntu as much, usually just as a change of pace if I am just goofing off and not working - checking email, playing a little game, maybe writing a letter or something.  
But Kubuntu would not connect to the internet and it bugged me, so I tried to fix it.  I copied all my settings from my Ubuntu connection and put them in Kubuntu, even though they should have already been more or less the same anyway.  I then read a post about modifying the /etc/resolve.conf file and the /etc/network/interfaces file.  Still no 'net in Kubuntu.  Went back to Ubuntu to research some more and ... OOOPS!  No more 'net on Ubuntu either!  
I went back and renamed the two files I changed to a .old1a extention and deleted the ~ to restore the bak files to the origional again, but still no 'net in Ubuntu.  I have been trying to learn and write some programs for Ubuntu linux, but the internet stuff is still over my head.  Usually I would just fix this with another fresh install off my most recent backup, but I would really like to learn something here and figure this out.  
So now we need some info, well, you do if you think you can help that is.  First: Here is the result from my lshw -C Network:
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:24:6d:52:d4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:28 ioport:2000(size=256) memory:80000000-80000fff memory:80100000-8011ffff(prefetchable)
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:2c:70:13
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.102 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:29 memory:80200000-80201fff

Here are the results of iwconfig and ifconfig, respectively.  I did this while my laptop was at my second job at MetroPCS, so the wireless network is MetroPCS.
lobstercat@lobstercat-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"MetroPCS"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lobstercat@lobstercat-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:6d:52:d4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:117 errors:0 dropped:0 overruns:0 frame:0
          TX packets:117 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9952 (9.9 KB)  TX bytes:9952 (9.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:2c:70:13  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:e8ff:fe2c:7013/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:183 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1700 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20679 (20.6 KB)  TX bytes:515838 (515.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-2C-70-13-32-63-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

As I said, I had been reading and trying to fix Kubuntu's internet connection and changed two files.  First, here is the /etc/resolv.conf file that I created:
domain Home
nameserver 192.168.1.47
nameserver 71.242.0.12
nameserver 71.250.0.12
And here is the origional, which I returned to its rightful place having renamed the above to resolv.conf.bak1a:
nameserver 71.242.0.12
nameserver 71.250.0.12

Now this is the modified /etc/network/interfaces file, which I have also since changed to interfaces.old1a:
auto lo wlan0
iface lo inet loopback


iface wlan0 inet static
address 192.168.1.102
netmask 255.255.255.0
gateway 192.168.1.47
dns-domain 192.168.1.47
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid MetroPCS

auto wlan0

And here is the origional, which is now once again back in place:
auto lo
iface lo inet loopback


iface wlan0 inet static
address 192.168.1.102
netmask 255.255.255.0
gateway 192.168.1.47
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid MetroPCS

auto wlan0

And last but not least, here is a interfaces~ file that was created by the computer at some point here:
auto lo wlan0
iface lo inet loopback


iface wlan0 inet static
address 192.168.1.102
netmask 255.255.255.0
gateway 192.168.1.47
dns-domain 192.168.1.47
wpa-psk 480e7b6840793778eba00cb1ab9171c178ab471f63eeed60a46ca3e75bb6c0bd
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid MetroPCS

auto wlan0

My computer is a Toshiba Satellite U305 w/Intel Core2 T5300 1.73Ghz w/2G Ram & 802.11a/g/n wireless LAN which dual boots into Vista Home Premium.
I know that is probably information overload, but you never know what is going to be useful.
I was reading the sticky about the ndiswrapper, but I don't think it applies, because the drivers are already in place, and windows still works just fine, and even Ubuntu worked just fine until a few days ago when I tried to fix Kubuntu.  Of course, I am not opposed to anything if it works, but I would like to understand exactly what happened and why and ... you get the idea.
So any ideas how to fix my wireless in Ubuntu?  And while I'm at it, any ideas why Kubuntu would not connect when Ubuntu and Xubuntu would and how could I have fixed it or can I fix it now?
Thanks for your time, and hope you all have a great day.

---

