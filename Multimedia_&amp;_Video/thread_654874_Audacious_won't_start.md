---
title: "Audacious won't start"
date: 2007-12-31
forum: Multimedia &amp; Video
---

### Post by Nathan Otis on 2007-12-31
I hope this is the correct forum. Please move it if I'm in the wrong spot.

I've been trying to get Audacious running under Gutsy this morning with no luck. I'm not getting any error messages... It just won't start up. I've tried using the "A" icon, right clicking an mp3 and selecting "open with", and just now I tried terminal. Here is the output:

[COLOR="Blue"][FONT="System"]otis@otis-desktop:~$ audacious

(audacious:6269): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `filename != NULL' failed

** (audacious:6269): WARNING **: loading of (null) failed

(audacious:6269): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `filename != NULL' failed

** (audacious:6269): WARNING **: loading of (null) failed

(audacious:6269): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `filename != NULL' failed

** (audacious:6269): WARNING **: loading of (null) failed

(audacious:6269): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `filename != NULL' failed

** (audacious:6269): WARNING **: loading of (null) failed

(audacious:6269): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `filename != NULL' failed

** (audacious:6269): WARNING **: loading of (null) failed

(audacious:6269): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `filename != NULL' failed

** (audacious:6269): WARNING **: loading of (null) failed

(audacious:6269): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `filename != NULL' failed

** (audacious:6269): WARNING **: loading of (null) failed

(audacious:6269): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `filename != NULL' failed

** (audacious:6269): WARNING **: loading of (null) failed

(audacious:6269): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `filename != NULL' failed

** (audacious:6269): WARNING **: loading of (null) failed

(audacious:6269): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `filename != NULL' failed

** (audacious:6269): WARNING **: loading of (null) failed

(audacious:6269): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `filename != NULL' failed

** (audacious:6269): WARNING **: loading of (null) failed

(audacious:6269): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `filename != NULL' failed

** (audacious:6269): WARNING **: loading of (null) failed

(audacious:6269): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `filename != NULL' failed

** (audacious:6269): WARNING **: loading of (null) failed

(audacious:6269): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `filename != NULL' failed

** (audacious:6269): WARNING **: loading of (null) failed[/FONT][/COLOR]

Something is obviously wrong. Any help would be appreciated.
Thank you.

---

### Post by logos34 on 2007-12-31
I'd check if you have these packages installed:

gtk2-engines-pixbuf
librsvg2-common


Try reinstalling audacious.  Or completely remove audacious and reinstall.

---

### Post by Nathan Otis on 2007-12-31
Both packages are installed. I should have mentioned that I have uninstalled and reinstalled (with restarts, even) twice today via Synaptic.

---

### Post by disturbed1 on 2007-12-31
Try these -

Change to the default Ubuntu theme.
Delete the skins in the audacious skins folder ($HOME/.local/share/audacious/Skins) Open nautilus press ctrl-h to see hidden files/folders.

---

### Post by Nathan Otis on 2008-01-01
> **disturbed1 said:**
> Delete the skins in the audacious skins folder ($HOME/.local/share/audacious/Skins) Open nautilus press ctrl-h to see hidden files/folders.

We have a winner!! Is this something you knew from experience, or was there a clue given somewhere in that text?

Thanks!
n.

---

### Post by logos34 on 2008-01-01
so it was a skins issue...hmm.  

funny though, I have a plugins and Skins folders in ~/.local/share/audacious but it's empty...Why?  Because it installs everything to /usr/share/audacious

---

### Post by disturbed1 on 2008-01-01
> **Nathan Otis said:**
> We have a winner!! Is this something you knew from experience, or was there a clue given somewhere in that text?

Thanks!
n.

It happened to me :)

I went to winamp.com and downloaded a slew of skins and put them all in there, then attempted to start audacious, and had the exact same problem as you. Figured it was the skins, because that was the last thing I did.

Try to stick with the version 2.x or classic skins. MOST of those seem to work. Also, on the preferences page where you chose which skin audacious uses, there's a refresh button. That way you can drop a few skins in the folder and hit refresh to see if those skins will work or not. It's better than dropping 30 skins in and trying to figure out which one is bad :D.

---

### Post by disturbed1 on 2008-01-01
> **logos34 said:**
> so it was a skins issue...hmm.  

funny though, I have a plugins and Skins folders in ~/.local/share/audacious but it's empty...Why?  Because it installs everything to /usr/share/audacious

Sorry, missed you post ;)

You can get winamp skins and put them in the above folder. Read the post above about types and problems. Haven't tested out the plugin folder. I'd imagine it would take xmms plugins though? There's a slew out there on the net. Things like dsp's, APE decoders and so on. I just haven't had the need to try out any plugins that didn't come bundled. 

And a screen shot of my favorite audacious skin :D

---

### Post by logos34 on 2008-01-01
> **disturbed1 said:**
> Sorry, missed you post ;)

You can get winamp skins and put them in the above folder. Read the post above about types and problems. Haven't tested out the plugin folder. I'd imagine it would take xmms plugins though? There's a slew out there on the net. Things like dsp's, APE decoders and so on. I just haven't had the need to try out any plugins that didn't come bundled. 

And a screen shot of my favorite audacious skin :D

Haven't tried any xmms plugins, but now that you mention it a monkey's audio decoder could conceivably come in handy.  

My fav skins are the [almond series]("http://www.gnome-look.org/content/show.php/Almond+(VUmeter+skin+added)?content=41102") and the good 'ol xmms Ultrafina2000 (if only for the crisp, bright helvetica LED font)

---

