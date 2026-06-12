---
title: "Reset KDenLive settings"
date: 2018-05-02
forum: Multimedia Software
---

### Post by kazakore on 2018-05-02
Just installed Ubuntu Studio 18.04 on a new SSD, going through my configurations to get everything looking and feeling as I like, got to configuring KDenLive to look how I want (dark theme) and going through the visible settings and very quickly it got a point where the menus were pure black with no visible text at all!

I tried to guess the menu location for the theme etc and have now clicked on a menu item that closes the entire top menu so I can't even access it for blind clicking around now!

So I tried a apt-get purge/install kdenlive hoping this would reset all settings but it has not done so.
I've tried deleting the contents of /home/userisme/.local/share/kdenlive/ and the unusable settings remain.

How can I reset Kdenlive to default settings? And please can somebody try and make this program so you can't break it into an unusable condition like this! (I know that's not for people on this forum ,just a mild rant to the ether...)

---

### Post by howefield on 2018-05-02
After purging kdenlive you'll likely be left with kdenlive folders in ~/cache and ~/.local/share.. delete those manually.

---

### Post by kazakore on 2018-05-02
> **howefield said:**
> After purging kdenlive you'll likely be left with kdenlive folders in ~/cache and ~/.local/share.. delete those manually.

I'd got the local/share folder initially but missed the cache one. Just tried with deleting both after doing a purge and then install but the problem still persists! No menu visible in KDenLive. Workarounds like Alt+F to get to the File menu and then navigate don't do anything. Even if they did the menu colour was black on black so it wouldn't be possible to change the settings knowingly anyway!

It can't be that hard to reset the settings surely. How come Purging the program then removing all related user data doesn't even seem to do it?!

---

### Post by kazakore on 2018-05-08
Solved.

Had to delete file:
~/.config/kdenliverc

I knew it would be simple but easily missed.

---

### Post by Timmoore001 on 2018-05-16
At last !  Kdenlive user !     I'm a newbie on video editing and wondered if there was a simple sample file/project I could load to get the ball rolling.

I'm only just starting so looking for some very simple instructions .  I have just download KdenLive and it seems to work ok..  but I don't know how to put a Project together. 

And thoughts very very welcome....

Tim

---

### Post by kazakore on 2018-05-16
> **Timmoore001 said:**
> At last !  Kdenlive user !     I'm a newbie on video editing and wondered if there was a simple sample file/project I could load to get the ball rolling.

I'm only just starting so looking for some very simple instructions .  I have just download KdenLive and it seems to work ok..  but I don't know how to put a Project together. 

And thoughts very very welcome....

Tim


I'm afraid I've only used it very sporadically, but out of the programs I've tested it seemed the most complete of the video editors on Ubuntu (worth adding their own ppa, at least in 16.04 the feature set difference between the version provided by Ubuntu and by them was huge!!)

They have their own forum on the KDE website and this is the best place to get help. It's where I eventually got my answer to the issue here.

[https://forum.kde.org/viewforum.php?f=265](https://forum.kde.org/viewforum.php?f=265)

Or their own website has lots of information!

[https://kdenlive.org/](https://kdenlive.org/)

Maybe check their tutorials

[https://kdenlive.org/en/category/tutorials/](https://kdenlive.org/en/category/tutorials/)
[https://userbase.kde.org/Kdenlive/Manual/Tutorials](https://userbase.kde.org/Kdenlive/Manual/Tutorials)

Or search Youtube etc for some to watch......

---

### Post by Timmoore001 on 2018-05-18
Many many thanks for responding.

I will l follow your suggestions.

As always its just getting started can be a struggle !

Thanks again

:  ))

Tim

---

