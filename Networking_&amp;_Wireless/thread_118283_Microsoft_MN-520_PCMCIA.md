---
title: "Microsoft MN-520 PCMCIA"
date: 2006-01-16
forum: Networking &amp; Wireless
---

### Post by lilolpete on 2006-01-16
:::NEWBIE FRUSTRATION::: lol
OK. Been trying all morning and all afternoon to get my laptop to pickup a wireless signal. First I realized that Ubuntu was not picking up my pcmcia card so I went ahead I read off some forums that I could just do the following:

I added the following lines to /etc/pcmcia/config:

card "Microsoft Wireless Notebook Adapter MN-520 1.0.3"
version "Microsoft", "Wireless Notebook Adapter MN-520", "", "1.0.3"
bind "orinoco_cs"

I think it picks my card up I'm not sure( I go into the Networking to activate it, and changing the configuration to DHCP) it outputs the following when entering ifconfig:

eth1      Link encap:Ethernet  HWaddr 00:50:F2:76:2A:70
          inet6 addr: fe80::250:f2ff:fe76:2a70/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:2108 (2.0 KiB)
          Interrupt:3 Base address:0x100

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:20188 (19.7 KiB)  TX bytes:20188 (19.7 KiB)

When entering iwconfig (seems to pickup my neighbor Ohashi's WAN?): 

eth0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"Ohashi"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.437 GHz  Access Point:
           00:12:17:BB:1D:7E
          Bit Rate:2 Mb/s   Tx-Power=15 dBm   Sensitivity:1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=10/92  Signal level=136/153  Noise level=111/153
          Rx invalid nwid:0  Rx invalid crypt:15  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions. 

Now when I look at the upper left handcorner of my screen I see my network connection is set to “lo”. How do I go about finding a set of available connections? Its driving me nutts! lol Is there something in Ubuntu that I'm not finding, to see this? I want to be able to go everywhere, including school, and connect to the internet. How do I go about this? Where do I go to see available connections?

---

### Post by Lambert on 2006-01-16
lo is your loopback interface. Right click on the icon, click properties and choose eth1 interface to show that activity.

You need to install a package for graphical management of wireless connections

wifiradar or network manager is in the repos. gtkwifi is a third part project you can find here in the forums

You can also scan for networks with this terminal command

sudo iwlist eth1 scan

some drivers don't support this so you might get output stating that.

Then to connect to the signal you can use this command

sudo ifconfig eth1 up

sudo iwconfig eth1 essid ____ key ____ ap __:__:__:__:__

then if you associate with the router you can run this command to get an ip assigned if router uses dhcp settings

sudo dhclient eth1

If you go to the wiki you can search for wifi or wireless for more help

---

### Post by lilolpete on 2006-01-16
ah thanks yeah my driver apparently doesn't support that. But I found out what the problem was... my /etc/network/interface file was somehow incorrect. I had to type in the following to get it so I could actually even select something from the drop down menu in Network Connections lol.
```

# The primary network interface
iface eth1 inet dhcp

auto eth1


```

lol now I must attempt installing one of those apps you mentioned above :???:

---

### Post by lilolpete on 2006-01-16
So what if my driver doesn't support scanning. Is there anything I can do about it?

---

### Post by Lambert on 2006-01-16
I'm not that knowledgeable about the orinoco driver so hopefully someone else can jump in here.

you can find more information about the driver here.

[http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Orinoco.html]("http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Orinoco.html")

I see a section about patching the driver which include some links about adding the scan function. But again, not that knowledeable so I don't know what this involves and how hard it might be. It also says latest v doesn't need a patch so I'm not sure what version comes with breezy etc....

---

### Post by robotgeek on 2006-01-16
I know for sure that people have had issues with getting this card working on Ubuntu. 

However, you have already gotten the card working, so kudos! The orinoco driver doesn't support scanning, so most of the wireless utilities will be a pain to work with. However, network-manager allows you to enter the network details manually. I use it regularly on my laptop, and it's definetly a must have app for laptops. 

[https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto)

---

