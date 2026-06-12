---
title: "Newbie: Tune OTA and ClearQAM at the same time."
date: 2009-03-07
forum: Mythbuntu
---

### Post by Mikieboyblue on 2009-03-07
Hi folks,

I am completely new to Mythbuntu and I am venturing down this route because my father would like a PVR and I think Myth is the best solution. I am in the process of picking a case and required hardware.

One of the things I have been struggling with is what kind of tuner card to get. I was hoping to give him a setup that would allow him to use the following combinations:

[LIST]
[*]Tune 2 OTA stations at a time
[*]Tune 2 Clear QAM stations at a time
[*]Tuen 1 OTA and 1 Clear QAM
[/LIST]

Can this be done with one tuner card?

It seems like the Hauppauge WinTV-HVR-1800 could do this but then I read it doesn't work with Mythbuntu.

The Hauppauge WinTV-HVR-2250 looks really nice but it has one coax input and that clearly wont work.

He would also like to output at 1080p. From my understanding that is video card dependent and not so much the tuner card. Is that correct?

If he needed two tuner cards to achieve the above, would that work seamlessly with Mythbuntu and be transparent to him (the user)?

Lastly, if anyone has a suggestion on HTPC cases, let me know too. I think I want one with a built in Ir receiver but I am not sure. He wants to do web browsing as well and I think a keyboard with integrated mouse might be good as well. Are there any remotes out there that can do that? Also, can a built in Ir receive work with any remote? That is, can it be programmed?

Thank you so much!
Mike

Thanks folks!

---

### Post by VeeDubb on 2009-03-08
Talk about jumping off the deep end with your first post.  ;)

I'm in the process of pricing out my own HTPC, so I've been doing a lot of checking on the stuff you're talking about.  I'll answer what I can, and leave the rest for others.

1. Many, but not all cards with 2 inputs can get two channels at the same time.  However, there are few if any tuner cards that can tune different TV signal formats at the same time.  So, if you're getting OTA on one, you have to get OTA on both.  In fact, if you're getting NTSC over the air on one, you can't even get ATSC over the air on the other.  Both would be NTSC or both would be ATSC.  (Not sure if you're from a country with ATSC or not.  I forgot to look)

2. As for what card to get, God bless you and good luck.  There are so many options with so many different chip sets, and so little information on their performance with Linux, that even getting one that is reported to work is a crap-shoot.

3. HDMI output is 100% a matter of your video card.  However, you don't need a video card with an HDMI output.  A DVI connector (the one that replaced d-sub VGA connectors when everybody when to LCD) is 100% compliant with HDMI.  You can literally buy a cable with HDMI on one end, and DVI on the other.  DVI to the video card, HDMI to the TV.

The downside of doing that however, is that you won't get audio, so you'd have to run a second cable from your sound-card to your TV, which 'can' create sync issues between the sound and video depending on your system, and on your TV.

The downside of getting a video card with a dedicated HDMI port, is that you 'may' find that it's not so easy to get the sound into your video card to begin with.  

In any case, best of luck, and I hope other can give better details.

---

### Post by Mikieboyblue on 2009-03-08
I'm in the US and yes, right off the deep end!

Sounds like you echo some of the very frustrations I have had trying to figure this out. I also, much like you, I don't have a money to blow on the "wrong" component!

I find it interesting that there could be video/audio sync issues if outputting video from the video card and sound from the sound card? The audio will probably be routed to a receiver and the video directly to the TV. It looks like most video card candidates will use a DVI - HDMI connector. That said, the TV does support DVI but I think it will take a higher resolution when using HDMI.

I have seen a few very nice sound cards with HDMI 1.3a outpout and an HDMI input so you could run a wire from the video card to the sound card and then the sound card to the receiver/tv. I plan to SPDIF for the sound (optical) - I pray this works.

I am also thinking I might be a bit confused as I thought MythTV had been around long enough that it should work quite well. It is starting to seem like Vista media center might be best (oh no!).

---

### Post by agamotto on 2009-03-09
The Hauppauge 1800 will work fine for digital, but the analog input is not fully supported.  It may/may not work for you with the current driver.  For your analog viewing, add any of the cards in the Myth wiki that show up in the analog/SDTV section.  I myself am having a curious issue with sound on my setup, but someone has sent me a possible fix that I will be trying soon.

---

### Post by Dartr on 2009-03-09
I can only speak from my very limited experience, but so far it has been a good one.

The Silicondust HD Homerun will support tuning OTA ATSC and NTSC clear QAM tuning simultaneously on the separate tuners.  However, my experiment was limited to just ATSC on one tuner and NTSC on the other.  I did not attempt to set up a 2nd set of inputs for both so that I could tune 2 ATSC at the same time and 2 NTSC at the same time.

