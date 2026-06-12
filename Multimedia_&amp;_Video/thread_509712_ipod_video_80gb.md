---
title: "ipod video 80gb"
date: 2007-07-25
forum: Multimedia &amp; Video
---

### Post by rbprogrammer on 2007-07-25
has any ever gotten the white 80gb video ipod to work correctly with videos??

i have tried everything, gtkpod, [http://ubuntuforums.org/showthread.php?t=114946](http://ubuntuforums.org/showthread.php?t=114946) , but nothing seemed to work.. is it my system or have people gotten their video ipods to work?

---

### Post by fearevilleet on 2007-07-25
lol, I have never gotten that to work either. I gave up and just use my mac.

---

### Post by rbprogrammer on 2007-07-25
a few months ago i completely got rid of my windows partition and i am 100% ubuntu now, but the problem is that i can never seem to find anyone or any tutorials or any help that gets my video ipod to play videos..

funny thing is that i thought this would have been one of those problems that lots of people had and fixed a long time ago :( ..

---

### Post by asktoby on 2007-07-28
Does it work okay for music out of the box?
I've just set my friend up with Ubuntu 7.04 and Rhythmbox, and he's asking me to recommend an MP3 player. He wants an 80gb ipod.

---

### Post by rbprogrammer on 2007-07-29
music wise it's great, i use amarok to upload music and it definitely worked right out of the box for me.

the video uploading is the problem that no one seems to know how to do.. :confused:

---

### Post by rbprogrammer on 2007-08-03
bump

---

### Post by rbprogrammer on 2007-08-05
has anyone had any luck with iPod linux on the 80gb video iPod??

[http://ipodlinux.org/Main_Page](http://ipodlinux.org/Main_Page)

---

### Post by count_zero on 2007-09-10
I'm gonna bump this now. I've been trying for days, and this problem is not filling me with joy and happy thoughts. I've tried to install GTKPOD V0.99.10, which is supposed to give video support, but so far all I've had is problems. Any suggestions? Has anyone managed to get this to work yet?

---

### Post by kostkon on 2007-09-10
You have to install *gtkpod-aac*, not *gtkpod*, to be able to load videos to your *iPod Video*. Nevertheless, I recommend you to try [Floola]("http://www.floola.com/"), it's a very good program!

You can get [a deb package from *getdeb.net*]("http://www.getdeb.net/app.php?name=Floola") or you can get the binary straight from [its site]("http://www.floola.com/modules/wiwimod/index.php?page=download").

---

### Post by kostkon on 2007-09-10
Don't forget that the videos have to be MPEG4 in order to be able to be accepted by *gtkpod-aac* and *Floola*. Use something like ffmpeg (and with a GUI like *WinFF*) to convert any videos to MPEG4 format.

---

### Post by count_zero on 2007-09-11
OK, I'll try Floola. BTW, any idea how much space it takes up on the ipod?

Now I've just gotta get rid of all the useless stuff I've installed trying to get GTK to work... :(

---

### Post by rbprogrammer on 2007-09-11
> **count_zero said:**
> OK, I'll try Floola. BTW, any idea how much space it takes up on the ipod?

Now I've just gotta get rid of all the useless stuff I've installed trying to get GTK to work... :(

lol, yes me too, i've tried the gtkpod-aac and that never worked. even when i converted the movies to mp4 with ffmpeg

---

### Post by count_zero on 2007-09-11
Mkay... I've downloaded and installed the .deb package, and I can get it up and running. However, I can only see my videos when I search for them, and when I try to view the ones I've already got on there it locks up, and it doesn't want to convert/transfer them either. I've tried manually changing the ipod to the 80gb video, but it still doesn't want to play...
BTW, the problem I have with gtkpod V0.99.10 is an error message that I have libgpod v.0.4.2, not 0.5.2, and I've installed it already!!

---

### Post by kostkon on 2007-09-11
If the videos don't play when uploaded, means that they, maybe, have a resolution or bitrate that is too high for the *iPod*.

---

### Post by Quiane on 2007-10-02
Thank you...man, this should be a sticky, or just a sticky tutorial...the gtkpod is ****...floola is the way to go..thanks a lot!

---

### Post by count_zero on 2007-10-02
Well, I've managed to get Floola working to a point, but I'm still struggling a bit.
I've got DVDrip to convert a DVD to .avi (for some reason it won't convert to mp4...), and added it to the queue in Floola. It then says it's converting the file, but it's adding it as .avi to the ipod and it won't play. Is this because it's an .avi, or have I got the bitrate/resolution wrong still? I would have thought Floola would have taken care of that during it's convertion phase... I tried this with a youtube video and it works fine!

Suggestions?

---

### Post by rbprogrammer on 2007-10-03
yup, i'm pretty sure that the video ipods dont play avi's... :(

i was trying to mess with the linux for ipod thing since i'm sure they can play avi's, but classes this semester got significantly more difficult and i just have not had much time to mess around with it..

---

### Post by justinmiller87 on 2007-10-03
If you don't mind going back to using iTunes, someone's figured out how to install version 7.3, which gives support for all iPods up through the phone, in WINE. Check out the info here:
[http://ubuntuforums.org/showthread.php?t=566134](http://ubuntuforums.org/showthread.php?t=566134)

---

### Post by mike_tyrell on 2008-02-20
> **count_zero said:**
> I'm gonna bump this now. I've been trying for days, and this problem is not filling me with joy and happy thoughts. I've tried to install GTKPOD V0.99.10, which is supposed to give video support, but so far all I've had is problems. Any suggestions? Has anyone managed to get this to work yet?

here is how I made it to work

I installed libgpod_0.3.0-1_i386.deb
then I installed mpeg4ip-libs_1.2.5+cvs20050126.20-0.0_i386.deb
if you get a conflict remove that file and install the one above

google the deps and you will find

then finally sudo apt-get install gtkpod-aac

my system is toshiba laptop satellite U300 series
iPod 80GB Video Black
I am a newbi like you guys so we should try to simplify to each other as much as possible
now any one know how to compile more then one packages :)

---

### Post by rbprogrammer on 2008-02-21
> **mike_tyrell said:**
> 
here is how I made it to work
...
my system is toshiba laptop satellite U300 series
iPod 80GB Video Black
...

i might have time to work on this sometime this weekend.  i have given up all hope, but if you got your 80G black, then i will try for my 80G white.  i dont think there is any hardware difference between the two, so if yours works, mine should too.  then i might be able to make a how-to and put it in the how-to section.  but i will have to see if i will have the time.

---

