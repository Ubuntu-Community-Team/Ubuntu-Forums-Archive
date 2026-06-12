---
title: "Need Help"
date: 2006-06-24
forum: Networking &amp; Wireless
---

### Post by blitz091 on 2006-06-24
Hi, im very new to linux and i was wondering if someone could help me with this situation.

My current setup is like this:

A Windows running computer connected to a WRT54G Linksys router
A Linux running computer connected to a WMP54G Linksys PCI card

What im trying to do is establish an internet connection on the Linux PC, and possibly have a type of shared folder between the two computer.
The internet connection is the prioity here.

I have been trying for a few days now to set this up (ive tried changing the protection to WEP, changing the Linux network set-up to Static IP, many unsuccesful attempts). I have been doing searches for solutions and im not quite sure which ones apply to my situation.

It would be great if someone could explain to me how to set this all up.

---

### Post by jostein on 2006-06-25
I'll try my best to help.

First of all, lets try the wireless. I have the exact same router as you do, problem is that I use Kubuntu, so I haven't got access to the GNOME GUI tools for networking now - when I did use GNOME (Ubuntu) I was able to get just about everything working from the GUI, so don't get worried about me using the console now. Once this is working, you can play with the settings in the GUI to see what works.

The goal will be to setup a network with a WEP encryption and DHCP for IP addresses. Make the relevant changes to your router config before you begin. And of course, make sure your Windows machine can access the internet wtih theese settings.

You need to get the interface name of your wireless card on your linux machine.
Go to a console and type
```

iwconfig

```
My output is this:
```

root@sm466:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"kaflomark"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:BF:2E:EA:DC
          Bit Rate:36 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:0000-0000-0000-0000-0000-0000-00   Security mode:restricted
          Power Management:off
          Link Quality=42/94  Signal level=-53 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


```
(I changed the WEP key to all zeros here for security reasons.)

The interface names are in the left column - mine is called ath0 (among other common names are wlan0). If you only get entries with "no wireless extensions" here, it means ubuntu hasn't detected your wireless card properly. It might be a driver problem. If that is the case: post a reply here with the output of the commands "lspci -v" and "lspci -n" (those two are completely harmless, they just fetch info about your pci devices). From now on, I'll be using ath0 as the interface name, and you shold substitute ath0 for the appropriate value on your system.

Now we are going to set the standard settings for your wireless interface so that it will reset to these values on each reboot. As root (or with sudo), type
```

ifdown ath0
gedit /etc/network/interfaces

```
This brings up a text editor with a configuration file (you can find the full documentation for this file by typing "man interfaces"). The relevant section for us is the part that contains the interface name of your wireless. This is what mine looks like:
```

# "auto interfaceName" makes sure the interface is brougth up at boot time
auto ath0
# the next line is the same for all interfaces using dhcp to get IPs. Just change the interface name if necessary. Check the man page (remember "man interfaces"?) for info on static IPs.
iface ath0 inet dhcp
# the next line defines the ssid of your network. Look in the wireless tab of the WRT54Gs configuration to check what this is on your network. You can change it there if you like.
        wireless-essid kaflomark
# and this defines your WEP key. Look in the man pages for details on what "restricted" does. Again, the real WEP key is replaced by zeros.
        wireless-key restricted 0000-0000-0000-0000-0000-0000-00

```

One really important thing about the WEP key: You should place a dash ("-") for every fourth character (like the zeros in the example above). And it's always in hex (to convert ascii to hex, you could use xxd in a terminal, try "man xxd" for more info on that). There are probably GUI applications out there that put in these dashes after you input your key, and they might be able to convert ascii to hex. But for the console and config files, the above is true. And I would recommend that you use the first WEP key as your "Default transmit key" (check "Wireless -> wireless security" in the router config). Using number 2 or 4 or 3 requires some extra care, and it doesn't increase security much.

This should be all of the configuration required. Now you can test it with (as root or with sudo)
```

ifup ath0

```
Now try accessing the internet. If it doesn't work, try (still as root)
```

dhclient ath0

```
and give the internet another try. If it still doesn't work, try to ping your router (in a terminal: ping -c 4 IP-adress-to-router-goes-here), then try to ping some machine on the internet (4.2.2.2, for instance). Write another post, and include /etc/network/interfaces and the output of the commands "route", "iwconfig" and "ifconfig -a".

And yes, file sharing. You probably want to install samba to be able to share files with Windows machines (but be sure to have a firewall running). You can install it with "apt-get install samba" as root. There's probably gui tools for gnome that can do the rest of the setup once you've got this package.

Good luck!

---

### Post by blitz091 on 2006-06-25
woo.

Thanks for all the help man :)

got it all working.

I actually switched to kubuntu last night to see if i had any luck and i at least got an internet connection. Problem is when ever i switched to WEP the connection wouldnt go thorugh. Then i checked in here and saw that you replied. So i switched back to ubuntu and did all this this and its working well now. :)

so do you by any chance know how to set this all up using WPA now?

---

