---
title: "Exaile cannot play files from removable drive after upgrade to jaunty"
date: 2009-05-01
forum: Multimedia Software
---

### Post by p3tris on 2009-05-01
SOLVED: It seems that the problem was the character # in front of my files. as soon as i removed it everything run smoothly. Thanks.


Hi,

I upgraded to jaunty and since then my music player (exaile) cannot play my mp3's from the removable drive. Before updating to jaunty could since all my library and files are on the removable drive. To test i tried playing from a different removable drive i have (the backup of my collection, and it doesn't work either). From my harddisk it plays like charm. I tried both the exaile from the synaptic and the exaile-devel downloaded from the exaile.org site (as a deb file for ubuntu).

Here's what i get:

```
p3tris@Dell-icious:~$ exaile 
INFO    : Loading Exaile 0.2.99.1...
INFO    : Loading settings
INFO    : Loading plugins...
INFO    : Loading collection...
INFO    : Loading devices...
INFO    : Loading interface...
INFO    : Playing file:///media/VAULT_/#MUSIC/sorted/#greek/C-REAL/&#924;&#951;&#957; &#945;&#957;&#951;&#963;&#965;&#967;&#949;&#943;&#962;/07 Mhn Anhsyxeis.mp3
INFO    : Attempting to find covers for 'Unknown' by 'C-REAL' from 'Mhn anhsyxeis'
ERROR   : <gst.Message GstMessageError, gerror=(GstGError)(NULL), debug=(string)"gstgnomevfssrc.c\(864\):\ gst_gnome_vfs_src_start\ \(\):\ /GstPlayBin:player/GstGnomeVFSSrc:source:\012Could\ not\ open\ vfs\ file\ \"file:///media/VAULT_/\#MUSIC/sorted/\#greek/C-REAL/\316\234\316\267\316\275\ \316\261\316\275\316\267\317\203\317\205\317\207\316\265\316\257\317\202/07\ Mhn\ Anhsyxeis.mp3\"\ for\ reading:\ Is\ a\ directory\ \(25\)"; from source at 0xaa1ecd8> ['__class__', '__cmp__', '__delattr__', '__dict__', '__doc__', '__format__', '__getattribute__', '__grefcount__', '__gstminiobject_init__', '__gtype__', '__hash__', '__init__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'copy', 'flags', 'parse_async_start', 'parse_buffering', 'parse_clock_lost', 'parse_clock_provide', 'parse_duration', 'parse_error', 'parse_info', 'parse_new_clock', 'parse_segment_done', 'parse_segment_start', 'parse_state_changed', 'parse_tag', 'parse_warning', 'set_buffering_stats', 'set_seqnum', 'src', 'structure', 'timestamp', 'type']
ERROR   : <gst.Message GstMessageError, gerror=(GstGError)(NULL), debug=(string)"gstgnomevfssrc.c\(864\):\ gst_gnome_vfs_src_start\ \(\):\ /GstPlayBin:player/GstGnomeVFSSrc:source:\012Could\ not\ open\ vfs\ file\ \"file:///media/VAULT_/\#MUSIC/sorted/\#greek/C-REAL/\316\234\316\267\316\275\ \316\261\316\275\316\267\317\203\317\205\317\207\316\265\316\257\317\202/07\ Mhn\ Anhsyxeis.mp3\"\ for\ reading:\ Is\ a\ directory\ \(25\)"; from source at 0xaa1ef58> ['__class__', '__cmp__', '__delattr__', '__dict__', '__doc__', '__format__', '__getattribute__', '__grefcount__', '__gstminiobject_init__', '__gtype__', '__hash__', '__init__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'copy', 'flags', 'parse_async_start', 'parse_buffering', 'parse_clock_lost', 'parse_clock_provide', 'parse_duration', 'parse_error', 'parse_info', 'parse_new_clock', 'parse_segment_done', 'parse_segment_start', 'parse_state_changed', 'parse_tag', 'parse_warning', 'set_buffering_stats', 'set_seqnum', 'src', 'structure', 'timestamp', 'type']
WARNING : No covers found
INFO    : Playing file:///media/USB-HDD/#MUSIC/sorted/#greek/B.D. FOXMOOR/1999b - &#931;&#964;&#951; &#967;&#940;&#963;&#951; &#954;&#945;&#953; &#963;&#964;&#951; &#966;&#941;&#958;&#951;/05 &#924;&#953;&#945; &#945;&#960;&#959;&#961;&#943;&#945;.mp3
ERROR   : <gst.Message GstMessageError, gerror=(GstGError)(NULL), debug=(string)"gstgnomevfssrc.c\(864\):\ gst_gnome_vfs_src_start\ \(\):\ /GstPlayBin:player/GstGnomeVFSSrc:source:\012Could\ not\ open\ vfs\ file\ \"file:///media/USB-HDD/\#MUSIC/sorted/\#greek/B.D.\ FOXMOOR/1999b\ -\ \316\243\317\204\316\267\ \317\207\316\254\317\203\316\267\ \316\272\316\261\316\271\ \317\203\317\204\316\267\ \317\206\316\255\316\276\316\267/05\ \316\234\316\271\316\261\ \316\261\317\200\316\277\317\201\316\257\316\261.mp3\"\ for\ reading:\ Is\ a\ directory\ \(25\)"; from source at 0xaac7010> ['__class__', '__cmp__', '__delattr__', '__dict__', '__doc__', '__format__', '__getattribute__', '__grefcount__', '__gstminiobject_init__', '__gtype__', '__hash__', '__init__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'copy', 'flags', 'parse_async_start', 'parse_buffering', 'parse_clock_lost', 'parse_clock_provide', 'parse_duration', 'parse_error', 'parse_info', 'parse_new_clock', 'parse_segment_done', 'parse_segment_start', 'parse_state_changed', 'parse_tag', 'parse_warning', 'set_buffering_stats', 'set_seqnum', 'src', 'structure', 'timestamp', 'type']
ERROR   : <gst.Message GstMessageError, gerror=(GstGError)(NULL), debug=(string)"gstgnomevfssrc.c\(864\):\ gst_gnome_vfs_src_start\ \(\):\ /GstPlayBin:player/GstGnomeVFSSrc:source:\012Could\ not\ open\ vfs\ file\ \"file:///media/USB-HDD/\#MUSIC/sorted/\#greek/B.D.\ FOXMOOR/1999b\ -\ \316\243\317\204\316\267\ \317\207\316\254\317\203\316\267\ \316\272\316\261\316\271\ \317\203\317\204\316\267\ \317\206\316\255\316\276\316\267/05\ \316\234\316\271\316\261\ \316\261\317\200\316\277\317\201\316\257\316\261.mp3\"\ for\ reading:\ Is\ a\ directory\ \(25\)"; from source at 0xaac6f48> ['__class__', '__cmp__', '__delattr__', '__dict__', '__doc__', '__format__', '__getattribute__', '__grefcount__', '__gstminiobject_init__', '__gtype__', '__hash__', '__init__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'copy', 'flags', 'parse_async_start', 'parse_buffering', 'parse_clock_lost', 'parse_clock_provide', 'parse_duration', 'parse_error', 'parse_info', 'parse_new_clock', 'parse_segment_done', 'parse_segment_start', 'parse_state_changed', 'parse_tag', 'parse_warning', 'set_buffering_stats', 'set_seqnum', 'src', 'structure', 'timestamp', 'type']
INFO    : Attempting to find covers for '&#924;&#953;&#945; &#945;&#960;&#959;&#961;&#943;&#945;' by 'B.D.Foxmoor' from '&#931;&#964;&#951; &#967;&#940;&#963;&#951; &#954;&#945;&#953; &#963;&#964;&#951; &#966;&#941;&#958;&#951;'
WARNING : No covers found
INFO    : Playing file:///home/p3tris/Music/alexiou-arvanitaki - megali sinantisi live2009/02. &#919; &#918;&#937;&#919; &#924;&#927;&#933; &#922;&#933;&#922;&#923;&#927;&#933;&#931; &#922;&#913;&#925;&#917;&#921; - &#913;&#923;&#917;&#926;&#921;&#927;&#933;.mp3
WARNING : No covers found

```

You can see me trying to access 2 files from my 2 external hardisks and then playing a file from my internal.

Also other players (Mplayer, VLC etc) can see and play files from my external drives! Only exaile does this.

Any help appreciated.

Thanks

---

