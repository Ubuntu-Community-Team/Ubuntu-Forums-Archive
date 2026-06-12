---
title: "Issues with connman and reinstalling network-manager-gnome"
date: 2013-02-17
forum: Networking &amp; Wireless
---

### Post by Jakssoul on 2013-02-17
I'm a moron and installed Connman (It certainly conned me!) like a complete idiot, and it, as it always does, uninstalls the other network manager. Connman doesn't like me, and I refuse to use it. I use Xubuntu 12.10, with OpenBox instead of XFCE. I was going to try out Enlightenment, which requires connman, but oh no, not now! I will stick to OpenBox. I only have this single computer, with a WIRELESS ONLY connection. So does anyone have a compressed folder or something with network-manager-gnome with ALL dependencies or something magical like this? The way I am accessing the web right now is through a seperate Windows 7 partition. I desperately want this fixed. Windows 7 is beginning to tear at my soul.

Thanks in advance!

---

### Post by Jakssoul on 2013-02-17
By the way, I've got a USB Flash drive with a Live Xubuntu 12.10 installation on it, so if I can just use that to get all of the packages, please let me know! I haven't figured out how I could accomplish this, but if it's do-able, tell me please!

---

### Post by papibe on 2013-02-17
Hi Jakssoul.

First option: there's a chance the the deb package is in the cache.

Go to this directory:
```
/var/cache/apt/archives
```
and look for file like this:
```
network-manager*.deb
```
If it's there, you can install it by doing:
```
sudo dpkg -i network-manager*.deb
```
Second option: Identify your package name, and download it from any computer with a browser.

Open a terminal and run:
```
apt-cache policy network-manager
```
The result would be something like this:
```
network-manager:
  Installed: 0.9.4.0-0ubuntu4.2
  Candidate: **[COLOR="Red"]0.9.4.0-0ubuntu4.2[/COLOR]**
  Version table:
 *** 0.9.4.0-0ubuntu4.2 0
        500 http://ubuntu.mirrors.tds.net/pub/ubuntu/ precise-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     0.9.4.0-0ubuntu3 0
        500 http://ubuntu.mirrors.tds.net/pub/ubuntu/ precise/main amd64 Packages
```

Take note of the version detail (in red).

Using any OS and browser to your disposal, and go to: [http://packages.ubuntu.com/]("http://packages.ubuntu.com/"). There you can search for the network-manager package, and then for the specific version you are looking.

Once downloaded, you can use a USB stick to copy the file into your machine.

Finally, boot into it, and install the package using the previous 'dpkg' command.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Jakssoul on 2013-02-17
I'm about to try out both methods you suggested, hopefully one works! Thank you, I'll let you know in about half an hour.

---

### Post by Jakssoul on 2013-02-17
Method 1 was a no-go. Attempting Method 2 now.

---

### Post by Jakssoul on 2013-02-17
Method two worked - sort of. It installed the network manager. Now, I don't know how to configure the network using Terminal, and I'm not getting my friendly little GUI taskbar thing. I'd prefer the friendly little taskbar thing. Any idea why it's not appearing?

---

### Post by papibe on 2013-02-17
Did you uninstall connman?

You can run the network-manager tool from the terminal like this:
```
nm-connection-editor
```
Regards.

---

### Post by Jakssoul on 2013-02-17
I purged that bastard, connman. Uninstall wouldn't have made me feel good enough. Hahaha, I'll try that out now.

---

### Post by Jakssoul on 2013-02-17
nm-connection-editor Requires network-manager-gnome , which I have downloaded a .deb of, but it clearly isn't the correct one, as sudo dpkg -i networkblahblah******.deb has LOADS of unresolved dependencies and isn't compatible with network-manager. Where should I get one that works with network-manager? I got network-manager 9.6.0.

---

### Post by Jakssoul on 2013-02-17
network-manger_0.9.6.0-0ubuntu7_i386.deb to be exact.

---

### Post by steeldriver on 2013-02-17
How about configuring a temporary connection via the networking service instead? either by adding a stanza to your /etc/network/interfaces or directly on the command line with ifconfig ... up etc.

Should be fairly straightforward especially if you have a wired connection

Then you could reinstall everything from the regular online repo

---

### Post by Jakssoul on 2013-02-17
Wired connection is a definite no: no matter what.

Could you give me instructions on how to configure a wireless connection through Terminal, then? My wifi adapter is wlan0.

---

### Post by papibe on 2013-02-17
I double check my xubuntu machine. Both network-manager and network-manager-gnome are installed. You may try installing both of them.

steeldriver's suggestion could be a faster solution. Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=202834&highlight=wireless") for details. I wouldn't worry for the package 'wpasupplicant' since it should be preinstalled.

Let us know how it goes.
Regards.

---

### Post by steeldriver on 2013-02-17
OK try this (no promises it will work - I have just brought up a working connection on my laptop this way but ymmv)

1. edit your /etc/network/interfaces file e.g.

```
gksudo leafpad /etc/network/interfaces
```or

```
sudo nano /etc/network/interfaces
```It will likely contain only a couple of lines defining the loopback interface('lo'); add the following lines

```

auto wlan0
iface wlan0 inet dhcp
    wpa-ssid *your-ssid*
    wpa-psk *your-wpa-psk*

```2. in case the broken network-manager is still running

```
sudo service network-manager stop
```3. (re)start the (alternative) networking service

```
sudo service networking restart
```You may have trouble with (3) not restarting (I just did) - if so try rebooting instead

This assumes you are getting everything via DHCP - if you need to set up non-DHCP supplied DNS servers or a wholly static IP we will need to add more lines.

Once it's up you can confirm whether you have a working connection and which service is configuring it e.g.

```
ifconfig wlan0

service networking status

service network-manager status

ping google.com
```

---

### Post by Jakssoul on 2013-02-17
Sorry, I was out on call, that's why I haven't responded. I will attempt all of the suggestions, and let you know how it went when finished.

---

### Post by Jakssoul on 2013-02-17
> **papibe said:**
> I double check my xubuntu machine. Both network-manager and network-manager-gnome are installed. You may try installing both of them.

steeldriver's suggestion could be a faster solution. Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=202834&highlight=wireless") for details. I wouldn't worry for the package 'wpasupplicant' since it should be preinstalled.

Let us know how it goes.
Regards.

How would I go about installing the correct network-manager-gnome? I'd like to try that first.

---

### Post by Jakssoul on 2013-02-17
Alright, I give up. You guys have been awesome, and I really appreciate it a lot. So, Xubuntu is going out the window. I hate XFCE. I wanna use #!, but I don't like that they now use Debian as a base.

SO! What OS should I get? I just want speed. Preferably something that will work with OpenBox. Archlinux scares me too much.

---

### Post by sudodus on 2013-02-18
I enjoy Lubuntu (with xubuntu-desktop installed) and I have also found that Openbox is great, when performance is important. So I suggest that you simply save your personal files and reinstall Xubuntu. That is often the quick and clean solution ;-)

If you are not happy with any Ubuntu flavour, try Knoppix or Fuduntu.

---

### Post by Jakssoul on 2013-02-20
Well, this is closed, as I have uninstalled Xubuntu and moved to Arch Linux, despite my fears. Arch is wonderful! :D Thanks for the help, anyway, guys.

---

