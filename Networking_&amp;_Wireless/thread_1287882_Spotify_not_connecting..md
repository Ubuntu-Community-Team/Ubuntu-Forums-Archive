---
title: "Spotify not connecting."
date: 2009-10-10
forum: Networking &amp; Wireless
---

### Post by nicohasa on 2009-10-10
Hey!

Installed Wine and spotify on ubuntu, and all was great. a
Then, some time later, when I was trying to open up spotify, it just wouldn't connect.

Tried uninstalling spotify and installing it again, made it work once, then the problem reoccured.

hlp plx? Any ideas?

---

### Post by george_ubu on 2009-10-12
Not any help I know but I've had a similar problem. I removed wine and spotify & reinstalled. Also tried a fresh install of both the above on another installation. On both machines I found if I left it it would eventually start up however this morning it loads the app and then says it's in offline mode.

I haven't got a clue what's going on or what to do about it. Anyone else got any ideas?

(Running Ubuntu 9.04)

---

### Post by vicshrike on 2009-10-12
When Spotify says it is in offline mode just leave it there for a couple of minutes and it will get the connection, at least that is what happens here.

---

### Post by george_ubu on 2009-10-19
Does seem to have got better again over the last few days & connected immediately when I tried it this morning. I guess the problem has probably been at their end - possibly the victim of their own success and unable to keep up with the demand? Maybe the lesson is to be patient and not assume the fault's with your PC. (Maybe not!)

---

### Post by maxmekker on 2009-10-21
Same problem, but when I comment my local routers ip address in

/etc/resolv.conf

#nameserver 192.168.1.1

it works for a while before it suddenly stops working again.
I don't know why this is the case.

---

### Post by maxmekker on 2009-11-28
Hi 
this solved my problem
[https://store.opendns.com/setup/device/ubuntu](https://store.opendns.com/setup/device/ubuntu)

---

### Post by Max Williams on 2012-02-15
> **maxmekker said:**
> Hi 
this solved my problem
[https://store.opendns.com/setup/device/ubuntu](https://store.opendns.com/setup/device/ubuntu)

This (setting up OpenDNS) worked straight away for me too.  thanks :)  Although now i think of it, it may have just needed a restart all along!

For the record, i'm using the native Ubuntu version of Spotify, rather than via WINE.

---

### Post by nothingspecial on 2012-02-15
[IMG]http://img845.imageshack.us/img845/6976/necro2.png[/IMG]

---

