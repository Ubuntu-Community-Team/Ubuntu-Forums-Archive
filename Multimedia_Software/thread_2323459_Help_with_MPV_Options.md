---
title: "Help with MPV Options"
date: 2016-05-05
forum: Multimedia Software
---

### Post by dannymichel on 2016-05-05
Was wondering if someone could help me with MPV options. What I need is as follows:
[LIST]
[*]Automatic episode detection so i can click next and go to the next episode
[*]High quality playback
[*]Automatic save position on exit.
[/LIST]

---

### Post by matt_symes on 2016-05-05
As your thread is not [SOLVED], I have removed that prefix for you.

---

### Post by mc4man on 2016-05-06
Re:3, see screen 1 If your build has man pages in pdf then you can open in evince. Also available in [html online]("https://mpv.io/manual/master/") 
If wanting all the time add to mpv.conf, ex.  scr. 2, line 6
Re:1 - don't know, don't have such files
Re:2 - that's very much dependent on your files, hardware - read the man

---

### Post by SeijiSensei on 2016-05-06
> **dannymichel said:**
> Was wondering if someone could help me with MPV options. What I need is as follows:
[LIST]
[*]Automatic episode detection so i can click next and go to the next episode
[*]High quality playback
[*]Automatic save position on exit.
[/LIST]

If you install smplayer and configure it to use mpv (Options > Preferences > General; enter /usr/bin/mpv in the box), it can handle both the first and last requests.  In your file browser, select all the episodes, then right-click and choose "Enqueue in SMPlayer".  Alternatively use Options > Playlist and select all the episode files there.

SMPlayer will automatically save your position when you close it.

As for the second issue, this depends on the video card you are using and the quality of the file you are playing.  I watch 720p/1080p files encoded in H.264 and stored in the Matroska container all the time and have no issues with quality.  In smplayer, you can try different video drivers (Options > Preferences > Video; select from drop-down list) to see which one works best for you.  On my computer with an NVIDIA card, I use the "vdpau" driver.  On some systems OpenGL works better, while on others I use xv.

---

### Post by shantiq on 2016-05-08
> **dannymichel said:**
> Was wondering if someone could help me with MPV options. What I need is as follows:
[LIST]
[*]Automatic episode detection so i can click next and go to the next episode 
[*]High quality playback 
[*]Automatic save position on exit. 
[/LIST]



hi there is you want position saved  [will automatically play best quality]>>


enter

```
--save-position-on-quit
```

in a text document called [may need to be created] so:

```
sudo gedit  ~/.config/mpv/mpv.conf
```


for any additional command use ```
mpv  --list-options
```


