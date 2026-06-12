---
title: "easy way to install older vlc version?"
date: 2018-06-03
forum: Multimedia Software
---

### Post by babag on 2018-06-03
for reasons too long to bother with i need to install an older version of vlc, maybe v2.2.8. is there an easy way to do this? when i use synaptic with my basic setup i just get the new v3 version.

thanks,
babag

---

### Post by ajgreeny on 2018-06-03
Probably no "easy" way short of compiling it yourself, and I'm not sure how easy that will be for an older version.

Without wishing for too long a description, what is your real reason for needing the 2.2.# version rather than v3?
There may be other ways we can help you to be happy with the new version.

---

### Post by babag on 2018-06-03
i'm using some beta software that uses vlc for its video playback and it has not yet been made compatible with vlc 3. being unreleased i can't be more specific. binaries seem to still be available for windows and mac but i haven't seen anything that easy for linux.

thanks,
babag

---

### Post by mohicann on 2018-06-03
Have you tried to look up for the right version for you here:

[http://ubuntuhandbook.org/index.php/2017/11/install-vlc-2-2-7-2-2-8-in-ubuntu-16-04-14-04/](http://ubuntuhandbook.org/index.php/2017/11/install-vlc-2-2-7-2-2-8-in-ubuntu-16-04-14-04/)

[https://launchpad.net/~jonathonf/+archive/ubuntu/vlc](https://launchpad.net/~jonathonf/+archive/ubuntu/vlc)

---

### Post by babag on 2018-06-04
just tried adding the jonathonf repository per the instructions on the linked page and get:

The repository 'http://ppa.launchpad.net/jonathonf/vlc/ubuntu bionic Release' does not have a Release file.

any thoughts?

thanks,
babag

---

### Post by Holger_Gehrke on 2018-06-04
> **babag said:**
> 
The repository 'http://ppa.launchpad.net/jonathonf/vlc/ubuntu bionic Release' does not have a Release file.


That error means that there are no files meant for your distribution in that repository.

You could try to manually download the packages for the older version of vlc from [http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/](http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/) and install them with dpkg, but those packages probably depend on older versions of various libraries than the ones in your system, so they might not install.

Holger

---

### Post by kazakore on 2018-06-04
> **Holger_Gehrke said:**
> That error means that there are no files meant for your distribution in that repository.

You could try to manually download the packages for the older version of vlc from [http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/](http://archive.ubuntu.com/ubuntu/pool/universe/v/vlc/) and install them with dpkg, but those packages probably depend on older versions of various libraries than the ones in your system, so they might not install.

Holger

I didn't know about that Archive page, could be useful.

I'd usually search for the package thus:
[https://packages.ubuntu.com/search?keywords=vlc](https://packages.ubuntu.com/search?keywords=vlc)
Then you can see the most recent version of Ubuntu which had the version you want and trying to install the .deb from that using dpkg. Once you click on the package name it also gives a list and links to all required dependancies, of which there seems to be a few for VLC, all named vlc-(something) and all exactly match the version number and thus would almost definitely need to be installed to get it working correctly.

Also note you will likely want to Mark the manually installed packages as Held so that the system doesn't try and upgrade them.

---

### Post by Holger_Gehrke on 2018-06-04
> **kazakore said:**
> I didn't know about that Archive page, could be useful.

That's just the way repositories work: A repository is just a website. There's a directory 'dists' which has a directory per distribution with informations for apt (basically telling apt what packages belong to the distribution it's running on) and a directory pool with all the packages, split into directories for the various series' and the starting letter(s) of the packages.

Holger

---

### Post by Habitual on 2018-06-04
Couple of "options". Virtual guest that incorporates v.2.x.x 
or 
[source code]("http://download.videolan.org/pub/videolan/vlc/") install
or

---

### Post by monkeybrain20122 on 2018-06-04
I will go source code install. You never said which Ubuntu is it, but if it is 18.04 you probably need to compile an old version of ffmpeg as well and vlc to it. It is not hard, just a bit tedious. You may need a copy of ffmpeg 2.8 (version for Ubuntu 16.04)

(If system ffmpeg works, then don't need to build, so you should try building vlc with system ffmpeg first, if not work get a ffmpeg tarball and build it then vlc)

so install the prerequistes

```
sudo apt build-dep vlc &&
sudo apt build-dep ffmpeg

```

get the build tools
```

sudo apt install automake build-essential
```

download whatever ffmpeg version you need, extract the tarball

download whatever vlc version you need, extract to a folder which I will call vlc_source_code_folder (not to be confused with the vlc folder you create below)


create a folder called vlc in your home

```
mkdir vlc

export PREFIX=/home/your_username/vlc

```

compile ffmpeg


```
cd /path/to/ffmpeg/folder

./configure --prefix=$PREFIX  
    --enable-gpl --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray--enable-libbs2b --enable-libcaca --enable-libcdio \
    --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm \
   --enable-libmodplug--enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopus --enable-libpulse --enable-librubberband \
   --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora \
   --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxvid --enable-libzimg \ 
   --enable-libzmq --enable-libzvbi --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-nonfree \
    --enable-libfdk-aac --enable-nvenc --enable-libdc1394 --enable-libiec61883 --enable-libopencv --enable-frei0r --enable-libx264 --enable-shared \
  make -j4
  make install -j4

```

Some options may not work depending on your ffmpeg version or you may need to install extra dependencies from repo. just check the ./configure outputs for errors. 

now for vlc

```
cd /path/to/vlc_source_code_folder

./bootstrap

./configure --prefix=$PREFIX

make -j4

make install -j4

```

if all work you will find vlc binary in ~/vlc/bin, you can click it or create a .desktop file with exec=/home/usrname/vlc/bin/vlc

---

