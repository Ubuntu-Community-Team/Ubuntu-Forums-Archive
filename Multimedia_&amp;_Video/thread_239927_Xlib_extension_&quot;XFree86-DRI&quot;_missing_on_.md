---
title: "Xlib: extension &quot;XFree86-DRI&quot; missing on display &quot;:0.0&quot;"
date: 2006-08-20
forum: Multimedia &amp; Video
---

### Post by mmmpancakes on 2006-08-20
Apologies, I realized I posted this in the wrong thread a few minutes ago. Here's my question:

I just installed UT2004 successfully, but when I try to run the program I get the "Xlib: extension "XFree86-DRI" missing on display ":0.0"." error message. It is my understanding that this is a graphics card issue. I tried to update the NVIDIA drivers, but apparently my card isn't NVIDIA compatible. What can I do from here?

My card is:

Stealth S80 128 MB PCI Graphics Card

Thanks in advance for advice.

---

### Post by tseliot on 2006-08-20
Please, post the output of this command:
```
lspci -n | grep 300
```

---

### Post by mmmpancakes on 2006-08-20
> **tseliot said:**
> Please, post the output of this command:
```
lspci -n | grep 300
```

0000:01:01.0 0300: 1002:5960 (rev 01)

---

### Post by tseliot on 2006-08-20
Your card is an ATI Radeon 9200 SE, not an Nvidia. Therefore you should install the ATI driver

---

### Post by mmmpancakes on 2006-08-20
Ok. Can you point me to a tutorial on how to do this?

---

### Post by tseliot on 2006-08-20
You can use the search function of the forum.

Anyhow here's one:
[http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)

Another one can be found on the Wiki.

---

