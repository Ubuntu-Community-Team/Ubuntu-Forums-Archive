---
title: "On the fly DTS/Dolby Digital encoding"
date: 2007-07-22
forum: Multimedia &amp; Video
---

### Post by NCAANFI on 2007-07-22
Can anyone tell me of any PCI soundcards that are linux friendly and capable of on the fly Dolby Digital/DTS encoding?

---

### Post by NCAANFI on 2007-07-22
So I guess no-one uses Ubuntu for HTPC and is trying to get dolby digital. that's a shame, what's the point of having HD when you can't get DD

---

### Post by untoldone on 2007-10-26
I use Ubuntu for a HTPC... To respond to your latter post -- you don't need to encode to dolby digital to output dolby digtial sound.  Chances are you either need to decode it and pass it to your (potentially 5.1 speakers) via analog cables, or you can have it pass through from a dolby digital/dts source (such as the audio from most DVDs) over spdif to your receiver/amplifier that support dolby digital.  Both of these can be done with ease in general given the correct hardware and maybe a few searches....first thing to check is that the correct outputs are enabled in alsamixer.

To respond to the first post:  I have wondered the same thing.  Is it possible to encode in real time (dolby digital live/DTS Connect)?  I bought a soundcard (Montego DDL) that advertises its support for dolby digital live, which is supposed to be real time dolby digital encoding, but I have no idea if the linux drivers support this feature.  I also don't know if there is something out there that does real time software encoding to dolby digital in linux ... or windows for that matter

---

### Post by lane32x on 2007-11-01
Hmm. the DDL card from Montego was working fine for me in Feisty and in Edgy. my digitial optical output was always the only thing linking my computer to my receiver. 

however, upon updating to not only Gutsy, but also to Linux Mint...I can not get sound thru the digital optical cable. 

it used to be that all you had to do was open a console window (xterm, konsole, whatever) and open alsamixer. then you had to un-mute one of the CMI devices that was muted. ...that was it.  ...none of mine fix my problem currently however.  ...hope this helps. kinda vague, i know. sorry

Jay

---

### Post by lane32x on 2007-11-01
Nevermind.  got it working. the Montego DDL at least sends everything through the digital optical cable.

opened alsamixer, enabled the <IEC958  0> and muted the other IEC958 channels. it works like a charm now.

---

