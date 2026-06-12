---
title: "What is the best Samba GUI tool?"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by Roasted on 2010-05-10
I like Samba. But it's a pain in the *** to edit the smb.conf.

I like system-config-samba, but it doesn't have the features I need.

I like gadmin-samba, but it seems to be very cumbersome. Maybe it's just me.

I like Webmin, but I feel like to do each task I need to click 7 times.

What is the most well rounded Samba GUI tool out there? Is there anything else I'm missing?

I'm trying to find a basic one that will allow me to add users/shares/set permissions/set access levels/adjust the default create mask + directory mask settings.

Thoughts?

---

### Post by Charlietje on 2010-05-10
how about SWAT? (Samba Web Administration Tool)

---

### Post by Roasted on 2010-05-10
> **Charlietje said:**
> how about SWAT? (Samba Web Administration Tool)

I thought SWAT was a dead program now?

---

### Post by Charlietje on 2010-05-10
> **Roasted said:**
> I thought SWAT was a dead program now?

no, apt-get install swat

it's still in the repositories


regards

---

### Post by Morbius1 on 2010-05-10
gedit

---

### Post by Roasted on 2010-05-10
> **Charlietje said:**
> no, apt-get install swat

it's still in the repositories


regards

Ah hah, it may be in the repos but it is a dead product:


swat
Samba Web Administration Tool
 
Samba is an implementation of the SMB/CIFS protocol for Unix systems, providing support for cross-platform file and printer sharing with Microsoft Windows, OS X, and other Unix systems.

This package allows you to administer a Samba server via a web browser.

SWAT is no longer actively maintained, and its default configuration is not secure for use over an untrusted network.

---

### Post by Charlietje on 2010-05-11
sorry, my bad

---

