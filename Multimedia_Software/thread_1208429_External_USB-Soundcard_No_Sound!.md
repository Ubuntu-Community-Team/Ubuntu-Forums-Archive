---
title: "External USB-Soundcard: No Sound!"
date: 2009-07-09
forum: Multimedia Software
---

### Post by Dysport on 2009-07-09
Hi everyone!
I'd be really really happy if someone could help me with my problem.
I'm not getting any sound through the external soundcard (internal speaker works fine).
Here are various ouputs from the terminal:
```
$ lsusb
…
Bus 004 Device 007: ID 0d8c:0102 C-Media Electronics, Inc. CM106 Like Sound Device
…

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB Sound Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_usb_audio

```

The Pulse Audio Applet shows an output when I play music in rhythmbox, but I don't hear a thing (see attached screenshot).

I'm using the computer as a media center in the living room, that's why the sound is really important for me to work!

---

### Post by d_liebscher on 2009-07-09
Hi,

did you selected the external sound card as standard output device?
I also use an external usb sound device and I had the same problem some time ago. 
First I looked for my card name:
```
asoundconf list
```then I selected the external card and after restarting the player everything worked fine:
```
asoundconf set-default-card *name*
```Alternatively you can use asoundconf-gtk package.

Daniel

---

### Post by Dysport on 2009-07-09
As you may see on the screenshot of asoundconf-gtk in my first post, I did set it as standard output and the computer seems to recognize the hardware. That's why I don't know where the problem is (might it be the chipset/vendor of my soundcard? 0d8c:0102)

But thanks for your help anyway!

---

### Post by d_liebscher on 2009-07-09
Sorry,
i was a bit cursorily.

 If the card is listed here: [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main) and there is no Note like [Unsupported],
it should be possible to get some sound out of it and the problem is not the chipset/vendor otherwise you'll hardly be able to get it working.

Daniel

---

### Post by Dysport on 2009-07-09
Thanks a lot for the link. Okay, according to [this page]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-C-Media") the chipset should be supported by ALSA - which is probably why im _seeing_ some output on the screen (but have yet to hear something)

---

### Post by d_liebscher on 2009-07-09
Hm,

there are a lot of possibilities for that...

