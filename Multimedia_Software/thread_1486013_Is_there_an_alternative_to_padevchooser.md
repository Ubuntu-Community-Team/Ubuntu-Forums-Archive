---
title: "Is there an alternative to padevchooser?"
date: 2010-05-17
forum: Multimedia Software
---

### Post by kendoori on 2010-05-17
Am running Karmic with my Thinkpad X61 laptop. I have both the internal intel sound card, but also an outboard USB SoundBlaster Audigy NX. I don't use both cards at the same time, but have a need to control sound from various sources (inbound and outbound) depending on use (I also have a Creative webcam as part of this setup).

padevchooser does give me the control I need, but UI wise is very dense, and simply switching between inputs or outbounds that are controlled volume wise requires many clicks, and I often find myself clicking around to do simple things like make the webcam mike work when I use Skype.

I kind of wish there was a way to create profiles that are saved (e.g. external sound card out, webcam mike vs. internal sound card in and out).

Curious as to how others have overcome this interface issue.

---

### Post by Andy.N.Z on 2010-05-26
Ok, I´ve come up with what for me is a good work around.

I´m new to this as I have only just upgraded to Lucid Lynx from Jaunty missing the Koala. I use Skype on my laptop when I travel. I have some powerful external speakers that I use for music but also so that I can hear Skype when it rings & not miss a call. I use a USB headset but route the ringing to the main speakers. 

So I have been playing around with the Pulse Audio Applet & obviously am disappointed that I now can´t use my USB C-Media headset while having the ringing on the speakers. I need to have the external speakers ring otherwise I would never hear the calls. I don´t use the Skype standard ringing tone either. I switched it for an audio file that is a real old style ringing telephone sound. People hear it & swear I have an actual old telephone there!

The next best thing from what I can see is to have Pulse output the Skype sounds to **both** the external speakers and the USB headset simultaneously. This means I can use my USB headset that I like to use. I have have it ready & configured to answer calls but I can also have the ringing on the external speakers. While not ideal this is still an ok situation. It just means when I take a call I need to manually turn down the volume on the external speakers, because the callers voice will also be routed to them. As I am quite often playing music from my laptop this is something I usually have to do anyway. 

The only downside in that answering a call you need to be a bit of an octopus, using the touch pad to answer the call, put on my headset & turn down the speaker volume all at the same time. I´m still young so I can do it, anyway it makes you sound busy when you answer the call. 

To set this up is easy. In the devise chooser go to **[COLOR=Navy]´[/COLOR][COLOR=Navy]Configure Local Sound Server´[/COLOR]**. In there you will see 4 tabs the last of which is called [COLOR=Navy]´**Simultaneous Output´**[/COLOR][COLOR=Black] Tick the box in there which says ´Make[/COLOR] discoverable PulseAudio network sound devices available locally.

Now back in your Volume Control window for each application you will be able to select from 3 output options. Your internal sound card, your USB sound devise and simultaneous output. I have Skype set to simultaneous output and everything else set to the internal sound card. 

I think this is a much better option than removing Pulse audio. I did a dummy install of Lucid 1st & tried removing Pulse. That allowed me to set up Skype the same as I had in Jaunty, but it messed a lot of other things up.

Also on my particular laptop (Compaq CQ40) Pulse gives me much more volume from the internal speakers. Under Intrepid & Jaunty the maximum speaker volume was pathetic, now Pulse lets me get full volume from the speakers.

My advise, keep Pulse, forget Jaunty & try simultaneous output.
:guitar:





[**]("http://www.google.co.nz/url?sa=t&source=web&ct=res&cd=1&ved=0CBsQFjAA&url=http%3A%2F%2Fwww.ubuntu.com%2Ftesting%2Flucid%2Falpha2&rct=j&q=ubuntu+lucid+lynx&ei=XZj8S7L0BMLCrAfN6aTtAQ&usg=AFQjCNHJho0aQZ5jcUSSYdcHKT9WdL2W1A&sig2=g4ac8BHU5gqZrNLJAXAobw")

---

