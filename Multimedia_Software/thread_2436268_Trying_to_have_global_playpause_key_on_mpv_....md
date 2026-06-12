---
title: "Trying to have global playpause key on mpv ..."
date: 2020-02-03
forum: Multimedia Software
---

### Post by shantiq on 2020-02-03
... and not getting there as yet

if the player is visible on desktop the "p" key will do that but i want this as a global key

as I have in all my other players xmms / moc / winamp / foobar and all flawlessly recorded in ~/.config/openbox/lxde-rc.xml  . I use LXDE as DE.

mpv seems to be rigged up differently

ANY ideas?

thanx shan


```

<keyboard>
#xmms


    <keybind key="A-x">
      <action name="Execute">
          <command>xmms -t</command>
          </action>
    </keybind>


#moc

<!-- Keybindings for mocp play/pause -->
  <keybind key="A-m"><action name="Execute"><command>mocp -G</command></action></keybind>


<!-- Keybindings for mocp previous -->
  <keybind key="A-C-r"><action name="Execute"><command>mocp -r </command></action></keybind>


<!-- Keybindings for mocp next -->
  <keybind key="A-C-f"><action name="Execute"><command>mocp -f </command></action></keybind>
  


  
[COLOR=#800000]#mpv playpause[/COLOR]
[COLOR=#800000]
[/COLOR]
[COLOR=#800000]  <keybind key="A-z">[/COLOR]
[COLOR=#800000]      <action name="Execute">[/COLOR]
[COLOR=#800000]          <command>"mpv --pause"[/COLOR]
[COLOR=#800000]          </command></action>[/COLOR]
[COLOR=#800000]    </keybind>[/COLOR]




  
  
#winamp 


  <keybind key="A-b">
      <action name="Execute">
          <command>wine ~/.wine/dosdevices/c:/"Program Files (x86)"/Winamp/CLEveR.exe playpause</command></action>
    </keybind>
    
  <keybind key="C-7">
      <action name="Execute">
          <command>wine ~/.wine/dosdevices/c:/"Program Files (x86)"/Winamp/CLEveR.exe voldn</command></action>
    </keybind>   
    
  <keybind key="C-8">
      <action name="Execute">
          <command>wine ~/.wine/dosdevices/c:/"Program Files (x86)"/Winamp/CLEveR.exe volup</command></action>
    </keybind>      


#foobar


<keybind key="A-f"><action name="Execute"><command>wine ~/.wine/dosdevices/c:/"Program Files (x86)"/foobar2000/foobar2000.exe /playpause</command></action></keybind>


<keybind key="C-0"><action name="Execute"><command>wine /home/shan/.wine/dosdevices/c:/"Program Files (x86)"/foobar2000/foobar2000.exe /command:Up</command></action></keybind>


<keybind key="C-9"><action name="Execute"><command>wine /home/shan/.wine/dosdevices/c:/"Program Files (x86)"/foobar2000/foobar2000.exe /command:Down</command></action></keybind>

</keyboard>
```

---

### Post by SeijiSensei on 2020-02-03
I'm not sure I understand the question. I've always used the space bar to start and pause playback in mpv and its predecessor mplayer.  Works with mpv with SMPlayer as the front-end, too. The man page for mpv shows "p" and the space bar as synonyms.

I use SMPlayer and have it configured to pause playback when the application is minimized. If I use mpv alone from the command prompt, the video continues to play when minimized, but if I hit the space bar in the window that spawned mpv, the playback is paused. If the focus is in any other window, the keystroke is ignored, and playback continues. Are you looking for a keystroke sequence that works in this case?

---

### Post by mc4man on 2020-02-04
What you're doing clearly won't work, the command mpv --pause does nothing without mpv being opened on a file to pause on
mpv  /path/to/file --pause

