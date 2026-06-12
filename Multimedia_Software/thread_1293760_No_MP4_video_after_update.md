---
title: "No MP4 video after update"
date: 2009-10-17
forum: Multimedia Software
---

### Post by ezacon on 2009-10-17
I am running Ubuntu 9.04/64. Yesterday, during an update i get this error:
```
E: /var/cache/apt/archives/libavcodec-extra-52_4%3a0.5+svn20090924-0ubuntu0~ppa1_amd64.deb: intentando sobreescribir `/usr/lib/libavcodec.so.52', que está también en el paquete libavcodec-unstripped-52

```
After running "apt-get upgrade" in console window, the failing packages configures without error.
At this time, i can no longer play MP4 (Divx encoded AVI files). i get audio but no video, vith any player (VLC, Kafeine etc...)

This is the APT log from the update failure:
```
/var/log/apt/term.log

Log started: 2009-10-16  18:56:42
Seleccionando el paquete libavutil-extra-49 previamente no seleccionado.
(Leyendo la base de datos ...
251091 ficheros y directorios instalados actualmente.)
Desempaquetando libavutil-extra-49 (de .../libavutil-extra-49_4%3a0.5+svn20090924-0ubuntu0~ppa1_amd64.deb) ...
Seleccionando el paquete libdirac0c2a previamente no seleccionado.
Desempaquetando libdirac0c2a (de .../libdirac0c2a_1.0.2-0ubuntu1_amd64.deb) ...
Seleccionando el paquete libopenjpeg2 previamente no seleccionado.
Desempaquetando libopenjpeg2 (de .../libopenjpeg2_1.3+dfsg-3_amd64.deb) ...
Seleccionando el paquete libx264-67 previamente no seleccionado.
Desempaquetando libx264-67 (de .../libx264-67_1%3a0.svn20090924-0ubuntu0~ppa1_amd64.deb) ...
Seleccionando el paquete libavcodec-extra-52 previamente no seleccionado.
Desempaquetando libavcodec-extra-52 (de .../libavcodec-extra-52_4%3a0.5+svn20090924-0ubuntu0~ppa1_amd64.deb) ...
dpkg: error al procesar /var/cache/apt/archives/libavcodec-extra-52_4%3a0.5+svn20090924-0ubuntu0~ppa1_amd64.deb (--unpack):
 intentando sobreescribir `/usr/lib/libavcodec.so.52', que está también en el paquete libavcodec-unstripped-52
Preparando para reemplazar ffmpeg 3:0.svn20090303-1ubuntu6 (usando .../ffmpeg_4%3a0.5+svn20090924-0ubuntu0~ppa2_amd64.deb) ...
Desempaquetando el reemplazo de ffmpeg ...
Preparando para reemplazar libavdevice52 3:0.svn20090303-1ubuntu6 (usando .../libavdevice52_4%3a0.5+svn20090924-0ubuntu0~ppa2_amd64.deb) ...
Desempaquetando el reemplazo de libavdevice52 ...
Preparando para reemplazar libavformat52 3:0.svn20090303-1ubuntu6 (usando .../libavformat52_4%3a0.5+svn20090924-0ubuntu0~ppa2_amd64.deb) ...
Desempaquetando el reemplazo de libavformat52 ...
Preparando para reemplazar libavfilter0 3:0.svn20090303-1ubuntu6 (usando .../libavfilter0_4%3a0.5+svn20090924-0ubuntu0~ppa2_amd64.deb) ...
Desempaquetando el reemplazo de libavfilter0 ...
Preparando para reemplazar libpostproc51 3:0.svn20090303-1ubuntu6 (usando .../libpostproc51_4%3a0.5+svn20090924-0ubuntu0~ppa2_amd64.deb) ...
Desempaquetando el reemplazo de libpostproc51 ...
Preparando para reemplazar libswscale0 3:0.svn20090303-1ubuntu6 (usando .../libswscale0_4%3a0.5+svn20090924-0ubuntu0~ppa2_amd64.deb) ...
Desempaquetando el reemplazo de libswscale0 ...
Preparando para reemplazar libavcodec-unstripped-52 3:0.svn20090303-1ubuntu2+unstripped1 (usando .../libavcodec-unstripped-52_4%3a0.5+svn20090924-0ubuntu0~ppa1_amd64.deb) ...
Desempaquetando el reemplazo de libavcodec-unstripped-52 ...
Preparando para reemplazar libavutil-unstripped-49 3:0.svn20090303-1ubuntu2+unstripped1 (usando .../libavutil-unstripped-49_4%3a0.5+svn20090924-0ubuntu0~ppa1_amd64.deb) ...
Desempaquetando el reemplazo de libavutil-unstripped-49 ...
Preparando para reemplazar libsndfile1 1.0.17-4ubuntu1 (usando .../libsndfile1_1.0.17-4ubuntu1.1_amd64.deb) ...
Desempaquetando el reemplazo de libsndfile1 ...
Preparando para reemplazar python-zopeinterface 3.4.0-0ubuntu3 (usando .../python-zopeinterface_3.4.0-0ubuntu3.3_amd64.deb) ...
Desempaquetando el reemplazo de python-zopeinterface ...
Preparando para reemplazar mplayer 2:1.0~svn29714-0ubuntu0~ppa0 (usando .../mplayer_2%3a1.0~svn29756-0ubuntu0~ppa0_amd64.deb) ...
Desempaquetando el reemplazo de mplayer ...
Preparando para reemplazar x264 1:0.svn20081230-0.0ubuntu1 (usando .../x264_1%3a0.svn20090924-0ubuntu0~ppa1_amd64.deb) ...
Desempaquetando el reemplazo de x264 ...
Procesando disparadores para man-db ...
Se encontraron errores al procesar:
 /var/cache/apt/archives/libavcodec-extra-52_4%3a0.5+svn20090924-0ubuntu0~ppa1_amd64.deb
Log ended: 2009-10-16  18:57:05

```

