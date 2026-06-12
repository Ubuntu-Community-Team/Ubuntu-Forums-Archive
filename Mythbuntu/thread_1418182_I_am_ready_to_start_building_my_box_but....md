---
title: "I am ready to start building my box but..."
date: 2010-02-28
forum: Mythbuntu
---

### Post by tk2kewl on 2010-02-28
Below is a diagram of what I would like to accomplish.  I have read through much of the documentation but I have a few questions.


[LIST=1]
[*]I think I need to use the FiOS boxes to change channels because Verizon encrypts everything.  Is this correct?
[*]If the answer to (1) is yes, do I need tuner cards or just capture cards?
[*]Can MythTV be used to control output of an IR transceiver so that I can use one remote or a GUI interface to control the FiOS boxes and the Yamaha receiver? If yes, is there a place to lookup supported cards/devices?
[*]Is there anything else about my proposed diagram that looks wrong?
[/LIST]
[IMG]http://yellowfinmusic.com/myth.png[/IMG]

---

### Post by frego on 2010-02-28
You'll want a dedicated frontend to each display, assuming you'll want to be able to watch what you want independent on each TV.

---

### Post by tk2kewl on 2010-02-28
Can that be done on the one box?  Front ends serving on different ports or URIs or something like that.

---

### Post by frego on 2010-02-28
Well, it might be "possible", but I think it would be a challenge.  You could put in multiple video cards and have different X sessions running, theoretically.  And install different remotes to each session.  But I think once you've spent about 40 hours trying to get everything working, you'll start finding the idea of separate frontends quite appealing.

---

### Post by tgm4883 on 2010-02-28
1.  Yes, you need to change the channel on the FIOS boxes

2.  You need to get a card that will write to the hard drive whatever it is given. It doesn't need to tune anything. On this note though, you will need a way to change the channel on the FIOS boxes, you need to either have an IR blaster, or if you are very lucky you can use firewire to change the channels, I doubt that though.

3. Yes

4. Lots. You can't go out from the FIOS boxes into the computer using HDMI, there isn't a single card that supports that. You will want to use something like the HD-PVR (Component in). You will also need separate frontends (different actual computers) for each display. You might be able to do it from a single computer, but AFAIK this hasn't been tried before so you will be figuring this all out on your own. Along those lines, you may run into resource issues where your only option may be to use separate computers for each frontend. Also, not sure why you are going HDMI out and analog out to the surround sound receiver, why not just use HDMI?

---

### Post by nickrout on 2010-02-28
> **tgm4883 said:**
> 

4. Lots. You can't go out from the FIOS boxes into the computer using HDMI, there isn't a single card that supports that. You will want to use something like the HD-PVR (Component in).


I endorse that, HDPVR seems to be the only way to go if you want Hi Def in this scenario. >  You will also need separate frontends (different actual computers) for each display. You might be able to do it from a single computer, but AFAIK this hasn't been tried before so you will be figuring this all out on your own. 

Actually it has been done before and there are some examples in the archives of the mythtv users mailing list. However it always makes my eyes glaze over, particularly compared to the simplicity and cheapness of, eg, a revo box for US$199 that will do HD decoding on the GPU and be small and quiet.

---

### Post by tk2kewl on 2010-03-01
The analog audio is intended for playback of other audio only sources such as mp3 and cd.  I am wrong that that would go out over analog?   suppose i wanted tv on but the audio to be some other source not the tv signal.

---

### Post by tgm4883 on 2010-03-01
> **tk2kewl said:**
> The analog audio is intended for playback of other audio only sources such as mp3 and cd.  I am wrong that that would go out over analog?   suppose i wanted tv on but the audio to be some other source not the tv signal.

Audio only sources would still use the HDMI. You might be able to get another audio source to use the analog out, although you wouldn't be using mythmusic at that point. If you want to watch tv and have a different audio source on (why?), they you would have to set that up at the receiver most likely. The mythbox is considered 1 source (video+audio) not 2 sources (video&audio)

---

