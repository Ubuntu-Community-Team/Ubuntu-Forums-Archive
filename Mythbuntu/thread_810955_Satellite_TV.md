---
title: "Satellite TV"
date: 2008-05-28
forum: Mythbuntu
---

### Post by Mike.42 on 2008-05-28
If I want to use Mythbuntu and I have a satellite box what do I need to get? I am a little confused b/c devices like the Hauppauge WinTV-PVR-500 seem like for cable, so what do I need to capture the output video from the satellite box? Is this even possible? I love the idea of Mythbuntu as a PVR but I am worried that I will not get full functionality from Mythbuntu  because of my satellite TV.

---

### Post by tgm4883 on 2008-05-28
For satellite high definition you will need something like the HD PVR from Hauppauge.  For standard definition you will need something like the PVR-500.  If you are high def directv boxes a PVR-500 will work.  That is how mine is setup, High Def boxes to a PVR-500.  I've upped the bitrate on the PVR-500 and told it to record in 720x480.  I change the channel via usb/serial cable.  I'm very happy with this setup and I get full mythtv benefits.

Couple things to note.  You will need 1 satellite box for every show you want to record at the same time.  You will also need a way to change the channel on the box.  You can do this via ir blasting or by (at least with directv) a usb/serial cable.  

!Do not get a digital tuner.  It will not work for what you want to do!

---

### Post by Mike.42 on 2008-05-28
I have some Linux experience (put fedora on one laptop and ubuntu on the other). How hard is it to "change the channel via usb/serial cable"?

---

### Post by tgm4883 on 2008-05-28
Not difficult at all, providing you can either make the cables or buy them.  You will also need a channel change script.  These are usually premade and you can easily find the directv one by googling directv.pl

---

### Post by Mike.42 on 2008-05-28
The PVR-500 has the ability to recode two or watch/record at the same time. But I only have one sat box. I also have cable. Am I able to use cable and sat on the same card?

---

### Post by Mike.42 on 2008-05-28
Do I need a sound card or is on bored audio good? I have a 5.1 surround sound system. I can only imagine the headache of configuring one of those. My friend complains about his causing problems in his windows system...

---

### Post by tgm4883 on 2008-05-29
You can use both cable and satellite.  You'll just need to setup 2 different channel lineups.  I'd just go with stereo audio.  There are a few cards in linux that will do 5.1 over optical or HDMI, but I myself don't know much about them so you will have to research them yourself.

---

### Post by DutchLoki on 2008-05-29
If you want to watch satelite with MythTV or MythBuntu you don't want to buy a PVR-150 or pvr-500 card. These cards are analogue and just as expensive as the digital ones. Satelite is digital (in europe it is... I asume it's also the case in the rest of the world).

There are 4 types of digital cards:

ATSC Cards (only in US/Canada) 
DVB-C cards (Cable viewing) 
DVB-S cards (Sattelite viewing) 
DVB-T cards (Terresterial viewing) 

So dvb-s is to watch Sattelite television. With such a card, you don't need a satelitebox. This card you can connect to the coax cable of your satelite.

If the channels are encrypted, you also need a CI and Cam module. (The smartcard goes into the CAM, the Cam goes into the CI and the CI goes into the computer).


You can find alot about these cards on the MythTV wiki: [http://www.mythtv.org/wiki/index.php/Video_capture_card](http://www.mythtv.org/wiki/index.php/Video_capture_card)  

I personally order my satelite stuff at [www.dvbshop.net](www.dvbshop.net). They deliver around the world.

---

### Post by foxbuntu on 2008-05-29
> **DutchLoki said:**
> If you want to watch satelite with MythTV or MythBuntu you don't want to buy a PVR-150 or pvr-500 card. These cards are analogue and just as expensive as the digital ones. Satelite is digital (in europe it is... I asume it's also the case in the rest of the world).

There are 4 types of digital cards:

ATSC Cards (only in US/Canada) 
DVB-C cards (Cable viewing) 
DVB-S cards (Sattelite viewing) 
DVB-T cards (Terresterial viewing) 

