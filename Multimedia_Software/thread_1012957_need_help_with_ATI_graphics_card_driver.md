---
title: "need help with ATI graphics card driver"
date: 2008-12-16
forum: Multimedia Software
---

### Post by foges on 2008-12-16
To sum it up, i cant get ubuntu 8.10 to run in anything  but low graphics mode. I have tried everything to get it to run properly, but it wont:

1) ATI drivers from website (says DKMS part of installation failed)
2) Envy 
3) System > admin > Hardwaare drivers > activate

They usually give the error, something along the lines of "Screen graphics and input device could not detect correctly, please configure these manualy"

My setup is:
ATI 3450 512MB 
Intel Q9450
4 GB corsairs XMS

Im on the verge of buying an nVidia graphics card (my server computer has some old cruddy 8MB graphics card and it runs perfectly, with all cool transition effects). On my computer i cant even move around the file browser without the audio output from Rhythmbox freezing.

Any ideas...

---

### Post by foges on 2008-12-17
ok, well what graphics cards work well with ubuntu? (cheap, but HD capable and monitor resolution of 1600x1200)

---

### Post by NewDisciple on 2008-12-17
What I did on my HD3850 was go into synaptic/settings/repositories/updates check mark on pre-released updates.  Close that box & then re-load synaptic.  After it is done hit mark all upgrades.  Then apply.  This will install a newer fglrx driver.  I don't know anything about your card so no promises, I'm just saying it worked for me.

---

### Post by foges on 2008-12-19
i tried it, thanks, but i still get the same startup error :s

---

### Post by markbuntu on 2008-12-19
You need to remove all those drivers that did not work. The driver for the ati site can be removed by going to the usr/share/ati and 

sudo sh ./fglrx-uninstall.sh

Remove the driver you got with envy by running envy again and selecting remove.

You can remove the driver you got with Hardware by using synaptic and using the search function for fglrx and remove completely all the fglrx packages. 

This will either give you a black screen when you reboot or dump you into the VESA drver. If you get a black scren reboot into recovery mode and reconfigure x to use the vesa driver and set the screen resolution for your display.

Once you do all that and get back into a desktop use System/Hardware again and just click enable for the restricted driver. Let it download and install itself, reboot and everything should work. If not, from a terminal

sudo aticonfig --initial -f

then reboot. Then you can use the Catalyst Control Center to adjust your settings.

The driver in Hardware (the repository) has been tweaked for Intrepid. The other drivers do not work and will screw it up. This is your problem.

---

### Post by jprovostla on 2008-12-20
My GPU is running too hot also... [over 100'C & sometimes causes the system to shut down]
from the terminal command "aticonfig --lsp [list powerstate] I found out that the default setting is 3 [high voltage - 324 mhz] and I would like to set it to 1 [low voltage - 135mhz]
But the command "aticonfig --set-powerstate=1" fails because there's no layout section [flgrx] in the xorg.conf file and the command "aticonfig --initial" fails to create the section due to a "bad file descriptor... 

Does anybody know the syntax of the fglrx primary device section in xorg.conf so I can add it in...

I really need to cool down th GPU...

Thanks

---

### Post by markbuntu on 2008-12-21
you need to run aticonfig as sudo

sudo aticonfig

---

### Post by foges on 2008-12-22
Hey markbuntu, i tried exactly what you said but i get the following error before the loginscreen:

(EE) fglrx(0): Unable to initialize PCS database
(EE) fglrx(0): Missing PCS defaults file /etc/ati/amdpcsdb.default
(EE) fglrx(0):  PreInit failed
(EE) Screen(s): found, but none have usable configurations


If i run aticonfig --initial -f i get:

Unable to open /etc/ati/control, please reinstall driver
Uinitialised file found, configuring
Segmentation fault 


Any idea? 
Thanks

---

### Post by Eddie Wilson on 2008-12-22
I believe that you may have some other problem besides the video drivers. Mark is pretty well right on how to install an ATI driver. I have the same graphics card (HD3450) and I had no problems with the install of the drivers. I wish I could help but I don't think there is anything I can add. You may be able to remove the drivers and then check out your xorg file to see if the other installs made any changes. Sorry I couldn't help.

---

### Post by Blue Beard on 2008-12-23
I got nowhere until I removed 2GB leaving 2GB in system.

Now I get the same image on both of my monitors.

---

### Post by foges on 2009-01-08
Ok, if anyone is interested, i solved this problem by removing all drivers and disabling the restricted drivers. Then downloading a fresh copy of the ati drivers from the website, now it works fine :)

