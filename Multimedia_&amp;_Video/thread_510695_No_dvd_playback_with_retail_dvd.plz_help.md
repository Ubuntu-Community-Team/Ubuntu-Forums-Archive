---
title: "No dvd playback with retail dvd.plz help"
date: 2007-07-26
forum: Multimedia &amp; Video
---

### Post by mrdouble on 2007-07-26
First let me say I'm very green to Linux but I am starting to find my way around and this is my first real issue.
 I have been through many dvdcss, dvdread and other codex installation  walk throughs all yielding  that I have files,repository, dependences needed for dvd playback for retail (unripped) dvds. 

I have tried many dvds and have installed and tried many players (xine, kaffine,totem, Mplayer). they generaly drop out with some specific warning such as "no  stream found" or "are you sure you have libdvdcss installed?"

I am lost:confused:. Did I put to many players in system or modify source.list in a wrong manner?

the thing I don't get is that I can rip retail dvd with acidrip and play ripped dvds perfectly so I'm pretty sure its not a issue with the drive itself.

I have spent way to much time trying to figure this out myself so figured I would pass the baton onto someone a little smarter:guitar:

Thanks in advance
Micheal

---

### Post by mrdouble on 2007-07-26
Also, It has crossed my mind that maybe I should have invoked the codex by use of an option                      (totem -libdvdcss)? but I didnt see any options available for it.

---

### Post by RomeReactor on 2007-07-26
Hi. There's no need to invoke libdvdcss as an option for Totem (or any other player); open a terminal (Applications->Accessories->Terminal) and please post the output of this command:
```
cat /etc/apt/sources.list
```

---

### Post by mrdouble on 2007-07-26
Im sorry if this is not what you were looking for

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb http://us.archive.ubuntu.com/ubuntu/ feisty restricted main
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://ubuntu.beryl-project.org feisty main
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://ubuntu.beryl-project.org feisty main

deb http://www.getautomatix.com/apt feisty main

#AUTOMATIX REPOS START

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
deb http://packages.medibuntu.org/ feisty free non-free
deb http://packages.medibuntu.org/ feisty free non-free

deb http://packages.medibuntu.org/ feisty free non-free

```

---

### Post by RomeReactor on 2007-07-26
Yes, this is the sources list. Now we'll proceed to install the necessary packages. To avoid typos, please copy and paste the commands as follow--it may seem a bit complicated at first, so if you have trouble with any command, just post back. You'll be playing DVDs in no time ;)

You'll need to add the Medibuntu repositories: to do so, run this from the terminal:
```
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```
This command will add the repositories to your **sources.list**, your list of repositories; then enter this:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
which will fetch and add a key to authenticate the repositories you just added, and will update the repository information on your package managers. Now run this command from the terminal:
```
sudo apt-get install libdvdread3 libdvdcss2 libxine1-ffmpeg totem-xine
```
to install the necessary packages. Besides installing the necessary libraries, it will change **totem-gstreamer** for **totem-xine** which will be able to play the menus and use subtitles. After all the packages finish installing, you should be able to play encrypted DVDs.

---

### Post by mrdouble on 2007-07-26
I previously did all steps so it didn't surprise me that all files were already the newest therefore not installed:)

what now? lol

heres the terminal output 

```
 sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
Password:
--23:00:22--  http://www.medibuntu.org/sources.list.d/feisty.list
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving www.medibuntu.org... 81.169.138.125
Connecting to www.medibuntu.org|81.169.138.125|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 233 [text/plain]

100%[====================================>] 233           --.--K/s             

23:00:22 (13.48 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [233/233]

micheal@micheal-laptop:~$ sudo apt-get install libdvdread3 libdvdcss2 libxine1-ffmpeg totem-xine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread3 is already the newest version.
libdvdcss2 is already the newest version.
libxine1-ffmpeg is already the newest version.
libxine1-ffmpeg set to manual installed.
totem-xine is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
micheal@micheal-laptop:~$ 


```

---

### Post by benx009 on 2007-07-26
have you installed libdvdnav and libdvdplay?

---

### Post by benx009 on 2007-07-26
that's *libdvdplay0* and *libdvdread3* in synaptic:)

---

### Post by mrdouble on 2007-07-26
```
micheal@micheal-laptop:~$ sudo apt-get install libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdcss2 is already the newest version.
libdvdnav4 is already the newest version.
libdvdplay0 is already the newest version.
libdvdread3 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

this is from terminal.. does it matter which packager I use? I have used them all at one point to resolve issue

---

### Post by benx009 on 2007-07-26
no, the package manager you use does not matter:)

i would think this would be a drive problem, but a dvd successfully mounts on your system, right?

---

