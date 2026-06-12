---
title: "LIRC Help"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by truptrup on 2007-04-21
I have an encore enltvfm tv card with remote. its is a phillips saa7134 chipset.

anyway I have lirc running correctly, irw returns the correct key names, but i cant get mplayer or mythtv to recognize the commands. When i push up down left or right on the remote it corresponds to the keyboard directional keys. This is what v4l tells x to do with these commands even before i made lirc config. What do i do to stop x and allow lirc to control the remote. 
Here is my lircrc and lircd.conf is below it. Any help?
```
begin
   remote = *
   prog = mplayer
   button = hand
   config = run /usr/bin/tvswitch
end
begin
   remote = *
   prog = mplayer
   button = pause
   config = pause
end
begin
   remote = *
   prog = mplayer
   button = fastrewind
   repeat = 3
   config = seek -120
end
begin
   remote = *
   prog = mplayer
   button = fastforward
   repeat = 3
   config = seek 120
end
begin
   prog = mplayer
   button = c
   repeat = 3
   config = seek -10
end
begin
   prog = mplayer
   button = d
   repeat = 3
   config = seek 10
end
begin
   remote = *
   prog = mplayer
   button = down
   config = seek -10
end
begin
   remote = *
   prog = mplayer
   button = up
   config = seek 10
end
begin
   remote = *
   prog = mplayer
   button = left
   repeat = 2
   config = volume -1
end
begin
   remote = *
   prog = mplayer
   button = right
   repeat = 2
   config = volume 1
end
begin
   remote = *
   prog = mplayer
   button = ap4
   config = osd
end
begin
   remote = *
   prog = mplayer
   button = esc
   config = quit 166
end
begin
   remote = *
   prog = mplayer
   button = winstart
   config = menu toggle
end
begin
   remote = *
   prog = mplayer
   button = video
   config = set_menu open_file
end
begin
   remote = *
   prog = mplayer
   button = dvd
   config = menu hide\nplay_dvd
end
begin
   remote = *
   prog = mplayer
   button = tv
   config = set_menu tv_settings
end
begin
   remote = *
   prog = mplayer
   button = dvdtext
   config = sub_visibility
end
begin
   remote = *
   prog = mplayer
   button = record
   config = seek 0
end
begin
   remote = *
   prog = mplayer
   button = ok
   config = menu ok
end
begin
   remote = *
   prog = mplayer
   button = cursor-right
   config = menu ok
end
begin
   prog = mplayer
   button = mouse-right
   config = menu ok
end
begin
   remote = *
   prog = mplayer
   button = cursor-left
   config = menu cancel
end
begin
   prog = mplayer
   button = mouse-left
   config = menu cancel
end
begin
   prog = mplayer
   button = cursor-up
   repeat = 2
   config = menu up
end
begin
   prog = mplayer
   button = mouse-up
   repeat = 6
   config = menu up
end
begin
   prog = mplayer
   button = cursor-down
   repeat = 2
   config = menu down
end
begin
   prog = mplayer
   button = mouse-down
   repeat = 6
   config = menu down
end
begin
   prog = mplayer
   button = e
   repeat = 3
   config = sub_pos -1
end
begin
   prog = mplayer
   button = f
   repeat = 3
   config = sub_pos +1
end
begin
   remote = *
   prog = mplayer
   button = mute
   config = mute
end
begin
   remote = *
   prog = mplayer
   button = stop
   config = quit
end
begin
   remote = *
   prog = mplayer
   button = fullscreen
   config = set_menu aspect
end
begin
   remote = *
   prog = mplayer
   button = a
   config = set_menu jump_to
end
begin
   remote = *
   prog = mplayer
   button = dvdlang
   config = set_menu audio_sel
end

```

```
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.0(userspace) on Sat Feb 24 21:27:02 2007
#
# contributed by 
#
# brand:                       ENCORE ENLTV-FM
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  enltv
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   16
  pre_data       0x8001
  gap          195847
  toggle_bit      0


      begin codes
          next                     0x0197
          ok                       0x001C
          exit                     0x00AE
          up                       0x0067
          down                     0x006C
          left                     0x0069
          right                    0x006A
          winstart                 0x0066
          recall                   0x0195
          tv                       0x0179
          video                    0x0189
          music                    0x0188
          picture                  0x016F
          esc                      0x0001
          desktop                  0x0020
          tab                      0x000F
          switch                   0x00E3
          menu                     0x008B
          fullscreen               0x0174
          timeshift                0x0167
          source                   0x0175
          record                   0x00A7
          pause                    0x00CF
          stop                     0x0080
          next2stop                0x00D4
          fastrewind               0x00A8
          fastforward              0x00D0
          skipback                 0x019C
          skipforward              0x0197
          tvwall                   0x016C
          dvdsound                 0x00D5
          dvdlang                  0x0170
          dvdtext                  0x0184
          sysshutdown              0x008E
          main                     0x0175
          sap                      0x0161
          teletext                 0x0094
          ap1                      0x018E
          ap2                      0x018F
          ap3                      0x0190
          ap4                      0x0191
          1                        0x0002
          2                        0x0003
          3                        0x0004
          4                        0x0005
          5                        0x0006
          6                        0x0007
          7                        0x0008
          8                        0x0009
          9                        0x0004
          9                        0x000A
          0                        0x000B
          -/--                     0x018B
      end codes

end remote



```

