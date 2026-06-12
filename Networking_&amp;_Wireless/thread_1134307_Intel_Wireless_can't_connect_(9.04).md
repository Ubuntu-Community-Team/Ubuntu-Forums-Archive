---
title: "Intel Wireless can't connect (9.04)"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by shaze on 2009-04-23
Hi Guys,

Just installed on a Dell D410 (all intel) laptop, and no matter what I try, I can't get the wireless to connect to any network. For the past releases I have been using a HEX/128 bit key without issue, but now it seems that it won't connect to any network; no matter the security type. Wired connections work as expected, but all the wifi networks I try to connect to either time out, or prompt me for passphrase again.

I can't seem to find anything regarding this, and would appreciate any assistance you could provide.

Kind Regards,
Shaze

---

### Post by shaze on 2009-04-24
Output of "sudo lshw -C network"

description: Wireless interface
product: PRO/Wireless 2200BG [Calexico2] Network Connection
vendor: Intel Corporation
physical id: 3
bus info: pci@0000:02:03.0
logical name: eth1
version: 05
serial: 00:13:ce:52:a1:4c
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated
*-network DISABLED
description: Ethernet interface
physical id: 2
logical name: pan0
serial: be:b7:e7:fa:72:79
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

please help, this sucks

---

### Post by shaze on 2009-04-24
Just setup XP on the laptop, tested that the Wireless is working correctly with the latest Intel driver.

---

### Post by rlzyoner on 2009-04-24
This should be helpful.

