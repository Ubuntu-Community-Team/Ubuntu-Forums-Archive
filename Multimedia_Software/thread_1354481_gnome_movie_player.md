---
title: "gnome movie player"
date: 2009-12-13
forum: Multimedia Software
---

### Post by wolverine48456 on 2009-12-13
I'm having trouble playing dvd on ubuntu 10.9 here is what I get:
gnome movie player is what I have.

 No URI Handler implemented for 'dvd'  what do I need to do to be able 
to play dvd.

---

### Post by mc4man on 2009-12-14
Open a terminal and run
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```

and
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

some extra plugins, may or not be useful for your purposes ( blue is only for 32 bit install and W32codecs from [medibuntu]("http://packages.medibuntu.org/")

```
sudo apt-get install gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly-multiverse [COLOR="Blue"]gstreamer0.10-pitfdll[/COLOR]
```

---

### Post by wolverine48456 on 2009-12-14
i'm not very familiar with ubuntu  please explain what I need to do.

---

### Post by wolverine48456 on 2009-12-14
i'm not very familiar with ubuntu  please explain what I need to do.



I got it working  thanks a lot

---

### Post by wolverine48456 on 2009-12-14
I replied too fast, now I have no sound

---

### Post by wojox on 2009-12-14
Double check System > Preferences > Sound. It may of muted the Output volume.

---

### Post by wolverine48456 on 2009-12-14
all mute boxes I found are unchecked



can I make VLC media player my default player,if so  how?

---

### Post by mc4man on 2009-12-14
> now I have no sound 

In your upper panel is a little speaker icon. click on it and in the dropdown slider - move it and ck. again.

Otherwise a few simple things

If by gnome movie player you meant Totem Movie Player then in a terminal
```
gstreamer-properties
```
Try pulseaudio rather than 'default' - screen 1

If you meant gnome-mplayer then open it up -> edit -> prefereces - screen 2
> 
can I make VLC media player my default player,if so how? 

Several ways - 
Put your media in drive and hold down the shift button, you'll get a popup, choose vlc.
or
run this in a terminal and ck. under the media tab
```
nautilus-file-management-properties
```
or
run this in a terminal and under System -> Preferences enable 'file management, you'll then find it in your System -> Preferences menu

```
alacarte
```

In karmic pulseaudio should usually be set as audio output
vlc -> tools -> preferences, click on audio tab, look in the 'output' dropdown
vlc-plugin-pulse has to be installed

---

### Post by wolverine48456 on 2009-12-14
Now I got sound working  thanks a million  :)

---

