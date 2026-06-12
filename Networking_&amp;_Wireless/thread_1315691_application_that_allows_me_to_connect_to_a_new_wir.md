---
title: "application that allows me to connect to a new wireless network without gnome panel"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by Makmiller on 2009-11-05
Dear list, 

with the gnome panel, one can easily list the available wireless networks and choose one of them by just clicking on the wireless applet. However, if I don't use the gnome panel, is there any application that allows me to list available wireless networks and connect to one of them? 
(I know I can launch the nm-connection-editor, but I didn't find any option in this application that allows me to list the available wireless networks..

Thanks already!

mak

---

### Post by howlingmadhowie on 2009-11-05
you can list the available wireless networks by entering 'iwlist scan' at a terminal prompt.

---

### Post by i.r.id10t on 2009-11-05
> **howlingmadhowie said:**
> you can list the available wireless networks by entering 'iwlist scan' at a terminal prompt.

Yup, and then use iwconfig to set the ssid

---

### Post by Makmiller on 2009-11-05
> **i.r.id10t said:**
> Yup, and then use iwconfig to set the ssid

"iwlist scan" works nicely. But I think I'm doing something wrong when I use the iwconfig command. I typed: 

```
 iwconfig essid *"<essid-name>*" 
```

but I get an error message saying: 

unknown command "<*essid-name*>"

Do you any clue of what I'm doing wrong when I use the iwconfig command?

Thank you so much for the quick replies!

mak

---

### Post by i.r.id10t on 2009-11-05
If the essid is "foo" (no quotes) then it would be

iwconfig wlan0 essid foo

---

### Post by Makmiller on 2009-11-05
> **i.r.id10t said:**
> If the essid is "foo" (no quotes) then it would be

iwconfig wlan0 essid foo

With the above command, I don't get the error message any more. However, I still don't connect to the wireless network for some reason.  

I tried to type "sudo dhclient" as well (after using the iwconfig command) but it doesn't solve my problem either. 

Any clue?

---

