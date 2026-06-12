---
title: "Proposal: 3d benchmark wiki project"
date: 2007-01-29
forum: Multimedia &amp; Video
---

### Post by bwhite82 on 2007-01-29
I have a dream.....
I have a dream that new (K)Ubuntu users can visit a wiki page and easily locate a small *range* of expected FPS for their video card+driver combination...
I have a dream to end the "benchmark problem" on Linux by referring everyone to a common set of easily available, free tools to reliably benchmark their video card...
I have a dream that users who have superior FPS gains with common cards, add links to the wiki page to a "howto" on how they achieved this...
I have a dream.....

Anyways, now that I got my MLK spiel out of the way, the tools I am referring to are:

-UT2004 Demo (Current version: 3334, 285mb)
-UMark (Current version: Beta3, 219kb **You will need Automake1.8 and libgtk2.0 + libgtk2.0-dev)

First, a little about these two excellent programs:
[B]
UT2004 Demo-[/B]

Unreal Tournament, basically since it's inception, has been a standard benchmark for gaming enthusiasts and the professional gaming world itself. Countless gaming magazines have utilized this program alone to write about benchmarks for the latest and greatest video card. It's FPS scores are universally accepted by just about every card-tweaker that you know. It rose to prominence in this arena for always being able to test the limits of the latest video cards. Although UT2k4 is now aging, it still retains this inherit ability.

**UMark **(As quoted from the webpage)-

"UMark is a free graphical user interface that allows gamers and hardware reviewers to easily configure and run benchmarks on Unreal® Tournament 200x (UT2003 and UT2004, both demo and retail versions). Benchmarking with UMark is very flexible, as it can run totally customizable benchmarks. At the same time, it also offers standard benchmarking which imitates the official UT200x benchmark batch file tests.

UMark supports three types of UT200x benchmarking: "botmatch","flyby", and "timedemo" benchmarks. Each benchmark type has its own upsides and downsides."

Basically, UMark is a frontend for the already-existing, built-in benchmark tests in UT2K3,2K4. So this program can reliably be used, and trusted, because it's simply providing a graphical frontend for UT's benchmark.

**Q&A:**

Q: "Where can I download these tools?"
A: [UT2004 Demo]("ftp.games.skynet.be/pub/misc/ut2004-lnx-demo3334.run")
    [UMark]("http://ut2k3botbench.sourceforge.net/index.php")

Q: "You really *are* dreaming, it is virtually impossible to reliably benchmark 3d acceleration   in Linux, simply too many variables at play."
A: I beg to differ. The definition of "benchmark":

benchmark

noun
1. 	a standard by which something can be measured or judged; "his painting sets the benchmark of quality" 

Basically *anything* can be used as a benchmark. My goal is to simply set some minor perameters, and point folks to a common set of utilities for achieving this. I understand that there will be fluctuations in scores, which is why I propose an FPS "range" for your video card, this range will be achieved by numerous UMark scores for the same video card.

Q: "Why these two programs? Why not any other like, glxgears or SPECViewPerf?"
A: Everyone should know by now that glxgears cannot be trusted as a measure of 3d acceleration performance, it is a tool that was designed with one purpose in mind: To allow a user to see whether he/she simply has rendering activated, nothing more. SPECViewPerf, while an excellent tool in it's own right, is not very user-friendly, do a little google research and you'll quickly see why. Ubuntu is all about user-friendliness, so that option is a NO-GO.

Q: "You just said that "anything" could be used as a benchmark, now you're telling me that these two utilities are a "NO-GO", what's up with that you know-nothing, Army punk?
A: For the reasons I listed in the above question.

Q: "Ok, I'll bite. How do I get started?"
A: Download and install the aforementioned programs, benchmark your card, and post the data here on this thread. The obvious data must be included: OS/Version, video card, driver/version, if you performed tweaks, etc, etc. (If you have recommendations on what data should be included in the wiki, please let me know. This is simply a proposal at this point.

Q: "This whole proposal is asinine, you should be drawn and quartered."
A: If you have nothing valuable to add to this discussion, then please don't post. I welcome opposition to the idea, but please back up your statements with relative information explaining why this is a bad idea.

Q: "Do you rly think you're the first to think of this? I have this already going on at my website: www.blahblah.com"
A: That may be, all I know is that I'm a fairly new Ubuntu user, and I could not find any benchmark results with *Linux* programs to compare my own card with. So if you DO have something like this already started, it's not widely known and hence not very accessible.

[B]Disclaimer: This is being proposed with the idea to provide Ubuntu users a *reference point* for the performance of their particular video card. This is not a "contest" to see who can achieve the most FPS. Although it is encouraged to test the limits of your hardware by tweaking, it is implied that you also provide documentation on how you went about doing so. Either way, if you tweak your hardware as much as you can, and achieve a really high score, then your number would simply be the "high" number in the range that will be in the wiki, thus, telling users that, "this particular card is *capable* of achieving scores as high as this."
[/B]

---

### Post by bwhite82 on 2007-01-30
**System Specs:**

Dell E1505, Centrino Core Duo proc 1.8ghz, _ATI Mobility X1400_
Ubuntu 6.10 Edgy Eft, _ATI Proprietary driver v. 8.32.5_
No Tweaks

**UMark Scores:**

Map       /        Bots / Detail / Resolution /  Min. FPS  / AVG FPS  / Max FPS   Score

AS-Convoy   /   12  /  High /  1024x768 /   17.1244 /  41.8907 /  98.8474 /  41.8383
ONS-Primeval /  12  /  High /  1024x768 /   6.3528  /   45.8251 /  78.3581 /  45.8523

---

### Post by lingnoi on 2007-02-07
Does anyone know of a GNU/GPL project to replace 3DMark ?

---

### Post by TuxCrafter on 2007-03-09
I am looking for a good GPL 3D benchmark tool? That can be executed and run from a X enabled terminial.

---

### Post by staeryatz on 2007-04-06
Wow! People still use my program? Maybe I'll make a UMark for UT3 when it comes out later this year. Maybe...

-Jeffrey Bakker

---

### Post by Farenheit on 2007-12-02
I've just started playing with Ubuntu for the past month, and have finally gotten my system to a point where it's stable enough to run 3D (giving my Vista install a run for it's money).  I hope one day this modern benchmark utility comes to pass, as I really would like to see how my rig stands up against others.  3DMark for Windows is a joke...who ever heard of paying for something that serves no other purpose besides benchmarking your system (and shoving ads in your face).  I suppose we'll see what we'll see.

---

