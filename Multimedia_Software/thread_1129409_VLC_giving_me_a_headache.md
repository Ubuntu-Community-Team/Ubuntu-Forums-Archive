---
title: "VLC giving me a headache"
date: 2009-04-18
forum: Multimedia Software
---

### Post by king EZi on 2009-04-18
I recently installed VLC on my ubuntu 8.10 and i loved it...problem is when i tried installing skins, i copied the file in a folder and went to the player's menu and selected the folder...nothing happened. After i closed it and opened i started getting "double" players opening with same skin and when i close one they all close...tried a different account on the same machine and it works fine, please help!!!! Is it something to do with my /home folder?? is there some configurations i need to make???

---

### Post by WatchingThePain on 2009-04-18
> Preferences > Advanced > Check "allow only one running instance" > Save > Close vlc.

---

### Post by king EZi on 2009-04-18
> **WatchingThePain said:**
> > Preferences > Advanced > Check "allow only one running instance" > Save > Close vlc.

Sorry i cant get to the menu, the skin that loads doesnt enable me to. Is there a way i can do that on shell?? Thanks for the response

---

### Post by mc4man on 2009-04-18
If you want to fool around with different skins in vlc 0.9.x then you should know this command

```
vlc --reset-config
```
Then when it screws up you can reset to orig. config and try again

---

### Post by king EZi on 2009-04-18
> **mc4man said:**
> If you want to fool around with different skins in vlc 0.9.x then you should know this command

```
vlc --reset-config
```
Then when it screws up you can reset to orig. config and try again

It works, Thanks dude....

---

