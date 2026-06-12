---
title: "mythtv, saa7134, edgy, and the everylasting sound problem"
date: 2006-11-29
forum: Multimedia &amp; Video
---

### Post by eldragon on 2006-11-29
ok, ive got a flyvideo 2000 with the saa7134 chipset.

this card, as specified by the maker, doesnt support audio through the pci bus. and, thus, i run the audio through a passthrough cable, from my tuner to my audio line in jack.

tvtime had no time working with it in edgy.

xawtv doesnt work at all, dont know why, it freezes.

mythtv: works, sorta.......its being detected by mythtv alright. i get it to tune my cable channels, i get it to record, everything works fine.
but i get no audio.

is there a way to get mythtv to capture the audio from the line in input on my souncard? AND sync it with the video?, only thing ive been able to do is:

$ v4lctl -c /dev/video0 volume mute off

wich forces the capture card to output audio. this works. but i get audio off sync by 1 or 2 seconds, and NO audio control on mythtv works with it (timeshift, time stretch, volume).
even recording ignores the audio channel.

so. what am i doing wrong?
the audio output is set to /dev/dsp
im setting the controls to: /dev/mixer and make mythtv work with 'line'

audio is being init ok according to mythtv:

2006-11-29 17:41:50.418 TV: Attempting to change from None to WatchingLiveTV
2006-11-29 17:41:50.419 Using protocol version 31
2006-11-29 17:41:50.944 Opening OSS audio device '/dev/dsp'.
2006-11-29 17:41:50.970 VideoOutputXv: XvMCTex: Init failed
2006-11-29 17:41:50.970 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon Video Overlay'

did anyone manage to get this running?

---

### Post by josesanders on 2006-11-30
I'm having a very similar problem, and unfortunately I don't have an answer, just a question.  How do you get the command v4lctl to work?  I tried that, but the command was not found.

---

### Post by eldragon on 2006-11-30
> **josesanders said:**
> I'm having a very similar problem, and unfortunately I don't have an answer, just a question.  How do you get the command v4lctl to work?  I tried that, but the command was not found.

hmmm, i wouldnt know, it just did. did you try querying apt-cache with v4lctl?

could be in a package i insalled in the past? :-k 

i think the issue resides in the card NOT being able to send audio through the saa7134 module. and mythtv not realizing it. 
anyway, doing the v4lctl trick wont help watching or recording, there is a considerable lag between sound and video, and its not adjustable since mythtv isnt being able to capture audio from the line input of the soundcard.
when dealing with these types of cards, mythtv should: unmute the card, mute the line in, and capture through it. then output its processed audio signal in sync with the video through the pcm channel. if anyone knows how to do this. drop a message :D

---

### Post by eldragon on 2006-11-30
ok, ive managed to get audio off the card.

so, after unmutting the card (and mutting the line-in output, yet,checking the capture checkbox)

stop the mythtv backend:sudo /etc/init.d/mythtv-backend stop
run mythtv-setup
and setup the capturecard: 

for sound input: edit the box, and type /dev/dsp:line

this got mythtv running as it should. sound is a bit distorted. im still trying to figure out how to fix that. but its a start.

---

### Post by Lem on 2006-12-01
If you're having problems with distorted sound in mythtv, have yuou tried the 'enable extra audio buffering' (or something similar - I'm not at my box right now) in the setup dialogue (on the frontend)

---

### Post by josesanders on 2006-12-04
/dev/dsp:line

I tried that and it didn't do anything.  My card has only a microphone input, not a line input, so I also tried changing it to /dev/dsp:mic, but also with no effect.  Maybe I have the name of the input wrong?  Could it be "microphone"?  Is there a command that lists the names of the available inputs?

---

### Post by Caraibes on 2006-12-04
Hey guys, I also have a Flyvideo 2000 :

And it is precisely why I don't run Ubuntu on my desktop. I run Bag, and here's a very easy how-to for our TV card :

