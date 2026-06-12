---
title: "Alesis Multimix 8 Firewire"
date: 2007-10-09
forum: Multimedia Production
---

### Post by punkrockguy318 on 2007-10-09
I'm aware that there is no way to get the Alesis Multimix Firewire to work in Ubuntu.  Is there some other firewire 8 channel mixer that works with ubuntu that has a similar price?

I see they're putting out a multimix usb 2.0; does anyone know if this acts as an 8 channel input audio interface to the PC?

I'm really interested in a mixer that will send all of the tracks to the PC, not just the mix.  Is there anything that works with linux that is in the $300 pricerange?

---

### Post by Stochastic on 2007-10-09
it sounds like all you're looking for is 8 inputs to the PC, and in that case I'd steer away from Alesis as I've heard bad things about their overall sound quality.  I've got a PreSonus Firepod (I think the newer version is called FP10) and the sound quality is great! With the current freebob firewire drivers I get nearly all functionality, and with the upcoming ffado drivers EVERYTHING is supported.  I paid $450 Canadian for mine (should have gone shopping in the states with the exchange rate).

---

### Post by tgalati4 on 2007-10-09
M-Audio has pretty good linux support.  I'm not aware of an 8-channel, but I use a Delta 66 which is a 6 in/6 out pci/firewire sound card.  It uses the envy24control panel and it records 24-bit/96 kHz reliably on a PII/ 300 MHz machine using Dynebolic 2.4.2.

You can record 6 input streams (2 microphone, 4 line inputs) and mix down later or mix within the card and record 2-track.

---

### Post by punkrockguy318 on 2007-10-09
> **Stochastic said:**
> it sounds like all you're looking for is 8 inputs to the PC, and in that case I'd steer away from Alesis as I've heard bad things about their overall sound quality.  I've got a PreSonus Firepod (I think the newer version is called FP10) and the sound quality is great! With the current freebob firewire drivers I get nearly all functionality, and with the upcoming ffado drivers EVERYTHING is supported.  I paid $450 Canadian for mine (should have gone shopping in the states with the exchange rate).

The firepod looks good for 8 channel in, but $400 is a little bit steep for me.  I can do wihtout multi-track in.  The only reason I wanted the alesis mixer was because I could get a stellar deal on it.

What would be a good choice for a linux audio interface?  Is it better to buy a seperate mic preamp or to buy one built-in?  What's a good linux interface (usb/firewire perferably) that will include XLR and 1/4 inch inputs?

