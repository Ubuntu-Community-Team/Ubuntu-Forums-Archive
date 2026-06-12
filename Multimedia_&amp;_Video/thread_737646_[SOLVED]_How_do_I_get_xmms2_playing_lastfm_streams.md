---
title: "[SOLVED] How do I get xmms2 playing lastfm streams?"
date: 2008-03-27
forum: Multimedia &amp; Video
---

### Post by kaivalagi on 2008-03-27
I have xmms2 installed on Gutsy 64 and have no problem playing mp3's etc.

What I want to do is play last.fm content with xmms2, but can't seem to find any useful help on the subject anywhere.

I have the xmms2-plugin-lastfm installed, as well as xmms2-scrobbler.

I have edited the ~/.config/xmms2/xmms2.conf file to have the correct username and password, which I registered and can use okay in the lastfm player. These same details have also been created in a config file in ~/config/xmms2/clients/xmms2-scrobbler. This file being linked to by ~/config/xmms2/startup.d/xmms2-scrobbler

Have I done enough to, in theory, have last.fm support, if this isn't the case can anyone explain what I need to do or where I can find a good step by step guide?

Also once last.fm is setup for xmms2, how do you go about adding last fm content to the playlist? I was expecting to have to run something like this in the console:

xmms2 add lastfm://user/$kaivalagi/personal

But even after a response saying the url has been added, nothing shows in the playlist???

Can someone please set me straight with all of this  'cause I really don't know what to do next...is it even possible to play lastfm content in xmms2, or does it just support submissions to lastfm?

Thanks in advance

---

### Post by kaivalagi on 2008-03-28
Got it sorted via the #xmms2 chat room on freenode.net. Config was all okay but I needed Ruby installed and had more than one instance of xmmsd running...

If you need to debug issues make sure you run  the following before trying to use xmms commands that seem not to work, it will kill all existing instances of xmms2d and give you verbose output from the new instance:
```

killall xmms2d
xmms2d -v
```

Cheers

---

