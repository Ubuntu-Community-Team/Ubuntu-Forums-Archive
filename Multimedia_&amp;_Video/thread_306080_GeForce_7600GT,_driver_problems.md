---
title: "GeForce 7600GT, driver problems"
date: 2006-11-24
forum: Multimedia &amp; Video
---

### Post by maniacmusician on 2006-11-24
Okay so I just scored a brand new 7600GT, and tossed it into my box. I used automatix bleeder to install the latest nvidia drivers (the beta ones), and I have to say, it's not working out too well. I have a feeling that it's a conflict with kde. When I open the display configuration module, it still shows the computer as using the "nv" driver.  There's an option showing "standard driver" and one for "proprietary driver" but they're both grayed out; but standard is selected. and I can't change it.

So I'm in a pickle. Is it just the way that automatix installed it? I hope so. I'm off to try it manually. If anyone can help, please reply.

Some additional info;
-my highest resolution is limited to 1280x1024, no matter what I put in xorg.conf
-whenever i put in a query that requires the use of the graphics card, such as glxgears or glxinfo, the fan on the card starts spinning very fast (i'm assuming it's the fan making the noise) and doesn't stop till I restart the computer. couldn't this be dangerous for the card?

So yeah, any help would be appreciated.

edit: updating with a list of what's going wrong:
-when queried with glxgears or glxinfo, fan starts up, very noisy, and doesn't stop until at least the X-server is restarted (or in about 5 minutes)
-glxgears gives out a very very low fps (around 60)
-The resolutions are all screwed up. I can set the resolution at 1280x1024 using Nvidia Settings, but that doesn't stick. Next time I log in, either after a restart or just logging out and back in, the settings are all screwed up again. 
-when the computer first starts up, the fan on the card is really loud for about 2 seconds. Not critical, but a bit annoying.
-KDM Resolution is f*cked up. have to scroll sideways to be able to see all of it
-Splash screen (after kdm) is screwed up, same as KDM

To be honest, after all the trouble I had with ATI, I was hoping Nvidia would be a breeze. So this is a bit of a bummer. C'est la vie, I guess. All I can hope is that it's easily mendable.

---

### Post by Stealth on 2006-11-24
And in your xorg.conf it says its using "nvidia" right?

---

### Post by maniacmusician on 2006-11-24
Yes, it does.

edit: I have tried to install the drivers in the method prescribed by tseliot in the sticky at the top of this forum (Please help us test ATI/NVIDIA drivers), and am getting the same results. It seems to be the same method used by AX_Bleeder.

---

### Post by maniacmusician on 2006-11-25
using dpkg-reconfigure xserver-xorg, I can regress back to the nv driver, which gives me a higher resolution, but this is something I could do even with my ATI card, and I obviously didn't spend money on an nvidia card just to have the same experience. Mainly I want 3d acceleration, and done decently. 

I also tried to do a dpkg-reconfigure xserver-xorg and choose the nvidia driver but that gives the same results as well.

edit: just tried it again and it is now doing something different....it's decreasing the horizontal screen size and increasing the vertical...so everything looks smushed into the middle of the screen and when I bring my mouse to the top or bottom of the screen, it scrolls that way. I think the nvidia driver is creating its own screen and placing everything inside of it?

edit again: okay, I've played around with the "nvidia settings" tool. I've gotten it to display at 1280x1024, but I'd really like at least 1400x1050.

Also, when I click on "OpenGL/GLX Information" the fan on the card started spinning like crazy, making lots of noise, and it's still doing that, even though I've lowered it back to quality. [COLOR="Red"]**"How Do I Make it Stay Quiet?"**[/COLOR], I guess would be another essential question. i also updated the first post.

thanks.

---

### Post by tseliot on 2006-11-25
> **maniacmusician said:**
> -The resolutions are all screwed up. I can set the resolution at 1280x1024 using Nvidia Settings, but that doesn't stick. Next time I log in, either after a restart or just logging out and back in, the settings are all screwed up again.
launch it with sudo (otherwise your settings will not be permanent):
```
sudo nvidia-settings
```

---

### Post by maniacmusician on 2006-11-25
sorry that didn't work. I ran it using sudo, Changed everything, and when I restarted X, it was all crapped out again. 

I really never imagined it would be such a pain. People should stop spreading propaganda about how Nvidia is really easy to set up ](*,) I got my hopes up lol.

---

### Post by maniacmusician on 2006-11-25
I think I figured out the problem. When I run sudo nvidia-settings, I get erros:

```

ERROR: Cannot open display 'Alexis:0.0'.


ERROR: Unable to assign attribute DigitalVibrance specified on line 19 of configuration file '/home/user/.nvidia-settings-rc' (no Display connection).

```

and it repeats that second error for every single value in the .rc file. No Display connection? Why can it not open the display?

edit: tried the [fix at this thread]("http://ubuntuforums.org/showthread.php?t=221408") but it didn't work.

---

