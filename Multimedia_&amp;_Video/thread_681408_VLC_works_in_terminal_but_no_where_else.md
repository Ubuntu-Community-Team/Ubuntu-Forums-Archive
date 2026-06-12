---
title: "VLC works in terminal but no where else"
date: 2008-01-28
forum: Multimedia &amp; Video
---

### Post by pmgr33r on 2008-01-28
I am having problems getting VLC to run. When i run it in terminal, it works fine but if i try to open a file by right-clicking or opening vlc through the applications menu, nothing happens. I have tried apt-get remove vlc and reinstalling but the same things happens. I had it working fine a few weeks ago and i'm not sure what happened.

Thanks for the help

---

### Post by Casual Fan on 2008-01-28
Is VLC running in the background? Open System>Administration>System Monitor and see if it's running, and if so, end the process and try to open from the Applications menu.

---

### Post by pmgr33r on 2008-01-29
VLC is not running in the background

---

### Post by mc4man on 2008-01-29
it's possible  the vlc executable is not where it's expected to be (/usr/bin) or you've deleted one of the links to it.
under a normal repo install the menu item will call a link (wxvlc) to the executable (vlc), both should be in /usr/bin
So you should check /usr/bin to see what's there.(if wxvlc is there ck. properties to see where it links to)  If you right click application>edit menus, select sound and video, right click vlc, select properties you can ck. or edit the command. As far as the right click, open with  - you can do another custom command (/usr/bin/vlc or vlc or wxvlc - doesn't matter) but note it will give you a 2nd right click option for vlc - probably better to figure out why the existing one doesn't work

---

### Post by pmgr33r on 2008-01-30
ok so i tried a sudo apt-get remove --purge vlc and reinstalling. Now i no longer have vlc in /usr/bin and i cannot run it from terminal any longer. Any suggestions?
I also tried mc4man's suggestion found vlc in /usr/bin (it is no longer there) and could not get it to run by changing the menu shortcut to /usr/bin/vlc, vlc and wxvlc, none of which worked.
After running: locate vlc the following are all that were found in /usr/bin

/usr/bin/wxvlc
/usr/bin/svlc

---

### Post by mc4man on 2008-01-30
Wasn't really suggesting you change anything , just to check what was were and where your menu item was pointing. Just to ask - are you using Ubuntu or something else? If Ubuntu go to synaptic, search vlc, and see if it's installed.

---

### Post by pmgr33r on 2008-01-30
I'm Using Ubuntu. Used synaptic to reinstall vlc and now it works again in terminal, the file usr/bin/vlc is now back but i still cannot get it to work outside of terminal. Default vlc command in menu is "wxvlc %F" neither that nor "vlc" get any response

---

