---
title: "Mplayer keyboard shortcuts"
date: 2008-05-28
forum: Multimedia Software
---

### Post by Hallvor on 2008-05-28
MPlayer is a multimedia player that has a lot of options, but not all are available through the GUI.

Anyway, here is a list of available shortcuts that will make you able to change subtitles, audio track, sync audio and much more.

To get a list of these shortcuts, it is also possible to type man mplayer in the terminal to get the manual in text mode:

keyboard control
              <- and ->
                   Seek backward/forward 10 seconds.
              up and down
                   Seek forward/backward 1 minute.
              pgup and pgdown
                   Seek forward/backward 10 minutes.
              [ and ]
                   Decrease/increase current playback speed by 10%.
              { and }
                   Halve/double current playback speed.
              backspace
                   Reset playback speed to normal.
              < and >
                   Go backward/forward in the playlist.
              ENTER
                   Go forward in the playlist, even over the end.
              HOME and END
                   next/previous playtree entry in the parent list
              INS and DEL (ASX playlist only)
                   next/previous alternative source.
 p / SPACE
                   Pause (pressing again unpauses).
              .
                   Step forward.  Pressing once will pause movie,  every  con&#8208;
                   secutive  press  will play one frame and then go into pause
                   mode again (any other key unpauses).
              q / ESC
                   Stop playing and quit.
              + and -
                   Adjust audio delay by +/- 0.1 seconds.
              / and *
                   Decrease/increase volume.
              9 and 0
                   Decrease/increase volume.
              ( and )
                   Adjust audio balance in favor of left/right channel.
              m
                   Mute sound.
              _ (MPEG-TS, AVI and libavformat only)
                   Cycle through the available video tracks.
# (DVD, MPEG, Matroska, AVI and libavformat only)
                   Cycle through the available audio tracks.
              TAB (MPEG-TS only)
                   Cycle through the available programs.
              f
                   Toggle fullscreen (also see -fs).
              T
                   Toggle stay-on-top (also see -ontop).
              w and e
                   Decrease/increase pan-and-scan range.
              o
                   Toggle OSD states: none / seek / seek  +  timer  /  seek  +
                   timer + total time.
              d
                   Toggle  frame  dropping  states: none / skip display / skip
                   decoding (see -framedrop and -hardframedrop).
              v
                   Toggle subtitle visibility.
              j
                   Cycle through the available subtitles.
              y and g
Step forward/backward in the subtitle list.
              F
                   Toggle displaying "forced subtitles".
              a
                   Toggle subtitle alignment: top / middle / bottom.
              x and z
                   Adjust subtitle delay by +/- 0.1 seconds.
              r and t
                   Move subtitles up/down.
              i (-edlout mode only)
                   Set start or end of an EDL skip and write  it  out  to  the
                   given file.
              s (-vf screenshot only)
                   Take a screenshot.
              S (-vf screenshot only)
                   Start/stop taking screenshots.
              I
                   Show filename on the OSD.
              ! and @
                   Seek to the beginning of the previous/next chapter.
              D (-vo xvmc, -vf yadif, -vf kerndeint only)
Activate/deactivate deinterlacer.

              (The  following keys are valid only when using a hardware accel&#8208;
              erated video output (xv, (x)vidix, (x)mga,  etc),  the  software
              equalizer (-vf eq or -vf eq2) or hue filter (-vf hue).)

              1 and 2
                   Adjust contrast.
              3 and 4
                   Adjust brightness.
              5 and 6
                   Adjust hue.
              7 and 8
                   Adjust saturation.

              (The  following keys are valid only when using the quartz or ma&#8208;
              cosx video output driver.)

              command + 0
                   Resize movie window to half its original size.
              command + 1
Resize movie window to its original size.
              command + 2
                   Resize movie window to double its original size.
              command + f
                   Toggle fullscreen (also see -fs).
              command + [ and command + ]
                   Set movie window alpha.

              (The following keys are valid only when using the sdl video out&#8208;
              put driver.)

              c
                   Cycle through available fullscreen modes.
              n
                   Restore original mode.

              (The following keys are valid if you have a keyboard with multi&#8208;
              media keys.)

              PAUSE
Pause.
              STOP
                   Stop playing and quit.
              PREVIOUS and NEXT
                   Seek backward/forward 1 minute.

              (The following keys are only valid if GUI support is compiled in
              and will take precedence over the keys defined above.)

              ENTER
                   Start playing.
              ESC
                   Stop playing.
              l
                   Load file.
              t
                   Load subtitle.
              c
                   Open skin browser.
              p
                   Open playlist.
r
                   Open preferences.

              (The  following  keys  are only valid if you compiled with TV or
              DVB input support and will take precedence over the keys defined
              above.)

              h and k
                   Select previous/next channel.
              n
                   Change norm.
              u
                   Change channel list.

              (The  following  keys are only valid if you compiled with dvdnav
              support: They are used to navigate the menus.)

              keypad 8
                   Select button up.
              keypad 2
Select button down.
              keypad 4
                   Select button left.
              keypad 6
                   Select button right.
              keypad 5
                   Return to main menu.
              keypad 7
                   Return to nearest menu (the order of preference  is:  chap&#8208;
                   ter->title->root).
              keypad ENTER
                   Confirm choice.

              (The  following  keys  are only valid if teletext support is en&#8208;
              abled during compilation: They are used for controlling TV tele&#8208;
              text.)

              X    Switch teletext on/off.
              Q and W
                   Go to next/prev teletext page.

---

### Post by K.Mandla on 2008-05-29
Moved to Multimedia and Video.

---

### Post by Nameless_one on 2008-06-11
Has anyone noticed that some of these don't work? 

For example, try loading more than one subtitle files at once. I tried cycling through the available subtitles using y and g, but y delayed the subtitles for about 90 seconds instead. g lessened the delay by a second or two. b does nothing. Only j cycles through subtitles. 

Also, I tried cycling through audio tracks today. The manpage lists #, but when I pressed it, it only displayed the name of the current audio track, it didn't change it. 

Is the manpage outdated? Am I the only one having these problems? I am using Gutsy.

---

