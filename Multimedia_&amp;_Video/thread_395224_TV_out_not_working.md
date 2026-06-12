---
title: "TV out not working"
date: 2007-03-27
forum: Multimedia &amp; Video
---

### Post by mic159 on 2007-03-27
Hi there,

i wanted to try out linuxMCE, and found out that you have to have ubuntu 6.10 installed already, so i burnt it to CD and put it in.
The thing is, the box im installing it on only has a CRT TV on it, and when the install CD trys to start X, the screen goes black and i cant see what im doing. I have tryed all the options in the boot menu to do with graphics, but still have no luck.
I am using a Geforce4 MX440 (64MB).
I can plug in a monitor to the analogue port on the card, and it has no siginal...

I managed to get it to show the desktop on the monitor after restarting the copmuter, but the TV goes crazy and shows random colours. (The card is set to clone output).

do i need to install some drivers?? i downloaded the ones from the NVIDIA site and tryed to install  that, but it says stuff like this graphics card is supported by legacy drivers and stuff like that.

what should i do??

---

### Post by fenian on 2007-03-27
Yes you need to install the nvidia drivers you can use the > Envy script to do this.
After you install the drivers open a terminal and type...
> 
sudo nvidia-settings

this will bring up the nvidia settings window from where you can add the TV and adjust other ssettings.

---

### Post by mic159 on 2007-03-27
Thanx heaps, it works now :)
time to install MCE


thanx for the quick reply
-Mic

---

### Post by mic159 on 2007-03-28
ok, now im stuk again

i installed the drivers using Envy, and all was good, it was showing fine on the TV
then i installed MCE (without rebooting first, was that a bad idea?)

and when it finished, it said it needed to reboot. i pressed the only button there "close", and it just closed the window. so i tried to restart it, but the bar at the top of the screen (dunno what u call it) was frozen...
so i hard reset it and now whenever it starts the X window session, the gfx on the TV r all funny again... a bit diffrent this time, as you can kinda make out the desktop.

what should i do??
should i reinstall the graphics drivers?
how can i do that from a console, coz i can start it in repair mode.

i tried to use Envy again, but it said there was an error in the file when i did "sh Envy_0.8.something.bin"
should i be using sh??

sorry about the long winded post
thanx
-Mic

---

### Post by fenian on 2007-03-28
I dont think that linuxMCE is ready for prime time yet , you can read a review [here]("http://www.progbox.co.uk/wordpress/?p=266").If your looking for something to watch and record TV ,play music , play DVD's etc... You may want to look into [mythtv]("http://www.mythtv.org/").Guides for installing on Ubuntu can be found[ here]("https://help.ubuntu.com/community/MythTV?highlight=%28mythtv%29").

---

### Post by mic159 on 2007-03-28
what i need to know is how can i use Envy from the recovery terminal??
coz the way i used it before was in a Xwindow session and i have no idea how to do it in the terminal.
or alternativly, how can i edit Xorg.conf to enable the monitor again?? because for some reason it disabled my monitor and is just using the TV.
do i need to edit Xorg.conf for that or some other nvidia file?

---

### Post by fenian on 2007-03-28
Try...

> sudo envy -t

---

