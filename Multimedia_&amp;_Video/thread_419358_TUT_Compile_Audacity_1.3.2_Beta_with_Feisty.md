---
title: "TUT: Compile Audacity 1.3.2 Beta with Feisty"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by delmore on 2007-04-22
I accidently posted this to the wrong place, here it is again (sorry) :

I found this great guide earlier today! Not only is it user friendly, its also very imformative... 

it doesnt just spit terminal commands for you to copy paste without any understanding oh whats going on... it educates you using simple comparisons... really great... 

i not only walked away understand HOW to compile... but also how to compile special features into Audacity and how to know what those special commands are... anyways :

[http://digg.com/linux_unix/Compile_the_Audacity_1_3_2_Beta_with_Ubuntu_Feisty](http://digg.com/linux_unix/Compile_the_Audacity_1_3_2_Beta_with_Ubuntu_Feisty)

---

### Post by 5-HT on 2007-04-23
Thanks a lot for posting this! There have been some great improvements in this version!

A few issues came up for me that I'm just posting solutions for in case anyone else encounters them:

1. I had to modify the syntax a bit from what was indicated in 'configure --help' to compile in support for optional packages.
   E.g. to add vorbis support, instead of using **--with-vorbis **I had to use **--with-libvorbis **(appropriate -dev packages will need to be installed).

2. Was getting some 'msgfmt:unknown command' errors that were solved my installing the **gettext **package

3. If using checkinstall, please edit version number from 'beta' to a proper version number (e.g., 1.3.2) or else the debian package build will fail.

---

### Post by jondecker76 on 2007-04-23
wow, excellent find - thanks for sharing!

---

### Post by mahiyar on 2007-04-28
Thanks, somehow I was having problems with current audacity with menus not showing and all. And I ended up reinventing the wheel of 5-HT, with exact same problems. Next time I will read a post completely. :)

---

### Post by mahiyar on 2007-04-28
5-HT even after compiling with-libvorbis, could not open ogg files, is that normal?

---

### Post by 5-HT on 2007-05-01
> **mahiyar said:**
> 5-HT even after compiling with-libvorbis, could not open ogg files, is that normal?

Did you have **libvorbis-dev** installed prior to compilation? That package in addition to adding '--with-libvorbis' during ./configure should allow ogg support.

---

### Post by zeus77 on 2007-05-16
Don't mean to exude negative karma, but I found the Howto to be a bit lacking... to compile a version of Audacity with full support for OGG/FLAC/MP3, you also need to install all these 10 development libraries:```
sudo apt-get install libwxbase2.6-dev libwxgtk2.6-dev wx2.6-headers libmad0-dev libvorbis-dev libogg-dev libflac-dev libflac++-dev libid3tag0-dev zlib1g-dev
```
and you don't need to worry about any command line options with ./configure, as everything will be enabled by default once these development libraries are in place.

After compiling, you can later remove the development libraries if you want (by replacing "sudo apt-get install ..." with "sudo apt-get remove --purge ..." above).  This will leave the necessary standard libraries (which should have been installed as dependencies), and will only remove the development libraries which aren't necessary to run -- they're only to necessary to compile.

zeus77

---

### Post by timmie on 2007-05-27
> **zeus77 said:**
> Don't mean to exude negative karma, but I found the Howto to be a bit lacking... to compile a version of Audacity with full support for OGG/FLAC/MP3, you also need to install all these 10 development libraries:```
sudo apt-get install libwxbase2.6-dev libwxgtk2.6-dev wx2.6-headers libmad0-dev libvorbis-dev libogg-dev libflac-dev libflac++-dev libid3tag0-dev zlib1g-dev
```


I had to install the following packages, too:
```
sudo apt-get install libwxbase2.6-dev libwxgtk2.6-dev wx2.6-headers libmad0-dev libvorbis-dev libogg-dev libflac-dev libflac++-dev libid3tag0-dev zlib1g-dev libtwolame0 libtwolame-dev libgtk-dev libwxgtk-dev 
twolame libasound2-dev libjack0.100.0-dev portaudio19-dev libgtk2.0-dev
```

Then I could install audacity 1.3.3

If you use the suffix as suggested in the Tutorial then Audacity won't recognize the locales!

```
./configure --program-suffix=beta
```

A workaround:
install with suffix and the do a 

```

cd /usr/local/share/locale/de/LC_MESSAGES
sudo ln -s audacitybeta.mo audacity.mo