### Post by benx009 on 2007-07-26
another question: did you install the codecs before or after installing your dvd players?  if before, you would want to uninstall all your dvd players and try reinstalling them again so they can properly detect where the codecs are located.  i recommend paying special attention to mplayer because it is the only dvd player that works right for me, thus making it my only preference:)

---

### Post by RomeReactor on 2007-07-26
If Totem still complains about encrypted DVDs, run this:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```
In Feisty you shouldn't need to do this, but it may help.

---

### Post by mrdouble on 2007-07-26
yes..well, I think it does, I have full access to it without issue  ( it reads and writes):)

---

### Post by mrdouble on 2007-07-26
> **RomeReactor said:**
> If Totem still complains about encrypted DVDs, run this:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```
In Feisty you shouldn't need to do this, but it may help.

ok well, i did that and it downgraded something, still did not fix issue.

however. I think most of the players were already on sys when I downloaded libdvdcss stuff. however, Kaffine did recognize that it was installed during its setup screen

---

### Post by RomeReactor on 2007-07-26
> **mrdouble said:**
> ok well, i did that and it downgraded something, still did not fix issue.

Yes it downgraded libdvdcss. If you want to use the newer version, update the repository information:
```
sudo apt-get update
```
The Update Manager should pop up telling you of the update.

Have you tried other DVDs? If so, do you have this problem with all of them?

---

### Post by mrdouble on 2007-07-27
yea.. I have done update many times.. I have tried many cds even a couple brandnew ones always the same thing. but ripped cds work great

---

### Post by RomeReactor on 2007-07-27
Can you post a screenshot of the error message?

---

### Post by mrdouble on 2007-07-27
for which playeer? Mplayer?
 and.. um..can I ask how to capture? PRNTSC?

---

### Post by mrdouble on 2007-07-27
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=39126&stc=1&d=1185510170[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=39127&stc=1&d=1185510170[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=39128&stc=1&d=1185510170[/IMG]

---

### Post by mrdouble on 2007-07-27
OK.  seems something I did got Mplayer working to some extent.. it looks like I need to set DMA on it though.. cant seem to figure that out yet:(

---

### Post by RomeReactor on 2007-07-27
The error in Mplayer can be solved by opening it, then go to "Preferences->Video" tab, and selecting **xv   X11/Xv** as the driver. Did you install **totem-xine**. As for Totem and Xine, the only packages that may be missing are:
```
sudo apt-get install libxine-extracodecs w32codecs
```

This is odd. Totem *should* be playing the DVDs by now...

To enable DMA:
```
sudo hdparm -d1 -k1 /dev/dvd
```
assuming **/dev/dvd** is the correct designation of your DVD reader.

---

### Post by mrdouble on 2007-07-27
```
/dev/dvd:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 setting keep_settings to 1 (on)
 HDIO_SET_KEEPSETTINGS failed: Inappropriate ioctl for device
micheal@micheal-laptop:~$ 


```

rats.. I guess that means it was already on..hmm..I know I ran a diagnostic software that said it was not dma enabled.

Thank you for that last code though. I tryed many variation I seen around but all of them were for hda and hdc but they were for dvd which really dosnt make a whole hell of lota sence but anyways termial always said /dev/hdc not found

---

### Post by RomeReactor on 2007-07-27
Go into **/dev** and see if you can find the correct designation. You can also try something: let's eject the drive using **hdc** and see if it *is* the correct designation:
```
eject /dev/hdc
```
if it doesn't eject (or if you have more than one CD/DVD device, and ejects the wrong one) just close it--either by using its "Eject" button, or the following command:
```
eject -t /dev/hdc
```
By the way, this is useful if you have a DVD reader whose eject button doesn't work, like mine.

In any case, if it wasn't **hdc**, try **hdd**.

---

### Post by SteveTraylen on 2007-07-29
Hi, I look to have the same problem as this , libdvdcss installed but totem-xine, mplayer, vlc
all refuse to play an encrypted DVD.

Are you by any chance using a 64bit operating system as well.

---

### Post by nzadLithium on 2007-07-29
I have it working fine with totem movie player and gxine.
Also works in vlc using dvd if i use dvd(menus) it crashes though. Atm i use totem movieplayer because its defaults.

These are the packages containing dvd i have installed that may be useful:

gstreamer0.8-a52dec
gstreamer0.8-dv
gstreamer0.8-dvd
gstreamer0.8-mpeg2dec
liba52-0.7.4
libdvdcss2
libdvdnav4
libdvdread3
libvlc0
libxine1
libxine-extracodecs

check if all of those are installed.

If that doesnt work try using ogle. That is supposed to work with only libdvdread and libdvdcss installed.

hope this helps

Oh and im running 64bit too.

---

### Post by kavani on 2007-07-29
Thanks to everyone.  I hadn't given much thought to dvd playback.  I'm usually watching streaming media.  I appreciate the help.  This works for 32-bit Ubuntu Studio 7.04 too.  Though, I had to go through all the commands and eject the dvd once.  :)

---

### Post by RomeReactor on 2007-07-29
> **SteveTraylen said:**
> Hi, I look to have the same problem as this , libdvdcss installed but totem-xine, mplayer, vlc
all refuse to play an encrypted DVD.

Are you by any chance using a 64-bit operating system as well.

Hi. If you have the required packages installed, you shouldn't have problems watching DVDs, regardless of the architecture. It's been a while since I used Ubuntu 64-bit, but I seem to remember DVDs worked fine. Try posting in the [64-bit users]("http://ubuntuforums.org/forumdisplay.php?f=134") section also; maybe someone there can give you a more appropriate answer.

If you **do** have the necessary packages, you **should** be able to play DVDs though.

---

### Post by MikeyJ on 2007-07-29
Thanks benx009. I work great and I can play DVDs now. I am trying to build a media center but am new to Linux. I tip my hat to helpers like you for us newbies.

---

### Post by mrdouble on 2007-07-31
Thanks nzadLithium and everyone else.. i was missing every single Gstreamer file in your list.. I had a bunch of Gstreamer files but not them.. Thank you =)

Its working finally.. can someone make files STICKY =)

