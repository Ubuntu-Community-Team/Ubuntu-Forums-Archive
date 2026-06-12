---
title: "wireless connectivity - ca certificate problem"
date: 2009-07-23
forum: Networking &amp; Wireless
---

### Post by cyrax2kx on 2009-07-23
i am a student at a university in malaysia (IIUM) and we have our wireless community which is backed by Aruba Networks. we use our user id's and pass-codes to register ourselves to the network and then browse. the problem lies when our university assigned a ca-certificate to use this wireless-community. 

[http://wireless.iiu.edu.my/reg/UIA-wificfg.exe]("http://wireless.iiu.edu.my/reg/UIA-wificfg.exe")

i want to use the above xp based certificate in ubuntu.

please help.:confused:

---

### Post by spd106 on 2009-07-24
Looks like you'll need to hand-craft a wpa_supplicant.conf file as Network-Manager doesn't yet have support for PEAP-GTC.

[http://bugzilla.gnome.org/show_bug.cgi?id=565065](http://bugzilla.gnome.org/show_bug.cgi?id=565065)

You should be able to extract the certificate from that exe file and use it with a suitable .conf file that has the settings you need. Use the one from the bug report as a template.
[http://bugzilla.gnome.org/attachment.cgi?id=133262&action=view](http://bugzilla.gnome.org/attachment.cgi?id=133262&action=view)

There are a few guides around for configuring wireless in this fashion, but it's not a GUI method. See the following wiki page for help.
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo#WPA%20Supplicant](https://help.ubuntu.com/community/WifiDocs/WPAHowTo#WPA%20Supplicant)

---

### Post by cyrax2kx on 2009-07-27
ok i will give it a shot .. but all of it seems real complicated.

thanks

---

