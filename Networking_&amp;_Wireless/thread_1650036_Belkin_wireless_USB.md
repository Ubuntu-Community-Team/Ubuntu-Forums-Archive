---
title: "Belkin wireless USB"
date: 2010-12-21
forum: Networking &amp; Wireless
---

### Post by Zucriy Amsuna on 2010-12-21
[COLOR=Navy]I have Ubuntu 10.10 on a laptop and need to have an internet connection. I also have a Belkin 802.11g "F5D7050 Wireless G Adapter v1000/v2000" (the quotes are what the lsusb command says). The Internet says that v1000 works nicely without much to do and that v2000 works well if you do something. However...

I simply can't get this thing to work. It does nothing. Ndiswrapper does nothing. Additional Drivers finds nothing. And I might have only a small idea how to use Network Connections (it just seems to do nothing at all with whatever I put in the fields). I've spent five hours too much research on this, and I give up. This place is my last hope.[/COLOR] [COLOR=Navy]

Will someone please help me?[/COLOR]  ](*,)

---

### Post by PhantmKllr on 2010-12-21
Use ndiswrapper with the driver from the wireless card's website. Then set ndiswrapper to load as a kernel module.

```
sudo ndiswrapper -m
```

Then

```
sudo ndiswrapper -ma
```

Then

```
sudo ndiswrapper -mi
```

Then restart.

---

### Post by Zucriy Amsuna on 2010-12-21
[COLOR=Navy]The website does not have .inf files, so ndiswrapper can't do anything.

Also, I checked the adapter on another computer, and it says that it is v1000. This doesn't have a driver on the site and should, according to sites like [http://linux-wless.passys.nl/query_part.php?brandname=Belkin](http://linux-wless.passys.nl/query_part.php?brandname=Belkin), work upon plugging it in (something with firmware?).
[/COLOR]

---

### Post by PhantmKllr on 2010-12-21
If the wireless adapter's manufacture provides windows executables, you can use a program like PeaZip to extract the drivers:

[http://www.peazip.org/]("http://www.peazip.org/")

---

### Post by Zucriy Amsuna on 2010-12-21
[COLOR=Navy]As I said, the site doesn't provide a driver for v1000. It's supposed to work automatically, but it doesn't.

I tried the driver for v2000, but ndiswrapper's Windows Wireless Drivers said that it was an invalid driver.
[/COLOR]

---

### Post by PhantmKllr on 2010-12-21
Well, all I know is that Belkin wirelss cards don't play well with Linux. I don't think that I can be of any help to you at this point.

---

### Post by Zucriy Amsuna on 2010-12-21
[COLOR=Navy]Thank you for your time, though.

This thing works well on Linux Mint (as v1000), but Ubuntu hates it. However, I can't stand Linux Mint...
[/COLOR]

---

### Post by PhantmKllr on 2010-12-22
Perhaps a future update will solve your issue. That's strange that Linux Mint supports, but Ubuntu doesn't.

---

### Post by Zucriy Amsuna on 2010-12-22
[COLOR=Navy]I went the other way. Ubuntu 9.10 happily accepted the Belkin wireless adapter. I don't know why the newer version couldn't accept it; my only guess is the compatibility of the adapter's Prism54 driver was lost because of its redundancy.

This thread is solved. Thank you for your time; at least I learned a little more about Linux. ^_^
[/COLOR]

---

### Post by mark bower on 2010-12-22
glad to hear you got it going.  for a long time i posted the F5D 7050 as a great USB wireless device, based on native Ubuntu driver support in 9.10.  i still use 9.10, tho with wifi PCI cards now so i can play with antenna's for more signal strength.  

i hate to see where newer versions become problematic.

mark bower

---

### Post by PhantmKllr on 2010-12-22
> **Zucriy Amsuna said:**
> [COLOR=Navy]I went the other way. Ubuntu 9.10 happily accepted the Belkin wireless adapter. I don't know why the newer version couldn't accept it; my only guess is the compatibility of the adapter's Prism54 driver was lost because of its redundancy.

This thread is solved. Thank you for your time; at least I learned a little more about Linux. ^_^
[/COLOR]
Sorry that we couldn't help you out more. Please marked the thread as solved. Thanks

---

