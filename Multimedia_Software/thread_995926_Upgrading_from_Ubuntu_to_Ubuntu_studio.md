---
title: "Upgrading from Ubuntu to Ubuntu studio"
date: 2008-11-28
forum: Multimedia Software
---

### Post by Gusss on 2008-11-28
Hi,

I am a sound designer and us a a lot of music software. So vista pushed me over the edge and I have downloaded and installed a Ubuntu 8:10 (intrepeid ibex) dual boot partition on my computer. Now I find out there is "ubuntu studio" which I am downloading now. I am a COMPLETE beginner to Linux. Can I somehow upgrade from Ubuntu to studio or do I need to do a clean install. How do I do either of these things ? I do not want to completely wipe my vista yet as I have to copy the files across (is there anyway of doing that by the way, I cant see my vista partition)
Any help appreciated,
cheers,
Gus

---

### Post by DiscoKiller on 2008-11-28
Hi Gusss, 
 
The basic difference between Ubuntu and Ubuntu Studio is the software included in the distribution and also the drivers used. Basically a tuned up version designed for audio production. 
 
You can look into what software is on the studio distribution and download them or you can do an install to replace your current ubuntu, this would just be a clean install- I dont think there is an easy way of 'upgrading' to Studio but I may be wrong. 
 
Hope it goes well compadre. I`d just like to mention that Ardour is quality!
 
Peace
 
DK

---

### Post by Gusss on 2008-11-28
> **DiscoKiller said:**
> Hi Gusss, 
 
The basic difference between Ubuntu and Ubuntu Studio is the software included in the distribution and also the drivers used. Basically a tuned up version designed for audio production. 
 
You can look into what software is on the studio distribution and download them or you can do an install to replace your current ubuntu, this would just be a clean install- I dont think there is an easy way of 'upgrading' to Studio but I may be wrong. 
 
Hope it goes well compadre. I`d just like to mention that Ardour is quality!
 
Peace
 
DK
Muchas Gracias compadre !
I should have done thois years ago really. So how do I do the clean install ? Just burn the DVD and wipe my present ubuntu partition ?

---

### Post by Bucky Ball on 2008-11-28
There is another big difference - the real time kernel (rt kernel) designed for low latency. I have just installed Ubuntu Studio from within Ubuntu but can't get the rt kernel to work, drops me to a black screen where the login should be. See here.

[http://ubuntuforums.org/showthread.php?t=995818](http://ubuntuforums.org/showthread.php?t=995818)

... but you can follow this page for installing it from within Ubuntu and drop back to the kernel you are using now if you run into problems:

[http://www.ubustu.com/globe/2007/05/23/add-ubuntu-studio-to-an-existing-ubuntu-install/](http://www.ubustu.com/globe/2007/05/23/add-ubuntu-studio-to-an-existing-ubuntu-install/)

I like the blends! :) There is absolutely no problem with mixing things, I do it on all my machines. The only problem I've encountered is the rt problem but though ripping my hair out, probably something simple and you will probably be fine. I wouldn't go for a full install without trying this first. I go the blend cos I don't like the Studio desktop particularly (even though you can spend time changing it).

---

### Post by Gusss on 2008-11-28
Wow ! So its true ! There arent even any trolls in Linux heaven :)
Im getting exited now. However that link is for Ubuntu studio 7:10 no ? There is a new version I believe 8:10 is it still the same process to upgrade ? Checking out their wiki now. Excuse my ignorance but what is a "blend" a mixture between ubuntu and studio perhaps ?
By the way Bucky I use an HP Dv2000 laptop - have you had any issues with drivers etc ? Where do you get your drivers from ?

---

### Post by Bucky Ball on 2008-11-28
> **Gusss said:**
> However that link is for Ubuntu studio 7:10 no ? There is a new version I believe 8:10 is it still the same process to upgrade ? 

Yep, no difference cos it doesn't mention 7.10 in the command and will go for the latest for your machine. Working fine for me now in the Ubuntu kernel. I have jack running in realtime no problem. 

> **Gusss said:**
> Excuse my ignorance but what is a "blend" a mixture between ubuntu and studio perhaps ?
By the way Bucky I use an HP Dv2000 laptop - have you had any issues with drivers etc ? Where do you get your drivers from ?

A blend is exactly that, my way of putting it mind you ... I have base Xubuntu on one machine with ubuntu-desktop loaded also and Kubuntu with ubuntu desktop loaded on my laptop. That one is soon to change though as I never use KDE (but have a heap of different Desktop Environments to play with - I use Gnome/openbox which is fast).

