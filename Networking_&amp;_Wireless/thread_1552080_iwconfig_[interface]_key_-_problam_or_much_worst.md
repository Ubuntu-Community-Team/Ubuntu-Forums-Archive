---
title: "iwconfig [interface] key - problam or much worst"
date: 2010-08-13
forum: Networking &amp; Wireless
---

### Post by 2xd on 2010-08-13
hi,

i'm kind of new in linux and last week i removed gnome-desktop by mistake (wanted to uninstall and then reinstall gnome-settings-daemon)

since then, i'm working in shell mode and cann't connect the internet in order to reinstall gnome-desktop using apt-get.

i've read a lot of WEP wireless connections manuals on-line and even some in here but none would help.

i'm using Ubuntu Lucid (10.04) and HP Pavilion Dv3-2150ej
my Wifi card is Intel(R) WiFi Link 5100 AGN

===

well, first when i tried to enter my wifi network key "John2010" using
```
 sudo iwconfig wlan0 key s:John2010 
```i've recevied:
```

Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.

```so i've just entered the Hex key and it was received.

then my esssid have "-" in it, so i've tried "J-ohn" and "J\-ohn" 

then tired to 
```
 sudo dhclient wlan0 
```and
```
 sudo dhclient wlan0 -s 255.255.255.0 
```and every time i get:

```


Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/00:xx:xx:xx:xx:20
Sending on   LPF/wlan0/00:xx:xx:xx:xx:20
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```===

i've tired it in another network (at friend house) and all the same...

can anyone help me please ?

thanks ahead.

---

### Post by 2xd on 2010-08-14
any idea anyone ?

please I'm desperate

---

### Post by 2xd on 2010-08-20
?

---

### Post by pete_m on 2010-08-21
Hey John - sorry to hear of your plight.  .

I'm in the same boat..making progress to manual WiFi.

Can't help directly but. ..

/etc/network/interfaces

is the file that defines the i'faces and how they will behave.  .

i'm able to write this using a Wired connection on eth0 - 
ifup eth0 does the trick and it automatically does its dhcp stuff . .

so using route commmand


```


root@pete-ee# route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

I've updated to the latest 2.6.35  kernel and I can now set ESSID.  .

but stuck with the same error as you when setting key . .
```

root@pete-ee:/home/pete#  iwconfig wlan0 key s:John2010
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.

```
using iwconfig with no args to see what's going on . .
```

root@pete-ee:/home/pete#  iwconfig wlan0               
wlan0     IEEE 802.11bgn  ESSID:"virgin broadband"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=8 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
```


Hmm.  .will post back if/ when I get it fixed. . 

FIXED - at least for me .. 
[http://forums.debian.net/viewtopic.php?f=5&t=36549](http://forums.debian.net/viewtopic.php?f=5&t=36549)

put me on to package wicd. I installed this and was immediately able to configure the connection, connect and pull out the eth0 wire !

going to reboot now and see if the connection comes up automatically.  .

I have another install on this EEE PC which is an unmodified EB4.
Wireless works fine there but .  .. 
trying to track down the differences.  .

Do you use upstart and the network-manager ? ( as does  the EB4 )

Good luck . .

P.S. did you get your gnome stuff back ok ?

---

### Post by pete_m on 2010-08-21
Well wicd fixed things for me . . a successful reboot and the WiFi connection was established automatically . .

iwconfig currently shows no encryption . .this is clearly not the case . .
something to do with wpa_supplicant ( used by wicd ) being the only way to get on . .

on my other install iwconfig displays the hex value of the key. .
 
if you do not want to use wicd then perhaps if you can connect using a different box/ install you may be able to find the Hex key and use that for iwconfig.  .

Best of luck

---

### Post by 2xd on 2010-08-22
hi there pete_m, thanks you very much for replaying and trying to help :)

first, my name is not John, but Dee - no problam m8 :)

anyway, the hex things is not what seems to be the problem as I already knew my Hex key since I'm the one who set the pass phrase in the router 's settings but that didn't seems to help.

any way, i would be happy if you could explain a little bit more about the thing you told regarding updating the Kernel using the "route" command - what it does ? why is it related to using a wired connection ? 

thanks ahead.

btw - i w'll try wicd... thanks

---

### Post by pete_m on 2010-08-25
Hi Dee,

> . . anyway, the hex things is not what seems to be the problem as I 
> already knew my Hex key 

in that case - iwconfig wlan0 -essid "my wireless" key HEX_KEY_HERE
might work .. from what i've read n experienced it is only with the Ascii WPA style that iwconfig has probs.

> any way, i would be happy if you could explain a little bit more 
> about the thing you told 
two separate things . .

> regarding updating the Kernel

i wanted to get the latest kernel in case its default wireless drivers might fix my problems.
it helped, as noted  above, in that i could now set ESSID which i couldn't using 2.6.32
if you want to do this ( At Your Own Risk ) then apt-get install linux-image ( always points to latest kernel)
depending on what version of Ubuntu/ Debian you are running you may need to turn on Maverick repos in your /etc/apt/sources.list
NB. only turn on Maverick when everything is already upgraded to Lucid/ Sid

> using the "route" command - what it does ? 
from cmd line route displays what routes are available/ in use

> why is it related to using a wired connection ? 
if you use eth0( wired) as well as your wlan0 then you would see it here when in use.  .

>btw - i w'll try wicd... thanks
let me know how you get on - it's working well for me with wifi now .. but doesn't seem to allow hot-plugging wired connection. .'ve yet to see if it finds/ prefers the wired connection if already present at start-up


Hope this helps.

John Dee might be a useful moniker for dealing with these arcana !

---

### Post by 2xd on 2010-08-27
well then, i've installed wicd using python commands (my first time using that).

but - I found that wicd does not support any CLI !?

well since I have no X in my current Lucid since I (as i told before) uninstalled gnome-desktop by mistake.

so how can I enjoy wicd ?

any one ?

---

### Post by 2xd on 2010-09-03
?

---

### Post by 2xd on 2010-09-09
help ?!

---

### Post by 2xd on 2010-09-25
?

---

### Post by pete_m on 2010-12-23
> **2xd said:**
> well then, i've installed wicd using python commands (my first time using that).

but - I found that wicd does not support any CLI !?

well since I have no X in my current Lucid since I (as i told before) uninstalled gnome-desktop by mistake.

so how can I enjoy wicd ?

any one ?
not been on here for ages  - i believe you can just type wicd from the command line ( gtk-wicd when you've got yr X back). that should activate yr network and the usual cmd line tools should reflect that.
re gnome - have you tried any other windows msnagers such as ICE, Fluxbox or Enkightenment

---

