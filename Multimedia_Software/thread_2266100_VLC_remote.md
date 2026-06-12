---
title: "VLC remote"
date: 2015-02-19
forum: Multimedia Software
---

### Post by steve188 on 2015-02-19
I am very new to Ubuntu and i tried to install vlc remote and it didnt work so I want to go back to when I didnt try it. Now I cant get it to open up. I have read some of the older post but the newest one I have found is from 2010. I have un installed and reinstalled and have had no changes yet. this is what I get when I put vlc in the terminal. 
VLC media player 2.1.4 Rincewind (revision 2.1.4-0-g2a072be)
[0x1c90958] [http] lua interface: Lua HTTP interface
[0x1c90958] [http] main interface error: socket bind error (Permission denied)
[0x1c90958] [http] main interface error: socket bind error (Permission denied)
[0x1c90958] [http] main interface error: cannot create socket(s) for HTTP host
[0x1c90958] [http] lua interface error: Error loading script /usr/lib/vlc/lua/intf/http.luac: lua/intf/http.lua:328: Failed to create HTTP host


I am running ubuntu 14.04 LTS if that helps

update now I can use 
mv $HOME/.config/vlc/vlcrc $HOME/.config/vlc/vlcrc_bak
and it will run in interface but not on its own ?????

---

