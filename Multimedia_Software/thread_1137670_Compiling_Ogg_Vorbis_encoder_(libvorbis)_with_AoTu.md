---
title: "Compiling Ogg Vorbis encoder (libvorbis) with AoTuV tuning"
date: 2009-04-25
forum: Multimedia Software
---

### Post by ariel on 2009-04-25
[Update: 2011/Nov: this works fine with 11.10 as well]

I just installed jaunty/ubuntu 9.04 and I couldn't find any .deb out there of libvorbis for jaunty/amd64 including a recent AoTuv patch, since Ubuntu uses the original Xiph version of libvorbis with a very old version of the patch.

I turned out that compiling a new patched libvorbis was quite simple [1]. 

First choose the version you want and get the source code from here: 
[http://www.geocities.jp/aoyoume/aotuv/](http://www.geocities.jp/aoyoume/aotuv/)

If you've never built from source in your box, get the basic tools:
```
sudo *apt*-*get install build*-*essential* 
```Then get libvorbis build dependencies:
```
sudo *apt*-*get build-dep libvorbis* 
```Finally, open a terminal in the folder where you extracted aotuv's source code and do:
```
CFLAGS=-fno-strict-aliasing sh ./configure --prefix=/usr
make 
sudo make install 

``````

[COLOR=Blue]Note if Using Ubuntu 11.10, Aotuv 6.03 (latest as of November 2011):[/COLOR]

In addition to the above, you will need: 

sudo cp /usr/lib/libvorbis.so.0.4.5 /usr/lib/x86_64-linux-gnu/
sudo cp /usr/lib/libvorbisfile.so.3.3.4 /usr/lib/x86_64-linux-gnu/
sudo cp /usr/lib/libvorbisenc.so.2.0.8 /usr/lib/x86_64-linux-gnu/

Reason: for reasons beyond me, in ubuntu 11.10 oggenc uses
the libvorbis libraries that reside in the folder /usr/lib/x86_64-linux-gnu/, 
which contains a binary copy of the original libvorbis - which needs
 to be updated with the newly compiled one that resides int the default /usr/lib folder.

Without this, oggenc/gstreamer/shntool will keep using the old libvorbis


```That should be it.

To test that oggenc is in fact using aotuv: encode a file to ogg using any tool (or command line via oggenc), then do:
```
ogginfo filename.ogg
```The output should look like this:
```
New logical stream (#1, serial: 2d171ce4): type vorbis
Vorbis headers parsed for stream 1, information follows...
Version: 0
[COLOR=Blue]Vendor: AO; aoTuV b5d [20090301] (based on Xiph.Org's libVorbis)[/COLOR]

```If for whatever reason you want to revert back to ubuntu's default libvorbis, just reinstall the libvorbis package using apt or synaptics.

```
sudo apt-get instsall vorbis-tools libvorbis0a libvorbisenc2 libvorbisfile3  --reinstall
```
For more info:
[1] [http://wiki.hydrogenaudio.org/index.php?title=Compiling_aoTuV](http://wiki.hydrogenaudio.org/index.php?title=Compiling_aoTuV)[IMG]chrome://dictionarytip/skin/book.png[/IMG]

---

### Post by sojyujai on 2009-05-06
Thanks for this.

I did an upgrade from Intrepid to Jaunty and noticed that pjssilva's ppa repository with the aotuv patched versions of libvorbis hasn't been updated for jaunty (yet anyway).

After the upgrade I still have the aotuv patched versions I originally installed in Intrepid so it wasn't such a problem for me - but it's still nice to see this howto in case I ever have to do a clean install or some other problem comes up.

---

### Post by l3lackEyedAngels on 2010-06-02
I'm running Lucid (10.04). I tried the procedure in the OP. Now I get a" segmentation fault" when I run oggenc. Can someone help me fix this problem, please?
```
kurt@El-Savior:~/Music$ oggenc -q8 '/media/My Book_/Media/Music/Pink Floyd/Pink Floyd - Wish You Were Here (Mastersound Gold CD) (1975) [FLAC]/04 - Wish You Were Here.flac'
Opening with flac module: FLAC file reader
Encoding "/media/My Book_/Media/Music/Pink Floyd/Pink Floyd - Wish You Were Here (Mastersound Gold CD) (1975) [FLAC]/04 - Wish You Were Here.flac" to 
         "/media/My Book_/Media/Music/Pink Floyd/Pink Floyd - Wish You Were Here (Mastersound Gold CD) (1975) [FLAC]/04 - Wish You Were Here.ogg" 
at quality 8.00
Segmentation fault
```

EDIT: I got rid of the problem. All I did was to add [Tobias Wolfe's PPA]("https://launchpad.net/%7Etowolf/+archive/codecs?field.series_filter=karmic") for karmic to my sources and then force and lock his version of libvorbis in the package manager. You have to force and lock his version or else Ubuntu will try to "upgrade". To do that, select the libvorbis packages (libvorbisenc2, libvorbis0a, and libvorbisfile3) and then Package-->Force Version. Then select Tobias's version (1.2.2+aotuv-b5.7...). You have to go one at a time. Click Apply. Then, one at a time, select each libvorbis package again and Package-->Lock Version.

---

### Post by ariel on 2010-06-03
> **l3lackEyedAngels said:**
> I'm running Lucid (10.04). I tried the procedure in the OP. Now I get a" segmentation fault" when I run oggenc. Can someone help me fix this problem, please?
```
kurt@El-Savior:~/Music$ oggenc -q8 '/media/My Book_/Media/Music/Pink Floyd/Pink Floyd - Wish You Were Here (Mastersound Gold CD) (1975) [FLAC]/04 - Wish You Were Here.flac'
Opening with flac module: FLAC file reader
Encoding "/media/My Book_/Media/Music/Pink Floyd/Pink Floyd - Wish You Were Here (Mastersound Gold CD) (1975) [FLAC]/04 - Wish You Were Here.flac" to 
         "/media/My Book_/Media/Music/Pink Floyd/Pink Floyd - Wish You Were Here (Mastersound Gold CD) (1975) [FLAC]/04 - Wish You Were Here.ogg" 
at quality 8.00
Segmentation fault
```EDIT: I got rid of the problem. All I did was to add [Tobias Wolfe's PPA]("https://launchpad.net/%7Etowolf/+archive/codecs?field.series_filter=karmic") for karmic to my sources and then force and lock his version of libvorbis in the package manager. You have to force and lock his version or else Ubuntu will try to "upgrade". To do that, select the libvorbis packages (libvorbisenc2, libvorbis0a, and libvorbisfile3) and then Package-->Force Version. Then select Tobias's version (1.2.2+aotuv-b5.7...). You have to go one at a time. Click Apply. Then, one at a time, select each libvorbis package again and Package-->Lock Version.

For the record, you can always roll-back to the original package version by reinstalling:

sudo apt-get instsall vorbis-tools libvorbis0a libvorbisenc2 libvorbisfile3  --reinstall

For me, the instructions worked in Lucid (clean install) with no crash however, after installing aotuv (sudo make install) I found that aotuv was not being used by oggenc, instead ubuntu's default ogg encoder version was still used.

After some tinkering, I realized that the following was needed (after the "sudo make install"):

(Do at your own risk!)

```
cd /usr/lib
sudo rm libvorbisenc.so.2
sudo ln -s libvorbisenc.so.2.0.4 libvorbisenc.so.2

sudo rm libvorbisfile.so.3
sudo ln -s libvorbisfile.so.3.3.0 libvorbisfile.so.3

sudo rm libvorbis.so.0
sudo ln -s libvorbis.so.0.4.1 libvorbis.so.0

```

This was needed because aotuv's code compilation & installation produces ogg libraries that have a version number that is one notch below ubuntu lucid's, which will take precedence.

If any problem occurs, just roll-back with this:
sudo apt-get instsall vorbis-tools libvorbis0a libvorbisenc2 libvorbisfile3  --reinstall

---

### Post by hmuenz on 2010-06-16
@ariel:

I've tried your sollution, and initially it seemed to work. But after updating **any **package, the links point to the files of the ubuntu package again. So it's better to use the karmic package of Tobias Wolf's ppa. Just enter the ppa to your sources and force this version for the respective packages.

Heiner

---

### Post by ariel on 2010-06-16
> **hmuenz said:**
> @ariel:

I've tried your sollution, and initially it seemed to work. But after updating **any **package, the links point to the files of the ubuntu package again. So it's better to use the karmic package of Tobias Wolf's ppa. Just enter the ppa to your sources and force this version for the respective packages.

Heiner

Thanks for advising! I didn't notice, you are totally right.

The question for you now is - how do you force the installation of Tobia's package? that's the part I'm missing, I didn't know this was possible. TIA

---

### Post by hmuenz on 2010-06-17
It is just like [B]l3lackEyedAngels has posted:

[/B]
[LIST=1]
[*]Open a terminal and type "sudo add-apt-repository **ppa:towolf/codecs**"
[*]Open Synaptic and click Settings / Repositories. Go to the "Other Software" section and edit the freshly added repository: Change Distribution to "karmic".
[*]Press the "Reload" Button.
[*]Enter "libvorbis" into the Quick search field and do the folowing steps for the packages ""libvorbisenc2", "libvorbis0a" and "libvorbisfile3":
[*]Select the respective package and click Package / Force version. Select the "AoTuV" version, ignore any warnings and click the "Force Version" button.
[*]Click Package / Lock Version
[/LIST]
That's it! These packages will not be updated by synaptic unless you unlock them again. But be careful: These settings only work inside synaptic. If you should ever update your system via commandline (apt-get dist-upgrade), they will be ignored. In this case you should use apt-pinning.

Good luck!
Heiner

---

### Post by oldmankit on 2010-09-02
Hi,

I'm about to rip a whole CD collection so want to get this right!

I tried the original instructions but used checkinstall instead of 'make install':

```
sudo *apt*-*get install build*-*essential* 
sudo *apt*-*get build-dep libvorbis* 
```change to source code directory
```
CFLAGS=-fno-strict-aliasing sh ./configure --prefix=/usr
make 
sudo checkinstall 

```I got this warning:
> *** Warning: The package version "b5.7_20090301" is not a
*** Warning: debian policy compliant one. Please specify an alternate oneso gave it the version 5.7
It gets to the end, says 'installing debian package', but fails, with the following log file:
> 
Reading database ... 266744 files and directories currently installed.)
Unpacking aotuv (from .../aotuv_5.7-1_i386.deb) ...
dpkg: error processing /home/kit/downloads/linux/media/aotuv-b5.7_20090301/aotuv_5.7-1_i386.deb (--install):
 trying to overwrite '/usr/lib/libvorbis.so.0', which is also in package libvorbis0a 0:1.2.3-3ubuntu1
Errors were encountered while processing:
 /home/kit/downloads/linux/media/aotuv-b5.7_20090301/aotuv_5.7-1_i386.deb
/var/tmp/tmp.ticl9SnwIM/dpkginstall.log (END) I cannot remove libvorbis0a because a lot of my system depends on it.
I tried manually removing /usr/lib/libvorbis.so.0, but this does not solve the problem.

Please help!

---

### Post by l3lackEyedAngels on 2010-09-02
> **oldmankit said:**
> Please help!I can't help with the  method you've described, but you might want to try the method that I  posted, which hmuenz nicely summarized.

---

### Post by oldmankit on 2010-09-02
> **l3lackEyedAngels said:**
> I can't help with the  method you've described, but you might want to try the method that I  posted, which hmuenz nicely summarized.

Thanks for that.  I've done that and it works, so I can get cracking with my CD collection.

If anyone knows how to upgrade from these versions to the source code I downloaded (i.e. my first question), do let me know!

---

### Post by mc4man on 2010-09-02
> If anyone knows how to upgrade from these versions to the source code I downloaded (i.e. my first question), do let me know!
I guess that would depend on what you are actually looking to do.

If it's to have an oggenc (vorbis-tools) that use the AoTuV tuned libvorbis without touching the current installed libvorbis shared libs then that's very simple. (just did so on maverick

If you're looking to use a specific app that uses libvorbis then it would depend on the app (can it be built statically linked to libvorbis.

If you're looking replace your shared vorbis libs with ones built from the tuned source then in theory no problem but the actual libvoris version (of the source) probably would preclude doing so (or break other apps if managed

---

### Post by oldmankit on 2010-09-07
> **mc4man said:**
> 

If it's to have an oggenc (vorbis-tools) that use the AoTuV tuned libvorbis without touching the current installed libvorbis shared libs then that's very simple. (just did so on maverick

If you're looking to use a specific app that uses libvorbis then it would depend on the app (can it be built statically linked to libvorbis.

If you're looking replace your shared vorbis libs with ones built from the tuned source then in theory no problem but the actual libvoris version (of the source) probably would preclude doing so (or break other apps if managed

Thanks for that.  I've digested the question and got an answer: option one.  I just want to use oggenc with the AoTuV modifications.  I don't need to touch anything else.  How would I do that?

---

### Post by mc4man on 2010-09-07
Very simple and quick.
What you're going to do is build a static only version of AoTuV tuned libvorbis and install to /usr/local
(it can be removed afterwards
The you'll install the build deps for vorbis-tools, after which removing the libvorbis-dev package.
Finally you get the vorbis-tools source, build and install to usr/local with checkinstall - the oggenc will have built-in encoding support using the tuned libvorbis

```
sudo apt-get build-dep vorbis-tools
```
Also install checkinstall if not already
```
sudo apt-get install checkinstall
```
After done open synaptic, search libvorbis and remove the libvorbis-dev package.
 (not 100% nessasary but i'd do this - if any other -devs are removed a record will be in synaptics history - re-install afterwards as desired

Might as well do this all in one folder, so make a folder in your home directory, I used ogg_build. Take your tuned source, place it in the folder and cd to it in a terminal.
Ex.
> doug@doug-laptop:~/ogg_build/aotuv-b5.7_20090301$

Make sure the configure file is executable, either r. click on properties - permissions or
```
chmod +x configure
```

Then a simple configure (if you want to use the Cflags as in prior post do so
```
./configure --disable-shared && make
```
Then just use make install
```
sudo make install
```

If good 
```
cd .. && apt-get source vorbis-tools
```

Then cd to the vorbis-tools folder (will guess it's vorbis-tools-1.2.0 on lucid

```
./configure && make
```
```
sudo checkinstall --backup=no --deldoc=yes  --deldesc=yes \
--delspec=yes  --default --pkgversion 1.2.[COLOR="Blue"]1[/COLOR]
```
(blue is to make a number higher than lucid package

That's it - took me longer to write then it should take you to do.

Test your oggenc, if all is well I'd cd back to the vorbis source and run sudo make uninstall

Quick example - oggenc encode wav to ogg  no options
> doug@doug-laptop:~$ oggenc '/home/doug/Music/luckynight.wav' -o /home/doug/Music/luckynight2.ogg
Opening with wav module: WAV file reader
Encoding "/home/doug/Music/luckynight.wav" to 
         "/home/doug/Music/luckynight2.ogg" 
at quality 3.00
    [ 99.1%] [ 0m00s remaining] | 

Done encoding file "/home/doug/Music/luckynight2.ogg"

    File length:  1m 00.0s
    Elapsed time: 0m 02.7s
    Rate:         22.3522
    Average bitrate: 106.9 kb/s
see screen for mediainfo

EDit: anything that uses oggenc will also encode w/ the tuned  - soundkonverter is one ex.

---

### Post by oldmankit on 2010-09-28
Thanks so much mc4man.  I've followed your instructions (mainly understanding what's going on) and it's working nicely now. 

One question:
> if all is well I'd cd back to the vorbis source and run sudo make uninstallWhich one am I uninstalling: vorbis-tools-1.2.0 or the aotuv-b5.7?

Thanks again for the help.

---

### Post by ron999 on 2010-09-28
Hi
I have added the ppa:towolf repository as shown in post #7.
I can verify that when I use oggenc it does use the aoTuV version OK.
But when I use ffmpeg with libvorbis will it automatically use the aoTuV version too?

---

### Post by mc4man on 2010-09-28
> Which one am I uninstalling: vorbis-tools-1.2.0 or the aotuv-b5.7?
Sorry - should have been a bit more clear - remove the aotuv-b5.7? (the one you used the make install on 
While it could stay installed it's only use would be to build some other source against, better to remove and if the need arises just redo. 
oggenc no longer needs it, it now has tuned libvorbis support built-in.

The vorbis-tools package contains oggenc so that should stay installed (the checkinstall package

---

### Post by mc4man on 2010-09-28
> I have added the ppa:towolf repository as shown in post #7.
I can verify that when I use oggenc it does use the aoTuV version OK.
But when I use ffmpeg with libvorbis will it automatically use the aoTuV version too?

I'd guess so, - if ffmpeg uses the shared libvorbis when encoding. 
If you built ffmpeg previously using the standard libvorbis-dev then not sure what effect that would have when replacing the shared repo libvorbis with the tuned (ppa) one, guess you'd need to see.

---

### Post by ron999 on 2010-09-28
Hi
I suppose it was a dumb question really.
Now I've looked in Synaptic the original versions of the libvorbis programs have disappeared.
The four packages are now all 1.2.2+aotuv-b5.7-OubuntuO~ppa9 versions.
libvorbisOa
libvorbis-dev
libvorbisenc2
libvorbisfile3

And ffmpeg is functioning OK with libvorbis commands.:)

---

### Post by oldmankit on 2010-09-30
Finally think I understand what we've done.  Please correct me if I'm wrong.

1) ```
./configure --disable-shared && make
```This installs aotuv to /usr/local rather than /usr/shared.  I wasn't able to install it the first time because it couldn't overwrite certain files in /usr/shared.

2) ```
sudo checkinstall --backup=no --deldoc=yes  --deldesc=yes \
--delspec=yes  --default --pkgversion 1.2.[COLOR=Blue]1[/COLOR]
```I don't understand all these options, but this creates a version of vorbis-tools that with a higher version than the one shipped as standard (so it supercedes it), which uses aotuv which temporarily lived at /usr/shared. 

Aotuv package can be removed after step two, because vorbis-tools used it during installation but doesn't during usage.

---

### Post by mc4man on 2010-09-30
> Finally think I understand what we've done. Please correct me if I'm wrong.
That's pretty much it. 
> Aotuv package can be removed after step two, because vorbis-tools used it [COLOR="Blue"]during compiling [/COLOR]but doesn't during usage. 
By using a static build of Aotuv (--disable-shared),  vorbis-tools was built statically linked to Aotuv, ie, Aotuv is now part of oggenc so it doesn't need or use a shared libvorbis anymore.
It makes vorbis-tools (oggenc) slightly larger, in this case an insignificant amount.

The checkinstall options just remove some build/packaging files you don't need - del = delete

(I did test the modified oggenc with soundkonverter to rip a cd to ogg - worked out fine

---

### Post by ariel on 2010-10-11
> **l3lackEyedAngels said:**
> I can't help with the  method you've described, but you might want to try the method that I  posted, which hmuenz nicely summarized.

is this method still working for you in Maverick / 10.10 ?

I tried it, tobias' libraries do install OK (I can see that by using apt-cache show), however, oggenc is *not* using them for whatever reason. I need oggenc to use aotuv

---

### Post by mc4man on 2010-10-11
ariel
When I was working out the method for oldmankit I was on maverick, quite simple if what you desire is an oggenc that uses the tuned source
(though have also built tuned libvorbis support  into ffmpeg and others.

You just can't use the vorbis-tools source and by extension the provided oggenc that maverick uses - it requires libvorbis 1.3

The advantage here is you don't replace the maverick vorbis libs - your oggenc has the tuned vorbis built-in

Ex. from maverick - simple encode no parameters
> doug@doug-laptop:~$ oggenc --version
oggenc from vorbis-tools 1.2.0 
doug@doug-laptop:~$ oggenc '/home/doug/Music/ogg/luckynight.wav' 
Opening with wav module: WAV file reader
Encoding "/home/doug/Music/ogg/luckynight.wav" to 
         "/home/doug/Music/ogg/luckynight.ogg" 
at quality 3.00
	[ 99.1%] [ 0m00s remaining] | 

Done encoding file "/home/doug/Music/ogg/luckynight.ogg"

	File length:  1m 00.0s
	Elapsed time: 0m 02.6s
	Rate:         22.8291
	Average bitrate: 106.9 kb/s

mediainfo in screen

If you wish I'll post maverick specific (basically the same w/ 2 small variations

---

### Post by l3lackEyedAngels on 2010-10-11
> **ariel said:**
> is this method still working for you in Maverick / 10.10 ?We'll see. I just started the upgrade before leaving for work this morning.

---

### Post by ariel on 2010-10-11
> **mc4man said:**
> ariel

If you wish I'll post maverick specific (basically the same w/ 2 small variations

Thanks - that would be nice, please do post the maverick / aotuv howto.

---

### Post by l3lackEyedAngels on 2010-10-12
> **ariel said:**
> is this method still working for you in Maverick / 10.10 ?Nope. Tried to redo it my way with no luck. Then I tried it [this way]("http://ubuntuforums.org/showpost.php?p=9817388&postcount=13") and everything seems borked now. :( I tested oggenc, but all I get is a ```
Segmentation fault
```.

---

### Post by mc4man on 2010-10-13
Edit: no longer needed - new source works as is...

For maverick - very straightforward
(build oggenc w/ built-in tuned vorbis support

**first remove any outside vorbis lib's, ppa's - return maverick to normal as far as libvorbis libraries** and vorbis-tools if installed

Quick review -
What you're going to do (if you wish to do otherwise than below command set...

create a build folder (ogg_build in commands 
Get the AoTuV source from here and extract in above folder
[http://www.geocities.jp/aoyoume/aotuv/](http://www.geocities.jp/aoyoume/aotuv/)

Get vorbis-tools source 1.2.0 from here and also extract into build folder
[http://packages.ubuntu.com/lucid/vorbis-tools](http://packages.ubuntu.com/lucid/vorbis-tools)

Install the build-deps for libvorbis and vorbis-tools
Remove libvorbis-dev and install checkinstall
Build a static only libvorbis to /usr/local and install with make install
Build a new vorbis-tools, version higher than mavericks, install as a .deb

After vorbis-tools build you can remove the static libvorbis with
sudo make uninstall (cd back to the vorbis source folder
If any packages were un-installed when removing libvorbis-dev they then can be re-installed - would only be some -dev packages.
(you can use the static libvorbis for othe builds... doesn't matter here.
That's it.

Complete start to finish commands  (am going to post as separate, can be combined, or pick and chosen as needed - don't get lost

```
mkdir ogg_build && cd ogg_build
```
```
sudo apt-get build-dep vorbis-tools
```
```
sudo apt-get build-dep libvorbis
```
```
sudo apt-get install checkinstall
```
```
sudo apt-get remove libvorbis-dev
```
```
wget http://www.geocities.jp/aoyoume/aotuv/source_code/libvorbis-aotuv_b5.7.tar.bz2
```
```
tar -xvjf libvorbis-aotuv_b5.7.tar.bz2
```
```
wget http://archive.ubuntu.com/ubuntu/pool/main/v/vorbis-tools/vorbis-tools_1.2.0.orig.tar.gz
```
```
tar xzvf vorbis-tools_1.2.0.orig.tar.gz
```
```
cd ./aotuv-b5.7_20090301 && chmod +x configure
```
```
./configure --disable-shared && make 
```
```
sudo make install
```
```
cd ../vorbis-tools-1.2.0 && ./configure && make
```
```
sudo checkinstall --backup=no --deldoc=yes  --deldesc=yes \
--delspec=yes  --default --fstrans=no  --pkgversion 1.4.1+aotuv-b5.7

```

---

### Post by l3lackEyedAngels on 2010-10-13
It's working mc4man! Thanks for the help.

---

### Post by jocheem67 on 2010-10-13
There's also the possibility to use foobar2000 under wine and use the aotuv's from within foobar. 
Just a possibility and quite simple to use.

---

### Post by mc4man on 2010-10-14
> **l3lackEyedAngels said:**
> It's working 
Good to hear - 
Don't forget you have that static make installed libvorbis (pretty much equivalent to libvorbis-dev.


as far as apps for ripping and or encoding, -  rubyripper, abcde and soundkonverter are happy to use the 'new' oggenc. (probably others.

It also appears ffmpeg will build off of the static libvorbis, somewhat hard to confirm it's use.

---

### Post by ron999 on 2010-11-12
Hi
I've come across a problem with the AoTuV version.
I had used the ppa:towolf method as shown in post #7.
The versions installed were 1.2.2+aotuv-b5.7-OubuntuO~ppa9.
That was two months ago.

Now, when I tried to compile VLC v1.1.4 I got an error.
```
CCLD   libvorbis_plugin.la
/bin/sed: can't read /usr/lib/libogg.la: No such file or directory
libtool: link: `/usr/lib/libogg.la' is not a valid libtool archive
make[5]: *** [libvorbis_plugin.la] Error 1
make[5]: Leaving directory `/home/ron/vlc_build/vlc-1.1.4/modules/codec'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/ron/vlc_build/vlc-1.1.4/modules/codec'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/ron/vlc_build/vlc-1.1.4/modules/codec'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/ron/vlc_build/vlc-1.1.4/modules'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ron/vlc_build/vlc-1.1.4'
make: *** [all] Error 

```
When I googled for help I found a thread that suggested:-
> Looks like too old (or too recent?) libvorbis

So I found some Karmic deb packages for libvorbis and I installed them using sudo dpkg -i ...
libvorbisOa
libvorbis-dev
libvorbisenc2
libvorbisfile3
And I've unchecked the towolf ppa.
The libvorbis packages I've got installed now are 1.2.0.dfsg-6ubuntu0.1

VLC v1.1.4 has compiled and installed OK.:guitar:

---

### Post by l3lackEyedAngels on 2010-11-12
> **ron999 said:**
> Hi
I've come across a problem with the AoTuV version.
I had used the ppa:towolf method as shown in post #7.
The versions installed were 1.2.2+aotuv-b5.7-OubuntuO~ppa9.
That was two months ago....What version of Ubuntu are you running? You may want to try mc4man's method.

---

### Post by mc4man on 2010-11-12
The real purpose here was to build an oggenc that used  AoTuV tuning, whether used standalone or with an app that uses oggenc like soundkonveter, ect..

You can use the static build of vorbis in compiling other sources, ffmpeg for instance, as far as vlc should also be ok though not sure of any advantage there. Due to other inter-dependencies libvorbis-dev shouldn't be removed though vlc should link to the static vorbis in /usr/local

Ex. 
built here
> ldd '/usr/lib/vlc/plugins/codec/libvorbis_plugin.so' 
	linux-gate.so.1 =>  (0x00963000)
	libpthread.so.0 => /lib/libpthread.so.0 (0x00262000)
	libm.so.6 => /lib/libm.so.6 (0x005c3000)
	libogg.so.0 => /usr/lib/libogg.so.0 (0x00ab6000)
	libvlccore.so.5 => /usr/lib/libvlccore.so.5 (0x00e9a000)
	libc.so.6 => /lib/libc.so.6 (0x0027c000)
	/lib/ld-linux.so.2 (0x00e51000)
	libdbus-1.so.3 => /lib/libdbus-1.so.3 (0x00f8e000)
	librt.so.1 => /lib/librt.so.1 (0x00ad9000)
	libdl.so.2 => /lib/libdl.so.2 (0x00a5e000)
current videolan ppa (1.2) for maverick
> ldd '/usr/lib/vlc/plugins/codec/libvorbis_plugin.so' 
	linux-gate.so.1 =>  (0x00c1e000)
	libpthread.so.0 => /lib/libpthread.so.0 (0x0033d000)
	[COLOR="Blue"]libvorbisenc.so.2 => /usr/lib/libvorbisenc.so.2 (0x00110000)
	libvorbis.so.0 => /usr/lib/libvorbis.so.0 (0x00d3b000)[/COLOR]
	libm.so.6 => /lib/libm.so.6 (0x00e1f000)
	libogg.so.0 => /usr/lib/libogg.so.0 (0x00792000)
	libvlccore.so.5 => /usr/lib/libvlccore.so.5 (0x00357000)
	libc.so.6 => /lib/libc.so.6 (0x0056a000)
	/lib/ld-linux.so.2 (0x009a3000)
	libdbus-1.so.3 => /lib/libdbus-1.so.3 (0x00b35000)
	librt.so.1 => /lib/librt.so.1 (0x00288000)
	libdl.so.2 => /lib/libdl.so.2 (0x00ce4000)


---

### Post by ron999 on 2010-11-13
Hi
On the xiph website it shows that some packages have been updated.
libogg --> 1.2.1
libvorbis --> 1.32
vorbis-tools --> 1.4.0

Would it be difficult to compile and install these new versions?
Using the svn.
(Like the way we compile x264 and libvpx)

And while compiling them use the AoTuv tuning?

---

### Post by ron999 on 2011-02-03
Hi
I've used the mc4man method in post #26 with Karmic.
The towolf ppa caused problems when compiling VLC.

The Karmic package version is vorbis-tools_1.2.0-6 so I made the compiled package version vorbis-tools_1.2.1+aotuv-b5.7-1.

I left the static libvorbis installed. MediaInfo shows that ffmpeg and vlc seem to have compiled with it.
;)


When I run a command like post #32 above, the result is as the top example.
No mention of libvorbis.
I don't understand the significance of this command though.:confused:

[VLC media player 1.2.0-git Twoflower (revision d1ca34e)]
> 
ron@ubuntu:~$ ldd '/usr/local/lib/vlc/plugins/codec/libvorbis_plugin.so'
	linux-gate.so.1 =>  (0x00a80000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x0072f000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x00bfd000)
	libogg.so.0 => /usr/lib/libogg.so.0 (0x00655000)
	libvlccore.so.5 => /usr/local/lib/libvlccore.so.5 (0x0016e000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x00e46000)
	/lib/ld-linux.so.2 (0x00d58000)
	libdbus-1.so.3 => /lib/libdbus-1.so.3 (0x006c7000)
	librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0x00c4e000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x00572000)

---

### Post by mc4man on 2011-05-03
Ron - was checking this out for natty (works fine), noticed your last post

What it shows is that there is no shared vorbis libs linked in vlc, so the support was statically linked (built-in) in vlc, using your AoTuV build in /usr/local

- again limited value in vlc, may be useful in an ffmpeg build (or may not, not sure if ffmpeg would like this version anymore or statically linking

---

### Post by nethero on 2011-05-21
Hi there,

I'm using maverick and I'd like to compilte aotuv beta 6.0.3.  I successfully followed the instructions [listed here]("http://wiki.hydrogenaudio.org/index.php?title=Compiling_aoTuV")

However, all that did was put the files I need in /usr/local/lib.  When I want to encode I need to use the line...

LD_PRELOAD=`echo /usr/local/lib/libvorbis*.so` oggenc -q4 foo.wav

I'm confused because I thought I was compiling and installing the oggenc itself.  What exactly am I compiling?  I'm kind of new to using vorbis on linux so any detail you could give me would be appreciated.  

Also, is there anyway to compile/install this so that I don't have to type that PRELOAD command everything I want to encode using aotuv?  Thanks.

---

### Post by mc4man on 2011-05-21
> **nethero said:**
> Hi there,

I'm using maverick and I'd like to compilte aotuv beta 6.0.3.  
I'm confused because I thought I was compiling and installing the oggenc itself.  What exactly am I compiling?  I'm kind of new to using vorbis on linux so any detail you could give me would be appreciated.  

Also, is there anyway to compile/install this so that I don't have to type that PRELOAD command everything I want to encode using aotuv?  Thanks.
You could probably create an alias that did the preload for you - I wouldn't bother.
If you wish then  remove what you've done and follow the command set in post 26 starting right after the overview
This will give you an oggenc in /usr/local for standalone use (oggenc <whatever>) and will also be available for any app that uses oggenc directly.
Should only take you a few min. start to finish

---

### Post by nethero on 2011-05-21
Thanks for the reply mc4man.  I didn't know what an alias was so I  looked it up.  It seems like the ideal solution to my problem.  I made  one by running...

```
alias aotuv='LD_PRELOAD=`echo /usr/local/lib/libvorbis*.so` oggenc'
```So now I type...
  
```
aotuv soundfile.wav
```and it encodes using the latest aotuv version.
  
I was wondering, is there a disadvantage to this?  It seemed like you  didn't think this would be ideal. 

If you think it is better for me to do it the other way, I will try.  Also, when I read post 26 I noticed it was for vorbis-tools 1.2  and aotuv beta 5.7; however, I'd like to use vorbis-tools 1.4 and aotuv beta 6.03.  Will the same procedure work for vorbis-tools 1.4 and aotuv beta 6.03?  Thanks.

---

### Post by mc4man on 2011-05-21
> I was wondering, is there a disadvantage to this? It seemed like you didn't think this would be ideal.
If it's working as you needed then that's all that matters

One of the advan.'s of the method I described is that it builds an oggenc that was statically linked to the AoTuV vorbis library , ie. once done that support is 'built-in' to oggenc. (in other words not using/needing a AoTuV shared lib.

That is mainly useful if you wanted to use apps that encoded with oggenc, if you're just using oggenc itself doesn't particularly matter

One of the issues with the orig. described methods in this thread was that installing a shared libvorbis of lower version could cause some issues  - this prevented that because we aren't building vorbis as shared

If deciding to redo start with a fresh AoTuV source (or just do all the steps i outlined

Edit : a side advantage was that if the static vorbis build was left after doing this it could be used to statically link vorbis (AoTuV) in ffmpeg and vlc builds - that's what the prior several posts were referring to
(post 13 describes for lucd, may have some add. info, post 26 is for maverick and natty

---

### Post by ariel on 2011-05-22
> **nethero said:**
> Thanks for the reply mc4man.  I didn't know what an alias was so I  looked it up.  It seems like the ideal solution to my problem.  I made  one by running...

```
alias aotuv='LD_PRELOAD=`echo /usr/local/lib/libvorbis*.so` oggenc'
```So now I type...
  
```
aotuv soundfile.wav
```and it encodes using the latest aotuv version.
  
I was wondering, is there a disadvantage to this?  It seemed like you  didn't think this would be ideal. 

If you think it is better for me to do it the other way, I will try.  Also, when I read post 26 I noticed it was for vorbis-tools 1.2  and aotuv beta 5.7; however, I'd like to use vorbis-tools 1.4 and aotuv beta 6.03.  Will the same procedure work for vorbis-tools 1.4 and aotuv beta 6.03?  Thanks.


Just to let you know that in Natty/11.04, the following works "out of the box" with no tweaking or messing around with symlinks (like I remember having to do on 10.10) 

Get the latest aotuv code ([http://www.geocities.jp/aoyoume/aotuv/](http://www.geocities.jp/aoyoume/aotuv/) - Beta6.03 / 2011 04 25)

Then:
```

CFLAGS=-fno-strict-aliasing sh ./configure --prefix=/usr
make 
sudo make install 

```This will replace Natty's oggenc with a new one.

To verify that aotuv is being used: encode anything with oggenc and then try and ogginfo on the resulting ogg. This is what I see:

```
Processing file "01_-_test-file.ogg"...

New logical stream (#1, serial: 559d9d28): type vorbis
Vorbis headers parsed for stream 1, information follows...
Version: 0
**Vendor: AO; aoTuV [20110424] (based on Xiph.Org's libVorbis)**
Channels: 2
Rate: 44100

Nominal bitrate: 192.000000 kb/s

```

---

### Post by mc4man on 2011-05-23
> **ariel said:**
> Just to let you know that in Natty/11.04, the following works "out of the box" with no tweaking or messing around with symlinks (like I remember having to do on 10.10) 


Excellent - so there have been  new AoTuV source releases (latest 04/25), better and easier - should be equally fine in maverick
(hadn't been paying attention to since last year - was 
> Libvorbis aoTuV was unified with Xiph.Org's libvorbis1.3.2.
in feb. so no more conflict wich current libs

---

### Post by Thoralyon on 2011-05-28
If i try to execute the following code
> CFLAGS=-fno-strict-aliasing sh ./configure --prefix=/usr
make 
sudo make install
configure fails and gives me this error:
"configure: error: must have Ogg installed!"

---

### Post by Thoralyon on 2011-06-03
Could use some pointers on how to get this to work :(
*bump*

---

### Post by ron999 on 2011-06-03
> **Thoralyon said:**
> Could use some pointers on how to get this to work :(
*bump*
Show the output of this command:-
```
cat /etc/issue
```

---

### Post by ariel on 2011-06-03
> **Thoralyon said:**
> Could use some pointers on how to get this to work :(
*bump*

did you install the ogg encoder? 
```

sudo apt-get install vorbis-tools
```

---

### Post by Thoralyon on 2011-06-03
vorbis-tools are installed, I can encode "normal" ogg vorbis files just fine
I am running natty, the output of cat /etc/issue is "Ubuntu 11.04 \n \l
"

---

### Post by Thoralyon on 2011-06-07
bump?

---

### Post by h8uthemost on 2011-06-23
I'm getting hung up at ./configure --disable-shared && make on post #26.

Any help? The error that I"m getting is: bash: ./configure: No such file or directory

Thanks.

---

### Post by mc4man on 2011-06-23
> **h8uthemost said:**
> I'm getting hung up at ./configure --disable-shared && make on post #26.

Any help? The error that I"m getting is: bash: ./configure: No such file or directory

Thanks.

That post is a bit outdated, presented a solution to an issue that no longer exists.
As it was a response to 1 post I wasn't sure where the poster wanted to pick up, if done start to finish that line is incorrect because you'd already be in the "ogg_build" dir, so you'd do this instead
```
cd ./aotuv-b5.7_20090301 && chmod +x configure

```

I'd suggest using the latest source and possibly doing as above (ariel's post #40)  - building as shared/static and letting it overwrite your existing vorbis lib's and headers if installed in /usr/*

(note he says it will replace your oggenc - that's not true - it will replace the vorbis libs

(for myself I'll continue to build static only and rebuild vorbis-tools to produce a standalone oggenc or possibly do a shared/static install to usr/local/* instead, either as a package set or maybe checkinstall - if you mention what release of ubuntu and what you're looking for ...

---

### Post by h8uthemost on 2011-06-23
Thanks for the response mc4man.

But I can't believe that there's not an easier way to using AoTuV. I know I could just use Foobar, but I like using scripts to do all my converting.

I don't know, I really don't hear a difference at all if I listen to a file that was converted without AoTuV, so maybe I won't bother with any of this after all. Since I'm not the best at installing through Terminal(I ALWAYS run into a problem), I'm just not that big of a fan of going through a bunch of trouble to get something to work on Linux.

But again, thanks for the response.

Or actually, the May 2011 edit or Ariel's initial post looks a lot easier to do. This is the method you would suggest for me to use? I don't know what shared/static means, so I'm guessing that's what his post explains to do?

Thanks.

EDIT: And again...I run into a problem(it wasn't exaggeration when I said that I always run into a problem when installing through Terminal). When I get to the part of:

```
CFLAGS=-fno-strict-aliasing sh ./configure --prefix=/usr
make 
sudo make install

```

I get this error:

```
~$ CFLAGS=-fno-strict-aliasing sh ./configure --prefix=/usr
sh: Can't open ./configure
~$ make 
make: *** No targets specified and no makefile found.  Stop.
~$ sudo make install
make: *** No rule to make target `install'.  Stop.
```

There must be some make or .configure or something files that I don't have installed. I'm on a fresh distro install.

---

### Post by h8uthemost on 2011-07-01
I've finally gotten libvorbis to use the latest beta of AoTuV thanks to ariels initial post.

I do have one question though. When a new version of AoTuV comes, do I simply follow this part of ariels post again with the new version?

```
CFLAGS=-fno-strict-aliasing sh ./configure --prefix=/usr
make 
sudo make install
```

It appears that's all I'll have to do but I just wanted to make sure.

Thanks ariel for providing us with the instructions to get this working.

---

### Post by andrew.46 on 2011-07-02
Wooo hoooo!!!

```

andrew@skamandros~/Desktop$ mediainfo finches.ogg 
General
Complete name                    : finches.ogg
Format                           : OGG
File size                        : 16.3 KiB
Duration                         : 2s 455ms
Overall bit rate                 : 54.5 Kbps

Audio
ID                               : 1752265441 (0x687172E1)
Format                           : Vorbis
Duration                         : 2s 455ms
Bit rate mode                    : Constant
Bit rate                         : 44.0 Kbps
Channel(s)                       : 1 channel
Sampling rate                    : 11.025 KHz
Compression mode                 : Lossy
Stream size                      : 13.2 KiB (81%)
**[COLOR="Red"]Writing library                  : aoTuV 20110424 (UTC 2011-04-24)[/COLOR]**

```

Thanks to the OP, I had not really had much to do with aotuv before this :).

---

### Post by ron999 on 2011-07-02
It's taken months to get my head around this thread.:(
But now the penny has dropped.:D

The tuned aoTuV libraries get installed in the **local** folder like this:-
(I can tell by checking the dates)

[B]/usr/local/lib/libvorbisenc.la
/usr/local/lib/libvorbisenc.a
/usr/local/lib/libvorbisfile.la
/usr/local/lib/libvorbisfile.a
/usr/local/lib/libvorbis.la
/usr/local/lib/libvorbis.a[/B]

So that the original ones in **/usr/lib** get ignored.
I think the original ones have names libvorbis0, libvorbisenc2 and libvorbisfile3.

And now it seems, anything that is compiled with libvorbis uses aoTuV.

As well as vorbis-tools(oggenc), VLC and FFmpeg use them also.

Using commands like this:-
```
vlc foo.wav --sout "#transcode{acodec=vorb}:std{access=file,mux=ogg,dst=foo1.ogg}"
```

```
ffmpeg -i foo.wav -acodec libvorbis foo2.webm
```

> ron@ubuntu:~$ mediainfo foo1.ogg
General
Complete name                    : foo1.ogg
Format                           : OGG
File size                        : 2.20 MiB
Duration                         : 3mn 8s
Overall bit rate                 : 97.6 Kbps
Writing application              : [COLOR="Red"]VLC [/COLOR]media player

Audio
ID                               : 262313113 (0xFA29499)
Format                           : Vorbis
Format settings, Floor           : 1
Duration                         : 3mn 8s
Bit rate                         : 96.0 Kbps
Channel(s)                       : 2 channels
Sampling rate                    : 44.1 KHz
Compression mode                 : Lossy
Stream size                      : 2.16 MiB (98%)
Writing library                  : [COLOR="Red"]aoTuV 20110424 (UTC 2011-04-24)[/COLOR]


> ron@ubuntu:~$ mediainfo foo2.webm
General
Unique ID                        : 250489903628497252997079403068497805190 (0xBC7299C200693A340F6290DE0AD73F86)
Complete name                    : foo2.webm
Format                           : WebM
File size                        : 1.28 MiB
Duration                         : 3mn 9s
Overall bit rate                 : 57.0 Kbps
Writing application              : Lavf53.5.0
Writing library                  : [COLOR="Red"]Lavf53.5.0[/COLOR]

Audio
ID                               : 1
Format                           : Vorbis
Format settings, Floor           : 1
Codec ID                         : A_VORBIS
Duration                         : 3mn 9s
Bit rate                         : 64.0 Kbps
Channel(s)                       : 2 channels
Sampling rate                    : 44.1 KHz
Compression mode                 : Lossy
Stream size                      : 1.44 MiB
Writing library                  : [COLOR="Red"]aoTuV 20110424 (UTC 2011-04-24)[/COLOR]
Language                         : English


---

### Post by mc4man on 2011-07-02
> It's taken months to get my head around this thread.
But now the penny has dropped.
If you are using an ubuntu release that uses the 1.3.X version of vorbis then AoTuV source can also be built as suggested in #40  - to /usr/* as shared/static.
In that case it will overwrite the existing vorbis libs in addition to installing headers for building against. (libvorbis.so.0.4.5, libvorbisenc.so.2 libvorbisfile.so.3.3.4, ect.

I'm not 100% keen on that way but it should work fine
(one must use sudo make install for that way, checkinstall will refuse to overwrite exiting libs in same location 
I'd prefer, if building as shared, to install to usr/local/* with ck.install or just continue as before as static only and build against as desired

---

### Post by ron999 on 2011-07-02
Hi
I'm using Natty now, so the libvorbis libraries are 1.3.2 I think.
Information is here:- [http://packages.ubuntu.com/natty/libvorbis-dev]("http://packages.ubuntu.com/natty/libvorbis-dev")

This is the method I used from an earlier post:-

```
sudo apt-get build-dep libvorbis

mkdir ogg_build && cd ogg_build

wget http://www.geocities.jp/aoyoume/aotuv/source_code/libvorbis-aotuv_b6.03.tar.bz2

tar -xvjf libvorbis-aotuv_b6.03.tar.bz2

cd ~/ogg_build/aotuv-b6.03_20110424 && chmod +x configure

./configure --disable-shared && make

sudo make install
```


Then afterwards I compiled vorbis-tools, FFmpeg and VLC.

---

### Post by andrew.46 on 2011-07-02
Mind you for my *other* distro I created a monster patch from the aoTuV b6.03 version and applied it against the existing libvorbis 1.3.2 package. Thus it integrated nicely into the package management system. The patch is here:

```
wget http://www.andrews-corner.org/slackbuilds/libvorbis_aoTuV/aotuv-b6.03.diff
```

and I am pretty sure this could be used to rebuild the libvorbis package under Ubuntu, this would be a particularly neat way of doing it I think. I have not done so yet as I am BBQing today for my extended family but feel free to jump in use the patch :).

---

### Post by mc4man on 2011-07-03
For certain reasons aren't going to use or try shared/patched vorbis libs on this install but the patch did apply cleanly on ubuntu's libvorbis-1.3.2 source (in a package build, so well done there
> 
dpkg-source: info: building libvorbis in libvorbis_1.3.2-1ubuntu1.dsc
 debian/rules build
dh build --with quilt
   dh_testdir
   dh_quilt_patch
Applying patch aotuv-b6.03.patch
patching file COPYING
patching file aoTuV_README-1st.txt
patching file aoTuV_technical.txt
patching file lib/analysis.c
patching file lib/block.c
patching file lib/codec_internal.h
patching file lib/envelope.c
patching file lib/envelope.h
patching file lib/highlevel.h
patching file lib/info.c
patching file lib/mapping0.c
patching file lib/masking.h
patching file lib/misc.h
patching file lib/modes/floor_all.h
patching file lib/modes/psych_11.h
patching file lib/modes/psych_16.h
patching file lib/modes/psych_44.h
patching file lib/modes/psych_8.h
patching file lib/modes/residue_16.h
patching file lib/modes/residue_44.h
patching file lib/modes/residue_44p51.h
patching file lib/modes/residue_44u.h
patching file lib/modes/residue_8.h
patching file lib/modes/setup_11.h
patching file lib/modes/setup_16.h
patching file lib/modes/setup_22.h
patching file lib/modes/setup_32.h
patching file lib/modes/setup_44.h
patching file lib/modes/setup_44p51.h
patching file lib/modes/setup_44u.h
patching file lib/modes/setup_8.h
patching file lib/modes/setup_X.h
patching file lib/psy.c
patching file lib/psy.h
patching file lib/vorbisenc.c

Now at patch aotuv-b6.03.patch

---

### Post by andrew.46 on 2011-07-03
Good to hear :). I have a certain horror of the whole debian build system and have never really had more than a cursory look at it. Anyway I shall leave the patch in place, it may prove useful for a while at least!

---

### Post by mc4man on 2011-07-03
For the most part i don't think there is any issue with modified shared vorbis libs though a few small possibilities.
The shared libavcodec is dependent, possibly a scenario where it's affected by some missing define.

The other thing to keep in mind is the vorbis .so's are a bit more ingrained than one might suspect for a codec - marking any of the 3  for removal in synaptic gives some idea.
(not a codec you'd want to bork up..

---

### Post by andrew.46 on 2011-07-03
It is a conclusion I have come to many times in my contact with both Ubuntu and Slackware: things like this are much, much easier under Slackware!

---

### Post by mc4man on 2011-11-27
small update as to how i'd do on 11.04/11.10, though the quicker way is still thru post 40 which replaces current libvorbis* libs, ect. in /usr & should provide gstreamer support in addition to the default supplied oggenc

This is to build a static AoTuV-vorbis, then build vorbis-tools to /usr/local
This provides a 'standalone' oggenc as far as vorbis & a static libvorbis if building vlc ect.

```
sudo apt-get  build-dep libvorbis vorbis-tools
```
```
sudo apt-get install checkinstall
```
```
cd 
mkdir -p ogg_build && cd ogg_build && \
wget http://www.geocities.jp/aoyoume/aotuv/source_code/libvorbis-aotuv_b6.03.tar.bz2 && \
tar -xvjf libvorbis-aotuv_b6.03.tar.bz2 && \
cd aotuv-b6.03_20110424 && chmod +x configure && \
./configure --disable-shared && make && \
sudo checkinstall --pkgname=aotuv-vorbis  --backup=no --default \
--deldoc=yes --fstrans=no --pkgversion=6.03 
```
```
cd
cd ogg_build
apt-get source vorbis-tools && \
cd vorbis-tools-1.4.0 && ./configure && make && \
sudo checkinstall --backup=no --deldoc=yes  --deldesc=yes --delspec=yes \
--default --fstrans=no  --pkgversion 1.4.0+aotuv-b6.3
```

The aotuv-vorbis package can be left or removed after building vorbis tools, only useful to build against.
oggenc is not dependent on it as seen here

>  ldd '/usr/local/bin/oggenc' 
	linux-gate.so.1 =>  (0x00f18000)
	liboggkate.so.1 => /usr/lib/liboggkate.so.1 (0x00af6000)
	libkate.so.1 => /usr/lib/libkate.so.1 (0x0076b000)
	libFLAC.so.8 => /usr/lib/i386-linux-gnu/libFLAC.so.8 (0x008a8000)
	libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0x00d3d000)
	libogg.so.0 => /usr/lib/i386-linux-gnu/libogg.so.0 (0x00ac6000)
	libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0x0026d000)
	/lib/ld-linux.so.2 (0x0024d000)

---

### Post by flebber on 2011-11-27
From a reply on ask ubuntu here [http://askubuntu.com/questions/83086/is-gstreamer-the-best-encoder-for-vorbis-or-is-there-a-better-encoding-engine-i]("http://askubuntu.com/questions/83086/is-gstreamer-the-best-encoder-for-vorbis-or-is-there-a-better-encoding-engine-i")regarding vorbis I found this thread.

I found a ppa by tobias wolf offering amongst other patched audio codec a patched vorbis with aotuv. Here [https://launchpad.net/~towolf/+archive/codecs]("https://launchpad.net/~towolf/+archive/codecs")

Anyone used?

---

### Post by ron999 on 2011-11-27
> **mc4man said:**
> 
This is to build a static AoTuV-vorbis, then build vorbis-tools to /usr/local
This provides a 'standalone' oggenc as far as vorbis & a static libvorbis if building vlc ect...

The aotuv-vorbis package can be left or removed after building vorbis tools, only useful to build against.

Hi mc4man
This is a smart method to use.:)
Thanks.
Easy enough now to un-install and re-install (apt-get remove, dpkg -i).
aoTuV library has been picked up OK when compiling:-
oggenc
VLC
FFmpeg (shows up with webm and mka)
Sox

---

### Post by ariel on 2011-11-27
> **mc4man said:**
> small update as to how i'd do on 11.04/11.10, though the quicker way is still thru post 40 which replaces current libvorbis* libs, ect. in /usr & should provide gstreamer support in addition to the default supplied oggenc

This is to build a static AoTuV-vorbis, then build vorbis-tools to /usr/local
This provides a 'standalone' oggenc as far as vorbis & a static libvorbis if building vlc ect.

```
sudo apt-get  build-dep libvorbis vorbis-tools
``````
sudo apt-get install checkinstall
``````
cd 
mkdir -p ogg_build && cd ogg_build && \
wget http://www.geocities.jp/aoyoume/aotuv/source_code/libvorbis-aotuv_b6.03.tar.bz2 && \
tar -xvjf libvorbis-aotuv_b6.03.tar.bz2 && \
cd aotuv-b6.03_20110424 && chmod +x configure && \
./configure --disable-shared && make && \
sudo checkinstall --pkgname=aotuv-vorbis  --backup=no --default \
--deldoc=yes --fstrans=no --pkgversion=6.03 
``````
cd
cd ogg_build
apt-get source vorbis-tools && \
cd vorbis-tools-1.4.0 && ./configure && make && \
sudo checkinstall --backup=no --deldoc=yes  --deldesc=yes --delspec=yes \
--default --fstrans=no  --pkgversion 1.4.0+aotuv-b6.3
```The aotuv-vorbis package can be left or removed after building vorbis tools, only useful to build against.
oggenc is not dependent on it as seen here


Actually, I found that post #40 (and the original post), where no longer working in 11.10; the reason being that the newly built aotuv ends up win /usr/lib/libvorbis*, whereas ubuntu 11.10's oggenc is using libvorbis from /usr/lib/x86_64-linux-gnu/libvorbis*  - this last folder has its own binary copy of the 3 vorbis libraries files that aotuv patches. You can confirm this in your system by doing

```
ldd /usr/bin/oggenc
```This is what I see:

```
$ ldd /usr/bin/oggenc
    linux-vdso.so.1 =>  (0x00007fff1bfff000)
    libvorbisenc.so.2 => /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2 (0x00007fc2c8ae6000)
    libvorbis.so.0 => /usr/lib/x86_64-linux-gnu/libvorbis.so.0 (0x00007fc2c88af000)
    libFLAC.so.8 => /usr/lib/x86_64-linux-gnu/libFLAC.so.8 (0x00007fc2c8664000)
    libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007fc2c83e0000)
    libogg.so.0 => /usr/lib/x86_64-linux-gnu/libogg.so.0 (0x00007fc2c81d9000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fc2c7e39000)
    /lib64/ld-linux-x86-64.so.2 (0x00007fc2c8fe7000)

```

To fix this, this is what I did (with aotuv 6.03, latest as of today):

   sudo cp /usr/lib/libvorbis.so.0.4.5 /usr/lib/x86_64-linux-gnu/
   sudo cp /usr/lib/libvorbisfile.so.3.3.4 /usr/lib/x86_64-linux-gnu/
   sudo cp /usr/lib/libvorbisenc.so.2.0.8 /usr/lib/x86_64-linux-gnu/

After that, oggenc (and shntool which I use all the time) started to "behave"

```
New logical stream (#1, serial: 156c5945): type vorbis
Vorbis headers parsed for stream 1, information follows...
Version: 0
**Vendor: AO; aoTuV [20110424] (based on Xiph.Org's libVorbis)**
Channels: 2
Rate: 44100

```I added a note to the original post with this hack.

---

### Post by yaztromo on 2011-11-30
Thanks for that helpful bit of info.

What I had to do get oggenc with aotuv 6.03 on 32bit working.

1.
sudo apt-get build-dep libvorbis vorbis-tools

2. Get the source code for aotuv 6.03
chmod +x configure
./configure
make
sudo make install

3.
sudo cp /usr/local/lib/libvorbisenc.so.2.0.8 /usr/lib/i386-linux-gnu/
sudo cp /usr/local/lib/libvorbisfile.so.3.3.4 /usr/lib/i386-linux-gnu/
sudo cp /usr/local/lib/libvorbis.so.0.4.5 /usr/lib/i386-linux-gnu/

4. Encode a file
oggenc something.wav

5. ogginfo something.ogg
New logical stream (#1, serial: 43b79fbc): type vorbis
Vorbis headers parsed for stream 1, information follows...
Version: 0
Vendor: AO; **aoTuV** [20110424] (based on Xiph.Org's libVorbis)
Channels: 2
Rate: 44100

Can someone explain to me how step 3 works it's magic? Since those three files don't overwrite any others, I don't really understand how oggenc picks them up.

---

### Post by Tekippie on 2012-07-29
Is it still relevant to compile aoTuV into libvorbis? because I read they included it from libvorbis version 1.1 and up..

With ubuntu precise ogginfo says; Vendor: Xiph.Org libVorbis I 20101101 (Schaufenugget)

---

### Post by ariel on 2012-07-29
> **Tekippie said:**
> Is it still relevant to compile aoTuV into libvorbis? because I read they included it from libvorbis version 1.1 and up..

With ubuntu precise ogginfo says; Vendor: Xiph.Org libVorbis I 20101101 (Schaufenugget)

As I understand it, libvorbis 1.1 included a very old version of the aotuv patch, not the one praised in the hydrogenaudio forums

---

### Post by andrew.46 on 2012-12-31
For those who are still interested I have remade my patch against the libvorbis 1.3.3 and this might be useful for Ubuntu users as well as Slackware:

[http://www.andrews-corner.org/slackbuilds/libvorbis_aoTuV/](http://www.andrews-corner.org/slackbuilds/libvorbis_aoTuV/)

I have not exhaustively tested this but my first encode using oggenc seemed to work well enough:

```

andrew@skamandros~/media/fist$ **[COLOR="Red"]ogginfo cantonese_quiet.ogg [/COLOR]**
Processing file "cantonese_quiet.ogg"...

New logical stream (#1, serial: 4b27216f): type vorbis
Vorbis headers parsed for stream 1, information follows...
Version: 0
**[COLOR="Red"]Vendor: AO; aoTuV [20110424] (based on Xiph.Org's libVorbis)[/COLOR]**
Channels: 2
Rate: 48000

Nominal bitrate: 192.000000 kb/s
Upper bitrate not set
Lower bitrate not set
Vorbis stream 1:
	Total data length: 11881970 bytes
	Playback length: 10m:32.661s
	Average bitrate: 150.247463 kb/s
Logical stream 1 ended

```

and I will be compiling MPlayer, FFmpeg and vlc against the patched library...

---

### Post by mc4man on 2012-12-31
> **andrew.46 said:**
> 

and I will be compiling MPlayer, FFmpeg and vlc against the patched library...
Thanks for easy link
Also use here to rebuild vorbis-tools (oggenc)

---

### Post by andrew.46 on 2012-12-31
I guess there is an issue with some of the changes made in libvorbis 1.3.3, I am not completely sure that these changes are retained when the aoTuV changes are made. It would be nice if Aoyumi had a look at this...

---

### Post by ariel on 2013-01-01
> **andrew.46 said:**
> For those who are still interested I have remade my patch against the libvorbis 1.3.3 and this might be useful for Ubuntu users as well as Slackware:

[http://www.andrews-corner.org/slackbuilds/libvorbis_aoTuV/](http://www.andrews-corner.org/slackbuilds/libvorbis_aoTuV/)

I have not exhaustively tested this but my first encode using oggenc seemed to work well enough:

```

andrew@skamandros~/media/fist$ **[COLOR=Red]ogginfo cantonese_quiet.ogg [/COLOR]**
Processing file "cantonese_quiet.ogg"...

New logical stream (#1, serial: 4b27216f): type vorbis
Vorbis headers parsed for stream 1, information follows...
Version: 0
**[COLOR=Red]Vendor: AO; aoTuV [20110424] (based on Xiph.Org's libVorbis)[/COLOR]**
Channels: 2
Rate: 48000

Nominal bitrate: 192.000000 kb/s
Upper bitrate not set
Lower bitrate not set
Vorbis stream 1:
    Total data length: 11881970 bytes
    Playback length: 10m:32.661s
    Average bitrate: 150.247463 kb/s
Logical stream 1 ended

```and I will be compiling MPlayer, FFmpeg and vlc against the patched library...

not sure how to use the diffs in ubuntu.... details anyone? or debs?

---

### Post by mc4man on 2013-01-01
> **ariel said:**
> not sure how to use the diffs in ubuntu.... details anyone? or debs?
You could grab the 1.3.3 source (libvorbis-1.3.3.tar.xz) & diff  (aotuv_b6.03_libvorbis_1.3.3.diff.gz)
Place them in a folder, extract both as in screen
cd to the extracted source, (libvorbis-1.3.3) & run - 
```
patch -Np1 -i ../aotuv_b6.03_libvorbis_1.3.3.diff
```

Ex.
> doug@doug-XPS-M1330:~/Documents/vorbis/libvorbis-1.3.3$ patch -Np1 -i ../aotuv_b6.03_libvorbis_1.3.3.diff
patching file CHANGES
patching file COPYING
patching file Makefile.am
patching file Makefile.in
patching file aclocal.m4
patching file aoTuV_README-1st.txt
patching file aoTuV_technical.txt
patching file config.h.in
patching file configure
patching file configure.ac
patching file doc/01-introduction.tex
patching file doc/03-codebook.tex
patching file doc/04-codec.tex
patching file doc/05-comment.tex
patching file doc/06-floor0.tex
patching file doc/07-floor1.tex
patching file doc/08-residue.tex
patching file doc/09-helper.tex
patching file doc/10-tables.tex
patching file doc/Makefile.am
patching file doc/Makefile.in
patching file doc/Vorbis_I_spec.css
patching file doc/Vorbis_I_spec.html
patching file doc/Vorbis_I_spec.pdf
patching file doc/Vorbis_I_spec.tex
patching file doc/libvorbis/Makefile.in
patching file doc/vorbisenc/Makefile.in
patching file doc/vorbisfile/Makefile.in
patching file examples/Makefile.in
patching file include/Makefile.in
patching file include/vorbis/Makefile.in
patching file lib/Makefile.in
patching file lib/analysis.c
patching file lib/block.c
patching file lib/books/Makefile.in
patching file lib/books/coupled/Makefile.in
patching file lib/books/floor/Makefile.in
patching file lib/books/uncoupled/Makefile.in
patching file lib/codebook.c
patching file lib/codec_internal.h
patching file lib/envelope.c
patching file lib/envelope.h
patching file lib/floor0.c
patching file lib/floor1.c
patching file lib/highlevel.h
patching file lib/info.c
patching file lib/mapping0.c
patching file lib/masking.h
patching file lib/misc.h
patching file lib/modes/Makefile.in
patching file lib/modes/floor_all.h
patching file lib/modes/psych_11.h
patching file lib/modes/psych_16.h
patching file lib/modes/psych_44.h
patching file lib/modes/psych_8.h
patching file lib/modes/residue_16.h
patching file lib/modes/residue_44.h
patching file lib/modes/residue_44p51.h
patching file lib/modes/residue_44u.h
patching file lib/modes/residue_8.h
patching file lib/modes/setup_11.h
patching file lib/modes/setup_16.h
patching file lib/modes/setup_22.h
patching file lib/modes/setup_32.h
patching file lib/modes/setup_44.h
patching file lib/modes/setup_44p51.h
patching file lib/modes/setup_44u.h
patching file lib/modes/setup_8.h
patching file lib/modes/setup_X.h
patching file lib/psy.c
patching file lib/psy.h
patching file lib/vorbisenc.c
patching file libvorbis.spec
patching file ltmain.sh
patching file m4/Makefile.in
patching file test/Makefile.in
patching file vq/Makefile.in
patching file win32/VS2008/libvorbis/libvorbis_static.vcproj

Then configure (./configure) or (./autogen.sh), build & install.
If not wishing the default options then check ./configure --help & adjust the ./configure as desired.

(here just went with the defaults of shared/static to /usr/local, in past probably just built as static to /usr/local. Am on 13.04 so wanted to see if any issue with shared in /usr/local, none seen.
Used checkinstall with a made up name for package - 
```
sudo checkinstall --pkgname=vorbis-aotuv  --backup=no \
--deldoc=yes --fstrans=no --deldesc=yes --delspec=yes
```

---

### Post by mc4man on 2013-01-02
> **andrew.46 said:**
> I guess there is an issue with some of the changes made in libvorbis 1.3.3, I am not completely sure that these changes are retained when the aoTuV changes are made. It would be nice if Aoyumi had a look at this...

Then maybe just 1.3.3 straight up..
Seeing as 1.3.2 upped to 1.3.3 after the last aoTuV patch there would be some code 'reverted', whether it matters or affects the add. security/bug patching in 1.3.3, no clue (would have to see the details of 1.3.2 > 1.3.3 & even then...

The bulk of what I see the aoTuV patch changing from 1.3.3 is makefiles & some code, for instance the attached seems to the 1.3.2 > 1.3.3 'code' changes the patch reverts in /lib. Again no real idea if it matters
(the attached puts the 'reverts' back

---

### Post by andrew.46 on 2013-01-02
Those changes have moved way beyond my knowledge level, I shall battle on with the straight aotuv patch on libvorbis 1.3.3 and see how it all goes. A 'unification' of the AoTuV work for libvorbis 1.3.3 by Mr Aoyumi (as he did for 1.3.2) is on my birthday list :)

---

### Post by ariel on 2013-01-02
> **mc4man said:**
> You could grab the 1.3.3 source (libvorbis-1.3.3.tar.xz) & diff  (aotuv_b6.03_libvorbis_1.3.3.diff.gz)
Place them in a folder, extract both as in screen
cd to the extracted source, (libvorbis-1.3.3) & run - 
```
patch -Np1 -i ../aotuv_b6.03_libvorbis_1.3.3.diff
```Ex.


Then configure (./configure) or (./autogen.sh), build & install.
If not wishing the default options then check ./configure --help & adjust the ./configure as desired.

(here just went with the defaults of shared/static to /usr/local, in past probably just built as static to /usr/local. Am on 13.04 so wanted to see if any issue with shared in /usr/local, none seen.
Used checkinstall with a made up name for package - 
```
sudo checkinstall --pkgname=vorbis-aotuv  --backup=no \
--deldoc=yes --fstrans=no --deldesc=yes --delspec=yes
```


thanks for this!

Initially I didn't use the default answers for checkinstall and this didn't work properly (aotuv was not being used by oggenc), but then redoing the checkinstall and just in case doing a "sudo ldconfig" fixed the problem. 

Now ogginfo shows:

Vendor: AO; aoTuV [20110424] (based on Xiph.Org's libVorbis)

---

### Post by mc4man on 2013-01-02
> **ariel said:**
>  (based on Xiph.Org's libVorbis)

That's the one that did it if you built as shared - got me before on a rebuild, I forgot to do it & couldn't figure what went wrong... till I remembered always run on shared & checkinstall.

(checkinstall does have an option to do an ldconfig after install though I believe there was a warning about using it?

---

