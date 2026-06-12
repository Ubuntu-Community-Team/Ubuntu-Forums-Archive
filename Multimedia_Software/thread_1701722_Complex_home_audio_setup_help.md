---
title: "Complex home audio setup help"
date: 2011-03-06
forum: Multimedia Software
---

### Post by ricardisimo on 2011-03-06
It should be easy enough to wire my computer to a receiver, and this then to speakers around my house, either through the ceiling or under the floor, wirelessly... whatever. No problem there.

However, is there any way for me to send different signals to different sets of speakers? In other words, can I send jazz to the living room, salsa to the back porch, and classical to the bedroom all at the same time? What player(s) can do this on Ubuntu, and what type of sound card am I looking at? Thanks in advance for any tips or tricks, product reviews or any other help.

---

### Post by SuperFreak on 2011-03-06
Perhaps not quite what you are looking for , but consider the Squeezebox ([http://www.logitech.com/speakers-audio/wireless-music-systems](http://www.logitech.com/speakers-audio/wireless-music-systems)).
It is a wired or wireless music player that interfaces between your computer and stereo. I have 3 and this allows me to play music in different areas of the house even outside with the Boom model which has it's own speakers and amplifier. Sound quality is excellent depending on the quality of the source music files and 1000s of internet radio stations are available for free and many more by subscription.

---

### Post by b0b138 on 2011-03-06
Very interesting ;)

I have no definite answer, but can maybe help point to the right direction.

First, you'll need multiple sound cards, or a sound card that does multiple channels. 2 channels covers left and right. So 3 rooms is 6 channels. Each room would also need its own receiver/powered speakers.

Second, you'll have to have some way to tell the music player to use a specific sound card or channels. This might be easier through a command line player. aplay seems to have some options for this, but seems limited on what formats it will play.  I think mplayer works well from command line, and will probably have more options than aplay.

So if that would work, next you would need to uses playlists? Or edit the desktop launchers to use the options of using specific cards/channels.

---

### Post by SuperFreak on 2011-03-06
The software that Squeezebox uses is Open Source and free . You can download it from the Ubuntu Software Center. This would have numerous advantages over your soundcard solution including; better sound quality, ability to control the music in another room either from that room by a remote or the computer, ability to see what is being played in the other room as the Squeezebox has a display (newer models show album art not just song information), no need to buy additional soundcards or other equipment, RSS feeds, some models will display photos from a memory card in slideshow fashion.
There are other devices like the Squeezebox (ie Sonos) but I am familiar with the Squeezebox and have been using it on both Linux and Windows systems for about 7 years


edit: Ricardismo I notice you are from California. The Squeezebox was developed in Mountain View California

You could use powered speakers eliminating the need for a receiver

---

### Post by ricardisimo on 2011-03-07
Superfreak: thanks, but I am indeed going to search around first for a computer and receiver solution before I start buying other accouterments.

b0b: would a 5.1-ready sound card work? Are the channels on such a card pre-assigned (i.e., the sub has to be sub, and surrounds have to be surrounds, etc.)? Or can I reassign them all to play three pairs of left-right stereo?

I've had little audio joy since pulseaudio was implemented on Ubuntu, so I'm holding out hope that there is some ultimate purpose and advantage to this abomination. Like, in this case, allowing me to control separate outputs to different speakers.

---

### Post by b0b138 on 2011-03-07
In theory I guess it could, it just all depends whether the software can output to specific channels. (unfortunately, nothing to do with pulse...not that I know of anyway ;))

A 5.1 card would only give you 2 rooms of stereo sound though.  Front L-R and Rear L-R.  The center and sub channels are mono

---

### Post by b0b138 on 2011-03-07
hmmm...ok so I was able to play one song in sone speaker and another song in the other :) following this guide [http://www.mplayerhq.hu/DOCS/HTML/en/advaudio-channels.html](http://www.mplayerhq.hu/DOCS/HTML/en/advaudio-channels.html) which I barely understand lol

```
mplayer -af channels=2:2:from:to:from:to /path/to/musicfile
```

the from and to is routing the channels. So for me to listen to something in only the left (channel 0) I say ok, left plays in left, and right plays in left....left:left:right:left....0:0:1:0

so the whole line is this to play in the left

```
mplayer -af channels=2:2:0:0:1:0 /path/to/musicfile1
``` 

and this to play in the right

```
mplayer -af channels=2:2:0:1:1:1 /path/to/musicfile2
``` 

so if
0=front left
1=front right
2=rear left
3=reat right
4=center
5=sub

I think you could do this for the front speakers
```
mplayer -af channels=2:2:0:0:1:1 /path/to/musicfile1
```

and this for the rear
```
mplayer -af channels=2:2:0:2:1:3 /path/to/musicfile2
```

I don't have a surround card so I can't test that

---

### Post by nothingspecial on 2011-03-08
If you have any old computers lying around you can use the squeezeboxserver software without the hardware.

Just build squeezeslave on each box, you don't even need a gui so it will run on really old machines.

[http://wiki.slimdevices.com/index.php/SqueezeSlave#Linux_build_instructions](http://wiki.slimdevices.com/index.php/SqueezeSlave#Linux_build_instructions)

---

### Post by aeiah on 2011-03-08
once you have all the sound outputs you need  (3, is it?) you might enjoy using mpd. this is if you're wiring your house.. everyone seems rather fond of the squeezebox idea but it depends how easy wiring your house would be. wires are always more reliable than wifi and streaming.


mpd works in a server/client way. i have two mpd server daemons running on this computer - one is called main and this outputs through my soundcard. the other is called http and this outputs an http stream. this means i can listen to one thing locally and stream another to a different computer. there's no reason why you couldnt have 3 mpd daemons running called livingroom, porch, bedroom each outputting to different local soundcards (or channels in a 5.1 soundcard or whatever solution you arrive at). then you can wire these to your receiver(s) and so forth.

because mpd uses a server/client architecture, you could control it from anywhere in the house too with a laptop, mobile phone, tablet etc.

---

### Post by aeiah on 2011-03-08
then just control the daemons using something like gmpc on any pc/smartphone/pda/tablet on the network 

[img]http://ompldr.org/vN3BxeA[/img]

---

### Post by ricardisimo on 2011-03-08
Thank you so much. You're very right: first I have to run the wires before I can even begin to speculate on how to split my signals. Still, I'm going to look closely at GMPC, and I also just noticed JackEQ. The description for it in synaptic makes it sound ideal. However, I would still need to **** around with it to see if it's what I need.

As far as center and sub being mono, I believe all six outputs are mono. That's what one channel is, right? It's just a question of whether they are wired solely for certain frequencies, or if they will carry any signal. If they will, then you just need to pair them together with one another, call one left and the other right. There might also be either hardware or software gain settings to be tweaked (L-C-R tend to be set several dB louder than the surrounds).

---

