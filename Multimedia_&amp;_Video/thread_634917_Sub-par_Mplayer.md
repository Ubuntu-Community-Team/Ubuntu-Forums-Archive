---
title: "Sub-par Mplayer"
date: 2007-12-08
forum: Multimedia &amp; Video
---

### Post by Canew on 2007-12-08
Hi:

I'm clearly missing something here with Mplayer, as everyone raves about how utterly wonderful this thing is. No disrespect to all the advocates, but for me, personally, I think it's got the worst interface I've ever seen.

Yes, the video plays perfectly (no mean feat, considering all the trouble I went through trying to do this with Edgy - I now have Gutsy), but what good is it when I only have four buttons to click on? In my Windoze days, I had a player (no, I don't recall the name of it now) that had a nice little floating widget-esque interface that I could make appear and disappear at will.

On the sleek, stylish interface, I had buttons for absolutely everything -- full screen toggle, automatic switching between audio streams, subtitles, angles, and all the other options were available on the fly, without going back to the title screen, but if I wanted to, there were buttons for that, too. There was a slider wheel that not only allowed me to scan forward and backward with ease, but it even controlled how fast I could do it. There was also a slow-motion button, which I like when watching certain action movie fight scenes. Finally, I could scan forward and backward at various speeds using the mouse wheel, and toggle different slow-motion speeds by clicking center button.

Again, maybe I'm just dumb, but I see NONE of these options with Mplayer. Even the chapter skip buttons are nothing to get excited about. Could someone enlighten me as to whether an interface exists with Mplayer that allows these things, either built-in or available as an add-on somewhere?

And if there is no such thing, then pardon me for being blunt, but... what's so special about the player?

---

### Post by shirilover on 2007-12-08
I assume you don't know anything about the keyboard shortcuts then.
[quote= "mplayer man page']

INTERACTIVE CONTROL
       MPlayer has a fully configurable, command-driven control layer which allows you to control MPlayer using keyboard, mouse, joystick or remote control (with LIRC).  See the  input option for ways to customize it.

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
                   Step forward.  Pressing once will pause movie, every consecutive press will play one frame and then go into pause mode again (any other key unpauses).
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
              TAB (MPEG-TS and libavformat only)
                   Cycle through the available programs.
              f
                   Toggle fullscreen (also see -fs).
              T
                   Toggle stay-on-top (also see -ontop).
              w and e
                   Decrease/increase pan-and-scan range.
              o
                   Toggle OSD states: none / seek / seek + timer / seek + timer + total time.
              d
                   Toggle frame dropping states: none / skip display / skip decoding (see -framedrop and -hardframedrop).
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
                   Set start or end of an EDL skip and write it out to the given file.
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

              (The  following  keys are valid only when using a hardware accelerated video output (xv, (x)vidix, (x)mga, etc), the software equalizer (-vf eq or -vf eq2) or hue filter
              (-vf hue).)

              1 and 2
                   Adjust contrast.
              3 and 4
                   Adjust brightness.
              5 and 6
                   Adjust hue.
              7 and 8
                   Adjust saturation.

              (The following keys are valid only when using the quartz or macosx video output driver.)

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

              (The following keys are valid only when using the sdl video output driver.)

              c
                   Cycle through available fullscreen modes.
              n
                   Restore original mode.

              (The following keys are valid if you have a keyboard with multimedia keys.)

              PAUSE
                   Pause.
              STOP
                   Stop playing and quit.
              PREVIOUS and NEXT
                   Seek backward/forward 1 minute.

              (The following keys are only valid if GUI support is compiled in and will take precedence over the keys defined above.)

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

              (The following keys are only valid if you compiled with TV or DVB input support and will take precedence over the keys defined above.)

              h and k
                   Select previous/next channel.
              n
                   Change norm.
              u
                   Change channel list.

              (The following keys are only valid if you compiled with dvdnav support: They are used to navigate the menus.)

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
                   Return to nearest menu (the order of preference is: chapter->title->root).
              keypad ENTER
                   Confirm choice.

              (The following keys are only valid if teletext support is enabled during compilation: They are used for controlling TV teletext.)

              X    Switch teletext on/off.
              Q and W
                   Go to next/prev teletext page.

              mouse control
                     button 3 and button 4
                          Seek backward/forward 1 minute.
                     button 5 and button 6
                          Decrease/increase volume.

              joystick control
                     left and right
                          Seek backward/forward 10 seconds.
                     up and down
                          Seek forward/backward 1 minute.
                     button 1
                          Pause.
                     button 2
                          Toggle OSD states: none / seek / seek + timer / seek + timer + total time.
                     button 3 and button 4
                          Decrease/increase volume.
[/quote]

---

### Post by Canew on 2007-12-08
Yeah, I know about those, but overall I'm not impressed with some of the commands, and what about the graphical version?

---

### Post by Thanoulis on 2007-12-08
The great about Mplayer isn't its user friendliness (imo). It its superb functionality, stability and the ability to play everything (at least everything i have thrown in it! :) ) .
If you prefer something more gui-able, try out VLC, or the build-in Totem.

---

### Post by Canew on 2007-12-08
Yeah, I like Mplayer's stability, too. Yes, the keyboard commands work ok, but I'd MUCH rather have something like what I once had. Hmmm, I've been looking for an excuse to experiment with creating stuff in Linux. I can't believe no one's thought of this in the past. I would think it would just be a matter of creating a window/widget with clickable buttons linked to the keyboard commands. I know, not as easy as it sounds, but let's say that can be done. Would it be as easy as creating a program that I could run in terminal at the same time Mplayer was running? I can't believe it would be much more complicated than that, would it?

---

### Post by eye208 on 2007-12-08
> **Canew said:**
> but what good is it when I only have four buttons to click on? In my Windoze days, I had a player (no, I don't recall the name of it now) that had a nice little floating widget-esque interface that I could make appear and disappear at will.
Right-clicking on the MPlayer window/screen will open a menu with lots of options (if you started the player with the -gui option). There are several graphical front-ends available in separate packages.

MPlayer should be seen not as a media player, but as a media player *engine*. MPlayer works when all the other media players fail. That's one reason why people prefer it over anything else. The other reason is its usefulness as a format transcoding tool (in combination with MEncoder).

---

### Post by Canew on 2007-12-08
> **eye208 said:**
> Right-clicking on the MPlayer window/screen will open a menu with lots of options (if you started the player with the -gui option). There are several graphical front-ends available in separate packages.

MPlayer should be seen not as a media player, but as a media player *engine*. MPlayer works when all the other media players fail. That's one reason why people prefer it over anything else. The other reason is its usefulness as a format transcoding tool (in combination with MEncoder).

Yeah, this is what I figured. So what's a good graphical front end for it?

---

### Post by andrew.46 on 2008-01-08
Hi,

 Of course the gui for mplayer is not even enabled by default, you have to pass the option at configure time. I have always believed that if you want to start learning how to utilise this program properly you *have* to use the CLI. The gui, although a bit more sophisticated than many might believe, masks much of the power of the program.

   Andrew

---

