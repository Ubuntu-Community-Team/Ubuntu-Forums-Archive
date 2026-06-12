---
title: "wireless network connection from terminal"
date: 2010-04-10
forum: Networking &amp; Wireless
---

### Post by Esthellin on 2010-04-10
I wish to do this as simply as possible (using a config file or script) with the appropriate programs.

I currently use Network Manager, but that has conniptions frequently, so having the connection via terminal would be better. Also, I don't like using X much and getting connected to the internet without X has always been a difficulty.

Interface:wlan0
Required configuration options:
WEP encryption with key and index
DHCP settings (want addresses only)
DNS server choice

I have read forums about using iwconfig and setting the key and essid, but because I can't set the WEP index, I can't connect to the network.
And I couldn't find anyway of having this automated (in a script) after logging in.

---

### Post by chili555 on 2010-04-10
You can set up /etc/network/interfaces something like this:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-ssid yourlilrouter
wireless-key2 0123456789 
wireless-defaultkey 2

#auto eth0
iface eth0 inet dhcp
```I believe, according to *man iwconfig*, that you can set the key index:```
sudo iwconfig wlan0 index 2
```The interface should start on boot with no human intervention required.

---

### Post by 2hot6ft2 on 2010-04-10
You may find this helpful too.
[How To: Manual Network Configuration without the need for Network Manager]("http://ubuntuforums.org/showthread.php?t=571188")

By the way you can disable NM temporarily in
System > Preferences > Startup Applications
While you test your configuration before removing it, that way you can re-enable it if you need to. Just be sure to remove all but the first 2 lines in the interfaces file when re-enabling it.

---

### Post by Esthellin on 2010-04-18
> **chili555 said:**
> You can set up /etc/network/interfaces something like this:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-ssid yourlilrouter
wireless-key2 0123456789 
wireless-defaultkey 2

#auto eth0
iface eth0 inet dhcp
```I believe, according to *man iwconfig*, that you can set the key index:```
sudo iwconfig wlan0 index 2
```The interface should start on boot with no human intervention required.

I tried that with the following

iface wlan0 inet dhcp
wireless-essid HomePlugMusicRoom
wireless-key open [2] XXXX-XXXX-XX
wireless-mode managed

And it didn't work at all. Restoring the networking always came up with that there were "no leases" or something, and would go to sleep
iwlist scan (when using Network manager) told me the mode of my connection should be master, but in network manager, it was set to infrastucture (e.g. managed)

I uninstalled network-manager-gnome to see if the thing worked. Nope. Reinstalled it. Now the applet fails - the internet connects but the applet doesn't show there has been a connection. /etc/resolv.conf also does not get rewritten with the DNS server ip's I give it.

What is weirder, is that I turned off the applet from running at the start (from Startup Applications) but had removed everything except the loopback info from the /etc/networks/interfaces file.

And yet I can connect to the internet! What on earth have I done?! I wanted to be able to connect to the internet without X, so apparantly this has done it, but I have no idea what actually happenned.


Any ideas?

---

