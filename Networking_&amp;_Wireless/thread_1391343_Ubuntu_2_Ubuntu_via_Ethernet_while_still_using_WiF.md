---
title: "Ubuntu 2 Ubuntu via Ethernet while still using WiFi?"
date: 2010-01-26
forum: Networking &amp; Wireless
---

### Post by 2hot6ft2 on 2010-01-26
I'm wondering if this is even possible. I've searched high and low and have yet to find and answer to this particular setup.

The setup:
Router is in another building.
Desktop connected by WiFi
Laptop connected by WiFi
Both the Desktop and the Laptop are in the same building together. About 5' apart.

SSH server is setup on Desktop
FreeNX client is setup on Laptop

So they can connect just fine via WiFi for remote desktop control of the Desktop from the Laptop (so SSH and FreeNX are working).

All is good so far, so here's the questions.

Is it possible to connect the 2 pc's directly to each other by Ethernet cable AND transfer files between them by Ethernet while still being connected to the Internet by WiFi on them both?

Or would the WiFi have to be disabled while using the Ethernet connection?

Neither has a Gigabit Ethernet NIC so I know it would at least require a crossover cable or another router to connect the 2 by Ethernet cable.

The idea behind all this is to be able to transfer files between computers quickly by Ethernet while the computers are still busy doing other things on the Internet by WiFi.

I know I have other options for how to do the transfer via Ethernet like FileZilla and vsftpd. But the question still remains, can it be done.

I'm suspecting that this can't be done.

Thanks in advance.

---

### Post by Fire_Chief on 2010-01-26
Sure it can be done. This is actually pretty easy.

First choose an IP subnet that is different from what you are getting on your wireless network (i.e. 10.10.10.0).
On each system, edit the Wired network connection through NetworkManager and assign a static IP address to each one (laptop uses 10.10.10.1 and desktop uses 10.10.10.2 for example). 
Set the subnet mask to 255.255.255.0 on both.

Do NOT set a gateway on either system. This is important. By not setting a gateway you allow the default Internet gateway on the Wireless network to still work.

Once you have each system setup, connect your crossover cable between them. You should now be able to communicate between the systems (ping, ssh, file shares, etc). Be sure to use the 10.10.10.x address to connect to the target system and it will use the wired connection.

Make sense?

Cheers!

---

### Post by 2hot6ft2 on 2010-01-26
> **Fire_Chief said:**
> Sure it can be done. This is actually pretty easy.

First choose an IP subnet that is different from what you are getting on your wireless network (i.e. 10.10.10.0).
On each system, edit the Wired network connection through NetworkManager and assign a static IP address to each one (laptop uses 10.10.10.1 and desktop uses 10.10.10.2 for example). 
Set the subnet mask to 255.255.255.0 on both.

Do NOT set a gateway on either system. This is important. By not setting a gateway you allow the default Internet gateway on the Wireless network to still work.

Once you have each system setup, connect your crossover cable between them. You should now be able to communicate between the systems (ping, ssh, file shares, etc). Be sure to use the 10.10.10.x address to connect to the target system and it will use the wired connection.

Make sense?

Cheers!
Thanks Fire_Chief

That was the way I was looking at doing it but since I don't have a crossover cable right now I wanted to find out if it would work before getting one.

I'll stop by Unclaimed Baggage tomorrow and pick one up for a couple bucks.
:popcorn:

---

### Post by Iowan on 2010-01-26
You could use a hub/switch and a couple of straight cables, but for a couple of bucks, the crossover would make more sense.

---

### Post by 2hot6ft2 on 2010-01-26
> **Iowan said:**
> You could use a hub/switch and a couple of straight cables, but for a couple of bucks, the crossover would make more sense.
The single crossover also has the advantages of only 1 more cable as opposed to 2 and a hub/switch with power supply being added to all the cables, cords and everything I already have running everywhere. Don't really want anymore stuff to plug in....;)

---

### Post by 2hot6ft2 on 2010-01-27
Looks like it wont work after all. I was able to ping, connect by ssh and freenx via the crossover cable but the wiwfi wouldn't work at the same time.

Guess it's either one or the other but not both at the same time.

I'll keep playing with things but there are only so many settings. Looks lie the only way to do file transfers AND Internet at the same time is to use another router as a bridge and plug both computers in by Ethernet.

Bummer

---

