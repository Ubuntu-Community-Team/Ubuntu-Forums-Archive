---
title: "Composing Sheet Music"
date: 2007-05-14
forum: Multimedia Production
---

### Post by jstritar on 2007-05-14
Are there any good programs for composing sheet music in Linux? Ideally I'd be able to write my sheet music and play it back with a midi player, etc.

---

### Post by tenzindorje on 2007-05-14
There are several solutions.[COLOR="Blue"]_ [Rosegarden]("http://www.rosegardenmusic.com/")_[/COLOR] is included in  [COLOR="Blue"]_[Ubuntu Studio]("http://www.ubuntustudio.com/")_[/COLOR], or can be downloaded using the Synaptic Package manager. Its website describes it:

[FONT="Times New Roman"][I]"Rosegarden is a professional audio and MIDI sequencer, score editor, and general-purpose music composition and editing environment.
Rosegarden is an easy-to-learn, attractive application that runs on Linux, ideal for composers, musicians, music students, and small studio or home recording environments."[/I]
 [/FONT]
There are some issues with Rosegarden - it requires a low-latency kernel -- search for this on the forums. Ubuntu Studio comes with a low-latency kernel.

There is also the[COLOR="Blue"]_ [Brahms sequencer]("http://www.hitsquad.com/smm/programs/Brahms/")_[/COLOR] and[COLOR="Blue"]_ [MuSE ]("http://www.muse-sequencer.org/")_[/COLOR].

[COLOR="Blue"]_[Lilypond ]("http://lilypond.org/")_[/COLOR] is probably the most sophisticated music notation typesetter available (its printed output is considerably better than Finale). It exports notation to PDF files and sound to MIDI files, and can include music notation in HTML web pages. It is a text-based system, although there is a simple notation program called [COLOR="Blue"]_[Denemo ]("denemo.sourceforge.net")_[/COLOR] which, although is not a notation program itself, is a graphical front end to Lilypond and can play back music through CSound.

Besides the sequencer, you might want to look at 
[LIST]
[*][COLOR="Blue"]_[FluidSynth ]("www.fluidsynth.org/") _[/COLOR]
[*]or [COLOR="Blue"]_ [TiMidity++]("timidity.sourceforge.net/")_[/COLOR] for soundfont playback (I prefer fluidsynth),
[*][COLOR="Blue"]_ [QSynth ]("http://qsynth.sourceforge.net/qsynth-index.html")_[/COLOR], a graphical front end to FluidSynth,
[*] and[COLOR="Blue"]_ [QJackCtrl ]("http://qjackctl.sourceforge.net/")_[/COLOR], a graphical front end to JackD, which is a patch bay application to connect all your sequencers, synthesizers, effects, etc.
[/LIST] 

Finally, you can record your music into [COLOR="Blue"]_[Ardour]("ardour.org/")_[/COLOR]

UbuntuStudio includes all of this (except for Denemo???), as well as a huge amount of music (and video) editing software -- all FREE!!! The site's been down, but as of right now (May 14, 2:55 PM CDT), it's UP! There are several posts regarding it on the forums.

---

### Post by drosky on 2007-05-14
> **tenzindorje said:**
> There are several solutions.[COLOR="Blue"]_ [Rosegarden]("http://www.rosegardenmusic.com/")_[/COLOR] is included in  [COLOR="Blue"]_[Ubuntu Studio]("http://www.ubuntustudio.com/")_[/COLOR], or can be downloaded using the Synaptic Package manager. Its website describes it:


Just for completeness, there is another program called Noteedit.  Whereas Rosegarden is first and foremost a midi sequencing app with some score editing capability, Noteedit is intended primarily for score editing, though it does support midi playback for previewing what you are composing.

Noteedit tends to get less attention because it was abandoned by its author a few years ago and was a dead project for a while.  It has recently been picked up by a [[COLOR="Blue"]new development team[/COLOR]]("http://canorus.berlios.de"), however, which will be rewriting major portions of it and changing the name to "Canorus".  They have also done an intermediate bug-fix release under the existing Noteedit name.

Noteedit doesn't give as fine control over the midi output as does Rosegarden, and its interface doesn't look as polished, but it has more score editing features which can be critical or convenient in some cases, such as showing multiple voices on the same staff, and exporting more complete score formatting to Lilypond.

---

