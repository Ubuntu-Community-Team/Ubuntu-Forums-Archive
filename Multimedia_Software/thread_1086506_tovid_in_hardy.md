---
title: "tovid in hardy"
date: 2009-03-04
forum: Multimedia Software
---

### Post by chitowner on 2009-03-04
I am posting this for other newbies out there who are tripping over how to use tovid. it can be tricky, but the most important thing i can say is to PROOREAD YOUR COMMANDS CAREFULLY before you run them!

in my case i started by calling tovidgui using alt+F2 and typing that label in. tovidgui is a decent app and is helpful for those who have issues with command line usage. BUT there are a lot of issues that are not intuitive. i had to back out of botched tries several times to get something that worked. in particular DO NOT use any non-alphanumeric characters in any of the labels. tovid will snag on them.

what i found best about tovidgui is that once you have a set of useful commands you click on the top button labeled ENCODE and it then displays a set of run-ready commands.

now, the options that tovidgui allows are not as flexible as the CL options. once i realized that i found i could copy the pre-formated commands into a text editor (like kwrite) and jigger them to suit. once that is done the commands can be copied from there into a shell and run in CL mode. pretty cool.

SO - here is a list of "canned" commands and some notes to get y'all started:
&&&&&&&&&&&&&&&&&&&&&&&&


Here is a dummy set of commands for tovid to make a DVD with a simple menu that will run in a generic video deck.

Once the first 3 commands have been run, if the resulting files are saved in a seperate folder, the last command will create a new movie DVD every time it is run.

Edit the following to use whatever names you like for your backgrounds, movies and menus. Do not change "/tmp" to another path. This is the Tovid default, so make sure your /tmp has plenty of room!


makemenu -noask -quiet -overwrite -ntsc -dvd -align middle -background "/home/mypics/mypic.jpg" -length 10 -font "Helvetica" -fontsize 24 -textcolor "rgb(255,255,255)" -fontdeco '-stroke rgb(0,0,0) -strokewidth 1' -button "play" -highlightcolor "rgb(100,255,0)" -selectcolor "rgb(255,0,0)" -button-outline "rgb(140,140,140)" "A Movie.avi" -out "/tmp/A_Movie";
%%%%%%%%%%%%%%%%%%%%%%%%%%%%
tovid -overwrite -ntsc -dvd -wide -quality 10 -in "/home/mymovies/A Movie.avi" -out "/tmp/A Movie.avi.tovid_encoded" -from-gui -noask;
%%%%%%%%%%%%%%%%%%%%%%%%%%%%
makexml -overwrite -dvd -chapters 9 -menu "/tmp/A_Movie.mpg" "/tmp/A Movie.avi.tovid_encoded.mpg" -out "/tmp/A_Movie";
%%%%%%%%%%%%%%%%%%%%%%%%%%%%
makedvd -author -burn -device /dev/dvdrw /tmp/A_Movie.xml

NOTES:
1.  The strings of %%%% have no function.
2.  Do not change "/tmp" to another path. This is the Tovid default!
3.  Pay attention to_the_use_of_underscores. Also pay attention to "the use of quotes". It is critical to use them as shown. Underscores replace spaces in the movie_name for the output file of each 'make' command. "Quotes" must be used for ALL paths except in the makedvd command.
4.  "-quality ##" can be 1 to 10. higher number will create bigger file. A 700Mb avi can produce an mpg that is up to 4Gb at level 10.
5.  "-chapters ##" can be any integer number. It's function is to allow stepping or jumping through the DVD movie and refers to actual minutes of play time.
6.  A "\" can be used as a line break, followed by a hard return to make the commands easier on the eyes. this may be helpful to some.
7.  A ";" may used at the end of the first 3 commands to allow stringing all 4 together. You can use this option once you become proficient. Just make the 4 commands contiguous with no returns and make sure that a blank DVD is in the burner.

&&&&&&&&&&&&&&&&&
Enjoy!
:popcorn:

---

### Post by Paddy Landau on 2009-03-05
Thank you for the ideas.

I had been using ManDVD (much easier!), but there's one AVI that, for some reason, it doesn't cope with.

Now, following your instructions, I have a problem. Although I have tovid, I don't have makemenu, makexml, or makedvd.

Where do I get those programs?

---

### Post by mrtomservo on 2009-04-04
If you were still looking, they're probably located under:

/usr/share/tovid/makedvd

There's likely no link to that directory so they're not found when you type makedvd for instance in the terminal, so use the full path.  I thought I was missing them too, but I used 'locate' to find them after 'sudo updatedb'.

---

### Post by Paddy Landau on 2009-04-04
> **mrtomservo said:**
> If you were still looking...
Thank you!

I'll try them next time.

---

### Post by stoppage on 2010-05-07
On creating menu I'm stuck on „Default“ font. So I downloaded and exercised (to /home folder) „ Anthony Thyssen's imagick_type_gen.pl script“ from the Tovid Wiki but font isn't seeing any more fonts as default. Any suggestions please?

---

### Post by stoppage on 2010-05-21
> **stoppage said:**
> On creating menu I'm stuck on &#8222;Default&#8220; font. So I downloaded and exercised (to /home folder) &#8222; Anthony Thyssen's imagick_type_gen.pl script&#8220; from the Tovid Wiki but font isn't seeing any more fonts as default. Any suggestions please?

A solution to the fonts problem found by gaspard.leon at [http://ubuntuforums.org/showthread.php?t=183936&highlight=fonts&page=48](http://ubuntuforums.org/showthread.php?t=183936&highlight=fonts&page=48)
Quote...&#8220;In the tovid scripts, replace convert -list type with convert -list font

if your version of ImageMagick has updated that feature as mine had...
(run those 2 commands in a shell to test)

i found that the following files had to change:
Code:
/usr/share/tovid/makemenu
/usr/share/python-support/tovid/libtovid/gui/configs.py&#8220;

---

