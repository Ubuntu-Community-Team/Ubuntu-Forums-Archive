---
title: "Midi for ubuntu?"
date: 2008-04-15
forum: Multimedia Production
---

### Post by TBOL3 on 2008-04-15
i like to compose songs.  However, as some composers may know, it is difficult to impossible to get people to play your songs.  And usually, if you do get people to play it for you, you either know them well and the songs sound horrible, or you are paying lots of $$$.

Well, neither of these are options (true I can play the piano, and I have access to a few people that play other instruments well), but I don't have enough people to play a piece for me.

Thus I am forced to resort to a midi file with some touch up in other programs to make it sound nicer.  (Yes I do know that midi files that are automatically generated sound like crap, or cool old video games).

But the problem comes with getting the midi at all.  Yes, I have kMid, alsa, timidity, rosegarden, and jack (but I can't get jack to work properly).  But the quality of the midi file pails in comparison with something that would be played on windows' soft synth.

The main problem comes from lack of voices.  For example, there is no viola.  Sure, you can pick one out of the menu, but it won't make any noise whatsoever.  (I particularly need this instrument).

So, is there anything I can do about these lost voices?  Or am I stuck to going back to some proprietary program to get them?

Thank You

---

### Post by eric71 on 2008-04-16
You should send Rosegarden's midi output to Qsynth which uses soudfonts. Download a good GM soundfont (something like those found here: [http://www.personalcopy.com/linuxfiles.htm](http://www.personalcopy.com/linuxfiles.htm)). Load this up in Qsynth and things should sound a bit better.

---

### Post by TBOL3 on 2008-04-16
Thank you, but I still can't get it to work.

I have qsynth and the soundfont installed.  However, every time I start up jack, I can't get any sound out of rosegarden.  I had rosegarden streaming to qsynth, and qsynth streaming to alsa.  But it won't work.  (BTW, rosegarden strait to alsa doesn't work either).

Could you help me?

Thank you.

---

### Post by heartburnkid on 2008-04-16
You know, I was never able to get qsynth to work either.  I ended up switching over to Timidity, because I was able to find a more detailed how-to for that here: [https://help.ubuntu.com/community/MidiSoftwareSynthesisHowTo](https://help.ubuntu.com/community/MidiSoftwareSynthesisHowTo)

One thing that it doesn't mention is that you may have to reboot once you've done all the work to set Timidity up as a server.  I spent quite some time scratching my head over it, and then I shut down my machine, and the next time I started back up, it just worked.  Go fig.

---

### Post by TBOL3 on 2008-04-16
So, is sf2 a form of sfArk?

---

### Post by TBOL3 on 2008-04-16
Thanks, I got it to work.  I'm guessing that sf2 is the same format, but not proprietary compressed?

Now, here comes the search for a decent soundfont, (rolls eyes).

BTW, can you combine soundfonts?  When I added the first on, timidity let go of the original sounds altogether.  If so, how do I tell timidity which instrument to pick over another?

Thank You

---

### Post by kayosiii on 2008-04-18
Could you install and open "patchage" after starting jack....
you can use this to check that the audio and midi routing is correct - the gm-midi out port on Rosegarden should go to qsynths midi input (labeled fluidsynth here) port and the audio outputs of qsynth should be routed to your soundcards output ports (click and drag from one port to another to connect them).

Make sure that qsynth is set to jack and the sample rate matches the one set in Jack. If the above steps don't work try running the Virtual Midi Keyboard
and routing that to the input midi port for qsynth.

---

