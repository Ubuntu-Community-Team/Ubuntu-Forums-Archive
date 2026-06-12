---
title: "few dual monitor questions"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by Hardnuttywutty on 2007-05-07
I have a geforce 6600 pci-e card which has dual dvi slots, I have 2 monitors but one is vga so I just need an adapter, but when I plug the dvi monitor into the other dvi slot it doesn't work, is this just because it's a secondary one and will only work once I have my other monitor in the dvi adapter?

Also can you plug in 2 mice and use one for one screen one for the other?

Regards

Pete.

---

### Post by RTrev on 2007-05-07
> **Hardnuttywutty said:**
> I have a geforce 6600 pci-e card which has dual dvi slots, I have 2 monitors but one is vga so I just need an adapter, but when I plug the dvi monitor into the other dvi slot it doesn't work, is this just because it's a secondary one and will only work once I have my other monitor in the dvi adapter?

Also can you plug in 2 mice and use one for one screen one for the other?

Regards

Pete.

Hi,

I've got a similar setup, with a GeForce 7300 GT with dual digital outputs driving two identical flat panels.

You're right.. the second monitor won't display much except plain text until you get the Twinview set up.  Mine just duplicates the other screen while the BIOS text displays, but as soon as we shift into a graphics mode there is nothing but gibberish.

It isn't so much having the other monitor hooked up, as having the Twinview enabled.  While I was clearing space for the second monitor, I just used one of them plugged into the first output of the card.  I believe that should work for you too.

I assume you're planning on using Twinview?  If so, there's no need for two mice.. and I can't think of any way to do it anyway.  If you just move the mouse off one display it appears on the other one.  It's simple and intuitive.  If you maximize a window, it stays on the single monitor its currently on, and you can drag windows and icons around as if it were all one big monitor.

I think you're going to enjoy it!  :)

---

### Post by Nythain on 2007-05-07
hehe... left out the important part of running
gksudo nvidia-settings
to enable and set up the twinview, or dual x screens WITH xinerama (unless you are me, then without is exactly what the doctor prescribed, oh yeah)

---

### Post by RTrev on 2007-05-07
> **Nythain said:**
> hehe... left out the important part of running
gksudo nvidia-settings
to enable and set up the twinview, or dual x screens WITH xinerama (unless you are me, then without is exactly what the doctor prescribed, oh yeah)

I figured we could get into that stuff once he has both monitors hooked up and running.  

BTW, since you jumped in and sound like you've got the tee-shirt, there's something I haven't solved yet.  When I turn on "Coolbits" I can run sudo nvidia-settings and set the card slightly over-clocked.  It claims it's saved the data, and it appears to have, but nothing I've tried will preserve the setting across a reboot.  People say to run something like "nvidia-settings --load-config-only" as part of the login, but that doesn't work.  Have you solved this one yet?

Thanks,
Bob

---

### Post by olafbooij on 2007-05-09
Hi,

I can maybe give you some advice on the nvidia-settings --load-config-only not loading your saved configuration (although you should really see me as a newbie!).

I have a monitor and tv hook up to my pc and set my system up using the "NVIDIA TV-OUT for Newbies HOWTO". The standard nvidia settings makes the picture on my tv quite dark and reddish. So I used nvidia-setting to make it better and saved the settings (by default to ~/.nvidia-settings-rc). Then after a reboot (well, usually a hibernate) I used 
 nvidia-settings --load-config-only
to load my correct configuration.

But since a few months this stopped working... I do not know why, probably a bug introduced by one of the updates, or me breaking something in my system.
The strange thing is that if I start nvidia-settings again, it does automatically load the configuration of my first DISPLAY (my monitor) and after I change one random setting of my second DISPLAY (my tv) it all of a sudden remembers all my settings and all is okay. Strange...

This can also be done automatically without using the gui as I found out an hour ago:
```

nvidia-settings --load-config-only
# hmmm the nvidia-settings --load-config-only does not seem to load the
# config file...
# I have to explicitly set some values.... 
# first set some value of my TVDISPLAY wrongly:
nvidia-settings --assign=:0.1/TVOverScan=15
# then change it back to the right value
nvidia-settings --assign=:0.1/TVOverScan=16

```

Try it out, maybe maybe maybe it works....

Greets,
Olaf

---

### Post by RTrev on 2007-05-09
> **olafbooij said:**
> Hi,

This can also be done automatically without using the gui as I found out an hour ago:
```

nvidia-settings --load-config-only
# hmmm the nvidia-settings --load-config-only does not seem to load the
# config file...
# I have to explicitly set some values.... 
# first set some value of my TVDISPLAY wrongly:
nvidia-settings --assign=:0.1/TVOverScan=15
# then change it back to the right value
nvidia-settings --assign=:0.1/TVOverScan=16

```

Try it out, maybe maybe maybe it works....

Greets,
Olaf

Thanks, Olaf!  I will give this a try.  But as a newbie, I'm not sure -- is this the /etc/X11/xorg.conf file that we put this type of code in?  Or some new file we need to create and include in our startup somehow?

