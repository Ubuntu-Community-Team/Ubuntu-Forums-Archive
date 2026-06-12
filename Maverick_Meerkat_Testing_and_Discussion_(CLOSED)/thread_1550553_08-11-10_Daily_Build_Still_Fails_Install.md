---
title: "08-11-10 Daily Build Still Fails Install"
date: 2010-08-11
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by krash1220 on 2010-08-11
Ubiquity 2.3.4
** Message: pygobject_register_sinkfunc is deprecated (GtkWindow)
** Message: pygobject_register_sinkfunc is deprecated (GtkInvisible)
** Message: pygobject_register_sinkfunc is deprecated (GtkObject)
exception: <urlopen error [Errno 101] Network is unreachable>
Fontconfig warning: Directory/file mtime in the future. New fonts may not be detected
exception: <urlopen error [Errno 101] Network is unreachable>
** Message: pygobject_register_sinkfunc is deprecated (GtkWindow)
** Message: pygobject_register_sinkfunc is deprecated (GtkInvisible)
** Message: pygobject_register_sinkfunc is deprecated (GtkObject)
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <> line 181.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <> line 181.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <> line 181.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <> line 191.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <> line 191.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <> line 191.

---

### Post by Nesaskewatch on 2010-08-11
At least the outputs are changing.  Fubar.  Borked.  "It's dead Jim."

---

### Post by jppr on 2010-08-11
I did this morning fresh daily alternate installations both Ubuntu and Kubuntu, and haven´t   any problems.

---

### Post by krash1220 on 2010-08-11
Well, maybe I should try alternate install. I like the gui install but at this point I would just like to be able to get Maverick installed.

---

### Post by rtalcott on 2010-08-11
Same issue/errors here too....
rt

---

### Post by cariboo on 2010-08-11
I tried the daily live today. and got a desktop, but no panels or icons. The alternate iso installed with zero problems.

---

### Post by rtalcott on 2010-08-11
I get a desktop too but when I try to install it fails at random point during the install...I'll try again tomorrow.

rt

---

### Post by VMC on 2010-08-12
> **cariboo907 said:**
> I tried the daily live today. and got a desktop, but no panels or icons. The alternate iso installed with zero problems.
What you can try is Ctrl+Alt+T for Terminal. A terminal will pop up, then type ```
sudo ubiquity
```.
I would be interested to know if it completes using this method.

 I get the ubiquity dialog an progression but it never fully installs.

---

### Post by ronacc on 2010-08-12
for me I didn't even get a response from "sudo ubiquity "  not even a cmd not found .

---

### Post by rtalcott on 2010-08-12
LiveCD from 8-12 boots fine (I removed the "ui")...click on Install and it hangs on ALLOCATE DRIVE SPACE...

maybe tomorrow.

rt

---

### Post by kansasnoob on 2010-08-12
I noticed just a few issues were addressed in ubiquity (2.3.5), but not nearly enough:

> ubiquity (2.3.5) maverick; urgency=low

  [ Mario Limonciello ]
  * Drop the (now) unused install_window and references to it.
  * Don't start the ubiquity panel on xfwm4.  It doesn't appear to work properly
    for now even with the proper indicators installed.
  * Set the priority the prepare page higher to prevent timezone from being
    shown instead.
  * Fix misc.get_release to return the proper data for non-ubuntu disks.
  * Correct the text in the stepLanguage widgets to reflect ${RELEASE}
    rather than hardcoding to Ubuntu.
  * depends on python-vte for GTK frontend (LP: #616272)
  * depends on python-webkit for GTK frontend (LP: #616275)

  [ Jonathan Riddell ]
  * In ubi-wireless.py and ubi-prepare.py only load gtkwidgets.py when
    creating the GTKPage, else KDE frontend breaks

 -- Jonathan Riddell <jriddell@ubuntu.com>  Wed, 11 Aug 2010 18:02:35 +0100

For now I'd recommend either just using the alternate CD or sticking with the actual Alpha 3 Live CD.

---

### Post by rtalcott on 2010-08-12
Alpha 3 works?!?
GREAT!
I'll try that!
Thank you!
rt

---

### Post by ronacc on 2010-08-12
with todays daily 8/12 I got as far as "who are you ? " and ubiquity froze  .

---

### Post by VMC on 2010-08-12
> **ronacc said:**
> with todays daily 8/12 I got as far as "who are you ? " and ubiquity froze  .
Same here but I closed Ubiquity dialog box and restarted. After three tries I finally got it installed.

What's weird is the ubiquity Install dialog is getting smaller instead of larger, which it should. We have to contend with both horizontal & vertical scrolls. No way to max the dialog box.

---

### Post by ronacc on 2010-08-12
yeah I noticed that too . I figgured it was because I started ubiquity from term with a crippled GDM .

---

