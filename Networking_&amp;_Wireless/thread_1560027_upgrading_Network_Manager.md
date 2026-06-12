---
title: "upgrading Network Manager"
date: 2010-08-24
forum: Networking &amp; Wireless
---

### Post by arinegara on 2010-08-24
NetworkManager 0.8.1 has been released and it has so many new features.  The important feature is that we can force a connection type so we won't  be annoyed by low-signal-connection-drop thing.
Unfortunately, this  new version is not packed with any available ubuntu distro to date yet so  manual upgrade is needed. The official NetworkManager website doesn't  mention a brief step-by-step how to do it so that's why this guidance  will hopefully help you how to do it.

This guidance is working only for Ubuntu Lucid, it may work for other ubuntu version.

Guidance : 
1. run terminal and type  **sudo add-apt-repository ppa:network-manager/trunk**
please refer to [this url]("https://help.launchpad.net/Packaging/PPA") for more PPA detail


2. go to menu [B]System-->Administration-->Update Manager
[/B]
this will retrieve new items to be installed or upgraded. I was choosing default setting (tick them all) and install

3. restart PC. Go find edit connection and see that you can force connection type there

---

### Post by Iowan on 2010-08-24
From Code of Conduct: > Please use color and font properties for highlighting portions of your text, and not for all of the text in your post.

---

### Post by RonCam on 2012-07-12
:KS :KS :KS :KS :KS
> **arinegara said:**
> NetworkManager 0.8.1 has been released and it has so many new features. ... This guidance is working only for Ubuntu Lucid, it may work for other ubuntu version.After about two years, arinegara's advice is still helpful to those coming across it when searching for solutions!  

This is working fine for EasyPeasy v1.6 on the ASUS 701 netbook, while waiting for v2.0 to come out of alpha.  Thanks again for the clear instructions.

---

### Post by wildmanne39 on 2012-07-12
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