So dvb-s is to watch Sattelite television. With such a card, you don't need a satelitebox. This card you can connect to the coax cable of your satelite.

If the channels are encrypted, you also need a CI and Cam module. (The smartcard goes into the CAM, the Cam goes into the CI and the CI goes into the computer).


You can find alot about these cards on the MythTV wiki: [http://www.mythtv.org/wiki/index.php/Video_capture_card](http://www.mythtv.org/wiki/index.php/Video_capture_card)  

I personally order my satelite stuff at [www.dvbshop.net](www.dvbshop.net). They deliver around the world.

While parts of what you said are correct there are some fundamental faults that need clarified. 

1) ALL NTSC and ATSC Content Via Satellite in the US is encrypted and cannot be recorded with a DVB-S card, while in other parts of the world this might not be the case it is strictly regulated and prohibited by law in the USA.

2) DVB-C unless provided/supported by your local cable company in the USA will also not work. Trying to do so without support from your local cable co. is also highly prohibited by law.

3) DVB-T transmission does not exist in the USA but does work well in other parts of the world.

4) ATSC cards are able to access unencrypted ATSC content, this is usually Over-the-Air but could just be unencrypted content via your local cable company. No unencrypted ATSC content is provided in the USA via Satellite. A good option for this is a [HDHomeRun]("http://www.silicondust.com") from Silicon Dust.

This all brings me to your mention of the PVR-150s and PVR-500 tuners, since you cannot get ATSC content in the USA via any type of DVB card, using a PVR-150/PVR-500 for analog (NTSC) content is perfectly acceptable.

---

### Post by Mike.42 on 2008-05-30
So then do I just use the outputs from the satbox and hook the output into a PVR-150? (what DVB-S card would you recommend getting that works really well with MythBuntu)

---

### Post by DutchLoki on 2008-05-30
Well I would like to call it a mistake, its only a fault when you read it from the US. ;) 

Some minor additions for mike42:

> **foxbuntu said:**
> While parts of what you said are correct there are some fundamental faults that need clarified. 

1) ALL NTSC and ATSC Content Via Satellite in the US is encrypted and cannot be recorded with a DVB-S card, while in other parts of the world this might not be the case it is strictly regulated and prohibited by law in the USA.

Encrypted channels can be decrypted on a DVB-S card, but this seems to be prohibited in the US. So this is a no go... 

> **foxbuntu said:**
> 
4) ATSC cards are able to access unencrypted ATSC content, this is usually Over-the-Air but could just be unencrypted content via your local cable company. No unencrypted ATSC content is provided in the USA via Satellite. A good option for this is a [HDHomeRun]("http://www.silicondust.com") from Silicon Dust.

I'm so glad i'm not living in the us. This sounds so limited and old school.

> **foxbuntu said:**
> 
This all brings me to your mention of the PVR-150s and PVR-500 tuners, since you cannot get ATSC content in the USA via any type of DVB card, using a PVR-150/PVR-500 for analog (NTSC) content is perfectly acceptable.

I agree, if the use of a cablebox is required, than you need to convert a perfectly good digital signal to an analoge one before putting it into your computer to again make it digital. 

So you need to put something in your computer to connect it to. If such a cablebox does not has a digital out (like a hdmi connection) than a pvr 150, 350 or better a pvr500 (two 150's on one pci card) would be a good choice. 

also most computer these days have a video in or a analogue tuner on their system (often without mpeg decoder) you could use this one if you have it in your system.

---

### Post by tgm4883 on 2008-05-30
> **DutchLoki said:**
> 
If the channels are encrypted, you also need a CI and Cam module. (The smartcard goes into the CAM, the Cam goes into the CI and the CI goes into the computer).

If my understanding is correct (and I like to think that it is) this is prohibited almost everywhere.  Especially on this board.

---

### Post by DutchLoki on 2008-05-30
> **tgm4883 said:**
> If my understanding is correct (and I like to think that it is) this is prohibited almost everywhere.  Especially on this board.


Well I hope this does not makes you think to badly about yourself ;) 

