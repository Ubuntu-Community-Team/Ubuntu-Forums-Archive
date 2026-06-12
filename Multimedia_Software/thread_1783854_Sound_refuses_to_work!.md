---
title: "Sound refuses to work!"
date: 2011-06-16
forum: Multimedia Software
---

### Post by aloraloz on 2011-06-16
So, after an update my sound stopped working at all. Music won't even play on Banshee. I tried fixing this several ways with no luck. Now, my computer's sound output is stuck at "Dummy".

Any clues?

---

### Post by StrayEddy on 2011-06-16
check **alsamixer**, problem always there, should be easy to fix.

EDIT: Type "alsamixer" in a terminal (Ctrl+Alt+T)

---

### Post by aloraloz on 2011-06-16
> **StrayEddy said:**
> check **alsamixer**, problem always there, should be easy to fix.

EDIT: Type "alsamixer" in a terminal (Ctrl+Alt+T)

That is not the issue. I have already unmuted all my channels.

---

### Post by lidex on 2011-06-18
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

Now this - Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by MSBF on 2011-07-14
> **lidex said:**
> Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

Now this - Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

Kuedoes!

---

