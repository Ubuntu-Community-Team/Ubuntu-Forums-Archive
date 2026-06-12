---
title: "Dual Monitors displayed as one large &quot;Laptop&quot; Display"
date: 2012-07-29
forum: Multimedia Software
---

### Post by iSephy on 2012-07-29
I just want to preface this with the fact that the people on these forums have always been VERY helpful, and that's why I come back to request help again.

I recently came back to Ubuntu after a long stint with Windows 7, as I learned that gaming with Steam was now a very viable possibility. I have an nVidia GTX 550 Ti graphics card with two Dual-Link DVI monitors (Acer S202HL) attached.

When I open the System Settings and go to Displays, there is one large display labeled "Laptop." The resolution is accurate for two 1600x900 monitors next to each other (3200x900), but they should be appearing as separate monitors, should they not? I have installed the current nVidia drivers and the cutting-edge (beta, I would suppose) drivers. I can configure the two monitors separately with no troubles there. 

Now comes the real problem; the combined display wouldn't be a problem if it didn't prevent me from playing CoD:MW2 in any resolution than 3200x900. I tried forcing the resolution from the config file, but it resets to 3200x900 every time. When the game is fullscreen, the game fills the leftmost monitor (the one I want it to be on), but I can't move my cursor past the halfway point of the screen; it "glitches" over to my second monitor and gets stuck. When I press Alt+Enter to send the game into windowed mode, the window is full size at 3200x900. I can pull it across both, monitors, but I would like to be able to have either the game windowed at a smaller resolution or fullscreen in a normal way.

---

### Post by Laiquendi on 2012-07-29
1. You have ubuntu 9.10 as it is written in your profile? If yes then it's way too old to work properly with newest devices...
2. You're playing through wine? If yes then try with wine configuration.

---

### Post by iSephy on 2012-07-29
No, sorry, I'm running 12.04 with all the latest updates. I haven't been on the forums since 2010 or so. I've tried messing with Wine, but to no avail. I remember seeing something about games stretching about dual monitors, but I can't seem to find it no matter how much Google-fu I use.

---

### Post by apollothethird on 2012-08-16
> **iSephy said:**
> No, sorry, I'm running 12.04 with all the latest updates. I haven't been on the forums since 2010 or so. I've tried messing with Wine, but to no avail. I remember seeing something about games stretching about dual monitors, but I can't seem to find it no matter how much Google-fu I use.

I'm plagued with the same.  I doesn't have anything to do with Wine because I don't use Wine.  I have changed and tested the two "Additions Drivers" option.  That doesn't fix it.

I'm running the latest of all driver updates on Ubuntu 12.04.

I never experienced this problem with any of the previous Ubuntu versions.

The nVidia setting tool shows the monitors as to distinct objects.  But Ubuntu's system display settings shows the two monitors as on large laptop screen.

This flaw is causing the mouse to be stuck between displays.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by smartboyhw on 2012-08-16
It shouldn't be a problem using 12.04. It is improved now, the drivers were better too.

---

### Post by apollothethird on 2012-08-16
> **smartboyhw said:**
> It shouldn't be a problem using 12.04. It is improved now, the drivers were better too.

I agree.  It shouldn't be a problem, especially 4 months of release, bug fix and tweaking.  I'm really surprised there isn't a solution.

Since Ubuntu's display settings doesn't see two monitors there no relief from the stuck mouse between display syndrome.  Having to fight the to get the mouse to the alternate screen is extremely disruptive to my work flow.

