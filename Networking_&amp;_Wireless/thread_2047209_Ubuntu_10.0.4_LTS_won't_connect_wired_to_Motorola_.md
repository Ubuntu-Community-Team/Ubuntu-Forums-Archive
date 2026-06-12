---
title: "Ubuntu 10.0.4 LTS won't connect wired to Motorola Netopia Motorola 2247-N8 router"
date: 2012-08-24
forum: Networking &amp; Wireless
---

### Post by jkuzenka on 2012-08-24
Hello All,

I was hoping someone could help me fix connecting my Dell Desktop PC that is running Ubuntu 10.0.4 LTS to a new Motorola Netopia Motorola 2247-N8 router. This Wireless DSL router is configured with DHCP, NAT, LAN using AT&T PPOE connection.  I have public IPs DNS servers and gateways that are passed from my ISP.  

I created 
**_Static Private LAN subnet as follows:_**

_IP ADDRESS Range_: 10.1.0.XXX to 10.1.0.XXX
_DNS_ = Automatic configure on Windows machines. 
_DCHP_ - Enabled on Router.
_Gateway_: 10.1.X.X

I can successfully connect Windows XP OS by Ethernet to Router and connect to the internet.  I have 3 Windows 7 Laptops that can connect Wirelessly via WEP security setup through the Router to the Internet.

My struggle is even though I have updated the /etc/resolv.conf and entered the namesservers to the /etc/hosts file I still cannot get my Dell Desktop to ping the Gateway 10.1.X.X.  I can ping other IP Addresses on the private network that start with 10.1.X.X.  I also cannot get [www.google.com](www.google.com) to be pinged successfully.  

I get an error message if I try to do a "sudo route add default gw 10.1.X.X eth0" command in Terminal.  I logon to my router through the IP 10.1.X.X on my Windows PC.  I also do an ipconfig /all and the Gateway equals the 10.1.X.X.

I also tried with factory default 192.168.1.XXX settings and wired connection with multiple restarts for both router and PC eth0 connection through network manager.

I spent a week searching Google and trying all recommended troubleshooting steps to get this to work without success.

This same setup worked with the old router 2-Wire model before it died and I had to replace it with the new motorola model I put in last weekend.  My family is happy as they use the Windows Machines but, I like using my Linux machines and cannot get connected to the internet.

Any help would be appreciate as I cannot think of how to get this to work.

~Josh

---

### Post by jkuzenka on 2012-08-24
FYI - More info on the Router incase anyone needs this with helping me troubleshoot the problem:
[http://www.bhphotovideo.com/c/product/845336-REG/Motorola_579765_003_00_2247_N8_Wireless_DSL_Modem.html](http://www.bhphotovideo.com/c/product/845336-REG/Motorola_579765_003_00_2247_N8_Wireless_DSL_Modem.html)

Thanks,

Josh

---

### Post by chili555 on 2012-08-24
Please post:```
ifconfig
route -n
cat /etc/resolv.conf
cat /etc/network/interfaces
nm-tool
```Thanks.> IP ADDRESS Range: 10.1.0.XXX to 10.1.0.XXXIt is not necessary and, in fact, not helpful, to obscure these numbers. 10.1.x.y is a private network and knowing you are at 10.1.0.23 doesn't tell the hackers anything useful if they don't know the IP address the router got from your ISP, which you *should* obscure. However, knowing the address of the router is 10.[COLOR="Red"]1.0[/COLOR].1 and you set a route of 10.[COLOR="Red"]0.1[/COLOR].1 would be very helpful.

---

### Post by jkuzenka on 2012-08-24
Thank you chili555 for your response.

Sorry for masking the IP as I have seen this used in other forums on the web and followed suit.  I guess they may have been posting IP Addresses that were not Private.

I am away from my Desktop PC during the day and won't have access to it until tonight. I will run the commands tonight on my Linux machine and provide you with this information.

The IP Address I mentioned for router Gateway is 10.1.0.0.  The IP assigned to the Linux PC with Ubuntu is 10.1.0.2.  I'll get you the rest of the info you requested.

Appreciate your quick response.  Thank you.

~Josh

---

### Post by chili555 on 2012-08-24
I'll look forward to your readings. >  I have seen this used in other forums on the web and followed suit. I guess they may have been posting IP Addresses that were not Private.Correct. We were all just learning at one time, even ole Doc Chili and even Linus.

---

### Post by sanderj on 2012-08-24
> **jkuzenka said:**
> 

The IP Address I mentioned for router Gateway is 10.1.0.0.  The IP assigned to the Linux PC with Ubuntu is 10.1.0.2.  I'll get you the rest of the info you requested.



AFAIK, 10.1.0.0 is not an IP address.

On a Windows computer (with a wired connection), type:

```
ipconfig

```

and post the output here.

Checking: I hope you're using DHCP on your Linux (and Windows) system?

---

### Post by jkuzenka on 2012-08-24
Hi sanderj,

> AFAIK, 10.1.0.0 is not an IP address.

10.1.0.0 Gateway? If I am incorrect please tell me what it is so I can be using the right terms when posting on this.

I will post my Windows XP PC ipconfig tonight along with what chili555 requested for linux PC.

I will check when I get home tonight but, I believe both Ubuntu Linux PC & Windows XP PC are setup to use DCHP automatically.  

Thanks for your help.

~ Josh

---

### Post by sanderj on 2012-08-24
> **jkuzenka said:**
> Hi sanderj,



10.1.0.0 Gateway? If I am incorrect please tell me what it is so I can be using the right terms when posting on this.

I will post my Windows XP PC ipconfig tonight along with what chili555 requested for linux PC.

Thanks for your help.

~ Josh

In general, .0 would be considered as a network identifier and .255 would be a broadcasting address. 

So your gateway should not end with .0 (nor 2.55)

(You can have a different (bigger) netmask and then have an IP address ending in .0, but let's not dive into that).

---

### Post by praseodym on 2012-08-24
Please show additionally on Ubuntu:

```
lspci -nnk | grep -iA2 net
lsmod
```

---

### Post by jkuzenka on 2012-08-24
Here is the results from UBUNTU 10.0.4.4 LTS from terminal commands:
 
**ifconfig**
> 
[FONT=Times New Roman][SIZE=3]jkuzenka-test@jkuzenka-test-desktop:~$ ifconfig[/SIZE][/FONT]
 
[SIZE=3][FONT=Times New Roman]eth0 Link encap:Ethernet HWaddr 00:11:11:97:29:da [/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]inet addr:10.1.0.2 Bcast:10.1.0.255 Mask:255.255.255.0[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]inet6 addr: fe80::211:11ff:fe97:29da/64 Scope:Link[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]UP BROADCAST RUNNING MULTICAST MTU:1429 Metric:1[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]RX packets:64166 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]TX packets:445 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]collisions:0 txqueuelen:1000 [/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]RX bytes:4330537 (4.3 MB) TX bytes:70730 (70.7 KB)[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]Interrupt:16 [/FONT][/SIZE]
 
 
 
