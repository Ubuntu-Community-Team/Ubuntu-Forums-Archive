---
title: "audio format legal questions"
date: 2010-02-11
forum: Multimedia Software
---

### Post by parminides on 2010-02-11
I've noticed that Ubuntu doesn't play audio cd's out of the box.

It made me wonder about the patents (software or otherwise) involved in the cdda format. I suppose that those patents may have expired by now.

While I was wondering about possible legal restrictions on audio formats, I also thought about the wav audio format.

I use wav files as an intermediary in ripping cd's with cdda2wav and oggenc (eventually to ogg files). The wav format was apparently designed by Microsoft.

Is it clearly legal to play or otherwise use audio cd's in Linux? Is the use and manipulation of the cdda and wav audio formats legal? 

There's a lot of information about the legality of mp3's, and I have satisfied myself (thanks to Fluendo) that playing them in Linux is ok. But I haven't been able to find anything about the legality of native cd format or wav files in Linux.

I would appreciate some thoughts and opinions.

---

### Post by HappyFeet on 2010-02-11
If you are worried about the codec police knocking down your door in the middle of the night, don't. First of all, there is no way anyone can know what codecs you are using. Secondly, if you have ever used windows, you have already paid for codecs such as mp3. Thirdly, most everyone downloads non-free codecs as needed. Relax, and download what you need.

But, if you are one of the ultra-do-gooders that can't sleep at night, knowing you have downloaded codecs without paying "the man", go [HERE]("http://shop.canonical.com/index.php?cPath=19") and get your credit card out.

---

### Post by mc4man on 2010-02-11
> I've noticed that Ubuntu doesn't play audio cd's out of the box.
If you've noticed that then you have some local issue unrelated to any codec/lib, ect.

Any install will play audio cd's with nothing additional installed, even a live cd can play them if you have a free cd/dvd drive

---

### Post by parminides on 2010-02-13
> **mc4man said:**
> If you've noticed that then you have some local issue unrelated to any codec/lib, ect.

Any install will play audio cd's with nothing additional installed, even a live cd can play them if you have a free cd/dvd drive

Well, maybe they would have played in some program, but they wouldn't play in rhythmbox. I had to install some plugin. Perhaps I made an erroneous generalization that they wouldn't play in Ubuntu at all.

---

### Post by parminides on 2010-02-13
> **HappyFeet said:**
> If you are worried about the codec police knocking down your door in the middle of the night, don't. First of all, there is no way anyone can know what codecs you are using. Secondly, if you have ever used windows, you have already paid for codecs such as mp3. Thirdly, most everyone downloads non-free codecs as needed. Relax, and download what you need.

But, if you are one of the ultra-do-gooders that can't sleep at night, knowing you have downloaded codecs without paying "the man", go [HERE]("http://shop.canonical.com/index.php?cPath=19") and get your credit card out.

I guess that I am an ultra-do-gooder compared to HappyFeet. There's no need for anyone else to reply with some variant of "don't worry, everybody does it, you won't get caught." I'm well aware of that. I live without fear of the codec police.

I went to the Canonical Store and found only 4 products, none of which mentioned native cd or the wav formats. Since the ultra-do-gooder Canonical Store didn't offer those formats, I strongly suspected that they are legal.

The big controversy about Linux's use of the native dvd format several years ago has been well-chronicled and needs no further elaboration here. And the ultra-do-gooder Canonical Store does offer a dvd player. It seemed to me that playing cd's is completely analogous to playing dvd's.

But I'd never heard of anyone making a big deal about playing cd's. I had a couple of guesses why. One was that the patents have expired. The other was that whoever owns the cd patents (Phillips? Sony?) just wants anyone and everyone to play cd's.

I became very curious about this issue as I tweaked the audio on my Ubuntu box the other day. Someone must have thought about it, and I wanted something a little deeper than "if you ever bought a cd player, then you already paid for it, so relax, buddy."

As for wav files, they certainly existed before mp3's. I suspected that the patent has expired. The other day I tried to find some information about this on Google but came up completely dry.

However, since no one answered my questions, I hit Google again and discovered the following (which applies to the United States):

Before June 8, 1995, patents lasted for 17 yr after date of issue. The law changed at that time to 20 yr after the effective application date. For patents active at the time the law changed, the duration was 17 years after issue date or 20 yr after the effective application date, whichever is longer.

cd's were first introduced in 1982, 28 years ago. Therefore, they've been in the public domain for at least 8 years.

The wav audio format was developed by IBM and Microsoft and introduced with Windows 3.1 in 1991. I didn't bother finding out when the patent for wav files was issued because the situation is complicated by the fact that since then the format was updated (with probable associated patents for the updates).

Nonetheless, according to the Digital Preservation section of the Library of Congress "[n]o licensing required" for wav files (cf. [http://www.digitalpreservation.gov/formats/fdd/fdd000001.shtml](http://www.digitalpreservation.gov/formats/fdd/fdd000001.shtml)).

So both native cd and wav formats are now in the public domain. We don't have to worry about those codec cops for those 2 formats! I know I'll sleep easier, now. That answers my questions. Thank you to HappyFeet and mc4man for responding.

---

### Post by markbuntu on 2010-02-13
The way patent law works is that only people who distribute these codecs need to pay for a license. Users do not. So, no matter where you got these codecs from the only one liable for you having them is the one who you got them from which can vary widely from country to country.

This is the way patent law works. All a patent does is give the patent holder the right to exclude others from the local market. It does nothing to prevent individuals from using patented items for their own personal use.

It would be a very interesting and high profile court case if one of these codec patent holders ever tried to sue someone for using a "illegally obtained" codec on their home computer. The barriers they would need to overcome would be so huge just to get it into court that they do not even think about going there. Nevertheless they can prevent an international company like Canonical from distributing them without paying a license fee.

Patents are only good for 20 years, MP3 will be out of patent in a few years. That is why we have MP4 and a slew of new proprietary codecs being pushed on us.

---

### Post by SuperSonic4 on 2010-02-13
Depends where you are, I believe the EU does not recognise mp3 as patented.

---

### Post by mc4man on 2010-02-13
Just one  further thing concerning audio cd's - really,  nothing is needed for playback, - if rhythmbox was balking, well gstreamer and rhythmbox do have some inconsistencies that may have caused that, not the playback of cd's.

Happen to be on a karmic livecd for something - added nothing, only enabled wireless, rhythmbox plays an audio cd fine.

As mentioned as far as the codecs that do require installing libs, plugins, ect. - nobody cares about what you do for personal use, encoding or decoding and in some cases any licensing has been taken care of. 
I'd think many patent holders are glad individuals  use their formats

---

