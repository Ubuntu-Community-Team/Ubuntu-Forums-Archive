---
title: "title bar of smplayer and vlc player unreadeable"
date: 2009-06-06
forum: Multimedia Software
---

### Post by glord2005 on 2009-06-06
**title bar of smplayer and vlc player unreadeable** 			
 			 			 		   		 		 		Hi,
     i  upgraded my ubuntu from intrepid to jaunty and everything went on fine. 
Later i installed vlc player and smplayer. 
before installing these packages i also executed these following commands :
sudo apt-get --purge remove vlc*
sudo apt-get --purge remove smplayer*
 then installed these players using following commands:
sudo apt-get install vlc
sudo apt-get install smplayer

These got intalled fine and also work fine but the title bar is not readable.
it is filled with all weard arbitrary symbols or signs (i dunno what to call them)

I am attaching a screenshot.
PLz help

---

### Post by rvm4000 on 2009-06-06
It seems qt-4 applications are using a wrong font. You may try to run qtconfig (from qt4-qtconfig package) and change the font.

---

### Post by glord2005 on 2009-06-06
Hi ,
 Thanx for the reply. 
 after u told me abt qt- config , i checked my synaptic manager if it was installed.
it wasn't , so i installed it and it also shows the same symbols.
here is a screenshot.

i dunno what to do now.
Plz help

---

### Post by rvm4000 on 2009-06-06
You can try to delete the file ~/.config/Trolltech.conf

If that doesn't work, maybe you'll have to try to change the font in qtconfig blindly. The font is selected in the 2nd tab. Maybe this picture can help you.

---

### Post by glord2005 on 2009-06-06
thanx again for a reply 
but when i type 
sudo qtconfig
 i get a perfectly normal window with a good font as i have attached in my screenshot3.png
