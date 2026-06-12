---
title: "Problem with Network Manager"
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by slamelov on 2008-12-31
Hi

I have a strange problem with Ubuntu 8.10. When I configure the network using the Network Manager, it works ok. But, after booting, I have to re-configure again. Every time I reboot, the configuration is lost.

IF CONFIG shows:

```
ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:11:09:86:f6:c1  
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:16 

eth1      Link encap:Ethernet  direcciónHW 00:02:44:6f:c0:64  
          inet dirección:192.168.1.5  Difusión:192.168.1.255  Máscara:255.255.255.0
          dirección inet6: fe80::202:44ff:fe6f:c064/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:43014 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28389 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:14 txqueuelen:1000 
          RX bytes:55383618 (55.3 MB)  TX bytes:3288827 (3.2 MB)
          Interrupción:17 Dirección base: 0xd800 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

```

So, I use eth1.

Editing interface I put:


```
auto lo
iface lo inet loopback
iface eth1 inet static
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.100
auto eth1
```

But then, eth1 dissapear from Network Manager.

Any help?

---

### Post by namdung on 2008-12-31
How many NICs do u have? By default the first one is eth0. Network manager in Intrepid has some issues.

Do try to change the value in interfaces from *eth1* to *eth0*.
```
sudo gedit /etc/network/interfaces
```

Restart PC and see.

---

### Post by slamelov on 2009-01-01
I have tried changing to eth0 and still the same.

The net works... but I have to configure every time I start the Pc.

Should I use WICD?

---

### Post by stderr on 2009-01-01
My understanding of NM is that it only kicks in when a GUI is started. Before the GUI has loaded, you're relying on /etc/network/interfaces for connectivity. But when NM loads (i.e. when you get your GUI up) it DOESN'T look in /etc/network/interfaces but instead relies on its own configuration.

Therefore I'm wondering if NM is actually starting on boot?

After a reboot, before re-configuring anything, what is the output of running this in a terminal:

```
ps aux | grep nm
```

---

### Post by kevdog on 2009-01-01
I thought that network manager actually called ifup which in turn reads the configuration from the /etc/network/interfaces file.  This file, unknown to many, is actually the configuration file for the ipup command.  I'm not sure how Network Manager interacts with the ifup command, however I thought if Network Manager was set to manual configuration, it would default to using this file, rather than its own configuration files.

---

### Post by stderr on 2009-01-01
I thought it didn't call ifup, but I'm not 100% sure. I would test it later but I need to get some scripts written for NM so I can avoid having to reboot all the time. I hate NM.

---

### Post by kevdog on 2009-01-01
I'm no expert at Network Manager but am fairly certain in calls ifup (which in turn calls ifconfig up) (which is part of the linux-wireless-tools package) to configure its interfaces.  These GUI programs are nice, but they all have to end the end work through the same commands that you and me can type at the command line to configure the wireless cards manually.  There is no secret "backdoor" to wireless configuration.

---

### Post by stderr on 2009-01-01
No, I agree (apart from the NM being nice bit ;))... it's just I recently added some commands to exec pre-ifup, and the only time I noticed them getting called was when I manually did an ifup.

However, when I looked through the /etc/NetworkManager/dispatcher.d/01ifupdown script a couple days back, I saw it was trying to call the pre/post ifup/down scripts. I think I read somewhere that it does something weird though, like taking the network down and up after exec'ing it or something - which may be why I didn't think it was being run.

---

### Post by lswb on 2009-01-01
Take a look (on 8.04 system) at the script in /etc/NetworkManager/dispatcher.d

It implies that NM does not call ifup, however, it tries to create the same environment that ifup/down would create and then calls the the /etc/network/if-xxxx.d scripts the same as ifup would do. Also, if an interface is listed in /etc/network/interfaces, then NM will not try to manage it. This is for NM 0.6.6, I believe 0.7 is the same in this respect. If you look at a stock 8.04 /etc/rc2.d directory you will see that /etc/init.d/networking is not linked in to the init sequence. Instead NetworkManager is started by dbus; (look at /etc/init.d/dbus)
Now for the real surprise, where do you think NM stores configuration info? get ready: in the gconf database!