CAM modules are legal in europe and most countries outside of europe. They are mostly sold by the TV providers themselfs. E.g. Canal digital ([http://www.canaldigitaal.nl](http://www.canaldigitaal.nl)), tv vlaanderen and many more. With google you can find al about them. They even sell their own cam and cards online, so you can use it and pay them for it. 

Also nice to know for future remarks: every self respecting DVB softwarepackage (including MythTV / MythBuntu) supports the use of CI, CAMS and smartcards. This makes it possible for people to watch paytv and delivers the money to the TV, cable and satelite providers.

I understand your reaction, but it seems mainly the case in the US.

---

### Post by tgm4883 on 2008-05-30
> **DutchLoki said:**
> Well I hope this does not makes you think to badly about yourself ;) 

CAM modules are legal in europe and most countries outside of europe. They are mostly sold by the TV providers themselfs. E.g. Canal digital ([http://www.canaldigitaal.nl](http://www.canaldigitaal.nl)), tv vlaanderen and many more. With google you can find al about them. They even sell their own cam and cards online, so you can use it and pay them for it. 

Also nice to know for future remarks: every self respecting DVB softwarepackage (including MythTV / MythBuntu) supports the use of CI, CAMS and smartcards. This makes it possible for people to watch paytv and delivers the money to the TV, cable and satelite providers.

I understand your reaction, but it seems mainly the case in the US.

I stand corrected.  I was thinking this thread was headed in a sascng direction, which is bad.

---

### Post by Mike.42 on 2008-05-30
So, for clarification, can I use the out put of may satbox with a PVR-150?

---

### Post by tgm4883 on 2008-05-30
> **Mike.42 said:**
> So, for clarification, can I use the out put of may satbox with a PVR-150?

Yes you can

---

### Post by DutchLoki on 2008-05-31
> **tgm4883 said:**
> I stand corrected.  I was thinking this thread was headed in a sascng direction, which is bad.

I understand, no problem.

---

### Post by rickyble on 2008-05-31
Dont know if this will help but you can purchase the older 10-250 dvr directv box and hack it quite simply using an image from an online source.  Very credible.  The hack lets the dvr capture the ota and other feeds unencrypted in an mpg2 format.  You can then very easily copy it to your mythbox.  It will do both DT and HDTV.   I have been looking for a capture card to go directly from this boxes output to myth but its not out there.  I use a PC in between to move the videos from the dvr to the myth using somba.  The results are unbelievable.  Someone else made the statement that there is not much difference between the raw analog and digital but believe me there is nothing better.  If you use that for a source to burn a DVD you wont believe the clarity and output from the original source.  It is an extra step but it is worth it if you are looking for the best quality and you can use the dvr itself to do the scheduling.  You can pick up a 10-250 pretty cheap on ebay.  YOu can then play then back on your front end to whatever tv you want in either HD or DT.  I use the nvida with dvi output for the digital signals to the TV.

---

### Post by tgm4883 on 2008-05-31
> **rickyble said:**
> Dont know if this will help but you can purchase the older 10-250 dvr directv box and hack it quite simply using an image from an online source.  Very credible.  The hack lets the dvr capture the ota and other feeds unencrypted in an mpg2 format.  You can then very easily copy it to your mythbox.  It will do both DT and HDTV.   I have been looking for a capture card to go directly from this boxes output to myth but its not out there.  I use a PC in between to move the videos from the dvr to the myth using somba.  The results are unbelievable.  Someone else made the statement that there is not much difference between the raw analog and digital but believe me there is nothing better.  If you use that for a source to burn a DVD you wont believe the clarity and output from the original source.  It is an extra step but it is worth it if you are looking for the best quality and you can use the dvr itself to do the scheduling.  You can pick up a 10-250 pretty cheap on ebay.  YOu can then play then back on your front end to whatever tv you want in either HD or DT.  I use the nvida with dvi output for the digital signals to the TV.

While this does sound nice, it makes me wonder about a few things.

1.  How automated is it?   Sounds like you lose a lot of MythTV functionality since you have to manually copy the shows over, they probably record just fine on the DirecTV box, but the box is doing that so they don't get any show data in MythTV.  Correct me if I'm wrong.

2.  Are you just talking about the shows being in HD?  If so, you can use the HD PVR when it gets support in MythTV (might already have it) and the show will be in stellar quality.  I've had HD quality material and it is really good, but at the moment it isn't in the cards for me.  I'd need an HD PVR for each tuner I have and I don't feel like shelling out $400 more dollars just for HD.  Perhaps when the price comes down.

---

### Post by Mike.42 on 2008-05-31
Ok, so I decided to get another satbox to recode and watch at the same time. What card do I need to get to do this?

---

### Post by tgm4883 on 2008-05-31
> **Mike.42 said:**
> Ok, so I decided to get another satbox to recode and watch at the same time. What card do I need to get to do this?

PVR-500 is two PVR-150's in one card.  Would work nicely for this.

---

### Post by Mike.42 on 2008-05-31
Ok, here is my plan. I am going to get a PVR-500 and two satboxes. Then use the coax from one into the PVR-500 and the RCA from the other also into the PVR-500. Will this setup work? Also I am ordering from tigerdirect and they have it come with a MCE remote. Does this remote work with Mythbuntu?

---

### Post by tgm4883 on 2008-06-01
Yes the remote works with ubuntu.  And yes that setup should work.  I use both composite inputs on my PVR-500, but the composite and coax should work fine.

---

### Post by Mike.42 on 2008-06-01
Ok, here is the hardware I am ordering, let me know if this will all work.  	   	 

Abit IP35V Motherboard
D-Link WDA-1320
Hauppauge WinTV-PVR-500
Patriot Dual Channel 2048MB PC6400 DDR2 800MHz Memory (4 x 1024MB)
XFX GeForce 8500 GT Video Card - 512MB
Thermaltake VB8000BNS Bach HTPC Home Entertainment PC Case
Ultra X-Connect V-Series ULT33134 ( XVS)400-Watt Power Supply

Solidtek - KB-5010BP - PS/2 Mini Wired Keyboard With Built In Trackball      

-Thanks,
Mike

---

### Post by rickyble on 2008-06-01
> **tgm4883 said:**
> While this does sound nice, it makes me wonder about a few things.

1.  How automated is it?   Sounds like you lose a lot of MythTV functionality since you have to manually copy the shows over, they probably record just fine on the DirecTV box, but the box is doing that so they don't get any show data in MythTV.  Correct me if I'm wrong.



2.  Are you just talking about the shows being in HD?  If so, you can use the HD PVR when it gets support in MythTV (might already have it) and the show will be in stellar quality.  I've had HD quality material and it is really good, but at the moment it isn't in the cards for me.  I'd need an HD PVR for each tuner I have and I don't feel like shelling out $400 more dollars just for HD.  Perhaps when the price comes down.

1-Well the scheduling is automated thru DTV.  You are correct in that the shows are copied to myth.  I use myth to then distribute them to any box I want and to do all the other things you can do with myth that dtv doesnt offer...cds music dvds streaming internet  etc.  Plus I can burn these to dvds if I like and free space.  At that point they all really become appliances to be used anyway you like not bound by some media company.  The moving of the shows from dtv to myth can be as automated as you like with scripting.

2-I am actually talking about both HD and dt and analog. I believe the HDPVR is only for ota not a sat box but I could be wrong.  You are right about one for each tuner and with my set up I dont have that problem.   Each sat box has two tuners already so they can record two at once and once the shows are moved to the myth back end then they can be watch anywhere there is a front end.  If you have two sat boxes then you can record four shows at once.  With the sat box at the tv u of course get the live pause etc and still are recording two other shows or four other if you have two boxes.  It really is the best combo. If I had some HD component capture card in the myth box it would be the ultimate set up.  And you are right about the $400.  Thats why I ended up with what I have. The price for everything was waaaaaaaaaaay under that and that includes the back end front end and used dtv boxes.

---

### Post by tgm4883 on 2008-06-01
> **rickyble said:**
> 1-Well the scheduling is automated thru DTV.  You are correct in that the shows are copied to myth.  I use myth to then distribute them to any box I want and to do all the other things you can do with myth that dtv doesnt offer...cds music dvds streaming internet  etc.  Plus I can burn these to dvds if I like and free space.  At that point they all really become appliances to be used anyway you like not bound by some media company.  The moving of the shows from dtv to myth can be as automated as you like with scripting.

2-I am actually talking about both HD and dt and analog. I believe the HDPVR is only for ota not a sat box but I could be wrong.  You are right about one for each tuner and with my set up I dont have that problem.   Each sat box has two tuners already so they can record two at once and once the shows are moved to the myth back end then they can be watch anywhere there is a front end.  If you have two sat boxes then you can record four shows at once.  With the sat box at the tv u of course get the live pause etc and still are recording two other shows or four other if you have two boxes.  It really is the best combo. If I had some HD component capture card in the myth box it would be the ultimate set up.  And you are right about the $400.  Thats why I ended up with what I have. The price for everything was waaaaaaaaaaay under that and that includes the back end front end and used dtv boxes.

The HD PVR will take any Component input and encode it to mpeg4 on the fly.  I still disagree with you on the copying over from the sat box.  When you transfer the shows over, do they show up in recordings?  Do they have any data associated with them?  Do they have commercial skipping?

---

### Post by rickyble on 2008-06-02
I just went out and looked at the hd pvr again and you are correct. It does take the component in.  Even though thats analog and then converted I am betting it would look pretty good.  I am confused as to how this hooks into mythbuntu?  How does the physical connections for the out from the HD pvr get hooked into the myth box? (*Never mind I just ready the Brent evans thing and it has a usb port.!* This being an external box how would myth be aware of the box?  

The copying over from dtv box is a pain.  There is however a command you can execute that will pick up the recorded shows from the subdirectory and then list them for replay.  Still not the ideal thing.  I guess my biggest thing is going from digital to analog to digital again.  No matter how good the equipment everytime you do a convert you lose and degrade the signal.  On that part I do agree with this:
[http://www.zatznotfunny.com/2008-04/hauppauge-hd-pvr-specs-revealed/](http://www.zatznotfunny.com/2008-04/hauppauge-hd-pvr-specs-revealed/)
In this article he mentions the loss in signal migrating from digital to analog to digital.  He is right I have done just that and played side by side the difference is quit noticeable.  However with nothing to compare it to the average person would not notice it I dont think.   Its kinda like the cable and sats local HD programming.  If you have an OTA and sat and switch back and forth between them watching the same show there is a marked difference in picture.
The main thing is that myth still is the best and way better than anything else.

---

### Post by tgm4883 on 2008-06-02
> **rickyble said:**
> I just went out and looked at the hd pvr again and you are correct. It does take the component in.  Even though thats analog and then converted I am betting it would look pretty good.  I am confused as to how this hooks into mythbuntu?  How does the physical connections for the out from the HD pvr get hooked into the myth box? (*Never mind I just ready the Brent evans thing and it has a usb port.!* **This being an external box how would myth be aware of the box?  **

The copying over from dtv box is a pain.  There is however a command you can execute that will pick up the recorded shows from the subdirectory and then list them for replay.  Still not the ideal thing.  I guess my biggest thing is going from digital to analog to digital again.  No matter how good the equipment everytime you do a convert you lose and degrade the signal.  On that part I do agree with this:
[http://www.zatznotfunny.com/2008-04/hauppauge-hd-pvr-specs-revealed/](http://www.zatznotfunny.com/2008-04/hauppauge-hd-pvr-specs-revealed/)
In this article he mentions the loss in signal migrating from digital to analog to digital.  He is right I have done just that and played side by side the difference is quit noticeable.  However with nothing to compare it to the average person would not notice it I dont think.   Its kinda like the cable and sats local HD programming.  If you have an OTA and sat and switch back and forth between them watching the same show there is a marked difference in picture.
The main thing is that myth still is the best and way better than anything else.

I don't understand your question.  It's a USB device.  MythTV can use USB devices.

---

### Post by rickyble on 2008-06-02
I saw that......as homer would say.......    doooooh!  Wish I had the bucks to buy one!  It looks sweet!

---

