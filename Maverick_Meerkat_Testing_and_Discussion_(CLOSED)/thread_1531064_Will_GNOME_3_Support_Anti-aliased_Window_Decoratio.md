---
title: "Will GNOME 3 Support Anti-aliased Window Decorations?"
date: 2010-07-14
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by cyberkilla on 2010-07-14
Hello, will GNOME 3 support anti-aliased window decorations?

Without resorting to Emerald, that is.

---

### Post by cyberkilla on 2010-07-15
Does nobody know?:)

Of all the things they're changing for GNOME 3, you'd think someone would have latched onto this by now.

---

### Post by zekopeko on 2010-07-15
One can only hope. Why don't you file a bug against mutter in Unity project?

---

### Post by cyberkilla on 2010-07-16
> **zekopeko said:**
> One can only hope. Why don't you file a bug against mutter in Unity project?

I would, but the problem is just so incredibly obvious. If they aren't working on it now, they have their reasons, I'd imagine.

Does anybody know anything about it?

---

### Post by zekopeko on 2010-07-16
> **cyberkilla said:**
> I would, but the problem is just so incredibly obvious. If they aren't working on it now, they have their reasons, I'd imagine.

Does anybody know anything about it?

Don't assume. File a bug or I will.

EDIT: Bug filed: [https://bugs.launchpad.net/unity/+bug/606315](https://bugs.launchpad.net/unity/+bug/606315)

---

### Post by cyberkilla on 2010-07-16
> **zekopeko said:**
> Don't assume. File a bug or I will.

EDIT: Bug filed: [https://bugs.launchpad.net/unity/+bug/606315](https://bugs.launchpad.net/unity/+bug/606315)

I wasn't assuming. I was imagining;)

Thanks for submitting it though. Fingers crossed..

---

### Post by cb951303 on 2010-07-16
I think it's called RGBA support not anti-aliasing.

---

### Post by cyberkilla on 2010-07-16
> **cb951303 said:**
> I think it's called RGBA support not anti-aliasing.

Good point. I should have mentioned that in the thread title.

---

### Post by cyberkilla on 2010-07-18
Anyone heard something about this yet?

---

### Post by autocrosser on 2010-07-18
Well--I would be "fairly" sure that RGBA will be used & a accelerated desktop is also a "fair" bet.....One of the interesting reads I have came across is:  [http://live.gnome.org/MikkelKamstrup/Gnome3Vision](http://live.gnome.org/MikkelKamstrup/Gnome3Vision)

Not sure how much of that document will come to pass, but there is mention of "bling"---so we can only hope.................

---

### Post by 23meg on 2010-07-22
> **zekopeko said:**
> Don't assume. File a bug or I will.

EDIT: Bug filed: [https://bugs.launchpad.net/unity/+bug/606315](https://bugs.launchpad.net/unity/+bug/606315)

Is there a particular reason you reported the bug in Unity, rather than Metacity / Mutter upstream (where there is [an existing bug report]("https://bugzilla.gnome.org/show_bug.cgi?id=345249") anyway)? Unity uses Mutter, but is an unlikely party when it comes to implementing the feature in GNOME 3.

---

### Post by cyberkilla on 2010-07-22
> **23meg said:**
> Is there a particular reason you reported the bug in Unity, rather than Metacity / Mutter upstream (where there is [an existing bug report]("https://bugzilla.gnome.org/show_bug.cgi?id=345249") anyway)? Unity uses Mutter, but is an unlikely party when it comes to implementing the feature in GNOME 3.

Nice. 2006. Glacial. No chance now:)

By the way, that's reported against Metacity, but [<this post>]("http://blogs.gnome.org/metacity/2009/07/06/the-future-of/") suggests that Metacity is at death's door now.

If it's ever going to be implemented, the likelihood is that it'll be via Mutter.

I sincerely hope Mutter supports a non-compositing mode if that's the case. On the version included by Lucid Lynx, "mutter --help" has a switch for non-compositing (it doesn't seem to work though).

---

### Post by 23meg on 2010-07-22
> **cyberkilla said:**
> Nice. 2006. Glacial. No chance now:)

By the way, that's reported against Metacity, but [<this post>]("http://blogs.gnome.org/metacity/2009/07/06/the-future-of/") suggests that Metacity is at death's door now.

If it's ever going to be implemented, the likelihood is that it'll be via Mutter.

It doesn't really matter, since the bugs that are relevant are to be migrated to Mutter, as the post you linked to indicates. It wouldn't hurt to file another bug in Mutter in the meantime, if that doesn't seem to be happening (#bugs on irc.gnome org would be a good place to ask around).

---

### Post by zekopeko on 2010-07-22
> **23meg said:**
> Is there a particular reason you reported the bug in Unity, rather than Metacity / Mutter upstream (where there is [an existing bug report]("https://bugzilla.gnome.org/show_bug.cgi?id=345249") anyway)? Unity uses Mutter, but is an unlikely party when it comes to implementing the feature in GNOME 3.

It's filed because I'm using Unity and that is the only platform where Mutter is used in Ubuntu.

---

### Post by Universal344 on 2010-07-23
Maybe I am mistaken, but isn't RGBA for transparency and cleaning up widget borders, whereas anti-aliasing is for smoothing the edges of rounded objects?

---

### Post by cyberkilla on 2010-07-23
> **Universal344 said:**
> Maybe I am mistaken, but isn't RGBA for transparency and cleaning up widget borders, whereas anti-aliasing is for smoothing the edges of rounded objects?

I am referring to window decorators. GNOME's window decorator is lacking the ability to draw anti-aliased, rounded window borders.

KDE, Windows 7, and OS X, etc., have been able to do this for a while. OS X has had it for ages; Windows, since late 2006.

---

### Post by 23meg on 2010-07-23
> **Universal344 said:**
> Maybe I am mistaken, but isn't RGBA for transparency and cleaning up widget borders, whereas anti-aliasing is for smoothing the edges of rounded objects?

[http://live.gnome.org/GTK+/ClientSideDecorations](http://live.gnome.org/GTK+/ClientSideDecorations) has some basic information.

---

### Post by 23meg on 2010-07-23
> **zekopeko said:**
> It's filed because I'm using Unity and that is the only platform where Mutter is used in Ubuntu.

It's usually a better idea to file enhancement requests directly upstream, especially if you're in the know regarding upstream bug trackers, policies and the like.

---

### Post by zekopeko on 2010-07-23
> **23meg said:**
> It's usually a better idea to file enhancement requests directly upstream, especially if you're in the know regarding upstream bug trackers, policies and the like.

Attribute me not doing so to my Bugzilla aversion and my love for Launchpad.

---

