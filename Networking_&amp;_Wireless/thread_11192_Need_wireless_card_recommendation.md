---
title: "Need wireless card recommendation"
date: 2005-01-14
forum: Networking &amp; Wireless
---

### Post by kepardue on 2005-01-14
Hello all,

After being frustrated with not being able to get a Netgear wireless card to work with Ubuntu, I've decided that I just need to get another one.  Does anyone here have any recommendations on laptop wireless cards that would work with Ubuntu without ANY configuration other than entering the WEP key (er... right out of the box support)?  I'd love to have a Ubuntu system on my laptop to play with, but don't have much experience or time to configure.

Many thanks in advance for recommendations!
Kenneth

Edited to add: "affordable" being the second consideration behind "works out of the box"-- most important.

---

### Post by kepardue on 2005-01-14
Thoughts on whether or not this card would easily work?

[http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&category=45000&item=5742682548&rd=1&ssPageName=WDVW](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&category=45000&item=5742682548&rd=1&ssPageName=WDVW)

Thanks,
Kenneth

---

### Post by jdodson on 2005-01-14
you can get the card to work.  my card which is a linksys, is not supported in the current version of ubuntu.  i used a program called ndiswrapper to get it working.

it works very well.

the docs on the ndiswrapper site are pretty easy to use.

you can install ndiswrapper from universe.

---

### Post by kepardue on 2005-01-14
Problem is I can't install ndiswrapper from the universe because the only way I have of connecting through the internet is *through*  the offending wlan card that's not configured.  ndiswrapper isn't included on the Ubuntu CD, is it?  If you're pretty confident that the card linked on ebay will work, I'm gonna go ahead and get one.

Thanks!
Kenneth

---

### Post by costoa on 2005-01-14
[QUOTE=kepardue]Problem is I can't install ndiswrapper from the universe because the only way I have of connecting through the internet is *through*  the offending wlan card that's not configured.  ndiswrapper isn't included on the Ubuntu CD, is it?  If you're pretty confident that the card linked on ebay will work, I'm gonna go ahead and get one.

Thanks!
Kenneth[/QUOTE]

If you're using Synaptic Package Manager just select the needed package, click "Apply" and select the checkbox "Download package files only". This will download the needed package(s) and store them in "/var/cache/apt/archives/". When you're ready to install just select the package previously selected, click "Apply" (on the toolbar) and click on the "Apply" button. The package(s) will now be installed without the need of a network connection.

Good Luck.

---

### Post by jdodson on 2005-01-14
[QUOTE=kepardue]Problem is I can't install ndiswrapper from the universe because the only way I have of connecting through the internet is *through*  the offending wlan card that's not configured.  ndiswrapper isn't included on the Ubuntu CD, is it?  If you're pretty confident that the card linked on ebay will work, I'm gonna go ahead and get one.

Thanks!
Kenneth[/QUOTE]

it sounded to me like you already have a wlan card.  if you do then get on a machine with internet access and download the ndiswrapper package(tar.gz) to a disk and then transfer it to your ubuntu.  you will have to install the gcc package that is on the ubuntu cd to compile ndiswrapper.  use that on the wlan card you have and configure it using the instrutions in the text file in the ndiswrapper source package.

i did not check the link for the card on ebay i have no idea if it works.  if you want to see what card are supported in gnu/linux natively run a google search, that might help.

i had the problem you described, i.e. couldnt get on the net with my ubuntu box, needed ndiswrapper for wlan, got it, compiled it, configed it.  now my ubuntu machine is on the internet.  i am reasonably confident you can get it working because i was able to.  however there are some cards that do not work in ndiswrapper, check the compatability list here: [http://ndiswrapper.sourceforge.net/phpwiki/index.php/List?PHPSESSID=2dbac40833a48cd1972674e93005267d](http://ndiswrapper.sourceforge.net/phpwiki/index.php/List?PHPSESSID=2dbac40833a48cd1972674e93005267d)

**EDIT** forgot to mention you will need to install the linux-headers package as well to get ndiswrapper to work.

---

### Post by castrojo on 2005-01-14
Don't use ndiswrapper for that card, ubuntu comes with the madwifi driver (the page says it's a madwifi card) out of the box. Install linux-restricted-modules, which is on the Ubuntu CD. 

Also, there's a list of cards on the wiki [here](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsWirelessNetworkCards/).

EDIT: We're talking about the card he linked right?

---

### Post by byourg on 2005-01-18
The Blitzz 712 super G works right out of the box. I just put in the WEP code and network name and it works.

---

### Post by wulfepup on 2005-06-06
[QUOTE=byourg]The Blitzz 712 super G works right out of the box. I just put in the WEP code and network name and it works.[/QUOTE]

I'm using the Ubuntu Live CD (Hoary 5.04 for AMD64) ...
I can't figure out how to get Ubuntu to even know I have this card (The Blitzz 712 super G) ... Help? 
 ](*,)

---

### Post by blu.gecko on 2005-06-18
check out the broadcom website the actually supply linux drivers for there ext. wifi cards, my onboard works with ndiswrapper........ :???:

---

