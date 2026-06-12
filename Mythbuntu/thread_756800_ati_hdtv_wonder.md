---
title: "ati hdtv wonder"
date: 2008-04-16
forum: Mythbuntu
---

### Post by jrhartley on 2008-04-16
Ive just recently switched from mythdora 4 to mythbuntu 8.04. everything went smoothly except mythbuntu doesnt properly recognize my hdtv wonder. in mythdora when i selected generic dvb card the driver it selected was the nextwave 2002/2004 or something like that. this is not what happens in mythbuntu.mythbuntu has no problem with my dvico card only the ati. does anyone know how to fix this?

---

### Post by jrhartley on 2008-04-16
ok no replies yet...does anyone have an older ati hdtv wonder working in mythbuntu 8.04. if yes how did you do it?..thanx

ps Im using it to tune unencrypted qam out of time warner cable not ota ive had it working no problems in mythdora 4

---

### Post by blackoper on 2008-05-30
I'm going to mess with it now. i have the ati hdtv wonder and I'll see if it works correctly for me. I also have the aver a180 which uses the same firmware right now they are showing up as air2pc cards

---

### Post by blackoper on 2008-06-03
I've gotten both the ati hdtv wonder and the avermedia a180 cards working fine. You have to install the nxt-2004.fw firemware by downloading source and then pulling the firmware. I'll post the topic I referenced to install it. I favorited it on my home computer. It still says air2pc in mythtv setup but the cards now work correctly.

Here is the the post I used to get the nxt-2004 driver up and running.
[http://www.backports.ubuntuforums.org/showpost.php?p=4203943&postcount=5](http://www.backports.ubuntuforums.org/showpost.php?p=4203943&postcount=5)

---

### Post by richwillal on 2008-07-01
I started out with Ubuntu 7.04 running MythTV and an HDTV Wonder.  I got it working with the nxt2004 firmware, and everything worked great.  I then upgraded to 7.10 and everything stopped working.  I just get garbage when I try to use it.  I'm planning on a re-install (new box) soon, so I was going to wait to fix it.  I'd like to use the original firmware if possible, but don't know what's required to switch back.

Anyone know if there's an easy way to do this or if the process noted here: [http://www.backports.ubuntuforums.org/showpost.php?p=4203943&postcount=5](http://www.backports.ubuntuforums.org/showpost.php?p=4203943&postcount=5) is still applicable?

TIA.

---

### Post by blackoper on 2008-07-14
anytime you update the kernel you need to re-download the source and move the nxt-2004.fw to the new generic kernel listed in /lib/firmware otherwise the card will stop working (a lot of times you don't need a new firmware file just copy the old one over )

---

