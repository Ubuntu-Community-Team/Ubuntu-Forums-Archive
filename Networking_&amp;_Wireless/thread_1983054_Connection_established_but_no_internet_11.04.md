---
title: "Connection established but no internet 11.04"
date: 2012-05-19
forum: Networking &amp; Wireless
---

### Post by PTo on 2012-05-19
A bit more than a week ago my internet suddenly stopped working on my Ubuntu 11.10. Restarting the modem didn't work. When I plug the cable in my windows laptop I have internet so it isn't a problem with the modem. I'm also able to access te modem from my ubuntu-pc

Even when I put the live-cd in it cannot connect to internet. It says 'connection established' but I can't browse the internet or download any updates.

I can ping localhost, but I cannot ping for example google.com

When I look in the interface statistics of the eth0 I see both send and received packages (and the number is increasing) and zero errors.

sudo ifconfig gives:

```
eth0      Link encap:Ethernet  HWaddr 00:1a:a0:b8:39:06  
          inet addr:[MY INETADRESS] Bcast:[MY BCAST]Mask:255.255.252.0
          inet6 addr: fe80::21a:a0ff:feb8:3906/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7970 (7.9 KB)  TX bytes:11465 (11.4 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:488 errors:0 dropped:0 overruns:0 frame:0
          TX packets:488 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:38880 (38.8 KB)  TX bytes:38880 (38.8 KB)
```

gksudo gedit /etc/network/interfaces

```
auto lo
iface lo inet loopback
```

lspci

```
00:00.0 Host bridge: Intel Corporation 82Q963/Q965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82Q963/Q965 PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express (rev 02)
```

I really hope someone can help me because I pretty much tried all I could think of.

---

### Post by PTo on 2012-05-19
Excuse me, in the titel I mentioned 11.04 but I'm running 11.10

---

### Post by PTo on 2012-05-19
Just tried the live-cd 12.04, also no internet :(

---

### Post by PTo on 2012-05-20
I just ran a system test and it said that networking/detect passed (and gave the details of my network card) and that networking/internet failed (no internet connection).
So it seems like nothing is wrong with my network card.

Anyone a good idea what I can do?

---

### Post by steeldriver on 2012-05-20
can you ping by ip? if so possibly a dns issue?

what test did you run, exactly?

---

### Post by PTo on 2012-05-20
Thanks for your reply! I'm getting kinda desperate here...

The test I mentioned in my previous post is the 'system testing' tool that ubuntu provides in the application. I ran it from the livecd 12.04. The output:

networking/detect	PASSED	Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express (rev 02)
networking/internet	FAILED	No Internet connection 


When I ping an IP-adress (using the livecd 12.04 as well) still no success, however a different failure than pinging an adress:

```
ubuntu@ubuntu:~$ ping www.google.com
ping: unknown host www.google.com
ubuntu@ubuntu:~$ ping 69.147.76.15
PING 69.147.76.15 (69.147.76.15) 56(84) bytes of data.
^[^C
--- 69.147.76.15 ping statistics ---
590 packets transmitted, 0 received, 100% packet loss, time 593712ms

ubuntu@ubuntu:~$ ping 62.69.168.13
PING 62.69.168.13 (62.69.168.13) 56(84) bytes of data.
^[^C
--- 62.69.168.13 ping statistics ---
61 packets transmitted, 0 received, 100% packet loss, time 60480ms
```

---

### Post by steeldriver on 2012-05-20
tell us some more about your setup - do you have a router or is it just a modem? what kind (cable? dsl?)

also I noticed you are running a 22-bit netmask (255.255.252.0) - is that intentional or did something get screwed up there?

what does the 'route' command return (i.e. can you see your local gateway)?

just throwing some things out here

---

### Post by rmjones85 on 2012-05-20
try running these commands in the terminal: 

```
sudo ifconfig eth0 down
``````
sudo ifconfig eth0 up
```if that fails try running this in your terminal:

```
sudo /etc/init.d/networking restart
```Good luck

---

### Post by PTo on 2012-05-21
Thanx for the suggestions.

@steeldriver
I have a wired connection directly to my modem (ubee) which is I think some sort of a router and modem in one.
The 22-bit netmask is surely not intentional, I don't even know what it is...
What command do you mean by the 'route' command?

@rmjones85
I tried all three but no success unfortunately... It disconnects and reconnects the wired connection however still no internet.

---

### Post by steeldriver on 2012-05-21
I just mean 

```
$ route
```

The reason I was asking about your setup is some cable services are tied to 1 or 2 MAC addresses, if you have been plugging different computers in and out it is possible the modem has bound to one of those and is now rejecting this one - 'route' would at least tell us if your computer can see a gateway; and then maybe traceroute after that

---

### Post by PTo on 2012-05-21
Ok, that was easier than I thought :)

