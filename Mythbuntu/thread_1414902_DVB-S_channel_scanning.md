---
title: "DVB-S channel scanning"
date: 2010-02-24
forum: Mythbuntu
---

### Post by My Name on 2010-02-24
I have a fully working Mythtv setup and I am very happy with it, but I have never been able to get the EIT to work on the DVB-S card. i have no problem with the DVB-T one.

I think it is because I have to import a channels.conf file rather than letting mythtv do the scanning. Unfortunately scanning in mythtv never works for satellite TV.
Is there a way of getting the scanning of DVB-S to work in mythtv? If nothing else but to test my theory.
I am in the UK using a Nova-S card I think. I'm not a 100% sure of the model number though, but I suspect it matters little.

---

### Post by SiHa on 2010-02-24
I've got an old Nova-S, managed to scan OK, and EIT does work.

It was a while ago, but here's what I did, as best as I can recall, on a fresh install of 9.10 i386. I won't bother with the LNB bit, as I guess you must have that working already! 

I'm using the details for Atra2D 28.2°, and using the transponder that has BBC-HD, 'cos that's all I wanted really. It seems that once it has one transponder, it will find them all.

Edit: Here's a link to lyngsat, if you want any other transponders: [http://www.lyngsat.com/astra2d.html](http://www.lyngsat.com/astra2d.html)

One important point to note. The helper text at the bottom of the screen tells you that the frequency should be in KHz. This is **wrong**, it should be in Hz. I've sumitted a bug report, but I guess it's fairly low-priority, so nothing's hapened.

Anyway:

[B]Scan type: Tuned - Full Scan
Services: TV Only, Non-Encrypted only
Transponder: Frequency 10847000
Polarisation: Vertical
Symbol Rate: 22000000
FEC: Auto[/B]

I have the feeling that there's another box above the FEC, but I can't recall the name. That should be Auto too.

This won't get ITV-HD. I was told that you need to select 'All Services', rather than just TV, because it is detected as an MHEG stream. Doing this, I got loads of ITVi channels, but none of them are ITV-HD, so I gave up on this one.

The first time I ran this scan it bombed after sitting @ 100% for 5-10s, so next time I waited until it got to 100% then stopped it. It might mean I've missed 'babestation east midlands', but I can probably live with that. Just make sure you hit 'Stop' rather than 'Cancel', otherwise, you'll have another 20 minute wait. Not that I ever did that myself, you understand:D

This should hopefully give you about 150 channels found. I found the easiest way to get rid of all the trash was to let it import them all, then open up the channel list in Mythweb and delete all the ones you don't want. It's important to delete them, rather than just make them 'Not Visible', otherwise they will still come up in searches, like Program Finder for recording scheduling. I found the 'Stroke my pu**y' type show names from Television X a bit wearing.

Do you have a DVB-T card as well? If so, in order to get Myth to use the DVB-S card for a freeview recording when your DVB-T tuner(s) are busy, you need to edit the DVB-S freeview channels in Mythweb, so that their channel numbers and callsigns are identical to the DVB-T ones.

Edit2: I've not tried the 'Enable Cross-Source EIT Data', but if you can't get the above to work, maybe you could try this to at make Myth assign the DVB-T data to the DVB-S freeview channels.

Hope this helps some.

Cheers,

Simon

---

### Post by My Name on 2010-02-24
excellent!
I'll give this a pop. Thanks for the info, the missus will be chuffed if this works for me

---

### Post by My Name on 2010-02-25
Woop woop, that works a treat :popcorn:

just one question though, how does the info get linked to the channels? Is it through the channel number, name or something else? The reason I ask is that I would like to organise the channels so that I have film4+1 next to film4 etc.

---

### Post by SiHa on 2010-02-25
Good, glad it worked.

I think you can just edit the channel numbers, and reorder them as you see fit. Thinking about it, that's exactly what you have to do to get the DVB-S & DVB-T channels to match up, as decsribed above.

Probably best to try it with something unimportant first though, just in case!

---

### Post by My Name on 2010-02-25
Simon, you are the UK mythbuntu GOD :D
I'll give it a bash with northern birds :o

---

### Post by SiHa on 2010-02-25
I wouldn't go quite that far, but I'm glad to have helped.
> I'll give it a bash with northern birds 
Fnar Fnar...

---

### Post by ds1direct on 2010-12-06
I know this post was a long time ago but i think this is the closet ive found to what I want to achieve. 

I can get my TV card to work and create a .conf files to play back the channels found. using this command. $ scan /usr/share/doc/dvb-utils/scan/dvb-t/uk-WinterHill >channels.conf

This issue I have is I want to scan for my local sky box.

My sky box sends out a signal from the RF2 output. this i can plug in to a TV and scan for channels it picks up the transmitted frequencies. but am trying to achieve this using my tv card. 

As the above command needs to use the uk-WinterHill I can't find away to scan for all VHF/UHF Channel frequencies which the Sky box sends out.

---

