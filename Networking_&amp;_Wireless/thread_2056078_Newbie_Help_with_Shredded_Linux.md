---
title: "Newbie Help with Shredded Linux"
date: 2012-09-10
forum: Networking &amp; Wireless
---

### Post by Snake4eva on 2012-09-10
I ran an apt-get -f install to repair my package list and it removed some of the core packages and updates on my system. I used recovery mode an installed all of the installed packages and manually configured them. I am now able to see the login screen but each time i enter my username and password i get redirected to the login screen. I di some more digging and released that a number of the built in packages have also beeen deinstalled. Which include apt-daemon, file-roller, gnome-applets, gnome-session etc. My idea was to use apt-get from a shell and download and reinstall the packgages manually from the recovery shell. But my problem is that i'm using an wired network connection from school that seems to be behind a firewall. Now i am able to see the network, ping it and i know the network is up. The problem is that when i run apt-get update/upgrade i am getting connection errors. I would like to know how to connect to a wired lan with a password from the shell and how to approach getting apt-get to work.

---

### Post by critin on 2012-09-10
Sounds like you have installed/uninstalled leaving a mixed bag of broken packages behind.  It would be easier to do a fresh install.  Is it the school's machine or your personal one?  Would they permit you to do that?

I'm sure if this can be done by teminal, someone will come along to explain it.

---

### Post by steeldriver on 2012-09-10
> **Snake4eva said:**
> I am now able to see the login screen but each time i enter my username and password i get redirected to the login screen. 

have you checked the obvious stuff that often stops the X session from starting e.g. that your home dir is writeable and that you don't have a root-owned .Xauthority of .ICEauthority file?

```
ls -ld
```

```
ls -l ~/.{ICE,X}authority
```

---

