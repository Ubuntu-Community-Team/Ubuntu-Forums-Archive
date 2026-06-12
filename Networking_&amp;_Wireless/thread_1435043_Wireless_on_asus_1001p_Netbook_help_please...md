---
title: "Wireless on asus 1001p Netbook help please.."
date: 2010-03-21
forum: Networking &amp; Wireless
---

### Post by Zone242424 on 2010-03-21
Hi 

Im a newb to ubuntu just wiped my brand new asus 1001p netbook of windwos 7 and put ubuntu netbook remix on it 9.10....

Everything works great except the wireless...

I know theres probally a billion topics on this, but i just need step by step easdy to follow guide on how to do this...

I asked the IT at my work and he claims it cant be done, unless i switch out the internal wireless to a card that "just works", which im not comfortable with or use a usb wireless stick, which defeats the purpose of a netbook being so small....

Im sure this can be done so please help me show up a IT that doesnt know linux :)

BTW the wireless card is a atheros thats all i know..

---

### Post by rudy.b on 2010-03-21
Hi, 

you may find this thread useful: [Asus EEE 1001P wireless & mobile broadband]("http://ubuntuforums.org/showthread.php?t=1396854").  It seems to deal with the same issue as you have.[URL="http://ubuntuforums.org/showthread.php?t=1396854"]
[/URL]

---

### Post by borabosna on 2010-03-22
I tried everything, madwifi etc... none works, it's all about having the RIGHT WinXp drivers. The drivers that came with my Asus Cd don't work. 

Visit [www.atheros.cz](www.atheros.cz)

If your card is an AR2427 like mine (also 1001p like you) then install ndiswrapper and ndisgtk, and using ndisgtk's graphical interface, install the XP-32bit drivers named 7.7.0.329 on the above website. You should install a file named 'netathw.inf' . 
The website doesn't let you choose drivers according to release number but rather according to the card you have. So, just click on SOME card in the list (one around the middle of the list) and then you will have a list of different releases for that card. 7.7.0.329 will be there. Click 'Download' below the explanation for 329, and then wait a little bit... it's coming from CZ so it takes some time for the download to begin. It's a 1.1mb file. 7.7.0.363 or 7.7.0.456 also works on my 1001p. 

If you need help installing ndiswrapper and ndisgtk just reply here.

---

### Post by olaf-g on 2010-03-28
I solved the issues with the wireless and the screen brightness control. As I am writing down my experiences and fixes in a blog you can find the exact steps over there:

[http://linuxon1001p.blogspot.com]("http://linuxon1001p.blogspot.com/2010/03/fixing-wireless.html")

For wireless I use a self compiled native driver which was really not difficult to do and the brightnes issue is fixed completely including on screen notifications and auto dimming working.

---

### Post by khunter1 on 2010-04-08
> **borabosna said:**
> I tried everything, madwifi etc... none works, it's all about having the RIGHT WinXp drivers. The drivers that came with my Asus Cd don't work. 

Visit [www.atheros.cz]("http://www.atheros.cz")

If your card is an AR2427 like mine (also 1001p like you) then install ndiswrapper and ndisgtk, and using ndisgtk's graphical interface, install the XP-32bit drivers named 7.7.0.329 on the above website. You should install a file named 'netathw.inf' . 
The website doesn't let you choose drivers according to release number but rather according to the card you have. So, just click on SOME card in the list (one around the middle of the list) and then you will have a list of different releases for that card. 7.7.0.329 will be there. Click 'Download' below the explanation for 329, and then wait a little bit... it's coming from CZ so it takes some time for the download to begin. It's a 1.1mb file. 7.7.0.363 or 7.7.0.456 also works on my 1001p. 

If you need help installing ndiswrapper and ndisgtk just reply here.

I would suggest to go to the official Driver site and download the .inf file:

[http://support.asus.com/download/download.aspx](http://support.asus.com/download/download.aspx)

And also post here:

[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.32/+bug/521967](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.32/+bug/521967)

---

### Post by uRock on 2010-04-08
> **Zone242424 said:**
> Hi 

Im a newb to ubuntu just wiped my brand new asus 1001p netbook of windwos 7 and put ubuntu netbook remix on it 9.10....

Everything works great except the wireless...

I know theres probally a billion topics on this, but i just need step by step easdy to follow guide on how to do this...

I asked the IT at my work and he claims it cant be done, unless i switch out the internal wireless to a card that "just works", which im not comfortable with or use a usb wireless stick, which defeats the purpose of a netbook being so small....

Im sure this can be done so please help me show up a IT that doesnt know linux :)

BTW the wireless card is a atheros thats all i know..

I ran this command to get my Atheros card working on my 1005 model Asus netbook.
```
sudo apt-get install linux-backports-modules-karmic
```
Hope it helps,
Ronnie

---

### Post by dionblundell on 2010-04-18
The backports never worked for me in Ubuntu 9.10 or 10.04beta1/beta2. Windows lists my driver as a AR2427, in an Asus 1005PE which I believe is similar?

I instead added the latest kernel modules manually. There is talk at the moment of having it in the backports for Lucid 10.04, but that is far from certain.

Anyway, this works for me, and I would suggest you give it a go.

This means the kernel has access to the latest wireless driver modules. It is better than the madwifi kludge, and of course, backports didn't work for me.

 Go here:
 [http://wireless.kernel.org/download/compat-wireless-2.6/](http://wireless.kernel.org/download/compat-wireless-2.6/)
 and download the latest drivers, for example:
 [URL="http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-04-16.tar.bz2"][http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-04-18.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-04-18.tar.bz2)
[/URL]
 Now extract these files
 Open a SHELL, and change into the directory created with the archive,  it's probably something like:
 ```
cd ~/Downloads/compat-wireless-2010-04-18
 
```now select the driver
 ```
./scripts/driver-select ath9k
```You now need to build the  drivers
 ```
make
```Now install them with this
 ```
sudo make install
 sudo make unload
 sudo modprobe ath9k
 
```You will need to do ALL the above EACH TIME the kernel is  updated.
 
 Networking works perfectly for me on my ASUS 1005PE now

---

### Post by eltonw on 2010-04-19
> **olaf-g said:**
> I solved the issues with the wireless and the screen brightness control. As I am writing down my experiences and fixes in a blog you can find the exact steps over there:

[http://linuxon1001p.blogspot.com]("http://linuxon1001p.blogspot.com/2010/03/fixing-wireless.html")

For wireless I use a self compiled native driver which was really not difficult to do and the brightnes issue is fixed completely including on screen notifications and auto dimming working.

I have had a quick look at your blog. _Is there any way to do this with the *live* CD?_ I'm not prepared to install the LUCID beta at this time, but running it as a live CD causes this problem:[http://ubuntuforums.org/showthread.php?p=9140633#post9140633]("http://ubuntuforums.org/showthread.php?p=9140633#post9140633")

I am running Karmic on an Asus EEE 1000 PC which has the RaLink 2860 card.


viele Danke!:)

---

### Post by jonathanross on 2010-04-28
Hi Dionblundell,

You just saved me a LOT of head scratching.

I can confirm this works on Lucid Lynx (RC) on the Asus 1001P 64bit (the newest laptop version of that variety) in case anyone else is looking for a wireless fix.

Wifi connects to WPA etc fine. If you're bored of upgrading kernels (and having to rebuild modules) then try [www.ksplice.com](www.ksplice.com) - it's fantastic.

Chocolate milkshakes are on me, Dionblundell !

JR :P

---

