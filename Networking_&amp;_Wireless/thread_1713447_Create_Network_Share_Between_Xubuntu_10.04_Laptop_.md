---
title: "Create Network Share Between Xubuntu 10.04 Laptop &amp; Ubuntu 10.10 Tower"
date: 2011-03-24
forum: Networking &amp; Wireless
---

### Post by fleamour on 2011-03-24
I have shared my home folder under Ubuntu 10.10.  Then, using Gigolo to SFTP connect via IP address, from my Xubuntu 10.04 laptop... It'll create the link but then says "File doesn't exist" when double clicking link.  

I would like to connect via GUI/file manager rather than CLI as I am no pro.  I can however ping 10.10 from 10.04 & sharing a printer works.

---

### Post by fleamour on 2011-03-24
The only hint of something wrong is:

Your CPU appears to be lacking expected security protections.
Please check your BIOS settings, or for more information, run:
  /usr/bin/check-bios-nx --verbose

This CPU is family 6, model 23, and has NX capabilities but is unable to
use these protective features because the BIOS is configured to disable
the capability.  Please enable this in your BIOS.  For more details, see:
[https://wiki.ubuntu.com/Security/CPUFeatures](https://wiki.ubuntu.com/Security/CPUFeatures)

However my BIOS has no such setting.  Could this possibly be why I seem to be blocked?

I did mod my IBM T21 to a 1GHz chip over the usual 800MHz.  Maybe this is why it reports a capability my BIOS does not feature.  I'm pretty sure I am running latest BIOS as would've been updated donkey's years ago.

---

### Post by spiky001 on 2011-03-24
Hi have you made any type of connection between the 2 machines?

---

### Post by fleamour on 2011-03-24
The laptop is networked to tower's printer.  Also can ping in both directions.

```
ssh username@IP address
```

results in nx security warning, if you call it that.

---

### Post by spiky001 on 2011-03-24
Have you checked the firewall settings on tower to allow connection on ssh port (22)

---

### Post by fleamour on 2011-03-24
I managed to SSH from Windows into my Xubuntu box.  Is port 22 a security risk?  Is there a safer form of networking so as to share home folder?

---

### Post by spiky001 on 2011-03-24
Is xubuntu the tower? You can change the port number but I would make sure it all works 1st

---

### Post by fleamour on 2011-03-24
Xubuntu is the laptop.

How can I open, or test to see if port open?

---

### Post by spiky001 on 2011-03-24
I have installed gufw (gui for firewall) then you can open port

---

### Post by fleamour on 2011-03-24
Good thinking.  OK.

---

### Post by fleamour on 2011-03-24
Tried enabling SSH as a service, same error.  Can you explain TCP/UDP?

---

### Post by spiky001 on 2011-03-24
Prehaps some one else can do that. You did install ssh openserver on the tower

---

### Post by fleamour on 2011-03-24
Secure Shell installed on both work stations.  Nothing gets through at the moment. Timeout by message bus, no reply error.

---

### Post by spiky001 on 2011-03-24
Are you doing this from terminal

---

### Post by fleamour on 2011-03-25
I think it mounts fine under CLI.  I was hoping for a graphical interface, silly me.

---

### Post by spiky001 on 2011-03-25
Try from terminal```
ssh username@ipaddress
``` see if it connects at least that will show ssh is installed ok

---

