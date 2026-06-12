---
title: "Can't play WMV files; need Windows decoder plugins"
date: 2010-02-15
forum: Multimedia Software
---

### Post by techiewannabe on 2010-02-15
I am unable to play WMV files. When I try to, I am prompted to seek and install plugins. I have been unable to locate them. The message I get is:

"No packages with the requested plugins found.
The requested plugins are:
Windows Media Audio 8 Decoder
Microsoft MPEG-4 4.3 Decoder"

I understand that WMV files are not open source and I believe that I have correctly loaded the Medibuntu links, but I am not sure. 

About 8 weeks ago, I did a full reinstall of Ubuntu 9.04 and thought that I had everything working fine. I do not recall whether I had trouble with WMV files before the reinstall.

I am still very much a noobie.

Any help would be appreciated.

---

### Post by ajgreeny on 2010-02-15
If you  really have enabled the medibuntu repos, install w32codecs (or w64codecs if using 64 bit OS) and that should solve your problems.

---

### Post by techiewannabe on 2010-02-15
ajgreeny:

Thanks for your prompt reply. Unfortunately, when I looked at the programs in Syaptic Package Manager, it already had W32codecs installed. Nonetheless, I reinstalled it, but it didn't solve my problem. I then tried to install "non-free-codecs," but that didn't help either.

I assume that I have correctly installed Medibuntu. When I go to Synaptic Package Manager>Settings>Repositories>Third Party Software, Medibuntu Source and Medibuntu Ubuntu 9.04 are both checked.

I'm fairly sure that I'm running a 32 bit OS. My computer is over 5 years old. (It is a Compaq Presario R3000 laptop.)

Thanks.

techiewannabe

---

### Post by ajgreeny on 2010-02-15
Try installing all the gstreamer good, bad and ugly plugins that you can see in synaptic; that might help.  Also search for wmv and see what that shows you.

---

### Post by techiewannabe on 2010-02-16
Thanks Ajgreeny:

As you suggested, I installed the "good," "bad," and "ugly" files found in Gstreamer 

Still no luck, I'm afraid.

I also looked at anything under WMV but none of the uninstalled programs sounded like they were what I needed.

If you, or anyone else, has any other ideas, I would appreciate hearing from you.

Thanks, again.

Techiewannabe

---

### Post by mutex023 on 2010-02-16
Install VLC media player.

---

### Post by montini on 2010-02-16
there is a solution:

