---
title: "Jumping on a wireless network"
date: 2009-02-16
forum: Networking &amp; Wireless
---

### Post by naaman fletcher on 2009-02-16
I have ubuntu 6.06 (on another computer.  This is vista, which blows, but at least with vista you can jump on a wireless network).

So, I once set it up to jump on the wireless network at my house.. this goes back over a year ago and I remember it being a pain, but I don't remember how I did it).  So, now, I give that computer to my son and he wants to bring it back and forth to his mothers house.  So I come over to his mothers house, and bring his computer on Ubuntu, and his older sisters, which is Vista.  

I am typing on the Vista computer now.  Vista blows, but again, you just "show available networks" and then you get on.

Ubuntu of course is linux and you guys are the best programmers in the world, so surely there must be some way to simply see what networks are available and get on one, but alas, after an hour searching forums and manuals I can't find it.  

I can go to system.. administration tools.. network settings.

I see wireless connection, ethernet connection, and modem connection.

The wirless connection, however is set specifically to my house.  There is no "create new connection" command, or anything like that.  There is also no button to search for available networks, or anything like that.

Can someone please help me?

By the way, you linux programmers who wonder why people are on POS operating systems like Vista.. here is your answer.  Any moron can jump on an open wireless network with Vista.

Again, this is a simple unprotected Linksys router.  How does one find it in ubuntu and connect to it?

Thanks

---

### Post by trepid666 on 2009-02-16
scan mode wlan0

or something like that

---

### Post by trepid666 on 2009-02-16
click on network manager in the applications bar and it'll show all wireless there

---

### Post by yther on 2009-02-16
Note that you are probably not directly addressing any of the "linux programmers" in this forum, although you never know.  ;)

I use KDE, but I assume there must be something similar in Gnome:  There's a small app called KNetworkManager that seems to be an interface to the system service called NetworkManager.  Perhaps you could check in Synaptic... let's see, we've got something called [network-manager-gnome](http://www.gnome.org/projects/NetworkManager/) that appears to be similar.

Assuming it's supported in 6.06, you could try installing that and see if it helps.

---

### Post by naaman fletcher on 2009-02-16
to first reply  wlan0?  I don't know what that means.

To second reply:  I don't appear to have that on my tool bar.  Quite likely my son or daughter might have removed it from toolbar.

Thanks for replies!

---

