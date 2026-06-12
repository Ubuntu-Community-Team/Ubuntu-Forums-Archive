---
title: "problems with video"
date: 2009-07-22
forum: Multimedia Software
---

### Post by austar on 2009-07-22
hi guys im having problems with my video i cant view any online videos, when i go on you tube i get this message:Upgrade to Flash Player 10 for improved playback performance. [Upgrade Now]("http://www.adobe.com/go/getflashplayer/") or [get more info]("http://help.youtube.com/support/youtube/bin/answer.py?answer=95402").please help

---

### Post by Bigtime_Scrub on 2009-07-22
What version of Ubuntu are you using? Also do you use 32-bit or 64-bit?

---

### Post by Bigtime_Scrub on 2009-07-22
If you are using Any 32-bit Ubuntu version of 8.04, 9.10, or 9.04 then here is an easy tutorial for you. [http://www.howtoforge.com/installing-adobe-flash-10-on-ubuntu-8.04-i386](http://www.howtoforge.com/installing-adobe-flash-10-on-ubuntu-8.04-i386)

If you are  using 64-bit Ubuntu see this thread. [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by lovinglinux on 2009-07-23
See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

### Post by kc4mts on 2009-07-23
Hello There!
Try this to solve your issue...It worked for 32 bit Ubuntu 8.04
One other thing you can try is as follows: (follow these directions ONLY IF you are using Ubuntu AND Synaptic Package Manager) in Synaptic search for Adobe flash and right click and chose "mark for complete removal" Adobe-flashplugin and select apply. Only after this is completed, do NOT install from Synaptic, instead, go to [http://www.adobe.com/go/getflash](http://www.adobe.com/go/getflash) and select the correct package for you system ( they have YUM, tar.gz, rpm, and deb packages... for Ubuntu that is usually the .deb package) at the time of this writing it is version 10.0.22.87-1 and I would recommend installing instead of saving and then installing( it saves a lot of work). This should get your flash pages working. Almost as soon as you finish doing this, synaptic will alert you to an update (ver 10.0.22.87-2). This update from Ubuntu repositories seems to work fine.
Back ground: I have not had flash working for a long, long time and and completely removing it and re-installing from Adobes site (not the Ubuntu repository)
seems to have cured my problems. I can only assume that something was incorrect on the 8.04 Ubuntu Live CD or one of the updates shortly after I reinstalled Ubuntu on this machine. The original Flash version was 9.0.....something.

Disclaimer......this fix may work for other flavors of Linux but has not been tested on them... use at your own risk. Back up files if possible before trying this method as I REALLY do not like screwing up other peoples machines....remember re-image takes 20 minutes and one or two explitives....reinstall can last a lifetime.

---

### Post by kc4mts on 2009-07-23
Hello There!
Try this to solve your issue...It worked for 32 bit Ubuntu 8.04
One other thing you can try is as follows: (follow these directions ONLY IF you are using Ubuntu AND Synaptic Package Manager) in Synaptic search for Adobe flash and right click and chose "mark for complete removal" Adobe-flashplugin and select apply. Only after this is completed, do NOT install from Synaptic, instead, go to [http://www.adobe.com/go/getflash](http://www.adobe.com/go/getflash) and select the correct package for you system ( they have YUM, tar.gz, rpm, and deb packages... for Ubuntu that is usually the .deb package) at the time of this writing it is version 10.0.22.87-1 and I would recommend installing instead of saving and then installing( it saves a lot of work). This should get your flash pages working. Almost as soon as you finish doing this, synaptic will alert you to an update (ver 10.0.22.87-2). This update from Ubuntu repositories seems to work fine.
Back ground: I have not had flash working for a long, long time and and completely removing it and re-installing from Adobes site (not the Ubuntu repository)
seems to have cured my problems. I can only assume that something was incorrect on the 8.04 Ubuntu Live CD or one of the updates shortly after I reinstalled Ubuntu on this machine. The original Flash version was 9.0.....something.

Disclaimer......this fix may work for other flavors of Linux but has not been tested on them... use at your own risk. Back up files if possible before trying this method as I REALLY do not like screwing up other peoples machines....remember re-image takes 20 minutes and one or two explitives....reinstall can last a lifetime.

---

