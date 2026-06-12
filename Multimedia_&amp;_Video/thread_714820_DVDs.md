---
title: "DVDs"
date: 2008-03-04
forum: Multimedia &amp; Video
---

### Post by rob1984 on 2008-03-04
so, im so close to completely making the switch from windows but theres one thing i still need it for - burning dvds. so can anyone help me find the right program? i need:-

to convert avi/mpg/divx to VOB/IFO
create menus
write my new VOB/IFO set to a blank dvd

preferably all in one go, i'd rather use one program than several. finally, the lighter the better. i only have one laptop so i'd like to be able to run it in the background while i do other stuff (although this may be asking too much)

any help/comments are greatly appreciated.

thanks

---

### Post by ron999 on 2008-03-04
Hi
To convert and author DVDs there's a GUI app called DeVeDe, but there may be problems with the sound. Read about it on their website.
Here:-[http://www.rastersoft.com/programas/devede.html]("http://www.rastersoft.com/programas/devede.html")

These days I use 'tovid' from the command line instead.
Here:-[http://tovid.wikia.com/wiki/Main_Page]("http://tovid.wikia.com/wiki/Main_Page")

K3b is probably best for burning discs.

---

### Post by empthollow on 2008-03-04
To create custom menus and burn dvd's i use DVDStyler. This program requires mpeg files.  I use avidemux to create these.  there is an auto menu in avidemux that makes this very easy.  If you are looking for a program that is a little simpler DEVEDE is great.  you can use any filetype, This program will convert the videos and create bin/cue or iso files which you then burn to disc.  the tradeoff is that the menu is not very customizable.  You can change the font and background but not much else.

---

### Post by rob1984 on 2008-03-04
cheers, i will try these all. 

if tovid has a CLI version then thats very appealing.
DeVeDe looks great but i find sound is the biggest issue when encoding dvds.

i'll let you know how i get on.

---

### Post by empthollow on 2008-03-04
just so you know i have not had a problem with sound in devede, i did find that on ocasion the encoding isn't as good as it could be and have ended up with choppy video.  to circumvent this issue i use avidemux to encode my files to mpeg and just check in devede that the file is already compliant.  this way i get a better encoded mpeg and i can reuse them on different dvds.  devede will put tracks every 5 min and create the iso very easily.  hope this helps.

---

### Post by Motorhead Kaze on 2008-03-04
There is a real difference from computer to computer regarding DeVeDe.  It is maddening that some people can use it and some can't. In my PC, DeVeDe with .avi is garbage.  There have been known issues with the sound since Feisty.  Some people have a good time with it, but in my computer, even the "Fix" puts out green horizontal lines across the screen.  With .mv's DeVeDe is good, but Mencoder is wacked. DeVeDe works for some and not at all for others.

This seems to be the real issue in Ubuntu: How to make a DVD using as few steps and as few programs as possible.

**Question for Tovid users:**  How many hours does it take you to make a DVD from .avi?  If one doesn't need menus and such (for example, I want to put several episodes of Battlestar Galactica, in .avi format onto a DVD) can I go straight from .avi to DVD in Tovid?

---

### Post by ron999 on 2008-03-04
@Motorhead Kaze

**Answer from a tovid user.**

To make a simple DVD with tovid. Just 3 steps.

1 Convert file to mpg using 'tovid' command.
2 Make an xml file using 'makexml' command.
3 Author a dvd structure using 'makedvd' command.

Then burn it with K3b

These are the commands that I would use:-

tovid -pal -ffmpeg -in filename.avi -out movie
makexml -dvd movie.mpg -out MyDisc
makedvd -author MyDisc.xml

Those commands take the file 'filename.avi' and make a directory called 'MyDisc' which contains two folders:- Audio_ts and Video_ts. Ready to burn.

The longest time is taken in the first step, converting the avi into mpg. That depends on the speed of your PC.
Read about it at the tovid link in my first post.
:guitar:

Edit
In Japan it is NTSC system, not PAL
So the first instruction is only:-
tovid -ffmpeg -in filename.avi -out movie
(NTSC is default)

Edit 2
I expect that tovid will work with other files as well as avi. Whatever ffmpeg will accept.

---

### Post by Motorhead Kaze on 2008-03-05
Oh yeaaaah!  Your advice and Tovid have saved me from my .avi to DVD in Ubuntu perils.  (A very specific peril, but none the less perilous)

I tried out Tovid, and it rules.  I tried the GUI first, and it is so easy to use!  I adore simple.  I admit, I stayed away from Tovid for a long time because people said it was so slow.  But...it is slow because it does all the conversions for you!  Just what I wanted, a program that does everything I need.  My darling wife is enjoying season 1 of Battlestar Galactica on the TV as we speak, via the  DVDs I made with Tovid.

Thank you for the recommendation, I will pass it on.

PS Ntsc or Pal is fine for us, we found out right away that we needed a multi-regional DVD player when coming here.  But thanks for the warning.

---

### Post by Motorhead Kaze on 2008-03-06
Oh, BTW, one doesn't need to use K3b or not at least in using the Tovid GUI.  There is a button for BURN, which makes this a very, very useful tool.

---