```
mpv  --list-options
Options:

 --ab-loop-a                      Time (default: no)
 --ab-loop-b                      Time (default: no)
 --ad                             String (default: -spdif:*)
 --ad-lavc-ac3drc                 Float (0 to 6) (default: 0.000000)
 --ad-lavc-downmix                Flag (default: yes)
 --ad-lavc-o                      Key/value list (default: )
 --ad-lavc-threads                Integer (1 to 16) (default: 1)
 --ad-spdif-dtshd                 Flag (default: no)
 --af*                            Object settings list (default: )
 --af-defaults                    Object settings list (default: )
 --aid                            Choices: no auto (or an integer) (0 to 8190) (default: auto)
 --alang                          String list (default: )
 --ao                             Object settings list (default: )
 --ao-defaults                    Object settings list (default: )
 --ass-force-margins              Flag (default: no)
 --ass-force-style                String list (default: )
 --ass-hinting                    Choices: none light normal native (default: none)
 --ass-line-spacing               Float (-1000 to 1000) (default: 0.000000)
 --ass-scale-with-window          Flag (default: no)
 --ass-shaper                     Choices: simple complex (default: complex)
 --ass-style-override             Choices: no yes force signfs (default: yes)
 --ass-styles                     String (default: ) [file]
 --ass-vsfilter-aspect-compat     Flag (default: yes)
 --ass-vsfilter-blur-compat       Flag (default: yes)
 --ass-vsfilter-color-compat      Choices: no basic full force-601 (default: basic)
 --audio-buffer                   Double (0 to 10) (default: 0.200000)
 --audio-channels                 Audio channels or channel map (0 to any)
 --audio-client-name              String (default: mpv)
 --audio-delay                    Float (-100 to 100) (default: 0.000000)
 --audio-demuxer                  String (default: )
 --audio-device                   String (default: auto)
 --audio-display                  Choices: no attachment (default: attachment)
 --audio-fallback-to-null         Flag (default: no)
 --audio-file                     String list (default: ) [file]
 --audio-file-auto                Choices: no exact fuzzy all (default: exact)
 --audio-file-paths               String list (default: )
 --audio-format                   Audio format
 --audio-normalize-downmix        Flag (default: no)
 --audio-pitch-correction         Flag (default: yes)
 --audio-samplerate               Integer (1000 to 768000) (default: 0)
 --audio-spdif                    String (default: )
 --autofit                        Window size (default: )
 --autofit-larger                 Window size (default: )
 --autofit-smaller                Window size (default: )
 --autosync                       Choices: no (or an integer) (0 to 10000) (default: 0)
 --bluray-angle                   Integer (0 to 999) (default: 0)
 --bluray-device                  String (default: ) [file]
 --border                         Flag (default: yes)
 --brightness                     Integer (-100 to 100) (default: 1000)
 --cache                          Choices: no auto yes (or an integer) (32 to 2147483647) (default: auto)
 --cache-backbuffer               Integer (0 to 2147483647) (default: 75000)
 --cache-default                  Choices: no (or an integer) (32 to 2147483647) (default: 75000)
 --cache-file                     String (default: ) [file]
 --cache-file-size                Integer (0 to 2147483647) (default: 1048576)
 --cache-initial                  Integer (0 to 2147483647) (default: 0)
 --cache-pause                    Flag (default: yes)
 --cache-secs                     Double (0 to any) (default: 10.000000)
 --cache-seek-min                 Integer (0 to 2147483647) (default: 500)
 --cdda-cdtext                    Flag (default: no)
 --cdda-device                    String (default: )
 --cdda-overlap                   Integer (0 to 75) (default: -1)
 --cdda-paranoia                  Integer (0 to 2) (default: 0)
 --cdda-sector-size               Integer (1 to 100) (default: 0)
 --cdda-skip                      Flag (default: yes)
 --cdda-span                      Int[-Int]
 --cdda-speed                     Integer (1 to 100) (default: 0)
 --cdda-toc-bias                  Integer (default: 0)
 --cdda-toc-offset                Integer (default: 0)
 --cdrom-device                   String (default: ) [file]
 --chapter                        Int[-Int]
 --chapter-merge-threshold        Integer (0 to 10000) (default: 100)
 --chapter-seek-threshold         Double (default: 5.000000)
 --chapters-file                  String (default: ) [file]
 --config                         Flag (default: yes) [global]
 --config-dir                     String (default: ) [global] [nocfg]
 --contrast                       Integer (-100 to 100) (default: 1000)
 --cookies                        Flag (default: no)
 --cookies-file                   String (default: ) [file]
 --correct-pts                    Flag (default: yes)
 --cursor-autohide                Choices: no always (or an integer) (0 to 30000) (default: 1000)
 --cursor-autohide-fs-only        Flag (default: no)
 --deinterlace                    Choices: auto no yes (default: auto)
 --demuxer                        String (default: )
 --demuxer-lavf-allow-mimetype    Flag (default: yes)
 --demuxer-lavf-analyzeduration   Float (0 to 3600) (default: 0.000000)
 --demuxer-lavf-buffersize        Integer (1 to 10485760) (default: 32768)
 --demuxer-lavf-cryptokey         String (default: )
 --demuxer-lavf-format            String (default: )
 --demuxer-lavf-genpts-mode       Choices: lavf no (default: no)
 --demuxer-lavf-hacks             Flag (default: yes)
 --demuxer-lavf-o                 Key/value list (default: )
 --demuxer-lavf-probescore        Integer (1 to 100) (default: 26)
 --demuxer-lavf-probesize         Integer (32 to 2147483647) (default: 0)
 --demuxer-max-bytes              Integer (0 to 2147483647) (default: 419430400)
 --demuxer-max-packets            Integer (0 to 2147483647) (default: 16000)
 --demuxer-mkv-probe-start-time   Flag (default: yes)
 --demuxer-mkv-probe-video-duration Choices: no yes full (default: no)
 --demuxer-mkv-subtitle-preroll   Choices: no yes index (default: index)
 --demuxer-mkv-subtitle-preroll-secs Double (0 to any) (default: 1.000000)
 --demuxer-mkv-subtitle-preroll-secs-index Double (0 to any) (default: 10.000000)
 --demuxer-rawaudio-channels      Audio channels or channel map (1 to any)
 --demuxer-rawaudio-format        Choices: u8 s8 u16le u16be s16le u16be u24le u24be s24le s24be u32le u32be s32le s32be floatle floatbe doublele doublebe u16 s16 u24 s24 u32 s32 float double (default: s16le)
 --demuxer-rawaudio-rate          Integer (1000 to 384000) (default: 44100)
 --demuxer-rawvideo-codec         String (default: )
 --demuxer-rawvideo-format        FourCC
 --demuxer-rawvideo-fps           Float (0.001 to 1000) (default: 25.000000)
 --demuxer-rawvideo-h             Integer (1 to 8192) (default: 720)
 --demuxer-rawvideo-mp-format     Image format
 --demuxer-rawvideo-size          Integer (1 to 268435456) (default: 0)
 --demuxer-rawvideo-w             Integer (1 to 8192) (default: 1280)
 --demuxer-readahead-secs         Double (0 to any) (default: 1.000000)
 --demuxer-thread                 Flag (default: yes)
 --display-fps                    Double (0 to any) (default: 0.000000)
 --display-tags*                  String list (default: Artist,Album,Album_Artist,Comment,Composer,Genre,Performer,Title,Track,icy-title,service_name)
 --dump-stats                     String (default: ) [global]
 --dvbin-card                     Integer (1 to 4) (default: 1)
 --dvbin-file                     String (default: ) [file]
 --dvbin-full-transponder         Flag (default: no)
 --dvbin-prog                     String (default: )
 --dvbin-timeout                  Integer (1 to 30) (default: 30)
 --dvd-angle                      Integer (1 to 99) (default: 1)
 --dvd-device                     String (default: ) [file]
 --dvd-speed                      Integer (default: 0)
 --edition                        Choices: auto (or an integer) (0 to 8190) (default: auto)
 --embeddedfonts                  Flag (default: yes)
 --end                            Relative time or percent position
 --external-file                  String list (default: ) [file]
 --ff-aid                         Choices: no auto (or an integer) (0 to 8190) (default: auto)
 --ff-sid                         Choices: no auto (or an integer) (0 to 8190) (default: auto)
 --ff-vid                         Choices: no auto (or an integer) (0 to 8190) (default: auto)
 --field-dominance                Choices: auto top bottom (default: auto)
 --force-media-title              String (default: )
 --force-rgba-osd-rendering       Flag (default: no)
 --force-seekable                 Flag (default: no)
 --force-window                   Choices: no yes immediate (default: no)
 --force-window-position          Flag (default: no)
 --fps                            Double (0 to any) (default: 0.000000)
 --framedrop                      Choices: no vo decoder decoder+vo (default: vo)
 --frames                         Choices: all (or an integer) (0 to 2147483647) (default: all)
 --fs                             Flag (default: no)
 --fs-black-out-screens           Flag (default: no)
 --fs-screen                      Choices: all current (or an integer) (0 to 32) (default: current)
 --fullscreen                     Flag (default: no)
 --gamma                          Integer (-100 to 100) (default: 1000)
 --gapless-audio                  Choices: no yes weak (default: weak)
 --geometry                       Window geometry (default: )
 --h                              Print [global] [nocfg]
 --heartbeat-cmd                  String (default: )
 --heartbeat-interval             Float (0 to any) (default: 30.000000)
 --help                           Print [global] [nocfg]
 --hls-bitrate                    Choices: no min max (or an integer) (0 to 2147483647) (default: max)
 --hr-seek                        Choices: no absolute yes always (default: absolute)
 --hr-seek-demuxer-offset         Float (default: 0.000000)
 --hr-seek-framedrop              Flag (default: yes)
 --http-header-fields             String list (default: )
 --hue                            Integer (-100 to 100) (default: 1000)
 --hwdec                          Choices: no auto vdpau videotoolbox vaapi vaapi-copy dxva2-copy rpi (default: no)
 --hwdec-codecs                   String (default: h264,vc1,wmv3,hevc,mpeg2video)
 --hwdec-preload                  Choices: no auto vdpau videotoolbox vaapi vaapi-copy dxva2-copy rpi (default: no)
 --idle                           Choices: no once yes (default: no)
 --ignore-path-in-watch-later-config Flag (default: no)
 --include                        String (default: ) [file]
 --index                          Choices: default recreate (default: default)
 --initial-audio-sync             Flag (default: yes)
 --input-ar-delay                 Integer (default: 200) [global]
 --input-ar-rate                  Integer (default: 40) [global]
 --input-cmdlist                  Print [global] [nocfg]
 --input-conf                     String (default: ) [global] [file]
 --input-cursor                   Flag (default: yes) [global]
 --input-default-bindings         Flag (default: yes) [global]
 --input-doubleclick-time         Integer (0 to 1000) (default: 300)
 --input-file                     String (default: ) [global] [file]
 --input-key-fifo-size            Integer (2 to 65000) (default: 7) [global]
 --input-keylist                  Print [global] [nocfg]
 --input-right-alt-gr             Flag (default: yes) [global]
 --input-terminal                 Flag (default: yes) [global]
 --input-test                     Flag (default: no) [global]
 --input-unix-socket              String (default: ) [file]
 --input-vo-keyboard              Flag (default: yes) [global]
 --input-x11-keyboard             Flag (default: yes) [global]
 --keep-open                      Choices: no yes always (default: no)
 --keepaspect                     Flag (default: yes)
 --keepaspect-window              Flag (default: yes)
 --lavfi-complex                  String (default: )
 --length                         Relative time or percent position
 --list-options                   Flag [nocfg]
 --list-properties                Print [global] [nocfg]
 --list-protocols                 Print [global] [nocfg]
 --load-scripts                   Flag (default: yes) [global]
 --load-unsafe-playlists          Flag (default: no)
 --log-file                       String (default: ) [global] [file]
 --loop                           Choices: no inf yes force (or an integer) (1 to 10000) (default: no)
 --loop-file                      Choices: no yes inf (or an integer) (0 to 10000) (default: no)
 --mc                             Float (0 to 100) (default: -1.000000)
 --merge-files                    Flag (default: no)
 --mf-fps                         Double (default: 1.000000)
 --mf-type                        String (default: )
 --monitoraspect                  Float (0 to 9) (default: 0.000000)
 --monitorpixelaspect             Float (0.2 to 9) (default: 1.000000)
 --msg-color                      Flag (default: yes) [global]
 --msg-level                      Output verbosity levels (default: ) [global]
 --msg-module                     Flag (default: no) [global]
 --msg-time                       Flag (default: no) [global]
 --mute                           Choices: auto no yes (default: auto)
 --native-keyrepeat               Flag (default: no)
 --network-timeout                Double (0 to any) (default: 0.000000)
 --no-audio                       Flag
 --no-sub                         Flag
 --no-video                       Flag
 --no-video-aspect                Flag
 --o                              String (default: ) [global] [nocfg]
 --oac                            String (default: ) [global]
 --oacopts*                       String list (default: ) [global]
 --oafirst                        Flag (default: no) [global]
 --oaoffset                       Float (-1000000 to 1000000) (default: 0.000000) [global]
 --oautofps                       Flag (default: no) [global]
 --ocopyts                        Flag (default: no) [global]
 --of                             String (default: ) [global]
 --ofopts*                        String list (default: ) [global]
 --ofps                           Float (0 to 1000000) (default: 0.000000) [global]
 --oharddup                       Flag (default: no) [global]
 --omaxfps                        Float (0 to 1000000) (default: 0.000000) [global]
 --ometadata                      Flag (default: yes) [global]
 --on-all-workspaces              Flag (default: no)
 --oneverdrop                     Flag (default: no) [global]
 --ontop                          Flag (default: no)
 --orawts                         Flag (default: no) [global]
 --ordered-chapters               Flag (default: yes)
 --ordered-chapters-files         String (default: ) [file]
 --osc                            Flag (default: yes) [global]
 --osd-align-x                    Choices: left center right (default: left)
 --osd-align-y                    Choices: top center bottom (default: top)
 --osd-back-color                 Color
 --osd-bar                        Flag (default: yes)
 --osd-bar-align-x                Float (-1 to 1) (default: 0.000000)
 --osd-bar-align-y                Float (-1 to 1) (default: 0.500000)
 --osd-bar-h                      Float (0.1 to 50) (default: 3.125000)
 --osd-bar-w                      Float (1 to 100) (default: 75.000000)
 --osd-blur                       Float (0 to 20) (default: 0.000000)
 --osd-bold                       Flag (default: no)
 --osd-border-color               Color
 --osd-border-size                Float (0 to 10) (default: 3.000000)
 --osd-color                      Color
 --osd-duration                   Integer (0 to 3600000) (default: 1000)
 --osd-font                       String (default: sans-serif)
 --osd-font-size                  Float (1 to 9000) (default: 55.000000)
 --osd-fractions                  Flag (default: no)
 --osd-level                      Choices: 0 1 2 3 (default: 1)
 --osd-margin-x                   Integer (0 to 300) (default: 25)
 --osd-margin-y                   Integer (0 to 600) (default: 22)
 --osd-msg1                       String (default: )
 --osd-msg2                       String (default: )
 --osd-msg3                       String (default: )
 --osd-playing-msg                String (default: )
 --osd-scale                      Float (0 to 100) (default: 1.000000)
 --osd-scale-by-window            Flag (default: yes)
 --osd-shadow-color               Color
 --osd-shadow-offset              Float (0 to 10) (default: 0.000000)
 --osd-spacing                    Float (-10 to 10) (default: 0.000000)
 --osd-status-msg                 String (default: )
 --ovc                            String (default: ) [global]
 --ovcopts*                       String list (default: ) [global]
 --ovfirst                        Flag (default: no) [global]
 --ovoffset                       Float (-1000000 to 1000000) (default: 0.000000) [global]
 --panscan                        Float (0 to 1) (default: 0.000000)
 --pause                          Flag (default: no)
 --playlist                       String (1 to any) (default: ) [nocfg] [file]
 --playlist-pos                   Choices: no (or an integer) (0 to 2147483647) (default: no)
 --profile                        String list (default: )
 --quiet                          Flag (default: no) [global]
 --really-quiet                   Flag [global]
 --rebase-start-time              Flag (default: yes)
 --referrer                       String (default: )
 --reset-on-next-file             String list (default: ) [global]
 --resume-playback                Flag (default: yes)
 --rtsp-transport                 Choices: lavf udp tcp http (default: tcp)
 --saturation                     Integer (-100 to 100) (default: 1000)
 --save-position-on-quit          Flag (default: no)
 --screen                         Choices: default (or an integer) (0 to 32) (default: default)
 --screenshot-directory           String (default: )
 --screenshot-format              String (default: jpg)
 --screenshot-high-bit-depth      Flag (default: yes)
 --screenshot-jpeg-quality        Integer (0 to 100) (default: 90)
 --screenshot-jpeg-smooth         Integer (0 to 100) (default: 0)
 --screenshot-jpeg-source-chroma  Flag (default: yes)
 --screenshot-png-compression     Integer (0 to 9) (default: 7)
 --screenshot-png-filter          Integer (0 to 5) (default: 5)
 --screenshot-tag-colorspace      Flag (default: no)
 --screenshot-template            String (default: mpv-shot%n)
 --script                         String list (default: ) [global] [file]
 --script-opts                    Key/value list (default: ) [global]
 --secondary-sid                  Choices: no auto (or an integer) (0 to 8190) (default: no)
 --show-profile                   String (default: ) [nocfg]
 --shuffle                        Flag (default: no)
 --sid                            Choices: no auto (or an integer) (0 to 8190) (default: auto)
 --slang                          String list (default: )
 --softvol                        Choices: no yes auto (default: auto)
 --softvol-max                    Float (100 to 1000) (default: 130.000000)
 --speed                          Double (0.01 to 100) (default: 1.000000)
 --sstep                          Double (0 to any) (default: 0.000000)
 --start                          Relative time or percent position
 --stop-playback-on-init-failure  Flag (default: no)
 --stop-screensaver               Flag (default: yes)
 --stream-capture                 String (default: ) [file]
 --stream-dump                    String (default: ) [file]
 --stream-lavf-o                  Key/value list (default: )
 --stretch-dvd-subs               Flag (default: no)
 --stretch-image-subs-to-screen   Flag (default: no)
 --sub-ass                        Flag (default: yes)
 --sub-auto                       Choices: no exact fuzzy all (default: exact)
 --sub-clear-on-seek              Flag (default: no)
 --sub-codepage                   String (default: auto)
 --sub-delay                      Float (default: 0.000000)
 --sub-demuxer                    String (default: )
 --sub-file                       String list (default: ) [file]
 --sub-fix-timing                 Flag (default: yes)
 --sub-forced-only                Flag (default: no)
 --sub-fps                        Float (default: 0.000000)
 --sub-gauss                      Float (0 to 3) (default: 0.000000)
 --sub-gray                       Flag (default: no)
 --sub-paths                      String list (default: )
 --sub-pos                        Integer (0 to 100) (default: 100)
 --sub-scale                      Float (0 to 100) (default: 1.000000)
 --sub-scale-by-window            Flag (default: yes)
 --sub-scale-with-window          Flag (default: yes)
 --sub-speed                      Float (default: 1.000000)
 --sub-text-align-x               Choices: left center right (default: center)
 --sub-text-align-y               Choices: top center bottom (default: bottom)
 --sub-text-back-color            Color
 --sub-text-blur                  Float (0 to 20) (default: 0.000000)
 --sub-text-bold                  Flag (default: no)
 --sub-text-border-color          Color
 --sub-text-border-size           Float (0 to 10) (default: 3.000000)
 --sub-text-color                 Color
 --sub-text-font                  String (default: sans-serif)
 --sub-text-font-size             Float (1 to 9000) (default: 55.000000)
 --sub-text-margin-x              Integer (0 to 300) (default: 25)
 --sub-text-margin-y              Integer (0 to 600) (default: 22)
 --sub-text-shadow-color          Color
 --sub-text-shadow-offset         Float (0 to 10) (default: 0.000000)
 --sub-text-spacing               Float (-10 to 10) (default: 0.000000)
 --sub-use-margins                Flag (default: yes)
 --sub-visibility                 Flag (default: yes)
 --sws-cgb                        Float (0 to 100) (default: 0.000000)
 --sws-chs                        Integer (default: 0)
 --sws-cs                         Float (-100 to 100) (default: 0.000000)
 --sws-cvs                        Integer (default: 0)
 --sws-lgb                        Float (0 to 100) (default: 0.000000)
 --sws-ls                         Float (-100 to 100) (default: 0.000000)
 --sws-scaler                     Choices: fast-bilinear bilinear bicubic x point area bicublin gauss sinc lanczos spline (default: bicubic)
 --term-osd                       Choices: force auto no (default: auto)
 --term-osd-bar                   Flag (default: no)
 --term-osd-bar-chars             String (default: [-+-])
 --term-playing-msg               String (default: )
 --term-status-msg                String (default: )
 --terminal                       Flag (default: yes) [global]
 --title                          String (default: ${?media-title:${media-title}}${!media-title:No file} - mpv)
 --tls-ca-file                    String (default: ) [file]
 --tls-cert-file                  String (default: ) [file]
 --tls-key-file                   String (default: ) [file]
 --tls-verify                     Flag (default: no)
 --tv-adevice                     String (default: )
 --tv-alsa                        Flag (default: no)
 --tv-amode                       Integer (0 to 3) (default: -1)
 --tv-audio                       Flag (default: yes)
 --tv-audioid                     Integer (0 to 9) (default: 0)
 --tv-audiorate                   Integer (default: 44100)
 --tv-automute                    Integer (0 to 255) (default: 0)
 --tv-balance                     Integer (0 to 65535) (default: -1)
 --tv-bass                        Integer (0 to 65535) (default: -1)
 --tv-brightness                  Integer (-100 to 100) (default: 0)
 --tv-buffersize                  Integer (16 to 1024) (default: -1)
 --tv-chanlist                    String (default: europe-east)
 --tv-channel                     String (default: )
 --tv-channels                    String list (default: )
 --tv-contrast                    Integer (-100 to 100) (default: 0)
 --tv-decimation                  Integer (1 to 4) (default: 2)
 --tv-device                      String (default: )
 --tv-driver                      String (default: )
 --tv-forceaudio                  Flag (default: no)
 --tv-forcechan                   Integer (1 to 2) (default: -1)
 --tv-fps                         Float (default: -1.000000)
 --tv-freq                        String (default: )
 --tv-gain                        Integer (-1 to 100) (default: -1)
 --tv-height                      Integer (0 to 4096) (default: -1)
 --tv-hue                         Integer (-100 to 100) (default: 0)
 --tv-immediatemode               Flag (default: yes)
 --tv-input                       Integer (default: 0)
 --tv-mjpeg                       Flag (default: no)
 --tv-norm                        String (default: pal)
 --tv-normid                      Integer (default: -1)
 --tv-outfmt                      FourCC
 --tv-quality                     Integer (0 to 100) (default: 90)
 --tv-saturation                  Integer (-100 to 100) (default: 0)
 --tv-scan-autostart              Flag (default: no)
 --tv-scan-period                 Float (0.1 to 2) (default: 0.500000)
 --tv-scan-threshold              Integer (1 to 100) (default: 50)
 --tv-treble                      Integer (0 to 65535) (default: -1)
 --tv-volume                      Integer (0 to 65535) (default: -1)
 --tv-width                       Integer (0 to 4096) (default: -1)
 --untimed                        Flag (default: no)
 --use-filedir-conf               Flag (default: no)
 --user-agent                     String (default: mpv git-d3f32cb)
 --v                              Flag [global] [nocfg]
 --V                              Print [global] [nocfg]
 --vd                             String (default: )
 --vd-lavc-bitexact               Flag (default: no)
 --vd-lavc-check-hw-profile       Flag (default: yes)
 --vd-lavc-fast                   Flag (default: no)
 --vd-lavc-framedrop              Choices: none default nonref bidir nonkey all (default: nonref)
 --vd-lavc-o                      Key/value list (default: )
 --vd-lavc-show-all               Flag (default: no)
 --vd-lavc-skipframe              Choices: none default nonref bidir nonkey all (default: default)
 --vd-lavc-skipidct               Choices: none default nonref bidir nonkey all (default: default)
 --vd-lavc-skiploopfilter         Choices: none default nonref bidir nonkey all (default: default)
 --vd-lavc-software-fallback      Choices: no yes (or an integer) (1 to 2147483647) (default: 3)
 --vd-lavc-threads                Integer (0 to any) (default: 0)
 --version                        Print [global] [nocfg]
 --vf*                            Object settings list (default: )
 --vf-defaults                    Object settings list (default: )
 --vid                            Choices: no auto (or an integer) (0 to 8190) (default: auto)
 --video-align-x                  Float (-1 to 1) (default: 0.000000)
 --video-align-y                  Float (-1 to 1) (default: 0.000000)
 --video-aspect                   Float (-1 to 10) (default: -1.000000)
 --video-aspect-method            Choices: hybrid bitstream container (default: hybrid)
 --video-output-levels            Choices: auto limited full (default: auto)
 --video-pan-x                    Float (-3 to 3) (default: 0.000000)
 --video-pan-y                    Float (-3 to 3) (default: 0.000000)
 --video-rotate                   Choices: no (or an integer) (0 to 359) (default: 0)
 --video-stereo-mode              Choices: no mono sbs2l ab2r ab2l checkr checkl irr irl icr icl arcc sbs2r agmc al ar (default: mono)
 --video-sync                     Choices: audio display-resample display-resample-vdrop display-resample-desync display-adrop display-vdrop display-desync desync (default: audio)
 --video-sync-adrop-size          Double (0 to 1) (default: 0.020000)
 --video-sync-max-audio-change    Double (0 to 1) (default: 0.125000)
 --video-sync-max-video-change    Double (0 to any) (default: 1.000000)
 --video-unscaled                 Flag (default: no)
 --video-zoom                     Float (-20 to 20) (default: 0.000000)
 --vo                             Object settings list (default: )
 --vo-defaults                    Object settings list (default: )
 --volume                         Float (-1 to 1000) (default: -1.000000)
 --volume-restore-data            String (default: )
 --wid                            Integer64 (default: -1)
 --window-dragging                Flag (default: yes) [global]
 --window-scale                   Float (0.001 to 100) (default: 1.000000)
 --write-filename-in-watch-later-config Flag (default: no)
 --x11-bypass-compositor          Flag (default: yes)
 --x11-name                       String (default: )
 --x11-netwm                      Choices: auto no yes (default: auto)
 --ytdl                           Flag (default: yes) [global]
 --ytdl-format                    String (default: ) [global]
 --ytdl-raw-options               Key/value list (default: ) [global]
 --{                              Flag [nocfg]
 --}                              Flag [nocfg]

Total: 452 options




```

