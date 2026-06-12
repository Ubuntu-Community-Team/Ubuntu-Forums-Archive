---
title: "&#9668; moc a terminal music player &#9658;"
date: 2012-07-27
forum: Multimedia Software
---

### Post by shantiq on 2012-07-27
singing the praises of moc a terminal music player


[CENTER]                   [ATTACH]221851[/ATTACH][[IMG]http://img706.imageshack.us/img706/6336/lm3y.th.png[/IMG]]("http://img706.imageshack.us/img706/6336/lm3y.png")[/CENTER]





for a while i have been using terminal music players like sox nvlc and mplayer;   even knocked up a little [**how to**]("https://help.ubuntu.com/community/PlayMusicFromCommandLine?highlight=%28%5CbCategoryCommandLine%5Cb%29")



so i am extremely grateful to **sysaxed** for having introduced me to moc

which seems is no longer[** maintained**]("http://moc.daper.net/node")    but has so much going for it

that i thought to share this here as many probably have never heard of it
...


Navigation [all details with h key] is possibly better than on nvlc [ will even go from visible to hidden folder with no trouble]
only drawback i have found so far is it does nor seem to handle cuefiles
& fast forward and rewind on long files is slow [compared to nvlc]  ....   **Correction**  ...    until i realized keys  "[" and "]" silently will zip through a 4-hour recording in seconds



&#9668;  first i suggest to install gnome-open-terminal

```
sudo apt-get-install gnome-open-terminal 
```


go to your Music folder right-click and pick open in terminal

&#9668; to install

```
sudo apt-get install moc moc-ffmpeg-plugin
```


&#9668;  to play   ```
mocp
```


and there you are   key h  for all navigation tools



&#9658;&#9668;&#9658;&#9668;&#9658;&#9668;&#9658;&#9668;&#9658;&#9668;&#9658;&#9668;&#9658;&#9668;&#9658;&#9668;&#9658;&#9668;&#9658;&#9668;&#9658;&#9668;&#9658;&#9668;&#9658;&#9668;&#9658;&#9668;&#9658;&#9668;&#9658;&#9668;&#9658;&#9668;&#9658;&#9668;


NOW the default theme might not be to your taste; but it can be changed

```
shift +t 
```    does give you choices

to make them stick read [**here**]("http://ubuntuforums.org/showpost.php?p=12082864&postcount=12")

> [COLOR=#000000] create a new file in /home/yourusername/.moc called "config"[/COLOR]
[COLOR=#000000]Now add this line to your config file(for example):[/COLOR]
[COLOR=#000000]Code:
[/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono]Theme = /usr/share/moc/themes/darkdot_theme[/FONT][/COLOR]

this firms up your theme change

```
sudo chmod 755 /home/yourusername/.moc/config
```
[B]
PS[/B]   if you use ccsm  set > mocp  -G   for pause and play as a hotkey    > ctrl+g as a key binding

**PS 2**  if you have not yet try nvlc/sox/mplayer too   [**all info**]("https://help.ubuntu.com/community/PlayMusicFromCommandLine?highlight=%28%5CbCategoryCommandLine%5Cb%29")


**PS 3   **sample[ ]("http://dotfiles.org/~chillu/.moc/config")[config sample 1]("http://dotfiles.org/~chillu/.moc/config")  [sample 2]("http://fullcirclemagazine.org/moc-config/")

---

### Post by FakeOutdoorsman on 2012-07-28
*moc* is also my player of choice. The first thing I do is copy the example moc config file to my home directory:

```
mkdir ~/.moc
cp -n /usr/share/doc/moc/config.example ~/.moc/config
```

It has a bunch of commented out examples and explains various settings. The next thing I do is change from the ugly default theme to something less ugly by changing *Theme* in config (as you've already mentioned).

You can set your main music directory (or playlist) in the moc config file (with *MusicDir*). moc will then always start in the directory, and using "m" key will then quickly return to the music directory if you navigate away from it. If you want more than one hot-keyed directory then set *Fastdir1*, *Fastdir2*, etc., in config.

Sometimes I'll use it to play music that is on another computer through *sshfs*:
```
mkdir remotemusic
sshfs username@192.168.1.168:music remotemusic
mocp
```
Then navigate to 'remotemusic' in *mocp*.

Only problem is that it crashes randomly on my graybeard of a hand-me-down laptop, but I tend to use *ffplay* on that machine instead.

---

### Post by shantiq on 2012-07-29
Thanx nice evolved tricks and tips FakeO for the more advanced user:KS

absolute corker of a player;  not used anything else for the last 3 days

the navigation is simply a DREAM

Other players do not go to hidden folders mostly; this one does   and you can add all you want to your playlist

with "a" key; then tab and move from playlist to files and back and add more


then save playlist  ```
ctrl+v
```

---

### Post by kevinmchapman on 2012-07-29
I have to endorse the comments here. moc is one of the best examples of a terminal application. It really is incredibly easy to use, but still gives a huge amount of functionality.

---

### Post by Aikifuku on 2012-08-14
I love moc as well. Just what I was looking for to free me from yet another GUI. However,...

When I try to reduce the volume below 16% the player just mutes itself. This is a problem while I'm working and listening to music with headphones. If I'm using RhythmBox the music can be played much quieter. 

Anyone know a fix to this?

---

### Post by shantiq on 2012-08-14
> **Aikifuku said:**
> 

When I try to reduce the volume below 16% the player just mutes itself. This is a problem while I'm working and listening to music with headphones. If I'm using RhythmBox the music can be played much quieter. 

Anyone know a fix to this?



Aikifuku this here is the way to control sound

very precisely in moc

[ATTACH]222707[/ATTACH]



so use the comma to go down and dot to go up once moc is running

---

### Post by Aikifuku on 2012-08-15
Thanks Shantiq. However, I think you misunderstood my problem. I can reduce the stated volume on moc from 16% to 15% using the "<" key. On my computer moc is muted when it has a stated volume of <15% though. So I cannot get the audio as quiet as I want. 

I was thinking there may be a way to specify the sound level that the player mutes at.

---

### Post by shantiq on 2012-08-15
yes was not sure exactly what you meant:KS  it modifies the master volume

on my system that means mute/silent way before 15%

sorry no other thoughts:KS

---

### Post by Aikifuku on 2012-08-15
Solved the problem if anyone is interested. 

What fixed this for me is to eliminate pulseaudio from my ubuntu install and make alsa my default audio mixer. A good HOW-TO on that is found here 

[http://howto.blbosti.com/2010/04/ubuntu-make-alsa-default-instead-of-pulseaudio/](http://howto.blbosti.com/2010/04/ubuntu-make-alsa-default-instead-of-pulseaudio/)

I also had to change the ~/.moc/config file to make sure ALSA was the sound driver that was loading. That was done by making sure this line was in the file (order matters),

SoundDriver = ALSA, JACK, OSS

---

### Post by shantiq on 2013-07-11
if anyone ever wondered about global hotkeys

mocp --help yields the answer


> mocp -G     pause/play
mocp -f      next
mocp -r      previous


personally using those through ccsm; no doubt many other routes


** on lxde**   [light desktop environment]


do this

```
 gedit    ~/.config/openbox/lxde-rc.xml
```


and add   between   <keyboard>    and </keyboard>

```
<!-- Keybindings for mocp play/pause -->
  <keybind key="A-m"><action name="Execute"><command>mocp -G</command></action></keybind>

<!-- Keybindings for mocp previous -->
  <keybind key="A-C-r"><action name="Execute"><command>mocp -r </command></action></keybind>

<!-- Keybindings for mocp next -->
  <keybind key="A-C-f"><action name="Execute"><command>mocp -f </command></action></keybind>
```

---

### Post by FakeOutdoorsman on 2013-07-11
I use the moc global hotkeys with my windows environment, Openbox:

~/.config/openbox/rc.xml:
```
<keybind key="W-space">
  <action name="Execute">
    <execute>mocp -G</execute>
  </action>
</keybind>
```

Also for controlling system audio with the keyboard (much faster for me than a point-and-click volume control):
```
<keybind key="W-1">
  <action name="Execute">
    <execute>amixer -q set Master 1+ unmute</execute>
  </action>
</keybind>
<keybind key="W-2">
  <action name="Execute">
    <execute>amixer -q set Master 1- unmute</execute>
  </action>
</keybind>
```

The "W" is the Windoughs key.

---

### Post by shantiq on 2013-07-12
thanx for that FakeOM




another area with moc is color and customization and gathering info from here and there it becomes quite easy to do




```
shift+T
```   shows all the themes available   pick one and enter




they are situated in /usr/share/moc/themes/ and can therefore be easily edited with say


```
sudo gedit /usr/share/moc/themes/nameofthemeyouwanttotweak

```



personally wanted bold writing and different colours on the transparent theme so did this ...
added bleu blanc rouge on the time monitors to make it look like a French flag ::}}




```
# Transparent background theme tweaked by Shan


background         = default        default 
frame                 = cyan           default  bold
window_title       = cyan           default  bold
directory        = white              default     bold
selected_directory    = cyan        blue     bold
playlist        = cyan        cyan     bold
selected_playlist    = cyan        blue    
file            = cyan        default  bold
selected_file        = cyan        cyan     bold
marked_file        = cyan        default     bold
marked_selected_file    = cyan        blue     bold
info            = blue        default    
status            = cyan        default 
title            = cyan        default    
state            = cyan        default    
current_time        = blue         default    bold
time_left        = white        default    bold
total_time        = red        default    bold
time_total_frames    = cyan        default 
sound_parameters    = cyan        default    bold
legend            = cyan        default 
disabled        = blue        default    
enabled            = cyan        default    
empty_mixer_bar        = cyan        default 
filled_mixer_bar    = black        cyan     
empty_time_bar        = cyan        default 
filled_time_bar        = black        cyan    
entry            = cyan        default 
entry_title        = black        cyan     
error            = red        default    
message            = cyan        default    
plist_time        = cyan        default    

```




and got


[[IMG]http://s20.postimg.org/yx9rvfjx5/MOC_play.jpg[/IMG]]("http://postimg.org/image/yx9rvfjx5/")  [[IMG]http://s20.postimg.org/3rou70ec9/MOC_play_4_CAN_Bel_Air_Future_Days_001.jpg[/IMG]]("http://postimg.org/image/3rou70ec9/")



then to **make it permanent** once you have the design YOU wish for


1. create a config file in .moc folder   


```
gedit .moc/config

```

and enter Theme = /usr/share/moc/themes/nameofthethemeyouwantasdefaultwhenstartingprogram   then save




Now you have your own design change colours and bold

choices are


Black
Red
Green
Yellow
Blue
Magenta
White
Cyan


you can also use "bold"  and "reverse" and modify the look that way too


Finding the reverse option allowed for a nifty Italian Tricolour


[[IMG]http://img23.imageshack.us/img23/5609/jg7m.th.png[/IMG]]("http://img23.imageshack.us/img23/5609/jg7m.png")


which i got this way


> # Transparent background theme tweaked by Shan [Italian flag]

background        = default        default   
frame            = white        default  bold
window_title        = white        default  bold
directory        = green        default     bold
selected_directory    = white        green     bold
playlist        = white    white     bold
selected_playlist    = white        white    
file            = white        default  bold
selected_file        = green        green     bold
marked_file        = white        default     bold
marked_selected_file    = white        green     bold
info            = cyan        default    
status            = white        default 
title            = white        default    
state            = white        default    
current_time        = green      default    reverse
time_left        = white        default    reverse
total_time        = red        default    reverse
time_total_frames    = white        default 
sound_parameters    = white        default    bold
legend            = white        default 
disabled        = green        default    
enabled            = white        default    
empty_mixer_bar        = white        default 
filled_mixer_bar    = black        white     
empty_time_bar        = white        default 
filled_time_bar        = black        blue    
entry            = white        default 
entry_title        = black        white     
error            = red        default    
message            = white        default    
plist_time        = white        default    





2 great forum pages from Crunchbang guys with options discussed

**[1 ]("http://crunchbang.org/forums/viewtopic.php?id=7596")   [2]("http://crunchbang.org/forums/viewtopic.php?id=15634")**












Good additional info    


[http://v1.corenominal.org/howto-setup-moc-music-on-console/](http://v1.corenominal.org/howto-setup-moc-music-on-console/)


================


PS also add line

```
 Allow24bitOutput = yes
```

to the config file if you wish for 24-bit to play as 24-bit  ...    default plays at 16-bit

also useful

```

SavePlaylist = yes
ShowFormat = yes
Repeat =yes
ShowHiddenFiles =yes
```

**if any of you know of further useful tweakings to the config please say.     thanx**

---

