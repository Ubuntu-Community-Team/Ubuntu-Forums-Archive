---
title: "Changing master monitor in dual set-up"
date: 2009-10-31
forum: Multimedia Software
---

### Post by ssherlock on 2009-10-31
I need help tweaking my dual monitor set-up:

On previous versions my dual screens were fine - I had my 19" monitor as the main screen and the laptop as the secondary. Since upgrading to 9.10 though (from 9.04) the laptop has become the main screen and the 19" the secondary i.e the Ubuntu menu's and clock etc all show on the laptop and I'd like all that on the 19" monitor if possible.

I'm sure I'm doing something daft and this will be easy but how can I swap them round again?

---

### Post by GonZo on 2009-11-02
Same issue!

I've got a desktop computer with two flat monitors, previous configurations worked fine. Now, ubuntu 9.10 decides that smaller monitor is the master and I can't change it.

There must be a checkbox on each Screen Configuration window with the text "This is the main screen"

---

### Post by dro0g on 2009-11-02
I haven't found a way to do it through the GUI. I'm working with a laptop that has an internal screen and two external monitors, one on DVI and one on VGA. From the command line:

Shut off the internal screen:
```
xrandr --output LVDS1 --off
```

Shut off the secondary:
```
xrandr --output VGA1 --off
```

Set the DVI interface as primary:
```
xrandr --output DVI1 --auto --primary
```

Enable the secondary and put it to the right of the primary
```
xrandr --output VGA1 --auto --right-of DVI1
```

This works for me and keeps the panels, icons, etc. on the DVI monitor. Hope this helps.

---

### Post by ssherlock on 2009-11-02
Brilliant thanks, that worked a treat.

Simon

---

### Post by Donalb on 2009-11-03
This sounds like my (and some others) problem also.

However before I try it, can someone tell me what happens after doing this when/if the laptop is restarted without the External monitor connected? Will the Laptop screen then become (only) primary screen? As was the case previously for me in Intrepid before a Karmic install?

Thanks.

Oh, btw, I assume you mean from command line outside the gnome desktop? (I know, this may be Duh! question)

---

### Post by ssherlock on 2009-11-03
> **Donalb said:**
> However before I try it, can someone tell me what happens after doing this when/if the laptop is restarted without the External monitor connected? Will the Laptop screen then become (only) primary screen? As was the case previously for me in Intrepid before a Karmic install?

I just rebooted without the external monitor and the laptop works a treat. Plugged it back in, rebooted and all fine again.

> **Donalb said:**
> Oh, btw, I assume you mean from command line outside the gnome desktop? (I know, this may be Duh! question)
I did it from a normal terminal window on the Gnome desktop.  I would add that I needed to run the command on it's own to display my monitor types first as they weren't exactly as above.

---

### Post by Donalb on 2009-11-04
Again, thanks. But when I went to do it I realised I didn't know the command to display my monitors first?

My search-fu skills aren't finding anything, probably because the search terms are too generic.

I've never edited (or even looked at) xorg.conf. ( I can cut & paste commands but that's about it.)
Now I understand it's no longer present anyway.  Can you illuminate further?

Thanks in advance.

---

### Post by ssherlock on 2009-11-04
> **Donalb said:**
> Again, thanks. But when I went to do it I realised I didn't know the command to display my monitors first?
Just *xrandr* on it's own will list the monitors (you may need to use sudo but I can't remember.

There was no need to edit any files - I can't pretend I fully understand how it works but I'm happy it did!

---

### Post by Donalb on 2009-11-04
Ok, bear with me if that's ok?

xrandr give me;

```

donal@donals-e6400:~$ xrandr
Screen 0: minimum 320 x 200, current 2560 x 1024, maximum 8192 x 8192
VGA1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      75.0*    60.0  
   1024x768       75.1     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     60.0  
   720x400        70.1  
LVDS1 connected 1280x800+1280+0 (normal left inverted right x axis y axis) 304mm x 190mm
   1280x800       60.0*+   40.0  
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
DP3 disconnected (normal left inverted right x axis y axis)
TV1 disconnected (normal left inverted right x axis y axis)
```

My ext. monitor isn't connected on HDMI but VGA.

