---
title: "AcerHK GUI -- GUI for users of the 'acerhk' driver to control wireless/bluetooth"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by arm-c on 2009-02-04
ATTN:  if you are looking for an appindicator for ubuntu that will give the basic functionality (on/off) as well as other things, check out the Displex project at [https://sourceforge.net/p/displex](https://sourceforge.net/p/displex)  

**_New Release -- v. 0.7.2 _**
Version 0.7.2 is BETA.  OK.  If you are an ACERHK user, this package is a huge step forward.  The package SHOULD build the driver from source now _successfully_.  The source code is included in the /usr/share/acerhkgui for the acerhk driver.  PLEASE provide feedback... especially if it works for you.  I have tried to test it as best as possible, to include removing the compiled driver and re-running, installing in various kernels that have been pushed, etc...  

IF IT FAILS TO COMPILE, 
a.  run 'acerhkgui' from a command prompt and see if that works.  It will have much more messages.
or
b.  run 'sudo /usr/share/acerhkgui/acerhk_install_acerhkgui.sh' from the command prompt.

Debian Package:  [AcerHK GUI 0.7.2 (beta)]("https://sourceforge.net/projects/acerhkgui/files/")

RPM Package:  Not released.  Use Alien to create from deb. (what I do).

IF YOU JUST NEED THE DRIVER TO BE INSTALLED:  Try this [script]("https://downloads.sourceforge.net/project/acerhkgui/acerhk_driver_install_script/acerhk_driver_install.sh?r=https%3A%2F%2Fsourceforge.net%2Fprojects%2Facerhkgui%2Ffiles%2F&ts=1282431892&mirror=voxel").

If the link doesn't work above, go to the project page at [SourceForge]("https://sourceforge.net/projects/acerhkgui/")

[end of new release info]
-------------------------------------------------

Please see last post of mine for latest information on the AcerhkGui
If you don't need the acerhk driver installed (ie: using ubuntu before 9.10) or are using a 64-bit version of Linux, use AcerHK Gui 0.6 for present time -- thanks.

I have written a GUI interface to use in Linx to access and control the acerhk driver. 

To me, this has been very helpful for the following reasons:
a.  Sometimes I want my wireless/Bluetooth radio off (IE: Plane)
b.  Bluetooth is not enabled by default on my ubuntu and there was no obvious way to enable it.
c.  I don't want Bluetooth on unless I am using it -- Rarely
d.  My buttones -- if they worked correctly on my computer with the acerhk driver -- aren't accessible when I am in tablet mode -- this gives a means to access both radio controls.

 The acerhk driver is used primarily by older computers (Acers and other -- not limited to just acers.  See:  [http://rfswitch.sourceforge.net]("http://rfswitch.sourceforge.net") for a list of laptops and what drivers they use).  

There are packages available on sourceforge.net in .deb, .rpm, and .zip formats.  I recommend the .deb as it is easier to install and includes an application launcher that goes to the Applications | System  menu.

I would like to note that even though it will activate the hardware, the wireless LED will not light up unless you modify the /etc/modprobe.d/options file and change
```
options ipw2200 associate=0
```
to
```
options ipw2200 associate=0 led=1
```

My project is hosted at [http://sourceforge.net/projects/acerhkgui/]("http://sourceforge.net/projects/acerhkgui/")

I am looking for feedback on the functionality of both the program and the .deb file, so, if you are a user of the acerhk driver, I ask that you download my file and give it a whirl and send me some feedback. 

Mine is an Acer Travelmate C300 Tablet with wifi and bluetooth in it.  Newer Acers are using different drivers to control their hardware; however, like me, I am sure there are others that use this driver.

[IMG]http://sourceforge.net/dbimage.php?id=203212[/IMG]
[http://sourceforge.net/projects/acerhkgui/]("http://sourceforge.net/projects/acerhkgui/")

A couple of years ago, through research (love Google!), I found out how to activate my bluetooth through the command line:

```
echo "on" > /proc/driver/acerhk/blueled
```

Honestly, that is quite a pain.  I know there are those that have written scripts to automate this task and attached those scripts to the hot keys.  But, for me, the acerhk driver doesn't seam to match my keys to the correct actions.  

As I have been fascinated with wanting to learn to program and was thinking that Python was a good place to start, I started this as a Project to augment my learning.  It is always best to learn by doing.  It is a work in progress and I do hope to continue to expand its features for a bit as I learn more about the wonderful language Python.

I used python-wxglade to design the interface, inkscape for icon creation, and gedit for editing the files. 

I look forward to the feedback from the wonderful Ubuntu and Open Source community!

---

### Post by arm-c on 2009-02-05
Well, so far the .deb file for the project works fine.  Still looking for feedback on functionality and such... 

Thanks.

---

### Post by arm-c on 2009-02-12
Probably not the right place for this; however, I have released a .rpm package file for this project since there are a good many distros based on that package manager.

The .rpm file has been tested and installs fine.  If it doesn't work for you, read the help forum on [http://sourceforge.net/project/acerhkgui](http://sourceforge.net/project/acerhkgui)

---

### Post by arm-c on 2009-02-28
Well,

It doesn't look as though there have been any responses to the survey (probably because it requires login) or the posting.  

Of course, that could be a good sign! Why?  because people only respond when they have an issue with something for the most part.  And to echo this in reality, I have had a response from one user who couldn't get it to work on their system -- but they weren't using the AcerHK driver, so the GUI would do nothing.  Outside of that, it there have been none; however, I have had 60 .deb package dounloads fromt he site.  That must mean it works.

Well, the next time I post to this thread, I hope to be posting about a release of the next version and feature of that version.

Thanks much to all who have downloaded it.  Even more thanks if you are using it!

---

### Post by arm-c on 2009-03-01
**_AcerHKgui v.0.3:_**  The widely popular acerhk driver now has a GUI.  The AcerHK GUI is a front end to the acerhk (Acer Hot Key) driver that enables certain buttons on the computer and an interface with wireless and bluetooth hardware.  In some cases, the buttons are not associated properly -- if at all.  The GUI provides an interface to the driver and enables user to activate and deactivate associated wireless and bluetooth hardware radios regardless of the button assignments.  

In the first month, there were 84+ downloads of the AcerHK GUI from the sourceforge project page.

Enhancements in this release:
General -- the primary changes are:

a.  Incorporation of variables into the code and simplify customization for variations in instalation of the acerhkgui and acerhk software.  This set the foundation for a future GUI configuration interface.

b.  Enhanced feedback from the script to the Terminal when launched/ran from the terminal to facilitate trouble shooting.

  - If the driver was found where expected.
  - Info from the acerhk driver

c.  The acerhk driver information is now saved to the users home directory. (~/.acerhkdriverinfo.txt file).  This is re-written each run of the program.

This release includes .deb, .rpm, and .zip (package manager independent) packages.

Feedback is welcome and encouraged.  Any donations received are 100% passed on to other great organizations supporting the open source movement.  Details on sourceforge at: [http://sourceforge.net/projects/acerhkgui/](http://sourceforge.net/projects/acerhkgui/)

---

### Post by arm-c on 2009-04-11
Version 0.4 has been released.  The GUI was converted to pyGTK and "trimmed" down to provide a cleaner and more professional look. The difference in colors is that I changed my theme between making the screen shots.  The main window and preference window will follow a theme consistent with your Gnome theme.

[IMG]https://sourceforge.net/dbimage.php?id=211982[/IMG]

Version 0.4 also added a preference button.  This button provides access to enable users to do some limited configuration (in the future).  Right now, it provides information from the driver:

[IMG]https://sourceforge.net/dbimage.php?id=211978[/IMG]

The second tab now enables the user to select the path to the driver, but this is not persistent yet.  Version 0.5 will enable persistent settings.  Here is a screen shot of the driver path selection tab:

[IMG]https://sourceforge.net/dbimage.php?id=211980[/IMG]

Well, please stay tuned, but the next feature to be implemented will be the persistent configuration settings in version 0.5.

Thanks loads to the one person who responded to my poll so far. :)

---

### Post by Count Belisarius on 2009-04-18
Hi, 
Really appreciate your efforts on this. I'm actually using it on a Fujitsu Siemens Amilo Li 1718. I've had a real battle with the wireless on this over the last 18 months. Had it working under 8.04. Then went to 8.10 and it stopped working. Back to 8.04 and then last week for no reason it stopped again.

Now have 9.04beta. Ran the live CD and wireless worked from the off (5700EG). Great I thought. At last. Installed it. Wireless didn't work...

Now, have acerhk module loading at start and use your little app to turn the wireless button on. It doesn't always work straight off though and I think this may be the path persistence thing? Do I need to set the path to the driver (down in /lib/kernel... ) each time?

I'd like to set it so the LED and wireless are on at boot time all the time as the laptop is currently home use and wireless only.

Anyway, look forward to 0.5 and if you have any suggestions it will be appreciated.

Thanks again for you effort.

Andy

---

### Post by arm-c on 2009-04-20
> **Count Belisarius said:**
> Hi, 
Really appreciate your efforts on this. I'm actually using it on a Fujitsu Siemens Amilo Li 1718. I've had a real battle with the wireless on this over the last 18 months. Had it working under 8.04. Then went to 8.10 and it stopped working. Back to 8.04 and then last week for no reason it stopped again.

Now have 9.04beta. Ran the live CD and wireless worked from the off (5700EG). Great I thought. At last. Installed it. Wireless didn't work...

Now, have acerhk module loading at start and use your little app to turn the wireless button on. It doesn't always work straight off though and I think this may be the path persistence thing? Do I need to set the path to the driver (down in /lib/kernel... ) each time?

I'd like to set it so the LED and wireless are on at boot time all the time as the laptop is currently home use and wireless only.

Anyway, look forward to 0.5 and if you have any suggestions it will be appreciated.

Thanks again for you effort.

Andy

Andy, thanks for the feedback.  The issues you are having don't relate to the GUI directly, as the GUI really only passes commands to the existing driver.  The acerhk driver was installed by default on my system.  Now, let me see if I can help with this:

a.  If your LED doesn't come on when you in fact have the driver active, then you will need to modify the /etc/modprobe.d/options file.  See my first post in this thread regarding that.

b.  If your LED does come on all the time when the driver is active, but the problem is that your driver isn't always active at reboot, then you have a different problem.  To that I reference you to this outstanding [blog post]("http://insidethebrackets.blogspot.com/2008/02/acerhk-and-ubuntu-update.html") (and a post of the content of my /etc/modules file)  Basically, you should be able to edit the file ```
sudo gedit /etc/modules
```

My /etc/modules file:
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
# ADD FOR TABLET PC
acerhk
# END ADD FOR TABLET PC

```

c.  My acerhk.ko file is located here (note, yours may be slightly different, but should be in the Kernel you are booting from)
```
/lib/modules/2.6.27-11-generic/kernel/ubuntu/misc/acerhk.ko

```

d.  Finally, your driver issue may be less with acerhk than it is with your wireless card driver.  Keep in mind that the acerhk driver is only a driver that interfaces with some specific hardware keys.  While it may activate the card, if after activated Linux is having problems loading your wireless driver, that could be the entire source of your problems. What kind of wireless card are you using in the computer?  

I hope this helps.  Sorry it is a bit outside of my area, but guilty by association. :)

I apologize for the extended delay in my response.  I usually get email notification, but Yahoo has been acting up and not sending me email alerts when I get new mail.  

Thanks for the kind words.  I appreciate the feedback and look forward to an update to what the issue turned out or more specific symptoms.  I empathize with you.  I had a laptop with a Broadcom card which constantly gave me issues.  It was up... then down... then up...  :)

---

### Post by arm-c on 2009-06-20
[FONT="Arial"]Version 0.5 of the AcerHK GUI is now released and available for download on SourceForge!  

The new version has a little more functionality over the previous version.  Key enhancements:
- Now runs modprobe if driver not found.
- Preferences now saved to configuration file. (~/.config/acerhkgui/)
- Able to browse for driver location in rare case it is not located in default location (/proc/driver/acerhk)

SPECIAL NOTES:  
- Preferences has added tab for mail led configuration; however, this function does not work at present time.
- If at any time, you need to refresh your configuration, you can delete the ~/.config/acerhk directory.  On next run, the default configuration will be rebuilt
- The diver information tab in preferences refresh is delayed if driver not found and then later manually selected from preferences.  Closing and reopening the preferences (maybe twice) will resolve this.

Thanks much for the interest in this little program.  The interest has kept me developing it more and more.  :)[/FONT]

---

### Post by arm-c on 2009-06-23
v. 0.6:
    This version added better modprobe support and options for the user to configure system on first run.

        - Checks for modprobe success.
        - Alerts if modprobe unsuccessful.
        - If modprobe success, added option to modify the /etc/modules file
        - Checks to see if /etc/modules already has 'acerhk' in it, if so,
            will not add again.  Notifies user of possible problem
            that the module is in 'modules' but isn't loaded.

FEEDBACK is very welcome, especially problems/bugs.

---

### Post by Killer_B on 2009-07-06
Thank you. 

Let's keep this one up, guys!

---

### Post by arm-c on 2009-07-09
Thanks for the feedback.  I appreciate the word of encouragement. :)

---

### Post by lunarok on 2009-07-09
Hi, I just get Acer laptop some months before and your gui is helpful.
I just wonder on why your deb package is not put for "all" architecture instead of i386 as it's python. I'm using amd64 distribution so it's a little anoying (must force installation)

---

### Post by arm-c on 2009-07-09
""is not put for "all" architecture instead of i386 as it's python""

Well, good question.  Yes, everything in the package should run equally well on 386 / 64 architectures; however, I did that because it was my understanding that the acerhk driver only works on i386 machines.  In doing so, I had hope to avoid a lot of questions about why it won't work on my machine.

I had no idea that it worked on 64 bit versions of Linux.

I will look at changing the architecture to any for the next release when I package it.

Which version are you using?

---

### Post by lunarok on 2009-07-10
On amd64 we need to compile it too to have the led working and it's compiling well with last acerhk module avalaible on PPA for karmic
I use the 0.6 version of the gui

---

### Post by arm-c on 2009-07-10
Ok.  Great.  I did not know that.  I will update packages to be "any".

I wish I received more feedback such as this.

Thanks Much
Arick

---

### Post by arm-c on 2009-11-09
I just recently upgraded to Ubuntu 9.10.  Not sure why the AcerHK module doesn't load.  Investigating.  While my wireless works fine, without acerhk, I have no way to enable my bluetooth (that I am aware of).  Anyone that can give me more information about the acerhk driver and where on earth it went/how to load it, will be much appreciated.

---

### Post by neojames on 2009-11-09
I can vouch for this brilliant program, my computer dosnt always connect to wifi automaticly when I turn my computer on and this is the best way to fix this.

---

### Post by arm-c on 2009-11-10
I have just posted version 0.7 of this little program.

The key changes here has been the incorporation of downloading and installing the acerhk.ko (32-bit) precompiled module.

**_NOTE_**:  There is a bug in the code I have not been able to work out so far that fails to run the proper code that will enable the module to be seen.  Perform the following:

a.  Do a first run of acerhkgui and then Exit. 

b.  From a command line the following code:
```
sudo depmod -a
```

c.  Run acerhkgui and it should find the module then.  All subsequent runs until the kernel is updated again will work perfectly.  :)

