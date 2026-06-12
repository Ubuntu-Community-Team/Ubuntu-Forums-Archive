---
title: "Cannot change resolution in 14.01.1 (nvidia)"
date: 2014-10-05
forum: Multimedia Software
---

### Post by Elwro on 2014-10-05
I just upgraded from 13.10 to 14.04.1; I'm using the nvidia drivers.

My monitor is LG Flatron W1943S, 1440x900. Already in 13.10 after booting the corners of the display were not visible; I had to run nvidia-settings -> X Server Display Configuration -> Resolution -> Auto -> Apply and only then the corners of the display were aligned with the corners of the screen. (Saving into configuration files had no effect, I had to do this every time after startup.)

I upgraded hoping this issue would have been fixed.

To my dismay I discovered that it's actually worse: I still have the display problem, but running the procedure outlined above ends with the following error message:

```
The program 'nvidia-settings' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 538 error_code 2 request_code 157 minor_code 25)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```
So after upgrading I'm stuck with a badly displaying screen. Of course, all applications display badly, too. (E.g. portions of buttons are hidden.)

What should I do? Thanks in advance!

---

### Post by cfultz on 2014-10-05
No solution, but you are not alone. I'm in the same boat atm. Tried using xrandr to set the config to no avail. Good luck and godspeed!

Just wondering, is your computer booting into "nomodeset" from the GRUB? Mine was and now that I've changed it to quiet splash, rebooted, and set the Nvidia driver (340), logged out, I have more settings to chose from!

---

### Post by Elwro on 2014-10-05
> **cfultz said:**
> Just wondering, is your computer booting into "nomodeset" from the GRUB? Mine was and now that I've changed it to quiet splash, rebooted, and set the Nvidia driver (340), logged out, I have more settings to chose from!Mine has been set to quiet splash for a long time now. I thought it just meant I wouldn't see many starting messages?

Nvidia-settings, apart from telling me "error querying target relations" on start but starting anyway, does show me a lot more options than in 13.10.

Thanks to your pointer I did find out that my installation is using a 'legacy binary driver' from nvidia, 304. The highest option in the 'software & updates' -> 'proprietary drivers' menu is 331.38. I will choose that and see what happens.

---

### Post by Elwro on 2014-10-05
PARTIAL SUCCESS: namely,things are back to how they were in 13.10. In my case setting the drivers to 331.38, rebooting and running nvidia-settings again had the effect of it displaying
 
** Message: PRIME: No offloading required. Abort
** Message: PRIME: is it supported? no


but starting anyway; then I set the display to 'Auto', hit 'apply' and I now have a nice-looking screen. I 'save it to the default configuration file'. We'll see if it works after a reboot. Fingers crossed.

edit: nope, the change is not remembered. I'll have to do this every time after reboot again.

Another bit of info: right after reboot xrandr reports the dimensions of the screen to be "410mm x 260mm". After the screen is 'fixed', xrandr reports "410mm x 256mm". This has to be wrong, since I see that initially the screen is too wide and according to xrandr the change is only in the vertical dimension. Anyway, it would be good to know how to make the system remember the "410mm x 256mm" information.

So now my 2 questions are:

1) What the correct way of saving the video configuration after changing the resolution? (Which file is the one to write to?) /etc/X11/xorg.conf is not it.
2) Suppose I know the precise dimensions of my screen (e.g. from nvidia-settings -> X Screen 0 or from xrandr) in milimeters. Is there a way of 'hardcoding' this information into some configuration file?


I hope you'll have some progress with you issue too, cfultz! Fingers crossed!


(Incidentally, the clock again appears in the top bar about every second reboot (instead of always). Even that hasn't been fixed, and it's 14.04.1 already!)

---

### Post by Elwro on 2014-10-06
I hope I'll be forgiven for making another post on this.

So, I inserted the '410 256' screen dimensions by hand to xorg.conf (section Monitor, option DisplaySize). No change.
Right after startup, xrandr reports dimensions as 410x260, while nvidia-settings reports them as 381x238. Weird!

So to repeat my current question: what is the graphical config file read by 14.04.1 on startup when a proprietary nvidia driver is in use?


edit: there seems to be something wrong with how nvidia-settings writes to config files! Namely, whenever I xave the data to file 'a', a NEW FILE 'a.backup' is created WITH THE NEW INFORMATION while the old file 'a' is left intact! I found out while editing the XF86Config file; unfortunately, this isn't it, too.

---

### Post by Elwro on 2014-10-06
So yeah, I guess in this thread I will be documenting my fascinating adventures into the mess which is the nvidia relationship with X.

Today I learned that the system has an X log file (yeah, I'm a newbie I guess), in 14.04.1 it is /var/log/Xorg.0.log. Now, this file can tell you for example which config file is used:
```
[    20.668] (==) Using config file: "/etc/X11/xorg.conf"
```
So at least I know that. Of course, I don't know what to write there.

But then there's another bit of info: when finally I set the screen properly using nvidia-settings, the log file contains the following line:
```
[  1070.108] (II) NVIDIA(0): Setting mode "DPY-1:nvidia-auto-select+0+0"
```
So now the question is: where is a config file which contains a place in which I can write "DPY-1:nvidia-auto-select+0+0" so that the change is persistent? :-)

