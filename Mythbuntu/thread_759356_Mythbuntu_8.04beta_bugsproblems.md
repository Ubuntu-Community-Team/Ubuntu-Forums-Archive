---
title: "Mythbuntu 8.04beta bugs/problems"
date: 2008-04-19
forum: Mythbuntu
---

### Post by 13ojo on 2008-04-19
This is mainly alot of minor stuff. That probably won't be too hard to fix, but if you guys know of it you can do it. :)

MAJOR STUFF

1) The realtek 8111c chips don't seem to work. This is documented on ubuntu bugs, so hopefully it will be fixed with ubuntu 8.04 and subsequently mythbuntu 8.04.

They report that they are working (eg can ifup them etc), but they just don't connect to the network, very strange.

2) volup /down does not work when watching tv. 0%=100%, using a dtv1000t. I had to disable the internal mixer to gets some volume, even then it is very quiet. I think the driver might not be playing nice with volume/sound.

MINORY STUFF

Probably easy stuff/ not even required to fix

1) Couldn't get the dtv1000t remote working at all, apparently it requires recompiling the drivers for it. As a bit of a noob, i'm not sure how to do this. Also the remote doesn't turn up in the graphical "select you remote" thing.

2)When i'm using an older realtek card (pci), which autoinstalls. It doesn't start up correctly. I must "sudo ifup eth0" it to get it working.
Not particularly nice as the backend is far away and can't be used at day. This may just be this card however.

3) Dtv1000t has to be added to /etc/modules. Though this is probably desired behaviour.(if so maybe document it somewhere?).

That's all i can think of for now. But it seems very very stable, which is great. The only thing that could be improved is better no signal handling, it makes the frontend useless for a good while.

Also, if your silly enough to play a music file, through the watch video menu , you lose all control of the frontend. (i had to kill mplayer via ssh remotely).

---

### Post by laga on 2008-04-19
Cool, thanks for your feedback!

> **13ojo said:**
> 
2) volup /down does not work when watching tv. 0%=100%, using a dtv1000t. I had to disable the internal mixer to gets some volume, even then it is very quiet. I think the driver might not be playing nice with volume/sound.


I have no experience with that card.. I assume it's a digital card, so there are no volume controls for the card itself. Maybe you can look at alsamixer to see if something is wrong..
Another thing that I've noticed with 0.21 is that AC3 streams are quieter. If you bring up the on-screen menu by pressing 'm', can you select a different audio stream? The MP2 ones I get here are usually louder.

> 
1) Couldn't get the dtv1000t remote working at all, apparently it requires recompiling the drivers for it. As a bit of a noob, i'm not sure how to do this. Also the remote doesn't turn up in the graphical "select you remote" thing.


File a bug report against lirc: [https://bugs.launchpad.net/ubuntu/+source/lirc](https://bugs.launchpad.net/ubuntu/+source/lirc)
Also include a link to driver patches/guides etc.

> 
2)When i'm using an older realtek card (pci), which autoinstalls. It doesn't start up correctly. I must "sudo ifup eth0" it to get it working.
Not particularly nice as the backend is far away and can't be used at day. This may just be this card however.


Should be very easy to fix. Can you post your /etc/network/interfaces?

> 
3) Dtv1000t has to be added to /etc/modules. Though this is probably desired behaviour.(if so maybe document it somewhere?).


It should work automagically. File a bug report against [https://bugs.launchpad.net/mythbuntu](https://bugs.launchpad.net/mythbuntu), we'll assign it to the correct package then.

> 
That's all i can think of for now. But it seems very very stable, which is great. The only thing that could be improved is better no signal handling, it makes the frontend useless for a good while.


Are you talking about WLAN?

> 
Also, if your silly enough to play a music file, through the watch video menu , you lose all control of the frontend. (i had to kill mplayer via ssh remotely).

Heh. Not sure what we can do about that :)

---

### Post by Titus A Duxass on 2008-04-19
My tuppence worth.

Clean install, only one hardware problem.
My EDIMAX wlan is not recognised (rtl 8180) at all. WOTB with 6.06.

I can no longer use firefox instead of the internal browser (I need to run realplayer).

The xserver config is RRPITA!

---

### Post by Titus A Duxass on 2008-04-20
Hardware: Normal PC, Nvidia card, pvr 150 running on a Phillips 32" LCD TV through a DVI to HDMI converter cable.

Did another install of 8.04 this morning (0530 CET) and have the following little niggles:

1. I get an internal error message centre screen - Failed to initialise HAL, this is only visible outside of myth on the desktop.

2. The network icon (top left) shows network to be broken. I disabled the roaming mode and set it to DCHP. The network nows works but the icon still shows it as broken. Again only visible outside of myth.

3. In terminal I cannot use sudo -i command, it freezes the system and Ctrl+Alt+Esc is the only escape. Normal sudo commands work okay.

