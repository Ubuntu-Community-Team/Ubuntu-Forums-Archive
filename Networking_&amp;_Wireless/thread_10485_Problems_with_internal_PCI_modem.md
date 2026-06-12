---
title: "Problems with internal PCI modem"
date: 2005-01-08
forum: Networking &amp; Wireless
---

### Post by haakon on 2005-01-08
I have built a PC for my father, who has hardly any experience with computers from before. To avoid having to support problems caused by worms and spyware, I decided to install Ubuntu on his machine. It's been working great so far, I've been showing him around the menus and important applications, and he is catching on.

The problem, however, is internet access. He doesn't need broadband, so I got him a 56.6 PCI modem. My only experience with modems from before is the old external serial ones. I tried one I had lying around, and it worked fine. However, that's only a 28.8 modem, and wow, I had really forgotten all about how slow they were.

I could not get the 56.6 modem working at all. lspci shows the modem alright. I haven't been messing with ppp for years, so I had to rely mostly on the GUI tools (which worked surprisingly well for his printer). This is the 100% standard Ubuntu desktop, I go to Applications -> System configuration (or something) -> Network. I chose to add a new PPP/modem connection. It prompted me for phone number, username and password, and I was done. But it made no attempt to connect. The little checkbox next to the modem connection got activated for around 1-2 seconds, then deactivated again. The same when I manually pressed "Activate" on the connection. I selected "Properties" or "Configure" (I'm working by memory here, I don't remember exactly), and I saw the modem device was /dev/modem, which didn't exist. So I pressed on the "Detect automatically" button, which worked for some 10 seconds before letting me know it couldn't detect anything. This detection had worked fine on the old 28.8 serial modem, but not now. So instead, I tried to enter /dev/ttyS1 through /dev/ttyS5, but it was the same -- checkbox got activated, wait 1-2 secs, got deactivated.

I naturally checked /var/log/messages. It seemed like for every time I tried to dialup and connect, there was one line saying "PPP whateverversion blahblah" (just showing PPP starting up), immediately followed by a line saying "PPP disconnected". 

So I'm interested in any suggestions. Debugging is unfortunately very impractical since he lives a while away, and there is no net access there (until I get that modem working). If there are any additional packages I need, I can burn them here and pay a visit, but it would be nice to get it working too, so not to give him the impression of computers being hard to use and unreliable ;)

Thanks for any suggestions, and for a great distribution!

---

### Post by tiiim on 2005-01-08
[QUOTE=haakon]I have built a PC for my father, who has hardly any experience with computers from before. To avoid having to support problems caused by worms and spyware, I decided to install Ubuntu on his machine. It's been working great so far, I've been showing him around the menus and important applications, and he is catching on.

The problem, however, is internet access. He doesn't need broadband, so I got him a 56.6 PCI modem. My only experience with modems from before is the old external serial ones. I tried one I had lying around, and it worked fine. However, that's only a 28.8 modem, and wow, I had really forgotten all about how slow they were.

I could not get the 56.6 modem working at all. lspci shows the modem alright. I haven't been messing with ppp for years, so I had to rely mostly on the GUI tools (which worked surprisingly well for his printer). This is the 100% standard Ubuntu desktop, I go to Applications -> System configuration (or something) -> Network. I chose to add a new PPP/modem connection. It prompted me for phone number, username and password, and I was done. But it made no attempt to connect. The little checkbox next to the modem connection got activated for around 1-2 seconds, then deactivated again. The same when I manually pressed "Activate" on the connection. I selected "Properties" or "Configure" (I'm working by memory here, I don't remember exactly), and I saw the modem device was /dev/modem, which didn't exist. So I pressed on the "Detect automatically" button, which worked for some 10 seconds before letting me know it couldn't detect anything. This detection had worked fine on the old 28.8 serial modem, but not now. So instead, I tried to enter /dev/ttyS1 through /dev/ttyS5, but it was the same -- checkbox got activated, wait 1-2 secs, got deactivated.

I naturally checked /var/log/messages. It seemed like for every time I tried to dialup and connect, there was one line saying "PPP whateverversion blahblah" (just showing PPP starting up), immediately followed by a line saying "PPP disconnected". 

So I'm interested in any suggestions. Debugging is unfortunately very impractical since he lives a while away, and there is no net access there (until I get that modem working). If there are any additional packages I need, I can burn them here and pay a visit, but it would be nice to get it working too, so not to give him the impression of computers being hard to use and unreliable ;)

Thanks for any suggestions, and for a great distribution![/QUOTE]
 have you seen if the drivers are available? internal modems are not exactly the best things on the planet with the ol' driver front...

---

### Post by haakon on 2005-01-08
I can't say I have checked if drivers are available or if it's supposed to work in Linux at all. The guy at the store talked to another guy and said this particular card has been known to work with Linux.

Would an external USB modem have a better chance? Good old serial modems don't seem to be available anymore.

---

### Post by tiiim on 2005-01-08
[QUOTE=haakon]I can't say I have checked if drivers are available or if it's supposed to work in Linux at all. The guy at the store talked to another guy and said this particular card has been known to work with Linux.

Would an external USB modem have a better chance? Good old serial modems don't seem to be available anymore.[/QUOTE]
 USB modems are generall more supported and if you buy one some of them today have linux drivers on the cd.

Your card maybe supported try [http://linmodems.org/](http://linmodems.org/) or google around if not find the usb that comes with Linux supported.

---

### Post by haakon on 2005-01-08
I don't think the PCI card is a winmodem. I asked specifically if it was in the store, and they said no, completely standard stuff. I did see "Conexant" mentioned on the card, though, and they are listed as a winmodem chipset ... Hm.

I see I forgot to mention which card it is. It's a CNet CN5614RV (56k V90/92), quite low-priced.

Thanks for your input so far.

---

### Post by tiiim on 2005-01-08
[QUOTE=haakon]I don't think the PCI card is a winmodem. I asked specifically if it was in the store, and they said no, completely standard stuff. I did see "Conexant" mentioned on the card, though, and they are listed as a winmodem chipset ... Hm.

I see I forgot to mention which card it is. It's a CNet CN5614RV (56k V90/92), quite low-priced.

Thanks for your input so far.[/QUOTE]
 after looking around i dont think your modem is officially supported you can hack it and make it work but i dont think they provide the official drivers. So either hack it following a how to or take it back and get a usb one with the Linux drivers on the cd... if in doupt google for usb modems that work on Linux. At the same time if you have problems under networking you can get hold of GNOME-PPP or something that may help you connect. Could work with this one but you need to download the file speratly and install it under Ubuntu.

---

### Post by jkndrkn on 2005-05-18
[http://www.newegg.com/ProductSort/SubCategory.asp?Subcategory=18](http://www.newegg.com/ProductSort/SubCategory.asp?Subcategory=18)

I'm thinking of buying the Hawking RS232 modem:

[http://www.newegg.com/Product/Product.asp?Item=N82E16825100204](http://www.newegg.com/Product/Product.asp?Item=N82E16825100204)

The PCI modem I have has proven impossible to set up so far.

---