This what i get with "vlc -vvv --no-plugins-cache --list --color|grep -i ffmpeg":
```
VLC media player 1.0.2 Goldeneye
[0x1236888] main libvlc debug: VLC media player - version 1.0.2 Goldeneye - (c) 1996-2009 the VideoLAN team
[0x1236888] main libvlc debug: libvlc was configured with ./configure  '--build=x86_64-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--config-cache' '--enable-fast-install' '--with-binary-version=1~ppa1' '--disable-update-check' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--enable-dvb' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--enable-flac' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-mod' '--enable-theora' '--enable-dvdnav' '--enable-gnutls' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-dca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[0x1236888] main libvlc debug: translation test: code is "es"
[0x1236888] main libvlc debug: checking plugin modules
[0x1236888] main libvlc debug: recursively browsing `/usr/lib/vlc'
[0x1236888] main libvlc warning: cannot find symbol "vlc_entry__1_0_0e" in file `/usr/lib/vlc/audio_output/libesd_plugin.so' (/usr/lib/vlc/audio_output/libesd_plugin.so: undefined symbol: vlc_entry__1_0_0e)
[0x1236888] main libvlc warning: cannot load module `/usr/lib/vlc/codec/libavcodec_plugin.so' (libavutil.so.49: no se puede abrír el archivo de objeto compartido: No existe el fichero ó directorio)
[0x1236888] main libvlc warning: cannot load module `/usr/lib/vlc/demux/libavformat_plugin.so' (libavutil.so.49: no se puede abrír el archivo de objeto compartido: No existe el fichero ó directorio)
[0x1236888] main libvlc debug: module bank initialized (375 modules)
[0x1236888] main libvlc debug: opening config file (/home/alvaro/.config/vlc/vlcrc)

```

These are external repositories in /etc/apt/sources.list:
```
# Drivers Nvidia
deb http://ppa.launchpad.net/thefirstm/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/thefirstm/ppa/ubuntu jaunty main

## Medibuntu - Ubuntu 9.04 "jaunty jackalope"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ jaunty free non-free
deb-src http://packages.medibuntu.org/ jaunty free non-free

# Google software repository
deb http://dl.google.com/linux/deb/ stable non-free

# Repositorio para VLC
deb http://ppa.launchpad.net/c-korn/vlc/ubuntu jaunty main
deb-src http://ppa.launchpad.net/c-korn/vlc/ubuntu jaunty main

```

I have forced reinstall all packages updated during the failled update with same results.

Somebody can help?

Thanks

---

### Post by ezacon on 2009-10-20
If i remove all external entries in sources.list, How can i remove all pckages downloaded fron those sources?
Is it any way to revert an update?
I realy d'ont want to do a bare betal reinstall.

---

### Post by mc4man on 2009-10-20
While I don't read spanish I can see you used the m. marley ppa. Whether  you were using just for nvidia drivers or all the other packages available I don't know.
( running an update with that ppa enabled can update a lot of packages.

There is certainly the possibility that you've installed his ffmpeg lib's and possibly the xine libs.
The versions of those libs could present an issue with apps that depend on ffmpeg libs and were built off of earlier versions ffmpeg. ( particularly when a ppa uses ffmpeg sources around 09/24 or later

If so, you could either build a vlc, ect. using the m.marley ffmpeg lib -dev's or remove the ppa, delete all ffmpeg libs (libavcodec, libavformat ,ect ) and then re- install using the jaunty repo versions of the ffmpeg libs and ffmpeg plugins ( gstreamer and libxine

---

### Post by ezacon on 2009-10-21
Thanks for your answere.
One more question. If i remove the source for marley ppa from sources.list then do an "apt-get update" and an "apt-get --reinstall install package", is the default ubuntu versión of "package" reinstalled?

---

### Post by ezacon on 2009-10-21
SOLVED.
The problem was with some lib from marleys ppa.
After some uninstall and reinstall, i can again play mp4 files.

Thanks.

---

### Post by vinutux on 2009-10-21
plz.... mark thread SOLVED under thread tools

---