So the  Commands, switching off the internal & external should be fine?
(I'm extrapolating here from what you wrote).

Switch off VGA & Laptop screens:
```

donal@donals-e6400:~$xrandr --output LVDS1 --off

donal@donals-e6400:~$xrandr --output VGA1 --off

```

Then I should make the VGA primary like this?:

```

donal@donals-e6400:~$xrandr --output VGA1 --auto --primary

```

Then enable laptop screen? Any need to specify it on the right (since that's where it is)?
```

donal@donals-e6400:~$xrandr --output LVDS1 --auto --right-of VGA1

```

OR

```

donal@donals-e6400:~$xrandr --output LVDS1 --auto

```

Which one?

I'd input it first myself but I'm afraid of screwing up something and not being able to see anything so I'm taking it slowly/carefully. 

Thanks for your continued patience. (I think this post will end up being a good answer thread for this problem for other non-terminal types like myself).

---

### Post by ssherlock on 2009-11-04
I must admit to just playing with it until I got it working how I wanted so may have exhausted how much help I can be.  It only ever blanked one screen at a time for me but that may also have been more good lick than good management...

---

### Post by mozillalives on 2009-11-04
I had this same problem too. I had to change a few things but this is what finally worked.

my output of xrandr was 

VGA1 connected 1920x1080+1600+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080      60.0*+
   1280x1024      75.0  
...blah blah blah...
LVDS1 connected 1600x1024+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1920x1200      60.0 +   49.8  
   1600x1200      85.0     75.0     70.0     65.0     60.0  
...blah blah blah....

VGA1 is my secondary monitor (which I use as my primary) and LVDS1 is my laptop display.

After shutting off both screens (doh!) I ran a couple of tests to be sure I was talking to the right screen.

```
xrandr --output VGA1 --off
```

turned my secondary off and 

```
xrandr --output VGA1 --auto
```

turned it back on. Tried the same with the other and verified that it was LVDS1.

So my final script was 

```

xrandr --output LVDS1 --off;
xrandr --output VGA1 --off;
xrandr --output VGA1 --auto --primary;
xrandr --output LVDS1 --auto --right-of VGA1;

```

Which puts my secondary monitor as the primary one (and restores the panel and main menu and all that jazz).

I saved that in a file named switch.bash and ran it by typing

```
bash switch.bash
```

HTH

---

### Post by Donalb on 2009-11-05
Dro0g, Mozillabeans & SSherlock, 

I want to have your babies!

;)

Yes this worked perfectly. Although after running the script the UI resized itself to a 3 x 2 inch square portion of UI, too small to do anything, but I did a CTRL/ALT/Backspace Logout and back in and it was back the way I wanted it. External LCDprimary active & laptop secondary.

Thanks very much guys.

NOTE: Karmic has the CTRL/ALT/Backspace DISABLED but I had already re-enabled it.

Before running the (or similar) script, just is case it can be re-enabled through System>Preferences>Keyboard -> LAYOUTS Tab onder the Options.

Anybody creating their first script Like I did for this, save the text file, then set the executable permissions, Then it's run by prefacing the filename with ./ 
i.e.
```
./bash_dislay.sh
```

---

### Post by ajesh on 2009-12-07
It works for me, but I have to run the script every time I log in to set up the dual monitors like I want.

It seems from the thread that for others the monitor setup is saved. Do you know how I can achieve this?

Thanks

---

### Post by HappyFeet on 2009-12-08
Do:
```
sudo rm /etc/X11/xorg.conf
```
then restart nvidia-settings with:
```
gksudo nvidia-settings
```
then make all the changes you need, apply, then save configuration, and it will see you don't have a xorg.conf file. A new window will open. Hit the button lableled **show output**, and copy the file. Leave nvidia-settings open, and open a new terminal. Do:
```
sudo touch /etc/X11/xorg.conf && sudo gedit /etc/X11/xorg.conf
```
then paste what you copied from nvidia-settings. Save and reboot.

---

### Post by Donalb on 2009-12-08
It's been fine for the past 2 weeks for me. One of the updates obviously fixed it, but I can't tell you which. I no longer have to run the script.

---

### Post by m0sand on 2010-10-11
Thanks for the script! It works like a charm, except it seems my main desktop now seems to have been pushed one pixel to the right creating a one pixel space and a weird graphical bug/line at the left of my screen. 

I'm using a ATI Mobility Radeon HD 5850 card, and I'm wondering why ATI just can't get it right with the dual monitor set up.

---

