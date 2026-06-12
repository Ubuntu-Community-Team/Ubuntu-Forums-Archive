---
title: "Streaming Web Video on dr.dk/tv"
date: 2006-11-13
forum: Multimedia &amp; Video
---

### Post by Fafnr on 2006-11-13
Hey all you lovely geeks out there! :-D

I'm a new Ubuntu user (though I have some limited experience with Red Hat).
After installin Ubuntu and getting everything set up just the way I like it,
I still manage to hit a problem when using a Danish web-tv website.
(I hope the problem is general enough to warrant a response, though)
The site is [www.dr.dk/tv](www.dr.dk/tv), and I'm especially eager to make it work since from next year all Danes with a computer with internet-access will HAVE to pay for access to that site...

Anyway, I've installed VLC and mplayer, and tried setting firefox up to use both. (network.protocol-handler.bla.bla = /usr/bin/gmplayer  or /usr/bin/vlc)
But no matter what I do, all I see is a black screen with "(no video)" printed in the middle...

Any help out there? :-)

Regards,

Søren

---

### Post by nomasteryoda on 2006-11-13
I am in the US and tried the site.

mplayer works, but my IP is blocked because I am not in your country.

These instructions should help, if not try the IRC channel irc.freenode.net #ubuntu for immediate help.

[http://www.debianadmin.com/install-mplayer-ubuntu.html]("http://www.debianadmin.com/install-mplayer-ubuntu.html")

---

### Post by Fafnr on 2006-11-13
Thx for your help!

Doing what that page said at least got me a decent error-msg :)
Seems Totem was trying to play it... Unsuccessfully, as it happens. :)

After the Totem-plugin was uninstalled, mplayer does take over!
It seems to have problems picking up the stream (talking to the server) but I'm guessing that's a whole other problem...


Anyway, thx!

/Søren

---

### Post by Fafnr on 2006-11-17
Ok, so we're at the next point in the saga of getting MPlayer to play video's for me on a very special webpage! :-D

Basically, it seems the .deb you get from apt-get doesn't include the codecs I need, so I need to compile mplayer from scratch...

So, I tried and got:
Error: X11 support required for GUI compilation.

Browsing a bit, it seems I need the x-window-support which on ubuntu is called:
libx11-dev and libx11-6...

But, here's the kicker! When I do apt-get I get:
The following packages have unmet dependencies:
  libx11-dev: Depends: libx11-6 (= 2:1.0.3-0ubuntu4) but 2:1.0.3-2 is to be installed

which I do not understand a word of! :-)

I don't know if this is the wrong forum, but if anybody has any tips, I'd like to hear 'em. :-)

/Søren

---

### Post by basambora on 2006-12-09
libx11-dev: Depends: libx11-6 (= 2:1.0.3-0ubuntu4) but 2:1.0.3-2 is to be

I'm not completely sure if it's correct but I think the line above translated to normal text would be:
     libx11-dev needs libx11-6 with version number 2:1.0.3-2 but from which the version number currently is 2:1.0.3-0ubuntu4

This means that the version number from the current libx11-6 package is not correct. The version numbers translated would be:
     current: the 4th revision of the first ubuntu version which is taken from the original package with version 2:1.0.3-0
     needed: the 2nd revision of the original package with version 2:1.0.3

Maybe this can be solved by using version 2:1.0.3-2ubuntux, so that the ununtu developers started with the needed version from the original package, but I'm one of the many newb(ie)s so it may be false.

Couldn't find a link to more info, but I think I saw it on the [ubuntuguide]("http://www.ubuntuguide.org")

Hope this helps and good luck

---

