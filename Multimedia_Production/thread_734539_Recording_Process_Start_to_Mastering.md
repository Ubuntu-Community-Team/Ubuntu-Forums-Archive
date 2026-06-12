---
title: "Recording Process: Start to Mastering"
date: 2008-03-24
forum: Multimedia Production
---

### Post by otheracco on 2008-03-24
I'm looking for one great post or a few on the entire recording process.  From start to finish, including how to export songs keeping stereo (if necessary), and which programs to use at which stages of the process.

What program do you use to add EQ and/or effects?
What program is used for mastering?
What's the best program to editing?
etc, etc, etc...

If I'm completely missing a sticky, please forgive me, but I didn't see one stickied nor did I find a thread like this in a search.

Thanks!

---

### Post by robeast on 2008-03-24
Someone could probably fill a few books trying to answer your question! The first link in my sig is a good place to start if you are new to recording in Ubuntu. Here's a quick list for you:
Ardour - multitrack recording and editing (free ProTools)
Rosegarden - midi sequencing, composition, notation (MusE is similar)
ZynAddSubFX - software synthesizer (there are many more of these)
JaMin - mastering software
Creox - guitar effects processor

That should get you started. What type of recordings are you planing to make?

---

### Post by otheracco on 2008-03-25
> **robeast said:**
> Someone could probably fill a few books trying to answer your question! The first link in my sig is a good place to start if you are new to recording in Ubuntu. Here's a quick list for you:
Ardour - multitrack recording and editing (free ProTools)
Rosegarden - midi sequencing, composition, notation (MusE is similar)
ZynAddSubFX - software synthesizer (there are many more of these)
JaMin - mastering software
Creox - guitar effects processor

That should get you started. What type of recordings are you planing to make?

Thank you for your input.

Most of it will be with distorted guitar, but a good portion acoustic.  I'll check out Creox, I've been using a few things from JackRack and it's pretty amateur, so I've been recording guitars mic'd.  Everything goes through my Presonus Firepod.
For bass, I DI and/or mic per track with a rack mount basspod XP pro.
Vox are on a cheap condensor mic that was a pack in with my firepod.

In short, it's all real instruments with drums from Hydrogen.

---

### Post by robeast on 2008-03-25
In that case you should go straight for Ardour. Creox is also kinda cheap sounding, but if you play with it you can get some nice effects. I'd recommend using it as an effects processor while you're recording if you need that extra ambience to really rock out and lay down the track you want, but simply route that signal into your monitors and only the dry signal into Ardour. Then you can add some nicer LADSPA or VST plugins in Ardour and tweak them until your ears bleed :)

---

### Post by Stochastic on 2008-03-26
For guitar effects Creox does do the job but I'd much sooner recommend JackRack.  It has many more effects available (the LADSPA set) .  Other than that, Robeast is spot on - Ardour is your best friend.  And once you've gotten the tracks laid, the effects on, and the mix right, head for Jamin to give your tracks polish and umph (particularly the acoustic stuff).

---

### Post by otheracco on 2008-03-26
Both of you, you don't even know how much of a help this is.  I now have clarity on the process.

Thank you both very much!

One thing just occurred to me however.  The one piece I'm missing is a program that will allow me to EQ each instruments soundspace.  As an example, I want to see which frequencies each instrument is using and adjust the EQ from there.  For the drums, I want to adjust for the kick, ride, and snare to add clarity to everything.  Of course I would also want to view frequency for every other instrument and adjust into individual soundspace as well.

Which program would I use for this?

---

### Post by robeast on 2008-03-27
Jamin has a real-time spectrum graph, parametric EQ, 32 band constant Q EQ and three band compressor. Obviously for mastering, but you could pipe a track from Ardour though Jamin and back into Ardour to make use of those great filters and compressors.

---

### Post by otheracco on 2008-03-27
Thanks.  So what's the best place to adjust levels?  

> **robeast said:**
> Jamin has a real-time spectrum graph, parametric EQ, 32 band constant Q EQ and three band compressor. Obviously for mastering, but you could pipe a track from Ardour though Jamin and back into Ardour to make use of those great filters and compressors.

---

### Post by Stochastic on 2008-03-27
> **otheracco said:**
> Thanks.  So what's the best place to adjust levels?

adjust the levels of what?  Ardour has a mixer (alt+m) that can be fully automated for each track.  Or do you mean EQ levels?

