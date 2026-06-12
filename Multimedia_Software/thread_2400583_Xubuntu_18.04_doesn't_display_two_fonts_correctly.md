---
title: "Xubuntu 18.04 doesn't display two fonts correctly"
date: 2018-09-07
forum: Multimedia Software
---

### Post by tmp79 on 2018-09-07
I've just installed Xubuntu 18.04.1 on a laptop and, even after installing the "ttf-mscorefonts-installer" package, although I can now see some of the fonts on my blog being displayed correctly, still the "Book Antiqua" and "Helvetica" ones are substituted by other fonts.

=====================[Examples]=====================

1) For Book Antiqua, notice the "g" (on the word "Engels") in the following screenshot (from this blog post: [https://blackfernando.blogs.sapo.pt/o-real-objectivo-da-falsa-esquerda-do-144494](https://blackfernando.blogs.sapo.pt/o-real-objectivo-da-falsa-esquerda-do-144494)) and compare it to a sample of this font here: [http://www.identifont.com/show?1MX](http://www.identifont.com/show?1MX)

[[IMG]https://s15.postimg.cc/4xn7r4onb/Screenshot_2018-09-06_14-52-57.png[/IMG]]("https://postimg.cc/image/4xn7r4onb/")

2) For Helvetica, notice the "y" (on the word "Party") in the following screenshot (from this blog post: [https://blackfernando.blogs.sapo.pt/voltamos-aos-atentados-de-bandeira-146254](https://blackfernando.blogs.sapo.pt/voltamos-aos-atentados-de-bandeira-146254)) and compare it to a sample of this font here: [http://www.identifont.com/show?MR](http://www.identifont.com/show?MR)

[[IMG]https://s15.postimg.cc/3wrkfb9rr/Screenshot_2018-09-06_14-49-43.png[/IMG]]("https://postimg.cc/image/3wrkfb9rr/")

=================================================

I have had this same problem when using Debian, without the default desktop environment. And, for some reason, in Debian I can "solve" it by installing GIMP and its dependencies ([http://forums.debian.net/viewtopic.php?f=6&t=137150#p678676](http://forums.debian.net/viewtopic.php?f=6&t=137150#p678676)). But, having I tried the same method in Xubuntu, it didn't work. (And repeatedly using the command "sudo fc-cache -f -v" to refresh the fonts cache files doesn't solve the problem either.)

I'm very much clueless as to why this happens. But, I suspect that I probably need to install some library/package, for these fonts to be properly displayed (instead of being substituted by other fonts), and I think that only one of these fonts, that I'm trying to make be correctly displayed, is still a "Windows" font.

Also, I know very little about these font issues. I just have the strong impression that this problem didn't occur on previous versions of Xubuntu that I've used.

---

### Post by tmp79 on 2018-09-22
I just came here to add that,

Even if I follow the Debian instructions (I've written here: [http://forums.debian.net/viewtopic.php?f=6&t=137150#p678676](http://forums.debian.net/viewtopic.php?f=6&t=137150#p678676)) on how to make fonts render properly, after a minimal installation (i.e. even if I create or modify the "~/.Xdefaults", "~/.config/fontconfig/fonts.conf" and "~/.Xresources" files) still these two fonts are not properly displayed.

---

### Post by tmp79 on 2018-09-22
Also, I was able to test an old laptop I remembered I have, that still has Xubuntu 16.04 installed, and on that laptop these fonts are *properly* displayed...

So, as I suspected, this is a problem that appeared in this new (18.04) version of Xubuntu.

---

### Post by Holger_Gehrke on 2018-09-22
Both of these are commercial fonts (Helvetica by Lynotype, Book Antiqua by Monotype). Neither of them is part of the ttf-mscorefonts-installer package (check 'apt show ttf-mscorefonts-installer' to see which fonts are). So you're very likely to get some substitute for both fonts on a Linux system. Add to this the deprecation of (Postscript) Type1 Fonts due to the use of Harfbuzz for type rendering.

The situation in a web browser is slightly different because the web master might either host a font on his site and refer to it in his CSS or use a provider like fonts.com (or google) to get fonts.

Holger

---

### Post by tmp79 on 2018-09-22
Hi, Holger.

Thank you for your information. (Indeed, whenever I install the "ttf-mscorefonts-installer" package, I can see references to several fonts, but never to these two...)

This situation that I describe (of the fonts being properly displayed when using 16.04, but not when using 18.04) happens on the exact same webpages (i.e. I'm using the same "experimental samples" - and, I'll post tomorrow some screenshots to demonstrate it).

So, whatever is the way that Xubuntu has to deal with these two fonts, it has changed from 16.04 to 18.04 - and, now they are not properly displayed.

---

### Post by tmp79 on 2018-09-23
So, the following are, respectively, the screenshots I get when using **Xubuntu 16.04** and **Xubuntu 18.04** on a laptop,

1) when using [this]("https://blackfernando.blogs.sapo.pt/voltamos-aos-atentados-de-bandeira-146254") "experimental sample":

[[IMG]https://i.postimg.cc/F7sYhKC9/Captura_de_ecr_2018-09-23_07-21-12.png[/IMG]]("https://postimg.cc/F7sYhKC9")

[[IMG]https://i.postimg.cc/T5232k9k/Captura_de_ecr_2018-09-23_07-38-44.png[/IMG]]("https://postimg.cc/T5232k9k")

2) and when using [this]("https://blackfernando.blogs.sapo.pt/como-o-ditador-estaline-descarrilou-os-147252") "experimental sample":

[[IMG]https://i.postimg.cc/QHydsJWb/Captura_de_ecr_2018-09-23_07-22-46.png[/IMG]]("https://postimg.cc/QHydsJWb")

[[IMG]https://i.postimg.cc/vxmGw4Yk/Captura_de_ecr_2018-09-23_07-39-44.png[/IMG]]("https://postimg.cc/vxmGw4Yk")

---

### Post by Holger_Gehrke on 2018-09-23
Try fc-match on both machines to see what fonts they actually use when asked to display a specific font.
```

fc-match 'Helvetica'
fc-match 'Book Antiqua'

```
With a bit of luck you'll know what font to install after this. 

Be aware though: just because it displays correctly on your machine doesn't mean it will display correctly on your reader's browsers. That's why using unusual fonts on the web is a bad idea unless you're providing the font to the reader in some way, as I mentioned in Post #4.

Holger

---

### Post by tmp79 on 2018-09-23
Hello again, Holger.

Thank you very much for your help, and your explanations. :)


Yes, after starting to use other devices myself, I realized that the same texts on my blog are displayed differently, depending on the OS - and even the browser - used... But, I'm hoping that these fonts are at least displayed properly on the major desktop OSes (Windows, Mac OS) so that I can have a good idea of how my texts will appear to most people on their home computers.

And, as for what appears on my and other people's GNU/Linux computers, using the "identifont.com" website (that I link to in [Post #1]("https://ubuntuforums.org/showthread.php?t=2400583&p=13798821#post13798821")) the (after all) "substitutes" that GNU/Linux (usually) uses were enough to fool me. And, being so identical to the original font, if I can get these same "substitutes" to be used again, that's what I mean (then) by having these two fonts "properly displayed".

*(And, as for the fonts I've chosen, these two are part of the lists of fonts offered by the two mainstream blog hosting services I've used, which have both short lists of fonts - so, there's not much to choose from. And, being at least the first font offered by both blogging services, I had no idea that these fonts could be problematic... And, now it's too late or inconvenient to change everything...)* :\


Here are the results of those commands,

1) on _Xubuntu 16.04_:

(Helvetica)             **n019003l.pfb: "Nimbus Sans L" "Regular"**
(Book Antiqua) **    DejaVuSans.ttf: "DejaVu Sans" "Book"**

2) on _Xubuntu 18.04_:

(Helvetica)             **Arial.ttf: "Arial" "Regular"**
(Book Antiqua)     **DejaVuSans.ttf: "DejaVu Sans" "Book"**


Which could explain the differences when using "experimental sample 1" (first pair of screenshots, on [Post #6]("https://ubuntuforums.org/showthread.php?t=2400583&p=13802983#post13802983")), but apparently not when using "experimental sample 2" (second pair of screenshots).

Anyway, any idea on what should I do next?


=======[Extra]=======

3) By the way, the following are the results I get when using Debian 9 (on which Xubuntu 16.04 is based, and) that also displays these two fonts correctly:

(Helvetica)        n019003l.pfb: "Nimbus Sans L" "Regular"
(Book Antiqua)   NotoSans-Regular.ttf: "Noto Sans" "Regular"

Which just adds to the confusion...

---

### Post by Holger_Gehrke on 2018-09-23
I think I'm getting closer to the root of the problem ...

In the html of the blog you're giving the font-family in a style-attribute as "font-family: book antiqua, palatino;". While this is quite correct ('book antiqua' is a Monotype lookalike of Linotype's 'Palatino'), if you look at the results of fc-match you'll be surprised:
```

$ fc-match 'Palatino'
DejaVuSerif.ttf: "DejaVu Serif" "Book"
$ fc-match 'Book Antiqua'
DejaVuSans.ttf: "DejaVu Sans" "Book"

```
And checking with the 'Inspector' in the firefox web-developer tools, I find it's actually using "DejaVu Serif". This seems correct, since it falls through from the first to the last looking for a font it has and then using a substitution for the last one it doesn't have. So after looking for a better match for the Palatino, I ended up installing the package 'fonts-texgyre', a package containing free lookalikes of the 35 standard Postscript fonts of which Palatino is one. Now the text set in Palatino (or "Book Antiqua") comes out in "TeX Gyre Pagella" (which is what fc-match says to use for Palatino after installation of the font package; strangely the match for "Book Antiqua" does not get changed). Comparing the sample of "Book Antiqua" and "Palatino" at identifont.com to text set in "TeX Gyre Pagella" makes it seem like a very close match indeed.

Holger

---

### Post by tmp79 on 2018-09-29
Hello again, Holger.

Thank you very much for your help, and your detailed explanations...

But, I've just discovered that I can't also make my scanner work with this new (18.04) version of Xubuntu (but am able to with another distro). And, because this last functionality is something that I really need to have working on my laptops, I'm going to have to abandon Xubuntu for that other distro (Debian).

Anyway, because this thread - of the problem related to the two fonts I mentioned - might be of interest to someone else, I'll leave it "open", in case anyone is interested in solving this problem. (But, in my case, unfortunately it is no longer of interest to me to search for a solution - and, above all, I also won't be able to make any more tests.) :\

Thank you very much again, Holger, for all your help.

---

