---
title: "anybody compile amarok for x64 8.04 heron?"
date: 2009-05-28
forum: Multimedia Software
---

### Post by logos34 on 2009-05-28
getting make errors...what besides apt-get build-dep amarok do you need to install?

using this line
> 
./configure --prefix=`kde-config --prefix` --enable-mysql --enable-postgresql --without-arts --without-gstreamer --with-libmtp --with-mp4v2 --with-libgpod

looks good for make, but latter complains about sqlite3 (I have the -dev files installed), then dies with 
> 
/src/magnatunebrowser/libmagnatunebrowser.la -lkutils -lkio -lkdeui -lkdecore -lkhtml -lknewstuff -ltag   -lGL  ../../amarok/src/sqlite/libsqlite.la -ltunepimp -Wl,-Bsymbolic-functions -L/usr/lib/mysql -lmysqlclient -L/usr/lib -lpq 
/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make[4]: *** [libamarok.la] Error 1
make[4]: Leaving directory `/home/logos34/amarok-1.4.9.1/amarok/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/logos34/amarok-1.4.9.1/amarok/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/logos34/amarok-1.4.9.1/amarok'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/logos34/amarok-1.4.9.1'
make: *** [all] Error 2
logos34@ubuntu:~/amarok-1.4.9.1$ 

ideas anyone?

---

### Post by logos34 on 2009-05-28
apparently the 

> /usr/bin/ld: cannot find -lGL

refers to opengl lib...tried '--without-opengl' and I get past the error only to land at another '-lffi' (libgpod?)...Trying again right now without ipod support (don't really need it), hope it works

several of the -mesa dev pkgs alluded to conflict with libgl-dev on mine, which should have provided the necessary files

---

### Post by mc4man on 2009-05-29
Just curious as to the reason to build amarok for hardy, is there anything to be gained?

---

### Post by logos34 on 2009-05-29
well, I got it to compile, but it doesn't solve the problem I hoped it would: gapless playback of ogg.  It's still inserting a brief moment of silence between tracks (very annoying on live albums)...I thought there was a chance, however slim, that the embedded version of amarok-xine engine it built would fix it, but alas it was not to be...The problem lies deeper, probably somewhere in libxine1...And I'm not about to try to compile THAT from source...

forget it, life's too short, audacious or moc player will do for gapless output

---

### Post by logos34 on 2009-05-29
> **mc4man said:**
> Just curious as to the reason to build amarok for hardy, is there anything to be gained?

just saw you post after finishing mine above

---

### Post by logos34 on 2009-05-29
mc4man,

oh, and amarok no longer opens up the artist or album wiki page in the side pane/context view (athough it will open it up in external browser).  Couple of other minor issues...it's just too much of a hassle to worry about it any longer..I tried the ppa version of amarok 1.4.9.3.2 (?) on launchpad (almost exactly the same as the medibunut I was using)..no improvement...

thanks again for the wmap mplayer patch and all the help... I was really nice to get it working to full capability, or close to it.

---

### Post by mc4man on 2009-05-29
libxine1 is part of xine-libs which is pretty sraightfoward to build, though I don't think what your looking for is something that can be configured in.

I tend to just have live stuff extracted  from dvd's which playback without gaps. If it's cd's your using too bad that they aren't produced as 'gapless' like a very few I have.

I do have a few live concert cd's, will have to try. I built these on my new hardy, though I wouldn't expect that would change anything as far as gapless

> libxine1_1.1.16.3-0ubuntu1_i386.deb
libxine1-bin_1.1.16.3-0ubuntu1_i386.deb
libxine1-console_1.1.16.3-0ubuntu1_i386.deb
libxine1-x_1.1.16.3-0ubuntu1_i386.deb
libxine1-dbg_1.1.16.3-0ubuntu1_i386.deb
libxine1-doc_1.1.16.3-0ubuntu1_all.deb
libxine1-ffmpeg_1.1.16.3-0ubuntu1_i386.deb
libxine1-gnome_1.1.16.3-0ubuntu1_i386.deb
libxine1-misc-plugins_1.1.16.3-0ubuntu1_i386.deb
libxine1-plugins_1.1.16.3-0ubuntu1_all.deb
libxine-dev_1.1.16.3-0ubuntu1_i386.deb
libxvmc1_2%3a1.0.4-2ubuntu1_i386.deb

---

### Post by logos34 on 2009-05-29
> **mc4man said:**
> ...I don't think it's a 64-bit issue (as is, say, the inability to import .m3u playlist and .cue). 

well, I found that's wrong...it CAN import .m3u playlists, as long as the tracklist paths are correct! If not, it refuses to open

---

