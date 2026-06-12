---
title: "VLC wont open on newly installed LUbuntu"
date: 2018-08-31
forum: Multimedia Software
---

### Post by iamtheeggman2 on 2018-08-31
Hello everyone,

I'm new to this forum, I was using Fedora happily for several years however it has been problematic to use on my new graphics card.

The issues I have at the moment are VLC crashses without explanation when I go to play a video, the card I have is ASUS Radeon HD 4350 (512 MB) SILENT HDMI PCI Express Video Card

I understand given its an old card the system is using some open drivers rather than legacy ones, is there something I need to do? I don't play games or do any graphics intensive things.

I have only just installed Lubuntu, nothing beyond a standard installatin and it has gstreamer codecs installed. 

I can play videos on youtube ok however there were some weird graphics issues I noticed for example I had a picture viewer open and when the window was closed a white space was left behind rather than the rest of the systems windows to view.


Manjaro was installed on another partition and had the same issue in that it wouldnt play video? Curiously vlc itself wont even open, so I am not sure if this is just a codecs issue or something more systemic?


Any and all help welcome!

---

### Post by Perfect Storm on 2018-08-31
Moved to Multimedia Forum

---

### Post by iamtheeggman2 on 2018-08-31
Thanks for moving this to the correct section. 

Is there a way to see error messages or why it failed?

---

### Post by Perfect Storm on 2018-08-31
you could run
```
vlc
```

from the terminal.

---

### Post by iamtheeggman2 on 2018-08-31
house@house:~$ vlc
VLC media player 3.0.3 Vetinari (revision 3.0.3-1-0-gc2bb759264)
[01603bc0] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.

(vlc:5436): dbind-WARNING **: 16:07:57.533: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name org.a11y.Bus was not provided by any .service files
QApplication: invalid style override passed, ignoring it.

^CSegmentation fault (core dumped)
house@house:~$

---

### Post by Perfect Storm on 2018-08-31
Try:
```
vlc --help
```

then use vlc with some kind of debug flag, I don't have vlc so I can't help you further.

---

### Post by Yellow Pasque on 2018-08-31
How did you install it? Are you using the Snap version or the .deb package version? There seems to be some issues with the Snap version.
```
snap list
```

---

### Post by mc4man on 2018-09-01
You could try this,
Open .config/vlc/vlcrc in a text editor.
Search for this line,
```
#avcodec-hw=any
```
Change it to ```

avcodec-hw=none
```

See if vlc will now open..

---

### Post by iamtheeggman2 on 2018-09-01
> **Temüjin said:**
> How did you install it? Are you using the Snap version or the .deb package version? There seems to be some issues with the Snap version.
```
snap list
```

Straight out of software manager.

house@house:~$ snap list

Command 'snap' not found, but can be installed with:

sudo apt install snapd

house@house:~$

Before I waste time dl ubuntu can anyone clarify it would have exactly the same issue or not as lubuntu? I dl lubuntu to see if it would wrk better on my older light weight graphics card.

> **mc4man said:**
> You could try this,
Open .config/vlc/vlcrc in a text editor.
Search for this line,
```
#avcodec-hw=any
```
Change it to ```

avcodec-hw=none
```

See if vlc will now open..

Hi, thanks but there is no fie or folder called .config/vlc/vlcrc  ?

gnome mpv crashes too??

> **iamtheeggman2 said:**
> gnome mpv crashes too??


rWow I have got this working and all I did was untick enable prefeth metadata and untick enable mpris support, whatever that is! Although I doubt vlc has such options I will check!

---

