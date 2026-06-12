---
title: "Ubuntu won't stop transforming my WPA key..."
date: 2009-07-12
forum: Networking &amp; Wireless
---

### Post by jeyros12 on 2009-07-12
Hi,
My Ubuntu workstation won't connect to my WPA2 wifi home network.

I've noticed that when I enter my key in NetworkManager, it will try to connect then asking me to enter the key again and again, but presenting me the key i've just entered as a long character chain. I believe it transforms my key into hex or something whereas it is not needed (well, needed not to actually ;) ). I have to say that I think the key is already in hex since it's only 8 numbers and letters between A and F.
For now I have added a few lines to /etc/network/interfaces as a workaround (and it connects really fast this way) :```
 auto wlan0
 
 iface wlan0 inet dhcp
    wpa-conf managed
    wpa-ap-scan 1
    wpa-scan-ssid 1
    wpa-ssid XXXX
    wpa-key-mgmt WPA-PSK
    wpa-psk 12345678
```But I'ld like to have a more proper way to connect via NetworkManager for when I want to connect my laptop in another network.
This might be a Ubuntu problem since I have a friend who had exactly the same problem on his own network (but for him the problem disappeared with the 9.04 version of Ubuntu.

Thanks for your help.

PS: I've tried Wicd but it won't connect either.

---

### Post by Brandon Williams on 2009-07-13
Try editing the passphrase in seahorse (in xubuntu it's 'Accessories -> Passwords and Encryption Keys' in the menu). I think that nm-editor and/or nm-applet always assumes it's a passphrase, but seahorse will let you enter anything and does not post-process it like the network-manager utilities do.

---

### Post by jeyros12 on 2009-07-14
First off, thank you for your answer! :)

It seems that seahorse is also the default in Ubuntu (Applications > Accessories > Passwords and encryption keys). However I can't find out what to do with it... It will only let me creating keyrings, locking, deleting or making them default.
Sorry to be so newbie about that, how do I "edit the passphrase"?

---

### Post by Brandon Williams on 2009-07-14
When I open seahorse and click on the Passwords tab, I get a list that includes, among other things, 'Network secret for Auto/myssid/802-11-wireless-security/psk'. If I right-click on that entry and select properties, I get a dialog that includes an editable password field. Enter the correct key value into the password field.

---

### Post by jeyros12 on 2009-07-18
Thank you for your answer!
Sorry for the late answer : I have been very busy at work...

In seahorse, on the password tab, I only get one item (which has the folder icon)with the name "Passwords:login" ("Passwords:" is in bold).
It seems I can't see nothing network related whatsoever in there...

---

### Post by Brandon Williams on 2009-07-18
Is there some sort of triangle next to that label? If you click on the triangle, does it expand out to a list?

---

### Post by jeyros12 on 2009-07-18
I'm sorry but there is no such things...
All I can do is right click, then either "Properties", "Delete", "lock" or "Change password" which let me "Change the password for the default keyring" by entering the actual password then entering the new password twice (I don't really know what it means anyway).
Here's a screenshot :
[IMG]http://i32.tinypic.com/2qbf3x0.png[/IMG]

---

### Post by Brandon Williams on 2009-07-20
My guess is that network manager doesn't actually save the key in the keyring until it has been able to connect successfully at least once. If there were any keys stored in your login keyring, there would be a triangle. I guess that this means that editing the key in seahorse is out as a work-around.

You might be able to configure wpa-supplicant to handle the security side of your wireless network itself and just use network manager for dhcp and monitoring the signal. I've never tried that, though, so I don't know if it can even be done.

FWIW, the 8 character string is _not_ the actual HEX WPA2 key. A WPA key will be much longer 64 characters (256 bits) if memory serves correctly. Such an 8 character passphrase is generally considered a very bad idea, since it's relatively easy to hack. The usual recommendation is to use a 20 character passphrase.

One more possibility that occurs to me is to figure out what the dull 64-char key is and enter that directly into the field in network manager.
```
$ wpa_passphrase XXXX 12345678
network={
	ssid="XXXX"
	#psk="12345678"
	psk=bcff4ca8c7fe4eba67b88261f305b5dd40d309a22d77d11b046b080579aaeffe
}
```
The with the fake ssid and passphrase from your example, the above shows what the full 64-char key would be. First, try putting that into /etc/network/interfaces as the wpa-psk value, and if that works, try entering it into the field in network manager.

---

