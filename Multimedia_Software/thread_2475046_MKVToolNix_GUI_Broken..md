---
title: "MKVToolNix GUI Broken."
date: 2022-05-15
forum: Multimedia Software
---

### Post by Robert_Gaines on 2022-05-15
I'm using MKVToolNix GUI v64.0.0 ('Too Much') 64-bit on Ubuntu MATE 22.04 amd64 desktop, and the GUI is broken. I mean, it's just not working right. I'll include a picture. I don't know if I have it use it as command line or what, but this is weird. I've tried reinstalling it, and it still is like this.

---

### Post by TheFu on 2022-05-15
xorg or Wayland?

---

### Post by #&amp;thj^% on 2022-05-15
Even on a Xwayland session it should work.
```
apt policy mkvtoolnix mkvtoolnix-gui
mkvtoolnix:
  Installed: 67.0.0-0~ubuntu2204bunkus01
  Candidate: 67.0.0-0~ubuntu2204bunkus01
  Version table:
 *** 67.0.0-0~ubuntu2204bunkus01 500
        500 https://mkvtoolnix.download/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status
     65.0.0-1 500
        500 http://ca.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
mkvtoolnix-gui:
  Installed: 67.0.0-0~ubuntu2204bunkus01
  Candidate: 67.0.0-0~ubuntu2204bunkus01
  Version table:
 *** 67.0.0-0~ubuntu2204bunkus01 500
        500 https://mkvtoolnix.download/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status
     65.0.0-1 500
        500 http://ca.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages

```
How was it installed, did you follow a link perhaps?
Any way if you would like or have any interest I'll post mine:
I start by importing his key:
```
sudo wget -O /usr/share/keyrings/gpg-pub-moritzbunkus.gpg https://mkvtoolnix.download/gpg-pub-moritzbunkus.gpg

```
Then I'll add the source to "/etc/apt/sources.list.d":
```
sudoedit /etc/apt/sources.list.d/mkvtoolnix.download.list

```
and add the pools like:** CODE is fixed now.** see post #4
```
deb [arch=amd64 signed-by=/usr/share/keyrings/gpg-pub-moritzbunkus.gpg] https://mkvtoolnix.download/ubuntu/ jammy main
deb-src [arch=amd64 signed-by=/usr/share/keyrings/gpg-pub-moritzbunkus.gpg] https://mkvtoolnix.download/ubuntu/ jammy main

```
And then update package manager.
```
sudo apt update
``` 
it should now show a upgrade to " mkvtoolnix mkvtoolnix-gui"
Strictly your choice here, my suggestion is all.

---

### Post by Robert_Gaines on 2022-05-16
I tried ```
[COLOR=#000000][FONT=&quot]sudoedit /etc/apt/sources.list.d/mkvtoolnix.download.list[/FONT][/COLOR]
``` and put this in the file ```
[COLOR=#000000][FONT=&quot]deb [arch=amd64 signed-by=/usr/share/keyrings/gpg-pub-moritzbunkus.gpg] https:/>
[/FONT][/COLOR][COLOR=#000000][FONT=&quot]deb-src [arch=amd64 signed-by=/usr/share/keyrings/gpg-pub-moritzbunkus.gpg] htt>[/FONT][/COLOR]
``` and it broke apt. I had to delete the code to truncate the file to 0 bytes to get apt to load the repositories again. I don't know if I did something wrong, or if you gave me bad code. Ubuntu MATE uses xorg. Only xorg is installed. As far as I can tell, MKVToolNix is installed correctly. It is installed from the Ubuntu repository.

---

### Post by Robert_Gaines on 2022-05-16
```
apt policy mkvtoolnix mkvtoolnix-gui
mkvtoolnix:
  Installed: 65.0.0-1
  Candidate: 65.0.0-1
  Version table:
 *** 65.0.0-1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status
mkvtoolnix-gui:
  Installed: 65.0.0-1
  Candidate: 65.0.0-1
  Version table:
 *** 65.0.0-1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by #&amp;thj^% on 2022-05-16
Yep something went astray, but forward to now, add them with nano this time.
```
sudo nano /etc/apt/sources.list.d/mkvtoolnix.download.list

```
Add this, and I will check the correct syntax after I post this: **_EDIT all code looks as it should._**
```
deb [arch=amd64 signed-by=/usr/share/keyrings/gpg-pub-moritzbunkus.gpg] https://mkvtoolnix.download/ubuntu/ jammy main
deb-src [arch=amd64 signed-by=/usr/share/keyrings/gpg-pub-moritzbunkus.gpg] https://mkvtoolnix.download/ubuntu/ jammy main 
```
save the file and close.
then show me the return of:
```
cat /etc/apt/sources.list.d/mkvtoolnix.download.list