Also on the eq note, there are many LADSPA plugins that do various eq things and this would work much faster than routing to jamin and back to ardour, plus you would have full automation control if implemented in an ardour session.  The downside is that the plugins don't give you visual feedback of the signal changes (though you could easily set this up with an external app like jamin or freqtweak).

---

### Post by otheracco on 2008-03-27
> **Stochastic said:**
> adjust the levels of what?  Ardour has a mixer (alt+m) that can be fully automated for each track.  Or do you mean EQ levels?

Also on the eq note, there are many LADSPA plugins that do various eq things and this would work much faster than routing to jamin and back to ardour, plus you would have full automation control if implemented in an ardour session.  The downside is that the plugins don't give you visual feedback of the signal changes (though you could easily set this up with an external app like jamin or freqtweak).

Actually I didn't explain myself well enough.  What I'm really trying
to ask is how to get the right levels when running the drums right from
Hydrogen.  I have it maxed right now and am getting distortion, yet
the drums are still too quiet in the mix.

Should I import them into Ardour?  How can I keep the panning
when importing though?

I think I know how to import them into different tracks already.  I believe it's all done through JackConnect.

While I'm at it, I wonder if you could tell me how to set a 'count-in'.  I don't see
any options for it in Ardour, and it's kind of a glaring ommission if there's no way to do it.  Is there a count-in?

Do you usually run things through JaMIN more than once, or is it that when your at that point you don't go back?

thanks for your expertise!

---

### Post by robeast on 2008-03-27
> **Stochastic said:**
> 
Also on the eq note, there are many LADSPA plugins that do various eq things and this would work much faster than routing to jamin and back to ardour, plus you would have full automation control if implemented in an ardour session.  The downside is that the plugins don't give you visual feedback of the signal changes (though you could easily set this up with an external app like jamin or freqtweak).

Nice, why didn't I think of that? You can use EQ plugins on your tracks in Ardour and simply route the signal from a track into Jamin for the spectrum graph.

You typically will only use Jamin as a mastering program, so you run your final mixdown through it and tweak the spectrum of everything at once to balance it out in the way you think sounds best.

There's definitely a count-in somewhere. There are Punch-in and Punch-out buttons next to the clock in Ardour, which you're probably going to want to use with the count in.

---

### Post by otheracco on 2008-03-27
This is great, even though I'm utterly overwhelmed by the sheer multitude of plugins, I'm using the 'multiband eq' and it really makes a difference.  Still, my head is spinning from not knowing which ones would be good for me to use.  It would take months just to go through them all!

Now all I need are the secrets and shortcuts of eq'ing different instruments to put them in there own soundspaces.

Thank you both for your invaluable help!

---

### Post by robeast on 2008-03-27
The Multiband EQ is one of my go-to-plugins for cleaning up some unwanted frequencies on a track. Definitely take some time to look through the whole list and try anything that catches your eye. It is extremely long...I found an awesome new plugin yesterday but I didn't save my settings in Jack Rack and I can't find it!

---

### Post by Stochastic on 2008-03-28
You could easily shorten the time of experimenting with plugins if you do a little documentation reading.  [http://www.ladspa.org/](http://www.ladspa.org/) links to the developers sites, many of which give a detailed description of what each plugin does.  Though trial and error is always fun.

As for learning freqency space you might want to do a little reading as well.  At this site [http://www.psbspeakers.com/audio-topics/The-Frequencies-of-Music](http://www.psbspeakers.com/audio-topics/The-Frequencies-of-Music) they give this nifty little chart of instruments' frequencies. [IMG]http://www.psbspeakers.com/Images/Audiotopics/fChart.gif[/IMG]  There are lots of these floating around the net.

Here's a well written article that focuses a bit more on the drumkit: [http://www.soundonsound.com/sos/aug01/articles/usingeq.asp](http://www.soundonsound.com/sos/aug01/articles/usingeq.asp)

But keep this in mind too: one could spend a lifetime understanding the whole recording/mastering process if they really wanted yet still not know how to make good music.  Others make awesome music in their garage with a four-track tape recorder.

---

### Post by otheracco on 2008-03-28
:) Stochastic, that last sentence is pure gold!

Fortunaltely for me, I learned how to good music long ago, I'm just behind on recording.

Wow, what a great reply.  I think I'm ready to embark on my journey now.  I can't wait to start reading these sites you gave me, in fact, I'm not gonna wait, cause I'm reading them right now.

That chart is like a fair maiden on a sea voyage, ahh visual aids are nice.

Thank you so much for all the help you two!  I'm glad there are people who are willing to help, it would be a much longer learning process without :)

---

