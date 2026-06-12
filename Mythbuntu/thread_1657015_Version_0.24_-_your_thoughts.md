---
title: "Version 0.24 - your thoughts"
date: 2010-12-31
forum: Mythbuntu
---

### Post by ian dobson on 2010-12-31
Hi,

So I've been running MythTV/Mythbuntu since 2008 and always followed the leading edge (daily builds then fixes branch). Since 23.1 I've not bothered with updating.

So my question is, all of you running 0.24, what do you think of it? Are there any real reasons to upgrade? It's not like there's a killer feature like VDPAU in version 23 or 22 with the JYA backports).

Regards
Ian Dobson

---

### Post by BicyclerBoy on 2010-12-31
I've very recently upgraded to JYA 0.24+fixes ppa from 0.23+fixes compiled source.
The upgrade delay was due to lack of LATM_AAC in 0.24 until ffmpeg finally added support.

There is no one killer feature unless you are into blueray etc.
But I think there has been a huge amount of work done.

The improvements I hoped for were DVD playback (big improvement) & A/V sync offsets stored in database (not sure).
The audio configuration stuff is very nice to use.

So 0.23+fixes was so good that upgrade was only forced by DVD issues..
And 0.24 does so many things I can not currently use..

---

### Post by williammanda on 2010-12-31
The audio change is a big + for me. All versions before .24 I had to turn my volume up 100% to hear it well. Now my volume is at 40% and that is loud. Also I like the database backup feature (I don't think that is mythtv related but more mythbuntu). I don't like the removal of dvd ripping but I have substituted Makemkv. Mythweb has problems but I think it is going to be fixed in an upcoming patch (if .24 is installed from scratch, upgrading works ok). My remote, snapstream, isn't supported in lirc any more. You have to set it up as a ati/x10 and the remote quits working at random but not as much lately (that could be due to upgrades).

---

### Post by newlinux on 2010-12-31
for me there is no killer feature. It has some enhancements to HD-PVR support which is one reason I upgraded. The Internal player seems to get better with every release with handling random files with various encoding methods from various sources, and I have noticed more improvements here too. I think this release is close to completely allowing me to rely on the Internal player in mythvideo.

There are some cool (but incomplete) themes out there for .24, but the OSD being completely tied to the theme now is a detriment for some.

---

### Post by 4romany on 2010-12-31
I've not saw a "got to" reason to upgrade - but with that said I really like the UI interface - and as the previous poster said the internal player does get better.   Not sure if I'm ready to say goodbye to mplayer for my movies but this version does come closer to the idea...

---

### Post by ian dobson on 2011-01-01
Hi,

So the main thing is the nice UI, that's not a killer function for me. I just want to watch videos not play with menus.

I'm quite happy with how the internal player works. I've only found afew mkv's that don't play that well, and they didn't play too well on my windows box.

So, I'll stay with 23.1 until the next ubuntu update (11.04).

Thanks for the information

Ian Dobson

---

### Post by uncle hammy on 2011-01-01
Storage groups now play .iso and Video_TS...no more local file systems for those...'nuff said right there for me to have upgraded :).  Audio is vastly better and the UI is all nicer.

---

### Post by sami8519 on 2011-01-01
> **newlinux said:**
> There are some cool (but incomplete) themes out there for .24, [COLOR=Red]but the OSD being completely tied to the theme now is a detriment for some[/COLOR].

yup, me included.

---

### Post by ian dobson on 2011-01-01
> **uncle hammy said:**
> Storage groups now play .iso and Video_TS...no more local file systems for those...'nuff said right there for me to have upgraded :).  Audio is vastly better and the UI is all nicer.

Hi,

I've got no problems with a network mount (I need them for other things) and I don't have any DVD rips, only afew mkv's. I'm using HDMI to my TV for audio, so would that make any difference for me?

Regards
Ian Dobson

---

### Post by williammanda on 2011-01-01
> **ian dobson said:**
> Hi,

I've got no problems with a network mount (I need them for other things) and I don't have any DVD rips, only afew mkv's. I'm using HDMI to my TV for audio, so would that make any difference for me?

Regards
Ian Dobson

As I stated before the sound is greatly enhanced.

---

### Post by ian dobson on 2011-01-01
> **williammanda said:**
> As I stated before the sound is greatly enhanced.

Sorry, but in my setup I just past the sound through spdif to my graphic card, that just sends the raw stream to the TV. So what can you improve on that? Digital all the way to the TV.

Regards
Ian Dobson

---

### Post by BicyclerBoy on 2011-01-02
S/PDIF to the video card is not how it is done on the newer video cards.
S/PDIF is limited to 48KHz 5.1 matrix encoded or 2ch 96KHz (i think)

So there is was a lot of work to support EAC3 & DTS-MA & LPCM via HDMI (needs alsa 1.0.23).

Any audio coming out of TV speakers is destroyed anyway so wouldn't make any difference using wet string for wire.

The DVD playback is greatly improved.
I have not found a new release that does not play perfect. 
As a media centre this is important.

---

### Post by jmeads on 2011-01-03
I upgraded to 0.24 from a nice stable 0.23 fixes setup; I had issues with dvb tuning after the upgrade and frontend crashes so ended up rolling back after 24 hours (thankfully I'd made mysql backups before the upgrade) .

From an end user perspective there is no reason to upgrade, I'm going to wait and see what 0.25 brings.

---

