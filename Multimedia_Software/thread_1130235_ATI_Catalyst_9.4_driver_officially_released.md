---
title: "ATI Catalyst 9.4 driver officially released"
date: 2009-04-19
forum: Multimedia Software
---

### Post by Pitboss on 2009-04-19
So anyone tried it with jaunty? I'm afraid to install it cause last time I had to reisntall, and the performance was pretty poor.

---

### Post by markbuntu on 2009-04-19
I do believe that is the same driver that is in Hardware Drivers in Jaunty. If you have a rv200-rv500 card the driver will not work for you, neither will any future driver from ati.

---

### Post by SorinN on 2009-04-21
I installed the driver from AMD site and all seem to work OK (I build debs first from the .run file, then I install debs).
Globally I lost ~ 300 frames per second but the quality of rendering is improuved on videos ..no flickering with glxgears or in videos with Xv mode. 

Also I observed some 2D rendering enhancements ( Inkscape / Cairo ).

Comparison were made against catalyst 9.2

---

### Post by Pitboss on 2009-04-21
Nice to hear that. I installed the driver from System > Preferences > Hardware Drivers, and the result was like before: even maximizing window took 2-3 seconds on average. So maybe the beta of 9.4 is in the repository still. My card is HD3650 so, I believe it's still supported.

---

### Post by markbuntu on 2009-04-22
Has anyone got dual monitors working with this driver?
I installed it on one of my Hardy (amd64) installs and there seems to be no way to get big desktop working. So I removed it with the script and went back to 9.3 and now I can't get big desktop there either. I hear it is the same in Jaunty with this driver. This is really bad.

In Jaunty I am using the radeon driver which seems fine for my HD3650. I would rather have a big desktop than compiz at this point. The 9.3 driver works great on my other Hardy(i386) and on Intrepid amd64. 

I think I will just skip this one.

---

### Post by xieu90 on 2009-04-22
hi i havent tried it yet
but i want to share my experience
I have ati x1950 pro and i believe it is r500
long ago i installed ati through envy and also tried the file in ati.amd.com website

they both worked but later i found out that the temperature of my ati card was always very hot.
so if you install those new driver dont forget to check the temperature

---

### Post by xfearxnxloathing on 2009-04-24
i've installed this driver, i have ati radeon 9200 SE pro and when i get to this section 5 of this [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide") i get this > envy@Elemented:~/Desktop$ sudo dpkg -i xorg-driver-fglrx_8.593-0ubuntu1_i386.deb fglrx-kernel-source_8.593-0ubuntu1_i386.deb fglrx-amdcccle_8.593-0ubuntu1_i386.deb 
dpkg: error processing xorg-driver-fglrx_8.593-0ubuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing fglrx-kernel-source_8.593-0ubuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing fglrx-amdcccle_8.593-0ubuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 xorg-driver-fglrx_8.593-0ubuntu1_i386.deb
 fglrx-kernel-source_8.593-0ubuntu1_i386.deb
 fglrx-amdcccle_8.593-0ubuntu1_i386.deb
  

can anyone help me, i miss compiz i use hardy heron.  might i add that at once i had 8.10 on this pc and compiz worked just after installing via synaptic package manager.  

where i'm at now, staying with 8.04 till i get the balls to try to upgrade to 8.10 again because last time i did the upgrade there were broken packages and whatever when i restarted it never came to a screen and my monitor turned itself off like there was no video signal.

---

### Post by bebox on 2009-04-24
having the same problem:

> dpkg: dependency problems prevent configuration of fglrx-kernel-source:
 fglrx-kernel-source depends on dkms; however:
  Package dkms is not installed.
dpkg: error processing fglrx-kernel-source (--install):
 dependency problems - leaving unconfigured
Setting up fglrx-modaliases (2:8.602-0ubuntu1) ...
dpkg: dependency problems prevent configuration of libamdxvba1:
 libamdxvba1 depends on libstdc++5; however:
  Package libstdc++5 is not installed.
