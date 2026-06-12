---
title: "Major problems with all music players"
date: 2011-01-22
forum: Multimedia Software
---

### Post by Grapevine on 2011-01-22
I'm trying to find a music player that I can just use without major problems after not liking or rage-quitting all the most used music players:

- Rythmbox: Doesn't seem to have any easy way to explore your music collection while playing music. Also a bit limited for my taste.

- Banshee: Tried to reorganize my music collection (because I choose the option). But then it was unable to find the reorganized music, leaving me with half albums and stuff like that. Also frequent crashes (but I could live with that).

- Amarok2: My choice until recently. It could find all the music that Banshee had left in different directories with no problem. But it has an annoying "Show under various artists" near the "Show cover" button that I end up frequently pressing, yes, my fault. But it seems like when I try to press the button "Do not show under Various Artists" the album just disappears from my collection and I have to delete, and create again the directory so it shows again.

Any other music players I could try or just deal with Amarok2 problems for now and wait for the next version?

Thanks.

---

### Post by Yellow Pasque on 2011-01-22
To name a few: guayadeque, exaile, audacious, deadbeef, clementine (amarok1 ported to modern KDE libraries), etc.

---

### Post by wbee on 2011-01-22
Grapevine:

Sooner or later,you'll find one that works well for your needs.

One you might explore is VLC-available in the Synaptic Package Manager.

I use it in its lightest weight version and see from your post you need it to do more and I'll defer to others on that who have souped it it.

That said,I like it's sound(with that twenty dollar Creative Audigy Se sound card that is ubiquitous).

Among its other virtues,it has an option to feed it to a Sony/Phillips Digital Interface out,to feed the sound to an external DAC if you wish to. Also,there is a simple graphic equalizer and an onboard volume control that functions as a preamplifier.

Best wishes finding the best one. Enjoy the hunt.:-)

---

### Post by malty on 2011-01-22
Running 10.04 on a Dell Dimension desktop, playback via external amp and speakers or high quality headphones.  Over the years I have tried most of the available music players finally throwing in the towel with Exaile, constantly crashing. Now using XBMC media player, not perfect but stores, catalogues and plays my very large music collection with aplomb. Fussy interface, slow cursor and lack of easy access volume control are the main gripes but still the best of a bad bunch.
If only J.Rivers could run in Wine.

---

### Post by Rasa1111 on 2011-01-22
Try Clementine~
Best Ive ever found/used!

and it also works as rhythmbox does now, in the volume control applet! 

But it's far better than rhythmbox! 
Inspired by amarok.

[http://www.clementine-player.org/](http://www.clementine-player.org/)

It's an amazing piece of software!

---

### Post by ivanovnegro on 2011-01-24
> **Rasa1111 said:**
> Try Clementine~
Best Ive ever found/used!

and it also works as rhythmbox does now, in the volume control applet! 

But it's far better than rhythmbox! 
Inspired by amarok.

[http://www.clementine-player.org/](http://www.clementine-player.org/)

It's an amazing piece of software!

I agree totally with Clementine. Im even a new Clementine user and its amazing. And funny, I never used Amarok 1.4.

---

### Post by Rasa1111 on 2011-01-24
> **ivanovnegro said:**
> I agree totally with Clementine. Im even a new Clementine user and its amazing. And funny, I never used Amarok 1.4.

Yeah, I never used it either. 

I did install it sometime last year..
checked it out..
found there was something I didnt like, so removed it. lol

I thinkIve tried just about every "major" music player there is for Ubuntu/Linux..
and even a few "not-so-major" ones.. 

Every one that Ive tried..
There was always something I didnt like..
or that didnt do exactly what it should..

Then I tried clementine a few months ago..
and after a day or two of using it..
Decided *this is the one!*  lol

I like it more than i used to like winamp, when i was on windows.. and i loved winamp! lol

I also love how clementines "side panel", and "equalizer", and everything else changes with the main color of your theme.
(and the equalizer is best ive found also!)

---

### Post by johntaylor1887 on 2011-01-24
> **Temüjin said:**
> To name a few: guayadeque, exaile, audacious, deadbeef, clementine (amarok1 ported to modern KDE libraries), etc.

Thanks for turning me on to clementine. I used to like the old amarok and this is perfect for my needs. Great no-nonsense music player.

Edit: Clementine might just be the best all around music player I've ever used. Since there's a windows version, I'll have to let my friends know about it.

---

### Post by dewdrop_world on 2011-01-24
Well, drat. clementine-player.org is not accessible where I live.

For fun, I tried amarok for about 10 minutes and then uninstalled it. Seemed OK when sorting by artist, but I prefer sorting by album. Then, out of 4700 tracks on my ipod, it showed me only 10 or so. Whaaaaa? That's silly. Plus I hate the volume control. Rotary knobs by mouse are one of the most idiotic interface developments ever.

Would like to try clementine but don't know where to get the .deb. Any hints? (As stated above, the downloads page at clementine-player.org won't help me.)

*Update:* I really need to quit posting questions, then finding the answer on my own 10 seconds later.

[http://code.google.com/p/clementine-player/downloads/list](http://code.google.com/p/clementine-player/downloads/list)

---

### Post by dewdrop_world on 2011-01-24
Spoke too soon. It doesn't install.

```
The following packages have unmet dependencies:
  libqt4-sql-sqlite: Depends: libqt4-sql (= 4:4.6.2-0ubuntu5) but 4:4.7.0-0ubuntu2~lucid1~ppa1 is to be installed
                     Depends: libqtcore4 (= 4:4.6.2-0ubuntu5) but 4:4.7.0-0ubuntu2~lucid1~ppa1 is to be installed
```

How do you fix version-specific dependencies like this?

---

### Post by Yellow Pasque on 2011-01-24
dewdrop_world, you would have to open the .deb in file-roller/archive manager and edit the control file, converting '='  to '>='. You could also use this to force installation anyway:
```
sudo dpkg -f install <debname>
```

Personally, I am liking audacious more and more (I'm using the latest source from the repo). It needs an option to sort by year so I can put my collection in chronological order instead of alphabetical albums. It also could deal with multi-disc sets more intelligently.

---

### Post by markling on 2011-02-01
I'm getting some joy out of Quod Libet.

---

### Post by aeiah on 2011-02-01
i use mpd with gmpc. mpd's server/client modal allows for easy control from smart phones, netbooks, other computers etc. easy streaming too, when i want it. i can also control it from within xbmc, on the command line with nvmpcpp (for if i ssh in) or the aforementioned gmpc

---

### Post by markling on 2011-02-06
You can't beat Mplayer though. It lets you play spoken word at faster-speeds. A friend of mine's got a TV hard disk recorder with the same function. So you sit down to watch one of those documentaries that could have been squeezed into 10 minutes, you just whack the speed up and get it over and done with. All media players should have them.

---

### Post by Rasa1111 on 2011-02-06
markling,
 VLC also does that. 

but for music player,
really can't beat clementine

---

