---
title: "Two sound questions (karmic)"
date: 2010-01-03
forum: Multimedia Software
---

### Post by PHaLaNX on 2010-01-03
Hi,

I have two things I can't figure out in ubuntu's sound system.

First, how can I use multiple sound programs at once? If one program is using the sound device I get no sound from other programs.

Second, is there a way to record (or just capture) the sound output (other than connecting the output to the input with a cable)?

Thanks.

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by PHaLaNX on 2010-01-04
Any help?

I still have a hard time understanding how the capability of having multiple sound applications running at the same time doesn't come out of the box.

---

### Post by Ubuntaqua on 2010-01-04
> **PHaLaNX said:**
> Any help?

I still have a hard time understanding how the capability of having multiple sound applications running at the same time doesn't come out of the box.

It does come out of the box for everybody. Most of those who have problems have tampered with it badly enough that it break things. Not to say that you have, of course, but it's the most common case.

That beeing said. A few rather vague lines is clearly not enough for people to understand your issue. What programms you tried to use, what hardware configuration, ... Getting help, is about as difficult as asking for it correctly.

---

### Post by SuperSonic4 on 2010-01-04
Often it's a problem with the phonon backend. Which one do you have?

---

### Post by PHaLaNX on 2010-01-04
Maybe it doesn't like my hardware, I don't know for sure. But it never worked for me. For example, if I have virtualbox open I can't use audacious or amarok at the same time, or if I have audacity recording Firefox can't use the sound. 

This is what happens if some other program is using the sound device. It's not a particular application, it happens with all of them. 

```
$ sudo echo 1 > /dev/dsp
bash: /dev/dsp: Device or resource busy

```

@SuperSonic4
Sorry I don't know what is that you're talking about.

---

### Post by PHaLaNX on 2010-01-04
Any ideas?

---

### Post by PHaLaNX on 2010-01-05
Up, no one knows about this?

---

### Post by PHaLaNX on 2010-01-06
:o

---

### Post by Yellow Pasque on 2010-01-06
I'm sure there are easier GUI ways to do it, but you can capture output with gstreamer (of course, you have to install the appropriate gstreamer packages). Example:
```
gst-launch-0.10  alsasrc  !  audioconvert  !  vorbisenc  !  oggmux  !  filesink location=input.ogg
```

Also, maybe this will help with your dmix problem: [http://madberry.org/2008/08/sound-problem-fixed/](http://madberry.org/2008/08/sound-problem-fixed/)

---

### Post by PHaLaNX on 2010-01-06
If I understand correctly this command will record the output and save it in input.ogg right? But I also need to use the output in programs like baudline (a real time spectrum analyzer) so a recording file does me no good.

I will try to apply the ideas on that page about the other issue. I've never seen any dmix so far (only kmix if it's related) but I'll let you know if it works.

---

### Post by PHaLaNX on 2010-01-08
Apparently I  don't have alsa-oss installed, and this command says it'll remove kubuntu-desktop. It looked like something that will crash things if I run it. May there be another way of solving this?

```
$ sudo apt-get remove --purge alsa-oss alsa-base

Reading package lists... Done
Building dependency tree
Reading state information... Done
Package alsa-oss is not installed, so not removed
The following packages will be REMOVED:
  alsa-base* kubuntu-desktop*
0 upgraded, 0 newly installed, 2 to remove and 127 not upgraded.
After this operation, 532kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```

---

### Post by Yellow Pasque on 2010-01-08
Why are you running that command?

---

### Post by VertexPusher on 2010-01-08
> **PHaLaNX said:**
> First, how can I use multiple sound programs at once? If one program is using the sound device I get no sound from other programs.
ALSA provides predefined PCMs for both shared and exclusive sound card access:

[LIST]
[*]"default" works for multiple applications. Sample rate/format conversion is performed automatically.
[*]"plughw" works for one application at a time. Sample rate/format conversion is performed automatically.
[*]"hw" works for one application at a time. No automatic conversion is done.
[/LIST]

As the name implies, "default" is what applications should use by default unless you configure them to use something else. If an application manages to occupy the sound card exclusively, it may be for any of these three reasons:

[LIST]
[*]The application uses a PCM other than "default". Solution: Check the application preferences.
[*]The application does not use ALSA at all but OSS instead. Solution: Run the application with the "aoss" tool.
[*]The application uses "default", but "default" is not configured for shared access (i.e. it is mapped to plughw instead of dmix). Solution: Redefine "default" using a .asoundrc file in your user home directory.
[/LIST]
Here's an .asoundrc that should work for your card:
```
pcm.!default {
    type plug
    slave.pcm {
        type asym
        playback.pcm {
            type dmix
            ipc_key 10001
            slave {
                pcm {
                    type hw
                    card Intel
                }
                format S32_LE
                rate 48000
                channels 2
                period_size 1024
                buffer_size 8192
            }
        }
        capture.pcm {
            type hw
            card Intel
        }
    }
}
```

