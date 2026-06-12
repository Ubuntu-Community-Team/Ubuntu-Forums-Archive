---
title: "Any ideas on how to time scale audio?"
date: 2008-12-19
forum: Multimedia Software
---

### Post by brundlelinux on 2008-12-19
I'm looking for an audio app or plugin for Amarok that will allow for time scaled playback while still keeping the original pitch of the audio.  I currently use Amarok 1.4 (Amarok 2.0 is a little bare for me), but I'm willing to install a secondary audio app if I can get this functionality.

An older portable media device I had about 10 years ago had this ability, so I know it exists and it's possible. 

Anybody know of any apps or any plugins for apps that can satisfy my needs?

---

### Post by tgalati4 on 2008-12-19
```
man mplayer

mplayer -speed 1.2 boring_podcast.mp3
```

This will play a boring podcast 20% faster.  Pitch is not preserved, nor is podcast any less boring.

Audacity has a speed/pitch filter, but intelligibility gets  lost over 30% increase.

---

### Post by brundlelinux on 2008-12-20
Hmmm.  Perhaps I wasn't specific enough.

I need to slow audio down, not speed it up, and this is for music files.  I'm a musician and I want to use this tool to help figure out how to play some technical fast measures in music, so the pitch aspect is very important.  And, of course, since I'll be doing this on a routine basis with many different files, it needs to be GUI-oriented, not terminal.

But thanks for the info.  Sorry I wasn't more specific to start with.

---

### Post by draffel on 2008-12-20
If your a musician you might want to give Audacity try [http://audacity.sourceforge.net/](http://audacity.sourceforge.net/)

It's an open source free multi-track audio editor and recorder that has a protools-esque feel to it.  you can do what your asking and more.

Cheers -D

---

### Post by brundlelinux on 2008-12-20
Eh, just gave it a try or 5.  Audacity is nice, but the speed scaling has pitch-shifting built in.  The stand-alone pitch shifting is pretty low quality as well.  To get what I need, I'd have to work with each track individually to first slow it down, the readjust the pitch back up, with the end result being less than desirable.

What I need is something that works on-the-fly by just clicking a checkbox or something for 3/4, 1/2, 1/4 etc etc time scale with my pre-existing library.

Thanks though.

---

### Post by andrew.46 on 2008-12-20
Hi,

Certainly the svn MPlayer can do this, not sure if the repository version can, by using the audio filter scaletempo. There is the usual bewildering range of sub-options but basic usage is:

```
$ mplayer -speed 0.5 -af scaletempo myfile.mp3
```

and  this will play at half speed and maintain the original pitch, even if the audio is subsequently made faster. The -speed option, which I can see has been mentioned before, has a range of 0.01-100 with integers less than 1.0 representing slowing and greater than 1.0 speeding up.

Obviously this is not a gui, as requested, but the best software is CLI :-).

Hope this helps,

  Andrew

---

### Post by n8chz on 2013-05-05
```
rubberband -t 2 bowonke.ogg bowonke2.ogg
```

---

### Post by tgalati4 on 2013-05-05
This is an old thread that will get closed shortly, but thanks for the tip on *rubberband*.

---

### Post by wildmanne39 on 2013-05-05
Thread closed. Please do not post in old threads.

---

