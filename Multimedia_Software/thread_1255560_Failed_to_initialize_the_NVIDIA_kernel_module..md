---
title: "Failed to initialize the NVIDIA kernel module."
date: 2009-09-01
forum: Multimedia Software
---

### Post by bertles86 on 2009-09-01
Hi folks,

[B]
EDIT:[/B]


I've got a totally fresh install, and have installed the latest updates but my display is very choppy. Whenever I open a new app, or minimise/maximise something **vertical or horizontal lines** appear on the display.

I thought it might be the refresh rate so I changed it from 75Hz to 60Hz but no change.

Any ideas?

---

### Post by bertles86 on 2009-09-02
Edit: see above.

---

### Post by bertles86 on 2009-09-02
Edit: see above.

---

### Post by bertles86 on 2009-09-02
Bump - please help!!

---

### Post by bertles86 on 2009-09-02
Would installing Envy fix this?

---

### Post by RedRat on 2009-09-02
> **bertles86 said:**
> Would installing Envy fix this?

it certainly might help. However, remember when you run anything to do with graphics, you need to run it with sudo or gksudo from the command line, otherwise the settings don't stick.

---

### Post by bear24rw on 2009-09-02
what does System > Admin > Hardware Drivers  say? Maybe you need some drivers. what graphics card do you have?

---

### Post by bertles86 on 2009-09-03
I'm running a Nvidia Geforce 7600GS from Inno3D.

I've installed EnvyNG from the Synaptic Package Mgr, it now shows up in Apps>Sys Tools.

Sys>Admin>HW Drivers shows no drivers installed, because last time I tried the 180 is when everything went tits up!

So can I not just use Envy from the menu and install a driver, or should I run it from terminal?

---

### Post by RedRat on 2009-09-03
Run envyng from the command line using sudo or gksudo command with it:
```
sudo envyng
```

or 
```
gksudo envyng
```

Also download nvidia-settings and install it. Run it also with the sudo or gksudo command. 

When you run the nvidia-settings it should set the proper resolution.

---

### Post by bertles86 on 2009-09-03
Thanks redrat, I ran EnvyNG with sudo and installed the 180 series drivers which are the recommended ones. All installed fine, restarted and it all went tits up again.

Monitor went into standby repeatedly and eventually a dialog popped up saying Ubuntu is running in low res mode. Then it says:

> There already appears to be an X server running on display :0. Should another display number be tried? Answering no will cause GDM to start the server on :0 again. 

Yes or No?

Thanks for any help in getting my display working!

---

### Post by RedRat on 2009-09-03
> **bertles86 said:**
> Thanks redrat, I ran EnvyNG with sudo and installed the 180 series drivers which are the recommended ones. All installed fine, restarted and it all went tits up again.

Monitor went into standby repeatedly and eventually a dialog popped up saying Ubuntu is running in low res mode. Then it says:



Yes or No?

Thanks for any help in getting my display working!
Did you run nvidia-settings? Use sudo or gksudo. It is nvidia-settings that write to the xorg.conf file but only when run with sudo or gksudo.

---

### Post by bertles86 on 2009-09-03
Ah ha no I did not, can I do from command line from the grub as my desktop is not loading?

---

### Post by bertles86 on 2009-09-03
Ok from the root login I've done this:

> sudo envyng --uninstall-all

Now I'm going to do this:

> sudo envyng

Followed by:

> sudo nvidia-settings

---

### Post by bertles86 on 2009-09-03
Right I've sudo envyng -t on the command line all good, but when I:

sudo nvidia-settings

I get:

> ERROR: The control display is undefined; please run 'nvidia-settings --help' for usage information.

Any help on running this?

---

### Post by bertles86 on 2009-09-05
Bump - any ideas on how to get this working?

---

### Post by RedRat on 2009-09-05
> **bertles86 said:**
> Right I've sudo envyng -t on the command line all good, but when I:

sudo nvidia-settings

I get:



Any help on running this?

OK, I am confused here. Here is what you posted:
Ok from the root login I've done this:

Quote:
sudo envyng --uninstall-all
Now I'm going to do this:

Quote:
sudo envyng
Followed by:

Quote:
sudo nvidia-settings 

Ok, it looks as if you uninstalled envyng in the first command. Then you "ran" envyng (second quote). what did you get when you ran that command? It should have given you a GUI with choices of what driver to install, for me it was 175.xxx or 180.xxx. You click on one of them. Did that happen?

Once the driver is installed, then you run nvidia-settings. That should have changed your resolution and you can also put your monitor type in there too.

---

### Post by bertles86 on 2009-09-06
Yes I uninstalled because I installed from synaptic, whereas you said to install it on the command line. So I removed it, then reinstalled it, *then* ran it with sudo envyng.

Then it all installed fine, and said to reboot. I did so and Ubuntu entered low graphics mode. I got onto a terminal as the desktop GUI would not boot, and entered sudo nvidia-settings and it would not run saying my display has not been setup correctly.

Since then I have decided (Sadly may I add) to return to XP, as graphics simply do not work on Ubuntu - for my card at least. I'll back one day when Ubuntu's stable for sure as it's a nice OS barring the bugs with graphics etc.

One thing that did throw me, is why on earth does an OS require you to install graphics drivers on the command line? And how come the drivers installed during install of the OS will not work well enough? That's a major stumbling block for me!

---

### Post by RedRat on 2009-09-06
> **bertles86 said:**
> Yes I uninstalled because I installed from synaptic, whereas you said to install it on the command line. So I removed it, then reinstalled it, *then* ran it with sudo envyng.

Then it all installed fine, and said to reboot. I did so and Ubuntu entered low graphics mode. I got onto a terminal as the desktop GUI would not boot, and entered sudo nvidia-settings and it would not run saying my display has not been setup correctly.

Since then I have decided (Sadly may I add) to return to XP, as graphics simply do not work on Ubuntu - for my card at least. I'll back one day when Ubuntu's stable for sure as it's a nice OS barring the bugs with graphics etc.

One thing that did throw me, is why on earth does an OS require you to install graphics drivers on the command line? And how come the drivers installed during install of the OS will not work well enough? That's a major stumbling block for me!

I know this is frustrating because I had similar problems in updating from 7.10 to 8.04. Everytime a new kernel change came out, I had to go through this damn graphic tomfoolery. As I have said before, if Ubuntu and Linux has a singular fault, it is dealing with graphics. Here we have leading graphic card maker like Nvidia and they do make Linux drivers, and we still seem to have problems getting these to work smoothly. I would hope that the developers of Ubuntu would take some time and see if they can straighten this messy business out. Believe me, it has improved since my update to 8.04 but it really does need some attention. I think Linux/Ubuntu loses a significant number of people like you just because of this problem. Nevertheless, I encourage you to stick to it if you can, but i certainly understand your mood.

Added comment: I was just reading something in the Ubuntu newsgroups. At least for one poster there, he found that switching to a different distro, some of his multimedia problems seemed to have eased. He also complained of difficulties in that videos that he watched flawlessly in 7.10 got worse in 8.04 and even worse in 9.04. He tried a less demanding windows manager than Gnome, Fluxbox. You might want to look into perhaps using Mint, which seems to be a bit better. You might find that graphics might be a tad better.

---

