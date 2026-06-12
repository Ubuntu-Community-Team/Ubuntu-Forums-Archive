---
title: "Personal summary of Installing RealPlayer 10 GOLD"
date: 2007-05-23
forum: Multimedia &amp; Video
---

### Post by chunchengch on 2007-05-23
Here is the complete procedure to install **RealPlayer 10 GOLD**, wish it will be helpful!



**1.Download Latest RealPlayer 10 GOLD to Desktop:**

[http://www.real.com/linux](http://www.real.com/linux)

**2.Change the mode of RealPlayer10GOLD.bin to be executable:**

[COLOR="Red"]$ cd /home/<YourLoginName>/Desktop
$ chmod +x RealPlayer10GOLD.bin[/COLOR]

**3.Install RealPlayer 10:**

[COLOR="Red"]$ sudo ./RealPlayer10GOLD.bin[/COLOR]

(please keep in mind the destination where you install realplayer, I prefer to install software under **/opt**, so in this case the destination is **/opt/realplay** which I will use for following descriptions)
.......
Copying RealPlayer files...configure system-wide symbolic links? [Y/n]: **[COLOR="Red"]Y[/COLOR]**
.......

**4. If you use [B]SCIM**, you have to modify realplay:[/B]

[COLOR="Red"]$ sudo gedit **/opt/RealPlayer**/realplay[/COLOR]

add this line to the beginning of the file opened and then save it.

[COLOR="Red"]export GTK_IM_MODULE=xim[/COLOR]

**5. Modify RealPlayer to support ALSA audio output:**

[COLOR="Red"]$ sudo apt-get install alsa-oss[/COLOR]

[COLOR="Red"]$ sudo gedit **/opt/realplayer**/realplay[/COLOR]

find text line  **$REALPLAYBIN "$@"**  and replace it with  **[COLOR="Red"]aoss $REALPLAYBIN "$@"[/COLOR]**

**6. Restart RealPlayer and enjoy it:**

Applications > Sound & Video

---

### Post by FDPOD on 2007-07-14
Hi chun,

thanks for the walk through.
Worked fine so far - RealPlayer installed and it can be started OK. 
However when opening a .RM file it produces the error message: 
[INDENT] [I]  The player does not have the capability to play back this content. 
   Following components are required: application/x-pn-imagemap[/I]
[/INDENT]
Totem plays the file fine just without the f****** audio. :-(

Any constructive ideas ?

P.S.: What BTW is SCIM or ALSA ..... ????

---

### Post by djchandler on 2007-07-15
> **FDPOD said:**
> Hi chun,

thanks for the walk through.
Worked fine so far - RealPlayer installed and it can be started OK. 
However when opening a .RM file it produces the error message: 
[INDENT] [I]  The player does not have the capability to play back this content. 
   Following components are required: application/x-pn-imagemap[/I]
[/INDENT]
Totem plays the file fine just without the f****** audio. :-(

Any constructive ideas ?

P.S.: What BTW is SCIM or ALSA ..... ????

First, chunchengch, thanks for the walkthrough from me as well. I've been trying to figure this out for a couple of days, but not a high priority.

FDPOD, this is SCIM. It's probably already installed.

> 
Smart Common Input Method (SCIM) is an input method (IM) platform.  Input methods are needed to enter complex characters in many non-latin languages. SCIM provides a common platform for various plugin modules and independent IM programs, as well as a set of modules and programs on its own.  It is highly modularized and exposes abstract interfaces, so that plugin modules with different functions can easily communicate with each other.  The currently supported module types are configuration, IM engine, front end, filter, and setup GUI. SCIM achieves the communication between IM engines and front ends through both shared library linking and server/client mode.  It supports XIM protocol, as well as GTK+ IM module and Qt IM module.

This package is the main binary package of SCIM.  It includes: the main program scim (GTK+ based) and other support programs; simple configuration module, X11 front end module, rawcode IM engine module, simplified/traditional Chinese conversion filter module, and their corresponding setup GUI modules; GTK+ panel and its setup GUI module; and a GTK+ based setup tool.

SCIM is a well accepted platform and features various input method engines for many languages.  In Debian you can find the following separately packaged IMs useful: scim-table-{additional,ja,po,zh}, scim-pinyin, scim-uim, scim-m17n, scim-chewing, scim-anthy, scim-canna, scim-prime, and scim-skk. GTK+ users would also find package scim-gtk2-immodule useful for GTK+ IM module support.

For development on SCIM platform, please see the description of scim-dev package.

Homepage: [http://www.scim-im.org/](http://www.scim-im.org/)


This is alsa-oss

> 
ALSA wrapper for OSS applications. This package contains a program loader, aoss, which wraps applications written for OSS in a compatibility library, thus allowing them to work with ALSA.

There are two ways of getting an application to work with ALSA if the application was written for OSS. The first way is to load the special ALSA drivers that emulate the OSS kernel interface; these allow the application to open /dev/dsp0 and other OSS device files. The second way is to wrap the application in the libaoss library provided in this package; the wrapper causes the application to access native ALSA device files such as /dev/snd/pcmC0D0c instead of OSS device files.

Use of the alsa-oss library is recommended over the use of OSS-emulation drivers if you want to use ALSA's PCM plugin layer.

ALSA is the Advanced Linux Sound Architecture:
    [http://alsa.sourceforge.net](http://alsa.sourceforge.net)
OSS is the free version of the Open Sound System.


SCIM is commonly installed by default. The alsa-oss wrapper must be installed most likely. You can use Synaptic if you don't want to use apt-get.

I found both these definitions in the Synaptic repository database.

Thanks again, chunchengch.
:guitar:

DJ

---

### Post by FDPOD on 2007-07-16
Well, why a version like the above ever can become released on the Real Website beats me .... :mad:

To solve the error message problem with the:
[INDENT]***[COLOR="Magenta"]Following components are required: application/x-pn-imagemap[/COLOR]***[/INDENT]

Download a new version from Helix:
[http://forms.helixcommunity.org/helix/builds/?category=realplay-current]("http://forms.helixcommunity.org/helix/builds/?category=realplay-current")

For me the version : *realplay-10.1.0.3297-linux-2.2-libc6-gcc32-i586.bin* 
worked for Ubuntu Feisty 7.04 and fixed the problem 

(The installation however was a little rocky since there are error messages of which I have no idea if they are relevant or not ....)

Follow the instruction from *chunchengch* with the newly downloaded file.

---

### Post by raym0nd on 2008-01-06
> **chunchengch said:**
> Here is the complete procedure to install **RealPlayer 10 GOLD**, wish it will be helpful!



**1.Download Latest RealPlayer 10 GOLD to Desktop:**

[http://www.real.com/linux](http://www.real.com/linux)

**2.Change the mode of RealPlayer10GOLD.bin to be executable:**

[COLOR="Red"]$ cd /home/<YourLoginName>/Desktop
$ chmod +x RealPlayer10GOLD.bin[/COLOR]

**3.Install RealPlayer 10:**

[COLOR="Red"]$ sudo ./RealPlayer10GOLD.bin[/COLOR]

(please keep in mind the destination where you install realplayer, I prefer to install software under **/opt**, so in this case the destination is **/opt/realplay** which I will use for following descriptions)
.......
Copying RealPlayer files...configure system-wide symbolic links? [Y/n]: **[COLOR="Red"]Y[/COLOR]**
.......


**5. Modify RealPlayer to support ALSA audio output:**

[COLOR="Red"]$ sudo apt-get install alsa-oss[/COLOR]

[COLOR="Red"]$ sudo gedit **/opt/realplayer**/realplay[/COLOR]

find text line  **$REALPLAYBIN "$@"**  and replace it with  **[COLOR="Red"]aoss $REALPLAYBIN "$@"[/COLOR]**

**6. Restart RealPlayer and enjoy it:**

Applications > Sound & Video

realplayer - NO SOUND - MULTIPLE SOUND CARDS -SOLVED :guitar:
Thanks for posting your procedure chunchengch.
Making realplayer to use alsa-oss solved my problem of not having sound with realplayer after installing a second sound card in  Kubuntu 7.10 (Gutsy).

---

### Post by wake69 on 2008-03-01
Newbe ,  Just instaled ubuntu 7.10 and followed the instructions above.   when I did < sudo ./ RealPlayer10GOLD.bin >  it asked me to enter my password which i did and it geve me this error. 

./RealPlayer10GOLD.bn: error while loading shared libraries: libstdc++.so5: cannot open shared object file: N such file or directory

please help.

---

### Post by raysaunders on 2008-03-03
I have the same problem and have been unable to find a way to address it. All help appreciated.

---

### Post by raysaunders on 2008-03-03
Finally found a method that works for me:

Downloaded this .deb file:

[http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.9-0.1_i386.deb](http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.9-0.1_i386.deb)

Firefox offered to open the file with the default gdebi-gtk 0.3.2ubuntu1 included in Ubuntu 7.10

The only issue I had was removing all traces of my various previous attempts before the installation would proceed:

sudo dpkg -r realplayer

I then used Synaptic Package Manager to completely remove the Helix installation (including all configuration files).

Credit to [https://help.ubuntu.com/community/RealPlayerInstallationMethods](https://help.ubuntu.com/community/RealPlayerInstallationMethods) (n.b. This wiki page URL is case sensitive!)

Shame there had to be so many "blind alleys" to be followed before finding that page,...

---

