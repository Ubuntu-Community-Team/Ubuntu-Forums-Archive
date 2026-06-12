---
title: "Wireless working, cant get IP address"
date: 2006-06-14
forum: Networking &amp; Wireless
---

### Post by jitesh on 2006-06-14
My wireless card seems to be working, but I can't seem to get connection from my router. I ran "wifi-radius" and it showed my router but I could'nt connect. What do I do?

---

### Post by twotonz on 2006-06-14
Hallo jitesh,
I have just answered your mail, so in order not to repeat myself, please check your email first. I shall be finishing work in about 30 mins, when I get home, I am at your desposal (around 15:00 German time).
In the meantime, pehaps you could post the stuff that I asked for.

Love & Peace
anthony

---

### Post by jitesh on 2006-06-14
Hey thanks for the correspondance, I'm currently working on Breezy Badger and have a Broadcom wireless card on the HP nx6125 laptop

Heres the output of [COLOR="Cyan"]iwconfig
[/COLOR]
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  Nickname:"marconi"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate=54 Mb/s   Tx-Power:25 dBm
          RTS thr=2347 B   Fragment thr=2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

the output [COLOR="Cyan"]ifconfig[/COLOR]
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:C0:68:7F
          inet addr:10.0.0.5  Bcast:255.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::20f:b0ff:fec0:687f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2469 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2377 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1544010 (1.4 MiB)  TX bytes:600996 (586.9 KiB)
          Interrupt:10

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11079 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11079 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1004339 (980.7 KiB)  TX bytes:1004339 (980.7 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:14:A5:64:80:8D
          inet6 addr: fe80::214:a5ff:fe64:808d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:d0010000-d0011fff

the contents of my [COLOR="Cyan"]interface file[/COLOR]

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

iface eth0 inet dhcp

iface wlan0 inet dhcp
wireless-essid Marconi
wireless-key AF1B25C4760B080B8C6790F1DF 

auto wlan0

auto eth0

---

### Post by twotonz on 2006-06-14
Hi again,
ummm, when I said post your interfaces, you should first blank out the key you use, nobody needs to know it except you of course. :-)
Ok, looks fine, except that you are not connecting (ok i'm pointing out the obvious, just give me a minute). What chip-set is on the card? I'm afraid broadcom doesn't say a lot, could it be the same as found on dell laptops? To find out, do a "sudo lshw" You are going to get a long read-out, find the section that deals with your wlan, at the bottom should be an entry about which driver your card is using. Sorry to keep asking these questions, but I do not have this card, so I have to start from the beginning. Suggestions will follow........

Love & Peace
anthony

Here is my iwconfig (to compare)
 iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"gate5"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:95:01:BF:DE
          Bit Rate:36 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=29/100  Signal level=1/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

my ifconfig
eth0      Protokoll:Ethernet  Hardware Adresse 00:B0:D0:5F:28:63
          inet Adresse:192.168.2.67  Bcast:192.168.2.255  Maske:255.255.255.0
          inet6 Adresse: fe80::2b0:d0ff:fe5f:2863/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:51456 (50.2 KiB)  TX bytes:5056 (4.9 KiB)
          Interrupt:5 Basisadresse:0xa800

lo        Protokoll:Lokale Schleife
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:103 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0
          RX bytes:8971 (8.7 KiB)  TX bytes:8971 (8.7 KiB)

wlan0     Protokoll:Ethernet  Hardware Adresse 00:0C:F6:00:CB:93
          inet Adresse:192.168.178.42  Bcast:192.168.178.255  Maske:255.255.255.0
          inet6 Adresse: fe80::20c:f6ff:fe00:cb93/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2495 errors:8 dropped:0 overruns:0 frame:0
          TX packets:331 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:512193 (500.1 KiB)  TX bytes:49093 (47.9 KiB)
          Interrupt:5 Basisadresse:0xe000

Here my interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.


# The primary network interface
iface wlan0 inet dhcp
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid gate5


iface dsl-provider inet ppp
provider dsl-provider


auto wlan0

You will notice, there are a few differences, do not worry, we will get to the bottom of this.

******EDIT EDIT
One thing that has occured to me, is that very often, the nic's get in the way of the wlan config. If you do not need the nic's active whilst trying the wlan, then disable them in network-settings. (you can simply enable again when you need them.)

---

### Post by jitesh on 2006-06-14
Ran the command and heres the output, hope it helps. 

*-network:1
                description: Wireless interface
                product: Broadcom Corporation
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@02:02.0
                logical name: wlan0
                version: 02
                serial: 00:14:a5:64:80:8d
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical wireless
                configuration: broadcast=yes driver=ndiswrapper link=no multicast=yes wireless=IEEE 802.11g
                resources: iomemory:d0010000-d0011fff irq:11

---

### Post by twotonz on 2006-06-14
Hi-di hi,
Ok you are using ndiswrapper, do a lsmod, to see if the ndis is loaded, if not do a .....
```
sudo modprobe ndiswrapper
```
Did you make a directory (I put it under /opt/"whatever you want" or /opt/broadcom in your case), and then put the *.inf *.cat *.sys data that belongs to the driver in there?
Have you installed ndisgtk? Have you installed the drivers? What is it saying? A point that may or maynot be important, are you using gnome or kde? At a guess I would say Gnome

Love & Peace
anthony

EDIT AGAIN **********
It is important that you put the files on your harddrive instead of installing them directly from the CD (This will not work!)

---

### Post by jitesh on 2006-06-15
Hey, the ndis is loaded, using gnome and I installed ndisgtk, it says that my hardware is present, but still can't get it to work. I read somewhere that this version of NDISWRAPPER does not work, and that I should install the latest one. Should I do this or will I be wasting my time.

---

### Post by twotonz on 2006-06-15
hallo again,
 With regards to the ndis wrapper version, I think you might be right. I also have the ndis that came with ubuntu (on my other computer), and to be quite honest am not too impressed. Sometimes it works, mostly though not, and just recently, I am starting to get wierd addresses as AP's. As I was searching the forums for a solution, many people are saying that the new ndis, that one has to compile yourself, works much better. I have to go to work for a few hours, when I get back I shall give it a go.
 I would say, you should perhaps do the same, or you could wait for about 4/5 hours, and see if I have any luck (the other computer, is just there to experiment with, so it's not important if something breaks), I could then warn you about any pitfalls.
  From the looks of things, you have done everything right, before you do anything drastic, you could perhaps try a different driver, (I had to play around a bit before I found the right driver to use). On the driver cd, there are normally different drivers for the various platforms, when I tried the winxp drivers, they didn't work, the NT drivers do, sort of.
 Just in case you cannot wait, then let me know how you got on, perhaps you could then warn me of any problems ;-)

Love & Peace
anthony

---

### Post by jitesh on 2006-06-19
Have you had any luck with the new NDISWRAPPER?

---

### Post by joaocorreia on 2006-06-20
Same problem here ... it was working with Breezy after upgrade Wifi no longer works, it cant get an IP address.

Regards
Joao Correia

---

### Post by twotonz on 2006-06-25
Hi again,
A few minites to spare, so I thought I should jot down something that has occured to me. Jitesh, have you tried to disable the eth0 interface, and then try to connect with wireless?  I know that with some cards, I have had to disable all ethx interfaces before I could connect. Just a thought.

Love & Peace
anthony

---

