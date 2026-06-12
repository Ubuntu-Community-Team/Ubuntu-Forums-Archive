---
title: "making non-antialiased fonts looks nice."
date: 2006-03-04
forum: Multimedia &amp; Video
---

### Post by vrode on 2006-03-04
[Apologies to those of you who receive this note in multiple forums]

Hi,

Looking for anyone who can help me with the ugly fonts output. I've
spent 80 hours on this issue and I'm still struggling to make my
Thinkpad T43 w/ ubuntu 5.10 come close to microsoft fonts output or
better yet similar to Apple/OSX render fonts.

I want to know how can they be improved and what did you do to fix it.

The fonts always seem slightly blurry and jagged and feel like I'm
straining my eyes in order to get a clear image.

Turning off anti-aliasing can get really crappy.

I've been through several forums trying to get the fonts look just like
as in windows for my ubuntu 5.10 installation w/ no avail.

I'd appreciate any insight and replies to this thread.


Following are the steps I took to make my linux workstation come close
to msfonts. See below for more information.


Step 1.

Installed and configured the most current
ati-driver-installer-8.22.5-i386.run for my ATI x300 which comes w/
thinkpad T43.

#fglrxinfo

reports correct info:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 2.0.5642 (8.22.5)


Step 2:

Made sure my /etc/X11/xorg.conf was set correct for what my LCD
(1400x1050) offers include correct DPI. Windows uses a default setting
of 96 dpi and linux defaults to 75 or 81 dpi.

The results are as follows:

HorizSync   30.0-97.0
VertRefresh 50.0-160.0
Option	    "DMPS"
DisplaySize 370.0 277.8

#xdpyinfo |grep resolution
resolution:	96x96 dots per inch


Step 3:

Copying true type fonts from windows to my linux w/s

# cd /usr/share/fonts/truetype
# mkdir windowsfonts
# cp /media/hda1/windows/Fonts/*.ttf .
# chown root.root *.ttf
# chmod 644 *.ttf
# mkfontdir

edited fonts.cache-1 w/

"windowsfonts" 0 ".dir"

Lastly ran the command fc-cache.

So that now I can have access to windows fonts in all X applications
including firefox and OpenOffice.org.


Step 4:

Getting freetype

FreeType is really a great system, and it's capable of rendering
True-Type fonts just as well as Windows or Macs. It is held back by
several patents by Apple. Fortunately, we can get around that quite easily.

Download the latest the latest version which is 2.1.10 as of this writing.

Recompiled freetype2 to enable the bytecode interpreter.

# ./configure --prefix=/usr
# make
# make install (as root)
# ldconfig (as root)

After taking the above steps I went into my Gnome font preferences and
set the Font Rendering to 'monochrome', Smoothing to 'none and Hinting
to to 'full'.

I even tried changing my ~/fonts.conf settings and my fonts appears to
faint (not dark) and getting jaggedness to them.

Looking for any sort of feedback or maybe share config files if yours
worked for your thinkpad t43.


tia,


regards,
/virendra

---

### Post by varunus on 2006-03-04
I frankly like the way linux renders fonts.  However, here's a howto I'm sure you'll be interested; you can adjust your X dpi and gnome font settings to look almost like windows.

[http://ubuntuforums.org/showthread.php?t=20976&highlight=fonts](http://ubuntuforums.org/showthread.php?t=20976&highlight=fonts)

---

### Post by vrode on 2006-03-04
I will give this a shot.

thanks for the pointer.


regards,
/virendra

---

### Post by vrode on 2006-03-05
I followed the link you provided and the fonts are still coming out to be real thin (monochrome), nothing close to microsoft fonts which I copied over to my ubuntu box as mentioned (step 3) in my original thread.

Is there anything else I can try to get fonts similar to that of ms?


Please advice.

regards,
/virendra

---

### Post by varunus on 2006-03-11
Hmm...if that howto doesn't give you good fonts, then I'm not sure what will...Try using bitstream vera sans as your system font, or maybe try installing the new windows vista fonts (calibri, etc).  I personally like the way linux antialiases my fonts.  Maybe your screen DPI is too low or high in the advanced tab of the fonts file?  Try finding out what your monitor base DPI is (use "xdpyinfo | grep resolution" in a terminal to get your res) and then set the GNOME DPI to that value.  This might make your fonts all look better.

---

