---
title: "NVidia 180.06 driver with PureVideo support [SUCCESS!]"
date: 2008-11-16
forum: Multimedia Software
---

### Post by crispy_chunks on 2008-11-16
For some time ive been puzzling around planning to buy some new hardware and upgrade my media center so i can play my x264 encoded movies at a decent framerate. However with nvidias new driver I dont have to upgrade anything to do this! If you want to install the new driver you can get it from [here]("ftp://download.nvidia.com/XFree86/Linux-x86_64/180.06/") (you need all 3 packages i think)

(EDIT: I should probably add that x264 decoding is only supported by 8k and 9k series)

So run these commands to download:

```

wget ftp://download.nvidia.com/XFree86/Linux-x86_64/180.06/NVIDIA-Linux-x86_64-180.06-pkg0.run

wget ftp://download.nvidia.com/XFree86/Linux-x86_64/180.06/NVIDIA-Linux-x86_64-180.06-pkg1.run

wget ftp://download.nvidia.com/XFree86/Linux-x86_64/180.06/NVIDIA-Linux-x86_64-180.06-pkg2.run

```

This is the installer. You will have to close you Xserver now (will close the GUI, so read the rest of this guide):

I didnt have any troubles installing the new driver, but if you are afraid to fix broken stuff you probably dont want this.

```

sudo /etc/init.d/gdm stop

```

Which can be started again with 

```

sudo /etc/init.d/gdm start

```

Now run the installer:

```
sudo sh NVIDIA-Linux-x86_64-180.06-pkg0.run
```

and follow the instructions. If all goes well you will after starting gdm be running the new driver with PureVideo support.

To use this new feature you will have to compile a new version of mplayer. Download and extract and go to the folder:

```
wget ftp://download.nvidia.com/XFree86/vdpau/mplayer-vdpau-3076399.tar.bz2

tar xvf mplayer-vdpau-3076399.tar.bz2

cd mplayer-vdpau-3076399

```

This is from the README in that folder:

> Current support:
        The NVIDIA 180.06 beta driver for Linux, Solaris, and FreeBSD
        provides initial VDPAU support for some GeForce 8xxx and 9xxx
        series GPUs.  Please see the VDPAU announcement on the nvnews.net
        Linux forum for further details.

Prerequisite:
        The following should be acquired using your distribution package
        management system, or from source if required:

        * Subversion (svn); See [http://subversion.tigris.org](http://subversion.tigris.org)
        * C development tools: make, gcc, binutils.
        * Various X11 libraries (and their development packages)
          that MPlayer relies upon.

Installing the patch:
        Run the supplied shell script:

        $ sh checkout-patch-build.sh
Running MPlayer:
        $ cd mplayer-vdpau
        $ ./mplayer -vc <VDPAU-codec-name> -vo vdpau <filename>

        'VDPAU-codec-name' can be one of:

            ffmpeg12vdpau
            ffh264vdpau
            ffwmv3vdpau
            ffvc1vdpau

        based on the type of video bitstream (ffmpeg12vdpau for MPEG-1
        or MPEG-2, ffh264vdpau for H.264, ffwmv3vdpau for WMV3, and
        ffvc1vdpau for VC-1).

        If a VDPAU codec is used, the VDPAU output module must be used.

        Alternatively, you may use the VDPAU output module without specifying
        a VDPAU codec. In this case, the bitstream decoding is not accelerated
        using VDPAU, but the decoded video is still presented using VDPAU:

        $ cd mplayer-vdpau
        $ ./mplayer -vo vdpau <filename>




So run the script and run mplayer as they suggest and it should work. Compiling might take some time though.

You might also need to install svn (subversion), binutils  and build-essential as they suggest.

Mine has not yet compiled, so I havent actually tried it yet, but it worked for the guys at phoronix.

---

### Post by crispy_chunks on 2008-11-16
Hehe, was a bit too fast in declaring this a success. I get this error when I try to play zodiac which is in x264 format:

```
Error at libvo/vo_vdpau.c:826

```

Seems like this post explains it: [http://www.nvnews.net/vbulletin/showpost.php?p=1846159&postcount=82](http://www.nvnews.net/vbulletin/showpost.php?p=1846159&postcount=82)

---

### Post by Duranxl on 2008-11-17
So any idea when this whole VDPAU thing will be fully implanted into VLC, mplayer..etc?..supporting x264..wmvhd maybe, hdmov?

---

### Post by crispy_chunks on 2008-11-17
> **Duranxl said:**
> So any idea when this whole VDPAU thing will be fully implanted into VLC, mplayer..etc?..supporting x264..wmvhd maybe, hdmov?

Nope. But from the looks of it, it only seems like this mplayer thing is pretty rough, but many people can play the different formats, so much of it should be working and the rest is down to bugfixes. My guesstimate is that we will have a mplayer that is capable of playing the announced formats in a month and i build that upon absolutely nothing :)

---

### Post by Duranxl on 2008-11-17
Edit:
okai i fixed my problem (no codec found) by removing .mplayer in /home/user
however now i get 
```
'Error at libvo/vo_vdpau.c:637'
or
'Error at libvo/vo_vdpau.c:826'
``` depending on what i'm trying to play (MKV & WMV3)

If neither works, what DOES work??

---

### Post by laceration on 2008-11-18
I was recently reading a howto build a multimedia computer at Arstechnica.com and learned that a linux machine takes considerable more horsepower than a ms windows machine to watch hidef video because the drivers for linux do not support purevideo.  This is a significant advance for linux.  Even though I get some stuttering occasionally, I have some decent hardware so I'll take the easy route and wait for the new drivers upstream.  Nvidia drivers are frequently updated.

---

### Post by SuckerBlood on 2008-11-23
Hi!, :popcorn:

When I compile with the mplayer I execute the video and i have and error:
```
Error at libvo/vo_vdpau.c:179
```

What can I resolve this?? :confused::confused:

---