---

### Post by Dubstar_04 on 2007-04-22
Is your lircrc file in the home/user/.mythtv  folder??

If so use 

```
 
 $ cd  .xine (or .mplayer)
 $ ln -s .mythtv/lircrc .lircrc 
```

to make links in the correct folders. this sorted it for me.

---

### Post by truptrup on 2007-04-22
Thanks for the reply.
Right now i am just trying to get it working in mplayer. So i have the lircrc file in 
/home/mythtv/.mplayer and /home/mythtv (wasnt sure where to put it)
Just getting lirc to work by directly playing a video with mplayer is the goal, no mythtv involved.
the strange thing is irw captures the correct commands but mplayer receives different commands.

and just for reference this is the commands v4l gives x when i push a button. This is what mplayer receives. 

```
+ [ 0x1e ] = KEY_TV,
+ [ 0x00 ] = KEY_VIDEO,
+ [ 0x01 ] = KEY_AUDIO, /* music */
+ [ 0x02 ] = KEY_MHP, /* picture */
+
+ [ 0x1f ] = KEY_1,
+ [ 0x03 ] = KEY_2,
+ [ 0x04 ] = KEY_3,
+ [ 0x05 ] = KEY_4,
+ [ 0x1c ] = KEY_5,
+ [ 0x06 ] = KEY_6,
+ [ 0x07 ] = KEY_7,
+ [ 0x08 ] = KEY_8,
+ [ 0x1d ] = KEY_9,
+ [ 0x0a ] = KEY_0,
+
+ [ 0x09 ] = KEY_LIST, /* -/-- */
+ [ 0x0b ] = KEY_LAST, /* recall */
+
+ [ 0x14 ] = KEY_HOME, /* win start menu */
+ [ 0x15 ] = KEY_EXIT, /* exit */
+#if 0
+ [ 0x16 ] = KEY_CHANNELUP, /* UP */
+ [ 0x12 ] = KEY_CHANNELDOWN, /* DOWN */
+ [ 0x0c ] = KEY_VOLUMEUP, /* RIGHT */
+ [ 0x17 ] = KEY_VOLUMEDOWN, /* LEFT */
+#else
+ [ 0x16 ] = KEY_UP,
+ [ 0x12 ] = KEY_DOWN,
+ [ 0x0c ] = KEY_RIGHT,
+ [ 0x17 ] = KEY_LEFT,
+#endif
+
+ [ 0x18 ] = KEY_ENTER, /* OK */
+
+ [ 0x0e ] = KEY_ESC,
+ [ 0x13 ] = KEY_D, /* desktop */
+ [ 0x11 ] = KEY_TAB,
+ [ 0x19 ] = KEY_SWITCHVIDEOMODE, /* switch */
+
+ [ 0x1a ] = KEY_MENU,
+ [ 0x1b ] = KEY_ZOOM, /* fullscreen */
+ [ 0x44 ] = KEY_TIME, /* time shift */
+ [ 0x40 ] = KEY_MODE, /* source */
+
+ [ 0x5a ] = KEY_RECORD,
+ [ 0x42 ] = KEY_PLAY, /* play/pause */
+ [ 0x45 ] = KEY_STOP,
+ [ 0x43 ] = KEY_CAMERA, /* camera icon */
+
+ [ 0x48 ] = KEY_REWIND,
+ [ 0x4a ] = KEY_FASTFORWARD,
+ [ 0x49 ] = KEY_PREVIOUS,
+ [ 0x4b ] = KEY_NEXT,
+
+ [ 0x4c ] = KEY_FAVORITES, /* tv wall */
+ [ 0x4d ] = KEY_SOUND, /* DVD sound */
+ [ 0x4e ] = KEY_LANGUAGE, /* DVD lang */
+ [ 0x4f ] = KEY_TEXT, /* DVD text */
+
+ [ 0x50 ] = KEY_SLEEP, /* shutdown */
+ [ 0x51 ] = KEY_MODE, /* stereo > main */
+ [ 0x52 ] = KEY_SELECT, /* stereo > sap */
+ [ 0x53 ] = KEY_PROG1, /* teletext */
+
+
+ [ 0x59 ] = KEY_RED, /* AP1 */
+ [ 0x41 ] = KEY_GREEN, /* AP2 */
+ [ 0x47 ] = KEY_YELLOW, /* AP3 */
+ [ 0x57 ] = KEY_BLUE, /* AP4 */ 
```

---

