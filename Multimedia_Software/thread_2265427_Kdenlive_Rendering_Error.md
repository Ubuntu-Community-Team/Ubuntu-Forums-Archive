---
title: "Kdenlive Rendering Error"
date: 2015-02-15
forum: Multimedia Software
---

### Post by Rvdpeet on 2015-02-15
Hello fellow ubuntu users,

For video editing I use Kdenlive, I've used it several times a few months ago, and now I know exactly how it works. Now, I wanted to edit another video, everything works fine, but if I try to render, I get an error:

Error Log:
 [libmp3lame @ 0x7f994c0d2520] channel_layout not specified
*** Error in `/usr/bin/melt': double free or corruption (!prev): 0x00007f994c0d29e0 ***

I render in Lossless/HQ 
MPEG-4 I-frame only (video) + MP3 (sound)
1080p 30 fps

It's really important to me that that's the output file.

Does anybody have an idea or solution for my problem? Maybe something I could try?

Thanks in advance,

Regards, Rvdpeet

---

### Post by Rob Sayer on 2015-02-16
Is kdenlive working OK with other files?  Does the problem file play all the way through with vlc?

---

### Post by Rvdpeet on 2015-02-16
Hello, Rob Sayer,

I tried rendering some other files, and they all had the same error. When I try to play the file with vlc, after about 3 seconds vlc doesn't respond and then closes on its own.
I also tried reinstalling the libmp3lame and libmp3lame-dev package as well as kdenlive itself, but this didn't solve anything either.

Are there any more options I could try?

Thanks and regards,

Rutger

---

### Post by Rvdpeet on 2015-02-24
Hello,

Now that a week has passed, I tried updating my packages, I reinstalled Kdenlive, but the error hasn't been solved.
I made some screenshots of the error report, maybe that will help:

#1/11
[IMG]http://i.imgur.com/snWzto3.jpg[/IMG]

#2/11
[IMG]http://i.imgur.com/wu9j9Pg.jpg[/IMG]

#3/11
[IMG]http://i.imgur.com/10mUQXZ.jpg[/IMG]

#4/11
[IMG]http://i.imgur.com/AIyohnM.jpg[/IMG]

#5/11
[IMG]http://i.imgur.com/gXtT2x1.jpg[/IMG]

#6/11
[IMG]http://i.imgur.com/5rwQ3Q9.jpg[/IMG]

#7/11
[IMG]http://i.imgur.com/FVBzMXP.jpg[/IMG]

Last screenshots in next post...

---

### Post by Rvdpeet on 2015-02-24
...Last pictures:

#8/11
[IMG]http://i.imgur.com/RXV4cG6.jpg[/IMG]

#9/11
[IMG]http://i.imgur.com/pgzpWgK.jpg[/IMG]

#10/11
[IMG]http://i.imgur.com/48DIL6U.jpg[/IMG]

#11/11
[IMG]http://i.imgur.com/TXSPXqm.jpg[/IMG]

Hopefully this will help.

Regards and thanks,

Rvdpeet

---

