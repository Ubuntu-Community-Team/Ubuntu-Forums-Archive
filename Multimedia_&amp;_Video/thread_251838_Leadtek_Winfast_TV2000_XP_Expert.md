---
title: "Leadtek Winfast TV2000 XP Expert"
date: 2006-09-06
forum: Multimedia &amp; Video
---

### Post by tdshiv on 2006-09-06
I tried to install this card using:

sudo modprobe bttv card=34 tuner=2

However, i don't recieve any input on the channels. Can anyone help me get this working please?

---

### Post by nikoPSK on 2007-09-27
nope, sorry... I have the same card. Thanks for the #s! They worked!:KS

---

### Post by beefbowel on 2007-11-11
what worked?

---

### Post by nikoPSK on 2007-11-12
Ill tell you tomorrow.

---

### Post by beefbowel on 2007-11-12
another cryptic response.  lol wait no lol.  not lol.

---

### Post by nikoPSK on 2007-11-12
> **beefbowel said:**
> another cryptic response.  lol wait no lol.  not lol.

you have nsm yahoo or AIM? or just email me:

[email]modular_folder@hotmail.com[/email]

---

### Post by beefbowel on 2007-11-12
got it to work in tvtime.  mythtv still says "failed to open card".  

anyway high five!

i'm not sure what i did but to the best of my knowledge i did these things:

looked in   /lib/modules/2.6.22-14-generic/kernel/drivers/media/video/cx88
to see if the drivers were there.

then, i typed in root terminal         
modprobe cx88xx

i put  in /etc/modules
cx88xx

then i unscrewed the coxial cable from my leadtek winfast 2000xp expert's FM jack and screwed it into the TV jack.  what a difference that made!  i now have tv.  

but i still am mythtv-less.  any help would be appreciated.

---

### Post by nikoPSK on 2007-11-12
> **beefbowel said:**
> got it to work in tvtime.  mythtv still says "failed to open card".  

anyway high five!

i'm not sure what i did but to the best of my knowledge i did these things:

looked in   /lib/modules/2.6.22-14-generic/kernel/drivers/media/video/cx88
to see if the drivers were there.

then, i typed in root terminal         
modprobe cx88xx

i put  in /etc/modules
cx88xx

then i unscrewed the coxial cable from my leadtek winfast 2000xp expert's FM jack and screwed it into the TV jack.  what a difference that made!  i now have tv.  

but i still am mythtv-less.  any help would be appreciated.

well myth tv didnt like me neither. i'd stick with tvtime (and I am:lolflag:)

---

### Post by swampy5 on 2007-12-31
Hi all - guess what Ive also been wrestling with MythTV with the Leadtek TV2000 capture card - got to the same point - the card runs tvtime beautifully but will not scan channels in mythtv giving the same error message as reported here. Just wondering if anyone managed to resolve this -Ive tried all the suggested tips but none have worked - tvtime is doing the job fine but I would love to be able to give MythTV a good try out. I suppose the other option is to buy a new card that definitely is MythTV compatible - but the Leadtek is supposed to be! its listed as one of the compatible cards.
cheers swampy
:guitar:

---

### Post by Walc on 2008-01-05
hmm
Im also hving the same leadtek tv2000 xp card.
Ive chosen PAL+Europe, scanned for channels and ..........well:

1. video quality of some of em is ..medicore -->how can i fix it? <i know it can be much better ->thats they way it is on vista>

2.**[COLOR="Red"] it doesnt remember my settings, i.x lets say ive changed picture settings of channel nr.1, brighteness and so on, now ive choosed to save it for this channel, but once i reboot tvtime my new settings r gone.....[/COLOR]**

nvmd i got it all sorted:

1: adjusted screen settings <mainly contrast and brighteness>
2: it came out i wasnt authorised to make changes to tvtime

---

### Post by chris_keegan on 2008-01-08
I've been wrestling with this beast (trying to get the winfast tv2000 expert to work in mythtv) for the last few days now and my forehead is well blooded.

After trawling the web I found some cryptic instructions that claim to get cx2388x-based cards installed and working but being a *total* linux-neophyte, not knowing a modprobe from my elbow, the instructions are, well, arcane. I wondered if anyone here might be able to decrypt for me:

