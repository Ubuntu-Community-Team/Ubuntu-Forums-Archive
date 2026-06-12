---
title: "Why isn't there a GUI Audio Ripper that just works?"
date: 2010-11-10
forum: Multimedia Software
---

### Post by GuiGuy on 2010-11-10
All I'd like to reliably do is rip a few audio CDs. 

SoundKonverter - doesn't work at all. Log tells me nothing

SoundJuicer - OK for one disk. Usually crashes when the read disk is ejected and attempts are made to read the next. Failing that, it will read a few tracks and then lock up.

K3B - Only rips first disk, then the progress window (form) locks up at 100%. Cancel button doesn't work. Need to kill task. 

RipOff - works OK, but sooooo sllllooowwwww... life's too short

goobox - locks up before it even reads the disk and despite its claims I don't think it's a "rip" tool anyway. 

So, I'm back to the hated shell using ripit, unless someone has another suggestion?

Cheers

---

### Post by pastalavista on 2010-11-10
Have you tried Asunder? It's in the repositories (Software Center) and it works fine for me.

---

### Post by cchhrriiss121212 on 2010-11-10
Or ripperx.

---

### Post by mcduck on 2010-11-10
All the tools you mentioned are commonly used and reliable. Are you *absolutely sure* your problem isn't, for example, with your CD drive?

Perhaps try following the system logs when you are ripping a CD to see if you get any I/O errors or stuff like that.

---

### Post by cascade9 on 2010-11-10
I havent had any issues with rubyripper. That and EAC (windows) are the only rippers I use these days.

---

### Post by Steeperton on 2010-11-10
I use grip still... It's not in the repos, but you can easily find a deb. Easily the best ripper I've ever used, hence still using it even though it's depreciated.

Edit: ppa available: [https://launchpad.net/~futurepilot/+archive/ppa](https://launchpad.net/~futurepilot/+archive/ppa)

---

### Post by Grenage on 2010-11-10
I've never had a problem with Soundjuicer; last time I used it, I ripped about 20 discs in a row.  Now I'm using rubyripper.

---

### Post by I'mGeorge on 2010-11-10
I've didn't ripped an audio CD for a long long time but I believe K3b has an option for ripping and encoding audio tracks.

---

### Post by GuiGuy on 2010-11-10
> **mcduck said:**
> All the tools you mentioned are commonly used and reliable. Are you *absolutely sure* your problem isn't, for example, with your CD drive?

<sigh>... please believe me; those (obvious) items have already been eliminated. In any case, ripit works fine. I just find the shell tedious.

---

### Post by GuiGuy on 2010-11-10
> **I'mGeorge said:**
> I've didn't ripped an audio CD for a long long time but I believe K3b has an option for ripping and encoding audio tracks.

Correct, but as I wrote, the modal progress window cannot be closed when the rip finish, meaning the k3b task needs to be killed and k3b restarted.

---

### Post by GuiGuy on 2010-11-10
Thanks guys, and apologies, I had to vent. I needed to rip 20 audio CDs and it was a real PITA under linux. I gave up after number 5 disk and used CDEX for the rest on a windows machine. 

Some things windows just does so much better, 

Cheers

---

### Post by dr_duck on 2010-11-10
Audex is a nice qt4 ripper - I have never had an issue with it.  Not sure if it is in the usual repos though?

---

### Post by GuiGuy on 2010-11-10
> **dr_duck said:**
> Audex is a nice qt4 ripper - I have never had an issue with it.  Not sure if it is in the usual repos though?

Thanks. I'll check it out.

---

### Post by friTTe81 on 2010-11-10
+1 for Rubyripper, works really good

---

### Post by GuiGuy on 2010-11-11
I was pleased to see that CDEX runs OK in WINE. CDEX in my experience has always been faster than any other audio ripper I've tried and under WINE it certainly performs better than any linux option I've come across. 

At least I don't have to find a Windows PC now. 

Cheers

---

### Post by cascade9 on 2010-11-12
I agree with McDuck. I dont know whats going on, but your got some issue for sure, those tools are used by tons of people with no problems. 

> **GuiGuy said:**
> I was pleased to see that CDEX runs OK in WINE. CDEX in my experience has always been faster than any other audio ripper I've tried and under WINE it certainly performs better than any linux option I've come across. 

At least I don't have to find a Windows PC now. 

Cheers

You like fast rippers? Rubyripper wont do it for you, its not quick at all (and if you do a decent 2-pass rip then its even slower). I prefer slow and accurate, rip it once, get it right and never worry about errors.

---

### Post by VanillaMozilla on 2010-11-12
SoundJuicer crashes if a track is not found in an Internet database (in other words, it mainly works only for questionable or illegal use, if you do NOT own the content).  This has been fixed, but I don't know if the fix has made it to the desktop yet.

K3b works fine for me, even for multiple disks.

I strongly suspect that the problem is with your CD drive, or possibly elsewhere in your system.

---

### Post by GuiGuy on 2010-11-12
> **VanillaMozilla said:**
> 
I strongly suspect that the problem is with your CD drive, or possibly elsewhere in your system.

No. I can duplicate the issues across three linux machines I have access to. As I said earlier, I had eliminated the obvious before my OP. 

Anyway, I'm happy enough to use CDEX running in WINE.

---

### Post by I'mGeorge on 2010-11-13
About that K3b problem, check if you also have installed sox and normalize-audio and give it a try again ripping using k3b.

---

### Post by GuiGuy on 2010-11-13
> **I'mGeorge said:**
> About that K3b problem, check if you also have installed sox and normalize-audio and give it a try again ripping using k3b.

Yea, they've been installed and are functional. 

It's a shame that the K3B logs don't give any clues, but I suppose that has to do with the progress window becoming unresponsive when the first rip finishes.

NB: for the benefit of my critics, google confirms I'm not alone with the [K3B ripping problem]("https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/576500").

---

### Post by VanillaMozilla on 2010-11-15
I assume you have filed bug reports, then?  Just checking.

If bug 576500 is what you experienced, then you probably noticed that it's fixed? -- although you'll have to compile it yourself.

---

### Post by Lawrence Talbot on 2011-05-28
I use RipperX and it works fine for me.  You might also fork out about $12.00 and buy Nero Linux, it works great.

---

