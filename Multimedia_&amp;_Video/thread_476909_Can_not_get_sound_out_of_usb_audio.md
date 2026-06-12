---
title: "Can not get sound out of usb audio"
date: 2007-06-17
forum: Multimedia &amp; Video
---

### Post by foreverdaed on 2007-06-17
Everything appears to be working, but I can not seem to configure it correctly.

beau@beau-desktop:~$ cat /proc/asound/cards
 0 [CK804          ]: NFORCE - NVidia CK804
                      NVidia CK804 with ALC850 at 0xf3105000, irq 18
 1 [Headset        ]: USB-Audio - Plantronics Headset
                      Plantronics Plantronics Headset at usb-0000:00:02.0-2, full speed

i can only get audio out of my onboard, even when i go to system->pref->sound and switch it all to usb-audio, it still comes out of my mainboard connection. I have no other idea how to make card 1 defualt.

I can not seem to configure this correctly. Was wondering if anyone had a guide online or had xperience with this issue.

thanks -- foreverdaed

---

### Post by Hammystyle on 2007-07-22
Hi, here's a link to another article that fixed all my issues:

[http://ubuntuforums.org/showthread.php?t=480930]("http://ubuntuforums.org/showthread.php?t=480930")

Basically you have to list your devices with:     **asoundconf list**  and then find the name of the USB device (Headset in my case) to make it default with: **asoundconf set-default-card Headset**.

---

