---
title: "Linux compatible alternatives to Netflix?"
date: 2010-08-12
forum: Multimedia Software
---

### Post by Nick_Jinn on 2010-08-12
A client of mine really wants to use his PC to stream netflix to his television....I might be able to help him with hooking up his laptop to the TV....he only has VGA so I dont know what kind of adapter he is using, but he said it worked in windows but not linux.....I will try to set that up for him so it works automatically without having to keep messing with the settings....ideally I dont want him to have to do anything but plug and play.


But this leaves the problem of Netflix....I dont personally care for Netflix but he wants it.

I dont know if dual booting is a good idea as he only has 60gb (56 in real life) hard drive. That doesnt leave much. I guess its possible though.


So, maybe I can sell him on an alternative to Netflix that supports Linux? I would love doing that because I dont want to give business to a company that doesnt support us. A company that thought about our demographic deserves our support. 


If not, what is the best way to go? I know its possible to get Netflix working, but I am no guru. My use of the command line is limited to apt-get, Aptitude, reboot, and copying and pasting lines of commands....I might know a few others, but its not an area I feel comfortable with. 


1. I might be able to talk him into buying one of those netflix streaming devices.....maybe.

2. I could try and dual boot....it might be tough on a laptop this old with only 56gb. He says he doesnt download much.

3. I could try Wubi.....How is the performance of Wubi vs a partitioned install?

4. Finally, I could try installing a virtual machine. Ive used virtual machines before, but linux virtual machines with someone else's help. I havnt tried installing Windows to a virtual machine inside of Linux....is it relatively painless? Should it all be point and click for my guy after i install it?



Id like some opinions on which way to go out of the above 4 options before I go an experiment. I have a lot on my plate right now without having to do it over again.

---

### Post by hortstu on 2010-08-23
I have no ideas for you but I'd be interested to hear how you made out.

---

### Post by Nick_Jinn on 2010-08-23
I think we decided that Amazon was the best mainstream alternative but a few others were mentioned.

---

### Post by jadonchristensen on 2011-01-10
The easiest way and the only way that I know of to get Netflix working on Linux is to use a Virtual Machine. 

-Install VirtualBox from Ubuntu Software Center
-Run Application > Accessories > VirtualBox
-Click New, accept the defaults
-Insert your Windows disk (I used XP)
-Select the new Machine that you created
-Click Start
-It should boot from the CD or press F12 to change boot
-Install Windows, Firefox, Silverlight

I take it one step further and install the Free Comodo Firewall, block access to Internet Explorer, install the Firefox Add-on named Procon and block all other sites but netflix.com and related. I try to make sure that Windows VM is only used for Netflix.

Some tips for running Full Screen movies, screen resolution, etc.
-With XP running in the Virtual Machine, click Devices, Install Guest Additions (need to be XP admin)
-Guest Additions should prompt you to reboot the Windows VM when done installing
-Once Windows has started again, press RIGHT Ctrl + F, then press RIGHT Ctrl + G [this should get you full screen and automatically correct your resolution]

P.S. If you want to get rid of the annoying mini-bar at the bottom of the Full Screen VM...

-On the main VirtualBox screen
-Settings
-General
-Advanced
-deselect Mini Toolbar options
-Ok to save

---

