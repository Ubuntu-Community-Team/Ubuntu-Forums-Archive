---
title: "Can not reenable wireless= HP Pavilion dv5"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by Montalo on 2009-06-29
I have a pavilion dv5, and my wireless was disabled

I can use all my multimedia buttons except, i can not use the wireless one that is used to let me go wireless



Does anyone have any fixes, either through commands or otherwise, that could help me

---

### Post by Ayuthia on 2009-06-29
> **Montalo said:**
> I have a pavilion dv5, and my wireless was disabled

I can use all my multimedia buttons except, i can not use the wireless one that is used to let me go wireless



Does anyone have any fixes, either through commands or otherwise, that could help me
Have you checked System->Adminstration->Hardware Drivers to see if there is an option there for your wireless?  If so, can you post the results of:
```
lspci -nn
```

---

### Post by computer13137 on 2009-06-29
I think you're saying that your computer has a button to enable\disable your wireless network card, and it's not working in Ubuntu, right?

I'm interested in a solution to this too.  My eeePC 1000HA has a hotkey (Function F2) to do the same thing.  Now that I reformatted from Windows XP to Ubuntu, the WiFi is always enabled, and the hotkey has no effect.  I'm thinking this is probably the same problem.

Unfortunately, I never really looked into a solution to this, but I'll do some Googling for you, and I'm subscribed to this thread in case anyone else finds anything out.

-Kirk

---

### Post by Ayuthia on 2009-06-29
> **computer13137 said:**
> I think you're saying that your computer has a button to enable\disable your wireless network card, and it's not working in Ubuntu, right?

I'm interested in a solution to this too.  My eeePC 1000HA has a hotkey (Function F2) to do the same thing.  Now that I reformatted from Windows XP to Ubuntu, the WiFi is always enabled, and the hotkey has no effect.  I'm thinking this is probably the same problem.

Unfortunately, I never really looked into a solution to this, but I'll do some Googling for you, and I'm subscribed to this thread in case anyone else finds anything out.

-Kirk
Can you try going to the Terminal and running acpi_listen?  Once it is running, press your Function F2 button and see if it returns anything.  I am curious if your eee will return something or not.  Press control-c to exit the program.

I don't think that it will work on an HP though.  It is a switch instead of using the keyboard.

---

### Post by computer13137 on 2009-06-29
> **Ayuthia said:**
> Can you try going to the Terminal and running acpi_listen?  Once it is running, press your Function F2 button and see if it returns anything.  I am curious if your eee will return something or not.  Press control-c to exit the program.

I don't think that it will work on an HP though.  It is a switch instead of using the keyboard.

I have done that.  Sorry about the large-ish image, but I didn't want to waste time, lol.  eeePC's aren't that high resolution anyway. :P

[img]http://www.imghost.oabw.net/img02/1246396426.png[/img]

-Kirk

---

### Post by Ayuthia on 2009-06-29
> **computer13137 said:**
> I have done that.  Sorry about the large-ish image, but I didn't want to waste time, lol.  eeePC's aren't that high resolution anyway. :P

-Kirk

Thanks.  I wanted to see if the hotkey still worked or not.  It apparently does because it responded.

Can you check and see if /sys/class/net/wlan0/device/rfkill/rfkill*/state exists and report what it shows:
```
cat /sys/class/net/wlan0/device/rfkill/rfkill*/state
```
Please check it when you press the wireless button to see if it changes or not.  I am curious if we are able to turn on the card by manually changing that state or not.  If it toggles and your wireless card does not turn on, then the issue is most likely a code change rather than just a switch in the system.

---

