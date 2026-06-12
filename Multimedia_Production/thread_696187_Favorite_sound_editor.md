---
title: "Favorite sound editor"
date: 2008-02-13
forum: Multimedia Production
---

### Post by Jacobian on 2008-02-13
I'm looking for a good application for editing sound files. There are a many, many sound editors out there, and some of them could have useful features that are not necessarily obvious at a first glance, so I'm curious to hear what other people use and like.

My reason for wanting a sound editor is that I want to make a simple speech synthesizer. I know about Festival, but I'm not trying to synthesize any of the known languages. My language is phonetic and completely regular with predictable accentuation.

The English speech synthesizers I've heard sound computer generated for arbitrary words. I want something that sounds a little more natural, and I imagine it should be possible given how simple and regular this invented language is.

Here's a really well done synthesizer that's along the lines of what I'd like to accomplish:
[http://www.theparselmouth.com](http://www.theparselmouth.com)

Festival sounds primitive in comparison, although to be fair, Festival is solving a vastly harder problem:
[http://www.cs.cmu.edu/~awb/festival_demos/sounds/intro2.wav](http://www.cs.cmu.edu/~awb/festival_demos/sounds/intro2.wav)

I'd like to produce something simple like the parseltongue synthesizer. My initial approach is to try recording each distinct syllable in my language. Then I would use a sound editor to remove as much noise and standardize the syllable files as much as practically possible, before stringing the syllables together into complete words. I'd like to be able to slightly blend or "smooth" two adjacent syllables so that it sounds like fluent speech, even when the waveforms from the two files don't quite match up.

Once I've gotten that far, I could either simply generate a big library of sound files, one for each possible word, up to a certain syllable length; or, if the sound editor turns out to be scriptable, I could try writing a Java program to convert text into speech in real time. Either way would be satisfactory.

Anyway, I'm curious to hear what other people more experienced than me are using for their sound editors. It doesn't matter if it's a graphical or a command-line sound editor, I'm just curious to hear what you like best and why!

---

### Post by Stochastic on 2008-02-13
My favorite editor is Rezound, just a nice stable editor with good visualization that works efficiently out of the box.  It's not the most powerful in the world, but it's my fav.

---