Since you can toggle inputs while watching, and can toggle inputs for recording, I don't see why this wouldn't work.

I could be wrong, but since the tuning is performed on the input and not on the tuner directly, I don't know why there would be a limitation for any card.  Maybe the HD Homerun is unique in this regard.

---

### Post by Mikieboyblue on 2009-03-09
> **agamotto said:**
> The Hauppauge 1800 will work fine for digital, but the analog input is not fully supported.  It may/may not work for you with the current driver.  For your analog viewing, add any of the cards in the Myth wiki that show up in the analog/SDTV section.  I myself am having a curious issue with sound on my setup, but someone has sent me a possible fix that I will be trying soon.

Ok, so, if I understand how the 1800 works, it has an ATSC/NTSC OTA (Ant In) input and a Clear QAM (TV In) input. This means that Ant It will tune **one** DTV OTA channel at a time and the TV In will tune **one** Clear QAM channel at a time, correct?

The reception of analog SDTV stations do not matter in our case as in all situations, the OTA DTV stations have much better reception than the SDTV stations.

In the Clear QAM scenario, will it pick up HD and SD CQ channels?

Thank you!

---

### Post by Mikieboyblue on 2009-03-09
> **Dartr said:**
> I can only speak from my very limited experience, but so far it has been a good one.

The Silicondust HD Homerun will support tuning OTA ATSC and NTSC clear QAM tuning simultaneously on the separate tuners.  However, my experiment was limited to just ATSC on one tuner and NTSC on the other.  I did not attempt to set up a 2nd set of inputs for both so that I could tune 2 ATSC at the same time and 2 NTSC at the same time.

Since you can toggle inputs while watching, and can toggle inputs for recording, I don't see why this wouldn't work.

I could be wrong, but since the tuning is performed on the input and not on the tuner directly, I don't know why there would be a limitation for any card.  Maybe the HD Homerun is unique in this regard.

What do you mean by "inputs"? That is, what is an input? Are you implying you could turn four channels at once?

How well does the HD Homerun work as it streams over the network? Do you ever have issues with your router/switch or network latency?

Sorry for being so far behind on this subject!

---

### Post by Boppy3125 on 2009-03-10
> **Mikieboyblue said:**
> 
I was hoping to give him a setup that would allow him to use the following combinations:

[LIST]
[*]Tune 2 OTA stations at a time
[*]Tune 2 Clear QAM stations at a time
[*]Tuen 1 OTA and 1 Clear QAM
[/LIST]

Can this be done with one tuner card?


Short, no.
One card might have two tuners on it.  I would suggest going the HD Homerun route by the way.  Each tuner can be connected to an antenna or your cable system.  Either/or not both.  Of your list, you can have any one of those three options, but you need to configure one of those three options.  Device 1 will be connected to either cable or antenna, then in Myth Backend setup you will tell it which it is and scan the channels appropriately.  Device 2 will be connected to either cable or antenna, then in MythBackend setup you will tell it which it is and scan the channels appropriately.  

If you want to change Device 1 from Cable QAM to OTA using antenna, you need to unplug your Cable company cable and plug in the antenna, then change the tuning in MythBackend.  Oh yeah, then you will need to change its source to give the proper listing, unless you are mapping channels the same.

Now, the right card will give you the option, it just won't be able to switch its signal in software.  And if it can, I think you will have problems getting MythBackend to have all the available channels for both sources.

---

### Post by newlinux on 2009-03-10
> I am completely new to Mythbuntu and I am venturing down this route because my father would like a PVR and I think Myth is the best solution. I am in the process of picking a case and required hardware.

One of the things I have been struggling with is what kind of tuner card to get. I was hoping to give him a setup that would allow him to use the following combinations:

    * Tune 2 OTA stations at a time
    * Tune 2 Clear QAM stations at a time
    * Tuen 1 OTA and 1 Clear QAM

Can this be done with one tuner card?



What you would need to be able to do is diplex cable and OTA signals like many do with Satellite and OTA or Satellite and cable, but the problem is that OTA ATSC and QAM use the same frequencies, so you can't diplex them.

That said, I actually can think of one way you can do this with two tuner cards. The Kworld ATSC 110/115 actually has two inputs and can do ATSC and QAM (as well as NTSC).  It can of course, only do one of these at the same time (it is a single tuner). I've had these cards for almost 3 years now and over that time (with driver changes) the assignment of QAM/ATSC OTA and NTSC to each of the inputs has changed multiple times with the driver version (some versions have QAM on one input and ATSC OTA on the other, some have them both on the same input - you'd want the former). If you get a version of the driver that assigns QAM to one input, and OTA ATSC to the other, you could do what you want with two of these cards. You'd need to set up input groups in myth so that it never tries to use QAM and ATSC on the same card at the same time (I've done this exact thing, except using ATSC OTA and cable NTSC  on these cards -- on separate inputs - without having to plug and unplug or reconfigure anything)

