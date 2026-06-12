---
title: "VPN Grey buttens"
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by itchyball on 2009-09-14
I'm running ubuntu 8.0.1 and the VPN buttons in network manager are unavailable.  When I install network-manager-pptp, it removes network-manager.  I been reading and trying different things for week now with no avail.  I have a Dell Inspiron 1210.  Any help would be greatly appreciated.

---

### Post by JCoster on 2009-09-14
If I were you, i'd remove network-manager and network-manager-pptp totally via Synaptic.

Then run:

```
sudo apt-get install network-manager
```

Then update:

```
sudo apt-get update
```

Then install network-manager-pptp: 

```
sudo apt-get install network-manager-pptp
```

Then you MUST restart network-manager.  The easiest way is to just reboot.

If it is still greyed out then are you sure that network-manager-pptp installed correctly?

Is there any reason you haven't updated Ubuntu to a later version?

Cheers,
JC

---

### Post by itchyball on 2009-09-15
Thank you for the reply.  I have not upgraded because my system is still under Dell warranty.  Dell informed me I would lose support if I went to Ubuntu 9.0.4.

Anyways, I did what you showed and stopped when asked this:

[php]mpb@mpb:~$ sudo apt-get install network-manager-pptp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  pptp-linux
Suggested packages:
  kernel-patch-mppe
The following packages will be REMOVED:
  network-manager network-manager-gnome
The following NEW packages will be installed:
  network-manager-pptp pptp-linux
0 upgraded, 2 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B/169kB of archives.
After this operation, 3641kB disk space will be freed.
Do you want to continue [Y/n]? 
[/php]Last night Dell had me do a clean install with reinstall disk, then update through update manager.  Today they informed me there is nothing more they can do, it's a problem with Ubuntu.  I need to connect through a VPN to set up a remote desktop with my company.

I would greatly apperciate any help.

---