---

### Post by lswb on 2009-01-01
> **stderr said:**
> I thought it didn't call ifup, but I'm not 100% sure. I would test it later but I need to get some scripts written for NM so I can avoid having to reboot all the time. I hate NM.

I wouldn't say hate, I think "loath" is more accurate.

Here is a script I find handy with NM. I gave it the name "netman" and put it in my path:

```

#!/bin/bash

[ "0" != "$UID" ] && ( echo "Must run as root!" ) && exit

/etc/dbus-1/event.d/25NetworkManager $@
/etc/dbus-1/event.d/26NetworkManagerDispatcher $@

```

Then you can "sudo netman stop" to shut off NM and "sudo netman start" when you want it to run again. It is also handy for calling from other scripts when you want to shut down NM, e.g. when setting up an ad-hoc wireless network.

---

### Post by stderr on 2009-01-01
That's what I thought - re: "creating the same env" but not actually using ifconfig. I was quite sure initially, uncertain now :)

Yeah, someone else on these forums introduced me to NM's gconf configurations the other day. It's one of those things: I see *why* they did it. I just *hate* the fact that now I've got to deal with it.

However, you say that it doesn't try to manage any connections managed in interfaces. Therefore, would it not be a good move for slamelov to essentially remove everything from /etc/network/interfaces aside from 

auto lo
iface lo inet loopback

(i.e. strip it down to barebones config), then hopefully NM should kick in and handle it? (Assuming NM is being auto-started correctly).

Anyway, regardless, I would change the /etc/network/interfaces file so that 

auto eth1

is above the iface definition for eth1. Don't know if that's really going to make a difference...

---

### Post by stderr on 2009-01-01
> **lswb said:**
> Here is a script I find handy with NM. I gave it the name "netman" and put it in my path:

Hehe, funny you should post this. I'm trying to do that exact thing. However, I've already tried the 25/26 scripts. I don't know if you're running Hardy, but under this Intrepid installation I only have 26 left, and that's only a random backup of the old script. 

I had bumped into a page which claimed this would work to stop:

dbus-send --system --type=method_call \
  --dest=org.freedesktop.NetworkManager \
  /org/freedesktop/NetworkManager \
  org.freedesktop.NetworkManager.sleep

(replace sleep with wake to bring up again)

but that has no effect. I mean, this is utterly ridiculous... I really don't know how to stop/start NM, and this is meant to be production-quality.

---

### Post by lswb on 2009-01-01
> **stderr said:**
> Hehe, funny you should post this. I'm trying to do that exact thing. However, I've already tried the 25/26 scripts. I don't know if you're running Hardy, but under this Intrepid installation I only have 26 left, and that's only a random backup of the old script. 

I had bumped into a page which claimed this would work to stop:

dbus-send --system --type=method_call \
  --dest=org.freedesktop.NetworkManager \
  /org/freedesktop/NetworkManager \
  org.freedesktop.NetworkManager.sleep

(replace sleep with wake to bring up again)

but that has no effect. I mean, this is utterly ridiculous... I really don't know how to stop/start NM, and this is meant to be production-quality.

That dbus stuff is just so much mumbo-jumbo to me. I've tried reading through a couple dbus tutorials and MEGO* pretty quickly :)

However, in intrepid NM is started by it's own /etc/init.d script instead of being tacked on to the dbus start sequence. You should be able to stop/start it with the old traditional form like:
"sudo /etc/init.d/NetworkManager stop" 

.
.
* MEGO: **M**y **E**yes **G**laze **O**ver

---

### Post by stderr on 2009-01-01
Haha, yeah, I encountered the same MEGO scenario the other day when I thought why don't I look into Dbus. I soon discovered an excellent reason not to bother ;)

I can't even get control over NM through the /etc/init.d/NetworkManager script - it just does, seemingly, nothing, apart from report that it's stopped successfully, which it hasn't, and report that it's started successfully.

But I did trawl through it yesterday, and it's all wrong anyway. The PID file it refers to is never created, for example, which is probably why nothing happens. And all it seems to do anyway is to pass the start-stop-daemon a load of params. I mean, I may as well use killall myself :)