dpkg: error processing libamdxvba1 (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xorg-driver-fglrx:
 xorg-driver-fglrx depends on fglrx-kernel-source; however:
  Package fglrx-kernel-source is not configured yet.
dpkg: error processing xorg-driver-fglrx (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xorg-driver-fglrx-dev:
 xorg-driver-fglrx-dev depends on xorg-driver-fglrx; however:
  Package xorg-driver-fglrx is not configured yet.
dpkg: error processing xorg-driver-fglrx-dev (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on xorg-driver-fglrx; however:
  Package xorg-driver-fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 fglrx-kernel-source
 libamdxvba1
 xorg-driver-fglrx
 xorg-driver-fglrx-dev
 fglrx-amdcccle

...ok...a red sign poped up in my notification area and i clicked on it and it installed missing dependencies and configured broken pakages.

Now i hope when i restart my computer that it will work.

---

### Post by bebox on 2009-04-24
it didn't work...i had to enter recovery mode and tipe:

> apt-get install remove xorg-driver-fglrx

...hmm...this is horible...

---

### Post by bebox on 2009-04-24
Driver that is in the repository (2:8.600) is working...but horrible!compiz is awful, and vertical sync is also horrible.

In intrepid ibex the ati driver was working superb...

btw...a have ati HD 3400 series on my laptop...

Did anyone manage to get working the new ati driver (2:8.602) from amd site?

---

### Post by 00arthuryu on 2009-04-24
It works, but video playback is horrendous as in it cannot resize a video bigger than its default size, and any sort of playback is very choppy, regardless of 8.10 or 9.04 (i have a 4850) and I will be reverting back to 9.2 as 9.3 didn't work too well either.

I'm beginning to wonder if its my compiz settings?:confused:

---

### Post by DangerIsGo on 2009-04-24
How did you get it to work?  I followed the instructions but upon after restarting, the I was greeted with two small ubuntu logos on the top of my screen which were much smaller, were very pixelated (and greenish) and it just hung there.  I tried the drivers from ATIs site and I tried the restricted ones.  Both made my system failed to boot.  I have a 4870x2.

---

### Post by bebox on 2009-04-24
> **DangerIsGo said:**
> How did you get it to work?  I followed the instructions but upon after restarting, the I was greeted with two small ubuntu logos on the top of my screen which were much smaller, were very pixelated (and greenish) and it just hung there.  I tried the drivers from ATIs site and I tried the restricted ones.  Both made my system failed to boot.  I have a 4870x2.

Same here...:(

---

### Post by DangerIsGo on 2009-04-24
Really?  Good that there's other people that have this issue besides myself.  Anyone find a fix?

---

### Post by gocek on 2009-04-24
Hello

Well, I'm on Ubuntu 9.04 with my Radeon HD 4870 right now with ATI 9.4 drivers (version 2:8.602) downloaded and installed from ATI site and... they're working.

Of course they didn't work 'just like that'. Both installing through Synaptic and Hardware Drivers (even followed with sudo aticonfig --initial -f ) failed. The driver was installed, but system froze after login screen (right after hitting ENTER after my password). The furthest I managed to get was to see my wallpaper (instead of black screen) and two panels (with no graphics, buttons or whatever, just two grey bars) and then nothing would happen.

I'd just like to mention that on Ubuntu 9.04 RC I got the repository drivers to work only by two simple steps:
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial -f 
[reboot]
and it worked

On the Ubuntu 9.04 Final it doesn't work anymore for me, system keeps hanging the way I described above.

ALTHOUGH:
I followed this guide here [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_restricted_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_restricted_drivers_manually) 
TO THE LETTER and everything magically works, dunno really why repository drivers don't.
Also: if I tried to omit some steps and just install the *.run file followed by "sudo aticonfig --initial -f" the driver would keep hanging after login screen.

Hope I helped a bit, if you have any questions - just ask, I'll try to help out, as I have some experience with those **** ATI drivers ;)

cheers

---

### Post by acreda on 2009-04-24
I downloaded the 9.4 driver (2:8.602) has when I upgraded to 9.04 I was using 9.2 before and I was sure that it was worse so I downloaded and installed it directly from terminal rather than making deb files like last time and everything went fine after running sudo aticonfig --initial -f and rebooting.

oh BTW I'm running a HD4830 in case that makes a difference I can only iterate that I have only had graphic driver problems by not properly uninstalling the old one even if it was Nvidia.....

sorry can't be much help

---

### Post by gocek on 2009-04-24
oh, well, actually the system hung again after login screen, although I haven't done any changes. Seems it's just a lottery: sometimes it boots, sometimes it doesn't. But I noticed one interesting thing:
if the system is about to load correctly with the fglrx driver I get that ubuntu sound when the login screen pops up. But when it's going to be screwed, there's no sound o.O
Additionally, when there's no sound (so I know the system WILL hang at black screen or with empty panel bars), when I switch to console with ctrl-alt-1 and log in, even the console will hang after typing in any command... ctrl-alt-del only sometimes works for rebooting.

---

### Post by markbuntu on 2009-04-24
** You must remove drivers from ati before upgrading to jaunty**

There is a script in /usr/share/ati that will remove the fglrx drivers. It is absolutely required to do this since these drivers are not compatible with the Jaunty xserver. Failure to do so will result in the fglrx kernel modules for the new driver to not be loaded wich will result in the new driver falling back to indirect rendering and extremely poor performance if x does manage to start. In most cases x will not start at all after upgrading.

To fix this, run the uninstaller script in usr/share/ati and then use either Hardware Manager to get the driver or install the 9.4 driver from the ati web site.

---

### Post by nibbana84 on 2009-04-24
> **xfearxnxloathing said:**
> i've installed this driver, i have ati radeon 9200 SE pro and when i get to this section 5 of this [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide") i get this   

can anyone help me, i miss compiz i use hardy heron.  might i add that at once i had 8.10 on this pc and compiz worked just after installing via synaptic package manager.  

where i'm at now, staying with 8.04 till i get the balls to try to upgrade to 8.10 again because last time i did the upgrade there were broken packages and whatever when i restarted it never came to a screen and my monitor turned itself off like there was no video signal.

New driver work just with newer cards... So does Ubuntu 9.04. You have to use open driver (radeon).

---

### Post by rafaelsousa on 2009-04-24
Not working for me... I'm almost giving up on installing this driver... I have a Radeon Xpress 1250, and seems this card is in legacy list... I'm afraid ATI is not doing drivers for my card anymore

---

### Post by DangerIsGo on 2009-04-24
Well, i just followed that wiki entry to install them manually, with no luck.  Same thing after reboot.  I had something similar to this when installing on ibex, but after 5 minutes of blackness, it finally went to the login screen and I had no issue since then, I'm guessing it was an initial install thing.  but with this time, I waited 1/2 hour and still nothing, and my PC is pretty top of the line, 

Q9550 @ 3.5GHz
4GB DDRII OCZ 
150GB Raptor
4870x2
ASUS x48 Rampage Formula

So I don't know what could be the issue if everyone says it works.

---

### Post by Eneerge on 2009-04-25
I'm having trouble with my ATI HD4850 card and 9.4 as well when running compiz.  The cube works fine.  Videos play decently, but you can occasionally see some choppyness like a satellite picture that's fading out in bad weather.  Increasing or decreasing the volume also causes the video to stop playing for about 5 seconds before it resumes playing again.  The most annoying problem is that it takes around 2-3 seconds to restore a minimized window.

I've pretty much decided that I'm just going to disable compiz.  All problems I had with everything went away after I disabled compiz.  I may try an older driver later.  

I've always had video playback trouble with compiz enabled with my ATI card even on 8.10, but only when the video was not maximized.  Now I have trouble regardless.  It may be the driver, but it seems strange that the cube works fine and a simple restore bugs it out.

---

### Post by franklee on 2009-04-25
hey guys I also have an ATI mobility 3650 and I cannot select anything from System, Admin, Hardware drivers...there isnt anything there to choose! any suggestions? at the moment Im running xorg.nv which SUCKS and is for the wrong card....argh! thats what was installed default....

---

### Post by gocek on 2009-04-25
> **markbuntu said:**
> ** You must remove drivers from ati before upgrading to jaunty**

There is a script in /usr/share/ati that will remove the fglrx drivers. It is absolutely required to do this since these drivers are not compatible with the Jaunty xserver. Failure to do so will result in the fglrx kernel modules for the new driver to not be loaded wich will result in the new driver falling back to indirect rendering and extremely poor performance if x does manage to start. In most cases x will not start at all after upgrading.

To fix this, run the uninstaller script in usr/share/ati and then use either Hardware Manager to get the driver or install the 9.4 driver from the ati web site.


I have a clean install made with Wubi, so older drivers are not the case here. Maybe it's just because of those many attempts to install them correctly. I'll try to completely remove the drivers and install them from scratch from ATI website.

As a sidenote:
Is there anybody with ATI HD4870 who managed to get properitary drivers to work and rebooted with no errors say... 5 times?
I can only get to the point when first reboot is ok, following ones give me black screen o.O

---

### Post by loquendo on 2009-04-25
I've installed the drivers successfully, however, the video playback on all media(internet or from HDD and all format - avi, mpg etc...) are choppy and annoying.  I will try later to get this drivers out and try the repo drivers.  Last resort, I'll try the ENVY NG way, since it has always been successful.  I'll keep you all posted!

---

### Post by fmfrisch on 2009-04-25
> **loquendo said:**
> I've installed the drivers successfully, however, the video playback on all media(internet or from HDD and all format - avi, mpg etc...) are choppy and annoying.  I will try later to get this drivers out and try the repo drivers.  Last resort, I'll try the ENVY NG way, since it has always been successful.  I'll keep you all posted!

I tried that it ended up crashing my xserver. Had to manually go back and restore the original xorg.conf file! It was a pain in the ***.

---

### Post by DangerIsGo on 2009-04-25
I tried the 9.4 drivers in ibex and they work fine, so its not a driver issue.  Its either a jaunty issue or, most likely, a jaunty/driver compatibility.  I wasn't able to install anything older than 9.4 on Jaunty.  This sucks.  I really want to get this working.

---

### Post by Redsunz on 2009-04-25
I have a ATI 4870 X2 and have not been able to get the restricted driver working either.  
I have reinstalled Ubuntu 9.04 about six times now after messing up my video drivers.
I did find this which sure beats re-installing and updating each time my display crashes.
Press escape key on grub start up.  then select recovery and drop to the terminal.
type this in apt-get remove --purge xorg-driver-fglrx 
then resume normal boot up and an error comes up about video error its extreamly hard to read due to the messed up color and small font size.
But after clicking on recover Ubuntu comes back up with open drivers.
Then I can try to install the restricted driver's again.
Good luck.

---

### Post by DangerIsGo on 2009-04-25
> **Redsunz said:**
> I have a ATI 4870 X2 and have not been able to get the restricted driver working either.  
I have reinstalled Ubuntu 9.04 about six times now after messing up my video drivers.
I did find this which sure beats re-installing and updating each time my display crashes.
Press escape key on grub start up.  then select recovery and drop to the terminal.
type this in apt-get remove --purge xorg-driver-fglrx 
then resume normal boot up and an error comes up about video error its extreamly hard to read due to the messed up color and small font size.
But after clicking on recover Ubuntu comes back up with open drivers.
Then I can try to install the restricted driver's again.
Good luck.

I did the same thing with the apt-get remove xorg-driver-fglrx but when I tried to resume normal boot up, it said that there was already a display at display:0 and that i could retry or start another one at display:1, which I did the both.  The first failed and the second worked, but I had a feeling that this would do the same thing again on each boot up.  I tried to reinstall the restricted drivers again, to no avail.  Anyone get this working?  Thanks.

---

### Post by Redsunz on 2009-04-25
> **DangerIsGo said:**
> I did the same thing with the apt-get remove xorg-driver-fglrx but when I tried to resume normal boot up, it said that there was already a display at display:0 and that i could retry or start another one at display:1, which I did the both.  The first failed and the second worked, but I had a feeling that this would do the same thing again on each boot up.  I tried to reinstall the restricted drivers again, to no avail.  Anyone get this working?  Thanks.

Yeah I had that error as well, start a new display option works for me and once I boot, shut down and restart it doesn't come up with any errors.
I still haven't been able to get the restricted driver working.  Dang I really wanted to play some Savage 2 tonight.  I'm hopping this will be sorted out soon.  Maybe with the next ATI driver?
In the mean time I set this Thread as my home page.

---

### Post by DangerIsGo on 2009-04-26
Ill try with the x64 and see if that does the same thing.  Probably will but doesn't hurt to try.

EDIT:  Nope.  Same thing.

---

### Post by DangerIsGo on 2009-04-26
Bump...anyone know of a fix?

---

### Post by markbuntu on 2009-04-26
You people really should read the release notes and installer instructions.

---

### Post by Redsunz on 2009-04-26
> **markbuntu said:**
> You people really should read the release notes and installer instructions.

I did read the release notes and they worked perfectly in Ubuntu 8.10 now it won't work in 9.04.

I just tried this.
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_restricted_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_restricted_drivers_manually)

The only problem I had trouble with was this.

"add the following line to the Device section (if it does not already exist). Include the following lines without [...]:

Section "Device"
	[...]
	Driver		"fglrx"
	[...]
EndSection
"
When I did it as described I got an error message about an invalid line.
So I left out the ...
Same thing as soon as I re-booted I got the Ubuntu loading window then BAM smeared colors and lock up.

---

### Post by s3lekta on 2009-04-27
> **bebox said:**
> Driver that is in the repository (2:8.600) is working...but horrible!compiz is awful, and vertical sync is also horrible.

In intrepid ibex the ati driver was working superb...

btw...a have ati HD 3400 series on my laptop...

Did anyone manage to get working the new ati driver (2:8.602) from amd site?

i got it working, but it is horribly choppy as hell, cpu & ram climbing up every so often when i try to do a task (like open firefox or hover over cairo dock icons ... it would not animate or allow me to launch) compiz works ... everything seem fine but is just choppy

i too have a hd 3400, installed through wubi... upgraded 8.10 to 9.04 through "upgrade manager & mounted alternate"

my last resort is probobly doing a clean install and running the drivers off ati's site again

---

### Post by bebox on 2009-04-27
it look's like all people that have a hd 3xxx series have a problem.

also me...i have hd 3470

---

### Post by Dave_Man on 2009-04-27
Hi, 

I am also having some of these issues.
Fresh install of Jaunty final.
ATI HD3200 card.

Installed official ATI drivers without problems from the "Hardware drivers" menu.
Synaptic shows that version 2:8.600 is installed.


Am having problems with choppy movies and high CPU load when compiz is enabled.
Also had a complete system crash when I tried to change to full screen.

Everything works OK when compiz is disabled.

I believe these problems are caused because the movie player doesn't offload the playback to the graphics card and uses the CPU alone instead.

Any help on how to fix this?

Thanks,
Dave.

---

### Post by sea_man on 2009-04-27
Same problem here.

In Ubuntu Studio 8.10 whit Catalyst 9.3 all work whit my 4850x2

but now whit the 9.04 nothing to do... Catalyst form AMD site, don`t work, restricted drivers don`t work... ](*,)

Please help !!

---

### Post by s3lekta on 2009-04-27
> **Dave_Man said:**
> Hi, 

I am also having some of these issues.
Fresh install of Jaunty final.
ATI HD3200 card.

Installed official ATI drivers without problems from the "Hardware drivers" menu.
Synaptic shows that version 2:8.600 is installed.


Am having problems with choppy movies and high CPU load when compiz is enabled.
Also had a complete system crash when I tried to change to full screen.

Everything works OK when compiz is disabled.

I believe these problems are caused because the movie player doesn't offload the playback to the graphics card and uses the CPU alone instead.

Any help on how to fix this?

Thanks,
Dave.

me you both, i guess i'll hold off on the clean install :(

---

### Post by DangerIsGo on 2009-04-27
Yeah 4870x2 here and still no go.  Tried again to no avail.  I hope they release new drivers soon to fix these because I really want to get on Jaunty.

---

### Post by markbuntu on 2009-04-28
Has anyone filed a bug report at launchpad or with ati?
If you don't file a bug report the devs will not know there are problems.

If anyone has filed a bug report please provide a link and those with the same problems can pile in.

One very important item that everyone here should be aware of. You absolutely must remove any ati proprietary driver **BEFORE** upgrading. Failure to do so will cause the new drivers DKMS kernel modules to not load which in turn will lead to serious performance issues up to and including x-server failure to start.

There is a script in usr/share/ati which will remove the fglrx driver. For anyone having problems I suggest you run the script and then restart in recovery kernel and use fix x option to revert to the VESA driver and then continue and when you get back to your desktop try the hardware driver restricted driver again.

The installer notes from ati state that old drivers must be removed before installing new ones. Upgrading from Intrepid to Jaunty means a new driver so......

---

### Post by screaminj3sus on 2009-04-28
so is the one in the repo still the beta? or do I need to install it manually from the site??

If its still the beta I think its freakin ridiculous they wont upgrade from a crappy beta quality driver in the repos to the final.

---

### Post by Pitboss on 2009-04-28
I don't give a rat's ***, anymore. I'm using the opensource driver, and I maybe lacking some smooth compiz effects, but I don't have memory problems, and my X server doesn't crash.

---

### Post by asuastrophysics on 2009-04-28
> **nibbana84 said:**
> New driver work just with newer cards... So does Ubuntu 9.04. You have to use open driver (radeon).

i have a card i bought back in early september:

ATI Radeon HD 2400 Pro

is this going to be supported in catalyst 9.4? six months really isnt that old for a video card...

---

### Post by markbuntu on 2009-04-28
> **asuastrophysics said:**
> i have a card i bought back in early september:

ATI Radeon HD 2400 Pro

is this going to be supported in catalyst 9.4? six months really isnt that old for a video card...

From the release notes

ATI Workstation Product Support
        The ATI CatalystTM Linux software suite is designed to support the following ATI
        Workstation products:
                     AMD Workstation Family Product Support
         ATI FireProTM V8700                    ATI FireGLTM V8650
         ATI FireProTM V7750                    ATI FireGLTM V8600
         ATI FireProTM V5700                    ATI FireGLTM V7700
         ATI FireProTM V3750                    ATI FireGLTM V7600
         ATI FireProTM V3700                    ATI FireGLTM V5600
         ATI FireProTM 2450                     ATI FireGLTM V3600
         ATI FireProTM 2260
ATI MobilityTM and Integrated MobilityTM Product Family
Support
        The ATI CatalystTM Linux software suite is designed to support the following ATI MobilityTM
        products:
                        AMD Mobility Product Family Support
         ATI Mobility RadeonTM X3870            ATI Mobility RadeonTM X3430
         ATI Mobility RadeonTM X3850            ATI Mobility RadeonTM X3400
         ATI Mobility RadeonTM X3830            ATI Mobility RadeonTM X2600
         ATI Mobility RadeonTM X3670            ATI Mobility RadeonTM X2400
         ATI Mobility RadeonTM X3650            ATI Mobility RadeonTM X2300
ATI Desktop Product Family Support
        The ATI CatalystTM Linux software suite is designed to support the following ATI
        desktop products:
                        AMD Desktop Product Family Support
         ATI RadeonTM HD 4890 Series            ATI RadeonTM HD 4350 Series
         ATI RadeonTM HD 4870 X2 Series         ATI RadeonTM HD 3800 Series
         ATI RadeonTM HD 4850 X2 Series         ATI RadeonTM HD 3600 Series
         ATI RadeonTM HD 4800 Series            ATI RadeonTM HD 3400 Series
         ATI RadeonTM HD 4670 Series            ATI RadeonTM HD 2900 Series
         ATI RadeonTM HD 4650 Series            ATI RadeonTM HD 2600 Series
         ATI RadeonTM HD 4600 Series            ATI RadeonTM HD 2400 Series
         ATI RadeonTM HD 4550 Series
                                                                                                  2
                               ATI Proprietary Linux Release Notes
                   Note: The ATI RadeonTM HD 3870 X2 series of product is currently
                   not supported by the ATI CatalystTM Linux software suite.
                   Note: All-in-WonderTM variants based on the above are also
                   supported. However, video capture is not supported.
                   Note: Software driver support for ATI FireGLTM, Integrated,
                   MobilityTM and Desktop products prior to the RadeonTM 9500 is
                   available from [www.amd.com](www.amd.com).
ATI Integrated Product Family Support
         The ATI CatalystTM Linux software suite is designed to support the following ATI
         desktop products:
                              AMD Chipset Product Support
          ATI RadeonTM HD 3300 Series          ATI RadeonTM 3100 Series
          ATI RadeonTM HD 3200 Series          ATI RadeonTM 3000 Series
AMD FireStream Product Family Support
         The ATI CatalystTM Linux software suite is designed to support the following AMD
         products:
                            AMD FireStream Product Support
          AMD FireStream 9270                 AMD FireStream 9170
          AMD FireStream 9250

---

### Post by Redsunz on 2009-04-28
> **markbuntu said:**
> Has anyone filed a bug report at launchpad or with ati?
If you don't file a bug report the devs will not know there are problems.

If anyone has filed a bug report please provide a link and those with the same problems can pile in.

One very important item that everyone here should be aware of. You absolutely must remove any ati proprietary driver **BEFORE** upgrading. Failure to do so will cause the new drivers DKMS kernel modules to not load which in turn will lead to serious performance issues up to and including x-server failure to start.

There is a script in usr/share/ati which will remove the fglrx driver. For anyone having problems I suggest you run the script and then restart in recovery kernel and use fix x option to revert to the VESA driver and then continue and when you get back to your desktop try the hardware driver restricted driver again.

The installer notes from ati state that old drivers must be removed before installing new ones. Upgrading from Intrepid to Jaunty means a new driver so......

Thanks Mark.
I just did everyone on this Thread please add your name to the bug.  So the Ubuntu team can see its affecting many users.
[https://bugs.launchpad.net/bugs/368964](https://bugs.launchpad.net/bugs/368964)
If you don't have a Launchpad account just register it only takes a minute.  Please I really want to get back to my 3d Linux Gaming :)
I used the following headline "ati restricted driver not working in Jaunty"
So while you may have different hardware the problem its still the same problem  ATI restricted driver no longer working in Jaunty!!!

---

### Post by screaminj3sus on 2009-04-28
> **markbuntu said:**
> From the release notes

ATI Workstation Product Support
        The ATI CatalystTM Linux software suite is designed to support the following ATI
        Workstation products:
                     AMD Workstation Family Product Support
         ATI FireProTM V8700                    ATI FireGLTM V8650
         ATI FireProTM V7750                    ATI FireGLTM V8600
         ATI FireProTM V5700                    ATI FireGLTM V7700
         ATI FireProTM V3750                    ATI FireGLTM V7600
         ATI FireProTM V3700                    ATI FireGLTM V5600
         ATI FireProTM 2450                     ATI FireGLTM V3600
         ATI FireProTM 2260
ATI MobilityTM and Integrated MobilityTM Product Family
Support
        The ATI CatalystTM Linux software suite is designed to support the following ATI MobilityTM
        products:
                        AMD Mobility Product Family Support
         ATI Mobility RadeonTM X3870            ATI Mobility RadeonTM X3430
         ATI Mobility RadeonTM X3850            ATI Mobility RadeonTM X3400
         ATI Mobility RadeonTM X3830            ATI Mobility RadeonTM X2600
         ATI Mobility RadeonTM X3670            ATI Mobility RadeonTM X2400
         ATI Mobility RadeonTM X3650            ATI Mobility RadeonTM X2300
ATI Desktop Product Family Support
        The ATI CatalystTM Linux software suite is designed to support the following ATI
        desktop products:
                        AMD Desktop Product Family Support
         ATI RadeonTM HD 4890 Series            ATI RadeonTM HD 4350 Series
         ATI RadeonTM HD 4870 X2 Series         ATI RadeonTM HD 3800 Series
         ATI RadeonTM HD 4850 X2 Series         ATI RadeonTM HD 3600 Series
         ATI RadeonTM HD 4800 Series            ATI RadeonTM HD 3400 Series
         ATI RadeonTM HD 4670 Series            ATI RadeonTM HD 2900 Series
         ATI RadeonTM HD 4650 Series            ATI RadeonTM HD 2600 Series
         ATI RadeonTM HD 4600 Series            ATI RadeonTM HD 2400 Series
         ATI RadeonTM HD 4550 Series
                                                                                                  2
                               ATI Proprietary Linux Release Notes
                   Note: The ATI RadeonTM HD 3870 X2 series of product is currently
                   not supported by the ATI CatalystTM Linux software suite.
                   Note: All-in-WonderTM variants based on the above are also
                   supported. However, video capture is not supported.
                   Note: Software driver support for ATI FireGLTM, Integrated,
                   MobilityTM and Desktop products prior to the RadeonTM 9500 is
                   available from [www.amd.com](www.amd.com).
ATI Integrated Product Family Support
         The ATI CatalystTM Linux software suite is designed to support the following ATI
         desktop products:
                              AMD Chipset Product Support
          ATI RadeonTM HD 3300 Series          ATI RadeonTM 3100 Series
          ATI RadeonTM HD 3200 Series          ATI RadeonTM 3000 Series
AMD FireStream Product Family Support
         The ATI CatalystTM Linux software suite is designed to support the following AMD
         products:
                            AMD FireStream Product Support
          AMD FireStream 9270                 AMD FireStream 9170
          AMD FireStream 9250

So I take it that means it DOES support the mobility 2xxx? (I have a x2600)

And is the version in the repos still beta?

---

### Post by emarkay on 2009-04-28
Bump.

---

### Post by screaminj3sus on 2009-04-28
all I did is download the driver from ati, cd to the dir, type sudo ./sh <driver name> and it installed finr on 9.04 64 bit.

---

### Post by emarkay on 2009-04-28
> **screaminj3sus said:**
> all I did is download the driver from ati, cd to the dir, type sudo ./sh <driver name> and it installed finr on 9.04 64 bit.

Do I have to uninstall anything that may be already there?  FGLRX, ATI, ???

---

### Post by Redsunz on 2009-04-29
> **screaminj3sus said:**
> all I did is download the driver from ati, cd to the dir, type sudo ./sh <driver name> and it installed finr on 9.04 64 bit.

The 9600 is a nvidia and you installed a ATI driver???
It sounds like it probably worked and you just installed a unneeded driver.
The people on this forum have ATI cards.

---

### Post by screaminj3sus on 2009-04-29
> **Redsunz said:**
> The 9600 is a nvidia and you installed a ATI driver???
It sounds like it probably worked and you just installed a unneeded driver.
The people on this forum have ATI cards.

What crack are you on? in my post eariler I stated I have an ATI MOBILITY X2600 

Which is VERY MUCH an ati. I have a 9600gt on my other pc.

I'm sitting here using compiz with my ati driver which I installed, please don't assume I'm that much of an idiot I know what freakin card I have.

---

### Post by urbanphilosopher on 2009-04-29
[SIZE=2]Hello, my new machine (including a 4870X2) arrived yesterday and jaunty went straight onto it and of course i hit the same problem described here.

Given that this release and my graphics drivers just don't mix, is it worth wiping and starting again with 8.10 and what would be the disadvantages of doing so?

As you may have noticed I'm a bit of newbie - my Ubuntu experience previously has been limited to proof-of-concept testing for the new machine.
[/SIZE]

---

### Post by emarkay on 2009-04-29
Let's get all the Jaunty 9.04 ATI HD 2 series card data on one post to get this solved:

[http://ubuntuforums.org/showthread.php?t=1133931](http://ubuntuforums.org/showthread.php?t=1133931)

---

### Post by fmfrisch on 2009-04-29
> **bebox said:**
> Driver that is in the repository (2:8.600) is working...but horrible!compiz is awful, and vertical sync is also horrible.

In intrepid ibex the ati driver was working superb...

btw...a have ati HD 3400 series on my laptop...

Did anyone manage to get working the new ati driver (2:8.602) from amd site?

I'm on a HD 3650 and also having problems with Compiz. Minimizing/Maximizing windows etc. I've seen a lot of people having problems with their HD 3xxx and 4xxx. Anyone else?

I downloaded my driver from ATI's website and it made no difference to me

---

### Post by screaminj3sus on 2009-04-29
> **fmfrisch said:**
> I'm on a HD 3650 and also having problems with Compiz. Minimizing/Maximizing windows etc. I've seen a lot of people having problems with their HD 3xxx and 4xxx. Anyone else?

I downloaded my driver from ATI's website and it made no difference to me

same problem with mobility 2600 with repo driver and the one from the ati site.

---

### Post by Melcar on 2009-04-29
The slow response with Compiz I think is due to xserver 1.6 (either the xserver itself, the driver, or a combination).  Everyone already using xserver 1.6 was reporting these same issues, but most Ubuntu users still using the patched xserver 1.5 were only reporting minimal issues that were eventually resolved.  Now that everyone is on Jaunty and xserver 1.6, everyone is reporting regressions with fglrx's composite support.

---

### Post by Redsunz on 2009-04-29
> **screaminj3sus said:**
> What crack are you on? in my post eariler I stated I have an ATI MOBILITY X2600 

Which is VERY MUCH an ati. I have a 9600gt on my other pc.

I'm sitting here using compiz with my ati driver which I installed, please don't assume I'm that much of an idiot I know what freakin card I have.

Im on the crack that made me read your signature :)
"EVGA 9600gt"

---

### Post by Redsunz on 2009-04-29
*UPDATE**
So the bug I reported is a duplicate of 313027.
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/313027](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/313027)
"fglrx does not support xserver 1.6"
Apparently its a bug in ATI's driver that was not exposed until the new xserver was released?  So we are waiting until ATI releases its next driver.
Can we just roll back xserver to 1.5 until ATI releases the new driver?
I went in to Synaptic Package manager and the force version is grayed out.
How do you activate it?

---

### Post by Melcar on 2009-04-29
Supposedly it's due to a change in the way the Compiz version in Jaunty handles window management (particularly maximizing/minimizing).  Straight from the fglrx devs. on the beta mailing list.  True or not I don't know, but it would not be the first time Compiz breaks/changes things.  Mind you, the open source driver also exhibits similar regressions, but not as noticeable (for me it's only delayed maximizing windows).

---

### Post by screaminj3sus on 2009-04-30
> **Melcar said:**
> Supposedly it's due to a change in the way the Compiz version in Jaunty handles window management (particularly maximizing/minimizing).  Straight from the fglrx devs. on the beta mailing list.  True or not I don't know, but it would not be the first time Compiz breaks/changes things.  Mind you, the open source driver also exhibits similar regressions, but not as noticeable (for me it's only delayed maximizing windows).

Well nvidias drivers seem to handle the change flawlessly, just installed jaunty on my desktop computer and compiz runs smooth as hell compared to the ati card and vsync actually works.

---

### Post by Melcar on 2009-04-30
The nvidia driver is very intrusive and replaces most of the underlying graphics structure.  A lot of applications end up running differently because of this.  Just because the nvidia driver runs it fine does not necessarily mean that everything is peachy.

---

### Post by Longinus00 on 2009-04-30
Has anyone been able to get big desktop working? I can get my two monitors working perfectly using the open source drivers but there is no 3D acceleration for my card yet (4850). As soon as they get halfway decent 3D implemented in the radeon drivers I'll dump fglrx in a heartbeat, but in the meantime is there anyway to get big desktop back?

---

### Post by urbanphilosopher on 2009-04-30
[SIZE=2]Update: I did a fresh install of 8.10 and all was well - that is until Intrepid installed some updates and there goes my graphics  - presumably it updated xorg or similar to an incompatible version.  I see a Windows purchase rearing it's ugly head.[/SIZE]

---

### Post by cajunaggie on 2009-04-30
urbanphilosopher,
It *is* technically an illegal hack of Windows, but might I suggest using TinyXP instead?

---

### Post by Redsunz on 2009-04-30
So how long until Catalyst 9.5 comes out?  What its been a week already.
I'm not waiting more than two weeks.  This is B.S. my 4870X2 is obsolete.
The last time I bought a ATI card before this one was in 1998 ATI express.
They couldn't get their open gl driver working back then either.  Which is why I wasn't going to ever buy an ATI card again.  But I did with the 4870X2 because it was supposed to be the best at the time.  I guess I forgot the hardware is only as good as the software driver.
Any one have any suggestions on a high end Nvidia?

---

### Post by urbanphilosopher on 2009-05-01
[SIZE=2]Although I'm rather pleased that someone's sharing my 4870x2 problems, I suppose I should still suggest some alternatives.

The absolute best (even slightly better than the 4870x2) is the GTX295 - this is another dual GPU card - in this case two GTX275s.
The best route if you wanna go a step down from that is SLi - two GTX260s would be a good choice, this would be roughly equivalent (possibly a slight loss) to the 4870x2.
[/SIZE]

---

### Post by DangerIsGo on 2009-05-02
So it looks to be mostly dealing with the x2 cards.  Does anyone have any insight as to when AMD might release a driver update?  Like past fixes, on avg, how long it takes?

---

### Post by bstanley on 2009-05-02
> **screaminj3sus said:**
> Well nvidias drivers seem to handle the change flawlessly, just installed jaunty on my desktop computer and compiz runs smooth as hell compared to the ati card and vsync actually works.
I am using a Radeon 7000/VE  (rv100 QY) card with jaunty and compiz responds and works well except
after about 15 minutes of use (or there abouts), the system will just completely lock up.
I have to do a hardware reset to get the system back.  I am using the open source driver.

Is this a problem with the driver or with compiz?

---

### Post by VastOne on 2009-05-02
> **Redsunz said:**
> So how long until Catalyst 9.5 comes out?  What its been a week already.
I'm not waiting more than two weeks.  This is B.S. my 4870X2 is obsolete.
The last time I bought a ATI card before this one was in 1998 ATI express.
They couldn't get their open gl driver working back then either.  Which is why I wasn't going to ever buy an ATI card again.  But I did with the 4870X2 because it was supposed to be the best at the time.  I guess I forgot the hardware is only as good as the software driver.
Any one have any suggestions on a high end Nvidia?

This past week I built a new computer and decided on a Gigabyte MB with a built in RadeonHD 3300.  It is the first ATI card I have used in many years and I wish I had read deeper in these forums before I bought it.  The MB itself is fine and I will obviously keep it, but I have disabled the Radeon and installed a 512k GeForce 9400 GT and it is perfect. I have a high end samsung HD LCD screen and I am getting true 1900 * 1200 running perfectly with nVidia 180.51 drivers as does Compiz, Emerald and any video.

With the ATI card, everything suffered. Videos (esp full screen), music, and the general performance of a Phenom II 8 gig machine sucked.

As soon as I booted up with the nVidia card, this machine has rocked like I expected it to.

I seriously doubt I will ever consider anything with an ATI graphics card again

VastOne

---

### Post by asuastrophysics on 2009-05-03
I installed Catalyst 9.4 in hopes that compiz would work.
....No change at all. 
I've got an ATI HD Radeon 2400 Pro and it is supported under the release. 
How long am I stuck with metacity? Should I just scrap Jaunty and stay with 8.10 for a couple more months? 
Metacity is almost completely unusable. Are there any solutions out there?

---

### Post by Redsunz on 2009-05-04
> **asuastrophysics said:**
> I installed Catalyst 9.4 in hopes that compiz would work.
....No change at all. 
I've got an ATI HD Radeon 2400 Pro and it is supported under the release. 
How long am I stuck with metacity? Should I just scrap Jaunty and stay with 8.10 for a couple more months? 
Metacity is almost completely unusable. Are there any solutions out there?

If you have Ubuntu 8.10 installed you might want to stay with that until ATI comes out with a fix.  
I have Jaunty installed it defiantly boots faster and everything seems a little faster but I have no 3d which really sucks.
All the applications have been updated Open Office 3 ect.
I'm waiting for ATI's next driver I don't really want to re-install Ubuntu 8.10 and reconfigure everything again.
I'm not sure how long my patience with ATI will hold out, I'm seriously considering a new Nvidia card.

---

### Post by lvleph on 2009-05-04
ATI Forums complaint thread.
```
http://forums.amd.com/game/messageview.cfm?catid=260&threadid=112829&enterthread=y
```

---

### Post by defaria on 2009-05-04
OK, lacking a solution for my 3200 HD can anybody suggest an alternative card that works?

It doesn't look like the ATI driver for my specific video card will be coming out anytime soon and I'm at the point of giving up on this motherboard ATI card and I'm thinking perhaps it'd be best to just buy a better video card and install it instead of continue to fight this problem. Question is: What would be a good video card to buy for my system. I want to use my dual monitor as well as compiz style effects. I want to be able to run Boxee or XBMC as well as Google Earth or Cool Iris. I also want to be able to play DVD videos, etc. IOW I want a video card that performs well. I don't necessarily need a card that handles Crysis or that does heavy gaming as I have a PS3. But if the video card can handle it without breaking the bank then why not?

So what video card do you use that works with 9.04 64-bit, does dual monitor and 3d acceleration without a hitch?

---

### Post by asuastrophysics on 2009-05-04
> **defaria said:**
> OK, lacking a solution for my 3200 HD can anybody suggest an alternative card that works?

It doesn't look like the ATI driver for my specific video card will be coming out anytime soon and I'm at the point of giving up on this motherboard ATI card and I'm thinking perhaps it'd be best to just buy a better video card and install it instead of continue to fight this problem. Question is: What would be a good video card to buy for my system. I want to use my dual monitor as well as compiz style effects. I want to be able to run Boxee or XBMC as well as Google Earth or Cool Iris. I also want to be able to play DVD videos, etc. IOW I want a video card that performs well. I don't necessarily need a card that handles Crysis or that does heavy gaming as I have a PS3. But if the video card can handle it without breaking the bank then why not?

So what video card do you use that works with 9.04 64-bit, does dual monitor and 3d acceleration without a hitch?

ANYTHING man. Anything other than ATI. 
particularly, go for an nVidia card. Go for one with a LOT of video memory, 500MB - 1GB 
and hopefully has dual core GPU's

---

### Post by defaria on 2009-05-04
> **asuastrophysics said:**
> ANYTHING man. Anything other than ATI. 
particularly, go for an nVidia card. Go for one with a LOT of video memory, 500MB - 1GB 
and hopefully has dual core GPU's

I could have sworn I've heard other state they've had problems with nvidia cards too - hence my hesitation. If I can just hear one person say "Yeah get card X. It works with 64-bit, does dual monitors and all the compiz stuff and I can run Boxee, GoogleEarth and stuff like that without a problem" I'd run out and buy it today.

BTW: I'm not really looking to do gaming as I'll do my gaming on my PS3. However getting a card that does all I've asked for above is problem a card of gaming class.

Would this be good: [EVGA GTS 250 SC 1GB PCI-Express Video Card]("http://shop3.frys.com/product/5867493?site=sr:SEARCH:MAIN_RSLT_PG")

---

### Post by VastOne on 2009-05-04
> **defaria said:**
> I could have sworn I've heard other state they've had problems with nvidia cards too - hence my hesitation. If I can just hear one person say "Yeah get card X. It works with 64-bit, does dual monitors and all the compiz stuff and I can run Boxee, GoogleEarth and stuff like that without a problem" I'd run out and buy it today.

BTW: I'm not really looking to do gaming as I'll do my gaming on my PS3. However getting a card that does all I've asked for above is problem a card of gaming class.

Would this be good: [EVGA GTS 250 SC 1GB PCI-Express Video Card]("http://shop3.frys.com/product/5867493?site=sr:SEARCH:MAIN_RSLT_PG")

GeForce 9400 GT does all that you ask and more... Mine is 512k and as a non gamer, I am completely satisfied running it HD 1900 * 1200 on my Samsung pure 1080 LCD.

I am installing a GeForce 9500 GT 1 gig tomorrow and will give you the results of that but from what I have read from others who have used it I am positive I will be quite happy...

---

### Post by defaria on 2009-05-05
OK so I got the GeForce 9500 GT 1GB DD$2 PCI-E 2.0. Installed it and switched to the proprietary drivers (NVIDIA accelerated graphics drive (version 180) [Recommended]. After a lot of hassle I finally got it to be dual monitor. Seems the Nvidia X Server Settings wants to re-write /etc/X11/xorg.conf yet it fails to run the application as root so it can't write that file and even if I chmod it so it can write the file it still screws up! I had to copy and paste configurations to get it to utilize both of my monitors. 

Still I am unable to get any compiz stuff working. Cool Iris works (yeah!) and Boxee does somewhat (although playing of audio screws up and sometimes things play at fast forward or the audio doesn't start and I've had segv's... ugh!). GoogleEarth doesn't work...

OK, let's take it one step at a time. Given this new Nvidia card, how am I supposed to get compiz, let's say the cube, working. Or the wobbly Windows? Because it doesn't work for me at all!

---

### Post by one51 on 2009-05-05
> **Longinus00 said:**
> Has anyone been able to get big desktop working? I can get my two monitors working perfectly using the open source drivers but there is no 3D acceleration for my card yet (4850). As soon as they get halfway decent 3D implemented in the radeon drivers I'll dump fglrx in a heartbeat, but in the meantime is there anyway to get big desktop back?

Hi Longinus, Can I ask you what driver/versions/settings you have with the open source options that are working with dual monitors?  This is my main blocking point.  I don't use much 3D but the missing dual monitors is about to force me to buy a cheap Nvidia card (instead of my onboard 3200HD).

After a bad experience with audio, I will not try any Launchpad drivers for my video.

My setup: Ubuntu Jaunty, Asus M4A78 Pro, built-in ATI 3200 (unfortunately)

---

### Post by VastOne on 2009-05-05
> **defaria said:**
> OK so I got the GeForce 9500 GT 1GB DD$2 PCI-E 2.0. Installed it and switched to the proprietary drivers (NVIDIA accelerated graphics drive (version 180) [Recommended]. After a lot of hassle I finally got it to be dual monitor. Seems the Nvidia X Server Settings wants to re-write /etc/X11/xorg.conf yet it fails to run the application as root so it can't write that file and even if I chmod it so it can write the file it still screws up! I had to copy and paste configurations to get it to utilize both of my monitors. 

Still I am unable to get any compiz stuff working. Cool Iris works (yeah!) and Boxee does somewhat (although playing of audio screws up and sometimes things play at fast forward or the audio doesn't start and I've had segv's... ugh!). GoogleEarth doesn't work...

OK, let's take it one step at a time. Given this new Nvidia card, how am I supposed to get compiz, let's say the cube, working. Or the wobbly Windows? Because it doesn't work for me at all!

In System/Preferences/Appearance the last tab is visual effects. Make sure that you have selected either normal or extra (I always select extra).  If you get no errors, then compiz is working. Then you must install the Compiz configuration settings manager from Synaptic manager.  Then the tweaking begins..Look within these forums for the how-tos on Cube setup, emerald and on and on...the compiz manager is pretty self explanatory so try out some of the things on yer own..Google Earth sounds like a flash issue.  Are you running 64 bit Ubuntu?  If so, make sure you have only the Alpha 64 bit Adobe flash code running... I will wait for your answer to go any further


:guitar:

VastOne

---

### Post by defaria on 2009-05-05
I appreciate you sticking with me and being patient. Yes I'm running 64 bit. I'll worry about Google Earth later. That app is not essential and there are other, different problems with it (Like when it starts up it complains about not being able to create the directory /root/.googleearth! Excuse me? Why are you trying to do that! Anyway...)

Yeah I forgot about having to toggle that on. One would think if you ran the compiz-settings-manager it would either turn it on for you, warn about it not being on, or offer a toggle to turn in on right in the compiz-settings-manager. I find all of Ubuntus settings and the like (X and Linux/Unix in general) to be all over the play with no cohesive strategy or sense.

When I try to enable either Normal or Extra I get a dialog box stating "The Composite extension is not available". There are threads about that problem. No time to work on this now - gotta get to work but will continue tonight. Gee you'd think they'd put a toggle here too... Ugh. This need not be this difficult...

Oh, yes, another wonderful UI innovation here - the dialog stating "The Composite extension is not available" does not close. It has only an OK button. Clicking it does nothing! You gotta hit the X to close that dialog.

---

### Post by VastOne on 2009-05-05
> **defaria said:**
> I appreciate you sticking with me and being patient. Yes I'm running 64 bit. I'll worry about Google Earth later. That app is not essential and there are other, different problems with it (Like when it starts up it complains about not being able to create the directory /root/.googleearth! Excuse me? Why are you trying to do that! Anyway...)

Yeah I forgot about having to toggle that on. One would think if you ran the compiz-settings-manager it would either turn it on for you, warn about it not being on, or offer a toggle to turn in on right in the compiz-settings-manager. I find all of Ubuntus settings and the like (X and Linux/Unix in general) to be all over the play with no cohesive strategy or sense.

When I try to enable either Normal or Extra I get a dialog box stating "The Composite extension is not available". There are threads about that problem. No time to work on this now - gotta get to work but will continue tonight. Gee you'd think they'd put a toggle here too... Ugh. This need not be this difficult...

Oh, yes, another wonderful UI innovation here - the dialog stating "The Composite extension is not available" does not close. It has only an OK button. Clicking it does nothing! You gotta hit the X to close that dialog.

First thing is to make sure that you have nVidia X Server Settings and when you click on it that it tells you that you have the drivers loaded. If not, it will tell you immediately.  If this is the case you may just have to go back into Administration/Hardware Drivers and re-enable nVidia 180.  I have had to do this on a couple of occasions in switching around cards and/or drivers.   If they are installed and you are getting these messages, we will approach it from another angle.

---

### Post by Longinus00 on 2009-05-05
> **one51 said:**
> Hi Longinus, Can I ask you what driver/versions/settings you have with the open source options that are working with dual monitors?  This is my main blocking point.  I don't use much 3D but the missing dual monitors is about to force me to buy a cheap Nvidia card (instead of my onboard 3200HD).

After a bad experience with audio, I will not try any Launchpad drivers for my video.

My setup: Ubuntu Jaunty, Asus M4A78 Pro, built-in ATI 3200 (unfortunately)

I have a hd4850 and I was able to get the dual monitors working on a clean install. By default it mirrors the screens I opened up the Display Preferences under System->Preferences and just unchecked the "mirror screens" checkbox. After that you can move the screens around in the window they have representing your monitors. I think that they are stacked one on top of another by default so just drag it around and you'll see both screens.

I actually am much more impressed by the open source implementation of multi-screen setups than bigdesktop. My two monitors are not the same resolution so when I set up bigdesktop there is actually some desktop that is outside what I can see. This causes the background to be applied to a bigger area that I can see and it seems to screw around with virtualbox's full screen integration mode.

---

### Post by one51 on 2009-05-05
> **Longinus00 said:**
> I have a hd4850 and I was able to get the dual monitors working on a clean install. By default it mirrors the screens I opened up the Display Preferences under System->Preferences and just unchecked the "mirror screens" checkbox. After that you can move the screens around in the window they have representing your monitors. I think that they are stacked one on top of another by default so just drag it around and you'll see both screens.


My god.  After reading dozens of threads about BigDesktop, binary drivers, and people recommending I try this or that PPA (no thanks)... this worked on the first try.  Who would have thought something in Linux could be as simple as a Display Preferences configuration window.

In the past my smaller resolution display always had a very distorted output when I tried both at once.  And no xorg configuration file that I saw looked like it would do what I needed: just display non-blurry desktops on both monitors.  I didn't even think to look for something as simple as a config window.

I have yet to try it with one or the other of the monitors turned off.  But at least in principle it works!  Longinus, that makes your suggestion the most useful and successful of any I've had in my 1 month of Linux use so far.  THANK YOU!

---

### Post by Longinus00 on 2009-05-05
> **one51 said:**
> My god.  After reading dozens of threads about BigDesktop, binary drivers, and people recommending I try this or that PPA (no thanks)... this worked on the first try.  Who would have thought something in Linux could be as simple as a Display Preferences configuration window.

In the past my smaller resolution display always had a very distorted output when I tried both at once.  And no xorg configuration file that I saw looked like it would do what I needed: just display non-blurry desktops on both monitors.  I didn't even think to look for something as simple as a config window.

I have yet to try it with one or the other of the monitors turned off.  But at least in principle it works!  Longinus, that makes your suggestion the most useful and successful of any I've had in my 1 month of Linux use so far.  THANK YOU!

No problem. This is actually the first release where I've gotten the gnome display preferences window to actually work correctly so props to the maintainers. Of course if I try using fglrx, the display preferences window hangs my computer for awhile (it also does this any time the resolution changes) which it definitely didn't do before. :(

---

### Post by defaria on 2009-05-05
> **VastOne said:**
> First thing is to make sure that you have nVidia X Server Settings and when you click on it that it tells you that you have the drivers loaded. If not, it will tell you immediately.

OK, **System: Administration: NVIDA X Server Settings**. First screen shows me **Operating System:** *Linux-x86_64*, **NVIDIA Driver Version:** *180.44* (**NV_Control Version:** *1.17*, **X Screens:** *1 (Xinerama)*). So it looks like I indeed have Nvidia drivers loaded.

BTW: This is the dialog where when I click on **Save to X Configuration File** I get a dialog stating:

[INDENT]Unable to remove old X config backup file '/etc/X11/xorg.config.backup'[/INDENT]

Even though both /etc/X11/xorg.config.backup and xorg.config are 666. Even if I chown to me it **still** get this error!

> If this is the case you may just have to go back into Administration/Hardware Drivers and re-enable nVidia 180.  I have had to do this on a couple of occasions in switching around cards and/or drivers.   If they are installed and you are getting these messages, we will approach it from another angle.

Looks like we'll need that other angle. When I go to **System: Administration: Hardware Drivers** it says "Searching for available drivers" then puts up a dialog box that say I have the **NVIDIA accelerated graphics driver (version 180) [Recommended]**. There is another one listed, **NVIDIA accelerated graphics driver (version 173)**. Perhaps I'll try that...

OK, about the only difference is that **NVIDIA X Server Settings** says **NVIDIA Driver Version:** [i173.14.15[/i] and **NV-Control Version:** *1.16*. Still trying **System: Appearance: Visual Effects** toggling on **Extra** (or **Normal**) yields:

[indent]The Composite extension is not available[/indent]

I'll re-activate 180 and then I'm off to looking for threads about that error message... Sure wish this would just work out of the box...

---

### Post by VastOne on 2009-05-06
> **defaria said:**
> OK, **System: Administration: NVIDA X Server Settings**. First screen shows me **Operating System:** *Linux-x86_64*, **NVIDIA Driver Version:** *180.44* (**NV_Control Version:** *1.17*, **X Screens:** *1 (Xinerama)*). So it looks like I indeed have Nvidia drivers loaded.

BTW: This is the dialog where when I click on **Save to X Configuration File** I get a dialog stating:

[INDENT]Unable to remove old X config backup file '/etc/X11/xorg.config.backup'[/INDENT]

Even though both /etc/X11/xorg.config.backup and xorg.config are 666. Even if I chown to me it **still** get this error!



Looks like we'll need that other angle. When I go to **System: Administration: Hardware Drivers** it says "Searching for available drivers" then puts up a dialog box that say I have the **NVIDIA accelerated graphics driver (version 180) [Recommended]**. There is another one listed, **NVIDIA accelerated graphics driver (version 173)**. Perhaps I'll try that...

OK, about the only difference is that **NVIDIA X Server Settings** says **NVIDIA Driver Version:** [i173.14.15[/i] and **NV-Control Version:** *1.16*. Still trying **System: Appearance: Visual Effects** toggling on **Extra** (or **Normal**) yields:

[indent]The Composite extension is not available[/indent]

I'll re-activate 180 and then I'm off to looking for threads about that error message... Sure wish this would just work out of the box...

Take a look at this thread and try some of it's suggestions. It is older but maybe something will trigger a solution or you or I to continue on...

[http://ubuntuforums.org/showthread.php?t=436110](http://ubuntuforums.org/showthread.php?t=436110)

And this...

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/231697](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/231697)

What I do not understand is why it is a bug for some and not others..

---

### Post by asuastrophysics on 2009-05-06
> **VastOne said:**
> GeForce 9400 GT does all that you ask and more... Mine is 512k and as a non gamer, I am completely satisfied running it HD 1900 * 1200 on my Samsung pure 1080 LCD.

I am installing a GeForce 9500 GT 1 gig tomorrow and will give you the results of that but from what I have read from others who have used it I am positive I will be quite happy...

he's right man. i know you're hesitant to buy nVidia, but with linux, it's the lesser of the three evils.

ATI cards suck, and since upgrading to jaunty, my intel chipset now sucks too...thanks canonical. I haven't had properly working compiz ever since upgrading. probably won't ever be fixed.

---

### Post by defaria on 2009-05-07
The fix that most people said worked for them was to install xserver-xgl. Yet when I try apt-get install xserver-xgl it state Couldn't find package xserver-xgl. I do have a package named nvidia-glx-180 installed though.

Also, when I type in say nvidia-settings I get "Xlib: extension RANR missing on display :0.0"

Ugh! Your second link points out that this is busted!

> This bug remains.. Anytime Xinerama is enabled the composite extension shows its going to be enabled in the log, but does not. There is also now a bug in Jaunty that causes the mouse cursor to stick to the xscreen on all video cards.. So if you move the mouse from one monitor to the next it leaves a "copy" of the mouse cursor behind on the previous xscreen you transitioned from right where the mouse transitioned to the next monitor.. If you move the mouse back the cursor picks right back up on your mouse movements.. This was not in intrepid, but is now in Jaunty.. I read someplace this is a bug in the kernel, but I have yet to find the bug report..

Main issue of this report howerver - remains.. When Xinerama is enabled with nvidia drivers - composite is disabled.

So it looks like I'll have to go back to Frys and return this. So again, I'm back to asking, does anybody have...

Wait a second! I tried a number of things and viola! Now I'm working. I don't know which thing I did that caused it to work. On thing I did was to download EnvyNG. I also changed to TwinView mode. Now I'm working. Great...

---

### Post by VastOne on 2009-05-07
> **asuastrophysics said:**
> he's right man. i know you're hesitant to buy nVidia, but with linux, it's the lesser of the three evils.

ATI cards suck, and since upgrading to jaunty, my intel chipset now sucks too...thanks canonical. I haven't had properly working compiz ever since upgrading. probably won't ever be fixed.

I would not blame it on canonical.  IMHO, one of the major difference between Ubuntu/Linux and any Microsoft updates is that there is no fear in going forward and allowing us, the owners and users, to assist in resolving issues with these new releases.

ATI is trying very hard to keep up with Ubuntu and I applaud their efforts. nVidia is slightly better (IMHO) but not without major issues of their own.  Both should be greatly applauded for seeing the future of Linux and keeping up with every kernel change there is....This is really a great view of Open Source and how companies are working together.  I have worked in this area for many years and I can tell you it is amazing at how fast both companies (and others) are keeping up with us and our needs and the Linux changes....

Hang in there, help will find a way...

VastOne

---

### Post by VastOne on 2009-05-07
> **defaria said:**
> The fix that most people said worked for them was to install xserver-xgl. Yet when I try apt-get install xserver-xgl it state Couldn't find package xserver-xgl. I do have a package named nvidia-glx-180 installed though.

Also, when I type in say nvidia-settings I get "Xlib: extension RANR missing on display :0.0"

Ugh! Your second link points out that this is busted!



So it looks like I'll have to go back to Frys and return this. So again, I'm back to asking, does anybody have...

Wait a second! I tried a number of things and viola! Now I'm working. I don't know which thing I did that caused it to work. On thing I did was to download EnvyNG. I also changed to TwinView mode. Now I'm working. Great...

Wow, in the 11th hour, he comes through!

I would suspect that EnvyNG may have completely cleaned all traces of any other driver and put the exact settings in place....

And, I ma totally happy with this card (nVidia Geforce 9500 GT 1 gig) for 60 bucks, it ROCKS...as do the current nvid drivers...

Happy you finally made it dude:P

VastOne

---

### Post by defaria on 2009-05-07
The one remaining issue is that my two displays are not the same size. I'm not sure but I believe this TwinView thing insists on treating both screens as just one large display thus if I size my larger monitor as 1600x1200 then my smaller screen at 1280x1024 I get about an inch of extra space on the smaller screen. IOW I can move windows off the smaller display itself. 

Now it's off to Boxee and getting that working...

Just for reference, here's my xorg.conf file

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@crested)  Sun Feb  1 20:25:37 UTC 2009

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder62)  Tue Mar 24 06:15:32 PST 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500 GT"
EndSection

Section "Screen"

# Removed Option "TwinView" "True"
# Removed Option "MetaModes" "nvidia-auto-select, nvidia-auto-select"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "NoLogo" "True"
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "RandRRotation" "True"
    Option         "DisableGLXRootClipping" "True"
    Option         "DamageEvents" "True"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: 1280x1024 +1600+0, DFP: 1600x1200 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection


```

---

### Post by ssri on 2009-05-10
Hey,

I created Intrepid debs from the linux driver on ATI/AMD's site (8.602).  My chip is listed in the 9.4 release notes as being supported (Mobility Radeon x2300).  Purged 9.3 from my 6910p laptop and dpkg -i --force-overwrite the new debs (x86_64).  Installation went without a hitch, dkms modules were automatically added, etc.  However, aticonfig --initial -f did not work, which gave me an inkling that all was not well.  Rebooted and intrepid couldn't startx, forcing me to login at the prompt.  fglrxinfo could not identify my card and left a "null screen()" message.  Purged 9.4 and reinstalled my Intrepid 9.3 debs and everything is back to normal.  I assume this indicates my card is not supported even though it is listed on ATI/AMD's release notes as otherwise.  Or maybe 9.4 does not play well with x server 1.5.2?  Anyone got around this?  I just want to test both opensource and ATI's restricted drivers for their 3D capability (I do imaging research) before jumping into Jaunty.  Everything is working fine on Intrepid, and I can remain patient, but I do not want to bork my system when I have a grant due in a few weeks.

---

### Post by one51 on 2009-05-10
> **ssri said:**
> Everything is working fine on Intrepid, and I can remain patient, but I do not want to bork my system when I have a grant due in a few weeks.

The drivers finally installed for me on my HD3200.  Video was slow and jerky, and maximizing the screen crashed X.  I don't know the details of what is wrong with this driver, but even if it does partly work, it's much worse than the open-source drivers.

I recommend after my experience, and that of others I've read about here, to keep on waiting.

My plan is to wait until this thread is filled with replies saying "Wow, the 9.x (10.x?) drivers actually work well with Jaunty and my HDxxxx card!"  Then I'll try again.

---

### Post by ssri on 2009-05-10
> **one51 said:**
> The drivers finally installed for me on my HD3200.  Video was slow and jerky, and maximizing the screen crashed X.  I don't know the details of what is wrong with this driver, but even if it does partly work, it's much worse than the open-source drivers.

I recommend after my experience, and that of others I've read about here, to keep on waiting.

My plan is to wait until this thread is filled with replies saying "Wow, the 9.x (10.x?) drivers actually work well with Jaunty and my HDxxxx card!"  Then I'll try again.

Yeah, I've heard those who have supported cards complain about the regression in performance with Catalyst 9.4.  I decided in the beginning that I will wait too, albeit testing new Catalyst and opensource builds from time to time ;).  Still, it does not hurt to hold the feet of those responsible close to the fire in order to *ahem* speed up the process.

---

### Post by markbuntu on 2009-05-11
It seems to me that the 9.4 driver is totally borked. I was hoping to get a more recent flgrx working with my rt kernel on Hardy 64 since the last one to work was 8.6 but the rt patch was misplaced into the wrong directory so the build cannot find it. No reply to my bug report on that yet.

I guess I will just wait for the next release......and lurk the forums for a while before trying it out. I have not even attempted to use this driver in Jaunty because of all the bugs people were reporting.

If you are having problems the only way the devs will know about them is if you file a bug report. So please, file bug reports against fglrx at Launchpad or at the ati bugzilla.

---

### Post by guizmo124 on 2009-05-13
Hi,
I have the same problems as some of you (HD3400 -- crash in full screen, horrible vsync ...) but it seems that ATI heard us, in some way ...    Catalyst 9.4 for Linux  are no longer available on AMD website. AMD went back to 9.3

---

### Post by Clancy_s on 2009-05-14
> **guizmo124 said:**
> Catalyst 9.4 for Linux  are no longer available on AMD website. AMD went back to 9.3

It's available atm.

---

### Post by guizmo124 on 2009-05-14
It's weird, if the regional parameters of the site is set to north America, 9.4 is available but since 05/13, it's no longer available with regional set to France. I haven't check for other locations.

---

### Post by one51 on 2009-05-14
> **guizmo124 said:**
> It's weird, if the regional parameters of the site is set to north America, 9.4 is available but since 05/13, it's no longer available with regional set to France. I haven't check for other locations.

Perhaps the French have wisely banned version 9.4 of the Catalyst drivers.  :-P

---

### Post by Clancy_s on 2009-05-14
> **guizmo124 said:**
> It's weird, if the regional parameters of the site is set to north America, 9.4 is available but since 05/13, it's no longer available with regional set to France. I haven't check for other locations.

I'm in Aus - still working here.

more amd oddity???

---

### Post by braveerudite on 2009-05-15
I have ATI 4870 and the propietary drivers suck major !@#$%.

What is ATI waiting for?  Why they ignoring us Linux users. This is one of the major reasons Linux gaming sucks.

---

### Post by TTonic on 2009-05-15
I got it working straight from the "box" with 9.4 / 9.04. Downloaded the drivers from Ati's netsite and after that, all i had to do was "sudo sh ./ati-something-driver" and automatic installer did the rest. Compiz is working, even Trackmania Nations Forever is somewhat working. 

Radeon Ati 2600 PRO / 256MB (PCI-E)

---

### Post by HavocXphere on 2009-05-15
HD3850 on a Jaunty x64 install. Driver from ati site.

[LIST]
[*]Nexuiz/Games -> Works well enough, but below Windows standards on performance
[*]Glxgears -> Worse fps than open-source driver
[*]Loads of rendering glitches in ubuntu (without compiz). Parts of the windows just go black. Not cool.
[*]Compiz slow on Maximize/minimize
[*]OpenGL output on VLC pixilated
[/LIST]

Not sure how to split the blame between ATI / Xorg1.6 / Compiz.

Not all that happy about the situation.:rolleyes:

On a positive note though, the flashing glxgears/OGL is gone though.

---

### Post by Nathan.Flow on 2009-05-15
> **markbuntu said:**
> Has anyone got dual monitors working with this driver?
I installed it on one of my Hardy (amd64) installs and there seems to be no way to get big desktop working. So I removed it with the script and went back to 9.3 and now I can't get big desktop there either. I hear it is the same in Jaunty with this driver. This is really bad.

In Jaunty I am using the radeon driver which seems fine for my HD3650. I would rather have a big desktop than compiz at this point. The 9.3 driver works great on my other Hardy(i386) and on Intrepid amd64. 

I think I will just skip this one.

look up the commands using aticonfig --help.

I got big desktop to work with an 4870 in harty using the command line. use the aticonfig command line find the command for dule head inital, then run desktop = horzontal, then run the command for xrandrea.. you might get the error can't enable while xradnr is enabled..

---

### Post by Redsunz on 2009-05-15
Catalyst 9.5 is supposed to be out today its not on ATI site yet but apparently some people have it already any one try it yet??
I googled it.

---

### Post by ebucha on 2009-05-15
I'm running it on Jaunty X64.  Here is the link to the installer: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-5-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-5-x86.x86_64.run)  It's been on the file server since this morning.

Observations:
1) Xinerama is still borked - I think this is an issue with Xorg and Xinerama at this point
2) Monitor setup in CCC is working better but still not what I would call finished (especially for multi-monitor setups)
3) Using Aticonfig with multi-head still doesn't work very well
4) There are a few graphical anomalies (courser and redraw weirdness)
5) User prompts and dialogs now show up in the middle of a monitor when using a virtual screen for multi-monitor (they used to show up in the center of the virtual screen)
6) Application maximization now works properly by default - maximize to monitor not screen 

Overall I'd say it's a good improvement.  Assuming you have a working Xorg.conf this release should only make your system work better.

---

### Post by andy17 on 2009-05-15
hi mates,

I got a ATI RADEON 3100 integrated and I'm on KUBUNTU 9.04...
using proprietary drivers keeps crashing the system, what should I do to activate 3d???

thanks!

---

### Post by Redsunz on 2009-05-15
9.5 drivers still not working.  I just finished re-installing Ubuntu.
Same thing as before they appear to install okay then on reboot my system locks up and the display has a bunch of weird colors all over it.
That's it for me I'm going to go buy a Nvidia card.
4870X2 big waste of money!!

---

### Post by fmfrisch on 2009-05-16
I'm on a Radeon 3650. With the upgrade to Jaunty and the new XOrg/ATI 9.4 I encounted these problems with compiz enabled:

*Slow maximization of windows
*Crash when video in fullscreen
*3D games or other 3D software lagging
*More CPU usage than before

When now upgrading to the brand new ATI driver 9.5 I cannot say that I can see any difference in performance compared to before..

Just thought I should share

---

### Post by DangerIsGo on 2009-05-16
> **Redsunz said:**
> 9.5 drivers still not working.  I just finished re-installing Ubuntu.
Same thing as before they appear to install okay then on reboot my system locks up and the display has a bunch of weird colors all over it.
That's it for me I'm going to go buy a Nvidia card.
4870X2 big waste of money!!

Yeah, I had the same thing.  Did doing the aticonfig --initial -f work for you?  I thought I did that last time, but didnt work for me with 9.4.  I mean, I'm not going to go ahead and get a new video card just for linux (sorry, heh), but I'm just disappointed that they 'support' linux but do it in a half-assed way.

---

### Post by markbuntu on 2009-05-16
I just found an interesting thread:

[http://ubuntuforums.org/showthread.php?t=1152121](http://ubuntuforums.org/showthread.php?t=1152121)

---

### Post by divxclub on 2009-05-16
> **Redsunz said:**
> 9.5 drivers still not working.  I just finished re-installing Ubuntu.
Same thing as before they appear to install okay then on reboot my system locks up and the display has a bunch of weird colors all over it.
That's it for me I'm going to go buy a Nvidia card.
4870X2 big waste of money!!

I feel you. I got ASUS 4870x2 ... the TRI_FAN one and screen is all messed up . I made a little video here to show.

[http://www.youtube.com/watch?v=sFzRUkQS7_U](http://www.youtube.com/watch?v=sFzRUkQS7_U)

---

### Post by VastOne on 2009-05-16
> **one51 said:**
> Perhaps the French have wisely banned version 9.4 of the Catalyst drivers.  :-P

:lolflag:

---

### Post by Redsunz on 2009-05-17
> **DangerIsGo said:**
> Yeah, I had the same thing.  Did doing the aticonfig --initial -f work for you?  I thought I did that last time, but didnt work for me with 9.4.  I mean, I'm not going to go ahead and get a new video card just for linux (sorry, heh), but I'm just disappointed that they 'support' linux but do it in a half-assed way.

Nope the aticonfig --initial -f
didn't work for me.
My new Nvidia card is in the mail never again will I buy an ATI card!!

---

### Post by Redsunz on 2009-05-17
> **divxclub said:**
> I feel you. I got ASUS 4870x2 ... the TRI_FAN one and screen is all messed up . I made a little video here to show.

[http://www.youtube.com/watch?v=sFzRUkQS7_U](http://www.youtube.com/watch?v=sFzRUkQS7_U)

That looks good compared to what happened to mine.  The Ubuntu Logo kind of showed up then a blurred mess!!

---

### Post by DangerIsGo on 2009-05-17
> **divxclub said:**
> I feel you. I got ASUS 4870x2 ... the TRI_FAN one and screen is all messed up . I made a little video here to show.

[http://www.youtube.com/watch?v=sFzRUkQS7_U](http://www.youtube.com/watch?v=sFzRUkQS7_U)

same thing as me! Exactly!

---

### Post by markbuntu on 2009-05-17
that looks like missing kernel modules.

---

### Post by rbond on 2009-05-20
anybody played with 9.5 yet...did not seem to help my performance much

EDIT: It did, however, seem to fix the problem when I maximized a screen it maximized it across both monitors...now it only maximizes inside of the monitor the application is running

---

### Post by Exsecrabilus on 2009-05-20
So after I download the .RUN file, do I open up Terminal and do the usual "sudo sh" command, or do I make .DEB files out of that .RUN file? (which I read how to do on some AMD-Linux tutorial site)

Which one is better and why? Is the second way easier to uninstall or what?

---

### Post by markbuntu on 2009-05-20
The first way is the best. It makes it easier to uninstall. Only use the making deb route if the first method fails. If you are using an rt kernel that does not matter, both methods will fail becasue the rt patch is misplaced and DKMS cannot find it to make a successful build.

---

### Post by robspangler on 2009-05-22
> **rbond said:**
> anybody played with 9.5 yet...did not seem to help my performance much
 
EDIT: It did, however, seem to fix the problem when I maximized a screen it maximized it across both monitors...now it only maximizes inside of the monitor the application is running
 
I've been messing with it (9.5) for a couple of days now and can't seem to get it to work correctly. I am having the same issues as has been previously stated and in the video that was posted...scrambled "Ubuntu" screen and PC locks up. I have a Dell OptiPlex 755 (Intel) with an ATI Radeon HD 2400 Pro and dual monitors. I have gotten it to work on a single display (mirrored on both monitors), but as soon as I attempt to configure dual screens I start having problems. I have settled (for now) on having the two monitors configured as two separate desktops (I forget what the name was, Independent Screens or something) and it does seem to work, but I would prefer to have the single desktop stretched across both screens. It seems that if I enable the "Xinerama" function, which I understand is required to stretch the desktop, all hell breaks loose... This is my work PC so I only use it for Internet, word processing, and I run VMware with a Windows host, so I can't comment on the graphics performance. I am hoping that a fix will be coming in the very near future, and am posting here in case anyone figures out a work-around in the meantime...
 
Thanks,
Rob Spangler

---

### Post by Tomatosoup on 2009-05-22
Also got a scrambled screen, with my ATI Radeon 3870 X2 video card (using proprietary driver). Using Ubuntu 9.04 (64-bit).

Open-source driver has low frame rate. Can't even view videos decently. Choppy. Too bad.

But no solution yet?

---

### Post by asuastrophysics on 2009-05-24
i doubt there ever will be. 

video drivers suck in linux. period. 
really high performance graphics cards that were capable of running some of the newest, most realistic games on windows can barely render some glxgears and compiz on ubuntu. 

and don't try to argue that WINE will run games at decent quality. that is wishful thinking. it is only capable of running games that are older than a decade or more. OpenGL will never be directx. games that were designed to run on directx will fail miserably under opengl because opengl is inferior. 

bottom line: linux gives your advanced hardware the capabilities of a desktop calculator. it doesnt matter how much $$$$$ you fork over for your high end gear. all of it is useless under ubuntu. i get the same performance out of this $200 laptop that i do out of my $4,000 machine. 

I'm sorry there's no solution to your ATI problems, but people seem to forget one very important principle: You get what you pay for.

---

### Post by travis.cthall on 2009-05-24
I'll have to try this and report back

---

### Post by alphacrucis2 on 2009-05-24
> **rbond said:**
> anybody played with 9.5 yet...did not seem to help my performance much

EDIT: It did, however, seem to fix the problem when I maximized a screen it maximized it across both monitors...now it only maximizes inside of the monitor the application is running

For me 9.5 seems to have removed the problem with googleearth flickering when desktop effects are enabled.

---

### Post by rbond on 2009-05-25
> **alphacrucis2 said:**
> For me 9.5 seems to have removed the problem with googleearth flickering when desktop effects are enabled.

You know...I have not even tried to enable desktop effects. When I do it, I get a prompt saying that "Desktop effects could not be enabled" with an OK button. I wonder why it won't let me. Any suggestions anyone?

Thanks.

---

### Post by Redsunz on 2009-05-26
I got mine working!  After having the Catalyst 9.5 driver crash my Computer with a blurry screen on startup I bought a new Nvidia card. ;) While the drivers are not perfect either.  It was like night and day Google Earth even works perfectly.  The Nvidia X server Settings menu item doesn't run in Super User mode so any settings you make are not saved had to type in the command in terminal superseded with sudo.  I also had to edit my xorg file to put in the correct frequency and resolution settings apparently my LG LCD TV screen has the firmware programmed incorrectly.  Good luck waiting on those ATI drivers to correct the problem. The open source drivers will probably support 3d before ATI gets it right.

---

### Post by Tomatosoup on 2009-05-27
> **Redsunz said:**
> I got mine working!  After having the Catalyst 9.5 driver crash my Computer with a blurry screen on startup I bought a new Nvidia card. ;) While the drivers are not perfect either.  It was like night and day Google Earth even works perfectly.  The Nvidia X server Settings menu item doesn't run in Super User mode so any settings you make are not saved had to type in the command in terminal superseded with sudo.  I also had to edit my xorg file to put in the correct frequency and resolution settings apparently my LG LCD TV screen has the firmware programmed incorrectly.  Good luck waiting on those ATI drivers to correct the problem. The open source drivers will probably support 3d before ATI gets it right.

Another 'solution': use Windows. ;)
You have circumvented it, but not solved it.

---

### Post by zika on 2009-05-27
> **Tomatosoup said:**
> Another 'solution': use Windows. ;)
You have circumvented it, but not solved it.
Chuck Norris uses ATI card in Ubuntu ... :)

---

### Post by one51 on 2009-05-27
> **zika said:**
> Chuck Norris uses ATI card in Ubuntu ... :)

LOL

Maybe we should send Chuck Norris over to ATI and roundhouse a few more Linux developers out of 'em.

---

### Post by dvalphen on 2009-06-12
For those of you still struggling to get fglrx working for X2 cards, use the 9.4 catalyst driver. Got it working this morning using the updated instructions in the wiki at [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

In particular the "sudo aticonfig --initial -f --adapter=all" command after installing the debs made all the difference.

fglrxinfo now produces:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4870 X2
OpenGL version string: 2.1.8591

Visual effects works, flash video great, xvid also good.

---

### Post by 321limelight on 2009-07-12
This is my first time trying to post onto a forum.

I have been mussing with Ubuntu for over a year, and I have an AIW9600XT video card which had installed well using the Ubuntu defaults when I moved up to 9.04. I checked off the proprietary drivers for ATI in the Add/Remove software section of my system in an attempt to gain the functionality of my TV tuner. On my next reboot a day or so later I get splashed/ smeared video where I should be seeing my Ubuntu splash screen.

I have spent hours on the net and all over these forums. and at this point seems fairly obvious I need to revert back to the open source defaults. My card is legacy now and was running well with the open source drivers until I picked a fight with it. I am having some challenges even getting to a command line, as my graphics splash me all over the monitor after I hit the Ubuntu splash screen after leaving Grub, and my computer does not seem to want to let me boot Parted Magic from my optical drive despite my efforts in BIOS setup and hitting a good variety of keys during boot. [sigh] I have tried using all the options in the recovery mode, and it did not help at all. On the forums I found as a possibility:

[B]sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial -f[/B]
(reboot)

Would that be what I would type into the command line [once I find a way in] to manually re-install the default open source video drivers? So I can get back into my Add/remove software or Synaptic and uninstall the troublesome proprietary restricted ATI package. 

Barring that possiblility if I do a full fresh install of Ubuntu 9.04 onto my machine do I lose my settings and files? Other than now being locked out by my frozen video card my machine was running top form for an old beater. And yes it is a dual boot I'm over on the XP side to do the search and recovery research.

Can anyone offer thoughts or insight?

---

### Post by one51 on 2009-07-12
I guess you don't need much or any 3D performance if you are using open source drivers?

Since I was on this thread for months trying to get my onboard ATI 3200HD to work I'll give an update.  ATI driver support blows, and I bought a cheap ($50) fanless NVIDIA 9500GT last week.  Installed the drivers manually by downloading the .run file from NVIDIA.  Everything worked flawlessly on the first try.  Compiz, 3D screensavers, and even Doom 3.  The performance is not great in Doom 3, barely better than the card I played it on 4 years ago (in Windows), and it's a bit jerky.  But the best I ever got from the ATI chip was... nothing.  So NVIDIA is a vast improvement in driver support.  Even the dual-monitor support works perfectly through the NVIDIA monitors tool, which sets up the xorg.conf for Jaunty just fine!

cheers,
dave

---

### Post by Nathan.Flow on 2009-07-20
Looking for some help with multiple moniters and KDE 4.x+ can't seem to get the hole extended desktop thing to work, Got it working fine in kde 3.5 just no luck in KDE 4.x+ 

Any help appreciated

---

### Post by markbuntu on 2009-07-21
> **Nathan.Flow said:**
> Looking for some help with multiple moniters and KDE 4.x+ can't seem to get the hole extended desktop thing to work, Got it working fine in kde 3.5 just no luck in KDE 4.x+ 

Any help appreciated

The only way I found to get 2 monitors to work in KDE4 with my ati cards is to use fglrx and disable randr. Directions are here

[http://ubuntuforums.org/showthread.php?t=1152121](http://ubuntuforums.org/showthread.php?t=1152121)

---

### Post by zetanuxi on 2009-07-21
> **SorinN said:**
> I installed the driver from AMD site and all seem to work OK (I build debs first from the .run file, then I install debs).

How do you build .deb packages from the .run file. I tried unpacking the .run file and installing it and it gave me an error saying my distribution was not supported.

---

### Post by internalkernel on 2009-07-21
> **zetanuxi said:**
> How do you build .deb packages from the .run file. I tried unpacking the .run file and installing it and it gave me an error saying my distribution was not supported.

```
sh ati-driver-installer-9-6-x86.x86_64.run --buildpkg Ubuntu/jaunty 
```

from:
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

---

### Post by ezcex on 2009-07-21
Hi guys, so I've read through this thread and it looks like ATI is just **** with linux, but I'm going to post my problem anyways just incase it's different. I am on a gigabyte mobo with amd II x4 955 cpu and sapphire radeon 4890 with 4gb gskill ram. My system is in dualboot and windows 7 works perfectly fine, but my ubuntu 9.04 won't go full resolution or dual screen. They only mirror each other. When I go to the panel and displays thing, the mirror check box is not even clicked, i tried dragging the little box in the display settings but no other box was behind it. When I try to install the propietery drivers from the hardware drivers option, everything is super slow, it takes forever to get back into the display options to deactivate the drivers. It kinda sucks not getting full resolution from my screens but it sucks even more that i cant dual screen them. So even if I use the open source drivers, i can't dual screen my monitors, is there a way to fix this? Sorry for the wall of text, thanks in advance.
 
 
edit: fix'd

---

### Post by mr_e_uss on 2009-09-06
See this link: [http://ubuntuforums.org/showthread.php?t=1237478](http://ubuntuforums.org/showthread.php?t=1237478)

"stalet"'s post claims that fglrx works now with the W500 and V5700.  Is it possible that the newest versions of ATI Catalyst (now at version 9.8) works properly?

---

### Post by iboot on 2009-09-06
I have an HP txt2z tablet running Ubuntu 9.04 (fresh install). In order to get auto-rotation to work, I set the following:

aticonfig --set-pcs-str="DDX,EnableRandr12,TRUE"

After setting, Xorg would refuse to load. When I used the following in recovery mode:

```
sudo aticonfig --initial -f --adapter=all
```

Machine booted up fine. Thanks!

---

