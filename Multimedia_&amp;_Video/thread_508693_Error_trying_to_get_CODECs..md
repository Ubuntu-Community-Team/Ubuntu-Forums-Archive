---
title: "Error trying to get CODECs."
date: 2007-07-24
forum: Multimedia &amp; Video
---

### Post by Pepse3 on 2007-07-24
I went to "Enabling Multimedia in Feisty (How-To), then from there I went to "Add/Remove" programs, and added the 4 "GStreamer" items and then I went to a terminal (Konsole) and typed in the first command of:  gksudo gedit /etc/apt/sources.list and the error is:

Error: BadDevice, invalid or unitilialized input device 167   .

Major opcode: 144

Minor opcode: 3

Resource id: 0X0

Then it repeated the same error and gave me my jim@jims computer.  What's up with this?

Pepse.

---

### Post by linuxwizard on 2007-07-24
If you want to install the codecs do this.
Go to Synaptic and install these some maybe already installed if it worked when you went to Add/Remove if they are installed the box next to them will be colored in. When installing these don't use your terminal I don't understand what you were trying to do earlier after add/remove in the terminal. 

Install With Synaptic
gstreamer0.10-plugins-ugly

gstreamer0.10-plugins-ugly-multiverse

gstreamer0.10-plugins-bad
    
gstreamer0.10-plugins-bad-multiverse

gstreamer0.10-ffmpeg

libdvdread3


Use the individual packages to install libdvdcss2 and w32codecs (copy & paste)

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)


Do you have Flash Player installed ? Go here to check if it is installed and what version
[http://www.adobe.com/products/flash/about/](http://www.adobe.com/products/flash/about/)

---

### Post by Pepse3 on 2007-07-25
Yes all the packages are installed that I did through ADD/REMOVE.  My Flash is ver 9,0,31,0.  As for why I went to a terminal?  If you look at Adamant1988's sticky he states "Edit the file /etc/apt/sources.list using either of the following commands in a terminal".  So, that is why I tried to use a terminal.  Now if any of this stuff HAS to be done by cut & paste I'm screwed as for all the years of using a computer I never did cut and paste.  I have tried and it is (to me) a screwy mess.  I would rather type a long command than try to do cut & paste.

Later. Pepse.

---

### Post by linuxwizard on 2007-07-25
You don't have to copy & paste it is just faster. You can type it into a terminal just make sure you don't miss anything than it will not work.

---

### Post by Bablefish on 2007-07-25
It's like when I installed Medibuntu myself and let me tell you I HAD PROBLEM!!!!! I could not install it period until I went to the offical site of Medibuntu (I googled it) and discovered they had command lines for a direct terminal install. All I had to do was copy and paste and within a few minutes Medibuntu was installed

---

### Post by Pepse3 on 2007-07-26
Thanx to Babelfish my problem is solved.  I went to Medibuntu's offical web and proceeded with the necessary info they provided and I now can watch DVD movies.  Then someday I might figure out what the W32codecs are for.

Thanx, again.

Pepse.

---

### Post by linuxwizard on 2007-07-26
Pepse3
If would have looked at that link that I give you it explains what each package is for and how to install. You did not have to go to the main site to install.

Use the individual packages to install libdvdcss2 and w32codecs (copy & paste)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Pepse3 on 2007-07-29
I did look at that link for a bit and then looked at Medibuntu's site and decided that between the two Medibuntu's was easier to deal with.

Later. Pepse.

---

