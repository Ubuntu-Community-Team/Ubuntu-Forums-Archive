---
title: "Wine - itunes"
date: 2009-08-18
forum: Multimedia Software
---

### Post by accodata on 2009-08-18
Hi

Can someone please give this stupid person writing this post a step by step to install itunes through wine, I have no idea.

thanks

Accodata

---

### Post by realzippy on 2009-08-18
...first install wine:

Terminal:

**sudo apt-get install wine**

download the windows wine installer (exe)

Right click on it,choose "open with wine" ....

---

### Post by accodata on 2009-08-18
thank you I tried that but got this[IMG]tracey/desktop/screenshot.png[/IMG]

---

### Post by accodata on 2009-08-18
/home/tracey/Desktop/Screenshot.png

---

### Post by realzippy on 2009-08-18
??? again,please

---

### Post by accodata on 2009-08-18
Hi

Now I am trying to work out how I get the screenshot in here

---

### Post by accodata on 2009-08-18
[IMG]Screenshot.png[/IMG]

---

### Post by accodata on 2009-08-18
the screenshot says

The installer encountered errors before iTunes could be configured.

Your system has not been modified . To retry these 
operations at a later time, please run the installer again.

Click finish to exit the installer.

---

### Post by realzippy on 2009-08-18
hit attachments,right to the smiley

---

### Post by realzippy on 2009-08-18
which ubuntu you are using?
32 or 64 bit?
which iTunes version?

---

### Post by accodata on 2009-08-18
I downloaded the 32 bit of itunes installer, i am running 9.04 upgraded from 8.10.

---

### Post by realzippy on 2009-08-18
...I tested also,same error.Older version works:

[http://www.oldapps.com/itunes.php?old_itunes=20](http://www.oldapps.com/itunes.php?old_itunes=20)


Thats 7.2

---

### Post by Grenage on 2009-08-18
Hi there  **accodata**,


Out of raw curiosity, is there any particular reason you need itunes over a native as Amarok?

Gren.

---

### Post by realzippy on 2009-08-18
> **grenage said:**
> hi there  **accodata**,


out of raw curiosity, is there any particular reason you need itunes over a native as amarok?

Gren.

+1

---

### Post by accodata on 2009-08-18
ipodcopy_setup.exe is that the correct file?

---

### Post by accodata on 2009-08-18
i have an ipod shuffle that I use to take to bed............ but Amarok doesn't allow me to change music nice enough

---

### Post by Grenage on 2009-08-18
How does it give you problems?  People here will help you either way, but I only ask because I was once in your position, with an ipod.  I found it way simpler to manage and synchronize music with Amarok than I did with itunes.

---

### Post by accodata on 2009-08-18
so I didn't actually muck it up?

that is good to know

thank you for your help I do appreciate it!!

Have a great day

Accodata

---

### Post by accodata on 2009-08-18
So you can use Amarok instead of iTunes for a shuffle....

let me download it, and ask for help

---

### Post by realzippy on 2009-08-18
> **accodata said:**
> ipodcopy_setup.exe is that the correct file?

No,that one:

[http://download.oldapps.com/iTunes/iTunesSetup72.exe](http://download.oldapps.com/iTunes/iTunesSetup72.exe)

---

### Post by accodata on 2009-08-18
found it thank you

sorry,

But I had a post on why I don't use Amarok, so I am installing both and see how I go..........:lolflag:

---

### Post by Grenage on 2009-08-18
let us know how you get on :)

---

### Post by accodata on 2009-08-18
I have no idea how to get music from Amarok to Shuffle ipod!

Help!!!!!!!!

Accodata

---

### Post by Grenage on 2009-08-18
[http://www.simplehelp.net/2007/07/04/how-to-use-amarok-to-manage-your-ipod-in-ubuntu/](http://www.simplehelp.net/2007/07/04/how-to-use-amarok-to-manage-your-ipod-in-ubuntu/)

Take a look here :)

---

### Post by accodata on 2009-08-18
I am now reading..............LOL

thanks

:popcorn:

---

### Post by riazrahaman on 2009-08-18
If you don't yet have wine, install wine

sudo apt-get install wine

next download the itunes for windows binary.

Right click on the itunes.exe file and select open with wine.

Follow the steps and it should install.

---

### Post by realzippy on 2009-08-18
> **riazrahaman said:**
> If you don't yet have wine, install wine

sudo apt-get install wine

next download the itunes for windows binary.

Right click on the itunes.exe file and select open with wine.

Follow the steps and it should install.


Please read whole thread before posting !

---

### Post by thenailedone on 2009-08-18
> **realzippy said:**
> Pease read whole thread before posting !

Just a bit of over zealousness from a new forum member ;)

