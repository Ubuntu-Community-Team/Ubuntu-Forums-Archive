---
title: "Problems converting .MTS to .AVI [UBUNTU 14.04 LTS]"
date: 2014-06-20
forum: Multimedia Software
---

### Post by hervasiop12345 on 2014-06-20
Hello guys.

I'm trying to convert a file .mts to .avi using the program ffmpeg but the execution fails.
I'm following the steps of this tutorial: [http://www.tatblog.net/2012/02/convertir-videos-mts-a-avi-en-gnulinux/](http://www.tatblog.net/2012/02/convertir-videos-mts-a-avi-en-gnulinux/)
The command used is:

ffmpeg -i Nombre_del_fichero.MTS -vcodec libxvid -b 12000k -acodec  libmp3lame -ac 2 -ab 256k -deinterlace -s 1440x1080  Nombre_del_fichero_de_salida.AVI

The errors ocurred are: 

Please use -b:a or -b:v, -b is ambiguous 
Unknown encoder 'libxvid'

Thanks.

---

### Post by ajgreeny on 2014-06-20
Here is a command I used in the past to convert to mpg, not avi, but assuming things have not changed now, it may give you some idea about your problem.  Note that my command shows **-codec:a** and **-codec:v**, and also, as suggested in your error, mine shows **-b:a 192k** not just **-b 12000k**.

I am no ffmpeg expert and now always use avconv instead, which is now the Ubuntu default.

```
ffmpeg -i file.mkv -codec:v mpeg2video -codec:a mp2 -qscale:v 2 -b:a 192k -ac 2 output.mpg
```

---

### Post by andrew.46 on 2014-06-20
Perhaps this:

```

ffmpeg -i Nombre_del_fichero.MTS \
       -c:v mpeg4 -q:v 5 -vtag XVID \
       -vf "yadif=0:-1:0,scale=1440:-1"\
       -f avi -mbd rd -flags +mv4+aic -trellis 2 -cmp 2 -subcmp 2 -g 300 \
       -c:a libmp3lame -ac 2 -ab 256k \
       Nombre_del_fichero_de_salida.AVI

```

You would be best to quote the full command line and terminal output of FFmpeg to get a more informed response...

**Edit:** The yadif options:**[COLOR="#FF0000"] 0:-1:0[/COLOR]** are actually* the defaults* but I guess it does not hurt to see them in the command line.

---

