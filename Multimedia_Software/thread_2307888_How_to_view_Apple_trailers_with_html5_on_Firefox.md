---
title: "How to view Apple trailers with html5 on Firefox?"
date: 2015-12-29
forum: Multimedia Software
---

### Post by monkeybrain20122 on 2015-12-29
e.g go to [http://trailers.apple.com/trailers/fox/kungfupanda3/](http://trailers.apple.com/trailers/fox/kungfupanda3/) On Chrome  it plays in html5, but on Firefox it asks for the quicktime plugin.  Of  course there is no quicktime plugin on Linux (gecko-mediaplayer has been  removed from wily's repo) But strangely using  user-agent-overrider  with Linux/Chrome the trailer plays (though doesn't go fullscreen and  has no   hd option). 

Aside from user-agent spoof the mpv addon also work (and best quality). 

I am curious why this is and whether there is a way to make FF play these in html5. Thanks.

---

### Post by mc4man on 2015-12-29
I guess there is a convoluted way to get them playing on FF, hardly seems worth it as - 
their vids are on youtube
mpv plugin works better than native player
Videos (totem) can also play from 'channels'

For FF there is a user-agent add-on though it only has old ua's. You'd also need to get a newer .xml from github & import the .xml
see screens, no idea what it's playing codec/rez size, though it does go to fullscreen

---

### Post by monkeybrain20122 on 2015-12-29
Hmmm. It plays on Opera in html5 as well, but get blackscreen in Ubuntu's Broswer. The fact that uer-agent-overrider works means that it is not because of proprietary codecs (like netflix). I am just curious why this is.

---

### Post by mc4man on 2015-12-29
> **monkeybrain20122 said:**
> Hmmm. It plays on Opera in html5 as well, but get blackscreen in Ubuntu's Broswer. The fact that uer-agent-overrider works means that it is not because of proprietary codecs (like netflix). I am just curious why this is.

There was some post I ran across, (not here), that alluded to apple serving FF with quicktime while using html5 for other browsers. That could explain why on Linux FF will only play via a user-agent as there is no viable quicktime plugin anymore.

---

### Post by QIII on 2015-12-29
I looked through the HTML5.  It's either terrible design or a deliberate snub of FF on Linux.  The QuickTime is still wrapped in HTML5.

Normally, you would want to give a series of possible src video types that will "fall through" until the browser/OS finds on it can use, and give a nice message like "Your browser cannot render the HTML5 video" or something if it can't find one it can use.

That is

```

<tag>
     <video type="blah" src="\foo\bar\video.blah ...
     <video type="blahblah" src="\foo\bar\video.blahblah ...
     <video type="blahblahblah" src="\foo\bar\video.blahblahblah ...
     Sorry, you are out of luck.
</tag>

```

Instead, this is doing a lookup and giving only one option, probably m4v (I think that is what the QuickTime file extension is.)

So even if you use a user agent, you are likely to still get some default type instead of the m4v and it won't work completely, such as the controls won't function.

Bad design.  Naughty designers.

---