Don't want to thread jack but seeing as this thread is still active and has veered slightly off-topic (into the topic I need some answers too)...

For Amarok to work with an ipod... are there specific versions it works with (I have a Touch) and do you need a specific version of Amarok (I have version 2.0.2)... cause I am using the tutorial [here]("http://www.simplehelp.net/2007/07/04/how-to-use-amarok-to-manage-your-ipod-in-ubuntu/") and it not working for me so far :(  (Can't get to the settings for Media Devices as stated in step 2)


Cheers
Neil

---

### Post by realzippy on 2009-08-18
"Don't want to thread jack"

..you do.
Have you ever connected your Ipod to a Windows Itunes installation?
If not,the Ipods filesystem isn't converted from apple's HFS+ to
FAT32 yet...and cannot be read until you install **hfsplus**
and connect to a MAC to disable journailing..
Gparted is another way....

BTW maybe you better use 1.4.xx of amarok....heard about many bugs in new version...tutorial is 2 years old!

---

### Post by thenailedone on 2009-08-18
> **realzippy said:**
> "Don't want to thread jack"

..you do.Threadstarter did not ask about ipods...
Have you ever connected your Ipod to a Windows Itunes installation?
If not,the Ipods filesystem isn't converted from apple's HFS+ to
FAT32 yet...and cannot be read until you install **hfsplus**
and connect to a MAC to disable journailing..
Gparted is another way....

BTW maybe you better use 1.4.xx of amarok....heard about many bugs in new version...tutorial is 2 years old!

:) your right he didn't... then again he didn't ask anything about amarok either ;) ... thx for advice, but just found info [here]("http://amarok.kde.org/wiki/Media_Device:IPod") and ipod touch is a no go... oh well...

*edit: and yes, Amarok 2 not playing along nicely at all... doesnt even play a single song in my library (Rhythm Box works 100%)...*

---

### Post by realzippy on 2009-08-18
...just corrected.He indeed asked about Ipod shuffle.
Still there,accodata?

---

### Post by accodata on 2009-08-18
I am still here, yes I do have a ipod shuffle

still can't get it to work with Amarok... any other suggestions

---

### Post by dtoronto on 2009-08-18
itunes doesn't work extremely well with WINE, you'll want to check the app db for wine BEFORE you start trying to dual layer random windows apps.  WINE is still new and isn't the magic fix all to run all your windows apps.  You're way better off finding one of the Open Source music management apps off the repos.

---

### Post by realzippy on 2009-08-19
Have you ever connected your Ipod to a Windows Itunes installation?
If not,the Ipods filesystem isn't converted from apple's HFS+ to
FAT32 yet...and cannot be read until you install **hfsplus**
and connect to a MAC to disable journailing..
Gparted is another way....

BTW maybe you better use 1.4.xx of amarok....heard about many bugs in new version...tutorial is 2 years old!

---

### Post by NotJustANewbie on 2009-08-19
I used to use Amarok for my ipod but now the new version sucks, I'm using Rhthmbox which actually works pretty well, just dragging and dropping :) V fast too

---

### Post by Sidthedeviant on 2010-02-24
I tried installing the itunes v7.2 from the link earlyer in this thread, however now I am recieving an error : Quicktime was not found, tried reinstalling or repairing but to no avail. has anyone else run into this

---

