---
title: "No window decorations with Compiz"
date: 2010-11-19
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by NCLI on 2010-11-19
Anyone else having this problem? I can manage by opening a terminal and running metacity --replace, but it's quite annoying.

Also, trying to launch Unity returns "The program 'unity' is currently not installed.  You can install it by typing:
sudo apt-get install unity", even though it is installed.

EDIT: Ok, CCSM is also MIA... I'm starting to think I botched the install somehow...

EDIT2: And I am officially an idiot. I just needed to *install* ccsm, then enable the "Ubuntu Unity" and "Window Decorations" plugins. 


...duh

---

### Post by Quackers on 2010-11-20
The only way I can keep the Window borders and the minimize/maximize buttons is by using the gtk windows decorations. Emerald loses them, whereas in Maverick it works fine. Is emerald no good now?

---

### Post by Decatf on 2010-11-20
Seems like it. I don't think anybody has really worked on Emerald since the Compiz C++ port began.

---

### Post by Quackers on 2010-11-20
Ah, ok, thanks. I don't think I've seen anything about emerald being updated myself.

---

### Post by Anduu on 2010-11-20
Yup Emerald is definitely broken for 0.9x Compiz as is fusion-icon.

Been poking around some on the Compiz forums and it seems poeple are working on Emerald...start here:

[http://forum.compiz.org/viewtopic.php?f=112&t=12565&hilit=emerald&start=150](http://forum.compiz.org/viewtopic.php?f=112&t=12565&hilit=emerald&start=150)

I haven't read through all the posts so I don't know if there is any source code that can be tried out by the general public but there may be...

---

### Post by Quackers on 2010-11-20
> **Anduu said:**
> Yup Emerald is definitely broken for 0.9x Compiz as is fusion-icon.

Been poking around some on the Compiz forums and it seems poeple are working on Emerald...start here:

[http://forum.compiz.org/viewtopic.php?f=112&t=12565&hilit=emerald&start=150](http://forum.compiz.org/viewtopic.php?f=112&t=12565&hilit=emerald&start=150)

I haven't read through all the posts so I don't know if there is any source code that can be tried out by the general public but there may be...

ooh thanks, I'll have a look at that when I've finished re-installing :-)

---

### Post by Baul on 2010-11-22
I don't know if other people are having this problem - but compiz does not seem to shut down when I exit Ubuntu (Obviously Narwhal is very early in the developmental process)  - Like many people I had a real problem with the panel "max,min and exit" disappearing last week - however it seemed to be corrected by stripping out compiz and nvidia drivers and then updating.

Yet one of the bug that preceded not having a (X-windows desktop?) functioning computer was this recurring thing about a programme not being able to shut down.

There is no crash report the I can file - but the problem seems to be consistent.

I have used this as a testing/learning process - so my machine is probably is loaded with old files and propriety files (Dropbox and Nvidia).

I upgraded from Karmic to Lucid to Maverick to Narwal and have always bkup data so it not a loss to re-install - I was interested to see what went wrong along the way! 

One thing I tried was enabling "Unity" but it gave me a desktop with no access to programmes (again last week when I was trying to problem solve).

If anyone has comments on this hangup when compiz seems to stall on shut-down I would be interested to hear.

---

### Post by cariboo on 2010-11-22
At this point there isn't much to worry about, I'm sure we all see the same thing, I know I do on the 5 systems I have Natty installed on.. The time to start worrying, is if it is still around by alpha 3. :) :)

---

### Post by Baul on 2010-11-22
Cheers Caraboo307

Hopefully I can help out in discovering and tracking bugs!

---

### Post by Slug71 on 2010-11-23
Slightly off topic but is Compiz 0.9 going to be default in Natty?

---

### Post by MacUntu on 2010-11-23
? Natty already has 0.9.2. AFAIK 0.9.4 is the target (not sure, though).

---

### Post by Slug71 on 2010-11-23
> **MacUntu said:**
> ? Natty already has 0.9.2. AFAIK 0.9.4 is the target (not sure, though).

Thanks.

---

### Post by bladerunner6 on 2010-11-24
i have to type metacity --replace in terminal to get the full bars working
(latest updates natty)
how do make metacity automatically enabled?

---

### Post by avaddon on 2010-12-15
> **bladerunner6 said:**
> i have to type metacity --replace in terminal to get the full bars working
(latest updates natty)
how do make metacity automatically enabled?

Uninstall emerald
or
In compiz "window decoration" plugin change /usr/bin/compiz-decorator to /usr/bin/gtk-window-decorator

---

### Post by chrismine on 2010-12-15
I found that you lose right click funcionality with Compiz and Unity running in Naautilus, Firefox and Chrome.

Does it happen on your installs also?

---

### Post by ntetreau on 2011-03-02
> **avaddon said:**
> Uninstall emerald
or
In compiz "window decoration" plugin change /usr/bin/compiz-decorator to /usr/bin/gtk-window-decorator

Thanks, that worked perfectly.  Else, I lose my window decorations every 5 minutes using emerald...

---

### Post by beew on 2011-03-03
> **Anduu said:**
> Yup Emerald is definitely broken for 0.9x Compiz as is fusion-icon.

Been poking around some on the Compiz forums and it seems poeple are working on Emerald...start here:

[http://forum.compiz.org/viewtopic.php?f=112&t=12565&hilit=emerald&start=150](http://forum.compiz.org/viewtopic.php?f=112&t=12565&hilit=emerald&start=150)

I haven't read through all the posts so I don't know if there is any source code that can be tried out by the general public but there may be...

Sorry your link doesn't work.

---

