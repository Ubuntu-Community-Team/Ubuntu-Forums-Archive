---
title: "Poor HD MKV playback within Myth, fine outside"
date: 2011-03-13
forum: Mythbuntu
---

### Post by geekyhawkes on 2011-03-13
hi all;

so i have a few Bluray rips on my mythbox and have the problem of pixcelation during playback if i open the file from myth.  If i exit myth and load the mkv from vlc then it plays fine, likewise if i open a terminal and type mplayer -fs filmname.mkv it plays fine. 

Because the files work fine outside of myth, and on other pcs i know its not source data or the machines hardware that is the problem, what i dont know is why the pixcelation occurs and how to best fix it?

I have run top during playback in myth and just from mplayer in the terminal and to be honest the difference is minimal with both cpu readings not going over 50% and spending most of the time mid 30s.

One thing i was wondering is codec myth would use with mplayer for the mkv file?  

Any thoughts on this would be welcome, very low WAF/cool factor having to quit myth to watch HD films at the moment!

Thanks

---

### Post by newlinux on 2011-03-13
try adjusting your playback profile. Which one are you using now? Cycle through the presets (I'd try CPU++ to start, then maybe normal and high quality) as a start and hopefully you won't need to create a custom one.

---

### Post by nickrout on 2011-03-13
> **geekyhawkes said:**
> hi all;

so i have a few Bluray rips on my mythbox and have the problem of pixcelation during playback if i open the file from myth.  If i exit myth and load the mkv from vlc then it plays fine, likewise if i open a terminal and type mplayer -fs filmname.mkv it plays fine. 

Because the files work fine outside of myth, and on other pcs i know its not source data or the machines hardware that is the problem, what i dont know is why the pixcelation occurs and how to best fix it?

I have run top during playback in myth and just from mplayer in the terminal and to be honest the difference is minimal with both cpu readings not going over 50% and spending most of the time mid 30s.

One thing i was wondering is codec myth would use with mplayer for the mkv file?  

Any thoughts on this would be welcome, very low WAF/cool factor having to quit myth to watch HD films at the moment!

Thanks

Are you using vdpau? If so try adjusting upwards the vdpaubuffersize - see the wiki for details.

---

### Post by geekyhawkes on 2011-03-14
Im not using vdpau as I had lots of pixcelation during tv playback under the vdpau playback options.  I have been using CPU ++ but I didnt realise these also effected how mplayer runs under myth. 

Is there a way i can run one profile under mythvideo and one for mythlivetv?  Im really happy with CPU++ for livetv.

Thanks

---

### Post by newlinux on 2011-03-14
> **geekyhawkes said:**
> Im not using vdpau as I had lots of pixcelation during tv playback under the vdpau playback options.  I have been using CPU ++ but I didnt realise these also effected how mplayer runs under myth. 

Is there a way i can run one profile under mythvideo and one for mythlivetv?  Im really happy with CPU++ for livetv.

Thanks

No the playback profiles don't affect mplayer. Are you using the internal player or mplayer or a combination for mythvideo? The default for mythvideo in later releases of mythtv is the Internal player (the same player as livetv and recordings). I suspect you are using the internal player if using mplayer outside of mythtv results in a different outcome.

---

### Post by nickrout on 2011-03-14
> **geekyhawkes said:**
> Im not using vdpau as I had lots of pixcelation during tv playback under the vdpau playback options.  I have been using CPU ++ but I didnt realise these also effected how mplayer runs under myth. 


it doesn't affect mplayer> 
Is there a way i can run one profile under mythvideo and one for mythlivetv?  Im really happy with CPU++ for livetv.

Thanks

No there isn't, without going into the settings and changing it (and possibly restarting the frontend?). If you have a vdpau capable machine, use vdpau and troubleshoot the options. As I say, I found vdpaubuffersize the most important one. See the wiki.

---

### Post by newlinux on 2011-03-14
Oh and your playback profile can do different things based on resulotion, but not mythvideo vs recordings/livetv. You'll have to manually switch them. I ran into a problem where VPDAU works great for some types of recordings, but not so well with recordings with artifacts (from a different source - the signal isn't that great) and I created a script that modifies the database to change the playback profile, and then mapped it to a button using irexec and LIRC and now I can toggle the playback profiles with a button on my remote...

---

