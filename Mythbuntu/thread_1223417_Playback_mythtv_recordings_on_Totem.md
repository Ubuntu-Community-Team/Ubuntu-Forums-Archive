---
title: "Playback mythtv recordings on Totem"
date: 2009-07-26
forum: Mythbuntu
---

### Post by axelsvag on 2009-07-26
I do not think this problem is new, but all of a sudden I really would like to find the answer to my problem. 

When I want to play my recordings from another player for example totem I get very weird results. For the first if I try to run it on my Mythtv machine the sound increase in speed as times goes by so in the end of an hourly recording there are a lot of Donald Ducks. The sound is very cracking and popping aswell. The same goes for VLC but with XINE and Mplayer this works OK. 

If I try to use my samba network with totem on another computer I am unable to jump in the recording and it just allow me to direct playback much like youtube recordings. And the player normally freeze after 2-3 minutes. The same things occur if I copy the file to any computer. It is recorded in 720x576 and the framerate it is 25 frames/s Sound is MPEG1 48kHz 384kb/s. So to summarize Mythtv recordings plays well in Mplayer and Xine but not in Totem and VLC.

Edit: I tried to convert the mythtv mpeg file to avi with avidemux and the avi file that came out worked perfectly in totem.

I hope someone have any suggestions

---

### Post by axelsvag on 2009-08-07
bump

---

### Post by dannyboy79 on 2009-08-08
have you tried to play the original mpg file in totem from command line to see what the output is? also start vlc via command line and either log output to a file or just watch the terminal to see why audio goes haywire after awhile. that's all i can suggest.

---

### Post by axelsvag on 2009-08-09
OK I will try that.

---

### Post by axelsvag on 2009-08-09
OK Totem give this before I start playing a file.
```
xxx@xxx-mythtv:~$ totem
** (totem:11074): DEBUG: Init of Python module
** (totem:11074): DEBUG: Registering Python plugin instance: YouTubeH264+TotemPythonPlugin
** (totem:11074): DEBUG: Creating object of type YouTubeH264+TotemPythonPlugin
** (totem:11074): DEBUG: Creating Python plugin instance
** (totem:11074): DEBUG: Init of Python module
** (totem:11074): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:11074): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:11074): DEBUG: Creating Python plugin instance

** (totem:11074): WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name

```

After starting a file and totem freeze. No more

---

### Post by axelsvag on 2009-08-09
OK and with VLC I get this 
```
xxx@xxx-mythtv:~$ vlc
VLC media player 0.8.6e Janus

** (.:11152): CRITICAL **: clearlooks_style_draw_focus: assertion `height >= -1' failed
[00000363] pulse audio output error: Failed to connect to server: Connection refused
[00000363] pulse audio output error: Pulse initialization failed



```

---

### Post by dannyboy79 on 2009-08-11
> **axelsvag said:**
> OK and with VLC I get this 
```
xxx@xxx-mythtv:~$ vlc
VLC media player 0.8.6e Janus

** (.:11152): CRITICAL **: clearlooks_style_draw_focus: assertion `height >= -1' failed
[00000363] pulse audio output error: Failed to connect to server: Connection refused
[00000363] pulse audio output error: Pulse initialization failed



```

for vlc you'll have to check out some pulseaudio guides. your username needs to be in 3 different pulse groups. there's a guide here: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
for totem, it appears as though you're missing org.gnome.SettingsDaemon.service file. i am not sure how to help but tell you whats in that filename I have. it might be because you're not using gnome because you're using xfce within mythbuntu? if you want to try this you can, issue this and the file will be created with the same thing I have in my file.

sudo echo 'Exec=/usr/lib/gnome-settings-daemon/gnome-settings-daemon' > /usr/share/dbus-1/services/org.gnome.SettingsDaemon.service

note that this will only work if you have the file located where it's looking for it. if you have a file called gnome-settings-daemon located at /usr/lib/gnome-settings-daemon/  then this should work. then you'll haev to make sure the owner and group are correct using the below commands.

```
sudo chown root:root /usr/share/dbus-1/services/org.gnome.SettingsDaemon.service && sudo chmod 644 /usr/share/dbus-1/services/org.gnome.SettingsDaemon.service
```

the above command will set the owner:group to root and make the file read and write by the owner and read by group and others. that's how my system is set up. if it doesn't work for you then I would just delete the file you created with the above commands. you can accompliosh this by issuing:

```
sudo rm -rf /usr/share/dbus-1/services/org.gnome.SettingsDaemon.service
``` BE VERY CAREFUL, using sudo rm -rf is extremely dangerous because it permanently delete anything you tell it to because the "-rf" is forcing removal of the file. good luck

---

### Post by axelsvag on 2009-08-12
Thank you for your advices. I will try all of them tonight. But I am a little puzzled because they do not seems to have anything to do with the originally video problem connected to mythtv created files (mpg) from analog tuner (PVR500), or??

---

### Post by dannyboy79 on 2009-08-14
> **axelsvag said:**
> Thank you for your advices. I will try all of them tonight. But I am a little puzzled because they do not seems to have anything to do with the originally video problem connected to mythtv created files (mpg) from analog tuner (PVR500), or??
what do you have for sound playback in the frontend settings? it shouldn't be /dev/dsp, it should be ALSA:DEFAULT, i am pretty sure about this. give that a try.

---

### Post by axelsvag on 2009-08-16
I will look into that aswell. But it really does not explain that the problem is persistent even if I copy the video file on a usb stick and try to play it on another computer. Maybe som codecs are missing in Totem and VLC?

---