---

### Post by ntbutler on 2009-01-30
Heya.

Foges, I hate to be a pain, but could you just give me a hint as to what to do to remove the old drivers? I thought I did this, but I am having problems, just getting the black screen on bootup.

Thanks

---

### Post by duststorm on 2009-08-15
I found the solution as to why you get the aticonfig Unable to open /etc/ati/control error.

It seems to happen when you had previously installed and then deinstalled the fglrx driver.
More specifically, when the files of the /etc/ati/ directory are removed, but the directory remains on the disk

The easy fix: 
- Uninstall the driver (either by typing sudo apt-get remove xorg-driver-fglrx or by using the uninstaller if you installed from the ati installer:  sh /usr/share/ati/fglrx-uninstall.sh)
- Remove the directory /etc/ati
> sudo rm -R /etc/ati
- Reinstall the driver any way you like, for example with 
> sudo apt-get install xorg-driver-fglrx


I haven't tested the above method but I believe it will work, I will also post how I fixed it.  This is guaranteed to fix the Unable to open /etc/ati/control error in aticonfig and make the driver work:

- Uninstall fglrx (as mentioned above)
- Download the installer from the ati website
- Use it to create a package for your distribution with the following command (note: you need to cd to the location where you downloaded the driver):
> sh ati-driver-installer*.run --buildpkg "Ubuntu/8.10"

Note that this is for 8.10 Intrepid.  You can change this with your ubuntu version number, eg
sh ati-driver-installer-9-3-x86.x86_64.run --buildpkg "Ubuntu/9.04"
for jaunty (sh ati-driver-installer-9-3-x86.x86_64.run --listpkg for all possible names)

