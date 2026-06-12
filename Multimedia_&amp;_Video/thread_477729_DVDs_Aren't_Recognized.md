---
title: "DVDs Aren't Recognized"
date: 2007-06-18
forum: Multimedia &amp; Video
---

### Post by Bishop286 on 2007-06-18
Hey everyone,

I'm new to the community, and Linux in general (though I have used Unix before to write/run programs so I'm not *completely* in the dark), and I've just been installing Ubuntu (7.04 feisty).

Anyway, on to my problem -- I have a Plextor PX-708A DVD RW drive, and it works fine for the most part.  Reads CDs and data DVDs just fine.  I haven't tried burning with it yet, so I'm not sure about that, but my problem is that it doesn't recognize DVDs.  I've tried several different DVDs and  it doesn't register them as movies, so I can't watch them in Movie Player.

What it does come up with is "DVD-ROM Disc" with the location of "Burn:///".  Am I needing some drivers (I looked a tiny bit and didn't find any, but that just means I didn't look hard enough probably ;) ) or is there a specifically incompatibility with this disc drive, or perhaps I need to do something that I didn't do?

If this is in the wrong forum, sorry.  I am unsure where I should post this.

Thanks in advance,

Bishop

---

### Post by kelvin spratt on 2007-06-18
i use plextor but mine is not the premium edition i had probs in windows with mine but no probs with Linux if your movies are protected you will have problems playing them. I was expecting problems with mine but was lucky but my Liteon is only recognised  as a cd rom for some reason

---

### Post by Bishop286 on 2007-06-18
I had problems in Windows once upon a time, but that was a strange case.

Here and now I have no problems in Windows, but I don't want to have to restart my computer and boot to Windows every time I want to watch a movie.

As for the protected bit, I am unsure if all of them are protected.  I've tried Blade Runner, The Scorpion King, Spaceballs, and Meet Joe Black and run into the same problem each time.  All the discs (save Blade Runner) are in nigh perfect condition, so I highly doubt it's some sort of odd disc read error.

---

### Post by Gremlinzzz on 2007-06-18
You could try smplayer works for me . [http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/)      
codecs if ya need em.  [https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)

---

### Post by Bishop286 on 2007-06-18
Well, I tried installing the codecs and SMPlayer.  Still get the same thing and when I try to play the DVD from CD via the option on SMPlayer, the disc spins for a while and SMPlayer slows down the system and eventually locks up.

---

### Post by Bishop286 on 2007-06-18
Here are some pictures so you can visualize what I'm talking about:

[IMG]http://img.photobucket.com/albums/v691/bishop186/ubuntu/screenshot1.png[/IMG]
This icon shows up on my desktop when I put in a DVD.

[IMG]http://img.photobucket.com/albums/v691/bishop186/ubuntu/screenshot2.png[/IMG]
When I open the icon from the first picture, this is what comes up.

[IMG]http://img.photobucket.com/albums/v691/bishop186/ubuntu/screenshot3.png[/IMG]
And finally, a view of what it looks like under "Computer:///"

---

### Post by Bishop286 on 2007-06-19
So, nobody has any other ideas?

---

### Post by kelvin spratt on 2007-06-19
Just looked at your screen shots seems strange as mine shows the title of the film and play in totem as it should, perhaps it needs remounting to get permissions there is some good info on this forum and on the debian site on that sort of thing and on Dvd not being recognized or you could try Linux mint or PC Linux as they come with the codecs already installed except, the libdecss? codec and that's in this and their repos i'm sorry i can't help any more but unless i  get a particular problem its very hard for me. you might have to keep posting every day to get your answers due to to size of the forum and it would help to post your specs and anything else that can help in the meantime.

---

### Post by RomeReactor on 2007-06-19
Hi. It's odd that DVDs are (seemingly) recognized as blank discs, since they open in the Nautilus burner; I don't know why that is. However, in order to play video DVDs, you need to do [this]("http://ubuntuforums.org/showpost.php?p=2465766&postcount=7") first, if you haven't already.

Note that doing this will most likely break totem-mozilla (the plugin for playing streaming media in Firefox). If you intend to play streaming media in Firefox, you would then need to install mozilla-mplayer (or another plugin such as kaffeine-mozilla or mozilla-plugin-vlc). Or leave totem-gstreamer installed (by **not** executing the last command from the [link]("http://ubuntuforums.org/showpost.php?p=2465766&postcount=7")). The problem with having totem-gstreamer is that you don't have access to the DVD menus or subtitles (as far as I know; someone please correct me if I'm wrong).

---

### Post by Bishop286 on 2007-06-19
Well, the link above worked.  I feel silly for not knowing that/doing that.

It still doesn't recognize the discs as DVDs, which, as you said, is odd, but I can open them with SMPlayer, now.  I might just not know how to use it completely/properly, but I'm not a very big fan of it so far because it doesn't have a "Go to Menu" command or anything like that.

As for the final command breaking the video on Mozilla/Firefox, everything works just fine except for Javascript-based apps/vids, but I've been having a problem with Java in general (Azureus is being a giant, dirty, and rotten bitch, excuse my language) which is a seperate issue for a seperate forum.

---

### Post by RomeReactor on 2007-06-19
Well, glad to hear you can now watch the DVDs! As for Azureus, yes... it's bloated as can be; even the version from their site is almost unbearable (though it definitely is better than the one in the repositories). Back to the issue of the DVDs, what command is set for **Play video DVD discs when inserted**, on the "Multimedia" tab in "System-->Preferences-->Removable Drives and Media"? It should be **totem %m**. Just in case...

---

### Post by Bishop286 on 2007-06-19
Yep, they are indeed set that way.  Sadly, if it doesn't recognize it as a DVD disc, well, it's not going to play them.  ;)

---