[SIZE=3][FONT=Times New Roman]lo Link encap:Local Loopback [/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]inet addr:127.0.0.1 Mask:255.0.0.0[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]inet6 addr: ::1/128 Scope:Host[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]UP LOOPBACK RUNNING MTU:16436 Metric:1[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]RX packets:321603 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]TX packets:321603 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]collisions:0 txqueuelen:0 [/FONT][/SIZE]
 
[FONT=Times New Roman]RX bytes:35622669 (35.6 MB) TX bytes:35622669 (35.6 MB)[/FONT]

**[FONT=Times New Roman][SIZE=3]route -n[/SIZE][/FONT]**
> 
[FONT=Times New Roman][SIZE=3]kuzenka-test@jkuzenka-test-desktop:~$ route -n[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Kernel IP routing table[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Destination Gateway Genmask Flags Metric Ref Use Iface[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]10.1.0.0 0.0.0.0 255.255.255.0 U 1 0 0 eth0[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 eth0[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]127.0.0.0 0.0.0.0 255.0.0.0 U 0 0 0 lo[/SIZE][/FONT]
 

 
**cat /etc/resolv.conf**
> 
[FONT=Times New Roman][SIZE=3]jkuzenka-test@jkuzenka-test-desktop:~$ cat /etc/resolv.conf[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]# Generated by NetworkManager[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]domain domain_not_set.invalid[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]search domain_not_set.invalid[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]nameserver 10.1.0.0[/SIZE][/FONT]


 
**cat /etc/network/interfaces**
> 
[FONT=Times New Roman][SIZE=3]jkuzenka-test@jkuzenka-test-desktop:~$ cat /etc/network/interfaces[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]auto lo[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]iface lo inet loopback[/SIZE][/FONT]
 
 
 
[FONT=Times New Roman][SIZE=3]auto eth0[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]iface etho inet static[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]address 10.1.0.2[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]netmask 255.255.255.0[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]gateway 10.1.0.0[/SIZE][/FONT]
 

 
 
**lspci -nnk | grep -iA2 net**
> 
[FONT=Times New Roman][SIZE=3]jkuzenka-test@jkuzenka-test-desktop:~$ lspci -nnk | grep -iA2 net[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)[/SIZE][/FONT]
 
[SIZE=3][FONT=Times New Roman]Kernel driver in use: tg3[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]Kernel modules: tg3[/FONT][/SIZE]
 
 

 
 
**lsmod**
> 
[FONT=Times New Roman][SIZE=3]jkuzenka-test@jkuzenka-test-desktop:~$ lsmod[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Module Size Used by[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]nls_iso8859_1 3249 1 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]nls_cp437 4919 1 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]vfat 8933 1 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]fat 47767 1 vfat[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]usb_storage 40033 1 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]iptable_filter 2271 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]ip_tables 9991 1 iptable_filter[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]x_tables 14299 1 ip_tables[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]binfmt_misc 6587 1 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]pci_stub 1102 1 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]vboxpci 14531 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]vboxnetadp 19352 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]vboxnetflt 16780 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]vboxdrv 251300 3 vboxpci,vboxnetadp,vboxnetflt[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]fbcon 35102 71 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]tileblit 1999 1 fbcon[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]font 7557 1 fbcon[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]bitblit 4707 1 fbcon[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]softcursor 1189 1 bitblit[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]vga16fb 11385 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]vgastate 8961 1 vga16fb[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]snd_intel8x0 25652 2 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]snd_ac97_codec 100646 1 snd_intel8x0[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]ac97_bus 1002 1 snd_ac97_codec[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]snd_pcm_oss 35308 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]snd_mixer_oss 13746 1 snd_pcm_oss[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]snd_pcm 70694 3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]snd_seq_dummy 1338 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]snd_seq_oss 26722 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]snd_seq_midi 4557 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]snd_rawmidi 19056 1 snd_seq_midi[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]snd_seq_midi_event 6003 2 snd_seq_oss,snd_seq_midi[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]snd_seq 47263 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]radeon 678607 2 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]snd_timer 19130 2 snd_pcm,snd_seq[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]snd_seq_device 5700 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]ttm 49847 1 radeon[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]drm_kms_helper 29329 1 radeon[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]snd 54244 14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]ppdev 5259 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]drm 163779 4 radeon,ttm,drm_kms_helper[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]soundcore 6620 1 snd[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]dell_wmi 1793 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]dcdbas 5422 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]parport_pc 25962 1 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]psmouse 63677 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]serio_raw 3978 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]snd_page_alloc 7076 2 snd_intel8x0,snd_pcm[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]agpgart 31724 2 ttm,drm[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]i2c_algo_bit 5028 1 radeon[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]lp 7028 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]parport 32635 3 ppdev,parport_pc,lp[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]tg3 109324 0 [/SIZE][/FONT]
 

 
**WINDOWS XP SP3:**
 
