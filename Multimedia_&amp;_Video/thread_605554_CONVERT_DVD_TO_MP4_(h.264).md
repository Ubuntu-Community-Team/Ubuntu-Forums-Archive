---
title: "CONVERT DVD TO MP4 (h.264)"
date: 2007-11-07
forum: Multimedia &amp; Video
---

### Post by bonka on 2007-11-07
3 Questions

What is the best converter which will give me the best quality?

Will it be able to play on the Xbox 360?

Are there any decent avi (Xvid) to mp4 (h.264) converters?

Provided guides would be great

---

### Post by dirtNap on 2007-11-08
Hi, I'm a noob but check out handbrake cli  [http://handbrake.m0k.org/?article=documentation]("http://handbrake.m0k.org/?article=documentation")

---

### Post by rsambuca on 2007-11-16
What is this - invasion of the non-linux folk again?  Those two prior posts are non-linux apps!

You can try avidemux to do the conversions.  It is in the repos.

---

### Post by Shampyon on 2007-11-16
When I'm converting from DVD to MP4 I use k9Copy. It's available in Add/Remove Programs. You can rip the files to your hard drive with another app (like DVDRip, also in the repos) if you want, or just use k9Copy to create an ISO then mount it (for example, with this [Nautilus scrip]("http://ubuntuforums.org/showthread.php?t=87369&highlight=mount+ISO+nautilus+script")t). It'll convert to h263, x264, XVid, Divs 3/4/5 and a few others.

Another possibility is to use [ConvertIt]("http://ubuntuforums.org/showthread.php?t=567016&highlight=ConvertIt"). On Windows I used to use SUPER Video Converter for this kind of thing, and ConvertIt is every bit as easy to use. Does just about every type of video and audio conversion you could want. Just make sure you've got all the relevant codecs installed. Run the GUI from a terminal command if you want to be extra safe and check for potential codec errors.

(Links go to other UbuntuForums threads with all the releavant info)

Edit: I neglected to answer your other two questions. So far I've found that the quality of the MP4s are fine when played on my Ubuntu box. On those occasions I go for a set bitrate rather than a specific filesize (k9Copy gives you both options), I use [this web-based bitrate calculato]("http://www.icon.co.za/~thief/stuff/divx/divx.html")r to figure out the best bitrate for DivX or XVid.

As for your other question, I'm sorry but I have no idea whether it will play on your XBox360. Still, I know that here in australia it's fairly easy to get spindles of 50 blank DVDs for about $18 and CDs for a little less. If where-ever you are has similar pricing, it should be cheap enough for you to do a little experimentation. Just make sure to post your findings here for the next person to come along with the same question :)

---

### Post by imon9 on 2007-11-18
second the "Converit"

here is the link for guide for installation (for now, installation might look a bit too complex, but worth the trouble, SERIOUSLY :) no regret afterward)
[http://ubuntuforums.org/showthread.php?t=567016&highlight=convertit](http://ubuntuforums.org/showthread.php?t=567016&highlight=convertit)

---

### Post by disturbedite on 2007-11-19
i second avidemux.

btw, nice avatar rsambuca.  ;)

---

### Post by easyease on 2007-11-20
do we really want to see all these expensive windows based apllications on this forum? its UBUNTU LINUX that we use round here,,,,,,,,,,im trying to be polite and civil but can feel my blood start to boil so i better shut up now.

---

### Post by picklesmagee on 2008-01-06
see Pastebin..
 DVD to MP4 Script..
 Dual - Audio + idx subs..
apps Needed
Mplayer - Mencoder
MP4Box
a52dec
Faac
x264
dvdxchap (OGMTools)
..an any depencieds needed for Mplayer!

[SIZE="3"][[COLOR="DarkRed"]DvD to MP4 - Dual Audio[/COLOR]]("http://dvdscript.pastebin.com/d743ce31b")[/SIZE]

---

### Post by Lostincyberspace on 2008-01-06
Their is iriverter it does a pretty good job.

---

### Post by Duroon on 2008-01-06
> **rsambuca said:**
> What is this - invasion of the non-linux folk again?  Those two prior posts are non-linux apps!

You can try avidemux to do the conversions.  It is in the repos.

Handbrake now comes in a Linux version.However there is no documentation on how to use the program in Linux.

---

### Post by picklesmagee on 2008-01-07
yes handbrake has a linux cli mac os x cli an it works on windows..

handbrake fails at idx sub's that is is crap if you ask me..
  hardcoded subs are weak... an cruel
  you can use "CLI" with mplayer/mencoder an all dependencies to rip/encode..
 GUI is not needed..
 try my script.. it works well

---

### Post by picklesmagee on 2008-01-09
looking back over .. pasting code into here.. 
 makes for bad copy paste.. :-P
anyways............
 here.. i went for using pastebin.. 
 works better..
  dvd to mp4 dualaudio with subs script!!
 [http://dvdscript.pastebin.com/](http://dvdscript.pastebin.com/)

.. goodluck.. find me if you want anything added or changed..
I opted not to use the $Save function.. 
 being well i have no idea where another user wants to save their rip's..
 easy enuff to add yourself..

#path to save directory
$SAVE="/media/rip/dvdrip"

then add $SAVE to the start of every output..

mplayer dvd://$TRACK\
       -dumpstream\
       -dumpfile $SAVE/$TITLE.mpg

get it?.. ok.. 
:popcorn:

---

