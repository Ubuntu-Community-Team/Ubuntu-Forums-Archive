---
title: "how do i save a denemo music score as PDF?"
date: 2008-03-08
forum: Multimedia Production
---

### Post by Th3Professor on 2008-03-08
(question in subject)

thanks!

(EDIT: "Export PDF" doesn't do it.)

---

### Post by Stochastic on 2008-03-09
I've never used Denemo (how is it?) but from their website it states > Denemo exports its internal xml format to LilyPond and ABC music notation formats.
And once you have a LilyPond file (probably a .ly extension) simply do ```
lilypond <filenamehere>
``` and it should give you both a pdf and ps file of your music.  I personally just code straight into lilypond files myself as you can do unimaginable things with lilypond once you learn how. See [http://lilypond.org/web/](http://lilypond.org/web/)

---

### Post by Th3Professor on 2008-03-10
Hi, thank you for that input.

I tried it out, and some variants of it, but no luck.

Here's the result of trying it out...

```

$ lilypond file.ly 
GNU LilyPond 2.10.25
Processing `file.ly'
Parsing...
error: Incorrect lilypond version: 2.6.0 (2.7.38, 2.10.25)
error: Consider updating the input with the convert-ly script
file.ly:105:955: error: syntax error, unexpected
file.ly:105:1181: error: syntax error, unexpected
file.ly:105:1424: error: syntax error, unexpected
file.ly:108:8: error: errors found, ignoring music expression
file.ly:116:16: error: syntax error, unexpected
error: failed files: "file.ly"
$
```

I tried an update, no luck.

The printout above shows 2 conflicting versions of LilyPond. I'm guessing 2.10.25 is the LilyPond app and "2.6.0 (2.7.38, 2.10.25)" is the version that was associated with the Denemo app when I used Denemo to convert the file (actually just "save as") into LilyPond format. The parantheses has 2.10.25, so you'd think it wouldn't conflict. A bit confuzzled there.

I'll keep fishing around with it but welcome all ideas. Thanks again :)

---

### Post by heffo_j on 2008-03-11
Hi,

I've used Denemo and had trouble with it simply disappearing after a half hour of input. Bingo! Gone!! Same with its predecessor Notedit. 

I now use Nted (which starts from the command-line). It has an "export to .ps" option under the "file" menu. This program has worked well for me.

I also use under Wine, Finale Notepad 2008. Its free and does the job too.

Regards
John

---

### Post by Stochastic on 2008-03-11
> **Th3Professor said:**
> 
The printout above shows 2 conflicting versions of LilyPond. I'm guessing 2.10.25 is the LilyPond app and "2.6.0 (2.7.38, 2.10.25)" is the version that was associated with the Denemo app when I used Denemo to convert the file (actually just "save as") into LilyPond format. The parantheses has 2.10.25, so you'd think it wouldn't conflict. A bit confuzzled there.

I'll keep fishing around with it but welcome all ideas. Thanks again :)

Well I'd open up your file.ly in your favorite text editor and find the line that looks like this ```
\version "2.6.0"
``` and change it to be ```
\version "2.10.25"
```
This isn't a proper fix, just a hack fix really and as a result you may see some further errors.  It looks like Denemo is just a GUI frontend for two really powerful (and elegant) music notation scripts.  It also looks like Denemo is a little on the flaky side if it can't give appropriate lilypond code - or as heffo_j noted, crashes regularly.

---

### Post by Th3Professor on 2008-03-12
> **heffo_j said:**
> Hi,

I've used Denemo and had trouble with it simply disappearing after a half hour of input. Bingo! Gone!! Same with its predecessor Notedit. 

I now use Nted (which starts from the command-line). It has an "export to .ps" option under the "file" menu. This program has worked well for me.

I also use under Wine, Finale Notepad 2008. Its free and does the job too.

Regards
John

Hey, yeah I've used both notedit and finale's notepad, and the full-legit version of finale (which is nice), though I'm not fond of WINE. I'll look into Nted.

I noticed Rosegarden has a notation feature, though on opening it up it wouldn't let me access the notation feature, not sure why.

> **Stochastic said:**
> Well I'd open up your file.ly in your favorite text editor and find the line that looks like this ```
\version "2.6.0"
``` and change it to be ```
\version "2.10.25"
```
This isn't a proper fix, just a hack fix really and as a result you may see some further errors.  It looks like Denemo is just a GUI frontend for two really powerful (and elegant) music notation scripts.  It also looks like Denemo is a little on the flaky side if it can't give appropriate lilypond code - or as heffo_j noted, crashes regularly.

I figured out the issue with Denemo... I had to remove the text I added to the notation. I used "lyrics" and apparently it disagrees with that in the conversion process.

After removing the text I tried the "Export PDF" option again, and bingo... it worked. Perfect. (Almost... I just wish it'd work with the inserted text.)

---

