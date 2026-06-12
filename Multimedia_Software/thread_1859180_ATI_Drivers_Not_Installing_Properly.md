---
title: "ATI Drivers Not Installing Properly"
date: 2011-10-13
forum: Multimedia Software
---

### Post by Apache14 on 2011-10-13
Hi i have installed a clean install of 11.10 and seem to be having issues activation the ATI prop. driver from "additional drivers"

It tells me that it faild and to look at jockey.log, the only error i can see is 

> ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing

(BTW the driver i installed was the post rls update one)

I also have issues installing with apt-get as one of the servers times out (dunno if that will be affecting this) but thats just a ubuntu server issue id imagin

Any ideas ?

Many Thanks In Advance

---

### Post by ExnuX on 2011-10-13
Same problem here.

systemspecs:
Asus E35M1-I DELUXE 
Crucial M4 SSD 64 GB
Kingston 8GB 1333 DDR3 Non-ECC CL9 DIMM (Kit of 2) 8GB 1333MHz 

running the 64bit version

attached my jockey log

---

### Post by Apache14 on 2011-10-13
Ohh yer my setup is 

AMD Phenom X6 1055t
ATI (AMD) HD5870 1GB
ASUS 990fx sabertooth mobo

---

### Post by possibarendless on 2011-10-13
Same issue, 

ATI Radeon HD 2400 XT
AMD Athlon 64 X2 5200+
64 bit Ubuntu 11.10

---

### Post by jemartti on 2011-10-13
I'm having the same issue, only with the post-release version though. I can install the regular release just fine. Clean release of 11.10.

System specs:
3GiB memory
Intel Q8200
Radeon HD3400

---

### Post by Morientes on 2011-10-13
Same problem. I installed via the "restricted drivers" program but got an error. It seems the driver is installed though. If I run the flgxinfo I get the proper output and I can run the aticcc program as well and configure the driver so it seems to work. The restricted drivers program still tells me that the driver is not activated, though...

---

### Post by cgolson84 on 2011-10-13
I am having problems getting the ATI proprietary drivers installed also.  I have tried using the additional hardware method, building my own packages with the .run file with --buildpkg Ubuntu/oneiric, aswell as trying to just sudo sh the .run file.  None of these methods work for me on either 32 or 64 bit.

ATI Mobility Radeon HD 5650
Core i5
4GB Ram
64 bit Ubuntu 11.10

---

### Post by mwolfe on 2011-10-13
Same problem here,
Ubuntu 11.10

Radeon HD 4850
core i7 920

---

### Post by 4Orbs on 2011-10-13
> I am having problems getting the ATI proprietary drivers installed also. I have tried using the additional hardware method, building my own packages with the .run file with --buildpkg Ubuntu/oneiric, aswell as trying to just sudo sh the .run file. None of these methods work for me on either 32 or 64 bit.
If you managed to build the debs without errors: On my machine it was necessary to install the debs using the force overwrite command found on the wiki page near the bottom of the page under "Issues" "Errors were encountered processing fglrx/amdcccle".

---

### Post by cgolson84 on 2011-10-13
> **4Orbs said:**
> If you managed to build the debs without errors: On my machine it was necessary to install the debs using the force overwrite command found on the wiki page near the bottom of the page under "Issues" "Errors were encountered processing fglrx/amdcccle".

Can you link the wiki page you are talking about?  I don't see anything.

---

### Post by 4Orbs on 2011-10-13
[These are the instructions]("http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide") I followed. They are meant for Natty, but work the same for Oneiric.

