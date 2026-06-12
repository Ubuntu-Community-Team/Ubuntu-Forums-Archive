---
title: "Secure Remote Desktop in Ubuntu 13.04 and SSH"
date: 2013-05-19
forum: Networking &amp; Wireless
---

### Post by bandrew02 on 2013-05-19
Today when I was searching the web my machine started a remote desktop connection to allow others to control my desktop. They then started to proceed to try and do god knows what. But 5 connections where opened by them. I managed to disconnect all of them but is there a way of stopping this.

I've looked about closing the SSH port on my Sky Router but is there more I can do

---

### Post by 2F4U on 2013-05-19
You could install a firewall on your machine with incoming ports closed. As far as I know, the remote desktop application is running in the background as autostarted application. So it may also help to remove it from the autostarted applications.

---

