---
title: "Please help me with DAAP and Avahi"
date: 2008-05-30
forum: Multimedia Software
---

### Post by flaggh on 2008-05-30
I've searched everywhere and can't figure out how to setup Avahi to allow Rhythmbox to play music off a remote server.  When I use RendezvousProxy it works great, and an icon pops up in Rhythmbox, but I see nothing from Avahi.  Weird thing is, if I run the Avahi Discovery program, I see both the Avahi and the RendezvousProxy instances but they don't both appear in Rhythmbox.  

Here's the contents of my service file /etc/avahi/services/itunes.service

```
<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
<name>iTunes Music sharing</name>
<service>
<type>_daap._tcp</type>
<port>3689</port>
</service>
</service-group>
```

I've left the avahi-daemon.conf file unmodified.  I see the daemon running.  What am I doing wrong?

---

### Post by flaggh on 2008-05-31
My configuration seems to work fine with Amarok.  Anybody know what the difference is between the way Rendezvous Proxy handles the mDNS proxy and the way Avahi does it?  I've been reading that Banshee doesn't show any DAAP servers on the localhost to prevent redundancy with a local shared library, so I guess this is a bug with Banshee, but why then does it work with Rendezvous Proxy?

---

