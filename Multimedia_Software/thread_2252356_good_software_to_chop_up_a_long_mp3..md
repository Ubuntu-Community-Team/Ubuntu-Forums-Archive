---
title: "good software to chop up a long mp3."
date: 2014-11-11
forum: Multimedia Software
---

### Post by Arminius on 2014-11-11
I've got a 15 hour mp3, need to turn it into 15 different mp3 files that are each 1 hour long.
What's the best software to do that?

---

### Post by VMC on 2014-11-11
Maybe Audacity: [http://audacity.sourceforge.net/about/](http://audacity.sourceforge.net/about/)

---

### Post by FakeOutdoorsman on 2014-11-11
"**mp3splt** is a free command-line utility that allows you to split mp3, ogg vorbis and native flac files from several splitpoints, without need of decoding and reencoding. It is useful to split large mp3, ogg vorbis and native flac to make smaller files or to split entire albums to obtain original tracks."

Untested example:
```
mp3splt -t 60.00 audio.mp3
```
There is also **mp3splt-gtk** if you prefer GUI.

---

### Post by monkeybrain20122 on 2014-11-13
[https://apps.ubuntu.com/cat/applications/mp3splt-gtk/](https://apps.ubuntu.com/cat/applications/mp3splt-gtk/)

Edited: As fakeoutdoorsman said.

---

### Post by Bucky Ball on 2014-11-13
> **VMC said:**
> Maybe Audacity: [http://audacity.sourceforge.net/about/](http://audacity.sourceforge.net/about/)

Definitely Audacity. Used by pros and hobbyists alike. A swiss army knife of audio. Can't go past it.

Install from the Software Centre or Synaptics. It's in the repos. Will do what you're after with ease. You just need to get used to using it (which really isn't hard). 

Enjoy! ;)

PS: A tip: Mark out the section you want and 'trim' it. Save that as an MP3. Hit ctl+z and that will give you the whole audio file back again. Same with the next bit, and the next. There are other ways of doing this in Audacity, and sure you'll find what works best for you.

---

### Post by FakeOutdoorsman on 2014-11-13
Audacity is nice, but for this type of task it sounds tedious. I'm not sure if it can handle such a long file (15 hours), and also it would need to decode the whole file and re-encode each segment resulting in generational quality loss. mp3splt may address all of these issues.

---

### Post by shantiq on 2014-11-14
This might be of use if one chooses Audacity ; you can also boost the sound volume-wise treble bass filters the lot
Adapt to suit your needs here...


How can I split a long recording into multiple files or CD tracks?    

If you have a long file/image with no cue or a Bluray PCM image or for personal use a radio program and you want to trim the chat out or a fifteen-hour mp3




[IMG]http://s20.postimg.org/yq90qiexp/silence_finder.png[/IMG]


> [COLOR=DarkSlateGray]Follow these steps to create a separate file for each song or segment of a long recording. This is particularly useful if you are creating a CD, since each file will appear as a separate track on the CD.


Click to place the cursor at the start of the first song.
Choose &#8220;Add Label at Selection&#8221; from the Project menu (or Tracks menu in Audacity Beta). If you wish, you can type the name of the song.
Repeat steps 1 and 2 for each song.
When you are finished, choose &#8220;Export Multiple&#8221; from the File menu. When you click the &#8220;Export&#8221; button, Audacity will save each song as a separate file, using the format and location you choose.
Alternatively, Audacity can attempt to detect the silences between tracks then label them automatically using Analyze > Silence Finder. If you do not have Silence Finder in your version of Audacity, it can be found in the Audacity legacy 1.2.6 Plug-in Pack.[/COLOR]




PS   


1- Be careful  as sometimes silences might also exist in the middle of a song **so check before labelling**
2- >>Tracks/Edit Labels
3- Then to save >>File/**Export Multiple** SHIFT+CTRL+L

---

