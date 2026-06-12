---
title: "building k3b"
date: 2011-11-03
forum: Multimedia Software
---

### Post by beew on 2011-11-03
Hi, 

I am trying to build k3b from source and ran into problems with ffmpeg decoder plugins.
It is the bug reported here [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=638546](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=638546)
It says an upstream fix is release and provides a link but I have no idea what to do with it.
Please help (ffmpeg is installed)

Meanwhile, I tried to compile without ffmpeg[COLOR=Blue]
[/COLOR]```
[COLOR=Blue]
[/COLOR]cmake -DK3B_BUILD_FFMPEG_DECODER_PLUGIN=OFF .. 
```That seemed to compile but still the make process failed with errors like these

```
^
index.docbook:183: element note: validity error : No declaration for element note
(&eg; Mandriva) you do not need to install any additional packages.</para></note
                                                                               ^
index.docbook:185: element sect2: validity error : No declaration for attribute id of element sect2
<sect2 id="selecting-files"><title>Selecting the files</title>
                           ^
index.docbook:185: element title: validity error : No declaration for element title
<sect2 id="selecting-files"><title>Selecting the files</title>
                                                              ^
index.docbook:186: element para: validity error : No declaration for element para
 are two ways to select the audio files you want to burn onto an audio cd:</para
                                                                               ^
index.docbook:189: element term: validity error : No declaration for element term
<term>Using &k3b;</term>
                        ^
index.docbook:191: element guilabel: validity error : No declaration for element guilabel
ttom half of the &k3b; window click on <guilabel>New Audio CD Project</guilabel>
                                                                               ^
index.docbook:192: element para: validity error : No declaration for element para
</para>
       ^
index.docbook:193: element guilabel: validity error : No declaration for element guilabel
 &k3b;'s window automatically starts a <guilabel>New Audio CD Project</guilabel>
                                                                               ^
index.docbook:194: element para: validity error : No declaration for element para
</para>
       ^
index.docbook:195: element listitem: validity error : No declaration for element listitem
</listitem>
           ^
index.docbook:196: element varlistentry: validity error : No declaration for element varlistentry
</varlistentry>
               ^
index.docbook:199: element term: validity error : No declaration for element term
<term>Using the file manager</term>
                                   ^
index.docbook:201: parser error : Entity 'dolphin' not defined
<para>Go to the folder containing your music files in &dolphin; or &konqueror;</
                                                               ^
index.docbook:201: parser error : Entity 'konqueror' not defined
<para>Go to the folder containing your music files in &dolphin; or &konqueror;</
                                                                              ^
index.docbook:201: element para: validity error : No declaration for element para
a>Go to the folder containing your music files in &dolphin; or &konqueror;</para
                                                                               ^
index.docbook:202: element guimenu: validity error : No declaration for element guimenu
<para>Choose the files to burn and select <menuchoice><guimenu>Actions</guimenu>
                                                                               ^
index.docbook:202: element guimenuitem: validity error : No declaration for element guimenuitem
><guimenu>Actions</guimenu><guimenuitem>Create Audio CD with &k3b;</guimenuitem>
                                                                               ^
index.docbook:202: element menuchoice: validity error : No declaration for element menuchoice
ions</guimenu><guimenuitem>Create Audio CD with &k3b;</guimenuitem></menuchoice>
                                                                               ^
index.docbook:202: element para: validity error : No declaration for element para
eate Audio CD with &k3b;</guimenuitem></menuchoice> from the context menu.</para
                                                                               ^
index.docbook:203: element listitem: validity error : No declaration for element listitem
</listitem>
           ^
index.docbook:204: element varlistentry: validity error : No declaration for element varlistentry
</varlistentry>
               ^
index.docbook:206: element variablelist: validity error : No declaration for element variablelist
</variablelist>
               ^
index.docbook:207: element sect2: validity error : No declaration for element sect2
</sect2>
        ^
index.docbook:209: element sect2: validity error : No declaration for attribute id of element sect2
<sect2 id="edit-the-title-information"><title>Edit the Title Information</title>
                                      ^
index.docbook:209: element title: validity error : No declaration for element title
<sect2 id="edit-the-title-information"><title>Edit the Title Information</title>
                                                                               ^
index.docbook:210: element acronym: validity error : No declaration for element acronym
para>You can give the tracks titles or import those from <acronym>CDDB</acronym>
                                                                               ^
index.docbook:211: element para: validity error : No declaration for element para
</para>
       ^
index.docbook:212: element sect2: validity error : No declaration for element sect2
</sect2>
        ^
index.docbook:213: element sect2: validity error : No declaration for attribute id of element sect2
<sect2 id="burn-the-cd"><title>Burn the CD</title>
                       ^
index.docbook:213: element title: validity error : No declaration for element title
<sect2 id="burn-the-cd"><title>Burn the CD</title>
                                                  ^
index.docbook:214: element guilabel: validity error : No declaration for element guilabel
nc CD-R or CD-RW disc into your CD writer and click on <guilabel>Burn</guilabel>
                                                                               ^
index.docbook:214: element guilabel: validity error : No declaration for element guilabel
g check if you like the presets and when done click on <guilabel>Burn</guilabel>
                                                                               ^
index.docbook:215: element para: validity error : No declaration for element para
</para>
       ^
index.docbook:216: element sect2: validity error : No declaration for element sect2
</sect2>
        ^
index.docbook:217: element sect1: validity error : No declaration for element sect1
</sect1>
        ^
index.docbook:219: element chapter: validity error : No declaration for element chapter
</chapter>
          ^
index.docbook:221: element chapter: validity error : No declaration for attribute id of element chapter
<chapter id="credits">
                     ^
index.docbook:222: element title: validity error : No declaration for element title
<title>Credits and License</title>
                                  ^
index.docbook:225: element ulink: validity error : No declaration for attribute url of element ulink
<ulink url="http://userbase.kde.org/index.php?title=K3b&amp;action=history">K3b 
                                                                           ^
index.docbook:225: element ulink: validity error : No declaration for element ulink
serbase.kde.org/index.php?title=K3b&amp;action=history">K3b page history</ulink>
                                                                               ^
index.docbook:225: element para: validity error : No declaration for element para
e.kde.org/index.php?title=K3b&amp;action=history">K3b page history</ulink></para
                                                                               ^
index.docbook:227: parser error : Entity 'underFDL' not defined
&underFDL;
          ^
index.docbook:228: element chapter: validity error : No declaration for element chapter
</chapter>
          ^
index.docbook:229: parser error : Entity 'documentation.index' not defined
&documentation.index;
                     ^
index.docbook:230: element book: validity error : No declaration for element book
</book>
       ^
make[2]: *** [doc/index.cache.bz2] Error 1
make[1]: *** [doc/CMakeFiles/doc-handbook.dir/all] Error 2
make: *** [all] Error 2

```I would appreciate any help, thanks.

