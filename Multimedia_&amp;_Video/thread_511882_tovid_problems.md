---
title: "tovid problems"
date: 2007-07-28
forum: Multimedia &amp; Video
---

### Post by valkarin on 2007-07-28
I am trying to burn some tv shows to a DVD using tovid.  I have successfully burned a movie with no menu and a movie with a three item menu.  However, I have four episodes that I would like to burn to this DVD.  I have an entry for each one on the menu.  Here is the makemenu command I used:
```
 makemenu -ntsc -dvd -background /secdrv/Pictures/various/avatar9 -audio /secdrv/Music/Soundtraks/Avatartheme.mp3 -length 60 -menu-title "Avatar Book One Water" -font Courier-Oblique -textcolor red "Episode 1 and 2" "Episode 3" "Episode 4" "Episode 5" -overwrite -out Avab1d1

```

Here is the output:
```
--------------------------------
makemenu
A script to generate DVD/(S)VCD menus
Part of the tovid suite, version 0.30
http://www.tovid.org
--------------------------------
Adding 4 titles to the menu:
    1: Episode 1 and 2
convert: invalid argument for option `PNG': -size.
    2: Episode 3
convert: invalid argument for option `PNG': -size.
    3: Episode 4
convert: invalid argument for option `PNG': -size.
    4: Episode 5
convert: invalid argument for option `PNG': -size.
Making the DVD buttons...
convert: invalid argument for option `PNG': -size.
convert: unable to open image `/secdrv/Videos/TV Shows/Avatar/mpgs/Avab1d1.0/00_button-placeholder.png': No such file or directory.
convert: unable to open image `/secdrv/Videos/TV Shows/Avatar/mpgs/Avab1d1.0/00_title-00_placeholder.png': No such file or directory.
convert: unable to open image `/secdrv/Videos/TV Shows/Avatar/mpgs/Avab1d1.0/00_title-00_placeholder.png': No such file or directory.
convert: unable to open image `/secdrv/Videos/TV Shows/Avatar/mpgs/Avab1d1.0/00_button-placeholder.png': No such file or directory.
convert: unable to open image `/secdrv/Videos/TV Shows/Avatar/mpgs/Avab1d1.0/00_title-01_placeholder.png': No such file or directory.
convert: unable to open image `/secdrv/Videos/TV Shows/Avatar/mpgs/Avab1d1.0/00_title-01_placeholder.png': No such file or directory.
convert: unable to open image `/secdrv/Videos/TV Shows/Avatar/mpgs/Avab1d1.0/00_button-placeholder.png': No such file or directory.
convert: unable to open image `/secdrv/Videos/TV Shows/Avatar/mpgs/Avab1d1.0/00_title-02_placeholder.png': No such file or directory.
convert: unable to open image `/secdrv/Videos/TV Shows/Avatar/mpgs/Avab1d1.0/00_title-02_placeholder.png': No such file or directory.
convert: unable to open image `/secdrv/Videos/TV Shows/Avatar/mpgs/Avab1d1.0/00_button-placeholder.png': No such file or directory.
convert: unable to open image `/secdrv/Videos/TV Shows/Avatar/mpgs/Avab1d1.0/00_title-03_placeholder.png': No such file or directory.
convert: unable to open image `/secdrv/Videos/TV Shows/Avatar/mpgs/Avab1d1.0/00_title-03_placeholder.png': No such file or directory.
Creating the text menu...
Creating the DVD button overlays...
Adding the menu title...
convert: invalid argument for option `PNG': -size.
convert: unable to open image `/secdrv/Videos/TV Shows/Avatar/mpgs/Avab1d1.0/02_menu-title-placeholder.png': No such file or directory.
convert: unable to open image `/secdrv/Videos/TV Shows/Avatar/mpgs/Avab1d1.0/02_menu-title-placeholder.png': No such file or directory.
Placing text menu in the safe area...
Placing DVD buttons in the safe area...
Working on the the background...
Centering the safe area over the background...
Positioning the DVD button overlays on the background...
Generating preview...
Type 'q' to close the preview window.
Was the preview ok [y/N]?  y
Preview was OK. Continuing...
Converting "/secdrv/Music/Soundtraks/Avatartheme.mp3" to ac3...
expr: syntax error
/usr/local/bin/makemenu: line 778: test: -eq: unary operator expected
Converting menu image to video. This may take a while...
Multiplexing video and audio streams...
Adding the DVD buttons to menu...
Cleaning up...
=========================================================
Finished! Your menu should be in the file "Avab1d1.mpg".
You can use this menu on a DVD disc with:

  makexml -dvd -menu "Avab1d1.mpg" <title 1> <title 2> ... \
          -out <output name>

where <title N> is an MPEG video file corresponding to title N as listed
on your menu. Run 'makexml' without any options for more usage information.
=========================================================
Thanks for using makemenu!

```

