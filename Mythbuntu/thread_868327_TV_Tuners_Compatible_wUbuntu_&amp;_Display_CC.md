---
title: "TV Tuners Compatible w/Ubuntu &amp; Display CC"
date: 2008-07-23
forum: Mythbuntu
---

### Post by kshsj777 on 2008-07-23
I have three questions:

1) Does Myth TV display captions? If not which tv programs will?

2) What tv tuners are compatible with myth tv (the cheaper the better) or with whatever program that will display captions.

3) How do I tell if a tv tuner supports displaying captions or not?

Thanks!
kshsj777

---

### Post by kshsj777 on 2008-07-26
Can someone at least answer some of my questions?  Thanks.

---

### Post by newlinux on 2008-07-26
I can only speak to what I have.

Yes Myth can display digital and analog captions. I use this feature from time to time. For digital transmissions I think any card will support captions (not sure, but every digital card I've used is capable - I think the CC information is embedded in teh digital stream). For analog I don't know - as I rarely watch analog channels.

As far as compatibility, nothing I've seen on the web is comprehensive, but check the myth tv wiki, linuxtv.org and the ubuntu documentation.

---

### Post by newlinux on 2008-07-27
Also, we could narrow down the tuners if you told us what type of signal you are trying to capture (ATSC OTA, QAM, NTSC, DVB-S, etc.)

---

### Post by agamotto on 2008-07-27
The Hauppauge line support CC pretty well.  I have both an older pvr-150 and a hvr-1800 card, both support CC quite well.  The matter of programming is up to the show creators/networks.  I quite often use CC during news casts as I quite often can't hear things when two or more people decide to start overspeaking each other.

---

### Post by kshsj777 on 2008-07-27
I'm not sure about the format... let's see...

digital = ATSC, so I want that
analog = NTSC, so I want that too   
Not sure what the other formats are.

So Hauppauge 150 works with myth tv and supports cc?  

Thanks

kshsj777

---

### Post by kshsj777 on 2008-07-27
I found out that hauppauge 150 is an analog only.  I need a hybrid that works with myth tv and supports CC.  Also, it doesn't really matter if it is usb or pci slot.

---

### Post by newlinux on 2008-07-27
[http://linuxtv.org/wiki/index.php/ATSC_PCI_Cards](http://linuxtv.org/wiki/index.php/ATSC_PCI_Cards) along with the other places I mentioned earlier are good place to start looking...

QAM is digital format for cable, ATSC is the digital format for OTA. (in the us). So if you want OTA cable you want an ATSC compatible card, if you want cable digital you'll want a card that is also compatible.

---

### Post by kshsj777 on 2008-07-27
Thanks for the link!

Any way to tell if these support captioning?  Or do all digital cards support captioning?

Nevermind, I saw they say analog cc.  What about the other new cc format?

---

### Post by newlinux on 2008-07-27
my understanding is that all of the digital cards simply capture the mpeg-2 stream from the signal, which should have any available CC information embedded in the stream. I could be wrong but I've used 4 different digital tuner cards that all provided closed captioning when available.

I should have given you this link:

[http://www.linuxtv.org/wiki/index.php/ATSC_Devices](http://www.linuxtv.org/wiki/index.php/ATSC_Devices)

so you can look at PCIe (of which I don't think there is any analog support yet) and USB tuners.

---

### Post by kshsj777 on 2008-07-29
Thanks for the link!

It is not so bad if it is just digital.

---

