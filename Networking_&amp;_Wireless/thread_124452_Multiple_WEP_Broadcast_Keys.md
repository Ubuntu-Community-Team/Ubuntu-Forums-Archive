---
title: "Multiple WEP Broadcast Keys"
date: 2006-02-01
forum: Networking &amp; Wireless
---

### Post by Yarianist on 2006-02-01
I have a quick question.  I am new to Linux/Ubuntu and I am trying to get my desktop setup so that I can really dig in.  My problem is that I can't seem to define multiple WEP keys?  I have a wireless network setup in my home and use the #2 WEP broadcast key.  When I go into the network configuration screen to setup this connection, it asks for everything but the broadcast key.  I'm sure it's something I'm missing, but I can't seem to find anything in the forums about it (prolly due to bad search terms).  Any ideas or a direction to continue my search?

---

### Post by closeyourwindows on 2006-02-02
I saw multiple key entries in wifi radar
open synaptic and go to wireless, click on wifi radar or here is a link to it from gnome [wifi-radar]("http://www.gnomefiles.org/app.php?soft_id=332")
there is support there for 4 keys and wpa as well

---

### Post by Lambert on 2006-02-02
You can set multiple keys in your /etc/network/interfaces file. the stanzas look like this.

wireless-key1 xxxxxxx
wireless-key2 xxxxxxx
wireless-defaultkey 2

you can also read the man page for iwconfig on setting interface and key from command line.

---

### Post by SandyJ on 2008-02-20
> **closeyourwindows said:**
> I saw multiple key entries in wifi radar
open synaptic and go to wireless, click on wifi radar or here is a link to it from gnome [wifi-radar]("http://www.gnomefiles.org/app.php?soft_id=332")
there is support there for 4 keys and wpa as well

I just installed the program.  If it supports 4 WEP keys for a SSID I can't find where to enter them.

Help!!!!!!!!!!!!!!!!!!!!!!

---

### Post by SandyJ on 2008-02-20
> **Lambert said:**
> You can set multiple keys in your /etc/network/interfaces file. the stanzas look like this.

wireless-key1 xxxxxxx
wireless-key2 xxxxxxx
wireless-defaultkey 2

We've got a newbie here, folks.

I took a look at my copy of that file.  It doesn't reference any SSIDs.

Do SSID entries get recorded in this file?  If so, could someone provide a sample I could look at?




> **Lambert said:**
> you can also read the man page for iwconfig on setting interface and key from command line.

[embarrassment, frustration ignorance, ...]

I haven't the foggiest idea what this means, much less how to do it.


[whimper]

HELP!   PLEASE!!!!

---

### Post by chewearn on 2008-02-20
hi SandyJ
That was an old thread you are responding to (two years old), the info might not apply anymore.  There has been multiple ubuntu versions since then.

I suggest you open a new thread to seek help.  Any reason the gutsy network manager is not working for you?

---

