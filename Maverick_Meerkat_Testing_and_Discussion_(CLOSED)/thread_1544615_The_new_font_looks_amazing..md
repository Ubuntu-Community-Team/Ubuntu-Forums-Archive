---
title: "The new font looks amazing."
date: 2010-08-02
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Starks on 2010-08-02
Instructions: [http://www.webupd8.org/2010/08/new-ubuntu-1010-font-available-for.html](http://www.webupd8.org/2010/08/new-ubuntu-1010-font-available-for.html)

Package is ubuntu-private-fonts in Synaptic.

In Preference>Appearance>Fonts, assign all Sans to UbuntuBeta Regular, all Sans Bold to UbuntuBeta Bold.

If you want autohinting: sudo ln -sf /etc/fonts/[conf.avail/10-autohint.conf]("http://conf.avail/10-autohint.conf") /etc/fonts/conf.d/ 

Here are the results: [http://img248.imageshack.us/img248/4244/newfontb.png](http://img248.imageshack.us/img248/4244/newfontb.png)

---

### Post by jpeddicord on 2010-08-02
Agreed. Been using it for the past few weeks and can say that it doesn't take long to get used to it. :)

---

### Post by x-shaney-x on 2010-08-02
I've been using the old ripped font for a while and like it so thought I would try it:
```
Failed to fetch https://private-ppa.launchpad.net/ubuntu-font-beta-testing/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz  The requested URL returned error: 401
Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by Starks on 2010-08-02
Do you have a launchpad account with private ppa access?

---

### Post by jpeddicord on 2010-08-02
> **x-shaney-x said:**
> I've been using the old ripped font for a while and like it so thought I would try it:
```
Failed to fetch https://private-ppa.launchpad.net/ubuntu-font-beta-testing/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz  The requested URL returned error: 401
Some index files failed to download, they have been ignored, or old ones used instead.
```

You can't use the PPA url directly; you need to get an access code by following the private PPA instructions from the original post.

---

### Post by x-shaney-x on 2010-08-02
Yes all instructions were right and that isn't the repo url I added to synaptic but that's what it outputted.
In any case, it seems it takes a short while before you can actually use it, reloaded the repos about 15 minutes later and it went through ok.

---

### Post by krazyd on 2010-08-02
Does the new font have a monospaced variant? If so, I would be very keen to see a screenshot! :D

---

### Post by jpeddicord on 2010-08-02
> **krazyd said:**
> Does the new font have a monospaced variant? If so, I would be very keen to see a screenshot! :D

No, at least not right now.

---

### Post by Atermoon on 2010-08-02
> **krazyd said:**
> Does the new font have a monospaced variant? If so, I would be very keen to see a screenshot! :D

Not yet but I think there will be.

The font looks gorgeous, probably the first one that looks so good I actually made it 9pt (I usually use 8 or 8.5, fonts like Sans look lame at bigger sizes imho).


Edit: WTF didn't see jpeddicord 's comment :-s

---

### Post by JustinR on 2010-08-02
This news is oldddddddddddddddddddddddd - the private PPA has been out for a while now - just wait 'till August 5?th - the font will be public.

---

### Post by Atermoon on 2010-08-02
> **JustinR said:**
> This news is oldddddddddddddddddddddddd - the private PPA has been out for a while now - just wait 'till August 5?th - the font will be public.

I don't see the point of posting comments like this. Using the same logic Gnome-Shell is also old news. So what? Do we wait until it's done to talk about it? Come on...

---

### Post by JustinR on 2010-08-02
> **Atermoon said:**
> I don't see the point of posting comments like this. Using the same logic Gnome-Shell is also old news. So what? Do we wait until it's done to talk about it? Come on...

The first part of the comment, maybe. But why not wait until everybody can comment on the new font - in just a few days when the font becomes public?:popcorn:

---

### Post by kyleabaker on 2010-08-02
> **JustinR said:**
> The first part of the comment, maybe. But why not wait until everybody can comment on the new font - in just a few days when the font becomes public?:popcorn:

You know you're talking to the people who **aren't** waiting to try the next version of Ubuntu right? Most of us are here to test the latest and greatest, not wait for public releases. :P

I've been using this font since the leaked beta a while back. Looks great so far!

---

### Post by x-shaney-x on 2010-08-03
Call me MR Picky but I actually thought the slight blurriness of the ripped fonts looked slightly better :)
Having said that I do like these fonts a lot, they're different but not TOO different if you know what I mean.

---

### Post by nilarimogard on 2010-08-03
> **JustinR said:**
> This news is oldddddddddddddddddddddddd - the private PPA has been out for a while now - just wait 'till August 5?th - the font will be public.


Except that now anyone with a Launchpad account can get access to the private PPA. The news is from yesterday :)

---

### Post by Starks on 2010-08-03
My god.

My Thunderbird inbox has never looked so sexy.

---

### Post by Starks on 2010-08-21
Font still has some issues.

---

### Post by kyleabaker on 2010-08-22
> **Starks said:**
> Font still has some issues.

Interesting. I've heard people mention problems, but I've not noticed any problems since I've been using it.

---

### Post by nilarimogard on 2010-08-22
> **kyleabaker said:**
> Interesting. I've heard people mention problems, but I've not noticed any problems since I've been using it.

The font got quite a few updates since this thread was created... it's much better now. 

But... what happened with the public beta which was supposed to start somewhere around August 5?

---

### Post by jpeddicord on 2010-08-22
> **nilarimogard said:**
> The font got quite a few updates since this thread was created... it's much better now. 

But... what happened with the public beta which was supposed to start somewhere around August 5?

Delayed: [http://design.canonical.com/2010/08/font-friday/](http://design.canonical.com/2010/08/font-friday/)
Though that was > 2 weeks ago, and I don't know what's happened since.


[QUOTE=Starks]Font still has some issues.[/QUOTE]Does that still look bad when using other themes?

EDIT: Tried it here and only see an issue with the Ambiance beta theme. Filed [lpbug]622284[/lpbug].

---

### Post by ktp on 2010-08-22
> **jpeddicord said:**
> Delayed: [http://design.canonical.com/2010/08/font-friday/](http://design.canonical.com/2010/08/font-friday/)
Though that was > 2 weeks ago, and I don't know what's happened since.

I am also wondering what is going on...I hope there is some news because I know they are working hard to fix issues.  Lets hope there is some news coming soon.

But is nice to use the font from private ppa.

---

### Post by Mr. Picklesworth on 2010-08-22
> **Starks said:**
> Font still has some issues.

> **kyleabaker said:**
> Interesting. I've heard people mention problems, but I've not noticed any problems since I've been using it.

Unless I'm mistaken, which I may be, the Bold style isn't in yet. In its absence, Freetype tries to approximate it using some tricks. The reason for that is each style is being done by hand. For example, the proper Italic style just landed a little while ago:
[http://design.canonical.com/2010/08/a-true-italic/](http://design.canonical.com/2010/08/a-true-italic/)
(I spent about half an hour playing around in Specimen after noticing that)

Similar magic is, as I understand it, going to happen with Bold. Later they'll work on other styles such as a light style and a monospaced style.
(DejaVu Sans is an example of a font that has lots of different styles, if you're wondering how that works).

By the way, that's a nice reason for this not being a massive, easily reached public release yet. It isn't finished, so if everyone and his dog starts sharing around this font *as if* it's finished, unfortunate things can happen ;)

If you do encounter text that is harder to read than it should be, consider submitting a bug report over at [fonttest.design.canonical.com]("http://fonttest.design.canonical.com/")

---

### Post by kyleabaker on 2010-08-22
> **Mr. Picklesworth said:**
> Unless I'm mistaken, which I may be, the Bold style isn't in yet. In its absence, Freetype tries to approximate it using some tricks. The reason for that is each style is being done by hand. For example, the proper Italic style just landed a little while ago:
[http://design.canonical.com/2010/08/a-true-italic/](http://design.canonical.com/2010/08/a-true-italic/)
(I spent about half an hour playing around in Specimen after noticing that)

Similar magic is, as I understand it, going to happen with Bold. Later they'll work on other styles such as a light style and a monospaced style.
(DejaVu Sans is an example of a font that has lots of different styles, if you're wondering how that works).

You may be right about the current Bold font, just even still...it looks very nice. :D

[IMG]http://a.imageshack.us/img838/7683/screenshot1mg.png[/IMG]

---

### Post by nilarimogard on 2010-08-22
> **Mr. Picklesworth said:**
> Unless I'm mistaken, which I may be, the Bold style isn't in yet. In its absence, Freetype tries to approximate it using some tricks. The reason for that is each style is being done by hand. For example, the proper Italic style just landed a little while ago:
[http://design.canonical.com/2010/08/a-true-italic/](http://design.canonical.com/2010/08/a-true-italic/)
(I spent about half an hour playing around in Specimen after noticing that)

Similar magic is, as I understand it, going to happen with Bold. Later they'll work on other styles such as a light style and a monospaced style.
(DejaVu Sans is an example of a font that has lots of different styles, if you're wondering how that works).

By the way, that's a nice reason for this not being a massive, easily reached public release yet. It isn't finished, so if everyone and his dog starts sharing around this font *as if* it's finished, unfortunate things can happen ;)

If you do encounter text that is harder to read than it should be, consider submitting a bug report over at [fonttest.design.canonical.com]("http://fonttest.design.canonical.com/")

Actually bold came in before italic. So it looks like they just have to fix the bugs now...

Edit: and here's a link to the announcement: [http://design.canonical.com/2010/07/ubuntu-font-beta-now-with-added-bold/]("http://design.canonical.com/2010/07/ubuntu-font-beta-now-with-added-bold/")

---

### Post by jpeddicord on 2010-08-22
Bold should already be included in the font if you're up-to-date. I clearly remember ugly window titles before bold was introduced, and now they look pleasant.

---

### Post by kyleabaker on 2010-08-23
The only annoyance I have with the new font is that it doesn't look as polished and clean when you enter your password into a dialog since the font size is so small..

[img]http://a.imageshack.us/img690/8434/screenshotcp.png[/img]

I hope they fix this by the time the new font is released so it looks as clean as the previous font did here.

---

### Post by dxxvi on 2010-08-23
Does anybody know which package on [http://packages.ubuntu.com/maverick/]("http://packages.ubuntu.com/maverick/") has these new fonts? Does anybody try them on Ubuntu 10.04?

Thank you.

---

### Post by MacUntu on 2010-08-23
So am I the only one that doesn't like the new font? Or, to be more specific: I don't like the font below the size of 14 pt. If it's smaller it looks like the next Comic Sans to me. :(

---

### Post by Kobalt on 2010-08-23
> **dxxvi said:**
> Does anybody know which package on [http://packages.ubuntu.com/maverick/]("http://packages.ubuntu.com/maverick/") has these new fonts? Does anybody try them on Ubuntu 10.04?

Thank you.

Here you go : [http://blog.nschirrer.com/testing-ubuntu-private-font](http://blog.nschirrer.com/testing-ubuntu-private-font)

---

### Post by TrueTom on 2010-08-23
> **MacUntu said:**
> So am I the only one that doesn't like the new font?

No,  don't like it either. It's a nice font for logos but way to playfull for a system font. Lucidia Grande is still the best... :)

---

### Post by coffeecat on 2010-08-23
> **TrueTom said:**
>  Lucidia Grande is still the best... :)

A person after my own heart! :wink: It is a most elegant desktop font. Problem is, we'll upset the freedom brigade, seeing as it's an Apple font.

<nitpicking_mode>
Actually it's Lucida Grande. You had too many i's. :p
</nitpicking_mode>

---

### Post by fooman on 2010-08-26
woah,  this font is awesome!

thanks for posting Starks.  :D

---

### Post by Cenotaph on 2010-09-16
what's the situation with the font if anyone have news? The public beta never happened, is this still going to make it to maverick?

---

### Post by 23meg on 2010-09-16
> **Cenotaph said:**
> what's the situation with the font if anyone have news? The public beta never happened, is this still going to make it to maverick?

Follow [the main inclusion + Feature Freeze exception bug]("https://bugs.launchpad.net/ubuntu/+bug/629622") for the latest happenings.

---

### Post by Cenotaph on 2010-09-17
thank you. i really hope to see this in maverick soon

---

### Post by lamb123 on 2010-09-18
This font seems to be buggy in terminal, no? Some letters overlapping and some widths between letters too big.

Also when I start terminal the '@' symbol username@machine-name line is messed a little.

Are these known bugs?

Other than that font is beautiful.

---

### Post by MacUntu on 2010-09-18
Why would you use a variable width font in a terminal?

---

### Post by lamb123 on 2010-09-18
> **MacUntu said:**
> Why would you use a variable width font in a terminal?

Dunno, i will try to learn whats the difference now. :)

---

### Post by krazyd on 2010-09-18
> **lamb123 said:**
> This font seems to be buggy in terminal, no? Some letters overlapping and some widths between letters too big.

Also when I start terminal the '@' symbol username@machine-name line is messed a little.

Are these known bugs?

Other than that font is beautiful.

Terminals align glyphs in columns and expect fixed width fonts with the same size even for bold and italic variants (so can't even use monospaced fonts without bold & italic glyphs because freetype's "bold approximation" changes the glyph width).

Unfortunately it looks like the monospaced variant isn't going to be completed until next year..
[https://bugs.launchpad.net/ubuntu-font-family/+bug/640382](https://bugs.launchpad.net/ubuntu-font-family/+bug/640382)

I really hope it's better than [Consolas](http://www.microsoft.com/typography/fonts/family.aspx?FID=300), my current favourite monospaced font. I feel a bit dirty using a microsoft product! :-P

---

### Post by Reiger on 2010-09-18
Well Consolas *is* an awesome font.

---

