---
title: "Maverick  adobe-flashplugin wont install"
date: 2010-10-04
forum: Multimedia Software
---

### Post by ptipton on 2010-10-04
Am running Maverick RC1 and when I try to install adobe-flashplugin in synaptic i get the message " Depends:libgdk-pixbuf2.0-0(>2.21.6) but this is not installable"

Any help much appreciated.

---

### Post by kerry_s on 2010-10-04
install flashplugin-installer

---

### Post by Roliat on 2010-11-16
> **kerry_s said:**
> install flashplugin-installer

Worked for me, thanks.

---

### Post by gornety on 2010-12-14
i install the flashplugin-installer
then i try to install the plugin itself
it desinstalls the installer and then go back to the message :
Dépend: libgdk-pixbuf2.0-0 (>=2.21.6) but it is not installable

somebody has an idea ?

---

### Post by theozzlives on 2010-12-14
> **gornety said:**
> i install the flashplugin-installer
then i try to install the plugin itself
it desinstalls the installer and then go back to the message :
Dépend: libgdk-pixbuf2.0-0 (>=2.21.6) but it is not installable

somebody has an idea ?

I've always did:
```
sudo apt-get install ubuntu-restricted-extras
```
It's never failed and installs Flash, Java, MS Fonts, and other codecs.

---

### Post by xintera. on 2010-12-14
Hi there ptipton,did you run an update while installing mm? I had the same problem too,but after reinstalling mm with internet connected and "Download updates while installing" ticked,it worked. Bam adobe-flashplugin installed with a tick

---

