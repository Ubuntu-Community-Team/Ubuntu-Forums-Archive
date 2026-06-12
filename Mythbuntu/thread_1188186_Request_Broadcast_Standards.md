---
title: "Request: Broadcast Standards"
date: 2009-06-15
forum: Mythbuntu
---

### Post by Barky on 2009-06-15
hey all,

forgive me if this has been done, after searching for a while I couldn't come up with anything. I need a comprehensive guide to Clear QAM, NTSC, ATSC standards in cable. I see some scattered across the internet but can't seem to find what kind of tuner support I need for my setup. What is the difference between ATSC and Clear QAM? I've been told they are both digital HD cable formats, very confused about that one. What standard is being used on basic cable channels? on the HD "digital" channels (ones the are displayed in the format "XXX-XX" on my tv) what standard is that?

Just trying to find out what standard support I need for my HTPC, thanks.

---

### Post by bawilson2 on 2009-07-10
ATSC is the Advanced Television Systems Committee for digital television transmission.  Basically ATSC is digital and NTSC is analog.  QAM is a type of encryption that is used by cable companies to encrypt ATSC signals. Clear QAM is usually just used for local tv channels that are being rebroadcast by the cable company, like CBS, ABC, FOX, NBC and such.  For the non basic cable channels, like CNN, ESPN, TNT, TBS, they might have them broadcast in Clear QAM but from what I've heard they are usually on different channels so you'd have to do some mapping to get them to line up correctly.  For the premium cable channels, like ESPN HD, HBO, STARZ, they'd probably be encrypted using a QAM-256 encryption. 

Hopefully that helps out a little.  Let me know if you have any other questions.

---

### Post by agamotto on 2009-07-10
Most cable operators use QAM-256 for ANALOG channels.

Digital is usually left in 8-VSB format.  I have Mediacom analog cable, and I can get the digital pass-through channels by choosing Cable high in the scanning portion of Myth setup.  The downside is that the cable company seems to be blocking/dropping the 'guide' info from the channels, as a converter box hooked up to cable won't have info in the 'guide,' just as my television doesn't get the info.  Getting the digital channels OTA gets both the data and the guide working again, even under Myth.  Go figure.

---

### Post by Jayy on 2009-07-10
ATSC = Over the air digital channels
Clear QAM = Unencrypted digital cable channels
NTSC = Over the air analog channels (discontinued) and cable analog channels.

---

