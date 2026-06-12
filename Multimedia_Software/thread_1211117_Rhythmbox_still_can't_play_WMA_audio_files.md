---
title: "Rhythmbox still can't play WMA audio files"
date: 2009-07-12
forum: Multimedia Software
---

### Post by 7Lj3)(P38J on 2009-07-12
Folks,

I have Ubuntu 9.04 clean install.
I still can't play WMA audio files, and I already installed:

ubuntu-restricted-extras
Medibuntu codes
w32codecs
Gstreamer codes, also Rhythmbox is unable to find any plugins before or after the above installations.

.... and it still can't play my WMA sounds and musics.

Can you help me please how to troubleshoot this?  I want to be able to play proprietary formats.

However I can play WMV videos with Totem...

Thanks in advance for your help.

Carlos

---

### Post by d90 on 2009-07-12
same problem here!!!!

---

### Post by d90 on 2009-07-12
I found solution:

DISABLE CROSSFADING :) and wma plays smooth :)

---

### Post by vinutux on 2009-07-12
make sure installed these plugins

gstreamer-plugins-bad

gstreamer-plugins-bad-multiverse

gstreamer-plugins-ugly

gstreamer-plugins-ugly-multivers

and check th wma file with DRM

---

### Post by 7Lj3)(P38J on 2009-07-13
Hi vinutux

How do I know if I have those plugins and where can I download them ?

And what is DRM ?


thanks
Carlos

---

### Post by vinutux on 2009-07-14
> **crolidge said:**
> Hi vinutux

How do I know if I have those plugins and where can I download them ?

And what is DRM ?


thanks
Carlos

use **synapic** for installing and un installing programs


[B][COLOR="DarkGreen"]System->Administration->Synaptic pakage manager
[/COLOR][/B]

Then search there for gstreamer plugins and mark for installation 

Then applay

(you need enable restricted repos before this System->Administration->software sources and enable **restricted and multiverse**)


.

---

### Post by 7Lj3)(P38J on 2009-07-14
Hi Vinitux

I did what you suggested. I went to Synaptic Manager, made a search for "gstreamer plugins" and installed everything starting with "gstreamer" in the name.
Even after rebooting, sill Rhythmbox can't play any WMA and keeps looking for plugins during startup and never finds anything!

Any further tips to solve this mind-blogging issue?
thanks a lot

However, I installed Amarok and it plays well WMA files. Strange.... but I don't like it anyway since I don't like the KDE appearance of Amarok.

regards
Carlos

---

### Post by mc4man on 2009-07-14
If your wma's are lossless than rhythmbox can't play them. It should however play wma2 and wma3 (pro). (though on some installs it may not handle wma3

Amarok can play them all, as can mplayer, totem-xine and a properly built vlc.

Most xine based players should be good, most gstreamer based will do wma2 and maybe wma3, no wmal. (unless you purchase the fluendo codec pack for gstreamer

edit:
don't use gstreamer much so forgot to mention, make sure gstreamer-pitfdll is installed (that's the plugin that allows use of w32codecs

---

### Post by vinutux on 2009-07-15
> **crolidge said:**
> Hi Vinitux

I did what you suggested. I went to Synaptic Manager, made a search for "gstreamer plugins" and installed everything starting with "gstreamer" in the name.
Even after rebooting, sill Rhythmbox can't play any WMA and keeps looking for plugins during startup and never finds anything!

Any further tips to solve this mind-blogging issue?
thanks a lot

However, I installed Amarok and it plays well WMA files. Strange.... but I don't like it anyway since I don't like the KDE appearance of Amarok.

regards
Carlos


well....thats not worked 4 u okey

Try **[COLOR="DarkGreen"]Banshee[/COLOR]** it is better than Rhythmbox and amarock....Banshee is the best music palyer out for gnome......

```
sudo apt-get install banshee
```

.

---

### Post by 7Lj3)(P38J on 2009-07-16
Sorry, I installed Banshee and the same thing happens, it can't play WMA files. With VLC shows error message "can't read WMA1" similar to that.

OK, so now I tried everyhing, Medibuntu, w32codecs, and nothing works!

How can people expect the average user to use Ubuntu in this way. One can't expect to play non-proprietary formats all the time.... it's a pity such a beautiful operating system needs so many workaround, sometimes unfortunately useless.
Is there someone out there still willing to help me?

Amarok was the only program  who managed to play WMA, but I hate its interface.
thanks
Carlos

---

### Post by vinutux on 2009-07-17
> **crolidge said:**
> Sorry, I installed Banshee and the same thing happens, it can't play WMA files. With VLC shows error message "can't read WMA1" similar to that.

OK, so now I tried everyhing, Medibuntu, w32codecs, and nothing works!

How can people expect the average user to use Ubuntu in this way. One can't expect to play non-proprietary formats all the time.... it's a pity such a beautiful operating system needs so many workaround, sometimes unfortunately useless.
Is there someone out there still willing to help me?

Amarok was the only program  who managed to play WMA, but I hate its interface.
thanks
Carlos

Install program called **totem-xine** from synaptic (totem you have is gstreamer version)

and open it in terminal as **totem-xin** coz... it does not have a menu entry...

[check wich version of totem u are running Help>about]

.

.

---

### Post by Andras B. on 2009-07-17
I too had problems with the default totem-gstreamer, it doesn't play DVD-s properly (no menus, can't change sound track etc), virtually every video I tried to play with it had clicking sound, I have a standard FLAC file, that totem-gstreamer plays at half speed for no apparent reason.. With totem-xine, none of these issues exist. Why isn't xine the default backend for totem in Jaunty? It seems much better than gstreamer..

About the "Why can't linux play WMA" boo-hoo, I say, Why can't Windows Media Player play FLAC? It is the very same thing, though I don't see much complaints about that on windows support sites. Ubuntu has it's reasons why it doesn't support (on purpose!) proprietary formats, you can read all about it on the Ubuntu website. It's kind of an aggressive pro-free-formats propaganda, Ubuntu virtually forces you to use the "supported" formats, but doesn't windows do the exact same thing, promoting their formats by not supporting others? At least Ubuntu has a point, a philosophy to back it up, Windows has nothing, if not the will to suck you into a vendor lock vortex, so that you keep buying new windows versions, one after another..

---

### Post by vinutux on 2009-07-17
> **Andras B. said:**
> I too had problems with the default totem-gstreamer, it doesn't play DVD-s properly (no menus, can't change sound track etc), virtually every video I tried to play with it had clicking sound, I have a standard FLAC file, that totem-gstreamer plays at half speed for no apparent reason.. With totem-xine, none of these issues exist. Why isn't xine the default backend for totem in Jaunty? It seems much better than gstreamer..

