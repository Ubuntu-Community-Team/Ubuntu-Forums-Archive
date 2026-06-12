---
title: "nVidia 5200 card and resolution problems"
date: 2009-04-27
forum: Multimedia Software
---

### Post by lidaka on 2009-04-27
Hey guys,

First of all, let me state that I'm a complete noob who just went from Win to Ubuntu 9.04, so I don't really know anything.

I've got a fx 5200 geforce card on my comp, and it's stuck on max resolution of 640X480. I've searched the web, but I can't find a solution to max my resolution up.
My TV is a Hitach falt-screen with max res of 1200 and up, and I use a VGA cable to connect my comp to it.

So, if you have an idea that I can perform myself without breaking my head, please help me. I really want to stick to Ubuntu... :)

---

### Post by marshmallow1304 on 2009-04-27
Are you using NVIDIA drivers? i.e. is a driver activated under System->Administration->Hardware Drivers?

---

### Post by lidaka on 2009-04-28
> **marshmallow1304 said:**
> Are you using NVIDIA drivers? i.e. is a driver activated under System->Administration->Hardware Drivers?

indeed. I'm using the 173 driver of Nvidia.

---

### Post by andrea000 on 2009-04-28
go to systems->administration->nvidia x server settings then click x server
display configuration over to the right it will say display then under that 
resolution and see if you can set it from there now under that and over the
right you will see save to x configuration file click that and see if that 
will work.that what i did but like all i can only tell you what worked for me.
173 driver is what i use and does a good job

---

### Post by lidaka on 2009-04-28
hey andrea,
I've tried that already,
the max resolution over there is still 600X480.

---

### Post by andrea000 on 2009-04-28
Ok what about a edit to x org config file?I dont know what version your running so i will just think that your running 8.10 because thats what i run
If you do not see the required resolution values in the GUI tool, you can add additional screen resolutions by editing the xorg.conf file.

The full path of the file is /etc/X11/xorg.conf. Suppose I want to add the resolution “1024×768&#8243; which is supported by my monitor. I do the following :

Open /etc/X11/xorg.conf in a text editor. I usually use vi. You have to use sudo to open it to make changes so the actual command will be something like follows :

$ sudo vi /etc/X11/xorg.conf

Xorg.conf file in Ubuntu is quite sparse and contain only a few lines. I made the following changes to get 1024×768 resolution on my machine. The changes / additions are highlighted in bold font.

Section "Device"
	Identifier	"Configured Video Device"
Driver    	"vboxvideo"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
   Identifier    "Default Screen"
   Device    "graphics card"
   Monitor    "Configured Monitor"
DefaultDepth    24
   SubSection "Display"
         Depth     24
         Modes     "1024x768"
   EndSubSection
EndSection

If you are running it natively then, in all probability, Ubuntu would have detected and configured the correct driver and resolution for your machine. If not, you can change the line Driver “vboxvideo” to the driver suited for your hardware. Possible candidates are intel, nvidia, nv and so on.
Use dpkg-reconfigure script to change the xorg.conf file

If you are skeptical of your skills in editing a text file (xorg.conf) by hand, then you can also use the dpkg-reconfigure script to do the same. Open up a terminal and run the following command :

$ sudo dpkg-reconfigure -phigh xserver-xorg

This will start a wizard albeit on the console, which will walk you through configuring Xorg server. Among other things, it will ask you to choose the video driver and the resolution of your monitor from a list. Once all the questions are answered, the wizard will make a backup copy of your current xorg.conf file and write in the new values. You will have to restart Xorg server for the changes to take effect. If you are in graphical mode, you can press the key combination

---

### Post by lidaka on 2009-04-28
thanks for the quick reply
I use ubuntu 9.04
what you said to me sounds like chinese... I have no I idea what xorg is, and how to use the things you wrote.... what can I say, I'm a total noob... :(

---

### Post by Sephoroth on 2009-04-28
> **lidaka said:**
> thanks for the quick reply
I use ubuntu 9.04
what you said to me sounds like chinese... I have no I idea what xorg is, and how to use the things you wrote.... what can I say, I'm a total noob... :(

Applications -> Accessories -> Terminal

Paste the following line into the terminal.

```
sudo vi /etc/X11/xorg.conf
```

You may then make changes as andrea0000 suggested.

For me my Nvidia GeForce FX 5200 worked out of the box on Intrepid Ibex so I suppose I am lucky.

---

### Post by andrea000 on 2009-04-28
One basic way to put it is xorg is were all your video display 
setting are stored.I am sorry i don't use 9.04 yet it just seems 
to me it has a lot of bugs or maybe its just me.

try this

sudo dpkg-reconfigure -phigh xserver-xorg

that should start a wizard that will let you set the display 
setting up.Oh welcome to the world of ubuntu and don't worry 
every body is a noob to start.

---

### Post by andrea000 on 2009-04-28
I am sorry do this first open a terminal
Applications -> Accessories -> Terminal
then do the above.