### Post by mc4man on 2008-01-30
go back into /usr/bin and see if wxvlc is there. If so try r.click - open, normally vlc will open. Also go r. click >properties and see what  link target is (should be /usr/bin/vlc

edit: because wxvlc is the default skin you don't really need the link, if you want go into edit menus like before and in the launcher properties for vlc media player use the browse button to go to /usr/bin/vlc (or just type that in), same for r. click open with other app.>use a custom command

---

### Post by pmgr33r on 2008-01-30
wxvlc is in /usr/bin. When i r. click >open nothing happens, looking at the properties, the link target is /usr/bin/vlc

---

### Post by mc4man on 2008-01-30
try what I added in edit

---

### Post by pmgr33r on 2008-01-30
Changed menu command to /usr/bin/vlc - still nothing

---

### Post by mc4man on 2008-01-30
Did you install vlc previously from somewhere other than the ubuntu repo?
In any event try once more from the top
Go in synaptic, search vlc and mark/apply a _complete_ removal - then re search and install - see what happens

edit :just for a bit of clarity - any command that opens vlc in the terminal should work when used as the command anywhere else, like in the apps menu or the r.click open with. In a normal install entering in the terminal  - vlc, or wxvlc, or /usr/bin/vlc will all open vlc. All 3 lead to the same place/result

---

### Post by pmgr33r on 2008-01-30
Tried a complete uninstall and reinstall and still nothing, although when i click on the vlc icon in the menu, "wxvlc" will pop up in CPU top processes for a second but quickly disappear and i cannot find it in system monitor. Also i'm running compiz, could that be causing problems?

---

### Post by pmgr33r on 2008-01-30
Upon entering "vlc" "wxvlc" or "/usr/bin/vlc" the text based player in the terminal is run. But i can't get the graphic one to open anywhere

---

### Post by mc4man on 2008-01-30
Post what version of vlc you have - like - 0.8.6.release.c-0ub (this is current ubuntu version - wxWidgets interface )
edit : if this is your version ck. in synaptic for libwxgtk2.6-0 - I don't think vlc can install without it - maybe try a reinstallation

---

### Post by pmgr33r on 2008-01-30
VLC media player 0.8.6c Janus

---

### Post by mc4man on 2008-01-30
pmgr33r - ck. pm

---

### Post by pmgr33r on 2008-01-30
What happens when vlc is entered into terminal

---

### Post by mc4man on 2008-01-30
Well you've installed a compiled version from somewhere else. If you simply want the the 'regular' version with the wx interface then go to software sources and uncheck whatever repo your getting it from. Then do the whole complete remove and install again. I've never used a ncurses version so I don't know how/if you can force it into wx mode - should be possible though
double ck. on that lib I mentioned

---

### Post by pmgr33r on 2008-01-31
How is it that i uncheck whatever repo i got it from, i've been downloading it through synaptic or apt-get. by just searching vlc and install whatever it tells me too.

---

### Post by eye208 on 2008-01-31
Please copy and paste the output of the following commands here:

dpkg -s vlc
dpkg -L vlc

---

### Post by pmgr33r on 2008-01-31
Here they are
```
pat@ALLSTARME:~$ dpkg -s vlc
Package: vlc
Status: install ok installed
Priority: optional
Section: graphics
Installed-Size: 3228
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 0.8.6.release.c-0ubuntu5
Replaces: vlc-plugin-dvb (<< 0.5.2-2), vlc-plugin-xosd (<< 0.5.2-2), vlc-plugin-dv (<< 0.5.2-2), vlc-plugin-mad (<< 0.5.2-2), vlc-mad (<< 0.5.0), vlc-plugin-a52 (<< 0.5.2-2), vlc-plugin-ogg (<< 0.5.2-2), vlc-plugin-lirc (<< 0.5.2-2), vlc-lirc (<< 0.5.0), vlc-plugin-aa (<< 0.5.2-2), vlc-aa (<< 0.5.0), wxvlc (<< 0.8.5-test3.debian-4), vlc-plugin-alsa (<< 0.8.5-test3.debian-4)
Provides: mp3-decoder
Depends: vlc-nox (= 0.8.6.release.c-0ubuntu5), libaa1 (>= 1.2), libatk1.0-0 (>= 1.13.2), libc6 (>= 2.6-1), libcaca0 (>= 0.99.beta11-1), libcairo2 (>= 1.4.0), libcdio6, libcucul0 (>= 0.99.beta11-1), libdbus-1-3 (>= 1.1.1), libdbus-glib-1-2 (>= 0.74), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.3.5), libfribidi0 (>= 0.10.7), libgcc1 (>= 1:4.2.1), libgl1-mesa-glx | libgl1, libglib2.0-0 (>= 2.14.0), libglu1-mesa | libglu1, libgtk2.0-0 (>= 2.12.0), libice6 (>= 1:1.0.0), libiso9660-4, libjpeg62, libnotify1 (>= 0.4.4), libnotify1-gtk2.10, libpango1.0-0 (>= 1.18.2), libpng12-0 (>= 1.2.13-4), libsdl-image1.2 (>= 1.2.5), libsdl1.2debian (>= 1.2.10-1), libsm6, libstdc++6 (>= 4.2.1), libtar, libtiff4, libvcdinfo0 (>> 0.7.23), libvlc0 (>= 0.8.6.release.c), libwxbase2.6-0 (>= 2.6.3.2.1.5ubuntu12), libwxgtk2.6-0 (>= 2.6.3.2.1.5ubuntu12), libx11-6, libxcomposite1 (>= 1:0.3-1), libxcursor1 (>> 1.1.2), libxdamage1 (>= 1:1.1), libxext6, libxfixes3 (>= 1:4.0.1), libxi6, libxinerama1, libxosd2 (>= 2.2.13), libxrandr2 (>= 2:1.2.0), libxrender1, libxv1, zlib1g (>= 1:1.2.3.3.dfsg-1), ttf-dejavu
Recommends: videolan-doc
Suggests: mozilla-plugin-vlc
Conflicts: vlc-plugin-dvb (<< 0.5.2-2), vlc-plugin-xosd (<< 0.5.2-2), vlc-plugin-dv (<< 0.5.2-2), vlc-plugin-mad (<< 0.5.2-2), vlc-mad (<< 0.5.0), vlc-plugin-a52 (<< 0.5.2-2), vlc-plugin-ogg (<< 0.5.2-2), vlc-plugin-lirc (<< 0.5.2-2), vlc-lirc (<< 0.5.0), vlc-plugin-aa (<< 0.5.2-2), vlc-aa (<< 0.5.0), wxvlc (<< 0.8.5-test3.debian-4), vlc-plugin-alsa (<< 0.8.5-test3.debian-4)
Description: multimedia player and streamer
 VLC is the VideoLAN project's media player. It plays MPEG, MPEG2, MPEG4,
 DivX, MOV, WMV, QuickTime, mp3, Ogg/Vorbis files, DVDs, VCDs, and multimedia
 streams from various network sources.
 .
 VLC can also be used as a streaming server that duplicates the stream it
 reads and multicasts them through the network to other clients, or serves
 them through HTTP.
 .
 VLC has support for on-the-fly transcoding of audio and video formats, either
 for broadcasting purposes or for movie format transformations. Support for
 most output methods is provided by this package, but features can be added
 by installing additional audio plugins (vlc-plugin-esd, vlc-plugin-sdl,
 vlc-plugin-arts) or video plugins (vlc-plugin-sdl, vlc-plugin-ggi,
 vlc-plugin-glide, vlc-plugin-svgalib). There is also a web browser plugin
 in the mozilla-plugin-vlc package.
Original-Maintainer: Sam Hocevar (Debian packages) <sam+deb@zoy.org>

pat@ALLSTARME:~$ dpkg -L vlc
/.
/usr
/usr/bin
/usr/lib
/usr/lib/vlc
/usr/lib/vlc/access
/usr/lib/vlc/access/libscreen_plugin.so
/usr/lib/vlc/audio_filter
/usr/lib/vlc/audio_mixer
/usr/lib/vlc/audio_output
/usr/lib/vlc/codec
/usr/lib/vlc/codec/libsdl_image_plugin.so
/usr/lib/vlc/control
/usr/lib/vlc/demux
/usr/lib/vlc/gui
/usr/lib/vlc/gui/libskins2_plugin.so
/usr/lib/vlc/gui/libwxwidgets_plugin.so
/usr/lib/vlc/misc
/usr/lib/vlc/misc/libnotify_plugin.so
/usr/lib/vlc/video_chroma
/usr/lib/vlc/video_filter
/usr/lib/vlc/video_output
/usr/lib/vlc/video_output/libx11_plugin.so
/usr/lib/vlc/video_output/libxvideo_plugin.so
/usr/lib/vlc/video_output/libglx_plugin.so
/usr/lib/vlc/video_output/libaa_plugin.so
/usr/lib/vlc/video_output/libcaca_plugin.so
/usr/lib/vlc/video_output/libopengl_plugin.so
/usr/lib/vlc/visualization
/usr/lib/vlc/visualization/libxosd_plugin.so
/usr/lib/mime
/usr/lib/mime/packages
/usr/lib/mime/packages/vlc
/usr/share
/usr/share/doc
/usr/share/doc/vlc
/usr/share/applications
/usr/share/applications/vlc.desktop
/usr/share/pixmaps
/usr/share/pixmaps/vlc.png
/usr/share/vlc
/usr/share/vlc/skins2
/usr/share/vlc/skins2/fonts
/usr/share/vlc/skins2/skin.dtd
/usr/share/vlc/skins2/skin.catalog
/usr/share/vlc/skins2/winamp2.xml
/usr/share/vlc/skins2/default.vlt
/usr/share/vlc/pda-forwardb16x16.xpm
/usr/share/vlc/pda-openb16x16.xpm
/usr/share/vlc/pda-pauseb16x16.xpm
/usr/share/vlc/pda-playb16x16.xpm
/usr/share/vlc/pda-playlistb16x16.xpm
/usr/share/vlc/pda-preferencesb16x16.xpm
/usr/share/vlc/pda-rewindb16x16.xpm
/usr/share/vlc/pda-stopb16x16.xpm
/usr/share/vlc/vlc.xpm
/usr/share/vlc/vlc16x16.xpm
/usr/share/vlc/vlc48x48.ico
/usr/share/vlc/wxvlc.xpm
/usr/share/man
/usr/share/man/man1
/usr/share/menu
/usr/share/menu/vlc
/usr/bin/svlc
/usr/bin/wxvlc
/usr/share/vlc/skins2/fonts/FreeSans.ttf
/usr/share/vlc/skins2/fonts/FreeSansBold.ttf
/usr/share/man/man1/svlc.1.gz
/usr/share/man/man1/wxvlc.1.gz


```

---

### Post by mc4man on 2008-01-31
When I was compiling vlc awhile back the ncurses option was disabled by default - apparently the repo version has it enabled - sorry my mistake. Normally you'd have to call that interface like in  ```
vlc --intf ncurses
```, otherwise it should start in wx interface. You need to figure out why your defaulting to ncurses, the version you have is fine otherwise.
what happens if you try   ```
vlc --intf wx
```

edit: personally I'd try doing a complete removal of libwxbase2.6-0, followed by an install of vlc. (libwxgtk2.6-0 and vlc will be removed along with the base, note any other packages listed before applying)

---

### Post by pmgr33r on 2008-01-31
that did it! i set the command in the menu to "vlc --intf wx" and it works great. Thanks for all the help

---

