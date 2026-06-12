---
title: "Gnome 3; usable?"
date: 2011-04-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by encefalocardia on 2011-04-03
Last time I added the Gnome 3 Stack rep and updraged Gnome ended as a total mess. Crashing every minute, looking like 1998 all over again and as clunky as a dell computer.

However, after visiting [http://www.gnome3.org/](http://www.gnome3.org/) yesterday I liked what I saw so I_ was wondering, how many here are using Gnome 3 on Natty? It looks that good as the screenshots? It is usable?

---

### Post by 5149.5 on 2011-04-03
Last night I  added the gnome3 ppa, updated, and upgraded to see what would happen.  After reloading , I couldn't login and ended up using upgrade from my usb to recover my install.

---

### Post by cariboo on 2011-04-03
THere hasn't been much work done on gnome 3 during this cycle, I'd suggest you try Fedora 15, or wait until the next dev cycle.

---

### Post by ronacc on 2011-04-03
its pretty stable for me when locally compiled .

Edit : oops please ignore I thought he ment Gnome-shell

---

### Post by msrinath80 on 2011-04-03
> **encefalocardia said:**
> Last time I added the Gnome 3 Stack rep and updraged Gnome ended as a total mess. Crashing every minute, looking like 1998 all over again and as clunky as a dell computer.

However, after visiting [http://www.gnome3.org/](http://www.gnome3.org/) yesterday I liked what I saw so I_ was wondering, how many here are using Gnome 3 on Natty? It looks that good as the screenshots? It is usable?

I downloaded the Fedora based Live CD from their webpage to give it a shot. Is it pretty. Totally. Is is usable? Not so much. I found myself irritated with it after an hour.

---

### Post by kansasnoob on 2011-04-03
> **5149.5 said:**
> Last night I  added the gnome3 ppa, updated, and upgraded to see what would happen.  After reloading , I couldn't login and ended up using upgrade from my usb to recover my install.

It's been a few days for me but ditto.

If you look here:

[https://launchpad.net/~gnome3-team/+archive/gnome3/+packages](https://launchpad.net/~gnome3-team/+archive/gnome3/+packages)

I assume the "101 failed" actually means something ;)

---

### Post by Quackers on 2011-04-03
Could somebody enlighten me please? 
What is the difference between Gnome3 and gnome-shell?
I'm confused!

---

### Post by thiebaude on 2011-04-03
Gnome 3, is the next version of gnome

---

### Post by CoolJohnB on 2011-04-03
I also tried Gnome 3 which worked fine, although I didn't like it much and it disabled ALL my Ubuntu desktops i.e. Ubuntu -Unity and Ubuntu-Classic the only way I was able to get them back was to do a re-install!

---

### Post by Quackers on 2011-04-03
> **thiebaude said:**
> Gnome 3, is the next version of gnome

and gnome-shell?

---

### Post by kansasnoob on 2011-04-03
> **Quackers said:**
> Could somebody enlighten me please? 
What is the difference between Gnome3 and gnome-shell?
I'm confused!

Gnome3 is the gnome base itself. ATM they're pushing ahead with 100% focus on gnome-shell which is their default UI for gnome3.

When Fedora 15 alpha released it had no option but gnome-shell w/gnome3. They've since added the option to use "panels" similar to gnome 2.3* but IMHO it's really, really rough - even for an alpha.

You can also get a test version here:

[http://www.gnome3.org/tryit.html](http://www.gnome3.org/tryit.html)

NOTE: I haven't tried the openSUSE version, nor will I.

I find it interesting that Mint is supposedly going to build on the Natty base w/gnome3 and a panel similar to what they usually do. AFAIK they'll be the first with a gnome3 final release ...... AFAIK!!!!!!!!!!!!!

---

### Post by kansasnoob on 2011-04-03
> **CoolJohnB said:**
> I also tried Gnome 3 which worked fine, although I didn't like it much and it disabled ALL my Ubuntu desktops i.e. Ubuntu -Unity and Ubuntu-Classic the only way I was able to get them back was to do a re-install!

How can you say, "it worked fine", if you didn't like it and couldn't use a different DE?

I had a mule once that I really liked, but the second time it kicked me it was gone :lolflag:

---

### Post by msrinath80 on 2011-04-03
> **kansasnoob said:**
> How can you say, "it worked fine", if you didn't like it and couldn't use a different DE?

I had a mule once that I really liked, but the second time it kicked me it was gone :lolflag:

I guess he was trying to say that it did not crash/hang  on him?

---

### Post by Quackers on 2011-04-03
Thanks kansasnoob :-)
I've tried Fedora15 with gnome-shell and I've currently got opensuse 11.4 using gnome-shell. It works well and I like it. I'm currently building from source in Natty.
TBH I thought gnome-shell and gnome3 were the same thing. Hence my confusion :-)

---

### Post by Mblackwell on 2011-04-03
Gnome 3 from the PPAs is mildly broken. Most things will work but for example rhythmbox didn't start the other day, and for whatever reason I couldn't gksudo/sudo most apps. Basically at this point it's adding more breakages on top of what's already there from the last few weeks in Natty. On top of that Shell was broken because it needed a slightly newer version of gjs.  For most people it's not really worth it and I'd just say wait until after 1) April 7th, so G3 is officially released and 2) Natty has calmed down a bit more.

Compiling just Gnome Shell though is fun and simple. There are two current issues though (one might be caused by Ubuntu's libtool, and the other is caused by a bug with search providers in Shell itself). They can be worked around at this point though.

I have to say that the Gnome 3 apps using the Adwaita theme are quite lovely.

Edit: For those that try it from repositories, don't forget to have ppa-purge on hand.

---

