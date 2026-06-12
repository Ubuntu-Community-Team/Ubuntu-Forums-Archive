---
title: "MP3Gain GUI"
date: 2007-01-02
forum: Multimedia &amp; Video
---

### Post by Balaam's Miracle on 2007-01-02
Hey everyone,

I'm an Ubuntu user since early december, before this i have been using Windows since Windows 3.1 so i'm pretty much a GUI addict.
For a GUI addict i think i hold myself up pretty well in Linux :-)

Anyway, here's my question: In Windows, i used MP3Gain quite extensively but there it has a GUI. In Linux i have yet to find a GUI frontend for MP3Gain, if there is one at all, so i was wondering how hard it would be to build one myself.

I do have Glade installed, but am not sure if that will do what i want. The idea i have is to build a standalone GUI that will pass the switches and variables to the command-line version of MP3Gain.
Would this be doable for someone with hardly any programming experience? If so, what would my first steps be bcause i don't know how to start.

---

### Post by Checketts on 2007-01-05
This JavaMp3Gain user interface works: [http://www.step.polymtl.ca/~guardia/javamp3gain.php](http://www.step.polymtl.ca/~guardia/javamp3gain.php)

I've only just found it. Also, you probably would like this [post about MP3Gain]("http://ubuntu.wordpress.com/2006/09/11/normalize-the-gain-playback-volume-of-your-mp3s/") over on the ubuntu blog. ([http://ubuntu.wordpress.com/2006/09/11/normalize-the-gain-playback-volume-of-your-mp3s/](http://ubuntu.wordpress.com/2006/09/11/normalize-the-gain-playback-volume-of-your-mp3s/))

---

### Post by Balaam's Miracle on 2007-01-05
Thanks for the tip, but i'm currently already using JavaMP3Gain. However, i'm sorry to say that it's not nearly as complete as the Win32 version.

In the Win32 version of MP3GainGUI, about all the options that are available from the commandline have their GUI equivalents.
When loading one or more files, the files are automatically analyzed and the results are shown in the GUI. Volume levels are calculated and converted to dB (i've set all my files to 93dB, which is loud enough to give it some more "oomph", but not too loud). The process priority can be set (useful when doing a lot of files), etc.
I'm afraid that there's hardly any hope of JavaMP3Gain looking or functioning more like the Win32 version any time soon, since the last version of JavaMP3Gain dates from 2004.

I was hoping that i could use the MP3GainGUI (win32) in wine, but it complains about some stupid .OCX file that's not correctly registered, even though i did a full install which includes the VB libs.

Anyway, that's why i was hoping i could make a GUI for Linux myself, to get some of the ease-of-use back that i have grown so accustomed (sp?) to.

---

### Post by stokedfish on 2007-04-19
There's another GUI as well...

[http://forum.ubuntuusers.de/topic/74902/](http://forum.ubuntuusers.de/topic/74902/)

;)

---

### Post by H3retic on 2008-04-07
It's not the prettyest of fastest, but the windows version runs under Wine...

---

### Post by Balaam's Miracle on 2008-04-09
Nope, it's still complaining about the unregistered .OCX file on my end.

However, i have found a (non functional) wxWindows version of the MP3gain GUI at
[http://mp3gain.cvs.sourceforge.net/mp3gain/mp3gainwx/](http://mp3gain.cvs.sourceforge.net/mp3gain/mp3gainwx/)
Maybe some programmer can get this one to work? Because the development of this version seems to have halted.

---

### Post by Giantics on 2008-04-13
Why running the Wine-Version or completing the wxWidgets Version?

Haven't you seen this message?
[Click]("http://ubuntuforums.org/showpost.php?p=4604999&postcount=7")
:-)

Giantics

---

### Post by Balaam's Miracle on 2008-04-13
Wow, i love easyMP3Gain!!! It's fast, it's GTK+ and it should be in the Ubuntu repositories!!!!

Just a suggestion though, have it accept files and folders as agrument and you're golden.
Oh, and support for gettext translations would also be a great idea, because not everyone understands Egnlish and/or German.

---

### Post by Giantics on 2008-04-15
Thank you!

> Just a suggestion though, have it accept files and folders as agrument and you're golden.

Isn't this a feature just terminal programs should have;-) ?
Would you use it? Therefore the GUI has the capability of adding files by both menu and Drag&Drop. I'm going to put it on my to-do-list.

> Oh, and support for gettext translations would also be a great idea, because not everyone understands Egnlish and/or German.

I didn't know "gettext", sounds interesting, but unfortunately Lazarus (my Developing IDE) doesn't support gettext, yet.  However if someone wants to translate the GUI, it can be done easily by just modifying the german-language-file. The file is self-explanatory. Try it, send it to me and I will upload it :-)

Giantics

---

### Post by Balaam's Miracle on 2008-04-15
> **Giantics said:**
> 
Isn't this a feature just terminal programs should have;-) ?
Would you use it? Therefore the GUI has the capability of adding files by both menu and Drag&Drop. I'm going to put it on my to-do-list.


I like to add apps that i often use to my right-click menu in Nautilus. For instance, i have added Audio Tagtool so that i can quickly edit ID3 tags, and Cream so that i can quickly view and/or edit textfiles.
Since i have a radio show on the local radio station, easyMP3Gain would be used that way at least once a week, but usually more often.

> 
I didn't know "gettext", sounds interesting, but unfortunately Lazarus (my Developing IDE) doesn't support gettext, yet.


Did you ever wonder how comes that all your apps are automatically translated to the language you are using? The answer to that is gettext.
Gettext is what creates .po and .mo files, which are used to translate applications and documentation, so that when you install application XYZ on a computer with language ABC, the correct translation gets applied without user intervention.
I'm no programmer (just a translator), but i wouldn't be surprized if gettext worked roughly the same way as your solution. With that i mean that it will replace certain strings in your code that are marked as translatable. But one of the biggest advantages of using gettext would be allowing for translations to be made through LaunchPad whereas the system you are probably doesn't.

If you want to explore the struture of these gettext .po files, just go to [http://translations.launchpad.net](http://translations.launchpad.net), pick a file and click "download" from the actions menu.

> 
However if someone wants to translate the GUI, it can be done easily by just modifying the german-language-file. The file is self-explanatory. Try it, send it to me and I will upload it :-)


I think i will wait a bit until easyMP3Gain is in the repositories :-)

---

### Post by kahlil88 on 2008-05-18
Is there a front-end that also supports Vorbis? Preferably GTK as well. It would also be nice to auto-adjust the volume like MPTrim (Windoze shareware).

---

### Post by Giantics on 2008-05-21
I think there is no front-end that supports both mp3 and vorbis.
I'm working on vorbis-support for easymp3gain at the moment (perhaps I should rename it ;-))
However it will take a few more months.

---

