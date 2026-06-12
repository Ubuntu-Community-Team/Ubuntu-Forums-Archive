---
title: "[SOLVED] Network icon in the taskbar shows wrong status!"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by BB2008 on 2009-01-07
Hi All:

I have a simple but frustrating issue that I am trying to resolve. On the ubuntu desktop in the taskbar on the top right hand corner I have the network icon that shows the network connection status. For me, that icon always has a red exclamation mark on the corner, indicating no connectivity, even when i do have a working wireless connection. Why is that so, and how can i fix this? Any ideas will be helpful. I have attached a screenshot of the network icon as it looks like with this thread.

Some more data - when i left click on tne icon, all options but the last one are greyed out - the only one that is not is the "VPN Connections" option.

Alternatively, when i right click on the icon, all options are available, but when i click on "connection information" option, i get a "Error displaying connection information: No valid active connections found!" error box. Again, connection is actually working at the time this is happening.

this is not a major issue, just annoying, and maybe an indication of a deeper configuration issue. Any help will be deeply appreciated!

Thanks for looking.

---

### Post by pytheas22 on 2009-01-07
How are you getting connected in the first place without Network Manager?  If you're on Ubuntu 8.04 or earlier, can you solve the problem by going to System>Administration>Network and making sure that 'roaming mode' is enabled?

You could also try reinstalling Network Manager by typing:
```

sudo apt-get remove --purge network-manager
sudo apt-get install network-manager-gnome
```

But this might make you lose your connection, which would make finishing the reinstallation impossible unless you manually reconnect.  If you have an ethernet connection available, plug it in and type:
```

sudo ifconfig eth0 up
sudo dhclient eth0
```

to reconnect.  You can also connect manually with wireless but it's more complicated, so I'll only explain it if you need it.

---

### Post by BB2008 on 2009-01-07
> **pytheas22 said:**
> How are you getting connected in the first place without Network Manager?  If you're on Ubuntu 8.04 or earlier, can you solve the problem by going to System>Administration>Network and making sure that 'roaming mode' is enabled?

Hi pytheas22, thanks for looking. This started happening about the time when I upgraded from 8.04 to 8.10, although I am not certain. I have seen the System>Administration>Network applet in the past, and enabled the roaming mode in it when i was doing my initial setup, but now, the only menu option I see under System>Administration is "Network Tools", which gives me an applet that has tools like ping, whois, finger etc. The only network configuration tool I see is under "System>Preferences>Network Configuration", which gives me an applet that has a tab for "Wireless", and I use that to setup my network. I am certain something is screwed up, but not sure what and where :-(.

Let me know if you want screen shots.

Further on your advice, when i open package manager, i do see "network-manager-gnome" and "network-manager" both installed. Will just doing a "re-install" on both of these packages work? Will I still lose connection if I do this. I do not have a wired connection anywhere near where i have this machine, so i do not want to take that risk. Please advice!

And again, thanx for looking!

---

### Post by pytheas22 on 2009-01-07
There were major changes to Network Manager between 8.04 and 8.10, so I imagine your problems result from that.

Reinstalling Network Manager might solve the problem (if you do it through Synaptic, be sure to right-click and choose the 'remove completely' option so that it removes all configuration files as well), but you might lose your connection while doing it.

A good way to avoid having problems would be to download the [network-manager]("http://packages.ubuntu.com/intrepid/network-manager") and [network-manager-gnome]("http://packages.ubuntu.com/intrepid/network-manager-gnome") packages to your computer before beginning the uninstall of NM (be sure to choose the right package for your computer--i386 for 32-bit systems, or amd64 for 64-bit).  This way, if you lose connectivity, you should be able to reinstall NM simply by double-clicking those packages (install the network-manager one first).

I would give this a shot.  In a worst case we can get you connected wirelessly via the command-line if something goes wrong, but that shouldn't be necessary as long as you have the packages saved to your desktop.

---

### Post by BB2008 on 2009-01-08
Hmmm...this is wierd...I uninstalled the network manager and network manager gnome through Synaptic, by right-click and choosing the 'remove completely' option. After that completed, in the same session I did a re-install of both the packages and then rebooted the system. Outcome - no change. Network manager icon still the same, and when i right clicked on the icon to see network config information, it was still the same.

I think I will have to completely remove, restart, and then install again.

Thoughts?

---

### Post by BB2008 on 2009-01-08
Well, I tried the "completely remove, restart, and then install again" routine as well using the package manager, and no change...still the exact same behavior from the network manager icon in the taskbar.

When I started the machine back after doing the complete removal of the two packages, I did see that the icon was no longer there in the taskbar. I was still on internet so I used the package manager again to install back the two packages, and then the system prompted me to restart. After I came back up, same thing!

What could be wrong here? Any thoughts?

---

### Post by pytheas22 on 2009-01-08
It's strange that completely reinstalling Network Manager doesn't make a difference.  That leads me to assume that the source of the behavior lies somewhere beyond NM's reach, however.  I'm wondering if there's something in your interfaces file that might be related to all this.  What is the output of:
```

cat /etc/network/interfaces
```

---

### Post by BB2008 on 2009-01-08
Here it is:
```
cat /etc/network/interfaces
auto lo
iface lo inet loopback






iface wlan0 inet dhcp
wpa-psk acd6cd4da5104b8d7ec631457b3dc433005113b0ba4f8cb7a529d4855f10b9ff
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid ASHIANA

```

Thanx for looking!

---

### Post by pytheas22 on 2009-01-09
As I suspected, it looks like your connection information is stored in the /etc/network/interfaces file.  The network-setup GUI in Ubuntu 8.04 (which has disappeared in 8.10) probably wrote them in.

It may help to comment-out the parts of the file relating to your wireless connection.  To do that, open up the file by typing:

```
sudo gedit /etc/network/interfaces
```

then put a # at the beginning of each of the six last lines in the file, so that it looks like:
```

auto lo
iface lo inet loopback






#iface wlan0 inet dhcp
#wpa-psk acd6cd4da5104b8d7ec631457b3dc433005113b0ba4f8cb7a529d4855f10b9ff
#wpa-driver wext
#wpa-key-mgmt WPA-PSK
#wpa-proto WPA
#wpa-ssid ASHIANA
```

Then save and close the file, and reboot.  Does Network Manager want to work correctly now?

---

### Post by BB2008 on 2009-01-09
:D :D :D :D :D :D :D

Buddy, gotta give it to you - you are a guru! Yes, that did work like charm! Thanx much!!!

---

### Post by dhimate on 2011-12-18
I am facing same issue. I am using ubuntu 10.04 (lucid). i tried uninstall/reinstall of network manager but it didn't solve the issue. If i use wicd, then it shows network status corrrectly, but i have some other problems with wicd. 

I checked /etc/network/interfaces file and it is as above only. 

Any idea why is this problem occuring?

---

### Post by pytheas22 on 2011-12-18
> I am facing same issue. I am using ubuntu 10.04 (lucid). i tried uninstall/reinstall of network manager but it didn't solve the issue. If i use wicd, then it shows network status corrrectly, but i have some other problems with wicd.

I checked /etc/network/interfaces file and it is as above only.

Any idea why is this problem occuring?

What is the output of:
```

ifconfig
cat /etc/network/interfaces
ps -e | grep Net
```

---

