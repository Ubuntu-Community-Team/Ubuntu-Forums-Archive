---
title: "Desktop issues after attempting to dual monitor using AMD catalyst control  center"
date: 2012-01-24
forum: Multimedia Software
---

### Post by oli_g on 2012-01-24
Hi,

I'm new to the forum. I also want to state to begin with that I wasn't sure if I should put this thread here, or in the Desktop Environments section.

------------- PC SPEC --------------
OS: Ubuntu 11.10 (64 bit, running gnome classic (didn't like unity at 11.04))
Computer: Asus M4A78LT-M motherboard (bought a motherboard bundle with ridiculously large heat sink... if you haven't seen silentKnight2 in action, you should see it! anyway...)
Graphics card: Integrated ATI Raeon HD 3000 GPU

-------- How I got to the problem (skip this if not interested) ------
So, I recently bought a Samsung S24A350H (24") monitor and I was attempting to dual monitor my Ubuntu with my old Samsung SyncMaster 152v (15").

I have windows7 dual booted with my Ubuntu 11.10, and I know it's possible to do dual monitoring with my system as I have managed to do so in windows7, using the AMD catalyst control center for windows.

I had issues setting the dual monitoring up in Ubuntu, but I managed to get around my issues following the advices given [URL="http://ubuntuforums.org/showthread.php?t=1867948"]here
[/URL]
where all I did was to install the AMD catalyst control center using:

```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade

```However, AMD catalyst control center kept acting up and not saving the dual monitor settings I implemented on its GUI, so I followed the advice [here]("http:askubuntu.com/questions/92562/amd-control-center-doesnt-save-preferences"):

to use the command:
```

gksudo amdcccl

```and manually open the AMD catalyst control center by going to Applications -> Other -> AMD control center (Administrative) to set the dual monitoring for real.

I initially selected the last option to basically create a larger desktop and have the two monitors show different areas. Rebooted, and this worked.
However because of the difference in monitor size, there was a blind spot to the virtual desktop and so I didn't like this option.

I then started to do some other stuff, rebooted the computer... and then the dual monitor set up was gone. 

So I then went back to typing in 'gksudo amdcccl', open AMD control center, but this time I selected my 15" monitor to be a single monitor with multiple desktops.

I was hoping this would show me two separate desktops at one time, which I would rather do...

I rebooted, and this is when things went mental.

------- Description of the problem  --------
I automatically log in, and now on my 24" monitor I see the desktop background and on my 15" monitor I see a fully white background. 

The 24" monitor shows the files on my desktop, and my 15" monitor shows nothing. What's worse, the top bar with 'Applications', 'Places' and whatnot, along with the bottom bar with the windows opened and the virtual desktops have both disappeared (I believe X server problem) which means I can't open up the AMD catalyst control center to revert this problem.

I tired
```

sudo startx

```but I get the following error:
> 
Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log
^CXIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
xinit:       after 8 requests (8 known processed) with 0 events remaining.
connection to X server lost
xinit: unexpected signal 2
chase@Chase:~$ sudo rm /tmp/.x0-lock
rm: cannot remove `/tmp/.x0-lock': No such file or directory
The '^CIO:' bit showed up after I hit CTRL + C.

I can hit CTRL+ALT+T to open up a terminal, and I can do a lot from there, but I can't open up the launch with ALT+F2 which would be my preference.

------- My questions --------

1. Anyway I can revert this?
2. If I do revert this issue, how would I go about setting up the two monitors so that they are individual desktops?

In fact on that latter question, I would rather have it implemented so that the gnome classic's 4 virtual desktops are shared evenly between the two monitors. So, when I hit CTRL + ALT + (left or right arrow) I switch monitors, as well as switching desktop. Is this possible to implement without having to hack into the software a lot? But I would be chuffed if the first question was answered...

Sorry for the long post, but I would rather not miss out the detail. I do like my ubuntu, but if you tell me I need to re-install unbuntu, I'm probably going to take it out completely and replace it with mint or fedora, as I have other issues with it...

Thanks!

Oli

---

### Post by BonnieH on 2012-02-28
I'm having this plus may other issues after installing a new ATI HD 6770 card.

In the issue of the white screen, I've been able to fix this by activating Xinerama in the Catalyst control center under Display Options and rebooting.

I still have other issues to sort out, but I hope this helps.

---

### Post by dunskii on 2012-03-08
Hi all,
Ok I'm just going to add a me too, to this.
Everytime I reboot I have to reset the dual monitor settings in AMD Catalyst Control.
When I open it it does say it has recommended setting and just to hit Apply which fixes everything, but why doesnt it just remember the settings from last logon. :confused:
That is all,
Enjoy the weekend.
D

---

### Post by dunskii on 2012-04-04
Howdy all,
Just so you all know I was able to solve this issue by following this wiki entry
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)
Hope it works for you 
D

---

