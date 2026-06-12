---
title: "Lost Network Communications"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by jonesy29847 on 2009-05-15
I have lost my network connections, both wired and wireless, the last thing I recall doing was working to get Totem to play music (terminal session shown below).
 
I think my problem is that I have locked all occurances of linux-restricted-modules-2.6.27xxxx.
 
I have no problem reinstalling, but need instruction to back up my personal files, including my evolution files.
 
I have an Acer Aspire One running V2.6.27.11
 
Thanks in advance for your help.
 
```

sudo aptitude install vlc
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
sudo aptitude install libdvdread3 libdvdnav4 libdvdcss2
sudo aptitude install non-free-codecs gstreamer0.10-pitfdll w32codecs

```

---

