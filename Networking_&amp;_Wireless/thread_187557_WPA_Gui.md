---
title: "WPA Gui"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by hyapadi on 2006-06-03
it seems the standard network manager don't have WPA support. Is there any other gui configurator that can be used with ubuntu?

Thanks

---

### Post by rdd on 2006-06-03
Check out this solution

[http://www.ubuntuforums.org/showthread.php?t=179643](http://www.ubuntuforums.org/showthread.php?t=179643)

Regards

rdd

---

### Post by anuski on 2006-06-09
I am new to all this and i am also struggling to get my wireless to work with WPA. I have found a GUI that aparently supports WPA (still doesn't work for me). It is Wifi-radar. I don't know however if it is supposed to work only throught wpareplicant or will only do if drivers natively support WPA or what. It only asks for a driver. This is probably of no help at all, but just in case.

---

### Post by hyapadi on 2006-06-09
Use Network Manager. It works well except for the keyring password request everytime you turn on your comp.

---

### Post by Vinze on 2006-06-11
[QUOTE=hyapadi]Use Network Manager. It works well except for the keyring password request everytime you turn on your comp.[/QUOTE]

Yeah, except for the fact that with me, there is no option "WPA"...

---

### Post by hyapadi on 2006-06-11
What I mean is not the one default from ubuntu, but Network Manager that installed by Automatix.

[http://www.ubuntuforums.org/showthread.php?t=177646](http://www.ubuntuforums.org/showthread.php?t=177646)

---

### Post by Darrena on 2006-06-11
[QUOTE=Vinze]Yeah, except for the fact that with me, there is no option "WPA"...[/QUOTE]

This means that your card is not telling NM that it supports WPA, this usually means that the driver does not support the latest wireless extensions.

What wireless card do you have?

---

### Post by Vinze on 2006-06-11
[QUOTE=Darrena]This means that your card is not telling NM that it supports WPA, this usually means that the driver does not support the latest wireless extensions.

What wireless card do you have?[/QUOTE]

Intersil Corporation Intersil ISL3890 [Prism GT/Prism Duette] (eth1).

I used to think it needed the hostap drivers, but now I found out that has to be prism54, which is not supported by wpa_supplicant. However, when running NetworkManager --no-deamon, it says it uses the "fully supported prism54 driver". If it does not support WPA, I'm going nuts... All those hours I've spent on it. And I have no idea how to find a cheap network card that does...

---

### Post by Darrena on 2006-06-11
[QUOTE=Vinze]Intersil Corporation Intersil ISL3890 [Prism GT/Prism Duette] (eth1).

I used to think it needed the hostap drivers, but now I found out that has to be prism54, which is not supported by wpa_supplicant. However, when running NetworkManager --no-deamon, it says it uses the "fully supported prism54 driver". If it does not support WPA, I'm going nuts... All those hours I've spent on it. And I have no idea how to find a cheap network card that does...[/QUOTE]

Unfortunately the Prism drivers do not support WPA:
[http://live.gnome.org/NetworkManagerHardware](http://live.gnome.org/NetworkManagerHardware)

I would suggest looking for a card with an IPW2200 chipset or one of the Atheros chipsets.  The Intel Pro Wireless cards (IPW) seem to work the best but Atheros chipset cards work ok as well...

---

### Post by Vinze on 2006-06-12
[QUOTE=Darrena]Unfortunately the Prism drivers do not support WPA:
[http://live.gnome.org/NetworkManagerHardware](http://live.gnome.org/NetworkManagerHardware)

I would suggest looking for a card with an IPW2200 chipset or one of the Atheros chipsets.  The Intel Pro Wireless cards (IPW) seem to work the best but Atheros chipset cards work ok as well...[/QUOTE]

Crap. Ah well, at least thanks for the information about the chipset, I'll see if I can get my hands on one.

---

