---
title: "Packet Tracer font sucks on 11.04"
date: 2011-09-07
forum: Networking &amp; Wireless
---

### Post by rodneykrobinson@gmail.com on 2011-09-07
Any help with this?  I have installed the latest version of Packet Tracer on my also newly installed unbuntu 11.04.  The font settings on the words in the app is not good.  Is there a way I can fix that?

---

### Post by JSchultheis on 2011-10-11
Can you give a link or walkthrough on the install of Packet Tracer?

I promise to try my best to help you thereafter :)

---

### Post by JSchultheis on 2011-10-11
> **JSchultheis said:**
> Can you give a link or walkthrough on the install of Packet Tracer?

I promise to try my best to help you thereafter :)

Scratch that. I have it installed. Sweet!! :guitar:


 But yeah what crazy font?!  Let's see if we can figure that out...](*,)

---

### Post by JSchultheis on 2011-10-11
[SIZE="3"][FONT="Times New Roman"][/FONT][/SIZE][[COLOR="Blue"]***_anybody looking to install packet tracer on ubuntu or peppermint os click here_***[/COLOR]]("http://ubuntuforums.org/showthread.php?p=11330139")

---

### Post by JSchultheis on 2011-10-11
check it yo!


> [URL="http://pvradu.blogspot.com/2010/04/packet-tracer-52-font-problem.html"][COLOR="Blue"][B][I][U][SIZE="4"]Packet Tracer 5.2 font problem[/SIZE]
Posted by pvradu at 01:04
I tried to start the newly installed Packet Tracer 5.2 on my Ubuntu 10.04 LTS beta 2. Unfortunately application fonts were really *effed* up. But, there is a fix for that.

- first of all, Packet Tracer runs on its own QT4 libraries, and you don't want that. So, to change that, edit this file "/usr/local/PacketTracer5/packettracer" 

```
gksudo gedit /usr/local/PacketTracer5/packettracer
```

and comment out (*delete*) this line:

```
export LD_LIBRARY_PATH=$PTDIR/lib
```


- after that, you have to install whatever QT4 missing packets you have to install this:
```
sudo apt-get install libqt4-gui
sudo apt-get install libqt4-webkit
sudo apt-get install libqt4-qt3support
```

if it still doesn't work after all this, just do this:
```
sudo apt-get install libqt4-dev
```

Then your Packet Tracer is ready to go and simulate Cisco equipment.
Have fun![/U][/I][/B][/COLOR][/URL]

My reality is Packet Tracer 5.3
And I run it in Peppermint OS.



See attached Image, no more font problems.:KS

---

### Post by JSchultheis on 2011-10-11
[COLOR="Blue"][SIZE="3"][FONT="Times New Roman"][B][I][U][URL="http://pvradu.blogspot.com/2010/04/packet-tracer-52-font-problem.html"][COLOR="Blue"]too much link, here is less link:

Packet Tracer 5.2, 5.3 font problem
Posted by pvradu[/COLOR][/URL][/U][/I][/B][/FONT][/SIZE][/COLOR]

- first of all, Packet Tracer runs on its own QT4 libraries, and you don't want that. So, to change that, edit:
```
gksudo gedit /usr/local/PacketTracer5/packettracer
```

and delete:

```
export LD_LIBRARY_PATH=$PTDIR/lib
```


- after that, install this:
```
sudo apt-get install libqt4-gui
sudo apt-get install libqt4-webkit
sudo apt-get install libqt4-qt3support
```

if it still doesn't work after all this, just do this:
```
sudo apt-get install libqt4-dev
```

Then your Packet Tracer is ready to go and simulate Cisco equipment.
Have fun!


-------------------
I run Packet Tracer 5.3
And I run it in Peppermint OS

:KS

---