Thanks again!
Bob

---

### Post by olafbooij on 2007-05-09
Sorry, I'm so used to command-line hacking, I forget that most people aren't. I'm on the other hand a newbie with regards to graphical interfaces, the reason for using ubuntu is because this is actually my wifes computer... so try to bear with me...

First of all: the code is not meant for the /etc/X11/xorg.conf . It is meant to be executed on the command prompt or put in a new script (or for example in an xinitrc file).

But first things first:
Do you have the same strange behaviour of nvidia-settings remembering your configuration after you change one of the attributes at random.

To test:
-Restart (or hibernate) your computer so the settings are forgotten.
-start nvidia-settings and see if the picture on tv/monitor changes
-change one of the sliders in the tv-section and see again if the  picture on tv/monitor changes
-report...

Olaf

---

### Post by RTrev on 2007-05-09
> **olafbooij said:**
> But first things first:
Do you have the same strange behaviour of nvidia-settings remembering your configuration after you change one of the attributes at random.

To test:
-Restart (or hibernate) your computer so the settings are forgotten.
-start nvidia-settings and see if the picture on tv/monitor changes
-change one of the sliders in the tv-section and see again if the  picture on tv/monitor changes
-report...

Olaf

Okay, but I have flat panel displays, and everything gets set right whether I run nvidia-settings or not.  So, I deliberately changed one setting so that both of my screens were very dark.  Quit from nvidia-settings, rebooted, and everything looked normal until I ran the nvidia-settings --load-config-only, or until I ran it interactively.  Then it resumed the settings I had monkeyed around with.  Soi that part is good news.

However, there is one single thing I do want to change, and that's the optimal clock frequency to run the GPU and memory at.

So, when I changed some of the screen color, it remembered the change and applied it immediately upon being run.  But when I enable the over-clocking, it does NOT save and restore that setting for me.

By the way, I realized something I guess I was doing wrong.. I was running *sudo* to start nvidia-settings, and I think now that I shouldn't have been.  But either way, it will save and restore the settings except for the single one I want to change.  

I've heard that this program is a bit buggy.. perhaps that's what we're seeing here?

Thanks again.. you've been very patient with this beginner!

---

### Post by olafbooij on 2007-05-09
Okay, thanks for trying out! It seems that we indeed have different problems. But maybe I can help you anyways.

The problem as I understand it is that one of the settings is not loaded while the rest is. And then you have to run the nvidia-settings gui to set that setting after every reboot. 

There is however probably also a way to set it from the command-line (or script) using something like this:
 ```

nvidia-settings --assign=<your display>/<some attribute>=<some value>

```

You can place this line in the same place (after it) as you placed the 
nvidia-settings --load-config-only
line. Or run it in a terminal of course (do you know how?).

The hard part is finding out the < ... > I guess. Probably something like this:
```

nvidia-settings --assign=:0.1/GPUCurrentClockFreqs=<some value>

```
just guessing!

Whoops... sorry, my spare times is up. Will continue this evening...

Olaf

---

### Post by RTrev on 2007-05-09
> **olafbooij said:**
> Okay, thanks for trying out! It seems that we indeed have different problems. But maybe I can help you anyways.

The problem as I understand it is that one of the settings is not loaded while the rest is. And then you have to run the nvidia-settings gui to set that setting after every reboot. 

There is however probably also a way to set it from the command-line (or script) using something like this:
 ```

nvidia-settings --assign=<your display>/<some attribute>=<some value>

```

You can place this line in the same place (after it) as you placed the 
nvidia-settings --load-config-only
line. Or run it in a terminal of course (do you know how?).

The hard part is finding out the < ... > I guess. Probably something like this:
```

nvidia-settings --assign=:0.1/GPUCurrentClockFreqs=<some value>

```
just guessing!

Whoops... sorry, my spare times is up. Will continue this evening...

Olaf

Okay, with your help I now have a file which works when run!  It looks like this:

```

# Set the NVIDIA GeForce 7300 GT video overclocking rates
nvidia-settings -a GPUOverclockingState=1
nvidia-settings -a GPU2DClockFreqs=350,439 -a GPU3DClockFreqs=399,439

```

Now I just have to figure out where to put it and what to call it.  :)

That part should be easy after the rest.  

Thanks again!!

---

### Post by olafbooij on 2007-05-10
Okay, great.

You can put those lines in the same file as you placed the
nvidia-settings --load-config-only line.
Normally this is your ~/.xinitrc file (i think). Or the system-wide one: /etc/X11/xinit/xinitrc

Olaf

---

### Post by RTrev on 2007-05-10
> **olafbooij said:**
> Okay, great.

You can put those lines in the same file as you placed the
nvidia-settings --load-config-only line.
Normally this is your ~/.xinitrc file (i think). Or the system-wide one: /etc/X11/xinit/xinitrc

Olaf

Perfect, problem solved!  Thank you very much, Olaf!

---