4. After the install and the mega-update my keyboard layout returned to US even though System-Settings-Keyboard-Layout shows it to be DE. I got round this by adding the German layout again.

5. Mythstream has some issues. It will not play youTube (failure - no URLs).

6. The screen saver needs to be disabled or set to a long time otherwise is stops mythstream when it kicks in. I actually apt-get removed both the xscreensaver and the gnome-screensaver to stop this.

7. Replacing the mythbrowser with firefox in the set-up no longer works. In a terminal you get "/usr/lib/firefox.../firefox [options...][URL] as a fail message. Replacing the command firefox with firefox + a url gives the same results.

There are some grabber problems that I have to fix and the remote control config needs tweaking (there is no possibility to back out of a selected option).

Everything else works great.

I did not experience the same problems with the x-config this time around, once I had set my display to 1280x768 it stayed that way.

I wish the internal browser would support realplayer and flash plugins.

---

### Post by superm1 on 2008-04-20
> **Titus A Duxass said:**
> Hardware: Normal PC, Nvidia card, pvr 150 running on a Phillips 32" LCD TV through a DVI to HDMI converter cable.

Did another install of 8.04 this morning (0530 CET) and have the following little niggles:

1. I get an internal error message centre screen - Failed to initialise HAL, this is only visible outside of myth on the desktop.

2. The network icon (top left) shows network to be broken. I disabled the roaming mode and set it to DCHP. The network nows works but the icon still shows it as broken. Again only visible outside of myth.

3. In terminal I cannot use sudo -i command, it freezes the system and Ctrl+Alt+Esc is the only escape. Normal sudo commands work okay.

4. After the install and the mega-update my keyboard layout returned to US even though System-Settings-Keyboard-Layout shows it to be DE. I got round this by adding the German layout again.

5. Mythstream has some issues. It will not play youTube (failure - no URLs).

6. The screen saver needs to be disabled or set to a long time otherwise is stops mythstream when it kicks in.

There are some grabber problems that I have to fix and the remote control config needs tweaking (there is no possibility to back out of a selected option).

Everything else works great.

I did not experience the same problems with the x-config this time around, once I had set my display to 1280x768 it stayed that way.

I wish the internal browser would support realplayer and flash plugins.
A lot of your issues sound like they are boiling down to this fix coming this week in linux-ubuntu-modules for cx88 related issues.

[https://bugs.edge.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/212271](https://bugs.edge.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/212271)

[https://bugs.edge.launchpad.net/ubuntu/+source/alsa-driver/+bug/212960](https://bugs.edge.launchpad.net/ubuntu/+source/alsa-driver/+bug/212960)

---

### Post by RWN on 2008-04-20
Hello,

last Kernel works fine, was 12er, after Upgrade to 14,15,16 it dident work´s.
also Hal-Problems, no Network and so one......

I installed the Kernel 16 rt and it´s works. Only the Picture isn´t so fine as Kernel 12.

Sorry for my bad English

Using Nova S plus with CX88

---

### Post by RWN on 2008-04-20
superm1,

wood the new Driver from ATI/ATM 8.04 releasd in MythBunut Final ?

bg
Rainer

---

### Post by superm1 on 2008-04-20
> **RWN said:**
> superm1,

wood the new Driver from ATI/ATM 8.04 releasd in MythBunut Final ?

bg
Rainer
The AMD driver I hope makes it in, but that's not what fixes this hal issue.  Anyone encountering the hal issue should try the PPA as described on

[https://bugs.edge.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/212271/comments/66](https://bugs.edge.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/212271/comments/66)

until the fix is in.

---

### Post by RWN on 2008-04-20
Thx for Repost,

> The AMD driver I hope makes it in, but that's not what fixes this hal issue. Anyone encountering the hal issue should try the PPA as described on

[https://bugs.edge.launchpad.net/ubun...71/comments/66](https://bugs.edge.launchpad.net/ubun...71/comments/66)

until the fix is in.

But for a Beginner, it wood no easy tu run it into the Kernel. **** will Happens for my English :popcorn:

Best Regards

Rainer

---

### Post by RWN on 2008-04-20
Sorry, i see you dev  the last Driver for ATI (8.03).

It´s right that´s ist´s not solved the iisus of Hal, Netwerk and so one..........

---

### Post by samch on 2008-09-25
> **Titus A Duxass said:**
> My tuppence worth.

Clean install, only one hardware problem.
My EDIMAX wlan is not recognised (rtl 8180) at all. WOTB with 6.06.

I can no longer use firefox instead of the internal browser (I need to run realplayer).

The xserver config is RRPITA!

Did you ever get the rtl8180 working? I have the same problem. It works fine in 6.06 but not in 8.04
Any advice would be appreciated.
Thanks,
Sam

---

