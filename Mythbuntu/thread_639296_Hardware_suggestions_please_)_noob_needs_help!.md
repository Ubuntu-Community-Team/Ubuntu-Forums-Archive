---
title: "Hardware suggestions please :) noob needs help!"
date: 2007-12-13
forum: Mythbuntu
---

### Post by Qslugs on 2007-12-13
Hello all! Im new here. I have a few question I'm hoping someone can help me with.

I'm looking for hardware suggestions for my Mythbuntu box.

Heres what Hardware I have

Dell precision 530 - Dual 1.7 Xeon each chip has 256k cache
1.2 gigs of ram
Pioneer a104 dvd -r drive
onboard sound, firewire 400, usb
Nvidia 5700 128mb
20 gig and 120 gig drives ATA100 I think

What I am hoping to do is to to store my animation DVD's on the computer and play them back via Mythbuntu. I teach animation, I would like to be able to store stuff for easier access. My current TV is a 27 inch panasonic CRT.

So what I dont know is this, what else do I need?
Do I need a sound board or is onboard sound good enough?
The Nvidia 5700 has video out. Is this all I need for video out? 
What other hardware will I need to rip and encode dvd's to mpeg 2? 
Do I need something like the PVR 350 for hardware mpeg 2 encoding for my dvd's?

Thanks for any assistance in advance. Any help I can get will help me to spread the word how great myth tv is :)

---

### Post by volkswagner on 2007-12-13
I don't think you will need any additional hardware.  In my opinion mythbuntu may not be what you need.  I think it is better suited for pvr which you do not need.  You should only need codecs for ripping the dvds and storing on your hard drive.  I would search for ripping dvds in linux or ubuntu.

Run th live dvd and see how well it plays with your hardware.  You will be able to listen to sound output and see or hear if you like the onboard sound.  Other things to consider will this be a dual boot?  What is the current OS you are running?

Just my $.02

Cheers

---

### Post by DrMega on 2007-12-13
Make sure you have the necessary codecs. From Synaptic package manager choose to install the following packages:

ubuntu-restricted-extras - this contains most of your codecs.
ffmpeg - this seems to be needed if you use the xine version of Totem (which is better than the GStreamer version which is installed by default in my opinion).

I can't comment specifically about your TV-out on your setup, but I have a similar setup but with an ATI card. I had a hard time getting TV out to stay configured. (it would work with a monitor attached but as soon as I unplug the monitor and reboot, it was all gone). This may have been a conflict with Ubuntu and the ATI driver so nVidea may be OK, but if you do get grief, let me know and I'll describe how I fixed it in my case.

---

### Post by theacoustician on 2007-12-13
DVD::RIP + Avidemux + VLC will do everything you need.  In fact, you could probably get away with just using VLC to rip DVDs to file for something quick and dirty.  You can do that with just about any hardware.  Onboard sound is fine considering you're just using a CRT.  Most video cards, and indeed most motherboards with onboard graphics, can output composite or s-video, so you should be fine there.

The only thing you gain from building a Myth box is an easy way to enable the ability to walk away from computer while you're talking and still launch videos via IR remote.

---

### Post by NightCrawler03X on 2007-12-13
You want to rip DVD movies in linux?
```

sudo apt-get install dvdrip

```

---

### Post by Qslugs on 2007-12-13
Hey all, thanks for the responses. I was able to get Mythbuntu up and running without issue in very little time. I think a few of you are correct, it's probably a bit more than I need. However with that said, I love the interface, and  I do want to get a remote. I want to watch my dvd's from a media center type thing on my tv and listen to them through my expensive home theater system.

As for other os's. Myth TV is for computer 5 of 5 :) I have 5 computers at the house, my wife was threatening to send 2 of them off for recycling, I balked and said I had an idea for them.  There will be no other OS on the myth tv machine other than Ubuntu.

Im actually quite impressed with how quickly everything installed. I got wireless interent up and running in like 5 min, everything else more or less worked without issue. I will be spreading the word until people tell me to shut up already!

So it ends up I was testing mythbuntu on another computer altogether. I think I may keep that one as the myth box actually. The computer I was testing on was a Dell Precision 330, its a smaller form factor, has less expansion slots than a normal box, but I think its exactly what I am looking for. Plus now I can keep the big behemoth dual xeon refrigerator sized thing for more sinister purposes  :)

I think all I will need for this alternative configuration is a bigger hard drive, or another external one, and a new video board with analog video out. The current board is some ati dual head thing that came with the machine. its only got 32mb and its more or less worthless for going out to tv.

One last question

Should I get a sound card for this thing? The current sound out is the 1/8th inch jack on the back of the computer. I was thinking that optical out of some creative labs board would work? Or should I scrap that idea and try a Hauppage Pvr-350? I guess the pvr350 is cheaper than replacing the video or audio board. Am I correct in this assumption? If that will do audio and video out I'm thinking its an ideal solution.

---

### Post by DrMega on 2007-12-14
Isn't the Haupage 350PVR just a TV tuner? If so it won't help you with your Video or Sound out.

It sounds like you are going for a media centre setup similar to mine. I have a Pinnacle TV tuner which just doesn't work in Linux (it is listed as supported, but no luck in my case). Let us know how you get along with the Haupage one. I understand they are much better supported than Pinnacle cards so you might not have the same trouble that I encountered.

---

### Post by volkswagner on 2007-12-14
The pvr350 is an excellent card.  You do pay for what you get.  IMHO you can get the best of both worlds with a pvr150 bundled with a remote and an inexpensive video card with svideo out for the tv (for roughly the same cost as the pvr350).  I am not 100% sure but the video out on the 350 may be limited, I am not sure if you can send the desktop to it.

Your sound output is to taste.

---

### Post by Qslugs on 2007-12-18
Hey thanks again for the replys. 

So I am back to the dual 1.7 machine. The Dell Precision 340 (not 330 like I previously mentioned) seems too limited. I figured out what video quality I am looking for, I think I will need to go with more drive space than I can fit in the smaller box. The big box has a ton more space in it anyway, along with many more extra open slots.

So heres my new question, what  brands sound board will supports 6.1 or 7.1 digital out, and will work flawlessly with mythbuntu? M-Audio? Creative Labs? 

 I saw some huge compatibility matrix on one of the other support sites, but I couldn't dechiper which one would cause the least problems.

 Anyone having any luck going digital optical out of a sound card into a home theater receiver?

Again I don't care much about price, I'm more concerned with guaranteed compatibility. I would prefer cheaper over more expensive though.

I have a home theater that supports up to dts 6.1 btw. I don't know if theres any known limitations with that sort of standard and Ubuntu/Mythbuntu. Although with that said, I know there are only a few DVD discs in existence that utilize 6.1 dts. So if theres a solution that will do 5.1 optical out flawlessly for 10 bucks, I might be swayed going with that over 100 bux for 6.1 or 7.1 capiable card. Although I do want something that is not on its way out tech wise. I'd like to keep it around for a few years.

Again, thanks all in advance. Mythbuntu is really fun to play around with. Once I get my box fully running, its going into work to show the guys :)

---

