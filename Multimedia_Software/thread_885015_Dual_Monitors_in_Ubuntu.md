---
title: "Dual Monitors in Ubuntu"
date: 2008-08-09
forum: Multimedia Software
---

### Post by Pippinuk on 2008-08-09
Instructions to setup multiple monitors in Ubuntu (this has tested in 8.04 but should work in earlier versions)

Open the Synaptic Package Manager

*System>Administration>Synaptic Package Manager*

Search for EnvyNG

Install the EnvyNG-core and EnvyNG-gtk

Once installed open EnvyNG:
*Applications>System Tools>EnvyNG*

Select either ATI or Nvidia (depending on your Graphics card) from the list on the left of the window.

Make sure that 'Install the Ati/Nvidia driver )Automatic Hardware Detection)' is selected and click *Apply*.

The installation will take place.  When complete reboot your system.

After reboot, login and go to *System>Administration>Nvidia X Server Settings*

This is where you will configure the displays.  If one of the monitors is disabled select it from the window at the top and click *'configure'*.  Now click *'Twinview'* and click *'OK'*.

Both monitors will now be enabled and you can set the desired position of each monitor in the window at the top of the 'Nvidia X Server Settings'. Make sure the you click the 'Make This The Primary Display For X Screen' for the display you want to use as Primary. 

By clicking each monitor you can then change the settings for each with the options available below. I advise you to set the resolution and refresh rate for each monitor.

When the settings are correct click *'Apply'* and the new config will be activated.  

Next click *'Save X Configuration File'*.  You need root privileges to do this so if you're logged on as a standard user I recommend the following:

Click *'Save X Configuration File'*.  Save the configuration to your desktop.  Close the Nvidia X Server Settings window.  Open a Terminal and run the following command:

sudo cp /home/*user*/Desktop/xorg.conf /etc/X11 
Enter your password

This will copy the Xorg.conf file to the correct directory.  Reboot your system.

PLEASE NOTE I'M A NEWBY - PLEASE FEEL FREE TO CORRECT THE ABOVE POST!

ENJOY

---

### Post by Huss on 2008-08-11
For those that have already installed a Nvidia driver:

Go to synaptic and install 'nvidia-settings' instead of envy.

---

### Post by lilbarba on 2008-08-11
i have set up my 2 monitors, but i can't get a higher resolutin on the second one (640x480 max) it's a 24" HD monitor it should get more ...

---

### Post by executedisaster on 2008-08-25
> **lilbarba said:**
> i have set up my 2 monitors, but i can't get a higher resolutin on the second one (640x480 max) it's a 24" HD monitor it should get more ...

Go into your NVIDIA XServer Settings, and check to see if the backend resolution is up to snuff. If they frontend resolution is not matching the backend this will tell you something is wrong. 

If this is the case I suggest uninstalling all nvidia drivers, both through Envy and through terminal, restart and reinstall the newest drivers from the nvidia site. 

I had some issues with 2 9600s that I am working through, and it has been an interesting battle to say the least :) Also, post your xorg.conf... and if you are using the Nvidia X Server Settings, make sure you run it from the terminal.

sudo nvidia-settings

Cheers.

---

### Post by d2globalinc on 2008-08-27
I have a good example of a 6 and 3 monitor setups complete with getting compiz-fusion effects working over in this other forum post in case anyone is looking - I know I scoured these forums looking for a solution - So my work is your gain! [http://ubuntuforums.org/showthread.php?t=884161](http://ubuntuforums.org/showthread.php?t=884161)

- Shane

---

### Post by padlefot on 2008-09-02
can I use nvidia-settings to configure TwinView for xorg.conf with my ATI card? or is it nvidia specific?

---

### Post by azTom on 2008-09-04
Logged in as root user, things went OK up to "Save X Configuration File", then receive "Unable to creat new X config backup file '/etc/x11/xorg.conf.backup' "

Thanks for any and all advice.

---

### Post by azTom on 2008-09-05
Performed the multi monitor setup as posted by Pippinuk, things seemed (?) to go OK.  On reboot the system goes back to a single monitor, what am I doing wrong?:confused:

---

### Post by azTom on 2008-09-05
I have an Nvidia GeForce 7300 video card, to begin with BOTH monitors were displaying the same thing. Installed EnvyNG per Pippinuk's instructions. Then I ended up with a single monitor working.

Next ried Administration> Nvidia Server Settings which gave me two monitors but both tied together.  In other words if I opened a package it spread across both monitors.

Plus when I reboot I'm back to a single monitor.
 a
Resolutions are working fine.

---

### Post by Nax10 on 2008-09-06
Thanks for the instructions above.

They have not been successful for me.

I've been trying for months to make Ubuntu use two LCDs on a Nvidia FX 5200 without much progress.

After the latest install of Ubuntu earlier this afternoon, I installed the Nvidia restricted driver, installed the NVidia config application, but the second LCD still is blank like it's disabled, even though it shows up and correctly identified in the NVidia XServer Settings program.

So I tried the instructions on the original post above, rebooted and got a script asking me to configure the two monitors - first time I ever saw that.

After I booted into Ubuntu I had a mirrored monitor on the two LCDs but at 800x600 resolution. All navigation with the mouse, typing here, etc, has slowed down to a crawl... possibly because of video driver conflicts.

Is there a way to clean up all video related drivers and start with the initial Ubuntu configuration without having to uninstall/install Ubuntu again from scratch? I'm now up to a dozen times of reinstalling Ubuntu and it's very frustrating and tiring to try and make it use two LCDs - something I would think should be easy to do.

Thanks for your help.

---

### Post by wizekid on 2008-09-09
when i try to access the nvidia x server settings i get this erroe

```
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.
```

what could it be?

---

### Post by seriousstorm85 on 2008-09-10
Thanks alot dude,

I am not keen on envy. I would have installed it, if u didn't reply to this thread.

---

### Post by azTom on 2008-09-18
Followed Pippinuk's   8-9-08 advice and selected absolute for each monitor.  Works GREAT, now I have two separate monitord, able to drag and drop between them.  Just like in XP.

---

### Post by Nax10 on 2008-09-27
Pippinuk,

You are a savior!

Out of desperation I tried your instructions again and it worked!

I finally have two independent monitors in Ubuntu!

Thank you! :guitar:

---

### Post by ateubrasileiro on 2008-10-09
i had the same problem as NAX10 =/
dont want to reinstall ubuntu =///
if any1 could help, thanks in advance
P.S.: mine is an ATI

---