edit: I see that in xorg.conf the Screen section does contain the following:
    ```
Option         "metamodes" "nvidia-auto-select +0+0"
```

edit2: the command
  ```
nvidia-settings --assign CurrentMetaMode="nvidia-auto-select +0+0"
```
is doing the trick; however, I put it in ~/.xinitrc and it does not seem to be executed on starting X!

ALRIGHT! THIS IS THE COMMAND! But I have completely no idea where to put it so it would be ran when starting X. I tried ~/.xinitrc; I also even put it inside /etc/X11/xinit/xinitrc even though I felt like a sinner doing so. Anyway, it still does not work. What should I do?


edit3: I created a file 73nvidia-setup consisting of that single command and put it in /etc/X11/Xsession.d directory, because I thought Xsession would, on starting X, execute it. But it didn't. Any pointers would be greatly appreciated.

The way I'm restarting X is 
```
sudo restart lightdm
```

---

### Post by Elwro on 2014-10-07
OK, the issue is solved for me. In a dirty way.

If someone has a similar problem like, here's what I did:
1) created a file correctvideomode.sh (it can be whenever you want) consisting solely of the following line
```
nvidia-settings --assign CurrentMetaMode="nvidia-auto-select +0+0"
```
2) made it executable 
```
chmod +x correctvideomode.sh
```(ran from the folder with the file)
3) Found "Startup Applications" using the Windows key on my keyboard and typing the name; clicked "Add" and then under 'command' the following:
```
bash /path/to/my/file/correctvideomode.sh
```

Then my new 'startup application' went right to the top of the list and I couldn't do anything about it; I thought it should be after Nvidia X Server Setup but hey, it worked: because right now AFTER EACH LOGIN my screen looks correct.


Why is it 'dirty'? Because really the command should be ran everytime X starts, not everytime I login. But I spent a few hours trying to figure out how to make lightdm run it when starting an X session - with no result. So hey, at least I found out something that gives the correct result for me in a 'primitive' way. Who knows, maybe someone will benefit from this in the future.
(The key was looking at the end of the X log file after setting the mode correctly using nvidia-settings and discovering the command was listed as a 'metamode' in xorg.conf.)

---

### Post by matt_symes on 2014-10-07
Hi

> **Elwro said:**
> Why is it 'dirty'? Because really the command should be ran everytime X starts, not everytime I login. But I spent a few hours trying to figure out how to make lightdm run it when starting an X session - with no result. 

Check out the link below, specifically the section on system hooks. 

[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

Point display-setup-script to your script.

Kind regards

---

### Post by Elwro on 2014-10-07
> **matt_symes said:**
> Hi



Check out the link below, specifically the section on system hooks. 

[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

Point display-setup-script to your script.

Kind regardsThank you, but I did that (in [COLOR=#333333]/etc/lightdm/lightdm.conf)[/COLOR], and unfortunately it didn't work. (There was no difference in screen behaviour after logging out and back in.)

---

### Post by matt_symes on 2014-10-07
Hi

> **Elwro said:**
> Thank you, but I did that (in [COLOR=#333333]/etc/lightdm/lightdm.conf)[/COLOR], and unfortunately it didn't work. (There was no difference in screen behaviour after logging out and back in.)

Oh. That's a surprise.

Did you try this hook ? 

```
session-setup-script
```

Also try rebooting just in case.

Kind regards

---

### Post by Elwro on 2014-10-07
> **matt_symes said:**
> Hi



Oh. That's a surprise.

Did you try this hook ? 

```
session-setup-script
```

Also try rebooting just in case.

Kind regardsThanks for the suggestion. I just tried that -- it also doesn't work! (I rebooted.) This is 14.04.1 64-bit. I doublechecked the path to the script, and that the script really does his job when ran. I would be happy to try if you have any other suggestions!

---

### Post by matt_symes on 2014-10-07
Hi

> **Elwro said:**
> Thanks for the suggestion. I just tried that -- it also doesn't work! (I rebooted.) This is 14.04.1 64-bit. I doublechecked the path to the script, and that the script really does his job when ran. I would be happy to try if you have any other suggestions!

Well you have tried just about everything i would have from a custom xorg.conf file to creating a script and calling it from the various system hooks.

I can only assume it's some vagary of the nvidia driver and that's a driver i have not used since 2011.

Still you have a work around so all is not lost.

Kind regards

---

### Post by SeijiSensei on 2014-10-07
I just experienced the problem in the original post.  It appears to be a versioning conflict between the driver itself and the nvidia-settings application.  On my 14.04 system, the driver was using nvidia-304, but nvidia-settings was at version 331.  I solved the problem by first uninstalling all the nvidia items, then using
```
sudo apt-get install nvidia-331
```
rather than using "nvidia-current" as I normally do.  The driver worked fine with this machine, a rather old ASUS 1201n with an Ion processor that is equivalent to the 9500GT series of adapters.

I have a suspicion that it's a packaging problem either from Debian or Canonical.

---

### Post by Elwro on 2014-10-10
> **SeijiSensei said:**
> I just experienced the problem in the original post.  It appears to be a versioning conflict between the driver itself and the nvidia-settings application.(...)Thanks! Unfortunately right now I won't try your solution since I shouldn't risk any video catastrophe in the coming days and so I will not remove the drivers, but I will check this in the future.

---