---

### Post by wolfen69 on 2011-11-03
May I ask why you're trying to compile K3B when it is available in the repos?

---

### Post by beew on 2011-11-03
> **wolfen69 said:**
> May I ask why you're trying to compile K3B when it is available in the repos?

None of the Ubuntu builds (repo or ppa) support dvd. All are compiled without libdvdcss.

---

### Post by wolfen69 on 2011-11-03
> **beew said:**
> None of the Ubuntu builds (repo or ppa) support dvd. All are compiled without libdvdcss.

Then why not just add libdvdcss2?

---

### Post by wolfen69 on 2011-11-03
Also, in addition to installing k3b, to get the extra codecs needed for k3b, do
```
sudo apt-get install libk3b6-extracodecs 
```
this will give you mp3 and ffmpeg codecs for k3b.

---

### Post by beew on 2011-11-03
> **wolfen69 said:**
> Then why not just add libdvdcss2?

It doesn't work. It has to be compiled with it.

---

### Post by haqking on 2011-11-03
> **beew said:**
> It doesn't work. It has to be compiled with it.

I have always used the K3B out of the repos in my Ubuntu Builds and burn DVD's all the time.

I am on debian now and only have Ubuntu in VM but K3B is always my choice of authoring software, never had an issue with DVD ?

Edit: oh i see you want to rip a DVD

---

