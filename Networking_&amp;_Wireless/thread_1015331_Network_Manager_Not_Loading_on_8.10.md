---
title: "Network Manager Not Loading on 8.10"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by thevenerablez on 2008-12-18
Hi,

I am running Ubuntu 8.10 on my Dell Inspiron (came loaded with Ubuntu 8.04, I have since upgraded).

Whenever I try to run the Network Manager application, I get the following error message:

```
(nm-applet:6398): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
```

Could anyone give me some help? I can't connect to my wireless network.

Thanks in advance,
Zach

---

### Post by mspraveen on 2008-12-19
Hi there,

I face the same problem with the same/similar errort result in the terminal when I tried to execute "nm-applet --sm-disable".

Furthermore, the network manager shows signs as in the image:

[[IMG]http://img296.imageshack.us/img296/4182/networkmanagererrorcopywj5.th.jpg[/IMG]](http://img296.imageshack.us/my.php?image=networkmanagererrorcopywj5.jpg)

Hence, I cannot connect to my wireless network. When I reinstall the distro (done it thrice already), it works fine until the first reboot. Thereafter the above problem begins. The wireless works fine on Live CD though. 

For details about my system: Ubuntu 8.10 Intrepid Ibex on Thinkpad R50e.

Can somebody please help? 

Thanks!

> **thevenerablez said:**
> Hi,

I am running Ubuntu 8.10 on my Dell Inspiron (came loaded with Ubuntu 8.04, I have since upgraded).

Whenever I try to run the Network Manager application, I get the following error message:

```
(nm-applet:6398): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
```

Could anyone give me some help? I can't connect to my wireless network.

Thanks in advance,
Zach

---

### Post by superprash2003 on 2008-12-19
try using old network manager .. [http://prash-babu.blogspot.com/2008/11/how-to-enable-roaming-mode-in-ubuntu.html](http://prash-babu.blogspot.com/2008/11/how-to-enable-roaming-mode-in-ubuntu.html) system->admin->network

---

### Post by mspraveen on 2008-12-20
Hi there! 

Thanks for the reply. I can't try your option unless I reinstall the distro again. I don't know, but it is a strange issue!

I tried, however, installing KNetworkManager as per one suggestion. But that doesn't work either. The Wireless is shown as "unmanaged" as in the above given picture.

> **superprash2003 said:**
> try using old network manager .. [http://prash-babu.blogspot.com/2008/11/how-to-enable-roaming-mode-in-ubuntu.html](http://prash-babu.blogspot.com/2008/11/how-to-enable-roaming-mode-in-ubuntu.html) system->admin->network

---

### Post by mspraveen on 2008-12-20
I seemed to have a solution to this. After browsing through some pages, I somehow managed to tweak the nm-system-settings.conf file in /etc/NetworkManager.

Previously, it was the following:
```
[ifupdown]
managed=false
```

I changed to the following:
```
[ifupdown]
managed=true
```

I believe that this leads to the Network Manager manage the connections. All is well here. 

Cheers!

---

