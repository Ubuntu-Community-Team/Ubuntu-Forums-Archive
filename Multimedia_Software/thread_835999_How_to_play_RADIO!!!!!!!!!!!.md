---
title: "How to play RADIO!!!!!!!!!!!"
date: 2008-06-21
forum: Multimedia Software
---

### Post by smartygoldenfish on 2008-06-21
i have ubuntu 8.04 not kubuntu 7.10
i just stumbled on Radio feature of rythmbox. 
it played pre-listed stations flawlessly. I thought to add some hindi radio station links for new new radio stations.
i browsed some pages and then got some links on which if some one clicks..radio starts.
i posted it on Rythmbox. Alas! it told i needed Gstreamer plugins (bad set). i installed it.
but! when i now click on new radio station, it says it needs a HTTP encoder.

So i browsed ubuntu forums, and installed STREAMTUNER. they said it would play any station easily
i installed it
then if i click on ANY prelisted station there it says:
FAILED TO EXECUTE CHILD PROCESS
XMMS (NO SUCH FILES OR DIRECTORY)

so i went to synaptic and installed XMMS.
But there was no change i still got that message.
So i thought may be i am wrong.
I opened ubuntu FAQ
and saw how to install XMMS.
i downloaded the source from xmms site (oh! what a site)
and then i *tried * to install it EXACTLY as given in Ubuntu FAQ
and i got a holy error
[B](why cant streamtuner itself install xmms, if its useless without it! thats the problem with ubuntu. ubuntu appears so easy at start and becomes a ghost when u have to do a right angled task. 
Why dont they distribute  XMMS.deb? Why not create a Setup.exe counterpart in Ubuntu? Are u listening developers!
Seriously, Windows is 1000 times better than Ubuntu in this aspect because you can install anything so easily! No dependencies, no synaptic! get setup,install it! In ubuntu this is REALLY HECTIC.
Cant the developers develop, a Source to DEB converter! )[/B]

```
prateek@prateek-desktop:~/xmms-1.2.11$ ./configure --prefix=/usr
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
```
now?

PLEASE HELP

[B]aim: should be able to play and record all (most) types of radio and add my own streams too. using streamtuner is preferred but not necessary
[/B]

Not the aim: 
Dont tell me to google for this and that. 


Thank You

---

### Post by kyphi on 2008-06-21
Go into Rhythmbox, then to Radio, click on New Internet Radio Station and type in the URL of the station that you want to listen to.

Example: [http://radio.internode.on.net:8132/](http://radio.internode.on.net:8132/) or mms://baroque.1.fm/otto128k%3FMSWMExt%3D.asf.

---

### Post by smartygoldenfish on 2008-06-21
> **kyphi said:**
> Go into Rhythmbox, then to Radio, click on New Internet Radio Station and type in the URL of the station that you want to listen to.

Example: [http://radio.internode.on.net:8132/](http://radio.internode.on.net:8132/) or mms://baroque.1.fm/otto128k%3FMSWMExt%3D.asf.

sorry dear, but from where can i get links for hindi radio stations??
or the thosuands listed in streamtuner?

---

### Post by gandaran on 2008-06-21
> **smartygoldenfish said:**
> sorry dear, but from where can i get links for hindi radio stations??
or the thosuands listed in streamtuner?

you'll have to dig it out of the website! there are many ways you can do that, one easy way is to use the media player connectivity addon for firefox, and I believe mplayer plugin can do it too.


you can use any player with streamtuner, no need to install xmms (xmms in synaptic is xmms2, thats why it doesn't work if you don't set it up) , just change the player in preferences.

---

### Post by smartygoldenfish on 2008-06-22
> **gandaran said:**
> you'll have to dig it out of the website! there are many ways you can do that, one easy way is to use the media player connectivity addon for firefox, and I believe mplayer plugin can do it too.


you can use any player with streamtuner, no need to install xmms (xmms in synaptic is xmms2, thats why it doesn't work if you don't set it up) , just change the player in preferences.

thankx!
i set vlc as default player.
but i am able to play only m3u streams
how to get http streams playing (those who dont end in m3 u but in asp or htm)
also how to record! vlc gives a error.
any recording player known to u?

---

