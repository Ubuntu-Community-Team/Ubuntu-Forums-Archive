---
title: "Getting a silent graphics card"
date: 2009-04-07
forum: Multimedia Software
---

### Post by noamik on 2009-04-07
This thread is half a question, half meant to help other users.
Today my new graphics card arrived. It's a MSI N260GTX-T2D Twin Frozr.

Unluckily the two fans make quite some noise, no matter if I use Windows or Linux. For Windows Riva Tuner should help. But I need it to be silent when running Linux.

This is what I achieved to do. With a combination of nvclock Beta 4, Coolbits acitvated in xorg.conf and underclocking I got the fans to run at half their speed making much less noise (to the point I can't hear them anymore as my CPU-Fan makes more noise now) with less than 5°C temperature increase of the GPU.


What I am missing now is a way to react on increasing temperature (for example when playing 3D games). I want the same behavior as with the fan set to auto, but with another curve. Is their any tool which would allow to change the thresholds for the fans? If not, is their any tool which can control nvclock in function of the gpu temperature?


However, I want to share what I achieved to do already. **But before you continue reading you shall be warned. Messing around with your hardware can actually break it (not kidding!). If you do not know what you are doing, you should not do any of the following.**

Steps to take:
[LIST]
[*]install/activate restricted/proprietary nvidia drivers
[*]open your /etc/X11/xorg.conf and add
 Option      "Coolbits" "1"
to the Screen Section.
[*]start /usr/bin/nvidia-settings, go to Clock Frequencies and check Enable Overclocking
[*]Lower the Frequencie for "3D Clock Frequencies". For my Graphics card I used the same values the PowerMizer showed me for performance level 1, though 400 MHz for the GPU and 300 MHZ for the Ram. You can check with the Power Mizer if your change was applied.
[*]During all your work you can check the temperature in the Temperatur Monitor. You should consider to write the temperature down.
[*]Download [nvclock Beta 4]("http://www.linuxhardware.org/nvclock/") or a newer version if available. with **./configure && make && sudo make install** you build and install the software. I needed to install the package xorg-dev first, as some libraries were missing.
[*]*/usr/local/bin/nvclock -f -F 30* will set your fan to a fixed rpm-rate, where 30 is a value between 10 and 100. If you want your card to get back to normal, use auto instead.
[*]Observe the temperature for an extended period. It should increase slightly, but not to much. Play around with the fan speed value to find out, which one is your preferred compromise between noise and heat.
[*]Once you understand what you are doing there, you can use:
 nvclock -h
to learn more about nvclocks options. I use
 nvclock -f -m 300 -n 400 -F 30
to set video memory clock to 300 MHz, GPU clock to 400 MHz and fan to 30 (around 475 rpm) in just one command line.
[/LIST]

Troubleshooting: if you happen to see a black screen next time you reboot your machine, your card is kind of messed up. Luckily this can be resolved. You only need to successfully start your Ubuntu again with a black screen (so, hopefully your boot menu is not so complicated as mine is). Ubuntu will fail to load the Nvidia-driver and reset Graphics. This will also bring back your screen :-D
I'm not sure what triggers this behavior, but I have the impression that it's related to an early system power down during shutdown (I was impatient) while the card is still "underclocked". In this state the card will not even show the Bios prompt, so it may give you a well deserved heart attack. I told you not to mess with your hardware ;-) :-D
I have similar problems after a normal shutdown, but the card is not in a messed up state than and Nvidia drivers are loading just fine at next startup. I use the exact same clock and fan rpm values on windows, but at reboot the card behaves just fine.

---

