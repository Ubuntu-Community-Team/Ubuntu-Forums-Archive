---
title: "Convert from DVR to MP4"
date: 2013-05-31
forum: Multimedia Software
---

### Post by alfirdaous on 2013-05-31
Hello everybody,

I would like to convert a vdr video to mp4 file, it does not work:

```

ffmpeg -i test_write1.dvr -vcodec libx264 -preset medium copy -acodec copy outputFile.mp4
ffmpeg version 0.8.6-6:0.8.6-1ubuntu2, Copyright (c) 2000-2013 the Libav developers
  built on Mar 30 2013 22:20:06 with gcc 4.7.2
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[mp3 @ 0x1c76b80] Format detected only with low score of 1, misdetection possible!
[mp3 @ 0x1c78f20] Header missing
    Last message repeated 448 times
[mp3 @ 0x1c76b80] Could not find codec parameters (Audio: mp2, 0 channels, s16)
[mp3 @ 0x1c76b80] Estimating duration from bitrate, this may be inaccurate
test_write1.dvr: could not find codec parameters

```

file mediainfo:

```

 mediainfo test_write1.dvr 
General
Complete name                            : test_write1.dvr
File size                                : 1.47 MiB

```

which codec shall I use??

Thx in advance

---

### Post by andrew.46 on 2013-06-07
Looks like a small file, can you post it somewhere so I can have a look?

---

### Post by Dale61 on 2013-06-09
Can you convert it with Handbrake?  Handbrake can be found in the Software Centre.

---

### Post by alfirdaous on 2013-06-09
> **andrew.46 said:**
> Looks like a small file, can you post it somewhere so I can have a look?

