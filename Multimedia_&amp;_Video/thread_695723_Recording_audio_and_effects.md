---
title: "Recording audio and effects"
date: 2008-02-13
forum: Multimedia &amp; Video
---

### Post by dcroxton on 2008-02-13
I am very frustrated with the problems of recording audio and applying effects.

I have used Audacity successfully in the past.  Now, I can't record anything to save my life because I keep getting the "Error while opening sound device" error.  I tried all the workarounds I could find.  Installing alsa-oss and running "aoss audacity" actually worked for me -- once.  But now I can't get it working again.  I've tried every combination of input device, output device, and project rate that seems halfway reasonable, and none of them work.  It is more than a little annoying that I should have to guess which combination actually works, but at least if I could find one and stick to it.  But the combination that actually worked for me a few days ago now no longer does.

I tried Jokosher, but that just plain crashes when I try to record.

I tried Ardour.  It is a little difficult to get used to, but, okay, I can record things on it.  And I downloaded a bunch of LADSPA plugins to use.  The problem is that they all have names like "sinus wavewrapper" and "pointer cast distortion" and "Hilbert transformer" and "Chebyshev distortion."  I could probably do anything I could want to with these plugins, but I have no idea what most of them do.  I can experiment, but there dozens of them, and it is not always obvious what effect is being applied.  I would really have to experiment with the settings (sometimes many for each) of every one.  If there is any documentation for them, I would be glad to know about it.  (And I mean for any batch of LADSPA plugins.  I've looked at several, and I can't find any documentation in layman's terms for any of them.)

I miss Audacity, whose effects have such comprehensible names as "noise removal" and "change pitch" and "amplify."

Sincerely,
Derek

---

### Post by Brians Bedroom on 2008-02-13
Hey,

I understand your problem and I also hate mis-leading names. I cannot answer your question directly, except by saying install ubuntu studio - the effects are pre-loaded and some have better names. my favourite effects are:

1. MultibandEQ
2. SC4 compressor (There is a SC4 mono and stereo)
3. Gverb

note: professionally, noise removal effects are know as gates. Also to get higher signal output open the mixer window in Ardour and raise the relevant faders(volume levels).

That's mostly what I use in combination with JAMin mastering software. I wrote an article on how to interface JAMin with Ardour here: [http://briansbedroom.blogspot.com/2008/01/interfacing-jamin-with-ardour.html](http://briansbedroom.blogspot.com/2008/01/interfacing-jamin-with-ardour.html)

Take a look at the rest of my blog, it is related to recording and playing music with ubuntu Studio and freeware: [http://briansbedroom.blogspot.com/](http://briansbedroom.blogspot.com/)

Later
Brian

---

### Post by dcroxton on 2008-02-13
By "Ubuntu studio," I assume you mean the entire ubuntu distribution focusing on multimedia.  The application that goes under the name "Ubuntu studio" in add/remove programs is, as far as I can tell, just a launcher; it doesn't actually interact with the programs at all.  I'd rather not install a whole new distribution to get the effects I want -- I'm not trying to do anything fancy here, just add some basic effects.

Sincerely,
Derek

---

### Post by roaldz on 2008-02-15
It can be installed as ¨a complete distribution¨. You can also use the packages, which are made for Ubuntu. Open up Synaptic Package Manager and look for ¨ubuntustudio¨, you´ll find something you like.

---

### Post by dcroxton on 2008-02-16
Strangely enough, even though I almost always use Synaptic, in this case I had only tried the Add/Remove programs route -- where Ubuntustudio is really Ubuntustudio Launcher.  Now that I see it in synaptic, I get the point.  Thanks.

---

