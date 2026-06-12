---
title: "HOWTO: EZ Point/Click Nvidia/ATI latest driver install- NO TERMINAL"
date: 2008-09-11
forum: Multimedia Software
---

### Post by rgb1701 on 2008-09-11
From threads here and similar posts I've seen around the net, it appears there is a lot of confusion regarding installing the latest Nvidia or ATI driver on any motherboard/Nvidia/ATI GPU combo, and in particular, getting on board Nvidia 7050 video working normally with 3D accelerations.

Too often, I see people doing or suggesting to others highly complicated procedures and manual methods in a terminal to install the latest Nvidia or ATI drivers, and getting the TF7050-M2 in particular up and running.

Also, simply clicking the "Restricted Driver" popup in Ubuntu/Mint to enable the Nvidia/ATI driver may not result in the use of the latest driver, or may not install the driver and/or configure the xorg.conf file properly on some GPUs like the Nvidia 7050. The latest Envy utility appears to alleviate these issues for both Nvidia and ATI GPUs, at least through the Nvidia 7xxx series and ATI 9xxx series. I haven't tried any higher than these.

Envy is the equivalent of a special purpose Windows "Add/Remove Programs" utility made just for Nvidia and ATI driver installation and removal in Ubuntu, Mint and Debian Linux's- a good enough reason alone to stick with these Linux flavours 

