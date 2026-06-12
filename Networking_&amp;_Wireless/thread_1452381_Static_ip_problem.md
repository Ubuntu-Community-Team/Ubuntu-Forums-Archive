---
title: "Static ip problem"
date: 2010-04-11
forum: Networking &amp; Wireless
---

### Post by asharpham on 2010-04-11
I have followed some instructions to change to a static ip address and have now lost my connection to my router. The mistake I made was not copying the original "interfaces" file before making changes.

The file originally had:
[COLOR=Red]auto wlan0
iface wlan0 inet [/COLOR](something - I thought it was loopback but didn't work when I added it).

The instruction told me to put:
[COLOR=Red]auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1[/COLOR]

Which I did, using my own ip numbers, except for "broadcast". I didn't add that in because I didn't have a clue what to put there.

When it didn't work, I tried putting it back to what I originally had except I can't rememebr that last bit. I added dhcp instead of what I thought it was but this didn't work either.

Can anyone help?

---

### Post by Iowan on 2010-04-11
"Original" file will probably look like:```
auto lo
iface lo inet loopback

```Network Manager can be used to set up a static address, too...

---

### Post by chili555 on 2010-04-11
Are you trying to set up a static IP for ethernet or wireless? If it's wireless, it would be:```
auto wlan0
iface wlan0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid yourlilrouter
wireless-key 0123456789
```This assumes WEP encryption but the wording is a bit different for WPA.

Is Network Manager removed? This probably won't work with NM on the system.

---

### Post by asharpham on 2010-04-12
Now you may have something with those 2 wireless entries. I didn't have those. I know the key and the router SSID. Is that all I need to replace the things you list? Network Manager? Not sure. Where do I find it?

And thanks lowan - definitely is what was there.

---

### Post by chili555 on 2010-04-12
You can either edit connections in Network Manager; or remove NM and edit /etc/network/interfaces. If you never walk that computer down to the cyber cafe or coffee shop, then do you really need NM?

---

### Post by 98cwitr on 2010-04-12
:facepalm:

You configured your NIC...NOT your WLAN interface. you need to replace eth0 with wlan0. Just use network manager to configure your static wireless settings...make sure to press enter when you're finished putting in teh DG.

it's also good practice to leave your loopback in the file as well:

auto lo
iface lo inet loopback

---

### Post by asharpham on 2010-04-13
Where do I find the network manager?

---

### Post by chili555 on 2010-04-13
There is an icon in the upper right of your desktop in the Notification Area. If you don't see it, right-click the panel and add a Notification Area.

---

### Post by asharpham on 2010-04-13
I didn't see it so i right clicked, selected Notification Area and clicked Add. Nothing happened. If it's there it's invisible.

---

### Post by chili555 on 2010-04-13
Please open System > Administration > Synaptic and search for network. Maybe it isn't installed. If it is not, we can proceed with amendments to */etc/network/interfaces*.

To reiterate, are you trying to set up a static IP for ethernet or wireless?

---

### Post by asharpham on 2010-04-13
Synaptic tells me I have these files installed: network-manager-gnome and network-manager plus a whole lot of other files that I won't bother listing. So I'd say the answer is yes, I do have network installed. I'm trying to setup static ip for my Ubuntu computer that connects to the Internet via a wireless modem.

I'm beginning to wonder if it is even necessary as I started this process because of an instruction surrounding the loading of software to enable remote access to a Windows computer. Having installed WinXP in Virtualbox and TeamViewer in that Windows, I can do everything I want to in that regard. I've now totally forgotten what the software was that I was looking at using in Ubuntu (put ti down to age!!).

Neverthteless, I'd still like to know how to make this work. My ultimate aim is to get rid of Windows altogether.

---

