---
title: "help! no xorg.conf creates jitters, xorg.conf won't play DVD"
date: 2011-01-07
forum: Multimedia Software
---

### Post by jeffcox65 on 2011-01-07
Hi there -

I posted a question in a different forum a few days ago and got no response, so I've been doing research and think this actually might be the place for my question.

I installed Ubuntu 10.10 from a LiveCD onto an old Dell GX20 connected to my LCD HDTV. The default resolution of 1024x768 is jittery, but plays DVDs.

Since there's no xorg.conf, I created one with X -configure so I could select a different resolution to stop the jitteryness.

When I boot with the new xorg.conf, I can now select 1360x768 which stops the jitter problem, but now there's only audio and no video when I try to play a DVD.

console logs and xorg.conf are here: [http://ubuntuforums.org/showthread.php?t=1660637](http://ubuntuforums.org/showthread.php?t=1660637)

I'm stuck! I tried xrandr to create the desired resolution but get the error "no gamma for output"

Any help would be greatly appreciated.

Thanks!

- Jeff

---

### Post by BicyclerBoy on 2011-01-07
I tried to read the post logs..

The full screen DVD playback could be trying to use a different video mode that the video driver will not allow.

How do you connect the TV display ?
Do you use a proprietary intel driver ? I think your logs show free Xorg driver..

The free *buntu vesa driver is slow & jerky even on an i3 CPU-GPU.

Is there a closed non free driver shown in the gnome desktop menu/hardware drivers ?

 DVD playback requires the ubuntu-restricted-extras package
libdvdnav read4 css2  etc 
So don't confuse multiple problems as one..

---

### Post by tjones00 on 2011-01-07
It's probably a resolution issue as you have already guessed. To fix the jitters and display issues use a progressive resolution. (in reference to your first thread)

With HDTVs resolutions are typically in the ***p (progressive) format eg 1080p but there are also ***i (interlaced) formats eg 1080i.

[http://www.kasperconnections.com/blog/entry/62723/resolution-part-1-i-vs-p-what-does-it-mean-](http://www.kasperconnections.com/blog/entry/62723/resolution-part-1-i-vs-p-what-does-it-mean-)

[http://en.wikipedia.org/wiki/1080p](http://en.wikipedia.org/wiki/1080p)

[http://carltonbale.com/1080p-does-matter](http://carltonbale.com/1080p-does-matter)


Your tv will only work "properly" using the standardized p formats although some i formats are "possible" all the bells and whistles won't work properly. In your case you're getting frequency errors (jitters). If you try to push a HDTV that is already in a high resolution interlaced format you will receive crappy picture quality and refresh rates.

First determine whats possible with your tv. Hopefully you're using a 32b os since it's reported this step (the read-edid programs) does not work on 64b systems.

```
sudo apt-get install read-edid

sudo get-edid | parse-edid
```

This should grab the resolution file directly from your TV and display possible resolutions.  In order for your TV to be classified as HD it should have at least 720p. 1280x720

[http://en.wikipedia.org/wiki/720p](http://en.wikipedia.org/wiki/720p)

Next you can play in xrandr as you have already been and see if it reports 1280x720 as a possible resolution.

Look for the suitable progressive resolution match something that's found with get-edid | parse-edid and also present with xrandr -q ideally 1280x720p for your hardware.

The typical choices should be : 1080p 720p 576p 480p


As to the DVD playback BicyclerBoy is right it could be a DVD playback issue and have nothing to do with your xorg.conf or TV. Have you tried any locally stored media files?

---

### Post by BicyclerBoy on 2011-01-07
The packages read-edid only works on 32 bit intel & vesa driver (I think).

The I2C kernel modules are missing from some kernels as well.

The EDID DDC is an I2C interface.

It should be easy to force a required mode & disable video mode validation by EDID.
But I do not know the intel X server keywords...

---

### Post by tjones00 on 2011-01-07
read-edid/get-edid/parse-edid man

Posted this for that guy who had edid issues we were helping out the other week. His thread seems to be dead now. With all the edid issues coming up recently it doesn't hurt to get more copies of it out on this forum.

The cool thing is you can also use get-edid > edid.bin to create an edid.bin binary file independent of any proprietary driver.

Need to find something similar for 64b systems.

```
get-edid(1)                                                        get-edid(1)



NAME
       get-edid,  parse-edid - read-edid tools to retrieve and interpret moni&#8208;
       tor specifications using the VESA VBE DDC protocol

SYNOPSIS
       get-edid | parse-edid
       get-edid > filename
       parse-edid < filename

DESCRIPTION
       The read-edid utility comprises two tools: get-edid and parse-edid.

       get-edid uses Linux's vm86(2) system call to enter  virtual  8086  mode
       and  perform  Data  Display Channel (DDC) transfers using the VESA BIOS
       Extensions (VBE) to retrieve information from monitors, including iden&#8208;
       tification  strings,  supported sync ranges, available video modes, and
       video mode parameters.  Such information is often useful for  configur&#8208;
       ing X Window System servers such as XFree86.

       The  data obtained by get-edid is in a binary format, so the parse-edid
       command is available to interpret  it  and  generate  a  human-readable
       block  of  text  information  that  can  also be included in an XFree86
       XF86Config file.

       It is customary to invoke get-edid and parse-edid together in  a  pipe&#8208;
       line.

       get-edid  and  parse-edid  accept  no options, recognize no environment
       variables, read no input files, and create no output files.

AUTHOR
       get-edid and parse-edid were written by John  Fremlin,  Dan  Hugo,  and
       Martin  Kavalec,  using the LRMI (Linux Real-Mode Interface) library by
       Josh Vanderhoof.  This manual page was  written  by  Branden  Robinson,
       originally for Debian GNU/Linux.

SEE ALSO
       vm86(2)

       John              Fremlin's              read-edid              website
       &#10216;http://john.fremlin.de/programs/linux/read-edid/&#10217; at http://john.frem&#8208;
       lin.de/programs/linux/read-edid/



Debian GNU/Linux                  2002-10-03                       get-edid(1)
```Package description
```

read-edid consists of two tools:
 .
 get-edid uses a VESA VBE 2 interrupt service routine request to read
a 128 byte EDID version 1 structure from your graphics card, which
retrieves this information from the monitor via the Data Display
Channel (DDC).

get-edid uses architecture-specific methods for querying the video
hardware (real-mode x86 instructions on i386, Open Firmware device
tree parsing on PowerMac) and is therefore only available for i386 and
powerpc architectures.

parse-edid parses this data structure and outputs data suitable for
inclusion into the XFree86 or X.org configuration file. It is available
for any architecture.
```

---

### Post by jeffcox65 on 2011-01-07
Thank you both for your quick reply.

Yes, the jittery screen is due to a bad resolution setting. 1024x768@60 is a bad resolution for this TV.

I can fix the resolution by creating an xorg.conf file -- that allows me to set a 1360x768 resolution which is great. But once I do that VLC can't/won't play a DVD.

getting the EDID packages was interesting. If i try to run get-edid | parse-edid, one of two things happens. It either runs correctly but reports a failure trying to call VBE and advises not to trust the rest of the output. It provides no helpful resolutions.

If I run it with the intel driver loaded, it hangs X altogether, forcing a restart. again, no useful output.

I'm willing to use the intel driver, but *how do I troubleshoot what's happening in VLC?* Why audio but no video? VLC thinks the disc is playing. Are there some flags/fields/modules that the intel driver or VLC needs that I need to provide?

---

### Post by BicyclerBoy on 2011-01-08
Classic...
Maybe with the  intel driver loaded VLC tries to do hardware video acceleration & fails.

With vesa Xorg free driver VLC does not crash but is very slow & jittery.

Seems like you need a different driver or some kernel mode-setting bits setup..
Sorry no experience to draw on I've never bothered with intel except on netbook.

As a work around..
Try changing the VLC video playback setting.
Click on "show settings All" button then video tab.
Deselect overlay video output
Try all other video rendering methods (Output modules) openGL or X11 video or XVideo extension.

---

### Post by jeffcox65 on 2011-01-08
Okay, this problem is now SOLVED.

Once I realized that the 1024x768 mode I was seeing was lowres graphics, I embraced the xorg.conf that allowed me to keep 1360x768. So the problem was within VLC.

vlc -vvvv showed me that it was generating X11 errors:

xbc_xv generic debug: cannot put image: X11 error 11

Ironically, switching the video output method to X11 in VLC preferences is what fixed vlc playback.

Thank you again for your insight and help.

---

