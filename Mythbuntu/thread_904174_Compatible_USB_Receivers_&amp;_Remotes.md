---
title: "Compatible USB Receivers &amp; Remotes"
date: 2008-08-29
forum: Mythbuntu
---

### Post by jlp_engineer on 2008-08-29
This is probably an easy question with a hundred FAQ pages somewhere, but the more I read the more confused I am on what to purchase.  

I want to build a Myth installation with a single master backend with all the tuners and storage.  I will also build Front-Ends to match up with all the flat panel TV's I have.  I assume that since the tuners are going to be in the back-end in a different room that I will not be able to use their IR receivers.  So, my question is what Remote control and IR receiver combination should I buy???  I see a lot of homebrew receivers, both serial and USB, but it is not clear how Myth knows to listen at one of these ports for signals.  Can someone esplain?  

In general think I should stick to USB, as there seems to be a lack of serial ports on newer PC's these days.  I am sure that someone sells a nice cheap IR remote with a USB receiver.  Right now I don't need an IR blaster.  I have found one made by Cyberlink (20 USD), but have not found any support links in LIRC or Myth.

Recommendations?

TIA.

---

### Post by newlinux on 2008-08-29
The windows MCE remote/USB receiver combos used to be able to be had for about $30 at places like newegg.  I use MCE USB receivers with harmony remote controls.

---

### Post by bah1976 on 2008-08-29
Agreed - the Microsoft MCE works well.  Google a9o-00007 - that's the part number for the remote/IR receiver kit.  Depending on how many you need, they seem to be common in 3-packs for about $70.  Plus you get a nice slim remote for everyday functions.  The only drawback is that it's not a universal-type remote and the only buttons that can be programmed are TV power, and volume+/-.  But the IR receiver works great for any remote you point at it.

As for how - lirc is the keyword there.  Checkout lirc.org or just search the forums for more on that.  For the MCE specifically, try this:
[http://www.mythtv.org/wiki/index.php/MCE_Remote]("http://www.mythtv.org/wiki/index.php/MCE_Remote")

---

### Post by novellahub on 2008-08-29
The Streamzap remote is supported as well.  I did however had to edit the buttons in the lircrc to use Knoppmyth's default mapings since some of the buttons did not work the same in Mythbuntu.

[http://www.amazon.com/Streamzap-USBIR2-PC-Remote-Control/dp/B00008XETO](http://www.amazon.com/Streamzap-USBIR2-PC-Remote-Control/dp/B00008XETO)

---

### Post by DutchLoki on 2008-08-29
> **bah1976 said:**
>  As for how - lirc is the keyword there.  Checkout lirc.org or just search the forums for more on that.  For the MCE specifically, try this:
[http://www.mythtv.org/wiki/index.php/MCE_Remote]("http://www.mythtv.org/wiki/index.php/MCE_Remote")

Addendum: The MCE remote is supported by mythBuntu out of the box. Just connect it and than just select this remote in the mythbuntu configuration screen.

---

