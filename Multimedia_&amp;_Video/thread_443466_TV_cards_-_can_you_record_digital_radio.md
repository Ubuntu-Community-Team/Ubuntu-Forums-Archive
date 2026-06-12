---
title: "TV cards - can you record digital radio?"
date: 2007-05-14
forum: Multimedia &amp; Video
---

### Post by willnapier on 2007-05-14
Hi. I am considering getting a tv card for my feisty box. I will use the feisty MythTV guide if I do. I just have one quick question. My main interest is actually in recording music from the digital radio broadcasts, mostly from the BBC. The TV cards out there tend to say that they record onto mpeg2, divX, etc. These are video codecs. Does anyone know if you can record digital radio, perhaps into mp3 or some open sound file format? If they don't, there is no real incentive for me to get a tv card.

With thanks

Will

---

### Post by dannyboy79 on 2007-05-14
check out jebi, it allows you to record internet radio stations. but you wnat to be able to record the source of the am/fm tuner on  your tv card? don't get a tv card if all you want to do is record from am/fm radio! you can merely use a normal radio that you own, then buy a cable that plugs into the hradphone jack and the other end has the same kind of male plug on it and you plug that end into your computer audio in. the only bad part about that is your radio is what you have to turn the station with etc etc. there are probably many apps that can record the audio into your computer. otherwise get a am/fm tuner card then you can capture that to mp3's using gstreamer and or gnomeradio. [http://www.wh-hms.uni-ulm.de/~mfcn/gnomeradio/](http://www.wh-hms.uni-ulm.de/~mfcn/gnomeradio/)

---

### Post by willnapier on 2007-05-15
Thanks Dannyboy79 I hadn't known of those options. However my main interest is in recording the digital radio  broadcasts. In the UK we have 'freeview' digital TV channels, perhaps 80 or so of them. Some of these channels broadcast digital radio. My question is whether it is possible to record music from these channels to the hard disk, and if so in what form would it be done.
 
Regards, Will

---

### Post by jfinkels on 2007-05-15
> **willnapier said:**
> Thanks Dannyboy79 I hadn't known of those options. However my main interest is in recording the digital radio  broadcasts. In the UK we have 'freeview' digital TV channels, perhaps 80 or so of them. Some of these channels broadcast digital radio. My question is whether it is possible to record music from these channels to the hard disk, and if so in what form would it be done.
 
Regards, Will

We have that here (the States), too, if you subscribe to digital cable...there are some channels that play a song and show some static information and a photo, changing only every minute or so. It would be interesting to see how this works out, if you try to record that station.

---

### Post by dannyboy79 on 2007-05-15
according to here: [http://www.mythtv.org/wiki/index.php/Record_multiple_channels_from_one_multiplex#DVB-T_.28.22Freeview.22.29](http://www.mythtv.org/wiki/index.php/Record_multiple_channels_from_one_multiplex#DVB-T_.28.22Freeview.22.29)
you can use mythtv to record DVB-T ("Freeview") . Just get a card that is supported by the drivers. heres all the info you could ever need regarding DVB (digital video broadcast)

[http://linuxtv.org/v4lwiki/index.php/Main_Page](http://linuxtv.org/v4lwiki/index.php/Main_Page)

---

### Post by willnapier on 2007-05-15
Thanks for the link Dannyboy79. I have been looking on the packaging of some TV cards and I notice that none of them explicitly say that you can record digital radio. They offer listen and record DVB-T, and they only offer 'listen' to the digital radio broadcasts. You can record analogue broadcasts, but there is no point in that for me, as I already have a cd recorder on my analogue radio receiver. If anyone does know that it is possible to record digital RADIO, I would be very interested. With thanks, Will.

---

### Post by r76 on 2007-06-14
Sorry for the late reply!  I use Kaffeine to do this - I record the files as .m2t (mpeg2 transport stream) then use projectX to demux and remove any errors, saving sound as an .mp2 file.  This can easily be transcoded to .mp3 for greater compression if necessary (and you may be able to skip the projectX step to save time). Using Kaffeine, DVB radio channels are under 'Digital TV' - so you can use the same schedule recording facilities and timeshift recording.

---