After the fight to get it to the next screen (because I have to jerk it to get it there, then I have to spend time to find out where it appears.  There are times that moving it puts it back to the wrong screen and I have to start the struggle over to get it to the desired screen.

I can't imagine anyone seeing a stickiness between screens as productive in any way.  I wish I could see the developers trying to work with dual monitors, who what they see in designing stickiness when trying to switch.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by naviathan on 2012-08-16
The reason it shows as one large display is because of nVidia Twinview.  Search the menu for Nvidia and open the settings app.  Click on the X Server Display Configuration and change the Configurations: option on both monitors to Separate X Screen.  That will split the two screens up in the Displays app.

---

### Post by apollothethird on 2012-08-16
> **naviathan said:**
> The reason it shows as one large display is because of nVidia Twinview.  Search the menu for Nvidia and open the settings app.  Click on the X Server Display Configuration and change the Configurations: option on both monitors to Separate X Screen.  That will split the two screens up in the Displays app.

I did that once and lost a lot of functionality.  It took me about an hour to get it back.

I never could get Unity-3d to work with the "Separate X" screen so I eventually put it back to twin view.

I'll try it again and let you know if it works.  I'll try to organize the problems in cause someone here can identify why I can't have a workable environment with the Separate X option.

By the way, my video card is the GeForce GTX260.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by apollothethird on 2012-08-16
> **naviathan said:**
> The reason it shows as one large display is because of nVidia Twinview.  Search the menu for Nvidia and open the settings app.  Click on the X Server Display Configuration and change the Configurations: option on both monitors to Separate X Screen.  That will split the two screens up in the Displays app.

Naviathan.  Thanks for the tip.  I'm trying your advice.  At present I'm in the Separate X configuration.  I backed up my xorg.conf to a special file so that I can recover back to what was working if I can't get the separate X to work.

Here's where I am now:

* Boots to Unity-2d.  The last time I used the option to force Unity-3d and the system wouldn't boot.  So this time I'll try working with the drivers to see if I can get Unity-3d to working.

Also:

* Ubuntu's Display Settings doesn't work.  When trying to bring it up I get a popup that says:

```

Could not get screen information
RANDR extension is not present
Close
```

I'll eventually buy a new Video card if that's the problem.

By the way, the sticky between monitors isn't happening.  I'm almost considering weighing which is worst, living with the poor driver display and no stickiness or the stickiness.

Thanks in advance for any suggestions.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by apollothethird on 2012-08-17
> **naviathan said:**
> The reason it shows as one large display is because of nVidia Twinview.  Search the menu for Nvidia and open the settings app.  Click on the X Server Display Configuration and change the Configurations: option on both monitors to Separate X Screen.  That will split the two screens up in the Displays app.

Naviathan, thanks again for the input.

After having spent a number of hours with the Separate X configuration, I have resolved that, there are problems with that option and my system.  Unity-3d will not work in that environment.  Also, as I mentioned the Ubuntu's system settings also fails with the RANDR error message.

I changed nvida drivers.  That didn't help.  I added the line, "UNITY_FORCE_START=1" to the /etc/environment configuration.  This gave me no Unity-2d or Unity-3d.  I had to cntrl-alt-F1 to get to a terminal window to remove the configuration and reboot to make the system usable. 

I went back to the Twin View configuration which takes fuller advantage of my video adapter and allows the functionality of Unity-3D.  I'll revisit Separate X if someone has some information that make make it work.

I have resolved to make a workaround that I can live with in the meantime.  I changed the compiz settings to (Unity Plugin/Experimental):

```

Launcher Monitors: Primary Desktop

```

This seems to have removed the stickiness between the Monitors.

After having been plagued with the problem for over a year I'm surprised that I haven't seen this fix in any of the suggestions.  I had been using the popular suggestion to lower "Edge Stop Velocity".  However, the problem with that was that by the time the value was low enough to resolve the issue, you had to fight to get the menu on the left monitor.

Anyway, I hope the developers work out the problem with not recognizing the dual monitors under the Twin View option.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by draxbear on 2012-10-30
Just found post on here that put me in the right screen to remove the annoying "sticking" when mousing between screens.

[LIST=1]
[*]Click on the "gear" icon (used to logoff or power off)
[*]Select "Displays"
[*]Change sticky edges to OFF
[*]Change launcher placement to "laptop" from all displays (might be optional)
[*]Apply changes (OMGYAY!)
[/LIST]

---

