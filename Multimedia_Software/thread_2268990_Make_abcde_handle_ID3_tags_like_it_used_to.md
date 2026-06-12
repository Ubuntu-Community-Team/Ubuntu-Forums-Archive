---
title: "Make abcde handle ID3 tags like it used to"
date: 2015-03-12
forum: Multimedia Software
---

### Post by Keith_Helms on 2015-03-12
I've been using abcde for years now and over time its handling of ID3 tags has changed.  I never explicitly told it to do anything with the tags, so this is the default behavior.

In 10.04 it used to write just the ID3V1 tag.

In 12.04 it wrote both ID3V1 and ID3V2.3 tags.

Now, in 14.04, it just writes ID3V2.4 tags.

I liked the way it worked when it wrote both tags, since that gives you compatibility with the most devices and players, so I wanted it to work that way in 14.04.

Unfortunately, under the covers abcde has switched to using a tool called eyeD3 to write the tags.  As far as I can tell, eyeD3 will allow you to write either a V1 or a V2 tag, but not both.

The solution I came up with, which may not be the easiest way to do it, but was the only thing I could think of, was to stick a script in front of eyeD3.  I wrote a tiny little bash script, which I named eyed3_bothtags.sh, with the following in it:

```
#!/bin/bash

eyeD3 --to-v2.3 "$@"
filename="${@: -1}"
id3convert -1 "$filename"
```

The script also lets me default the version 2 tags back to 2.3 instead of 2.4.

I then edited /usr/bin/abcde and in the following block of code, I changed it to use my script instead of directly calling the eyeD3 command:

```
ID3=id3
ID3V2=id3v2
**EYED3="eyed3_bothtags.sh"**
VORBISCOMMENT=vorbiscomment
METAFLAC=metaflac
AACTAG=faac
ATOMICPARSLEY=AtomicParsley
```

This solution requires installing the libid3-tools package to get the id3convert command.

---

### Post by ajgreeny on 2015-03-13
Are you aware of the longish thread at [http://ubuntuforums.org/showthread.php?t=2257705](http://ubuntuforums.org/showthread.php?t=2257705) which at post 7 seems to touch on the problem you mention here with tags and the use of eyeD3; it might be worth looking at it.

---

### Post by andrew.46 on 2015-03-13
You might be interested in the current development version of abcde (which is very stable) which has this issue ironed out I believe...

---

### Post by Keith_Helms on 2015-03-13
> Are you aware of the longish thread at [http://ubuntuforums.org/showthread.php?t=2257705](http://ubuntuforums.org/showthread.php?t=2257705) which at post 7 seems to touch on the problem you mention here with tags and the use of eyeD3; it might be worth looking at it.

I had glanced through it, but not followed the links.

I wasted some time downloading the 2.6 version, downloading various patches linked to in the threads, and attempting to apply them.   Mostly the patches failed because they didn't exactly match the code.  I gave up, found a link to the current commit of abcde on git and got that version.  With the newest version and by adding ID3TAGV=id3v2.3 to my config file, I get the same results as I did with my little hack.

---

### Post by andrew.46 on 2015-03-13
Good to hear the latest abcde has fixed the issue, hopefully there will be a release soon (2.6.1) when the main developer has returned from an extended holiday...

---

### Post by mc4man on 2015-03-13
Latest git is available here for trusty only
[https://launchpad.net/~mc3man/+archive/ubuntu/cdda1](https://launchpad.net/~mc3man/+archive/ubuntu/cdda1)

---

### Post by andrew.46 on 2015-03-13
> **mc4man said:**
> Latest git is available here for trusty only
[https://launchpad.net/~mc3man/+archive/ubuntu/cdda1](https://launchpad.net/~mc3man/+archive/ubuntu/cdda1)

You never stop :).  A frustrating blocker in current git is this one:

COMMENT tag shows odd results when multiple OUTPUTFORMAT fields present
[https://code.google.com/p/abcde/issues/detail?id=133](https://code.google.com/p/abcde/issues/detail?id=133)

which I cannot get to the bottom of although omitting opus makes it all work. Otherwise on the road for the new release...

---

### Post by mc4man on 2015-03-13
> **andrew.46 said:**
> You never stop :).  A frustrating blocker in current git is this one:

COMMENT tag shows odd results when multiple OUTPUTFORMAT fields present
[https://code.google.com/p/abcde/issues/detail?id=133](https://code.google.com/p/abcde/issues/detail?id=133)

which I cannot get to the bottom of although omitting opus makes it all work. Otherwise on the road for the new release...
I see you've been busy at abcde git, glad you got back on board.
That ppa was born to help a couple of linux mint users who were getting issues with aac encoding to .m4a as the default faac has m4a support removed. I wanted to give them (or anyone else) a shorter list of possible upgrades vs. the multimedia ppa.

---

### Post by andrew.46 on 2015-03-15
> **mc4man said:**
> That ppa was born to help a couple of linux mint users who were getting issues with aac encoding to .m4a as the default faac has m4a support removed. I wanted to give them (or anyone else) a shorter list of possible upgrades vs. the multimedia ppa.

I would love to hear of any user problems with the updated abcde. Not sure where the 'official' bug tracker will be now that Googlecode is shutting down but a simple message on these forums would get attention...

---

### Post by ajgreeny on 2015-03-15
I'm just about to install the updated version from the mac3man ppa on my Xubuntu 14.04.2 so will add to this thread if I have any problems.

---

