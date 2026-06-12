---
title: "How can I re-add my sound device?"
date: 2010-02-11
forum: Multimedia Software
---

### Post by Blackie_Chan on 2010-02-11
Every once in a while when I reboot my machine, one of my sound devices (HDA Intel or Internal Audio) goes missing. With the device missing, I can hear any sound. To fix the problem, I usually just restart my computer. How can I fix the problem without restarting the computer? Is there a more convenient way?

Here's /proc/asound/cards, if everything works fine:
```
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf5ff8000 irq 36
 1 [U0x46d0x8d7    ]: USB-Audio - USB Device 0x46d:0x8d7
                      USB Device 0x46d:0x8d7 at usb-0000:00:1d.0-1.2, full speed

```

Here's the sound properties, when everything is fine:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=146822&stc=1&d=1265942459[/IMG]

---

