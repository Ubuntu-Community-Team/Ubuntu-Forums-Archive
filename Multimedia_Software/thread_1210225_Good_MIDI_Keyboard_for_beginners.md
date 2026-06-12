---
title: "Good MIDI Keyboard for beginners?"
date: 2009-07-11
forum: Multimedia Software
---

### Post by keenPenguin on 2009-07-11
Hi, 

I am a beginner who would like to learn to play on a keyboard. My general idea is this: I would like to find a MIDI Keyboard for beginners and then learn with the program Synthesia ([http://www.synthesiagame.com/](http://www.synthesiagame.com/) , used to be called "Piano Hero") which is only available for Windows. 

But I would also like to play the keyboard on Ubuntu. Do you know a good MIDI Keyboard for beginners which would work with Ubuntu? I would like to spend not too much beyond 100€, or possibly less. Do you have any suggestions which keyboards would be good for the purpose *and* would work with Ubuntu without major tweaking (if possible)?

I am using Hardy but will change to a newer Ubuntu or Kubuntu soon.

---

### Post by raboofje on 2009-07-11
A similar tool is 'piano booster' - it might be more suitable because it uses actual 'sheet music' notation instead of the 'piano roll'. It also has the option to pause until you found the right note, that sounds instructive.

The m-audio keystation series are nice and work fine with ubuntu. Depending on the number of octaves you require they might or might not be in your price range though.

---

### Post by keenPenguin on 2009-07-11
Thanks a lot!

I have several questions now:

- You mean [this one]("http://www.amazon.de/gp/product/B000FHP0E4/ref=s9_simb_gw_xu_s0_p23_t2?pf_rd_m=A3JWKAKR8XB7XF&pf_rd_s=center-2&pf_rd_r=08BRA684CK9AKZFKKJM3&pf_rd_t=101&pf_rd_p=463375173&pf_rd_i=301128"), right?
Does it not require any installation? Just plug it in via USB and use it on Hardy?

- piano booster is really cool. Synthesia has a commercial version (16 USD) which can scroll sheets and pause, just like booster. But I'd like to try Ubuntu/booster first. Question: I downloaded a midi file, but wasn't able to play it on Hardy. I also loaded it into booster, but no tune came out (although the sheet was loaded and visually played). What might be wrong?

- I have practically no experience on the piano, the only thing I can do is reading musical sheets (only the basics, reading them veeeery slowly). Would you say that 49 keys are sufficient to start with, or are they just an annoyance? I wouldn't start with Chopin, I'd prefer playing simple songs I know and like, and perhaps I'd find simplified versions of them. So would you say 49 are all right?

---

### Post by raboofje on 2009-07-12
> **keenPenguin said:**
> ]You mean [this one]("http://www.amazon.de/gp/product/B000FHP0E4/ref=s9_simb_gw_xu_s0_p23_t2?pf_rd_m=A3JWKAKR8XB7XF&pf_rd_s=center-2&pf_rd_r=08BRA684CK9AKZFKKJM3&pf_rd_t=101&pf_rd_p=463375173&pf_rd_i=301128"), right?
Does it not require any installation? Just plug it in via USB and use it on Hardy?

Jep, that's one. You just plug it in though USB and it shows up as an ALSA MIDI device.

> Synthesia has a commercial version (16 USD) which can scroll sheets and pause, just like booster.

Sounds like a cool app, too

> But I'd like to try Ubuntu/booster first. Question: I downloaded a midi file, but wasn't able to play it on Hardy. I also loaded it into booster, but no tune came out (although the sheet was loaded and visually played). What might be wrong?

Do you have 'normal' sound when playing an mp3 or so?

> I have practically no experience on the piano, the only thing I can do is reading musical sheets (only the basics, reading them veeeery slowly). Would you say that 49 keys are sufficient to start with, or are they just an annoyance? I wouldn't start with Chopin, I'd prefer playing simple songs I know and like, and perhaps I'd find simplified versions of them. So would you say 49 are all right?

I have the 49-key variant and that's quite sufficient for me, but i'm not a 'real' piano player either, so it just depends.... Perhaps take a look at some of the songs you'd like to be able to play and see what their range is?

---

### Post by keenPenguin on 2009-07-12
Thanks again!

Yes, I can play MP3s without any problems. And when I open a midi file in e.g. the standard Movie Player, KMid, or booster, they load the file and pretend as if they were playing it. But unlike with MP3, there is no sound! What could it be, what could I do?

---

### Post by raboofje on 2009-07-12
> **keenPenguin said:**
> when I open a midi file in e.g. the standard Movie Player, KMid, or booster, they load the file and pretend as if they were playing it. But unlike with MP3, there is no sound

in piano booster, what 'midi output device' did you configure?

---

### Post by keenPenguin on 2009-07-12
Tried all of the available...

---

### Post by raboofje on 2009-07-12
> **keenPenguin said:**
> Tried all of the available...

Which were available?

---

### Post by keenPenguin on 2009-07-12
I've uploaded a screenshot:

[[img]http://www.abload.de/thumb/piano_boosterxfn9.png[/img]](http://www.abload.de/image.php?img=piano_boosterxfn9.png)

---

### Post by raboofje on 2009-07-14
OK, 'None' is obvious, 'Midi through' doesn't really do anything. Not sure about 'MPU 401' is probably your sound card, to which you likely don't have a hardware synth connected.

Finding out how to convert a MIDI stream to audible sound seems to be a bit of a FAQ here, so I dug up the relevant wiki page and improved on it a bit.

Does [https://help.ubuntu.com/community/Midi/SoftwareSynthesisHowTo](https://help.ubuntu.com/community/Midi/SoftwareSynthesisHowTo) clarify things? Anything that needs further elaboration there?

---

### Post by keenPenguin on 2009-07-19
Hi raboofje!

Thanks a lot, the solution was simple! Like it said in your link, I simpliy installed TiMidity++. After the installation from the standard repositories, I was able to hear Midi out of the box. Movie Player and Piano Booster work fine now. I am going to order a keystation now :-)

Thanks a lot!

---

### Post by raboofje on 2009-07-19
Good to hear [https://help.ubuntu.com/community/Midi/SoftwareSynthesisHowTo](https://help.ubuntu.com/community/Midi/SoftwareSynthesisHowTo) was useful! Have fun!

---

### Post by keenPenguin on 2009-07-21
Hi raboofje, 

sorry, I was too happy too early. I found out now that not all .mid files are played. Some are played like I described, but playing other midis, e.g. movie player freezes and does not give even a tune. I tried midis from different websites, some did work, most didn't. This probably has to do with some kind of different midi specifications?

---

### Post by raboofje on 2009-07-24
> **keenPenguin said:**
> I found out now that not all .mid files are played. Some are played like I described, but playing other midis, e.g. movie player freezes and does not give even a tune. I tried midis from different websites, some did work, most didn't. This probably has to do with some kind of different midi specifications?

Could you give a specific example? E.g. which midi file, player and softsynth you used, and what happened instead of playing?

---

### Post by svenskmand on 2010-06-12
If anybody is browsing this thread I just wanted to say that I have also been on the lookout for a good keyboard for a beginner which also works as a midi keyboard with Ubuntu. And I just bought the Yamaha PSR-E423 which works with JACK straight out of the box, it is just plug and play, no configuration hassle at all :)

---

### Post by mczakk on 2011-04-26
slightly off topic, but its the only reference i can find to synthesia :S
i'm running it in wine, but there was no sound originally, so i installed timidity, now i am getting some of the instruments, but not all. i had a look at the wealth of midi information on the web, and now have a slightly blown mind with all the complexity of it! can anyone suggest a simple solution to my problem?

thanks:)

---

