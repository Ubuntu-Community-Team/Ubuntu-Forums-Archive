---
title: "Ripping to vbr mp3 with abcde?"
date: 2007-05-25
forum: Multimedia &amp; Video
---

### Post by tenth on 2007-05-25
I can rip tracks from a cd but they are all 128kbs. Anyone know how to set abcde to rip at variable bit rate?

---

### Post by Belathor on 2007-05-26
bump. I would like to know how to do this as well.

---

### Post by jenast on 2007-06-08
I think the exact command varies with the specific encoder abcde "calls" for the actual encoding.

Default encoder for mp3's seems to be "Lame".

This command rips from my cd and encodes at 192 kb/s at the moment: abcde -o mp3:"-b 192" 

Hope it helps...


/jenast

---

### Post by andrew.46 on 2007-08-27
Hi,

 Have a look at:

[http://people.aapt.net.au/~adjlstrong/ubuntu_cli.html#mp3](http://people.aapt.net.au/~adjlstrong/ubuntu_cli.html#mp3)

 For a bit of background to using abcde for cd to mp3. The -preset method is the easiest way of passing vbr to lame. From the manual:

```
       For VBR modes (generally highest quality):

       --preset standard
              This  preset  should  generally be transparent to most people on
              most music and is already quite high in quality.

       --preset extreme
              If you have extremely good hearing and similar  equipment,  this
              preset  will  generally provide slightly higher quality than the
              standard mode.

```

 Hope this helps!

        Andrew

---

