---
title: "Wireless and Linux"
date: 2006-03-01
forum: Networking &amp; Wireless
---

### Post by williamghanley on 2006-03-01
Im very New to Linux, and have a belkin wireless g desktop network card(f5d7001) and cant get anything to work with it. 
can someone please explain it to me and give me a solution.

im new to linux and probably wont understand technical things

---

### Post by Brunellus on 2006-03-01
You need to install the current driver.  Is it a USB wlan adaptor, a PCI card, or a PCMCIA (the sort tha slots into laptops) card?

---

### Post by jeremiebergeron on 2006-03-01
Your wireless card should work with ndiswrapper. See the following site and read it carefully:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu)

Ndiswrapper is a ubuntu program which uses Windows XP wireless drivers to make your card work under linux. The instructions are a tad complicated but everything is there.

Hope that helps.

Add: On that note, if you're going to use the examples on that page, make sure you use Example #2! Example #1 does some things which you should not have to do.

---

### Post by Brunellus on 2006-03-01
Ndiswrapper is neither necessary nor recommended with this card, as it runs the ralink chipset.

if it is a usb adapter, the following howto works:

[http://www.ubuntuforums.org/showthread.php?t=106846&highlight=rt2570](http://www.ubuntuforums.org/showthread.php?t=106846&highlight=rt2570)

---

### Post by jeremiebergeron on 2006-03-01
Ooops, ignore my post then. I didn't recognize the f5d7001 as a ralink card.

---

### Post by Brunellus on 2006-03-01
to the OP, if you have a PCI card, you want the RT2500 driver instead.  although I'm rather perplexed, since allegedly the rt2500 module ships with ubuntu by default.

---

### Post by williamghanley on 2006-03-02
thankyou for the help however
after typing:/usr/src/rt2570-1.1.0-b1/Module$ sudo make

i got this message: 
make: *** /lib/modules/2.6.12-9-386/build: No such file or directory.  Stop.
rt2570.ko failed to build!
make: *** [module] Error 1

Cna anyone please help me

---