**ipconfig /all**
 
 
> 
Windows IP Configuration
 
Host Name . . . . . . . . . . . . : KUZENKA
Primary Dns Suffix . . . . . . . : 
Node Type . . . . . . . . . . . . : Broadcast
IP Routing Enabled. . . . . . . . : No
WINS Proxy Enabled. . . . . . . . : No
DNS Suffix Search List. . . . . . : domain_not_set.invalid
 
Ethernet adapter Local Area Connection:
 
Connection-specific DNS Suffix . : domain_not_set.invalid
Description . . . . . . . . . . . : Intel(R) PRO/100 VE Network Connection
Physical Address. . . . . . . . . : 00-07-E9-8F-4F-F1
Dhcp Enabled. . . . . . . . . . . : Yes
Autoconfiguration Enabled . . . . : Yes
IP Address. . . . . . . . . . . . : 10.1.0.1
Subnet Mask . . . . . . . . . . . : 255.255.255.0
IP Address. . . . . . . . . . . . : fe80::207:e9ff:fe8f:4ff1%4
Default Gateway . . . . . . . . . : 10.1.0.0
DHCP Server . . . . . . . . . . . : 10.1.0.0
DNS Servers . . . . . . . . . . . : 10.1.0.0
fec0:0:0:ffff::1%1
fec0:0:0:ffff::2%1
fec0:0:0:ffff::3%1
Lease Obtained. . . . . . . . . . : Friday, August 24, 2012 5:58:58 PM
Lease Expires . . . . . . . . . . : Saturday, August 25, 2012 5:58:58 PM
 
Tunnel adapter Teredo Tunneling Pseudo-Interface:
 
Connection-specific DNS Suffix . : 
Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
Physical Address. . . . . . . . . : FF-FF-FF-FF-FF-FF-FF-FF
Dhcp Enabled. . . . . . . . . . . : No
IP Address. . . . . . . . . . . . : fe80::ffff:ffff:fffd%5
Default Gateway . . . . . . . . . : 
NetBIOS over Tcpip. . . . . . . . : Disabled
 
Tunnel adapter Automatic Tunneling Pseudo-Interface:
 
