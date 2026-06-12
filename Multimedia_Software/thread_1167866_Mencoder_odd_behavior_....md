---
title: "Mencoder odd behavior ..."
date: 2009-05-23
forum: Multimedia Software
---

### Post by walterp98@gmail.com on 2009-05-23
Hello ...

I used the following scripts to convert some .avi files to .mpg files (attribute to someone on the 'net ... can't remember who), but when I try to author them with Tmpgenc Authoring Works 4, it insists on re-encoding them and it doubles the filesize.  The files start as xvid 512x384 and I'm doing as little as possible with mencoder.

I opened one of the resulting .mpg files with bitrateviewer (found a link on afterdawn) and it reported my average bitrate was 2484 with a peak of 9894

Qdvdauthor and Todisc are not options for me right now since I'm running an Athlon, and those tools choke when using something to create the menus.  I can author with dvdauthor and xml, but can't get menus.  I've not yet tried devede (sp?).

This code is executed in a for loop:
```

      nice 19 mencoder "$file" \
       -msglevel all=2 \
       -of mpeg \
       -oac lavc -ovc lavc \
       -lavcopts acodec=ac3:abitrate=384:vcodec=mpeg2video:vbitrate=3200:vpass=1 \
       -mpegopts format=mpeg2:tsaf \
       -srate 48000 -ofps 30000/1001 \
       -o /dev/null 2>> $destDir/stderr.txt >> $destDir/stdout.txt

      nice 19 mencoder "$file" \
       -msglevel all=2 \
       -of mpeg \
       -oac lavc -ovc lavc \
       -lavcopts acodec=ac3:abitrate=384:vcodec=mpeg2video:vbitrate=3200:vpass=2 \
       -mpegopts format=mpeg2:tsaf \
       -srate 48000 -ofps 30000/1001 \
       -o $destDir/${file%%avi}mpg 2>> $destDir/stderr.txt >> $destDir/stdout.txt

```I'd really prefer to stay with this tool, because with my configuration, I'm getting 95-100 fps encoding speed, whereas tmpgenc express on XP gives me about 30.

Am I doing something wrong or is this a possible bug in mencoder?

Thanks in advance for your help.

Walter

---

