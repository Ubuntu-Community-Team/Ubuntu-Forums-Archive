---
title: "Ripping individual episodes of a mini-series"
date: 2016-01-19
forum: Multimedia Software
---

### Post by John Jason Jordan on 2016-01-19
Xubuntu 14.04.3, up to date.

I have a two-DVD set of a TV mini-series composed of six episodes. I am trying to rip each episode as an individual file. I have Handbrake 2.2.1 (from PPA), but it can't find the individual episodes; that is, from Disc 1 it will rip the first episode, but the others do not appear. And from Disc 2 it will rip only Episode 4. I tried DVD:RIP, and it also only sees one episode per disc. I also tried Acidrip, and it does better (although the video quality is lousy), but still can't figure out one of the episodes. I know the episode that it won't rip is on VTS_6_0.IFO through VTS_6_3.VOB because when I play those files directly in VLC it plays the episode in question. I don't understand why Acidrip rips a different episode when I tell it to rip those files. But because the quality from Acidrip is so poor I would prefer to use Handbrake, if only I could figure out how to get it to see more that just one episode per disc.

I think the majority of my trouble is because I don't understand clearly the relationship between an episode and the files in the VIDEO_TS folder that pertain to the episode. I've searched the Multimedia forum and googled for hours and can't find anything that helps. 

Any suggestions?

---

### Post by shantiq on 2016-01-23
hmm JJJ   I think that is a tricky one

The episodes probably do not match the VOBs [they usually do not]so the way to do this it seems is to rip the entire disc as an mkv or mp4   [Handbrake]and then to cut manually using avconv or ffmpeg   see[ here]("http://ubuntuforums.org/showthread.php?t=2309623&p=13421896#post13421896") for info
If there is a way to rip episodes I have for one never seen it ...

---

### Post by Rob Sayer on 2016-01-23
I think MakeMKV will usually rip individual episodes, and it 'rips' in the true sense of the word.  I.e. it doesn't compress (i.e. reencode) them.  You still need Handbrake or similar if you want to shrink the files.

Actually, if you want no quality loss at all and don't care about file size I think MakeMKV is probably the best option in general.

It's a tarball install, which I don't like doing, but it's a useful enough app that I've done it.  Here's a guide:

[http://www.makemkv.com/forum2/viewtopic.php?f=3&t=5266](http://www.makemkv.com/forum2/viewtopic.php?f=3&t=5266)

If MakeMKV doesn't rip individual files from a particular disk, which happens with some of them, you'll need something like mkvtoolnix-gui.  That's in the repos so you can use Synaptic.

---

### Post by QDR06VV9 on 2016-01-23
Or you could keep it simple and add his PPA:
```
**PPA description**

[COLOR=#333333][FONT=monospace]MakeMKV is your one-click solution to convert video that you own into free and patents-unencumbered format that can be 
played everywhere. MakeMKV is a format converter, otherwise called "transcoder". It converts the video clips from 
proprietary (and usually encrypted) disc into a set of MKV files, preserving most information but not changing it in any way. 
The MKV format can store multiple video/audio tracks with all meta-information and preserve chapters. There are many players that 
can play MKV files nearly on all platforms, and there are tools to convert MKV files to many formats, including DVD and Blu-ray discs.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]install:
sudo add-apt-repository ppa:heyarje/makemkv-beta
sudo apt-get update
sudo apt-get install makemkv-bin makemkv-oss[/FONT][/COLOR]


```
There is also installers native to your DE's: As Mate has one  [https://plus.google.com/+MartinWimpress/posts/PgoQi9G8Vk8](https://plus.google.com/+MartinWimpress/posts/PgoQi9G8Vk8)
Just another option is all..
Kind Regards

---

### Post by John Jason Jordan on 2016-01-23
Thanks shantiq and Rob for the suggestions.

Since posting my original query I discovered a solution that works some of the time. If you rip a multiple title DVD just straight away Handbrake will rip only the first title. But in the upper left corner of Handbrake there is a drop-down labeled Titles. The list of titles in the drop-down is not always accurate, so sometimes you have to rip each one to find what you want. For example, I was recently ripping a TV mini-series that I have on two DVDs, four episodes per DVD. Handbrake listed 11 titles for each DVD, which is certainly confusing. But by looking at the VOB files in Thunar I could see that there were eight VOBs of 1.1GB, each followed by another VOB of 700-900MB. The VOBs were "repeated" with an incremental number, leading me to suspect that the manufacturer had duplicated the VOBs so as to make a copy of each title. I have found that to be a common practice, so as to make the DVD more error-proof. Ultimately, by trial and error, I found that episode 1 was on Title 5, repeated on 6, episode 2 was on Title 7, duplicated on 8, and so on. 

But I have another DVD with three movie shorts and the Titles menu showed "No titles." For that DVD I played each of the large VOBs individually directly in VLC. By doing so I was able to determine which "set" of VOBs belonged to which movie. Then I created a separate folder for each movie and copied the VOBs just for that movie into its folder. When I pointed Handbrake to the first folder it ripped the first movie beautifully, and ditto for the second movie, but when I pointed it to the third folder it ripped another copy of the second movie. "WTH"? I thought. I double checked and the VOBs in the third folder were, indeed, the VOBs for the third movie; when I played them directly in VLC I saw the third movie, but something on that DVD confuses Handbrake. 

I should add that I have Handbrake 2.2.1 from a PPA on my laptop, which is what I normally use. I also have a desktop with Xubuntu 12.04 (yeah, yeah, I know, I'm lazy) and it has Handbrake from the 12.04 repositories. I tried the same three-separate-folder trick and Handbrake still got confused about the third movie. 

I also have makemkv and I tried using it on the same messed up DVD. Unfortunately I found makemkv difficult to figure out, and I never succeeded in getting any usable output from it. Nor could I get anything useful from Acidrip, OGMrip or DVD:RIP.

---

### Post by shantiq on 2016-01-23
JJJ looking again

there is one easy way with Handbrake; all you need is to write down your episode times from the DVD prior to ripping; not a big t[ask] :] then to do this for each ... set to seconds on the dropdown box and enter start and finish times

[[IMG]http://s20.postimg.org/dlfw4n2c9/image.jpg[/IMG]]("http://postimg.org/image/dlfw4n2c9/")

---