The outcome:

```
ubuntu@ubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         83.84.84.1      0.0.0.0         UG    0      0        0 eth0
83.84.84.0      *               255.255.252.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
```

I don't know if this is good or bad.

When I looked into my modem I found one 'cable modem MAC' and three 'CPE MAC' adresses. The MAC adress displayed in the connection information is one of the three CPE MAC adresses.

---

### Post by steeldriver on 2012-05-21
OK well it's good that your MAC is in the CPE list (Customer Premises Equipment - i.e. what is on your side of the gateway)

Can you ping the gateway (83.84.84.1) ?

Is your 'inet addr:' (from ifconfig) within the subnet (83.84.84.2 - 83.84.87.254 I think)?

---

### Post by PTo on 2012-05-21
Thanx again. Pinging the gateway gives a 100% package loss.

My inet adress in the ifconfig is 83.84.85.103

---

### Post by rockballad on 2012-05-21
You might try to change /etc/resolv.conf: add nameserver.

---

### Post by PTo on 2012-05-21
There is a nameserver in the /etc/resolve.conf being:

nameserver 127.0.0.1

What I don't understand is, if it's a problem with the settings of my Ubuntu, how come it doesn't work with the livecd as well? At the moment I'm doing everything with the livecd to make sure my settings are as 'pure' as possible, does that make sense at all?

---

### Post by steeldriver on 2012-05-21
If it is this ubee modem / router: 

