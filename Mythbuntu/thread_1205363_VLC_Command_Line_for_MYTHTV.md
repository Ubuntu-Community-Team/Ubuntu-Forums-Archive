---
title: "VLC Command Line for MYTHTV"
date: 2009-07-05
forum: Mythbuntu
---

### Post by Dragonflyoh on 2009-07-05
I am attempting to set up MYTHTV to use VLC as the player for AVI files. I found a command line of:

vlc file://%s vlc:quit

I set up AVI files with that line and VLC runs however it is not full screen and it will not send audio to SPDIF.  After some searching I think -ao alsa:device =spdif might work for the audio problem but I can find nothing about the full screen. Any assistance would be appreciated.

The reason for the switch from the Internal player is the internal player was giving bouncy video and halting audio on some avi files while VLC played them fine.

---

### Post by ian dobson on 2009-07-05
Hi,

try vlc --help from a terminal, that should list all the command line options that vlc supports.

Regards
Ian Dobson

---

### Post by crez79 on 2009-07-06
There is a pretty good wiki entry [here]("http://www.mythtv.org/wiki/VLC") that suggests:

> The command line for the video player should be: 

 ```
vlc file://%s vlc://quit
```This will execute vlc passing the file to play in a URL format. The vlc:quit portion adds the quit message to the end of the playlist so that VLC will exit once the playlist is completed. Also, there is an option in the vlcrc for "play-and-stop", which will stop after every playlist item. This will allow you to have a much cleaner command-line option of just "vlc". Whether you want this function as a default it up to you. There are many other options in 

 ```
#~/.vlc/vlcrc
```These are the options that I suggest.  You should read through the configuration file and create your own settings. 

```
intf=dummy    #starts vlc with no interfaces such as web, telnet, or wxWidgets
fullscreen=1  #tells vlc to playback in fullscreen
width=1920    #vlc will start in a window, I use these settings
height=1080   #to make the initial window the full size of my screen
spdif=1       #have vlc audio output over digital S/PDIF
osd=0         #vlc on screen display is different from MythTV, disable to look consistent
rt-priority=1 #a possible speed-up, setting vlc up for real-time priority level
control=lirc  #add LIRC as a control input
```

---

### Post by kadafi69 on 2009-07-06
all I did was open vlc outside of myth, go to preferences and set video to full screen and always on top.

---

### Post by joho500 on 2009-07-06
I set most options in vlc outside of mythtv but leave fullscreen off. I use the following command to run vlc from mythtv:

```
vlc -fullscreen -I dummy file://%s vlc://quit
```

The '-I dummy' tells vlc not to use an interface. Otherwise you see the vlc window with menus flashing to fullscreen.

Joost

---

### Post by Dragonflyoh on 2009-07-06
Thanks for all of the ideas. I combined several of the ideas and vlc is working fine. I appreciate the assistance.

---

