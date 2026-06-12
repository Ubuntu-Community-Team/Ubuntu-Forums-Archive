---
title: "From Ubuntu to Xubuntu, root to user, pulseaudio to no pulse, sound freezes system!"
date: 2008-12-30
forum: Multimedia Software
---

### Post by abben on 2008-12-30
Hey all, I have been wasting my whole xmass break banging my head over this, and so it would really make my vacation if anyone can help me solve the problem, or give me some clues. 

My sound related issue is not that I don't get sound, I do. Nor is it a problem with any particular program, because it happens across all programs trying to play sound. If I play a video, or a song (or use some flash-based site that has sound, like youtube), I will get anywhere from 5 seconds to 10 minutes of crisp, beautiful audio, no problems. 

But then, the whole system utterly freezes. Sound stops, the mouse freezes, no graphical responsiveness of any kind. Windows stay open, a half-loaded webpage will stay half-loaded, everything freezes. And, as though from a scene in The Ring, my little red cpu light is on, unflickering, as symbolic confirmation of the worst. The red light remains on despite everything being frozen, until I force restart.

My sound hardware is not automatically detected during the ubuntu install, so I manually add my alsa-supported driver:
```
sudo modprobe snd-sb16 (just to hear things)
sudo nano /etc/modules (add snd-sb16 as the last line)
sudo adduser abben audio
sudo adduser abben pulse (if necessary)
sudo alsactl store 0
```

Other clues
- This happened in Xubuntu (intrepid) on multiple installs, and Ubuntu (intrepid) which I am currently using
- It has happened with or without pulseaudio
- Not specific to any program or file format (avi, mp3, flash)
- I have a fairly old 800 mhz machine, 256mb ram
- Sound worked perfectly fine on older versions of ubuntu/xubuntu (I think 6.04, 6.10)
- I always install (x)ubuntu-restricted-extras before playing anything
- I'm suspicious that "sudo alsactl store 0" might be a part of the problem. I'm not quite sure I should be using it, and I never needed to on older versions of ubuntu.

I have spent lots of time tweaking with things, reinstalling alsa, adding/removing pulseaudio or esound, making sure everything is updated. I've googled all the word combinations I could think of that relate to this.

Has anyone heard of this happening before? Or can you think of something I haven't yet tried? If it looks like I've done alot, I should point out that all I've really done is look for simple fixes that involve reinstalling packages or a couple lines of terminal commands, but my exploration of *those* kinds of fixes has been fairly exhaustive and has thus far turned up no solution. 

Is there something more I should understand about alsa drivers? Should I just revert to an old version of Ubuntu?

Thanks for any help.

---

### Post by wolfen69 on 2008-12-30
does this happen in hardy too? i think you have to find what works and go with it, be it ubuntu, debian, fedora, open suse, etc. some distros will just not work correctly on certain hardware. the days of me spending hours trying to fix nagging problems are over. your time is better spent trying to find a distro that works. sorry i can't be of more help. personally, i would try [Tinyflux]("http://pcfluxboxos.wikidot.com/tinyflux") on a machine with low specs like yours. newer distros are not always the best for older hardware. [Mepis Antix]("http://antix.mepis.org/index.php/Main_Page") is another one to consider. like ubuntu, it is based on debian. both distros i've mentioned come with all codecs preinstalled and are easy to use. don't be stubborn, be smart. otherwise you can drive yourself crazy by limiting your options. it's all linux afterall. good luck.

---

### Post by abben on 2008-12-30
> **wolfen69 said:**
> does this happen in hardy too? i think you have to find what works and go with it, be it ubuntu, debian, fedora, open suse, etc. some distros will just not work correctly on certain hardware. the days of me spending hours trying to fix nagging problems are over. your time is better spent trying to find a distro that works. 

Thanks, and that is to an extent my thought. But, I've been using Ubuntu to a while and it's been working fine, and right now, everything besides sound, is doing awesome. As I said...

> - Sound worked perfectly fine on older versions of ubuntu/xubuntu (I think 6.04, 6.10)

I don't specifically know about Hardy. But this problem is most certainly recent. 

If anyone else has heard about this problem, or has a guess as to how it may be fixed, I'd appreciate it.

---

### Post by wolfen69 on 2008-12-31
> I don't specifically know about Hardy. But this problem is most certainly recent. 



i'll give your thread a bump here. if you've never tried hardy, i suggest you do so. in 2 days Hardy 8.04.2 is going to be released with all updates included and support for new hardware. it is the long term support version which may be better suited for your hardware. it can't hurt to try the live cd anyway.

---

### Post by abben on 2008-12-31
Shameless bump, in case anyone can help. Something about sending my cpu to 100%, I think?

---

### Post by markbuntu on 2008-12-31
You really need more ram.

---

### Post by abben on 2009-01-01
> **markbuntu said:**
> You really need more ram.

If I had money, I would buy more ram. Or a new soundcard recognized by alsa. Or both. Or a new laptop, perhaps with windows vista on it.

---

### Post by markbuntu on 2009-01-01
Ubuntu requires a lot of resources. You should really try a more lightweight distro because 256mb ram is not enough for Intrepid.

---

### Post by abben on 2009-01-02
> **markbuntu said:**
> Ubuntu requires a lot of resources. You should really try a more lightweight distro because 256mb ram is not enough for Intrepid.

You mean like Xubuntu, which doesn't require more than 256 mb of ram, which I've been using almost exclusively up until having this problem? I only tried installing Ubuntu about a week ago to see if I could get sound working on it. In any case it's not particularly relevant to the sound drivers issue.

---

