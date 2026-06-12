---
title: "[web TV] gmlive-0.20.2"
date: 2008-06-18
forum: Multimedia Software
---

### Post by chunchengch on 2008-06-18
[COLOR="Red"]**Update 2008/11/12**[/COLOR]

[COLOR="Red"]Here are the newest deb packages for Ubuntu 8.10 (Intrepid) and Ubuntu 8.04 (Hardy), the greatest advantage is that you can use other players in this version, I also fix the dependency in these deb packages to largely decrease the quantity of needed dependencies, and the installation size will be much smaller.[/COLOR]

[COLOR="Green"](for Ubuntu 8.10)[/COLOR] [ATTACH]92299[/ATTACH]
[COLOR="Green"](for Ubuntu 8.04)[/COLOR] [ATTACH]92298[/ATTACH]

[ATTACH]92295[/ATTACH]  [ATTACH]92296[/ATTACH]

[ATTACH]92297[/ATTACH]

gmlive is a convenient frontend to watch mms, sopcast and nslive web streaming TV, I am not the creator of this great software, I just make the deb file for the sake of easy installation.

Although I include lots of Chinese mms channels in this deb, it is still a good option for people to watch sopcast streaming TV, because gmlive offers the **[COLOR="Red"]full-screen[/COLOR]** feature, so take it a try and enjoy it!


PS: 

