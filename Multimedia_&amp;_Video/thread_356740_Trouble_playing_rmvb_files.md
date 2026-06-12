---
title: "Trouble playing rmvb files"
date: 2007-02-08
forum: Multimedia &amp; Video
---

### Post by Aune on 2007-02-08
I'm having biiiiig trouble playing .rmvb files in ubuntu 6.10. I've tried all the "tutorials" I've found online, but no one seems to do any good. Can someone give me some pointers  as to how to fix this ?

---

### Post by bebop_tango on 2007-02-08
There are quite a few options, truly.

The first one would be installing RealPlayer. The easiest one would be downloading the .deb package from [http://www.real.com/player]("http://www.real.com/player") and installing through dpgk or GDebi. I wouldn't recommend the binary install program since if you change your mind you'll have to manually delete the files from your system in order to uninstall the program.

So get the .rpm package and convert it with alien... install the *alien* package via apt-get and use to convert the .rpm to a .deb package.

There are other ways to install RealPlayer... Automatix is a good way to go. :) 

BUT there IS one thing... you'll have to use alsa-oss emulation in order to properly enjoy your videos.

First, install the *alsa-oss* package via apt-get (it's from the universe repository). Then run the program through the terminal:

```
aoss realplayer
```

Or you could just open the file /usr/bin/realplay (with sudo access) and edit this part of the code

```
while /bin/true;do
# Restart the player if exit code is 10
$REALPLAYBIN "$@"
```

by adding aoss to $REALPLAYBIN &#8220;$@&#8221; so that it looks like

```
while /bin/true;do
# Restart the player if exit code is 10
aoss $REALPLAYBIN "$@"
```

Save the file and presto!

:lolflag: 

Anyway, if you prefer not to use RealPlayer, you could do this:

```
sudo apt-get install libxine1 libxine-extracodecs 
```

And then search for w32codecs package. It's not from the repo's, but google it up or just use Automatix if you feel like it - it will download and install it for you.

Now totem-xine, gxine and mplayer should be able to play .rmvb files.

I hope this fixes it...

---

