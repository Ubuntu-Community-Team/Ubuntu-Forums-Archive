---
title: "using ffmpeg/ dvdauthor"
date: 2009-09-10
forum: Multimedia Software
---

### Post by onespeedbiker on 2009-09-10
I am using ffmeg to convert avi files to mpg files and dvdauthor to turn the mpg files into vob (dvd) files. The problem I am running into is dvd authour needs an aspect ratio of 4:3 or 16:9 to create vob files, and the "dvd" target command fixes the frame size at 720x480. This tends to distort many of the resulting mpg videos with a different frame size (I made a few mpg files using the source frame size and no aspect ratio and they came out perfect, but dvdauthor won't convert them). The only work around I have found is to add "pads" to the bottom and top to "squish" the video frame; there has to be a better way. I'm thinking I need to not use the "dvd" target comman and enter the bitrate, codecs and buffer size manually, but I don't know any of the default values. 

So, does anyone out there know what I'm talking about and can steer me toward a solution? THX

---

### Post by Cresho on 2009-09-11
use devede.  throw the files (anykind of files you name it) into devede, tell it you want 4 to 3 aspect, deinterlace, and it creates a iso dvd.  use brasero to burn dvd.

it is simple.  no hassle.  no problems.  Use the other softwares if you want to develope your workflow.  you can also preview your result...10 seconds, 1 minute, it is very very simple.  I mix and match wide or tv type.  Not a problem and not complicated.  Too simple.

#sudo apt-get install devede

---

### Post by bumanie on 2009-09-11
I agree that devede is a very simple program to use. If you want to use ffmpeg, go [here]("http://code.google.com/p/winff/wiki/UbuntuInstallation") and install the gui for it, you may find it easier than cli. Sorry, can't help with dvdauthor.

---

### Post by onespeedbiker on 2009-09-11
> **Cresho said:**
> use devede.  throw the files (anykind of files you name it) into devede, tell it you want 4 to 3 aspect, deinterlace, and it creates a iso dvd.  use brasero to burn dvd.

it is simple.  no hassle.  no problems.  Use the other softwares if you want to develope your workflow.  you can also preview your result...10 seconds, 1 minute, it is very very simple.  I mix and match wide or tv type.  Not a problem and not complicated.  Too simple.

#sudo apt-get install devede I tried Devede but it's to buggy. It reduces all video files, to 2.4 gig dvd/ ISO files (that is the 9660 limit) and errors out when you ask just for the files. What's the point of burning high quality dvd's if you are limited to files 1/2 the size that will fit on a 4.7 gb DVD? You would think that in the whole world, there would be more than one buggy avi to DVD program.

---

### Post by Cresho on 2009-09-11
how long is your video?  max bit rate on standard dvd is around 11.08 including audio and anything higher, dvd's will not work on players.  Did you click on the "adjust" button?

There is a standard, that's why you can't use the whole 4.7.  also, it's not 4.7, It is 4.37

what are the codecs your avi carries?

try mediainfo if you don't know.

[http://www.signvideo.com/bt-rts.htm](http://www.signvideo.com/bt-rts.htm)

devede adjusts and compensates for errors and compatability issues.  In hardy heron, the highest version you can use on ubuntu is devede_3.12c-0.0_all.deb

Do you have medibuntu installed?

I edit High definition videos for presentation, weddings, sweet 15 on cinelerra and burn them on devede.  I can do a 4 hour video editing and rendering and burning to devede anywhere between 6-8 hours.  THese are fast and stable softwares.  Your errors could be hardware related or version problems.  Also brand named burners and dvd-r's or even memory.  You will need to mix and match till you get something right including software but once you get your workflow together, the rest is easy.

---

### Post by onespeedbiker on 2009-09-11
> **Cresho said:**
> how long is your video?  max bit rate on standard dvd is around 11.08 including audio and anything higher, dvd's will not work on players.  Did you click on the "adjust" button? The adjust button only says it's adjusting the size, it does not.There is a standard, that's why you can't use the whole 4.7.  also, it's not 4.7, It is 4.37  The videos are around 2 hours. Devede says this is around 130% of a 4.37 disc (my bad). The adjust button says it's adjusting the size; but it does not. The ISO container used by Devede uses the 9660 level 2 which only allows fies sizes of 2.4 gs or less. So no matter what the size or length of your video it comes out at 2.4 gb. I had tried to burn the dvd files Devede says are 130% the size of a 4.37 disc and it still comes out @2.4 gbs. I am running Juanty 9.0.4. When I ask Devede to create just the file structure it says it is missing a plug-in, but numerous searches have failed to solve this problem.

---

### Post by Cresho on 2009-09-11
sounds like there is a problem.  Jaunty has given me nothing but headaches as well.  make sur eyou have pal or ntsc set correctly.

anyway, try
#sudo apt-get remove devede

go to the website and try the new version.
[http://www.rastersoft.com/programas/devede.html#download_section](http://www.rastersoft.com/programas/devede.html#download_section)

if you want to try a beta dvd authoring software specifically for gtk, I also would look into bombono [http://forum.videohelp.com/topic371977.html](http://forum.videohelp.com/topic371977.html)  I cannot use that since it has a deb for 32bit hardy heron.  It could work on your system.  Also, you need to have your mpeg2 already converted as this software does not convert the files for you.  it only creates the dvd layout and you provide the files converted.

---

### Post by Cresho on 2009-09-11
ohh just a point here, he added a jaunty repo

[http://www.bombono.org/cgi-bin/wiki/Install%20In%20Ubuntu](http://www.bombono.org/cgi-bin/wiki/Install%20In%20Ubuntu)

install with 
#sudo apt-get install bombono-dvd

or just look ofr bombono in synaptic

he also updated my problem with fixes and answered it with a deb file and a repo.

took him 3 days.  he says it takes vob files.  mpeg2 needs to be converted to vob files before this software will take them.  I have a feeling I will give winff a try because this software makes some really good dvd layouts.

---

### Post by onespeedbiker on 2009-09-11
> **Cresho said:**
> sounds like there is a problem.  Jaunty has given me nothing but headaches as well.  make sur eyou have pal or ntsc set correctly.

anyway, try
#sudo apt-get remove devede

go to the website and try the new version.
[http://www.rastersoft.com/programas/devede.html#download_section](http://www.rastersoft.com/programas/devede.html#download_section)

if you want to try a beta dvd authoring software specifically for gtk, I also would look into bombono [http://forum.videohelp.com/topic371977.html](http://forum.videohelp.com/topic371977.html)  I cannot use that since it has a deb for 32bit hardy heron.  It could work on your system.  Also, you need to have your mpeg2 already converted as this software does not convert the files for you.  it only creates the dvd layout and you provide the files converted. Well, I might have spoken too soon; I just installed mediaidea and Devede is now allowing me to make the DVD structure files. If this works, maybe Brasero will actually allow me to burn them (it also errored out, wanting a plug-in and would only burn an ISO file). Still once I get the vob files I can use a number of programs to shrink/burn them.

---

### Post by Cresho on 2009-09-11
how about k3b?  the created iso image by devede burns on it flawlessly as well.

---

### Post by onespeedbiker on 2009-09-11
> **Cresho said:**
> how about k3b?  the created iso image by devede burns on it flawlessly as well. I'm trying to get into the line command thing so I'm going to try growisofs/mkisofs; it's really cool when it works :D

---

### Post by Cresho on 2009-09-11
here is an update with bombono!!!!!!!!!!!

in menu list inside menu, you have menulist and medialist.  on menu list, you have 2 bottons on left side of edit.  they have nothing on the button.  So I did not know these buttons are to add or remove menus.  I had a hard time figuring  out how to add menus.  But it works its just it has no text.  edit says edit but the other 2 has nothing and only has buttons.
---------------------------------------------------------------------------
video converting anytype to vob files is easy.  you just need medibuntu installed if you have ubuntu and use winff to convert.
I created a ntsc wide screen high quality profile for you guys to try out.  you can edit the line..its easy.

preset Name: ntscdvdvobhqWS
preset label: NTSC DVD-vob HQ (16:9)
preset command line:
-target ntsc-dvd -r 29.97 -s 720x480 -aspect 16:9 -b 8000k -mbd rd -flags +trell -mv0 -cmp -subcmp 2
output file: VOB
category: DVD

now you can drag and drop the videos into it and it will work fine.

---

### Post by onespeedbiker on 2009-09-11
> **Cresho said:**
> ohh just a point here, he added a jaunty repo

[http://www.bombono.org/cgi-bin/wiki/Install%20In%20Ubuntu](http://www.bombono.org/cgi-bin/wiki/Install%20In%20Ubuntu)

install with 
#sudo apt-get install bombono-dvd

or just look ofr bombono in synaptic

he also updated my problem with fixes and answered it with a deb file and a repo.

took him 3 days.  he says it takes vob files.  mpeg2 needs to be converted to vob files before this software will take them.  I have a feeling I will give winff a try because this software makes some really good dvd layouts.Winff does not create the vob file structures; it just gives a .mpg file a .vob extension. Still looking..

---

### Post by onespeedbiker on 2009-09-11
> **Cresho said:**
> here is an update with bombono!!!!!!!!!!!

in menu list inside menu, you have menulist and medialist.  on menu list, you have 2 bottons on left side of edit.  they have nothing on the button.  So I did not know these buttons are to add or remove menus.  I had a hard time figuring  out how to add menus.  But it works its just it has no text.  edit says edit but the other 2 has nothing and only has buttons.
---------------------------------------------------------------------------
video converting anytype to vob files is easy.  you just need medibuntu installed if you have ubuntu and use winff to convert.
I created a ntsc wide screen high quality profile for you guys to try out.  you can edit the line..its easy.

preset Name: ntscdvdvobhqWS
preset label: NTSC DVD-vob HQ (16:9)
preset command line:
-target ntsc-dvd -r 29.97 -s 720x480 -aspect 16:9 -b 8000k -mbd rd -flags +trell -mv0 -cmp -subcmp 2
output file: VOB
category: DVD

now you can drag and drop the videos into it and it will work fine. Winff does not create a vob file structure; it just gives a mpeg file with a .vob extension.

---

### Post by Cresho on 2009-09-12
mpeg is vob and vob is mpeg but the important part of this story is it includes nav which is needed by bombono to create a dvd menu system.  It works and bombono concurs.

you can then create your dvd with custom menu system.  try it!

[http://en.wikipedia.org/wiki/VOB](http://en.wikipedia.org/wiki/VOB)

---