---

### Post by leona on 2007-08-30
|Hi there,
I am having a problem playing dvds no a new setup, Fiesty 7.04 on 32bit box.

Source list
```

# See http://help.ubuntu.com/community/Upgra deNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

```
medibuntu.list
```

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://packages.medibuntu.org/ feisty free non-free
#deb-src http://packages.medibuntu.org/ feisty free non-free

```

Followed all instructions on Wiki, and this thread, but nothing will play dvd's, I get an error in mplayer of "failed to open dvd://1."

I have a feeling this is some sort of mounting issue though, when I check the media directory I see "cdrom  cdrom0  floppy  floppy0" why don't I see a DVD listed? (or am I being a bit silly?).

Though when I insert a disc it shows up as an empty volume, but the disc icon appers and I can eject it, but that's it.

Its a working player, cos its the one I used to install Ubuntu :)

Where do I start in tracing this problem,

---

### Post by RomeReactor on 2007-08-31
> **leona said:**
> Where do I start in tracing this problem,

Hi. To start with, the Medibuntu sources must be included in the sources.list file, not as a separate file. I couldn't see an entry for Medibuntu in sources.list; you might want to open the sources.list file in Gedit to add the Medibuntu sources:
```
gksudo gedit /etc/apt/sources.list
```
look for the Medibuntu entry (the one you posted as Medibuntu.list):
```
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://packages.medibuntu.org/ feisty free non-free
#deb-src http://packages.medibuntu.org/ feisty free non-free
```
if it's not there, add it at the end of the file. then run an update of the repository information:
```
sudo apt-get update
```
and after that's done, install the necessary packages; for **totem-xine**:
```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs w32codecs libdvdplay0 libdvdcss2 libdvdread3 libdvdnav4
```
for **totem-gstreamer**:
```
sudo apt-get install totem-gstreamer gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-fluendo-mpegdemux gstreamer0.10-gl gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs libdvdplay0 libdvdcss2 libdvdread3 libdvdnav4
```

After that, you *should* be able to play DVDs.

---

### Post by leona on 2007-08-31
Arr that's me not understand the scripts as descibed then, I saw they created a seperate file but there was **no** instructions to say to copy these lines to the source.list file, that's what I was missing, ok I'll give that a go, thanks.

I feel I'm close, but Mplayer and Movie player are still refusing to play dvd's, I will try reinstalling them tomorrow to see if that helps.

---

### Post by leona on 2007-09-01
Ok all sorted thank you, just reinstalled it all again. :)

---

### Post by rgb on 2007-09-27
Hi, 

