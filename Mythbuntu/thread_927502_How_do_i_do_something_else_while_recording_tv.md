---
title: "How do i do something else while recording tv?"
date: 2008-09-23
forum: Mythbuntu
---

### Post by leeko on 2008-09-23
Hi all,

i'm a bit confused about how to do this:

I have a combined backend/frontend box, running mythbuntu 8.04. 

Tonight, I recorded an hour-long show while watching it (the "countdown to Heroes" at 8pm). I also scheduled mythtv to record the show immediately after it (the Heroes season premiere at 9pm). I watched the premiere until 9:37pm, when my wife got home from work. 

When she sat down, I pressed "escape" to get back to the main menu, then started watching the "countdown" recording again (which my wife had missed). We watched the whole hour-long recording. 

Later, when I went to start the recording of the "Heroes premiere", I found that it had stopped recording at 37 minutes - the moment I pressed "escape". Is this the correct behaviour? 

If so, how do I do something else with my mythfrontend while I'm recording a show? I have an ATI HDTV wonder, which has 2 tuners but the analogue tuner isn't set up. I realise that with only one tuner, I can't watch a different station, but I thought I should be able to watch a recording or listen to music while recording? 

I would fully understand this behaviour if I just pressed "record" while watching, then pressed escape. But, I had set this show to be a scheduled recording! 

Any help you can offer would be much appreciated!

Thanks,

Lee

---

### Post by volkswagner on 2008-09-23
Did you start viewing via live tv, or via select recording?

Take a look at the key bindings.  Perhaps you can select "o" or "d", then select keep, and esc. out of that.

Jump points may help.  You may bind a key on the remote to bring up the main menu, recordings, etc.  This can be accessed via mythweb.

[http://www.mythtv.org/wiki/index.php/Jump_points]("http://www.mythtv.org/wiki/index.php/Jump_points")

---

### Post by Bal_Zac on 2008-09-23
If you want to record a show and watch it at the same time, hit the record button (R).  This is normal behavior.  You didn't tell myth to continue recording the program, you just exited, so it thought you were done.  Remember computers are like robots.  They will do EXACTLY as they are told whether right or wrong, hence the matrix and many more great sci-fi movies.

---

### Post by leeko on 2008-09-23
Thanks for the replies. 

Bal_zac - as I mentioned in my original post, I had scheduled this recording. I didn't just hit 'R'. When I exited the liveTV, there was no warning that my recording would be cancelled - it just took me back to the menu. 

Volkswagner - I scheduled the recording of the show starting at 9pm, but happened to be watching that same channel leading up to 9pm. I had also hit 'R' to record the show before it, and it was still recording when heroes started at 9. 

I've now set up a jumppoint to take me straight out to the main menu. Thanks for the suggestion.  

The craziest thing, though: I found the complete heroes episode today! Last night, under "watch recordings" I had a bunch of partial shows from channel hopping, and I had the 37 minute segment of heroes. Nothing else.. 

Today, while messing around with it I deleted all of the recordings under "watch recordings" and "delete recordings", then scanned for videos again. Next time I opened up that folder, my full 2-hour episode of heroes was sitting right in front of me (and the show before it!). 

Do I have to wait for the recording to finish, then scan for new videos before a recording will show up? That seems a little bizarre. Or, is this likely a bug? 

Thanks again for your help,

Lee

---

### Post by mrand on 2008-09-23
> **lee_alkureishi said:**
> Thanks for the replies. 

Bal_zac - as I mentioned in my original post, I had scheduled this recording. I didn't just hit 'R'. When I exited the liveTV, there was no warning that my recording would be cancelled - it just took me back to the menu. 

Volkswagner - I scheduled the recording of the show starting at 9pm, but happened to be watching that same channel leading up to 9pm. I had also hit 'R' to record the show before it, and it was still recording when heroes started at 9. 

I've now set up a jumppoint to take me straight out to the main menu. Thanks for the suggestion.  

The craziest thing, though: I found the complete heroes episode today! Last night, under "watch recordings" I had a bunch of partial shows from channel hopping, and I had the 37 minute segment of heroes. Nothing else.. 

Today, while messing around with it I deleted all of the recordings under "watch recordings" and "delete recordings", then scanned for videos again. Next time I opened up that folder, my full 2-hour episode of heroes was sitting right in front of me (and the show before it!). 

Do I have to wait for the recording to finish, then scan for new videos before a recording will show up? That seems a little bizarre. Or, is this likely a bug? 

Thanks again for your help,

Lee

Howdy Lee,

This is all well used stuff, so it is pretty unlikely to be a bug.  I don't quite understand when you say that you scanned for videos though... are you saying you went to the MythVideo plugin and scanned for video's and it found your episode?

Is your mythvideo directory pointing to your recordings directory?  What was the filename of the recording?

You should be able to go to the recorded programs and recording schedules listings and get an idea of what occurred yesterday.

[INDENT]Marc[/INDENT]

---

### Post by leeko on 2008-09-23
Hi,

Believe me, I thought it was weird, too!

I ran a scan in mythvideo as an incidental thing - My network went down briefly this morning, so I had to re-scan my video library which is on a NAS disk samba share. I didn't expect it to have an effect on my recordings. It probably didn't, but for whatever reason, the recording showed up in my list at some point after that. 

My recording directory and video directory are completely separate. 

The recording filename is 1111_20080922210001.mpg. It's 11Gb in size. 

I swear, the recording wasn't present in any of the mythtv screens last night. It appeared magically this morning, only after I deleted all of the recordings I could find!

Lee

---

### Post by seeker5528 on 2008-09-23
If it's a scheduled recording, wait 'till it starts recording, go to 'media library --> watch recordings' and watch it from there.

Later, Seeker

---

### Post by toorima on 2008-09-23
Could be that it recorded it but also recorded it in live tv mode, same channel, same multiplex, multirecord works, and when you went into recordings had the live tv filter on, therefor only saw the 37 min version of hereos.

---

### Post by leeko on 2008-09-23
yeah, that seems like the most likely explanation... 

Thanks everyone for the help/advice in this thread :)

Lee

---

