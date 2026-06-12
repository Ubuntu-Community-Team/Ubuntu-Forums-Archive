---
title: "Pianobar Config File - UNSOLVED"
date: 2011-08-02
forum: Multimedia Software
---

### Post by Hank_The_Dog on 2011-08-02
When editing pianobar I found the file '/usr/share/doc/pianobar/contrib/config-example'

Here is a copy of what it looks like

```
[I]# This is an example configuration file for pianobar. You may remove the # from
# lines you need and copy/move this file to ~/.config/pianobar/config
# See manpage for a description of the config keys
#
# User
#user = your@user.name
#password = password

# Proxy (for those who are not living in the USA)
#control_proxy = http://127.0.0.1:9090/

# Keybindings
#act_help = ?
#act_songlove = +
#act_songban = -
#act_stationaddmusic = a
#act_stationcreate = c
#act_stationdelete = d
#act_songexplain = e
#act_stationaddbygenre = g
#act_songinfo = i
#act_addshared = j
#act_songmove = m
#act_songnext = n
#act_songpause = p
#act_quit = q
#act_stationrename = r
#act_stationchange = s
#act_songtired = t
#act_upcoming = u
#act_stationselectquickmix = x

# Misc
# mp3, mp3-hifi or aacplus
#audio_format = mp3
#autostart_station = 123456
#event_command = /home/user/.config/pianobar/eventcmd
#sort = quickmix_10_name_az
[/I]

```

Here are my questions..


[LIST=1]
[*]Where **exactly** should I put the file, and what should I rename it?
[*]The reason I am doing this is to automate my login credentials so I don't have to type ***"reallylongemail@address.com" "MySup3RpassW0rdz"*** every time I want some tunes, maybe there is a better way?
[/LIST]


Regards

---

### Post by TheOneEyedMan on 2011-10-19
From your home directory
```
cd .config
mkdir pianobar
gedit config

```
When gedit opens put the following in the file:
```
password = <replace this including brackets with password in plain text>
user = <replace this including brackets with email address used as user name>
```
Save and exit. 
Try running pianobar, you should be all set.

---

### Post by meierbac on 2011-11-16
I agree with TheOneEyedMan. You should basically create a config directory for pianobar, then put the file "config" in that directory. So the entire path will be located at [FONT="Arial"]~[/FONT]/.config/pianobar/config. 

Also, you can comment and uncomment the rest of the commands as you like. You can even set new shortcuts.

---

