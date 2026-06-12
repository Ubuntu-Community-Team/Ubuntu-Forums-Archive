---
title: "KDE DVD Authoring Wizard weird problem"
date: 2007-06-29
forum: Multimedia &amp; Video
---

### Post by tubunu on 2007-06-29
I am trying to author a DVD from three mpeg2 files using KDE DVD Authoring Wizard. 

Everything goes well up to a point where it asks me if I want to create an iso file to burn to a DVD. When I click YES *nothing happens*. 

I used this programme before reinstalling Feisty and it worked flawlessly. I have all the required packages installed (double checked). 

I tried making an iso out of the files KDE DVD AW created using 
```
mkisofs -r -o file.iso /home/user/dvd/ 
``` 
command, but after burning the DVD all I got is one continuous film whereas I wanted to have a selectable 3 film item menu. :(

What am I missing?

---

### Post by david_2001 on 2007-06-29
Not sure.  KDE DVD Authoring Wizard works fine here on feisty X86_64.  Do you have the latest version (1.4.6) installed?

---

### Post by tubunu on 2007-06-30
I have version 1.4.5, the latest version wouldn't install on my system. (I don't know why)

---

### Post by david_2001 on 2007-06-30
Version 1.4.6 installs without any problems here.  My first check would be that the kommander and dvdauthor packages are properly installed - note that DVD Authoring Wizard can be a little choosy about the version of dvdauthor.  Next I would remove DVD Authoring Wizard.  The files should be installed in /usr/lib/kde3/bin (DVDAuthorWizard-Builder.sh and DVDAuthorWizard.kmdr) and /usr/lib/kde3/share/apps/dvdauthorwizard.  Then I would reinstall DVD Authoring Wizard from wherever I had extracted the files:
```
sudo  kmdr-executor ./Installer.kmdr
```
In the meantime, DVD Authoring Wizard uses the following command to create the DVD iso image:
> mkisofs -V "`echo "$Label" | head -c 30`" -dvd-video -o "@OutputDir/$Label.iso" "@OutputDir/DVD/"
or, to put it another way:
```
mkisofs -V "DVDLabel" -dvd-video -o file.iso /home/usr/dvd
```

---

### Post by tubunu on 2007-07-02
Thank you **david_2001**. 
Unfortunately after following your advice and spending 4+ hours on it, the result is the same - on the last screen where it asks if I want to create an iso, nothing happens when I click it. I also tried via command line, which does work, but again after burning the DVD I don't have a selectable menu. The menu is just an 18 second mpeg movie which runs as first, followed by the other three films one after another.. :( 
I also tried QDVDAuthor, but it also gave me some errors upon creating iso. 

I hate to admit it, but what I finally did, was boot into Windows (first time this year!) and create an iso *with selectable menu* without much hassle. I really am an advocate of Linux, but authoring DVD's *really* has to be made much simpler for an average user. sigh..

---

### Post by david_2001 on 2007-07-04
This is curious.  I've been using DVD Authoring Wizard for more than a year now (through dapper, edgy and now feisty) and have never had any problems.  It's a nicely simple application, essentially a collection of scripts with a fancy interface utilising standard applications that can be installed with Synaptic.

Do you definitely have all of the necessary packages installed in addition to Kommander, i.e. ImageMagick, MJPEGTools, Sox, DVDAuthor and Transcode?  Did you check the log files that it saves in the storage folder?  And are you definitely clicking all of the necessary buttons as you move through the dialogs, i.e. "Build Menu" (not just "Preview"), "Finalize" and "Create ISO"?  Did you also wait for it to complete checking the mpeg files for compatibility while finalising the DVD file structure, which can take some time?

EDIT: And are you using Kubuntu?  If not, do you definitely have konsole installed - the create iso step does run in a console?

EDIT1: The common factor is that both DVD Authoring Wizard and QDVDAuthor depend on the DVDAuthor package.  Try reinstalling.  Otherwise, perhaps the 32-bit DVDAuthor package in feisty has some problem that the 64-bit package I'm using doesn't.

---

### Post by Stephen Shellard on 2007-07-17
The information in this thread has enabled me to make some progress with DVD Authoring Wizard, but to be honest I am pretty stuck with it at present.  Compiling a programme, which I seem to have done succesfully, was a straying into very deep waters for me, but my hope that the rest would be plain sailing has not been realised.  

