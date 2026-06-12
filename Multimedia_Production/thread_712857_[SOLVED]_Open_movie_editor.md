---
title: "[SOLVED] Open movie editor"
date: 2008-03-02
forum: Multimedia Production
---

### Post by Creative2 on 2008-03-02
Well i have used maybe most of editing software on linux

i think the open movie editor is really nice i think the best

-easy 
-practical 
-support many formats 
-with nice effects
fade in fade out 
-easy photo--to movie 

really well made

unluckly i think i have installed bad becasue i see i can't export file correctly i am pretty sure i have some problem but i can't find a nice debian package for that software , on repository there is an old version with no effects so...

anyone can post a step by step procedure to install it correctly?
i know there is some issue on jack 
i know this 
[http://pastie.caboo.se/113576](http://pastie.caboo.se/113576)
but it doesn't work for me it said it said i have not openmovieeditor package...ok that i have fixed...
now i get this error on make 


AudioFileFfmpeg.o: In function `AudioFileFfmpeg':
/home/Sbucatone/openmovieeditor-0.0.20080209/openmovieeditor-0.0.20080209/src/AudioFileFfmpeg.cxx:36: undefined reference to `av_find_input_format'
/home/Sbucatone/openmovieeditor-0.0.20080209/openmovieeditor-0.0.20080209/src/AudioFileFfmpeg.cxx:38: undefined reference to `av_open_input_file'
/home/Sbucatone/openmovieeditor-0.0.20080209/openmovieeditor-0.0.20080209/src/AudioFileFfmpeg.cxx:42: undefined reference to `av_find_stream_info'
/home/Sbucatone/openmovieeditor-0.0.20080209/openmovieeditor-0.0.20080209/src/AudioFileFfmpeg.cxx:59: undefined reference to `avcodec_find_decoder'
/home/Sbucatone/openmovieeditor-0.0.20080209/openmovieeditor-0.0.20080209/src/AudioFileFfmpeg.cxx:64: undefined reference to `avcodec_open'
collect2: ld returned 1 exit status
make[3]: *** [openmovieeditor] Error 1
make[3]: Leaving directory `/home/Sbucatone/openmovieeditor-0.0.20080209/openmovieeditor-0.0.20080209/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/Sbucatone/openmovieeditor-0.0.20080209/openmovieeditor-0.0.20080209/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/Sbucatone/openmovieeditor-0.0.20080209/openmovieeditor-0.0.20080209'
make: *** [all] Error 2

---

### Post by Creative2 on 2008-03-03
solved , i have compiled ffmpeg so i have not enalge  --enable-shared, recompiled with that and :D it just works 

 [http://propirate.net/oracle/archives/2007/10/19/open-movie-editor-weekly-news-6/](http://propirate.net/oracle/archives/2007/10/19/open-movie-editor-weekly-news-6/)
 
[http://www.youtube.com/watch?v=9ljEb1PdEdM](http://www.youtube.com/watch?v=9ljEb1PdEdM)

---

### Post by philc on 2008-03-04
I'm glad you solved this.

The OME Forum is a good place to check for bugs and resolutions. 

[http://www.openmovieeditor.org/board/](http://www.openmovieeditor.org/board/)

Richard, lead developer, answers queries posted there quite quickly.

Edit: which I now see you already did...

---