Now there could be ways, possibly a lua script if 'window unfocused' is a property that can be observed
(there is a lua script provided with most mpv packages that does 'pause when minimize' (/usr/share/doc/mpv/tools/lua
Or maybe some 3rd party app that could pass pause to the already open mpv window. 

There is a roundabout way though may have unintended consequences...

```
mkfifo /home/username/mpvfifo
```
Add line to .config/mpv/mpv.conf
```
input-file=/home/username/mpvfifo
```

Create an executable script in a bin folder in $PATH, lets say named cycle
```
#!/bin/bash
echo 'cycle pause' > /home/username/mpvfifo
```

Bind a system key with command of cycle
(- here in Ubuntu you can't bind a single key in keyboard > shortcuts > custom, so tested with ctrl+a, works fine on a foused or unfocused mpv window.

Location of mpvfifo doesn't matter, 1st tried /tmp but that is removed on reboot..
If you use mkfifo /tmp/mpvfifo then the fifo will be removed when rebooting. Then recreate by using the simple  mkfifo /tmp/mpvfifo command on session start. 

Note: you can use both the pause with minimize lua script with above fifo, min. > paused, ctrl+a starts while keeping minimized, ect.
You can have more than 1 fifo, just use different names, ex.  mkfifo /home/doug/mpvfifo1

There's a warning, Warning: option --input-file is deprecated and might be removed in the future (use --input-ipc-server).
(- that method unclear to me atm..

---

### Post by shantiq on 2020-02-04
thanx a lot mc4man will give it a whirl and report

---

### Post by shantiq on 2020-02-07
ok mc4man  I tried to follow instructions but there is confusion for me on some points

this is what i did

&#10122; ```
[COLOR=#000000][FONT=&amp]mkfifo /home/shan/mpvfifo

[/FONT][/COLOR]
```
&#10123; added [COLOR=#000000]line to .config/mpv/mpv.conf[/COLOR]
[COLOR=#000000]Code:
```
input-file=/home/shan/mpvfifo
```[/COLOR]
&#10124;  created  placed in home folder and made executable 
```
#!/bin/bash
echo 'cycle pause' > /home/shan/mpvfifo
```
&#10125; opened sudo leafpad ~/.config/openbox/lxde-rc.xml  [i am in LXDE] 
and added 
```
#mpv playpause

  <keybind key="A-z">
      <action name="Execute">
          <command>"'cycle pause'"
          </command></action>
    </keybind>



```

and refreshed ```
openbox --reconfigure && lxpanelctl restart
```

&#10126;  when i press A-z still getting     [ATTACH=CONFIG]284980[/ATTACH]


So no doubt misunderstood or placed items in wrong places

Thank you for your help with this
Mpv is still the best and it will be nice to have Global Key Command sorted too

---

### Post by mc4man on 2020-02-07
> **shantiq said:**
> ok mc4man  I tried to follow instructions but there is confusion for me on some points

this is what i did

&#10122; ```
[COLOR=#000000][FONT=&amp]mkfifo /home/shan/mpvfifo

[/FONT][/COLOR]
```
&#10123; added [COLOR=#000000]line to .config/mpv/mpv.conf[/COLOR]
[COLOR=#000000]Code:
```
input-file=/home/shan/mpvfifo
```[/COLOR]
The above(#1 &#2) is correct but after you're veering off, 1st. a little, then a lot..

> **shantiq said:**
> 
&#10124;  created  placed in home folder and made executable 
```
#!/bin/bash
echo 'cycle pause' > /home/shan/mpvfifo
```
This is correct though script is best placed in ~/bin. If not then your **binding command needs to full path to the script**.

> **shantiq said:**
> 
&#10125; opened sudo leafpad ~/.config/openbox/lxde-rc.xml  [i am in LXDE] 
and added 
```
#mpv playpause

  <keybind key="A-z">
      <action name="Execute">
          <command>"'cycle pause'"
          </command></action>
    </keybind>



```
#4 is wrong. You want to bind to the script, not mpv. Think of it this way - 
When the binding calls the script it sends "cycle pause" to the fifo, mpv is 'monitoring' the fifo so it receives the command and reacts. 

So the **binding command is the scriptname** if in a bin folder or** full path to the scriptname **if just loose in home folder, i.e /home/shan/scriptname

---

### Post by shantiq on 2020-02-08
yet again feeling admirative grateful and humbled  ...   and that is a good thing mc4man :mad: thanks for original explanation and clarification
PS:    funny that in such a sophisticated deep-level player that no thought has been given to easy Global Hotkeys
xmms / moc / winamp / foobar all fairly easy even winamp requiring CLEveR.exe 
Audacious can be set from the GUI


&#10122;   moved cycle script so now in :  /home/shan/bin/cycle
&#10123;  changed key to:

```
#mpv playpause

  <keybind key="A-z">
      <action name="Execute">
          <command>"/home/shan/bin/cycle"
          </command></action>
    </keybind>
```



and perfect and incredibly quick puter response ...so thanx
Could create cycle 1 cycle2 for other commands but fine for now


========

Now I can sit back feet away from my computer with a small keyboard ... punch "Alt-z" and have my beloved mpv on remote control   QED and play a mixture of YT videos audio and hard drive files ...   

```
[COLOR=#800000]*mpv --no-video --no-resume-playback --loop-playlist  alfred\ panou\ AEC.m3u*[/COLOR]
Warning: option --input-file is deprecated and might be removed in the future (use --input-ipc-server).

Playing: https://www.youtube.com/watch?v=UvnsbqZthFU  #AEC Reese and the Smooth Ones, Pt. 1
 (+) Audio --aid=1 --alang=eng (*) (opus 2ch 48000Hz)
AO: [pulse] 48000Hz stereo 2ch float
Title: Reese and the Smooth Ones, Pt. 1
A: 00:00:02 / 00:19:57 (0%) Cache: 34s/1MB

Playing: /home/shan/Music/Elissa - Ila Kol Elli Bihebbouni [2018]/kol.cue
     Video --vid=1 [P] (png 1600x1456)
 (+) Audio --aid=1 (flac 2ch 48000Hz)
File tags:
 Artist: Elissa
 Album: Ila Kol Elli Bihebbouni
 Date: 2018
 Genre: Lebanese Pop
Title: kol.cue
A: 00:00:15 / 01:13:24 (0%)

Playing: https://www.youtube.com/playlist?list=PLWMfoGAL4WggNmEjvB5hBohvbV7sJXtIr # Catherine Derain
A: 00:00:15 / 01:13:24 (0%)

Playing: https://youtu.be/HhlRuFOZ_os
A: 00:00:15 / 01:13:24 (0%)
 (+) Audio --aid=1 --alang=eng (*) (opus 2ch 48000Hz)
Title: Être femme en son temps
(Paused) A: 00:00:02 / 00:02:32 (1%) Cache: 149s/6MB


```

---

### Post by mc4man on 2020-02-09
> There's a warning, Warning: option --input-file is deprecated and might be removed in the future (use --input-ipc-server).
(- that method unclear to me atm.. 
So at some point they'll likely remove the --input-file option. The now preferred is pretty straightforward.
Typical usage would be to open a fresh terminal & send command(s) to open mpv instance but for this use (a binding), a script is way to go like before.

To do: 
This uses  socat so 1st.
```
sudo apt install socat
```

Then add this line to .config/mpv/mpv.conf, remove input-file= line if there.
```
input-ipc-server=/tmp/mpvsocket
```

Create an executable  script in $PATH (like ~/bin)
```
#!/bin/bash
echo '{"command": ["cycle", "pause"]}' | socat - /tmp/mpvsocket
```

Then create a binding to either scriptname or /path/to/scriptname.

---

### Post by shantiq on 2020-02-10
Thanx mc4 updated
means the pesky message disappears



very neat  ...   had read around [socat]("https://stackoverflow.com/questions/35013075/pause-programmatically-video-player-mpv") but could not make  sense of it   ... 


now >>
```
 mpv --no-video --no-resume-playback --loop-playlist  alfred\ panou\ AEC.m3u

Playing: https://www.youtube.com/watch?v=1Mp8yqVDAXo #Smiling Faces Sometimes - The Undisputed Truth
 (+) Audio --aid=1 --alang=eng (*) (opus 2ch 48000Hz)
AO: [pulse] 48000Hz stereo 2ch float
Title: The Undisputed Truth - Smiling Faces Sometimes (HD)
(Paused) A: 00:00:02 / 00:03:15 (1%) Cache: 191s/7MB


```


EDIT:   there is a kink tho with [COLOR=#000000][FONT=&amp]input-ipc-server=/tmp/mpvsocket   so for the time being i reverted to [/FONT][/COLOR]input-file=/home/YOURNAME/mpvfifo

[COLOR=#000000][I]Route 1 mpvfifo allows for one instance of mpv to be paused start other instance in a different tab or terminal window say for a film ; exit that then unpause the earlier mpv instance

Route 2 socat fails to do that; ie it switches to most recent then "forgets" earlier instance

So mpvfifo trumps socat so far

Since I do not understand what happens behind the scenes here I simply explain it as a user and mpvfifo route works better therefore
Hope this is explained well enough; I do not think I am mistaken here [/I][/COLOR]:KS[COLOR=#000000]PS:  also it seems reaction time on [/COLOR]*mpvfifo route even faster : Instant*[COLOR=#000000]


shan
[/COLOR]

---

### Post by shantiq on 2020-04-29
Now socat the only route :mad:   and yes it definitely remembers only ONE instance of mpv running ...   but that is fine

---

### Post by mc4man on 2020-04-29
> **shantiq said:**
> Now socat the only route :mad:   and yes it definitely remembers only ONE instance of mpv running ...   but that is fine
Yeah, it only works with last opened instance.
There's a lua script that allows a per instance socket but unsuitable for this use, it creates  sockets named after the instance pid so only useful for cli usages.

If you eventually find onerous one can pretty simply create multiple mpv binaries with different run names, i.e mpv, mpv2, ect..
Then you could have additional one  prior to commit change, or 0.32 release.
The --config-dir=<path> option allows a separate mpv.conf

---

