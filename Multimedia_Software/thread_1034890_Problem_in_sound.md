---
title: "Problem in sound"
date: 2009-01-09
forum: Multimedia Software
---

### Post by MajAfy on 2009-01-09
Hello,

I'm really newbie, I downloaded new version of ubuntu (8.10), I want to switch from windows to Linux (I Like Linux) I'm a PHP programmer .
Ok, let me explain my problem. (I search in this forum and Google but my problem does not solve yet :( )
My sound card is onboard and in windows the driver name is Realtek Sound Card AC`97 , and now in Linux I have volume icon on panel but I don't have sound in my speakers ! I trying to install latest version of ALSA (I searched in internet and I found I should use ALSA) but after that my volume icon disabled and I couldn't enabled that so I reinstalled the Linux !!! now, every things are default anybody can help me ?

(I just use this guide : [http://ubuntuforums.org/showthread.php?t=1025941](http://ubuntuforums.org/showthread.php?t=1025941) because this problem is same as my problem but my problem didn't not solved)

---

### Post by mwillams73 on 2009-01-09
I dont know if your problem is the same as mine( i had sound but no sound effects would play) This is a bug, I found the bug fix at launch pad and asked them to explain in simple terms how to fix it this was the reply


  If you are on Intrepid then you need to add the repository

"deb [http://ppa.launchpad.net/gkulyk/ubuntu](http://ppa.launchpad.net/gkulyk/ubuntu) intrepid main"

by going to System > Administration > Software Sources

Third Party Software tab.

Click on Add and give the above line without the quotes

Click Close .

It will ask to reload, let it do fetch.

In the updates you will get the new canberra 0.10

after it downloaded the updates it took like 5 seconds, I rebooted and now i have the sound effects. If this not your problem, you should look around the forums, ive had a few minor bugs and glitches and have found help for all of them . Goodluck I hope this helps!!!!

---

### Post by MajAfy on 2009-01-09
Thanks mwillams73,

I did all you said but it seem that nothing changed!
I searched on the net about 2 days ! and I cannot found any way :(

so cann't I have sound in Linux ? :(

---

### Post by MajAfy on 2009-01-10
I have this ptoblem yet, nobody cann't help me?

---

### Post by linux_tech on 2009-01-10
Post output of ```
aplay-l
```
and
```
at /proc/asound/card0/codec#* | grep Codec
```



Try installing few programs to improve sound in intrepid:
```
sudo apt-get install esound
sudo apt-get install alsa-oss

sudo apt-get install libasound2

sudo apt-get install libasound2-plugins

```
Also install and run gnome-alsamixer (easier to use than alsa-mixer
```
sudo apt-get install gnome-alsamixer

``` 
To open gnome-alsamixer type
```
gnome-alsamixer

```
check all settings, make sure nothing is muted

To open volume control type:

```
gnome-volume-control

```

---

### Post by MajAfy on 2009-01-10
Thanks for your help,

this is the output of 

```

$aplay -l :

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH7 [Intel ICH7], device 0: Intel ICH [Intel ICH7]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH7 [Intel ICH7], device 4: Intel ICH - IEC958 [Intel ICH7 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

and

```

$ at /proc/asound/card0/codec#* | grep Codec
syntax error. Last token seen: /
Garbled time

```


I'm in testning your another solutions , I will inform you the result here.

---

### Post by MajAfy on 2009-01-10
I cannot hear a sound.

this is the results of that commands:

```

majid@majid-desktop:~$ sudo apt-get install esound
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  pulseaudio-esound-compat ubuntu-desktop
The following NEW packages will be installed:
  esound
0 upgraded, 1 newly installed, 2 to remove and 0 not upgraded.
Need to get 28.1kB of archives.
After this operation, 131kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com intrepid/universe esound 0.2.40-0ubuntu1 [28.1kB]
Fetched 28.1kB in 2s (13.5kB/s)
(Reading database ... 138080 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing pulseaudio-esound-compat ...
Processing triggers for man-db ...
Selecting previously deselected package esound.
(Reading database ... 138065 files and directories currently installed.)
Unpacking esound (from .../esound_0.2.40-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up esound (0.2.40-0ubuntu1) ...
majid@majid-desktop:~$ sudo apt-get install alsa-oss
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  alsa-oss
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 52.6kB of archives.
After this operation, 221kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com intrepid/universe alsa-oss 1.0.15-1 [52.6kB]
Fetched 52.6kB in 3s (16.8kB/s)  
Selecting previously deselected package alsa-oss.
(Reading database ... 138068 files and directories currently installed.)
Unpacking alsa-oss (from .../alsa-oss_1.0.15-1_i386.deb) ...
Processing triggers for man-db ...
Setting up alsa-oss (1.0.15-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
majid@majid-desktop:~$ sudo apt-get install libasound2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libasound2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
majid@majid-desktop:~$ sudo apt-get install libasound2-plugins
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libasound2-plugins is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
majid@majid-desktop:~$ sudo apt-get install gnome-alsamixer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  gnome-alsamixer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 55.6kB of archives.
After this operation, 602kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com intrepid/universe gnome-alsamixer 0.9.7~cvs.20060916.ds.1-1 [55.6kB]
Fetched 55.6kB in 3s (17.1kB/s)         
Selecting previously deselected package gnome-alsamixer.
(Reading database ... 138088 files and directories currently installed.)
Unpacking gnome-alsamixer (from .../gnome-alsamixer_0.9.7~cvs.20060916.ds.1-1_i386.deb) ...
Processing triggers for man-db ...
Setting up gnome-alsamixer (0.9.7~cvs.20060916.ds.1-1) ...

majid@majid-desktop:~$ gnome-alsamixer

** (gnome-alsamixer:9749): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Surround Jack Mode"!

** (gnome-alsamixer:9749): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Mic Select"!

** (gnome-alsamixer:9749): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "IEC958 Playback Source"!

** (gnome-alsamixer:9749): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Mono Output Select"!

** (gnome-alsamixer:9749): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Channel Mode"!

** (gnome-alsamixer:9749): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "IEC958 Playback Source"!

** (gnome-alsamixer:9749): WARNING **: gam_toggle_set_state (). No idea what to do for mixer element "IEC958 Playback Source"!

** (gnome-alsamixer:9749): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "IEC958 Playback Source"!
majid@majid-desktop:~$ 

```

---

### Post by MajAfy on 2009-01-11
Dear linux_tech, would you please help me ?

---

### Post by umechanism on 2009-01-11
I'm having the same problem as you and started another thread here.  Let's keep each other updated if we find a solution.

[http://ubuntuforums.org/showthread.php?t=1021477](http://ubuntuforums.org/showthread.php?t=1021477)

---

### Post by mwillams73 on 2009-01-11
Did you run the repository update like I said?, if you havnt thats your problem, you have to down load the bug fix via synaptic. then you should have sound, also your sound card doesnt like linux, so you might be having additional problems on top of the sound bugs, first make sure that you got libcanberra 0.10, im gonna post the direct link to launchpad so you can see what Im talking about;

[https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507](https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507)

Go there and see for yourself if your having the same problem, I hope this helps

---

### Post by mwillams73 on 2009-01-11
Also you removed your alsa drivers but didnt replace them with anything so now you wont have sound until you find the correct drivers for your card, atleast thats what your terminal output says, try reinstalling those alsa drivers and see if that helps

---

### Post by umechanism on 2009-01-11
> **mwillams73 said:**
> Did you run the repository update like I said?, if you havnt thats your problem, you have to down load the bug fix via synaptic. then you should have sound, also your sound card doesnt like linux, so you might be having additional problems on top of the sound bugs, first make sure that you got libcanberra 0.10, im gonna post the direct link to launchpad so you can see what Im talking about;

[https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507](https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507)

Go there and see for yourself if your having the same problem, I hope this helps
I'm following this thread too and I did install the new repository and received the update but I still do not have any sound.  I may not have everything set correctly in Sounds>Preferences because when I choose "Sound Events" I have 13 selections to choose from.  OSS, ALSA, etc... I don't know which one to choose.  Do you?

---

### Post by MajAfy on 2009-01-16
Thanks for your reply,

Yes I did that commands, but I don't have sound yet.

I checked the libcanberra and installed (libcanberra 0.10-0ubuntu1~ppa1)

---

### Post by MajAfy on 2009-01-28
> **MajAfy said:**
> Thanks for your reply,

Yes I did that commands, but I don't have sound yet.

I checked the libcanberra and installed (libcanberra 0.10-0ubuntu1~ppa1)
oops, nobody not here to help me on this problem ?

---

### Post by umechanism on 2009-01-28
I found a solution that worked for my Dell Studio Desktop.  Go to this thread:

[http://ubuntuforums.org/showthread.php?t=997506&page=10](http://ubuntuforums.org/showthread.php?t=997506&page=10)

The link will start you on page 10 of the thread.  Look for my username towards the bottom and you will see the solution that I posted.

I now have sound coming from CD's and from last.fm (music radio station streamed from the internet) but I still do not have sound in Firefox when viewing YouTube.  At least I know my sound card is working.

The Firefox/sound issue is likely related to the Adobe Flash I have loaded.  It is just a matter of finding what tweak I need to resolve that.

Also, you need to read all of the posts in the thread I have linked you to.  Be patient and don't give up.

Cheers.

---

