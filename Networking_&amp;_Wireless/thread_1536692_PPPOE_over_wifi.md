---
title: "PPPOE over wifi"
date: 2010-07-22
forum: Networking &amp; Wireless
---

### Post by tivruski on 2010-07-22
Hello,I have a problem connecting to internet, in windows it`s pretty easy:
 i need to connect to my access point (i need to disable all the protocols IPv4 and IPv6 on my wireless card) 
and then connect to another network "wan miniport(PPPoE)" with my login and password.

I was able to connect to the internet on live cd and the first time after instalation by changing in network manager settings for my network(in the tab IPv4 I changed method from dhcp to "link-lokal only" or something like that) and computer connected(that wasn`t able with dhcp) then i run pppoeconf wlan0 and everything was fine.
But after restart Network manager is not managing wlan0 so pppoeconf isn`t working anymore.
When i changed settings for NM so that it is managing wlan0 pppoeconf gives me error that some other aplication is managing that protocol...

Can somebody give me a step by step tutorial how to set up a connection like this? I looked everywhere in the internet and i didn`t find any clue how to fix it, please help me i can`t stand vista anymore ;]

---

### Post by dineshs on 2010-07-23
I havent used wireless.You may wait for the suggestions of others before trying this.
1)Backup */etc/network/interfaces*
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak

```
2)Edit */etc/network/interfaces*
```
 gksudo gedit /etc/network/interfaces
```Copy and paste the following after removing all entries(The file should contain only this)
```
auto lo
iface lo inet loopback
```
3)Save and close the file
4)Restart the machine
5)Configure DSL tab in Network Manager as follows(see attachment also)
Right-click on the NM icon(two opposite arrows on top right of the panel) and then click on Edit Connections. 
Select the DSL tab- click add - Enter username and password-tick available to all users-apply(connection name =DSL connection by default)
To connect DSL click on NM icon click `DSL connection'
[Hope  wireless is configured in Network Manager]
Note  Please post the output of
```
cat /etc/network/interfaces.bak
```
If you have any problem pl let us know if you can ping your access point

---

### Post by tivruski on 2010-07-23
Your solution didn`t work but helped me greatly ;]

I configured DSL in NM but it didn`t appear in the menu that appears after clicking NM applet in the tray.

What I noticed is that after removing

auto wlan0
iface wlan0 inet manual

from /etc/network/interfaces I could use NM and pppoeconf in the same time again.

My /etc/network/interfaces before editing looked like this

```

auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig wlan0 up # line maintained by pppoeconf
provider dsl-provider

auto wlan0
iface wlan0 inet manual

```

after editing

```

auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig wlan0 up # line maintained by pppoeconf
provider dsl-provider


```

after few restarts 
```

auto wlan0
iface wlan0 inet manual

```
appear again in the file but at least now I know I need to delete it.

So thank you very much ;].

---

### Post by dineshs on 2010-07-23
> I configured DSL in NM but it didn`t appear in the menu that appears after clicking NM applet in the tray.
Did you tick the option [COLOR="DarkSlateBlue"]Available to all users[/COLOR] while configuring DSL?You should click the icon not rightclick
> after editing

Code:

auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig wlan0 up # line maintained by pppoeconf
provider dsl-provider


After editing it should only contain [COLOR="Navy"]only[/COLOR]
```
auto lo
iface lo inet loopback

```
Should restart

---

