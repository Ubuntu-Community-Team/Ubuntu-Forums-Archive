---
title: "Mythbuntu and anime"
date: 2007-11-03
forum: Mythbuntu
---

### Post by Awperator on 2007-11-03
Hello All!
First, my setup:
AMD 3400+ (2.4ghz) single core socket 754
DFI NF3 250GB
SATA WD Raptor (Primary)
SATA Seagate HD (Secondary)
Radeon 9600 connected to plasma tv via DVI
Onboard sound, onboard Ethernet
Media Center Remote version 2


I am at wits end. I've tried so many programs (Knoppmyth, GBPVR, Windows MCE), so many techniques, and I've lurked on forums for so many days this past month. All I want to do is have a system that plays my video files (xvid, avi, mkv, etc) and my anime with subtitles and multiple language streams (mostly .mkv) with me being lazy and controlling everything through the remote. Just a frontend. I don't want to record TV; I don't want any PVR applications, all I want is a HTPC that plays my library of mkv, avi, divx, and xvid files.

I ran windows media center for the longest time, and it worked fine when I was watching regular xvids or divx files, but if I wanted to watch anime (mostly KAA rips), I would have to bring out a mouse and manually control the computer via the core media player. Windows MCE didn't like the MKV file format; I had to mess with the registery for it to even know they existed, and when I then tried to play the file, I wasn't satisfied with the results, and I couldn't control with stream or which subtitles loaded. Then I tried GBpvr. That was a little bit of a pain to configure, I mean, coming from windows MCE (it just works!), but I was able to configure HIP with my MCE remote, and then run the program. The anime files played natively, but I couldn't get the subtitles to work. There was only one other person that posted about anime, but his post didn't help me that much. So then windows was down and out.

I think I want to try out mythbuntu. My question for you guys is are there any anime watchers out here? If so, do you use Mythbuntu to watch, and also how did you configure your setup so it can play xvid files and mkvs without skipping a beat?

---

### Post by zekopeko on 2007-11-03
check this out: [http://elisa.fluendo.com/](http://elisa.fluendo.com/)
i think its going to be perfect for your needs.

it plays everything (mkv, avi, ogm...). it loads subs as far as i can tell but i don't think you can change them at this moment (ie. it loads the default one)
try making a request in their forums for selecting audio streams and subs. i'll also pitch in for this to get implemented. 
aslo if you are running 7.10 you can just put links to your anime folder in the Video folder that gets made on install and Elisa is going to pick it up without a problem.

---

### Post by stevetv on 2007-11-03
i watch loads of anime.  (ergo proxy is very cool. flcl all time fav).  .mkv files work a treat with mplayer.  mythbuntu uses mplayer as the "default" player (different from the internal player).  

however the default run command for mplayer doesn't show me sub titles..and my remote isn't mapped great for mplayer (working on that).

 i created a new file type in video settings called mkv, and used the default mplayer run command but i added 
```

-slang eng

```
you can also use a specific run command for specific videos if you come across anything unusual.

---

