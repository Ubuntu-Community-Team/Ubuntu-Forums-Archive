---
title: "Updating ubuntu through automatic proxy configuration URL"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by proyectomx on 2009-09-03
Hi. Using ubuntu for over a year. My first post.

I am currently browsing using automatic proxy configuration URL at work.
this works fine for browsing... but for updates no luck.

I have already tried configuring proxy in the system->administration->sypnatic and select preferences->network to configure the proxy... but the issue is as follows:

the PAC file is in a subdirectory in the server.
everytime I browse, the browser asks me for a username/password (including domain name) for the first time, until I close and reopen the browser.

I have tried following many similar threads, and google different solutions, with no luck.

The ideal scenario would be that apt (or sypnaptic) connect using the network proxy configured in ubuntu (located in system->preference->network proxy) which the browsers can do.

Firefox, for example, connect to the internet using the environment settings, but sypnaptic or apt doesn't.

This issue also affects me trying to connect through console, (browser, ftp client, or anything text based)

By the way, I'm using ubuntu 9.04

Any help would be greatly appreciated.

---

### Post by slakkie on 2009-09-03
Hi, please see this thread, last post is your solution.. 

[http://ubuntuforums.org/showthread.php?t=513217](http://ubuntuforums.org/showthread.php?t=513217)

---

### Post by proyectomx on 2009-09-04
I have just done what suggests this thread, and now it keeps waiting for headers... and stops there.

Thorugh a graphic interface, I have to type domain\username and password. I am guessing it should be typed somewhere in the command line, or in the export line.

Am I missing something?

---

### Post by proyectomx on 2009-09-11
any other suggestions I may try ?

Keep in mind that my proxy server automatic URL asks for username/password the first time I connect with a browser.

---

### Post by proyectomx on 2009-10-15
would appreciate any other ideas I may try

---

