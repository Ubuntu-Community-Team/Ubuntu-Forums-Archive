---
title: "Belkin F5D7011 problems"
date: 2006-06-14
forum: Networking &amp; Wireless
---

### Post by dfoster on 2006-06-14
Just installed Dapper this morning and couldn't get the wireless card to work. Eventually after trawling many related threads decided the issue was that Dapper was using the bcm43xx driver but this fails to work with this card.

Solution was to install working driver using steps below:

1. Connect to internet using cable to router box.

2. Get correct driver and unzip file

Driver found here [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")

```

unzip -a R81435.EXE

```

3. Install driver (still connected to internet):-

```

sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
sudo ndiswrapper -m
sudo modprobe ndiswrapper

```

4. Then blacklist the bcm43xx driver:-

```

sudo gedit /etc/modprobe.d/blacklist

```
Add **blacklist bcm43xx**at the end of the file.

Jobs a goodun! :D

---

### Post by yanac on 2006-06-14
[QUOTE=dfoster]
Add **blacklist bcm43xx** at the end of the file.

Jobs a goodun! :D[/QUOTE]


It was on time! Thank you! =D>

---

### Post by betterliving on 2006-08-17
Thanks for the walkthrough, although I've hit a slight snag: after writing the modprobe configuration, I try inserting with sudo modprobe ndiswrapper and get "FATAL: Error inserting ndiswrapper (/lib/modules/2.6.15-26-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument" back. I've got only the faintest idea as to what this means and even less of an idea as how to fix it.... any help would be much appreciated, thanks!

---

### Post by acedward on 2006-08-21
try:
sudo ndiswrapper -l

it should say: 
bcmwl5   driver present

if it doesn't display it, something is wrong with your 'bcmwl5.inf'

---