However, I may as well track down the correct PID file and correct the script, I suppose. Then I may well be able to start|stop|restart etc again...

edit: Uhm... :| ... the PIDFILE is indeed there... *scratches head*. It even references a valid PID. I wonder why it wasn't there yesterday? 

Anyway, progress... somehow... so I *can* now stop NM with that command. The PIDFILE even disappears when it's stopped. The only problem is it isn't at all what I want :) I want a command to stop all networking, and all the NetworkManager script does is essentially stop the NetworkManager binary. And I really don't know what that actually means, in terms of... what use is that? Networking is still up on all interfaces. nm-system-settings is still running. I would assume only NM's autodetection of new interfaces is disabled. In terms of Use Cases though, I can't imagine many people wanting to disable autodetection of new interfaces... but I can imagine a lot of people (+myself) wanting to stop all interfaces instantly.

---

### Post by lswb on 2009-01-01
> **stderr said:**
> 
Therefore, would it not be a good move for slamelov to essentially remove everything from /etc/network/interfaces aside from 

auto lo
iface lo inet loopback

(i.e. strip it down to barebones config), then hopefully NM should kick in and handle it? (Assuming NM is being auto-started correctly).



From what I've seen about NM, that is exactly right, the only thing in /etc/network/interfaces shoule be a lo entry. See for example
[https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)

---

### Post by lswb on 2009-01-02
> **stderr said:**
> 

Anyway, progress... somehow... so I *can* now stop NM with that command. The PIDFILE even disappears when it's stopped. The only problem is it isn't at all what I want :) I want a command to stop all networking, and all the NetworkManager script does is essentially stop the NetworkManager binary. And I really don't know what that actually means, in terms of... what use is that? Networking is still up on all interfaces. nm-system-settings is still running. I would assume only NM's autodetection of new interfaces is disabled. In terms of Use Cases though, I can't imagine many people wanting to disable autodetection of new interfaces... but I can imagine a lot of people (+myself) wanting to stop all interfaces instantly.

You know, I've uninstalled and reinstalled NM on my system probably 3 or 4 times since switching to Hardy in April 2008. I've tried wicd but it has its own quirks, though I may switch back to it again. When I ran dapper, I had all my wired networking controlled by a combination of the interfaces file and ifplugd, and wifi-radar for wireless. (I use a laptop) It took me a little while to set that up, but it was dependable and understandable (eventually) 

Anyway, for your specific goal of shutting down networking, how about a script that first shuts down NM, then calls "ifconfig <interface> down" for all desired interfaces in your system?

---

### Post by stderr on 2009-01-02
> **lswb said:**
> Anyway, for your specific goal of shutting down networking, how about a script that first shuts down NM, then calls "ifconfig <interface> down" for all desired interfaces in your system?

I haven't yet tried WICD, although I've heard various people mention it. Ultimately, I want to either fallback to the good ol' CL tools, or "embrace" ;) NM. 

Now, that suggestion of yours is actually pretty damn good. Assuming NM does actually bring everything back online afterwards, that could be a really neat solution :D

edit: The only downside is that to use ifdown to take the interfaces down, you need them specified in /etc/network/interfaces. However, my current config is indeed like that, with the wireless wlan0 spec'd in interfaces as dhcp, but statically spec'd in NM - works fine.

edit: No dice so far... ifdown doesn't want to stop any interfaces at all, even though wlan0 is specified in interfaces.

```
#!/bin/bash
sudo /etc/init.d/NetworkManager stop
sudo ifdown -a
echo "All network interfaces stopped"
```

```
ace@ace5:~$ iwconfig
wlan0     IEEE 802.11abg  ESSID:"ace-net"
[etc...]
```

```
 ace@ace5:~$ cat /etc/network/interfaces
[etc...]
auto wlan0
iface wlan0 inet dhcp

```

---