Which drivers were you thinking? You have a Broadcom wireless card, perhaps? You would want to load, from synaptics (System->Administration->synaptics package manager):

```
ubuntu-restricted-extras
```

Just paste that in a search.

So, if you follow the page I posted, go for that first long piece of code - just copy and paste into a terminal (Applications->Accessories->Terminal), reboot and boot into the realtime kernel (has 'rt' on the end), or, leave that bit off (the last command in the code ending with 'rt') and see how you go with the Ubuntu straight kernel. You can always load the rt kernel later and play around. The beauty of Ubuntu! :) 

Welcome to the forums and the world of Ubuntu by the way. Studio64 is another one you might want to look at, along with pure.dyne

---

### Post by Bucky Ball on 2008-11-28
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

That one is a bit more complex but is for Ubuntu 8.10. :)

---

### Post by Gusss on 2008-11-28
So all I have to do is connect to the internet , paste this little bit of code into terminal :

sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt

and thats it ? That easy ?

---

### Post by markbuntu on 2008-11-28
I don't think the rt kernel is ready yet for 8.10 so 8.04 might be a better bet for now. Anyway, here are some links to get you started;

[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation) 

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/](http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/)

That is a little excerpt from my very extensive guide to sound in Ubuntu here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Bucky Ball on 2008-11-29
> **Gusss said:**
> So all I have to do is connect to the internet , paste this little bit of code into terminal :

sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt

and thats it ? That easy ?

Worked for me. That will load the appropriate packages to get you going. As I mentioned, you can leave out the bits you don't want (in my case, ubuntustudio-desktop. 

The reason I am getting the black screen where the login screen in the rt kernel is to do with the fact that I am using the nvidia-glx-new driver for my video card. Apparently there is a problem with the rt kernel and that driver (bizarre for an audio/visual OS, but there ya go ... ).

Gonna try and remedy that now but might be something to look out for.

:)

Hey, markbuntu; do you reckon it is the glx-new driver giving me problems? The full description of that problem can be found here:

[http://ubuntuforums.org/showthread.php?t=995818](http://ubuntuforums.org/showthread.php?t=995818)

... and the glx-new suggestion I found here:

[https://help.ubuntu.com/community/Ub...dioPreparation]("https://help.ubuntu.com/community/UbuntuStudioPreparation")

:)

Got my problem fixed. Start to finish I followed the original instructions from the first page I posted here and then did this:

[QUOTE=overdrank]1) Open a modules file for editing with:-
Code:

sudo nano /etc/default/linux-restricted-modules-common

2) Edit the DISABLED_MODULES line to make it look like this:-
Code:

DISABLED_MODULES="nv nvidia_new"[/QUOTE]

from this page:

