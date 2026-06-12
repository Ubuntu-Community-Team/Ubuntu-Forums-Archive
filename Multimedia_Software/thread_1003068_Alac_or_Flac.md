---
title: "Alac or Flac????"
date: 2008-12-05
forum: Multimedia Software
---

### Post by Shugs81 on 2008-12-05
thinking about ripping all my cd's to lossless and wondered if there's a difference? I know I can get iTunes working in linux using wine and would like to use my 160gb ipod classic... for which there are no new firmwares and due to apple discontinuing them I don't expect there to be...

I've seen you can get flac to alac converters and can get codecs to play them... if there's little difference is there an alac ripper for linux? or would it be better flac to alac converting so i can have em on my Ipod?

---

### Post by mc4man on 2008-12-05
I'm not sure if this would interest you and if it's free or just a free trial.

Just gave it a quick test and worked perfectly in wine. I really have no need for it so just installed the program and the add on apple codecs.

Though I may investigate a little further after seeing it work.

[http://www.dbpoweramp.com/](http://www.dbpoweramp.com/)

[http://www.dbpoweramp.com/codec-central.htm](http://www.dbpoweramp.com/codec-central.htm)

see screens


edit: definitely a trial, don't see any limitations atm other than access to 3 out of the 4 meta db's, seems to also include a converter.
For myself I'll probably stick to rubyripper using either flac or NeroAac, but am going to keep this installed.....

---

### Post by Existentialist on 2008-12-05
I use FLAC for my music in case I ever decided to buy something other than an Ipod, and the fact that the ALAC gstreamer plugins caused my Rhythmbox to randomly crash.

I have Rockbox installed on my Ipod because it supports FLAC playback.  The only drawback is that battery life is not as good as the stock apple firmware due to less efficient audio decoding.  Just thought I would mention it in case you decide to go with FLAC.

[http://www.rockbox.org/](http://www.rockbox.org/)

---

### Post by Shugs81 on 2008-12-06
i would have used rockbox but it doesn't support the Ipod classics which is what I've got.... apple have decided to stop the 160gb ones and just keep the 120gb ones cause they're smaller... swines...

Think i'll go for the alac option and convert everything to flac once on the ipod....

cheers peeps...

---

### Post by lister171254 on 2008-12-06
I suggest to rip to FLAC as you do not loose any sound quality (if that matters).

Install Amarok as the player and get the iPod plugin. It will convert the flac files on the fly when you transfer the files to the iPod.

---

### Post by Shugs81 on 2008-12-06
> **lister171254 said:**
> I suggest to rip to FLAC as you do not loose any sound quality (if that matters).

Install Amarok as the player and get the iPod plugin. It will convert the flac files on the fly when you transfer the files to the iPod.

oooo.... thanks for that!!!! solves my issues!!! cheers dude!!!\\:D/

---

### Post by Silent Warrior on 2008-12-06
Hm... Is this a good place to insinuate that proper audiophiles never transcode? (WMA->MP3, FLAC->MPC, whatever.) Um... Anyway, nuttin further.

---

### Post by Shugs81 on 2008-12-10
the flac files will be my main media for home use.... alac just for ipod when i'm driving about and posibly used when dj-ing...

---

### Post by Shugs81 on 2008-12-10
actually.... will it convert flac to alac when copying over???

---

### Post by the wizard of oz on 2009-03-20
> **lister171254 said:**
> I suggest to rip to FLAC as you do not loose any sound quality (if that matters).

Install Amarok as the player and get the iPod plugin. It will convert the flac files on the fly when you transfer the files to the iPod.It doesn't convert the .flac to .alac when transferring for me, am I missing something here?

---

### Post by 8086 on 2010-05-12
There is no (working) Alac encoder on Linux, and there won't be anytime soon either. I would just go for using Foobar2000 or dbPowerAmp via Wine. They can both rip to ALAC and transcode Flac->ALAC. You should then just stick to using ALAC for your music library.

Personally, I rip everything I have to FLAC, and then use mp3fs as a way of transcoding this to my iPod Nano. It has too little space for anything else but lossy compression anyway. Works well

---

### Post by atca on 2011-11-05
To add to this in case any one else is interested 
I've pulled together a script which converts a CD to FLAC and ALAC transcribing the meta data between FLAC and ALAC since they ue slightly different formats. It also performs conversion frmo FLAC to ALAC as part of this process and could be easily modified to go the other way. It takes the whole process from rip to FLAC/ALAC rip with 2 clicks and in under 15 minutes, it can also be used to batch CD rips.

See [here]("http://confoundedtech.blogspot.com/2011/11/ubuntu-automatically-rip-cd-to-flac-and.html")

---