This procedure is point and click, no term window needed. It assumes a new install of Linux Mint 4.0/5.x Gnome, which are Ubuntu 7.10/8.04x derivative distros. This procedure should work in other flavors of Ubuntu (X,K,Edu,etc.

I have used this procedure on Nvidia GPUS like an FX5200, FX5500 on a P3V4X motherboard with various P3 cpus, no issues. I've also tested with the Nvidia 6200, 7100GS, 7300, 7050 and ATI 9550 and 9600, AGP and PCIe.

I've tested the analog VGA, DVI and HDMI video outputs on all my rigs, including the TF7050-M2, connected to a 22" Envision 1680x1050 LCD and Acer 24" 1920x1200 LCD. 

Download latest Linux Mint Main edition (Gnome)
[http://www.linuxmint.com/mirrors.php?id=15](http://www.linuxmint.com/mirrors.php?id=15)

or Ubuntu 
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Burn the ISO and reboot.

For the TF7050-M2:
Go into your BIOs (hit Delete at boot up) and be sure your on board video is enabled (duh!), the on board video is initialized first, and the GPU settings are set to Auto. I also disabled the HDMI audio output, but kept the HD Audio on board sound chip enabled, as I don't need HDMI audio output- I plan to use SPDIF and analog from the motherboard connectors.

Also, if you are using a SATA hard disk, be sure to set the SATA mode to AHCI or Linux AHCI vs the default IDE mode, or Mint/Ubuntu won't recognize your hard disk.

Other motherboards/video cards:
Set the slot for your video card (PCI, AGP, PCIe) to be initialized first in your BIOS. 

Set your boot order properly, too, booting from CD-ROM first

After you verify the BIOs settings, save them and reboot with the LiveCD.

At the Install/Start screen, start in "Safe graphics mode".
EDIT: May not be needed in Ubuntu 8.04x or Mint 5.x

The OS should boot to the desktop.

For Mint and Ubuntu, just double click the Install icon on the desktop.

Follow the install prompts. I chose "Guided, entire disk" for the partition/format step.

After the install completes (only about 7-8 minutes on an X2 4200 with a 2003 WD hard drive!), reboot.

It should reboot fine back to the login prompt. Login with name/password.

Answer the root account (I don't set up one) and term window "fortune" (Mint) preferences.

The desktop should appear, using a standard VESA driver due to the Safe mode we picked at the start. 

Immediately go to the "Start" menu -> Administration -> Synaptic Package Manager icon.

Synaptic is like Control Panel->Add/Remove Programs in Windows, but far more powerful.

Enter your password, the same one you use to login to the desktop.

Use the Search field to find "envyng"

Right click on envyNG and select "Mark for complete removal"

Click Apply at the top of the Synaptic window.

Click the Edit-> Reload Package Information menu pick, then the Reload icon in the Synaptic GUI for good measure. This updates the links to the repos to ensure you get the latest versions when you install/reinstall/upgrade.

Then search for EnvyNG again in Synaptic, and install. When you run EnvyNG for the first time after this procedure, the 173.xxx driver should be listed instead of the older 169.xxx driver, as of 8/17/08.

After it completes, File-> Quit Synaptic.

ALTERNATE METHOD:

After removing EnvyNG from Synaptic, download the *.deb installer from the author's website and open it/execute it.

*.deb installers are executable in Ubuntu/Mint/Debian, and are the equivalent of Win *.msi or *.exe installers, acting like familiar Windows app/driver installers

Authors website
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

After the *.deb installer finishes, quit the installer.

Run the newly installed EnvyNG from Daryna ->System Tools

Ignore/close the warning about an older version if applicable.

Let Envy install the dependency updates if applicable.

Select "Install the Nvidia/ATI Driver" radio button (depending on the GPU brand you have), then Apply.

A WHOLE lot of stuff goes on in the term window installer automagically for you. Sit back, watch, and loin sumthin' 

When it finishes, agree to let EnvyNG "configure Xorg for you".

Restart the PC per the EnvyNG dialog.

Voila. You should be back at the login prompt. Log back into your fancy schmancy new Compiz ("Aero") enabled Linux powerhouse .

As of 8/21/08, you should have Nvidia driver version 173.xxx installed. Verify with the System Tools -> Nvidia Settings app now installed in your Daryna (Start) menu.

As of 2/12/08, the ATI driver should be 8.1. Verify with the Catalyst Control Center in your app menus.

There ya go- no muss, no fuss, no term window command, no xorg.conf editing, no nuttin'- just plain ole' Windows-style dumbed down pointin'-an-clickin' 

Easier than ATI drivers on Windows and VIA/AMD chipsets in the past 5-7 years, for you long timers. Heck, this is easier than installing the full set of drivers & applets plus WinTV 2K software for a typical Hauppauge TV tuner card in Windows

---

### Post by spandanj on 2008-09-11
I have never tried EnvyNG or ATI drivers directly from ATI website....

I use restricted because it pops up automatically, and its part of "default" ubuntu respository. So, I feel safe with what Ubuntu offers me instead of going out of my way to get a different version.

If the Ubuntu restricted drivers are not uptodate to latest ATI drivers I find that sad. 

Plus, its hard for me to trust 3rd party apps like envyng, b/c I dont know when they are going to stop supporting/updating it. I wont be checking every 2 months that they haven't stopped working on it. With Ubuntu repository, I put some responsibility on their shoulders.

However, I am going to try EnvyNG this time, b/c I am tired of pathetic OpenGL support by restricted driver. The compiz/openGL conflict. Hopefully, latest ATI drivers dont have this problem.

---

### Post by peakshysteria on 2008-09-12
This looks all hunky dory. I've installed EnvyNG via synaptic. Latest version 1.1.1. It installs the driver without problems. And there are some small changes to my system apparently. But the driver is not in use. fglrxinfo still gives me MESA. I've started a [_[COLOR="Red"]thread[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=904253") about it a while back. But still no luck. I seem to be the only one not able to make this work even though it should be enough to clik next --> next --> etc... Any help would be appreciated.

---

### Post by markbuntu on 2008-09-12
Envyng does not install the latest drivers from ATI. It installs a later version than the repositories, but not the latest. Envyng also does not recognize many of the newer ati cards and so will not install the correct driver for them. The best method for installing the latest ATI driver is here, Method 2:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

If you are having problems with Envy not recognizing your card, or other issues, you should use the link above. Be sure to follow the directions very carefully, especially if you are using 64 bit Hardy.

---

### Post by lavinog on 2008-09-12
[QUOTE=spandanj]If the Ubuntu restricted drivers are not uptodate to latest ATI drivers I find that sad. [/QUOTE]
A new driver is released every month. There are no Ubuntu packages that get updated to the latest version. Besides there are too many stability issues with changing video drivers every month.

I tried Envy once. It worked, but it bothered me that I didn't know what steps it was taking to install the driver. (This was before DKMS was used)

The past 4 versions of the ATI driver have an automatic installer that works with ubuntu.
The current issue with the restricted drivers is sometimes the latest version has more bugs than the previous: Currently 8.8 is the latest. I am using 8.7 because 8.8 will occasionally crash my system when watching videos, and I also see a 25% performance hit (using glxgears). 8.6 outperformed all of the drivers, but was highly unstable. I have no stability issues with 8.7.

I think if you want to use the restricted drivers you should learn how to switch between versions to find the version that works for you.
It seems that a version that works well for a 32-bit user will not work well for the 64bit users. I am currently using 64bit with 4 gigs of memory (the amount of system memory seems to also determine which versions work well.)

---

### Post by peakshysteria on 2008-09-18
> **markbuntu said:**
> Envyng does not install the latest drivers from ATI. It installs a later version than the repositories, but not the latest. Envyng also does not recognize many of the newer ati cards and so will not install the correct driver for them. The best method for installing the latest ATI driver is here, Method 2:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

If you are having problems with Envy not recognizing your card, or other issues, you should use the link above. Be sure to follow the directions very carefully, especially if you are using 64 bit Hardy.

Thanks man. But I have tried the Ubuntu Hardy Installation Guide wiki more than once. I I must say it's not easy for us who haven't got expert experience with the terminal from before. I'm not afraid of the terminal. But I'm still not so comfortable that I make it through the ati install wiki page. They should split the wiki into one 32 bit and one 64 bit page. Right now it's not for me, that's for sure. I know It's my best bet for making my card work. But so far no luck. Even though I know there are several people with my card who have made it. Both with Envy and the wiki recipe. As you guys can see my card ain't exceptionally new.

I think Envy installs the 8.6 driver for the time being. Latest version from AMD is 8.9. Released yesterday.

**lavinog** have you installed the latest drivers only by using the installer? Because that haven't worked for me in the past. The latest one I tried was 8.8. Which like all the others sent me into a low graphics loop hell. So now I have the driver installed (via Envyng) but now running :) Back in MESA hell.

---