> Second, is there a way to record (or just capture) the sound output (other than connecting the output to the input with a cable)?
You can do that using ALSA's loopback driver (snd-aloop).

---

### Post by Yellow Pasque on 2010-01-08
There's always Pulseaudio if you can set it up right. Have fun with that though...

---

### Post by PHaLaNX on 2010-01-08
@Temüjin
Because it's what it says in the page you mentioned. 

@VertexPusher
Thanks for the long answer, now I tried it with a couple of applications all set to use alsa and there is no problem with playback and recording. So the first problem is solved. Seems like there was an issue with oss. 

And for the other part, I think I should do 

```
sudo modprobe snd-aloop
```

but I don't have it, it says:

```
$ sudo modprobe snd-aloop
FATAL: Module snd_aloop not found.
```

I searched a bit but there isn't much about it as far as I saw, I would appreciate it if you could elaborate a little about how to install and use it.

---

### Post by PHaLaNX on 2010-01-09
:popcorn:

---

### Post by VertexPusher on 2010-01-11
You need to have linux-backports-modules-alsa-karmic-generic installed for this.

---

### Post by PHaLaNX on 2010-01-11
Ok, I installed that but still it can't find snd-aloop. And also I got 3 new entries in my grub menu now. 2.6.31-17-generic, it's recovery and a new memtest entry. If I boot from the new one (2.6.31-17) kwin crashes as the desktop opens and I can't run it again (it crashes everytime I run it). 

Here is my install log, I saved it in case something goes wrong:

```
$ sudo apt-get install linux-backports-modules-alsa-karmic-generic
Reading package lists... Done                                                          
Building dependency tree                                                               
Reading state information... Done                                                      
The following extra packages will be installed:                                        
  linux-backports-modules-alsa-2.6.31-17-generic linux-image-2.6.31-17-generic                                                  
Suggested packages:                                                                                                             
  fdutils linux-doc-2.6.31 linux-source-2.6.31                                                                                  
The following NEW packages will be installed:                                                                                   
  linux-backports-modules-alsa-2.6.31-17-generic linux-backports-modules-alsa-karmic-generic linux-image-2.6.31-17-generic      
0 upgraded, 3 newly installed, 0 to remove and 150 not upgraded.                                                                
Need to get 30,6MB of archives.                                                                                                 
After this operation, 96,8MB of additional disk space will be used.                                                             
Do you want to continue [Y/n]? y                                                                                                
Get:1 http://gb.archive.ubuntu.com karmic-updates/main linux-image-2.6.31-17-generic 2.6.31-17.54 [28,8MB]
Get:2 http://gb.archive.ubuntu.com karmic-updates/main linux-backports-modules-alsa-2.6.31-17-generic 2.6.31-17.19 [1.756kB]
Get:3 http://gb.archive.ubuntu.com karmic-updates/universe linux-backports-modules-alsa-karmic-generic 2.6.31.17.30 [3.382B]
Fetched 30,6MB in 4min 51s (105kB/s)
Selecting previously deselected package linux-image-2.6.31-17-generic.
(Reading database ... 99350 files and directories currently installed.)
Unpacking linux-image-2.6.31-17-generic (from .../linux-image-2.6.31-17-generic_2.6.31-17.54_i386.deb) ...
Done.
Selecting previously deselected package linux-backports-modules-alsa-2.6.31-17-generic.
Unpacking linux-backports-modules-alsa-2.6.31-17-generic (from .../linux-backports-modules-alsa-2.6.31-17-generic_2.6.31-17.19_i386.deb) ...
Selecting previously deselected package linux-backports-modules-alsa-karmic-generic.
Unpacking linux-backports-modules-alsa-karmic-generic (from .../linux-backports-modules-alsa-karmic-generic_2.6.31.17.30_i386.deb) ...
Setting up linux-image-2.6.31-17-generic (2.6.31-17.54) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-17-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.31-17-generic
 *  fglrx (8.661)...                                                                                                            fglrx (8.661): Installing module.
  Kernel headers for 2.6.31-17-generic are not installed.  Cannot install this module.
  Try installing linux-headers-2.6.31-17-generic or equivalent.
                                                                                                                         [fail]
run-parts: executing /etc/kernel/postinst.d/nvidia-common

Setting up linux-backports-modules-alsa-2.6.31-17-generic (2.6.31-17.19) ...
update-initramfs: Generating /boot/initrd.img-2.6.31-17-generic

Setting up linux-backports-modules-alsa-karmic-generic (2.6.31.17.30) ...

```

---

### Post by Yellow Pasque on 2010-01-11
...> Try installing linux-headers-2.6.31-17-generic or equivalent.

---

### Post by PHaLaNX on 2010-01-11
I saw it but I thought I would ask before doing anything. Last time I had to reinstall everything after trying to fix sound. 

Anyway did it now and the newer entry booted fine. Modprobe also gives no error. I'll try to figure out the sound setup. Thanks for the help.

---

