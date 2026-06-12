---
title: "Problem installing Ardour 2"
date: 2007-05-15
forum: Multimedia Production
---

### Post by Bollinja on 2007-05-15
Hi,

I am running Kubuntu 7.04 and have added the Ubuntustudio repos using:

sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'
wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update

I installed Wired with no problem.

When I try to install Ardour2 using Adept Manager I get the following error:

"There was an error committing changes. Possible reasons include problems downloading some of the packages or that the commit would break other packages."

And from the DPkg Run:

(Reading database ... 113670 files and directories currently installed.)
Unpacking ardour (from .../ardour_1%3a2.0-0ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/ardour_1%3a2.0-0ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/share/locale/de_DE/LC_MESSAGES/gtk_ardour.mo', which is also in package ardour-gtk
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ardour_1%3a2.0-0ubuntu2_i386.deb

Any suggestions? I better add that I have only been using Linux for 2 months so I am very much a newbie ;)

I haven't installed the low-latency kernel, if that might make a difference? (And is it safe to do that, ie. it will not damage my Kubuntu setting?) I do have the previous version of Ardour installed as well.

PS Hope this is the correct forum

---

### Post by Snoose on 2007-05-15
I am having the same problem. :(

---

### Post by genbod on 2007-05-16
I am having the same problem.  I installed 7.04 from the live CD first then, I added the UbuntuStudio repos and installed all of the UbuntuStudio packages.  After I tried to install updates I recieved the error: 

 /var/cache/apt/archives/ardour_1%3a2.0-0ubuntu2_i386.deb: trying to overwrite `/usr/share/locale/de_DE/LC_MESSAGES/gtk_ardour.mo', which is also in package ardour-gtk 

  I also recieved a message saying that the index was broken and I had to perform sudo apt-get install -f .  That ended up generating the same error message.  Then I recieved a message to go into synaptic and check for broken packages.  UbuntuStudio-audio was broken and I tried, reinstalling, uninstalling and reninstalling.  I also tried just removing ardour and reinstalling ubuntustudio-audio but always with the same result.  In the middle of all of this I got a need to restart message and when I finally gave up and rebooted into my Windows drive I noticed GRUB had made an entry for the low latency kernel, but I don't remember choosing to install that, so I don't know why that happened.  I guess I just assumed the low-latency kernel was intalled when I installed all of the ubuntustudio packages.  I performed the same type of install on another P3 computer without any problems so I know its not the live CD I have.  Any help would be greatly appreciated.  Thank you.

---

### Post by GadgetsGuy on 2007-05-16
Yep ..... same problem here .... 

Ubuntustudio-audio is listed in my Synaptic as "broken dependencies" 

Trying to reinstall gives me the following error :

**E: /var/cache/apt/archives/ardour_1%3a2.0-0ubuntu2_i386.deb: trying to overwrite `/usr/share/locale/de_DE/LC_MESSAGES/gtk_ardour.mo', which is also in package ardour-gtk**

---

### Post by Jussi01 on 2007-05-16
Hei,

try removing ardour before installing ardour 2.

Im pretty sure this is your problem.

Cheers

Jussi

---

### Post by Pocadotty on 2007-05-16
I agree with Jussi.

Remove Ardour 1 and try again.  This time try using Synaptic instead.  It worked great for me.

GadgetsGuy after you remove Ardour 1. Using Synaptic mark Ubuntu-Audio for reinstall and apply.  If that doesn't work remove it and try again.

Two reasons I see for Ubuntu-Audio being marked as Broken Dependencies are as follows.

1. Ardour 1 interferes with Ardour 2, resulting in the dependency problem. Hence remove Ardour1 and mark Ubuntu-Audio (which contains Ardour2) for reinstall.

2. Errors during download which left some packages un-applied. Hence remove package and try again to get a complete install.

cheers

---

### Post by genbod on 2007-05-16
As I mentioned earlier, I thought that was the problem so I uninstalled ardour using synaptic.  However, if I remember correctly gtk-ardour was marked for reinstall and would not permit me to mark it for removal.  I removed all the other ardour packages I could find through synaptic.  After that I tried reinstalling ubuntustudio-audio again with the same problem.  Are there any suggestions for not being able to remove a program that doesn't seem to want to go?  Is it possible that the update-manager and synaptic are conflicting and making it impossible to remove ardour?

---

### Post by Bollinja on 2007-05-16
Thank you for the help- uninstalled Ardour, used Adept Manager to download Ubuntustudio-audio rather than just Ardour2...and it all installed without a hitch, Ardour2 now up and running :)

