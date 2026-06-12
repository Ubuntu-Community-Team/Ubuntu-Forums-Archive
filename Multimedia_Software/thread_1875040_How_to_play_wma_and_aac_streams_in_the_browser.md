---
title: "How to play wma and aac streams in the browser?"
date: 2011-11-04
forum: Multimedia Software
---

### Post by kuric on 2011-11-04
Hello! Here's a challenge to you, wise guys!

How to play the following radio in ubuntu?

[http://www.tsf.pt/paginainicial/emdirecto.aspx](http://www.tsf.pt/paginainicial/emdirecto.aspx)

I'm only interested in answers that tell us how to play both streams (aac and wma) in the browser.

My experience until now:
Chromium - shows "missing plug-in" message
Firefox - crashes completely at startup

Gstreamer codecs, ubuntu restricted extras, vlc mozilla plugins are all installed.

Thank you! ;)

---

### Post by beew on 2011-11-04
I can play the wma stream easily though not the AAC one (I haven't fiddled around with it though, wma just plays out of the box) Use the gecko-mediaplayer plugin instead of the vlc one, vlc is an excellent standalone player but its Firefox plugin kind of sucks.  Don't use Chomium so can't say anything.

---

### Post by kuric on 2011-11-04
beew, thank you, you are right!

I had to uninstall mozilla-plugin-vlc to get rid of it and did a reinstall of gecko-mediaplayer + gnome-mplayer.

Firefox stopped crashing and both streams are now playing on both browsers :)

Slow opening while catching the stream, ok, but they work indeed!

So, THANK YOU very much once again! :D

---

### Post by andrew.46 on 2011-11-05
I realise that you are after a strictly browser solution but there is a very nice vlc extension that would allow you to have this radio station set in a nice menu. Details [here]("http://www.coderholic.com/extending-vlc-with-lua/"). The line for your station is:

```

{ name = "TSF Nacional", url = "http://www.tsf.pt/emdirecto.pls" },

```

and I attach a screenshot of this station playing with the menu to one side.

---

### Post by shantiq on 2011-11-05
> **andrew.46 said:**
> I realise that you are after a strictly browser solution but there is a very nice vlc extension that would allow you to have this radio station set in a nice menu. Details [here]("http://www.coderholic.com/extending-vlc-with-lua/"). The line for your station is:

```

{ name = "TSF Nacional", url = "http://www.tsf.pt/emdirecto.pls" },

```

and I attach a screenshot of this station playing with the menu to one side.



ALSO somthing called [**radiotray**]("http://www.liberiangeek.net/2011/10/how-to-install-and-use-radiotray-in-ubuntu-11-10-oneiric-ocelot/") makes it easy to have your favourite stations at hand


PS i use it on more traditional gnome setup /no unity but was designed to work on Unity too

 and it appears in Applications/Sound and video then topbar   [not a browser solution either but a really handy one]

---

### Post by andrew.46 on 2011-11-05
And thanks shantiq for putting me on to the vlc extension in the first place :).

---

### Post by shantiq on 2011-11-05
> **andrew.46 said:**
> And thanks shantiq for putting me on to the vlc extension in the first place :).

i had to thank Ron999 for my being aware of it  :KS:KS:KS this is the ubuntu way   ..............

---