I am having problem playing dvds. I have posted about this twice (last on)
[http://ubuntuforums.org/showthread.php?t=560503](http://ubuntuforums.org/showthread.php?t=560503)
 but have not received any help. 

Since then I have upgraded to Feisty. And have followed the instructions on this thread. 

A few more things that may help in pinpointing the problem:

1. I am running Feisty on a T42 laptop with a dvd rom. I have played dvds on this earlier, I have checked that two  dvds (They have movies in them) work on other computers (windows) but not on this laptop. On the other hand I am able to play audio cds using this drive. My fstab contents show:

```

/dev/cdrom        /media/cdrom0   udf,iso9660 user,auto     0       0
/dev/scd0        /mnt/dvd   udf,iso9660 auto,user     0       0

```

2. Gnome automounts audio cds but not dvds.  The gnome-volume-properties mark all options for removable drives to be mounted. The command for dvds was 

```

xine dvd:/

```

I changed this to 
```

vlc dvd:///mnt/dvd

```
but that did not help.

3.  I am able to eject the drive using 
```

eject scd0
eject /dev/scd0
eject /media/cdrom
 eject /media/cdrom0/
eject dvd
eject /dev/dvd
eject /mnt/dvd/
eject

```

4. I also have 
```

ls -l /dev/dvd 
lrwxrwxrwx 1 root root 4 Sep 27 02:10 /dev/dvd -> scd0
ls -l /dev/cdrom 
lrwxrwxrwx 1 root root 4 Sep 27 02:10 /dev/cdrom -> scd0

ls -l /dev/scd0 
brw-rw---- 1 root cdrom 11, 0 Sep 27 02:10 /dev/scd0

```

5. Trying to run xine and using the graphical interface for DVD gives:
```

libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading

```
on the command line, while a pop up says :
```

-xine engine error
There is no input plugin available to handle 'dvd:/'.
Maybe MRL syntax is wrong or file/stream source does not exist'

```

Please help.

---

### Post by RomeReactor on 2007-09-27
Hi. Did you change your Medibuntu sources accordingly (from Edgy to Feisty) after the upgrade? If you're not sure, please post the output of this:
```
cat /etc/apt-sources,list
```
If your Medibuntu entry specifically mentions Edgy, you'll need to change it. Open the sources.list file in Gedit:
```
gksudo gedit /etc/apt/sources.list
```
find the Medibuntu entry, and delete it. Save the file and close Gedit; now that you don't have it (or if you didn't have it to begin with), [go here]("http://ubuntuforums.org/showpost.php?p=3399733&postcount=8") for how to add the new entry.

---

### Post by rgb on 2007-09-27
> **RomeReactor said:**
> Hi. Did you change your Medibuntu sources accordingly (from Edgy to Feisty) after the upgrade? If you're not sure, please post the output of this:
```
cat /etc/apt-sources,list
```
If your Medibuntu entry specifically mentions Edgy, you'll need to change it. Open the sources.list file in Gedit:
```
gksudo gedit /etc/apt/sources.list
```
find the Medibuntu entry, and delete it. Save the file and close Gedit; now that you don't have it (or if you didn't have it to begin with), [go here]("http://ubuntuforums.org/showpost.php?p=3399733&postcount=8") for how to add the new entry.

Thanks a lot for replying.

I checked the sources.list file. It has Feisty packages for Medibuntu. The sources. file you are referring to is from my previous thread where I still had edgy. Anyway here is the output you asked for:
```

##deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/
##edgy main restricted
## Ubuntu Distribution: These would be on the CD
deb http://us.archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu feisty main restricted
##
## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu feisty-updates main restricted
##
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
##UNIVERSE AND MULTIVERSE for UBUNTU
deb http://us.archive.ubuntu.com/ubuntu feisty universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu feisty universe multiverse
##
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse
##
##Security:The main and restricted are on CD
deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
##Non CD security stuff from Universe and Multiverse
deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security universe multiverse
###
###
### Third party software
###
##Google Picasa for Linux repository
# deb http://dl.google.com/linux/deb/ stable non-free
##
#Amarok from kubuntu repository
# deb http://kubuntu.org/packages/amarok-144 edgy main
##
##Repository for g95
# deb ftp://www.gfd-dennou.org/library/cc-env/Linux/debian-dennou stable/
##Opera
deb http://archive.canonical.com/ubuntu feisty-commercial main
##
##Automatix
# deb http://www.getautomatix.com/apt edgy main

#AUTOMATIX REPOS START

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
deb http://www.getautomatix.com/apt feisty main
# Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://packages.medibuntu.org/ feisty free non-free
#deb-src http://packages.medibuntu.org/ feisty free non-free

```

---

### Post by nikoPSK on 2007-12-01
> **RomeReactor said:**
> Yes, this is the sources list. Now we'll proceed to install the necessary packages. To avoid typos, please copy and paste the commands as follow--it may seem a bit complicated at first, so if you have trouble with any command, just post back. You'll be playing DVDs in no time ;)

You'll need to add the Medibuntu repositories: to do so, run this from the terminal:
```
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```This command will add the repositories to your **sources.list**, your list of repositories; then enter this:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```which will fetch and add a key to authenticate the repositories you just added, and will update the repository information on your package managers. Now run this command from the terminal:
```
sudo apt-get install libdvdread3 libdvdcss2 libxine1-ffmpeg totem-xine
```to install the necessary packages. Besides installing the necessary libraries, it will change **totem-gstreamer** for **totem-xine** which will be able to play the menus and use subtitles. After all the packages finish installing, you should be able to play encrypted DVDs.

thanks once again rome reactor!

---

