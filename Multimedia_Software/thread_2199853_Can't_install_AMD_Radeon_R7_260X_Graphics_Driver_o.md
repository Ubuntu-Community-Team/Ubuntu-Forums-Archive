---
title: "Can't install AMD Radeon R7 260X Graphics Driver on 13.10"
date: 2014-01-16
forum: Multimedia Software
---

### Post by jweiner on 2014-01-16
I recently bought Radeon R7 260X graphics driver and have tried to install the driver on my desktop PC running 13.10.  It appears that the opensource drivers available do not include this model.  I went to the AMD website and downloaded their proprietary driver that they claim works with linux-x86.x86_64.

The zipped file to download is amd-catalyst-13.12-linux-_64.zip.  I unzipped it and followed the installation procedure indicated at [wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Removing_Catalyst.2Ffglrx]("http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Removing_Catalyst.2Ffglrx").  When I tired to create and install the .deb packages, however, I got an error saying that the deb package build had failed.  Now I don't know what to do.  Is there an alternative method of installation?  Are there alternative drivers that will give good 2D acceleration even if not providing all the 3D features?

Any advice about getting this graphics driver working would be greatly appreciated.

---

### Post by slooksterpsv on 2014-01-16
After you extract you should just have to run the .sh or .run file that was included in the archive. You may need to set it to executable. You don't have to make DEBs or that.

---

### Post by jweiner on 2014-01-16
I am just following the step-by-step indicated in the web link.  I did run the .run file.  After that, according to the step-by-step, one is supposed to issue the follwoing two commands.  The first executes without error.  

sudo ./amd-catalyst-13.11-beta\ V9.4-linux-x86.x86_64.run --buildpkg Ubuntu/saucy
sudo dpkg -i fglrx*.deb

The second command produces the error, 
Error! Bad return status for module build on kernel: 3.11.0-15-generic (x86_64)
Consult /var/lib/dkms/fglrx/13.251/build/make.log for more information.

The log indicates the following:
/var/lib/dkms/fglrx/13.251/build/2.6.x/kcl_acpi.c:999:5: error: too few arguments to function &#8216;(acpi_status (*)(u32,  void *, void *))handler&#8217;

---

### Post by chkneater on 2014-01-16
Find that make.log and poste it.  Also try updating before running those commands.

---

### Post by jweiner on 2014-01-16
Here is a copy and paste of the relevant parts of the log file:

/var/lib/dkms/fglrx/13.251/build/2.6.x/kcl_acpi.c:999:5: warning: passing argument 1 of &#8216;(acpi_status (*)(u32,  void *, void *))handler&#8217; makes integer from pointer without a cast [enabled by default]
     ((acpi_table_handler)handler)(hdr);
     ^
