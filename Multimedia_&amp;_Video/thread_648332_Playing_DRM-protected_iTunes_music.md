---
title: "Playing DRM-protected iTunes music"
date: 2007-12-23
forum: Multimedia &amp; Video
---

### Post by X40nick on 2007-12-23
Hi,

Over the year I have been using iTunes to buy music, I didn't use Linux and I didn't really worry over the DRM. 

Now I am trying to let go of Windows and my vast selection of music won't play with Linux!!! How can I get the music to play? I can browse my C drive and then choose to play with VLC but I hear nothing?

Do I need a certain package or am I just unlucky? I have heard about WINE (which I hate the name of) but I am not sure.

Can I do anything or am I stuck?

Nick.

---

### Post by davidgarcin on 2007-12-23
That's not an easy problem to solve, unfortunately.  The iTunes DRM requires that you use iTunes to play your purchased music.  From a quick look at the Wine app DB, iTunes does not run under Wine, so you can't use it in Linux.

There are a couple of programs that will help you strip the DRM from your purchased iTunes music, namely QTFairUse (which is Windows-only), or the JHymn project (which I don't think is working for iTunes 6+).  I haven't used these personally, so I'm not sure how well they work.

Last resort is burning your protected files to an audio CD, then re-importing them in your favourite unprotected format.

Good luck.
-David

EDIT:  Source code is available for QTFairUse, so you might be able to compile it under Linux, I'm not sure. There's also MyFairTunes.  See [http://hymn-project.org/](http://hymn-project.org/).

---

### Post by X40nick on 2007-12-24
Thanks for your reply, I will have to burn them all to a CD and then import them to my Linux library. I won't be buying any more music from them! 

Can I buy music which is DRM free under Linux?

Thank you.

Nick.

---

### Post by davidgarcin on 2007-12-24
In Linux, your best bet are web-based retailers.  There are a number of them that sell DRM-free music, such as CDBaby.com and Amazon.com.  There's more, just google and you'll find some.  iTunes recently started selling DRM-free songs, but at a higher price, and of course, you can't run iTunes under Linux.

When you burn your CDs, make sure that you are actually making audio CDs (that will play in a normal CD player), not just burning the protected files to a CD.  You will need iTunes to do that.

---

### Post by gutsy_psu on 2007-12-24
> **davidgarcin said:**
> That's not an easy problem to solve, unfortunately.  The iTunes DRM requires that you use iTunes to play your purchased music.  From a quick look at the Wine app DB, iTunes does not run under Wine, so you can't use it in Linux.

.

Well, I have to say I just set up Wine to run iTunes on Gutsy with no problems whatsoever last night, see this site for more details:[http://wine-review.blogspot.com/2007/10/itunes-73-on-linux-with-wine.html](http://wine-review.blogspot.com/2007/10/itunes-73-on-linux-with-wine.html)
 it was really easy (wine can be found in the synaptic package manager).

---

### Post by nwadams on 2007-12-24
becuase you own licenses to the songs, you can legally just torrent the non-DRM copies of them, instead of wasting time and cd's.

---

### Post by X40nick on 2007-12-29
Really???

I can just torrent the music that I own? I have read in the newspapers about people who have been arrested and sometimes sent to prison for doing that?

Are you sure it is legal???

Nick

---

### Post by davidgarcin on 2007-12-29
No, I'm sure it's not legal, you could get fined for downloading music like that, although the chances are extremely, extremely small.  I really doubt that anyone would chase you for downloading songs that you already own, and if they did, you would have a pretty good defense.

I think what nwadams is saying is that you can have a clear conscience because you have already bought the music.  What should be legal and what is legal are rather different things.

EDIT:  If gutsy_psu says that iTunes can work under wine, I would certainly give that a try.  It's the easiest solution if it works.  The Wine app dB should really be updated if that's the case.

---

### Post by ayenack on 2007-12-29
VLC Media Player can play mp4 (DRM) files. Take a look at this site.

[Play DRM]("http://all-streaming-media.com/streaming-media-faq/faq-playing-DRM-protected-m4p-AAC-Apple-iTunes-files.htm")

If you think it's worth the effort install VLC.

sudo apt-get install vlc

---

### Post by ron999 on 2007-12-29
Hi
While you are downloading a torrent you're also making parts of it available to be downloaded from you. Those other downloaders probably won't have paid anything to iTunes or anybody else.

BTW You don't need to waste any CD-Rs, just use a CD-RW disc.
8)

---

### Post by ayenack on 2007-12-29
If your Ubuntu install is on the same computer as your Microsoft Windows install you can use this app to copy the files to the home directory of Ubuntu.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

It says that it's only for ext2 file system but it'll write to ext3 without problems as well. Make sure to read the FAQ's [here]("http://www.fs-driver.org/faq.html#acc_ext3") and [here]("http://www.fs-driver.org/faq.html")

---

### Post by X40nick on 2007-12-30
I am using Microsoft Windows Vista, and I don't suppose that program will be able to do that?

I will give iTunes and Wine a try, That seems the best solution.

And VLC nor any other program won't play my music, it comes back saying it is encrypted.

Steve Jobs, worlds biggest hypocrite!

---

### Post by sageb1 on 2008-01-09
Blame the RIAA and bands who coopted to them.

Courtney Love supports the freeing of music of DRM. Maybe we should beg her to support the effort to locally free our bought music of DRM.

What DRM means is, it saves time to buy a CD at a music store. Also, considering the price of tickets  versus the time it costs to remove DRM, it's better to go to a concert.

---

### Post by Jive Turkey on 2008-01-09
> **X40nick said:**
> Really???

I can just torrent the music that I own? I have read in the newspapers about people who have been arrested and sometimes sent to prison for doing that?

Are you sure it is legal???

Nick

Not legal if you are uploading the songs at all.

---

### Post by MeduZa on 2008-05-12
> **ron999 said:**
> Hi
While you are downloading a torrent you're also making parts of it available to be downloaded from you. Those other downloaders probably won't have paid anything to iTunes or anybody else.

BTW You don't need to waste any CD-Rs, just use a CD-RW disc.
8)

you don need cd-r o cd-rw, just burn it to a image.iso!

---