this is the file: [http://www.speedyshare.com/vmw2y/test-write1.dvr](http://www.speedyshare.com/vmw2y/test-write1.dvr)

[QUOTE=Dale61]Can you convert it with Handbrake?  Handbrake can be found in the Software Centre.[/QUOTE]

```

# apt-get install handbrake-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package handbrake-gtk

```

---

### Post by Dale61 on 2013-06-09
> **alfirdaous said:**
> this is the file: [http://www.speedyshare.com/vmw2y/test-write1.dvr](http://www.speedyshare.com/vmw2y/test-write1.dvr)



```

# apt-get install handbrake-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package handbrake-gtk

```

Looks like you have to make an addition to your repositories.

In Software Sources, under the Other Software tab, click add

[http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu) precise

If you have an install other than precise (12.04), change the last entry to match what you have.

---

### Post by alfirdaous on 2013-06-10
I am having Ubuntu 13.04, but I dont know 'precise' with what I should change it:
```

# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring

```

EDIT:

```

sudo vim /etc/apt/sources.list

deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu raring main


sudo apt-get update
W: GPG error: http://ppa.launchpad.net raring Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8771ADB0816950D8
W: Failed to fetch http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/dists/raring/main/binary-amd64/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

my sources.list:

```

deb http://archive.ubuntu.com/ubuntu/ raring main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ raring-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ raring-updates main restricted universe multiverse

#Handbrake
deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu raring main

#Flash Plugin
# deb http://archive.canonical.com/ubuntu oneiric partner

```

---

### Post by Dale61 on 2013-06-10
Try it up to the ubuntu entry, and see what happens.  If nothing, add raring instead of precise.

If none of that works, try searching google for a how-to.

---

### Post by alfirdaous on 2013-06-10
post edited above

---

### Post by Dale61 on 2013-06-10
[How to Install Handbrake on Ubuntu 13.04]("http://linuxg.net/how-to-install-handbrake-on-ubuntu-13-04/")

---

### Post by alfirdaous on 2013-06-10
```

# wget -c https://launchpad.net/~stebbins/+archive/handbrake-releases/+files/handbrake-gtk_0.9.8%2Bppa1~quantal1_i386.deb
--2013-06-10 06:22:14--  https://launchpad.net/~stebbins/+archive/handbrake-releases/+files/handbrake-gtk_0.9.8%2Bppa1~quantal1_i386.deb
Resolving launchpad.net (launchpad.net)... 91.189.89.222, 91.189.89.223
Connecting to launchpad.net (launchpad.net)|91.189.89.222|:443... connected.
HTTP request sent, awaiting response... 404 Not Found
2013-06-10 06:22:15 ERROR 404: Not Found.

```

is there a way using Terminal instead??

---

### Post by Dale61 on 2013-06-10
[how to install handbrake ubuntu]("https://www.google.com.au/#output=search&sclient=psy-ab&q=how+to+install+handbrake+ubuntu&oq=How&gs_l=hp.1.0.35i39j0l3.2918.4057.0.8224.3.3.0.0.0.0.349.968.2-1j2.3.0.crnk_timepromotionb..0.0...1.1.16.psy-ab.8biI2F4fG5k&pbx=1&bav=on.2,or.r_cp.r_qf.&bvm=bv.47534661,d.dGI&fp=d0225229effbfdad&biw=1366&bih=583")

Look through these and see what you come up with.  All I did was find it in the Software Centre, and installed it from there.

---

### Post by Dale61 on 2013-06-10
Try:
sudo add-apt-repository ppa:stebbins/handbrake-releases

then:
sudo apt-get install handbrake-gtk handbrake-cli

---

### Post by alfirdaous on 2013-06-10
while importing the video, it is not imported successfully, I think it is not supported, I changed it to another video file:

```

$ mediainfo 001.dvr 
General
Complete name                            : 001.dvr
Format                                   : MPEG Video
Format version                           : Version 2
File size                                : 50.0 MiB
Overall bit rate mode                    : Variable

Video
Format                                   : MPEG Video
Format version                           : Version 2
Format profile                           : Main@Main
Format settings, BVOP                    : Yes
Format settings, Matrix                  : Custom
Bit rate mode                            : Variable
Maximum bit rate                         : 4 299 Kbps
Width                                    : 720 pixels
Height                                   : 576 pixels
Display aspect ratio                     : 16:9
Frame rate                               : 25.000 fps
Standard                                 : PAL
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Interlaced
Scan order                               : Top Field First
Compression mode                         : Lossy


```

---

### Post by andrew.46 on 2013-06-10
> **alfirdaous said:**
> this is the file: [http://www.speedyshare.com/vmw2y/test-write1.dvr](http://www.speedyshare.com/vmw2y/test-write1.dvr)

Hmmm.... this page would only let me download the file in conjunction with some sort of windows-based download manager :(

---

### Post by Dale61 on 2013-06-10
> **alfirdaous said:**
> while importing the video, it is not imported successfully, I think it is not supported, I changed it to another video file:

Maybe the .dvr filename is not recognised, but at least you were finally able to install Handbrake.

By importing, do you mean it can't successfully read from the source file?  If so, try another video file and see what happens.  I use Handbrake to convert from DVD to mp4, and the only trouble I've had is when it tries to read a dodgy DVD.

---

### Post by alfirdaous on 2013-06-10
I tried OGV file, it works, but with dvr it doesn't

---

### Post by FakeOutdoorsman on 2013-06-10
> **andrew.46 said:**
> Hmmm.... this page would only let me download the file in conjunction with some sort of windows-based download manager :(

It's a misleading site. The link to the file is the phrase "Download: test write1.dvr" at the top of the page.

---

### Post by andrew.46 on 2013-06-11
> **FakeOutdoorsman said:**
> It's a misleading site. The link to the file is the phrase "Download: test write1.dvr" at the top of the page.

I allow myself one stupidity per day, a pity this is my second :(. Now that I have seen the file it is unplayable and nonconvertible with all of the Linux-based applications at my disposal. I suspect it is either:

[LIST=1]
[*]A broken file
[*]Playable only with proprietary software
[/LIST]

---

### Post by alfirdaous on 2013-06-11
It was recorded from a receiver

---

### Post by Dale61 on 2013-06-11
Unless the source djsc was finalised, it will only play in the what it was recorded on.  When I have to use a DVD Recorded, I record to the HDD, then burn to a DVD-RW so I can re-use the disc at a later date.

---

### Post by SeijiSensei on 2013-06-12
> **alfirdaous said:**
> It was recorded from a receiver

If you mean it was recorded by a commercial DVR like the ones connected to cable TV systems, then it's very likely the file is encoded using closed proprietary methods.  Commercial DVRs are designed to make it impossible for someone simply to pull out the drive and archive the stored programs on it.  Otherwise copying from DVRs would be a simple method to create high-definition unauthorized copies of movies and TV shows.

---

### Post by alfirdaous on 2013-06-14
so I think there is no way to sort it out

---

### Post by Dale61 on 2013-06-14
Keep checking back as someone who is proficient in using dvr files might come up with an answer.

---

### Post by alfirdaous on 2013-06-14
thank you very much guys

---

