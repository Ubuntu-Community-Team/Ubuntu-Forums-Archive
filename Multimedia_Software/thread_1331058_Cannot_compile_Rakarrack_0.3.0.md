---
title: "Cannot compile Rakarrack 0.3.0"
date: 2009-11-18
forum: Multimedia Software
---

### Post by rxweitz on 2009-11-18
I just installed Ubuntu 9.10 (karmic koala) for AMD64, and everything seems to be working fine, but I'm having trouble installing the 0.3.0 version of Rakarrack.  I've checked and double-checked all of the dependencies, but every time I run make, I get the following output:

Making all in src
make[1]: Entering directory `/home/user/Downloads/rakarrack-0.3.0/src'
make  all-am
make[2]: Entering directory `/home/user/Downloads/rakarrack-0.3.0/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I.     -O2 -Wall -msse2 -fno-rtti -pipe -ffunction-sections -fomit-frame-pointer -Wno-format-y2k -fPIC -fno-exceptions -fno-strict-aliasing -I/usr/local/include -I/usr/local/include/FL/images -I/usr/include/freetype2 -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_THREAD_SAFE -D_REENTRANT   -MT rakarrack.o -MD -MP -MF ".deps/rakarrack.Tpo" -c -o rakarrack.o rakarrack.cxx; \
    then mv -f ".deps/rakarrack.Tpo" ".deps/rakarrack.Po"; else rm -f ".deps/rakarrack.Tpo"; exit 1; fi
rakarrack.cxx: In member function ‘void RKRGUI::save_stat(int)’:
rakarrack.cxx:10419: error: call of overloaded ‘set(char*, Fl_Color&)’ is ambiguous
/usr/local/include/Fl/Fl_Preferences.H:99: note: candidates are: char Fl_Preferences::set(const char*, int)
/usr/local/include/Fl/Fl_Preferences.H:100: note:                 char Fl_Preferences::set(const char*, float)
/usr/local/include/Fl/Fl_Preferences.H:102: note:                 char Fl_Preferences::set(const char*, double)
/usr/local/include/Fl/Fl_Preferences.H:104: note:                 char Fl_Preferences::set(const char*, const char*) <near match>
rakarrack.cxx:10420: error: call of overloaded ‘set(char*, Fl_Color&)’ is ambiguous
/usr/local/include/Fl/Fl_Preferences.H:99: note: candidates are: char Fl_Preferences::set(const char*, int)
/usr/local/include/Fl/Fl_Preferences.H:100: note:                 char Fl_Preferences::set(const char*, float)
/usr/local/include/Fl/Fl_Preferences.H:102: note:                 char Fl_Preferences::set(const char*, double)
/usr/local/include/Fl/Fl_Preferences.H:104: note:                 char Fl_Preferences::set(const char*, const char*) <near match>
rakarrack.cxx:10421: error: call of overloaded ‘set(char*, Fl_Color&)’ is ambiguous
/usr/local/include/Fl/Fl_Preferences.H:99: note: candidates are: char Fl_Preferences::set(const char*, int)
/usr/local/include/Fl/Fl_Preferences.H:100: note:                 char Fl_Preferences::set(const char*, float)
/usr/local/include/Fl/Fl_Preferences.H:102: note:                 char Fl_Preferences::set(const char*, double)
/usr/local/include/Fl/Fl_Preferences.H:104: note:                 char Fl_Preferences::set(const char*, const char*) <near match>
rakarrack.cxx:10422: error: call of overloaded ‘set(char*, Fl_Color&)’ is ambiguous
/usr/local/include/Fl/Fl_Preferences.H:99: note: candidates are: char Fl_Preferences::set(const char*, int)
/usr/local/include/Fl/Fl_Preferences.H:100: note:                 char Fl_Preferences::set(const char*, float)
/usr/local/include/Fl/Fl_Preferences.H:102: note:                 char Fl_Preferences::set(const char*, double)
/usr/local/include/Fl/Fl_Preferences.H:104: note:                 char Fl_Preferences::set(const char*, const char*) <near match>
rakarrack.cxx: In member function ‘void RKRGUI::preset_click_i(Fl_Button*, void*)’:
rakarrack.cxx:10825: warning: format not a string literal and no format arguments
make[2]: *** [rakarrack.o] Error 1
make[2]: Leaving directory `/home/user/Downloads/rakarrack-0.3.0/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/user/Downloads/rakarrack-0.3.0/src'
make: *** [all-recursive] Error 1

---

### Post by transmogrifox on 2009-11-20
I use Debian Lenny, but I am thinking the same applies to Ubuntu:
Just because you have the package for a given dependency involved does not necessarily mean you have the current enough version.

Most Linux distributions provide a way around this:
*-dev packages.

In the case of your 0.3.0 build, it looks like you need a more recent version of fltk.

On my Debian Lenny box, the package names are:
libfltk1.1
libfltk1.1-dev

You would need to also install the libfltk1.1-dev package if using Debian Lenny.  Ubuntu will have something for libfltk with a very similar name.  The main point is install the dependency, then the '-dev' package for the dependency as well.

I have to put in my plug since I have been developing some things for Rakarrack recently:
If you are successful compiling version 0.3.0, then consider the most current CVS version.  Here are some features added into CVS since the release of 0.3.0:
1) Josep has expanded MIDI support, so you can plug in a MIDI control surface and adjust parameters in Rakarrack (a real big plus for people who use it live).
2) I have made some significant bug fixes to the compressor.  I have also added some features.  
3) I have just submitted an analog phaser modeling effect.  The "beta" version has been sent to Josep, and should be hitting CVS real soon. If you pay attention to the project activity, you can tell when it's time to update your CVS copy when the sourceforge page notes code commits.  If you want to hear audio samples of the "pre-alpha" version, you can download the tar.gz from my blog, rakahack.blogspot.com .  The most recent beta sounds a little better, but I haven't recorded any samples from this one yet.

Things get broken from time to time in CVS.  Right now the presets don't work because of added features that break the preset system.  It's just a matter of updating things, but it will happen when it happens. That is said to encourage use of the official release 0.3.0 if you want stability over recent features.  I don't know when the rakarrack team intends to issue the next stable release, but it will be pleasantly improved at that point.

---

### Post by Oasu4g on 2009-12-31
I'm having the same problem here. And I have the most recent version of fltk, with developer libs installed. Did you get this to work, rxweitz?

---

### Post by transmogrifox on 2010-01-19
Rakarrack will be releasing Version 0.4.2 in a couple days.  There have been some bug fixes that I think will help this problem...and of course features mentioned earlier.

I don't know how quickly Ubuntu repositories will get the recent release, but if you try to build 0.4.2, please report back if you do have problems compiling.  Thanks.

---

