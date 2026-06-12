---
title: "My GeForce 9500 GT Video Card is running slow!"
date: 2009-07-10
forum: Multimedia Software
---

### Post by LHalladay on 2009-07-10
I don't know much about how all this stuff works, but I am working for a company using Adobe After Effects and they have built a computer for me.  It is supposed to be a really fast computer and they put a graphics card in it that is called GeForce 9500 GT.  All of the drivers have been installed, but it is still running slow.

Like I said, I don't know much at all about this stuff, so if anyone could provide me with a detailed step-by-step solution, that would be extremely wonderful.  Thank you!

---

### Post by dE_logics on 2009-07-10
Download your driver from this list - 

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

And download it to your desktop

Then goto applications>accessories>terminal

Then type 'cd /home/<your user name>/Desktop'

Next command will be './name of the file you downloaded with the extension'

There will be a wizard shown up...if it says that the drivers cannot be installed at this state, just quit the installer.

Then again in terminal type - 

```

sudo /etc/init.d/gdm stop

```

This will end your GUI...and you'll be completely in command line.

Now again do this - 
```

./name of the file you downloaded with the extension

```

Go through the wizard...and you should be done.

Then type in 'sudo /etc/init.d/gdm start'...to restart the display and reboot.

That should work.

---

### Post by dE_logics on 2009-07-10
The above is suppose to be applicable if the graphs are slow.

Exactly what is slow?

---

### Post by dE_logics on 2009-07-10
That software does not come for Linux.

You're using windows, or making it work through wine.

If its working through wine, it WILL be slow.

---

### Post by LHalladay on 2009-07-10
I'm using 32 bit Vista on this PC.  I'm more used to a Mac, and it sounds like that's what your directions were for, as "terminal" is a Mac thing as far as I know.  How would I do this on a PC?  Sorry I didn't mention this before.

The thing that makes me say the graphics card is slow is when I move something on the screen it is jumpy, or glitchy.  This is especially true in After Effects when I'm trying to preview what I'm working on.  Thanks again!

---

### Post by LHalladay on 2009-07-10
Does anybody know??  This is really pretty frustrating.  When I try to preview my videos in After Effects, they don't show smoothly.  As of right now, I have to export to a QuickTime Movie if I want it to look right.  I don't want to have to export every time I want to see what I've done.

---

### Post by dE_logics on 2009-07-11
This is not the right place, you're not using Ubuntu...in this place we discuss linux, you're using mac or Windows...none of them is Linux.

---

