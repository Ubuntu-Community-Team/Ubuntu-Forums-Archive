---
title: "How to enable a volume bar with Esound (after removing Pulseaudio)"
date: 2010-01-10
forum: Multimedia Software
---

### Post by slaol_121 on 2010-01-10
My OS is Ubuntu 9.10 64bit.

I have been having problems with audio in several of my applications - all of which were fixed by removing Pulseaudio and installing Esound.

After uninstalling pulseaudio, there is now no volume bar in the notification applet on my desktop panel.  

In addition to this, my volume keys on my keyboard (Lenovo Y550 Ideapad) no longer work.

Is there an application I can install that will put a volume bar back on my notification panel (using Esound)?

Thanks,
Slaol

---

### Post by alexandrius on 2010-01-11
Hi
First of all install all gstreamers from synaptic (My experiance)

A bit of fiddling I did, and I now notice I can add an applet to the panel regardless of whether pulseaudio is there or not.

I'm still missing the gnome-volume-control though, which is part of the 
What I did was recompile the gnome-applets package from the repos, and add in the applet.

I really don't recommend anyone try this, you'd be better off to just stick with pulse, but if you really want that applet back after removing pulseaudio, this is one such way.

If anyone's interested here's what I did:

> sudo apt-get install devscripts build-essential fakeroot
sudo apt-get build-dep gnome-applets
That'll pull in all the dependencies to build everything.

```
cd ~
mkdir build && cd build
apt-get source gnome-applets
cd gnome-applets-2.28.0
```
Then you're going to have to specify the configure options to enable the mixer applet. To do that

```
gedit debian/rules
```
Look for the line that starts with DEB_CONFIGURE_EXTRA_FLAGS +=
and add in --enable-mixer-applet on the same line, save and close.

Then run this to build the packages.
```
dpkg-buildpackage -b -j4 -D
```
once that's finished:
```
cd ..
```
To see the end result; there should now be 3 .debs in that directory, namely:
> gnome-applets_2.28.0-0ubuntu2_i386.deb
gnome-applets-data_2.28.0-0ubuntu2_all.deb
gnome-applets-dbg_2.28.0-0ubuntu2_i386.deb

Lastly install them with:
```
sudo dpkg -i *.deb
```
Restart gdm (log off and log on again, reboot or run sudo service gdm restart), and right click on the panel and you should now be able to add a volume control applet regarless of whether pulseaudio is installed or not.

Apt is now going to want to update those 3 packages to their original version, so to hold and tell it to leave them as is do:
```
sudo -s
```
```
echo 'gnome-applets hold' | dpkg --set-selections
echo 'gnome-applets-data hold' | dpkg --set-selections
echo 'gnome-applets-dbg hold' | dpkg --set-selections
```
Now you should be able to carry on as normal.
The tutorial is written by **Zoot7**

Also you may experiance some problems with autostart of gnome-applets which is easily fixed with reinstallation of gnome-applets-data and gnome-panel-data

Hope this helps

P.S volume controller buttons wouldn't work anyway

---

### Post by Yellow Pasque on 2010-01-11
If you removed pulse, install the gnome packages from: [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

> P.S volume controller buttons wouldn't work anyway
They should once you install gnome-settings-daemon from the above repo.

---

### Post by alexandrius on 2010-01-11
> **Temüjin said:**
> If you removed pulse, install the gnome packages from: [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)


They should once you install gnome-settings-daemon from the above repo.

thanks man, works like a charm :):D

---

### Post by jadonchristensen on 2010-01-19
Removing Pulse and installing Esound was the best thing I have done on Ubuntu 9.10 yet. No more crackling sounds.

I just use the following command if I need to adjust stuff.

gnome-alsamixer

---

### Post by sports.car.guy on 2010-01-19
> **jadonchristensen said:**
> Removing Pulse and installing Esound was the best thing I have done on Ubuntu 9.10 yet. No more crackling sounds.

I just use the following command if I need to adjust stuff.

gnome-alsamixer

Why put a client / server environment plagued with latency issues, which both Esound and Pulseaudio both suffer from severely on your systems? They both reference Alsa libraries so why not just use Alsa by itself instead?

I have had nothing but problems using Esound back in the day and Pulseaudio too. Chirping, crackling, hissing, all nasty things you don't want in sound. I am glad that Kubuntu still hasn't adopted Pulseaudio.

The only reason why the distribution creators are, it seems is because so many people go well windows does surround sound up-mixing without doing too much and Linux does not. Linux does if you set it up right and it isn't that hard. I am actually working on a tutorial thread for it with the ability to crossover points, etc. That is how mine is setup with no services like Esound or Pulseaudio, no latency issues, all working beautifully.

---

### Post by jadonchristensen on 2010-01-19
> **sports.car.guy said:**
> Why put a client / server environment plagued with latency issues, which both Esound and Pulseaudio both suffer from severely on your systems? They both reference Alsa libraries so why not just use Alsa by itself instead?


All I can say is that Esound works with my Skype, games, browser, youtube, etc. No issues yet, no headaches.

---

### Post by sports.car.guy on 2010-01-19
> **jadonchristensen said:**
> All I can say is that Esound works with my Skype, games, browser, youtube, etc. No issues yet, no headaches.

