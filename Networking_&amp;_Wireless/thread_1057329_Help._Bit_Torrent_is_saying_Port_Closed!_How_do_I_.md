---
title: "Help. Bit Torrent is saying Port Closed! How do I open?"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by EvilBear on 2009-02-01
I brought my laptop to work and it auto detected the wireless internet here. I can surf the web, but my BitTorrent files were not dwnlding. I checked preferences and it sayd Port is closed, which i though Ubuntu automatically opens and closes ports as needed. Help plese?

---

### Post by bgerlich on 2009-02-01
The problem is that when connected to that network, you don't get an external IP. The port on your computer is open, but from the Internet it looks like it is closed, because your computer is invisible, the router is. To remedy that you can turn on uPnp support in Transmission (your torrent program), this will tell the router to open a port and forward all the comunication on that port to your computer. Of course, the router has to be able to listen and that depends on the model, make and configuration. If this won't help, there is little you can do to speed up your torrents on any system.

---

### Post by EvilBear on 2009-02-01
I'll give that a try, but i don't see how to turn that on. Nothing under preferences. How does one go about attempting that? BTW, using Gnome, not the CLI, but i can use it if given step by step directions :)

---

### Post by bgerlich on 2009-02-01
In preferences, open the tab network and tick - "use UPnP or PNP-NAT", but as I said before the option could be disabled on your router at work, plus the employers sometimes block p2p traffic (bittorrent) on their networks.

---

### Post by EvilBear on 2009-02-02
When i open preferences, this is the screen i get...it has no tab like the one you speak of. Only thing i changed was to limit dwnld speed, thought that i may have had too much happenng since i was uploading around 200+kbs, twice as much as my usual dwnld speed.

---

### Post by EvilBear on 2009-02-02
OK, I'm at home, where it always works. It was working, said port was open, then just stopped ans said port closed...working intermitantly now.

I am really confused.

---

### Post by EvilBear on 2009-02-02
Someone that knows a little more than me tried to help, but i apparently have Transmission 1.06 and need to upgrade, which I have no idea how to. Tried to just sudo apt-get install transmission, but it just installs the exact same thing, not a more recent version.

---

### Post by EvilBear on 2009-02-02
anyone?

---

### Post by EvilBear on 2009-02-02
ok, got help in installing forums, it seems to work great here at home, which was the biggest worry. I will try it at work, but that is just a minor concern. The home was major..TY for all your help,

---

### Post by cariboo on 2009-02-02
You may want to check with your IT department if they allow bit-torrent, after all it is the company's network.

Jim

---

### Post by ProNux on 2009-02-17
> **EvilBear said:**
> ok, got help in installing forums, it seems to work great here at home, which was the biggest worry. I will try it at work, but that is just a minor concern. The home was major..TY for all your help,

This may help...

[http://ubuntuforums.org/showthread.php?t=331161&highlight=transmission](http://ubuntuforums.org/showthread.php?t=331161&highlight=transmission)

---

