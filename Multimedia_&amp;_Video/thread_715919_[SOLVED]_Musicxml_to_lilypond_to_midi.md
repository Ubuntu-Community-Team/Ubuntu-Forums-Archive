---
title: "[SOLVED] Musicxml to lilypond to midi"
date: 2008-03-05
forum: Multimedia &amp; Video
---

### Post by Paerez on 2008-03-05
Hey all,

I am using musicxml2ly to convert a musicxml document to lilypond format. This spits out lilypond that looks similar to this:

```

\version "2.10.33"
% converted from sample.xml
\include "sample-defs.ly" <<
        \new Staff <<
                \context Voice = "PartPOneVoiceOne"  \PartPOneVoiceOne
                >>
        \new Staff <<
                \context Voice = "PartPTwoVoiceOne"  \PartPTwoVoiceOne
                >>
        >>

```

I would like to export the xml file to midi, so I thought I would pass through lilypond and add a \midi to it and then run lilypond on it to get my midi. But I am really bad at lilypond and I have no clue how to properly add a \midi tag. I have tried putting it at the bottom, adding a \score and putting it in there, etc.

The one thing I can't do is change the lilypond to a non-include style, since that is what musicxml2ly generates.

Utimately, I want to create bash scripts that take musicxml files as input and spit out midis, so it needs to be a quick fix. I don't mind writing some ruby or perl to add in the midi tag, but it has to be relatively simple.

Thanks

---

### Post by Paerez on 2008-03-05
aaaaaannnd I got it:

```
\version "2.10.33"
% converted from sample.xml
\include "sample-defs.ly"
\score { <<
        \new Staff <<
                \context Voice = "PartPOneVoiceOne"  \PartPOneVoiceOne
                >>
        \new Staff <<
                \context Voice = "PartPTwoVoiceOne"  \PartPTwoVoiceOne
                >>
        >>
  \midi { }
}
```

---

### Post by thomasbonte on 2008-03-05
Hi there,
You might want to check MuseScore to convert musicXML to MIDI: [http://mscore.sourceforge.net](http://mscore.sourceforge.net)
I believe it will do a better job than musicxml -> lilypond -> midi If this is not the case, let me know bc I'm curious as well.

update: check out the latest build because musicXML import has been improvement a lot. For windows, take the latest build on [http://prereleases.musescore.org](http://prereleases.musescore.org)

---