### Post by Iowan on 2010-01-27
Your setup via Network Manager or */etc/network/interfaces*? NM usually only activates one interface at a time.

---

### Post by 2hot6ft2 on 2010-01-27
> **Iowan said:**
> Your setup via Network Manager or */etc/network/interfaces*? NM usually only activates one interface at a time.
Tried it both ways.
Just using System > Administration > Network
And using just the Network Manager Applet on the top panel

I did get it to actually show IP addresses (Using ifconfig) for both the eth0's and wlan0 & wlan1 (respectively server & client) at the same time with the Network Manager Applet.

That was not the case using the setting of
System > Administration > Network
where it would show either a eth0 or wlan0/wlan1 IP address using ifconfig. But not both eth & wlan at the same time.

Hope that makes sense. I would think it would be the other way around like what you're saying.

EDIT: If you mean did I edit /etc/network/interfaces then the answer is no.
I'm not sure how to format the information when adding it to the file since all that is in the file of the client right now is:
> auto lo
iface lo inet loopback
A few more lines in there and I could probably figure out the required formatting.

I messed around until I had to reset the network settings back to square 1....

It's still good though since I just had to delete all the settings I had put in and re-enter the settings for the WiFi. Shouldn't play with the routers configuration at the same time as working on other network configurations...
SSH & FreeNX still work fine.

I'm thinking it would be something like:
> managed eth0
iface eth0 IP=10.10.10.1 sub=255.255.255.0
But I'm just guessing.

---

### Post by Iowan on 2010-01-28
Perhaps you should try */etc/network/interfaces* Edit the file to look something like:```
auto lo
iface lo inet loopback 

iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255

```The last two lines may be unnecessary. You'll want a different address on each machine (of course) and it will probably work better if the subnet (network) is different than the WiFi.

---

### Post by 2hot6ft2 on 2010-01-28
Ok, I think I'll try it with something like this:

> auto lo
iface lo inet loopback 

iface eth0 inet static
address 10.10.1.2
netmask 255.255.250.0
network 10.10.1.0
broadcast 10.10.1.255

Since my WiFi is using
> inet addr:192.168.1.xxx  Bcast:192.168.1.255  Mask:255.255.255.0
I want to stay away from those.

Now to go hard reset the router and load my backup config for it.
I changed something and it's not responding like it should.

Been messing around with PuTTy and stuff trying to get it to where I can SSH in with FreeNX from outside the LAN. Something is still off. I have DD-WRT on the router and a DynDNS address since the IP from my ISP is dynamic.

Forwarded a port to the SSH server but that's another project that I have going. ;)

I can PuTTy in to the router now so I have made some progress there.

By the way I appreciate your help.

---

### Post by 2hot6ft2 on 2010-01-28
That didn't work.

If I put in just the first 3 lines OR all 5 lines then the Ethernet adapter doesn't even show up anymore using ifconfig.

Had to take it all out and reboot to get WiFi back.

Any other ideas?

---

### Post by Iowan on 2010-01-28
255.255.250.0 is not a valid subnet. You can use 255.255.255.0 or even 255.255.255.252 if you only need 2 addresses. I was afraid I might be adding confusion when I said "...subnet (network) is different". The subnet *mask* (netmask) can be the same - the subnet should be different. Your 10.10.1.0 network is OK.

---

### Post by 2hot6ft2 on 2010-01-28
Ok, I'll give it another try using 255 or 252.

---

### Post by Iowan on 2010-01-28
255.255.255.255 will allow only one machine in the subnet. [Here]("http://www.subnet-calculator.com/cidr.php") is a subnet calculator. It shows valid masks and how many IP's are available. Pick a valid number, and make it the same on both boxes.

---

### Post by 2hot6ft2 on 2010-01-28
Same results using
> auto lo
iface lo inet loopback 

iface eth0 inet static
address 10.10.1.1
netmask 255.255.255.0
or
> auto lo
iface lo inet loopback 

iface eth0 inet static
address 10.10.1.1
netmask 255.255.255.0
network 10.10.1.0
broadcast 10.10.1.255
The eth0 adapter vanishes from ifconfig. Removing all the lines except the original
> auto lo
iface lo inet loopback 
and rebooting brings back the eth0

I like that tool. Pretty cool. It is valid as far as network setups go.
I bookmarked it. Thanks
I know others setup more than 1 network adapter at a time just don't see why it's not letting me.

---

