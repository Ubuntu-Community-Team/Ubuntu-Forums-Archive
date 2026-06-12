---
title: "113 No route to host"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by randwyck on 2009-10-30
Hi all (guess that's my first post here:)).
I have a problem with my Ubuntu 9.04 desktop updating through apt-get (but no problem with Synaptic). Ubuntu is connected through Squid proxy server (some old Mandreake I believe), the proxy (192.168.226.5) is configured in:
System > Network proxy
Firefox
Synaptic. 
I have no problem with the internet when I use GUI, however I cannot connect from CLI:

```
Need to get 6468kB of archives.
After this operation, 3273kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://archive.ubuntu.com jaunty/main libconvert-binhex-perl 1.119+pristine-3
  Could not connect to  (192.168.226.26). - connect (113 No route to host)
Err http://archive.ubuntu.com jaunty/universe libcrypt-ssleay-perl 0.57-1
  Could not connect to 192.168.226.26:8080 (192.168.226.26). - connect (113 No route to host)

```I have no idea why it's trying to connect to 192.168.226.26:8080. Is there a way to configure this?

---

### Post by randwyck on 2009-10-30
Please? I really need some help here:( Got absolutely no idea what might be wrong with my setup.

---