Got ya.. It works..lol.

I totally understand your looking at it that way. Not everyone wants to deal with what I am talking about and just want to start the system and have things work. I think that is why PulseAudio has it's internal up-mixing which works, but not well. It doesn't do anything like frequency filtering to the channels like low and high pass crossover points. It just sends the full frequency range to each channel muddying your satellites and causing them to work harder then they should, even blowing due to this.

---

### Post by Yellow Pasque on 2010-01-20
> **jadonchristensen said:**
> All I can say is that Esound works with my Skype, games, browser, youtube, etc. No issues yet, no headaches.
Do you really have the esound daemon running with all those program set to output to esound/esd? I doubt it..

People seem to be getting esound confused with just running ALSA. esound is rarely needed anymore. Pulse has an esound module that converts the output of programs using esound to whatever pulse uses. When you remove pulse, you might install the esound daemon (though you probably don't need it) to satisfy dependencies. Actually running esd and having programs output to it takes more work than just removing pulseaudio.

---

### Post by jadonchristensen on 2010-01-20
> **Temüjin said:**
> Do you really have the esound daemon running with all those program set to output to esound/esd? I doubt it..

People seem to be getting esound confused with just running ALSA. esound is rarely needed anymore. Pulse has an esound module that converts the output of programs using esound to whatever pulse uses. When you remove pulse, you might install the esound daemon (though you probably don't need it) to satisfy dependencies. Actually running esd and having programs output to it takes more work than just removing pulseaudio.

This is all I did.

sudo apt-get remove pulseaudio
sudo apt-get install esound
sudo rm /etc/X11/Xsession.d/70pulseaudio
reboot

The crackling and popping went away after doing this.

---

### Post by budde on 2010-01-26
> **Temüjin said:**
> If you removed pulse, install the gnome packages from: [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)


They should once you install gnome-settings-daemon from the above repo.

Works perfectly with ALSA aswell! After I removed Pulse to install ALSA, the volume icon in the notification area was gone - and wouldn't start due to "lack of Pulse". This helped, even though it's the "old" volume bar. Thank you!

Just one question: is it possible to make it use the new notification system? When I change the volume with my keyboard shortcuts it shows the "old" notification - see attachment. Would be nice if I could force it to use notify-osd somehow. 

Any ideas?

---

### Post by khtaam on 2010-12-04
Quite an old thread but I found it because of the ppa. 
The gnome-settings-daemon should be patched to use the notify-osd.

But I wrote a small script that uses amixer to adjust the volume of Master channel and show the level with notify-osd.


```
#!/bin/bash
CTRL=Master

if [ "$1" == 'up' ]; then
    VOL="4dB+"
    amixer -c 0 set $CTRL $VOL > /dev/null
    if [ $(amixer sget $CTRL | grep Mono: | cut -c22-24) == 100 ]; then
	PERCENTAGE=101	
    else
        PERCENTAGE1=$(amixer sget $CTRL | grep Mono: | cut -c21-23)
   	PERCENTAGE=${PERCENTAGE1//[ %\[\]]/}
   fi
elif [ "$1" == 'down' ]; then
    VOL="4dB-"
    amixer -c 0 set $CTRL $VOL > /dev/null
    PERCENTAGE1=$(amixer sget $CTRL | grep Mono: | cut -c21-23)
    PERCENTAGE=${PERCENTAGE1//[ %\[\]]/}

elif [ "$1" == 'mute' ]; then
    VOL="toggle"
    amixer -c 0 set $CTRL $VOL > /dev/null
    PERCENTAGE=0
    
    
else 
    echo "Available options: up, down, mute"
    exit
fi

if [ $PERCENTAGE -lt 10 ];then
    ICON=audio-volume-muted
elif [ $PERCENTAGE -lt 25 ];then
    ICON=audio-volume-low
elif [ $PERCENTAGE -lt 75 ];then
    ICON=audio-volume-medium
else
    ICON=audio-volume-high
fi

notify-send "Volume" -i $ICON -h int:value:$PERCENTAGE -h string:x-canonical-private-synchronous:
```

save it in a place thats in your $PATH, like /usr/local/bin, and make executable.
Disable the default shortcuts and add custom shortcuts with the script with up, down and mute as options.

btw, thanks for the ppa, really makes a difference on a netbook.

---

### Post by Resting_stage on 2011-05-04
This is a great script! Now all my special keys are working on a HP Mini 5103 with Chrunchbang installed.
Two minor things, though:

When I turn the volume down to zero, I cannot turn it up again.
When I unmute the volume, the notification bar still shows a muted volume.

Cheers!

---

### Post by colo505 on 2011-07-25
I get the following error on running the script:

[: 28: unexpected operator
[: 28: unexpected operator
[: 28: unexpected operator
Available options: up, down, mute

Can you help me?

Thanks

---

### Post by beew on 2011-07-25
This is a very old thread and the script worked for Ubuntu9.04 or 9.10, both of which are dead. I would be quite surprised if it works for 11.04.

Why do you remove pulseaudio anyway?

---

### Post by colo505 on 2011-07-26
Because I get no sound using an optical (TOSCON) cable, while I do in Win7.

---

