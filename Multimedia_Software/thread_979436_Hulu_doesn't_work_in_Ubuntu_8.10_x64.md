---
title: "Hulu doesn't work in Ubuntu 8.10 x64"
date: 2008-11-11
forum: Multimedia Software
---

### Post by Kevin Fischer on 2008-11-11
At some point in the last week or so an update caused Hulu to stop working for me on my Ubuntu 8.10 x64 machine. Everything displays as usual, but the video never plays. The screen just stays black.

I single out Hulu in particular because it was working without a hitch previously.

Anybody else experience this? Any ideas?

---

### Post by IceBadger on 2008-11-12
Do other sites with flash work, or is it just Hulu?  Try visiting [www.youtube.com](www.youtube.com) or something and see if flash works there.

I know flash support for x64 systems has been flimsy in the past.  If it is flash in general there is a workaround using some 32bit components.

---

### Post by Kevin Fischer on 2008-11-12
Yeah, youtube works fine, as do other flash sites as far as I can tell.

---

### Post by zoomy942 on 2008-11-12
isnt Hulu.com a java site?

---

### Post by Kevin Fischer on 2008-11-12
Correct me if I'm wrong, but I'm pretty sure it's flash because when you right click on the screen the flash settings context menu comes up.

---

### Post by ds3 on 2008-11-14
I have also suddenly started having this problem on an AMD x64 system. It now just sits and claims to be loading. NBC's videos have been like this for a while, but it's new on Hulu. Is this just a 64bit problem with the nsplugin wrapper or are people seeing it on 32 bit systems as well? I'm still using Flash 9.0 r115 so from what I can tell the high resolution videos shouldn't work, but the normal resolution ones should still be okay.
Thanks.

---

### Post by Chubtoad on 2008-11-14
If you launch firefox from a terminal and go to hulu, you might see an error message in the terminal, which you can post here.

I installed **flashplugin-nonfree** after the upgrade and it started working for me again.

---

### Post by ds3 on 2008-11-15
Chubtoad, what do you mean "after the upgrade"? Also, are you using a 64 or 32 bit system?
The terminal doesn't give any errors while it's stalled. When I change pages it gives a series of Gtk warnings, but those appear to happen when I leave any Flash page, even ones that are working, although Hulu gives more of them which might just mean it has more Flash items:

leaving a stalled (unwilling to load) Hulu Flash page:

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7098): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed


leaving a working Flash page:

(npviewer.bin:7236): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:7236): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7236): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7236): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7236): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7236): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

---

### Post by adamovera on 2008-11-29
Go to Tools/Add-Ons/plugins in Firefox. Disable any older or multiple instances of Flash. I had 2x 9.0 & 1x 10.0 plugins for flash, I've disabled all but the 10.0 & the problem went away.

---

### Post by markbuntu on 2008-11-29
I just installed Intrepid amd64 today, updated and got the ubuntu-restricted-extras, hulu works just fine for me.

---

### Post by cpraets on 2008-12-02
I seem to be having the same issue as Kevin.  Where I have a amd64 system and Hulu was working and now it has stopped, Has anyone made progress on this?

---

### Post by Usufruct on 2008-12-02
I'm using Intrepid x64 and the 10.0 d20 64-Bit alpha release of Adobe Flash Player, and Hulu works fantastically for me.

---

### Post by philetus on 2008-12-02
I'm using 64 and flash 64 bit works great on Hulu.
Did you load the w64 codecs?

---

### Post by armagad on 2008-12-11
I am experiencing this same problem. Oddly enough I installed Opera and had no problem watching Hulu.

-Matt

---

### Post by armagad on 2008-12-11
Err... It's working now in Firefox. I don't know why it takes 3-4 minutes for it to come up in Firefox though.

---

### Post by QCompson on 2008-12-12
> **armagad said:**
> Err... It's working now in Firefox. I don't know why it takes 3-4 minutes for it to come up in Firefox though.

I have the same issue.  It eventually plays fine, but takes a couple minutes to start (before that it is just black).  On intrepid x64, flash 10rc2.

---

### Post by element on 2008-12-17
> **QCompson said:**
> I have the same issue.  It eventually plays fine, but takes a couple minutes to start (before that it is just black).  On intrepid x64, flash 10rc2.

Me too, this is frustrating.

---

### Post by LowSky on 2008-12-17
Mine works fine had to remove flash-nonfree and install the plugin by hand

/home/john/.mozilla/plugins ( you might have to create plugins folder

then add libflashplayer.so

[Click to download file]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz")

just unpack it and add to file

---

### Post by cybrsaylr on 2008-12-18
Hulu works for me on 32 bit 8.10 but takes longer to load than it did with 8.04.

---

### Post by QCompson on 2008-12-18
> **LowSky said:**
> Mine works fine had to remove flash-nonfree and install the plugin by hand

/home/john/.mozilla/plugins ( you might have to create plugins folder

then add libflashplayer.so

[Click to download file]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz")

just unpack it and add to file
Solved my problems, thanks.  Hulu videos now start immediately (or rather, the intro commercial starts immediately :p  )

---

### Post by newswitch on 2009-01-31
> **QCompson said:**
> Solved my problems, thanks.  Hulu videos now start immediately (or rather, the intro commercial starts immediately :p  )
This worked great!

I'm running 64 bit Intrepid.

Why does the hand install change anything?

---

### Post by SyberKowboy on 2009-02-09
I thought it wasn't working but I left the tab open and after about 30 secs it loaded and i was good to go. My guess is that something is preventing the advertising from loading and it still has the delay even though it doesn't play. Personally now that I have figured it out I'm much happier without the advertising.

---

### Post by jmorth on 2009-02-11
I got it to work just by creating an account at hulu.

---

### Post by Braytok on 2009-02-16
> **jmorth said:**
> I got it to work just by creating an account at hulu.

how odd, that did it for me as well. Must be something with the adds for non members... -meh stupid.

---

### Post by jharris0221 on 2009-02-21
> **Braytok said:**
> how odd, that did it for me as well. Must be something with the adds for non members... -meh stupid.


Confirmed, logging in works for me as well on x64 8.10

---

### Post by markbuntu on 2009-02-21
I think it looks for cookies and hangs when it can't find them.

---

### Post by Kevin Fischer on 2009-05-15
Seems to work fine in Jaunty out of the box, member or not.

---

### Post by dannymichel on 2010-05-12
> **QCompson said:**
> Solved my problems, thanks.  Hulu videos now start immediately (or rather, the intro commercial starts immediately :p  )where do i get this magical file now?

---

