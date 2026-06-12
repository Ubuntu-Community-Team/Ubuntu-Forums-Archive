---
title: "DH57JG + HDMI Audio + Ubuntu 10.04"
date: 2010-03-29
forum: Multimedia Software
---

### Post by mbulow on 2010-03-29
Hi all
 
I have just build a HTPC with an Intel DH57JG Mini-ITX motherboard.
 
The motherboard supports HDMI Audio but I just can't make it work.
 
Anyone got a solution, or some hints, that might help me?
 
If you need some additional information, just ask, I'll do what it takes :)

---

### Post by proyectomx on 2010-04-22
Hi.

I saw your post searching for something related to HDMI in google.

This might not be a solution to your problem, but maybe it will help you as a workaround.

Try connecting hdmi cable BEFORE turning on your htpc.
That will give you video, but audio, you will have to select it in system/preference/sound and select the hdmi interface for sound.

Getting support for HDMI in ubuntu is very difficult to find, this I had to figure out myself after hours of trying to make it work... I haven't found a solution so far.

My computer is a notebook, but it has hdmi interface as well.

See you.
Kev

---

### Post by maitrechang on 2010-04-24
Hi,

same motherboard, same HTPC configuration, same issue, no solution so far :(

However I tried Fedora 13 beta LiveCD and HDMI audio works perfectly with it. I don't know if it comes from the kernel (2.6.33 vs 2.6.32), from alsa drivers, or from intel HD Graphics drivers (2.11 vs 2.9.1).

I'm seriously thinking about replacing my Ubuntu 10.04 with a Fedora 13 beta for this HTPC.

The only drawback is that Fedora 13 does not seem to package XBMC as Ubuntu does.

---

### Post by maitrechang on 2010-04-25
OK I just upgraded my kernel to 2.6.33 from the Ubuntu PPA and now the sound works fine.

> FILES="linux-headers-2.6.33-02063302-generic_2.6.33-02063302_amd64.deb \
linux-headers-2.6.33-02063302_2.6.33-02063302_all.deb \
linux-image-2.6.33-02063302-generic_2.6.33-02063302_amd64.deb"

for f in $FILES
do 
    wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.2-lucid/$f
done

sudo dpkg -i $FILES
sudo update-grub2


---

### Post by maitrechang on 2010-04-25
It looks like pulseaudio has conservative defaults. 
Stereo, 44.1 kHz... 
I'm a little bit amazed that in order to get 5.1 channels with proper sampling rate I have to hack some configuration files.

Anyway I found the solution here :

[forum.xbmc.org]("http://forum.xbmc.org/showthread.php?t=59877")

Personnally I chose to put stuf in /etc/pulse instead of ~/.pulse.
I also had to tweak the channel_map.

Let me know if you need more details.

---

### Post by jefubu on 2010-06-26
Thanks maitrechang. I was having the same problem with a Gigabyte H55N board. I upgraded the kernel and now everything works.

---

### Post by garry.donnelly on 2010-10-05
Hi [maitrechang]("http://ubuntuforums.org/member.php?u=610657")

Thanks for sharing your work around for acquiring sound over hdmi.  I'm not overly comfortable with upgrading the kernal above the supported 10.04 repos but if this is the only solution I'll have to work with it.  You also mentioned some pulse audio settings.  Can you be more specific about what you took from the referenced xbms thread?  It's over 40 pages now so but i'm working my way through them.  

Any other tips regarding teh DH57JG board?  I'm using it with an i5-661 and having a few issues so far.  Wasn't too impressed to find out Intel's using fakeraid and it's not well supported by 10.04 so I'm going with a software RAID install instead.  Going to run VMWare Server too. - yet to test it.  Hoping to use this as a portable media server / software dev box.

Thanks again
-Garry

---

### Post by proyectomx on 2010-10-22
can anyone confirm if hdmi video and audio are working propperly in ubuntu 10.10 ?

It would be great to have this issue solved.

---

### Post by plalloni on 2010-12-11
Not working here.

Ubuntu 10.10 with Gigabyte GA-H55N-USB3.

---