### Post by Iowan on 2010-01-28
Looks like you may have forgotten the **auto eth0** line...
:oops: because somehow, I didn't manage to include it.

---

### Post by 2hot6ft2 on 2010-01-28
> **Iowan said:**
> Looks like you may have forgotten the **auto eth0** line...
:oops: because somehow, I didn't manage to include it.
LOL. Don't feel bad, it didn't dawn on me either. I'll play with it again tomorrow morning, my eyes are sore and I was about to call it a night. Just checking for any updates before logging off.

Goodnight.

---

### Post by 2hot6ft2 on 2010-01-29
OK, set it up and rebooted. WiFi connected.
ifconfig looks good
> inet addr:10.10.1.2  Bcast:10.10.1.255  Mask:255.255.255.0
But can't ping the other pc in either direction.
This is what I get:
> PING 10.10.1.1 (10.10.1.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
^C
--- 10.10.1.1 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 2999ms
using
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.10.1.2
netmask 255.255.255.0
network 10.10.1.0
broadcast 10.10.1.255
Same results if I take out the last 2 lines.

---

### Post by Iowan on 2010-01-29
I've seen this [before]("http://ubuntuforums.org/showthread.php?t=1141195") - but it cured itself, so I don't know what fixed it. 
Both machines do that? What are results of **route -n**?

---

### Post by 2hot6ft2 on 2010-01-29
> **Iowan said:**
> I've seen this [before]("http://ubuntuforums.org/showthread.php?t=1141195") - but it cured itself, so I don't know what fixed it. 
Both machines do that? What are results of **route -n**?
Yeah, both give the same results. Naturally when trying to ping the other one:
> 10.10.1.1 pinging 10.10.1.2
and vise versa

route -n returns the same thing on both computers, except wlan0 on the other instead of wlan1 shown here, everything else is the same.
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan1
10.10.1.0       0.0.0.0         255.255.255.0   U     0      0        0 eth0
[COLOR="Blue"]**169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0**[/COLOR]
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan1

```
Now where it gets that next to last line from beats me.
Never saw route -n used before I'll have to remember that one.

EDIT: I do show this in Network Connections but edit and delete are not accessible. And it took the place of Auto eth0 that was there before.
See pic

---

### Post by 2hot6ft2 on 2010-01-29
And here's System > Administration > Network
eth0 properties.

---

### Post by Iowan on 2010-01-30
Dunno if the "Enable roaming mode" is necessary - I've tried it both ways with no apparent change. Eth0 (probably) won't show up in Network Manager - it *should* ignore interfaces defined in */etc/network/interfaces*. The 169.254.0.0 is an **avahi** address - it *should* be harmless...

BTW, found [another]("http://ubuntuforums.org/showthread.php?p=8748598#post8748598") thread with that "ping" message.

---

### Post by 2hot6ft2 on 2010-01-30
> **Iowan said:**
> Dunno if the "Enable roaming mode" is necessary - I've tried it both ways with no apparent change. Eth0 (probably) won't show up in Network Manager - it *should* ignore interfaces defined in */etc/network/interfaces*. The 169.254.0.0 is an **avahi** address - it *should* be harmless...

BTW, found [another]("http://ubuntuforums.org/showthread.php?p=8748598#post8748598") thread with that "ping" message.
Looks like the same issue and setup i.e. WiFi and cabled connections together.

The "Enable roaming mode" is highlighted by default when opening that. It's not an attempt to highlight it on my part.

If I were to check that box then "Auto eth0" would return to Network Connections as it has before and the network info in that window would either fade out or disappear (I forget which it did). Found that out when I was putting the settings in there instead of the interfaces file.

Good to know about the 169.254.0.0 being a avahi address and that I can disregard it.

I'm kinda surprised that more people haven't jumped in on this. I know there are a lot of brilliant people here. Have the IT Techs. gotten bored with the forum?

I sure appreciate your help. Without it I think this thread would have died quickly without being solved.

I'm sure in the end it will end up being something so simple that it's just being overlooked since there are only a few connections. It's not like it's a large network with 50+ computers.

I've setup SSH, FreeNX, DD-WRT, PuTTy, and NFS among others but I'm just not seeing the answer to this. It will connect over the crossover cable. It just wont do it at the same time the pc's are using WiFi.

---

### Post by 2hot6ft2 on 2010-01-30
I hate these...found this [https://answers.launchpad.net/ubuntu/+question/54342](https://answers.launchpad.net/ubuntu/+question/54342) with a similar situation and they said they fixed it but not how. Only clue is that it was fixed using Mint 6.0 and not Ubuntu 8.10. I'm using Ubuntu 9.10. Funny since Mint is apparently a variation of Ubuntu.
> Update - I finally resolved my problem, but not on Ubuntu 8.10, rather on Mint v6.0 [Felicia]. I downloaded this and on installation ALL the 'problems' evaporated!.

Congrats to the development team 'cos this installation is the business!
I'm downloading Mint now to see how it's different.

---

### Post by Iowan on 2010-01-30
Yet [another]("http://ubuntuforums.org/showthread.php?t=345251") one... This one had to do with iptables.

---

### Post by 2hot6ft2 on 2010-01-30
> **Iowan said:**
> Yet [another]("http://ubuntuforums.org/showthread.php?t=345251") one... This one had to do with iptables.
A firewall issue aka Shorewall but right it just gives a gui to the iptables. I use Firestarter, I know it's dated and isn't being maintained upstream but GUFW didn't appeal to me and Firestarter is easy to configure without messing up. Which yes, I checked that and allowed the IP and port way back at the beginning.

The eth0 connection would be Ad-hoc pc <-> pc. And I'm finding some things but not the answer I'm looking for they all seem to be for ICS (Internet Connection Sharing) (You probably knew what that is but someone else tuning in may not) WiFi Ad-hoc like this one:
[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)

Google is not my friend today!!!

---

### Post by 2hot6ft2 on 2010-02-03
I'm kinda surprised that you can connect 2 pc's together to share an Internet connection but not for what I want to do.

---

### Post by 2hot6ft2 on 2010-03-02
To keep this thead up to date I am working in another thread here
[wireless with /etc/network/interfaces]("http://ubuntuforums.org/showthread.php?p=8905509")

And tried the suggestion by chili555 to get WPA working in the thread here
[HowTo: WPA with wpa_supplicant]("http://ubuntuforums.org/showthread.php?t=263136")

Which made it possible to connect by WiFi without using network manager which I disabled in System > Preferences > Startup Applications

I now have WPA working and can connect without network manager. But when I put both eth0 and wlan3 in the interfaces file the eth0 connects but wlan doesn't.

So still unable to use both adapters at the same time.

Here's what I did.

Made the key using
```
wpa_passphrase your_ssid your_psk
```
Added it to /etc/wpa_supplicant.conf
following the instructions and changing TKIP to AES so I had this
```
ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
	ssid="myapidhere"
        scan_ssid=1
        proto=WPA RSN
        key_mgmt=WPA-PSK
        pairwise=CCMP AES
        group=CCMP AES
	psk=reallylongstringoflettersandnumbershere
}

