---
title: "Belkin F5D7231-4 Driving Me Crazy"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by cam2009 on 2006-06-08
I have a Dell Inspiron 1150 laptop, with a wireless card that connects to our Belkin F5D7231-4. In windows, I go to the Dell website, here:
[http://support.dell.com/support/downloads/devices.aspx?c=us&cs=19&l=en&s=dhs&SystemID=INS_PNT_P4_1150&os=WW1&osl=EN#](http://support.dell.com/support/downloads/devices.aspx?c=us&cs=19&l=en&s=dhs&SystemID=INS_PNT_P4_1150&os=WW1&osl=EN#)
and download the "Dell Wireless WLAN Card" (not sure if thats the default, but it works in windows).

In Ubuntu, I can connect directly to the router no problem. That's how I'm writing this now. But how do I do wireless? I used ndiswrapper and tried installing a .inf file from some site. There are no errors, but I don't get any wlan0 in my network configuring. I know there are tons of questions about networking already, but I went through as many ideas as I could, and none of them helped. Some people said that it's not supported and you should get another router, but that's not really an option right now. any ideas? thanks.

---

### Post by ComplexNumber on 2006-06-08
you need to put 'modprobe ndiswrapper. in /etc/rc.d/something.local(can't remember the name of the 'something' at the moment) so that it starts every time you log in. you should have also have done this not long after you installed the drivers using ndiswrapper -i <driver>.inf. i assume they installed ok.
after you type in 'sudo modprobe ndiswrapper', what is the output when you type in 'iwlist wlan0 scan'(or it may be ndiswrapper ra0 scan' for you)?

---

### Post by cam2009 on 2006-06-08
I haven't been restarting the computer, so I haven't worried about that yet. ndiswrapper wlan0 scan doesn't come with anything really, just:

"Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile Install driver described by 'inffile'
(More commands)

where 'devid' is either PCIID or USBID of the form XXXX:XXXX"

and same output for ra0.

---

### Post by ComplexNumber on 2006-06-08
have you installed network manager and network manager dispatcher? if not, please do so.

---

### Post by cam2009 on 2006-06-08
I've installed Network Manager. Not sure where/what dispatcher is though. Is it KNetworkManager?

---

### Post by ComplexNumber on 2006-06-08
[quote=cam2009]I've installed Network Manager. Not sure where/what dispatcher is though. Is it KNetworkManager?[/quote] network manager dispatcher is nothing to do with KDE. its an additional funcion of network manager.

---

### Post by cam2009 on 2006-06-08
ah, then I have that. And if anybody has any experience with a Belkin with a Dell Inspiron, what'd you do to resolve it? I should also add that when I used Breezy, it didn't work either, but now in Dapper, when I go to the network config, there is a wireless conection option. not sure if i'll need to use that ever or not.

---

