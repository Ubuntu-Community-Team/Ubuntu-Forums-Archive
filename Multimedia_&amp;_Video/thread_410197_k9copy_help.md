---
title: "k9copy help"
date: 2007-04-15
forum: Multimedia &amp; Video
---

### Post by 42Wired on 2007-04-15
When backing up a DVD, k9copy will write the files on the DVD to the hard drive just fine. But after it asks me to put in a blank DVD, the burn speed will change from 0.0x to -15336541681.0x (or something similar), and just stay at 0% complete indefinitely.

I'm pretty sure that I have all of the correct repositories installed.

I'm using GNOME through Dapper.

Any help is appreciated.

---

### Post by 42Wired on 2007-04-15
Oh, and something else fun that happens: after I attempt to burn the backup copy, I have to reboot if I want to have the system detect anything else I put in the disk drive. Any ideas?

---

### Post by 42Wired on 2007-04-15
Also, when outputting to an .iso file, there is no .iso file; just the copy of the DVD's contents (as it would if it were just a straight up copy).

---

### Post by 42Wired on 2007-04-19
I still can't figure it out, and I can't seem to find any documentation on it. Any help is appreciated.

---

### Post by Foxmike on 2007-04-22
You may want to make a look at [this]("http://ubuntuforums.org/showthread.php?p=1098581&highlight=k9copy+source#post1098581")

Good luck!:)

---

### Post by 42Wired on 2007-04-22
Thanks for the link, but it lead me to a dead-end. I don't want to mess with wine quite yet.

I did get it to work by installing k3b, though. Now I have a new problem; when I open a dvd, then click on any checkbox at all, k9copy crashes. It only seems to be with this one DVD. It plays fine in MPlayer and in WinXP.

I don't know if this means anything, but here's what it gave me after it crashed. "k9copy crashed and caused the signal 11 (SIGSEGV)." The following is the backtrace data.

```
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1231607584 (LWP 5690)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0xb6590324 in k9CellCopyList::fill () from /usr/lib/libk9copy.so.0
#7  0xb6590588 in k9CellCopyList::k9CellCopyList ()
   from /usr/lib/libk9copy.so.0
#8  0xb659c671 in k9DVD::getfactor () from /usr/lib/libk9copy.so.0
#9  0x0807208d in QMemArray<char>::detach ()
#10 0xb728da5e in QCheckListItem::stateChange () from /usr/lib/libqt-mt.so.3
#11 0xb7297cfc in QCheckListItem::setState () from /usr/lib/libqt-mt.so.3
#12 0xb729839f in QCheckListItem::setState () from /usr/lib/libqt-mt.so.3
#13 0xb729868b in QCheckListItem::activate () from /usr/lib/libqt-mt.so.3
#14 0xb729bc68 in QListView::contentsMousePressEventEx ()
   from /usr/lib/libqt-mt.so.3
#15 0xb729c392 in QListView::contentsMousePressEvent ()
   from /usr/lib/libqt-mt.so.3
#16 0xb72cc549 in QScrollView::viewportMousePressEvent ()
   from /usr/lib/libqt-mt.so.3
#17 0xb72cf1ba in QScrollView::eventFilter () from /usr/lib/libqt-mt.so.3
#18 0xb7293885 in QListView::eventFilter () from /usr/lib/libqt-mt.so.3
#19 0xb719519a in QObject::activate_filters () from /usr/lib/libqt-mt.so.3
#20 0xb7195218 in QObject::event () from /usr/lib/libqt-mt.so.3
#21 0xb71d2742 in QWidget::event () from /usr/lib/libqt-mt.so.3
#22 0xb712df3e in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#23 0xb712e4c8 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#24 0xb78b2d7d in KApplication::notify () from /usr/lib/libkdecore.so.4
#25 0xb70bf1c5 in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
#26 0xb70ba873 in QETWidget::translateMouseEvent ()
   from /usr/lib/libqt-mt.so.3
#27 0xb70b8d59 in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#28 0xb70d24db in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#29 0xb7146a2f in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#30 0xb7146952 in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#31 0xb712ca4d in QApplication::exec () from /usr/lib/libqt-mt.so.3
#32 0x0806c403 in QValueListPrivate<QString>::QValueListPrivate ()
#33 0xb69afea2 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#34 0x08054dc1 in ?? ()

```

I'm using v1.0.2 in Dapper. I noticed that there is a new version (v1.1.1-3), but Synaptic won't pick it up, and manually installing it doesn't work with the instructions they gave.

---

### Post by 42Wired on 2007-04-23
Nearly the same thing happens in Feisty.

---

### Post by Manatherin on 2007-04-23
if your not that attatched to k9copy then u could try DVD95 instead

[http://dvd95.sourceforge.net/](http://dvd95.sourceforge.net/)

---

### Post by 42Wired on 2007-04-23
They really must not want anyone backing up this DVD. Here's a list of all the programs I've tried (all have failed):

AcidRip
Brasero
GnomeBaker
DVD95
k9copy
Thoggen
Graveman

This one won't even play in Ubuntu. I may have mentioned before that it did, but I didn't realize that I was in Windows at the time.

---

### Post by 42Wired on 2007-04-24
I think I have it working. It's creating an .iso now.

I had to install a codec for it to read the DVD (though it still won't play...).

---