1. here is the project home of gmlive [http://code.google.com/p/gmlive/](http://code.google.com/p/gmlive/)

2. [COLOR="Blue"]almost all the nslive channels are in Chinese, if you are willing to watch, you can open a terminal and run following commands, then you can find the channel list in gmlive.[/COLOR]

[COLOR="Red"]$ nslive -p 33
$ nsweb[/COLOR]

---

### Post by KuriKai on 2008-06-18
thanks

---

### Post by jjgomera on 2008-06-19
thank you very much

This program would perfect if it can connect too with tvants stream running in wine

---

### Post by Tridion2000 on 2008-06-20
How do you connect to Sopcast channels? I get no channels in the channel list but I also want to play sopcast URLs from the net. Any way of doing this?

---

### Post by chunchengch on 2008-06-20
> **Tridion2000 said:**
> How do you connect to Sopcast channels? I get no channels in the channel list ...

I got this problem sometimes, and really don't know what happened, I think that should be something about the sopcast server, because few minutes or few hours later, the channel list is just there.

---

### Post by chunchengch on 2008-06-20
> **jjgomera said:**
> ...This program would perfect if it can connect too with tvants stream running in wine

I don't know what tvants stream is, but you may leave a request at the project home of gmlive [http://code.google.com/p/gmlive/](http://code.google.com/p/gmlive/)

---

### Post by Tridion2000 on 2008-06-20
How do I manually enter a sopcast URL or copy and paste a sopcast URL from my web browser?

---

### Post by Maulkin on 2008-06-20
In all the mms channel, I dan't see even one user, is this supposed to be normal?

---

### Post by chunchengch on 2008-06-20
> **Tridion2000 said:**
> How do I manually enter a sopcast URL or copy and paste a sopcast URL from my web browser?

You can not do this in gmlive, maybe you should try gsopcast [http://ubuntuforums.org/showthread.php?t=728683&page=4](http://ubuntuforums.org/showthread.php?t=728683&page=4)

---

### Post by chunchengch on 2008-06-20
> **Maulkin said:**
> In all the mms channel, I dan't see even one user, is this supposed to be normal?

yes, it is normal, take a look at [http://en.wikipedia.org/wiki/Multimedia_Messaging_Service](http://en.wikipedia.org/wiki/Multimedia_Messaging_Service) for further understanding

---

### Post by Tridion2000 on 2008-06-21
> **chunchengch said:**
> You can not do this in gmlive, maybe you should try gsopcast [http://ubuntuforums.org/showthread.php?t=728683&page=4](http://ubuntuforums.org/showthread.php?t=728683&page=4)

Fair enough but gsopcast cannot do full screen. Are there any other Sopcast clients for Linux?

---

### Post by jjgomera on 2008-06-21
> **Tridion2000 said:**
> Fair enough but gsopcast cannot do full screen. Are there any other Sopcast clients for Linux?
yes, it can, if you use mplayer pick "f" to fullscreen, or if you preffer start in fullscreen add option &#8722;fs to mplayer in gsopcast options

---

### Post by Tridion2000 on 2008-06-21
> **jjgomera said:**
> yes, it can, if you use mplayer pick "f" to fullscreen, or if you preffer start in fullscreen add option &#8722;fs to mplayer in gsopcast options

Ok thanks very much, I'll give that a go.

---

### Post by sayantandas on 2008-07-02
hi, i have installed both sopcast and gmlive. they installed fine, with no errors. only thing is when i play any channel, i can only hear, cannot see any video. i cannot figure out why this is happening. pls help.

---

### Post by jualin on 2008-07-02
Thank you dude, I was looking for WebTV programs under Linux and this sounds like a good program. Greetings from Miami, USA.

---

### Post by chunchengch on 2008-07-02
> **sayantandas said:**
> hi, i have installed both sopcast and gmlive. they installed fine, with no errors. only thing is when i play any channel, i can only hear, cannot see any video. i cannot figure out why this is happening. pls help.

If this happens again, you can try to double click the channel again, to my experience, it will solve this problem.

---

### Post by sayantandas on 2008-07-02
hi, thanks for the reply, but i have been trying for the past two hours. it dint work out. is it possible to use other players like xine or vlc? if so, then how?

---

### Post by sayantandas on 2008-07-02
well, i fixed the problem. downloaded the latest mplayer from the website and compiled it from the source. now gmlive works just fine. :guitar:.  anyone, who has a problem with mplayer not running, just download the latest version from the site and compile it from source. it  will work. 
thanks to all

---

### Post by rykel on 2008-07-26
GSopcast, GMLive and SwarmPlayer are all very interesting developments!

I wonder if Singapore channels are available on Gmlive or Gsopcast?

Thanks.

---

### Post by chunchengch on 2008-11-12
Update 2008/11/12

Here are the newest deb packages for Ubuntu 8.10 (Intrepid) and Ubuntu 8.04 (Hardy), the greatest advantage is that you can use other players in this version, I also fix the dependency in these deb packages to largely decrease the quantity of needed dependencies, and the installation size will be much smaller.

---

### Post by 2xtreme4u on 2008-11-15
hi there,

first, thanks for the effort to create this program.

however, doesn't work for hardy 8.10.

the worst thin is, that it needs libstdc++5 while as default hardy 8.10 contains libstdc++6 - so I don't think it's a good idea to install libstdc++5 when version 6 is alreday installed.

some more broken dependencies I'm getting are:

 gmlive hängt ab von intltool; aber:
  Paket intltool ist nicht installiert.
 gmlive hängt ab von libstdc++5; aber:
  Paket libstdc++5 ist nicht installiert.
 gmlive hängt ab von libcairomm-1.0-1 (>= 1.6.4); aber:
  Paket libcairomm-1.0-1 ist nicht installiert.
 gmlive hängt ab von libglade2-0 (>= 1:2.6.1); aber:
  Paket libglade2-0 ist nicht installiert.
 gmlive hängt ab von libglademm-2.4-1c2a (>= 2.6.0); aber:
  Paket libglademm-2.4-1c2a ist nicht installiert.
 gmlive hängt ab von libglibmm-2.4-1c2a (>= 2.18.0); aber:
  Paket libglibmm-2.4-1c2a ist nicht installiert.
 gmlive hängt ab von libgtk2.0-0 (>= 2.14.1); aber:
  Version von libgtk2.0-0 auf dem System ist 2.12.9-3ubuntu5.
 gmlive hängt ab von libgtkmm-2.4-1c2a (>= 1:2.13.8); aber:
  Paket libgtkmm-2.4-1c2a ist nicht installiert.
 gmlive hängt ab von libpango1.0-0 (>= 1.21.6); aber:
  Version von libpango1.0-0 auf dem System ist 1.20.5-0ubuntu1.
 gmlive hängt ab von libpangomm-1.4-1 (>= 2.14.0); aber:
  Paket libpangomm-1.4-1 ist nicht installiert.
 gmlive hängt ab von libxcb-render-util0; aber:
  Paket libxcb-render-util0 ist nicht installiert.
 gmlive hängt ab von libxcb-render0; aber:
  Paket libxcb-render0 ist nicht installiert.
dpkg: Fehler beim Bearbeiten von gmlive (--install):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
Fehler traten auf beim Bearbeiten von:
 gmlive

(Sorry for the german messages, but I guess you can see the dependencies here).

Another question:

With your version, do I still need to download the binaries from sopcast.com? Seems the website is not available any more...

Cheers

Gregor

---

### Post by jjgomera on 2008-11-15
> **2xtreme4u said:**
> 
With your version, do I still need to download the binaries from sopcast.com? Seems the website is not available any more...

maybe a temporal problem, you can try with the deutchland mirror:

[http://sopcast.fuerzw.de/](http://sopcast.fuerzw.de/)

---

### Post by stefanr on 2008-12-21
> the worst thin is, that it needs libstdc++5 while as default hardy 8.10 contains libstdc++6 - so I don't think it's a good idea to install libstdc++5 when version 6 is alreday installed.

Fear not, libstdc++5 will peacefully coexist with libstdc++6.

Chunchengch, one question for you. I already installed gmlive from source, but I used your package to extract the nslive binary. Where is the home of nslive? I see a lot of references to newseetv.com, but that domain is 100% spam now.

Probably related to the demise of newseetv.com, the server which nsweb tries to download the channel list from (125.76.229.21) is not responding. Could someone maybe post their ~/.ulive/prog.list file with Chinese stations?

Cheers,
Stefan.

---

### Post by linuxvacuum on 2008-12-22
Thank you so much chunchengch for this program! I tried gsopcast but it didn't display any video. This gmlive works great.

---

### Post by Yeti can't ski on 2009-11-01
chunchengch, 

Thanks so much for the nice software. 

I am using it now with Ubuntu Karmic.

Just had to add libstdc++5 following what is established here: 

[http://ubuntuforums.org/showthread.php?t=1295318](http://ubuntuforums.org/showthread.php?t=1295318)

---

