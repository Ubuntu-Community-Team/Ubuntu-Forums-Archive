---
title: "Pulse Audio Equalizer Install"
date: 2017-04-15
forum: Multimedia Software
---

### Post by tf4545 on 2017-04-15
Hey Folks,

I have run into an issue installing Pulse Audio Equalizer in Ubuntu Gnome 17.04.

I installed the app through Synaptic which worked without a hitch. No errors or the such. The icon for the Equalizer appeared in my Activities Overview with my other apps just fine. No problems at all until I did a re-boot on my system. At that point the icon disappeared in the overview and I'm not able to launch the Equalizer via a command line as that tells me it is an invalid command.

The Pulse Audio is still running as I see than in listed Processes in the System Monitor but not the Equalizer which is running as the sound from my speakers dictate that I'm not hearing the normal un-equalized sound.

Question being-How can I get the icon to return to my installed apps so I can interact with the setting of the Equalizer?

Thanks in advance for the help!!!!!!

---

### Post by #&amp;thj^% on 2017-04-15
Please remember this is no longer maintained.
But maybe this may give us a clue:
```
qpaeq
```
return the output from the terminal here please.

---

### Post by tf4545 on 2017-04-15
The output of

```
qpaeq
```

resulted in

[HTML]There was an error connecting to pulseaudio, please make sure you have the pulseaudio dbus module loaded, exiting...[/HTML]

Also, I wasn't aware that this was unsupported. The only real reason I installed it was because I was hoping to have the ability to tweak the sound when using Firefox. Chrome/Chromium have a equalizer add-on but Firefox does not.

Thanks for the quick reply!

---

### Post by Yellow Pasque on 2017-04-16
Try this:
```
pactl load-module module-dbus-protocol
qpaeq&
```

---

### Post by tf4545 on 2017-04-16
Open Terminal, and ran the following:

[HTML]pactl load-module module-dbus-protocol[/HTML]

Which resulted in:

[HTML]Failure: Module initialization failed[/HTML]

Then I ran:

[HTML]qpaeq&[/HTML]

Which resulted in an equalizer app opening with the title in the window "qpaeq" which is farther than I've been and cool!

In that window, the Sink is listed as "ladspa_output.mbeq_1197.mbeq.equalizer", the Channel is default to "All", and there is nothing in the pull down for Presets.

When I manipulate the equalizer there is no difference in the sound coming from my speakers but the sound is not an un-equalized track. When I adjust the volume, the volume pop-up shows me "LADSPA Plugin Multi..." 

Any other ideas?

Thanks for all the help!

---

