---
title: "Editing m4a tags in Amarok"
date: 2007-07-16
forum: Multimedia &amp; Video
---

### Post by Rob_J on 2007-07-16
Hi guys,

Title says it all really; I've installed the packages required to play m4a files in Amarok and it reads their tags etc. correctly, but when I try and edit something like the artist I get an error similar to the following:

"Sorry, the tag for Paint It Black.m4a could not be changed"

Are there any particular packages I need to install to enable me to edit m4a tags?  I'm using the newest version of Feisty and GNOME if it helps.

Thanks a lot,
Rob

---

### Post by meindian523 on 2008-01-20
bump,though the OP is not here,I've the same problem.

---

### Post by meindian523 on 2008-01-21
bump

---

### Post by BandD on 2008-01-21
Is there any program that can edit m4a tags in the Linux world?  I've tried EasyTag as is has support for MP4 and AAC, but alas...it doesn't even recognize that those files exist.  Neither does Audio Tag Tool.  

Curse Itunes!!!!  How I wish there was a way to convert to ogg without losing any more quality...

---

### Post by ron999 on 2008-01-21
Hi
The version of EasyTag that's in the Ubuntu repo is v2.1.
This one doesn't allow editing of m4a tags. But the earlier version does.
So I have uninstalled EasyTag and installed an earlier version.

The one I am using is v1.99.13
I downloaded a deb.
This one:-easytag-aac_1.99.13-0.0_i386.deb
I think that this is where I got it from:-[http://www.hro.lkams.kernel.org/debian-multimedia/pool/main/e/easytag-aac/]("http://www.hro.lkams.kernel.org/debian-multimedia/pool/main/e/easytag-aac/")
:cool:

---

### Post by meindian523 on 2008-01-26
Um,problem is that synaptic goes into dependency hell around libmp4v2-0.Any other ideas?

---

### Post by kahlil88 on 2008-02-03
I've got some dependency issues as well - Easytag 1.99.13 wants an older version of **libflac** and **libmp4v2-0** than what I already have installed. I tried running Easytag without resolving the dependencies, but it refuses to even start without libflac7 (it doesn't like libflac8). Has anyone else managed to get an m4a-supporting version of Easytag installed, or is there perhaps another program specifically for m4a?

---

### Post by logos34 on 2008-02-03
> **kahlil88 said:**
> I've got some dependency issues as well - Easytag 1.99.13 wants an older version of **libflac** and **libmp4v2-0** than what I already have installed. I tried running Easytag without resolving the dependencies, but it refuses to even start without libflac7 (it doesn't like libflac8). Has anyone else managed to get an m4a-supporting version of Easytag installed, or is there perhaps another program specifically for m4a?

That's a hard one.  I even tried to compile mine from source, with the correct flags/options, but after all that it installed without m4a support!  Go figure.  

good luck finding a solution

---

### Post by ron999 on 2008-02-03
Hi
I'm using Ubuntu 7.04 Feisty Fawn.

I've checked in Synaptic to see which versions I'm using.

easytag-aac   v1.99.13-0.0
libmp4v2-0   v1:1.5.0.1-0.3
libmp4v2-0-dev  v1:1.5.0.1-0.3
libflac++5c2  v1.1.2-5ubuntu2.1
libflac7  v1.12-5ubuntu2.1

The above setup works ok for me. Tags for mp4 OK.

---

### Post by kahlil88 on 2008-02-03
Where can I get .deb packages for that version of libmp4v2-0?

---

### Post by ron999 on 2008-02-04
Here they are

---

### Post by cozmicharlie on 2008-02-04
Exfalso will edit m4a tags.  It is in Synaptic.

---

### Post by meindian523 on 2008-02-04
Dependency hell again,I had to run apt-get install -f,after this I've given up on Easytag,I believe it's easier to recompile amaroK itself with m4a tag editing capability.I just need a tutorial for that.I found one for Gentoo,but the author of that blog has not yet responded.

[http://www.cydeweys.com/blog/2007/11/21/gentoo-linux-tutorial-playing-m4a-song-files-in-amarok/](http://www.cydeweys.com/blog/2007/11/21/gentoo-linux-tutorial-playing-m4a-song-files-in-amarok/)

---

### Post by meindian523 on 2008-02-04
This was also an attempt to get "accurate" tag info + m4a tagging ability.No responses there either:

[http://ubuntuforums.org/showthread.php?t=677670](http://ubuntuforums.org/showthread.php?t=677670)

Another attempt to pry some info out of the OP:

[http://ubuntuforums.org/showthread.php?t=580091](http://ubuntuforums.org/showthread.php?t=580091)

No responses there either.

---

### Post by meindian523 on 2008-02-04
> **cozmicharlie said:**
> Exfalso will edit m4a tags.  It is in Synaptic.

No mention of m4a or even mp4/AAC in the description:
> 
audio tag editor for GTK+
Ex Falso displays and edits audio metadata tags. Supported formats include
MP3, Ogg Vorbis, FLAC, Musepack (MPC), WavPack, and MOD/XM/IT.

Notable features include:
 * Freeform tag editing for most supported formats, including ID3v2
 * Multiple values for tag keys
 * Flexible rename-by-tags and tag-by-filename patterns
 * Extensible using simple Python-based plugins
 * Edit multiple files in several formats at once

---

### Post by cozmicharlie on 2008-02-04
> **meindian523 said:**
> No mention of m4a or even mp4/AAC in the description:

You are correct but I use it and it works for me.  See also these threads - 
[http://ubuntuforums.org/showthread.php?t=102066&highlight=exfalso](http://ubuntuforums.org/showthread.php?t=102066&highlight=exfalso)
[http://ubuntuforums.org/showthread.php?t=677634&highlight=exfalso\](http://ubuntuforums.org/showthread.php?t=677634&highlight=exfalso\)

You might want to check it out.

---

### Post by meindian523 on 2008-02-05
Hmm,will try and get back to here.

---

### Post by cozmicharlie on 2008-02-05
Also, make sure you have the correct codecs installed.  You need faac, fmpeg and the gstreamer plug ins.  All available in Synaptic from the medibuntu repository.

---

### Post by Yadda on 2008-02-06
I was having the same problem with editing .m4a tags. I gave Ex Falso a shot just to see what happened and it does indeed edit .m4a tags. It's not the most intuitive thing in the world, but it works...

---

### Post by cozmicharlie on 2008-02-06
FYI - you may also want to check out Quodlibet.  It is a player with Exfalso integrated.

---

### Post by meindian523 on 2008-02-08
ExFalso works.It's good too.But I can think of a better GUI none the less.

---

### Post by cozmicharlie on 2008-02-08
Great - not sure why they do not list m4a in the description.  At first it does seem somewhat unintuitive but like any program, once you use it you will find it has some nice features.

Enjoy!

---

### Post by meindian523 on 2008-02-09
Well,I did use it and renamed my entire library and found some "hidden" tags like encoded by "so-and-so" application which I removed.I didn't know such tags existed!

---

### Post by kahlil88 on 2008-07-08
I've switched to Exaile now, and it can edit m4a tags! I highly recommend it for Gnome users.

---

### Post by meindian523 on 2008-07-09
What are the packages to install for m4a playback support?I searched the entire gstreamers and used m4a itself as a keyword,but all it turned up was converters from one format to another.Exaile can edit m4a tags all right,but I'm not able to play 'em due to lack of codecs.

---

### Post by kahlil88 on 2008-07-09
Did you try the gstreamer ugly and bad plugins? You might need to install the Multiverse variants.

---

### Post by meindian523 on 2008-07-09
Yeah,it works.Thanks!

---

