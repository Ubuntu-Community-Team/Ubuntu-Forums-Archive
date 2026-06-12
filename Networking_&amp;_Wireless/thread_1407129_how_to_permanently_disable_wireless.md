---
title: "how to permanently disable wireless"
date: 2010-02-14
forum: Networking &amp; Wireless
---

### Post by webdevelopment on 2010-02-14
i don't use wireless on my desktop so i would like it permanently disabled...

each time i boot up it's back and receving up to 80mb of data from an unknown connection via wireless (i dont use wireless) 

so, to avoid any weird connections to my neighboors house or some kid hacking the neighborhood driving by with a wireless router in his truck i'd like to permanently turn off wireless

this is kind of funny because i had a hard time getting wireless to work on my laptop, but this is my desktop where i do not want it.

i looked it up and your forum back in 2007 said to type in iwconfig in the shell then get the nickname of the wireless card then to black list the wireless card

i did this but it didn't work, so what do i do now?

i have ubuntu 9.10

---

### Post by webdevelopment on 2010-02-14
here is the post where it outlines the method to blacklist the wireless card's nickname

note: THIS DOES NOT WORK FOR ME

[http://ubuntuforums.org/showthread.php?t=483140](http://ubuntuforums.org/showthread.php?t=483140)

---

### Post by Mixalis0 on 2010-02-15
A simpler (or at least more conservative) solution may be to install Wicd, which would replace the default Network-manager. Unlike Network-manager, Wicd will not initiate a wireless connection unless prompted; thus, you should be safe from drive-by crackers. Simply run in a terminal```
sudo apt-get install wicd
```This should, additionally, automatically take care of removing Network-manager. Once this is complete, run```
wicd-client &
``` to restore the wireless connection icon in the applet panel.

---

### Post by webdevelopment on 2010-02-15
thanks!  im a big fan of staying default, so how would i deinstall this if needed?

---

### Post by Mixalis0 on 2010-02-15
```
sudo apt-get install network-manager network-manager-gnome
sudo apt-get remove wicd
``` should take care of it, though I don't foresee you switching back. Wicd is one of those programs that "just works."

---

### Post by 2hot6ft2 on 2010-02-15
If it has a wifi card turn the pc off and remove the card. You can always put it back in at a later date if you need to. It can't connect if it's not in the machine.

Or right click network manager
Edit connections
Select wireless
Remove all connections or
select them one at a time and click edit
Set both IPV4 AND IPV6 to Ignore

No protocol = No connection

---

### Post by bluelamp999 on 2010-02-15
Hi there,

If you want to disable wireless on startup but still have the option to enable it if needed, you could try the following...

Go to *System>Preferences>Startup Applications*

Click *Add* to add a new startup application.

Give it a name like 'Disable_Wirelss' and paste the below into the Command box...

```
dbus-send --system --type=method_call --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.DBus.Properties.Set string:org.freedesktop.NetworkManager string:WirelessEnabled variant:boolean:false

```

Save it and restart Ubuntu and your wireless should be disabled...

Right-clicking on your Network icon will allow you to re-enable wireless if needed.

This worked for me on Karmic and Jaunty.

I tried Wicd and didn't like it...

---

### Post by Iowan on 2010-02-15
Another quick/dirty (with no guarantees):
Discover what interface your wireless uses (eth1, wlan0, etc.).
In */etc/network/interfaces*, create a definition such as:
```
iface wlan0 inet manual
``` that should keep Network Manager from starting it.Another option I've seen to keep an interface away from Network Manager is to simply include in */etc/network/interfaces*:```
auto wlan0
```

---

### Post by alonbr on 2010-02-27
> **bluelamp999 said:**
> Hi there,

If you want to disable wireless on startup but still have the option to enable it if needed, you could try the following...

Go to *System>Preferences>Startup Applications*

Click *Add* to add a new startup application.

Give it a name like 'Disable_Wirelss' and paste the below into the Command box...

```
dbus-send --system --type=method_call --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.DBus.Properties.Set string:org.freedesktop.NetworkManager string:WirelessEnabled variant:boolean:false

```Save it and restart Ubuntu and your wireless should be disabled...

Right-clicking on your Network icon will allow you to re-enable wireless if needed.

This worked for me on Karmic and Jaunty.

I tried Wicd and didn't like it...

Bluelamp, you rock!! :p
You  don't know how many months I spent right clicking my Network Manager icon and manually disable the wireless connection.
Thank you very very much (here's a popcorn for your help... :popcorn:)

---

### Post by maya123ca on 2010-02-27
Thanks Bluelamp. Once again a community member comes to the rescue! I hope you enjoy your coffee- you deserve it.:D

---

### Post by moondog62 on 2011-10-09
> **bluelamp999 said:**
> Hi there,

If you want to disable wireless on startup but still have the option to enable it if needed, you could try the following...

Go to *System>Preferences>Startup Applications*

Click *Add* to add a new startup application.

Give it a name like 'Disable_Wirelss' and paste the below into the Command box...

```
dbus-send --system --type=method_call --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.DBus.Properties.Set string:org.freedesktop.NetworkManager string:WirelessEnabled variant:boolean:false

```Save it and restart Ubuntu and your wireless should be disabled...

Right-clicking on your Network icon will allow you to re-enable wireless if needed.

This worked for me on Karmic and Jaunty.

I tried Wicd and didn't like it...

Hope it's ok to revive an old thread. The solution by Bluelamp addresses the original posters concerns beautifully by disabling wifi on startup. However I notice that with this method, when the system returns from standby wifi is again enabled. Is there a way to also disable wifi when returning from standby?

Thanks,
Bill

---

