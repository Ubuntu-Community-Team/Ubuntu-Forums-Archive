---
title: "Mythbuntu 10.04: insert DVD, mythfrontend crashes"
date: 2010-12-05
forum: Mythbuntu
---

### Post by wayover13 on 2010-12-05
This refers to a Mythbuntu system that's been upgraded since 8.04. So it's been in operation for quite some time and has, for the most part, worked really well. No big hardware changes--just added a bit of RAM over the years and upgraded the CPU.

Anyhooz, I upgraded recently to 10.04 and things seemed fine for the most part. But then, last night I went to transdcode a DVD and, much to my dismay, as soon as the DVD mounted, mythfrontend crashed. I could not get mythfrontend to run again until I unmounted the DVD. I tried this several times, and it was evident that mythfrontend was not going to run any time a DVD was mounted.

I also tried rebooting the system, being interested in seeing what would happen if the DVD was mounted during the boot-up process. No change there: mythfrontend would not run with the DVD mounted. When I was dumped back at the xfce desktop, by the way, I was able to watch the DVD using VLC.

So what in tarnation is goin on here? I've watched and transcoded many DVD's on this machine and never had much problem. What changed in 10.04 that made this problem crop up? Any tips on diagnosing and fixing it?

Thanks,
James

---

### Post by thatguruguy on 2010-12-05
Are you running mythtv .23 or .24?

The software to rip DVDs was buggy, which prompted the removal of it from .24.  If you have .23, I suggest making sure that "Monitor CD/DVD is NOT checked in your frontend general setup.  At least on my mythbox, it caused crashes like you're having.  You'll still be able to watch DVDs by choosing "Optical Disks" from the main frontend menu.

As already mentioned, you can't rip DVDs directly in myth .24.  I suggest using handbrake for ripping DVDs.

---

### Post by wayover13 on 2010-12-05
Thanks for your reply, thatguruguy. I don't know which version 10.04 shipped with, but whichever version that was is the one I've got: I didn't compile any other one or get one from CVS or anything like that. I didn't find any obvious way to check the version (e.g., something like "mythtv --version") so it'll remain a mystery for the time being.

I understand you to be saying that, in addition to watching a DVD, if I've got .23, I can still transcode a DVD to my mythbuntu machine's HD--correct? But that, if I've got .24 I can only watch, but not transcode a DVD. Please let me know whether I've understood correctly.

Now, on handbrake. I've used both it and ffmpeg to transcode DVD's on another of my machines, so I know how to do that on said machine. But are you suggesting installing handbrake on mythbuntu and somehow using it to transcode on my myth machine? Or do you speak of transcoding the DVD on some other machine, then copying the transcoded file over to mythbuntu?

Myth seems to be losing functionality as time goes by. First it was loss of mythstream, now it's loss of the DVD-transcoding feature.

James

---

### Post by wayover13 on 2010-12-06
0.23.0+fixes24158-0ubuntu2 is the mythtv version that comes stock with 10.04, btw (found using apt-cache showpkg mythtv).

James

---

