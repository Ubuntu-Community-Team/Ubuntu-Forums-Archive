---
title: "Getting a Netgear WG311v2 working with WEP"
date: 2006-07-09
forum: Networking &amp; Wireless
---

### Post by sophrosune on 2006-07-09
Finally got my Netgear WG311v2 PCI wireless card working reliably with WEP under Ubuntu 6.06 and I thought I might share the settings so others might avoid my frustrations.

Setting the acx firmare_ver to 1.2.1.34 in /etc/modprobe.d/options (I'm not using ndiswrapper) meant I could actually find the access point on my wireless router (I'm using a Netgear router, BTW), without this **iwlist scan** turned up nothing. I had previously set the WEP key and SSID using the wireless configuration GUI.

Now it would link occasionally but the link would break unexpectedly and **iwconfig** would show the interface as 'Not-Associated'. After playing around with the various iwconfig options I evenutally tried **iwconfig <interface> key restricted** and I had connectivity. I might have had to use **ifdown** and **ifup** to force the changes, but I'm not entirely sure. On a side note, using **iwevent** came in handy as I could see the interface finding the access point but not connecting and then see the connection occur after I had changed the settings. 

Finally to make the change permanent (rebooting the machine wiped the iwconfig changes), I needed to add the following to the /etc/network/interfaces file, in the section for the wireless interface:

**wireless-keymode restricted**

Note that there will already be SSID and WEP key entries in the file if you use the wireless configuration GUI to set them.

Hope this helps

---

### Post by half_lif3 on 2006-07-14
could u explain more detail n step by step
im using same wireless card as u too

i've add wireless-keymode restricted at the /etc/network/interfaces
than
ifdown
ifup
but i stil cant make it work
it there any step i was missing](*,)

---

### Post by sophrosune on 2006-07-14
> **half_lif3 said:**
> could u explain more detail n step by step
im using same wireless card as u too

i've add wireless-keymode restricted at the /etc/network/interfaces
than
ifdown
ifup
but i stil cant make it work
it there any step i was missing](*,)

What you described is essentially what I did. Here's the complete entry for my wireless card in /etc/network/interfaces:

[FONT="Courier New"]iface wlan0 inet dhcp
wireless-essid <My SSID>
wireless-key <My Wireless Key>
wireless-keymode restricted 

auto wlan0
[/FONT]

You may want to turn off WEP on your wireless router (and remove the wireless-key and wireless-keymode entries) **temporarily** to see if you can get connectivity with no security turned on. Once you've proved that then I'd add the entries back and reconfigure your router (checking that your key matches the one in the router - that got me me than once). If you're restricting the MAC addresses of the devices that can connect to you router you may want to turn that off too (again, temporarily).

HTH

---

### Post by sophrosune on 2006-07-14
Forgot to ask - is 'iwlist scan' showing your access point?

---

### Post by ugufugu on 2006-07-18
With Ubuntu 6.06 LTS this worked for me, cheers!

I tried this:

```
$ sudo gedit /etc/modprobe.d/options
```
insert the line
  ```
options acx firmware_ver=1.2.1.34
``` 
(and if you don't want to reboot):
```
$ sudo modprobe -r acx
$ sudo modprobe acx
$ iwlist wlan0 scan
```
and now a list of access point is shown :)
I didn't need to set 'wireless-keymode restricted' because my accesspoint is open, but I am still using WEP.

---

