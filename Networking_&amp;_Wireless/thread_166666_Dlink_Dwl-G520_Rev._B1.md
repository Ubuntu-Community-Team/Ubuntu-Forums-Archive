---
title: "Dlink Dwl-G520 Rev. B1"
date: 2006-04-26
forum: Networking &amp; Wireless
---

### Post by Pimpity Snicket on 2006-04-26
(Dlink Dwl-G520 Rev. B1 ) <--PCI

*Sigh*...  I've been extensively looking up how to get my card working w/ Ubuntu or any other linux distro/livecd but I've had no luck so far.

First I installed Breezy and my card was detected as Atheros 5212 and shows up as ath0, but when I tried entering my key through gnome's network manager I couldn't get online.  I resorted to trying to configure my card from terminal using iwconfig trying a range of options but nothing has worked so far.  I get a signal but I can't get online.

[http://madwifi.org/wiki/Compatibility#DWLG520](http://madwifi.org/wiki/Compatibility#DWLG520)
My card is listed but no mention of Revision B1, and I had no luck finding any guides for my revision or peoples experiences w/ it.

I connected my pc to ethernet by my router and updated everything but still no luck.  I then upgraded to Dapper and still no luck.  I read somethin about hostapd and authentication but I have no idea if it even applies to fixing my card or how to use it.

I'm hoping to avoid using ndiswrapper but if anyone w/ my card and my revision has had a good experience please help me out, it would be much appreciated.  I've lost a lot of sleep over this card )-;

TIA

---

### Post by IYY on 2006-04-27
I am not sure about your card, but if it uses the atheros chipset (it seems that it does, since the correct driver is selected), it should work. Could you try to remove the protection key from your network and seeing if you can connect? It might just be a problem with authentication (it's tricky for some people).

---

### Post by Pimpity Snicket on 2006-04-27
[QUOTE=IYY]I am not sure about your card, but if it uses the atheros chipset (it seems that it does, since the correct driver is selected), it should work. Could you try to remove the protection key from your network and seeing if you can connect? It might just be a problem with authentication (it's tricky for some people).[/QUOTE]

That's what I figured but I have the key correct and I even disabled the key to test and it still didn't work.

---

### Post by Pimpity Snicket on 2006-05-01
I found the solution to my problem (finally!)...
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

If anyone else is having problems w/ this card, once you set your key w/ iwconfig (mine is a shared key so I also set 'iwconfig ath0 key restricted') then you have to set 'iwpriv ath0 authmode 2'.

```
When using wep, check driver files such as README as some drivers need a command to adjust the mode to work properly. Here are a couple examples.

*Madwifi driver needs to change to authmode 2 when using shared key setting.

o  manually from command line iwpriv ath0 authmode 2
o  add line pre-up iwpriv ath0 authmode 2 to interfaces file to automate during boot

```

---

