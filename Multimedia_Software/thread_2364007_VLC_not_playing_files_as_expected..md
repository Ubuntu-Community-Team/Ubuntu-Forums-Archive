---
title: "VLC not playing files as expected."
date: 2017-06-17
forum: Multimedia Software
---

### Post by shag00 on 2017-06-17
I have Ubuntu 16.04 and VLC 2.2.2 and VLC will play all my files when selected through it's menu but won't play any file if I browse through FILES and select a movie/song even though I get the right click - Open with VLC media player. Nothing happens at all, no message, no nothing. This is true for both normal and root user (gksudo).

Am I missing something really simple in some setup somewhere?

---

### Post by mc4man on 2017-06-17
Probably something you did, may be hard to troubleshoot.
I guess for starters try removing vlc  as such
```
sudo apt purge vlc-data
```
Then look & see if there is still a vlc context menu item, also see if there is an errant vlc about ( run vlc command in terminal.

If none of the above then re-install vlc 
```
sudo apt install vlc
```
Before re-trying vlc delete the ~/.config/vlc folder

---

### Post by shag00 on 2017-06-17
Re instal seems to have been the ticket.

---