### Post by slamelov on 2009-01-02
> **stderr said:**
> My understanding of NM is that it only kicks in when a GUI is started. Before the GUI has loaded, you're relying on /etc/network/interfaces for connectivity. But when NM loads (i.e. when you get your GUI up) it DOESN'T look in /etc/network/interfaces but instead relies on its own configuration.

Therefore I'm wondering if NM is actually starting on boot?

After a reboot, before re-configuring anything, what is the output of running this in a terminal:

```
ps aux | grep nm
```


```
root      4971  0.0  0.2   6768  2972 ?        S    09:51   0:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.conf
santiago  5504  1.0  1.1  22756 11976 ?        S    09:52   0:00 nm-applet --sm-disable
santiago  5691  0.0  0.0   3256   824 pts/0    S+   09:53   0:00 grep nm
santiago@
@santiago-ubuntusantiago@santiago-ubuntu:~$ antiago@santiago-ubuntu:

```

I have not this problem with 8.04. I have just tried in a Laptop with a 8.10 fresh installation, and the same problem occurs. Now I have this interfaces file:


```

auto lo
iface lo inet loopback
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.100
auto eth0

```

This is in the laptop

---

### Post by stderr on 2009-01-02
If you change the laptop's interfaces file to this

```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
  address 192.168.1.5
  netmask 255.255.255.0
  gateway 192.168.1.100
```

and reboot, do you still have 'net access?

---

