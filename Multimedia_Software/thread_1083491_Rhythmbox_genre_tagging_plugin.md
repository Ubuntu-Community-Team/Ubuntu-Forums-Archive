---
title: "Rhythmbox genre tagging plugin"
date: 2009-03-01
forum: Multimedia Software
---

### Post by karldiechmann on 2009-03-01
Hi all,

I've started to feel that the genre classification system in standard music players is rather limited.  For example, Wikipedia describes Led Zeppelin's Physical Graffiti as "Hard rock, heavy metal, blues-rock, folk rock".  A one-genre classification system cannot capture this breadth of performance.

I would like to write a plugin for Rhythmbox that allows multiple genres to be tagged to a single song, thus allowing the example album above to be listed in all the categories I have given.  Where would I start looking in the Rhythmbox API to do this?

---

### Post by surratta on 2009-06-17
oh please please please yes

---

### Post by bonfire89 on 2009-11-01
**this would be awesome.** I just started looking into it. It seems as if you separate the genres with slashes, and then do a search for a genre, you'll be able to search any of the genres.

ie. if the the genre field is "rock / hard-rock / metal"

if you search hard-rock it will come up.

---

### Post by deusdiabolus on 2010-01-06
You've probably already looked here, but I'll just drop it in anyway:  
[http://rhythmbox.sourceforge.net/development.html](http://rhythmbox.sourceforge.net/development.html)

You may also want to contact the developers at [http://rhythmbox.sourceforge.net/feedback.html](http://rhythmbox.sourceforge.net/feedback.html) and ask them directly.

None of the registered archives specifically mention tags, but somebody needs to focus on them.

For what it's worth, I think a good solution would be having Rhythmbox identify the major punctuation separators used in multiple genre tags ( , / ; ) and automatically parse them into individual categories, as opposed to listing the tagged tracks in their own space the way it does now.

ADDENDUM:  This may also help you.  [http://live.gnome.org/Rhythmbox/InternalDesign#head-fc7b4e01eab34ce374545333a9caca82f2210dec](http://live.gnome.org/Rhythmbox/InternalDesign#head-fc7b4e01eab34ce374545333a9caca82f2210dec)

---

### Post by Guitar John on 2010-01-06
That would be good.

---

### Post by Bramkaandorp on 2010-03-08
Over a year has passed, and I just stumbled across this problem. Can anyone tell me whether this has been resolved?

On a side note: How can I search by genre specifically? That is, in a similar way in which you search by title (button).

Cheers

---

