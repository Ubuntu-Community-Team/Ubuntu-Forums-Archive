---
title: "Can't install windows driver using ndiswrapper"
date: 2009-09-18
forum: Networking &amp; Wireless
---

### Post by sebastiaopburnay on 2009-09-18
Hi, I have a desktop on witch I want to install an USB network adapter (belkin FD750 with ID 050d:705e) and I tried to use both the command line and the graphic versions and they both returned errors while atempting to install the drivers.

ndiswrapper: /usr/sbin/ndiswrapper-1.9: 1: Syntax error: ";;" unexpected
ndisgtk: Error while installing

Thank you

---

### Post by Cuba71 on 2009-09-18
According to another post in this forum, that usb adapter uses Realtek's RTL8187B.

Look [here]("http://www.datanorth.net/~cuervo/blog/rtl8187b-drivers-and-patches/") for more info

---

### Post by sebastiaopburnay on 2009-09-23
Well, I get the same error

/usr/sbin/ndiswrapper-1.9: 1:Syntax error: ";;" unexpected

I don't know what to do now, I opened the file [/usr/sbin/ndiswrapper-1.9] and it seems lique the ;; is being used to comment the rest of the line it is used on.

I hope you can give me new directions, this problem has been bugging me for a while and I'm getting desperate about it.

Thanks

---

### Post by Crafty Kisses on 2009-09-23
Have you tried uninstalling ndiswrapper and reinstalling it? I know it seems kind of like a generic solution but it's worth a shot. It also looks like your using ndisgtk, so remove that and let's get you the source of the newest ndiswrapper. So first you should remove and purge ndisgtk:
```
apt-get remove --purge ndisgtk
```
Once you have done that, if you haven't done so already you should probably grab build-essential you are going to need this to compile ndiswrapper from source, so run:
```
apt-get install build-essential
```
Then once you have done that you can actually grab ndiswrapper right [here.]("http://sourceforge.net/projects/ndiswrapper/files/") Once you have that, you the need to extract ndiswrapper, I'm just guessing you saved it to your desktop, so navigate to your desktop and extract it by running:
```
tar xvjf ndiswrapper*
```
Then once you have done that, you can actually start the compile by running:
```
make
make install
```
Then once it's compiled try using ndiswrapper again.

---