[http://www.cetlot.com/2009/11/online-tv-mmsh-ubuntu/](http://www.cetlot.com/2009/11/online-tv-mmsh-ubuntu/)

It is in russian, but the main part is this:

sudo apt-get install gecko-mediaplayer

After that, you can play mms streams with gnome-mplayer.
Well, I am not sure how about .wmv files, but .wma should be played also.

---

### Post by mc4man on 2010-02-16
You really shouldn't be having much of an issue here, wma8 usually refers to wma2, sometimes wmas. Most players can handle those.
For gstreamer I'd re run this and try again, vlc can play wma2 by default thru avcodec.

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly gstreamer0.10-pitfdll 
```

You could also add the multiverse plugins if desired. (mainly for encoding, won't hurt to install

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly gstreamer0.10-pitfdll \
gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse

```

---

### Post by techiewannabe on 2010-02-17
Thanks to everyone for your suggestions. Unfortunately, my problem persists. When I used Montini's suggestions, I got the following message.

tom@Compaq:~$ sudo apt-get install gecko-mediaplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gnome-mplayer
The following NEW packages will be installed:
  gecko-mediaplayer gnome-mplayer
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 468kB of archives.
After this operation, 1659kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse gnome-mplayer 0.9.4-1 [292kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse gecko-mediaplayer 0.9.4-1ubuntu1 [175kB]
Fetched 468kB in 2s (163kB/s)          
Selecting previously deselected package gnome-mplayer.
(Reading database ... 200485 files and directories currently installed.)
Unpacking gnome-mplayer (from .../gnome-mplayer_0.9.4-1_i386.deb) ...
Selecting previously deselected package gecko-mediaplayer.
Unpacking gecko-mediaplayer (from .../gecko-mediaplayer_0.9.4-1ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Setting up gnome-mplayer (0.9.4-1) ...

Setting up gecko-mediaplayer (0.9.4-1ubuntu1) ...

Processing triggers for menu ...

    You have to configure "localepurge" with the command

        dpkg-reconfigure localepurge

    to make /usr/sbin/localepurge actually start to function.

    Nothing to be done, exiting ...


I don't know if this message means anything.
Thanks to each of you for your patience.

Techiewannabe

---

### Post by mutex023 on 2010-02-18
Do you only want to use Totem player ? Because VLC does a great job of playing everything.

---

### Post by montini on 2010-02-18
> **techiewannabe said:**
> 

        dpkg-reconfigure localepurge

Techiewannabe

Strange, as it was fluent in my situation. So did you actually try the suggested above?

---

### Post by techiewannabe on 2010-02-18
Montini:

Thanks for your note. 

I also noticed the directive to, "dpkg-reconfigure localepurge." However, I'm afraid that I have no idea what that means. Are you aware of a site that will walk me through this?

I'm still quite new to Linux.

Thanks.

Techiewannabe

---

### Post by techiewannabe on 2010-02-18
Mutex023:
Thanks for your suggestion. I tried opening the WMV file with VLC. It looked like it was "trying" to play the video, but there was no sound or image. The scroll bar was moving from left to right and it was showing the amount of time lapsed.

Also, Mantini:
I figured out how to "reconfigure the localepurge." Unfortunately, the problem persists.

I appreciate the suggestions that each of you has offered.

Techiewannabe.

---

### Post by PRC09 on 2010-02-18
I have wmv files playing fine on my system using Totem Movie Player using Xine.If you go to Applications > Add remove > select All available applications from the top drop down box > in the search box enter Totem and then select the following > Movie Player next Movie Player(Gstreamer)and  Movie Player Totem(xine backend).Then click apply changes and this should enable you to play wmv files.Not sure if all 3 are required but thats what is installed on mine.......

---

### Post by techiewannabe on 2010-02-20
PRCO9:
Thanks for your suggestion. I did exactly what you suggested but continue to have the same difficulty.

Jason Smith 1: 
I followed your suggestion. When I seek wmplayer or mplayer2, I cannot find either one of them. I looked to download them using Synaptic but couldn't find them. 

Any suggestions?

Thanks to each of you for your suggestions, along with others who have tried to help me with this annoying problem. I feel like there is probably a simple solution that I, because of my Linux ignorance, am overlooking.

Techiewannabe

---

### Post by mcduck on 2010-02-20
You need two things.

First, the Gstreamer module that allows Gstreamer to use .dll files:
**gstreamer0.10-pitfdll**

Second, you need **w32codecs** or **w64codecs**, depending if you are running 32- or 64-bit version of Ubuntu. These are not available in any of Ubutnu's own repositories, I suggest adding the Medibuntu repository to get them: [http://www.medibuntu.org/]("http://www.medibuntu.org/")

After installing those packages you should be able to play DRM-free windows media files in any app that uses Gstreamer. However if your files *do* have some sort of DRM you are pretty mch out of luck.

---

### Post by Pjotr123 on 2010-02-20
You can try this how-to:
[http://sites.google.com/site/easylinuxtipsproject/multimedia](http://sites.google.com/site/easylinuxtipsproject/multimedia)

---

### Post by techiewannabe on 2010-02-20
Thanks, mcduck and Pjotr123 for your suggestions. 

I do have medibuntu installed. Synaptic shows that I have gstreamer0.10-pitfdll andw32codecs installed. I have not installed w64codecs because I believe that my system is a 32 bit system. The computer, a laptop, is over 5 years old. (Is there a way I can check on this?)

I wasn't sure how to take advantage of the Google site you offered, Pjotr123.

Thanks for the suggestions.

I'm afraid that my newbie status is a real liability with this problem!

Techiewannabe.

---

### Post by PRC09 on 2010-02-20
Just something to try,if you can download the wmv file to your desktop and try and play it.if you cant play it try right click and try different players until you can.I originally had the problem that Firefox didnt pick the correct plugin or didnt see the plugin for some reason.So I had to download the wmv file and when I double clicked the file it would play just fine.I then found which player it was playing in and adjusted my Firefox applications to use that to play it and all was fine....

---

### Post by techiewannabe on 2010-02-21
PRC09:

Thanks for your suggestion. 

I did as you suggested and found the following problems. When I open Totem, the default player, I have the difficulties that led to this thread. The following programs fail to load: Gnome Player, MoviePlayer (Xine), and Mplayer. (I tried to reinstall these programs but it didn't help.) VLC opens and appears to be running. It shows a 1:42 minute clip that is counting down, yet there is no audio or video.

Thanks to you and the others for your help with this. I look forward to figuring this out!

Techiewannabe.

---

### Post by PRC09 on 2010-02-21
Another guess,check in Synaptic for any broken packages,System > Admin > Synaptic > lower left pane and select custom from there and then broken from top left and see if there is anything...... I am no expert so just something to check....

---

### Post by mc4man on 2010-02-21
For totem-xine (depending on the audio in your wmv may be your best bet) ck. that this is installed
```
sudo apt-get install libxine1-ffmpeg
```

For vlc, open vlc in a terminal with this and then open your file (or drag and drop the file onto vlc

```
vlc --vout x11
```

This will produce alot of debugging output so  try above first

```
vlc -vv --vout x11
```

(If your video contains wma3 audio then the repo vlc and most likely totem-gstreamer will not play, though you'd usually see an error box

---

### Post by techiewannabe on 2010-02-21
Problem resolved!! Thanks to everyone!

Here is what I found out. In following PRC09's suggestion, I went to Synaptic and looked for "broken packages." There were none. However, I also looked at the files under "Not Installed (Residual Configured)." I installed a couple of "residual files" and checked after each install. Finally I installed a file called "libavcodec52," which apparently solved the problem. I was immediately able to play the WMV file. 

Obviously, I need to learn more about "Not Installed (Residual Config)" files.

By the way, other than putting it in the subject line, is there some way to indicate that a problem has been resolved so that others can benefit from my excruciating learning experience? Likewise, I think that I read somewhere that there is a place to indicate a "thank you" to those who helped resolve a problem. How do I do that?

Thanks again to everyone for your help.

Techiewannabe.

:D

---

### Post by mcduck on 2010-02-21
> **techiewannabe said:**
> Problem resolved!! Thanks to everyone!

Here is what I found out. In following PRC09's suggestion, I went to Synaptic and looked for "broken packages." There were none. However, I also looked at the files under "Not Installed (Residual Configured)." I installed a couple of "residual files" and checked after each install. Finally I installed a file called "libavcodec52," which apparently solved the problem. I was immediately able to play the WMV file. 

Obviously, I need to learn more about "Not Installed (Residual Config)" files.

By the way, other than putting it in the subject line, is there some way to indicate that a problem has been resolved so that others can benefit from my excruciating learning experience? Likewise, I think that I read somewhere that there is a place to indicate a "thank you" to those who helped resolve a problem. How do I do that?

Thanks again to everyone for your help.

Techiewannabe.

:D

"Not Installed (Residual Config)" usually means that it's something you have installed at some point, and then uninstalled (but without doing a "Complete Uninstall", so that the configuration files are still left on the system).

What comes to marking threads as solved and thanking people, both those features are disabled for now since they caused some problems with the forum software. You can mark the thread as solved by editing the thread title, and thank people simply by saying "thanks" to them. :)

---

### Post by techiewannabe on 2010-02-21
Thanks, mcduck.

Your explanation of "Not Installed (Residual Config)" was quite clear; I suspected it was something like what you outlined. 

Thanks for your help in exploring solutions to this problem.

Techiewannabe

---

