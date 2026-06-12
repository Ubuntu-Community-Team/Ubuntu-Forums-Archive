---
title: "Xine Force Aspect Ratio"
date: 2007-04-30
forum: Multimedia &amp; Video
---

### Post by truptrup on 2007-04-30
Is it possible to start xine videos in 4:3 thru the command line with some kind of option or somewhere in the settings?

It would be great if i did not need to cycle the aspects each time a new video was started but it defaulted to 4:3.
I think it is set to auto now.

---

### Post by disturbedite on 2007-04-30
when i read the title of the thread i figured you were going to ask how to do that via gui and i was gonna respond that its easy to do that, but since you're asking from command line, i'd recommend reading the xine documentation.

---

### Post by truptrup on 2007-05-01
xine --aspect-ratio 4:3 is the answer

here is all commands for anyone interested
```
Usage: xine [OPTIONS]... [MRL]

OPTIONS are:
  -v, --version                Display version.
      --verbose [=level]       Set verbosity level. Default is 1.
  -c, --config <file>          Use config file instead of default one.
  -V, --video-driver <drv>     Select video driver by id. Available drivers:
                               dxr3 aadxr3 xv SyncFB opengl xshm xxmc none sdl f                                             b xvmc
  -A, --audio-driver <drv>     Select audio driver by id. Available drivers:
                               null alsa oss pulseaudio file none
  -u, --spu-channel <#>        Select SPU (subtitle) channel '#'.
  -a, --audio-channel <#>      Select audio channel '#'.
  -p, --auto-play [opt]        Play on start. Can be followed by:
                    'f': in fullscreen mode.
                    'h': hide GUI (panel, etc.).
                    'w': hide video window.
                    'q': quit when play is done.
                    'd': retrieve playlist from DVD. (deprecated. use -s DVD)
                    'v': retrieve playlist from VCD. (deprecated. use -s VCD)
                    'F': in xinerama fullscreen mode.
  -s, --auto-scan <plugin>     auto-scan play list from <plugin>
  -f, --fullscreen             start in fullscreen mode,
  -F, --xineramafull           start in xinerama fullscreen (display on several                                              screens),
  -g, --hide-gui               hide GUI (panel, etc.)
  -I, --no-gui                 disable GUI
      --no-mouse               disable mouse event
  -H, --hide-video             hide video window
  -L, --no-lirc                Turn off LIRC support.
      --visual <class-or-id>   Use the specified X11 visual. <class-or-id>
                               is either an X11 visual class, or a visual id.
      --install                Install a private colormap.
      --keymap [=option]       Display keymap. Option are:
                                 'default': display default keymap table,
                                 'lirc': display draft of a .lircrc config file.
                                 'remapped': user remapped keymap table.
                                 'file:<filename>': use <filename> as keymap.
                                 -if no option is given, 'default' is selected.
  -n, --network                Enable network remote control server.
      --network-port           Specify network server port number.
  -R, --root                   Use root window as video window.
  -W, --wid                    Use a window id.
  -G, --geometry <WxH[+X+Y]>   Set output window geometry (X style).
  -B, --borderless             Borderless video output window.
  -N, --animation <mrl>        Specify mrl to play when video output isn't used.
                                 -can be used more than one time.
  -P, --playlist <filename>    Load a playlist file.
  -l, --loop [=mode]           Set playlist loop mode (default: loop). Modes are                                             :
                                 'loop': loop entire playlist.
                                 'repeat': repeat current playlist entry.
                                 'shuffle': select randomly a yet unplayed entry                                              from playlist
                                 'shuffle+': same as 'shuffle', but indefinetely                                              replay the playlist.
      --skin-server-url <url>  Define the skin server url.
      --enqueue <mrl> ...      Enqueue mrl of a running session (session 0)
  -S, --session <option1,option2,...>
                               Session managements. Options can be:
                    session=n   specify session <n> number,
                    mrl=m       add mrl <m> to the playlist,
                    audio=c     select audio channel (<c>: 'next' or 'prev'),
                    spu=c       select spu channel (<c>: 'next' or 'prev'),
                    volume=v    set audio volume,
                    amp=v       set amplification level,
                    loop=m      set loop mode (<m>: 'none' 'loop' 'repeat' 'shuf                                             fle' or 'shuffle+'),
                    get_speed   get speed value (see man page for returned value                                             ).
                    (playlist|pl)=p
                                 <p> can be:
                                   'clear'  clear the playlist,
                                   'first'  play first entry in the playlist,
                                   'prev'   play previous playlist entry,
                                   'next'   play next playlist entry,
                                   'last'   play last entry in the playlist,
                                   'load:s' load playlist file <s>,
                                   'stop'   stop playback at the end of current                                              playback.
                                   'cont'   continue playback at the end of curr                                             ent playback.
                    play, slow2, slow4, pause, fast2,
                    fast4, stop, quit, fullscreen, eject.
  -Z                           Don't automatically start playback (smart mode).
  -D, --deinterlace [post]...  Deinterlace video output. One or more post plugin
                                 can be specified, with optional parameters.
                                 Syntax is the same as --post option.
  -r, --aspect-ratio <mode>    Set aspect ratio of video output. Modes are:
                                 'auto', 'square', '4:3', 'anamorphic', 'dvb'.
      --broadcast-port <port>  Set port of xine broadcaster (master side)
                               Slave is started with 'xine slave://address:port'
      --no-logo                Don't display the logo.
  -E, --no-reload              Don't reload old playlist.
      --post <plugin>[:parameter=value][,...][;...]
                               Load one or many post plugin(s).
                               Parameters are comma separated.
                               This option can be used more than one time.
      --disable-post           Don't enable post plugin(s).
      --no-splash              Don't display the splash screen.
      --stdctl                 Control xine by the console, using lirc commands.
  -T, --tvout <backend>        Turn on tvout support. Backend can be:
                               ati
      --list-plugins [=type]   Display the list of all available plugins,
                               Optional <type> can be:
                    audio_out, video_out, demux, input, sub, post,
                    audio_decoder, video_decoder.
      --bug-report [=mrl]      Enable bug report mode:
                                 Turn on verbosity, gather all output
                                 messages and write them into a file named
                                 BUG-REPORT.TXT.
                                 If <mrl> is given, xine will play the mrl
                                 then quit (like -pq).


examples for valid MRLs (media resource locator):
  File:  'path/foo.vob'
         '/path/foo.vob'
         'file://path/foo.vob'
         'fifo://[[mpeg1|mpeg2]:/]path/foo'
         'stdin://[mpeg1|mpeg2]' or '-' (mpeg2 only)
  DVD:   'dvd://VTS_01_2.VOB'
  VCD:   'vcd://<track number>'


```

---