About the "Why can't linux play WMA" boo-hoo, I say, Why can't Windows Media Player play FLAC? It is the very same thing, though I don't see much complaints about that on windows support sites. Ubuntu has it's reasons why it doesn't support (on purpose!) proprietary formats, you can read all about it on the Ubuntu website. It's kind of an aggressive pro-free-formats propaganda, Ubuntu virtually forces you to use the "supported" formats, but doesn't windows do the exact same thing, promoting their formats by not supporting others? At least Ubuntu has a point, a philosophy to back it up, Windows has nothing, if not the will to suck you into a vendor lock vortex, so that you keep buying new windows versions, one after another..

I think libxine1, which is used by xine-ui and totem-xine has a leagal trobule associated with....

---

### Post by Andras B. on 2009-07-18
> **vinutux said:**
> I think libxine1, which is used by xine-ui and totem-xine has a leagal trobule associated with....
oh I see.. too bad.. :(

---

### Post by vinutux on 2009-07-18
> **Andras B. said:**
> oh I see.. too bad.. :(

yeh..thatz the reason of fresh ubuntu need to install xtra codecs for playing mp3 and other mulimedia formats...

---

### Post by 7Lj3)(P38J on 2009-07-19
Ok folks, now it's official. I have quit trying to play WMA musics on Ubuntu. I even installed totem-xine, libxine1 and other affiliates, and nothing worked! Blast!

I installed Sound Converter and it failed to convert my WMAs into OGG or MP3, so what I did was installing a Windows-based free sound converter to do the change.

It's a shame really. How can people like Ubuntu with such need for so many tiring workarounds to make things behave properly??

Rating: 0

cheers anyway....

---

### Post by Andras B. on 2009-07-19
I'm starting to think the files you are trying to play are DRM protected. Maybe you (or the person) that ripped the CD had the "Protect media" option enabled in windows media player? Or are these songs from an online store? Either way, they are most likely DRM protected, and if so, not only Ubuntu, but none other operating system can play those, but the one that holds the license to the file.

If this is the case, the only option you have is to convert the files to another format on the OS which holds the license to play them.

---

### Post by vinutux on 2009-07-19
> **crolidge said:**
> Ok folks, now it's official. I have quit trying to play WMA musics on Ubuntu. I even installed totem-xine, libxine1 and other affiliates, and nothing worked! Blast!

I installed Sound Converter and it failed to convert my WMAs into OGG or MP3, so what I did was installing a Windows-based free sound converter to do the change.

It's a shame really. How can people like Ubuntu with such need for so many tiring workarounds to make things behave properly??

Rating: 0

cheers anyway....


i can play some of my wma....so its not probelem of ubuntu....its related to your file...

---

### Post by Soldeace on 2009-08-01
> **crolidge said:**
> Ok folks, now it's official. I have quit trying to play WMA musics on Ubuntu. I even installed totem-xine, libxine1 and other affiliates, and nothing worked! Blast!

I installed Sound Converter and it failed to convert my WMAs into OGG or MP3, so what I did was installing a Windows-based free sound converter to do the change.

It's a shame really. How can people like Ubuntu with such need for so many tiring workarounds to make things behave properly??

Rating: 0

cheers anyway....

You should not blame Ubuntu just because the proprietary file format you're trying to play is not legally allowed to be studied properly and carried out into other systems other than Windows.

---

### Post by Kangaroo_Style on 2010-04-08
Go to Synaptic Packet Manager, and then remove gnome-codec-install 

That's what worked for me, and now I don't get the searching for plug-ins error.

---

### Post by Chronon on 2010-04-08
> **Andras B. said:**
> I'm starting to think the files you are trying to play are DRM protected. Maybe you (or the person) that ripped the CD had the "Protect media" option enabled in windows media player? Or are these songs from an online store? Either way, they are most likely DRM protected, and if so, not only Ubuntu, but none other operating system can play those, but the one that holds the license to the file.

If this is the case, the only option you have is to convert the files to another format on the OS which holds the license to play them.

I suspect the same.

---

### Post by lidex on 2010-04-08
WMA = Windows Media Audio
Should be self-explanatory. They developed that format specifically to support DRM.

---