### Post by zika on 2009-01-02
[http://ubuntuforums.org/showpost.php?p=6404146&postcount=2](http://ubuntuforums.org/showpost.php?p=6404146&postcount=2)

---

### Post by slamelov on 2009-01-02
> **stderr said:**
> If you change the laptop's interfaces file to this

```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
  address 192.168.1.5
  netmask 255.255.255.0
  gateway 192.168.1.100
```

and reboot, do you still have 'net access?

No, still I have to reconfigure NM when I reboot.

The ETH0 dissapear from NM

---

### Post by zika on 2009-01-02
> **slamelov said:**
> No, still I have to reconfigure NM when I reboot.

The ETH0 dissapear from NM

(in case You do not use wireless)
try to edit:```
/etc/NetworkManager/nm-system-settings.conf
``` and change so that You have:```
[ifupdown]
managed=false
``` (see the link [http://ubuntuforums.org/showpost.php?p=6404146&postcount=2](http://ubuntuforums.org/showpost.php?p=6404146&postcount=2))
that way NM does not manage Your connection and You are left with /etc/network/interfaces. NM would show in Your panel with red triangle but You should not care. if this works for You than You can uncheck it from System->Preferences-Sessions->...

---

### Post by slamelov on 2009-01-02
But in the Laptop I need to use Wifi...

Do you think should I use WICP?

---

### Post by lswb on 2009-01-02
> **stderr said:**
> 
edit: No dice so far... ifdown doesn't want to stop any interfaces at all, even though wlan0 is specified in interfaces.

```
#!/bin/bash
sudo /etc/init.d/NetworkManager stop
sudo ifdown -a
echo "All network interfaces stopped"
```

```
ace@ace5:~$ iwconfig
wlan0     IEEE 802.11abg  ESSID:"ace-net"
[etc...]
```

```
 ace@ace5:~$ cat /etc/network/interfaces
[etc...]
auto wlan0
iface wlan0 inet dhcp

```

Try *ifconfig*, not ifdown. the ifconfig command does not reference /etc/network/interfaces. It configures the kernels internal network state. it's used like "sudo ifconfig eth0 down" or "sudo ifconfig eth1 up"
It does have an "-a" option to display all interfaces, but I'm not sure if that works for setting them too. There is also the newer "ip" command if you are more familiar with that.

We really should start a new thread for this since we are getting away from the OPs problem.

---

### Post by slamelov on 2009-01-08
The problem still continues, am I the only person with this issue?.

---

### Post by zika on 2009-01-08
> **slamelov said:**
> The problem still continues, am I the only person with this issue?.
I've sort of lost the track what You've done and what is the current situation. let's try to sort things out. no, You are not the only one, to the contrary.

what is, now, Your** /etc/network/interfaces**, **/etc/resolv.conf**,** /etc/NetworkManager/nm-system-settings.conf **..., to start with, also what is the result of **ifconfig -a**?

(from faded memory: I had (who didn't) the similar problem the moment I upgraded to 8.10 and was left without internet at all since I've done it on both machines at that time (luckily I had Vista on both). at first moment I've solved it by fiddling with NM. as far as I remember there were two or three important things (I've done it on three, four machines at that time) "remember" option might work as a negation of what You really want, uncheck it if You want it to remember what You've entered, check MAC entry 'cause it can be wrong, and always go back one step to check if it entered it correctly. its one of these things that You hate doing and once its done You forget about the whole ordeal ... :) )

---

### Post by slamelov on 2009-01-09
Lets see.

I start the system and NM appears with the default configuration. The /etc/network has this:

```

auto lo
iface lo inet loopback

```

The Mad Wifi runs OK, but I need to use cable.

So, I configure the network manager and the connection works OK. I can connect Internet ans LAN without problem. The /etc/network does not change when I do that. Resolv.conf shows the DNS correctly. In the /etc/NetworkManager/nm-system-settings.conf appears:

```

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

```

and once again, when I reboot, the configuration is lost.

---

### Post by slamelov on 2009-01-09
IFCONFIG -A
```

ath0      Link encap:Ethernet  direcciónHW 00:23:4d:9a:be:a7  
          DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:500 (500.0 B)  TX bytes:1026 (1.0 KB)

eth0      Link encap:Ethernet  direcciónHW 00:23:8b:01:93:ae  
          inet dirección:192.168.1.5  Difusión:192.168.1.255  Máscara:255.255.255.0
          dirección inet6: fe80::223:8bff:fe01:93ae/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:1248 errors:0 dropped:4289771548 overruns:0 frame:0
          TX packets:796 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:1685285 (1.6 MB)  TX bytes:72062 (72.0 KB)
          Interrupción:219 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

pan0      Link encap:Ethernet  direcciónHW 46:bc:43:21:c2:62  
          DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wifi0     Link encap:UNSPEC  direcciónHW 00-23-4D-9A-BE-A7-00-00-00-00-00-00-00-00-00-00  
          DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:1101 errors:0 dropped:0 overruns:0 frame:106
          TX packets:219 errors:3 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:280 
          RX bytes:97555 (97.5 KB)  TX bytes:11534 (11.5 KB)
          Interrupción:18 


```

---

### Post by slamelov on 2009-01-11
Bump

---

### Post by slamelov on 2009-01-20
Rebump

---

### Post by zika on 2009-01-20
try putting this in [B]/etc/network/interfaces:
[/B]```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface DHCP
#auto eth0
#iface eth0 inet dhcp

# The primary network interface static
auto eth0
iface eth0 inet static
    address 192.168.1.5
    netmask 255.255.255.0
    gateway check_this_one (I'm not sure from Your ifconfig)
    broadcast 192.168.1.255
```

or, if You want dhcp put #'s in front of third cestion and un-# second section.

---

### Post by slamelov on 2009-01-26
Nothing changes.This time, the eth0 dissapear from net manager.

---

### Post by normanp on 2009-01-28
Please see my post in [http://ubuntuforums.org/showthread.php?t=1050965&page=2](http://ubuntuforums.org/showthread.php?t=1050965&page=2) for a solution to allow use of NM.

---

### Post by slamelov on 2009-01-30
Solved. Thanks a lot

---

### Post by physeetcosmo on 2009-04-17
> **lswb said:**
> That dbus stuff is just so much mumbo-jumbo to me. I've tried reading through a couple dbus tutorials and MEGO* pretty quickly :)

However, in intrepid NM is started by it's own /etc/init.d script instead of being tacked on to the dbus start sequence. You should be able to stop/start it with the old traditional form like:
"sudo /etc/init.d/NetworkManager stop" 

.
.
* MEGO: **M**y **E**yes **G**laze **O**ver

Awesome, thanks for the command. The NetworkManager on the eeePC is disabled on bootup (for some reason, maybe I am causing this as I don't normally use ethernet, just Wifi). I couldn't figure out how to start it via command line until now, thanks!

---

