---
title: "No sound on YouTube"
date: 2006-11-17
forum: Multimedia &amp; Video
---

### Post by Halfling Rogue on 2006-11-17
I'm running Ubuntu 5.04, have the newest version of Flash installed, Firefox 2.0, and am operating on an IBM Thinkpad. When I try to view a YouTube video, I get visuals just fine, but there's no sound. Any thoughts on why this is happening or how I can fix it?

Although I'm also missing some mp3 plugins, apparently, since my music player tells me it can't play mp3s. I unfortunately haven't been able to find these plugins; still, could that be the reason why YouTube isn't working?

**ETA:** Right, and I know sound is working on my system, because when I'm working on the desktop or starting up/shutting down I get sound effects. And I can play music CDs. Just no mp3s or YouTube.

**ETA2:** Mp3s now working. YouTube still not.

---

### Post by noobuntoo on 2006-11-17
my advice would be to open up your synaptic package manager and install the gstreamer plugins and lame plugins (liblame0 i think?). Also, download automatix ([http://www.getautomatix.com](http://www.getautomatix.com)) and use it to get w32codecs and all the other multimedia codecs installed.

---

### Post by Halfling Rogue on 2006-11-17
Hm, it says I've already got gstream 0.8 installed, and it can't find liblame. I'll give automatix a shot, though. Thanks.

---

### Post by Halfling Rogue on 2006-11-17
> **noobuntoo said:**
> my advice would be to open up your synaptic package manager and install the gstreamer plugins and lame plugins (liblame0 i think?). Also, download automatix ([http://www.getautomatix.com](http://www.getautomatix.com)) and use it to get w32codecs and all the other multimedia codecs installed.

Actually, wait, I just went to automatix and they've only got it for Dapper; I'm running Hoary. If I download it will it screw up my system?

---

### Post by noobuntoo on 2006-11-18
> **Halfling Rogue said:**
> Actually, wait, I just went to automatix and they've only got it for Dapper; I'm running Hoary. If I download it will it screw up my system?

hmm forgot about that. Yeah, downloading a different version won't do you any good. You should consider upgrading your ubuntu version though. I started out with 6.06 and no sound, upgraded to 6.10 and suddenly it had sound for everything except youtube. Installed codecs and messed around with the config for my sound card and then i got sound on youtube too.

Also, check out this page [http://ubuntuguide.org/wiki/Ubuntu](http://ubuntuguide.org/wiki/Ubuntu)
I dont see a section for your version but they have one for 5.10 and most of the terminal commands will work for any version.

---

### Post by Halfling Rogue on 2006-11-18
> **noobuntoo said:**
> hmm forgot about that. Yeah, downloading a different version won't do you any good. You should consider upgrading your ubuntu version though. I started out with 6.06 and no sound, upgraded to 6.10 and suddenly it had sound for everything except youtube. Installed codecs and messed around with the config for my sound card and then i got sound on youtube too.

Also, check out this page [http://ubuntuguide.org/wiki/Ubuntu](http://ubuntuguide.org/wiki/Ubuntu)
I dont see a section for your version but they have one for 5.10 and most of the terminal commands will work for any version.


Aw man, 6.06 has the same problem?! That's the one I was planning to upgrade to soon as I got the CDs. :(

Thanks for the link, I'll check it out and see if I can dig up some compatible codecs. *crosses fingers*

---

### Post by little dave on 2006-11-18
> **Halfling Rogue said:**
> Aw man, 6.06 has the same problem?! That's the one I was planning to upgrade to soon as I got the CDs. :(

Thanks for the link, I'll check it out and see if I can dig up some compatible codecs. *crosses fingers*



 Look here.[http://http://www.kismetwireless.net/blog/]("http://www.kismetwireless.net/blog/")

---

### Post by saskboy on 2006-11-18
I run 6.06.1, and have had my sound stop working at times, where it works at first, then a program like skype will crash, and the sound goes with it. Mind you, I've also had YouTube sound in Windows Firefox 2.0 go out on me. I had to close some old YouTube tabs, and it would start working again. -so it could be a Flash bug.

---

### Post by Halfling Rogue on 2006-11-18
> **saskboy said:**
> I run 6.06.1, and have had my sound stop working at times, where it works at first, then a program like skype will crash, and the sound goes with it. Mind you, I've also had YouTube sound in Windows Firefox 2.0 go out on me. I had to close some old YouTube tabs, and it would start working again. -so it could be a Flash bug.

I wouldn't be surprised if it was a bug. I remember having this problem on one of our old Windows systems, but I can't remember how we fixed it. Plus having mp3 players open can conflict with priority for the sound card, but even when I have nothing open it won't play. So maybe it just doesn't like my Firefox or something. I'll keep trying.

---

### Post by partriv on 2006-11-18
to be honest kind of just browsed this thread, but you could try closing everything that might use sound, then open just firefox, and try going to youtube after that.

---

### Post by Halfling Rogue on 2006-11-18
> **partriv said:**
> to be honest kind of just browsed this thread, but you could try closing everything that might use sound, then open just firefox, and try going to youtube after that.

Tried it, no go. :neutral:

---

### Post by Choad on 2006-11-18
install the flashplayer 9 beta

its very easy, just copy the new flash binary blob to ~/.mozilla/plugins/

---

### Post by Halfling Rogue on 2006-11-18
> **Choad said:**
> install the flashplayer 9 beta

its very easy, just copy the new flash binary blob to ~/.mozilla/plugins/

Binary blob? Where can I get this?

---

