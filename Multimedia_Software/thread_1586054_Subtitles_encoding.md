---
title: "Subtitles encoding"
date: 2010-10-01
forum: Multimedia Software
---

### Post by jl2035 on 2010-10-01
I fount very little about this issue on web. It's bothering me, since I started to use Linux. 

In my language(Slovenian), and some others there are some special characters: like &#268;,Š,Ž,&#269;,š,ž ... and these are pretty important. 
So when I download any movie subtitles file it has these characters distorted. Like this:

[IMG]http://nikotomic.com/Jaka/screenshot_subs.jpg[/IMG]

Everytime I want to watch a movie I have to use gedit and the "Replace all" option to manually fix subtitles, and save the file in utf-8.

I would like to write an application that does this same thing, but I don't know how linux gets these letters. If I open subs in gedit or nano or OpenOffice, they are represented differently...

So how do I solve this confusion?

---

### Post by lovinglinux on 2010-10-01
Which application are you using to watch the movies?

You can change the default encoding in the player settings, in order to display the characters correctly.

---

### Post by jl2035 on 2010-10-06
Yeah but it was already set to utf-8 in MoviePlayer and VLC Player.

---

### Post by lovinglinux on 2010-10-06
> **jl2035 said:**
> Yeah but it was already set to utf-8 in MoviePlayer and VLC Player.

Try smplayer. I had a problem with a single subtitle that was encoded in UTF-8 instead of ISO-8859-1and was behaving like yours. I changed the default encoding to UTF-8 and selected the option to autodetect my language. It worked like a charm and the subtitles encoded with ISO-8859-1 works as well.

---

### Post by jl2035 on 2010-10-07
Whoa! Smplayer is great... Now my problems with subtitles are over...

---

### Post by lovinglinux on 2010-10-07
> **jl2035 said:**
> Whoa! Smplayer is great... Now my problems with subtitles are over...

Whoa!

Smplayer is really great indeed.

---

### Post by SeijiSensei on 2010-10-07
I really wish a mainstream distribution would adopt SMPlayer as its default media player.  It's just a pleasure to use.  If you want to keep up with new developments in smplayer, you can use the version rvm distributes from his Launchpad repository: [https://launchpad.net/~rvm/+archive/ppa](https://launchpad.net/~rvm/+archive/ppa). He has more up-to-date versions of mplayer there as well.

---

### Post by jl2035 on 2010-10-07
I'm surprised I never heard about it...And yes why is it not in the main ubuntu distribution - it's much better and friendly than Totem. 

I had these problems for more than two years now...I can't belive it's over!  :guitar:

Thanks

---