### Post by tk2kewl on 2010-03-02
First off I want to thank everyone for their help on my first cut at this idea posted in [http://ubuntuforums.org/showthread.php?t=1418182](http://ubuntuforums.org/showthread.php?t=1418182)

Since I got a lot of it wrong, I figured I would try again a new thread.  I figure on getting 2 Acer Aspire REVOs (R1600-U910H) for my 2 remote frontends.  My new questions are relative to the IR setup.

Can the frontend receive an IR signal and relay it to the backend for transmission to an IR transmitter controlling external input and out put devices as shown on my new diagram?

[IMG]http://yellowfinmusic.com/myth2.png[/IMG]

---

### Post by ian dobson on 2010-03-02
Hi,

How it works is that the frontend says to the backend pleas start playing this channel. On the backend you can configure an external script that sends a signal to your settop box to change to channel X. The backend then starts recording the requested channel and the frontend starts streaming it.

On my system I have an external settop box then can steam the video to the mythbackend over ethernet. To change channels I wrote a small script that requests the web page on the settop box that changes channel.

Regards
Ian Dobson

---

### Post by elgordo123 on 2010-03-02
It looks like it should work.  If you have an IR remote (or keyboard) that will work with the frontend, then yes, it will send that to the backend IR.  The frontend IR Remotes should work just like a keyboard.  

  Many people control frontends (I do) with a remote (or even smartphone). This also triggers the IR transmitter on the backend (pointing to my dish receiever) when I want to change channels.

  From your diagram, the only thing I am not sure about - is that without a frontend at each location- you may not be able to separate your audio to the different places.  A frontend will direct it's sound to only that particular frontend.   If you have say 6 speakers connected to your amp/receiver and it's connected to your main backend and then you start a music file (or video) that sound will be transmitted to all of those (speakers) at once, unless you can turn them off via your Yamaha.
i.e.  The "Family Room" setup should be ok, but your sound will go out to the "outdoor" locations too -Unless your yamaha can turn just those 2 off and you remember to do it so your neighbors aren't hearing everything you watch/listen to!

The audio for "Master bedroom" and "Office" would come from the TV audio inputs coming off the frontend computer (or it's own speakers/amp). It might be do-able, but I dont know how to tell myth "if you are using this remote frontend (bedroom) use this (2nd) soundcard".

---

### Post by tk2kewl on 2010-03-02
> **elgordo123 said:**
> i.e.  The "Family Room" setup should be ok, but your sound will go out to the "outdoor" locations too -Unless your yamaha can turn just those 2 off and you remember to do it so your neighbors aren't hearing everything you watch/listen to!

The yamaha can turn those off... I was hoping that i could manipulate the yamaha reciever in that way from the myth frontend, but if not i can always do that manually.

> **elgordo123 said:**
> 
The audio for "Master bedroom" and "Office" would come from the TV audio inputs coming off the frontend computer (or it's own speakers/amp). It might be do-able, but I dont know how to tell myth "if you are using this remote frontend (bedroom) use this (2nd) soundcard".
I hope i can figure out a way to tell myth to use the other sound device.

---

### Post by tk2kewl on 2010-03-02
I continued this in a new thread with a revised plan: [http://ubuntuforums.org/showthread.php?t=1419845](http://ubuntuforums.org/showthread.php?t=1419845)

---

### Post by nickrout on 2010-03-02
Audio for master bedroom is wrong. the audio is streamed over the ethernet along with the video. There is no need (or use) for a separate audio feed from the backend to the master bedroom frontend.

A revo has the choice of audio out over hdmi or analogue stereo out over a 3.5mm stereo plug. Your hdmi out could carry 5.1 audio to either the TV or to a amplifier with hdmi in.

PS nice diagram, what software did you use?

---

### Post by tgm4883 on 2010-03-02
Yep, audio would come from the frontends, not from the backend as a separate wire. 

I haven't done much investigating on it, but there are "system events" in 0.23 which look like they could trigger scripts to control your yamaha receiver.

---

### Post by tk2kewl on 2010-03-02
> **nickrout said:**
> Audio for master bedroom is wrong. the audio is streamed over the ethernet along with the video. There is no need (or use) for a separate audio feed from the backend to the master bedroom frontend.

I was hoping to avoid purchasing an amp and using a sound card from the backend for the upstairs audio as all of the speakers have runs back to the wiring closet.


> **nickrout said:**
> PS nice diagram, what software did you use?
I used Inksape ([http://www.inkscape.org/](http://www.inkscape.org/)) and downloaded some svg icons (not sure I remember where i got the icons but if I could see if i can trace back to the source in my history tonight.)

---

### Post by tk2kewl on 2010-03-02
icons are from this set [http://www.opensecurityarchitecture.org/cms/library/icon-library](http://www.opensecurityarchitecture.org/cms/library/icon-library)

---

### Post by nickrout on 2010-03-02
thank you :)

---

### Post by nickrout on 2010-03-02
> **tk2kewl said:**
> I was hoping to avoid purchasing an amp and using a sound card from the backend for the upstairs audio as all of the speakers have runs back to the wiring closet.


Why not use the frontend soundcard?

---

### Post by tgm4883 on 2010-03-03
> **nickrout said:**
> Why not use the frontend soundcard?

My guess is this is a home pre-wired for whole house audio. It's not really set up for a system like this (unless each room has a feed back as a source to the main system).

---

### Post by tk2kewl on 2010-03-03
Yes.  I recently finished building the house.  I wired CAT5e and speaker runs that terminate at a patch panel in the wiring closet.  

I am planning to run the HDMI to the display devices using HDMI over CAT5 extenders. I only have 2 CAT5e runs to the master bedroom TV location and the extenders I was planning on using require 2 runs, which left me no place to plug in my IR transmitter. 

Last night I found some rather pricey extenders ([http://www.siig.com/ViewProduct.aspx?pn=CE-HM0051-S1](http://www.siig.com/ViewProduct.aspx?pn=CE-HM0051-S1)) that will also carry the IR signal along with the HDMI on the two runs so my 3rd diagram should be a good approximation of how things will shake out.  I think I probably will get another inexpensive HDMI A/V receiver to place between the Frontend-2 and TV and speakers.  This will allow me to still use a simple revo and not build a custom box.

[IMG]http://yellowfinmusic.com/myth3.png[/IMG]

---

### Post by elgordo123 on 2010-03-03
yeah.. that looks better and should work for you.

---

