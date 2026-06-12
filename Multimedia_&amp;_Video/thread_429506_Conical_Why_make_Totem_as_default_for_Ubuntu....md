---
title: "Conical: Why make Totem as default for Ubuntu..."
date: 2007-05-01
forum: Multimedia &amp; Video
---

### Post by tman_ubuntu on 2007-05-01
when it seems the most multimedia applications preferred by Ubuntu users is either VLC or mplayer?  I personally have been using Ubuntu since 4.10.  And with every version there after, I've uninstalled totem plugins, and installed either VLC or mplayer because Totem wouldn't work correctly or I would have to spend way too much time necessary to get media to play.

So Ubuntu community, here is my question for everyone.  Why doesn't Conical use VLC as the default media player when this one seems to be the one most of us use to rescue our desktops from media woes?

---

### Post by az on 2007-05-01
First off, *Canonical* is the company that underwrites Ubuntu, but it does ont take the decisions as to what software is included and how it is configured.  The Ubuntu community does that.  Specifically, the technical board decide matters like that.  Th emeet every month over IRC and have a mailing list.

Totem works fine for me.

Totem also uses gstreamer as a backend.  Gstreamer is a plugin-based, community driven media framework.  It makes a lot more sense to base a project on Gstreamer than to build both the frontend and the backend yourself.  Totem is a frontend to Gstreamer.

Totem is also the default media player for Gnome and it would make little sense to Ubuntu to use a different default than what gnome uses.

---

### Post by reclusivemonkey on 2007-05-03
AFAIK, Totem complies with the Gnome HIG, the other players do not; this is why Totem is the default media player in Gnome.

[http://developer.gnome.org/projects/gup/hig/](http://developer.gnome.org/projects/gup/hig/)

---

### Post by temcat on 2007-05-04
I thought the default media player should be the one that does its job best, not the one that is most compliant to the HIG. That is not something that can be said about Totem-gstreamer. It gives me only problems.

---

### Post by jso2897 on 2007-05-04
Question, for anybody who knows - is there a way to select different players as a default player? Such as Kaffeine, VLC, whatever?:confused:

---

### Post by LuisGMarine on 2007-05-04
Yes there is.  Please refer to the link below, download the plugin for firefox, and when you run it it gives you an entire list of all the web media format, along with choosing the default application to open them with.  Just try it, I promise you wont be diappointed.  

Totem works perfect here, even better than VLC!  I might not have VLC installed correctly or whatever, but all I know is that totem deff. beats VLC on sound quality.  My videos under VLC lack the sound, but in totem they are just perfect.  Anyhow, here is the link below.  

[Click Here!]("http://ubuntuforums.org/showthread.php?t=431942")

Good Luck

---

### Post by jso2897 on 2007-05-04
Actually, Totem does not work well for me, for either sound or video. I have Kaffeine installed and I love it, especially the sound quality. But I can only make it the default player for files I have previously played with it. If I open a file I have not previously played with Kaffeine, it opens with Totem. I would  like to make Kaffeine my default player, I just can't figure out how to do it.:confused:


Edit: I think I figured out what the problem was with Totem. There was an update that hadn't been applied, and after I applied it, Totem works perfect.

---