[https://static.ziggo.nl/images/20110426_Geavanceerde_gebruikershandleiding_internet_UBEE_v1.0_web_tcm14-15225.PDF](https://static.ziggo.nl/images/20110426_Geavanceerde_gebruikershandleiding_internet_UBEE_v1.0_web_tcm14-15225.PDF)

then I think you need to work through the setup again - you really shouldn't be seeing 83.84.xxx.xxx addresses on the LAN side - that is your ISP / WAN side - you should only see addresses like that if you are running a simple modem (i.e. no address translation)

---

### Post by PTo on 2012-05-22
Ok I called ziggo today and found out that I don't have the modem/router you mentioned but a simple modem. Didn't know that... So that explains the 83.84.xxx.xxx adress.

They also said that I shouldn't be plugging the cable in and out two different computers because it will give an IP to one computer and reject the other, corresponding to what you said. (However I have been doing this like 25 times without a problem) They told me I should unplug the modem and then put the elecricity back on and it would reassign the IP-adress. I tried it but without success :(

I also tried to reset the modem but no luck either.

You mentioned something about the 22-bit netmask. Could that be the cause?

---

### Post by steeldriver on 2012-05-22
Hmm well the 22-bit netmask is explained by the fact that you are not on a private LAN - it allows the ISP to have up to 1022 hosts on that subnet. As long as your MAC is listed as one of the CPE addresses that *should* be OK too I think.

Obviously your /etc/resolv.conf is going to be a problem for DNS but I would not think it should stop you pinging by IP especially not even the gateway itself. FWIW *I* can ping 83.84.84.1 so we know it isn't blocking ICMP echo requests. You could manually change resolv.conf to point at one of the ziggo DNS servers or to one of opendns or google's nameservers however these days I would expect everything to be done automatically via DHCP.

Have you looked at your /etc/network/interfaces and /etc/NetworkManager/ yet?

```
cat /etc/network/interfaces

cat /etc/NetworkManager/NetworkManager.conf

ls /etc/NetworkManager/system-connections/

```In the last case there should be a file(s) describing your connection which you will need to open as root because it may have wireless keys and so on - you could check what it says under [ipv4] 

**Please don't post the  contents here without masking any authentication information (passwords, wireless keys etc.)**

You could also try 

```
tracepath 8.8.8.8
```but I don't really think it will go far since you apparently can't ping the default gateway. 

This is just how I would trouble shoot it - I am by no means an expert, maybe there is an obvious answer I am overlooking

---

### Post by hipogrito on 2012-05-22
Hi,

> **rockballad said:**
> You might try to change /etc/resolv.conf: add nameserver.


I solved my problem thanks to that.

[http://ubuntuforums.org/showthread.php?p=11960085#post11960085](http://ubuntuforums.org/showthread.php?p=11960085#post11960085)


Thanks,

Regards,
Hipo

---

### Post by PTo on 2012-05-23
@Hipo I tried to clear the /etc/resolv.conf in my normal 11.10 environment but no luck. It contained two nameservers which correspond to the primary and secondary DNS. After reboot it refilled it with the same stuff.

@steeldriver: this is the outcome of the commands you mentioned. I tried to look up the file eth0 using nautilus. Under ipv4 it says *method=auto *
As you expected tracepath 8.8.8.8 gave no response.

I'm starting to doubt if I will ever get my internet back...

```
x@x:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback



x@x:~$ sudo cat /etc/NetworkManager/NetworkManager.conf

[main]
plugins=ifupdown,keyfile

no-auto-default=[MAC ADDRESS],

[ifupdown]
managed=false
x@x:~$ sudo ls /etc/NetworkManager/system-connections
eth0
```

---

### Post by steeldriver on 2012-05-23
that all looks fairly sensible to me - obviously we could probe down into the eth0 definition file

but I'm starting to wonder if it might be a hardware or driver issue? can you try

```
$ grep eth0 /var/log/dmesg 
```

---

### Post by PTo on 2012-05-23
Ok, I think there is some problem in de last line:

```
awadi@OptiPlex-745:~$ grep eth0 /var/log/dmesg
[    3.690995] tg3 0000:03:00.0: eth0: Tigon3 [partno(BCM95754) rev b002] (PCI Express) MAC address 00:1a:a0:b8:39:06
[    3.691001] tg3 0000:03:00.0: eth0: attached PHY is 5787 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    3.691006] tg3 0000:03:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    3.691009] tg3 0000:03:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   17.288107] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

---

### Post by PTo on 2012-05-23
I just checked on this site [http://kmuto.jp/debian/hcl/]("http://kmuto.jp/debian/hcl/"). It seems I have the correct driver.

PCI ID -  Works? - Vendor - Device - Driver - Kernel
14e4167a - Yes - Broadcom Corporation - NetXtreme BCM5754 Gigabit Ethernet PCI Express - tg3 - v2.6.25-

---

### Post by steeldriver on 2012-05-23
have you tried using a different ethernet cable? does the computer have a second LAN interface (e.g. one on the mobo and a pci one) that is somehow not being detected?

can you provide any make/model info on the modem?

you can also get driver information with

```
$ ethtool -i eth0
```

---

### Post by PTo on 2012-05-23
Thanx again for all your effort.
I didn't try another cable, however it is the same cable I'm using right now in my windows laptop so it seems to work. There is just one entry to connect the utp-cable to my computer (on the back side)
My modem is an Ubee EMV3200. Ethtool gives back that it is not installed.

I would say that my network card is fine to as it is able to detect a connection and my computer is able to detect the network card. But maybe I'm thinking to easy now? Unfortunately I don't have one left that I could use to try.

---

### Post by steeldriver on 2012-05-23
I'm sorry we don't seem to be getting anywhere...

all I can suggest is it's a minor driver or firmware revision that's broken something? e.g.

[http://blog.sat.iit.edu/2012/05/ubuntu-11-10-tg3_stop_block-error/](http://blog.sat.iit.edu/2012/05/ubuntu-11-10-tg3_stop_block-error/)

---

### Post by PTo on 2012-05-24
Maybe I should just try to do a fresh install of 12.04 even though there is no internet on the livecd as well. I saw the driver is part of the kernel so perhaps the 11.10 kernel is somehow affecting the livecd? (I don't know whether that could be possible)

Let's hope for a miracle... :)

---

### Post by steeldriver on 2012-05-24
Aside from a possible driver / firmware issue, you have a somewhat non-standard configuration which is difficult to help with since I don't know why or how it was set up like that

AFAIK, the default setup using network-manager is to have an automatic 'Wired connection 1' with automatic IP configuration and automatic routes - this connection does not appear in /etc/NetworkManager/system-connections because there's nothing user-configurable. It usually 'just works' (at least in a LAN based setting).

In your case your primary wired connection apparently *is* in /etc/NetworkManager/system-connections - that could be for good reasons (e.g. requirements of your modem or ISP) or it could be because something went wrong

You *could* try restarting network-manager in an absolutely default config and seeing if it is smart enough to figure out the correct settings for you - either by purging and reinstalling the package (after backing up your current config files of course) or by moving the non-default system-connections file, removing your router's MAC from the no-auto-default list, and restarting network-manager. If you want a step-by-step for that post back and I will try to walk you through it.

BTW have you actually looked at the connection details (NetworkManager applet on the toolbar --> Edit Connections... select the wired connection you are trying to use and click Edit) to see if anything looks screwy?

---

### Post by PTo on 2012-05-24
I looked several times at the connection details and as far as I can tell it looks quite normal to me. If have no idea how I got this non-standard configuration, I never conciously changed anything in it.

Perhaps I could try do the install of 12.04 first. If it is a driver/firmware problem or a problem with my configuration the new install would probably repair it and I want to go to 12.04 anyway. It's a bit more work to reinstall the programs I have now but it will clean up all the messy stuff.

---

### Post by PTo on 2012-05-24
Just did a fresh install of 12.04 but still no luck... Possibly there is a problem with my NIC even though it is being detected.

---

### Post by PTo on 2012-05-26
Just went to the computerstore yesterday and they assured me that if both lights are on, one blinking and the other not, it's not a problem with my NIC. I'm kinda stuck right now...

Let's recapitulate:

Modem + cable --> working on my laptop so not the problem
Ubuntu settings --> always worked, changed nothing when it suddenly stopped and I now have fresh install. So doen't seem the problem to me?
NIC --> Both lights are on and can be detected so not the problem
Driver --> It seems I have the correct driver. Internet worked on 11.10, then suddenly stopped. So if this is the problem it would mean something got changed in the driver without me noticing and this thing is still broken in 12.04. Is this possible?

Do I miss a possible cause?

---

### Post by steeldriver on 2012-05-26
The only thing I can think to try at this point is a completely default NetworkManager conf i.e. stop network-manager, move any non-default connections out of the system connections dir to somewhere it won't find them, remove your no-auto-default line from the config file and then restart n-m. 

I'm really just throwing this out as an idea though.

Post back if you want to give it a try  - I can step you through exactly how I mean

---

### Post by PTo on 2012-05-26
I think we should give it a try. The only other option I can think of now is to install windows to see if it will work then.

---

### Post by steeldriver on 2012-05-26
OK let's first double-check we are dealing with NetworkManager not the older networking interfaces (although your minimal /etc/network/interfaces file suggests we are):

```
sudo service networking status

sudo service network-manager status
```

---

### Post by steeldriver on 2012-05-26
... then (assuming that only network-manager responded as running), stop it with

```
sudo service network-manager stop
```I think it's also OK to 

```
sudo rm /var/lib/NetworkManager/NetworkManager.state

``` in case state information persists across restarts (I don't know).

Then backup the conf file and move any existing connections someplace else 

```
sudo cp /etc/NetworkManager/NetworkManager.conf /etc/NetworkManager/NetworkManager.conf.old
```and

```
sudo mkdir /root/system-connections.old

sudo mv /etc/NetworkManager/system-connections/* /root/system-connections.old
```[it doesn't have to be there, that just seems like a good place since the system-connections files are supposed to be root:root and mode 600]

Then either

```
gksudo gedit /etc/NetworkManager/NetworkManager.conf
```and delete the no-auto-default line (or comment it out with a # at the start)

or, if your sed-fu is strong, 

```
sudo sed -i 's/^no-auto-default/# &/' /etc/NetworkManager/NetworkManager.conf
```and then restart network-manager

```
sudo service network-manager start
```You should then see it has created a default wired connection e.g. 'Wired connection 1' which you can view / edit via the taskbar applet; you could also run

```
nm-tool
```from the command line which should give you the same connection information.

If it doesn't help (I'm not holding my breath - it's just something to try), you can always reverse the steps to put everything back as before.

---

### Post by PTo on 2012-05-27
Still no luck. I have to say that there was no no-auto-default line in the NetworkManager.conf. It only contained:

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

How can I reverse the steps?

After the install of 12.04 the eth0 is als no longer in the system-connections.

---

### Post by steeldriver on 2012-05-27
OK so I'm confused - I based my suggestion on what you'd posted previously (post #20). If you already had a default wired config as a result of other reconfigs/updates then the commands I suggested would have had no effect.

FWIW you would reverse the steps by stopping the network-manager service  once more, moving any non-default config files back to  system-configurations, and copying the NetworkManager.conf.old file back  over top of the modified NetworkManager.conf file; then restarting the   network-manager service. However it seems like you already had a default config so nothing would have been modified in the first place.

Regardless, do you now have a default wired connection showing when you open the network manager applet? What does

```
nm-tool
```say?

---

### Post by PTo on 2012-05-28
My apologies for the confusion. A little while after post #20 I did a clean install of 12.04 bringing everything back to default. I didn't change anything in it. However it was an install without internet so I guess I don't have the latest updates.

nm-tool says:

```
NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        00:1A:A0:B8:39:06

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         83.84.85.103
    Prefix:          22 (255.255.252.0)
    Gateway:         83.84.84.1

    DNS:             212.54.40.25
    DNS:             212.54.35.25
```

---

### Post by steeldriver on 2012-05-28
no problem! I'm just sorry to have made you type all those commands... for nothing :(

is the status exactly the same? what happens now if you try to tracepath to one of the indicated DNS servers?

```
tracepath 212.54.40.25
```

everything else looks good to me so if you still can't get past the gateway then I really don't know what else to suggest - some kind of driver or firmware issue is about all that is left, I guess?

---

### Post by PTo on 2012-05-28
Everything is still the same, no internet. Tracepath gives no reply. I'm really puzzled, when I look at the output of nm-tool it looks pretty normal to me. 
I'm thinking of the driver as well. It's all that is left I guess. Perhaps there has been a driver-update in 11.10 and 12.04 that is causing this. I will try to search on the forum to see if I can find more about this.

---

### Post by PTo on 2012-06-01
I want to try to install the new 3.3.7 kernel hoping it will solve something (since the driver is integrated in the kernel). I found the kernel tar.bz2 on [www.kernel.org ]("http://www.kernel.org")and extracted it in a folder in my home-folder. However now I don't know how to continue the installation. I don't understand the readme very well. How can I install this kernel?

---

### Post by PTo on 2012-06-07
I find it still hard to believe but my problem is solved! Someone had the idea to install a router and gave me his old router. I installed it and at first the internet on my laptop stopped working as well. But then I cloned the MAC-adress of my laptop to the router and now everything is working!!!
So probably using one cable for two computers did mess it up after all (I have no idea why it worked for months though).

Thanks everyone for the advice!:D:D:D

---