---

### Post by genbod on 2007-05-17
finally works!  This time after rebooting I did not click the updates available button.  Instead I selected ardour to be removed and that ended up removing all of ubuntustudio-audio.  I then reinstalled ubuntustudio-audio and it seemed to install without a hitch.  Thanks again for the help.:)

---

### Post by GadgetsGuy on 2007-05-19
a quick follow-up

I got ardour uninstalled, and re-installed ubuntustudio-audio ....

now it tells me that the jactd server is not running?  :(

---

### Post by Pocadotty on 2007-05-20
yes... you need to start the JACK server before you start Ardour 2.

Most Audio Applications on Linux require JACK.

JACK is used to connect all the various programs together.  It is the HUB of the Linux sound studio

---

### Post by mkoyle on 2007-05-20
Also had the same problem.  I installed ubuntustudio-audio before feisty was released.  Today I tried to add the ubuntustudio repos and it couldn't finish the install because of a conflict between ardour-gtk and ardour.  Tried to remove ardour-gtk and got an error about ubuntustudio-audio.  The fixes noted above are the same as what I did to get it fixed (the following):

sudo apt-get remove ardour-gtk ubuntustudio-audio

sudo apt-get install ubuntustudio-audio

The way dependencies are, it will not let you remove ardour-gtk without removing ubuntustudio-audio too.  This probably requires some sort of bug fix (something like remove the old ubuntustudio-audio and ardour-gtk automatically before installing ubuntustudio-audio).

--Matthew

---

### Post by ricrac on 2007-05-20
Start jack, the sound server, before you start any audio apps.
Why jack?
[http://jackaudio.org/faq](http://jackaudio.org/faq)
[http://jackaudio.org/files/JACK-Diagram.png](http://jackaudio.org/files/JACK-Diagram.png)
Jack's real power is with two or more audio cards or high end multichannel cards.

Menu Location
Sound & Video, Jack control 
(Program being run, qjackctl  from the qjackctl package, 
version 0.2.21-1ubuntu1 is what I get with a 7.04 converted to studio)

Start jack control.
If it doesn't stay running you may need to run setup first (button's on the right side of qjackctl)
Defaults worked for my system, but can be tweaked better.

After jack is running you can start apps like ardour2.

An LJ article about ardour2 running on 64studio and ardour w/VST plugins running on Jacklab
[http://www.linuxjournal.com/node/1000224](http://www.linuxjournal.com/node/1000224)

---

### Post by TGArcher on 2007-05-21
Yeah, I had the same problem. The thing with it is that if you have the Ardor-gtk package and try installing ubuntustudio-audio, which tries to install the ardour package, it tries to write to this one config file and conflicts with the existing ardour install, so it says that its a broken dependancy. What I did was unitstall my previous installation of ardour and let ubuntustudio-audio deal with the dependencies, which includes Ardour 2. so I was good. I had to disable and re-enable my restricted drivers, but that was no big deal. :popcorn:

---

### Post by aum11 on 2007-05-22
Hello i am new to studio.

Trying to start ardour, which requires jack.  Cannot get jack control to start.  Cannot find qjackctl package in order to setup Jack.  It is not under apps/sound & video , at least that I can recognise.

Know where qjackctl is?

Thanks

---

### Post by mkoyle on 2007-05-23
On my system, it is under Applications --> Sound and Video --> JACK Control.

That launches the file /usr/bin/qjackctl

If that launcher isn't in the menu, check to see if the qjackctl package is installed on your system with synaptic or using a terminal: sudo apt-get install qjacktcl

Good luck!

After you find it, if you need information for configuring it, search the Ubuntu forums.  There is also a tutorial I used months ago at [http://gentoo-wiki.com/HOWTO_Jack](http://gentoo-wiki.com/HOWTO_Jack); that might be a bit outdated.  Depending on what you are trying to do, you may want to check the Realtime box under Setup.  You will probably need to select the correct interface on this screen (often this will be hw0, but this would depend a lot on your system).  If you are still having trouble, I would suggest starting a new thread with your questions.  New threads get a bit more attention ;)

--Matthew

---

### Post by aum11 on 2007-05-23
Thanks Mkoyle...just what I was after.

---

