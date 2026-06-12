---
title: "I broke my internet! :("
date: 2012-02-27
forum: Networking &amp; Wireless
---

### Post by spillin_dylan on 2012-02-27
Okay guys (and gals), I really need your help this time.  I'm not sure what I did or how I did it, but my networking on my Toshiba laptop is totally borked.  And has been for a while.

Here's the story:
Maybe a year or so ago, I was trying to set up my old Ubuntu 8.10 laptop with a static IP on wlan0, so I could log into it remotely from my new laptop.  I ended up installing WiCD, uninstalling WiCD, messing around in /etc/network/interfaces and a whole bunch of other files that I shouldn't have touched, and then leaving it all alone for a really long time hoping it would fix itself.  

Well, it didn't.  

So here I am with no network-manager in Gnome, and nothing anywhere else.  I know the hardware works (by using WinXP and the Live CD). 

I don't want to re-install just yet, as there is some stuff I'd like to transfer to my new laptop first.  

Can someone solve this mystery?  I will post the interfaces file (which I think is good) and anything else you might require.  

Thanks In Advance,

spillin

---

### Post by spillin_dylan on 2012-03-01
Bump.  

I know I'm not giving anyone much to go on here, but still hoping for some help.  I think my interfaces and DNS setups are okay; I think the problem lies with connecting wirelessly via CLI to a WPA protected network...?

---

### Post by chili555 on 2012-03-01
There is no question that connecting to a WPA network wirelessly is never going to happen with that interfaces file. Please try this.```
auto lo
iface lo inet loopback

iface eth0 inet static
	address 192.168.1.202
	netmask 255.255.255.0
	gateway 192.168.1.254

auto wlan0
iface wlan0 inet static
	address 192.168.1.222
	netmask 255.255.255.0
        gateway 192.168.1.254
        wpa-essid yournetwork
        wpa-psk yoursecretkey
```If you want to concentrate on wireless, I'd omit the auto eth0 declaration altogether. If you need to switch to wired, hook up the cable and do:```
sudo ifdown wlan0 && sudo ifup eth0
```Please make these changes, reboot and give us your report.

---

### Post by Iowan on 2012-03-02
> **chili555 said:**
> If you want to concentrate on wireless, I'd omit the auto eth0 declaration altogether.+1 Having both interfaces in the same subnet might cause problems (Spanning Tree Protocol).

---

### Post by spillin_dylan on 2012-04-12
Okay, sorry for the delay, but entering the wpa-essid and wpa-psk completely worked!  I think.  I can ping an IP address on my local network, and the outside internet now, but I still have to somehow configure DNS.

I will work on this, but be prepared for more questions!

---

### Post by chili555 on 2012-04-12
> I still have to somehow configure DNS.Pretty simple. Please do:```
sudo gedit /etc/resolv.conf
```Add a new line:```
nameserver 192.168.1.254
```Let the router supply it's nameservers. If you want a go-fast DNS nameserver, instead add:```
nameserver 8.8.8.8
```Proofread, save and close gedit. Test with:```
ping -c3 www.google.com
```It ought to resolve like this:>  ping -c3 [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (173.194.73.105) 56(84) bytes of data.
64 bytes from vb-in-f105.1e100.net ([COLOR="Red"]173.194.73.105[/COLOR]): icmp_req=1 ttl=43 time=38.1 ms
64 bytes from vb-in-f105.1e100.net (173.194.73.105): icmp_req=2 ttl=43 time=37.9 ms
<snip>Depending on your locale Google may not resolve to that exact number, but if the DNS nameserver is working, it ought to resolve to *some* number.

---

### Post by spillin_dylan on 2012-04-12
Okay, so apparently my DNS was set up properly.  All I have is one nameserver 192.168.1.254 and the search workgroup, etc....  I'm sure that part is right.

So I followed the tutorial on [https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic]("https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic"), which got me going a little bit better with the wpa_supplicant stuff.  I now am connected via dhcp (and writing this post to prove it), but I still can't get a static IP.

Thanks so far for everyone's help and patience!

---

### Post by chili555 on 2012-04-13
> I now am connected via dhcp (and writing this post to prove it), but I still can't get a static IP.Assuming you want to connect wirelessly, detach the ethernet cable and do:```
sudo ifdown wlan0 && sudo ifup wlan0
ifconfig
```Don't you get the address you declared in *interfaces*: 192.168.1.222?

You shouldn't have to mess with wpa_supplicant at all, frankly. With the *interfaces* set-up I suggested, no wpa_supplicant.conf file is required. I certainly don't have one!

---

