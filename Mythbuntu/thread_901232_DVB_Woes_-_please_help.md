---
title: "DVB Woes - please help"
date: 2008-08-26
forum: Mythbuntu
---

### Post by rflook on 2008-08-26
Hi there,

Finally after getting my internet connection back i am trying  (but failing) to get my Mythbuntu box to pick up freeview channels.

I have done a fresh install of the machine using 8.04.1. When it came to scanning for channels (I am in UK and selected Europe West for the channel frequency table) Mythbuntu picks up nothing. 

So i installed dvb-utils and dvbstream. I followed instructions on how to create a channels.conf file and then after running the following two commands

tzap -r "BBC ONE"
xine stdin://mpeg2 < /dev/dvb/adapter0/dvr0

I was able to watch the channel quite happily in Xine. So i know that my card works without issue, however how in gods name do i get it to work in myth. Please someone help me, this is the last thing i need to be able to do and then i will finally have a media centre i am happy with.

---

### Post by rflook on 2008-08-26
Hmm, just istalled kaffeine and that works fine too, any body give me any help please

---

### Post by newlinux on 2008-08-26
don't know much about non-us cards, but perhaps you can give is more information, like the card model, how you set it up in myth (card type, the rest of the scan settings). Also, I believe myth can import channels.conf files - maybe look into that.

Unfortunately i don't know what settings you should use, but maybe more info will help others help you.

---

### Post by rflook on 2008-08-26
newlinux, thanks for your post.

My card is a Winfast DTV1000-T, the card was set up as an Analogue V4L capture card. I left all the other settings in the setup as they were. 

I have also seen a few posts about importing the channels.conf file but i cant for the life of me figure out how to do that, it seems that where you would choose full scan on the channel set up you should instead choose import channels.conf, however for some reason i dont have that option available to me - odd.

---

### Post by newlinux on 2008-08-26
again, I am unsure of european cards. but if you are trying to tune digital stations you should use the DVB driver, not the V4L driver.

---

### Post by DutchLoki on 2008-08-26
I asume you realy use a dvb card instead of the analoge card mentionted above. Could it be you are using an DVB-C card for cable? if thats the case it could be you have the same problem as described in the following thread. 

[http://ubuntuforums.org/showthread.php?t=819903](http://ubuntuforums.org/showthread.php?t=819903)

if not can you give us the exact type of videocard you're using?

---

### Post by rflook on 2008-08-26
Thank you dutchloki for pointing out the bloomin obvious :-) Turns out all i needed to do was to change the card type to DVB DTV. Just did a scan and gots loads of channels pop up :-)

The reason i had it set at V4L was because i sometimes use the composite input on the card to record from my sky box, however the "DVB DTV capture card" option does not have the option to also use composite, but that i guess that is for another post :-)

---

### Post by newlinux on 2008-08-26
what I get no love for my suggestion of using the DVB driver? :)

For your analog needs just create a second capture card using the V4L driver. Then in input connections create an input group and put both inputs in the same input group so they can't be used at the same time.

---

### Post by DutchLoki on 2008-08-27
> **newlinux said:**
> what I get no love for my suggestion of using the DVB driver? :)

For your analog needs just create a second capture card using the V4L driver. Then in input connections create an input group and put both inputs in the same input group so they can't be used at the same time.

Excelent suggestion from newlinux... all love and hugs should go to him ;)

---

### Post by rflook on 2008-08-29
> **newlinux said:**
> what I get no love for my suggestion of using the DVB driver? :)

For your analog needs just create a second capture card using the V4L driver. Then in input connections create an input group and put both inputs in the same input group so they can't be used at the same time.

Sorry newlinux, big thanks to your suggestions as well, you guys have been a real help :-)

---

