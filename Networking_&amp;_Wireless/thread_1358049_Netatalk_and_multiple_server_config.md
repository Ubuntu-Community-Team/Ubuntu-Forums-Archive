---
title: "Netatalk and multiple server config"
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by cpt_tylor on 2009-12-17
I have a working netatalk server on 9.04, but I want to add a "Guest" server to it in addition to my main server. I am trying to access it from MacOS 10.3 and 10.4. 

I have in afpd.conf:
```
"Ubuntu-Fileserver" -transall ... (truncated)
"Music" -transall -uamslist uams_guest.so -port 12000 -defaultvol /etc/netatalk/AppleVolumes.music

```
The first one I can get to show up through avahi; Music I cannot.

In AppleVolumes.music I have:
```
/srv/shares/music "Music" options:usedots,mswindows,noadouble adouble:osx
```

In the avahi service directory (/etc/avahi/services) I have a copy of my netatalk service where I have changed the name and ports as such:
```
<name>Music</name>
<service>
    <type>_afpovertcp._tcp</type>
    <port>12000</port>
</service>

```

I'm not sure if the problem lies in my netatalk config or avahi service but I cannot get my Bonjour link to point to Music, and neither one seems to show up anywhere else on my mac network discovery.

---

