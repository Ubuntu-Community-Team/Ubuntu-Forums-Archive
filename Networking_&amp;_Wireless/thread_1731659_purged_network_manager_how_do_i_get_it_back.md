---
title: "purged network manager how do i get it back"
date: 2011-04-17
forum: Networking &amp; Wireless
---

### Post by bobbyjackson on 2011-04-17
Hello I'm in a little bit of a bind I'm hoping not to have to reinstall the whole OS.

I was having very slow wireless internet after installing ubuntu and while googling some advice. someone mentioned to try the following command.

Sudo apt-get purge network-manager 

it didnt hit me right away what i was doing and when I restarted it hit me. So the question is can I download network manager from another PC and transfer it over via thumb drive or something?

All help is appreciated thank you.

---

### Post by josephmills on 2011-04-17
Yes you can but it is 30x easier to hook up to your router and download that way if possible.

---

### Post by lidex on 2011-04-17
How did you install - was it a LiveCD? If so just use the disk. It could even be in your apt-cache.

---

### Post by dineshs on 2011-04-18
With the help any other machine or OS download [COLOR="Blue"]network-manager[/COLOR] and [COLOR="Blue"]network-manager-gnome[/COLOR] from [packages.ubuntu.com]("http://packages.ubuntu.com/") (Select the correct distribution while downloading) .Copy it using a thumb drive to ubuntu.Doubleclick to install.

---

### Post by Sergei_K on 2011-04-18
try to establish your connection by /etc/network/interfaces
 
```
man interfaces
```

---