===============

Still for me the best video player not used any other in 2 years

i use

```

--fs
--resume-playback
--save-position-on-quit
--screenshot-template=/media/extradrive/home/shantiq/Pictures/mpv/%F&#9755;%n
--screenshot-format=png
--screenshot-png-compression=9
--sub-text-back-color=0.9/1.0/0.25
```

--fs is fullscreen   and i love my yellow-boxed subs :] and to maximize quality of screenshots      //          so many options ...

---

### Post by mc4man on 2016-05-08
> **shantiq said:**
> hi there is you want position saved  [will automatically play best quality]>>


enter

```
--save-position-on-quit
```

in a text document called [may need to be created] so:

```
[COLOR="#FF0000"]sudo[/COLOR] gedit  ~/.config/mpv/mpv.conf
```



Generally in mpv.conf -- isn't needed, may (still) be some options where it's a hindrance. Also to note that is a user config file, don't use sudo on.

OT. - a useful lua script - [https://github.com/Argon-/mpv-stats/](https://github.com/Argon-/mpv-stats/)

---

### Post by shantiq on 2016-05-08
hmmm mc   funny   it would not let me save before i used sudo

[ATTACH=CONFIG]268922[/ATTACH]   and therefore i suggested one did but might be different on different setups :]

---

### Post by mc4man on 2016-05-08
> **shantiq said:**
> hmmm mc   funny   it would not let me save before i used sudo

