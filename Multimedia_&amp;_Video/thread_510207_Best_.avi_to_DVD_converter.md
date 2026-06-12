---
title: "Best .avi to DVD converter?"
date: 2007-07-26
forum: Multimedia &amp; Video
---

### Post by SPQQKY on 2007-07-26
I'm looking for a good all in one DVD creator. I need something for mostly converting .avi to DVD. I tried DeVeDe and I sure don't like it, much to limited in it's abilities.
If anyone is familiar with ConvertXtoDVD, I would like something like that if possible. 
In ConvertX, you can:
Add a menu screen with any image you choose, create chapters and burn right from the software. 
None of this is available with DeVeDe and it only creates an ISO which you have to burn using separate software.
Any tips would be greatly appreciated.

---

### Post by Saner on 2007-07-26
ManDVD is pretty good

---

### Post by dabl on 2007-07-26
I'm real interested to hear about this too.  I just got to the point where I can work with a mpg file using Avidemux.  I guess the next step is to get it from an avi file to a format ready to go on a DVD.  I'm all ears.  :)

---

### Post by SPQQKY on 2007-07-26
Just did a search, that's an awful lot of extras to install to get it to work.

---

### Post by Kreuger on 2007-07-26
I just use ConvertXtoDVD through wine because I found all the linux ones seem to be lacking a bit. Some can do just the file structures and no menus, some can just do menus and some cant even do either of them without problems such as creating everything but screwing up the audio quality and sometimes sync. So I just dont bother

---

### Post by kelvin spratt on 2007-07-26
The latest version of DeVeDe does menus and it is the nearest thing to  ConvertoX and if you have a sound problem go to their site and download the patch I've done over a 100 wedding movies with it never had a problem.

---

### Post by SPQQKY on 2007-07-26
```
dominic@dominic-desktop:~$ cd ManDVD-2.4
dominic@dominic-desktop:~/ManDVD-2.4$ ./mandvd
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

I get this error, but it still seems to open the GUI. But it will not allow me to select any .avi files.

---

### Post by SPQQKY on 2007-07-26
Anyone.....anyone........Bueller?

---

### Post by dabl on 2007-07-26
> X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

This looks like that goofy wacom driver error output -- it is harmless, and unrelated to anything about sound or video. It's caused by the wacom input devices listed in the default xorg.conf file -- you can comment out the relevant lines and stanzas (there are existing posts on the exact lines) and it will go away. :)

---

### Post by SPQQKY on 2007-07-26
Well, I tried to make a dvd (very confusing configuration in ManDVD) and then I went to generate and it said there was an error with dvdauthor. So I ran configuration in dvdauthor and it said I needed libz(-devel) installed. I cannot seem to locate that package.
What a major P.I.T.A.

---

### Post by bogolisk on 2007-07-26
If you don't **mind** the command line then:
```

    ffmpeg -i my_avi_1.avi -target ntsc-dvd my_avi_1.vob
    ffmpeg -i my_avi_2.avi -target ntsc-dvd my_avi_2.vob
    ...
    dvdwizard -T 'My Disc Title' -N NTSC -V my_res_such_as_640x480 -A my_lang_code_such_as_en -t 'My title 1' my_avi_1.vob -t 'My title 2' my_avi_2.vob ...... -x my_dvd.xml --xmlonly -o my_dvd_dir
    dvdauthor -x my_dvd.xml

```

Most of those DVDCreator sw on windows actually run dvdauthor behind the scene using cygwin!

---

### Post by SPQQKY on 2007-07-26
> **bogolisk said:**
> If you don't the command line then:
```

    ffmpeg -i my_avi_1.avi -target ntsc-dvd my_avi_1.vob
    ffmpeg -i my_avi_2.avi -target ntsc-dvd my_avi_2.vob
    ...
    dvdwizard -T 'My Disc Title' -N NTSC -V my_res_such_as_640x480 -A my_lang_code_such_as_en -t 'My title 1' my_avi_1.vob -t 'My title 2' my_avi_2.vob ...... -x my_dvd.xml --xmlonly -o my_dvd_dir
    dvdauthor -x my_dvd.xml

```

Most of those DVDCreator sw on windows actually run dvdauthor behind the scene using cygwin!

What in the world does that mean.......If I don't what?

---

### Post by fumduck on 2007-07-26
K3b.. I have used that.

---

### Post by SPQQKY on 2007-07-26
K3b does not convert .avi files to DVD format.

---

### Post by SPQQKY on 2007-07-26
No love today?

I guess I'll just have to use Winblows until I get this figured out.

---

### Post by SPQQKY on 2007-07-26
so how in the world can I get dvdauthor to work. It seems to only run from terminal, do I have to start it and then start mandvd? Any clue on the libz(-devel) error. I would really like to get this resolved. Other than this, I've been running Ubuntu soley now and I wouldn't mind saying goodbye to winblows forever.

---

### Post by misfitpierce on 2007-07-26
ManDVD and DeVeDe do great jobs and are excellent programs.

---

### Post by SPQQKY on 2007-07-26
DeVeDe is giving unbelievably bad audio output. And I see there is supposed to be a patch but I cannot understand their website as I no se abla espanol. ManDVD is not working because of a dvdauthor error even though I ran through everything and it says it's working properly and up to date. Perhaps if you read the thread you have realized that.

---

### Post by SPQQKY on 2007-07-27
Okay, one last request for help here.
I booted into winblows last night to make my sons b-day party video and it was like .....eeeewwwww, this thing again.
There are over 1600 people browsing this section, surely someone can throw some good advice my way.

---

### Post by serfcx on 2007-07-27
Nobody has suggested this yet.

Try Tovid. Its a collection of scripts and I have been using it for a year now without "many" issues, and those have been resolved by the forum.

Here is the main wiki [http://tovid.wikia.com/wiki/Main_Page](http://tovid.wikia.com/wiki/Main_Page)

Make sure you install all the dependancies - they are all in the Ubuntu reps and also apply the patches to the latest tovid 0.30 mentioned and linked to on the main wiki.

Forums are here [http://www.createphpbb.com/tovid/](http://www.createphpbb.com/tovid/) but are being moved.

Contained within tovid is a suite called todisc which you can create menus right through recoding avi to DVD and burn.

Have fun !:popcorn:

---

### Post by SPQQKY on 2007-07-27
Looks nice, but I really am getting tired of all this. I can't be bothered to spend all this time installing all these dependancies and working out all the bugs that come with them. To spend hours upon hours of my time to make a dvd when it' takes like 3 minutes from winblows. Sorry if I've wasted everyones time.

---

