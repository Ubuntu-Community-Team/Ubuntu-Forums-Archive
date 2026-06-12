---
title: "how to play avi videos in 10.04 LTS"
date: 2010-07-31
forum: Multimedia Software
---

### Post by fullmoon13 on 2010-07-31
[FONT=Tahoma][SIZE=3][COLOR=Black]Hello all, **peace be upon ya**! :D

I have used **ubuntu** for a long time but always using either a **live CD** or my **Flash stick**.

On past Thursday i decided to install **ubuntu **on my laptop and i did it :p. It is light and healthy (ha ha:popcorn:).
Any way, I would like to play **AVI**, **MKV**, **RMVB**, and **MP4** videos but i couldn't. I tried a lot of **debian **packages and drives (i.e. files with .deb extension) but no result except installing **RealPlay** that i am using it to play mp3 files **only**.

Please, can you give me some packages to play those files. (I can't connect my laptop to Internet for the time being). In addition, I have [/COLOR][/SIZE][/FONT]**[FONT=Tahoma][SIZE=3][COLOR=Black]Huawei E1750 USB Modem[/COLOR][/SIZE][/FONT]**[SIZE=3][COLOR=Black] but the system does not recogize it.
Is there any way to **play** those **video**s and **surf** the net using the modem in **UBUNTU 10.04 LTS**.
Thank you in advance. yours.
**fullmoon13**;)
[/COLOR][/SIZE]

---

### Post by Cavsfan on 2010-07-31
Install mencoder and ffmpeg from Synaptic Package Manager.
System > Adinistration > Synaptic Package Manager.
Just get the ones with the red symbol beside them.

---

### Post by Cavsfan on 2010-07-31
Install Totem via Synaptic too and that should give you **Movie Player** in Applications > Sound and Video.
This along with **ffmpeg** and **mencoder** will play most anything.

Also install anything it advises along with the above packages.

---

### Post by fullmoon13 on 2010-07-31
Thank you very much. I will try it once i return back to my room. But, Does not this way require online connection.

---

### Post by Cavsfan on 2010-07-31
> **fullmoon13 said:**
> Thank you very much. I will try it once i return back to my room. But, Does not this way require online connection.

Afraid so. It will have to download some stuff.

---

### Post by NFblaze on 2010-07-31
> **fullmoon13 said:**
> Hello all, peace be upon ya! :D

I have used ubuntu for a long time but always using either a live CD or my Flash stick.

On past Thursday i decided to install ubuntu on my laptop and i did it :p. It is light and healthy (ha ha:popcorn:).
Any way, I would like to play AVI, MKV, RMVB, and MP4 videos but i couldn't. I tried a lot of debian packages and drives (i.e. files with .deb extension) but no result except installing RealPlay that i am using it to play mp3 files only.

Please, can you give me some packages to play those files. (I can't connect my laptop to Internet for the time being). In addition, I have Huawei E1750 USB Modem but the system does not recogize it.
Is there any way to play those videos and surf the net using the modem in UBUNTU 10.04 LTS.
Thank you in advance. yours.
fullmoon13;)


For your modem to get internet, the Huawei_E1750 someone has created a script for the device. Looking thru the script you need to download and install [libusb-dev]("http://packages.ubuntu.com/karmic/libusb-dev") and usb-modeswitch [usb-modeswitch]("http://packages.ubuntu.com/karmic/usb-modeswitch"). After, that you should download and run the script over here [Huawei_E1750.sh]("http://fr.sourceforge.jp/projects/sfnet_huaweie1750ubun/releases/").


