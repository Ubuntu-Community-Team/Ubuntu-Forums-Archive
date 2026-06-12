---
title: "I downloaded nvidia drivers and now i can't get a graphical interface"
date: 2007-02-12
forum: Multimedia &amp; Video
---

### Post by mrmonday on 2007-02-12
Hi Everyone,

I have just installed Ubuntu 6.10 on my PC, and after a lot of messing around: it is connected to the internet.

Now I had the internet access I thought I would download the 3D graphics drivers, which would hopefully allow my monitor to display the correct resolution (1650x1050 - it currently shows up to  1280x1024). I tried the synaptic package manager, which wouldn't download anything, it just gave an error message. At one point, it managed to check for an update, when it did, I tried to download the package nvidia-glx as stated [here]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/graphics-cards.html").

The guide then said to run:
```
sudo nvidia-glx-config enable
```
The command returned that I would have to reboot my PC for the changes to take effect. I did so and now my PC can't boot into Ubuntu. It gives an error message which mentions something about X. At the prompt I tried to run:
```
sudo nvidia-glx-config disable
``` 
To no success.

I am new to Linux and am desperate to get it working, so any help would be appreciated.

Thanks in advance.

---

### Post by EvilMarshmallow on 2007-02-12
What card do you have in your computer?

I have an nVidia card (GeForce 4 Ti 4400) in mine and it requires an older driver... the one in Synaptic didn't work for me.

I had to go to the nVidia website and download the driver manually.  Fortunately they make it pretty easy.  Go into the archive, and on Step 1 of the README for each driver, there's a link to the list of models that driver supports.

Here's the thread where someone helped me with it.  These steps work for any nVidia card as long as you download the correct driver version.

