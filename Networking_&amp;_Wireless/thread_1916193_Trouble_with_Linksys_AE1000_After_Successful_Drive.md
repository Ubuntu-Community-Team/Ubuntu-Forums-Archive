---
title: "Trouble with Linksys AE1000 After Successful Driver Installation"
date: 2012-01-27
forum: Networking &amp; Wireless
---

### Post by LoserDude27 on 2012-01-27
Hello all,

I successfully installed the rt3572STA driver for my Linksys AE1000 (after editing the files, etc, etc.).  I can view networks without a problem, but when I try connect to my home network, it continuously asks for my password.

Last night, I was able to connect to my router for the first time after a week of hassle.  After about an hour of a great connection, it decided to disconnect and go back to asking me for my password continuously. It seems that after I'm prompted for my password several (around 5) times, it gives up trying.  Then my network menu freezes until I unplug the adapter...

It may help noting that I have a Linksys PCI card installed which I don't use because of its poor connectivity.  I'm not worried about getting that to work.  My AE1000 works fine in Windows 7 64-bit.  I'm running Ubuntu 11.10 64-bit. I'm fairly new with Linux, but I'm able to follow things pretty well.

This is my dmesg:

```
adam@adam-ubuntu:~$ dmesg | grep rt2
[  180.378020] rtusb init rt2870 --->
[  180.380595] usbcore: registered new interface driver rt2870
[  181.134437] <==== rt28xx_init, Status=0
[  182.117591] <==== rt28xx_init, Status=0
[  183.191855] <==== rt28xx_init, Status=0
[  561.440527] !!! rt28xx Initialized fail !!!

```

and my iwconfig:


```
adam@adam-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
ra0       Ralink STA  ESSID:"Adam"  Nickname:"RT3572STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
lsmod | grep rt2
``` returns nothing

Thanks in advance for any suggestions!

Edit: Sorry, but I won't be able to check back until tomorrow afternoon due to work, but don't hesitate to leave me a reply. :)

---

### Post by chili555 on 2012-01-28
Why do you have a wlan0 and an ra0? Do you have another wireless device? Also, let's have a look at:```
dmesg | grep -e ra0 -e rt3
```Thanks.

---

### Post by LoserDude27 on 2012-01-28
Thanks for the reply, Doc!

Yeah, I have a PCI wireless card which I don't want to use at all. If you think that might be conflicting, I can take it out.

**EDIT: I took out the other wireless card and I'm having the same issue still.**

Before reboot and removal of other card:

```
adam@adam-ubuntu:~$ dmesg | grep -e ra0 -e rt3
[ 4680.760222]  [<ffffffffa0f927ac>] RtmpOSTaskKill+0x1c/0x20 [rt3572sta]
[ 4680.760249]  [<ffffffffa0fa7d95>] RtmpMgmtTaskExit+0x35/0x110 [rt3572sta]
[ 4680.760276]  [<ffffffffa0f4df4f>] RTMPDrvClose+0xbf/0x1a0 [rt3572sta]
[ 4680.760304]  [<ffffffffa0f92c7f>] rt28xx_close+0x2f/0x70 [rt3572sta]
[ 4680.760334]  [<ffffffffa0f5a80f>] RTMP_COM_IoctlHandle+0x35f/0x620 [rt3572sta]
[ 4680.760360]  [<ffffffffa0f4e1a1>] ? RTMPInfClose+0x91/0x250 [rt3572sta]
[ 4680.760389]  [<ffffffffa0f92d26>] MainVirtualIF_close+0x66/0xa0 [rt3572sta]
[ 4680.760417]  [<ffffffffa0f93160>] ? RtmpOSIRQRequest+0x50/0x50 [rt3572sta]
[ 4680.760445]  [<ffffffffa0f92c50>] ? RtmpNetEthConvertDevSearch+0x80/0x80 [rt3572sta]
[ 4684.213566] RtmpOSNetDevDetach(): RtmpOSNetDeviceDetach(), dev->name=ra0!
```

After reboot and removal of card:

```
adam@adam-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"Adam"  Nickname:"RT3572STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: 00:18:F8:C8:A1:CE   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

