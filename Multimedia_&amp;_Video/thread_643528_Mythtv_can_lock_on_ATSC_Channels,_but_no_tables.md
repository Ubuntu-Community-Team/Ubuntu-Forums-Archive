---
title: "Mythtv can lock on ATSC Channels, but no tables"
date: 2007-12-17
forum: Multimedia &amp; Video
---

### Post by Andywmm9 on 2007-12-17
I'm using an ATI HDTV Wonder on Gusty Gibbon and the analog portion of the tuner is working just fine.  I used the DTV tuner a couple of months ago and it was working also.  However when I took my computer home after christmas break and started scanning for channels off my antenna, I get a signal lock but mythtv says it can't find the tables therefore no channels are added.  I know that the signal level is fine because I plugged in another TV and everything works great there.  I'm not even sure what no tables mean in the channel search, can anyone provide any assistance? 

Thanks

---

### Post by riverty on 2007-12-19
bump

I'm having the same problem and have found no solution as yet.

---

### Post by d_morgan on 2008-03-09
hi riverty,
  can you tell me about your sound configuration?  i'm having the same problem on the digital tuner and also getting no sound from the analog tuner... just video.

my sound comes from the integrated sound of the chipset (ich5).  there is no spdif or ac3 output...i'm just trying to get 2ch stereo out.  i've tried umuting everything in for the integrated sound card in alsamixer but still no luck.  do i need to enable one of the recording channels?

---

### Post by d_morgan on 2008-03-09
A STEP IN THE RIGHT DIRECTION

I was able to get the digital stations (atsc) to come up diurring a scan.  the steps i took were:
1) i tried to install the firmware following the ubuntu 7.04 instructions [here]("http://www.mythtv.org/wiki/index.php?title=ATI_HDTV_Wonder&oldid=27607") but it didn't work
2) i then removed all sources and all cards from the myth backend setup
3) then i removed the firmware /lib/firmware and the dvb directory from /usr/share/doc
4) i removed the module too with the command " modprobe -r cx88-dvb"
5) in myth backend setup i tried to add the dvb card again but it was not detected
6) i added the module again with the command "modprobe cx88-dvb"
7) added the card in myth, added schedules direct (free trial) in source, connected the card input to schedules direct, scanned for channels and they came up

in short i downloaded the firmware, added the module, removed the firmware, removed the module, and added the module back.  also i did go through the recorder options settings when adding the dvb card in myth even though i left everything default w/ no changes.. that could have been the fix too.

...working on getting sound out of analog channels next.

---

### Post by curryrice71 on 2008-03-17
I get the no tables error as well. I had given up on this card but messed around with it some more last night, and finally got it to pick up 2 channels, but the rest time out. I get the feeling that depending on where you live, you just need a really good antenna for this card.

I have 2 Pinnacle 800i cards that work great, and work with the crappiest antenna in the world (one I made)

---

