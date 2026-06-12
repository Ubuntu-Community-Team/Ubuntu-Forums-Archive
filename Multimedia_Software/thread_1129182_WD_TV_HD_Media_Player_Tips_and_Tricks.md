---
title: "WD TV HD Media Player Tips and Tricks"
date: 2009-04-18
forum: Multimedia Software
---

### Post by pedja_portugalac on 2009-04-18
I decided to open this thread as a place where we can talk about eventual problems and solutions. 
Yesterday I've purchased one for my home and lately I have discovered that it can not play DTS audio (Digital Theater System), found in most of the matroska HD files, if you don't have an external digital A/V receiver which prices starts, in EU, from 500€ above for the fair one. That's bad comparing to Popcorn Hour A-110 but the price difference between two is also more then double, 99€ for WD TV Med Player and 236€ for Popcorn Hour A-110 (without HDD).
Fortunately we can make that movies playable in 15 minutes converting a DTS sound file into AC3 5.1 using mkvtools and ffmpeg and merging it into the .mkv file.

I use a Death Race 10GB rip for this example.

1. First step is identifying DTS file. You can do it in terminal, from the same directory where is your .mkv movie.
> mkvmerge -i Death.Race.Unrated.2008.BluRay.1080p.DTS.x264.mkv
The output is
> File 'Death.Race.Unrated.2008.BluRay.1080p.DTS.x264.mkv': container: Matroska
Track ID 1: video (V_MPEG4/ISO/AVC)
Track ID 2: audio (A_DTS)
Track ID 3: subtitles S_TEXT/UTF8
Track ID 4: subtitles S_TEXT/UTF8
We see that the 2: audio (A_DTS) file is the one we want to extract for re-encoding and we do it with command: 
> mkvextract tracks Death.Race.Unrated.2008.BluRay.1080p.DTS.x264.mkv 2:audio.dts
Five minutes later we have that audio.dts extracted file in the same directory and now we convert it into AC3 5.1 file using ffmpeg.
> ffmpeg -i audio.dts -acodec ac3 -ac 6 -ab 448k audio.ac3
After it has been done it's time to merge your new AC3 audio file with existing .mkv file
> mkvmerge -o your_new_movie.mkv Death.Race.Unrated.2008.BluRay.1080p.DTS.x264.mkv audio.ac3 
And after 5 minutes you'll get your playable movie called your_new_movie.mkv or whatever you call it.

PS. To avoid original DTS audio file, 1.2GB, in your new creation, you can do it like this
> mkvmerge -o your_new_movie.mkv -A Death.Race.Unrated.2008.BluRay.1080p.DTS.x264.mkv audio.ac3
Where option -A will tell mkvmerge to avoid original audio file so you can save some space on your HDD.

---

### Post by unix1980 on 2009-04-19
Thanks for starting this topic.  The WD TV has some odd non-features.  I have found that it has trouble with even some AC3 audio tracks.  Using your technique I re-encoded from AC3 to AC3 and it fixed a problem of mine.  I haven't yet identified what the WD TV doesn't like about certain audio tracks, but if I figure it out I will post here.

