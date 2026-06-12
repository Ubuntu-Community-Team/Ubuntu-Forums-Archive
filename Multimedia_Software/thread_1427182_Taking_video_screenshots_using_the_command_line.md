---
title: "Taking video screenshots using the command line"
date: 2010-03-11
forum: Multimedia Software
---

### Post by hellocatfood on 2010-03-11
I want to take consecutive screenshots of a video using command line operations but I can't seem to find accurate documentation on different websites.

Does anyone know how to do this using vlc, totem or another program?



Note: I've used ffmpeg as well, but then reencodes and splits the video file. I just want to take consecutive screenshots

---

### Post by Barriehie on 2010-03-11
gnome-screenshot?  i.e. take 1 and then use history or write small bash script?

```

GNOME-SCREENSHOT(1)                                        GNOME-SCREENSHOT(1)



NAME
       gnome-screenshot  -  capture  screen  or window and save the image to a
       file.

SYNOPSIS
       gnome-screenshot [ -w ] [ -d SECONDS  ] [ -e EFFECT  ] [ -i ]


DESCRIPTION
       gnome-screenshot is a GNOME utility for taking screenshot of the entire
       screen or a window, with optional beutifying border effects.

       gnome-panel-screenshot  is  the same program.  It is provided for back-
       ward compatibility, and is considered deprecated.

OPTIONS
       -w, --window
              Grab the current active window instead of the entire screen.

       -d SECONDS, --delay=SECONDS
              Take screenshot after specified delay [in seconds].

       -e EFFECT, --border-effect=EFFECT
              Add effect to the outside of the screenshot border.  EFFECT  can
              be ``shadow'' (adding drop shadow), ``border'' (adding rectangu-
              lar space  around  the  screenshot)  or  ``none''  (no  effect).
              Default is ``none''.

       -i, --interactive
              Interactively set options in a dialog.

       -?, --help
              Show summary of options.

       In  addition, the usual GTK+ and GNOME command line options apply.  See
       the output of --help for details.

SEE ALSO
       gnome-options(7), gtk-options(7)

AUTHOR
       This  manual  page  was   written   by   Christian   Marillat   <maril-
       lat@debian.org>  for  the  Debian  GNU/Linux system (but may be used by
       others).

       Updated by Theppitak Karoonboonyanan <thep@linux.thai.net>.



                                 23 mars 2007              GNOME-SCREENSHOT(1)

```

---

### Post by LuridCinema on 2010-03-11
ffmpeg -i VIDEO.avi -r 30 -t 00:00:30 -f image2 images%05d.png              <<< 5 zeros in image name..... "-t" switch = do it for 30 seconds "-r"=30 frames per sec
ffmpeg -i VIDEO.avi -sameq -r 30 -ss 0:00:12 -t 00:00:02 -f image2 images%05d.png                << "-t"=do it for 2 secs "-ss" = start at 12 sec

that will give you .PNG files , Im sure you can do JPG as well

---

### Post by derrick81787 on 2010-03-11
If you find a way to take one screenshot, you can use the *watch* command to execute it every *n* seconds.

Just run **man watch** to get more information.  It's really simple to use.

- Derrick

---

### Post by andrew.46 on 2010-03-12
Hi hellocatfood,

You are after Tip 5 in this guide:

Top 10 Tricks and Tips for the svn MPlayer
[http://ubuntuforums.org/showthread.php?t=1154431](http://ubuntuforums.org/showthread.php?t=1154431)

Andrew

---

### Post by hellocatfood on 2010-03-20
> **andrew.46 said:**
> Hi hellocatfood,

You are after Tip 5 in this guide:

Top 10 Tricks and Tips for the svn MPlayer
[http://ubuntuforums.org/showthread.php?t=1154431](http://ubuntuforums.org/showthread.php?t=1154431)

Andrew

Thanks, that's exactly what I needed!

---

### Post by andrew.46 on 2010-03-20
Hi hellocatfood,

> **hellocatfood said:**
> Thanks, that's exactly what I needed!

Excellent news, I am pleased to see that this long forgotten guide has proved to be of some use :).

Andrew

---

### Post by hellocatfood on 2010-03-20
Actually, I spoke a little bit too soon...

It does indeed convert the movie to images (and I like how you can specify frames), but just like ffmpeg it reencodes it, or at least attempts to.

To put my situation into context:

I've got a slightly corrupted video file (I do something called [databending](http://www.hellocatfood.com/2009/11/16/databending-using-audacity/)) and when I try to import it into a video editor it attempts to rebuild it, so it ends up looking at bit more like [this](http://www.youtube.com/watch?v=DbJ19QzzIGM), when in fact it should end up looking more like [this](http://www.flickr.com/photos/hellocatfood/4442115921/).

Strangely, when I play it in totem, VLC or mplayer it *plays* as it should, and Pitivi can import it properly. Could it have something to do with using GStreamer over ffmpeg?

---

