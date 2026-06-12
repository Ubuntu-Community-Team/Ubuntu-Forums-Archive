---
title: "Remote control solution"
date: 2011-03-06
forum: Mythbuntu
---

### Post by itlarson on 2011-03-06
I am looking for a new universal remote for my entertainment center.  I need to control an all-in-one mythbox, an AV reciever, a DVD player, and a plasma TV.  I might be adding something which can stream Netflix and Hulu, like a Roku, Boxee, or even PS3.  Here is what I would consider the ideal remote control system:

-The remote would have RF capability as well as IR
-There would be a base station which sits by the AV components and mythbox, to receive the RF signal
-IR blasters connected to the base station would control AV components.
-A USB cable from the base station would send MCE compatible input to the mythbox.  The USB cable could also power the base station.  
-The remote would control the TV directly with IR.

I'm pretty sure this is a product which doesn't exist.  There are RF universal remotes that have a base station and IR blasters, but don't interface with a media computer, and there are RF MCE remotes which only control the computer.  I haven't found anything which can do both.

Currently I am leaning towards getting a product made by URC.  They have a package combining a RF remote, and a base station with six IR blasters.
[http://www.universalremote.com/products/retail/bundles/urc-rfs200](http://www.universalremote.com/products/retail/bundles/urc-rfs200)  I would have to put one of the IR blasters on my MCE receiver, (which is kind of a kludge) but it does everything else, and is only $80 on Amazon.

I have rejected the Logitec harmony 900 remote because of it's price, It's having only two IR blasters, and it's needing to be connected to a windows computer to be set up.  It isn't as well reviewed on Newegg either.

Before I buy anything, I am asking people on the forum how the URC solution looks to them, or if they have any better ideas.  I am also interested in what remotes people are using, and what components they are controlling with them.

---

### Post by newlinux on 2011-03-07
I know you've rejected the Harmony, but those are what I use. I have two old 680s (still love them) and a 720. All are only IR, but they work great. They all  control various components (Denon Receiver, JVC receiver, DirecTV boxes, cable boxes, mythboxes, pioneer tv, Westinghouse TV, Vizio TV, Samsung TV, and a couple of dvd players and ziova z500 networked dvd player, a fan, etc.). I don't know if it supports the harmony 900, but  I use congruity/concordance to program my harmony in Ubuntu - no need for the windows software.

Good luck in your search.

---

### Post by itlarson on 2011-03-07
I should have known that there would be linux software for the harmony.  How do you connect it to mythtv?

---

### Post by newlinux on 2011-03-07
> **itlarson said:**
> I should have known that there would be linux software for the harmony.  How do you connect it to mythtv?

I use cheap MCE ir receivers to connect it up to the HTPCs, and then LIRC for use with mythtv. I've got a custom lircd.conf that uses codes from MCE and snapstream remotes for all the buttons/commands I want to use with the HTPCs

---

### Post by rhpot1991 on 2011-03-07
Your best bet is a [Logitech Harmony]("http://www.amazon.com/gp/product/B002RL875A?ie=UTF8&tag=baablogicnet-20&linkCode=as2&camp=1789&creative=390957&creativeASIN=B002RL875A") or [This Cheaper Harmony]("http://www.amazon.com/gp/product/B0038OMEQI?ie=UTF8&tag=baablogicnet-20&linkCode=as2&camp=1789&creative=390957&creativeASIN=B0038OMEQI").

Then get [this MCE remote]("http://www.amazon.com/gp/product/B000W5GK5C?ie=UTF8&tag=baablogicnet-20&linkCode=as2&camp=1789&creative=390957&creativeASIN=B000W5GK5C") just for the receiver.

The Harmony will be able to throw everything you can at it, you can use concordance to program it in ubuntu.  Then with that MCE receiver it will just work in LIRC as a mceusb device, nice and easy to setup.

---

### Post by pu15e on 2011-03-07
For our 525, we bought a ~$AUD25 MCE-compatible remote from Jaycar (an electronics chain here in AU). It comes with a Holtek / Belkin USB IR receiver which pretends to be a keyboard (and mouse, if you could be bothered).

There are a couple of buttons that need to be re-mapped on your Myth boxen (they are upper case copies of a couple of the other commands, and Myth can't discern between upper and lower case commands). IIRC, one doesn't need to do that if one uses LIRC (with the Linux event driver)...

Works reliably, with or without LIRC :-)

Cheers,
 Mattt.

---

### Post by rhpot1991 on 2011-03-07
> **pu15e said:**
> For our 525, we bought a ~$AUD25 MCE-compatible remote from Jaycar (an electronics chain here in AU). It comes with a Holtek / Belkin USB IR receiver which pretends to be a keyboard (and mouse, if you could be bothered).

There are a couple of buttons that need to be re-mapped on your Myth boxen (they are upper case copies of a couple of the other commands, and Myth can't discern between upper and lower case commands). IIRC, one doesn't need to do that if one uses LIRC (with the Linux event driver)...

Works reliably, with or without LIRC :-)

Cheers,
 Mattt.

Its generally worth the few extra $s to make sure you get something that will work well and not the cheapest MCE receiver.  The ones that are a larger squarish receiver with 2 blaster ports are related to the official Philips MCE devices (like the one I linked).  The ones that are thinner are normally generic ones, which should work but may require some tweaking.

---

### Post by itlarson on 2011-03-09
Thanks for all the replies.  From what I am hearing people say, I think it will worth it to give the URC remote a try.  It's a lot cheaper, has more IR  blasters, and uses RF.  It looks like the only way to control Mythtv through RF at this time is to hook one of the IR blasters to my MCE reciever.  That or use one of those RF MCE remotes, but that would require a separate remote for everything else.  After I get back from vacation I will buy the remote and post a review.

---

### Post by Ülgen on 2011-05-24
Hello 

I found following device in my country (it's in Turkish but has photos)

[http://www.sahibinden.com/ilan/alisveris-bilgisayar-cevre-birim-microsoft-remote-control-and-receiver-model-no-1040-44812399/detay/](http://www.sahibinden.com/ilan/alisveris-bilgisayar-cevre-birim-microsoft-remote-control-and-receiver-model-no-1040-44812399/detay/)

I think it will work with Ubuntu 11.04, right ?. Could you verify that?

Thanks for your responses

Best regards
Ülgen

---

### Post by Meph1st0 on 2011-05-25
If price isn't an issue then I could suggest a solution from Control4.  They are a home automation company that provides a controller that'll control not only your entertainment system but anything else you can think of for your home.  It can also be configured to control your mythbox as well.  I've been using this system for a couple years and love it.  Expect to spend close to $1000.00 just for the controller and remote control.  Additional capabilties will cost more.

Just a suggestion anyway.  Check them out at [www.control4.com](www.control4.com).

---

### Post by phroman on 2011-06-01
I am not a fan of Sony products but this remote control is actually pretty good.  It would at least take care of all your IR needs.  It has numerous manufacturers codes built in or can it learn them if it doesn't.  I had one and liked it while I used it.  Here's an amazon link to it.

[http://www.amazon.com/Sony-RM-AV3100-18-Device-Editable-Universal/dp/B0001R05Y8/ref=sr_1_11?s=electronics&ie=UTF8&qid=1306959226&sr=1-11](http://www.amazon.com/Sony-RM-AV3100-18-Device-Editable-Universal/dp/B0001R05Y8/ref=sr_1_11?s=electronics&ie=UTF8&qid=1306959226&sr=1-11)

---