Does this ( [http://www.m-audio.com/products/en_us/MobilePreUSB-main.html](http://www.m-audio.com/products/en_us/MobilePreUSB-main.html) ) wok well in linux?

---

### Post by tgalati4 on 2007-10-09
Bus-powered products suffer from a few things:

USB is 5VDC power supply.  If you have high-quality, studio electret microphones, you will need phantom power.  I'm not sure if the mobile USB puts out phantom power.

USB is also limited to 500 mA.  That's half an amp.  Not much current to drive channels.  OK for casual use, but may be limiting for real studio-style recording.

This device is designed for portable field use.  For $200 you can get a used Delta 66 and that will give you a separate 12VDC power supply, 48VDC phantom power, and decent microphone preamps with 24-bit, 96 kHz recording.

Not sure what the USB box can do.

---

### Post by punkrockguy318 on 2007-10-09
The Delta 66 looks like it would work nicely, but I don't see any XLR inputs.  How would I input a mic into that?

The m-audio 1010LT is only $10 more.  Is there a significant advantage of getting the delta 66 rather than the 1010LT?  The 1010LT supports more channels, but is it missing any features from the delta 66?

---

### Post by Stochastic on 2007-10-09
The 10/10LT only has two balanced (properly grounded) inputs and it doesn't even look like it has any balanced outputs.  It's intended as a surround playback device at best, it isn't really designed for pro audio use.  The Delta 66 is okay, the 4 inputs on the breakout box are balanced but it doesn't have any mic preamps so you'd have to buy external preamps.  I should also note that the 10/10LT does have two preamps but I doubt that they'd sound terribly nice (ask the guy at the music store to hear them).

Really, when you start to look at the cost of multiple input/output channels plus the external preamps, the price tag of the Firepod really does become reasonable; particularly with the added sound quality. It has 8 Balanced Preamped Inputs!!!

An external preamp would give the best sound results in theory, but with an M-Audio card you probably wouldn't be able to notice any difference.

but that's just how my ears hear it

---

### Post by krissovo on 2007-10-09
I Have the multimix 8 USB, works well but its only a sterio channel.  There is a way to get an extra channel but you can google that.

The sound quality is ok in my opinion, could be better possibly but the price is good and it does me for my needs

---

### Post by punkrockguy318 on 2007-10-09
> **Stochastic said:**
> The 10/10LT only has two balanced (properly grounded) inputs and it doesn't even look like it has any balanced outputs.  It's intended as a surround playback device at best, it isn't really designed for pro audio use.  The Delta 66 is okay, the 4 inputs on the breakout box are balanced but it doesn't have any mic preamps so you'd have to buy external preamps.  I should also note that the 10/10LT does have two preamps but I doubt that they'd sound terribly nice (ask the guy at the music store to hear them).

Really, when you start to look at the cost of multiple input/output channels plus the external preamps, the price tag of the Firepod really does become reasonable; particularly with the added sound quality. It has 8 Balanced Preamped Inputs!!!

An external preamp would give the best sound results in theory, but with an M-Audio card you probably wouldn't be able to notice any difference.

but that's just how my ears hear it

I'm starting to see your point that the Firepod is the best way to go multitrack in.

Is there you a card you would reccomend that just had a stereo input?  After thinking about it, I doubt there will really be a time I would use the multi-input recording, as I don't even have a room in my house big enough to jam in right now.  What is a good linux-supported card that has an XLR and 1/4" inputs?

---

### Post by tgalati4 on 2007-10-09
The Delta 66 has an optional breakout box with two sweet microphone preamps.  It's normally bundled with it so if you find a used one, you often find it with the breakout box with preamps.  It's called the Omni-I/O breakout box.  The standard breakout box only comes with Line inputs.  This is OK if you are coming from a small mixboard or guitar stomp pedal or sometimes monitor amps have a microphone channel for those sidewalk gigs.  You know, the ones that pay the bills.

A friend gave me the Delta 66 for fixing his keyboard.  He upgraded his equipment to rack-based, Mac OS X, Pro Tools, etc so he didn't need the cheesy PC stuff any more.  That cheesy PC stuff works pretty well under Linux.

It's not fancy but it gets the work done.  Here are some recordings done with it.  These are binaural recordings of a Christmas church concert.  The microphones were two cheap electrets that I pulled out of retired telephones.

Binaural recordings are meant for headphone listening only.  They create a 3D sound image with only two microphones and a fake head.

[http://wofmusic.homelinux.org:9000/2006%2012%2003%20Christmas%20Celebration%204pm%20Program%20Binarual%20Recording/](http://wofmusic.homelinux.org:9000/2006%2012%2003%20Christmas%20Celebration%204pm%20Program%20Binarual%20Recording/)

Equipment:  Delta 66, Omni-I/O breakout box, PII, 300 MHz, Dynebolic 2.4.2, Audacity, 2-track recording.

Compare it to the mixboard recording of the same concert--Denon direct-to-CD recording:

[http://wofmusic.homelinux.org:9000/2006%2012%2003%20Christmas%20Celebration%204pm%20Mixboard%20Recording/](http://wofmusic.homelinux.org:9000/2006%2012%2003%20Christmas%20Celebration%204pm%20Mixboard%20Recording/)

---

### Post by paulg on 2007-10-11
> **punkrockguy318 said:**
> 
Is there you a card you would reccomend that just had a stereo input?  After thinking about it, I doubt there will really be a time I would use the multi-input recording, as I don't even have a room in my house big enough to jam in right now.  What is a good linux-supported card that has an XLR and 1/4" inputs?

The M-Audio MobilePre has two channels which can use either 1/4"/XLR balanced/unbalanced. It's great for guitars or mics and also has phantom power (though I've never tested this feature). As mentioned previously you can run into problems if your mic(s) require a lot of amperage but should be alright for most modern microphones I imagine. It has a stereo 1/8" output (for regular computer speakers), two 1/4" outputs and a stereo headphone amp output with a separate volume control.

As indicated I do own this card. It's served me well enough for many years but I do find myself wishing I had more inputs now that I'm regularly playing in a band setting if that's any indication to the direction you might want to take. Furthermore, I've specifically been eyeing the Presonus FirePod/FP10 - definitely worth looking into. If you're looking for something on the cheap I have no problem recommending the MobilePre. You can also find comparable devices for a bit more money in the M-Audio FireWire Solo (supported in FreeBob/FFADO) or the Presonus Inspire (supported in FreeBob/FFADO). Check out the [FreeBob]("http://freebob.sourceforge.net/index.php/List_of_Supported_Devices") and [FFADO]("http://www.ffado.org/?q=devicesupport/list") supported devices lists before you get any FireWire card. 

tgalati4's advice is also solid. You can get a lot more for the money if you get a PCI card and the M-Audio Delta line is very well supported. The 1010LT does have a couple preamps built into inputs one and two (XLR) but they are software controlled so maybe not as convenient as what you get with the Firepod but they are there. You could [probably*] run DI from any instrument amplifier/stompbox to the RCA inputs. The 1010LT is probably best suited with a mixer infront of the inputs but it offers a lot more connectivity than the Delta 66 if you can work out the connection issues.  The Delta 44/66/1010 also have the advantage of having the AD/DAC outside the box which _in theory_ would be less noisy than the 1010LT where the AD/DAC is inside the computer on the PCI card. In practise, for a home recording setup, you're probably not going to hear the difference.

The bottom line is you've got some good suggestions here from a few different people. Get something supported, with the features you need (e.g. portable, preamps) within your budget and you'll do well.

Hey Stochastic, where did you find the FirePod(/FP10) for $450? Haven't seen anyone listing it for less than $500 in Canada. Street price of $399 in the U.S. is looking awfully tempting... If I can ever pull the money together for the upgrade that is...

---

