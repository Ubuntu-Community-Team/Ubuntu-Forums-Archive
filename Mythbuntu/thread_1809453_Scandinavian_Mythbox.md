---
title: "Scandinavian Mythbox"
date: 2011-07-21
forum: Mythbuntu
---

### Post by Jompa on 2011-07-21
I live in Norway and I'm interested in setting up a Mythbox, so I wondered if any Scandinavian people have any tips on what hardware works for this in our area. I have satellite TV from Canal Digital, and especially wonder what you do about the card you get from your provider to use in the tuner?

---

### Post by agamotto on 2011-07-21
Whilst I am an American, I can answer your question about the satellite 'subscriber' card...  Most, if not all satellite providers require you to have their 'box,' which you usually wind up controlling with an IR blaster/channel changer from the Mythbox you setup.  Perhaps in Europe, you might be able to find a provider that allows the 'box' to talk directly to the Mythbox via USB or Firewire (1394)... but I seriously doubt it.

---

### Post by Jompa on 2011-07-22
So I will probably need the box from the provider along with the mythbox? Was hoping there would be a card reader I could get.

---

### Post by iamlindoro on 2011-07-22
> **agamotto said:**
> Whilst I am an American, I can answer your question about the satellite 'subscriber' card...  Most, if not all satellite providers require you to have their 'box,' which you usually wind up controlling with an IR blaster/channel changer from the Mythbox you setup.  Perhaps in Europe, you might be able to find a provider that allows the 'box' to talk directly to the Mythbox via USB or Firewire (1394)... but I seriously doubt it.

The above is actually the *opposite* of the case in most of Europe and Scandinavia, as well as many, many other DVB countries.  The above represents what one should expect with an American satellite provider.

To the OP:  You need a DVB-S tuner card with an integrated (not USB) CAM.  You need to make certain that both the card and the CAM are supported under linux.  At that point, you would insert your subscriber card into the CAM, and MythTV would scan and record your subscribed channels as normal.

You can see the linux supported cards with CAMs here:

[http://linuxtv.org/wiki/index.php/DVB_Conditional_Access_Modules](http://linuxtv.org/wiki/index.php/DVB_Conditional_Access_Modules)

---

### Post by agamotto on 2011-07-25
Hmmm, sounds like yet another reason to leave America!  Do you lot get to choose what channels you are paying for ala carte?

---

### Post by YaseenKriel on 2011-07-26
similar situation here in South Africa. DSTV is our satellite provider that supply decoder boxes. we use smart cards that we insert into the box and we get to watch what ever they have put in our packages.

now the box has RCA out puts and i have a 32" LCD panel that has RCA in put and AVI and HDMI ports that i can connect direct to my pc. i am looking for a capture device with RCA that will work with mythtv. anyone have any suggestions?

---

### Post by nickrout on 2011-07-26
RCA is not a video standard, it is a plug. composite (one plug, generally coloured yellow) is often delivered via rca. component (three plugs, generally red blue and green) is also generally delivered via rca.

If you have composite a pvr-150/250/350/500 is a good card because it compresses the analogue composite signal to mpeg2 in the card's hardware.

If you have component (which is far superior) you need a hdpvr device.

---

### Post by Jompa on 2011-07-27
I actually found a card reader to plug in the USB which shold work in Norway and Sweeden with a Hauppauge's HVR and NOVA TV-cards: [Hauppauge Smart CI USB]("http://prisguide.hardware.no/produkt/hauppauge-smart-ci-usb-88805") (link in Norwegian)

---

### Post by YaseenKriel on 2011-07-27
@nickrout thanx for the advice but the product is end of life. any other suggestions?

---

### Post by iamlindoro on 2011-07-27
> **Jompa said:**
> I actually found a card reader to plug in the USB which shold work in Norway and Sweeden with a Hauppauge's HVR and NOVA TV-cards: [Hauppauge Smart CI USB]("http://prisguide.hardware.no/produkt/hauppauge-smart-ci-usb-88805") (link in Norwegian)

As I mentioned before, USB card readers will not work.  None of them are supported in Linux.  You need a DVB-S card *with integrated CAM*.  You must pick from the list I linked above.

---

