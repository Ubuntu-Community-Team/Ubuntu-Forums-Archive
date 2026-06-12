---
title: "Video Editor Kdenlive - &quot;Looks promising&quot;, but..."
date: 2008-05-10
forum: Multimedia Software
---

### Post by wadelewis4 on 2008-05-10
Just wanted to say that I was hunting down video editing software - simply because I wanted to post a video on youtube. After tons of time passed, I tried several "solutions": Avidemux, LiVES, Cinelerra, etc. etc. The list goes on for days.. ok, not really but whatever. So I decided to try Kdenlive after reading about it. They are seriously on the right track (developers), but it still has major problems. My need is to have a pre-created video file (in AVI format) sitting pretty in my home folder, and on a time-line combine a simple audio track (mp3), thus creating the same video but with a soundtrack. I cannot do this with the other programs I've tried. But with Kdenlive I actually got this quasi-accomplished - with the exception of the fact that the program actually crashes X and knocks me back to my login window. :mad:

Sidenote: I had my sessions set to be recorded on exit, so everytime I logged in there Kdenlive sat staring at me with that stupid message window about crashing and wanting to know if I wanted to try to restore it. Yes? No? Close the freaking window? -- Doesn't matter, it crashes anyway, kicking me back out to login again. hahaha

I'm getting pwned by video editing. 

I managed to get it to stop, and I even deleted the files from the project and can get the program working again, but I'm hesitant to try it again. *sigh*

Ubuntu Hardy - Gnome

Questions? Comments? Snide remarks? I'm all ears.. or eyes.. or whatever..

---

### Post by cor2y on 2008-05-10
you could always mux the video and audio together using mencoder from the terminal :)
But since you probably need to add stuff like intros or text to the video kdenlive is needed.

Ok what version of kdenlive?
The one from the repos should work but if it is constantly crashing you might want to compile yourself (not as hard as it once was but still a challenge see the kdenlive wiki for compiling if you desire that)
Is compiz enabled?
If yes to the second question disable compiz when launching/working in kdenlive
Kdenlive sometimes crashes and kills/restarts x if compiz is enabled (note you can restart or start compiz when kdenlive has lauched/is open but not before)

---

### Post by cotcot on 2008-05-10
Cinelerra is able to this. Have a look in the File format list of the File --> Render dialog.

---

### Post by wadelewis4 on 2008-05-11
> **cor2y said:**
> Is compiz enabled?
If yes to the second question disable compiz when launching/working in kdenlive
Kdenlive sometimes crashes and kills/restarts x if compiz is enabled (note you can restart or start compiz when kdenlive has lauched/is open but not before)

You know, I didn't even think about that! So, when I stopped compiz I was able to combine the audio & video with absolutely no problems. 

Thanks a ton. (Going to click thanks on your post now...)

---

### Post by Ralphie on 2008-06-16
I was having the same issue and it was fixed thanks to cor2y!
Hopefully there is a fix for this in the near future, so that compiz does not have to be disabled

---

### Post by daka on 2008-06-18
newbie here....  Exactly how does one disable compiz....

I tried "disable compiz" ... didn't work... what is the terminal line I need to enter?

Thanks

daka

---

### Post by imon9 on 2008-06-18
weldevis4,

ur kdenlive config file got screwed, that is why it crash when i start the program... go to ur home folder and look for the hiden config file for kdenlive (user .kde or something like that), delete it and start kdenlive, it will ask u to choose the video format...choosing the correct one will get kdenlive started again

---

