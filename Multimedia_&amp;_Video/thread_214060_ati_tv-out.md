---
title: "ati tv-out"
date: 2006-07-12
forum: Multimedia &amp; Video
---

### Post by mwolfe on 2006-07-12
i have an ati 9600 on my laptop (asus m6n)
When i press function+switch tv out 
button my desktop freezes completely and i can't even kill x (control+alt+backspace). I have the fglrx proprietary driver, installed using the how-to on these forums.  

So i started looking up how to setup tv out and it seems like you've got to change some settings in your xorg config and it must be plugged into the tv when it starts up and all this junk.. Are there any good how to's or simpler ways of doing this?? Seems like ubuntu has got most things automated real well by now and was hoping there is an eaiser way to do this.

---

### Post by jayemef on 2006-07-12
I've always had success configuring TV out by simply running
```
$ sudo fglrxconfig
```
You can pretty much go with all the defaults, except choose yes when it gets to configuring TV out.

---

### Post by fridaythe14th on 2006-07-12
I haven't got a laptop but this is what worked for me.

I don't know if you need it but I see no reason not having your TV plugged to you graphics card and turned on (it's easier testing that it works that way ;)). Then do this in the terminal:

```
sudo apt-get install xorg-driver-fglrx                                    #you propbably already have these
sudo apt-get install linux-restricted-modules-$(uname -r)   #you propbably already have these
sudo nano /etc/X11/xorg.conf
```

Now look for the section "Device". You probably have a row that says
> Driver        "ati"

Change "ati" to "fglrx" and save (ctrl+o)

Ctrl-Alt-Backspace to kill X

It should work, but you might get letterbox format and a desktop bigger than your resolution (I did).



If you want to make you TV into a second workspace (desktop) instead of a clone (which also solves the mentioned problems):

sudo nano /etc/X11/xorg.conf

In the section "Device" add these lines:
        Option          "DesktopSetup" "0x00000200"
        Option          "MonitorLayout" "AUTO, AUTO"

Also copy the "Monitor" section and paste just below, change the Identifier to something else, like "TV", "Screen2" or whatever you like. The name doesn't matter, it just needs to be different than the other. 

example:
> Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "TV"
        Option          "DPMS"
EndSection

---

### Post by Mastus on 2006-07-12
I got mine working at last... 

Installed the drivers from ati.com (Howto is somewhere around here)
then I ran aticonfig --initial=dual-head

Trick in my case was that I _HAD_ to include this in xorg.conf

  Option ForceMonitors "crt1,tv,nocrt2"

---

### Post by mwolfe on 2006-07-13
> I've always had success configuring TV out by simply running
Code:

$ sudo fglrxconfig

You can pretty much go with all the defaults, except choose yes when it gets to configuring TV out.

I think this command is deprecated or something.. doesnt work, thanks though


as far as fridaythe14th's suggestion, first of all i already installed the driver, but if i am to make these changes, how do i use my tv then? Will it automatically figure out that its connected to the tv if i have it plugged in, so i just need to restart x or something (or reboot).. is there a command i type in to switch back and forth? You say you don't see any reason not to have it plugged in to the tv on boot up, but i rarely do have it hooked up to the tv first as its in the other room.. usually i download the movie/tv show from my pc to my laptop here and take it to the other room (takes too long to do wirelessly). Not a big deal but i'd prefer not to have to restart my computer or x. 

As far as mastus's suggestion, same applies, how do i switch from one output to another.. i dont want to try them all yet i'll probably messup my  settings altogether and have to reinstall everything. 

Thanks a lot though for the suggestions.

---

### Post by fridaythe14th on 2006-07-13
> **mwolfe said:**
> as far as fridaythe14th's suggestion, first of all i already installed the driver, but if i am to make these changes, how do i use my tv then? Will it automatically figure out that its connected to the tv if i have it plugged in, so i just need to restart x or something (or reboot)..
Yes. That did it for me. fglrx seems to automatically output a clone of your desktop to the S-video/composite output.


> is there a command i type in to switch back and forth? You say you don't see any reason not to have it plugged in to the tv on boot up, but i rarely do have it hooked up to the tv first as its in the other room.. usually i download the movie/tv show from my pc to my laptop here and take it to the other room (takes too long to do wirelessly). Not a big deal but i'd prefer not to have to restart my computer or x.
I see. You unfortunately have to start X with your TV plugged in. Ctrl-alt-backspace is enough, you don't have to reboot.

---

### Post by mwolfe on 2006-07-13
thats cool, i'll give it a try later.
thanks for the help

---

### Post by jayemef on 2006-07-13
Yeah, it's entirely possible that it was depricated. I'm using an older version of the driver, as the newer ones don't support xv properly, which is devastating on a MythTV system.

---