This is a link to the page: [http://www.linuxtv.org/v4lwiki/index.php/Cx88_devices_(cx2388x](http://www.linuxtv.org/v4lwiki/index.php/Cx88_devices_(cx2388x))

> Below you will see that all of the TV tuner related drivers are being compiled as modules. This allows MythTV to detect the TV tuner card and let you send parameters to the modules.

Kernel

When compiling the kernel, here are the options you need to tick:

Loadable module support:

[*] Enable loadable module support 
[*]   Module unloading
[*]     Forced module unloading
[*]   Automatic kernel module loading

Device Drivers->Multimedia devices:

[*] Video For Linux

Video Capture Adapters:

[*] Autoselect pertinent encoders/decoders and other helper chips 
<M> Conexant 2388x (bt878 successor) support
<M>   Conexant 2388x DMA audio support
<M>   DVB/ATSC Support for cx2388x based TV cards

If your card supports has blackbird mpeg encoder support, you'll need to compile the module for that. The DViCO FusionHDTV 5 Gold card does not have the blackbird mpeg encoder, so it's not necessary to tick this option for that card.

<M>   Blackbird MPEG encoder support (cx2388x + cx23416)  

Digital Video Broadcasting Devices:

[*] DVB for Linux 
<M> DVB Core Support




Any help appreciated, I'm beginning to grow faint!

Chris...

ps I can get tvvtime to do analog tv but not digital, anyone got any ideas why that may be?

---

### Post by hataricus on 2008-01-09
newbie alert:
hi guys, i am having a pb starting tvtime aswell:
```

 Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/hata/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.
```
---

what should i do !?
( i googled it and found nothing useful )

gutsy amd64 distro, video ati x1950pro configured with Envy ( it worked or so i think )
--
root@hata-desktop:/home/hata# fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.1.7170 Release

--> err help?

---

### Post by hataricus on 2008-01-10
anyone ?

---

### Post by nikoPSK on 2008-01-10
I can give you a link to my guide when I get home.
 
Best,
nikoPSK

---

### Post by hataricus on 2008-01-11
So, i ran the add/remove and installed XAWTV and Zapping.

When running XAWTV my screen goes blank, my system does not crash ( sound is still on ) but I can`t see anything ( duh ) and do not know how to get out of there ( alt+tab didn`t work :P )

When running Zapping: i see for a split second the "apps main menu" , actually just its borders and filled with white, after that its closing, but the sound is there and i cant tell if its a tv channel or a radio channel.
Looked in the System Monitor and did not find Zappin as beeing asleep or active !? weird ?!

EDIT: Tried with Gxine : this is what the terminal gives me:
```
root@hata-desktop:/home/hata# gxine --sync
gtkvideo: failed to connect to the dbus session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?
  sysname: Linux
  release: 2.6.22-14-generic
  machine: x86_64
X-Video Extension version 2.2
video_out_xv: Xv image format: 0x32315659 (YV12) planar
video_out_xv: this adaptor supports the yv12 format.
video_out_xv: Xv image format: 0x30323449 (I420) planar
received X error event: BadMatch (invalid parameter attributes)
The program 'gxine' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 762 error_code 8 request_code 140 minor_code 17)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


```

EDIT2: restarted the computer and ran zapping this time throught the terminal:
i can hear a buzz and some music in the backround and in the terminal:
```
 root@hata-desktop:/home/hata# zapping

(zapping:6340): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

** (zapping:6340): WARNING **: GConf key '/apps/zapping/plugins/deinterlace/method' is unset and has no default. Schemas incomplete or not installed?

Segmentation fault (core dumped)
 
```

Any help would be appreciated :)

---

### Post by nikoPSK on 2008-01-11
> **nikoPSK said:**
> I can give you a link to my guide when I get home.
 
Best,
nikoPSK

hmmm, my guide never got posted:confused: I thought I did....

---

### Post by hataricus on 2008-01-11
well could you repost it here please ? 

If it may help me, it is more than welcomed :)

---

### Post by esmerine on 2008-01-27
I have winfast tv2000xp deluxe. I did some essential things to make it work. I'm using tvtime. Managed to force it to show only one channel (Bloomberg). It's only ok when signal  detection is disabled. When it's enabled, i see "no signal".

And furthermore:

```

egle@pukuotukas:~$ tvtime
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/egle/.tvtime/tvtime.xml"
I/O error : Permission denied
I/O error : Permission denied
Cannot change owner of /home/egle/.tvtime/tvtime.xml: Permission denied.

```

What does it mean?

---

### Post by nikoPSK on 2008-01-27
> **hataricus said:**
> well could you repost it here please ? 

If it may help me, it is more than welcomed :)

well, here it is:
[http://ubuntuforums.org/showthread.php?t=647129](http://ubuntuforums.org/showthread.php?t=647129)

nikoPSK

---

### Post by Adamal on 2008-01-29
I found the information here to be helpful.

[http://www.linuxtv.org/v4lwiki/index.php/Leadtek_WinFast_2000](http://www.linuxtv.org/v4lwiki/index.php/Leadtek_WinFast_2000)

I got mine up and running with only adding the options in the modprobe.d configuration.

---

### Post by LeDechaine on 2008-02-01
Not working for me. Looks like it's not a "Card 34".

Mine's with a (supposedly) CX23880/1/2/3 chipset or something like that.

---

### Post by nikoPSK on 2008-02-01
> **LeDechaine said:**
> Not working for me. Looks like it's not a "Card 34".
 
Mine's with a (supposedly) CX23880/1/2/3 chipset or something like that.
 
find the right tuner and card numbers. :)

---

### Post by LeDechaine on 2008-02-03
Err, no way, like i said in another post, i'm not masochist enough to try all the modules, card, and tuner combinations only to get a TV Card working. Considering that "time is money" i'll actually **save** by buying a real, not crappy TV Tuner, or even a freaking TV.

---

### Post by LeDechaine on 2008-03-18
Well, finally the problem doesn't seem to be the card but that my audigy 2 drivers are crappy enough to not have the AUX Input enabled, and this is where the TV card must be plugged to output sound.

Waiting for a better Audigy 2 driver.

---