/var/lib/dkms/fglrx/13.251/build/2.6.x/kcl_acpi.c:999:5: note: expected &#8216;u32&#8217; but argument is of type &#8216;struct acpi_table_header *&#8217;
/var/lib/dkms/fglrx/13.251/build/2.6.x/kcl_acpi.c:999:5: error: too few arguments to function &#8216;(acpi_status (*)(u32,  void *, void *))handler&#8217;
make[2]: *** [/var/lib/dkms/fglrx/13.251/build/2.6.x/kcl_acpi.o] Error 1
make[1]: *** [_module_/var/lib/dkms/fglrx/13.251/build/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-15-generic'
make: *** [kmod_build] Error 2
build failed with return value 2

The system is updated and all the relevant tools and packages had been added previous to this attempt.

---

### Post by chkneater on 2014-01-16
Before going through all that much, let's try 'sudo amdconfig --initial -f' .  This should generate a good x.org file for you using the radeon driver.  After running that command you need to reboot.  After you reboot, open a terminal and paste this in there ' fglrxinfo '.  If you see ATI and Radeon anywhere in the following text, you shuld be good to go.


On that link follow these parts, they're out of order but they should work:

Removing Catalyst/fglrx

The uninstall script in the first command will only exist if you downloaded the drivers and installed them directly (rather than building packages as this guide does). Skip the first command if it does not exist.

'sudo sh /usr/share/ati/fglrx-uninstall.sh'
'sudo apt-get remove --purge fglrx*'

You want to purge any fglrx config files completely.  Do both commands just to be safe, I don't know what all has been done to this point.  Continue with these:

'sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon'
'sudo apt-get install xserver-xorg-video-ati'
'sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core'
'sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup'
'sudo rm -rf /etc/ati'

---

### Post by jweiner on 2014-01-16
Thanks for that very detailed reply.  I just have one question:  At present I am using a graphics driver that is included on the motherboard. It works more-or-less ok but is limited in what it can do.   In my previous attempts to install the Radeon driver, I have shutdown the system, plugged in the power to the Radeon card and attempted to boot the system.  The system never booted up but got stuck somewhere (in grub I suppose).  Therefore I never could get to a text login, let alone a GUI.  A reinstall of 13.10 from the live CD produced a very unstable system, and I was forced to do a clean install by erasing everything that I had done up to that point.  I would like to avoid that happening again so my question is...what precautions cautions can I take to save myself if that happens again?

This is especially pertinent because when I try to execute the amdconfig command, I get a message that no adapters are detected, which is of course true because I have the card physcially installed in the PCI slot but it is not powered.

---

### Post by chkneater on 2014-01-16
When you first boot your comp. the very first screen, called the splash screen will give you a few seconds to acces the BIOS.  You usually have to hit F6 or del or Esc, every comp is different, but anyway, once you figure out how to get to the BIOS you need to find the menu with the chipsets (this is all text based, no mice, just arrows and tab and space bar), eventually you'll see Onboard Vidio, scroll to it and turn it off, save changes and reboot.  Make sure you make no other changes.  If you mess up you can quit without saving and try again.

Get rid of the onboard video, purge the fglrx config files and 'sudo amdconfig --initial -f' should clear this up if not help clear up osme of the surrounding issues.

---

### Post by jweiner on 2014-01-16
Thanks for the Onboard Video tip.  Now I should be able to reboot without trembling.  I let you know how things turn out.

---

### Post by jweiner on 2014-01-16
OK I am at the "Chipsets" category in the BIOS (I'm logged in here on a different computer).  There are a few main categories: IOH Configuration, Compatibility RID, Memory Configuration, 
DIMM Configuration.  Of these the IOH Configuration looks like the most promising.  Inside it one finds: Intel(R) VT for directed I/O Configuration, VGA Priority [offboard]; Gen3 Equalization WA's [disabled]; MMCFG Base [0x80000000]; IOH O PCIe port Bifurcation Conrol, PCIe Slot1 speed [Gen3], PCIe Slot2 [Gen3]

Inside the Intel(R) VT for directed I/O Configuration one finds: Intel(R) VT-d [enabled] and ATS support [Disabled]

I'm not sure how any of this can be used to turn off the onboard video.
Should I invert the switches to Intel(R) VT-d [disabled] and ATS support [enabled]?

OK I get it...it should be the VGA Priority which is already "offboard".

So I let the boot proceed and it immediately takes me to the GNU Grub menu.  There I have a choice of editing "Ubuntu" or "Advanced Options for Ubuntu".  I am fully open to suggestions as to what to do now.

---

### Post by slooksterpsv on 2014-01-16
> **jweiner said:**
> I am just following the step-by-step indicated in the web link.  I did run the .run file.  After that, according to the step-by-step, one is supposed to issue the follwoing two commands.  The first executes without error.  

sudo ./amd-catalyst-13.11-beta\ V9.4-linux-x86.x86_64.run --buildpkg Ubuntu/saucy
sudo dpkg -i fglrx*.deb

The second command produces the error, 
Error! Bad return status for module build on kernel: 3.11.0-15-generic (x86_64)
Consult /var/lib/dkms/fglrx/13.251/build/make.log for more information.

The log indicates the following:
/var/lib/dkms/fglrx/13.251/build/2.6.x/kcl_acpi.c:999:5: error: too few arguments to function ‘(acpi_status (*)(u32,  void *, void *))handler’

Well if the run file ran just fine there's no reason you need to build DEB files unless you're going to redistribute them. Usually, at least when I've used the files from AMD (even the most recent ones), the driver installs just by running the run file. The only time I need to pass other arguments is if it failed to install and I need to recompile the package with distro-specific files (newer kernel, beta version of Ubuntu, etc.).

---

### Post by squakie on 2014-01-16
> **jweiner said:**
> I recently bought Radeon R7 260X graphics driver and have tried to install the driver on my desktop PC running 13.10.  It appears that the opensource drivers available do not include this model.  I went to the AMD website and downloaded their proprietary driver that they claim works with linux-x86.x86_64.

The zipped file to download is amd-catalyst-13.12-linux-_64.zip.  I unzipped it and followed the installation procedure indicated at [wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Removing_Catalyst.2Ffglrx]("http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Removing_Catalyst.2Ffglrx").  When I tired to create and install the .deb packages, however, I got an error saying that the deb package build had failed.  Now I don't know what to do.  Is there an alternative method of installation?  Are there alternative drivers that will give good 2D acceleration even if not providing all the 3D features?

Any advice about getting this graphics driver working would be greatly appreciated.
So does this mean you've tried fglrx and it didn't work, then removed that and tried fglrx updates?  I don't have your particular model, but I had to go with fglrx-updates to get my AMD Radoen based card to work correctly.

Just askin' - don't know.

---

### Post by jweiner on 2014-01-16
The build for the .deb files fails (cf earlier posts to this thread), and since that is true and since I am only following a seemingly authoritative source (cf earlier copies-and-paste), I don't really know what I am doing, I don't know what to do now.  Earlier attempts to reboot with the Radeon graphics adapter powered up have resulted in black or purple screens and the boot being stuck somewhere....impossible even to get to a console login.  Right now I have purged all flgrx stuff that was installed via the run command on the downloaded package.  I have rebooted with the on-board video turned off, and the Radeon card powered up.  The boot process lead to the GRUB 2 menu.  I suppose I need to fix something or edit something in GRUB 2, but I do not know what...so at the moment I am at the GRUB 2 menu awaiting further advice.

---

### Post by squakie on 2014-01-16
there are all ready to install packages for those drivers.  If you boot, can you ctrl-alt-F1 and get a terminal (text mode) login screen?  If so, sign in with your normal userid and password (the password won't be echoed so nothing looks like it is going in but it is).  After that, try the following:

sudo apt-get purge flgrx
sudo apt-get pur flgrx-updates

don't worry if these return some message about no package found or some such thing.

then:

sudo apt-get update
sudo  apt-get upgrade
sudo apt-get install flgrx

then reboot.  If the error persists, log in again via a terminal and do the following:

sudo apt-get purge fglrx
sudo apt-get install fglrx-uipdates

reboot and see if the problem is fixed.  If not, stop at the grub screen, move (via arrow keys) to your normal ubuntu boot option but DON'T boot it.  Instead, press the "E" key to edit the options.  Arrow down to the line where you see "quiet splash" .  Arrow over to just past "splash" and add a space, then the text "nomodeset" (without the quotes).  Then press ctrl-x to boot using those options and see how that works.

post back any and all results and questions.  Can't guarantee any of it will help, but it's worth a shot!

---

### Post by squakie on 2014-01-16
BTW - I'm going to be out for a while, but there are far more qualified people than me that can help you anyway.  Just trying some of the things I had to do to get my card working.

---

### Post by slooksterpsv on 2014-01-16
> **jweiner said:**
> The build for the .deb files fails (cf earlier posts to this thread), and since that is true and since I am only following a seemingly authoritative source (cf earlier copies-and-paste), I don't really know what I am doing, I don't know what to do now.  Earlier attempts to reboot with the Radeon graphics adapter powered up have resulted in black or purple screens and the boot being stuck somewhere....impossible even to get to a console login.  Right now I have purged all flgrx stuff that was installed via the run command on the downloaded package.  I have rebooted with the on-board video turned off, and the Radeon card powered up.  The boot process lead to the GRUB 2 menu.  I suppose I need to fix something or edit something in GRUB 2, but I do not know what...so at the moment I am at the GRUB 2 menu awaiting further advice.

Try adding nomodeset to the end after where it says quiet for the Grub boot item.

---

### Post by jweiner on 2014-01-16
OK I will try nomodset and see what happens.

OK I edited the line to substitute nomodeset for splash. The system booted to the GUI...BUT the fglrx213.251-Obuntu1 is a bug report that came up on my web browser.  "fglrx kernel module failed to build".  The mouse seems to be behaving somewhat erratically although I don't know if that is related.

---

### Post by slooksterpsv on 2014-01-16
You can check the log file (or use pastebin and post the link) and we can see why it failed to build. Sometimes its just a random dependency we need to download.

---

### Post by squakie on 2014-01-16
Did you try what I recommended?  nomodeset was one of the last things there, but I also mentioned trying the 2 drivers for AMD/ATI cards.  Only as a last resort should you need to download driver source from AMD and build it.  The packages will do this all for you.  Try them.  If you have errors then, post back what those error messages are.

---

### Post by jweiner on 2014-01-17
Here is a copy-and-&#8217;paste of some text in the bug report..."DuplicateSignature: dkms:fglrx:2:13.251-0ubuntu1:/var/lib/dkms/fglrx/13.251/build/2.6.x/kcl_acpi.c:999:5: error: too few arguments to function &#8216;(acpi_status (*)(u32, void *, void *))handler.

Link to the bug report is here, [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1263471](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1263471)

---

### Post by squakie on 2014-01-17
Does this happen when you (1) purge as I suggested (2) install fglrx via apt-get?

If so, what happens when you (1) purge fglrx as I suggest and (2) install fglrx-updates via apt-get?

Both os these will attempt to install the driver and also install Catalyst.  It would be nice to know if the problem is related only to fglrx, or if it also applies to fglrx-updates.

Please, let us know if you have tried these and then what any error messages were.

---

### Post by Bucky Ball on 2014-01-17
*Thread moved to **Multimedia & Video**.*

---

### Post by squakie on 2014-01-17
Also, someone here can probably tell you how (I don't know) to download a slightly older version - I running 2:13.101-0ubuntu3 of fglrx-updates and was able to remove and reinstall it just now just fine.

---

### Post by slooksterpsv on 2014-01-17
[http://support.amd.com/en-us/download/embedded?os=Linux+x86&rev=13.151](http://support.amd.com/en-us/download/embedded?os=Linux+x86&rev=13.151)

There's 13.151

---

### Post by jweiner on 2014-01-17
I have tried pretty much everything that has been suggested.  I purged all the fglrx and then after downloading and unpacking the zip files from the AMD site I tried

sudo apt-get install fglrx*

The result was...here is copy-and-paste of the messages from apt-get

john@samba:~$ sudo apt-get install fglrx*
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'fglrx-driver-dev' for regex 'fglrx*'
Note, selecting 'fglrx-pxpress' for regex 'fglrx*'
Note, selecting 'fglrx-updates' for regex 'fglrx*'
Note, selecting 'fglrx-dev' for regex 'fglrx*'
Note, selecting 'fglrx-control' for regex 'fglrx*'
Note, selecting 'fglrx-amdcccle-updates' for regex 'fglrx*'
Note, selecting 'xfree86-driver-fglrx-dev' for regex 'fglrx*'
Note, selecting 'xorg-driver-fglrx-dev' for regex 'fglrx*'
Note, selecting 'fglrx-glx' for regex 'fglrx*'
Note, selecting 'fglrx-control-qt2' for regex 'fglrx*'
Note, selecting 'fglrx-amdcccle' for regex 'fglrx*'
Note, selecting 'fglrx-driver' for regex 'fglrx*'
Note, selecting 'fglrx-updates-dev' for regex 'fglrx*'
Note, selecting 'fglrx' for regex 'fglrx*'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 fglrx : Conflicts: fglrx-driver
         Conflicts: xorg-driver-binary
 fglrx-amdcccle : Conflicts: fglrx-control
 fglrx-amdcccle-updates : Conflicts: fglrx-control
 fglrx-dev : Conflicts: fglrx-driver-dev
 fglrx-updates : Conflicts: fglrx-driver
                 Conflicts: xorg-driver-binary
 fglrx-updates-dev : Conflicts: fglrx-driver-dev
E: Unable to correct problems, you have held broken packages.

So now I don't know what to do and would really appreciate some more help.

---

### Post by slooksterpsv on 2014-01-17
After you extract the zip file are you running:

```

sudo ./extracted_AMD_file.run

```

Where extracted_AMD_file.run is the file it extracted?

---

### Post by jweiner on 2014-01-17
Yes I did, but I forgot to "sudo" and so the script hung.  I will be back after I do it correctly.

---

### Post by jweiner on 2014-01-17
Running the installer with "sudo" results in a message saying that there is another fglrx installed.   The log file says

Supported adapter detected.


[Error]A previous installation of fglrx driver detected to be installed in dkms.
User must uninstall existing fglrx driver 
or run install with force option.
Forcing the installation is not recommended.
Output of 'dkms status -m fglrx'
    fglrx, 13.101, 3.11.0-15-generic, x86_64: installed

---

### Post by slooksterpsv on 2014-01-17
There's a directory some where, it may be /usr/lib/fglrx that has a command to remove fgrlx, I'd have to research it, but it'll go through and manually rip everything out.

---

### Post by jweiner on 2014-01-17
I was able to get rid of the earlier fglrx files with sudo apt-get purge fglrx.  The proprietary installation proceeded but failed.  Here is the output from the install log

Supported adapter detected.
Check if system has the tools required for installation.
Uninstalling any previously installed drivers.


Creating symlink /var/lib/dkms/fglrx/13.251/source ->
                 /usr/src/fglrx-13.251


DKMS: add completed.


Kernel preparation unnecessary for this kernel.  Skipping...


Building module:
cleaning build area....
cd /var/lib/dkms/fglrx/13.251/build; sh make.sh --nohints --uname_r=3.11.0-15-generic --norootcheck....(bad exit status: 1)
[Error] Kernel Module : Failed to build fglrx-13.251 with DKM


Deleting module version: 13.251
completely from the DKMS tree.

---

### Post by jweiner on 2014-01-17
I was finally able to download, extract a package from the AMD site that seems to be a version of the catalyst software that actually works with 13.10.


**Installing Catalyst Manually (from AMD/ATI's site) *BETA/EXPERIMENTAL***

**[[edit]("http://wiki.cchtml.com/index.php?title=Ubuntu_Saucy_Installation_Guide&action=edit&section=9")]Download the latest Catalyst package**

[COLOR=#000000][FONT=sans-serif]This package contains both the 32-bit and 64-bit driver.[/FONT][/COLOR]
mkdir catalyst-13.11beta9.4 && cd catalyst-13.11beta9.4
wget --referer='http://support.amd.com/en-us/download/desktop?os=Linux+x86' [http://www2.ati.com/drivers/beta/amd-catalyst-13.11-beta-v9.4-linux-x86.x86_64.run.zip](http://www2.ati.com/drivers/beta/amd-catalyst-13.11-beta-v9.4-linux-x86.x86_64.run.zip)
unzip amd-catalyst-13.11-beta-v9.4-linux-x86.x86_64.run.zip
chmod +x amd-catalyst-13.11-beta\ V9.4-linux-x86.x86_64.run
**[[edit]("http://wiki.cchtml.com/index.php?title=Ubuntu_Saucy_Installation_Guide&action=edit&section=10")]Create and install .deb packages**

sudo ./amd-catalyst-13.11-beta\ V9.4-linux-x86.x86_64.run --buildpkg Ubuntu/saucy
sudo dpkg -i fglrx*.deb

When I carry out these instructions, and then type

fglrxinfo

I see

display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon R7 200 Series  
OpenGL version string: 4.3.12614 Compatibility Profile Context 13.25.18

So apparently the fglrx software recognizes the hardware adapter board.
 
 I don't know if I am actually using the driver because if I click on "about this computer" from the pull-down menu in the upper right corner of the GUI, I see in the Graphics rubric,

VESA: BONAIRE 

which is not what I would have expected.

The command

fgl_glxgears

also works...it opens a window where one sees the habitual glxgears rotating rapidly around in a 3D box that is rotating along many different axes.

So the point is that the "normal" fglrx that is installed from the open repositories does not work in 13.10...it crashes the the system with a segmentation fault error.  The bug has been reported many times now.
The latest "stable" version of the proprietary drivers from the AMD web site does not work either.
The experimental "beta" version, however, seems to do the job.  At least fglrxinfo gives the right answer without crashing.

I still don't know whether or not my video screen is being driven by a VESA software or the fglrx.  I have the impression that despite all this happy news, I still have not reached home base.

Last problem...on reboot the "flash" entry on the linux line of Grub leads to a purple screen and no system boot.  This line has to be edited to replace "flash" with "nomodeset".  Then, and only then, does the boot proceed to completion.

Every time I reboot I have to edit this line...there must be a simpler, better was of updating Grub permanently.  Is "nomodeset" the new normal for the boot loader?

But I suppose that is the subject of another post.

---

### Post by squakie on 2014-01-17
Assuming you mean making nomodeset permanent, it's pretty easy process.  rather than rehash it, I'll just post a link to the one of hundreds of posts on how to do:

[http://ubuntuforums.org/showthread.php?t=1675337](http://ubuntuforums.org/showthread.php?t=1675337)

---

### Post by jweiner on 2014-01-17
Thanks for the link...I found how to edit the grub file and now my system boots up without human intervention.  The driver is being recognized but I am not sure it is really being used.  Anyway, I understand things a little now than I did a week ago.  Let us hope that next week will bring even greater understanding.

Did I ever mention that I think your cat does look quite attractive with the Christmas reindeer antlers?

---

### Post by squakie on 2014-01-17
You know what's really funny?  He didn't mind those a bit - just sat around and walked around like nothing was different.  I had a matching red cloth collar with bells on it, but when I put it on him he was scared of the bells so he started running.  Needless to say, the more he ran the more the bells ran, the more scared he got, the more he ran.....  Well, it took me 10 minutes to catch him because he kept just going nuts - running into walls, etc..  Once I got the collar off of him he settled back down.  I'd say it was funny, but the poor little guy was REALLY scared!   Oh well.....

Glad to hear you have gotten your problem solved. ;)

---