### Post by Yellow Pasque on 2017-04-16
> **tf4545 said:**
> In that window, the Sink is listed as "ladspa_output.mbeq_1197.mbeq.equalizer" ...
When I manipulate the equalizer there is no difference in the sound coming from my speakers but the sound is not an un-equalized track. When I adjust the volume, the volume pop-up shows me "LADSPA Plugin Multi..."
I thought the ladspa mbeq module was for the older pulseaudio equalizer (don't quote me on that though). Were you trying to use/install any other equalizers before you installed pulseaudio/equalizer package? 

> and there is nothing in the pull down for Presets.
IIRC, there are no presets with the newer pulseaudio equalizer.

I hope someone who actually uses pulseaudio and the EQ can help you. I don't use pulse in my main system and I don't use EQ's.

---

### Post by tf4545 on 2017-04-16
> [COLOR=#000000]Were you trying to use/install any other equalizers before you installed pulseaudio/equalizer package?[/COLOR]

I have not installed or tried using any other equalizer other than the add-on extension in Chrome.

---

### Post by #&amp;thj^% on 2017-04-16
Like I said eariler this is no longer maintained...But I also edited /etc/pulse/default.pa

And Added this to it:
open file /etc/pulse/default.pa with root privilage:
```

sudo nano /etc/pulse/default.pa
```

Find line with load-module module-udev-detect, and then add** "tsched=0.**" Do it to the next line with command load-module module-detect like below:

```
    
### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect tsched=0
.else
### Use the static hardware detection module (for systems that lack udev/hal support)
load-module module-detect tsched=0
.endif
```
Then reboot and then deleted everything in :
~/.config/pulse via:
```
rm -rf ~/.config/pulse
rm -rf ~/.pulse
```

Now Pulseaudio is still kind of flakey...so you may also need to restart it.

```
pulseaudio --start
```

---

### Post by Yellow Pasque on 2017-04-16
Well, I played around with it in my Xubuntu VM and got it working. Don't ask me exactly how. I know I had to load the dbus module, start qpaeq, load the equalizer module, and then manually set the new equalizer sink using pacmd (couldn't set it in the volume control). Maybe see the 'configuring' section here: [https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/Equalizer/](https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/Equalizer/)

Quite frankly, I feel for folks trying to get this working. Having an easily-installable GUI EQ in Ubuntu is long overdue. Having to edit config files is probably beyond a lot of users' grasp. I really hope I'm just misunderstanding this and/or it's easier to use the EQ in the Unity desktop. *Shrug*

---

### Post by Yellow Pasque on 2017-04-16
> Like I said eariler this is no longer maintained...
What is no longer maintained? The older pulseaudio GUI EQ is no longer maintained. Using the qpaeq GUI on top of the built-in equalizer module should be maintained, unless I missed something. Heck, qpaeq was just added to the repo in 17.04

---

### Post by Frogs Hair on 2017-04-16
Non official package use with caution if needed.
[http://www.webupd8.org/2013/10/system-wide-pulseaudio-equalizer.html](http://www.webupd8.org/2013/10/system-wide-pulseaudio-equalizer.html)

---

### Post by #&amp;thj^% on 2017-04-16
> **Temüjin said:**
> What is no longer maintained? The older pulseaudio GUI EQ is no longer maintained. Using the qpaeq GUI on top of the built-in equalizer module should be maintained, unless I missed something. Heck, qpaeq was just added to the repo in 17.04

Here we go again...[http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html](http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html)
> Please note that PulseAudio Equalizer is no longer maintained so if you find a bug or if it doesn't work for you and the fix isn't trivial, there's nothing I can do. 
That's the last word I have to date.
...BTW who am I helping you or tf4545? :confused:

---

### Post by Frogs Hair on 2017-04-16
> **1fallen said:**
> Here we go again...[http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html](http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html)

That's the last word I have to date.
...BTW who am I helping you or tf4545? :confused:

Happens to work here , but I've been lucky.


> Please note that PulseAudio Equalizer is no longer maintained so if you find a bug or if it doesn't work for you and **the fix isn't trivial,** there's nothing I can do.
[COLOR=#222222][FONT=Verdana][/FONT][/COLOR]


[COLOR=#333333][FONT=Arial][/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2017-04-16
> **Frogs Hair said:**
> Happens to work here , but I've been lucky.




If it decides to crap out on anyone,...I usually have good luck with this:
```
killall pulseaudio
pulseaudio --start
``` 

And on rare occasions just delete pulse folder in ~.config/pulse
```
rm -rf ~/.config/pulse
rm -rf ~/.pulse
killall pulseaudio
pulseaudio --start
```

One Line at a time.

Hope this helps someone.

---

### Post by Yellow Pasque on 2017-04-16
> **1fallen said:**
> Here we go again...[http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html](http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html)
That's the last word I have to date.

..and it's from 2013. That's outdated information AFAICT. Yeah, you used to have to get a 3rd-party PPA version of pulseaudio that was built with the EQ module enabled. Ubuntu 17.04 now builds pulseaudio with the equalizer and it's split off into a separate **official** package (pulseaudio-equalizer). You don't need unofficial PPA's nowadays.

```
pulseaudio (1:9.0-5ubuntu3) zesty; urgency=medium

  * Re-add pulseaudio equalizer package, my understanding on build deps with
    main/universe wasn't quite correct, and I only dropped it to get the
    package through proposed, so a demotion of the equalizer package to
    universe is the better solution

 -- Luke Yelavich <themuso@ubuntu.com>  Wed, 23 Nov 2016 09:49:51 +1100
```

> ..BTW who am I helping you or tf4545?

You're certainly not helping me, but maybe the OP will find your info useful.

---

### Post by tf4545 on 2017-04-17
> [COLOR=#000000]Quite frankly, I feel for folks trying to get this working. Having an easily-installable GUI EQ in Ubuntu is long overdue. Having to edit config files is probably beyond a lot of users' grasp. I really hope I'm just misunderstanding this and/or it's easier to use the EQ in the Unity desktop. *Shrug*[/COLOR]

This is my sentiment, without question!

I installed stock Ubuntu 17.04 (Unity) on a separate machine and got it to work wonderfully. Just can't get it running on my main machine with Gnome 3.24/17.04.

I also tried installing the PPA from WebUpd8 and still no go. This really is a tester of patience. I guess I could always install stock 17.04 then install Gnome on top of it but all that pain isn't worth it at this point. I am going to live with the EQ in Chrome for the time being. I may keep playing around with the steps put forth in this thread but it won't be at the top of my to-do list.
[B]
I cannot tell you folks how much the help has been appreciated![/B]

At this point how should I mark this thread? It's not really solved as I'm just not going to continue.

Thanks!

---

### Post by #&amp;thj^% on 2017-04-17
> **Temüjin said:**
> ..and it's from 2013. That's outdated information AFAICT. Yeah, you used to have to get a 3rd-party PPA version of pulseaudio that was built with the EQ module enabled. Ubuntu 17.04 now builds pulseaudio with the equalizer and it's split off into a separate **official** package (pulseaudio-equalizer). You don't need unofficial PPA's nowadays.

```
pulseaudio (1:9.0-5ubuntu3) zesty; urgency=medium

  * Re-add pulseaudio equalizer package, my understanding on build deps with
    main/universe wasn't quite correct, and I only dropped it to get the
    package through proposed, so a demotion of the equalizer package to
    universe is the better solution

 -- Luke Yelavich <themuso@ubuntu.com>  Wed, 23 Nov 2016 09:49:51 +1100
```



Ok... good to know, Sometimes us testers are the last to know about these changes.:(

> **Temüjin said:**
> 

You're certainly not helping me, but maybe the OP will find your info useful.
Mea culpa....Bad day yesterday.:oops:

---

### Post by tf4545 on 2017-04-17
Hey Folks!

Well...I decided to have one last shot at this.

What I did was reverted all changes I had made. Did a re-boot then followed the instructions here:

> Here we go again...[http://www.webupd8.org/2013/03/insta...in-system.html]("http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html")

Which got qpaeq installed beautifully. I then fired up Synaptic and installed menulibre which allowed me to add an icon to my Activities overview.

The only down side is that the EQ does not have any presets (which are usually fairly good) but I am able to adjust the EQ and save my own presets.

Cool!

At this point I am going to say this is solved with a good alternative. Maybe not exactly what I was hoping for but it works and works well.

Is this sufficing for me to mark the thread as solved?

---

