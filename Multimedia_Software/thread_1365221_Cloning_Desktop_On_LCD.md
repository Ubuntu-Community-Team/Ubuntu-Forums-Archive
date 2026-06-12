---
title: "Cloning Desktop On LCD"
date: 2009-12-26
forum: Multimedia Software
---

### Post by JASONATRON on 2009-12-26
Hi,

I am having trouble with getting Ubuntu 9.04 to work the way that I want with my LCD television.  I have a nvidia 8500 gt video card and toshiba television.  I have up to date nvidia drivers for my card.  I am connecting to the television using HDMI.  I would like the television to be a clone of my desktop.  This so far has been impossible.  I have used the nvidia gui to edit the Xorg config file, but it never seems to get it right.  I do the following:

enable toshiba display, choose twin view for both displays, for position I choose clone for both displays, save to the xorg file, restart x.

Then instead of having an exact replica of my computer screen on my TV (which is what I want), I have on my television a version of my desktop which takes up the upper left corner of my television, and on my desktop I have just a section of my actual desktop so that if I open say a web browser only a corner of the window will appear and on my tv it appears centered (and the resolution is way off,even though it is set to auto in the nvidia gui). Also my mouse arrow can go off of the computer screen quite a bit, exploring areas of the television that aren't viewable on the monitor

Any Ideas about what is going on? or suggestions about how to get nvidia video cards to clone the desktop??  Thanks in advance.

---

### Post by HappyFeet on 2009-12-27
Twinview does not clone desktops. It only extends your desktop to span across 2 monitors.

Do:
```
gksudo nvidia-settings
```
and choose your settings from there. Apply and save. If it "fails to parse...." then follow the directions below.

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

### Post by JASONATRON on 2009-12-27
Regarding Twin-View.  Using the nvidia gui the only options for cloning are under Twin-View.  Is this correct?
Assuming so...

I set the settings to this.  Setting both displays to:
 (twin-view-->Clone) not (separate x display-->Clone)
because the former does not exist.

Then I applied the settings, saved to the xorg file and restarted x.

I got the parse error so I removed the xorg file and repeated the above steps.  This time upon restart I get two error messages.  The first says:"Warning:Screen isn't composited.  Please run compiz (-fusion) or another compositing manager."

I run gksudo nvidia-settings and get the second: "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server." 

I ran "sudo nvidia-xconfig" I get an output stating that a new x file was written.  So I restart and go back to the nvidia gui and none of my previous settings are saved.

What should I do now?

---

### Post by JASONATRON on 2009-12-29
Anyone?

---

### Post by HappyFeet on 2009-12-29
Did you install the nvidia drivers?

---

### Post by JASONATRON on 2009-12-30
Yes, the drivers are up to date.  There definitely seems to be something wrong with the driver though because every time I set the settings to clone both displays it just doesn't work.  I will click apply and nothing happens, meaning that it doesn't prompt me to restart x or save the x conf file or anything; and then if I restart nvidia settings it will be back on the previous setting.  Any ideas?? thanks in advance.

---

### Post by JASONATRON on 2010-01-06
So, can anyone help? this is the only thing holding me back from completely switching to Linux.  Right now anytime time I want to watch a movie or stream videos from the internet and watch on my lcd I have to reboot into windows which really sucks. :(

---

### Post by TidyBhoy on 2010-01-06
Sorry to come in on your post without any help, but i'm in a similar boat I think.

I to have my Samsung LCD TV Connected to My laptop Via HDMI, and like you its probably the only reason i'm still dual booting.

I have my laptop Cloned no problem but its just that the quality is far from the standard of windows Vista when playing back DVD's, in fact even the desktop doesn't look as crisp as it should. I mean by that just the TV Quality is lacking, looking at my laptop screen here is perfect apart from I'd like to change the resolution and make things smaller.

My graphics Card is an ATI Mobility Radeon HD 3650, and i have installed the Catalist Control Centre from the Ubuntu Software Centre (im on 9.10 btw). i notice that in the display manager of that theres a couple of settings grey'd out, which i thought was a bit strange.. i cant change the resolution for example.

I'm just praying here that some genius is able to tell be some method of boosting my performance in this area.

Thanks.

---

