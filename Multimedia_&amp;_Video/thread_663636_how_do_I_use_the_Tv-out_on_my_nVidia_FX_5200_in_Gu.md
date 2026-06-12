---
title: "how do I use the Tv-out on my nVidia FX 5200 in Gutsy?"
date: 2008-01-10
forum: Multimedia &amp; Video
---

### Post by hurtstotalktoyou on 2008-01-10
EDIT:  SOLVED

ORIGINAL MESSAGE:

With all the information out there about nVidia graphics cards, you'd think I'd be able to figure this out using Google.  However, I can't find the solution to my very specific problem, and I'm too unfamiliar with Ubuntu and Linux to understand and pick apart the information about related problems to formulate my own solution.

So, here's the deal:  I have an nVidia GeForce FX 5200 AGP graphics card, and am running Ubuntu Studio 7.10 Gutsy Gibbon.  I have already installed the "restricted" nVidia driver, and everything seems to be running just fine.  However, I need to be able to output a clone of my video signal to the s-video TV-out, and this is where I'm lost.

A Google search yielded suggestions ranging from manually editing Xorg (the last time I tried that I ruined the entire Ubuntu installation, and thus lost all my data and settings) to installing the PVR suite MythTV (which seems undesirable considering its alpha development status).  I did see something about "nvidia-settings" which looked promising, but I don't want to type random commands I find on the net in terminal without understanding what I'm doing.

Any help with this would be much appreciated.  Thanks in advance.

---

### Post by Del Piero on 2008-01-10
Try:

> gksudo nvidia-settings

In a terminal.

Make sure your Tv is plugged in before doing that.

From the left menu choose ''Xserver Display Configuration''.

Click on the tv screen then configure.

Choose separate view, then set the options you want save to xorg.conf and restart X.

**[COLOR="Red"]Important Note:[/COLOR]**

Before doing any of that i recommend doing the following.

> Sudo gedit /etc/X11/xorg.conf

Copy everything in that file by using select all and then close it.

Then paste to:

> Sudo gedit /etc/X11/xorg.conf.iknowthisworks

Save and exit.

This way you gonna have a back up in case anything goes wrong.

---

### Post by AlecJ on 2008-01-10
I have the same card that I'm using with Mythbuntu.

There is only one way that I have found to get the TV-Svideo out working, that is to edit the /etc/X11/xorg.conf 

Sudo nvidia-settings from the terminal will bring up the graphical setting tool, but I have not found this to be much use, but it does show the setting currently in place.

There are listings of xorg.conf about that enable both of the cards outputs, I can post here a copy of the mythbuntu xorg.conf and then you just copy and add the parts about the S-video to your file.

This worked on Gutsy before I opted for the PC under the TV running Mythbuntu and then talking to it for setup and stuff via VNC from another PC.

---

### Post by Del Piero on 2008-01-10
> **AlecJ said:**
> I have the same card that I'm using with Mythbuntu.

There is only one way that I have found to get the TV-Svideo out working, that is to edit the /etc/X11/xorg.conf 

Sudo nvidia-settings from the terminal will bring up the graphical setting tool, but I have not found this to be much use, but it does show the setting currently in place.

There are listings of xorg.conf about that enable both of the cards outputs, I can post here a copy of the mythbuntu xorg.conf and then you just copy and add the parts about the S-video to your file.

This worked on Gutsy before I opted for the PC under the TV running Mythbuntu and then talking to it for setup and stuff via VNC from another PC.

Why do things the hard way when they can be done much more easier? And what problems did you have with the Nvidia settings GUI?

---

### Post by AlecJ on 2008-01-10
I had a few problems with the GUI setting where after saving the config and reboot, I lost the Xserver GUI, more than once I'm afraid. So I stopped using it.

Only from my experience mine, I could well have been doing it wrong. I just found better results from editing the xorg file.

I also have a Nvidia 6600le with TV out, but it does not show the TV with the nividia-setting gui? any idears

---

### Post by Del Piero on 2008-01-10
> **AlecJ said:**
> I had a few problems with the GUI setting where after saving the config and reboot, I lost the Xserver GUI, more than once I'm afraid. So I stopped using it.

Only from my experience mine, I could well have been doing it wrong. I just found better results from editing the xorg file.


I am not an expert either mate, only trial and error but i had similar issues as you before but with Gutsy in specific the Gui  seems to be working really fine thats why i recommended it to the original poster. As i said all you have to with gutsy is back up your xorg just in case.

---

### Post by hurtstotalktoyou on 2008-01-10
> **Del Piero said:**
> Try:



In a terminal.

Make sure your Tv is plugged in before doing that.

From the left menu choose ''Xserver Display Configuration''.

Click on the tv screen then configure.

Choose separate view, then set the options you want save to xorg.conf and restart X.

The nvidia-settings panel worked great, thanks--though I should note I used "twinview" instead of "separate."

I have a follow-up questions, though:  Why "gksudo" instead of simply "sudo"?  What's the difference?  I initially used "gksudo" like you said, but afterwards I just tried "sudo" and that seemed to work, too.  How do I know when to use one or the other?

I thank the rest of you also for your assistance.  Gotta love community-driven support!

---

### Post by Del Piero on 2008-01-10
> **hurtstotalktoyou said:**
> The nvidia-settings panel worked great, thanks--though I should note I used "twinview" instead of "separate."

I have a follow-up questions, though:  Why "gksudo" instead of simply "sudo"?  What's the difference?  I initially used "gksudo" like you said, but afterwards I just tried "sudo" and that seemed to work, too.  How do I know when to use one or the other?

I thank the rest of you also for your assistance.  Gotta love community-driven support!

gksudo simply give the root permissions to the settings manager, and it works with any other software you need to run from a terminal. Without gksudo the settings manager won't be able to write on your Xorg.conf when you press save settings to xorg.conf. Some apps requires a root permission just to start and thats when you use ''sudo (program)'', some like the settings manager requires to be root if they are going to write changes on system files and thats when you use ''gksudo (program)''. Some programs have the root permission already therefor no gksudo is required. Try sudo settings-manager and most probably it won't be able to write the xorg.conf. Anyway i am glad i helped, mark this thread solved please :).

---

