---
title: "Looking for IEEE/Firewire PC Card for laptop. will it work?"
date: 2007-12-02
forum: Multimedia Production
---

### Post by jonsayer on 2007-12-02
I want to hook up my miniDV camera to my laptop, which unfortunately lacks ieee/firewire ports. So I am thinking about buying a PC Card, something like this: [http://cgi.ebay.com/2-Port-Firewire-IEEE-1394-PCMCIA-Cardbus-PC-Card-ilink_W0QQitemZ330194533441QQihZ014QQcategoryZ60269QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/2-Port-Firewire-IEEE-1394-PCMCIA-Cardbus-PC-Card-ilink_W0QQitemZ330194533441QQihZ014QQcategoryZ60269QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)

Problem is, each one I find says it requires windows.

Is it likely that Ubuntu will have all the right drivers so my lappy can talk to the card and I can start capturing some video?

Not necessarily the product in the link, but just any old card like that?

---

### Post by Prefader on 2007-12-03
I have an ADS API-601 ([http://salestores.com/adsteappy13c.html](http://salestores.com/adsteappy13c.html)), and it works fine for me.  The only catch is that it doesn't supply power without a separate dc power supply (I think this is true of all PCMCIA firewire cards, since the laptop's bus doesn't supply enough power), so your 6 pin devices will need to be powered from elsewhere.

The card shows up in lspci as
```
03:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
```
Hope that helps!

---

