---
title: "Screwed up sound for good"
date: 2014-02-07
forum: Multimedia Software
---

### Post by MaxPayneFH on 2014-02-07
Hello,

Ubuntu did some interference noise on my speakers and people said my voice quality on teamspeak and mumble was really bad when on Ubuntu, so I tried to install a driver from Realtek website and instead I got no sound at all.

Could someone please tell me how to revert to the previous original sound driver ?

And if possible does anyone know of any solution to the sound issues I had ?

The sound card is a Realtek ALC889 integrated on a Gigabyte 990FX-UD3 rev 1.2 motherboard.

---

### Post by tgalati4 on 2014-02-07
There are a lot of sound troubleshooting steps to perform.  Do you have a link to the driver that you installed?

Open a terminal and post the output of:

```
aplay -l
```

Which of these steps did you perform before installing the 3rd-party driver?  [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by Bucky Ball on 2014-02-07
*Thread moved to **Multimedia & Video**.*

[QUOTE=tgalati4 ]Do you have a link to the driver that you installed?[/QUOTE]

This. Extremely unlikely you need any drivers and this could now be confusing your situation.

---

### Post by MaxPayneFH on 2014-02-08
> **tgalati4 said:**
> 

Which of these steps did you perform before installing the 3rd-party driver?  [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

None :X but they where quite helpful in getting my sound back on XD

Thanks alot for the help guys.

PS: this is where I got the driver: ```
http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false 
```

---

