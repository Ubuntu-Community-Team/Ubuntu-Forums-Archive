---
title: "how to install codecs in mplayer"
date: 2009-04-30
forum: Multimedia Software
---

### Post by lgfish on 2009-04-30
so there's this quicktime file that is being a pain in the *** when i try to play it.  it plays in mplayer and vlc and sort of in kaffeine, but i can't fast forward, or skip around, or anything.  i figure i must be missing a codec.  ok so i went here - [http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)  and there are some nifty
codec packages.  i assume i want the top one listed there.. so i download it and check out the readme.  the readme says

>      Put the files contained in this archive in a directory where MPlayer will find them. The default directory is /usr/local/lib/codecs/ ($prefix/lib/codecs/) if you are compiling from source, but you can change that value by passing the '--with-codecsdir' option to './configure'.

    If you use a prebuilt MPlayer package it will most likely be /usr/lib/codecs, see the documentation of your package for details. 

    In the past /usr/local/lib/win32 or /usr/lib/win32 was the default directory, some packages as well as a few other Unix players like xine and avifile still use it, refer to their documentation for further details. 


which leaves me with a couple of questions 

1) do i just drop these files in? or do they need to be compiled (and if so, how?)

and 2) neither of those locations has the codecs on my mplayer installation.  It seems like my installation has the codecs here : /usr/share/doc/mplayer/examples   or, maybe i'm not even asking the question properly.  

I started down the path of looking for additional codecs b/c i got an error message (see attached image) when running kaffeine for the first time. 
  
I'm running intrepid.  any help much appreciated!

---

### Post by binbash on 2009-04-30
they do not need compiling.you will just extract it.

Why don't you add medibuntu repository to your list and install w32codecs (or w64codecs) ?

PS : you will extract it to /usr/lib/win32

---