I would appreciate an experienced python user that could help me figure out where my issue with the code running from the program is.

Sorry in advance for 64-bit users.  If someone knows of a pre-compiled version of the acerhk.ko that I can get or link to let me know.

MANY THANKS to the user at this link.  
[http://www.edbl.no/karmic/amilo_1718_wireless_in_ubuntu_9.10.txt]("http://www.edbl.no/karmic/amilo_1718_wireless_in_ubuntu_9.10.txt")
64-bit users will likely find support here that can help you.  You should compile and install acerhk.ko before running my gui.  Please let me know if my program checking for the acerhk.ko module on a 64-bit computer causes any problems.

Source Forge is where the program is located.  Many thanks to users.

---

### Post by Daverobb on 2010-03-23
Thanks for the program but i need some further help.

managed to get the gui installed and it looks like it says it should in this thread. when i finally got it to recognize the acerhk.ko file the card started to recognize wireless signals but had trouble connecting to a signal.  then it stopped working -- led stopped - no wireless signals evident, etc -- don't know what changed or happened but the gui doesn't seem to make any difference to the wireless button anymore.  

do you have any suggestions?

---

### Post by arm-c on 2010-03-24
> **Daverobb said:**
> Thanks for the program but i need some further help.

managed to get the gui installed and it looks like it says it should in this thread. when i finally got it to recognize the acerhk.ko file the card started to recognize wireless signals but had trouble connecting to a signal.  then it stopped working -- led stopped - no wireless signals evident, etc -- don't know what changed or happened but the gui doesn't seem to make any difference to the wireless button anymore.  

do you have any suggestions?

A few things will happen with this program and Ubuntu since ubuntu dropped the acerhk.ko driver from the kernel updates.  That makes it a little bit of a hassle every time the kernel gets updated.

Are you being asked to install the driver again?

What version of Ubuntu are you running?

Some computers have a hardware switch that will physically turn on and off the wifi.  Perhaps you did that?  The program won't work if the hardware is physically turned off.  (for me, I don't have that ability, it is software controled for my bluetooth).