adam@adam-ubuntu:~$ dmesg | grep -e ra0 -e rt3
[   27.520027] ra0: no IPv6 routers present
```

Also, after many tries of connecting, the network menu stops responding and iwconfig hangs. When I unplug the AE1000, the network menu works again and iwconfig finishes with: 

```
adam@adam-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  
```

---

### Post by chili555 on 2012-01-28
> [ 4680.760222]  [<ffffffffa0f927ac>] RtmpOSTaskKill+0x1c/0x20 [rt3572sta]
[ 4680.760249]  [<ffffffffa0fa7d95>] RtmpMgmtTaskExit+0x35/0x110 [rt3572sta]
[ 4680.760276]  [<ffffffffa0f4df4f>] RTMPDrvClose+0xbf/0x1a0 [rt3572sta]
[ 4680.760304]  [<ffffffffa0f92c7f>] rt28xx_close+0x2f/0x70 [rt3572sta]
[ 4680.760334]  [<ffffffffa0f5a80f>] RTMP_COM_IoctlHandle+0x35f/0x620 [rt3572sta]
[ 4680.760360]  [<ffffffffa0f4e1a1>] ? RTMPInfClose+0x91/0x250 [rt3572sta]
[ 4680.760389]  [<ffffffffa0f92d26>] MainVirtualIF_close+0x66/0xa0 [rt3572sta]
[ 4680.760417]  [<ffffffffa0f93160>] ? RtmpOSIRQRequest+0x50/0x50 [rt3572sta]
[ 4680.760445]  [<ffffffffa0f92c50>] ? RtmpNetEthConvertDevSearch+0x80/0x80 [rt3572sta]
[ 4684.213566] RtmpOSNetDevDetach(): RtmpOSNetDeviceDetach(), dev->name=ra0!Wow! That's an unhappy driver/card/OS combination. This may be a 64-bit issue. What version of the driver did you compile?```
modinfo rt3572sta | grep version
```Maybe there is another driver we can use. Please post:```
lsusb
```

---

### Post by LoserDude27 on 2012-01-28
I'm using the newest version of rt3572sta from the ralinktech site.

```
adam@adam-ubuntu:~$ modinfo rt3572sta | grep version
version:        2.5.0.0
srcversion:     76F1B8BB549BF51556EFB4F
vermagic:       3.0.0-15-generic SMP mod_unload modversions 
adam@adam-ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 13b1:002f Linksys AE1000 v1 802.11n [Ralink RT2870]
Bus 004 Device 002: ID 046d:0a15 Logitech, Inc. 
Bus 006 Device 002: ID 03f0:2b11 Hewlett-Packard PSC 2170 series
Bus 006 Device 003: ID 046d:c223 Logitech, Inc. G11/G15 Keyboard / USB Hub
Bus 006 Device 004: ID 046d:c221 Logitech, Inc. G11/G15 Keyboard / Keyboard
Bus 006 Device 005: ID 046d:c51a Logitech, Inc. MX Revolution/G7 Cordless Mouse
Bus 006 Device 006: ID 046d:c222 Logitech, Inc. G15 Keyboard / LCD
```

I'm not sure if it helps to note that I have two USB extensions attached in order to get the adapter close enough to the router for a good signal. The router is on the opposite side of the house and up one floor, so I don't a signal without the extensions.  This hasn't been a problem with Windows, and I do get the maximum speed possible when it works.

Also, I just thought of this: how can I find out which of my USB ports are 2.0 and which aren't? This might have something to do with my poor signal....

---

### Post by chili555 on 2012-01-29
> I'm not sure if it helps to note that I have two USB extensions attached in order to get the adapter close enough to the router for a good signal. The router is on the opposite side of the house and up one floor, so I don't a signal without the extensions. This hasn't been a problem with Windows, and I do get the maximum speed possible when it works.

Also, I just thought of this: how can I find out which of my USB ports are 2.0 and which aren't? This might have something to do with my poor signal....I'm not sure any of this is significant.> $ modinfo rt3572sta | grep version
version:        [COLOR="Red"]2.5.0.0[/COLOR]
srcversion:     76F1B8BB549BF51556EFB4F
vermagic:       3.0.0-15-generic SMP mod_unload modversions ...And I'm suspicious that *is* significant. Please check here: [http://confignewton.com/?p=104](http://confignewton.com/?p=104)>  Actually the newest version of the drivers for this card do not function correctly, they’ll compile sure but when it comes to actually using them they just won’t work and you’ll be left spinning your wheels for a few hours until you figure out what you’re doing differently from other folks who have gotten it to workI suggest you uninstall the version you have now:```
cd Desktop/RT3572   <---or wherever you extracted the file
sudo su
make uninstall
modprobe -r rt3572sta
exit
```Then download the pre-edited files referenced in the link and extract and compile as usual:```
cd Desktop/RT3572edited
sudo su
make clean
make
make install
modprobe rt3572sta
exit
```Now does the dmesg listings look a bit better?```
dmesg | grep -e rt3 -e ra0
```Does it connect?

---

### Post by LoserDude27 on 2012-01-29
Interesting! I did make uninstall for the 2.5 and installed the preedited, older version. It seems to have successfully installed, but I see nothing under the network menu.


```
adam@adam-ubuntu:~$ modinfo rt3572sta | grep version
version:        2.4.0.2
srcversion:     5B6BA19EC0AF027DB454414
vermagic:       3.0.0-15-generic SMP mod_unload modversions 