Connection-specific DNS Suffix . : domain_not_set.invalid
Description . . . . . . . . . . . : Automatic Tunneling Pseudo-Interface
Physical Address. . . . . . . . . : 0A-01-00-01
Dhcp Enabled. . . . . . . . . . . : No
IP Address. . . . . . . . . . . . : fe80::5efe:10.1.0.1%2
Default Gateway . . . . . . . . . : 
DNS Servers . . . . . . . . . . . : fec0:0:0:ffff::1%1
fec0:0:0:ffff::2%1
fec0:0:0:ffff::3%1
NetBIOS over Tcpip. . . . . . . . : Disabled

 
 
Please review and let me know what you recommend me to try. I have to do some volunteer work for Scouts but, I will be back online again later.
 
Thank you all for your help.
 
~Josh

---

### Post by sanderj on 2012-08-25
Woah:

```
Dhcp Enabled. . . . . . . . . . . : Yes
Autoconfiguration Enabled . . . . : Yes
IP Address. . . . . . . . . . . . : 10.1.0.1
Subnet Mask . . . . . . . . . . . : 255.255.255.0
IP Address. . . . . . . . . . . . : fe80::207:e9ff:fe8f:4ff1%4
Default Gateway . . . . . . . . . : 10.1.0.0
DHCP Server . . . . . . . . . . . : 10.1.0.0
DNS Servers . . . . . . . . . . . : 10.1.0.0

```

... your Windows really has 10.1.0.0 as gateway with 255.255.255.0 as netmask. And that works? I'm baffled.

Furthermore: your linux' eth0 has Tranmist and Receive bytes.

Once again: on your Linux, "ping 10.1.0.0" does not work, does it?

---

### Post by praseodym on 2012-08-25
Change "false" to "true" in /etc/NetworkManager/nm-system-settings.conf

---

### Post by chili555 on 2012-08-25
I am on my way out of town, so this will be brief and to the point. I suggest:

# I assume PPPoE authentication (user/password) is done in the router. That's what I recommend.

# Upgrade from WEP. You don't leave your credit cards in a shoe-box on the front porch, do you? That's about how secure WEP is.

# Remove Network Manager if you want to use manual methods, or else set up your static IP address *OUTSIDE* the DHCP range, in NM.

# Set the router to use 192.168.1.1. 

# If you need one, set a static IP in Ubuntu of 192.168.1.100. Do so in NM or /etc/network/interfaces, but not both.

# If you set a static IP in Ubuntu (why?) then set DNS nameservers to 8.8.8.8 and 192.168.1.1.

I don't believe the driver itself is an issue since you can connect...sort of:>  I can ping other IP Addresses on the private network that start with 10.1.X.X. I also cannot get [www.google.com](www.google.com) to be pinged successfully. I know, this is the boring, old-school method. However, it works.

If my colleagues want to jump in here, please do. I will be away for the week-end.

---

### Post by jkuzenka on 2012-08-25
@sanderj

Yes I was able to use 10.1.0.0 without any error messages from router or without issue form Windows PCs, Windows Laptops, or Blackberry phones.   Only Linux Fedora, Peppermint, and Ubuntu machines are giving me issues connecting to internet.

I can ping 10.1.0.0 from Windows but, not in Ubuntu Linux.

@chili555,

I will try changing my private address using some of your methods.  I have read that not all devices may support WPS so wasn't sure on setting this up when I got the new router since WEP worked for all of my laptops, smart phones, Wii, PCs before on the old router.

I only tried static IP in Linux because automatic DNS & DHCP wasn't getting me connected to the internet so I was trying anything I could think of to get it connected on Ubuntu.

I appreciate your help and responses.  I will let you know how it goes.

@praseodym

I will try making that change too.

Thank you all for your time.  I will try what you are suggesting and will report back.  

~Josh

---

### Post by jkuzenka on 2012-08-28
Hello All,

After changing my Private DCHP from 10.1.0.0 to 10.1.1.1, along with my IP Ranges 10.1.1.2 through 10.1.1.253, and restarting PCS & Router with new configurations I can now connect to the internet.  I removed all the manual settings in the hosts & resolv.conf files back to what they were before I made the changes.  So now with Auto DHCP turned on I am all set.  No more issues.

I am posting from my Dell machine with Ubuntu 10.04.4 LTS.

Here is the updated Routing Table:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.1.1.0        0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.1.1.1        0.0.0.0         UG    0      0        0 eth0

```Everything seems to work as good or better with my new router now.

Thank you for your help as my issue is now fixed.

Cheers!!!!  :p

Josh

---

### Post by jkuzenka on 2012-09-13
FYI - I installed 12.0.4.1 LTS on same Dell Machine and there are no issues Networking, Internet, and Motorola 2246-N8 router setup since it was fixed for 10.04.4 LTS.

Worked without any changes to settings.

;)

~ Josh

---

