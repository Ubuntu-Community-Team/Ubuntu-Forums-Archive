---
title: "firefox plugin to play mid files"
date: 2006-10-05
forum: Multimedia &amp; Video
---

### Post by cccc on 2006-10-05
hi

howto install firefox plugin to play midi sound files:

[http://jarnet2.net/kartki/upload/help.php?topic=music&song=http://jarnet2.net/kartki/upload/music/51.mid](http://jarnet2.net/kartki/upload/help.php?topic=music&song=http://jarnet2.net/kartki/upload/music/51.mid)

---

### Post by cccc on 2006-10-06
this problem is solved now:

1.) install timidity

2.) get sound patches: 

[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Three_Steps_to_MIDI_on_Linux](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Three_Steps_to_MIDI_on_Linux)

[http://gentoo.mirrors.pair.com/distfiles/eawpats12_full.tar.gz](http://gentoo.mirrors.pair.com/distfiles/eawpats12_full.tar.gz)

3.) replace /etc/timidity.cfg

4.) install mozplugger

5.) change in /etc/mozpluggerrc from:```
controls noisy stream: timidity -Od "$file"
```
to:```
controls noisy stream: timidity "$file"
```

and that's it !

greetings
cccc

---