- After it finished you can install the deb files
Do this with the console!!! (**IMPORTANT**)
enter:
> dpkg --install *fglrx*.deb
This is where I found out what was really the problem, because the installer works in interactive mode now.
You will get a message saying:
> Configuration file `/etc/ati/control'
 ==> Deleted (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** control (Y/I/N/O/D/Z) [default=N] 
And here is the solution to our problem.  It says you deleted the control file and asks to replace it, but get this, the DEFAULT OPTION is NO!!! (so it will, by default, not install the driver correctly)

Make sure to **enter Y** now **for every question** you get (you will get about 4 of these questions about files in the /etc/ati folder)
After you answered yes to all you  can run aticonfig

Run:
> sudo aticonfig --initial -f

Your're good to go now.  You can restart/start xserver again.
Now with working driver!!! :)



EDIT: You can also shorten the second method by just installing the driver from repository:
> - uninstall driver (see above)
sudo dpkg --install xorg-driver-fglrx
Do the YES answering thing
sudo aticonfig --initial -f
Restart X and you're done :)


I hope this will help some people since I noticed others had this problem too.  Maybe there is a better way to post this fix than replying here, I was maybe thinking of making a separate thread about it with the solution.  Maybe a mod can advise me here ;)

---

### Post by merry_meerkat on 2010-02-28
Just a quick note that I followed the instruction in the above post #13 ([http://ubuntuforums.org/showpost.php?p=7792744&postcount=13](http://ubuntuforums.org/showpost.php?p=7792744&postcount=13)) and it worked beautifully with the latest driver downloaded from the ATI website ([http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)).

I'm on a Dell Studio 1747 with Ubuntu Karmic 9.10 and an ATI Mobility Radeon HD 4650 graphics card.

The command for building the Karmic package was
```
sh ati-driver-installer-10-2-x86.x86_64.run --buildpkg Ubuntu/karmic
```

Thanks!

---

### Post by ting on 2010-03-18
Thanks, post number 13 worked for me. I used the repository version. Though I think i used purge xorg-etc instead of remove.

---

### Post by Missy375 on 2010-03-18
When I did this step. - 

After it finished you can install the deb files
Do this with the console!!! (**IMPORTANT**)
enter:
 	Quote:
 	 	 		 			 				dpkg --install *fglrx*.deb

I get this
melissa@melissa-desktop:~/Downloads$ sudo dpkg --install *fglrx*.deb 
(Reading database ... 155597 files and directories currently installed.)
Preparing to replace fglrx-amdcccle 2:8.702-0ubuntu1 (using fglrx-amdcccle_8.702-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx-amdcccle ...
Preparing to replace fglrx-kernel-source 2:8.702-0ubuntu1 (using fglrx-kernel-source_8.702-0ubuntu1_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement fglrx-kernel-source ...
Preparing to replace fglrx-modaliases 2:8.702-0ubuntu1 (using fglrx-modaliases_8.702-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx-modaliases ...
Preparing to replace xorg-driver-fglrx 2:8.660-0ubuntu4 (using xorg-driver-fglrx_8.702-0ubuntu1_i386.deb) ...
dpkg-divert: rename involves overwriting `/usr/lib/xorg/modules/extensions/libdri.so' with
  different file `/usr/lib/fglrx/libdri.so.xlibmesa', not allowed
dpkg: error processing xorg-driver-fglrx_8.702-0ubuntu1_i386.deb (--install):
 subprocess new pre-installation script returned error exit status 2
Preparing to replace xorg-driver-fglrx-dev 2:8.702-0ubuntu1 (using xorg-driver-fglrx-dev_8.702-0ubuntu1_i386.deb) ...
Unpacking replacement xorg-driver-fglrx-dev ...
Setting up fglrx-amdcccle (2:8.702-0ubuntu1) ...
Setting up fglrx-kernel-source (2:8.702-0ubuntu1) ...
Loading new fglrx-8.702 DKMS files...
Building initial module for 2.6.31-20-generic-pae, architecture -a i686
Done.

fglrx.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.31-20-generic-pae/updates/dkms/

depmod....

DKMS: install Completed.

Setting up fglrx-modaliases (2:8.702-0ubuntu1) ...
Setting up xorg-driver-fglrx-dev (2:8.702-0ubuntu1) ...
Processing triggers for desktop-file-utils ...
Errors were encountered while processing:
 xorg-driver-fglrx_8.702-0ubuntu1_i386.deb


What do I need to do now?

---

### Post by uwe.koch.k on 2010-03-19
I had the same problem shown on thread #16, but on a 64 bit installation. xorg-driver-fglrx falls back to 8.631 .

---

### Post by uwe.koch.k on 2010-03-22
> **Missy375 said:**
> When I did this step. - 

After it finished you can install the deb files
Do this with the console!!! (**IMPORTANT**)
enter:
 	Quote:
 	 	 		 			 				dpkg --install *fglrx*.deb

I get this
melissa@melissa-desktop:~/Downloads$ sudo dpkg --install *fglrx*.deb 
(Reading database ... 155597 files and directories currently installed.)
Preparing to replace fglrx-amdcccle 2:8.702-0ubuntu1 (using fglrx-amdcccle_8.702-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx-amdcccle ...
Preparing to replace fglrx-kernel-source 2:8.702-0ubuntu1 (using fglrx-kernel-source_8.702-0ubuntu1_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement fglrx-kernel-source ...
Preparing to replace fglrx-modaliases 2:8.702-0ubuntu1 (using fglrx-modaliases_8.702-0ubuntu1_i386.deb) ...
Unpacking replacement fglrx-modaliases ...
Preparing to replace xorg-driver-fglrx 2:8.660-0ubuntu4 (using xorg-driver-fglrx_8.702-0ubuntu1_i386.deb) ...
dpkg-divert: rename involves overwriting `/usr/lib/xorg/modules/extensions/libdri.so' with
  different file `/usr/lib/fglrx/libdri.so.xlibmesa', not allowed
dpkg: error processing xorg-driver-fglrx_8.702-0ubuntu1_i386.deb (--install):
 subprocess new pre-installation script returned error exit status 2
Preparing to replace xorg-driver-fglrx-dev 2:8.702-0ubuntu1 (using xorg-driver-fglrx-dev_8.702-0ubuntu1_i386.deb) ...
Unpacking replacement xorg-driver-fglrx-dev ...
Setting up fglrx-amdcccle (2:8.702-0ubuntu1) ...
Setting up fglrx-kernel-source (2:8.702-0ubuntu1) ...
Loading new fglrx-8.702 DKMS files...
Building initial module for 2.6.31-20-generic-pae, architecture -a i686
Done.

fglrx.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.31-20-generic-pae/updates/dkms/

depmod....

DKMS: install Completed.

Setting up fglrx-modaliases (2:8.702-0ubuntu1) ...
Setting up xorg-driver-fglrx-dev (2:8.702-0ubuntu1) ...
Processing triggers for desktop-file-utils ...
Errors were encountered while processing:
 xorg-driver-fglrx_8.702-0ubuntu1_i386.deb


What do I need to do now?

Please, read carefully the Ubuntu Jaunty/Karmic Installation Guide on [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide), especially that concerned with driver removal. It seems not being enough to do it via envy or synaptic, but search for any remaining related deb package. In the next thread I told that I had the same problem; after removing the related deb packages, I could succesfully install the 8.702 driver. But, I have not been able to enable compiz.

---

### Post by uwe.koch.k on 2010-04-12
> **uwe.koch.k said:**
> Please, read carefully the Ubuntu Jaunty/Karmic Installation Guide on [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide), especially that concerned with driver removal. It seems not being enough to do it via envy or synaptic, but search for any remaining related deb package. In the next thread I told that I had the same problem; after removing the related deb packages, I could succesfully install the 8.702 driver. But, I have not been able to enable compiz.

Also take yourself a moment and read: [http://distrowatch.com/table.php?distribution=ubuntu&language=EN](http://distrowatch.com/table.php?distribution=ubuntu&language=EN)

It tells you that the highest ati driver that should work on karmic is 8.660. In fact 8.702 works, but not compiz. 8.712 didn't do it on karmic on my machine.

---

### Post by sethtriggs on 2010-05-08
Thank you in #13 - this worked for me when I had this issue upgrading from 9.04 to 9.10 tonight. I am not going to try 10.04 since I have a Radeon HD3650 card.

-Seth

---

### Post by uwe.koch.k on 2010-05-08
> **sethtriggs said:**
> Thank you in #13 - this worked for me when I had this issue upgrading from 9.04 to 9.10 tonight. I am not going to try 10.04 since I have a Radeon HD3650 card.

-Seth

Strange, I've installed an ATI Radeon HD2600 PRO AGP on Lucid (64), which works flawlessly, even with compiz enabled!

---

### Post by sethtriggs on 2010-05-08
> **uwe.koch.k said:**
> Strange, I've installed an ATI Radeon HD2600 PRO AGP on Lucid (64), which works flawlessly, even with compiz enabled!
It's odd, but my Compiz is not working at all with that installation (and it's a dual monitor setup too). I ran the extraction of the new drivers and that helped me make things happen, finally.

I don't know if this is related to just the HD 3650 chipset or that I have dual monitors or what.

-Seth

---

### Post by Steve H on 2010-10-04
> **duststorm said:**
> I found the solution as to why you get the aticonfig Unable to open /etc/ati/control error.

It seems to happen when you had previously installed and then deinstalled the fglrx driver.
More specifically, when the files of the /etc/ati/ directory are removed, but the directory remains on the disk

The easy fix: 
- Uninstall the driver (either by typing sudo apt-get remove xorg-driver-fglrx or by using the uninstaller if you installed from the ati installer:  sh /usr/share/ati/fglrx-uninstall.sh)
- Remove the directory /etc/ati

- Reinstall the driver any way you like, for example with 



I haven't tested the above method but I believe it will work, I will also post how I fixed it.  This is guaranteed to fix the Unable to open /etc/ati/control error in aticonfig and make the driver work:

- Uninstall fglrx (as mentioned above)
- Download the installer from the ati website
- Use it to create a package for your distribution with the following command (note: you need to cd to the location where you downloaded the driver):


Note that this is for 8.10 Intrepid.  You can change this with your ubuntu version number, eg
sh ati-driver-installer-9-3-x86.x86_64.run --buildpkg "Ubuntu/9.04"
for jaunty (sh ati-driver-installer-9-3-x86.x86_64.run --listpkg for all possible names)

- After it finished you can install the deb files
Do this with the console!!! (**IMPORTANT**)
enter:

This is where I found out what was really the problem, because the installer works in interactive mode now.
You will get a message saying:

And here is the solution to our problem.  It says you deleted the control file and asks to replace it, but get this, the DEFAULT OPTION is NO!!! (so it will, by default, not install the driver correctly)

Make sure to **enter Y** now **for every question** you get (you will get about 4 of these questions about files in the /etc/ati folder)
After you answered yes to all you  can run aticonfig

Run:


Your're good to go now.  You can restart/start xserver again.
Now with working driver!!! :)



EDIT: You can also shorten the second method by just installing the driver from repository:



I hope this will help some people since I noticed others had this problem too.  Maybe there is a better way to post this fix than replying here, I was maybe thinking of making a separate thread about it with the solution.  Maybe a mod can advise me here ;)

FINALLY!! That has been driving me mad all night, thanks a million

---

