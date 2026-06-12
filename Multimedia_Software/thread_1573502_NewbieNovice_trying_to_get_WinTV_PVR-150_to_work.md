---
title: "Newbie/Novice trying to get WinTV PVR-150 to work"
date: 2010-09-12
forum: Multimedia Software
---

### Post by watson524 on 2010-09-12
Hi all,

I'm trying to get off windows and decided to take my Win TV PVR 150 card out of that machine and put it in my Ubuntu 8.04.4 LTS machine.

I downloaded TVTime and when I start it up, it says ivtv: invalid argument cannot open capture device /dev/video0 at the bottom and no signal in the middle.

interesting because at the very top in the "menu bar" area, it seems to know something is coming in because each time I start up the program, it changes based on what is on some TV channel (right now it says "recommended by Dr. mom")

I have read a bunch of postings but I think since I'm so new at all this, I'm getting more confused. I saw something where in terminal, you had it send the output to test.mpg so I did that, and sure enough the file created has video and sound so clearly something is working right but not on the front end app.

Can anyone offer some advice of what I should be doing?

thanks!

---

### Post by saedelaere on 2010-10-08
> **watson524 said:**
> Hi all,

I'm trying to get off windows and decided to take my Win TV PVR 150 card out of that machine and put it in my Ubuntu 8.04.4 LTS machine.

I downloaded TVTime and when I start it up, it says ivtv: invalid argument cannot open capture device /dev/video0 at the bottom and no signal in the middle.

interesting because at the very top in the "menu bar" area, it seems to know something is coming in because each time I start up the program, it changes based on what is on some TV channel (right now it says "recommended by Dr. mom")

I have read a bunch of postings but I think since I'm so new at all this, I'm getting more confused. I saw something where in terminal, you had it send the output to test.mpg so I did that, and sure enough the file created has video and sound so clearly something is working right but not on the front end app.

Can anyone offer some advice of what I should be doing?

thanks!

TVTime does not support your device. What works is [TV-Viewer]("http://tv-viewer.sourceforge.net"). Be sure to have Tcl/Tk >= 8.5 installed and consider upgrading ubuntu to a more recent version.

Regards

---

### Post by watson524 on 2010-10-08
Thanks for the advice. Excuse the newbie questions but what is Tcl/Tk and how hard is it to update the OS? It tells me in there that there's an upgrade available but it took me a lot of playing around to get drives set up properly for mapping and stuff and I didn't know if I'd have to do all that from scratch.

thanks!

---

### Post by saedelaere on 2010-10-09
> **watson524 said:**
> Thanks for the advice. Excuse the newbie questions but what is Tcl/Tk and how hard is it to update the OS? It tells me in there that there's an upgrade available but it took me a lot of playing around to get drives set up properly for mapping and stuff and I didn't know if I'd have to do all that from scratch.

thanks!

Open a terminal and type in the following commands 
```
sudo apt-get update
sudo apt-get install tcl8.5 tk8.5 libtk-img ivtv-utils mplayer-nogui xdg-utils
```

Now get the [latest version]("http://tv-viewer.sourceforge.net/mediawiki/index.php/Downloads#Stable_release") of TV-Viewer and install it as described in the included README. If the installer complains about missing Tcl/Tk 8.5 have a look at [this entry]("http://tv-viewer.sourceforge.net/mediawiki/index.php/FAQ#I_have_installed_Tcl_.2F_Tk_version_8.5.2C_still_the_installer_complains") in our FAQ.

As to upgrade your Ubuntu distribution, you will receive updates until April 2011 for 8.04. So no need to hurry :)

---

### Post by watson524 on 2010-10-09
Sorry to be such a newbie but I've never installed anything that didn't happen automatically. I ran the commands, all seemed ok. Downloaded the .gz file and don't know where I should extract it to before I run the install commands. Should I mkdir in terminal with the sudo command in order to make a folder in something other than my user folder?

thanks!

---

### Post by saedelaere on 2010-10-09
> **watson524 said:**
> Sorry to be such a newbie but I've never installed anything that didn't happen automatically. I ran the commands, all seemed ok. Downloaded the .gz file and don't know where I should extract it to before I run the install commands. Should I mkdir in terminal with the sudo command in order to make a folder in something other than my user folder?

thanks!

Hi,

I'm currently trying to build a ubuntu package what would make it  easier for you to install the program. I think it will be finished tomorrow. I will keep you posted

---

### Post by saedelaere on 2010-10-10
> **saedelaere said:**
> Hi,

I'm currently trying to build a ubuntu package what would make it  easier for you to install the program. I think it will be finished tomorrow. I will keep you posted

I have created a PPA and packages for various versions of Ubuntu:
[https://launchpad.net/~saedelaere/+archive/tv-viewer](https://launchpad.net/~saedelaere/+archive/tv-viewer)

When on you are on the mentioned website click on "(Read about installing)". Follow the guide carefully and install tv-viewer. 

Regards

---

### Post by watson524 on 2010-10-10
Thank you so much for putting this together for me! I was able to install it but something isn't right. It starts up and I have the big screen that I believe is where the picture would go and then another screen with with "TV Viewer 0.8.1.1" in the top bar. None of the buttons are activated. In help, I ran the diagnostic routine which crashed and said it created a file in my home directory called /home/michele/tv-viewer_diag.out but I can't find that file (even when viewing hidden files)....

---

### Post by watson524 on 2010-10-10
Actually, never mind..... I figured out that I had to do the station search first and now all seems ok. Not sure where the diagnostic file is but not sure I much care at this point.

Thanks so much for your help! I'll marked this solved.

---

### Post by saedelaere on 2010-10-11
Hi,

first thing is to check the configuration, second to search for stations. After that it is a good idea to restart TV-Viewer and then everything should be ok. Strange thing with the diagnostic routine. I will have a look at it. In the next release we will have a one-window design, because I think this is easier to handle for me and the user. 
Glad it works for now.

Best regards

---

### Post by watson524 on 2010-10-11
Thanks for the tips. Is there any way to get the remote that goes with the card to work? It's that little plug in eye thing but I know in Windows, the Hauppage software is seperate for that.

---

### Post by saedelaere on 2010-10-14
> **watson524 said:**
> Thanks for the tips. Is there any way to get the remote that goes with the card to work? It's that little plug in eye thing but I know in Windows, the Hauppage software is seperate for that.

TV-Viewer supports all remote controls that were configured with lirc. So get lirc working and use the irexec daemon, the rest is explained in TV-Viewer user guide. 

Regards

---

