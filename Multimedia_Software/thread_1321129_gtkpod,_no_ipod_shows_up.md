---
title: "gtkpod, no ipod shows up"
date: 2009-11-09
forum: Multimedia Software
---

### Post by djm227 on 2009-11-09
I'm really at a loss here....I did a bunch of searches but couldn't find ANYTHING about this, yet it has happened on both my and my brothers computer.

I just installed gtkpod, and started it (ipod is plugged in and mounted).  However, no ipod is listed and when I click Load Ipod(s), absolutely NOTHING happens.  I'm really not sure what to do...my ipod works fine with Rhythmbox, but in gtk it's nowhere to be found.

Any help would be appreciated.

---

### Post by greyfox1 on 2009-11-09
Hmm... whenever I'm trying to figure out why a program isn't doing what it should be, I run it from the terminal to see if it throws any error messages. Try opening a Terminal window, running the command gtkpod, and see what it does when you try to load your iPod. Chances are it will probably throw some errors. If it does, post those errors here.

---

### Post by djm227 on 2009-11-09
Good idea.  The following is what it spat out when I ran the program, but nothing at all new comes up when I click "load Ipod(s)".  What does come out doesn't look right to me though...but I'm still pretty new to Ubuntu so I don't know much.




(gtkpod:3441): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkImageMenuItem

(gtkpod:3441): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gtkpod:3441): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gtkpod:3441): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gtkpod:3441): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gtkpod:3441): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gtkpod:3441): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gtkpod:3441): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gtkpod:3441): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gtkpod:3441): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gtkpod:3441): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gtkpod:3441): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gtkpod:3441): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

---

### Post by greyfox1 on 2009-11-09
Darn, I was hoping this would turn something up. The messages you are getting are unrelated to the problem. I have only used GTKPod once or twice (and that was quite a while ago) so I'm not sure what to try next. [This thread]("https://answers.launchpad.net/ubuntu/+source/gtkpod/+question/65825") might help, though. There are suggestions there you could try.

---

### Post by nishant.singh28 on 2009-11-10
just select add repo/ipod from edit menu and set ur ipod's mount point and type

---

### Post by delcypher on 2009-11-11
Found thsi bug report with temporary fix, fixed the problem for me

[http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg353875.html]("http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg353875.html")

Although I didn't try nishant.sigh28's solution. I'd try his first

---

### Post by bke76 on 2009-11-15
I did have the same problem and nishant.singh28 solution worked fine for me:

* Edit -> Repository/iPod options

* add new repository/iPod

* at the iPod mountpoint browse to your iPod

* save settings and hit 'load ipod'

---

### Post by jeffltw on 2009-12-05
> **bke76 said:**
> I did have the same problem and nishant.singh28 solution worked fine for me:

* Edit -> Repository/iPod options

* add new repository/iPod

* at the iPod mountpoint browse to your iPod

* save settings and hit 'load ipod'

Thanks this fixed it. Ipod was mounted under a different name (no idea why) in /media.

---

