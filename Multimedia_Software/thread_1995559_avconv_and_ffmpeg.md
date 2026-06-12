---
title: "avconv and ffmpeg"
date: 2012-06-03
forum: Multimedia Software
---

### Post by Geffers on 2012-06-03
I am running 12.04 and noted a message that ffmpeg is not being developed anymore and suggested avconv instead.

A quick look and the flags look the same, are these actually the same program.

Geffers

---

### Post by mc4man on 2012-06-03
Some developers broke away from FFmpeg & started Libav which is what Debian/Ubuntu has chosen to use.
FFmpeg is very much alive - both FFmpeg & Libav seem to take commits from each other at times. So they are similar but there are differences

Many users choose to build the real FFmpeg for standalone use

The message you are seeing is due to be changed to be a bit more accurate, though the bug I had on that verged on the ridiculous to even get the current one- (applied in 12.10 but not yet in 12.04
> *** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.

Here's the bug if curious - even my orig. description had to be changed before being considered, the whole deal is a bit of a joke..
[https://bugs.launchpad.net/ubuntu/+source/libav/+bug/939863](https://bugs.launchpad.net/ubuntu/+source/libav/+bug/939863)

---

### Post by FakeOutdoorsman on 2012-06-04
> **mc4man said:**
> Here's the bug if curious - even my orig. description had to be changed before being considered, the whole deal is a bit of a joke..
[https://bugs.launchpad.net/ubuntu/+source/libav/+bug/939863](https://bugs.launchpad.net/ubuntu/+source/libav/+bug/939863)

That and the checkinstall runaround put me off of Launchpad for a while.

---

### Post by Geffers on 2012-06-04
> **mc4man said:**
> Some developers broke away from FFmpeg & started Libav which is what Debian/Ubuntu has chosen to use.
FFmpeg is very much alive - both FFmpeg & Libav seem to take commits from each other at times. So they are similar but there are differences

Many users choose to build the real FFmpeg for standalone use



So anyone any comments as to pros and cons, the message refers to avconv as Hyper fast Audio and Video encoder.

Geffers

---

### Post by FakeOutdoorsman on 2012-06-04
To the general user there should be little difference. I prefer FFmpeg but I'm biased (and the developers are nicer).

---

### Post by ajgreeny on 2012-06-05
> **FakeOutdoorsman said:**
> To the general user there should be little difference. I prefer FFmpeg but I'm biased (and the developers are nicer).
And as I use ffmpeg quite a lot, are there any big differences in the commands or syntax used for avconv versus ffmpeg?

---

### Post by Geffers on 2012-06-05
> **FakeOutdoorsman said:**
> To the general user there should be little difference. I prefer FFmpeg but I'm biased (and the developers are nicer).

Thanks FakeOutdoorsman.

I saved an ffmpeg folder from my old setup, I assume it will just run from there; I've had a couple of simple tests and it seems OK but wondering about codecs etc.

Geffers

---

### Post by FakeOutdoorsman on 2012-06-05
> **ajgreeny said:**
> And as I use ffmpeg quite a lot, are there any big differences in the commands or syntax used for avconv versus ffmpeg?

I have almost no experience with avconv, so I'm not really sure. I assume it's probably pickier about the new syntax structure while they all seem to work in ffmpeg: -c:v instead of -vcodec, -b:v instead of -b, etc. Here's a [list of changed options](http://libav.org/#fftools_rename).

> **Geffers said:**
> I saved an ffmpeg folder from my old setup, I assume it will just run from there; I've had a couple of simple tests and it seems OK but wondering about codecs etc.

Hard to say without knowing your old setup. If the ffmpeg binary is in your directory go ahead and give it a try: cd ~/ffmpeg; ./ffmpeg -i input ... output.

Nobody said you can't have both:
```
sudo apt-get update
sudo apt-get -y install build-essential git yasm
cd
mkdir -p junk/src
git clone git://git.videolan.org/x264
cd x264
./configure --prefix=$HOME/junk --enable-static
make
make install
cd
git clone --depth 1 git://source.ffmpeg.org/ffmpeg
cd ffmpeg
./configure --extra-cflags="-I$HOME/junk/include" --extra-ldflags="-L$HOME/junk/lib" --enable-gpl --enable-libx264
make
```
This will just perform a local installation of recent x264 (the x264 binary will be in *~/junk/bin*) and ffmpeg binary will be in *~/ffmpeg*.

---

