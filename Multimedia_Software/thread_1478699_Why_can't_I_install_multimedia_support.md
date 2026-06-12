---
title: "Why can't I install multimedia support?"
date: 2010-05-10
forum: Multimedia Software
---

### Post by Cityscape on 2010-05-10
I set up up Ubuntu 10.04 Lucid on my desktop. Why can I not install multimedia support for common formats following the guide [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683")?

I've added the medibuntu repo. I'm up to the part where it says "UBUNTU FAMILY 8.10 AND HIGHER USERS ONLY" and i'm following directions for "32-Bit Ubuntu Users". 
This is what I get when I paste the command in terminal:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnash is not installed, so not removed
Package gnash-common is not installed, so not removed
Package libflashsupport is not installed, so not removed
Package mozilla-plugin-gnash is not installed, so not removed
Package swfdec-mozilla is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 50 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-fonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-fonts has no installation candidate
It says "0 upgraded, 0 newly installed, 0 to remove", why am I being told this?

If this guide is not for Lucid than what guide is? Please help me. Last time (with Jaunty) I couldn't get help and I destroyed DVD support.

---

### Post by Dayofswords on 2010-05-10
you forgot to mention what command you pasted in :P

also this guide is more updated
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Cityscape on 2010-05-10
> **Dayofswords said:**
> you forgot to mention what command you pasted in :P
[CODE]sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar/CODE]

---

### Post by Cityscape on 2010-05-10
> **Dayofswords said:**
> also this guide is more updated
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
I don't see anything here that explains how to add support for .avi
's, MP3's, FLV's etc. on Lucid Lynx.

---

### Post by Cityscape on 2010-05-10
I tried to open a video file and Lucid wanted to search for suitable plugins. I let it and it recommend gstreamer0.10-plugins-ugly. Synaptic's description said that "ugly" can cause distribution problems! Why would Ubuntu want me to install it then?

---

### Post by cchhrriiss121212 on 2010-05-10
Just open synaptic and install ubuntu-restricted-extras, then download vlc and you can play anything you like.

---

### Post by wojox on 2010-05-10
Try this [http://wojox.homelinux.org/?p=12](http://wojox.homelinux.org/?p=12)

---

### Post by Cityscape on 2010-05-10
So basically I just install the "non-free-codecs" package. And that will install restricted extra plus other codecs. 

Right?

---

### Post by wojox on 2010-05-10
You are correct.

---

### Post by Cityscape on 2010-05-10
So did that install video DVD support? I need video DVD support. Last time with Jaunty i messed up the DVD support badly.

---

### Post by Cityscape on 2010-05-10
> **Cityscape said:**
> So did that install video DVD support? I need video DVD support. Last time with Jaunty i messed up the DVD support badly.
???

---

### Post by eltonw on 2010-05-10
> **Cityscape said:**
> So did that install video DVD support? I need video DVD support. Last time with Jaunty i messed up the DVD support badly.
The default installation of Movie Player is the app to play all videos, including DVD'S.

 _*You are jumping through hoops needlessly*_. 

You can install ***other*** sound and video programs. Simply run either Synaptic or "[COLOR=Sienna]**Ubuntu Software Center**[/COLOR]", do a  search for whatever you want to install. Either package manager can be used to remove installed applications.

In Lucid, the Ubuntu Software Center is even *more* improved: Packages are divided and subdivided into sections _to make selection easier_!

... install something, try it. If you don't like it, run the installer  to remove it.
That is the freedom of choice you have with open source (Ubuntu Linux)

---

### Post by Cityscape on 2010-05-14
> **Cityscape said:**
> So basically I just install the "non-free-codecs" package. And that will install restricted extra plus other codecs. 
Okay now I have support for Mp3's WMA's etc. But when I play the files I get a fuzz-like sound. I do not get that on my Vista computer. How do I get audio files to play smoothly without fuzz?

The difficulty of installing multimedia support in Ubuntu frustrates me so much that I'm gonna have to go back to Windows if I can't get this fixed.

---

### Post by qwerty2009 on 2010-05-14
if you did not install the first lot of codes in the first place i doubt you would of had problems you just simply

click: [here]("apt:ubuntu-restricted-extras?section=universe?section=multiverse") to enable the media playback

and copy and paste the following into terminal to enable dvd playback - 

sudo /usr/share/doc/libdvdread4/install-css.sh


ps.. as you've copied various of commands from that page that hasn't been updated since before karmic you might have various problems with conflicted packages as there is *tons* of commands its probably difficult to figure out which ones you've copied.

id sugest you re-install lucid and just use the commands ive pasted and everything will work straight away

---

### Post by Cityscape on 2010-05-14
> **qwerty2009 said:**
> id sugest you re-install lucid and just use the commands ive pasted and everything will work straight away
Are you sure?

Every release I have multimedia install problems. Last time (with Jaunty) I got audio support working. But I was given ton of different ways to install video DVD by different people. And all I got in the end was really bad skipping and messed up DVD support.

---

### Post by qwerty2009 on 2010-05-14
because back then there were various ways to it as you can see in the link you posted :),

 but now its just 1 click and a copy and paste to get media playback running :D 

