---
title: "How to screencast Unity8/MIR"
date: 2014-11-15
forum: Multimedia Software
---

### Post by pixelro on 2014-11-15
[COLOR=#404040][FONT=Roboto]use mirscreencast to record, mirscreencast --help (for help, doh)[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]by default records at 60FPS raw video (this will kill your HDD and maybe even your SSD) so you can use --cap-interval 3 to record at display rate/3 = 20FPS in my case
[/FONT][/COLOR]also you can record at "half" your resolution -s width height 

[COLOR=#404040][FONT=Roboto]ex: mirscreencast -f recorded.raw -m /run/lightdm-mir-0 -s 680 384 --cap-interval 3 [/FONT][/COLOR]

[COLOR=#404040][FONT=Roboto]to view the raw video use vlc[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]vlc --demux rawvideo --rawvid-fps 20 --rawvid-width 680 --rawvid-height 384 --rawvid-chroma=RV32 --rawvid-aspect-ratio 16:9 recorded.raw[/FONT][/COLOR]

[COLOR=#404040][FONT=Roboto]you can also use vlc to covert raw video to mp4[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]mir is on tty8
[/FONT][/COLOR][COLOR=#404040][FONT=Roboto]
the result here, Ubuntu NEXT 15.04 [/FONT][/COLOR][COLOR=#404040][FONT=Roboto]680x384@20FPS [http://www.youtube.com/watch?v=h1LO6hjvSPc](http://www.youtube.com/watch?v=h1LO6hjvSPc)[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]HAVE FUN! [/FONT][/COLOR]):P

---

### Post by pixelro on 2014-11-18
progress! :popcorn: windowing system by [Michael Zanetti]("https://launchpad.net/~mzanetti") [https://code.launchpad.net/~mzanetti/unity8/desktop-stage/+merge/242140](https://code.launchpad.net/~mzanetti/unity8/desktop-stage/+merge/242140)
[video=youtube;S7VzufzHOdk]http://www.youtube.com/watch?v=S7VzufzHOdk[/video]

---

### Post by s.fox on 2014-11-19
Not really appropriate for the Cafe so have moved the thread to Multimedia.

---

