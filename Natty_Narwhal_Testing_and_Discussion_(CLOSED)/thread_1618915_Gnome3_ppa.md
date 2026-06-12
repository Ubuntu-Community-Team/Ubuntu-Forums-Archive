---
title: "Gnome3 ppa"
date: 2010-11-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2010-11-11
Bored? Natty feels too stable? Then Robert Ancell has some good news for you:

[QUOTE=Robert Ancell]In the Ubuntu Desktop team we're currently packaging GNOME 3 components for Ubuntu as per [the blueprint](https://launchpad.net/~ubuntu-desktop/+archive/gnome3-builds) decided at the last Ubuntu Developer Summit.

If you're already brave enough to be running Natty, then you can additionally try some new GNOME 3 applications by adding the [GNOME3 builds PPA](https://launchpad.net/~ubuntu-desktop/+archive/gnome3-builds) into your sources.  Expect the usual - the packages may not work perfectly, and it's non-trivial to downgrade, so be warned!

We're going to evaluate these packages in the PPA and decide how many are appropriate to include in Natty.[/QUOTE]

Call me a wuss, but I'll try this one in a VM first. :P

---

### Post by MacUntu on 2010-11-11
I wouldn't do it if you need the machine:

[[img]http://img.xrmb2.net/612424.jpg[/img]](http://img.xrmb2.net/images/612424.png)

:D

No window border, no window list in the panel, gcalctool looks oldschool'd.

---

### Post by dino99 on 2010-11-11
installed here on a maverick -> natty upgrade, work and look good

---

### Post by Arla on 2010-11-11
Thanks for the link, this is kind of what I wanted to play with, we'll see how it goes.

---

### Post by ranch hand on 2010-11-11
I have had this ppa for some time now.  Worked OK the last time I was over there.

Update/upgrading happening now.

I need to reboot my Debian anyway so I will be over there today and see if anything has become FUN.

---

### Post by ranch hand on 2010-11-11
Everything is working great.  I did not upgrade the network or nautilus stuff that was held back as it was removing unimportant things like nautilus and network manager.

Had a vertical white stripe down the middle of the launch bar on top of the icons before.  Some upgrade seems to have fixed that.

I think I could use Unity if I had to.  Seems pretty cumbersome to use compared to the old panel set up.  This looks more modern and I guess that is more important than function but it is usable.

---

### Post by psusi on 2010-11-11
Oh boy, I can't wait!

LVM snapshots for teh winz!  Unstable new update borks your system?  Revert!

---

### Post by seeker5528 on 2010-11-11
I upgraded the stuff. Upgrading Nautilus wasn't a problem for me, it cause a couple of nautilus extensions to be removed, but not stuff I care about.

Unfortunately I was getting a white background instead of seeing my wallpaper, but I would see the wallpaper when logging out.

Ended up downgrading the nautilus extensions package, temporarily disabling the Gnome3 PPA, then purging and reinstalling nautils and nautilus-data to get back to the gnome2.x version again and the wallpaper stuff works normally again.

Have not had any other issues with the stuff from the gnome3 PPA.

Later, Seeker

---

### Post by Arla on 2010-11-11
So just upgraded all tonight, and right now gnome-panel is giving me a bit of an issue (can't kill it, can't find it) but other than that it all is working, looks fairly, 1970's, but other than that is working.

I like the new sounds (if I click on the left, I get a sound from the left speaker, click on the right, sound from the right speaker) not that I'd keep it, but it's kinda cool.

Just figured out my panel thing, for some reason autohide was making it so that I had to move the mouse to the top left corner (for a panel hidden at the top of the screen) so for now I've un-hidden it just to be on a slightly safer side.

---

### Post by Starks on 2010-11-12
Are you guys using maverick or natty sources from the ppa?

---

### Post by BwackNinja on 2010-11-12
For theme problems, in your theme just make a symlink from gtk-2.0 to gtk-3.0 and install gtk3-engines-murrine and gtk3-engines-pixbuf. (Other engines won't work yet of course)

---

### Post by MacUntu on 2010-11-12
The settings daemon won't start for me:

```
test@vbox:~$ gnome-settings-daemon

GLib-GIO-ERROR **: Settings schema 'org.gnome.settings-daemon.plugins' is not installed

aborting...
Trace/breakpoint trap
```

---

### Post by Arla on 2010-11-12
> **Starks said:**
> Are you guys using maverick or natty sources from the ppa?

Natty I'd assume, I just added it using the normal 
```

sudo add-apt-repository ppa:whatever

```

---

### Post by seeker5528 on 2010-11-12
Hmm, must be moving things around in the control panel, lost the appearance applet, but now there is a background applet that I don't remember having before. Still only see white in the background with the newer nautilus installed.

> **Starks said:**
> Are you guys using maverick or natty sources from the ppa?

Use Natty, if you follow the link to the PPA in the first post, then select natty in the dropdown box, then hit the filter button you see the difference in what packages are available. It even tells you how recently the packages were updated.

EDIT: Figured out the wallpaper thing, had to rename my '~/.config/gnome-session/' directory, must have been something bad left in there from upgrading/downgrading.

Looks like desktopnova is going to have to be updated to use gsettings so it can change the wallpaper at login.

EDIT2: If I use Mutter as my window manager, which has been my normal preference, I still get white in the background instead of seeing my wallpaper.

Later, Seeker

---

### Post by psusi on 2010-11-13
I'm confused.  The PPA does not appear to contain a gnome-shell package.  I tried installing gnome-desktop3 but it had unmet deps.

---

### Post by seeker5528 on 2010-11-13
> **psusi said:**
> The PPA does not appear to contain a gnome-shell package.

If gnome-shell is what you are wanting, I wouldn't expect it out of this PPA.

This effort looks to be more about just getting the base Gnome 3 stuff tested and deciding what things are ready for inclusion.

Gnome-shell is still pretty volatile and prone to breakage.

If you are a risk taker you could add the ricotz staging PPA to get Gnome-shell. 

[https://launchpad.net/~ricotz/+archive/staging](https://launchpad.net/~ricotz/+archive/staging)

But between the current volatile nature of Gnome-shell development and the effort to get Gnome3 stuff in to Ubuntu proper there are bound to be conflicts along the way. And if you have the Gnome3 PPA on top of that the shifting of the sands is even greater.

There is a whole thread about Gnome-shell, the safest way to test it is to build from source.

Later, Seeker

---

### Post by Harry33 on 2010-11-16
Ricotz staging PPA does not contain all of the gnome-shell packages and as such it does not work. I think Rico uses that PPA as a staging arena for single packages. The correct PPA to install GTK+3 gnome-shell is this one:

[https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)

---

### Post by cariboo on 2010-11-16
The packages in [ricotz staging]("https://launchpad.net/~ricotz/+archive/staging") are newer than the packages in [ricotz testing]("https://launchpad.net/~ricotz/+archive/testing").

I've been using gnome-shell from ricotz staging for the past several weeks, it seems to work quite well here.

---

### Post by Harry33 on 2010-11-17
> **cariboo907 said:**
> The packages in [ricotz staging]("https://launchpad.net/~ricotz/+archive/staging") are newer than the packages in [ricotz testing]("https://launchpad.net/~ricotz/+archive/testing")..

Yes PPA Staging is newer, meaning it contains packages not yet tested enough.
But, you cannot use only the staging PPA, because it does not contain all the packages (for example there are no gnome-shell nor gsettings-desktop-schemas packages).
You have to use testing PPA and if you wish, then **also** use staging PPA above it.

---

### Post by seeker5528 on 2010-11-17
> **Harry33 said:**
> You have to use testing PPA and if you wish, then **also** use staging PPA above it.

That makes more sense to me to do it that way, but for a while there were no packages in testing and you had to pull from staging to get it.

The continuous availability of of Gnome-shell through either of these seems a little questionable. Continuous compatibility between the stuff from these ricotz PPAs and the Gnome3 PPA is questionable. Even if you don't pull from the Gnome3 PPA, with Gnome3 stuff slowly being added to the official repositories, it seems likely there will be periods of incompatibility. I expect issues will start to become less as we get farther into the development cycle, if for no other reason than the similarity in the schedules between the Gnome and Ubuntu development cycles.

Later, Seeker

---

### Post by Harry33 on 2010-11-17
> **seeker5528 said:**
>  Continuous compatibility between the stuff from these ricotz PPAs and the Gnome3 PPA is questionable. Even if you don't pull from the Gnome3 PPA, with Gnome3 stuff slowly being added to the official repositories, it seems likely there will be periods of incompatibility. I expect issues will start to become less as we get farther into the development cycle, if for no other reason than the similarity in the schedules between the Gnome and Ubuntu development cycles.
Later, Seeker

Yes I also believe this to be true.
Me, I dont use Gnome3 PPA at all, because I like to follow the recent development of the Gnome-Shell. This is why ricotz PPA is valuable for me.
If breakages happen, I use Gnome2 (panel) instead till problems are solved.

---

### Post by kaitwospirit on 2010-11-19
I'm getting a segfault every time I try to navigate to another folder in nautilus. I'm guessing it has something to do with something in this ppa but I really don't even know. Nautilus itself doesn't seem to be the problem. Downgrading the package to vanilla just made it crash before I could even launch it. So... yeah I dunno.

Last few errors:
```
(nautilus:3774): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:3774): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

(nautilus:3774): GLib-GObject-WARNING **: specified class size for type `LocationWidget' is smaller than the parent type's `GtkHBox' class size

(nautilus:3774): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(nautilus:3774): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed
Segmentation fault
```

Anyone have any ideas?

---

### Post by dino99 on 2010-11-19
i have these errors (warnings) for a while now and i think they are not related t o the ppa. On my end, updating gcc have broken gnome-media (capplets) but i dont care anyway

---

