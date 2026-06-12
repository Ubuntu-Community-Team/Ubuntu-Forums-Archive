---
title: "MPV config file - remember last window setting"
date: 2016-05-09
forum: Multimedia Software
---

### Post by Kevin McCready on 2016-05-09
Every time I open mpv I have to resize and reposition the window. I want it to open each time in the same position and size.

I've checked the manual but I haven't had success with putting either of the following in my config file:
--geometry=<[683[x740]]>
or
--autofit=<[683[x740]]>

Hoping someone can tell me what I'm doing wrong, or how to solve. 

This is from the manual:
--geometry=<[W[xH]][+-x+-y]>, --geometry=<x:y>Adjust the initial window position or size. W and H set the window             size in pixels. x and y set the window position, measured in pixels             from the top-left corner of the screen to the top-left corner of the image             being displayed. If a percentage sign (%) is given after the argument,             it turns the value into a percentage of the screen size in that direction.             Positions are specified similar to the standard X11 --geometry option             format, in which e.g. +10-50 means "place 10 pixels from the left border and             50 pixels from the lower border" and "--20+-10" means "place 20 pixels             beyond the right and 10 pixels beyond the top border".
             If an external window is specified using the --wid option, this             option is ignored.
             The coordinates are relative to the screen given with --screen for the             video output drivers that fully support --screen.
                          Note
             Generally only supported by GUI VOs. Ignored for encoding.
             
                                       Note (X11)
             This option does not work properly with all window managers.
             
                          Examples
             50:40Places the window at x=50, y=40.50%:50%Places the window in the middle of the screen.100%:100%Places the window at the bottom right corner of the screen.50%Sets the window width to half the screen width. Window height is set             so that the window has the video aspect ratio.50%x50%Forces the window width and height to half the screen width and             height. Will show black borders to compensate for the video aspect             ration (with most VOs and without --no-keepaspect).50%+10+10Sets the window to half the screen widths, and positions it 10             pixels below/left of the top left corner of the screen.             
             See also --autofit and --autofit-larger for fitting the window into             a given size without changing aspect ratio.
             --autofit=<[W[xH]]>Set the initial window size to a maximum size specified by WxH, without             changing the window's aspect ratio. The size is measured in pixels, or if             a number is followed by a percentage sign (%), in percents of the             screen size.
             This option never changes the aspect ratio of the window. If the aspect             ratio mismatches, the window's size is reduced until it fits into the             specified size.
             Window position is not taken into account, nor is it modified by this             option (the window manager still may place the window differently depending             on size). Use --geometry to change the window position. Its effects             are applied after this option.
             See --geometry for details how this is handled with multi-monitor             setups.
             Use --autofit-larger instead if you just want to limit the maximum size             of the window, rather than always forcing a window size.
             Use --geometry if you want to force both window width and height to a             specific size.
                          Note
             Generally only supported by GUI VOs. Ignored for encoding.
             
                          Examples
             70%Make the window width 70% of the screen size, keeping aspect ratio.1000Set the window width to 1000 pixels, keeping aspect ratio.70%:60%Make the window as large as possible, without being wider than 70%             of the screen width, or higher than 60% of the screen height.

---

### Post by mc4man on 2016-05-09
No idea about size as I want mpv to always open at 'native' size of the video file which it does very well. However do always want it to open centered here so put this in mpv.conf (in the top 'general' section, I've other [extension] & [protocol] setting sections - 

geometry=50%:50%

(generally speaking options for cli should go in mpv.conf without --
Ex. of my general section, fairly sparse, # comments out options/commands without removing

```
geometry=50%:50%
hwdec=auto
vo=vaapi
#hr-seek=always
log-file=mpv.log
x11-bypass-compositor=no
#--ytdl-format=bestvideo+bestaudio
#fs=yes
save-position-on-quit

```

---

### Post by Kevin McCready on 2016-05-09
Thanks very much!
geometry=55%
save-position-on-quit

gave me what I want.   save-position-on-quit  is the position in the playlist video rather than window position on the screen.

save-window-size-and-screen-position-on-quit 
would be a nice option

---