I've read in later versions of the driver provide an option for allowing you to specify how the inputs are assigned (tuner-simple module, I believe). Haven't used it personally...

With one Kworld ATSC 110/115 you could do #1 and #2  for channels on the same multiplex using the multi-record feature.  So if you had the HDHomerun you could do #1 and #2 for channels on the same multiplex, and of course #3 anytime if you connected one input to ATSC OTA and the other to QAM. If you have a decent network you shouldn't have network problems with the HDHomerun. It has very good reviews. I stream multiple HD signals on my 100Mbps network all the time without problems, so I have no doubts the HDHomerun works just fine.

---

### Post by Dartr on 2009-03-11
Sorry about the poor explanation.  The HD Homerun can do everything on your list, but only one of those choices at a time.  If you wanted 2 choices at a time, you could add a 2nd (and 3rd, etc) HD Homerun.

No issues with bandwidth on a hardwired 100Mbps lan.  The HD Homerun only works inside of one subnet.  It will not work across a gateway.  If you have a typical home setup with the HDHR and the FE/BE sitting behind the same router, you're good to go.

---

### Post by Mikieboyblue on 2009-03-12
> **newlinux said:**
> What you would need to be able to do is diplex cable and OTA signals like many do with Satellite and OTA or Satellite and cable, but the problem is that OTA ATSC and QAM use the same frequencies, so you can't diplex them.

That said, I actually can think of one way you can do this with two tuner cards. The Kworld ATSC 110/115 actually has two inputs and can do ATSC and QAM (as well as NTSC).  It can of course, only do one of these at the same time (it is a single tuner). I've had these cards for almost 3 years now and over that time (with driver changes) the assignment of QAM/ATSC OTA and NTSC to each of the inputs has changed multiple times with the driver version (some versions have QAM on one input and ATSC OTA on the other, some have them both on the same input - you'd want the former). If you get a version of the driver that assigns QAM to one input, and OTA ATSC to the other, you could do what you want with two of these cards. You'd need to set up input groups in myth so that it never tries to use QAM and ATSC on the same card at the same time (I've done this exact thing, except using ATSC OTA and cable NTSC  on these cards -- on separate inputs - without having to plug and unplug or reconfigure anything)

I've read in later versions of the driver provide an option for allowing you to specify how the inputs are assigned (tuner-simple module, I believe). Haven't used it personally...

With one Kworld ATSC 110/115 you could do #1 and #2  for channels on the same multiplex using the multi-record feature.  So if you had the HDHomerun you could do #1 and #2 for channels on the same multiplex, and of course #3 anytime if you connected one input to ATSC OTA and the other to QAM. If you have a decent network you shouldn't have network problems with the HDHomerun. It has very good reviews. I stream multiple HD signals on my 100Mbps network all the time without problems, so I have no doubts the HDHomerun works just fine.

Thanks for the information. I am going to have to read this a few more times to make sure I understand it. By the way, those Kworld cards are hard to find.

Does anyone know why the HDHomerun is so much more expensive than the cards? In some cases double?

---

### Post by Dartr on 2009-03-19
> **Mikieboyblue said:**
> Does anyone know why the HDHomerun is so much more expensive than the cards? In some cases double?

Not sure the real answer, but a few considerations:

1. it's enclosed in its own case (compare internal and external HDD prices)
2. it has a built-in network card
3. it has a built-in web server (albeit very basic)
4. the tuners operate truly independent of each other
5. it comes with a power cord, and 3 very quality cables
6. built-in IR receiver

---

### Post by jaakan on 2009-03-19
> **Mikieboyblue said:**
> Thanks for the information. I am going to have to read this a few more times to make sure I understand it. By the way, those Kworld cards are hard to find.

Does anyone know why the HDHomerun is so much more expensive than the cards? In some cases double?

HDHomerun is about $150 USD If you had 3 free PCI-E 1X slots you could have 3 x Hauppauge WinTV HVR-1250 for that price.

the Hauppauge WinTV-HVR-2250 uses an internal splitter connect to two tuners both support ATSC and QAM for less than the HDHomerun but I can't say anything about the driver support ( IE: do both tuners work ) / real world use since I don't own this card, I just have the HVR-1250.

...then again the HDHomerun is a cool idea I'm thinking about getting one just for the hell of it.

---

