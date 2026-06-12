---
title: "OGMrip"
date: 2009-10-23
forum: Multimedia Software
---

### Post by eaglemob on 2009-10-23
Hi all,
In first place i want to say loud I LOVE UBUNTU 9.10.
I am not using windows for a month now.


I have been trying to encode my dvd collection to my usb 32Gig and HD.
Why i do that ?, it is to not stand up and change dvd's on my dvd player connected to the tv when i am watching.  lazy i guess :)

Well so far so good. I rip them with Ogmrip to the hard disk without any sub titles.
After it i use the option profile :divx for standalone player (700MB).

On the MKV file after ripping it's like 3,9 gig and no sub titles when i play it.
When i go to faze 2 and encode that to 700MB size, all goes smooth and perfect.

But when i watch the 700MB encoded file, all is good, the sound, the video.
Just one thing is wrong!!!!  Appears the the text in english wen some one talks, and i didn't rip any languages :( I guess is for ppl who can not hear.

How come that the subs comes, i didn't choose any subs ?

Any help appreciated.
Many thx,

Tino E.

---

### Post by vinutux on 2009-10-23
Try Handbrake **[http://handbrake.fr/]("http://handbrake.fr/")**

---

### Post by eaglemob on 2009-10-24
Thanks for the tip.

But Handbrake (svn2845 i686) does not support  Avi container.
And old dvd player can not read the new formats like matroska and so on.

[http://handbrake.fr/pastebin/pastebin.php?show=908](http://handbrake.fr/pastebin/pastebin.php?show=908)

---

### Post by vinutux on 2009-10-24
Try hand brake from **[getdeb.net]("http://www.getdeb.net/app/HandBrake")** it supported avi,mp4,ogm containers and x264,xvid,ffmpeg encoders... 

[**http://www.getdeb.net/app/HandBrake**]("http://www.getdeb.net/app/HandBrake")

---

### Post by eaglemob on 2009-10-24
I hoop it will do what i want.
I  go try that Vinutux.

I try before to install Handbrake but the UI gives me an error, it does not comes up.
So that's why i installed the svn version that works with ubuntu 9.10.
Don't know if i can fix that version that you say, to work with my ubuntu.
Did tests with handbrake and it's really good and faster then all the others.
Matroska encoding to a 700MB file size, is good quality.

I hoop to get that version working on this :)

Thx again Vinutux. :)

---

### Post by eaglemob on 2009-10-24
:(
Doesn't work that version *handbrake-gtk_0.9.3-0getdeb1_i386.deb* on ubuntu 9.10.

Gives me an error:

Unable to create ghb.
Internal error, Could not parse Ui description.

Dono how to fix that, i am using ubuntu for just a month.

anyway thx :)

---

### Post by benmoran on 2009-10-24
Thats a really strange problem you're having with OGMrip. I've been using it for over a year and ripped a ton of my personal DVDs without issue. I generally use the MKV container with x264 and AAC or Vorbis. 

I would edit the profile in question, and make sure forced subs isn't selected. Or better yet, just make your own profile. Handbrake is nice, but I personally like OGMrip a lot better. 

Since you're new to Linux, also check out Avidemux for other random video editing needs. It's basically a better virtualdub.

---

### Post by eaglemob on 2009-10-24
Yea Benmoran,

Everything works on Ogmrip except that it comes the text in english when they talk.

I even edit the profiles and make it sure that is no subs selected.
I make it a test to see if i select other sub it will appear or hardcoded. and it works, the subs that i selected went hardcoded.

I really don't know.
About Avidemux it's a really good program aswell , but for my skills i think is a bit complicated.
So what i did with ogmrip was:
Rip without encode .. just copy.
i got a file 3,9gig  mkv format.. i played that in vlc.. no sub titles and was perfect.

So i ripped the same with the profile 1X700Mb (avi,xvid,mp3) , also no sub titles selected.
But when i played that 700mb file, the sub title appear..
Very strange.

The programs that i am using are:
Subtitle editor 0.30.0
dvdrip 0.98.10
avidemux 2.5.1
k9copy 2.3.3
Ogmrip 0.13.2
Handbrake =Not in use. It doesn't work on 9.10, unless i install the svn version.

Plz help on this !!! i don't wanna go back to windows :(

thx all for the replays, i try my best to fix this.

---

### Post by vinutux on 2009-10-24
R u using Karmic ?

Anyway here is PPA for handbrake **[https://launchpad.net/~handbrake-ubuntu/+archive/ppa]("https://launchpad.net/~handbrake-ubuntu/+archive/ppa")**

select your version add ppa sources...and add it to synaptic with Signing key

reload synaptic and install from synaptic......

---

### Post by eaglemob on 2009-10-24
Again, i told you. Handbrake does not work on 9.10 
Yes i am using karmic 9.10

The version that works is svn and that NOT suport avi.

I have no options left. is just have go to windows again :(

A simple thing, encode without subs with one program. That doesn't do 
I make it like 10-15 tests with NO sub titlles selected not even hardcoded.
the first pass rip *copy* as mkv is ok. wen i encode then is wrong the dammn sub titles comes.

sorry i give up on this, i lost many time now.

thx for the help..
PS: HANDBRAKE doesnt work on ubuntu 9.10 !!!

---

### Post by andied on 2009-10-24
use the svn version of handbrake-works great in Karmic

---

### Post by eaglemob on 2009-10-25
> **andied said:**
> use the svn version of handbrake-works great in Karmic
yes i know, but not supports AVI.

---

### Post by vinutux on 2009-10-25
> **eaglemob said:**
> yes i know, but not supports AVI.

Try cli version | Help here [http://trac.handbrake.fr/wiki/CLIGuide]("http://trac.handbrake.fr/wiki/CLIGuide")

---

### Post by eaglemob on 2009-10-25
> **vinutux said:**
> Try cli version | Help here [http://trac.handbrake.fr/wiki/CLIGuide](http://trac.handbrake.fr/wiki/CLIGuide)

Yea cool, that works. :).

I wonder if i could fix the ui, that would be great because i am not that terminal user.

Thx for the help Vinutux youre the best.
If you know how to fix the ui plz  post it :)

Cya arround.

---

### Post by vinutux on 2009-10-25
sorry i am not a programmer....:(. I think cli have many more powefull than gtk version of handbrake...........:

---

### Post by eaglemob on 2009-11-03
Yea you not a programmer , but exist many programmers.
I don't see why not a Handbrake that works on 9.10 with ui support.

So difficult must not be.!!?? PS.. also with AVI container support.
The ui Hanbrake that works on 9.10 is SVN version ..and ..and again.. don't support avi.

So plz ppl who have send me e-mails about SVN.. plz read first the previous messages on the forums.

In other words: we need handbrake on 9.10 with UI that supports AVI container.

Tnx all for the replays.

Keep me posted

---

### Post by ghostborg on 2009-11-04
OGMRIP 13.2 in Karmic is doing the same to my encodes.
I got my version through Synaptic.

Found this Bug report which seems to point to Mplayer as being the culprit.
[https://bugs.launchpad.net/ubuntu/+source/ogmrip/+bug/458129]("https://bugs.launchpad.net/ubuntu/+source/ogmrip/+bug/458129")

I add the PPA and imported the key, then ran update.
OMGRIP subtitle problem fixed.

[https://launchpad.net/~mdeslaur/+archive/ppa]("https://launchpad.net/~mdeslaur/+archive/ppa")

---

### Post by soapBAR2 on 2009-11-04
Handbrake does not work with the new GTK library.

OP: You can try acidrip, it's reasonably good although a little more complex than handbrake. K9Copy is also quite nice.

---

### Post by JohnAStebbins on 2009-11-04
There is a development snapshot of HandBrake for Karmic now.
[http://handbrake.fr/snapshot.php](http://handbrake.fr/snapshot.php)

Regarding handbrake avi output.  It's not coming back.  If you need to create avi files, HandBrake is not the tool for you. From the snapshot release announcement:
> 
As we've had on our roadmap for quite awhile now, one of our goals for version 0.9.4 is to refocus on HandBrake's key strengths and to remove dead weight. As part of this process, several presets, containers, and a codec have been removed from HandBrake.

* AVI: AVI is a rough beast. It is obsolete. It does not support modern container features like chapters, muxed-in subtitles, variable framerate video, or out of order frame display. Furthermore, HandBrake's AVI muxer is vanilla AVI 1.0 that doesn't even support large files. The code has not been actively maintained since 2005. Keeping it in the library while implementing new features means a very convoluted data pipeline, full of conditionals that make the code more difficult to read/maintain, and make output harder to predict. As such, it is now gone. It is not coming back, and good riddance.


---

### Post by shayguitarra on 2009-11-05
@eaglemob, I find dvd::rip ok for ripping avi files. Occasionally it comes across a title it won't rip but 90% of the time I don't have a problem. (This may be a problem specific to my dvd drive of course.)

I was using OGMrip quite happily in Jaunty. I upgraded to Karmic two days ago and I've ripped the same title 6 times before I realised it wasn't something I was doing wrong that was forcing the subtitles. Epic fail, as the young people say! :-D

---

### Post by shayguitarra on 2009-11-05
> **ghostborg said:**
> OGMRIP 13.2 in Karmic is doing the same to my encodes.
I got my version through Synaptic.

Found this Bug report which seems to point to Mplayer as being the culprit.
[https://bugs.launchpad.net/ubuntu/+source/ogmrip/+bug/458129]("https://bugs.launchpad.net/ubuntu/+source/ogmrip/+bug/458129")

I add the PPA and imported the key, then ran update.
OMGRIP subtitle problem fixed.

[https://launchpad.net/~mdeslaur/+archive/ppa]("https://launchpad.net/~mdeslaur/+archive/ppa")

Just tried that (launchpad was down for a while this morning) and the first file ripped perfectly with not a subtitle in sight.

---

### Post by eaglemob on 2009-11-05
Yea i tough the same....forcing the subtitles, but was not that the case.
Anyway since avi output container is not supported by handbrake.
From now on i will encode with mastroka container, better quality.

I got the last svn snapshot and it works good.
About the subtitles, i will have to use dvd::rip or anyother program.

Thx, for all the help.
Ps: here is the last snapshot for handbrake 
[http://handbrake.fr/snapshot.php](http://handbrake.fr/snapshot.php)

---

### Post by eaglemob on 2009-11-05
> **shayguitarra said:**
> Just tried that (launchpad was down for a while this morning) and the first file ripped perfectly with not a subtitle in sight.

yea thx mate !!:)

---

### Post by ghostborg on 2009-11-10
Here is a link to a PPA that has a repack of the Handbrake 0.9.3 version with XVID that works under 9.10 Karmic.

Marc Deslauriers

Expand the arrow for "Technical Details about this PPA" for more instructions at the following link.

[https://launchpad.net/~mdeslaur/+archive/ppa]("https://launchpad.net/~mdeslaur/+archive/ppa")

OGMrip , for me worked fine except when I FF in Windows 7 MCE the voices lose sync. The same movie encoded with Handbrake XVID when FF does not lose voice sync.
K9copy Xvid encode- I loved until I found some strange frame dropping anomalies with the same source Handbrake used with no problems. During an explosion scene K9copy practically skipped it all. I check the source and that was fine. Very strange, so I don't trust K9 at this time.

---

