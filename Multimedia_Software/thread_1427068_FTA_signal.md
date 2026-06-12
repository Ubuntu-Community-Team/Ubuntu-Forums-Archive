---
title: "FTA signal"
date: 2010-03-11
forum: Multimedia Software
---

### Post by RasterBurn on 2010-03-11
does anyone have any experience with Free-To-Air? i cant really afford to run down to my local FTA dealer (who for the record refuses to talk about it:???:) and purchase an STB so what i am wondering does anyone watch any of the FTA channels using their DVB tv tuners on their computers? my dad will be bringing up a sat dish, lnb, and cable for me to hook things up with and see if i can get this working, so if anyone has done this vary task, could you point me in the right direction to make it work. (if i need to i will boot into my other HDD to run mythbuntu), if it is any constilation to the setup, i am using a Hauppauge 1250 tv tuner :)

---

### Post by RasterBurn on 2010-03-11
Bump

---

### Post by mocha on 2010-03-12
What do you want to know?  Why not just get a Twinhan card and use that as your tuner instead of an STB?  Or if you intend to input the STB signal into the Hauppauge card that will work as well.  I've done both personally.

---

### Post by RasterBurn on 2010-03-12
well, i am not sure i am understanding you answer or if you understood the question fully, but i think you have, anyways, i cant afford to buy an STB to use FTA, linux as stripped the analog signal support for tv tuners (all i can pick up where i am is a couple analog tv signals) my dad will be bringing up a mini dish and LNB so i can test things

correct me if i am wrong on what you are saying, but with my tv tuner i can plug the dish directly into it, point the dish at the FTA satelites and i will be able to watch a few channels with very little tuning? (asside from the normal adjusting the dish for best strength and scanning the channels for working signal)? or are you saying that with my tv card i will require an STB to decode the FTA signal?

---

### Post by mocha on 2010-03-12
In my systems I use both analog NTSC capture cards as well as DVB-S cards.  The DVB-S cards connect directly to the LNB on the satellite dish and your computer does the tuning, viewing, and capturing.  The analog capture card can only take a composite (or RF) signal in from an STB for viewing and capturing.  You need some external method to tune the STB either by hand or using a serial port IR blaster and a script on your computer to interface with something like MythTV which can use the script to send an IR signal out of the blaster when you change channels in Myth or setup a recording.

There is a lot of FTA stuff up there which can be viewed via a DVB-S card.  There is a scanning program in the repo.  You need it to create a channels.conf file for programs such as mplayer, totem, or xine.  The viewer programs use the channels.conf file to perform the tuning based on what you scanned.  There is alot of DVB programs for linux from very simple interface (MeTV, mplayer/smplayer) to very complex (MythTV, VDR), just do some searching.

Personally I use MythTV for my regular recording from DVB or analog, I just like it because it's a full fledged DVR program and allows me to make schedules and does the playback and so forth.  However, it's entirely possible to just use mplayer for everything via clever scripting to perform tuning and setup recording schedules.  With Linux the possiblities are endless but there is a large learing curve for this stuff.  LinuxTV.org has a good mailing list and wiki page, as well as MythTV and VDR mailing lists, and even the mplayer mailing list is a good place to search.

---

### Post by RasterBurn on 2010-03-12
the card i have is the [Hauppauge winTV HVR 125]("http://www.hauppauge.com/site/products/data_hvr1250.html") the page doesnt say anything about it supporting any DVB formats so i am not sure if it can be done with this card and no STB, but would i not be able to a software decoder for the signal?

---

### Post by mocha on 2010-03-13
> **RasterBurn said:**
> the card i have is the [Hauppauge winTV HVR 125]("http://www.hauppauge.com/site/products/data_hvr1250.html") the page doesnt say anything about it supporting any DVB formats so i am not sure if it can be done with this card and no STB, but would i not be able to a software decoder for the signal?

That's not a DVB card.  That card is for use with OTA and cable-based analog and digital signals.  But it does have a composite input, so you could connect the output of a DVB STB to it and make recordings, but like I said you'll need something like an IR blaster to change channels on the STB.  I don't understand what you mean by "software decoder", you can't connect a satellite dish directly to this card, so no, you aren't going to decode any satellite with this card.

---

### Post by RasterBurn on 2010-03-13
well i guess im up **** creek without a paddle on that one :( got the card as a gift the christmas before last and the only use i have really gotten out of it was recording "Trick r Treat"  off the sasktel box last year, was kinda hoping i could get a dish from my dad and put it to some good use without having to spend any money, maybe this guy i emailed earlier today still has 1 of his FTA receivers still for sale (cant really go wrong for $10)

---

