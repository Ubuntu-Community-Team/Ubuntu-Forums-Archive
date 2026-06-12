---
title: "Broadcom Drivers not activating"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by K_Boomer on 2009-11-03
I hope somebody can guide me to the light on this one. I just upgraded to ubuntu 9.10 from 9.04. My Broadcom BCM 4312 802.11b/g card was immediately detected in jaunty, but is not working in karmic. I have checked 15+ similar problems, but I feel I am much worse off after trying their solutions.

here is where I am at:
The B43 driver is not working (no wireless connection found) so I am trying the STA. 

When I try activating the STA via Hardware Drivers or via sudo jockey-gtk, it shows that it is downloading/installing, but then it will remain inactive.

I tried inactivating the B43 first, but I receive this message:

SystemError: E:I wasn't able to locate a file for the cabextract package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the flashplugin-installer package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the freepats package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the gstreamer0.10-ffmpeg package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the gstreamer0.10-pitfdll package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the gstreamer0.10-plugins-bad-multiverse package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the gstreamer0.10-plugins-ugly package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the gstreamer0.10-plugins-ugly-multiverse package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the libcdaudio1 package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the libcelt0 package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the libdirac0c2a package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the libfaac0 package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the libffado1 package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the libfftw3-3 package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the libfreebob0 package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the libid3tag0 package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the libiptcdata0 package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the libjack0 package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the libkate1 package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the libmimic0 package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the libmjpegtools-1.9 package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the libmms0 package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the libmp3lame0 package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the libmp4v2-0 package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the libofa0 package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the libopenspc0 package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the libquicktime1 package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the libsoundtouch1c2 package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the libwildmidi0 package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the libxml++2.6-2 package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the libxvidcore4 package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the ttf-liberation package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the ubuntu-restricted-extras package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the unrar package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the gstreamer0.10-plugins-bad package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the libdc1394-22 package. This might mean you need to manually fix this package. (due to missing arch), E:I wasn't able to locate a file for the libsidplay1 package. This might mean you need to manually fix this package. (due to missing arch)


Sorry about all that.

Anyways, there is something going on with my dpkg I think and I don't want to mess with it until I get some professional advice.


For what it is worth, I have installed the bcmwl-kernel-source, and have updated my repositories. When I tried installing B43fwcutter, I get responses like:

"dpkg: warning: files list file for package `file name' missing, assuming package has no files currently installed."

and

"Preparing to replace python2.6-minimal 2.6.4~rc2-0ubuntu1 (using .../python2.6-minimal_2.6.4~rc2-0ubuntu1_i386.deb) ...
Unpacking replacement python2.6-minimal ...
dpkg: error processing /var/cache/apt/archives/python2.6-minimal_2.6.4~rc2-0ubuntu1_i386.deb (--unpack):
 unable to create updated files list file for package python2.6-minimal: No such file or directory
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/python2.6-minimal_2.6.4~rc2-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)"



I hope somebody can help me. I have tried most of the help links posted, but I could use some more assistance with dpkg, wireless and such.

---

### Post by K_Boomer on 2009-11-03
Oh, and btw, here is my 
ifconfig ;  iwconfig;  route -n;  cat /etc/resolv.conf  and cat /etc/network/interfaces

eth0      Link encap:Ethernet  HWaddr 00:25:64:3e:3b:32  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:64ff:fe3e:3b32/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:613 errors:0 dropped:0 overruns:0 frame:0
          TX packets:536 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:630647 (630.6 KB)  TX bytes:84139 (84.1 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

lo        no wireless extensions.

eth0      no wireless extensions.

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
domain ***-Pen
search ***-Pen
nameserver 192.168.1.1
cat: and: No such file or directory
cat: cat: No such file or directory
auto lo
iface lo inet loopback

---

### Post by K_Boomer on 2009-11-04
Solution:

Reinstalled 9.10 from disk. 

sudo apt-get install bcmwl-kernel-source
sudo apt-get install b43-fwcutter
sudo reboot

---

