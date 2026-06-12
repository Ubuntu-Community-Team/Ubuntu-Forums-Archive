---
title: "Belkin PCI wireless-g with BCM4318 chip set"
date: 2009-08-06
forum: Networking &amp; Wireless
---

### Post by a.m.wink on 2009-08-06
Hi,

I posted this earlier by tacking it at the end of an existing thread ([http://ubuntuforums.org/showthread.php?p=7739655#post7739655](http://ubuntuforums.org/showthread.php?p=7739655#post7739655)), but not so sure now if it is the same problem.

Just installed Kubuntu 9.04 (linux kernel 2.6.28-11) on my Athlon 1GHz with 1GB memory.

I checked:
1. lspci: shows the Broadcom 4318 controller
2. iwconfig: shows wlan0 (used iwconfig wlan0 successfully to set ESSID)
    worryingly, TX-power, signal level, noise level etc are all 0
3. lshw gives the message
...
         network:0
         ... eth0 configuration ... (eth0 is not plugged in)
         network:1
         ... wlan0 configuration ...
...
*-network:0 DISABLED
  description: wireless interface
  physical id: 1
  logical name: wlan0
  serial: 00:17:3f:86:bb:cd
  capabilities: ethernet serial wireless
  configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
*-network:1 DISABLED
  ... eth0 properties ...
...

So the problem seems to be that (1) eth0 is network:0 in one place, and network:1 later, and wlan0 vice versa, and (2) both network interfaces are listed as DISABLED.

The eth0 card being disabled is not a problem (I have no ethernet cable) but wlan0 is disabled as well (not strange that it finds no networks!).

What needs to be done to enable the wlan0 interface? Is it a driver problem?

Many thanks for your help!
Alle Meije

---

### Post by gunksta on 2009-08-06
That card is a known problem:

[http://bcm43xx.berlios.de/?go=devices](http://bcm43xx.berlios.de/?go=devices)

4318 	PCI/Cardbus 	Unstable (transmission power issues, work in progress)
I'm sure the existing community documentation has instructions for how to use ndiswrapper and fw-cutter to use ndiswrapper (basically a form of driver emulation). I thought most of these cards were working with a mainline kernel these days, but evidently not.

Do remember to blacklist the bcm43xx driver before trying to use ndiswrapper, otherwise they will fight one another and the card won't work.

---

### Post by gunksta on 2009-08-06
This looks like it could be useful to you.

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

EDIT: HOLY S%$#T the thread is 196 pages long!

---

### Post by a.m.wink on 2009-08-06
Thanks for the reference!

I skipped to the last page and found that I dont have modules bcm4318 or ndiswrapper. Most solutions (such as the one using fwcutter) work only when you have internet. That is a Catch-22!

lsmod shows me that I do have a module b43, and no module wl, bcm4318, or ndiswrapper. 

Any thoughts?

Cheers
Alle Meije

---

### Post by alleycatuk on 2009-08-06
Hi,
I just posted on how I got the same chipset working without ndiswrapper - [http://ubuntuforums.org/showthread.php?t=1233448](http://ubuntuforums.org/showthread.php?t=1233448)

Hopefully that may help you out? I originally tried with ndiswrapper but it was very very hit and miss.... now I get wireless there when I boot up!

Good luck!

---

### Post by gunksta on 2009-08-07
I would start with [alleycatuk]("http://ubuntuforums.org/member.php?u=882660")'s link. I always recommend avoiding ndiswrapper if possible. I respect the work the ndiswrapper guys have done but it is ultimately a sub-optimal solution.

---

### Post by a.m.wink on 2009-08-12
Thanks guys,

I found a way to make my card work (TXpower not 0 any more) and find the wireless router (it's listed in `iwlist wlan0 scanning`), what I haven't got working is the DHCP communication that happens after the router is found. That wpa_supplicant seems the best way to do it.

It's very nice that there is a non-ndiswrapper solution for this, and what's more that is text-based doable by root. The Kubuntu solutions all seem to go through KDE windows, and have to be repeated every KDE session!

Will let you know how I get on, thx again

Alle Meije

---

### Post by a.m.wink on 2009-08-12
Hmm. My card is working now, it finds my router with SSID 'madness', and wpa_supplicant was already installed. So I skipped to step, and changed /etc/network/interfaces and /etc/wpa_supplicant.conf

The result after a reboot is still the same though, no network, and KDE lists the wireless as 'unmanaged'.

Any ideas?

---

### Post by a.m.wink on 2009-08-13
There is definitely something wrong with my wpa_supplicant setup. When I turn of the WPA(1) security on the router and remove wpa_supplicant from the /etc/network/interfaces files (just add the line "wireless-ssid madness") then get a DHCPOFFER.

That looks like a step forward. For now I know I need to keep WPA out of the story.

However, even after being given an IP address (192.168.0.180, sounds plausible),

* KDE still list the network as 'unmanaged' and the wireless IP address *** 'unk.now.add.ress' or something
* 'ping bbc.co.uk' returns 'unknown host'
* the web browser (konqueror) does not load the google start page

Not sure now if I am connected or not???

Thanks for all your suggestions! It seems this one's about to be cracked.

Alle Meije

---

### Post by gunksta on 2009-08-14
Do you know the IP address of your router? I would try pinging the router to see if you can get a reply locally. Alternatively, if you have another computer on the network you could try pinging it. This would confirm if you are in fact on the network.

---

### Post by a.m.wink on 2009-08-15
It looks like I've cracked it :)

The solution, for those who have come across a similar problem, was twofold in this case:

1. Make the driver working.
    The suggestions on the WWW often assume you have internet 
    (which might not be the case if your wireless does not work).
    I used the directions on
    [http://www.thirdstone.com/blog/2009/07/how-to-install-a-belkin-f5d7010-ver-4000-wireless-card-in-ubuntu-9-04/](http://www.thirdstone.com/blog/2009/07/how-to-install-a-belkin-f5d7010-ver-4000-wireless-card-in-ubuntu-9-04/)
    had to use USB stick to download the files
2. Set up the wireless protocols.
    This one is actually trickier for most people, I think. The site
    [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking#Using_iwconfig_For_wireless-tools_Configuration](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking#Using_iwconfig_For_wireless-tools_Configuration)
    gave me the information on how to eventually get in.

The files that needed editing were

#/etc/wpa_supplicant.conf
###################################
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=root
network={
ssid="TheSSID"
key_mgmt=WPA-PSK
pairwise=TKIP
psk="ThePreSharedKey"
}
###################################

#/etc/network/interfaces
###################################
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
        wireless-essid TheSSID
        pre-up wpa_supplicant -B -Dwext -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf
        post-down killall -q wpa_supplicant
###################################
 
This is so cool because it doesn't rely on WICD, NetworkManager or GUI tools.

Thanks to everyone for your help!

---

