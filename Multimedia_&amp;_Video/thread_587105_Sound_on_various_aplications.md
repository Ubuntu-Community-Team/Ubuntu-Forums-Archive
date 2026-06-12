---
title: "Sound on various aplications"
date: 2007-10-22
forum: Multimedia &amp; Video
---

### Post by UpSignal on 2007-10-22
Hello, i'm a new user of ubuntu, and i'm having some troubles now. here:
    When i'm playing runescape (a browser-based game) i can't use my audio player (XMMS) to listen my mp3, because he says some other application might be blocking the soundcard. 
    Same goes to my IM client (emesene). if i'm playing runescape, emesene doesn't give sound notifications, the same as if i'm listening music on Xmms.
    So, basically: I can't get sounds from more than 1 spot.

now, my suspicious: Possible messed up sound mixer? Salsa mixer, i believe. i clicked on it (near the clock) and i was trying some options, moving some bars... trying to get my mic working on skype. The reallity is: i couldn't get my skype working, and now i can't listen audio from various locations. and worst: i don't remember how the mixer was at the beggining, and there aren't "default" buttons to push. I hope someone helps! thanks!

Some other info:
 
Sound Card: Creative audigy
OS: Ubuntu Gybson (7.10)

---

### Post by daemmon on 2007-10-22
i'm having the same problem and i haven't messed with any mixer - i just can't hear sound in two aplications at the same time

---

### Post by UpSignal on 2007-10-22
so, the problem must be with ubuntu. because i had no problems on windows :s

---

### Post by UpSignal on 2007-10-22
Ok, i've done a little more researche and i found out the following:
it's all about the OSS driver. 

I set my audio player to use "alsa" and my movie player to use "OSS", and i can hear both audio. so, the problem now is..... firefox must be using OSS for it's flash. how the heck can i change it to alsa.. so i can hear various stuff :s

---

### Post by daemmon on 2007-10-22
still, there should be no problem when all players use alsa; it worked on edgy eft

---

### Post by UpSignal on 2007-10-23
erm... i'm still waiting for an expert reply. anyone can help? i'm pretty sure i'm not the only one with ubuntu. and not the only one with this audio problem

---

### Post by mig5 on 2007-11-02
1. Goto a terminal and type 'sudo gedit /etc/firefox/firefoxrc' .
2. On the file that it opens look for the line FIREFOX_DSP=
3. If after the equals sign it says 'none' or anything else except 'aoss' then carry on with these instructions. If it already says 'aoss' then this isn't the solution to your problem
4. Close the text editor, without making any modifications yet.
5. Go back to the terminal and type 'sudo apt-get install alsa-oss' .
6. Once it has installed write 'sudo gedit /etc/firefox/firefoxrc' again.
7. Find the line 'FIREFOX_DSP=' and change it to FIREFOX_DSP='aoss' (keep the commas around the aoss bit).
8. Save the file and exit the text editor.
9. Close any firefoxes that you have open.
10. Next time you run firefox the new aoss driver wrapper will be used and you should be able to hear runescape and your music at the same time.

---