It works when I play the menu in Totem.  I have sound and everything.  I then ran makexml.  Here is the output:

```
makexml -dvd -menu "Avab1d1.mpg" avb1c1_2.mpg avb1c3.mpg ab1c4.mpg ab1c5.mpg -out ab1d1 -------------------------------- makexml A script to generate XML for authoring a VCD, SVCD, or DVD.
Part of the tovid suite, version 0.30
http://www.tovid.org
--------------------------------
Adding a titleset-level menu using file: Avab1d1.mpg
    Avab1d1.mpg has aspect 133 (standard).
    avb1c1_2.mpg has aspect 133 (standard).
Adding title: avb1c1_2.mpg as title number 1 of titleset 1
    Calculating the duration of the video with:
        idvid -terse "avb1c1_2.mpg"
    This may take a few minutes, so please be patient...
    The duration of the video is 00:44:04
    avb1c3.mpg has aspect 133 (standard).
Adding title: avb1c3.mpg as title number 2 of titleset 1
    Calculating the duration of the video with:
        idvid -terse "avb1c3.mpg"
    This may take a few minutes, so please be patient...
    The duration of the video is 00:22:32
    ab1c4.mpg has aspect 133 (standard).
Adding title: ab1c4.mpg as title number 3 of titleset 1
    Calculating the duration of the video with:
        idvid -terse "ab1c4.mpg"
    This may take a few minutes, so please be patient...
    The duration of the video is 00:23:03
    ab1c5.mpg has aspect 133 (standard).
Adding title: ab1c5.mpg as title number 4 of titleset 1
    Calculating the duration of the video with:
        idvid -terse "ab1c5.mpg"
    This may take a few minutes, so please be patient...
    The duration of the video is 00:22:42
Closing titleset 1 with 4 title(s).
Done. The resulting XML was written to ab1d1.xml.
You can now author, image and/or burn the disc by running:
    makedvd "ab1d1.xml"
Thanks for using makexml!


```

Here is the problem:

```
/secdrv/Videos/TV Shows/Avatar/mpgs$ makedvd "ab1d1.xml"
--------------------------------
makedvd
A script to create a DVD-Video file structure and burn it to DVD
Part of the tovid suite, version 0.30
http://www.tovid.org
--------------------------------
Authoring disc from file: /secdrv/Videos/TV Shows/Avatar/mpgs/ab1d1.xml
<!-- makexml 0.30 -->
Putting output in ./ab1d1/
=========================================================
Authoring DVD-Video disc structure, estimated to require 1501MB.
Creating disc structure with the following command:
dvdauthor -x "/secdrv/Videos/TV Shows/Avatar/mpgs/ab1d1.xml"
=========================================================
DVDAuthor::dvdauthor, version 0.6.11.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: Locale=en_US.UTF-8
INFO: Converting filenames to UTF-8
INFO: dvdauthor creating VTS
STAT: Picking VTS 01

STAT: Processing Avab1d1.mpg...
ERR:  Cannot find button '5' as referenced by the subtitle
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
makedvd encountered an error during the DVD creation process:
Could not create the DVD-Video disc structure in ab1d1. Leaving ab1d1 for inspection.
See if anything in the above output helps you diagnose the
problem, and please file a bug report at tovid.org (_not_
the dvdauthor list) containing the above output.
Sorry for the inconvenience!
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

```

Does anybody know what went wrong and how to fix it?

---

### Post by izhitzza on 2007-07-28
Hi,

I am not familiar with tovid software, but I've had similar problems with dvdauthor when creating menus. The problem I had is that I used spumux to create the menues allowing it to atomatically determine the button region. Some times  it would split my button into two that way, so you could just run spumux by hand to generate menus specifying explicitly the button regions.

Good luck!
Alex.

---

### Post by valkarin on 2007-07-28
Okay.  Been tinkering with it and I got it to work.  After I deleted the -color and -font option, it worked sortof.  It got to the third video in the group and said WARN: Skipping sector, waiting for first VOBU...
What is that all about?

---

