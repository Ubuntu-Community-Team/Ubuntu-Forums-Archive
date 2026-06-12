---
title: "Problems compiling wxsvg-1.0.3 for DVDstyler 1.8.0.2"
date: 2010-03-27
forum: Multimedia Software
---

### Post by Statik on 2010-03-27
Hi all,

I'm trying to compile wxsvg-1.0.3 so that I can compile and install the latest version DVDStyler. I was following the older instructions here: [http://ubuntuforums.org/showthread.php?t=341791]("http://ubuntuforums.org/showthread.php?t=341791") and I've run into this error. Unfortunately, I can't make sense of the error. Can anyone help?

The last section of the compile:
```
Making all in svgview
make[1]: Entering directory `/home/statik/Desktop/wxsvg-1.0.3/svgview'
g++ -DPACKAGE_NAME=\"wxsvg\" -DPACKAGE_TARNAME=\"wxsvg\" -DPACKAGE_VERSION=\"1.0.2\" -DPACKAGE_STRING=\"wxsvg\ 1.0.2\" -DPACKAGE_BUGREPORT=\"wx-svg-users@lists.sourceforge.net\" -DPACKAGE=\"wxsvg\" -DVERSION=\"1.0.2\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DLT_OBJDIR=\".libs/\" -DHAVE_LIBEXPAT=1 -I. -I../include    -g -O2 -DUSE_RENDER_LIBART  -I/usr/lib/wx/include/gtk2-unicode-release-2.6 -I/usr/include/wx-2.6 -DGTK_NO_CHECK_CASTS -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -DNO_GCC_PRAGMA    -DUSE_FFMPEG   -MT svgview.o -MD -MP -MF .deps/svgview.Tpo -c -o svgview.o svgview.cpp
svgview.cpp: In member function ‘void MainFrame::OnSave(wxCommandEvent&)’:
svgview.cpp:120: error: ‘wxFD_SAVE’ was not declared in this scope
make[1]: *** [svgview.o] Error 1
make[1]: Leaving directory `/home/statik/Desktop/wxsvg-1.0.3/svgview'
make: *** [all-recursive] Error 1

```

Thanks!

Statik

---

### Post by mc4man on 2010-03-27
What version of libwxgtk do you have installed?, would suggest using 2.8
```

sudo apt-get install libwxgtk2.8-dev 
```

If need be you can also install and try the 2.6 version. wx-config is set in update-alternatives (by default, if installed, 2.8 will be used

> doug@doug-desktop:~$ sudo update-alternatives --config wx-config
There are 4 choices for the alternative wx-config (providing /usr/bin/wx-config).

  Selection    Path                                         Priority   Status
------------------------------------------------------------
* 0            /usr/lib/wx/config/gtk2-unicode-release-2.8   288       auto mode
  1            /usr/lib/wx/config/base-unicode-release-2.6   267       manual mode
  2            /usr/lib/wx/config/base-unicode-release-2.8   287       manual mode
  3            /usr/lib/wx/config/gtk2-unicode-release-2.6   268       manual mode
  4            /usr/lib/wx/config/gtk2-unicode-release-2.8   288       manual mode


---