### Post by beew on 2011-11-03
> **haqking said:**
> I have always used the K3B out of the repos in my Ubuntu Builds and burn DVD's all the time.

I am on debian now and only have Ubuntu in VM but K3B is always my choice of authoring software, never had an issue with DVD ?

Edit: oh i see you want to rip a DVD

yes, I want to rip dvds. Should have been more clear.

---

### Post by wolfen69 on 2011-11-03
> **beew said:**
> yes, I want to rip dvds. Should have been more clear.

K3B has an option to rip DVD's. Add the extra codecs and try it.

---

### Post by beew on 2011-11-03
> **wolfen69 said:**
> K3B has an option to rip DVD's. Add the extra codecs and try it.
I know it has an option, but it is crippled because the Ubuntu builds are not compiled with libdvdcss, that is why I am trying to compile it myself. I have also installed all the extra codecs, it doesn't work. You can try it yourself, maybe I am missing something.

I am using handbrake to rip dvds and it works well (except for one small problem which is not fatal [http://ubuntuforums.org/showthread.php?t=1864112](http://ubuntuforums.org/showthread.php?t=1864112)), but I would like to have other options and it just bothers me that they cripple k3b like that while it should work.

---

### Post by mc4man on 2011-11-04
There is no need to build k3b for libdvdcss support - it is built-in ( look in the source .. /libk3b/tools, you'll see the .h & .cpp

If you were simply asking k3b to rip to .iso it will do so no issue unless there is structure protection which would then may  cause errors

if you are looking to rip & transcode them maybe k3b can do that though I'd think you'd need to install some transcode libs.

As far as a ffmpeg patch - (k)ubuntu has done that for 11.10 - the patch is in 11.10 k3b source/debian/patches dir. (kubuntu_06_libav_0.7.diff, though no real need to build k3b

screen shows k3b retrieving the decrypt keys (using the installed libdvdcss

---

### Post by beew on 2011-11-04
Success! Well ALMOST.

Here is what I did. 

I build k3b basically following the instructions here (though I have to find the list of dependencies somewhere else,--I saved the list somewhere on a different computer so can't post them now)

[http://k3b.plainblack.com/git](http://k3b.plainblack.com/git)

But for this to work  I had to make the following changes before the step > cmake ..For the ffmpeg step to go through in compiling one needs to replace ffnpegdecoder and ffmpegwrapper with the updates here.

[http://quickgit.kde.org/?p=k3b.git&a=commitdiff&h=4d869c8a9377f3f319f60015dd2960d257966043](http://quickgit.kde.org/?p=k3b.git&a=commitdiff&h=4d869c8a9377f3f319f60015dd2960d257966043)

(open the link [a/plugins/decoder/ffmpeg/k3bffmpegdecoder.cpp]("http://quickgit.kde.org/?p=k3b.git&a=blob&h=974a644962ed9e95d3be39b820c16ddd2e4ccfb1&hb=4d869c8a9377f3f319f60015dd2960d257966043&f=plugins/decoder/ffmpeg/k3bffmpegdecoder.cpp"), copy and paste to gedit and then save as k3bffmpegdecoder.cpp and then replace the file with the same name in ~/k3b/plugins /decoder/ffmpeg with this one, do the same for k3bffmpegwrapper.cpp)

Also, in order for the make step to go through one needs to edit k3b/CMakeList.txt by deleting the line > add_subdirectory( doc )I have succeeded in ripping a test dvd into .avi with this build.

**Things that still don't work. **

For some reason all the audio plugins seem to be absent (flac, ogg, mp3 etc) even though all the codecs are in place and they seem to be built successfully (see screenshot) I tried to rip a CD the only output format available is .wav.

I would appreciate it if someone can tell me what went wrong.

```
[  0%] Built target k3bdevice_automoc
[  4%] Built target k3bdevice
[  4%] Built target k3b_automoc
[ 39%] Built target k3b
[ 39%] Built target k3b_bin_automoc
[ 87%] Built target k3b_bin
[ 87%] Built target actions for org.kde.k3b
[ 87%] Built target k3bhelper_automoc
[ 87%] Built target k3bhelper
[ 87%] Built target kio_videodvd_automoc
[ 88%] Built target kio_videodvd
[ 88%] Built target k3bwavedecoder_automoc
[ 89%] Built target k3bwavedecoder
[ 89%] Built target k3boggvorbisdecoder_automoc
[ 89%] Built target k3boggvorbisdecoder
[ 89%] Built target k3bffmpegdecoder_automoc
[ 90%] Built target k3bffmpegdecoder
[ 90%] Built target k3bflacdecoder_automoc
[ 91%] Built target k3bflacdecoder
[ 91%] Built target k3bmaddecoder_automoc
[ 92%] Built target k3bmaddecoder
[ 92%] Built target k3bmpcdecoder_automoc
....
-- Installing: /usr/local/lib/kde4/k3bwavedecoder.so
-- Set runtime path of "/usr/local/lib/kde4/k3bwavedecoder.so" to "/usr/local/lib"
-- Installing: /usr/local/share/kde4/services/k3bwavedecoder.desktop
-- Installing: /usr/local/lib/kde4/k3boggvorbisdecoder.so
-- Set runtime path of "/usr/local/lib/kde4/k3boggvorbisdecoder.so" to "/usr/local/lib"
-- Installing: /usr/local/share/kde4/services/k3boggvorbisdecoder.desktop
-- Installing: /usr/local/lib/kde4/k3bffmpegdecoder.so
-- Set runtime path of "/usr/local/lib/kde4/k3bffmpegdecoder.so" to "/usr/local/lib"
-- Installing: /usr/local/share/kde4/services/k3bffmpegdecoder.desktop
-- Installing: /usr/local/lib/kde4/k3bflacdecoder.so
-- Set runtime path of "/usr/local/lib/kde4/k3bflacdecoder.so" to "/usr/local/lib"
-- Installing: /usr/local/share/kde4/services/k3bflacdecoder.desktop
-- Installing: /usr/local/lib/kde4/k3bmaddecoder.so
-- Set runtime path of "/usr/local/lib/kde4/k3bmaddecoder.so" to "/usr/local/lib"
-- Installing: /usr/local/share/kde4/services/k3bmaddecoder.desktop
-- Installing: /usr/local/lib/kde4/k3bmpcdecoder.so
-- Set runtime path of "/usr/local/lib/kde4/k3bmpcdecoder.so" to "/usr/local/lib"
-- Installing: /usr/local/share/kde4/services/k3bmpcdecoder.desktop
-- Installing: /usr/local/lib/kde4/k3blibsndfiledecoder.so
-- Set runtime path of "/usr/local/lib/kde4/k3blibsndfiledecoder.so" to "/usr/local/lib"

```Also k3b complains that it doesn't have  mp3 plugin but k3bmaddecoder was built (not install?) from the output above.

Finally, as the output above shows the build process installs a whole bunch of things (the k3b bin file is in /usr/local/bin), how do I uninstall it? Do I just remove /usr/local/bin/k3b? It doesn't show up in Synaptic.

---

### Post by beew on 2011-11-04
> **mc4man said:**
> There is no need to build k3b for libdvdcss support - it is built-in ( look in the source .. /libk3b/tools, you'll see the .h & .cpp

If you were simply asking k3b to rip to .iso it will do so no issue unless there is structure protection which would then may  cause errors

if you are looking to rip & transcode them maybe k3b can do that though I'd think you'd need to install some transcode libs.

As far as a ffmpeg patch - (k)ubuntu has done that for 11.10 - the patch is in 11.10 k3b source/debian/patches dir. (kubuntu_06_libav_0.7.diff, though no real need to build k3b

screen shows k3b retrieving the decrypt keys (using the installed libdvdcss

Do you make iso by going to tools > copy medium? Otherwise I don't see any option to create iso

Anyway I go to tools> rip video dvd and nothing happens. It is not just one dvd, but all of then even though transcode and all the relevant stuffs have been installed (I have ripped them with handbrake with no problem) This does not happen in only one Ubuntu install, but in all of them. I actually did some research before I posted this thread and the answer I found was that the Ubuntu build cannot rip dvd because it is not compiled with libdvdcss because of some licensing politics.

  This explanation seems to make sense as I have sort of succeeded in building k3b myself and with this version I am able to rip the same dvds that I couldn't with the official build (tools > rip video dvd). If the official build already has libdvdcss enabled why do you think that is? (I should add the rips turn out to be quite good in quality except for the fact that I can't rip subtitles)

---

### Post by beew on 2011-11-05
I have recompiled k3b several times but still can't get the audio plugins working. They were created in the folder /usr/local/lib and /usr/local/lib/kde4 but somehow k3b appears to not able to detect them (Settings > Configuring k3b > Plugins shows nothing)

I have tried installing and deinstalling the package libk3b-extracodecs during and after compiling and still made no difference. The package libk3b-extracodecs basically just have the same plugins as those which are compiled but they live in /usr/lib/kde4/ instead of /usr/local/lib/kde4/

I think this is some kind of linking problem. Help will always be appreciated. Thanks.

---

### Post by beew on 2011-11-05
Tried create a folder /usr/share/apps/k3b/plugins  and moving all the plugins there. Didn't work.

---

### Post by wolfen69 on 2011-11-05
Do your videos *have* to be avi? Handbrake will rip a DVD pretty easily, but only supports 2 output formats- MP4 and MKV.

---

### Post by haqking on 2011-11-05
> **wolfen69 said:**
> Do your videos *have* to be avi? Handbrake will rip a DVD pretty easily, but only supports 2 output formats- MP4 and MKV.

k9copy will rip to avi.

VLC rips dvd's also amongst many others

---

### Post by beew on 2011-11-05
> **haqking said:**
> k9copy will rip to avi.

VLC rips dvd's also amongst many others

Oh I know there are other alternatives, I am quite happy with handbrake actually. But I use k3b for making and ripping CDs and I quite like it too, it just bothers me that it has options for ripping dvds but somehow it doesn't work. 

I am now able to rip with k3b dvds after compiling it. The only problem left is to make it link to the audio plugins properly. See my last 3 posts.

---

### Post by beew on 2011-11-05
> **wolfen69 said:**
> Do your videos *have* to be avi? Handbrake will rip a DVD pretty easily, but only supports 2 output formats- MP4 and MKV.

I use handbrake, that is actually the best ripping software among the few that I have tried and I actually prefer mkv. But that is not really the point. :)

I think it would be nice  to fix k3b so that it works as advertised, I think it is a very nice software and it is so pretty too, also I don't like to install crippled software in my machine . :) (and I think it should be able to rip in other formats if the plugins are linked properly)

---

### Post by mc4man on 2011-11-05
you were semi-correct, the default k3b will not do a dvdvideo rip & encode.

The reason is not that it hasn't been built with libdvdcss support, it is that it hasn't been built with libdvdread support.

That explains why it will copy & decrypt a dvd, but not do 'dvd video ripping', a copy does not need dvd navigation.

If you look at the build-deps for k3b (ubuntu repo), you'll see that libdvdread-dev is not included.

Can also be clearly seen in the configure, without libdvdread-dev installed the red won't be enabled
 > The following dependencies were found.
-----------------------------------------------------------------------------
   * kdelibs - The toolkit K3b uses to build
   *[COLOR="Red"] libDVDRead - Libdvdread provides a simple foundation for reading DVD video disks[/COLOR].

So anyway - went ahead & rebuilt the current ubuntu source as .deb's with libdvdread-dev installed, now dvdripping is enabled - screen

---

### Post by beew on 2011-11-05
Hi, mc4man

Thanks for the explanation. How do you rebuild the Ubuntu source as .deb? Can you provide a link for the instructions? Does your build find all the audio plugins?

I have built k3b from git and for that I needed to change 3 files (re ffmpeg and disabling add subdirectory (doc)) and still can't link to the plugins properly.

Thanks.

Question: what is the reason for not compiling with libdvdread??

---

### Post by mc4man on 2011-11-05
Warning - k3b uses the system shared libavcodec; libavformat, that's why you'll see the -devs for them installed as build-deps
If you have a self built  ffmpeg ala Fakeoutdoorsman's guide you must remove it prior to the k3b build or it will use those headers instead & the build will fail on ffmpeg errors - could be your current issue with the git?
(note - the above would also apply if you have a ppa versions of the ffmpeg libs, you must use the ubuntu packages

After the build is completed you can remove libavcodec-dev, libavformat-dev & re-install your self-built ffmpeg

Don't know why no libdvdread support, maybe some restricted deal, maybe a Debian thing.

I believe all plugins where built - it's on my 12.04 install, not currently on

A short, quick how-to, 1 command you'll need to do yourself because don't know if you're on natty or OO

```
sudo apt-get install -y libdvdread-dev \
libmp3lame-dev devscripts phonon-backend-gstreamer; \
sudo apt-get -y build-dep k3b

```

```
mkdir k3b1; cd k3b1; \
apt-get source k3b
```

Leave terminal open & do below if desired

If you wish to not have to remember to prevent these new packages being  updated back to the repo version then browse to the source folder > debian folder, open up the changelog. No need to be completely proper for your own build so at the very first line append to the version a +nmu1
Ex. 
> k3b (2.0.2-0ubuntu4[COLOR="Blue"]+nmu1[/COLOR]) oneiric; urgency=low

Now back at terminal cd to source dir., ex. here on 11.10
```
cd k3b-2.0.2
```
At that prompt just run
```
debuild -us -uc
```

Once the packages are built create a dir. in k3b1 named in & place all the .debs you wish to  upgrade in it. then cd to in & run
```
sudo dpkg -i *.deb
```
I'd just put these 4 in the 'in' folder, otherwise you'll likely get broken packages

> in$ ls
k3b_2.0.2-0ubuntu4+nmu1_i386.deb      libk3b6_2.0.2-0ubuntu4+nmu1_i386.deb
k3b-data_2.0.2-0ubuntu4+nmu1_all.deb  libk3b6-extracodecs_2.0.2-0ubuntu4+nmu1_i386.deb


debuild will produce a full build log file - if any issues you can review from it

---

### Post by beew on 2011-11-05
Thanks! I will try it out later and see how it goes. I am on 11.04 and using system ffmpeg but using libvacodec-extra abd libvaformat-extra from medibuntu, is that a problem? (Edit: ok I see I will just down grade the medibuntu packages and reinstall them after, or maybe the same patch for the git will work)

---

### Post by mc4man on 2011-11-05
> **beew said:**
> Thanks! I will try it out later and see how it goes. I am on 11.04 and using system ffmpeg but using libvacodec-extra abd libvaformat-extra from medibuntu, is that a problem? (Edit: ok I see I will just down grade the medibuntu packages and reinstall them after, or maybe the same patch for the git will work)

I don't think the medibuntu packages are an issue - you can leave
The ubuntu k3b source in natty does not need or have a ffmpeg patch, I'd just build it as described, leave the source alone as far as ffmpeg is concerned

---

### Post by beew on 2011-11-06
Hi, mc4man,
 
 Everything works, I have tested with 2 DVDS . Thanks for going out of  your way to actually compile k3b yourself, I really appreciate it.

Is this the general procedure for building from debian source?  What do the options -us and -uc  mean in the dbuild statement?

It takes a lot longer to build k3b this way than from git and it pulls  in a lot more dependencies. What would be the reason for that? I am  still curious why the git build doesn't link to the plugins. I think the  directory for the plugins is hard coded in one of the files. I am  wondering if you can give me some ideas where I should look? (If you don't have any suggestion off the top of your head don't  worry about it, you have done more than enough already)

 There is one little thing though, at least on Natty k3b doesn't build unless the line > add_subdirectory( doc )                       is deleted from k3b1/CMakeList.txt (same issue building from git) It is probably fixed in later versions.

Here is the explanation for not compiling k3b with libdvdread, it sounds kind of ridiculous to me, especially since they have already compiled it with libdvdcss
[https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/99448](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/99448)

Big thanks again!

---

### Post by mc4man on 2011-11-06
Not sure about the git build, haven't tried.
Many times after doing a make/make install or checkinstall you need to run this
```
sudo ldconfig
```

Most package builds have increased dep's mainly for libs needed to create .deb's, sometimes for add. configue options as .debs are built for everyone 
-us    Do not sign the source package.
-uc    Do not sign the .changes file.
.

---

