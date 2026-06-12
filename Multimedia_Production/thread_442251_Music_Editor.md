---
title: "Music Editor"
date: 2007-05-13
forum: Multimedia Production
---

### Post by ThinkBuntu on 2007-05-13
What are the most popular or best sheet music editors for *nix? I'm looking for one that I can use to compose music, etc, and it needs to be able to add an extensive range of notation...ease of use with slurs, crescendos and the like is greatly appreciated.

And a very nice perk could be the ability to compose from sound automatically with note tolerance. Although I'm on a laptop, I've considered using a line-in with a nicer microphone to compose directly from my performance.

EDIT: Bass, tenor, and treble clef are all necessary!

---

### Post by aysiu on 2007-05-13
The only sheet music program in the repositories is Lilypond: > A program for typesetting sheet music
LilyPond is a music typesetter, an automated engraving system.  It
produces beautiful sheet music using a high level description file as input.

LilyPond supports many forms of music notation constructs, including
chord names, drum notation, figured bass, grace notes, guitar tablature,
modern notation (cluster notation and rhythmic grouping), tremolos,
(nested) tuplets in arbitrary ratios, and more.

LilyPond's text-based music input language support can integrate into
LaTeX, HTML and Texinfo seamlessly, allowing single sheet music
or musicological treatises to be written from a single source.  Form and
content are separate, and with LilyPond's expert automated formatting,
users don't need typographical expertise to produce good notation.

LilyPond produces PDF, PostScript, SVG, or TeX printed output, as well
as MIDI for listening pleasures.  LilyPond is exported from the
RoseGarden and NoteEdit GUIs, and can import ABC, ETF and MIDI.

LilyPond is part of the GNU Project.

 Home Page: [http://lilypond.org/](http://lilypond.org/)
 Authors: Han-Wen Nienhuys <hanwen@cs.uu.nl>
          Jan Nieuwenhuizen <janneke@gnu.org>

---

### Post by drosky on 2007-05-14
> **aysiu said:**
> The only sheet music program in the repositories is Lilypond:

Lilypond is one of the best tools out there for music typsetting, but it's a typesetting language similar in nature to LaTeX, and has no GUI score editor, if that's what you are looking for.  There are, however, two Linux-based programs that can act as front ends for Lilypond.  Theyare Rosegarden and Noteedit.  I think they are both in the Ubuntu repositories; however, the version of Rosegarden is a little out of date (1.4.0 vs. the current stable release 1.5.1).  

Rosegarden is primarily a midi sequencing app, but it does have a usable score editor.  It is good for relatively simple stuff, but is a little awkward to use and is missing some important features, such as the ability to show multiple voices on one staff.  It would be nice if Rosegarden got updated to 1.5.1 in the repository, but I don't know if that will happen, since Ubuntu seems rather conservative about updating app versions within an Ubuntu release.  Of course you can always compile 1.5.1 yourself.

Noteedit on the other hand is mainly a score editor, and has some of the features that Rosegarden is missing, such as multiple voices on a staff.  The author of Noteedit abandoned the project a few years ago, so for a time it had no future; however, it has now been picked up by a new development team which will be carrying on development, re-writing it and changing the name to "Canorus".

They're probably both worth trying to see which you like best.  If your needs don't involve the features that Rosegarden is missing, it is a nice tool because it can easily give you other views of your music besides the score, such as the matrix view.  It also has a nice percussion matrix editor, and has a lot of fine controls over the midi output.  If you're doing complex classical style scores and don't care as much about the rendered midi output, Noteedit might be better.

---

### Post by Ananth on 2007-05-15
Denemo is also a score editor.

It crashes a lot in my system. But worth a try. Again, it's just a score editor. If you want to record audio etc, better try Rosegarden, ardour etc.

Ananth
[http://endoflist.blogspot.com](http://endoflist.blogspot.com)

---

