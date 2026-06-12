---
title: "solution: compiled totem on ubuntu dapper for h.264"
date: 2007-09-04
forum: Multimedia &amp; Video
---

### Post by Mrukant on 2007-09-04
Dear Frnds,

I compiled Totem 2.18.3 on ubuntu dapper for playing h.264 files.

Below is the comprehensive list of dependencies. You can find the same info as attachment to this post in a more readable format. Mail me if you have any problems still. I will try to answer whenever I find time.

regards,
Mrukant

---------------------------------------------------

Dependencies for Totem-2.18.3


XML::Parser --> [http://search.cpan.org/~msergeant/XML-Parser/Parser.pm](http://search.cpan.org/~msergeant/XML-Parser/Parser.pm)
Expat --> [http://www.libexpat.org/](http://www.libexpat.org/)

gstreamer-plugins-base-0.10  --> [http://gstreamer.freedesktop.org/](http://gstreamer.freedesktop.org/)    [0.10.14]
Glib >= 2.6 --> [http://www.gtk.org/](http://www.gtk.org/)
liboil-0.3.8 or later --> [http://liboil.freedesktop.org/wiki/](http://liboil.freedesktop.org/wiki/)
gtreamer-0.10 >= 0.10.13.1  --> [http://gstreamer.freedesktop.org/](http://gstreamer.freedesktop.org/)    [0.10.14]  
Bison >= 1.875 --> [http://www.gnu.org/software/bison/](http://www.gnu.org/software/bison/)
GNU M4 1.4 --> [http://www.gnu.org/software/m4/](http://www.gnu.org/software/m4/)
Flex --> [http://flex.sourceforge.net](http://flex.sourceforge.net)
libxml2 --> [http://xmlsoft.org/](http://xmlsoft.org/)

Gconf-2.0  --> [http://www.paldo.org/index-section-packages-page-main-releaseid-84387.html](http://www.paldo.org/index-section-packages-page-main-releaseid-84387.html)
ORBit2 --> [http://www.gnome.org/projects/ORBit2/download.html](http://www.gnome.org/projects/ORBit2/download.html)  
(I think we can do away with ORBit2. At present installed liborbit2 and liborbit2-dev through synaptic pkg mgr)
libIDL-2.0  
(Installed libIDL through synaptic pkg mgr..problems compiling libIDL)

gconfaudiosink
gst-plugins-good --> [http://gstreamer.freedesktop.org/](http://gstreamer.freedesktop.org/)  [0.10.6]

gst-plugins-bad --> [http://gstreamer.freedesktop.org/](http://gstreamer.freedesktop.org/)  [0.10.5]
faad2 – for decoding mpeg4 audio
( Installed faad2, libfaad2 and libfaad2-dev packages from packaged.ubuntu.com because unable to compile faad2)
x264 – for h.264 encoding support --> [http://www.videolan.org/developers/x264.html](http://www.videolan.org/developers/x264.html)

gtk+-2.0 
[
compiled 2.10.14 with ./configure –prefix=/usr
coz totem-2.18.3 gave compilation erros related to gtk_recent_info_has_group and many more. Basically I think it was looking for libgtk-x11-2.0.so in /usr whereas libgtk-x11-2.0.so by default goes into /usr/local/lib
]
Glib 2.12
Pango 1.13 [compiled 1.18] --> [http://ftp.gnome.org/pub/GNOME/sources/pango/](http://ftp.gnome.org/pub/GNOME/sources/pango/)
atk 1.9  [compiled 1.19] --> [http://ftp.gnome.org/pub/GNOME/sources/atk/](http://ftp.gnome.org/pub/GNOME/sources/atk/)
cairo 1.2 
[
	compiled 1.4.10 with ./configure –prefix=/usr
	coz gtk+2.10.14 gave compilation errors related to  cairo_pdf_surface_create
	and few others. Basically I think it was looking for libcairo.so in /usr/lib whereas 	cairo by default goes into /usr/local/lib
]  -> [http://www.cairographics.org/](http://www.cairographics.org/)
freetype and fontconfig (fond backends)
	( Installed libfreetype-dev and libfontconfig1-dev from synaptic)
xlibs
( Installed xlibs-dev from synaptic)
libtiff 
( Installed libtiff4-dev from synaptic )

libpng
( Installed libpng12-dev from synaptic )

checked for XopenDisplay during configure of gtk+-2.0. Inspite of libXrender being present, it gave error, so Installed libxrender-dev from synaptic.

libgnomeui-2.0
( Installed libgnomeui-dev from synaptic )

gnome-vfs-2.0 [compiled 2.19.91] --> [http://ftp.gnome.org/pub/GNOME/sources/](http://ftp.gnome.org/pub/GNOME/sources/)
libbz2
( Installed libbz2-dev from synaptic)
dbus-glib-1 [compiled dbus-1.0.2 with ./configure –prefix=/usr] --> [http://www.freedesktop.org/wiki/Software/dbus](http://www.freedesktop.org/wiki/Software/dbus)


gnome-desktop-2.0
( Installed libgnome-desktop-dev from synaptic )

gnome-icon-theme [compiled 2.19.91]  --> [http://ftp.gnome.org/pub/GNOME/sources/](http://ftp.gnome.org/pub/GNOME/sources/)
icon-naming-utils >= 0.8.1 [compiled 0.8.2] --> [http://www.linuxfromscratch.org/blfs/view/svn/general/icon-naming-utils.html](http://www.linuxfromscratch.org/blfs/view/svn/general/icon-naming-utils.html)
XML::Simple 
( Installed libxml-simple-perl from synaptic )

 
gst-plugins-ugly [compiled 0.10.6] --> [http://gstreamer.freedesktop.org/](http://gstreamer.freedesktop.org/)
mpeg2dec [compiled 0.4.1] --> [http://libmpeg2.sourceforge.net/](http://libmpeg2.sourceforge.net/)

---

