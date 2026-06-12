---
title: "Make overscan settings stick"
date: 2011-07-02
forum: Mythbuntu
---

### Post by itlarson on 2011-07-02
How can I make the over-scan setting from nvidia-settings stick after a reboot?  Preferably without having to start up nvidia-settings.  The "save configuration" button does nothing.

---

### Post by uteck on 2011-07-03
The settings are saved in a hidden file in the home of the user running it.  If you run "nvidia-settings -l " (lower case 'L') when the myth user logs in, it will load the saved settings without showing the Nvidia app.  You can add that to the end of the myth users .bashrc file and it will auto run each time or use some other system tool to run it on login.

---

### Post by itlarson on 2011-07-03
That would probably work if nvidia-settings was saving it's settings properly, but it isn't.  Every time I restart the X server there is overscan. When I then open nvidia-settings, overscan compensation is set to zero.  If I start it from a terminal, I get alot of output like :

ERROR: Cannot open display 'itlmyth:0.0'.

ERROR: Unable to assign attribute CursorShadow specified on line 21 of configuration file
       '/home/itl/.nvidia-settings-rc' (no Display connection).

...

ERROR: Unable to assign attribute OverscanCompensation specified on line 49 of
       configuration file '/home/itl/.nvidia-settings-rc' (no Display connection).

...and so on.

I specificly included line 49 because it is:

itlmyth:0.0/OverscanCompensation[DFP-1]=70

My TV shows up as DFP-1 ON GPU-0 in nvidia-settings.  What gives?

---

### Post by itlarson on 2011-07-03
OK, I think I found a solution on the internet.  If I run:

sed -i 's/^'`hostname`'//g' .nvidia-settings-rc

 It strips the hostname out of out of the settings file.  Lines in this file then look like:

:0.0/OverscanCompensation[DFP-1]=70 
instead of
itlmyth:0.0/OverscanCompensation[DFP-1]=70

I have to make this file read only, or nvidia-settings will add the hostname back.

Why this works, I don't know.  It's not ideal, because I can't use nvidia-settings to permanently change settings, but then, I couldn't do that before anyway.

Does anyone have a better solution?

---

### Post by agamotto on 2011-07-05
Have you tried altering the settings for the monitor/screen in the XFCE menu?  That might make your resolution/overscan 'stick.'

---

### Post by nickrout on 2011-07-06
I think that if you run nvidia-settings as root the settings will stick.

---