I noticed right yet, that your are from Switzerland. Probably this page may help you:
[http://wiki.ubuntuusers.de/Soundprobleme](http://wiki.ubuntuusers.de/Soundprobleme)
particularly the part about symptoms

---

### Post by Dysport on 2009-07-10
According to the guide on ubuntuusers.de I should check my alsamixer, because it seems to play correctly:```
$ aplay /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono

```
But everything seems to be set correctly there (screenshot attached)
Any more ideas?

(I also attached the .inf from the windoze driver, might contain relevant information?)

---

### Post by d_liebscher on 2009-07-10
Hi,

Alsa Mixer configuration seems to be correct.
No Idea right now, sorry. I have to go for working now, but I will think about it.

---

### Post by Dysport on 2009-07-12
bump…

no one else got an idea?

---

### Post by d_liebscher on 2009-07-12
Hi,

it's me again ;)

i stumble up on an article about the relative new Soundserver Pulse Audio.
Maybe the problem is a conflict between ALSA and PulseeAudio?

I have a lot of work at moment and couldn't read the whole article but maybe you find an advice for a solution.

Link: [http://wiki.ubuntuusers.de/PulseAudio](http://wiki.ubuntuusers.de/PulseAudio)

Daniel

---

### Post by snapback77 on 2009-07-12
I have a HRT Music Streamer.  Works fine after applying the following link.[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

---

### Post by Dysport on 2009-07-13
Thank you both for your input. I tried setting it to PulseAudio - no change.
I will post a screenvid of everything I do with detailed descriptions, maybe you'll get a better idea of what could be wrong.

UPDATE: Here is the screen video that I put on youtube: [http://www.youtube.com/watch?v=5UNCRoHICIE]("http://www.youtube.com/watch?v=5UNCRoHICIE")
Did that show you anything?

While screen-capturing and labelling the video I noticed something - however might be useless but to be sure I'm gonna post it: It's a USB **_5.1_** soundcard but volume control only shows _"left channel" and "right channel"_. Could it be possible that something is misdetected and the wrong driver is loaded?

---

### Post by Dysport on 2009-07-22
another bump…

---

### Post by jeremyc on 2009-07-26
Another bump.  I have the same problem, same or similar 5.1 channel USB soundcard.

---

### Post by jeremyc on 2009-07-26
Turns out some registers on the device need to be set, so the card doesn't really adhere to USB sound standards.  There's a patch discussed [here]("http://article.gmane.org/gmane.linux.alsa.user/32832"), which was merged into the kernel [2.6.31-rc1]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc1/CHANGES").  I just installed 2.6.31-rc5, and it's working.

Alternatively, you can grab the patch, apply it to the source of whatever kernel you're running, and rebuild.  I'll end up doing that myself if .31 gives me any grief.

---

### Post by Dysport on 2009-07-26
I'm not really getting it how/where I'm supposed to apply the [patch]("http://article.gmane.org/gmane.linux.alsa.user/32832"). Could you give me a few more detailed steps?

---

### Post by jeremyc on 2009-07-26
I made a patch from [here]("http://www.spinics.net/lists/alsa-devel/msg24602.html"), but guaranteeing it will work for you (not knowing what version of the kernel source you're using) would be difficult.

But there's only 1 file involved, so, first follow directions for compiling a kernel from source:
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

I did the "Alternate Build Method: The Old-Fashioned Debian Way", in which case, just before you do the 
```
make-kpkg clean
```
edit the sound/usb/usbaudio.c file with the following.

Paste in
```

static int snd_usb_cm6206_boot_quirk(struct usb_device *dev)
{
    /*
     * C-Media CM6206 is based on CM106 with two additional
     * registers that are not documented in the data sheet.
     * Values here are chosen based on sniffing USB traffic
     * under Windows.
     */
    return snd_usb_cm106_write_int_reg(dev, 0, 0x200c) +
        snd_usb_cm106_write_int_reg(dev, 1, 0x3000) +
        snd_usb_cm106_write_int_reg(dev, 2, 0xf800) +
        snd_usb_cm106_write_int_reg(dev, 3, 0x143f) +
        snd_usb_cm106_write_int_reg(dev, 4, 0x0000) +
        snd_usb_cm106_write_int_reg(dev, 5, 0x3000);
}

```
at around line 3300 (just after snd_usb_cm106_boot_quirk method) and paste in 
```


        /* C-Media CM6206 / CM106-Like Sound Device */
        if (id == USB_ID(0x0d8c, 0x0102)) {
                if (snd_usb_cm6206_boot_quirk(dev) < 0)
                        goto __err_val;
        }

```
at around line 3600, just after the similar conditional for the Turtle Beach Audio...


Then compile and install the new kernel, and you should be good to go.

A lot of work to get a cheap little sound card working, but necessary if you don't want to wait for 9.10.

Good luck, and let us know if that works for you.

---

### Post by martinbaselier on 2009-07-26
there's an easier way.

download the kernel here:
[http://packages.ubuntu.com/karmic/linux-image-2.6.31-3-generic](http://packages.ubuntu.com/karmic/linux-image-2.6.31-3-generic)

and double click the file. 

It will open in gdebi, which will allow you to install it. It will add the kernel to your boot menu. So if it doesn't work, you can always choose your old kernel. 


Alternatively you could compile a single kernel module:

see my howto here:

[http://ubuntuforums.org/showthread.php?t=1012054](http://ubuntuforums.org/showthread.php?t=1012054)

This will however probably not work in this case, since there are some changes in api between those 2 kernels.

---

### Post by Dysport on 2009-07-26
> **jeremyc said:**
> I made a patch from [here]("http://www.spinics.net/lists/alsa-devel/msg24602.html"), but guaranteeing it will work for you (not knowing what version of the kernel source you're using) would be difficult.


Thanks for your useful replies! I'm running the latest Kernel: 2.6.28-13-generic
If your patch works with my kernel please post it - I would like to avoid kernel compilation as I never needed to do it until now and I think it has a vast number of possibilities how I could mess up my machine  :)

---

### Post by jeremyc on 2009-07-26
> **martinbaselier said:**
> there's an easier way.

download the kernel here:
[http://packages.ubuntu.com/karmic/linux-image-2.6.31-3-generic](http://packages.ubuntu.com/karmic/linux-image-2.6.31-3-generic)


Yeah, I initially had just installed .31, but I ran into a couple of problems with an unrelated module (that I need working).  Neither is really "supported" and it seemed a small tweak to Jaunty would be more supported than using Karmic before it's released..

> **martinbaselier said:**
> 
Alternatively you could compile a single kernel module:
...

This will however probably not work in this case, since there are some changes in api between those 2 kernels.


That's an interesting idea, shouldn't have any api change problem if I use only .28 kernel.  But the Makefiles involved in sound/usb/usbaudio don't follow the pattern in your example.  If you have time, it would be great if you could show me how I'd tweak the Makefiles to recompile only sound/usb.  With any luck, it could take less time than the full recompile...:)

> **Dysport said:**
> 
...
If your patch works with my kernel please post it 

I'll try to do that.  My kernel is compiling right now, will take a little while.  Do you know where/how I should post a bunch of .deb files?

---

### Post by Dysport on 2009-07-26
> I'll try to do that.  My kernel is compiling right now, will take a little while.  Do you know where/how I should post a bunch of .deb files?

You could tar them into one file and upload it on let's say rapidshare.com or filefactory.com - many others available. 
But maybe that's a little much to ask, I don't want you to waste too much time with this: You could just post the commands you used (e.g. as a bash script), that would help me to ensure I do every step correctly.

---

### Post by jeremyc on 2009-07-27
[Here]("http://www.filefactory.com/file/ahf976c/n/c-media-kernel-mod_tar_gz") you go (MD5: 5ad09db70259cbde9b7658c92eec7c1d)

```

tar xzvf c-media-kernel-mod.tar.gz
sudo dpkg -i linux-headers-2.6.28.9-c-media-quirk_2.6.28.9-c-media-quirk-10.00.Custom_i386.deb
sudo dpkg -i linux-image-2.6.28.9-c-media-quirk_2.6.28.9-c-media-quirk-10.00.Custom_i386.deb

```

Hope it works for you.  Let me know.

---

### Post by Dysport on 2009-07-27
Awesome! Works great!! Thank you so much, finally I can enjoy full dolby surround sound on my MythTV Box :D

At first I thought it didn't work - but as it turned out it doesn't like being attached to a usb hub. Anyway, everything works now :D:D:D

---

### Post by erikthedrink on 2009-09-08
Go to Applications, then Accessories, then Terminal.  

[FONT=Georgia][SIZE=4]asoundconf set-default-card 1[/SIZE][/FONT]

Then close and re-open your browser (Mozilla Firefox) or restart your system.
:P
Note, if you unplug your usb speakers, your laptop speakers will take over.  In order to re-establish contact with the usb speakers, you will need to (plug them back in) restart the system.

---

### Post by guiclaw on 2009-09-09
Thank you! It's working brilliantly for my USB soundcard ([http://www.ebuyer.com/product/106540](http://www.ebuyer.com/product/106540)). Working fine over optical - however I can't seem to get DD passthrough working with XBMC, but that's another story, main thing is the optical out is working!

I did have to install all the linux-image and linux-headers for 2.6.28-9, as I was originally running a newer version.

---

### Post by superkenny on 2012-08-02
Can anyone please upload that C-media file again. Link is broken.. 

Would be really helpfull. :)

---

### Post by wildmanne39 on 2012-08-02
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