```
then update and upgrade.
BTW if your worried about the source, it comes straight from the Developers of " MKVToolNix":  [https://mkvtoolnix.download/downloads.html#ubuntu](https://mkvtoolnix.download/downloads.html#ubuntu)

---

### Post by #&amp;thj^% on 2022-05-18
I just love the reply's when someone asks for help, then offered and no reply. Sad just sad.

---

### Post by TheFu on 2022-05-18
> **1fallen said:**
> I just love the reply's when someone asks for help, then offered and no reply. Sad just sad.

That's why I try to drop subscriptions to forum threads after about a week.  I'd love to have a setting to automatically drop subscripts that haven't been touched in 30 days.  Inactivity tells me it isn't THAT important.  Too many nights of sleep between the question is bad for resolutions.

Out.

---

### Post by #&amp;thj^% on 2022-05-18
> **TheFu said:**
> That's why I try to drop subscriptions to forum threads after about a week. 

Great Idea! and Done. :)

---

### Post by Robert_Gaines on 2022-05-24
The output is:
```
deb [arch=amd64 signed-by=/usr/share/keyrings/gpg-pub-moritzbunkus.gpg] https://mkvtoolnix.download/ubuntu/ jammy maindeb-src [arch=amd64 signed-by=/usr/share/keyrings/gpg-pub-moritzbunkus.gpg] https://mkvtoolnix.download/ubuntu/ jammy main
```

---

### Post by Robert_Gaines on 2022-05-24
I did that, and the gui is still messed up.
```
apt policy mkvtoolnix mkvtoolnix-guimkvtoolnix:
  Installed: 68.0.0-0~ubuntu2204bunkus01
  Candidate: 68.0.0-0~ubuntu2204bunkus01
  Version table:
 *** 68.0.0-0~ubuntu2204bunkus01 500
        500 https://mkvtoolnix.download/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status
     67.0.0-0~ubuntu2204bunkus01 500
        500 https://mkvtoolnix.download/ubuntu jammy/main amd64 Packages
     65.0.0-1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
mkvtoolnix-gui:
  Installed: 68.0.0-0~ubuntu2204bunkus01
  Candidate: 68.0.0-0~ubuntu2204bunkus01
  Version table:
 *** 68.0.0-0~ubuntu2204bunkus01 500
        500 https://mkvtoolnix.download/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status
     67.0.0-0~ubuntu2204bunkus01 500
        500 https://mkvtoolnix.download/ubuntu jammy/main amd64 Packages
     65.0.0-1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages



```

---

### Post by Robert_Gaines on 2022-05-27
I tried uploading the new appimage, and I still have the same problem with the GUI. I'm not inclined to reinstall my OS because I don't have problems with my other applications.

---

### Post by #&amp;thj^% on 2022-05-27
If interested you can file a bug report, or open a ticket with them here: [https://mkvtoolnix.download/bugreports.html](https://mkvtoolnix.download/bugreports.html)
And thanks for the reply's ;)

---

### Post by Robert_Gaines on 2022-05-29
I got here for this issue here [https://gitlab.com/mbunkus/mkvtoolnix/-/issues/3358](https://gitlab.com/mbunkus/mkvtoolnix/-/issues/3358)

---

### Post by #&amp;thj^% on 2022-05-29
Keep checking there.
I'm wondering after reading your linked bug report, if you yet have tried installing these 2 deps:
"qt6-qpa-plugins" for a X11 session or "qt6-wayland" for a Xwayland session.
Either session works fine on my end as I've shown
Another Mate user reports they had luck with the new .deb same version as you show, but with some added QT libs: [https://mkvtoolnix.download/misc/issue3358/](https://mkvtoolnix.download/misc/issue3358/)
You can manually download the packages (mkvtoolnix & mkvtoolnix-gui, you need both; you don't need the -dgb debug symbol packages)
The Developer (Moritz Bunkus) is fighting with the new changes, on specific systems. QT5/QT6
That's about all I can add for you here, but Good Luck, and keep us updated.

---

### Post by csjcapital on 2023-05-03
> **Robert_Gaines said:**
> I'm using MKVToolNix GUI v64.0.0 ('Too Much') 64-bit on Ubuntu MATE 22.04 amd64 desktop, and the GUI is broken. I mean, it's just not working right. I'll include a picture. I don't know if I have it use it as command line or what, but this is weird. I've tried reinstalling it, and it still is like this.

Hey guy, I was looking for an answer and found this forum here, however we were both stuck on the issue.
I actually found a 2 way solution for the issue.

if your able to access APPEARANCE preference on UBUNTU, and in the selection of themes/backgrounds/fonts/ etc.

Change your fonts make sure all fonts are 10 or less, specifically the application font would be key for fixing this.
if once you do this, it looks decent enough to access the mKVtoolnix GUI (AT LEAST READ IT) click on it and once you see preference, then check the font there, if you still have issue, repeat step 1 and decrease the APP font to 8 and re-try. You should be able to access at least the settings and adjust to your liking.
Took me 6m of back and forth between the appearance of Ubuntu and the MKVtool gui to find the sweet spot. hope this helps and your still SUBBED

---

### Post by QIII on 2023-05-03
This thread is very nearly a year old.  I doubt that the OP is still watching this thread.

Rest in Peace.

Closed.

---