When you click the preferences tab, what does it tell you in the driver information tab?

Do you get any messages that ti can't find the driver on starting the program?

Will do what I can to help you out with this.  :)

---

### Post by maestrobwh1 on 2010-04-21
It was a bear to even get acerhk to compile in Lucid.

[https://bugs.launchpad.net/ubuntu/+source/acerhk/+bug/456123](https://bugs.launchpad.net/ubuntu/+source/acerhk/+bug/456123)

and then the GUI wants python 2.5 and I am not sure how to go about seeing how to fix that.  

Would be cool though.

---

### Post by arm-c on 2010-04-22
Well,  I fugure AcerHK might be difficult to compile..... however, the GUI on the otherhand should run just fine with Python 2.4 - 2.6  If you were not successful in installing the GUI, you can install it from the command line with the force option.

it may choke with Python 3.X, as the print command changed syntax.

a.  Download the .deb
b.  from the folder where the .deb is, run

sudo apt-get install --ignore-missing acerhkgui_0.7_i386.deb

You may need to update the name of the package you are using.

If that doesn't work, try the force option or the -m option (read man apt-get)

Hope that helps.

---

### Post by arm-c on 2010-04-29
Version 0.7.1 is BETA.  Main change is to "attempt" to automate installation of the acerhk.ko file.  This beta requires build-essentiala and headers.  It is hopefully smart enough to download source, install required dependencies, compile driver and install it.  This should now work for both 32 and 64-bit systems.  If you download the beta files posted at the following link, please provide feedback.

Debian Package:  [AcerHK GUI 0.7.1 (beta)]("http://dl.dropbox.com/u/195281/acerhk-pack/acerhkgui_0.7.1_all.deb")

RPM Package:  [AcerHK GUI 0.7.1 (beta)]("http://dl.dropbox.com/u/195281/acerhk-pack/acerhkgui-0.7-2.noarch.rpm")

-----------------------------------------
Additional Notes:

>  Tried to make it architecture independent. (all)
>  Now downloads and installs from source.  Dialogs in Beta not updated to reflect that it should work on a IA64 system.
>  Made dependency Python as opposed to "python2.5", so should hopefully help some of the issues.

I really need feedback on this to see if the new code is working correctly.

---

### Post by mugwash on 2010-06-15
> **maestrobwh1 said:**
> It was a bear to even get acerhk to compile in Lucid.

[https://bugs.launchpad.net/ubuntu/+source/acerhk/+bug/456123](https://bugs.launchpad.net/ubuntu/+source/acerhk/+bug/456123)

and then the GUI wants python 2.5 and I am not sure how to go about seeing how to fix that.  

Would be cool though.


I'm having the same problem. I'm running Lucid too. The .deb for 0.7 won't install because I don't have python 2.5. I tried ```
sudo apt-get install  -m acerhkgui_0.7
``` and ```
sudo apt-get install  --ignore-missing acerhkgui_0.7
``` but it says ```
E: Couldn't find package acerhkgui_0.7_i386.deb
```

I also tried the 7.1 beta because I saw you changed dependency to be "python" rather than "python 2.5". I was able to install the .deb without problems but when I try to run it I get into trouble: "AcerHK Module found at expected location" and then "acerhk module failed to load!". 

I tried adding acerhk to /etc/modules, then running sudo depmod -a, but I still get the same messages. I know this computer is compatible because I was using AcerHK GUI on the same laptop with an earlier version of Ubuntu. It's really good when it works :)

If anyone has any suggestions I'd really appreciate it.

---

### Post by arm-c on 2010-06-15
I sent you an email.  Hopefully we can work this out and get it working.  I look forward to your reply.

A

> **mugwash said:**
> I'm having the same problem. I'm running Lucid too. The .deb for 0.7 won't install because I don't have python 2.5. I tried ```
sudo apt-get install  -m acerhkgui_0.7
``` and ```
sudo apt-get install  --ignore-missing acerhkgui_0.7
``` but it says ```
E: Couldn't find package acerhkgui_0.7_i386.deb
```

I also tried the 7.1 beta because I saw you changed dependency to be "python" rather than "python 2.5". I was able to install the .deb without problems but when I try to run it I get into trouble: "AcerHK Module found at expected location" and then "acerhk module failed to load!". 

I tried adding acerhk to /etc/modules, then running sudo depmod -a, but I still get the same messages. I know this computer is compatible because I was using AcerHK GUI on the same laptop with an earlier version of Ubuntu. It's really good when it works :)

If anyone has any suggestions I'd really appreciate it.

---

### Post by arm-c on 2010-08-21
**_New Release -- v. 0.7.2 _**
Version 0.7.2 is BETA.  OK.  If you are an ACERHK user, this package is a huge step forward.  The package SHOULD build the driver from source now _successfully_.  The source code is included in the /usr/share/acerhkgui for the acerhk driver.  PLEASE provide feedback... especially if it works for you.  I have tried to test it as best as possible, to include removing the compiled driver and re-running, installing in various kernels that have been pushed, etc...  

IF IT FAILS TO COMPILE, 
a.  run 'acerhkgui' from a command prompt and see if that works.  It will have much more messages.
or
b.  run 'sudo /usr/share/acerhkgui/acerhk_install_acerhkgui.sh' from the command prompt.

Debian Package:  [AcerHK GUI 0.7.2 (beta)]("https://sourceforge.net/projects/acerhkgui/files/")

RPM Package:  Not released.  Use Alien to create from deb. (what I do).

Note:  The acerhk that can be compiled is located there if you just want that.  There is also a script to install the source in Ubuntu 10.04.

[SourceForge Project Page]("https://sourceforge.net/projects/acerhkgui/")

---

### Post by Cowboybebop79 on 2010-09-08
Hi, Just posted a thumbs up at your Sourceforge page as I said in my review smooth as butter no issues at all built the driver with no errors and loaded th drivers and added to modules file again with no problems and my wireless is green.One Happy Camper. :D

I would also like to say that I originally used AcerHK Gui to get up and running with 9.10 karmic which is when I said good by to windows if AcerHK had not worked I may not have stayed with Ubuntu and thats not because I have no patience "Time is Money" ever heard that one before. So if it takes to long to get something working you have to know when to cut your loses and stop wasting time.

From one Happy Ubunter Thank you very much. =D>

---

### Post by arm-c on 2010-09-09
Cowboy,

Thanks much for the great feedback.  Since my project is completely made without any expectation of financial gain, the only reward I get is knowing that other users find my project useful and helpful.  I know there must be some users that use it that never reply.  Most of the feedback received is when a person has problems with their system, so it is feedback like yours that make my efforts worth while.  Thanks so much for the feedback.

I don't have too much time to work on the project, so progress is slow.  The main updates have been driven by things such as the acerhk driver no longer being included in Ubuntu, however, I am still working on the project as time permits.

Thanks much!
ARM-C

---

### Post by Cnfys on 2010-11-13
I'm using xubuntu 10.10 but when i'm trying to install acerHK GUI, it sais acerHK is not insallled. Although when i check at the ubuntu software center, it sais it is installed..
My laptop is a Medion MD97600.

---

### Post by JamesSmith on 2010-11-13
v0.7.2

Wow, I spent all evening trying to install the acerhk driver in order to get wireless to switch on on my friend's Medion MD96500 laptop, and when I finally came across the acerhk gui it really did the trick.  I love how it downloads builds and installs the driver for me, it just works!

Thanks for your hard work!:)

---

### Post by kidoko on 2010-11-14
Just downloaded & installed v 0.7.2 & works great! Thanks for the hard work. Greatly appreciated!

I'm using Ubuntu 10.04 on a Fujitsu-Siemens Amilo Li1718

---

### Post by arm-c on 2010-11-17
Thank you very much for the feedback.

Are you using Ubuntu 10.10?  I have not tried 10.10 yet to verify if the software still functions as intended and which I know works under 10.04.

v/r
ARM-C

---

### Post by arm-c on 2010-12-17
All,

I have begun a large rewrite of the application.  I do not want to loose any functionality in the process; however, there will certainly be some issues that come up.  I am also looking at soliciting feedback on the changes I am making.

In short, the objective of this release is to shift the application to an AppIndicator Icon and incorporate Notify-OSD (ubuntu).

I want to do the main posts/feedback on this on my Sourceforge page in the forums.  Please go there for link.  Post all feedback for the Alpha there, as I want to keep this forum for actual releases.

[http://sourceforge.net/projects/acerhkgui/forums/forum/1329399](http://sourceforge.net/projects/acerhkgui/forums/forum/1329399)

---

### Post by arm-c on 2011-01-29
All,

I am currently writing the next version to provide for App Indicator support directly from the system tray.  HOWEVER, I have a second project that gives basic functionality for AcerHK users (On/Off for Wifi/Bluetooth).  The project is really to consolidate (multiplex) Display settings/links into one Indicator Icon menu [hence Displex]; however, I did add an AcerHK GUI control menu that will show if you have acerhk.ko installed in your system.  If not, you won't see it.

[https://sourceforge.net/p/displex](https://sourceforge.net/p/displex)

If you think you do, but it isn't showing, do install latest version of AcerHK GUI.  That could fix the issue for you.

Regards,
Arick

---

### Post by MountainX on 2011-02-24
arm-c, thank you for your work on AcerHK GUI. I have been looking for a solution to turn on my bluetooth on my Acer AO532h. I'm going to download your deb now. Thanks!

---

### Post by MountainX on 2011-02-24
I installed acerhkgui on two Acer netbooks: AO532h and AO D255E. It installed successfully on both. No problem. But it does not activate bluetooth on either one. I don't see any error message, but the end result is that bluetooth doesn't turn on. Here's the output:

```
# acerhkgui

   -=**  The Acer Hot Key GUI   **=-
      *  Command Line Feedback  *
------**************************------------------
You can get the latest version at sourceforge.net
https://sourceforge.net/projects/acerhkgui
--------------*-*-*-*-*-*-------------------------

Config file exists already. Loading saved preferences...
Configuration Loaded...
AcerHK driver found at: /proc/driver/acerhk
 
***********************************************************
Acer hotkeys version 0.5.35
Model(Type)	: (old)
request handler	: 0xc00fede0
CMOS index	: 0x10
events pending	: 0
kernel polling	: active
autoswitch wlan	: disabled
preg400		: 0x(null)
***********************************************************

Send -- Bluetooth :: on
----------------------------------------------------
Thanks for using AcerHK GUI (acerhkgui).  I hope it was helpful!
====================================================
```

What are the next steps?

---

### Post by arm-c on 2011-02-24
Hey,

Couple of questions after I let you know I don't have my Acer with me (finally died).  There are differences between systems and depending on the year of your machine, AcerHK may not be the driver for your hardware.  With that said, please the following from the command line and give me the output:

hcitool dev

and 

lsusb

On the positive, it does look like the driver loads successfully so your hardware is compatable in some ways (wifi probably).

---

### Post by MountainX on 2011-02-24
> **arm-c said:**
> Hey,

Couple of questions after I let you know I don't have my Acer with me (finally died).  There are differences between systems and depending on the year of your machine, AcerHK may not be the driver for your hardware.  With that said, please the following from the command line and give me the output:

hcitool dev

and 

lsusb

On the positive, it does look like the driver loads successfully so your hardware is compatable in some ways (wifi probably).

Sorry to hear your Acer died. This output is from my Acer AO D255E. I appreciate any further suggestions.

hcitool dev is empty:
```
Devices:
```

lsusb:
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 2.0 Stick (4GB) / PNY Attache 4GB Stick
Bus 001 Device 002: ID 0402:9665 ALi Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

lspci:
```
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
02:00.0 Network controller: Intel Corporation WiFi Link 1000 Series
```

---

### Post by arm-c on 2011-02-25
Does running 

lshw

yield any listing for your bluetooth hardware?  I hate to ask the question, as it seams you are quite knowledgeable about the commands, but is there bluetooth hardware in the device?  I have seen several computers that have "bluetooth" indicator on it, but the hardware is not installed.

There is a new replacement for the acerhk driver, but I think it only addresses the wifi issue.  I guess searches for your device and ubuntu and or linux have turned up nothing of value?

If you can find out what hardware you have through in make/model of card, search for that and linux to see if there are other users out there that have gotten it working and how.  Usually, the same hardware is used by several manufacturers in different computers.

If you find the hardware make/model, let me know.  I will try to do a search for it also.

I hope you can figure it out.  I have a CAC Card reader built in to my acer that never worked... ended up just getting an external.  Perhaps you may need to spend $12 - $20 to get a bluetooth dongle... (recommend the Belkin brand as they work good for me... worth the couple extra bucks.)

cheers,
A

---

### Post by MountainX on 2011-02-25
> **arm-c said:**
> Does running 

lshw

yield any listing for your bluetooth hardware?  I hate to ask the question, as it seams you are quite knowledgeable about the commands, but is there bluetooth hardware in the device?  I have seen several computers that have "bluetooth" indicator on it, but the hardware is not installed.

There is a new replacement for the acerhk driver, but I think it only addresses the wifi issue.  I guess searches for your device and ubuntu and or linux have turned up nothing of value?

If you can find out what hardware you have through in make/model of card, search for that and linux to see if there are other users out there that have gotten it working and how.  Usually, the same hardware is used by several manufacturers in different computers.

If you find the hardware make/model, let me know.  I will try to do a search for it also.

I hope you can figure it out.  I have a CAC Card reader built in to my acer that never worked... ended up just getting an external.  Perhaps you may need to spend $12 - $20 to get a bluetooth dongle... (recommend the Belkin brand as they work good for me... worth the couple extra bucks.)

cheers,
A

Thanks for your reply. Of the two Acer netbooks I have, I can be most confident that the Gateway LT2115u has bluetooth. The specs claim it "includes Bluetooth 2.1+EDR capabilities for wirelessly connecting to cell phones and peripherals." And I'm pretty sure I turned on the bluetooth radio when it had Windows -- before I loaded Ubuntu (but that was about a year ago, so my memory could be wrong). But lshw does not show a bluetooth adapter. Is it possible that the Linux kernel cannot see the bluetooth hardware?

My newer Acer Aspire One AOD255E may not actually have the bluetooth hardware... I loaded Ubuntu without ever booting into Windows on this netbook.

I have an Asus brand Bluetooth dongle (ASUS USB-BT211 USB 2.0 Mini Bluetooth Dongle). Here's the link to it:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833320057](http://www.newegg.com/Product/Product.aspx?Item=N82E16833320057)
I have not been able to get it to work yet, but I haven't found the Linux driver for it yet. So I might have to get a different dongle.

One comment on NewEgg says the AZiO BTD-V201 USB 2.0 Micro Bluetooth Adapter (Class 1, V2.1 + EDR) will work on Ubuntu out of the box. I like the 100m range. Here's a link:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833340012](http://www.newegg.com/Product/Product.aspx?Item=N82E16833340012)

EDIT: here's one more that people say will work on Ubuntu 10.04 and 10.10:
cirago BTA-6210 USB 2.0 Micro Bluetooth Dongle support Bluetooth 2.1
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833242003](http://www.newegg.com/Product/Product.aspx?Item=N82E16833242003)

EDIT2: BTW, the Acer AO D255E gives an error on bootup:
> acer-wmi: unable to detect available WMID devices
Could this be why lshw can't detect any bluetooth adapters?

---

### Post by arm-c on 2011-02-28
I honestly don't know which to tell you.  Read the reviews.  Problems I have had in the past are:  bt dongle not being recognized on insertion.  The Belkin ones I have always work great on being recognized.  The other ones I have tried have been finicky.

To my knowledge, the acer-wmi only handles wifi hardware... but i don't know for sure as i have never used it.  If you are loading both acer-wmi and acerhk.ko, there may be a conflict...  Try different combinations if certain that you have bluetooth hardware built in.  If all you have is wifi (or going with bluetooth dongle) and the acer-wmi meets  your wifi needs, uninstall the older acerhk.ko driver and use the newer standard.

for your infomation, the acerhk.ko driver serves as a software switch (on/off) for the hardware it supports.  In my old acer travelmate c300, once it was activated, it was seen as a usb device (as well as a hcid).  You will not need acerhk.ko for a dongle, as the usb system will pick it up and the standard linux bluetooth stack will handle it (if installed).  Same stack handles it for acerhk.ko devices once they are 'powered on'.  Weird system they choose to go with... guess it saved them a couple of dollars not to place a full "hardware" switch in.

I have no problem answering general questions, but if not directly related to the acerhkgui / acerhk, send me a private message.

Regards,
Arick

---

### Post by MountainX on 2011-02-28
> **arm-c said:**
> I honestly don't know which to tell you.  Read the reviews.  Problems I have had in the past are:  bt dongle not being recognized on insertion.  The Belkin ones I have always work great on being recognized.  The other ones I have tried have been finicky.

To my knowledge, the acer-wmi only handles wifi hardware... but i don't know for sure as i have never used it.  If you are loading both acer-wmi and acerhk.ko, there may be a conflict...  Try different combinations if certain that you have bluetooth hardware built in.  If all you have is wifi (or going with bluetooth dongle) and the acer-wmi meets  your wifi needs, uninstall the older acerhk.ko driver and use the newer standard.

for your infomation, the acerhk.ko driver serves as a software switch (on/off) for the hardware it supports.  In my old acer travelmate c300, once it was activated, it was seen as a usb device (as well as a hcid).  You will not need acerhk.ko for a dongle, as the usb system will pick it up and the standard linux bluetooth stack will handle it (if installed).  Same stack handles it for acerhk.ko devices once they are 'powered on'.  Weird system they choose to go with... guess it saved them a couple of dollars not to place a full "hardware" switch in.

I have no problem answering general questions, but if not directly related to the acerhkgui / acerhk, send me a private message.

Regards,
Arick

Thank you! Those suggestions are helpful! It is very nice of you to take the time to help on this forum.

---

### Post by burek021 on 2011-10-25
Hi, please take a look at the bug report that I've incorrectly placed in debian's mailing list, but should have sent it to AcerHK developers: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=646585](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=646585)

---

### Post by agustinventura on 2012-09-01
Hello,

After years of using this wonderfull tool, I've trying today to install it on Lubuntu 12.04. I had an error related to the module compiling, more accurately to linkage.h.
After several hours of working on it (it's been years since the last time I had to compile a kernel module :|), I've created a Makefile which can compile the module and load it, hope it helps!

```

obj-m += acerhk.o

all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean

install:
	mkdir -p /lib/modules/$(shell uname -r)/extra
	cp -v acerhk.ko /lib/modules/$(shell uname -r)/extra
	depmod -a

```

I don't know if this Makefile is correct or has any bugs (I'm a Java developer, duh...), but it works for me and hopes it helps!

Thanks again for this incredible tool!

---

