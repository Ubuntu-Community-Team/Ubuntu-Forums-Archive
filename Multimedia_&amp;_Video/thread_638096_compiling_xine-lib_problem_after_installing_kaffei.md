---
title: "compiling xine-lib problem after installing kaffeine8.5"
date: 2007-12-11
forum: Multimedia &amp; Video
---

### Post by Mo9a7i on 2007-12-11
[LEFT][COLOR=Black][B]I'm really really disparate guyz:(


[COLOR=Red] providing all the facts:[/COLOR]
1-installed kaffeine very well with skystar card! (Worked fine , watched channels , it was ok):popcorn:


2- tried to install sc-plugin for kaffeine ,,
          facing some problems with the linux-headers i managed to fix problems by providing
          the absolute  path to the directories of (asm) and (linux)..



3- the plugin was installed properly with kaffeine ,, i managed to see it in the dvb plugins section..
      i tried to open one of the channels (that used to work)

i started facing this problem :
[IMG]http://www.mo9a7i.com/Screenshot-Error%20-%20Kaffeine%20Player.png[/IMG]
'XinePart' failed



4- after googling and searching all over the www ,, all what i came with is that the xine-lib should be
    re-installed ,, i tried reinstalling it using synaptic ,, the same problem existed
    tried un-installing xine-lib and kaffiene and removing their config dir's ,, that didn't work either



5- downloaded the source code of the neweset xine-lib from _[COLOR=Blue]http://xinehq.de/index.php[/COLOR]_



6- ./configure works like a charm



7. make started to exit with this error[/B][/COLOR] :      

```
media_helper.c:47:2: warning: #warning "This might not compile due to missing cdrom ioctls"
media_helper.c: In function 'media_eject_media':
media_helper.c:107: error: 'CDROM_DRIVE_STATUS' undeclared (first use in this function)
media_helper.c:107: error: (Each undeclared identifier is reported only once
media_helper.c:107: error: for each function it appears in.)
media_helper.c:107: error: 'CDSL_CURRENT' undeclared (first use in this function)
media_helper.c:109: error: 'CDS_TRAY_OPEN' undeclared (first use in this function)
media_helper.c:110: error: 'CDROMCLOSETRAY' undeclared (first use in this function)
media_helper.c:116: error: 'CDS_DISC_OK' undeclared (first use in this function)
media_helper.c:117: error: 'CDROMEJECT' undeclared (first use in this function)
make[3]: *** [xineplug_inp_dvd_la-media_helper.lo] Error 1
make[3]: Leaving directory `/home/mo9a7i/Desktop/hey/xine-lib-1.1.8/src/input'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/mo9a7i/Desktop/hey/xine-lib-1.1.8/src/input'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/mo9a7i/Desktop/hey/xine-lib-1.1.8/src'
make: *** [install-recursive] Error 1
mo9a7i@Mo9a7i-laptop-ubuntu:~/Desktop/hey/xine-lib-1.1.8$ 


```




[B][COLOR=Black] i tried searching for anything near to cd rom ioctles ,, came up with nothing 
please please people i'm begging you ,, help me fix this :confused:[/COLOR][/B] [/LEFT]

---

### Post by Mo9a7i on 2007-12-14
Please Guyz ??
I'm begging you !

---

