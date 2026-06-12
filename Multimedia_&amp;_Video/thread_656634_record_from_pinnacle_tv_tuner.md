---
title: "record from pinnacle tv tuner"
date: 2008-01-02
forum: Multimedia &amp; Video
---

### Post by travist120 on 2008-01-02
HI, I'm using the Pinnacle PCTV Hd stick tv tuner, and I've installed the firmware for it, and I have also gotten it working under TV time, but I can't get it to work under vlc, so that I may record. Here is what happens when I try to get it to work with vlc (by terminal)

```
travis@travis-laptop:~$ vlc v4l:/dev/video0:norm=ntsc:frequency=77250:size=640x480
VLC media player 0.8.6c Janus
[00000299] v4l demuxer error: chroma selection failed
[00000299] v4l demuxer error: cannot set audio format (16b little endian) (Invalid argument)
[00000299] v4l demuxer error: cannot open device (No such file or directory)

```

and yet it works perfectly in TVtime, is there any program that I can use to record OTHER than mythtv?

---

### Post by chrismacgregor on 2008-02-17
The problem seems to be that vlc tests for available formats by trying them with ioctl VIDIOCSPICT, but usbvideo.c (the kernel device driver) does not actually pay any attention to the palette field at all in that ioctl.  I've just submitted a [patch (click here)](http://www.cybermato.com/projects/misc/usbvideo.patch) to fix this, but I don't imagine that will help anyone for a while.

However, in the meantime, you can work around the problem by setting the "Video input chroma format" parameter (under advanced options) to the FOURCC corresponding to the format you want to use.  You can find the list of formats and FOURCC's in the vlc source in modules/access/v4l/v4l.c (search for v4lchroma_to_fourcc), here (hmm, the file is in a different place in subversion already): [http://trac.videolan.org/vlc/browser/trunk/modules/access/v4l.c](http://trac.videolan.org/vlc/browser/trunk/modules/access/v4l.c)

In my case, for a Logitech Quickcam Messenger, setting it to RV24 did the trick.  Your mileage may vary.  It's not clear how you would find out what format your camera likes without hacking vlc; it might be buried someplace in the v4l-info output, but it's hard to tell and I don't seem to have that here on FC7. Of course, you could just try them all, but that's a pain. So I wrote a little program to print out the answer; source below, source and binary (works on FC6 and later, probably most other distros as well) on the [Cybermato Consulting Miscellany (click here)](http://www.cybermato.com/projects/misc) page.

```

// a little hack by Chris MacGregor (http://www.cybermato.com) to help determine what
// format to tell vlc (http://www.videolan.org) to use for a USB webcam on Linux.

#include <sys/ioctl.h>
#include <linux/videodev.h>

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <fcntl.h>

// This table was taken from the vlc sources (v4l.c) and restructured
// slightly.

struct format_to_fourcc
{
    int format;
    const char * fourcc;
};

static struct format_to_fourcc format_to_fourcc[] =
{
    { VIDEO_PALETTE_GREY, "GREY" },
    { VIDEO_PALETTE_HI240, "I240" },
    { VIDEO_PALETTE_RGB565, "RV16" },
    { VIDEO_PALETTE_RGB555, "RV15" },
    { VIDEO_PALETTE_RGB24, "RV24" },
    { VIDEO_PALETTE_RGB32, "RV32" },
    { VIDEO_PALETTE_YUV422, "I422" },
    { VIDEO_PALETTE_YUYV, "YUYV" },
    { VIDEO_PALETTE_UYVY, "UYVY" },
    { VIDEO_PALETTE_YUV420, "I42N" },
    { VIDEO_PALETTE_YUV411, "I41N" },
    { VIDEO_PALETTE_RAW, "GRAW" },
    { VIDEO_PALETTE_YUV422P, "I422" },
    { VIDEO_PALETTE_YUV420P, "I420" },
    { VIDEO_PALETTE_YUV411P, "I411" },
    { 0, 0 }
};

int main (int argc, const char * argv [])
{
    const char * usage_message
        = "Usage: %s /dev/video  (or whatever device you wish to query)\n";

    if (argc != 2)
    {
        printf (usage_message, argv[0]);
        return 1;
    }

    const char * devname = argv[1];

    int fd = open (devname, O_RDWR);
    if (fd < 0)
    {
        perror (devname);
        printf (usage_message, argv[0]);
        return 1;
    }

    struct video_picture vpic;
    if (ioctl (fd, VIDIOCGPICT, &vpic) < 0)
    {
        perror ("ioctl VIDIOCGPICT");
        close (fd);
        return 1;
    }

    const char * fourcc = "(unknown)";
    struct format_to_fourcc * fptr = format_to_fourcc;
    while (fptr->fourcc)
    {
        if (fptr->format == vpic.palette)
        {
            fourcc = fptr->fourcc;
            break;
        }
        ++fptr;
    }
    printf ("Current format is %d, fourcc is %s\n",
            vpic.palette, fourcc);

    close (fd);
    return 0;
}

```

---

### Post by msrinath80 on 2008-03-04
Travist, were there any special instructions on how to get the Pinnacle PCTV HD stick to work with TvTime? Are there any known issues with Ubuntu compatibility? Did you try both ATSC (cable) and HDTV?  I plan to buy one if I know that it will work in Ubuntu. By the way, which Ubuntu did you run it on? Feisty? Gutsy? Hardy?

Eagerly awaiting your response. Thanks for your help!


> **travist120 said:**
> HI, I'm using the Pinnacle PCTV Hd stick tv tuner, and I've installed the firmware for it, and I have also gotten it working under TV time, but I can't get it to work under vlc, so that I may record. Here is what happens when I try to get it to work with vlc (by terminal)

```
travis@travis-laptop:~$ vlc v4l:/dev/video0:norm=ntsc:frequency=77250:size=640x480
VLC media player 0.8.6c Janus
[00000299] v4l demuxer error: chroma selection failed
[00000299] v4l demuxer error: cannot set audio format (16b little endian) (Invalid argument)
[00000299] v4l demuxer error: cannot open device (No such file or directory)

```

and yet it works perfectly in TVtime, is there any program that I can use to record OTHER than mythtv?

---

