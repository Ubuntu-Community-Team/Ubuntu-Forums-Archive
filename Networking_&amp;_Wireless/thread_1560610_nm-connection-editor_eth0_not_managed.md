---
title: "nm-connection-editor eth0 not managed"
date: 2010-08-25
forum: Networking &amp; Wireless
---

### Post by mickwombat on 2010-08-25
Hi,
I'm getting rather fed up with this Network Manager applet on Ubuntu and its seemingly erratic behaviour.
I often use my laptop for things like dhcp server to do pxe boot on other machines for netboot installs and other stuff.  Often I have to set static address on eth0 etc.
I know how to set a static address for eth0 by editing /etc/network/interfaces and all that good stuff, but when I click on the Network Manager applet, it says 'Wired Network - not managed'.
I may have deleted it for some reason, but why does it no longer appear, even though eth0 is working?
I've also found in the past that changes to interfaces in the Network Manager, such as giving eth0 a static address, do not seem to stick?
It seems the only thing this applet is useful for is connecting to a wireless network.....and only with dhcp !!
Anyone else notice this behaviour?
Thanks
;)

---

### Post by dineshs on 2010-08-25
If you want to configure the connection manually
First backup your /etc/network/interfaces
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```
```
gksudo gedit /etc/network/interfaces
```
Edit the file so that it contains only these two lines
```
auto lo
iface lo inet loopback

``` 
Restart.Then try this
[http://ubuntuforums.org/showpost.php?p=9733891&postcount=6](http://ubuntuforums.org/showpost.php?p=9733891&postcount=6)
then [COLOR="Blue"]restart[/COLOR]
Note:substitute your network values while configuring
> I've also found in the past that changes to interfaces in the Network Manager, such as giving eth0 a static address, do not seem to stickAfter giving IP, mask and gateway [COLOR="Blue"]hit enter[/COLOR].Then give DNS and apply

---

### Post by Iowan on 2010-08-25
> **dineshs said:**
> 
After giving IP mask and [COLOR="Red"]DNS[/COLOR] [COLOR="Blue"]hit ente[/COLOR]r.Then give DNS and apply[COLOR="Red"]Gateway?[/COLOR]

---

### Post by dineshs on 2010-08-26
Sorry lowan and mickwombat forgot that
edited my post

---

### Post by BkkBonanza on 2010-08-26
Gateway would be the IP of your router - or path to the internet. ie. any non-local traffic gets sent to the gateway, where your router would handle it (usually by NAT'ing the local IP and sending it out to your ISP).

---

### Post by mickwombat on 2010-08-26
Tried all that and it's still saying eth0 is not being managed.

I must have done something to cause this....not sure what though.
Entering the config for eth0 in /etc/network/interfaces is the workaround.

Not ideal, but there you go.

---

### Post by varunendra on 2010-08-26
I was just wondering if you have any **/etc/default/NetworkManager** file? The /etc/NetworkManager/nm-system-settings.conf file says it (if exists) is meant to override the default settings.

Also, what does your nm-system-settings.conf file says about "managed=" (under [ifupdown])? It should be set to 'false' afaik.

---