For the codecs to play AVI,MKV,RVMB, and MP4. You can either install the Mediabuntu repository over at [http://packages.medibuntu.org](http://packages.medibuntu.org) but you will need internet connection to work correctly first if you want to do it using the easy sudo apt-get ways.



IF you still dont have internet you can individual download EACH package and EACH dependency that you dont already have from [http://packages.medibuntu.org/lucid/index.html](http://packages.medibuntu.org/lucid/index.html) and then install them. This will be a long and tedious process , though it can be done. Then if you save all of them in one you can install using dpkg -i *.deb

EDIT: Oh, just remembered the old SuperOS had created an offline installer (before Mininova went downhill) for Multimedia codecs among other things so I googled it and found it's still alive you can download it from [http://hacktolive.org/wiki/Ureoi](http://hacktolive.org/wiki/Ureoi) Although it says 9.04 it should still work.

---

### Post by Cavsfan on 2010-07-31
Oh yea, forgot you do need the medibuntu repositories for MP3s, AVIs, etc..

You will need Internet to do this though.

To get mp3 and other multimedia support on your Ubuntu 10.04 LTS (*Lucid Lynx*). 

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list
sudo apt-get --quiet update
sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring
sudo apt-get --quiet update
```After adding the repositories and key, install non-free-codecs

```
sudo apt-get install non-free-codecs
```Install DVD Support:

```
sudo apt-get install libdvdcss2
```Windows codecs: (for WMV, RealMedia and other formats)
If you have a 32bit machine:
```
sudo apt-get install w32codecs libdvdcss2
```Or if you have a 64 bit machine: (don't do both)
```
sudo apt-get install w64codecs libdvdcss2
```If VLC Mplayer is not already installed:

```
sudo apt-get install vlc mplayer
```And if you want Adobe Acrobat Reader:

```
sudo apt-get install acroread acroread-plugins

```If you want the Mplayer Plugin for Firefox:

```
sudo apt-get install mozilla-mplayer
```

---

### Post by fantomgr on 2010-08-01
Hi guys. I have the same problem and I have tried most of the recommended solutions on this forum (such as [http://ubuntuforums.org/showthread.php?t=1358690](http://ubuntuforums.org/showthread.php?t=1358690) ) and the steps described before by Cavsfan. I still get only sound without picture, with all the players I've tried (vlc, mplayer, etc.)

Any ideas? I don't know what else I could try...

Thanks in advance.

---

### Post by Cavsfan on 2010-08-02
> **fantomgr said:**
> Hi guys. I have the same problem and I have tried most of the recommended solutions on this forum (such as [http://ubuntuforums.org/showthread.php?t=1358690](http://ubuntuforums.org/showthread.php?t=1358690) ) and the steps described before by Cavsfan. I still get only sound without picture, with all the players I've tried (vlc, mplayer, etc.)

Any ideas? I don't know what else I could try...

Thanks in advance.

The only thing I can think of is to add the gstreamer PPA and key from [U][here.]("https://launchpad.net/%7Egstreamer-developers/+archive/ppa")
[/U][COLOR=SeaGreen]Click on Technical details about this PPA[/COLOR] to install the PPA and Key.

Then of course "sudo apt-get update" and "sudo apt-get upgrade" and see if it pulls in anything that will help.
These enabled me to play WMA files in RhythmBox. They will enable you to get the latest updates from the developers. 
I could not find where someone told me to do this.
They might fix your problem, but if not I don't have the slightest clue.
And you'll need someone that knows more than I.
HTH

---

### Post by fantomgr on 2010-08-02
I finally managed to play video files by changing a setting in VLC. Specifically, in Preferences -> Video I changed the Output setting from "Default" to "X11 video output". 

Although at random, at least I can watch videos again...

---

### Post by SunnyRabbiera on 2010-08-02
> **fantomgr said:**
> I finally managed to play video files by changing a setting in VLC. Specifically, in Preferences -> Video I changed the Output setting from "Default" to "X11 video output". 

Although at random, at least I can watch videos again...

Certain formats are a little shaky on linux, especially AVI as some AVI vidoes work and some dont.
This is because AVI is a microsoft format, and as such does not play nice with others.
Not all the time this is the case mind you but some AVis do have coding for windows media player 11 and above and linux can do up to WMP 10 thanks to the reverse engineered codecs.
you may wish to install realplayer as it does have compatibilty for later versions of the format.
Also graphics card can cause issues too, again this is thanks to graphics cards companies having mainly microsoft in mind when making them.
Linux does have its drawbacks though most of them are easy enough to get around

---

### Post by Cavsfan on 2010-08-02
> **fantomgr said:**
> I finally managed to play video files by changing a setting in VLC. Specifically, in Preferences -> Video I changed the Output setting from "Default" to "X11 video output". 

Although at random, at least I can watch videos again...

Glad you got it to work!

---

### Post by SunnyRabbiera on 2010-08-02
> **Cavsfan said:**
> Glad you got it to work!

Yeh it can be rough sometimes, the type of AVI files and his video card come into play a lot

---

### Post by fullmoon13 on 2010-08-03
> **fantomgr said:**
> I finally managed to play video files by changing a setting in VLC. Specifically, in Preferences -> Video I changed the Output setting from "Default" to "X11 video output". 

Although at random, at least I can watch videos again...
Hello dear,
 
can you tell me what u do to play those files?

I think the following INTERNET problem is what stop me from update and download using Synaptic manager. please see the following screen print:(.

---

### Post by fullmoon13 on 2010-08-04
[SIZE=3]Thank you all, now i can play videos in any type ( i hope )

I editted the setting the preference in the Synaptic manager by adding the proxy ip, port as well as my username and password.

then, easily use the synaptic which do the whole job ( where i faced pubkey problem ). anyway, my videos can be played now. thank you very much.):P
[/SIZE]

---

### Post by Cavsfan on 2010-08-04
> **fullmoon13 said:**
> [SIZE=3]Thank you all, now i can play videos in any type ( i hope )

I editted the setting the preference in the Synaptic manager by adding the proxy ip, port as well as my username and password.

then, easily use the synaptic which do the whole job ( where i faced pubkey problem ). anyway, my videos can be played now. thank you very much.):P
[/SIZE]

[SIZE=2]Glad you got the videos to work. Which key does it get the error on?
That can be fixed.[/SIZE]

---

### Post by fullmoon13 on 2010-08-10
> **Cavsfan said:**
> [SIZE=2]Glad you got the videos to work. Which key does it get the error on?
That can be fixed.[/SIZE]
I don't remember the name of the key, but it is some thing like gstreamer or getdeb.net. I am not sure, any way, I am thinking of uninstalling ubuntu and re-install it again because i gave it only 6 gb. if there is any way to increase the volume of the sys. without re-installing it please tell me.

Thank you dear.:D

---

### Post by Cavsfan on 2010-08-10
> **fullmoon13 said:**
> I don't remember the name of the key, but it is some thing like gstreamer or getdeb.net. I am not sure, any way, I am thinking of uninstalling ubuntu and re-install it again because i gave it only 6 gb. if there is any way to increase the volume of the sys. without re-installing it please tell me.

Thank you dear.:D

Ubuntu is a pretty lean system as it is. I forgot what mine was after initial install.
Probably not much more than 6GB.
I currently have ~ 20GB and that is with a bunch of movies (600MG per pop) and my music.

Have you updated the system? The initial updates are not huge, but fairly good sized.
I would not use Update Manager for updating your system as it is offering a partial upgrade right now.
And a partial upgrade can mess up your system!
Just use these three commands:
**sudo apt-get update**    (updates your resources from which to get updates from)
**sudo apt-get upgrade**  (installs some updates)
**sudo apt-get dist-upgrade**    (Gets other updates, remove some things, upgrade others  BUT, [COLOR=Red]don't[/COLOR] use this one right now.)
That is if it says it will remove something and not replace it. It is doing that right now to me for ffmpeg.
If you do not have ffmpeg installed, it may not give you any problems.

But, the 2nd of these 2 commands will tell you exactly what it is going to do.

I only use Update Manager to see if there are any updates out there.

I will look for that key. I have it somewhere.

---

### Post by Cavsfan on 2010-08-10
Edit your sources list - **gksudo gedit /etc/apt/sources.list**
Add this to the very bottom and then save the file:
```
#added gstreamer ppa
deb http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu lucid main
# deb-src http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu lucid main
```Then add the gstreamer key:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 051D8B58
```Then use the above commands to update your system. (I may have already mentioned this), 
but I can watch WMV (windows media video) and WMA (windows media audio) files in Ubuntu.

---

