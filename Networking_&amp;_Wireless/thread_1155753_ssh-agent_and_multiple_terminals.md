---
title: "ssh-agent and multiple terminals?"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by mjoolnir on 2009-05-11
I'm trying to setup password/passphraseless ssh, I've got the keys working, and can use ssh-agent, but it only works in the terminal I start it in. If I make a new tab in mrxvt I get asked for the key passphrase. How can I configure ssh-agent to run every boot and work in more than one terminal?

---

### Post by Peter09 on 2009-05-11
Check in the configuration file for your ssh server that you have not got the 'allow on one login' option set.

---

### Post by mjoolnir on 2009-05-11
Here is my config file [http://pastebin.com/md824a85](http://pastebin.com/md824a85)

---

### Post by Peter09 on 2009-05-11
Got somewhat confused there.

Try

System->Admin->Login in Window

there is a tick box there which allows/denies multiple logins. Not sure if this is just for Gnome though.

---

### Post by mjoolnir on 2009-05-11
Ah I'm using Awesome, no Gnome around here.

---