The wiki is actually more complicated than necessary IMHO. All I did was download the .run script to my Downloads folder; open the terminal in that folder and sudo sh the script... which opened the ATI installer interface, which allowed me to choose direct install or build the debs. I chose to have the installer build the debs...  When finished, I installed the debs with the force overwrite command in the terminal. Of course it was still necessary to first install the prerequisite packages listed at the top of the page, including the 32bit libraries (I'm running a 64bit system). I had also first purged the existing fglrx stuff using the instructions for removing the existing driver on the same page.

---

### Post by cgolson84 on 2011-10-13
> **4Orbs said:**
> [These are the instructions]("http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide") I followed. They are meant for Natty, but work the same for Oneiric.

The wiki is actually more complicated than necessary IMHO. All I did was download the .run script to my Downloads folder; open the terminal in that folder and sudo sh the script... which opened the ATI installer interface, which allowed me to choose direct install or build the debs. I chose to have the installer build the debs...  When finished, I installed the debs with the force overwrite command in the terminal. Of course it was still necessary to first install the prerequisite packages listed at the top of the page, including the 32bit libraries (I'm running a 64bit system). I had also first purged the existing fglrx stuff using the instructions for removing the existing driver on the same page.

Thanks, I'm going to try this out in a minute.  I will post my results back here.

---

### Post by 4Orbs on 2011-10-13
Oh, I forgot to mention the important last step. You need to initialize the installation after it's finished by:
1. hit CTRL+ALT+F2 so you exit the desktop and go to a shell.
2. Login the shell and password
3. sudo aticonfig --initial -f
4. Then reboot with the command sudo shutdown -r now

---

### Post by cgolson84 on 2011-10-13
If xserver-xorg-video-radeon or xserver-xorg-video-ati are installed should i remove them before installing the catalyst?  It seems logical but don't know if I should or not.

---

### Post by 4Orbs on 2011-10-13
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
```
These two commands (run each separately) should get everything out of your way so you'll be starting with a clean slate. The first command won't do anything unless you've already attempted to install the catalyst driver manually. Won't do any harm to run it anyway. There is no need to do anything from Synaptic Pkg Mgr... if that's what you are referring to.

If you used the "Additional Drivers" in Ubuntu to activate the drivers from the Ubu repo: if it shows the driver is activated you might want to deactivate it before anything else. And reboot.

---

### Post by 4Orbs on 2011-10-13
If all works correctly, when you do the step to initialize the installation from the console you should see a message something like this:

Warning; unable to hash xorg.conf so renaming it to xorg.con.bak
Adding new xorg.conf in it's place.

My wording isn't accurate, but you'll know what I mean if you see it. That should indicate that all was successful.

And after you reboot, your resolution might be different and the desktop might not fill the entire screen. If that happens, open the Catalyst Control Center and use the overscanning adjustment to resize the desktop.

---

### Post by cgolson84 on 2011-10-13
> **4Orbs said:**
> If all works correctly, when you do the step to initialize the installation from the console you should see a message something like this:

Warning; unable to hash xorg.conf so renaming it to xorg.con.bak
Adding new xorg.conf in it's place.

My wording isn't accurate, but you'll know what I mean if you see it. That should indicate that all was successful.

And after you reboot, your resolution might be different and the desktop might not fill the entire screen. If that happens, open the Catalyst Control Center and use the overscanning adjustment to resize the desktop.

I just tried these instructions and they didn't work for me.  Everything appeared to install correctly but when I rebooted it froze during boot while checking battery state and all that.  I think maybe it has to do with the fact that my laptop has switchable graphics.  It's a shame because it works fine in other distros.

---

### Post by 4Orbs on 2011-10-13
When you did the aticonfig --initial did you get the warning message that a new xorg.conf file was created?

---

### Post by cgolson84 on 2011-10-13
> **4Orbs said:**
> When you did the aticonfig --initial did you get the warning message that a new xorg.conf file was created?

Yea.  It installed like other distros.  aticonfig --initial gave the new file created reconfiguring messages but it didn't work.  This works fine in other versions of ubuntu for me so I'm assuming something is changed in 11.10 that causes a conflict.  Frustrating, as I really like 11.10 otherwise.

---

### Post by 4Orbs on 2011-10-13
Is this an Ubuntu installation to the hard drive, or did you install it from inside Windows with the wubi installer?

---

### Post by cgolson84 on 2011-10-13
> **4Orbs said:**
> Is this an Ubuntu installation to the hard drive, or did you install it from inside Windows with the wubi installer?

Installed from the 64 bit desktop live cd

---

### Post by 4Orbs on 2011-10-13
Yes, but did you do an actual installation to the hard drive? If you used wubi, then Ubuntu is installed inside a virtual machine on Windows and can be removed the same way you'd remove a Windows application. Did you re-partition your hard drive and create a new partition for Ubuntu plus a swap partition for Ubuntu?

---

### Post by cgolson84 on 2011-10-13
> **4Orbs said:**
> Yes, but did you do an actual installation to the hard drive? If you used wubi, then Ubuntu is installed inside a virtual machine on Windows and can be removed the same way you'd remove a Windows application. Did you re-partition your hard drive and create a new partition for Ubuntu plus a swap partition for Ubuntu?
Yea I installed to a new partition.  Never used wubi

---

### Post by 4Orbs on 2011-10-13
You should be able to get back to the desktop by booting into the recovery mode (on grub) and selecting root shell with networking, then enter this command:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bad
```
And if that works with no error you can then reboot:
```
sudo shutdown -r now
```
And you should be back at your desktop, but without the proprietary driver. Then you can decide what to do next.

---

### Post by cgolson84 on 2011-10-13
> **4Orbs said:**
> You should be able to get back to the desktop by booting into the recovery mode (on grub) and selecting root shell with networking, then enter this command:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bad
```
And if that works with no error you can then reboot:
```
sudo shutdown -r now
```
And you should be back at your desktop, but without the proprietary driver. Then you can decide what to do next.

Luckily I happen to have a dual boot installed right now with win 7 (happened to be playing some windows games lately) so I just booted into that.  Now I am gonna have to continue my search for a decent Ubuntu alternative.

---

### Post by 4Orbs on 2011-10-13
O.k. For what it's worth, the open source Gallium driver that comes standard with Ubuntu works pretty well, with enough 3d to run effects and some games, and great 2d that will play most movies quite nicely. The catalyst driver that installs from "Additional Drivers" isn't very different from the latest Catalyst available from ATI website. But the latest is the one to use if you want to run Gnome Shell. Good luck with whatever you choose instead.

---

### Post by Earsplit on 2011-10-13
Same problem here... I'm gonna keep trying to purge/reinstall via jockey.

I managed to get this working earlier today...

ATI Radeon Mobility HD4670 1gb in a Dell SXPS1645

edit:
Just got it working...
I did a "sudo apt-get purge" for everything related to fglrx, rebooted into GNOME classic, and tried again.

---

### Post by 4MUL8R on 2011-10-13
I have a Intel D875PBZ Pentium 4 with a new HIS 4670 video card in hopes of getting HDMI output to a big screen.  I upgraded via internet to 11.10 and have boot error.  As a newbie, I am having a bit of trouble.  I tried to remove anything ATI related using the terminal commands.  I cannot install from the fancy Ubuntu software center, and get an error to the jockey.log file that I cannot understand.  I'll try to follow the steps above.

---

### Post by rmcnamara on 2011-10-13
This is my first post on ubuntuforums. I am having the same problems with my ATI card which is a 5770 1gb. This is very frustrating. I have not been using ubuntu very long but i have not any problems like this with installing video drivers. I have followed all of the guides i have read.

Also one other thing any kind of updating seems to be taking extremely long. I'm guessing ubuntus servers are very slow because of this being release day and all. Anyone else experiencing this.

Thanks 
Rob

---

### Post by 4Orbs on 2011-10-13
Even if jockey crashes and says the driver failed to install, it might really have installed as the poster above said... even if it shows not-activated. I just this past hour installed Lubuntu and selected the plain fglrx (not the post release option) and it installed without error, but it was very slow to download and complete. It seems to work just as good as installing the newest driver from ati manually.

---

### Post by ExnuX on 2011-10-14
This still isn't working for me.
Tried purging and manually compiling but without result.


Any "easy" solutions?
Don't want to make really obscure changes to my freshly installed htpc.

---

### Post by collisionystm on 2011-10-14
> **ExnuX said:**
> This still isn't working for me.
Tried purging and manually compiling but without result.


Any "easy" solutions?
Don't want to make really obscure changes to my freshly installed htpc.

I had problems with 11.10 installing. It would go to a black screen.

I managed to get it installed with the alternative install cd, and then after removing xserver-xorg-video-ati and rebooting I was able to boot into Ubuntu.

I tried to install the ATI Catalyst from the website. I ran the ATI config for single mode. It modified the xorg. I rebooted. System would not boot up. It would freeze.

I had to do the following to fix....

Reboot your computer

after bios, hold the SHIFT KEY

Go to system rescue

hit the resume normal boot and hold the SHIFT KEY

this should take you into safe mode and a command prompt.

Login

sudo apt-get purge fglrx

If it fails, look at the error log. I had to manually run the fglxr uninstall script.

Once finished re-install

sudo apt-get install fglrx

reboot.


Hope this helps.

---

### Post by ExnuX on 2011-10-14
Don't get a black screen, just missing the drivers and catalyst center.
Will look into your solution tonight.

But to be honest, this feels a bit to complicated for something that should work "out of the box". I know you normally don't really need these proprietary drivers. But i'm going to use this machine as a htpc and i can use all the hardware acceleration i can get.

---

### Post by 4Orbs on 2011-10-14
Here is my (questionable?) insight into the current ATI driver situation with Oneiric. Maybe my hardware presents a unique set of circumstances, and maybe the Ubuntu developers would respond to this post with "4Orbs, you are full of baloney".

1. I get the best video playback by using the standard Radeon driver included in the stock X/K/L/Ubuntu install. But I also get poor 3D acceleration... so gaming is out of the question.

2. There is no need to manually install the 11.9 Catalyst driver because the 11.8 driver gotten from "Additional Drivers" works just as well and is much easier to install. However, if you plan on running Gnome Shell, then the 11.9 driver is mandatory.

3. Using the "Additional Drivers" method works best for me by selecting the regular "fglrx" option and NOT the "post release option". The installer doesn't give very good feedback while it's downloading and installing the driver, and you might think that it has hung or crashed. Just wait out the process. Sometimes it has taken more than 5 minutes for the driver to download (in my case) and the progress bar just sits there at 30% doing nothing.

4. Once the proprietary driver is installed, I've discovered that suddenly video playback is tearing (broken lines across the movie). So I open the catalyst control center and select the "Tear Free Desktop" option. Great... no more tearing, but now the videos play jerky and not smooth anymore. And there is an annoying delay when typing anything in the text editor or entering a password or typing a word in the search box. So I choose the lesser of two evils... and prefer having video tearing to jerky playback. So I turn-off the "Tear Free Desktop" (which is really just "sync to Vblank").

5. Playing commercial dvd's in the optical drive results in jerky playback regardless of any options I choose in the player or Catalyst Control Center. But, strangely, they play smoothly if I use the Parole player (only works with Xubuntu), or the gxine player. Maybe this means that the xine engine is superior?

6. Desktops environments. I've been a diehard Xubuntu user for more than three years, but this past week I have discovered that the very best media playback experience comes from using Kubuntu with the proprietary driver from "Additional Drivers" (NOT the post release option). Maybe this means that the xine engine is superior. Unity works pretty well also. Maybe this means that having desktop effects enabled somehow actually improves video playback. Illogical?

---

### Post by rmcnamara on 2011-10-14
I dont have the most ubuntu experience. But to me there appears to be something in 11.10 that is causing these problems. I have been on 11.04 for a couple of months and i did not have any issues installing the drivers at all. Hopefully this is something that is figured out in the near future. As of right now i think i am just going to stick with the driver that ubuntu installs at setup.

---

### Post by weelk on 2011-10-17
I'm joining this thread with the same problem. 
Also another thread on similar problem but related to dual monitor setup: [http://ubuntuforums.org/showthread.php?p=11356215](http://ubuntuforums.org/showthread.php?p=11356215)
Thought it might be related.

jockey.log

```
2011-10-17 11:52:09,673 WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver
2011-10-17 11:52:09,740 ERROR: xorg:fglrx_updates: get_alternative_by_name(fglrx-updates) returned nothing
```

Tried everything suggested - didn't work. For me it was working fine after upgrade to 11.10. I think it might be a  problem with compiz. Once I wanted to change some settings I've lost  unity immediately so was forced to terminal and unity --reset and  everything came back to normal. Each time I change anything in compiz  manager unity fails and have to reset it.


Setup:
Ubuntu 11.10
ATI HD4870X2
Asus II Maximus
Intel Core2Duo X9770 Extreme

---

### Post by flamarro on 2011-10-17
Hi guys,
for me it's annoying the sole movement of any window when i grab it, it tears, while i am moving it, it gives little jumps, like if i have a screen with a very low refresh rate. And if i use wobbly windows.... Jesus....
I did all of what you have done also, even have broken the system trying numerous things, and install it all over again.
I stick for now, with the proprietary drivers that indeed are working.
I have also installed in dual boot Pinguy OS 11.04, and, although i now it is not a perfect benchmark, i use glxgears to test it, because in Pinguy i get a so smooth movement of things, it is really great. When in Ubuntu 11.10, it's half the values i get in pinguy, and really jumpy. And in Pinguy all i did was install the proprietary drivers with "Addicional Drivers" too.

Sorry for my english! :)

PS:found this thread that is exactly what i was meaning
[http://ubuntuforums.org/showthread.php?t=1860437&highlight=ubuntu+tweak](http://ubuntuforums.org/showthread.php?t=1860437&highlight=ubuntu+tweak)

---

### Post by zerwas on 2011-10-26
Anyone having the same error as in the first posting of this thread, please subscribe to the [bug report]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/870560") on launchpad.

---

### Post by Lumsdoni on 2011-11-12
I had 11.10 installed with Gnome 3, but did not install the ATI Radeon drivers.

I then read (stupidly)  that the 11.10 ATI driver fixed the gnome 3 problem.  So I duly installed it.

Tada! The Menu bar was fine, no crazy colours, but the some weird tearing occured inpop up boxes.

I managed to get the Control Centre up to change the Tearing option, but no change.

I then followed the instructions below to remove ATI Radeon and revert to the open source drivers (please correct if wrong) From [here]("http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx")

$ sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
$ sudo apt-get install xserver-xorg-video-ati
$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
$ sudo rm -rf /etc/ati

Unity was fine but now even if I select Gnome3, it loads up Gnome Classic.

I then uninstalled Gnome3, and reinstalled it but no change, I can still only get Gnome Classic, despite the Gnome3 option being selected.

I would greatly appreciate any help in getting my Gnome3 access back, I really like it (each to their own) and as a linux newbie, have finally got my laptop dual booting with Win7 and a shared data drive, and shared dropbox folders all working superbly well, and I really cannot face yet another re-install of Ubuntu.

Please advise if you need any command outputs for help.

Laptop is an MSI-U230 single core 1.6ghz, 2MB ram. 1st partition Win7 (32bit), 2nd partition (extended) Ubuntu 11.10 (32bit) and Swap, 3rd partition FAT32 Shared Data drive.

Chip is AMD MV-40, Graphics Card is ATI Radeon 5200 HD.

Thank you

---

