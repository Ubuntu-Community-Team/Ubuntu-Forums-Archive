---
title: "True Grit: Unrippable!"
date: 2011-07-02
forum: Multimedia Software
---

### Post by bbbaldie on 2011-07-02
Something is going on with the latest True Grit movie. I've been able to convert *ANY* DVD to mp4 so i can watch it on my Android phone, as well as having a safe backup on my home network, but with True Grit (2010 version), handbrake either crashes, or times out. K3b no better. I've installed all of the latest ffmpeg and x264 codecs, and also installed vlc with its own decoding stuff. And libdvdcss is in place, obviously. Like I say, no probs with any DVD but this one.

The handbrake forum has a similar problem listed, but they pooh-pooh it with a "We handle software issues, not decoding issues." That's cool, apples/oranges and all of that.

So Ubuntu community, what say you about this thorny problem with this one DVD, presumably more coming?

---

### Post by handy on 2011-07-02
Firstly; its a tricky subject to discuss here due to the CoC.

Secondly; sometimes its easier to just go find a .torrent & move right along...

---

### Post by bbbaldie on 2011-07-02
Thanks for the reply from Oz! I hope to travel there before I pass from the scene...

It shouldn't be tricky. I'm making a backup of a movie I own, legal according to SCOTUS.

---

### Post by mc4man on 2011-07-02
If you can play it in vlc then you can probably use vlc to do a 'fast rip' of the main movie title to .mpg, Then encode that file as seen fit.
Can you play the movie in vlc?

---

### Post by handy on 2011-07-02
> **bbbaldie said:**
> 
Thanks for the reply from Oz! I hope to travel there before I pass from the scene... 

Cool, I hope you enjoy it. Plenty of variety of landscape & people, so if you land somewhere where you don't like it for whatever reason, just keep on moving, it will change.

> **bbbaldie said:**
> 
It shouldn't be tricky. I'm making a backup of a movie I own, legal according to SCOTUS.

Legal or not, a minority of DVDs have nasty copy protection which doesn't care whether you own it or not. ;)

---

### Post by SeijiSensei on 2011-07-02
Nor, to be persnickety, do you have the rights you claim.  If you think you have to right to make a backup copy of a DVD because of the Court's [decision]("http://www.law.cornell.edu/copyright/cases/464_US_417.htm") in the Sony "Betamax" case, you're wrong.  Stevens wrote a very circumscribed decision that applies only to "the home recording for home use of television programs broadcast free over the airwaves. No issue is raised concerning cable or pay television, or the sharing or trading of tapes." (fn.2)  

Making backups of copy-protected DVDs clearly does not fall under this scope of this decision.

---

### Post by mc4man on 2011-07-02
I can see this thread is headed nowhere good..

bbbaldie - 
it's likely vlc or any player using libdvdnav4 will have some trouble playing back this title
I happen to continue to use totem-xine which has no issue (uses it's own version of dvdnav

You may have some luck with this command for playback as long as vlc is correctly set to your drive's /dev
```
vlc dvd://@18
```
This will start the movie directly and bypass all the S.P. nonsense

As mentioned before, adjusting blue to match your particulars and assuming the main movie title is title 18

```
vlc dvdsimple://@18 --sout '#duplicate{dst=std{access=file,mux=ps,dst=[COLOR="Blue"]/home/doug/Videos/test[/COLOR].mpg}}'

```
took about 9 min.'s here

---

### Post by FakeOutdoorsman on 2011-07-02
Another interesting article by andrew.46 might be useful here (or at least an interesting read if the disc continues to give you the Troubles).

[FFmpeg and 'Fist of Fury'](http://www.andrews-corner.org/): Backing up a great martial arts movie using FFmpeg and host of other quality Linux programs.

---

### Post by bbbaldie on 2011-07-02
Thanks to all. I'll try the advice when i have a bit more time. Ubuntu forever! :)

---

### Post by GWBouge on 2011-07-13
I might be a bit late on this one, but I was having the same issue with the same movie, and found out it works great if you use HandBrakeCLI and point it to the right title track, such as mc4man suggested with VLC.  I actually used his suggestion to figure out what track I needed.  Here's the command I used (obviously, change the codecs and format to suit your needs):

```
HandBrakeCLI -i '/media/TRUE_GRIT/VIDEO_TS' -o '/path/to/True Grit.mkv' -e x264 -E ac3 -B 320 -D 2.0 -S 1723 -t 4
```

That goes straight to track 4, puts the video in x264, audio in ac3 @ 320kbps with a slight DRC (2.0, so the loud parts don't wake up the neighbors, but you still get some of the effect), and a target size at 1723MB (I tend to go about 1GB per hour for DVD's).  More info here:

[https://trac.handbrake.fr/wiki/CLIGuide]("https://trac.handbrake.fr/wiki/CLIGuide")

---

### Post by handy on 2011-07-14
I ripped it with HandBrakeCLi too. I usually use the following:

```
alias hb="echo HandBrakeCLI -t 0 -i /media/dvd -o NAME.HERE.mp4 -e x264 -b 1000 -B 192 -1 --subtitle-burn" 
```

After which I can read through just how the DVD is put together & select which part(s) of it I want to backup.

---

### Post by thomas.clark on 2011-07-14
Got it to work in the HandBrake GUI, by setting it to the correct title.

File > Open Source (Title Specific) > Navigate to DVD > Select TS folder > Enter Title # of Movie when prompted [18 on mine]

The second step, Open Source (Title Specific), is important as Handbrake errors and quits otherwise.  I understand this error has been fixed in a recent build of Handbrake.

Then set up the options as desired, and go.

---

### Post by JohnAStebbins on 2011-07-17
The latest nightly builds of HandBrake has fixed the crash associated with True Grit.

[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

---

### Post by handy on 2011-07-18
**@JohnAStebbins:** By the way John, a HandBrakeCLI-svn came through last night. So I am obviously still receiving them, but they certainly aren't coming through very often on Arch at least? 

Not that, that is a concern to me, just saying...

---