I have  installed all the relevant packages and following the advice of the Read Me file have used Kommander to run the Installer.kmdr file and attempted to author a DVD. (attempting to install "system wide"  by clicking on the DVDAuthorWizard.kmdr file seemed to fall at the fence with the request for the locaktion of my KDE - haven't a clue)  

Nevertheless, the installer.kmdr route seemed to be productive but I still get stuck at a fairly early stage.  

First I drag in a  folder where I want to save the output.  The path name seems to register nicely and I proceed to the next stage where I have to enter the files to be included.  I am trying to combine (concatenate?) two files - an .mp2 file and a .m2V file (which I have extracted from my digital TV recorder.)  I start by dragging the .mp2 file, and the path name fills in nicely;  however when I try to add this by clicking the add button, nothing happens.  Also, when I try to test the file using the relevant button, again there is no response.  Attempting to drag a second file (the .m2V file) goes nowhere.  

It occurs to me that a) I am completely out of my depth and b) that this programme is not the appropriate one for what I am attempting to do.  Are there simple steps I might take which would help me to make progress with this project?  Or should I be searching for some other solution entirely?

---

### Post by david_2001 on 2007-07-20
> **Stephen Shellard said:**
> The information in this thread has enabled me to make some progress with DVD Authoring Wizard, but to be honest I am pretty stuck with it at present.  Compiling a programme, which I seem to have done succesfully, was a straying into very deep waters for me, but my hope that the rest would be plain sailing has not been realised.  

I have  installed all the relevant packages and following the advice of the Read Me file have used Kommander to run the Installer.kmdr file and attempted to author a DVD. (attempting to install "system wide"  by clicking on the DVDAuthorWizard.kmdr file seemed to fall at the fence with the request for the locaktion of my KDE - haven't a clue)  

KDE is installed in /usr/lib/kde3.  If DVD Authoring Wizard works from where it actually installed itself then just leave it where it is.

> Nevertheless, the installer.kmdr route seemed to be productive but I still get stuck at a fairly early stage.  

First I drag in a  folder where I want to save the output.  The path name seems to register nicely and I proceed to the next stage where I have to enter the files to be included.  I am trying to combine (concatenate?) two files - an .mp2 file and a .m2V file (which I have extracted from my digital TV recorder.)  I start by dragging the .mp2 file, and the path name fills in nicely;  however when I try to add this by clicking the add button, nothing happens.  Also, when I try to test the file using the relevant button, again there is no response.  Attempting to drag a second file (the .m2V file) goes nowhere.  

It occurs to me that a) I am completely out of my depth and b) that this programme is not the appropriate one for what I am attempting to do.  Are there simple steps I might take which would help me to make progress with this project?  Or should I be searching for some other solution entirely?

You need to mux your m2v and mp2 files together into a single file before creating the DVD.  To do this use mplex, which is part of the mjpegtools package that you should have installed as a dependency for DVD Authoring Wizard.
```
mplex -f 8 -o my_video.mpg video_file.m2v audio_file.mp2
```

---

### Post by Stephen Shellard on 2007-07-22
I have produced an mpeg file from the audio.m2V and video.mp2 files, as you suggested.  

I continue to get stuck with the Kommander interface which is in general not responding as I might expect.  In other words, files dragged to the appropriate point do enter correctly, but when clicking on a button to effect an action, a dialogue box appears with a line of text - for example &Add to List -  and 3 options:  clear; OK ; cancel:  clicking on OK appears to make no change other than the dissapearance of the dialogue box.  The file is not being added to the list as I might expect.  Am I still missing a piece from the jigsaw of dependencies, or have I just not mastered the Kommander interface.  

Your patience is appreciated.

---

### Post by david_2001 on 2007-07-22
> **Stephen Shellard said:**
> I have produced an mpeg file from the audio.m2V and video.mp2 files, as you suggested.  

I continue to get stuck with the Kommander interface which is in general not responding as I might expect.  In other words, files dragged to the appropriate point do enter correctly, but when clicking on a button to effect an action, a dialogue box appears with a line of text - for example &Add to List -  and 3 options:  clear; OK ; cancel:  clicking on OK appears to make no change other than the dissapearance of the dialogue box.  The file is not being added to the list as I might expect.  Am I still missing a piece from the jigsaw of dependencies, or have I just not mastered the Kommander interface.  

Your patience is appreciated.
I'm old-fashioned (I started using computers in the days of the ASR 33 teletype) and rarely use drag and drop to do anything other than move files from one Nautilus window to another.  Anyway, I had a play with DVD Authoring Wizard to see what would happen if I tried to add files just by drag and drop.  Seems that it works until DVD Authoring Wizard tries to do something with the files such as generate the DVD menu, at which point one of the external programs, e.g. transcode, will choke.

Files that are dragged and dropped onto DVD Authoring Wizard appear with a path and filename in the format "file:///path/to/file".  Edit this to read "/path/to/file" and all will be fine; leave it as it is and problems will follow.  The quick fix then is to always use the select folder/open dialogs, which can be accessed by clicking the button with the ellipsis (three dots in a row), to select folders or add files.

---

