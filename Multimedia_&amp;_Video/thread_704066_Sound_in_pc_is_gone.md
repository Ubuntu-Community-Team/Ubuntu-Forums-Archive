---
title: "Sound in pc is gone?"
date: 2008-02-22
forum: Multimedia &amp; Video
---

### Post by delilahjed44 on 2008-02-22
Hello I currently have no sound at all in my pc, I had installed wine and some of my programs went sour and would not play, they all began with sound even though they would not fully play through, as I opened up the movie file it began to change the icon selection as I viewed it to movie player...no biggie except now I have no sound.  So I un-installed wine as it seems to be a big deal needing the equivalent to quicktime for Linux, that does not seem to be happening, I downloaded all the possible quicktime favors from synaptic to play in wine but it was no good.  Ok, so I put back in a CD that plays lanquage programs with no problems,,,well until now...I have no sound no where, I have made a few selections in the preferences under sound and nothing is working, can anyone help me? my sound is completely gone...never an issue before ever...

thank you 
Sherri

---

### Post by Bubba64 on 2008-02-22
From reading your post it sounds like you may be missing some additional what are called codecs and other overlap programs here is a forum post which hopefully will help you.
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
Best of luck
Since I am not an expert in Linux I have been using it for about a year and a half from Dapper to Gutsy. This post seems applicable though, but you might look for posts on sound card issues. Personally I have never used Wine I haven't been able to get it to work and have no real use personally for it. I have never had a sound problem, but I see a lot of people posting with these problems,

---

### Post by delilahjed44 on 2008-02-22
> **Bubba64 said:**
> From reading your post it sounds like you may be missing some additional what are called codecs and other overlap programs here is a forum post which hopefully will help you.
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
Best of luck
Since I am not an expert in Linux I have been using it for about a year and a half from Dapper to Gutsy. This post seems applicable though, but you might look for posts on sound card issues. Personally I have never used Wine I haven't been able to get it to work and have no real use personally for it. I have never had a sound problem, but I see a lot of people posting with these problems,
 

Hi Bubba, thank you, what happen is...when I used wine to open a program the program would freeze, so I used esc/contr..alt...del..then I just hit the switch user, so I did not have to shut down pc, each time it started back up I had no sound, and I was at my desktop, I dont have any other users on this pc just me.  I guess by logging on for a user switch I had no sound.  So I went ahead after fooling with sound 45 minutes and shut it down..then started it back up and *poof* sound,,,have no idea why each time I did switch user why I had no sound though, that does not make sense, because I was totally back at my desktop...oh well, I may try the wine again over the weekend for this program...I just cant get it to stop freezing up...thats a pain, works but not all the way...weird   ok bye for now and thanks again.

Sherri

---

### Post by ferdostar on 2008-02-22
> **delilahjed44 said:**
> Hi Bubba, thank you, what happen is...when I used wine to open a program the program would freeze, so I used esc/contr..alt...del..then I just hit the switch user, so I did not have to shut down pc, each time it started back up I had no sound, and I was at my desktop, I dont have any other users on this pc just me.  I guess by logging on for a user switch I had no sound.  So I went ahead after fooling with sound 45 minutes and shut it down..then started it back up and *poof* sound,,,have no idea why each time I did switch user why I had no sound though, that does not make sense, because I was totally back at my desktop...oh well, I may try the wine again over the weekend for this program...I just cant get it to stop freezing up...thats a pain, works but not all the way...weird   ok bye for now and thanks again.

Sherri

Could you please take a look at you alsamixer if everything is ok
```
alsamixer
```

---

### Post by delilahjed44 on 2008-02-22
> **ferdostar said:**
> Could you please take a look at you alsamixer if everything is ok
```
alsamixer
```

 Hello, thank you for the reply, I do have sound now,,,I did as requested even so to make sure that is ok, I see it there, I guess it is ok, I dont know what happen there, when I was in wine, the program half heartely opened up, and some files would not play, then it froze, I chose log-out,,,then I re-logged back in,,,I was at my desktop,,,as I am the only user on this pc, suddenly no sound at all, never came back till I shut it all down and started back up.  Something happen in wine for this program and I dont know what that was..

thank you 
Sherri

---

### Post by Bubba64 on 2008-02-23
A restart usually is the best way to start if you have installed and deleted programs that shouldn't effect a restart although I would do a update manager and or sudo apt-get upgrade check first.

---

