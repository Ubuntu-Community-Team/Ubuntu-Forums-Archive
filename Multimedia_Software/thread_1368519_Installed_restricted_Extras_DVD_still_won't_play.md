---
title: "Installed restricted Extras DVD still won't play?"
date: 2009-12-30
forum: Multimedia Software
---

### Post by Stewie2kill on 2009-12-30
Hey guys,

     I've tried to play this DVD for an hour now and nothing is working. I've downloaded both the Kubuntu and Ubuntu restricted extras (I'm running Gnome and KDE4.2), libdvdcssv2, and the w32 codecs and nothing seems to work. I've tried playing it from all the Media players on both KDE4.2 and Gnome and nothing seems to be working. The dvd is fine since I just opened it an hour ago. I'm running Ubuntu 9.10 with KDE4.2 installed as an extra which I've heard can cause clashes before - but I've never had it clash with codecs and certainly not when using Gnome instead of KDE4.2.

     I've had luck asking for help on the forums before so I figured I'd check before I get too frustrated and nuke my install. Any ideas?

---

### Post by DasEi on 2009-12-30
you wrote all mediaplayers, does this include vlc, too ?

---

### Post by Stewie2kill on 2009-12-30
Yes. I've tried VLC, Dragonplayer, Mplayer, Totem, and the included Movie Player. 

It's extremely odd. I've never had this problem before.

---

### Post by DasEi on 2009-12-30
hmm , I often copy movies to hd, because of reading problems of the optical drives, permission is something that comes in mind, else
/var/log/syslog could contain info about problems

sudo dd if=/dev/cdrom of=cd.iso                 





sudo mkdir /media/dvd_image

sudo mount -o loop cd.iso /media/dvd_image
sudo chown UrUserNameHere /media/dvd_image

would solve read or permission isssues

---

### Post by Objekt on 2009-12-30
I too am having a problem with Kaffeine 1.0-pre2 in Ubuntu 9.10.  

Kaffeine will not play DVD .iso files.  When I try, I get two error dialogs with no message in them.  Just blank.  Not very helpful.

Kaffeine also will not play an actual DVD.  The example I tried is Saving Private Ryan.  Clicking "Play DVD" with the disc in my DVD drive generates an error dialog with the following message:

```
Cannot find demultiplexer plugin for MRL [dvd:/]
```

The disc works fine in Movie Player and VLC Media Player.  Those two will also play a DVD .iso file without any problems.

Like you, I installed Ubuntu Restricted Extras, as well as installing everything listed at the Medibuntu page ([http://www.medibuntu.org/]("http://www.medibuntu.org/")).  Those two things were enough to get Kaffeine playing DVD *.iso files under Kubuntu 9.04, so I'm not sure why it's not working under Ubuntu 9.10.

I would rather play DVDs through Kaffeine, because in Kubuntu 9.04, they give better image quality than VLC Media Player.  When watching DVDs through VLC, I notice a lot of aliasing & other artifacts.  It's probably something to do with the software scaling used so that the 480-line DVD output fills my 1600x1200 desktop.  Kaffeine's images are smoother for some reason.

---

### Post by Stewie2kill on 2009-12-30
Tried that but still no go. My XP partition reads it fine so I'm fairly certain that it isn't my Optical Drive (though it has been known to act up).

Thanks for your help. I think it's an issue with the codecs not installing correctly because I installed them from the command line which can often entail much more than a simple sudo apt-get install command. 

I have a DVD player that I'll use to watch this instead (DVD in question would be Paranormal Activity) and in the meantime I'll keep an eye on this thread and any others that look similar to see if this might be a bug.

---

### Post by PaulReaver on 2009-12-30
in a terminal

sudo apt-get install ubuntu-restricted-extras



then in a terminal

sudo /usr/share/doc/libdvdread4/install-css.sh





hope it helps

---

### Post by Stewie2kill on 2009-12-30
> **PaulReaver said:**
> in a terminal

sudo apt-get install ubuntu-restricted-extras



then in a terminal

sudo /usr/share/doc/libdvdread4/install-css.sh





hope it helps

Unfortunately no this has also not helped. As I mentioned I've installed the Restricted extras from the terminal for both Ubuntu and Kubuntu as well as the Medibuntu repositories. 

I was hoping that the shell script you provided might also be a help but this seems not to be the case. I'm beginning to wonder if this might be an actual bug caused by the installation of KDE4.2 ontop of Ubuntu 9.10.

---

### Post by VertexPusher on 2009-12-30
Install vobcopy ([http://packages.ubuntu.com/karmic/vobcopy](http://packages.ubuntu.com/karmic/vobcopy)), delete the folder ~/.dvdcss, then run this command from a terminal:
```
vobcopy --mirror
```
This will decrypt and copy the entire DVD to a folder in the current directory. Then you can point VLC at the VIDEO_TS subfolder and play the DVD content straight from harddisk. If that doesn't work, vobcopy should at least give you some info about what went wrong (read errors, decryption failure etc.).

---

### Post by Objekt on 2009-12-31
FWIW, I have K3B installed and am able to rip DVDs, so clearly the decryption stuff is on my system.

It's only with Kaffeine I am having a problem, in that it won't play DVD images (.iso files).  I know Kaffeine is capable of playing *.iso's, because I used to do it in Kubuntu 9.04.

I thought it might be some problem with using KDE apps like Kaffeine under a different desktop environment, but then I realized K3B is also a KDE app.

---

### Post by MooPi on 2010-01-01
I'm having trouble using Thoggen and ripping a Christmas gift. As Thoggen starts it maxes my ram then my swap and pretty much locks computer. I can play the DVD but can't back it up to my hard drive. dvd:rip fails as well. Currently using Brasero to create an .iso  and maybe I can mount and backup from that. Has anyone else ran into a similar problem?

---

### Post by rosswmcgee on 2010-01-01
This did it for me, dvds now play.

---

### Post by juancarlospaco on 2010-01-01
Perfect, because they are on Medibuntu :)

---

### Post by Ratcrack on 2010-01-04
Most of my commercial DvDs won't work either, but I can still play some DvDs. :confused:

---

### Post by jimmers on 2010-01-06
To get Kaffeine working in Karmic I had to install Xine

Worth a try, hope it works.

---

### Post by Objekt on 2010-01-06
I'll have to try that.  I would have thought any of the necessary bits would have been installed as dependencies when I put in Kaffeine, but maybe not.  Devs aren't perfect, and Kaffeine is technically still in pre-1.0 status.

---