[http://forums.blagblagblag.org/viewtopic.php?t=2605&highlight=card](http://forums.blagblagblag.org/viewtopic.php?t=2605&highlight=card)

---

### Post by eldragon on 2006-12-05
> **Caraibes said:**
> Hey guys, I also have a Flyvideo 2000 :

And it is precisely why I don't run Ubuntu on my desktop. I run Bag, and here's a very easy how-to for our TV card :

[http://forums.blagblagblag.org/viewtopic.php?t=2605&highlight=card](http://forums.blagblagblag.org/viewtopic.php?t=2605&highlight=card)

i dont see what the problem is, i got mine working on ubuntu without a hitch.
mythtv has proven to be problematic. but everyday i get closer to my goal. flawless sound like tvtime. maybe on the next mythtv release

anyway, edgy has finally fixed all my issues (with some tuning). now i cant wait to see what feisty will bring us :)

---

### Post by fragmental on 2006-12-09
I have a similar, but slighty different card as the flyvideo 2000. It's a clone made by kobian mercury, and I have had the same problem. I get sound in tvtime without a hitch.

Recently I've made headway in a different way. I used the command "aplay -l" to get a list of "playback hardware devices" and I get the following

card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

This basically says I have a hw:0,0 device and a hw:1,0 device.  I guess those are the two DACs on the card?

Anyway, I can then start up tvtime and mute all my line-in mixers so I get no audio; then I can load "arecord -D hw:0,0 -r 32000 -c 2 -f S16_LE | aplay -" and get buffered audio that way.  Likewise I can also, with tvtime closed, run "mplayer tv://$channel -tv driver=v4l2:device=/dev/video0:chanlist=us-bcast:alsa:adevice=hw.0,0:amode=1:audiorate=32000:forceaudio:volume=100:immediatemode=0:norm=NTSC" and get audio and video together.

However, I haven't been able to get that to work in mythtv yet and all it does is use the audio through the patch cable.  However, I think it should be recording the audio so it should work for recording in mythtv.

It might essentially be the same thing you did here, only doing it a different way.  I can't tell right now because my tv card seems to have completely died or something just now so I'm going to have to figure out what that is all about.

---

### Post by fragmental on 2006-12-09
Yeah, I can't seem to change the sound output on the capture cound in mythtv-setup to anything except what is already there.  Whatever I type in just gets changed back whenever I close and reopen the file.  It works in the mythfrontend but not for the capture card in mythtv-setup.

I just realised that I do have audio coming out of mythtvfrontend though, it's just incredibly quiet and full of static.  Don't know what's up with that.  I'm just about to completely give up on it though.

---

### Post by fragmental on 2006-12-11
I can get audio perfectly through mythtv but I have to open up "watch tv" in mythtv and then unmute the card using "v4lctl volume mute off" on the command line.  After that it will work correctly, at least for a while.  After a reboot and possibly just after a period of time or some other event it will switch back and I will have to do it again.  I'm also getting crashing.

I have no idea how to permanently fix this.

---

### Post by fragmental on 2006-12-11
Yeah, so I think the problem is that mythtv does not know how to mute and unmute the capture card.  Therefore I have to unmute it manually using the v4lctl command(which comes with xawtv).  I have to then mute the line-in or get sound from the capture card all the time.  If I open up a program like tvtime that knows how to mute and unmute the capture card, I must unmute the line-in in order to get any sound from it, and after I close it, it will automatically mute the capture card and I will need to re-unmute the capture card in order to use it with mythtv.

So, in short mythtv is stupid and doesn't know how to mute and unmute my capture card.  Don't know why.  I can probably just add the v4lctl command to run at startup and then make sure to never open tvtime.

---

### Post by soodesune on 2006-12-11
In using Fedora Core 6, but the:

 v4lctl -c /dev/video0 volume mute off

solution works for me (fc6 saa7134 tv card driver).

Just to add another data point, I have 2 cards, one on /dev/dsp3(an ATI HDTV wonder) and the other on /dev/dsp1(a kworld tv7133, which uses the saa7134 tv driver and the saa1734-alsa sound driver).  I've never had any *sound* problem with the ATI card.  I found that if I run:

sox -c 2 -sw -r 32000 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp3

piping the output of /dev/dsp1 into /dev/dsp3, every thing works great with tvtime.  Mythtv, however, isn't so lucky.  Running the sox command wont allow either device to have audio, myth says they are both "in use by another device", which they are of coarse.

---

### Post by eldragon on 2006-12-17
> **fragmental said:**
> Yeah, so I think the problem is that mythtv does not know how to mute and unmute the capture card.  Therefore I have to unmute it manually using the v4lctl command(which comes with xawtv).  I have to then mute the line-in or get sound from the capture card all the time.  If I open up a program like tvtime that knows how to mute and unmute the capture card, I must unmute the line-in in order to get any sound from it, and after I close it, it will automatically mute the capture card and I will need to re-unmute the capture card in order to use it with mythtv.

So, in short mythtv is stupid and doesn't know how to mute and unmute my capture card.  Don't know why.  I can probably just add the v4lctl command to run at startup and then make sure to never open tvtime.

ok, im off the loop for a while, a storm fried my capture card........ woke up, computer was still as a lamp, rebooted, cant get the card to work, windows xp wont find it either.....now im looking for a replacement. what should i buy? stick with saa7134 or go with something else?

i dont have digital tv, so it must have a cabletv  input. If it supports hardware encoding, even better :D

---

### Post by fragmental on 2006-12-18
I think I have heard good things about a..hauppauge wintv pvr 150? I think.  I think they have hardware mpeg2 encoding.  I think they are saa7134 devices, but I'm not completely sure.  I think there may be some other hauppauge devices and some pinnacle devices that are supposed to be very good too.

The only card I can vouch for is the saa7130hl device by Kobian Mercury.  It is very cheap. I think mine was like $20 after  $10 mail in rebate. I can say for sure that it works perfectly with tv time if you set the tuner and card ID in the module correctly and it works well with mythtv if you make sure to unmute it every time the computer boots up. It does not have hardware encoding and the driver and software support in windows really sucks, however.
There is also a connexant based Kobian Mercury capture card that I don't know anything about.

Also, I haven't been able to get the FM support to work under Linux yet, though I admit, I haven't tried in a long time.

You could display digital tv on a regular tv with an digital capture card in your computer, though it wouldn't be in any sort of HD resolution...so I'm not sure if you would want to do that, but you might be able to get some of the channels you couldn't get otherwise.

---

### Post by eldragon on 2006-12-19
> **fragmental said:**
> I think I have heard good things about a..hauppauge wintv pvr 150? I think.  I think they have hardware mpeg2 encoding.  I think they are saa7134 devices, but I'm not completely sure.  I think there may be some other hauppauge devices and some pinnacle devices that are supposed to be very good too.

The only card I can vouch for is the saa7130hl device by Kobian Mercury.  It is very cheap. I think mine was like $20 after  $10 mail in rebate. I can say for sure that it works perfectly with tv time if you set the tuner and card ID in the module correctly and it works well with mythtv if you make sure to unmute it every time the computer boots up. It does not have hardware encoding and the driver and software support in windows really sucks, however.
There is also a connexant based Kobian Mercury capture card that I don't know anything about.

Also, I haven't been able to get the FM support to work under Linux yet, though I admit, I haven't tried in a long time.

You could display digital tv on a regular tv with an digital capture card in your computer, though it wouldn't be in any sort of HD resolution...so I'm not sure if you would want to do that, but you might be able to get some of the channels you couldn't get otherwise.


well, i think i might be vowing for a 7134 device, had a good ride with my last one. i dont really care about windows drivers. if only they suppposrted audio throught the pci bus. that would make mythtv work withouth a hitch.

doing some search, im looking into this: [http://www.comprousa.com/New/en/product/t750/t750.html](http://www.comprousa.com/New/en/product/t750/t750.html)

has a saa7135 (?) compat? gonna check that, and supports both dtv and atv. now i need to find a retailer here that has it.

cheers

---

### Post by fragmental on 2006-12-20
I'm fairly certain the kobian mercury saa7134 device does not do audio over pci.  At least, I have been unable to get it to work. I think that all of the flyvideo 2000 based oem devices, which is what the card is, cannot do audio over pci.  the flyvideo 3000 based oem devices can, I think, but I haven't tested it.

I recently bought a kworld atsc-110 and I believe it does both atsc and ntsc, but I don't have it yet so I can't vouch for it.  If you need dvb-t then I guess that card wouldn't work for you anyway.  Good luck.

---

### Post by eldragon on 2006-12-21
update, ended up buying a cheap pinnacle pctv. which has the saa7134 chipset. to be honest, i was happier with the cheaper flyvideo one.

this one seems slower when starting up and  takes more time to switch channels.

but, on the other hand, ive got the remote thing going, which isnt really working right now, plan to look into it during the weekend.

cheers, thanks for all the help

now, do you know a command to mute the line in output (not, capture)?

---

