---
title: "Wireless network installed and configured correctly, but it still doens't work"
date: 2005-01-29
forum: Networking &amp; Wireless
---

### Post by Spif on 2005-01-29
I need some help with my wireless connection. I succesfully installed the drivers from [http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/) and set up the network correctly. The strange thing is it still doesn't work. 

The signal-thingy-icon at the upper right corner just says I/T and when scanning for networks I get nothing. 

What is wrong? 

Thanks in advance!

---

### Post by grj on 2005-01-29
Did you try running Desktop->Administration->Networking?

Does the wireless card show up in the list?

If yes, verify the configuration is correct. Activate the card.

Also, verify the modules are loaded.

---

### Post by Spif on 2005-01-30
[QUOTE=grj]Did you try running Desktop->Administration->Networking?

Does the wireless card show up in the list?

If yes, verify the configuration is correct. Activate the card.

Also, verify the modules are loaded.[/QUOTE]
The wireless card is on the network list and everything has been set up correctly. When I activate it, the little marker disappears a few seconds after.

How do I check whether my modules are loaded or not?

---

### Post by king_arthur on 2005-01-30
[QUOTE=Spif]I need some help with my wireless connection. I succesfully installed the drivers from [http://ipw2200.sourceforge.net/]("http://ipw2200.sourceforge.net/") and set up the network correctly. The strange thing is it still doesn't work. 
    
    The signal-thingy-icon at the upper right corner just says I/T and when scanning for networks I get nothing. 
    
    What is wrong? 
    
    Thanks in advance![/QUOTE]
    
    First of all I think you should re-frase your thread for posting: 
    WiFi network is **not** correctly installed... (otherwise it would work) [img]http://www.ubuntuforums.org/images/smilies/icon_biggrin.gif[/img]
    
    I do not understand your setup and _which part exactly doesn't work_, pls give more details. 
    
  
 

[list]
[*]Firstly and most important: is there any another computer connected to the WiFi that proves your network Wireless Access Point works?
[*]You can't access your LAN?
[*]You can't surf the internet?
[*]what does iwconfig show you?
[/list]Your signal might be WEP encrypted and without knowing the key you wan't be able to access it.
    As for the module, there are different ways to check: 
    what is the answer to *insmod* yourmodulename?

---

### Post by Spif on 2005-01-30
[QUOTE=king_arthur]First of all I think you should re-frase your thread for posting: 
   WiFi network is **not** correctly installed... (otherwise it would work) [img]http://www.ubuntuforums.org/images/smilies/icon_biggrin.gif[/img]
   
   I do not understand your setup and _which part exactly doesn't work_, pls give more details. 
   
 

[list]
[*]Firstly and most important: is there any another computer connected to the WiFi that proves your network Wireless Access Point works?
[*]You cant's access your LAN?
[*]You can't surf the internet?
[*]what does iwconfig show you?
[/list]Your signal might be WEP encrypted and without knowing the key you wan't be able to access it.
   As for the module, there are different ways to check: 
   what is the answer to *insmod* yourmodulename?[/QUOTE]

My dad's laptop easily connected to the network. Can't surf the Internet expect when through LAN and iwconfig shows that eth1 has wireless extensions installed. 

When scanning for networks I find nothing at all. I think it has to do with a hotplug error I get when booting the computer:

"Starting hotplug subsystem…

Modprobe: FATAL: Error inserting hw_random (/lib/modules/2.6.8.1-3-386/kernel/drivers/hw_random.ko) No such device"

---

### Post by Vesperan on 2005-02-02
Spif, I have the same problem you, with the same wireless card.

I got it working last night when I setup the open source drivers, although at the time it didnt work straight away. I could connect to the wireless network, but could only ping other computers on the network. After enrolling my brothers aid, he did something (added default gateway with route command I know he did, not sure what else), and voila it worked. 

However after resetting I get the same problem as Spif. 

Using either Wifi Radar or Ubuntu Networking, I will manually set an ip or tell to automatically connect and it wont work (will not connect to the network at all, cannot ping even computers on the network like it allowed me to at first yesterday). All the settings, including WEP encryption key, are correct.

As it was working yesterday, it leads me to suspect something needs to be altered for the startup, or the driver is going wrong somehow.. or something (I dunno!).

King Arthur:
Modprobe for ipw2200 (driver) has no response, so that seems fine.
insmod ipw2200 returns: "insmod: can't read 'ipw2200': No such file or directory"
Currently I cannot connect to the wireless network at all, be it lan or internet.

iwconfig shows that eth1 (my wireless) is there with the details it last tried to use to connect with (ESSID, encryption key, mode it is in. I should note that I had tried setting these things through the interfaces file to see if it worked, and it didnt help any).

If I try to bring up the wireless in terminal, here I get the following (its trying for dhcp):
```
root@unity:/etc/network # ifup eth1
Internet Systems Consortium DHCP Client V3.0.1rc14
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:0e:35:48:7c:4a
Sending on   LPF/eth1/00:0e:35:48:7c:4a
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
``` 

That keeps trying but fails miserably (the DHCPDISCOVER changes to something ele though, but it too fails). While I cant remember from last night, shouldnt the DHCP be trying for something on the network (default gateway?)?

Any help is appreciated from what I've splatted up here, have to run now though - thanks!

---

### Post by Spif on 2005-02-02
Vesperan, I figured out how to solve my problem. I wrote a HOWTO, which you can find here: [http://ubuntuforums.org/showthread.php?t=13576](http://ubuntuforums.org/showthread.php?t=13576)

---

### Post by Vesperan on 2005-02-02
Thanks Spif, didnt see that there - although I had read the first half in another thread, and that was how I got it working for the first time (until I reset the laptop).

Now, if only I wasnt at work..

---

### Post by Viper12 on 2005-02-06
Here's another possibility............the one that plagued me.........make DAMN sure to type in the SSID properly.  My card did the EXACT same thing...1.5 seconds of check, and then poof..nothing.

Once I had my SSID typed properly (caps and lower case DO matter).......it came up just fine.

netgear wg311 v1 (atheros chipset).

fyi...................Just in case.

(one of those silly "is it plugged" things.......but can bite ya.)

---

### Post by mccan on 2005-02-08
Just in case, one might try disabling encryption on the access point to see if that has something to do with not connecting.  In my case, I figured out that I had to use a hex key instead of an ascii key to get things working.

David

---

### Post by jubuntus on 2005-02-12
[QUOTE=Viper12]Here's another possibility............the one that plagued me.........make DAMN sure to type in the SSID properly. My card did the EXACT same thing...1.5 seconds of check, and then poof..nothing.[/QUOTE]
 I think Viper12 has hit the nail on the head. If you haven't typed in the SSID then the WiFi network is not going to show up.
Gee that's a big call :)
Update: OK, I really should read the entire thread before posting... sorry! Can I delete this post?

---

