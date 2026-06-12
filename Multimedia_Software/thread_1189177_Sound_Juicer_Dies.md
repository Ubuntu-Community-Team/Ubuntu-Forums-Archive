---
title: "Sound Juicer Dies"
date: 2009-06-16
forum: Multimedia Software
---

### Post by PerfectReign on 2009-06-16
I'm fairly new to Ubuntu. I'd been using openSUSE/KDE for several years and have switched.

I wanted to rip a CD into MP3 tracks for my car stereo. (It plays MP3 files but not OGG.)

Upon inserting the CD, I was asked what to do. I chose audio extractor and filled out the information. When I clicked on "Extract" the application died.

I launched from the command line (ugh!) and got the following. The segmentation fault is where the app dies.

[FONT=Fixedsys]

[COLOR=Blue]kai@r2d2:~$ sound-juicer
MusicBrainz: Connecting to [http://musicbrainz.org:80](http://musicbrainz.org:80)
MusicBrainz: GET /ws/1/release/?type=xml&discid=C9Lg8KUqI4l.sh_fdjmwmsMNNcM-
MusicBrainz: Result: 0 (302 Found)
MusicBrainz: Status: 302
MusicBrainz: Response:

This CD could not be queried: Internal error: 54

(sound-juicer:5612): Gtk-CRITICAL **: gtk_entry_set_text: assertion `text != NULL' failed

(sound-juicer:5612): Gtk-CRITICAL **: gtk_entry_set_text: assertion `text != NULL' failed

** (sound-juicer:5612): CRITICAL **: musicbrainz_submit_message_area_new: assertion `title != NULL' failed

(sound-juicer:5612): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(sound-juicer:5612): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (sound-juicer:5612): CRITICAL **: gedit_message_area_set_default_response: assertion `GEDIT_IS_MESSAGE_AREA (message_area)' failed

(sound-juicer:5612): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
Segmentation fault[/COLOR]
[/FONT]

---

### Post by MeKino on 2009-06-17
I don't know what the problem is, but for me the error I get is:

kino@kino-desktop:~$ sound-juicer
MusicBrainz: Connecting to [http://musicbrainz.org:80](http://musicbrainz.org:80)
MusicBrainz: GET /ws/1/release/?type=xml&discid=9MshVFc48USbdMmHzCQpL3wgH6g-
MusicBrainz: Result: 0 (200 OK)
MusicBrainz: Status: 200
MusicBrainz: Response:
<?xml version="1.0" encoding="UTF-8"?><metadata xmlns="http://musicbrainz.org/ns/mmd-1.0#" xmlns:ext="http://musicbrainz.org/ns/ext-1.0#"><release-list></release-list></metadata>

(sound-juicer:18313): Gtk-CRITICAL **: gtk_entry_set_text: assertion `text != NULL' failed

(sound-juicer:18313): Gtk-CRITICAL **: gtk_entry_set_text: assertion `text != NULL' failed

** (sound-juicer:18313): CRITICAL **: musicbrainz_submit_message_area_new: assertion `title != NULL' failed

(sound-juicer:18313): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(sound-juicer:18313): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (sound-juicer:18313): CRITICAL **: gedit_message_area_set_default_response: assertion `GEDIT_IS_MESSAGE_AREA (message_area)' failed

(sound-juicer:18313): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
Segmentation fault

---

### Post by gordintoronto on 2009-06-21
I get that result with a CD which is "hot off the press," so it's not in the database yet.

The CD is also not in the database used by Windows Media Player, although disc 2 might be now...

It's a 5-CD set: Oscar Peterson, The Songbooks.  Fabulous!

Goobox rips the CD just fine, without putting any ID info in the songs.


> **MeKino said:**
> I don't know what the problem is, but for me the error I get is:

kino@kino-desktop:~$ sound-juicer
MusicBrainz: Connecting to [http://musicbrainz.org:80](http://musicbrainz.org:80)
MusicBrainz: GET /ws/1/release/?type=xml&discid=9MshVFc48USbdMmHzCQpL3wgH6g-
MusicBrainz: Result: 0 (200 OK)
MusicBrainz: Status: 200
MusicBrainz: Response:
<?xml version="1.0" encoding="UTF-8"?><metadata xmlns="http://musicbrainz.org/ns/mmd-1.0#" xmlns:ext="http://musicbrainz.org/ns/ext-1.0#"><release-list></release-list></metadata>

(sound-juicer:18313): Gtk-CRITICAL **: gtk_entry_set_text: assertion `text != NULL' failed

(sound-juicer:18313): Gtk-CRITICAL **: gtk_entry_set_text: assertion `text != NULL' failed

** (sound-juicer:18313): CRITICAL **: musicbrainz_submit_message_area_new: assertion `title != NULL' failed

(sound-juicer:18313): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(sound-juicer:18313): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

** (sound-juicer:18313): CRITICAL **: gedit_message_area_set_default_response: assertion `GEDIT_IS_MESSAGE_AREA (message_area)' failed

(sound-juicer:18313): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
Segmentation fault

---

### Post by hemmi7 on 2010-12-25
I had the same Problem:
solved it by giving the Tracks a name.

If you try to juice a CD that is not known, then you have give the tracks a name. 

There are no default names as eg Track1 Track2 ...     but there is just no name!

and when sound-juicer then tries to make the filename out of   unexisting Variable + ".mp3"  then you have the mentioned Problem.

Gr Hemmi7

---

### Post by greytinhouse on 2010-12-30
Hi Hemmi7

I love sound juicer and have had no problems at all when tracks have no name when using sound juicer version 2.2 with ubuntu 8.04 (hardy heron), but when I got a new computer and installed ubuntu 10.04 (lucid lynx) and all the latest software ie sound juicer 2.28, my sound juicer also just dies. I have kept my old computer set up just so that I can keep ripping audio books with sound juicer. I think that sound juicer is way nicer and quicker than any of the other ripping applications I have tried. I will try your solution as I am about to rip a new audio book. Thanks for the tip - I am new to forums and have never posted before! Will let you know how I get on.

---

