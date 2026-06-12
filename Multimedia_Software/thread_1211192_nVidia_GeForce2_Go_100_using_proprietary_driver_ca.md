---
title: "nVidia GeForce2 Go 100 using proprietary driver cause blank screen"
date: 2009-07-12
forum: Multimedia Software
---

### Post by nipponese on 2009-07-12
I am using a Ubuntu 9.04 on a Dell Inspiron with an NVIDIA GeForce2 Go 100. Using the default video driver, everything works well, but after installing the proprietary nvidia driver I only get a blank black screen after the Ubuntu loading screen.

From what I am reading on the forums, I guess this is caused by xorg.conf because I can reboot into recovery mode and use xfix to restore the file into a working state.

Can anyone help me out with this? I am kinda lost when it comes to xorg.conf or display drivers in linux.

These are the specs on the integrated video card: [http://support.dell.com/support/edocs/systems/ins2600/en/sm_en/specs.htm#1119628](http://support.dell.com/support/edocs/systems/ins2600/en/sm_en/specs.htm#1119628)

---

### Post by HappyFeet on 2009-07-12
You are better off staying with the default drivers. If you were looking for a performance boost, well, let's just say that a gforce2 is not going to be fast no matter what.

Start computer, and hit escape before grub loads. You wil see recovery mode. Choose that. After computer loads, you will eventually come to a command prompt. Log in.

Then do 
```
sudo nano /etc/X11/xorg.conf
```
Be mindful that the above X11 is with a **capital X**.

With the arrow keys, (the left part of the screen may not be showing, therefore you may not see the blinking cursor. Just hit the right arrow until you see the blinking cursor) navigate to the "driver" section. Change **nvidia** to **nv**. Do Ctrl+x, then y, and hit enter. Then ```
sudo reboot
```

If for some reason, the above does not work, you can change **nvidia** to **vesa** and see what happens.

---

### Post by Ian Ferguson on 2009-07-14
I'm having the same problem with a GeForce 4 440 GO (64MB).

When I do the above, there is no driver section in Xorg.conf. When I run nvidia-xconfig, I get the following:

```

ian@Fergubuntu:~$ sudo nvidia-xconfig
[sudo] password for ian: 

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

ian@Fergubuntu:~$ 

```So how do I get the right driver line into xorg.conf?

---

### Post by hackerlife on 2009-08-12
I too am having more or less the same issues.
I have a Dell Inspiron 2650, with the nVidia Geforce2 Go, and when I used the proprietary drivers, I would get a black screen on boot up, and would have to do and ctrl-alt-bckspc to get my screen to work. I also had frequent freezeups.

I decided to disable the driver, and all is well...
mostly...
Now I can't play Starcraft! (and I miss compiz)

I'm kinda a noob, how do I install/enable "default drivers"?

Or is that what I use when I disable the prop drivers?
Thanks for all the help, best of luck to all of you
-Will

---

### Post by mishdanicko on 2009-09-14
> **nipponese said:**
> I am using a Ubuntu 9.04 on a Dell Inspiron with an NVIDIA GeForce2 Go 100. Using the default video driver, everything works well, but after installing the proprietary nvidia driver I only get a blank black screen after the Ubuntu loading screen....
I had a similar problem with a GeForce 4 TI 4200 card.  I didn't exactly find a complete solution, but I did find a work-around.

I found that I could still log in at that blank black screen if I just entered my username and password as if everything was normal.  Other than this login screen issue (i.e. once your desktop loads) the proprietary driver has worked very well for me.  So, I figured changing the login window might solve the problem.

Assuming you can still log in at that black screen like I could, then, when your desktop comes up, Click System > Administration > Login Window.  Click the "Local" tab.  Select "Plain" from the "Style" menu.  Select a solid color for the background.  I'm not sure if this was necessary, but I deselected the logo and the title bar.

Now, the login screen is visible, but it's just a plain dialog box.  Unfortunately, it still displays at very low resolution, which makes it hard to read, but it's a damn sight better than a blank black screen.

If anyone has a better mousetrap, however, I'd love to hear about it.

---

### Post by imnotjack on 2010-10-30
Hey all. I'm having trouble with the same thing, can't remember what model it is. I can switch to terminal mode using ctrl - alt - F1
I can then login and all that. I try to install proprietary drivers after install and I have a gui then but after the install I am limited to the command line mode. on another hdd witch is in and running with the proprietary drivers on the same computer I have working graphics. (I'm actually running on it right now) I can do all the editing from this one. so one install works with proprietary drivers and the other one, Same operating system and same computer setup on a dual boot, does not work with proprietary drivers. it looks like the GUI is trying to load but messed up because I can see colors at the top of the screen and when doing things it seems to change color. and its not like interactive static its like I can see one line of pixels across the top of the screen. Hope this helps. I'm tired right now and the info may be a little jumbled but at least its not misspelled ( thanks to spell check) :)

---

