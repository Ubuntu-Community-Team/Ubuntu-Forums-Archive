---
title: "64 bit WEP Wireless not working"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by thedon_1 on 2010-01-15
I just built a new HTPC based on a zotac IONITX A-B board.

I am trying to connect to my wireless network but i'm not getting an option in Ubuntu to use 64 bit WEP (which is what i'm using)

It has 128 bit but not 64.

Any ideas how to fix this?

---

### Post by chili555 on 2010-01-15
I believe it has the option of 40/128-bit WEP. 40-bit WEP is actually 64-bit. Please see: [http://en.wikipedia.org/wiki/Wired_Equivalent_Privacy](http://en.wikipedia.org/wiki/Wired_Equivalent_Privacy) especially:> Standard 64-bit WEP uses a 40 bit keyPlease put your key in the 40/128-bit key space and connect.

---

### Post by thedon_1 on 2010-01-16
No luck with that.
I know i'm entering the key in correctly, i'm using it on every other device in the house.

---

### Post by thedon_1 on 2010-01-16
Just to let you know, the Wifi card in the PC is an N one.
The router is s standard b/g. I know N cards can receive b and g, but is there maybe some setting i need change?

---

### Post by bkratz on 2010-01-16
> **thedon_1 said:**
> Just to let you know, the Wifi card in the PC is an N one.
The router is s standard b/g. I know N cards can receive b and g, but is there maybe some setting i need change?

Just went to the webpage

[http://translate.google.com/translate?hl=en&sl=de&u=http://pden.zotac.com/index.php%3Fpage%3Dshop.product_details%26product_id%3D169&ei=DbFRS-K5PIWmNuOP_IIJ&sa=X&oi=translate&ct=result&resnum=1&ved=0CBAQ7gEwAA&prev=/search%3Fq%3Dzotac%2BIONITX%2BA-B%2Bboard%26hl%3Den](http://translate.google.com/translate?hl=en&sl=de&u=http://pden.zotac.com/index.php%3Fpage%3Dshop.product_details%26product_id%3D169&ei=DbFRS-K5PIWmNuOP_IIJ&sa=X&oi=translate&ct=result&resnum=1&ved=0CBAQ7gEwAA&prev=/search%3Fq%3Dzotac%2BIONITX%2BA-B%2Bboard%26hl%3Den)

and it says N (your are right) but it says nothing about being downward compatible with previous versions. I doubt that it is.


Nevermind I found this also

 802.11n connections should support data rates of over 100 Mbps. 802.11n also offers somewhat better range over earlier Wi-Fi standards due to its increased signal intensity. 802.11n equipment will be backward compatible with 802.11g gear.

---

### Post by thedon_1 on 2010-01-16
When i was buidling the PC, i saw the actual component and written on it was 802.11 b/g/n

---

### Post by bkratz on 2010-01-16
> **thedon_1 said:**
> When i was buidling the PC, i saw the actual component and written on it was 802.11 b/g/n

By the way I use 9.04 and it does give the option of 40/128 on mine.  Anyway, have you ever successfully connected to the router, say perhaps without any encryption or a different type of encryption? I do remember seeing something somewhere about the way pass phrases versus keys are entered but that may have been only if not using network manager, I will try to find that article and see if it is relevant.

---

### Post by bkratz on 2010-01-16
Well that was quick, it was in this thread
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)
about manually connecting in the section 

WEP Connection

You must have either your 64bit or 128 bit HEX Key or the ASCII Equivalent of your HEX Key.

Code:
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> key HEX_KEY <<<-------- If using ASCII Equivalent, this is s:ASCII_KEY (please make note of the prefix s:)
****Additional Comand that may be needed  -- sudo iwconfig <interface> key open  <<<----See note below
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>


and was about adding a prefix---so it is not relevant to what you are doing-sorry still looking

---

### Post by thedon_1 on 2010-01-16
I disabled security on the router and i still couldn't connect wirelessly.

Ok so i'm pretty sure it's the driver.

I have an Atheros Communications Inc. AR928X. Looks like other people have had this same problem but i have no idea how to install new drivers.

Anyone..please!

---