[http://ubuntuforums.org/showthread.php?t=864202](http://ubuntuforums.org/showthread.php?t=864202)

(Thanks overdrank). Rebooted and said there was a problem with the X server this time around. So ran the rt (recovery) kernel, chose the option to fix the X server, and voila! All working fine. Basically gave me a clean xorg.conf with no nvidia, so that is the only downside. You should be right to go with that code and if you are not using nvidia-glx-new driver, you won't have the same problems. It is not a problem with the way I was doing it, but a known bug with Ubuntu Studio so it wouldn't have mattered if I went for a clean install anyhow (unless Studio loads an appropriate nvidia driver that it can work with). Good luck!

---

### Post by BigD77 on 2008-11-29
> **DiscoKiller said:**
> Hi Gusss, 
 
The basic difference between Ubuntu and Ubuntu Studio is the software included in the distribution and also the drivers used. Basically a tuned up version designed for audio production. 
  
 
Hope it goes well compadre. I`d just like to mention that Ardour is quality!
 
Peace
 
DK

Is Ardour an audio recording software, similar to Abode Audition?  Is it any better than Audacity?

I have tried Audacity on a laptop I had with Ubuntu Feisty Fawn, and was not able to get a current upgraded version, yet Windows versions were available.  Unless of course I was doing something wrong, which could always be the case!  :lolflag:

BTW, what are the system requirements for Ubuntu Studio?

---

### Post by markbuntu on 2008-11-29
> **Bucky Ball said:**
> Worked for me. That will load the appropriate packages to get you going. As I mentioned, you can leave out the bits you don't want (in my case, ubuntustudio-desktop. 

The reason I am getting the black screen where the login screen in the rt kernel is to do with the fact that I am using the nvidia-glx-new driver for my video card. Apparently there is a problem with the rt kernel and that driver (bizarre for an audio/visual OS, but there ya go ... ).

Gonna try and remedy that now but might be something to look out for.

:)

Hey, markbuntu; do you reckon it is the glx-new driver giving me problems? The full description of that problem can be found here:

[http://ubuntuforums.org/showthread.php?t=995818](http://ubuntuforums.org/showthread.php?t=995818)

... and the glx-new suggestion I found here:

[https://help.ubuntu.com/community/Ub...dioPreparation]("https://help.ubuntu.com/community/UbuntuStudioPreparation")

:)

Got my problem fixed. Start to finish I followed the original instructions from the first page I posted here and then did this:



from this page:

[http://ubuntuforums.org/showthread.php?t=864202](http://ubuntuforums.org/showthread.php?t=864202)

(Thanks overdrank). Rebooted and said there was a problem with the X server this time around. So ran the rt (recovery) kernel, chose the option to fix the X server, and voila! All working fine. Basically gave me a clean xorg.conf with no nvidia, so that is the only downside. You should be right to go with that code and if you are not using nvidia-glx-new driver, you won't have the same problems. It is not a problem with the way I was doing it, but a known bug with Ubuntu Studio so it wouldn't have mattered if I went for a clean install anyhow (unless Studio loads an appropriate nvidia driver that it can work with). Good luck!

The rt kernels have problems with the nvidia and ati proprietary drivers, they are not able to load the dkms kernel modules. This happens in Hardy also. Once you get the kernel working, you can reinstall the driver and it should work, at least it did for me on Hardy. Just be aware that you may have to do this for every kernel update and you will be OK. 

The best way is to remove the driver before installing the rt kernel then installing it again after. But, if the driver is already there and misinstalled, you can dpkg the kernel module again and it should work. If you used a automatic installer that did not unpackage the modules, you need to reinstall the driver.

Anyway, after getting a new mobo and cpu I was finally able to get intrepid installed and will be trying to install the UbuntuStudio pkgs sometime soon.:guitar:

---

### Post by markbuntu on 2008-11-29
> **BigD77 said:**
> Is Ardour an audio recording software, similar to Abode Audition?  Is it any better than Audacity?

I have tried Audacity on a laptop I had with Ubuntu Feisty Fawn, and was not able to get a current upgraded version, yet Windows versions were available.  Unless of course I was doing something wrong, which could always be the case!  :lolflag:

BTW, what are the system requirements for Ubuntu Studio?

Ardour is one of the best recording suites around regardless of operating system. Ardour is only limited by the capabilities of your hardware. It has unlimited tracks, unlimited redo, a zillion options for every little tiny thing that you may need to adjust for perfect sound reproduction. It is used by professionals for everything, right up to mastering. 

Most audacity users are afraid of ardour because it shows them how complicated professional recording actually is and they just do not want to go there.

The only things comparable in windows is Reason or Pro-tools. There is nothing you can get for free that is even close to ardour.

System requirements depend on what you want to do, the more you want to do, the better your system needs to be. If you want to do 32 track real time recording, you will need the best machine you can find, or a couple of them. But if you are just doing remixing on like 4 or 8 tracks with a few live and a few prerecorded or midi tracks, a fairly new dual core should be good enough.

---

### Post by Bucky Ball on 2008-11-30
> **markbuntu said:**
> 
The only things comparable in windows is Reason or Pro-tools. There is nothing you can get for free that is even close to ardour.


... and Cubase which is excellent for midi (and audio). 

markbuntu, thanks for the tip with the nvidia driver. The kernels are all up and running and I had a good night exploring some of the apps in Ubuntu Studio. Looks good and now to just work out the sound connections (I am used to the commercial software you mentioned before so slightly different ways of doing the same things). I will try re-installing the nvidia driver later today and see what happens. :)

* Markbuntu - exactly the same problem as first time on reinstall of nvidia driver, but rather than crash this thread, I have posted a seperate one here:

[http://ubuntuforums.org/showthread.php?p=6280027#post6280027](http://ubuntuforums.org/showthread.php?p=6280027#post6280027)

---

### Post by BigD77 on 2008-12-01
> **markbuntu said:**
> Ardour is one of the best recording suites around regardless of operating system. Ardour is only limited by the capabilities of your hardware. It has unlimited tracks, unlimited redo, a zillion options for every little tiny thing that you may need to adjust for perfect sound reproduction. It is used by professionals for everything, right up to mastering. 

The only things comparable in windows is Reason or Pro-tools. There is nothing you can get for free that is even close to ardour.


Thanks a lot.  I am used to Adobe Audition (Windows) and would use it for commercial production and voice over work.  That software works well with either P3 or P4 computers.  I am thinking of trying Ubuntu Studio with my P3 computer and see how it works, then graduate it to my P4 machine.

---