```
This works for wlan
On the client (laptop) /etc/network/interfaces
```
auto lo
iface lo inet loopback

auto wlan3
iface wlan3 inet dhcp
wireless-essid myapidhere
pre-up wpa_supplicant -Bw -Dwext -iwlan3 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

On the server (desktop) /etc/network/interfaces
```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid myapidhere
pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```
So the WiFi works with the setup. I can ping back and forth and connect by SSH over the WiFi.

Now if I add the LAN crossover to the configuration like this

On the client (laptop) I changed /etc/network/interfaces to
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.10.1.1
netmask 255.255.255.0
network 10.10.1.0
broadcast 10.10.1.255

auto wlan3
iface wlan3 inet dhcp
wireless-essid myapidhere
pre-up wpa_supplicant -Bw -Dwext -iwlan3 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```

On the server (desktop) I changed /etc/network/interfaces to
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.10.1.2
netmask 255.255.255.0
network 10.10.1.0
broadcast 10.10.1.255

auto wlan0
iface wlan0 inet dhcp
wireless-essid myapidhere
pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant
```
Here's route -n on the desktop. I didn't think to run it before starting this post on the laptop but I'm sure it would be about the same.
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.10.1.0       0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
```
I can ping back and forth by the eth0 adapter using the 10.10.1.x addresses but not by the WiFi. I get
**Network is unreachable** when attempting to ping by wlan addresses which are assigned by the router to be static and can't reach the internet.

So I still have this.

The WiFi works.
The LAN crossover works.
They both just wont work at the same time.

I think the answer is going to be in using the route command to add the second network to the kernels routing.

---

