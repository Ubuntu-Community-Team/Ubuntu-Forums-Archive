---
title: "tor installation failed"
date: 2024-03-11
forum: Multimedia Software
---

### Post by henkchr on 2024-03-11
Tor instalation with Ubuntu 22.04.2 LTS fails in Ubuntu software center
 
 
 When trying to install Tor vwith the Torbrowser-lancher I see:  
 
 
 trying to download signature ( over tor)  
 
 
 And after that : Download error 404.  
 
 
 
 
 Is there something with a signature that needs to happen here ?  
 
 
 Hope to hear from you . Thank you.

---

### Post by yancek on 2024-03-11
You can get that error when the internet connection is bad or if connected to a server and the specific file can't be found.  Some other reasons you can find with an online search.  The link below has an  explanation at the Wikipedia site.  I'm using 20.04 and just installed Tor from the package manager without problems.  Have you waited and tried multiple times?

 [https://en.wikipedia.org/wiki/HTTP_404](https://en.wikipedia.org/wiki/HTTP_404)

---

### Post by henkchr on 2024-03-12
Thanks but nothing works. Mirror sides don´t work eigther.

---

### Post by #&amp;thj^% on 2024-03-12
I've seen this on 22.04 reported here in UF.
Would you please try:
```
sudo sed -i 's|self.language =.*|self.language = "ALL"|g' /usr/lib/python3/dist-packages/torbrowser_launcher/common.py
```
Now try and launch torbrowser.

It might not matter to you but it is also available as a flatpak 
```
flatpak list |grep torbrowser
Tor Project     org.torproject.torbrowser-launcher      0.3.7   stable  system

```
I prefer it.

---

### Post by henkchr on 2024-03-13
Tried your command in the shell first it looked good. Installing started but then every time a crash happend. I tried several times. 
I can´t mangage to add the crash report here because i made a picture of it and it seems not possible to copy it.

---

### Post by #&amp;thj^% on 2024-03-13
If you don't mind I have a question or two to ask.
1st. is tor really needed? And it might be at the heart of your current problem.
The flatpak version of torbrowser is now maintained through the "torproject team"
```
apt policy tor
tor:
  Installed: (none)
  Candidate: 0.4.8.10-1
  Version table:
     0.4.8.10-1build1 100
        100 http://archive.ubuntu.com/ubuntu noble-proposed/universe amd64 Packages
     0.4.8.10-1 500
        500 http://us.archive.ubuntu.com/ubuntu noble/universe amd64 Packages
```

2nd.Are you opposed to installing torbrowser as a flatpak?

---

### Post by henkchr on 2024-03-14
Thank you for your remarks. 
If i acually need tor is of course the question. 
I guess i have to try the flatpak version of it then. 
How do i install the flatpak version ? I assume it is in the software center of Ubuntu ?

---

### Post by henkchr on 2024-03-14
Okay, i installed flatpack and after this i managed to install tor browser on ubuntu based on the instruction for ubuntu. 
It is working fine. 
Thanks for your suggestion ! 
Hope on ubuntu 24.** release it will be working out of the box.

---

### Post by #&amp;thj^% on 2024-03-14
Nice, but i still don't know why you had problems with the .deb version on 22.04, but to answer your query for 24.04
```
apt policy torbrowser-launcher && flatpak list
torbrowser-launcher:
  Installed: 0.3.7-1
  Candidate: 0.3.7-1
  Version table:
 *** 0.3.7-1 500
        500 http://us.archive.ubuntu.com/ubuntu noble/universe amd64 Packages
        100 /var/lib/dpkg/status
Name                  Application ID                  Version  Branch      Installation
Flatseal              com.github.tchx84.Flatseal      2.1.1    stable      system
MakeMKV               com.makemkv.MakeMKV             1.17.6   stable      system
Freedesktop Platform  org.freedesktop.Platform        23.08.13 23.08       system
Mesa                  …reedesktop.Platform.GL.default 24.0.2   23.08       system
Mesa (Extra)          …reedesktop.Platform.GL.default 24.0.2   23.08-extra system
nvidia-545-29-06      …p.Platform.GL.nvidia-545-29-06          1.4         system
openh264              ….freedesktop.Platform.openh264 2.1.0    2.2.0       system
GNOME Application Pl… org.gnome.Platform                       45          system
Greybird GTK+ Theme   org.gtk.Gtk3theme.Greybird               3.22        system
Greybird-dark GTK+ T… org.gtk.Gtk3theme.Greybird-dark          3.22        system
KDE Application Plat… org.kde.Platform                         5.15-23.08  system
Firefox               org.mozilla.firefox             123.0.1  stable      system
Tor Project           …torproject.torbrowser-launcher 0.3.7    stable      system
VLC                   org.videolan.VLC                3.0.20   stable      system

```
Both the flatpak and .deb work as expected on 24.04.

---

### Post by henkchr on 2024-03-15
I don&#8217;&#8217;t know  either , i had a package that was missing , i installed it, but it did not resolve anything. 
In the end no installation in ubuntu 22.04 lts
Thank you for letting me know that on ubuntu 24.04 it works fine. 
I do plan to use 24.04 lts myself also when it is  available.

---

### Post by monkeybrain20122 on 2024-03-16
Why don't you just get it from here
[https://www.torproject.org/download/](https://www.torproject.org/download/)

---

