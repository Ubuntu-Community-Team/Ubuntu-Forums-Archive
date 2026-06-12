---
title: "Mythmusic - Compile error - Please help"
date: 2009-04-20
forum: Multimedia Software
---

### Post by staverts on 2009-04-20
I am trying to compile mythplugins, in praticular Mythmusic, all dependencies are met:

 MythArchive    plugin will be built
        MythBrowser    plugin will be built
        MythControls   plugin will be built
        MythFlix       plugin will be built
        MythGallery    plugin will be built
        MythGame       plugin will be built
        MythMusic      plugin will be built
        MythNews       plugin will be built
        MythPhone      plugin will be built
        MythVideo      plugin will be built
        MythWeather    plugin will be built
        MythZoneMinder plugin will be built
        MythMovies     plugin will be built
        DVD creation   support will be included in MythArchive
        Native Archive support will be included in MythArchive
        OpenGL         support will be included in MythGallery
        EXIF           support will be included in MythGallery
        OpenGL         support will be included in MythMusic
        libvisual      support will not be included in MythMusic
        FFTW           support will not be included in MythMusic
        SDL            support will not be included in MythMusic
        AAC            support will not be included in MythMusic
        FESTIVAL       support will not be included in MythPhone

Then I do the make, and it fails with there errors, it fails on myth music with something to do with the cddecoder.cpp..I think:

e/qt3 -I/usr/X11R6/include -o cddecoder.o cddecoder.cpp
In file included from cddecoder.h:15,
                 from cddecoder.cpp:10:
/usr/local/include/cdda_interface.h:87: error: expected unqualified-id before ‘private’
/usr/local/include/cdda_interface.h:87: error: expected ‘;’ before ‘private’
cddecoder.cpp: In member function ‘virtual void CdDecoder::commitMetadata(Metadata*)’:
cddecoder.cpp:517: warning: comparison with string literal results in unspecified behaviour
make[2]: *** [cddecoder.o] Error 1
make[2]: Leaving directory `/usr/src/mythplugins/mythmusic/mythmusic'
make[1]: *** [sub-mythmusic] Error 2
make[1]: Leaving directory `/usr/src/mythplugins/mythmusic'
make: *** [sub-mythmusic] Error 2

Any help with this would be GREATLY appreciated.

---

### Post by inobe on 2009-04-20
i really cant help with that' but hope that this site will.

[http://www.avenard.org/media/Home.html](http://www.avenard.org/media/Home.html)

that fella keeps a lot of precompiled applications and you can add the repo to synaptic.

[http://www.avenard.org/files/ubuntu-repos/](http://www.avenard.org/files/ubuntu-repos/)

---

### Post by staverts on 2009-04-20
Unfortunately, I really need to compile it, as my Mythtv is compiled for DVB support, so the plugins must be compiled as well, plus, I like the extended options I can choose with self compiling.  If there is anyone else who can help, I would greatly appreciate it.

---

