---
title: "Changing Hostname"
date: 2009-09-25
forum: Networking &amp; Wireless
---

### Post by Thomas Kenobi on 2009-09-25
Can anyone tell me how to change the system hostname? Some tutorials I found on the net suggested the following commands:

```
sudo hostname <new_hostname>
``````
sudo gedit /etc/hosts
```And then change the hostname in that file too.

However if I do that, then trying to start an application (e.g. synaptic), with root privileges, gets me the following error:

```
sudo synaptic
No protocol specified

(synaptic:4950): Gtk-WARNING **: cannot open display: :0.0
```And I'm also experiencing occasional lock-ups (of the hard-reset type) which may be related.

Quite evidently, I'm doing the wrong thing here, but I'm not sure what the correct procedure is. Can anyone advise?



edit:
Never mind, the latest google search provided the suggestion to edit: /etc/hostname
So far it seems to have worked. Time will tell...

---

### Post by bogdan.veringioiu on 2009-09-25
Hi.

sudo hostname --ok
sudo gedit /etc/hosts --ok

sudo gedit /etc/hostname --you have to do also this.

Bogdan

---

### Post by Thomas Kenobi on 2009-09-25
Thanks.

Eventually what I did, was follow the advice here [http://www.debianadmin.com/change-hostname-or-server-name-of-a-linux-machine.html](http://www.debianadmin.com/change-hostname-or-server-name-of-a-linux-machine.html) and it worked nicely.

---

