---
title: "Help please with mp3splt output file format."
date: 2016-08-09
forum: Multimedia Software
---

### Post by ron998 on 2016-08-09
Hi

This one for 1 hour splits.
```
mp3splt -t 60.0 foo.ogg
```

When I split a long file foo.ogg into 1 hour sections the result is like this...
> foo_000m_00s__060m_00s.ogg
foo_060m_00s__120m_00s.ogg
foo_120m_00s__180m_00s.ogg
foo_180m_00s__183m_15s_20h.ogg

There's some information about the output file format in ```
mp3splt -h
```
> -o + FORMAT: output filename pattern. Can contain those variables:
      @a: artist tag, @p: performer tag (might not exists), @b: album tag
      @t: title tag, @n: track number identifier, @N: track tag number
      (a digit may follow the 'n' or 'N' for the number of digits to output),
      @f: original filename, @g: genre

Is it possible to use this information to number the output files more sane?
For example...
> 1_foo.ogg
2_foo.ogg
3_foo.ogg
etc

Or
> 01_foo.ogg
02_foo.ogg
03_foo.ogg
etc

Or
> 00_foo.ogg
01_foo.ogg
02_foo.ogg
etc

---

### Post by coldraven on 2016-08-09
I just experimented with splitting a six minute track into 60 second chunks. Hope that helps :)
```

mp3splt -t 01.00 -o @n_@f foo.mp3

mp3splt 2.4.2 (13/05/12) - using libmp3splt 0.7.2
    Matteo Trotta <mtrotta AT users.sourceforge.net>
    Alexandru Munteanu <io_fx AT yahoo.fr>
THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK!
 Processing file 'foo.mp3' ...
 info: file matches the plugin 'mp3 (libmad)'
 info: found Xing or Info header. Switching to frame mode... 
 info: MPEG 1 Layer 3 - 44100 Hz - Joint Stereo - FRAME MODE - Total time: 5m.31s
 info: starting time mode split
   File "1_foo.mp3" created                   
   File "2_foo.mp3" created                   
   File "3_foo.mp3" created                   
   File "4_foo.mp3" created                   
   File "5_foo.mp3" created                   
   File "6_foo.mp3" created                   
 Processed 12697 frames - Sync errors: 0
 time split ok



```

---

### Post by ron998 on 2016-08-09
> **coldraven said:**
> ... Hope that helps...
Yes, that's done the job. Thanks. :)

```
@Xubuntu:~$ mp3splt -t 60.0 -o @n_@f foo.ogg
mp3splt 2.4.2 (13/05/12) - using libmp3splt 0.7.2
    Matteo Trotta <mtrotta AT users.sourceforge.net>
    Alexandru Munteanu <io_fx AT yahoo.fr>
THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK!
 Processing file 'foo.ogg' ...
 info: file matches the plugin 'ogg vorbis (libvorbis)'
 info: Ogg Vorbis Stream - 48000 - 125 Kb/s - 2 channels - Total time: 183m.15s
 info: starting time mode split
   File "1_foo.ogg" created                   
   File "2_foo.ogg" created                   
   File "3_foo.ogg" created                   
   File "4_foo.ogg" created                  
libmp3splt: error in splt_sp_set_splitpoint_value with value 152171064
libmp3splt: error in splt_sp_set_splitpoint_value with value 151983120
libmp3splt: error in splt_sp_set_splitpoint_value with value 152170992
libmp3splt: error in splt_sp_set_splitpoint_value with value 151983352
 time split ok

```

> 1_foo.ogg
2_foo.ogg
3_foo.ogg
4_foo.ogg

PS
Those error messages showed up before, but I haven't found anything wrong with the created files (yet).:confused:

---

### Post by ron998 on 2016-08-09
PPS
I've updated to a later version and the errors have gone.:)
(From here ---> [http://mp3splt.sourceforge.net/mp3splt_page/debian_downloads.php?version=Trusty&ubuntu=true](http://mp3splt.sourceforge.net/mp3splt_page/debian_downloads.php?version=Trusty&ubuntu=true))


```
@Xubuntu:~$ mp3splt -t 60.0 -o @n_@f foo.ogg
mp3splt 2.6.2 (09/11/14) - using libmp3splt 0.9.2
    Matteo Trotta <mtrotta AT users.sourceforge.net>
    Alexandru Munteanu <m AT ioalex.net>
THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK!
 Processing file 'foo.ogg' ...
 info: file matches the plugin 'ogg vorbis (libvorbis)'
 info: Ogg Vorbis Stream - 48000 - 125 Kb/s - 2 channels - Total time: 183m.15s
 info: starting time mode split
   File "1_foo.ogg" created                   
   File "2_foo.ogg" created                   
   File "3_foo.ogg" created                   
   File "4_foo.ogg" created                  
 time split ok

```

---

### Post by coldraven on 2016-08-09
You know that learning new stuff is a two way process. I'm glad that I could help because I learned something new, please mark as solved.

---

