---
title: "how to install listen .6"
date: 2009-07-04
forum: Multimedia Software
---

### Post by manosone on 2009-07-04
Hello to everyone.I just wanted to install listen by downloading the tarball from the developers site.When i type make install i take this...

mkdir -p /usr/bin
for dir in plugins plugins/webradio plugins/lyrics plugins/generic plugins/generic/spydaap plugins/generic/spydaap/parser source parse player widget updater vfs; do \
		mkdir -p /usr/lib/listen/${dir} ; \
	done
mkdir -p /usr/share/listen/img/source
mkdir -p /usr/share/pixmaps
mkdir -p /usr/share/applications
mkdir -p /usr/share/man/man1
mkdir -p /usr/share/dbus-1/services
for lang in ./ro ./fi ./uk ./cs ./br ./pa ./nb ./fr ./sk ./pt ./ar ./pt_BR ./lv ./ca ./et ./pl ./ru ./en_US ./zh_CN ./sr ./de ./be ./bn ./ko ./it ./da ./nl ./en_GB ./tr ./es ./sv ./hu ./gl ./vi ./en_CA ./ja; do mkdir -p /usr/share/locale/$lang/LC_MESSAGES; done
install -m 644 src/*.py /usr/lib/listen
install -m 644 src/*.pyc /usr/lib/listen
install: cannot stat `src/*.pyc': No such file or directory
make: *** [install] Error 1


Where exactly is the problem and what does this line means?

install: cannot stat `src/*.pyc': No such file or directory

---

### Post by jontresko on 2009-07-12
Same problem, same error here... Probably some simple, obvious yet oh so maddening detail we're missing!

---

### Post by jontresko on 2009-07-12
Ok, so I ended up getting it to work by installing some <g???-pty> stuff through package manager (can't remember exactly what it was and not sure it was even the problem). 
***I should really be keeping a log of my steps...***

What actually did it was going to the terminal ->$ cd <listen 0.6.2 folder> then typing separate commands in a sequence...

first: sudo make clean
it ran its course and everything went ok

second: sudo make:
it assembled; all is well

third: sudo make install
everything went ok; installed w/no errors!


Now, the only problem is that the program won't load!

So it is now in my amateur opinion that there is reason to the maddness.... maybe Listen 0.5 is the most recent version that works w/Ubuntu 9.04?

---

### Post by arsin225 on 2009-07-26
Checking for Python... /usr/bin/python
Checking Python version: 2.6
Checking for PyGTK >= 2.6: found
Checking for pyGTK-devel >= 2.6:
not found
Listen requires pyGTK-devel

Maybe that's our problem.. let me try... Once I installed that I got

Checking for Python... /usr/bin/python
Checking Python version: 2.6
Checking for PyGTK >= 2.6: found
Checking for pyGTK-devel >= 2.6: found
Checking for Xlib: not found
Try egg.trayicon instead:
not found
Listen require python-xlib or gnome-python-extras.
    ([http://python-xlib.sourceforge.net/](http://python-xlib.sourceforge.net/) or [http://ftp.gnome.org/pub/GNOME/sources/gnome-python-extras](http://ftp.gnome.org/pub/GNOME/sources/gnome-python-extras))
make: *** [check] Error 1


Installing gnome-python-extras.

Installed Listen, now that it's installed, it wont open.

---

### Post by Elisavet on 2009-10-12
Hey everyone,
I had the same problem a while ago but it had to do with my ubuntu theme
It seems that Listen supports only the default ubuntu themes, and even if the install is fine, the program won't load. I checked with one of the default ubuntu themes and it worked fine.
There's a simple way to make this go away, if that is the problem:
In terminal type
```
sudo gedit /usr/lib/listen/stock.py
```

That will open the text editor and it will look like this
```
# vim: ts=4
###
#
# Listen is the legal property of mehdi abaakouk <theli48@gmail.com>
# Copyright (c) 2006 Mehdi Abaakouk
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License version 2 as
# published by the Free Software Foundation
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA
#
###
#    From quodlibet 
###
LISTEN = "listen"

ALBUM_ART = 'listen_cover'
MEDIA_LIB = 'listen'
LASTFM = "source/lastfm_mini"
DYNAMIC = "dynamic"

WIKI_USERS = 'users'
WIKI_CD = 'cd'
PREF_OSD = "osd"
PREF_PODCAST = "pref_podcast"
PREF_LASTFM = "source/lastfm_mini"

SRC_BIBLIO = 'source/biblio'
SRC_DAAP = 'source/biblio'
SRC_IPOD = 'source/ipod'
SRC_PLAYLIST = 'source/playlist'
SRC_PLAYLIST_SMART = 'source/playlist_smart'
SRC_PLAYLIST_IPOD = 'source/playlist_ipod'
SRC_PODCAST_IPOD = 'source/podcast_ipod'
SRC_IRADIO='source/iradio'
SRC_WIKIPEDIA = "source/wikipedia"
SRC_LASTFM = "source/lastfm_mini"
SRC_PODCAST = "source/podcast"
SRC_LYRICS = "source/lyrics"



_ICONS = [SRC_DAAP,LISTEN,MEDIA_LIB,LASTFM,DYNAMIC,WIKI_USERS,WIKI_CD,\
        PREF_OSD,PREF_PODCAST,PREF_LASTFM,\
        SRC_BIBLIO,SRC_IPOD,SRC_PLAYLIST,SRC_PLAYLIST_IPOD,SRC_PODCAST_IPOD,\
        SRC_IRADIO,SRC_WIKIPEDIA,SRC_LASTFM,SRC_PODCAST,SRC_LYRICS,SRC_PLAYLIST_SMART]

IMPORT_FOLDER = "importfolder"
IMPORT_FILE = "importfile"
EDIT = "edit"
RENAME = "rename"
ENQUEUE = "enqueue"
PLAY = "play"
WIKI_ARTIST = "wiki-artist"
WIKI_ALBUM = "wiki-album"
LYRICS = "lyrics"
DELETE = "delete"
DELETE_DISK = "delete-disk"
MUSICBRAINZ = "musicbrainz"
NEW_PODCAST = "new-podcast"
NEW_RADIO = "new-radio"
EDIT_RADIO = "edit-radio"
ADD_FAVORITE = "add-favorite"
EXPORT = "export"
RELOAD_LIBRARY = "reload-library"
SHUFFLE = "stock_shuffle"
BURN = "burn"

import gtk,gobject
import const
factory = gtk.IconFactory()

def stock_init():
    import gtk
    for fn in _ICONS:
        pb = gtk.gdk.pixbuf_new_from_file(const.PIXMAP_DIR+fn+".png")
        factory.add(fn, gtk.IconSet(pb))
    factory.add_default()
    gtk.stock_add([
            (EDIT, _("_Edit"), 0, 0, ""),
            (RENAME, _("_Rename"), 0, 0, ""),
            (ENQUEUE, _("En_queue"), 0, 0, ""),
            (PLAY, _("_Play"), 0, 0, ""),
            (WIKI_ARTIST, _("About _artist"), 0, 0, ""),
            (WIKI_ALBUM, _("About a_lbum"), 0, 0, ""),
            (LYRICS, _("See _Lyrics"), 0, 0, ""),
            (DELETE, _('Remove'), 0, 0, ""),
            (DELETE_DISK, _('Move to trash'), 0, 0, ""),
            (SRC_PLAYLIST, _('_New Playlist'), 0, 0, ""),
            (SRC_PLAYLIST_SMART, _('New _Automatique Playlist...'), 0, 0, ""),
            (IMPORT_FOLDER,_('_Import Folder...'), 0, 0, ""),
            (IMPORT_FILE,_('_Import _File...'), 0, 0, ""),
            (MUSICBRAINZ,_('_Get file informations'), 0, 0, ""),
            (NEW_PODCAST,_('_New Podcast feed'), 0, 0, ""),
            (NEW_RADIO,_('_New Web Radio'), 0, 0, ""),
            (ADD_FAVORITE,_('_Add to favorite'), 0, 0, ""),
            (EDIT_RADIO,_("Edit Web Radio"), 0, 0, ""),
            (EXPORT,_("Export"),0,0,""),
            (RELOAD_LIBRARY,_("Reload Library"),0,0,""),
            (SHUFFLE,_("Shuffle"),0,0,""),
            (BURN,_("Burn"),0,0,"")
            
            ])

    icons = gtk.IconFactory()
    lookup = gtk.icon_factory_lookup_default
   
    icons.add(NEW_PODCAST,lookup(gtk.STOCK_NEW))
    icons.add(NEW_RADIO,lookup(gtk.STOCK_NEW))
    icons.add(EDIT_RADIO,lookup(gtk.STOCK_EDIT))    
    icons.add(EDIT, lookup(gtk.STOCK_PROPERTIES))
    icons.add(IMPORT_FOLDER, lookup(gtk.STOCK_OPEN))
    icons.add(IMPORT_FILE, lookup(gtk.STOCK_FILE))
    icons.add(RENAME, lookup(gtk.STOCK_EDIT))
    icons.add(ENQUEUE, lookup(gtk.STOCK_ADD))
    icons.add(PLAY, lookup(gtk.STOCK_MEDIA_PLAY))
    icons.add(WIKI_ARTIST, lookup(gtk.STOCK_ABOUT))
    icons.add(WIKI_ALBUM, lookup(gtk.STOCK_ABOUT))
    icons.add(LYRICS, lookup(gtk.STOCK_EDIT))
    icons.add(DELETE, lookup(gtk.STOCK_REMOVE))
    icons.add(DELETE_DISK, lookup(gtk.STOCK_DELETE))
    icons.add(MUSICBRAINZ, lookup(gtk.STOCK_NETWORK))
    icons.add(ADD_FAVORITE, lookup(gtk.STOCK_CONVERT))
    icons.add(EXPORT, lookup(gtk.STOCK_SAVE_AS))
    icons.add(RELOAD_LIBRARY, lookup(gtk.STOCK_REFRESH))
    icons.add(BURN,lookup(gtk.STOCK_CDROM))
    try:icons.add(SHUFFLE,  gtk.IconSet(gtk.icon_theme_get_default().load_icon("stock_shuffle",-1,gtk.ICON_LOOKUP_USE_BUILTIN)))
    except gobject.GError:pass 
        
    icons.add_default()
```

Erase the following lines, located at the end of the text
```
try:icons.add(SHUFFLE,  gtk.IconSet(gtk.icon_theme_get_default().load_icon("stock_shuffle",-1,gtk.ICON_LOOKUP_USE_BUILTIN)))
    except gobject.GError:pass
```
Save and exit

Now, reload Listen and it will work:cool:

---

