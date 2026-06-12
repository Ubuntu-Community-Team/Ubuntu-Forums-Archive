---
title: "where did mencoder go?"
date: 2007-05-20
forum: Multimedia &amp; Video
---

### Post by wolfen69 on 2007-05-20
i used synaptic package manager to download mencoder. i have no idea where it is. do i need to download something else to get it to work?

---

### Post by Steveway on 2007-05-20
It's a console app.
Open a terminal and type $mencoder in it.
You would want to try $man mencoder 
so you can check what you can do.

---

### Post by Pollywoggy on 2007-05-20
Are you saying you don't know where Synaptic put the downloaded file?
Take a look in /var/cache/apt/archive/
It is probably there.

To see if it is installed:

dpkg -l mencoder

If you see this:
   ii  mencoder   

It is installed.

---

### Post by wolfen69 on 2007-05-20
this is what happened in the terminal:

e@e-desktop:~$ dpkg -l mencoder
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  mencoder       1.0~rc1-0ubunt MPlayer's Movie Encoder

i really could use a video converter/encoder, but have no idea how to get this program to work.

---

### Post by webaake on 2007-05-25
Go into SYnaptic and look för mplayer. mencoder installs together with mplayer, i think.

---

### Post by eye208 on 2007-05-25
> **wolfen69 said:**
> i really could use a video converter/encoder, but have no idea how to get this program to work.
As someone already mentioned, mencoder is a console application. Very powerful, but without a GUI.

If you prefer to have a GUI, use Avidemux instead. It is very similar to VirtualDub on Windows.

---

