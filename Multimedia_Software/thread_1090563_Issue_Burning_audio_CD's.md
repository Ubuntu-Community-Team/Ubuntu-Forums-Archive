---
title: "Issue Burning audio CD's"
date: 2009-03-08
forum: Multimedia Software
---

### Post by residualbit on 2009-03-08
I'm not sure if this is hardware or software related, and to be honest I haven't really gotten that deep into yet. I just wanted to see if anyone had a similar problem before I wasted a bunch of time figuring it out.

Anyway, lately when I try to burn an audio cd with brasero or k3b, it burns a cd that is not compatible with any cd players. A few days ago it was burning cd's just fine and now its not. I haven't changed anything.

When I put one of the "successfully burned" cd's back in the drive, it shows up as a blank cd. When I view the properties it says volume and free space are unknown.

Neither brasero or k3b are throwing any errors.

---

### Post by residualbit on 2009-03-08
The files i am burning are just regular mp3's. Like i said, I haven't had any problems before and I haven't changed anything.

As a test. I tried to burn a cd that I successfully burned a few days ago. Now it isn't working.

---

### Post by andrew.46 on 2009-03-09
Hi,

I don't use either of the burning programs that you mention but I do know that mp3s should be burned to cd as data files, not audio files. Perhaps this would be worth a try?

Andrew

---

### Post by residualbit on 2009-03-09
First of all, which program do you use?

Secondly, I think brasero transcodes the mp3 files (to wav) on the fly as part of the burning process...right?

---

### Post by wolfen69 on 2009-03-09
to get k3b to burn mp3's onto a cd that will play in a regular cd player, you will need the **libk3b2-extracodecs** package. (in synaptic) then choose burn as audio cd.

---

### Post by andrew.46 on 2009-03-09
Hi nkirk1,

> **nkirk1 said:**
> First of all, which program do you use?

I use cdrdao for audio cds and the *real* cdrecord for data cds. But I suspect I am in the minority there :-).

Andrew

---

### Post by residualbit on 2009-03-12
ok so i have kind of tracked this issue down a little bit, but I have no idea what is causing it...brasero transcodes mp3 files as part of the burning process, and i have k3b with libk3b2-extracodecs installed. both go through the entire burning process without showing any error (shows write speed and everything.) I take it to my cd player and the cd doesn't work so I had the bright idea to put it back in my comp and it recognizes it as a blank cd...even lets me "burn" to it again...

also, the hardware works, i am able to burn data cds fine...anyone know what is going on?

---

### Post by bluester on 2009-04-16
I have Ubuntu 8.10, Brasero 0.9.1 with libbrasero-media0_0.9.1-1~getdeb3_i386; (both from [http://www.getdeb.net/release/3759](http://www.getdeb.net/release/3759))
I run into the same issue as the op.
I attempted to burn a few mp3's to a blank CD-R and Brasero begins to Transcode the files, afterwhich, the program states it burned successfully, ejects the cd - without writing the data to the disk.

I noticed a few things:

1. The amount of audio available to burn on the CD states 1 hr and 10 minutes.
2. The mp3's selected equated to an estimated 1 hr and 5 minutes of audio.

When I reduced the mp3's on the cd - resulting in an estimated 1hr and 2 minutes of audio, a successful audio cd was burned with 659 MiB burned to disk!

I believe the process of transcoding an mp3's to an traditional audio CD
may be a bit off. The 'estimated' audio to be burned appears to be slightly off;

The questions:

1. Why does Brasero 'not' give you a traditional error - "Not enough room on disc?"
2. Are there more accurate underlying programs to better estimate projected audio to disc size?
3. Am I missing something or way off here?

---

