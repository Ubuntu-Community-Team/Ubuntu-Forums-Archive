---
title: "Dapper rt2500 driver kind of works..."
date: 2006-06-02
forum: Networking &amp; Wireless
---

### Post by Mikael on 2006-06-02
I have a D-Link DWL-G122 rev B and it works fine with the built in driver in Dapper. All I need to do to get the WLAN up and running is:

sudo iwconfig rausb0 essid <my SSID>
sudo iwconfig rausb0 key <my WEP key>
sudo dhclient rausb0

Finished!

Any attempt to configure the rausb0 device through the "Networking" GUI results in a complete system freeze (as others have reported). Why is it that the three commands above can successfully activate the wlan, but the GUI can not?

Most importantly: Is there any way to carry out the short command sequence above automatically at system start?

EDIT: I solved it! I did the following to /etc/network/interfaces :

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.


# iface eth0 inet dhcp

auto rausb0

iface rausb0 inet dhcp
pre-up ifconfig rausb0 up
pre-up ifconfig rausb0 down
pre-up iwconfig rausb0 essid <my SSID>
pre-up iwconfig rausb0 key <my WEP key>
pre-up dhclient rausb0

```

Does this mean that I've found a work around for the lock-ups that seem to plague this version of the rt2500 driver and Dapper? There must be something that I've missed here...

Anyway, I just rebooted again and the wlan comes up within seconds without me having to do anything. It works just as good as in Windows!

EDIT: It turned out that wlan sometimes wouldn't come up at boot, using the interfaces file I originally posted. I edited it, adding the line "pre-up dhclient rausb0" instead of "pre-up ifconfig rausb0 up". It is the modified file that is shown above. This one has worked flawlessly. I don't know why it works, but it does and I'm happy.

---

### Post by tonyr on 2006-06-02
You can try adding these lines to **/etc/network/interfaces**:
```

iface rausb0 inet dhcp
wireless-essid <your-essid>
wireless-key <your wep key>
auto rausb0

```

I'm not completely sure about the  **wireless-key** entry.

EDIT:  There are other posts around, about adding things to **/etc/network/interfaces**,
and **wireless-key <wepkey>** seems to be correct.

---

### Post by dara on 2006-06-04
I've been using my Gigabyte GN-WBKG USB adapter for a day now with no problems using tonyr's text added to /etc/network/interfaces.  (I also commented out all other lines but the first two (leaving the loopback interface intact)).  

Huge improvement.  I got the GUI to work occasionally but it wasn't stable.  This is very strange to me - why doesn't the GUI just modify the interfaces file and then it would be the same wouldn't it?

Thanks for the help.  I had been getting quite frustrated.

Dara Parsavand

---

### Post by blackest_knight on 2006-09-11
Hi I have a Belkin F5D7050 usb wifi adapter I am currently testing using my laptop (which runs dapper). I intend to use it on another system if it works ok. 

the Graphical networking tool totally locks up ubuntu if you attempt to configure rausb0 with it (how I found this thread).

The 3 lines given in the first post work.
 
1 and 3 do anyway (I don't use encription). 3 got me an ip address and a flashing led. 

I didn't go much further with testing but its far enough to convince me it will work well enough on the other system. 

Messing around with other wifi devices makes the internal wifi sulk. easiest cure seems to be boot windows  and let it connect to the router then reboot into ubuntu and everything is fine again. 

Anyway for anyone who has the belkin adapter the model number may not be enough. The FCC number is unique. Belkin have used a number of chipsets in this usb stick and I think there are maybe 4 variants. I am not convinced all variants will work. 

so it seems currently the Belkin isn't ideally suited for dapper if you tend to change networks a lot and cannot remember the commandline voodoo to make it work. 

The easiest card I have had is an Edimax pcmcia which identifys as ra0 and it is plug and play. uses the ralink 2500 chipset.

anyway for me at least this belkin usb wifi adapter is good enough to use on my network. I wouldn't want it for my laptop thou.

---

### Post by Jack W on 2006-09-18
I have been playing with an early Belkin F5D7050 rev 1000 and found it to work well with an early kernel,the 2.6.15-21-386 in Dapper.

---

### Post by rssfed23 on 2006-09-28
Wow; you really are a godsend!
I was having similar problems (it would not boot up) and your fix fixed it for me (so thanks)!

Two questions though:
Every time I have to activate it when logging in through the manager, so is there any way to add a link to the desktop to do it automatically via the terminal?

Also (more importantly) I can't seem to get the WEP encryption working, but others have reported it working with WPA so how would I be able to modify your settings to enable and get WPA working (or at least trying to work!)?

Thanks again!
Rob

---

### Post by boz on 2006-10-31
> **rssfed23 said:**
> 
Also (more importantly) I can't seem to get the WEP encryption working, but others have reported it working with WPA so how would I be able to modify your settings to enable and get WPA working (or at least trying to work!)?


I think if you add the line ```
pre-up iwconfig rausb0 key **********
``` after the line ```
pre-up iwconfig rausb0 essid <YOUR ESSID>
``` this will fix your problem.  

Or you could just try it all on one line, which may be better:
```
pre-up iwconfig rasub0 essid <YOUR ESSID> key ********** mode Managed
```

It is likely that you're connected to a managed network, but if you want to be sure, type ```
man iwconfig
``` in the console and scroll down to its description of "mode."  I hope this helps.

I could be wrong, because I haven't tried this on a network with a WEP yet.  Please let me know if it works for you.

---

