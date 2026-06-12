---
title: "Rhythmbox Lyrics cannot display Apostrophes."
date: 2010-12-30
forum: Multimedia Software
---

### Post by silkworm2.5 on 2010-12-30
Hi.
I just set up my Rhythmbox to download the lyrics to my songs. It can get them allright, but when it try to display apostrophes it gives me a strange code instead of it.
I'm becomes "l  & # 0 3 9 ;  m", You're becomes "You  & # 0 3 9 ;  re".
I did some tweaking to see if it was the lyric providers. I found that only AstraWeb and TerraBrasil provided me with the lyrics, and both gave me the same problem, so I assume it must be a problem with Rhythmbox. Can anyone help please?

By the way, I don't think it matters much, but I'm Running Ubuntu 10.04 64 Bit.

(I just tried to add the code in as it appeared, but it displayed as a normal apostrophe, so I added the spaces.)

---

### Post by jehozadakk on 2011-01-02
I am having the exact same issue, same symptoms.  Most of the databases don't work, only TerraBrasil.  When it does find lyrics, it has trouble formatting the display properly.  Also using Ubuntu 10.04 64 bit.  Any help would great.

---

### Post by RobertoRecordo on 2011-01-05
> **jehozadakk said:**
> I am having the exact same issue, same symptoms.  Most of the databases don't work, only TerraBrasil.  When it does find lyrics, it has trouble formatting the display properly.  Also using Ubuntu 10.04 64 bit.  Any help would great.

again, 10.04 64 bit  - in FireFox apostrophe doesn work right - two apostorpe´s (just did two, I see one) to create one. If i type quote I apostrophe m quote   it creates a I&#7743;   (i see a special m character with a with something over it, not apostrophe m)

oh oh, I just opened accesoris/character map...this is not a firefox issue, I have the problem when typing in the search bar their, too. and in gedit.

I&#7743; a noob and I don know what to do next:confused:

9 January 2011 - discovered System > Preferences > Keyboard >   changed to standard US keyboard: now I don't have a problem.

---

### Post by silkworm2.5 on 2011-01-10
I see the weird accented M too. But not when I do it. Rhythmbox is the only application I have this issue with. I tried changing to the American Keyboard layout, but it made no difference.

One other thing... Sometimes when I hold the left shift key to write a capital letter, it doesn't capitalize it. It only happens with certain letters, and I can make it happen again. But then again, I have this issue in Windows too.
Anyone know anything to try?

---

### Post by silkworm2.5 on 2011-01-12
Bump

---

### Post by silkworm2.5 on 2011-01-22
Bump

---

### Post by angus73 on 2011-03-24
Hi, I also had this problem but I have just solved it. There is a patch for this at

[http://git.gnome.org/browse/rhythmbox/commit/?id=a1795c3dd1f00e351800d904970e018a8dedf7df](http://git.gnome.org/browse/rhythmbox/commit/?id=a1795c3dd1f00e351800d904970e018a8dedf7df)

The problem was a faulty regex in TerraParser.py

Remember to restart rhythmbox after you have applied the patch, and empty your lyrics folder if you set one.

Let me know if this solved it for you, too

Best wishes!
Andrea

---

### Post by silkworm2.5 on 2011-05-08
Wow! Thank you so much! That just solved the one problem I had with Rhythmbox! I wish I'd checked back sooner now ^^; Thank you!

---

### Post by angus73 on 2011-05-08
> **silkworm2.5 said:**
> Wow! Thank you so much! That just solved the one problem I had with Rhythmbox! I wish I'd checked back sooner now ^^; Thank you!
Great ;-)
Please add [SOLVED] to the thread title, thanx

Best regards,
Angus73

---

### Post by coolmauistuff on 2011-05-23
sorry for being so stupid but:
I have the same problem- what do I do with [http://git.gnome.org/browse/rhythmbo...0e018a8dedf7df](http://git.gnome.org/browse/rhythmbo...0e018a8dedf7df) patch?

---

### Post by angus73 on 2011-05-24
> **coolmauistuff said:**
> sorry for being so stupid but:
I have the same problem- what do I do with [http://git.gnome.org/browse/rhythmbo...0e018a8dedf7df](http://git.gnome.org/browse/rhythmbo...0e018a8dedf7df) patch?

just find the file TerraParser.py in your file system (for me it's located in /usr/lib/rhythmbox/plugins/lyrics/), and replace the file TerraParser.py with the file attached to comment#2 of the bug619247 page. Best if you first make a backup copy of the original TerraParser.py

Best wishes
A.

---

### Post by czgirb on 2012-07-13
> **angus73 said:**
> Hi, I also had this problem but I have just solved it. There is a patch for this at

[http://git.gnome.org/browse/rhythmbox/commit/?id=a1795c3dd1f00e351800d904970e018a8dedf7df](http://git.gnome.org/browse/rhythmbox/commit/?id=a1795c3dd1f00e351800d904970e018a8dedf7df)

The problem was a faulty regex in TerraParser.py

Remember to restart rhythmbox after you have applied the patch, and empty your lyrics folder if you set one.

Let me know if this solved it for you, too

Best wishes!
Andrea

Hi! I would like to try that too.
Would you mind for doing a favor by guiding me over it?
Cos my computer's (Linux especially) are minim.
So I do not understand what you said.
Please .....................

---

### Post by wildmanne39 on 2012-07-13
Hi, this is an old thread so it has been closed please start a new thread of your own with a descriptive title. 
Thanks

---

