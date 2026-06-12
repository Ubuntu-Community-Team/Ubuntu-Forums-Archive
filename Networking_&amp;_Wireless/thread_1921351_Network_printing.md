---
title: "Network printing"
date: 2012-02-06
forum: Networking &amp; Wireless
---

### Post by oldsoundguy on 2012-02-06
Recently acquired and installed an HP 2840 Color Laser All-In-One unit.  I have it installed directly on my network and can access it to print (not tried the fax or copy functions remotely .. not needed) without any issues from all of the computers on my net and can even print to it from my PDA when it is synchronized and networked .. that is I can print on the CMYK portion of the printer.  

HOWEVER, the unit comes with a secondary function that seems to work only in Windows.  That being a BLACK & WHITE ONLY driver (has HUGE separate toner cart for just that!)  The Linux boxes .. (everything from 10.04 LTS to 11.10 and Mint 9 and Mythbuntu) can access the CMYK standard function but not the CLJ2840PCL-6 Post Script driver (which is the B&W driver).

Sharing IS enabled. (Or at least it SAYS so on the Windows boxes on the network)

Sure would like to enable that B&W only as it is a GANG cheaper to operate in that mode for things like manuals, receipts and mailing labels and such.

Any suggestions will be appreciated.

---

### Post by praseodym on 2012-02-06
Tried the latest hplip version?

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

---

### Post by oldsoundguy on 2012-02-06
> **praseodym said:**
> Tried the latest hplip version?

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

Yes, latest version installed.  And the Linux based machines do NOT see the B&W as an installed network printer.  Color is fine. The Windows machines see both the Color and the B&W.

---

### Post by oldsoundguy on 2012-02-07
bumping as I still would like to find out something about this issue.  Thanks!

---

### Post by praseodym on 2012-02-07
Maybe the Linux-driver just doesnt support it?! Try

> hp-firmware

in a terminal

---

### Post by oldsoundguy on 2012-02-07
> **praseodym said:**
> Maybe the Linux-driver just doesnt support it?! Try



in a terminal

got:

error:  No devices that support firmware download found.

---

### Post by praseodym on 2012-02-08
Here are some other commands starting with "hp-":

```
hp-align           hp-hpdio           hp-plugin          hp-sendfax
hp-check           hp-info            hp-plugin-ubuntu   hp-setup
hp-clean           hp-levels          hp-pqdiag          hp-systray
hp-colorcal        hp-linefeedcal     hp-print           hp-testpage
hp-devicesettings  hp-makecopies      hp-printsettings   hp-timedate
hp-fab             hp-makeuri         hp-probe           hp-toolbox
hp-faxsetup        hp-mkuri           hp-query           hp-unload
hp-firmware        hp-pkservice       hp-scan            hp-wificonfig
```
Maybe one of these?!

---

### Post by oldsoundguy on 2012-02-18
> **praseodym said:**
> Here are some other commands starting with "hp-":

```
hp-align           hp-hpdio           hp-plugin          hp-sendfax
hp-check           hp-info            hp-plugin-ubuntu   hp-setup
hp-clean           hp-levels          hp-pqdiag          hp-systray
hp-colorcal        hp-linefeedcal     hp-print           hp-testpage
hp-devicesettings  hp-makecopies      hp-printsettings   hp-timedate
hp-fab             hp-makeuri         hp-probe           hp-toolbox
hp-faxsetup        hp-mkuri           hp-query           hp-unload
hp-firmware        hp-pkservice       hp-scan            hp-wificonfig
```
Maybe one of these?!

Nope, but thanks!!  Windows sees the B&W as a SEPARATE printer driver (HPCLJ24806), so think that CUPS may have dropped the ball on this one and that is up to Apple.  
This is NOT a brand new state of the art HP unit .. been around for a few years.  (newer ones are MUCH more expensive .. but have built in duplexing, something this unit lacks.  At the price I got this for, can live without that feature as, IF I need automatic duplexing, still have a pair of jets on the network that have it!!)  Really would like the B&W working in Linux, but it is not a deal breaker!

---

### Post by oldsoundguy on 2012-02-19
OK .. did some serious checking and it appears that the assumption that CUPS has dropped the ball is correct!  NO driver set up for OS-X either!  So will have to do the straight ahead black and white printing from a Windows box .. PITA, but doable!! 

Color printing and fax and scan work great!

For those that gave it a shot .. THANKS.

Mods .. go ahead and close this thread .. close/unsolved is not a user option.

---