```

After selecting Deutsch and a restart I had my language (German).

---

### Post by Janusz11 on 2007-05-27
Well, I've already installed all packages as advised, but still I can't build the Audacity (v1.3.3) package. 'make' always ends with the following error message: ```
generic/FileDialogPrivate.cpp:1499: error: no ‘void FileDialog::OnNew(wxCommandEvent&)’ member function declared in class ‘FileDialog’
generic/FileDialogPrivate.cpp:1508: error: no ‘void FileDialog::OnExtra(wxCommandEvent&)’ member function declared in class ‘FileDialog’
generic/FileDialogPrivate.cpp:1591: error: no ‘void FileDialog::UpdateControls()’ member function declared in class ‘FileDialog’
generic/FileDialogPrivate.cpp:86: warning: ‘int FileDataNameCompare(long int, long int, long int)’ defined but not used
generic/FileDialogPrivate.cpp:98: warning: ‘int FileDataSizeCompare(long int, long int, long int)’ defined but not used
generic/FileDialogPrivate.cpp:112: warning: ‘int FileDataTypeCompare(long int, long int, long int)’ defined but not used
generic/FileDialogPrivate.cpp:126: warning: ‘int FileDataTimeCompare(long int, long int, long int)’ defined but not used
generic/FileDialogPrivate.cpp:409: warning: ‘sm_eventTableEntries’ defined but not used
make[2]: *** [generic/FileDialogPrivate.o] Error 1
make[2]: Leaving directory `/home/eljot/audacity-src-1.3.3-beta/lib-src/FileDialog'
make[1]: *** [FileDialog-recursive] Error 2
make[1]: Leaving directory `/home/eljot/audacity-src-1.3.3-beta/lib-src'
make: *** [audacity] Error 2
```

This is just the tail of it, btw. 

Any ideas? I really need this new version!


Ubuntustudio here, btw.

---

### Post by timmie on 2007-05-27
make shure you have
```

sudo apt-get install** libwxbase2.6-dev libwxgtk2.6-dev wx2.6-headers** libmad0-dev libvorbis-dev libogg-dev libflac-dev libflac++-dev libid3tag0-dev zlib1g-dev libtwolame0 libtwolame-dev libgtk-dev libwxgtk-dev twolame libasound2-dev libjack0.100.0-dev portaudio19-dev **libgtk2.0-dev**

```

I think you are lacking the bold one.

Greetings.

---

### Post by Janusz11 on 2007-05-28
Thanks alot mate!

I was indeed missing one (or two?) of those packages. But after I've installed them compiling went smooth as silk and I now have v1.3.3-beta up and running here. Great!

Thanks again.

---

### Post by timmie on 2007-05-28
The suffix beta will disable the possibility to use a localized interface in your language!

If you need a non-english localisation see a forum post in the Audacity forum:
[no german locale after configured with suffix](http://audacityteam.org/forum/thread/5199)

---

### Post by wilberfan on 2007-06-15
Very nice thread!   Very helpful!  

I, like 5-HT, had to install "gettext" (I didn't realize there was a separate one for KDE!).   ./configure, make, sudo make install, and bingo!  (I ended up installing while under gnome, though....  Not sure if it would have worked or not under Kubuntu?)   I did NOT have to use any '--with'  parameters

I've only done a quick test re: ogg, but reading and writing that format were both successful!

I *really* like this version of Audacity, too...

:D

---

### Post by drworm01 on 2007-09-16
> **Janusz11 said:**
> Well, I've already installed all packages as advised, but still I can't build the Audacity (v1.3.3) package. 'make' always ends with the following error message: ```
generic/FileDialogPrivate.cpp:1499: error: no ‘void FileDialog::OnNew(wxCommandEvent&)’ member function declared in class ‘FileDialog’
generic/FileDialogPrivate.cpp:1508: error: no ‘void FileDialog::OnExtra(wxCommandEvent&)’ member function declared in class ‘FileDialog’
generic/FileDialogPrivate.cpp:1591: error: no ‘void FileDialog::UpdateControls()’ member function declared in class ‘FileDialog’
generic/FileDialogPrivate.cpp:86: warning: ‘int FileDataNameCompare(long int, long int, long int)’ defined but not used
generic/FileDialogPrivate.cpp:98: warning: ‘int FileDataSizeCompare(long int, long int, long int)’ defined but not used
generic/FileDialogPrivate.cpp:112: warning: ‘int FileDataTypeCompare(long int, long int, long int)’ defined but not used
generic/FileDialogPrivate.cpp:126: warning: ‘int FileDataTimeCompare(long int, long int, long int)’ defined but not used
generic/FileDialogPrivate.cpp:409: warning: ‘sm_eventTableEntries’ defined but not used
make[2]: *** [generic/FileDialogPrivate.o] Error 1
make[2]: Leaving directory `/home/eljot/audacity-src-1.3.3-beta/lib-src/FileDialog'
make[1]: *** [FileDialog-recursive] Error 2
make[1]: Leaving directory `/home/eljot/audacity-src-1.3.3-beta/lib-src'
make: *** [audacity] Error 2
```

This is just the tail of it, btw. 

I have the same problem but when I try timmie's soltuion:

```
sudo apt-get install libwxbase2.6-dev libwxgtk2.6-dev wx2.6-headers libmad0-dev libvorbis-dev libogg-dev libflac-dev libflac++-dev libid3tag0-dev zlib1g-dev libtwolame0 libtwolame-dev libgtk-dev libwxgtk-dev twolame libasound2-dev libjack0.100.0-dev portaudio19-dev libgtk2.0-dev
```

I get this response:

```
Note, selecting libgtk1.2-dev instead of libgtk-dev
libgtk1.2-dev is already the newest version.
Note, selecting libwxgtk2.4-dev instead of libwxgtk-dev
libwxgtk2.4-dev is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.12) but it is not going to be installed
                 Depends: libcairo2-dev (>= 1.2.0) but it is not going to be installed
E: Broken packages
```

What a difference a few months makes. Any help would be much appreciated. Audacity was the only reason I stuck with Windows as long as I did and now that I've completely scrapped my Windows install, I really need Audacity to work.

Thanks for any help you can give.

D-

---