[http://www.debuntu.org/2006/03/27/9-how-to-ipw2200-getting-intel-pro-wireless-2200-bg-to-work-on-debian-ubuntu](http://www.debuntu.org/2006/03/27/9-how-to-ipw2200-getting-intel-pro-wireless-2200-bg-to-work-on-debian-ubuntu)

---

### Post by shaze on 2009-04-24
I appriciate the response and followed the instructions to recompile my wireless driver with the latest firmware and 80211 subsystem. It seemed to compile and apply itself without error, however it did not fix the issue. 

As before I can still see all the wireless networks in my building, but when attempting to connect to them it times out or prompts me with the password screen again. 

Again to clarify, it seems that both sets of drivers are working to allow the card to recognize and function correctly; with the exception of establishing any connection. Also, every other past version of Ubuntu I've tried has worked flawlessly, with the exception of 9.04. So it appears that while this may have been related to a driver issue back in 2006, it was since fixed for at least 2-3 releases and this may be a new bug.

I welcome any other assistance or advice, thank you for replying!

---

### Post by richrussell on 2009-05-06
Oddly, wifi on my D410 worked straight away in 9.04. I am using 128 bit WEP (because my other laptop doesn't support WPA).

---

### Post by crom.osec on 2009-05-06
I've had same problem on kubuntu 9.04.

My solution was:
I've removed the network manager and I've changed myself the /etc/network/interfaces file as follows (for wep security):

auto wlan0
iface wlan0 inet static
address xxx.xxx.xxx.xxx
network xxx.xxx.xxx.0
netmask 255.255.255.0
gateway xxx.xxx.xxx.1
wireless-essid <Your Essid here>
wireless-key s:<your Essid password here>
dns-nameservers xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx


hope that helps.

---

### Post by montevjl on 2009-05-06
Hi
I've been fidling for a few days with same issue on a Fujitsu-Siemens Amilo M1439G which now runs Ubuntu 9 and fully updated. It had before 8 for a few days and problem was identical, even worse at the beginning since I had to use the windows driver utility to load the card driver!


- the PRO/Wireless 2200BG [Calexico2] has its drivers loaded but it refuses to connect to a router without ANY protection. (wlan1)
So I took an old usb fm Netgear and plugged it in. (wlan0)
here is the status of network:
-*-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:01:03.0
       logical name: wlan1
       version: 05
       serial: 00:12:f0:66:6b:d0
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+w29n51 driverversion=1.53+Intel,09/12/2005,9.0.3.9 latency=64 link=no maxlatency=24 mingnt=3 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: eth0
       version: 10
       serial: 00:03:0d:30:a7:35
       size: 10MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=r8169 multicast=yes port=MII speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0f:b5:00:ef:ad
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.100 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 5a:a5:06:28:59:8e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:2
       description: Ethernet interface
       physical id: 3
       logical name: pan1
       serial: fe:81:4b:cb:de:b1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=192.168.20.1 link=yes multicast=yes

I tried wo use WICD but had to drop because of connection problems when using an HSDPA phone (WICD doesn't see the connection the way NetworkManager does), and by the way keep it in mind if someone uses both wifi and dial-up.

I guess I read and somehow tried every single post on the issue: nothing works. I went to FSiemens website and posted... nothing. Intel gives some sort of a tutor (pretty bad since it misses many "details" and therefore is of little use to a beginner).

I even found something that mentioned to use a little device manager from Acer (I beleive) to "wake-up" special keys management. The wireless lights never turn on! No matter in what position is the switch... but I guess this is firmware and has todo with firmware updates.

If anyone has a clue on where to put fingers ! (I tried several wireless tools like wireshack to check if they could log any traffic on that device. Nothing, hardware is there but dead.
Mny tks
/jl

---

### Post by crom.osec on 2009-05-06
So, you are able to see the networks but you are not able to connect. Have you tried my previous suggestion?

---

### Post by shaze on 2009-05-06
> **crom.osec said:**
> I've had same problem on kubuntu 9.04.

My solution was:
I've removed the network manager and I've changed myself the /etc/network/interfaces file as follows (for wep security):

auto wlan0
iface wlan0 inet static
address xxx.xxx.xxx.xxx
network xxx.xxx.xxx.0
netmask 255.255.255.0
gateway xxx.xxx.xxx.1
wireless-essid <Your Essid here>
wireless-key s:<your Essid password here>
dns-nameservers xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx


hope that helps.

Not only did it not help, it made my situation much worse; allow me to explain. Following your instructions I removed network-manager and found that this disabled all my network interfaces; to be expected, I suppose. I then manually edited my /etc/network/interfaces file, and hardcoded the values as you suggested and rebooted. Nothing except the loopback value showed in ifconfig, so I played with the interfaces file again, and tried using your "xxx" values instead of the ones specific to my router. Again nothing showed, and as I can no longer reinstall any packages, I am forced to reinstall Ubuntu.

richrussell: Thanks for confirming that your laptop connected to your wireless network without issue. As my comments described below, I have tried connecting to multiple security types with the same result.

montevjl: This is the most frustrating issue with Linux I have ever had, and my launchpad bug I submitted has been ignored. You are not alone in your attempts though, as I have tried similar steps to no avail. Which would lead me to think that I have a defective wireless adapter, except that it works perfectly in XP/Vista/7, and even OSX (iDeneb).

---

### Post by cgb223 on 2009-05-09
i'm using an acer 7720 aspire laptop and am having the same issues. i see all the networks but when i try connecting to a non password protected wireless it tries and tries and tries and then says disconnected. i am dual booting with vista so to confirm i checked with that and it works fine.

Help? this seems to be a cross hardware problem, not just something related to one specific kind of computer or hardware.

---

### Post by montevjl on 2009-05-10
sorry, came back late... had not bookmarked the tread!
I confirm, the chip is seen, drivers loaded and firmware updated.
- Networkmanager fine and running perfect
- the Fujitsu-Siemens Amilo led doesn't turn on (trivial :-))

If I use the Windows driver thru "Windows Wireless Drivers", the Intel 2200BG is seen, else ... nothing.
I guess I should be on the go for an Atheros' chip!

I'm sorry I couldn't of any help.

---

### Post by asg1290 on 2009-05-13
This kinda anoys me, I put this ipw2200 in my laptop to replace the bcm4603 because it has "better support"  Ironically the bcm4603 worked better than the ipw2200 in 9.04 jaunty.  Anyway I cannot for the life of me connect to any G access points regardless of AP security settings using the ipw2200 driver included.  When I set the AP to B only it does connect and work fine.  It will see the G AP but cannot associate.  I know this card works in windows so it must be jaunty.

---

### Post by dughutch on 2009-05-19
I, too, am having issues. Platform is new Dell E6500 and everything works under WinXP Pro. I cannot connect to wireless networks... very odd...

---

### Post by dughutch on 2009-05-19
Well, a reboot made a liar out of me... now the wireless is working to a WEP encrypted AP... strange.

I had been fooling around with Kismet before... wonder if that messed something up?

I rebooted and everything came up and just worked... like I'm used to Ubuntu doing... a pleasant surprise but I'm curious why it failed before...

Hmmm....

---

### Post by rbond on 2009-05-20
I have a similar problem on an HP Compaq 8510p.

I can connect to my home network with WPA. (however, it drops me and reconnects every few minutes which is annoying).

I am unable to connect to any network without security. NM can see the networks, but does not connect. Reviewing the wpa_supplicant.log you can see that it briefly connected and then disconnected. It repeats this many times throughout the logs.

---

### Post by dadabear on 2009-05-20
Hi, i have installed ubuntu 9.04 (wubi) in my compaq 6510b, everything is fine except for the wifi.  I cannot detect any network here  but if i used windows its working.  I also tried wired network and it works.  I also updated my ubuntu (using wired network). Please help me. Thanks

---

### Post by rbond on 2009-06-28
Posting in case this helps someone. I have been following a few wifi related threads because I had problems with wifi after upgrading to Jaunty.

In the past I had manually setup my wifi WPA settings in the /etc/network/interfaces file. Then I started using the Gnome Network Manager. My manual settings did not cause a problem until I upgraded to Jaunty. Just for the heck of it I removed the manual settings from my file and it fixed the problems that I had. 

I know that for some people this is a kernel issue, but for me it turned out to be a problem with Gnome Network Manager not liking my config settings.

If you are having problems and you had previously manually configured settings, back up your current copy and try to revert to only auto settings such as this....

```
auto lo
iface lo inet loopback


iface eth1 inet dhcp

auto eth1

iface wlan1 inet dhcp

auto wlan1

```Hope this helps someone.

Forgot to note this: For the newbies - the eth1 and wlan1 values may be different on your machine. Use the network interface names for your machine.

---

### Post by Halfling Rogue on 2009-07-20
Been having the exact same problem with Jaunty on a slapdash IBM ThinkCentre 8187 (at least I think that's the model number) desktop with a Texas Instruments ACX 100 22mbps wireless interface. It can see local connections, but it can't connect to any of the encrypted ones -- it just prompts for the passphrase over and over again.

Our router is currently using a WEP 128-bit passphrase, and my laptop (a Dell Latitude D600 with another Texas wireless card) can connect just fine to the router. My laptop was running Hardy Heron until recently; I just did the online upgrade to Jaunty, and my connection remained intact. (Unlike the IBM, which I had Jaunty installed on scratch from CD.) I noticed that the Wireless Networks seem to have maintained my Hardy configurations (which were nothing special), which may be why it's still working. My laptop's Wireless Network info also informs me that it's storing the key as a WEP 64/128-bit Hex -- but Jaunty on the IBM only gives me the option of WEP 128-bit Passphrase or WEP 40/128-bit Key (along with LEAP and Dynamic WEP). Maybe that's where the problem lies?

Would like to see this fixed soon, it seems like a major problem for what's supposed to be the current stable version.

---

### Post by Halfling Rogue on 2009-07-20
> **rbond said:**
> If you are having problems and you had previously manually configured settings, back up your current copy and try to revert to only auto settings such as this....

```
auto lo
iface lo inet loopback


iface eth1 inet dhcp

auto eth1

iface wlan1 inet dhcp

auto wlan1

```Hope this helps someone.

I get told that auto isn't a command. Am I missing a package?

---

### Post by Halfling Rogue on 2009-07-20
Update: I managed to get a connection (not sure how; I think it was because I entered the WEP key in straight with 40/128 and input the bssid), but the internet refuses to go anywhere, so it's clearly still not accessing the router.

---

