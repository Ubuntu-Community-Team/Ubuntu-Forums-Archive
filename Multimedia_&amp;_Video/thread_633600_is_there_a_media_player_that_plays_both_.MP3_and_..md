---
title: "is there a media player that plays both .MP3 and .wma?"
date: 2007-12-06
forum: Multimedia &amp; Video
---

### Post by USFMD82 on 2007-12-06
OK I finally got .MP3s to work (Rhythmbox) by going to Terminal and typing
[PHP]sudo apt-get install gstreamer0.8-plugins[/PHP]

But after a bit of trouble with that I realize that it only plays MP3's I would like a media player that will play both MP3 and WMA's so I can listne to my whole library of songs without switching between Mplayer and Rhythmbox, and it would be cool if I could keep the album art feature too Thanks in advance for the hlp if anyone knows how to help!

---

### Post by disturbedite on 2007-12-06
all players do, its simply a matter of having the right libraries installed.

try audacious.

---

### Post by rainwalker on 2007-12-06
VLC will play just about anything

---

### Post by USFMD82 on 2007-12-13
Sorry guys, im really new to this.. what is VLC?

Also, how do I find the libraries to play .wma for rhythymbox is that inside rhythymbox somewhere or do I go to terminal or synaptic?

sorry for my noobishness, im still trying to catch on.

---

### Post by rainwalker on 2007-12-13
VLC is just the name of the media player. VideoLan Client (the name doesn't make sense to me, so don't worry if you don't get it). All I know is that if you tell it to play a file, I can almost guarantee it will play it.
I don't know about Rhythmbox, though; I don't use it
To install VLC, go System > Administration > Synaptic Package Manager
Search for "vlc" and install the package. VLC will be put in Accessories > Sound & Video

There's no noobishness on these forums, only people who need help. Don't be sorry for anything

---

### Post by Melcar on 2007-12-14
Do a search fo "gstreamer" in Synaptic and install all the available plugins.  Or you can simply install "ubuntu-restricted-extras".

---

### Post by USFMD82 on 2007-12-14
Thanks for the kind words Rainwalker. with VLC will it also display the album art? and have a library for my songs, as well, I just started getting into some podcasts and internet radio too.. am I good there too? ill read yoru reply and then check it out.

Melcar, I also was going to say I did download gstreamer a search on gstreamer in synaptic returns like no joke 13 results, is there a specific one I get? I typed in the command at the terminal screen so that I could finally get rhythymbox to play .mp3s

---

### Post by Melcar on 2007-12-14
> **USFMD82 said:**
> Thanks for the kind words Rainwalker. with VLC will it also display the album art? and have a library for my songs, as well, I just started getting into some podcasts and internet radio too.. am I good there too? ill read yoru reply and then check it out.

Melcar, I also was going to say I did download gstreamer a search on gstreamer in synaptic returns like no joke 13 results, is there a specific one I get? I typed in the command at the terminal screen so that I could finally get rhythymbox to play .mp3s


I think the "ugly" plugins allow you to play mp3.  I just install the whole restricted extras package.

---

### Post by USFMD82 on 2008-02-14
So trying other players I just really like the layout of Rhythymbox, but I still find that I am unable to play .wma files in rhythymbox, among others, its seems only able to play .mp3.. I also noticed that no program plays .mpeg

Any ideas what I need to D/L to get rhythymbox running .wma files?

---

### Post by rainwalker on 2008-02-14
VLC is just a media player; if you want something to manage your entire music library I have to recommend Amarok. It's a KDE app, but (pardon my language) it kicks major ***. You can install it through Synaptic

Also, go to Applications > Add/Remove, and in that window click the "Preferences" button down in the bottom left. Enable the Restriced and Multiverse repositories, then search in Add/Remove for "ubuntu restricted extras" and install it. That has a lot of the codecs you'll need, as well as Java and Flash.

---