```

It is plugged in...

```
adam@adam-ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 13b1:002f Linksys AE1000 v1 802.11n [Ralink RT2870]
Bus 004 Device 002: ID 046d:0a15 Logitech, Inc. 
Bus 006 Device 002: ID 03f0:2b11 Hewlett-Packard PSC 2170 series
Bus 006 Device 003: ID 046d:c223 Logitech, Inc. G11/G15 Keyboard / USB Hub
Bus 006 Device 004: ID 046d:c221 Logitech, Inc. G11/G15 Keyboard / Keyboard
Bus 006 Device 005: ID 046d:c51a Logitech, Inc. MX Revolution/G7 Cordless Mouse
Bus 006 Device 006: ID 046d:c222 Logitech, Inc. G15 Keyboard / LCD

adam@adam-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

I did several of these, but to no avail (and no errors):

```
make uninstall
make clean
make
make install
modprobe rt3572sta
```

EDIT: Looking through the pre-edited files, I saw that ./common/rtusb_dev_id.c didn't have the appropriate line added for the AE1000. I added it, uninstalled and reinstalled and I still get the same as above.

---

### Post by chili555 on 2012-01-29
> I saw that ./common/rtusb_dev_id.c didn't have the appropriate line Let's see wht it looks like now that you edited it. Please attach it as an attachment to your reply.

---

### Post by LoserDude27 on 2012-01-29
It's working!!  I rebooted into Windows to do a remote assistance for someone, came back on to Ubuntu, reinstalled one more time, and now it works!

I'll let you know if this is a fluke or not....

Thanks so much for your help, chili! :D