BTW, there is a nice script here that does basically the same thing except it uses dcadec instead of ffmpeg to re-encode the audio: [http://github.com/JakeWharton/mkvdts2ac3/tree/master](http://github.com/JakeWharton/mkvdts2ac3/tree/master)

In spite of the quirks of the WD TV, I think it is a very good device for the price.  I hope others will contribute tips for working around any problems they find.

---

### Post by pedja_portugalac on 2009-04-19
> **unix1980 said:**
> I have found that it has trouble with even some AC3 audio tracks.  Using your technique I re-encoded from AC3 to AC3 and it fixed a problem of mine.
ffmpeg can convert in many formats and it's, actually, one of the most powerful tools for this kind of jobs. I am not ready to pay 1000€ for the basic A/V HD Receiver (with speakers) witch is capable of reproducing DTS sound when I already have 5.1 surround capable system which is enough for my needs. 10 minutes job is acceptable for me. Maybe one day when the prices drop down I buy one but it's surely not tomorrow. My Sony full HD 42 inches TV costed 700€ and I'll pay 1000 for the "low priced" poor A/V Receiver, NO WAY.

---

### Post by jarek.uk on 2009-11-21
Hi [pedja_portugalac]("http://ubuntuforums.org/member.php?u=379082"),

I'm planning to get WD TV HD player for my brother for x-mass and I was wandering, what did you mean it can't play audio without A/V reciever with DTS.

My brother has one and i'm pretty sure I've seen dts logo on it. I'm not sure about a model and I can't check it as he's miles away or ask him, but I assume once connected via optic cable it should work fine. Did you have a chance to test it with A/V reciever?

And how you like it anyway. After more then 1/2 an year of using it your opinion would be useful before purchase.

thanks

---

### Post by pedja_portugalac on 2009-12-01
> **jarek.uk said:**
> Hi [pedja_portugalac]("http://ubuntuforums.org/member.php?u=379082"),

I'm planning to get WD TV HD player for my brother for x-mass and I was wandering, what did you mean it can't play audio without A/V reciever with DTS.
Hi. It means that it can not play DTS sound if you don't have an external DTS receiver/decoder [http://www.avland.co.uk/technics/sada8/sada8glrg.jpg](http://www.avland.co.uk/technics/sada8/sada8glrg.jpg)
You'll have to transcode as shown above. 
> My brother has one and i'm pretty sure I've seen dts logo on it. I'm not sure about a model and I can't check it as he's miles away or ask him, but I assume once connected via optic cable it should work fine. Did you have a chance to test it with A/V reciever?I haven't chance to test it but it will 100% work connected to receiver by optical cable.
> And how you like it anyway. After more then 1/2 an year of using it your opinion would be useful before purchase.

thanks
WD TV HD player was the best option for me as there wasn't lot of choice in Portugal. Pop Corn Hour is the best player but I couldn't buy it in Portugal. The price of PPH was from 250€. It accept internal HDD, later firmware and codecs updates and much more. On the other side WD TV HD player cost me 99€ but it's just player, not container, and you have to hook your external HDD to it all the time. Moreover it doesn't play DTS sound natively, you'll need extra hardware for that, but it can play mkv files, h264 codecs, and much more, which is widely used to distribute HD, Blue Ray rips over internet. Knowing that, now all depends on you budget. If you can and want the best one visit [http://www.popcornhour.com/onlinestore/](http://www.popcornhour.com/onlinestore/) for the information. If you can't afford or find that one, WD TV HD player is a very good player which demands lil-bit hooking and waiting for initial content read but image and playing quality is great on Full HD screens. If your brother already have external DTS receiver and one external HDD, it will be economic but fully functional option. ;)

---

### Post by Kanedagr on 2010-10-17
Hi and greetings from Greece. I have the same media player (version 1). Unfortunately WD stopped the updates for this particular machine, so we have to impovise ourselves. Recently i have downloaded an anime which was made with mkvtoolnix 4.3. The problem is the 4.3.0 uses compressed headers and WD HD TV doesn't recognize them and freezes so badly, that wants hard reset 2 or 3 times to unfreeze. The fansub group suggested to me to remux it with mkvtoolnix but using version 4. How can i install on kubuntu 10.10 64 bit the mkvtoolnix version 4.0.0? The repositories have the latest version (4.3.0). I tried downloading the source file and compile but i can't seem to make it work. Any suggestions?

---

### Post by Sin_fe on 2010-10-20
Open Synaptic, search Mkvtoolnix, highlight (clic) the package, go to "Package" in the Synaptic menu, choose "Forced version". Then select the 4.0.0 version in the opened window.

---

### Post by Kanedagr on 2010-10-20
Thank you very much!!

---

