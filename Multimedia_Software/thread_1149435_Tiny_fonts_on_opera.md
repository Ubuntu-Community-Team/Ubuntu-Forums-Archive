---
title: "Tiny fonts on opera"
date: 2009-05-05
forum: Multimedia Software
---

### Post by 0liv on 2009-05-05
Hi there!

I'm a bit bored that I frequently have to zoom in (a lot)
to be able to read half the websites when surfing with Opera 
(now 9.64 but my problem predates this version).

I don't have this problem neither with Firefox nor with Epiphany.

I've tried many ideas I've read in forums but nothing worked.

Could you help me, pleeeease?!

---

### Post by .nedberg on 2009-05-05
Go to Tools->Prefrences->Advanced->Fonts

You can set default font size there. Mine is set to 9 on a Windows machine. You can also change a lot of other font relatet stuff there.

---

### Post by .nedberg on 2009-05-05
You can also try to run opera with```
opera -personaldir ~/testopera
```

It will create a new folder for operas settings (testopera). and you will see if it is a problem with some of the settings.

---

### Post by 0liv on 2009-05-05
I tried "opera -personaldir ~/testopera" but
it doesn't change a damn thing [-X
Too bad...

But thanks for this tip: great way to investigate! :)

Then I tried to change the minimal font size.
It works as it enlarge the font but 
I have to put it into the 12-16 px range.

This doesn't look nice on most page because
the line-height is not scaled accordingly.
So i have readable font but cramped lines
and that's not a lot more readable... :(

Any other ideas?

---

### Post by .nedberg on 2009-05-05
Could you give me some links to pages with this problem?

I can test with WinXP from work and K/Ubuntu when I get home.

-personaldir did change something I hope? Like startpage and other things? I found -personaldir on opera.com, but IIRC I used -pd earlier... Opera should start with "Welcome to Opera" like it did the first time you started it.

---

### Post by 0liv on 2009-05-05
Here is two example of painful-to-read-on-opera website: 
* [http://www.jthink.net/jaikoz/](http://www.jthink.net/jaikoz/)
* [http://www.swarthmore.edu/NatSci/echeeve1/Ref/mna/MNA1.html](http://www.swarthmore.edu/NatSci/echeeve1/Ref/mna/MNA1.html)

BTW, you mention Opera on XP... 
I have no problem with the display on this OS.

And, yes, lots of things have changed 
with the alternate opera launch.
I meant "nothing regarding the fonts".

---

### Post by .nedberg on 2009-05-05
I just tested that page with Opera on XP, Opera on Ubuntu and Firefox on Ubuntu, all look the same!

Could it be that you are missing some fonts?

```
sudo apt-get install msttcorefonts
```

EDIT: No, I didn't have that on my machine either...

---

### Post by .nedberg on 2009-05-05
In fact, the fonts in Opera on both those pages are a blit bigger than on WinXP. They are, however, smaller than in Firefox on Ubuntu.

I suspect some problem with the fonts used by those pages.

---

### Post by 0liv on 2009-05-05
First, here is another example :
[http://www.swarthmore.edu/NatSci/echeeve1/Ref/mna/MNA1.html](http://www.swarthmore.edu/NatSci/echeeve1/Ref/mna/MNA1.html)

You can see the difference between Epiphany and Opera
thanks to the two attached screenshots.

Then, the msttcorefonts package is installed on my computer.
Removing it doesn't solve my problem :-(

:confused:

---

### Post by Arup on 2009-05-05
[http://www.robodesign.ro/mihai/blog/fix-configure-linux-font-rendering](http://www.robodesign.ro/mihai/blog/fix-configure-linux-font-rendering)

try this and also in opera:config under user prefs untick enable xcore fonts.

---

### Post by 0liv on 2009-05-05
**font rendering:** I already tried to tweak those settings in a lot of ways but that doesn't change anything regarding font size in Opera

**xcore fonts:** it was already unticked... so I tried and ticked it but nothing changed

:confused:

---

### Post by .nedberg on 2009-05-05
I'll do some more tests when I get home. But I'm afraid I can't help you more. The -personaldir should have shown the page with all the default settings. You didn't edit any of Operas default css files?

You could try to dl opera in tar.gz format and unpack it. You can then run a completely separate "install" of opera from that folder.

removing everything Opera-related and reinstall is another option...

---

### Post by .nedberg on 2009-05-05
I am now at home and have tested with Opera on Ubuntu and Kubuntu, both pages look fine here.

Some thoughts:
-Go to Show->Style, only "Author mode" should be selected
-opera:config, search for font. In "author mode" author font should be used.
-Try to dl opera in tar.gz format and test with that version
-Try a beta version of Opera 10 and see if the problem is still there
-Go to [http://my.opera.com/community/forums/](http://my.opera.com/community/forums/) and ask there
-It might be some setting in Gnome
-Tools->Settings->Advanced->Fonts find the one for normal webpages and see what it is set to (mine is times new roman(monotype) size 16)

---

### Post by 0liv on 2009-05-06
Okay, solved... This was a complex one.

[LIST=1]
[*] I've downloaded the tar.gz Opera and tested it: everything was fine. 
    So the problem was not with Gnome but only with Opera configuration.


[*] I checked if Show->Style was on Author mode only. 
    It was the case.


[*] I checked the Author Display Mode section of the opera:config page.
    Author Font and Colors was checked. 

    So was User Font and Colors, too! 
    So, I tried and unckeched it: the above mentionned page became readable!
    
    But it was not perfect, yet: a tad smaller than with fresh tar.gz Opera.


[*] So I checked in Tools->Settings->Advanced->Fonts the normal webpage text font.
    Its its size was 14.
    Changed it to its default of 16 (as in the tar.gz Opera) and ...boom, baby... that was it!
[/LIST]

Many thanks for your help! :KS

Note that Opera settings always fills the gaps stylewise. 
To see what I mean, have a look at [http://www.jthink.net/jaikoz/]("http://www.jthink.net/jaikoz/").
Its css files only specify the font family to use and let the browser use its default font size.
That's why it displays a *sans* font whose size depends on the *normal webpage text* font setting of Opera, even if this one is a *serif* font.

---

### Post by glotz on 2009-05-06
Can't read the *librettos*? lol

---

### Post by .nedberg on 2009-05-06
Glad it worked out for you!

Strange thing that it didn't work with -personaldir...

---

### Post by 0liv on 2009-05-07
**-personaldir:** I don't know why. I've tried it a few times during the whole process and it always showed me the same thing as with my main Opera settings.

---

### Post by .nedberg on 2009-05-07
As long as it worked out for you! I noticed that 'opera -help' lists -pd instead of -personaldir. Might be related, but I don't think so...

---