EDIT: Is there anything else I should do to make sure this configuration stays working?  Also, it appears that I have to unplug and replug my adapter every time I reboot (but I haven't rebooted since a successful connection). This happens in Windows, also.

---

### Post by chili555 on 2012-01-29
> **LoserDude27 said:**
> It's working!!  I rebooted into Windows to do a remote assistance for someone, came back on to Ubuntu, reinstalled one more time, and now it works!

I'll let you know if this is a fluke or not....

Thanks so much for your help, chili! :D

EDIT: Is there anything else I should do to make sure this configuration stays working?  Also, it appears that I have to unplug and replug my adapter every time I reboot (but I haven't rebooted since a successful connection). This happens in Windows, also.Please try this:```
sudo su
echo rt3572sta >> /etc/modules
exit
```Now does it start on boot?

Your rtusb_dev_id.c file looks perfect! Nicely done.

---

### Post by LoserDude27 on 2012-01-29
Works great. Thanks again!

---

### Post by chili555 on 2012-01-29
> **LoserDude27 said:**
> Works great. Thanks again!Glad it's working! Would you please use Thread Tools at the top and Mark Solved?

---

### Post by LoserDude27 on 2012-01-29
Done.

But I have another complicating matter now... Every so often, I'll lose connection to the internet while still connected to the router.

This sounds like a router issue, but I've never had this problem with Windows.  A simple unplug-replug solves the issue, but I don't want to have to do that while I'm in the middle of something important.

Any ideas?

---

### Post by chili555 on 2012-01-30
> Any ideas?Is there a logging capability on your router? On my ancient WRT54G with dd-wrt, it must be enabled. I'd start there.

---

### Post by LoserDude27 on 2012-01-30
I have DD-WRT also, so I'll try to find out. Thanks!

---

### Post by chili555 on 2012-01-30
> **LoserDude27 said:**
> I have DD-WRT also, so I'll try to find out. Thanks!It's under Security > Log Management.

---

### Post by LoserDude27 on 2012-01-30
In my incoming log, I see lots of drops for two IPs starting with 10. and 172. with something called bootpc. But it doesn't seem like I'm getting dropped as many times as I see listed. I also have several devices set up to automatically connect to wifi when in range, so I don't know which is which.

What does this mean and how can I fix it? How can I find out which IP is being assigned to which device? I only see 192.168. IPs in the LAN.

---

### Post by chili555 on 2012-01-30
> **LoserDude27 said:**
> In my incoming log, I see lots of drops for two IPs starting with 10. and 172. with something called bootpc. But it doesn't seem like I'm getting dropped as many times as I see listed. I also have several devices set up to automatically connect to wifi when in range, so I don't know which is which.

What does this mean and how can I fix it? How can I find out which IP is being assigned to which device? I only see 192.168. IPs in the LAN.Wierd. 10.xx and 172.xx are typically internal LAN IP addresses. In the setup for your router, it almost certainly specifies DHCP addresses in the 192.168.x.y range _only_. You might get some clues with *whois*; for example:```
whois 10.24.36.125
#

<snip>

NetRange:       10.0.0.0 - 10.255.255.255
CIDR:           10.0.0.0/8
OriginAS:       
NetName:        [COLOR="Red"]PRIVATE-ADDRESS[/COLOR]-ABLK-RFC1918-IANA-RESERVED
NetHandle:      NET-10-0-0-0-1
Parent:         
NetType:        IANA Special Use
Comment:        This block is used as private address space.
<snip>
```It is natural to get attempts to connect from the outside world which are dropped by the router because they don't have the WPA2 password.

---

### Post by LoserDude27 on 2012-01-30
Yeah, all of them seem to be private addresses (like your example) from the IANA (according to the WHOIS's), but their site ([http://www.iana.org/abuse](http://www.iana.org/abuse)) claims that they don't own those IPs, they just reserve them...

[QUOTE=http://www.iana.org/abuse]It is perfectly normal to see traffic from these numbers if you have a small home or office network. By default, most routers and access points use these numbers to assign to your local computers. It is most likely these numbers represent computers on your own internal network.[/QUOTE]

However... I don't have any local machines with 10.x.x.x.  There seem to be about four distinct IPs being dropped with UDP and bootpc. Should I be worried about an attacker?

---

### Post by chili555 on 2012-01-30
> Yeah, all of them seem to be from the IANANope; *NONE* of them are from IANA. IANA is simply the mechanism that quasi-regulates a simple system so that everyone gets a unique external address so that you don't get Yahoo when you are looking for Amazon. Therefor, they are also a logical look-up resourse to find out *who is* knocking on your virtual front door. If your home or office neighborhood is the least bit crowded, it will be natural for your router to "hear" knocks from other computers' wireless radios asking if there is a router with an IP address for them to use. When you see a 10.xx that was dropped, your router simply said, "If you want a 10.xx address and you also don't have my password, then no; go away."

Aside from those harmless entries, is there anything else that looks funny?

---

### Post by LoserDude27 on 2012-01-30
Oooh ok. 

Nothing else at all, but it's a temporary log which refreshes a lot and I haven't been dropped very recently. Is there a way to save the log so when I get dropped I can see it?

---

