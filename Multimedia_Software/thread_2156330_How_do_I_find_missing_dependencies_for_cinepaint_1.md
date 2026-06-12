---
title: "How do I find missing dependencies for cinepaint 1.0-4 Ubuntu 13.04"
date: 2013-06-21
forum: Multimedia Software
---

### Post by Derelinquat fenestras on 2013-06-21
[COLOR=#333333][FONT=UbuntuRegular]I am a photojournalist/digital photo artist and I am getting into video editing projects I have used GIMP for my photo editing for years...[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I've been doing some research on other alternatives which may have better quality results and I found Cinepaint. I found that there is a lack of .deb packages for installation into Ubuntu, so I tried 2 things.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]1) downloaded from SourceForge the .rpm package and converted it to .deb with alien. It seemed to work/open properly, but I can not get it to open .jpeg, .jpg, .JPEG, .JPG, ot .TIFF files... so I wasn't able to make use/test the program...[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]2) downloaded the .tar.gz from SourceForge and went to compile it... I first installed the list of dependencies provided in the install file, then I ran:[/FONT][/COLOR]
```

sudo ./configure 
```[COLOR=#333333][FONT=UbuntuRegular]It seemed to run fine until the end and I got an error output:[/FONT][/COLOR]
```

=================================================================                                 Configuration Results
GTK CinePaint Version 1.0-4
General dependencies:
Gtk2 toolkit                             yes    
2.24.17DnD support                  no
littleCMS                                 no     !! CinePaint will not build without !!
Oyranos                                  no

Plug-ins with external dependencies:
Python plug-in:                         no
OpenEXR plug-in:                      yes    
OpenEXR Tiff plug-in:                 yes
PNG plug-in:                             yes    
libpng 1.2.49Jpeg plug-in:           yes
Print plug-in:                            no
FLTK dependent plug-ins:            no     !! CinePaint will not build without !!
Thread dependent plug-ins:         no     !! ICC Examin will not build !!
Flex dependent plug-ins:             yes =================================================================
configure: error: !!! An ERROR occured !!!Please check the above messages to see why.For bug reports please include the complete above output.
```
[COLOR=#333333][FONT=UbuntuRegular]
I'm very interested in trying this program, but because the error list doesn't give specific package names, I'm not sure how to locate/install the missing dependencies.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]So I was wondering if anyone knows where to find the missing dependencies or can advise me as to how to locate them myself[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]or[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Has any suggestions about how to get the .rpm --> .deb conversion to work properly[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I usually research Ubuntu forums/askUbuntu/Google to see if there is relevant content to my problem before I post a question, however I was unable to find any content relative to Ubuntu past 8.04/.10.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I will be grateful for any suggestions or links to documentation relevant to new versions of Ubuntu or even a way to find/install a .deb package of filmgimp or glasgow or similar programs that will work on Ubuntu...[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Thanks for your time[/FONT][/COLOR]

---

### Post by mc4man on 2013-06-21
Note_ the below is to show how to configure & get  cinepaint to build it (cinepaint), though it  appears to Not be that useful/usable  in Debian/Ubuntu. So really just for info purposes. Whether it works well in a supported distro no clue, you'd have to try

So - 

Your best tool is to use synaptic & search a truncated name of missing, usually looking a -dev package.

Searching cms will return results for both liblcms1-dev & liblcms2-dev, which one is needed you'd have to see.
fltk will likewise return 2 possible, libfltk1.1-dev & libfltk1.3-dev (I'd say the earlier are good for both

What you want to do is keep running the ./configure until it fills in fully, just because it meets the min to build doesn't mean you'll get all you may want. Read back thru the full configure each time.

So with a little ./configure > search in synaptic, install a -dev, ect. get this - 
```
=================================================================
              Configuration Results

GTK CinePaint Version 1.0-4


General dependencies:
   Gtk2 toolkit                 yes    2.24.17
   DnD support                  yes    X11/Xmu
   littleCMS                    yes    lcms 1.19
   Oyranos                      no

Plug-ins with external dependencies:
   Python plug-in:              no
   OpenEXR plug-in:             yes    OpenEXR 1.6.1
   Tiff plug-in:                yes
   PNG plug-in:                 yes    libpng 1.2.49
   Jpeg plug-in:                yes
   Print plug-in:               yes    Gutenprint 5.2.9
   FLTK dependent plug-ins:     yes    bracketing_to_hdr collect pdf
   Thread dependent plug-ins:   yes    icc_examine
 [COLOR="#FF0000"]  Flex dependent plug-ins:     yes    iol[/COLOR]
=================================================================
```

In addition to the 2 mentioned packages above (liblcms1-dev libfltk1.1-dev
libopenexr-dev 
libgutenprintui2-dev
libgutenprint-dev 
libxmu-dev
[COLOR="#FF0000"]flex libfl-dev[/COLOR]

The deps above in red  will enable the red configure option, you don't want them as it likely will cause a build error that I've no reason to look in to...
 
The other issue that some of the individual makefiles (makefile.am in various folders) have their linking in the wrong order so your build will fail. The proper way would be to identify which ones & patch. In this case no reason to as the app will likely not be worth using or using very often. A muck around all the linking issues will be to use an LDFLAGS= in the configure.

So if you wanted to try install the above mentioned packages, make sure the red ones are not installed.
Then configure with - 
```
make distclean
```

```
./configure LDFLAGS="-lX11 -lstdc++ -lm"
```

screen 3 shows  1 ex. of a makefile that was ordered wrong, -lX11 -lstdc++ -lm are at the beginning (& still are, hence "muck around"), the LD flag added them to the end where they belong

If it succeeds then a make & sudo make install followed by a sudo ldconfig

The reason  files don't open is None of the folder paths are filled in, see screen 2 for filled in here. The palette & gradients paths, if enabled will segfault cinepaint,  so don't

Edit: read here for some alt.
[http://comments.gmane.org/gmane.comp.video.cinepaint.user/1364](http://comments.gmane.org/gmane.comp.video.cinepaint.user/1364)

---

### Post by Derelinquat fenestras on 2013-06-24
Thank you for your reply...

I followed your instructions and installed the missing dependencies via synaptic package manager..

It seemed to go okay, and when I ran

```
sudo make
sudo make install
```

It ran for much longer than it had previously and did not output any recursive errors...

However when I tried to run Cinepaint, I got this output:

```
cinepaint: error while loading shared libraries: libcinepaint.so.1: cannot open shared object file: No such file or directory

```
I'm getting pretty discouraged, but I still would like to try Cinepaint... I've never successfully built an application in this way, is there a simple way to uninstall, since the program did not come out of any of my existing repositories?

Would you recommend a distro that will install .rpms?
I'm pretty sure thats Fedora... do you know perhaps a lighter desktop than Fedora?  I've tried it before, but my system runs pretty slow with standard Gnome 3.6 and above...

---

### Post by Kujua on 2013-06-24
Perhaps setting LD_LIBRARY_PATH might help, since you said installation was successful.

Find the directory where libcinepaint.so.1 is installed: ' locate libcinepaint.so.1 '
Then set LD_LIBRARY_PATH to that directory: ' export LD_LIBRARY_PATH=path-to-dir '
Then start the application.

---

### Post by mc4man on 2013-06-24
> **Derelinquat fenestras said:**
> Thank you for your reply...

I followed your instructions and installed the missing dependencies via synaptic package manager..

It seemed to go okay, and when I ran

```
sudo make
sudo make install
```

It ran for much longer than it had previously and did not output any recursive errors...

However when I tried to run Cinepaint, I got this output:

```
cinepaint: error while loading shared libraries: libcinepaint.so.1: cannot open shared object file: No such file or directory

```

You really didn't quite follow what I posted - 
> If it succeeds then a make & sudo make install followed by a [COLOR="#FF0000"]sudo ldconfig[/COLOR]
That's why you get the "error while loading shared libraries"

So just run that command or if you happened to install anything since posting thru apt-get ,synaptic or software center it likely would have run an ldconfig for you.

---

### Post by Yellow Pasque on 2013-06-24
> **Derelinquat fenestras said:**
> Would you recommend a distro that will install .rpms? I'm pretty sure thats Fedora... do you know perhaps a lighter desktop than Fedora? 

If what mc4man suggested doesn't work, try alien (installs rpm's in debian distros) before trying a whole other distro.

---

### Post by mc4man on 2013-06-24
> **Temüjin said:**
>  try alien (installs rpm's in debian distros) before trying a whole other distro.
I think he did before & it's quite possible the converted rpm works as well as a built version (which isn't all that well

Like a self built  the problem with the converted rpm would be that the local config file has no paths entered.

---

### Post by wewecat on 2013-06-25
/usr/bin$ ./cinepaint
./cinepaint: error while loading shared libraries: libcinepaint.so.1: cannot open shared object file: No such file or directory
:?:

$ sudo make distclean
[sudo] password for wewe: 
make: *** &#27809;&#26377;&#35268;&#21017;&#21487;&#20197;&#21019;&#24314;&#30446;&#26631;&#8220;distclean&#8221;&#12290; &#20572;&#27490;&#12290;

---

### Post by Derelinquat fenestras on 2013-06-25
Thank you, mc4man, for all of your help... Seems like its almost there.  

I ran sudo ldconfig and it opened with no problem,  but none of the folder paths were filled in, as you said...

I filled in the paths, but I think I made a mistake, because now when I try to start it, I get the splash screen for Cinepaint, then it crashes. ..

Do you know if there is a way that I can edit the preferences via text editor or some other way, or will I need to uninstall/start over?

Please forgive my ignorance, but how would I go about uninstalling it?  I've never successfully installed a program by building it, so not sure how to remove it...

would

sudo apt-get remove cinepaint

do the job, or is there a different method?

---

### Post by mc4man on 2013-06-25
> **Derelinquat fenestras said:**
> Thank you, mc4man, for all of your help... Seems like its almost there.  

I ran sudo ldconfig and it opened with no problem,  but none of the folder paths were filled in, as you said...

I filled in the paths, but I think I made a mistake, because now when I try to start it, I get the splash screen for Cinepaint, then it crashes. ..

Do you know if there is a way that I can edit the preferences via text editor or some other way, or will I need to uninstall/start over?

Please forgive my ignorance, but how would I go about uninstalling it?  I've never successfully installed a program by building it, so not sure how to remove it...

would

sudo apt-get remove cinepaint

do the job, or is there a different method?


From my other post - 
> The palette & gradients paths, if enabled will segfault cinepaint, so don't
You can open your home folder > view > show hidden files (or ctrl+h) & you should see a folder .cinepaint
Inside is a file cinepaintrc, if you open in a text editor you can remove the bad entries, should have only be filled in as shown in previous screenshot. (screen #2 - in cinepaint's preferences
Or just remove cinepaintrc & try again  with paths

To uninstall just cd to cinepaint source & run 
```
sudo make uninstall
```

---

### Post by Derelinquat fenestras on 2013-06-25
Okay, so I edited the file, and Cinepaint started up again.  I filled in the paths as shown, then restarted the program and it crashes on splash screen again...

I attempted to run it from the terminal and got the following output:
```

(cinepaint:4473): Gtk-WARNING **: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().
cinepaint fatal error: sigsegv caught
cinepaint (pid:4473): [E]xit, [H]alt, show [S]tack trace or [P]roceed: 

```

Exit obviously kills the process, Halt and Stack trace don't seem to do anything, and Proceed outputs:

```

(cinepaint:4473): Gtk-CRITICAL **: IA__gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed


(cinepaint:4473): Gtk-CRITICAL **: IA__gtk_object_destroy: assertion `object != NULL' failed


(cinepaint:4473): Gtk-CRITICAL **: IA__gtk_object_unref: assertion `GTK_IS_OBJECT (object)' failed
cinepaint fatal error: sigsegv caught

```

Not sure how to proceed... this is the same output as when I had entered the incorrect paths...

---

### Post by Derelinquat fenestras on 2013-06-25
Okay, so I uninstalled and began to rebuild...

ran 
```

sudo make distclean

```

Which ran fine...

Then I ran :

```

./configure LDFLAGS="-lx11 -lstdc++ -lm"

```

and got the following output:
```

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether build environment is sane... yes
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: in `/home/jacob/cinepaint-1.0-4':
configure: error: C compiler cannot create executables
See `config.log' for more details.

```

Not sure what to make of the last 2 lines...  Not sure if I should go ahead with make && make install...

I will stand by...
Please let me know if I'm running futile cycles...

---

### Post by mc4man on 2013-06-25
> **Derelinquat fenestras said:**
> Okay, so I uninstalled and began to rebuild...

ran 
```

sudo make distclean

```
 


Who told you to run a distclean as sudo?

If inclined, from the top - 

Delete your current source folder (cinepaint-1.0-4), the whole folder
Delete the .cinepaint folder in your home folder
**In other words All gone**

Extract cinepaint-1.0-4.tar.gz, cd to the newly extracted cinepaint-1.0-4 folder

```
./configure LDFLAGS="-lX11 -lstdc++ -lm"
```
```
make
```
```
sudo make install && sudo ldconfig
```

Run cinepaint, open File >  Preferences, ** just add path to plugins **(/usr/local/lib/cinepaint/1.0-4/plug-ins
Close cinepaint, reopen, see if plugins are loaded

Ex. from terminal
> ~$ cinepaint
Locale found in /usr/local/share/locale

(cinepaint:9526): Gdk-CRITICAL **  ect, ect. ect
Searching plug-ins in path: /usr/local/lib/cinepaint/1.0-4/plug-ins
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/hdr
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/unsharp
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/cineon
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/gauss_rle
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/screenshot
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/mblur
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/rotate
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/decompose
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/compose
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/dbbrowser
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/fits
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/snoise
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/openexr
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/png
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/bmp
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/sobel
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/collect
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/print
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/spread
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/pic
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/psd
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/xwd
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/tga
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/bracketing_to_hdr
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/iff
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/gifload
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/noisify
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/psd_save
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/dicom
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/blur
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/tiff
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/median
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/pdf
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/rawphoto
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/script-fu
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/jpeg
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/sgi
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/edge
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/minimum
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/gbr
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/pnm
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/retinex
Loading plug-in: /usr/local/lib/cinepaint/1.0-4/plug-ins/sharpen
plugin count = 43
script-fu.c:115
/usr/local/lib/cinepaint/1.0-4/plug-ins/script-fu


If desired now add path to brushes (/usr/local/share/cinepaint/1.0-4/brushes
close & reopen, see if it crashes. If not then try to add path to patterns if desired. (/usr/local/share/cinepaint/1.0-4/patterns
close, reopen ect.
If crashing on brushes or patterns then open cinepaintrc  & delete the entry, all 3 work here.
Don't try to add any other paths

relevant section of cinepaintrc here
> #- Next line modified by GIMP on 2013-06-21 21:51:52
(plug-in-path "/usr/local/lib/cinepaint/1.0-4/plug-ins")

#- Next line added by GIMP on 2013-06-21 22:03:32
(brush-path "/usr/local/share/cinepaint/1.0-4/brushes")

#- Next line added by GIMP on 2013-06-21 22:03:32
(pattern-path "/usr/local/share/cinepaint/1.0-4/patterns")

---

### Post by Derelinquat fenestras on 2013-06-25
Thank you, as always.

I am starting over.  I guess I'm not too sure when to use sudo, I've kind of gotten in the habit of using it for most commands...

Does it make a difference when using it with make distclean?

I earnestly want to learn...
Thank you for all of your help

---

### Post by Derelinquat fenestras on 2013-06-26
Got it to work!  Hallelujah!

It turned out to be the gradients path that broke it for some reason, but all of the other one work just fine!

Thanks for all of the help!

I do have one more question, however...

Since I built this myself, when it comes to updating, I'll have to download and build a replacement, right?

---

### Post by mc4man on 2013-06-26
> **Derelinquat fenestras said:**
> Thank you, as always.

I am starting over.  I guess I'm not too sure when to use sudo, I've kind of gotten in the habit of using it for most commands...



When doing builds in your home folder only use root (sudo) to install/uninstall,  (if installing to your home folder then don't use sudo there either

> **Derelinquat fenestras said:**
> Got it to work!  Hallelujah!

It turned out to be the gradients path that broke it for some reason, but all of the other one work just fine!

Thanks for all of the help!

I do have one more question, however...

Since I built this myself, when it comes to updating, I'll have to download and build a replacement, right?
Correct. 

You likely can just get a new source, extract, configure, make & install letting it overwrite your previous install or before installing a new source go to old source & run an uninstall.

Another option would be to use checkinstall  instead of make install, then it's basically like any other package.

---

### Post by wewecat on 2013-06-27
God, seeking to compile detailed tutorial command thanks ~ ~ ~ ~ ~
My computer configuration: ubuntu studio 13.04 64bit ~! i5 + GTX 570

---

