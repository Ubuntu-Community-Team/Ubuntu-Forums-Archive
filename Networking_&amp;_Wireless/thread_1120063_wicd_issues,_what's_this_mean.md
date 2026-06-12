---
title: "wicd issues, what's this mean??"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by arnicainthemembrane on 2009-04-08
W: GPG error: [http://apt.wicd.net](http://apt.wicd.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FEC820F4B8C0755A

i get it every time I update... and wicd has a lot of trouble with some home routers.

---

### Post by SuperSonic4 on 2009-04-08
Did you recently add a repository? It's because you've not verified the PPA's identity

---

### Post by arnicainthemembrane on 2009-04-08
what is a ppa and how do i verify it?

---

### Post by Black_Wolf_92 on 2009-04-08
well basically it is a "license" key of sorts, that tells the package manager "yes this stuff is safe and has not been altered".

Go back to the wicd installation guide, or google one, and it will have the appropriete key you need. You may need to do a quick gedit on the liscence files etc, but its generally a pretty quick process.

---

### Post by kerry_s on 2009-04-08
in a terminal:

```
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
```

it's in the instructions: [http://wicd.net/download.php](http://wicd.net/download.php)

---