but when i type only 
qtconfig
i get the same window as i had shown in my previous screenshot
i changed its fonts by counting number of rows from the "sudo qtconfig" window
then i saved it
but the situation remains the same :(

---

### Post by glord2005 on 2009-06-06
bump

---

### Post by rvm4000 on 2009-06-06
Did you try to delete your ~/.config/Trolltech.conf?

---

### Post by glord2005 on 2009-06-07
yes i deleted that when u had first asked me to and also many times after that.
before rplying also i deleted it , did changes in qtconfig  but the problem exists

---

### Post by glord2005 on 2009-06-07
Problem solved.
I searched for a normal Trolltech.conf file on google and i found one on
[http://crunchbanglinux.org/forums/topic/119/theming-vlc-and-other-qt4-applications-under-openbox/](http://crunchbanglinux.org/forums/topic/119/theming-vlc-and-other-qt4-applications-under-openbox/)
i replacd my Trolltech.conf file with this:

[Qt%20Plugin%20Cache%204.4.false]
usr\lib\qt4\plugins\inputmethods\libqimsw-multi.so=40403, 0, i686 Linux g++-4 full-config, 2008-10-03T21:02:22
usr\lib\qt4\plugins\imageformats\libqgif.so=40403, 0, i686 Linux g++-4 full-config, 2008-10-03T21:02:22
usr\lib\qt4\plugins\imageformats\libqico.so=40403, 0, i686 Linux g++-4 full-config, 2008-10-03T21:02:22
usr\lib\qt4\plugins\imageformats\libqjpeg.so=40403, 0, i686 Linux g++-4 full-config, 2008-10-03T21:02:22
usr\lib\qt4\plugins\imageformats\libqmng.so=40403, 0, i686 Linux g++-4 full-config, 2008-10-03T21:02:22
usr\lib\qt4\plugins\imageformats\libqtiff.so=40403, 0, i686 Linux g++-4 full-config, 2008-10-03T21:02:22

[Qt%20Factory%20Cache%204.4]
com.trolltech.Qt.QInputContextFactoryInterface%3A\usr\lib\qt4\plugins\inputmethods\libqimsw-multi.so=2008-10-03T21:02:22, imsw-multi
com.trolltech.Qt.QImageIOHandlerFactoryInterface%3A\usr\lib\qt4\plugins\imageformats\libqgif.so=2008-10-03T21:02:22, gif
com.trolltech.Qt.QImageIOHandlerFactoryInterface%3A\usr\lib\qt4\plugins\imageformats\libqico.so=2008-10-03T21:02:22, ico
com.trolltech.Qt.QImageIOHandlerFactoryInterface%3A\usr\lib\qt4\plugins\imageformats\libqjpeg.so=2008-10-03T21:02:22, jpeg, jpg
com.trolltech.Qt.QImageIOHandlerFactoryInterface%3A\usr\lib\qt4\plugins\imageformats\libqmng.so=2008-10-03T21:02:22, mng
com.trolltech.Qt.QImageIOHandlerFactoryInterface%3A\usr\lib\qt4\plugins\imageformats\libqtiff.so=2008-10-03T21:02:22, tiff, tif

[Qt]
customColors\0=4280690214
customColors\1=4284374622
customColors\2=4294967295
customColors\3=4280690214
customColors\4=4294967295
customColors\5=4294967295
customColors\6=4294967295
customColors\7=4294967295
customColors\8=4294967295
customColors\9=4294967295
customColors\10=4294967295
customColors\11=4294967295
customColors\12=4294967295
customColors\13=4294967295
customColors\14=4294967295
customColors\15=4294967295
font="Sans Serif,9,-1,5,50,0,0,0,0,0"
Palette\active=#d1d1d1, #5e5e5e, #8d8d8d, #757575, #2f2f2f, #3e3e3e, #ffffff, #ffffff, #ffffff, #5e5e5e, #5e5e5e, #000000, #262626, #ffffff, #0000ee, #52188b, #e8e8e8, #000000, #ffffdc, #000000
Palette\inactive=#d1d1d1, #5e5e5e, #8d8d8d, #6c6c6c, #2f2f2f, #3e3e3e, #ffffff, #ffffff, #ffffff, #5e5e5e, #5e5e5e, #000000, #262626, #ffffff, #0000ee, #52188b, #e8e8e8, #000000, #ffffdc, #000000
Palette\disabled=#808080, #5e5e5e, #8d8d8d, #6c6c6c, #2f2f2f, #3e3e3e, #808080, #ffffff, #808080, #5e5e5e, #5e5e5e, #000000, #262626, #808080, #0000ee, #52188b, #e8e8e8, #000000, #ffffdc, #000000
fontPath=@Invalid()
embedFonts=true
style=Plastique
doubleClickInterval=400
cursorFlashTime=1000
wheelScrollLines=3
resolveSymlinks=false
globalStrut\width=0
globalStrut\height=0
useRtlExtensions=false
XIMInputStyle=On The Spot
audiosink=Auto
videomode=Auto
GUIEffects=none
Font%20Substitutions\arial=helvetica
Font%20Substitutions\courier%20new=courier
Font%20Substitutions\sans%20serif=helvetica
Font%20Substitutions\times%20new%20roman=times
filedialog="@ByteArray(\0\0\0\xbe\0\0\0\x3\0\0\0\x1e\0\0\0\xff\0\0\0\0\0\0\0\x2\0\0\0^\0\0\x1x\x1\0\0\0\x6\x1\0\0\0\x1\0\0\0\x2\0\0\0\x5\x66ile:\0\0\0\x18\x66ile:///home/corenominal\0\0\0\x1\0\0\0\x32\0/\0h\0o\0m\0\x65\0/\0\x63\0o\0r\0\x65\0n\0o\0m\0i\0n\0\x61\0l\0/\0\x44\0r\0o\0p\0\x62\0o\0x\0\0\0\x32\0/\0h\0o\0m\0\x65\0/\0\x63\0o\0r\0\x65\0n\0o\0m\0i\0n\0\x61\0l\0/\0\x44\0r\0o\0p\0\x62\0o\0x\0\0\0~\0\0\0\xff\0\0\0\0\0\0\0\x1\0\0\0\0\0\0\0\0\x1\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\x1\xc3\0\0\0\x4\x1\x1\0\0\0\0\0\0\0\0\0\0\0\0\0\0\x64\xff\xff\xff\xff\0\0\0\x81\0\0\0\0\0\0\0\x4\0\0\0\xea\0\0\0\x1\0\0\0\0\0\0\0:\0\0\0\x1\0\0\0\0\0\0\0;\0\0\0\x1\0\0\0\0\0\0\0\x64\0\0\0\x1\0\0\0\0\0\0\0\x1)"


and now my player looks good
Thanx for ur help. I would not have known about this file if u hadn't told me
Thnax a lot

---

### Post by glord2005 on 2009-06-07
how am i supposed to tell that problem solved?
is there some icon called "solved' to click?

---

