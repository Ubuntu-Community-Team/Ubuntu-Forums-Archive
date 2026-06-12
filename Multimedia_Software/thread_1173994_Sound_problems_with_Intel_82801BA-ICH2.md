---
title: "Sound problems with Intel 82801BA-ICH2"
date: 2009-05-30
forum: Multimedia Software
---

### Post by jenkinbr on 2009-05-30
I'm having a bit of troble getting sound to work in ubuntu lately. I've had no problems like this in 7.04, 7.10, and 8.10; some minor issues in 8.04.

The problem started after a software update about a month ago, and acts like there is no soundcard there, even though [FONT="Courier New"]***lshw -c Multimedia***[/FONT] shows the device as being present and active.

I tried doing a few things found in the Sound problems guide (sticky) such as checking /etc/group and making sure I was listed in the audio group, checking alsamixer, and such.

Settings in gnome-sound-properties:
Sound Events && Music and Movies && Audio Conferencing:Sound Playback = Intel 82801BA-ICH2 with AD1885 Intel 82801BA (ALSA)
Audio Congerencing:sound Capture - Alsa
Default Mixer Tracks:Device - Intel 82801BA ICH2 (Alsa Mixer)


Some output:
**lshw -c Multimedia**
```
jenkinbr@jenkinbr:~$ lshw -c Multimedia
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Multimedia audio controller
       product: 82801BA/BAM AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0
jenkinbr@jenkinbr:~$ 

```

[B]aplay -l/B]
```
jenkinbr@jenkinbr:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801BAICH2 [Intel 82801BA-ICH2], device 0: Intel ICH [Intel 82801BA-ICH2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jenkinbr@jenkinbr:~$ 

```

**grep sound /etc/group**
```
jenkinbr@jenkinbr:~$ grep audio /etc/group
audio:x:29:pulse:jenkinbr:root
jenkinbr@jenkinbr:~$ 

```

Any Ideas?

---

### Post by psyke83 on 2009-06-03
Since "aplay -l" displays a sound card, that indicates that sound should function on your system. That leaves two possibilities - either a mixer is muted, or PulseAudio isn't functioning properly.

It's probably a PulseAudio issue. See my guide for more details.

---

### Post by jenkinbr on 2009-06-06
Currently working on [psyke83's guide]("http://ubuntuforums.org/showthread.php?t=789578").

---

### Post by ububaba on 2009-06-06
> **psyke83 said:**
> Since "aplay -l" displays a sound card, that indicates that sound should function on your system. That leaves two possibilities - either a mixer is muted, or PulseAudio isn't functioning properly.

It's probably a PulseAudio issue. See my guide for more details.

For some reason **Volume Control**:HDA Intel (Alsa mixer) is showing ([COLOR="Magenta"]Recording[/COLOR]) 
microphones Capture, Capture1 and Capture2  as muted even though the little 
speaker icon on the right-hand corner on the panel shows that it is not muted. 
The mike has worked perfectly earlier. Even when I remove the little red crosses
the mike doesn't get activated. Later the muting symbols hop back. Can somebody 
kindly point out where my flaw lies? 

Thanks.

---

### Post by jenkinbr on 2009-06-16
> **RgnKjnVA said:**
> Could you save others some time and list the brand/model of that audio dongle since you did some homework on it? Is it a full-sized dongle or a mini dongle of the stick-it-and-forget-it variety? Would be helpful if it was for laptop users.

PS good idea using signature as a running ad for your pressing Ubuntu issues. You never know when someone with a nugget of info will see it in an unrelated thread and lend a hand.

[http://ubuntuforums.org/showpost.php?p=7466476&postcount=8](http://ubuntuforums.org/showpost.php?p=7466476&postcount=8)

The Product I purchased is as follows:

Vender: Turtle Beach
Product: Audio Advantage Micro
Product #: TBS-1120

[Wal-Mart Product Page](http://www.walmart.com/catalog/product.do?product_id=9188815) --> Ordered Site-to-Store here.
[newegg.com Product Page](http://www.newegg.com/Product/Product.aspx?Item=N82E16829118107)

Works good in sterio mode, Haven't tried using it in 5.1 mode as I don't have the equiptment for that, although I've read a few reviews that say it has buffering issues. Also has a rather obnoxious blue LED, but that doesn't bother me much - my entire keyboard lights up, plus I hide the thing behind my monitor so I can't see it.

This device would be a great solution for a laptop with the exception that it may hog several usb ports due to it's size.  I plugged it in and it simply worked. I don't know if a live system will read it, but I think it should - I plugged it in before boot.

Some pics of the device (It comes with a usb cable, but not the one in the picture - that is from my old Logitec Wave keboard that went defunct.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=117862&stc=1&d=1245163611[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=117863&stc=1&d=1245163611[/IMG]

Hope this info is useful to someone in the same boat as me.

---

### Post by jenkinbr on 2009-06-29
I'm glad to say that this issue is now properly solved.

> **Buntuyang said:**
> Try this , it worked for me.
---------------------------------

Ubuntu sound no sound speakers

In 8.04, double click on the volume control, click on Edit/Preferences, then check External amplifier to be visible. The switches tab then appears. Uncheck External amplifier in that tab. Worked for me anyway."
This really worked for me, I just installed ubuntu today and it took me 6 hours to get sound work.

Found that in another thread, and it works beautifully (even in 9.04).  

I am [size=7]HAPPY!!!!!![/size]:guitar::guitar:

---

