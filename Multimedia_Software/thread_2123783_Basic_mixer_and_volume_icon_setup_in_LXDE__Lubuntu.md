---
title: "Basic mixer and volume icon setup in LXDE / Lubuntu / Peppermint etc."
date: 2013-03-08
forum: Multimedia Software
---

### Post by billyb351 on 2013-03-08
I've installed a Debian based LXDE based distro (Peppermint which is itself based on Ubuntu) on an older laptop recently with pretty ancient hardware (circa 2005~2006).  I've been very impressed with LXDE.  It's faster than WinXP ever was on this machine, but the only thing that I was disappointed with was the audio.  It worked, and that was about it.  There was no mixer and the volume icon in the task bar didn't do much.  Over about 2 months, I've gotten it to the point where I'm happy with it.  The help on "pretty-fying" the sound in LXDE was fairly sparse.  I wrote this because I like LXDE and I want to help people avoid frustration with it.  The sound control is the only major drawback that I saw, and hopefully this will solve that problem.

LXDE is lightweight and the default installed sound support is VERY lightweight too.  This write-up is meant to keep things lightweight too, i.e. not installing Pulse audio and all the bells and whistles that come with it.  If you want all that, this write-up is not for you.  I'm gearing this towards those who install LXDE by necessity, because their hardware won't run Gnome or Unity or Cinnamon very well.  By default, ALSA provides the sound functionality in these LXDE distros and we are going to stick with that.  First, we need a mixer.  For that, I use "xfce4-mixer".  It's from the XFCE desktop, but it's pretty lightweight and works just fine for our purposes.

```
sudo apt-get install libasound2-dev
sudo apt-get install xfce4-mixer
```

At this point, a sound mixer is installed, but the volume icon still doesn't work right. I found a replacement volume icon.

Disable the default volume icon.  Remove it from the task bar by right clicking somewhere on the task bar, then Add/Remove panel items... then just disable it.

The rest of this write-up is more or less based on what I found at these two sites:
[http://softwarebakery.com/maato/volumeicon.html](http://softwarebakery.com/maato/volumeicon.html)
[http://mapopa.blogspot.com/2011/11/volumeicon-xfce-mixer-part-two-better.html](http://mapopa.blogspot.com/2011/11/volumeicon-xfce-mixer-part-two-better.html)

Before building and installing the new volume icon, make sure these basic things are installed.
```
sudo apt-get install gcc
sudo apt-get install pkg-config
sudo apt-get install libgtk2.0-dev
sudo apt-get install gstreamer0.10-alsa
```

I think these are all the packages you need... along with the two above.  if you find one I missed, please post.  I did this on Peppermint which is probably slightly different than Lubuntu.  If you find any discrepencies, please say so.

Now, download the volume icon source from the first site.  Version 0.4.6 is the last version based on GTK2 (this is the one you want).  Starting with 0.5.0, you need GTK3.

Attached here as well:
[ATTACH]239949[/ATTACH]

Extract volume icon tar file (where * is the version you downloaded):
    ```
gunzip volumeicon-*.tar.gz
tar -xvf volumeicon-*.tar
cd volumeicon-*
```

Then:

    ```
./configure --prefix=/usr
make
sudo make install
```

If multiple sound cards:

    ```
cat /proc/asound/cards
    0 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                         HDA ATI HDMI at 0xfeaec000 irq 44
    1 [default        ]: USB-Audio - Microsoft LifeChat LX-3000 
                         Microsoft LifeChat LX-3000  at usb-0000:00:1d.2-1, full speed
```

    ```
vim ~/.config/volumeicon/volumeicon
    [Alsa]
    card=hw:1
```

You can start volumeicon simply by:
    ```
volumeicon &
```

After the volumeicon is started, right click and in preferences:
    Change channel to be: "PCM"
    Change external mixer to be: "xfce4-mixer"
Choose your icon theme... I personally like "Blue Bar" as the blue bar next to the volume icon in the system tray changes with the volume level.

Now, make the Multimedia Hot Keys work correctly (if you don't have special volume up/down/mute hot keys on your machine, skip this).
Open:
    ~/.config/openbox/rc.xml (Pure LXDE/Debian/Lubuntu)
    ~/.config/openbox/peppermint-rc.xml (Peppermint)

Search for "XF86Audio" and there should be three entries.
Compare and change them to this:
    ```
<!-- Keybinding for Volume management -->
    <keybind key="XF86AudioRaiseVolume">
         <action name="Execute">
             <!-- 'amixer -q sset Master 3%+ unmute' does not work correctly -->
             <command>amixer -q sset PCM 3%+ unmute</command>
         </action>
    </keybind>
    <keybind key="XF86AudioLowerVolume">
         <action name="Execute">
             <!-- 'amixer -q sset Master 3%- unmute' does not work correctly -->
             <command>amixer -q sset PCM 3%- unmute</command>
         </action>
    </keybind>
    <keybind key="XF86AudioMute">
         <action name="Execute">
             <!-- 'amixer -q sset Master toggle' can be set here as well if this prooves insufficient -->
             <command>amixer -q sset PCM toggle</command>
         </action>
</keybind>
```

The actions are by default set to operate on the "Master" channel which is not the
true volume. To make the hot keys work right, they need to control the PCM channel.

Add the volume icon to startup session so it starts as soon as you login.
If on pure LXDE/Debian
    ```
vim ~/.config/lxsession/LXDE/autostart
    #add to the file
    @volumeicon
```

If you are on Lubuntu
    ```
vim ~/.config/lxsession/Lubuntu/autostart
    #add to the file
    @volumeicon
```

If you are on Peppermint
    ```
vim ~/.config/lxsession/Peppermint/autostart
    #add to the file
    @volumeicon
```

By default when you click on volume icon it mutes the sound card so in preferences i put Left Mouse Button Action to open the Slider And the Channel will be PCM.

At this point, you can restart the computer and all the changes should take effect.  The volume icon should appear in the system tray.  A single left mouse click on the volume icon will produce a slider.  Right clicking it will give you a menu where you can open the mixer if you like.  The multimedia hot keys if you have them should now also work and control the PCM volume, and mute.

A few more notes... The volume icon seems to actively use about 20 MB of RAM on average.  The xfce4-mixer seems to use about the same.  If you can't spare 40 MB of memory, perhaps you don't need sound control... you might need a new computer.

---