[http://ubuntuforums.org/showthread.php?t=338526](http://ubuntuforums.org/showthread.php?t=338526)

---

### Post by FenrisAbraxas on 2007-02-12
> **mrmonday said:**
> Hi Everyone,

I have just installed Ubuntu 6.10 on my PC, and after a lot of messing around: it is connected to the internet.

Now I had the internet access I thought I would download the 3D graphics drivers, which would hopefully allow my monitor to display the correct resolution (1650x1050 - it currently shows up to  1280x1024). I tried the synaptic package manager, which wouldn't download anything, it just gave an error message. At one point, it managed to check for an update, when it did, I tried to download the package nvidia-glx as stated [here]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/graphics-cards.html").

The guide then said to run:
```
sudo nvidia-glx-config enable
```
The command returned that I would have to reboot my PC for the changes to take effect. I did so and now my PC can't boot into Ubuntu. It gives an error message which mentions something about X. At the prompt I tried to run:
```
sudo nvidia-glx-config disable
``` 
To no success.

I am new to Linux and am desperate to get it working, so any help would be appreciated.

Thanks in advance.

Sorry for disapointing you, the resolution of the monitor is not 100% limited to the video driver you are using, AFAIK you can get that resolution with the open source nvidia driver ("nv"). you just have to let X know that you want to use that resolution.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
gksudo gedit /etc/X11/xorg.conf

```

look for the part that say something like this:

```
Section "Screen"
    Identifier  "Screen 0"
    Device      "Device[0]"
    Monitor     "Monitor[0]"
    DefaultDepth 24

    Subsection "Display"
        Depth       8
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection

```

And just in each SubSection add the resolutions you want to be displayed like:

```
Subsection "Display"
        Depth       24
        Modes       ""1650x1050" "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection

```

Now ctrl + alt + backspace to restart X and voila your resolution will now be displayed in the app to change resolutions (in kde is in the control panel and i dont use gnome so i cant help you there :P).

Good Luck!

P.S. i can't help you either with the manual driver installation because you didnt give ANY details on your system specs.

P.S2 i forgot to mention, if something goes wrong just do:
```

sudo mv /etc/X11/xorg.conf.old /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart

```

---

### Post by mrmonday on 2007-02-12
I have the nvidia geforce 7300gs, do you know if those instructions will work from the terminal, because i have lost my graphical interface.

Thanks

---

### Post by ehowell on 2007-02-12
As you are running a res of 1650x1050 I am assuming that you have a newer video card.

I had problems using the repo drivers. I used a program called envy to get the latest drivers from Nvidia.

Previous posts with info are here: [http://ubuntuforums.org/showthread.php?t=347107](http://ubuntuforums.org/showthread.php?t=347107)

and here:

[http://ubuntuforums.org/showthread.php?t=349823](http://ubuntuforums.org/showthread.php?t=349823)

hope that helps!

---

### Post by mrmonday on 2007-02-12
sorry FenrisAbraxasmy system spec is as follows:

~intel pentium 4 processor with ht technology 3.0ghz (630)
~1Gb ram
~xfx nvidia geforce 7300gs with turbocache

my PC is being dual booted with XP home and Ubuntu 6.10

By the way can I do anyof these things from the terminal?

---

### Post by Sqwishy on 2007-02-12
either try the links ehowell suggested or try using envy [[http://albertomilone.com/nvidia_scripts1.html]](http://albertomilone.com/nvidia_scripts1.html])

---

### Post by EvilMarshmallow on 2007-02-12
The driver you need is the latest one from nVidia...

[http://www.nvidia.com/object/linux_display_ia32_1.0-9746.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9746.html)

Download this file and burn it to a CD, or put it on a flash drive.  Copy it to your ubuntu machine.

Then follow the instructions in the thread I linked to earlier... you should be good to go.  Actually, you can't have X running while tinkering with the video driver so you'll have to run it from a command line anyway.

---

### Post by mrmonday on 2007-02-12
Sorry about this... I'm trying to do too many thing at once. Can someone tell me what i've got to do. I think I just have to get the driver EvilMarshmallow posted, follow the instructions from nvidia, then configure the file FenrisAbraxas said to edit, then I should be good to go?

Thanks for your patience...

---

### Post by mrmonday on 2007-02-12
Do any of you happen to know how to enable universe and multiverse repositories from the command line? I would like to try EvilMarshmallows way, and envy says it needs them enabled. Thanks.

---

### Post by FenrisAbraxas on 2007-02-12
You DO need the nvidia drivers to get the 3D power :P and 99% of the time the nvidia installer configures your /etc/X11/xorg.conf so you just have to test if your new resolution is supported :).

Try envy or automatix2 (thou i heard it brokes things up).

Once you have the nvidia drivers installed and working, try to change your resolution if it doen't show the resolution you want try to edit manually the xorg.conf file :).

I'll be around so don't worry :p

---

### Post by mrmonday on 2007-02-12
> **FenrisAbraxas said:**
> You DO need the nvidia drivers to get the 3D power :P and 99% of the time the nvidia installer configures your /etc/X11/xorg.conf so you just have to test if your new resolution is supported :).

Try envy or automatix2 (thou i heard it brokes things up).

Once you have the nvidia drivers installed and working, try to change your resolution if it doen't show the resolution you want try to edit manually the xorg.conf file :).

I'll be around so don't worry :p

about envy... it says you need the universe and multiverse repositories, how can I enable them from the command prompt? should I just go for it without them?

I read about using gedit? can you use this from within the prompt?

---

### Post by ehowell on 2007-02-12
sudo vi /etc/apt/sources.list 

(substitute vi for your favorite text editor)

and uncomment out the universe and multiverse repositories

example:

# deb blah blah

should be 

deb blah blah

in other words, remove the leading hash mark (#)

---

### Post by mrmonday on 2007-02-12
This might sound like a stupid question... but how do I access my memory stick from the command prompt?

---

### Post by mrmonday on 2007-02-14
Hi.

Envy couldn't download the drivers for some reason, so I tried to install them by hand.... Now I can't even get a terminal, except in recovery mode, any ideas? Can I make envy use local drivers (the ones I downloaded on windows?) or is there a reason envy can't get the drivers? Would I be able to just replace my configuration files, and start again? 

Thanks in advance for any help.

---

### Post by EvilMarshmallow on 2007-02-14
You could try to reconfigure using

```
sudo dpkg-reconfigure xserver-xorg
```

and see if it will let you at least get back to *status quo ante bellum*.  This rewrites the xorg.conf file... just follow the instructions, make sure you choose "nv", NOT "nvidia" YET from the drivers list at the beginning.  Once you're back to a gui, then we can retry the driver installation as follows:

1.  Download the .run file on the page I linked on page one.
2.  **sudo gedit /etc/default/linux-restricted-modules-common**
2a.   Make sure that the DISABLED_MODULES = "" line has nv inside the quotes... **DISABLED_MODULES="nv"**
2b.   Save & Close.
3.  CTRL-ALT-F1 to get to a command prompt.
4.  **sudo /etc/init.d/gdm stop** to kill the gui completely.
5.  cd to the directory where you saved the driver
6.  **sudo sh NVIDIA-driver-blah-blah-blah **(can't remember what it's called exactly)
7.  follow the on-screen instructions.
8.  When it's done and you're back at a command prompt, you can try to

[B]sudo /etc/init.d/gdm start
startx[/B]

to try to get it to come back up.  You should get an nVidia splash screen before the login window if it recognizes the nvidia driver properly.

If that doesn't work, try rebooting. I can't remember if it's necessary to do so or not.

---

### Post by mrmonday on 2007-02-14
I may have entered some settings wrong... but I still can't get a graphical interface.... any ideas? what should the settings be?

---

### Post by ehowell on 2007-02-14
When I have problems (and boy do I have problems on occasion!) I usually manually go into the /etc/X11/xorg.conf file by hand (with vi or nano or whatever) and change the line with "nvidia"  to "nv" to use the stock nvidia drivers that ship with Ubuntu. That should get you to a GUI at least. 

If you still can't get to a GUI with those, you can even change the "nvidia" to "vesa" to get default vesa drivers going.

Did you upgrade Envy? If you are upgrading you should purge the old version as was explained in the post referenced before. Otherwise I'm not sure why it would fail as it has worked like a charm for me in the past.

Also if the nvidia drivers are installed you can always try from the command line (not in X)

sudo nvidia-xconfig to configure X. It will back up your current xorg.conf file first.

I know this stinnks now but look on the bright side, you will know a heck of a lot about X when you get it working! ;)

---

### Post by mrmonday on 2007-02-14
OK heres a question...

```
sudo nano /etc/x11/xorg.conf
```

This brings up nano, however, it comes up with a new, blank file... this can't be right can it? what should be in it

---

### Post by EvilMarshmallow on 2007-02-14
See if you have backup copies of xorg.conf to work from.  If you worked with envy you probably do have at least one.

cd to your /etc/X11 directory and find the oldest backup copy of xorg.conf.  It should be labeled xorg.conf.######## with the ####### being a timestamp.

Copy it

sudo cp xorg.conf.###### xorg.conf

and then do

sudo nano xorg.conf

See if that helps.

---

### Post by ehowell on 2007-02-14
No it should definitely NOT be empty. If it is empty, that is a problem.

Try this:

more /etc/X11/xorg.conf to see if you can read anything from the file (hit q to quit when done looking or keep hitting spacebar to get to the end of the file). If nothing shows up try:

ls -l /etc/X11/xorg.conf

I get 

-rw-r--r-- 1 root root **4128** 2006-12-27 12:53 /etc/X11/xorg.conf

if you get 
ls: cannot access /etc/X11/xorg.conf: No such file or directory

then you have no configuration file, and you either need to generate a new one

try:

sudo dpkg-reconfigure xserver-xorg

If you followed these directions from an earlier post
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
gksudo gedit /etc/X11/xorg.conf

then you effectively moved your xorg.conf file to /etc/X11/xorg.conf.old and that could be why your file is empty. The advice was sound to back up your xorg.conf file FIRST before editing, but just substitute cp for mv in that command above.

But, since you changed things since then (I assume) in my humble opinion I would just generate a new xorg.conf file.

I'm working off memory here so hopefully this will help you, if not someone else will have more info for you.

---

### Post by mrmonday on 2007-02-14
Ok... It appears I have no x11 directory at all... this i am presuming is bad... so there are also no backups... help! I will try the reconfigure thing above now.

---

### Post by mrmonday on 2007-02-14
Nope... No luck, It hasn't created an X11 directory or the xorg.conf file... what now?

---

### Post by ehowell on 2007-02-14
Well,

at this point, since I think you just installed the OS that you repair it with the installation disc, or call this one a wash and just do a fresh install.

That is just my opinion and what I would do based on what you have told me, so you may want to wait for other advice from people before you do it. 

I find it weird that X11 is gone (if you ls /etc you see NO X11 directory?) but honestly, unless you spent a ton of time modifying things so far (installing new progs, changing  themes, etc) it would take you about 30 minutes to reinstall, much less time than trying to fix X.

You can also try to repair using the installation disc.

Again, there is a lot to be said for fiddling, and trying to fix things (you learn a LOT), but if it were me at this point, I would chalk this up to a learning experience and start anew (plus I love the smell of a fresh install).

Just my opinion. If you want to try and get X back then we can try that, tell me what you see when you type

ls /etc

:)

---

### Post by mrmonday on 2007-02-14
I think your probably right about re-installing it. ls /etc has a long output and at the moment I just want to get started using linux, as I don't have much time and was looking for a new experience... I actually enjoy messing around with all these settings... Could you tell me how I'd go about doing a repair install of ubuntu, I don't want do damage windows. Then I will ask how to install the drivers properly... Thanks.

---

### Post by EvilMarshmallow on 2007-02-14
I don't know how to repair install Ubuntu, but make a note of my previous post.  Those are the steps for installing the nvidia driver you need.  Once you've gotten the fresh OS on there, just start down that list and you shouldn't have any trouble with nvidia drivers.

---

### Post by mrmonday on 2007-02-14
Thanks, is it just a case of restarting with the ubuntu disk in? or do I need to wait for Grub to load?

---

### Post by ehowell on 2007-02-14
assuming that you boot from the CD first you won't even get to grub (since it is on your HD.)

When you boot from CD you will get the main text menu, and the option to repair install should be there.

It shouldn't touch your windows partition... If you do go with a fresh reinstall just make sure that you use the same partitions as the previous install and don't remove the windows one.

Some other advice would be to just take minutes and do a quick search for a repair guide or some other user's past experiences with this.

good luck :)

---

### Post by mrmonday on 2007-02-15
Thank you everyone for all your help! I now have a working version of Ubuntu Linux installed, with 3D graphics!

---

### Post by ehowell on 2007-02-15
Awesome!

Glad it worked out for you!

---