---

### Post by lidaka on 2009-04-28
when I try to type "sudo dpkg-reconfigure -phigh xserver-xorg" I get the message: "xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20090428111704"
when I type "sudo vi /etc/X11/xorg.conf I'm not able to write anything (maybe I just don't know how, but when I try to type with my keyboard nothing happens.

oooff.

---

### Post by andrea000 on 2009-04-28
the message you get on sudo dpkg-reconfigure -phigh xserver-xorg 
is just telling you that your going to overwrite the xorg file 
and it has made a back up copy for you then you sould then see a 
wizard in the terminal there should be some questions to answer
one will let you set the resolution setting.

---

### Post by lidaka on 2009-04-28
> **andrea000 said:**
> the message you get on sudo dpkg-reconfigure -phigh xserver-xorg 
is just telling you that your going to overwrite the xorg file 
and it has made a back up copy for you then you sould then see a 
wizard in the terminal there should be some questions to answer
one will let you set the resolution setting.
well, I just get those lines and then blank - like it's waiting for me to write something.

thanks for the patience...

---

### Post by andrea000 on 2009-04-28
the sudo vi /etc/X11/xorg.conf should pull your xorg
up in a text editor if you use vi as a editor

---

### Post by lidaka on 2009-04-28
what does it mean: "if you use vi as the editor"?

---

### Post by andrea000 on 2009-04-28
Ok try this and see if a text editor comes up

gksudo gedit /etc/X11/xorg.conf

---

### Post by andrea000 on 2009-04-28
vi is a modal editor a text editor it does a lot more
then a editor

---

### Post by lidaka on 2009-04-28
okey, I've done it and now it looks like this:

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
        DefaultDepth 24
        SubSection "Display"
        Depth 24
        Modes "1024x768"
        EndSubSection
EndSection

whats the next step? it still doesnt let me change a resolution above 640X480 when I try to do so on the Nvidia X server settings

---

### Post by andrea000 on 2009-04-28
find the line Modes and change it to what your looking to get
like this
Modes   "1280x1024" "1024x768" "640x480"

---

### Post by andrea000 on 2009-04-28
and from what i have read about 9.04 you may want to run driver 177
instead of 173 but i'm not sure

---

### Post by andrea000 on 2009-04-28
Here is what mine looks like

Section "Monitor"
    Identifier      "External DVI"
    Modeline        "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
    Option          "PreferredMode" "1280x1024_60.00"
EndSection
Section "Device"
    Identifier      "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
    Driver          "ati"
    Option          "Monitor-DVI-0" "External DVI"
EndSection
Section "Screen"
    Identifier      "Primary Screen"
    Device          "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
    DefaultDepth    24
    SubSection "Display"
        Depth           24
        Modes   "1280x1024" "1024x768" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Primary Screen"

---

### Post by andrea000 on 2009-04-28
Here like this just copy and past over yours

Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "640x480"
EndSubSection
EndSection

---

### Post by andrea000 on 2009-04-28
to automatically updated the xorg run the following command:
sudo dpkg-reconfigure -phigh xserver-xorg
and it may update your xorg file

---

### Post by lidaka on 2009-04-28
thank you so much! 
meanwhile I went to my parents house, so I won't be near the machine till friday. I'll try what you said and get back to tell you how it went.
thanks so much for now, happy ID.

---

### Post by NickiLee on 2009-09-10
FYI - I was having this same problem, tried editing the xorg.conf file, but this did not work for me.  I ended up trying different versions of the nvidia driver and found one that worked: driver 93 instead of 173 or 177.

---

### Post by gany1102 on 2009-11-02
Hello all,

I am a newbie to ubuntu (rather linux).  I just installed desktop version on my PC which has nVidia 5200 card.

The max resolution, I can see 600x480.  I installed nVidia 173 driver (recommended).  Still no use.

I guess, I am missing something....  Could you please navigate me resolving this issue.

Thanks in advance....

Gany

---

### Post by epek on 2009-11-02
Is the vga-cable connected directly to the PC or do you have a kvm-switch in between?
A cheap kvm-switch prevented me from using the correct settings on multiple PCs.

If that is not the case, I would check my /var/log/xorg.0.log for the recognized screen sizes.

Afterwards you can set them manually in /etc/X11/xorg.conf:

e.g.:

Section "Monitor"
        Identifier      "Configured Monitor"
        ModelName       "Hyundai Imagequest L72D"
        DisplaySize     338 270
        Modeline "1280x1024_75.00" 138.54 1280 1368 1504 1728 1024 1025 1028 1069 -HSync +Vsync
        Modeline "1280x1024_60.00" 108.88 1280 1360 1496 1712 1024 1025 1028 1060 -HSync +Vsync
... and so on ...

DisplaySize may be obsolete, if using Modelines.

I´d prefer the modelines over the "Modes", because they are much more precise.
If you don´t see modelines in your log, something more is wrong...

---

