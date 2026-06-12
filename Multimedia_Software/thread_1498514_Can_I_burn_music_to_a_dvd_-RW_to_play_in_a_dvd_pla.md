---
title: "Can I burn music to a dvd -RW to play in a dvd player and what program to use"
date: 2010-05-31
forum: Multimedia Software
---

### Post by rhawnied on 2010-05-31
Hi,

  So my wondering is if I can burn music on a dvd+rw (it is a +rw) and play it in either a dvd player or a stereo, in what format would be best and what program to use.  I am not sure what forum to post this in so I started here.

Thanks;)

---

### Post by rhawnied on 2010-06-01
:(

---

### Post by drreed on 2010-06-01
I guess you are using the Gnome desktop environment? If so then you should try Brasero Disk Burner on your <Applications,> <Sound & Video> menu.

If it's not there you can install it. Open a terminal and type:

```

sudo apt-get install brasero

```When it completes, it should be available on that menu.

If you are using the KDE environment, I'd suggest K3b.
Which you would install similarly to the above example, replacing brasero with k3b. To make sure I gave you the right commands, you can check to see what these packages are really called by entering:

```

sudo apt-cache search "application name or part there of"

```don't include the quotation marks. It will return every application you can install with the word brasero in it's description or name.
Typically, you'll want to choose the "metafiles" package that includes all the normal supporting applications and libraries that are required. In your screen listing, you'll see things (libraries, toolkits, etc) that have "brasero" in their description, but aren't the program you want to install. usually that won't necessarily be the If you study the listing carefully, you can usually figure out which one is the main program.

Of course, you can always go to your menu and choose Ubuntu Software center, Sound & Video, and choose from a list of available applications.

---

### Post by rhawnied on 2010-06-01
Thanks for your help!  Seems easy now but I had a hard time finding information on this.:???:

Btw I love that show too! and he is my favorite! ;)

---

