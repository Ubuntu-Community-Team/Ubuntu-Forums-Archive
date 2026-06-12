---
title: "Can't connect to the internet"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by firestorm10 on 2009-01-15
I just installed Ubuntu Studio (intrepid) and I can't connect to the internet.  I go to System > Administration and there is no Networking there the closest I get is Network Tools.

I had Intrepid on this same laptop previously and everything but the mic and 3D graphics would work.  I switched to a dual boot custom vista (until ati makes new drivers) and ubuntu studio for sound editing.  Thanks for any help you can bring to sorting this out.

Sincerely,
David

[EDIT] Tried connecting by lan... That didn't work either. :(

---

### Post by hazeyfaze on 2009-01-15
Look under System -> Preferences, there should be a Network Configuration option.  That is where you should set up your network information.

---

### Post by firestorm10 on 2009-01-15
Thanks for the help hazeyfaze, sadly the only network and internet related thing I have in System > Preferences are Network Proxy and Remote Desktop.  I entered main menu options to see if it was there but unselected it wasn't there either nor was it on the control center.

Is there anyway of getting the files needed somewhere else and installing them or of setting up the network manually using the terminal?

[EDIT] Tried connecting by lan... That didn't work either. :(

---

### Post by hazeyfaze on 2009-01-15
You can configure your network interfaces in the file /etc/network/interfaces.  For instance, on one of my pcs I have the following:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.196
gateway 192.168.1.1
netmask 255.255.255.0
```

or if using dhcp you could have:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

---

### Post by Iowan on 2009-01-15
My interfaces file looks pretty much like the example, but just for the sake of completeness (FYI?)...
**man interfaces** shows that you can put multiple interfaces on the "auto" line:```
auto lo eth0
```

---