[ATTACH=CONFIG]268922[/ATTACH]   and therefore i suggested one did but might be different on different setups :]
Maybe ownership of that file or directory got changed, if you open a terminal at normal prompt what's this show (doesn't matter if any files have root in name, looking for owner
```
ls -lA -R |grep root
```

---

### Post by shantiq on 2016-05-09
hi again mc   ths is the outcome

```
ls -lA -R |grep root
drwx------  2 root    root          4096 Feb 28  2015 .gvfs
-rw-r--r--  1 root    root           105 Feb 27  2015 .inputrc
-rw-r--r--  1 shantiq root          7460 Jun 23  2015 radios
drwxr-xr-x  2 root    root          4096 Mar 13 08:03 .rpmdb
drwx------  2 root    root     4096 Apr  6 14:17 dconf
ls: cannot open directory ./.cache/dconf: Permission denied
drwx------  2 shantiq root     4096 Jun 20  2015 leafpad
-rwxrwxrwx 1 shantiq root 34 May  8 20:04 leafpadrc
**-rw-r--r-- 1 root    root      210 May  8 08:31 mpv.conf**
ls: cannot open directory ./.gvfs: Permission denied


```


so changed it now

```
sudo chown shantiq mpv.conf 

giving me
-rw-r--r-- 1 shantiq root      217 May  9 05:58 mpv.conf




```   and therefore no need for sudo anymore

do not know what the OP will find on his setup ....   :]

---

### Post by mc4man on 2016-05-09
> **shantiq said:**
> hi again mc   this is the outcome
...

You should try to avoid using sudo <a gui app>. If need be go - 
sudo -H <app>

---