i dont suggest for you to reinstall unless you have the cd and/or a good internet connection tho

---

### Post by wojox on 2010-05-14
```
sudo apt-get install libdvdread4
```

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Reboot.

---

### Post by wojox on 2010-05-14
> **Cityscape said:**
> Are you sure?

Every release I have multimedia install problems. Last time (with Jaunty) I got audio support working. But I was given ton of different ways to install video DVD by different people. And all I got in the end was really bad skipping and messed up DVD support.

What are your system specs?

---

### Post by chamarams on 2010-05-14
click application go ubuntu software center in serch tab type VLC and install vlc give u password.after install you can play by right click.

---

### Post by Cityscape on 2010-05-15
> **qwerty2009 said:**
> because back then there were various ways to it as you can see in the link you posted :),

but now its just 1 click and a copy and paste to get media playback running :D 

i dont suggest for you to reinstall unless you have the cd and/or a good internet connection tho
so the only package I need for audio support is subunit-restricted-extras? Can you guaranty that it'll work? 

I have the Ubuntu CD, I don't think Internet is needed to install Ubuntu (although I have limited bandwidth high speed if necessary).
> **wojox said:**
> What are your system specs?
Intel Pentium 4 clocked at 3 Ghz (not sure if dual or single core)
2 GB of DDR2 RAM (.25 Ghz taken by graphics)
ATI Radeon X200 graphics with 256 MB video RAM
250 GB HDD
AOpen 16X DVD burner & a DVD reader drive

---

### Post by Cityscape on 2010-05-15
But if I reinstall Ubuntu and just installed ubuntu-restricted-extras and libdvdread4, will I get good working multimedia support? Yes or no?

If that'll get me working media support then I'll do it.


I mean all I want is a computer with good working media support, if Ubuntu can't give me that I'll have to go for Windows or LinuxMint. But I would like to keep my Ubuntu if possible.

---

### Post by Cityscape on 2010-05-15
What do you guys think?

---

### Post by Cityscape on 2010-05-15
Does no one have suggestions?

Should I reinstall ubuntu and follow qwerty2009's instructions for audio or not?

---

### Post by Cityscape on 2010-05-18
Okay, I reinstalled Ubuntu and installed ubuntu-restricted-extras like qwerty2009 said. Audio support is working great now, thanks a ton.

I then installed libdvdread4 the way you guys told me to. Some video DVD's would play perfect before I installed it. But some would not play at all. After I installed libdvdread4 the ones that would not play before now do play. But they don't play smoothly. I get some skipping (both video & sound).

How can I get these DVD's to play smootly too? This is a family multimedia PC so I need to get all DVD's to play well.

---

### Post by eltonw on 2010-05-18
> **Cityscape said:**
> Okay, I reinstalled Ubuntu and installed ubuntu-restricted-extras like qwerty2009 said. Audio support is working great now, thanks a ton.

I then installed libdvdread4 the way you guys told me to. Some video DVD's would play perfect before I installed it. But some would not play at all. After I installed libdvdread4 the ones that would not play before now do play. But they don't play smoothly. I get some skipping (both video & sound).

How can I get these DVD's to play smootly too? This is a family multimedia PC so I need to get all DVD's to play well.

It might be due to some BASIC things: have you cleaned the DVD drive lately? Are the disks clean, or do they have some scratches? if you are a smoker, do you smoke while at the computer? (Second-hand by-products can get into electronic equipment and degrade performance). Other things like swap space, and available buffer in the multimedia application settings may also affect performance.

Some useful links may help you, HERE: [http://ubuntuforums.org/showthread.php?t=1483371]("http://ubuntuforums.org/showthread.php?t=1483371")

cheers,

---

### Post by Cityscape on 2010-05-18
"have you cleaned the DVD drive lately?" **No I haven't**.
"Are the disks clean, or do they have some scratches?" **A few small scratches**
"if you are a smoker, do you smoke while at the computer?" **No one smokes in my house**.
"Other things like swap space, and available buffer in the multimedia application settings may also affect performance" **maybe that's my problem?**

---

