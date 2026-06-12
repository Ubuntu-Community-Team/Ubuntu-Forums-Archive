---
title: "Best USB Adapter(s) for 10.10"
date: 2010-10-30
forum: Networking &amp; Wireless
---

### Post by playaz on 2010-10-30
Hi guys,

I've got an Acer Aspire One D150 running UNR 10.10 (2yrs old but still running!) - I'd like to get a small, reliable and cheap USB adapter as the built in wifi device isn't cutting it.

Can you guys recommend some good cheap & small wireless adapters that will work right out the box without too much configuration.

P.S If you got links to UK sites even better!

Thanks in advance

---

### Post by playaz on 2010-11-05
Nobody got any ideas??? I'd just rather get the advice from a expert rather than an Ubuntu noob like me ;-)

---

### Post by jshuford on 2010-11-06
I too am looking at the same question!

The problem seems to be two-fold...

USB related and;

Which chip-set is used by what manufacturer.

I have had some decent results using a WUSB600N v.2 : [http://ubuntuforums.org/showthread.php?t=1590144&highlight=WUSB600N](http://ubuntuforums.org/showthread.php?t=1590144&highlight=WUSB600N)    credit to user rhill ...

---

### Post by jshuford on 2010-11-18
If you want a solution "out-of-the-box" then the Encore ENUWI-G2 is a good way to go... If you want wireless "N" then go with the Encore ENUWI-N4.

The -N4 needs firmware only, you can find it attached!

[http://ubuntuforums.org/showthread.php?t=1620923&highlight=8192SU](http://ubuntuforums.org/showthread.php?t=1620923&highlight=8192SU)

Ubuntu Forums user [chili555]("http://ubuntuforums.org/member.php?u=35909") deserves the credit on this one!

---

### Post by playaz on 2010-11-19
> **jshuford said:**
> If you want a solution "out-of-the-box" then the Encore ENUWI-G2 is a good way to go... If you want wireless "N" then go with the Encore ENUWI-N4.

The -N4 needs firmware only, you can find it attached!

[http://ubuntuforums.org/showthread.php?t=1620923&highlight=8192SU](http://ubuntuforums.org/showthread.php?t=1620923&highlight=8192SU)

Ubuntu Forums user [chili555]("http://ubuntuforums.org/member.php?u=35909") deserves the credit on this one!

Can't find any of those in the UK unfortunately - do you reckon this would work on Ubuntu?
[http://cgi.ebay.co.uk/Mini-Wireless-N-802-11n-g-WiFi-USB-WLAN-Network-Adapter-/200544177161?pt=UK_Computing_Networking_SM&hash=item2eb15d4c09#ht_1757wt_905]("http://cgi.ebay.co.uk/Mini-Wireless-N-802-11n-g-WiFi-USB-WLAN-Network-Adapter-/200544177161?pt=UK_Computing_Networking_SM&hash=item2eb15d4c09#ht_1757wt_905")

---

### Post by jshuford on 2010-11-19
> **playaz said:**
> Can't find any of those in the UK unfortunately - do you reckon this would work on Ubuntu?
[http://cgi.ebay.co.uk/Mini-Wireless-N-802-11n-g-WiFi-USB-WLAN-Network-Adapter-/200544177161?pt=UK_Computing_Networking_SM&hash=item2eb15d4c09#ht_1757wt_905](http://cgi.ebay.co.uk/Mini-Wireless-N-802-11n-g-WiFi-USB-WLAN-Network-Adapter-/200544177161?pt=UK_Computing_Networking_SM&hash=item2eb15d4c09#ht_1757wt_905)

I have always been very leery about ebay...

The adapter you mentioned uses the [FONT=Verdana][SIZE=2][SIZE=2]RTL 8188SU chip-set. Realtek has a driver for linux to use with it: [/SIZE][/SIZE][/FONT]http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=228&DownTypeID=3&GetDown=false&Downloads=true. I have never had much luck with dl'd drivers...

Either get one and try it, or do some research for an 8192SU chip-set based device or... contact someone and have them get one for you.

Sorry.

---

### Post by playaz on 2010-11-19
> **jshuford said:**
> I have always been very leery about ebay...

The adapter you mentioned uses the [FONT=Verdana][SIZE=2][SIZE=2]RTL 8188SU chip-set. Realtek has a driver for linux to use with it: [/SIZE][/SIZE][/FONT]http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=228&DownTypeID=3&GetDown=false&Downloads=true. I have never had much luck with dl'd drivers...

Either get one and try it, or do some research for an 8192SU chip-set based device or... contact someone and have them get one for you.

Sorry.

Dude that is really helpful don't apologise :-)

Hopefully get one soon cos my Aspire is in desperate need of the internet thanks again!

---

### Post by eddielad on 2011-01-11
I have also had issues with Acer AspireOne and its wireless connectivity. I found that installing wicd gave much better results. 

Information is availabe at [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) 

I think this program is available through Synaptic Package manager. 

Give it a go.

---

