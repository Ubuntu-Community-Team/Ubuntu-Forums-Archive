---
title: "Rhythmbox ID3 tags and Banshee sudden instability"
date: 2010-09-29
forum: Multimedia Software
---

### Post by tancrackers on 2010-09-29
I used Easy Tag to edit my songs' ID3 tags. Banshee reads them fine but Rhythmbox misreads them! For eg., blink 182, Blink 182, and Blink-182!!! Apparently it's because Easy Tag makes ID3v1 tags while Rhythmbox read ID3v4? That's SO stupid! What am I supposed to do now? I saw RB had a bug filed but it got closed because "it's not a problem with rhythmbox, it's a problem with ID3 tags."  RB should be able to read them! That's ridiculous. So how do I fix the tags?

As for Banshee, anyone else move from version 1.6 to 1.7.6? The new one crashes everytime I use it. It's simply awful. And this is supposed to lots of bugs fixed? It's the new stable version? What a joke! How do I fix this now? Or better yet, how to go back to version 1.6?
^ Never mind, I downgraded it.
Still have the rhythmbox problem!

I'm using Ubuntu Lucid 64 bit with Gnome.

---

### Post by ZenQuicker on 2011-03-09
[FONT=Verdana]Rhythmbox loads APE tags first them ID3 so your changes on easy tag will not work

I stripped my music library of APE and my Blink 182 blink-182 Blink-182 problem disappeared next Rhythmbox reload.[/FONT] [FONT=Verdana]

To strip APE I went here: [/FONT] [FONT=Verdana][http://brej.org/blog/?p=143](http://brej.org/blog/?p=143)
[/FONT] [FONT=Verdana] or in terminal type this:

su[/FONT][FONT=Verdana]
wget [http://brej.org/blog/wp-content/uploads/2009/11/ApeTag](http://brej.org/blog/wp-content/uploads/2009/11/ApeTag) -O/usr/bin/ApeTag[/FONT][FONT=Verdana]
chmod a+x /usr/bin/ApeTag
cd Music
ApeTag --delete */*/*/*.mp3 (or various permutations)

then enjoy a cleaned up Rhythmbox experience[/FONT]

---

