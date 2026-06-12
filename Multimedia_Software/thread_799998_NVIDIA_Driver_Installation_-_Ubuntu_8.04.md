---
title: "NVIDIA Driver Installation - Ubuntu 8.04"
date: 2008-05-19
forum: Multimedia Software
---

### Post by churfsan on 2008-05-19
Hello All,

I have just installed Ubuntu 8.04 on my home PC. The motherboard is MSI RS480IL-M2 (AMD64). The graphics card is XFX 8600GT PCI Express card. The Ubuntu 8.04 is the 32-bit desktop version (installed from the live CD).

I tried activating the NVIDIA driver from System->Administration->Hardware Drivers.

After restart, Ubuntu starts up and shows the progress bar. Just before reaching the login screen, the display switches off (as if there is no video signal), I do not get the login screen. 

I tried using ENVY drivers. The resulting behavior is exactly the same as above. I even tried downloading the binary driver directly from nvidia website "NVIDIA-Linux-x86-169.12-pkg1.run", but again the result is the same.

Please help me as this is becoming a stumbling block to embrace Ubuntu full-fledged. 

I earlier had Suse Linux 10.3. I was able to get the nvidia driver working without any problems, using the 1-click install.

Thanks for any help

---

### Post by kjbuente on 2008-05-19
I'm curently experiencing the same problem with my 9600GT and the 172 beta drivers. Exept I get to the nvidia splash screen and it goes all "matrixy" on me. (sparkles that are falling top to bottom). I've tried backing up the xorg.conf file and delete the orginal  making X rebuilt it, then I added the nvidia driver. This only get me to low resolution mode.

Would you mind doing a test to see if I am having the exact same issue as you? If you can't, then just ignore this... Try booting using the open source "nv" drivers. (Replace nvidia with nv in the /etc/X11/xorg.conf file) Then once the GUI is loaded replace the nv with the nvidia driver, save and restart X by ctrl+alt+backspace. (Not rebooting). I can use the nvidia drivers that way, but I can't boot with it in there. If that works for you, then I know that I'm not the only one. (I'm starting to loose my hair again because of this)!

---

### Post by zooLiz on 2008-05-19
I have a more weird problem. When I try download from nvidia and click the link it follows with a list of code. Instead of downloading the file I get to see all the code! 

I would realy apprecieate some help on this problem.

---

### Post by chyrania on 2008-05-19
> **zooLiz said:**
> I have a more weird problem. When I try download from nvidia and click the link it follows with a list of code. Instead of downloading the file I get to see all the code! 

I would realy apprecieate some help on this problem.

If you're seeing text while you download a file, you might want to try right-clicking on the download link and select 'save as'.

---

### Post by churfsan on 2008-05-20
> **kjbuente said:**
> I'm curently experiencing the same problem with my 9600GT and the 172 beta drivers. Exept I get to the nvidia splash screen and it goes all "matrixy" on me. (sparkles that are falling top to bottom). I've tried backing up the xorg.conf file and delete the orginal  making X rebuilt it, then I added the nvidia driver. This only get me to low resolution mode.

Would you mind doing a test to see if I am having the exact same issue as you? If you can't, then just ignore this... Try booting using the open source "nv" drivers. (Replace nvidia with nv in the /etc/X11/xorg.conf file) Then once the GUI is loaded replace the nv with the nvidia driver, save and restart X by ctrl+alt+backspace. (Not rebooting). I can use the nvidia drivers that way, but I can't boot with it in there. If that works for you, then I know that I'm not the only one. (I'm starting to loose my hair again because of this)!

I tried as suggested, but the problem remains. I cannot get back into the GUI.

I hope that someone will help solve this problem.

---

### Post by Jvaldezjr on 2008-05-20
I had this problem in Feisty, and I had to downgrade my drivers in feisty to  the 96.43 drivers in order for the monitor to stop cutting off.  Now I'm using hardy64, and i have this problem also.  I haven't figured out which version won't cut off on me, so far I've used 169, 171, and the 173 versions with no luck.

---

### Post by lordjoe_com on 2008-05-20
I have a dual boot system with a NVidia 5500 and a 6300 - three screens -
They work find until I reboot - then the system drops into low res graphics and I have  to shut down X and reinstall the beta drivers. This is getting VERY annoying - anyone have any idea what is happening???:confused:

---

### Post by churfsan on 2008-05-23
Hello all,

I am really struck on this, can some one help me out please?! I was using Suse 10.3 earlier, and I never faced any problem with NVIDIA drivers (same card and setup). I am sure that there must be a solution on Ubuntu, just some mistake somewhere. 

Maybe more experienced and knowledgeable Ubuntu users can help me out please! I may have to fall back on Suse 10.3 if no solution comes up, which I do not wish

Thanks in advance

---

### Post by krylon on 2008-05-23
> **lordjoe_com said:**
> I have a dual boot system with a NVidia 5500 and a 6300 - three screens -
They work find until I reboot - then the system drops into low res graphics and I have  to shut down X and reinstall the beta drivers. This is getting VERY annoying - anyone have any idea what is happening???:confused:


If you installed NVIDIA drivers using the downloaded binaries, try uninstalling the restricted driver manager.  Sometimes it will conflict and force you to reinstall the binaries after every reboot.

---

### Post by kjbuente on 2008-05-23
I finally got mine to work perfectly!

I noticed was the the nvidia module is not being loaded into the kernel. I had to manualy edit /etc/modules and add nvidia to the list and I had to blacklist the nv.

Just something to look out for and making sure that those changes are getting made...

Running a 9800gt with the 173.08 driver.

---

### Post by fsckedagain on 2008-05-23
Try this to solve your NVidia woes. :)

[http://ubuntuforums.org/showthread.php?t=805119](http://ubuntuforums.org/showthread.php?t=805119)

---

### Post by duncane on 2008-05-24
I have exactly the same issue as the parent post. I also have a AMD64 motherboard, but have an 8800 GT.

Enableing the restriced drivers, either via Hardware drivers, EnvyNg, or manually from the Nvidia site, all result in a black screen on reboot.

Everything looks fine in the x.org log but it just ends like this?:

(II) Setting vga for screen 0.
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.

Then nothing... just a black screen. I reboot in recovery and set the xorg.conf back to default and it boots fine.

---

### Post by churfsan on 2008-05-24
> **churfsan said:**
> Hello all,

I am really struck on this, can some one help me out please?! I was using Suse 10.3 earlier, and I never faced any problem with NVIDIA drivers (same card and setup). I am sure that there must be a solution on Ubuntu, just some mistake somewhere. 

Maybe more experienced and knowledgeable Ubuntu users can help me out please! I may have to fall back on Suse 10.3 if no solution comes up, which I do not wish

Thanks in advance

I did some more experiments. As suggested in one of the forum posts, I downloaded the 173.08 driver from NVIDIA and tried installing on a fresh copy of Ubuntu 8.04. 

This time around, the screen goes blank but I am able hear the 'welcome' audio note ( I am on auto login). There is no display, but after about 2-3 min, I get a text cursor blinking on the top of the screen, but the computer does not respond thereafter. I cannot get text login also (CTRL+ALT+F2 does not work)

Any suggestions would be very helpful

Thanks

---

### Post by duncane on 2008-05-24
churfsan,

I have the exact same problem as you.

Do you have a double head/monitor GFX card?

Have you tried plugging you monitor into the other ports on your card?

I fear we may have to wait for the next nvidia drivers.

Cheers 
Duncan

---

### Post by churfsan on 2008-05-24
> **duncane said:**
> churfsan,

I have the exact same problem as you.

Do you have a double head/monitor GFX card?

Have you tried plugging you monitor into the other ports on your card?

I fear we may have to wait for the next nvidia drivers.

Cheers 
Duncan

Ducan,

Yes, I have a dual-head card, I tried on both heads but it does not help. Could it be related to the monitor - resolution, frequency etc. Will using a DVI cable help, instead of VGA cable (Too simple !!).

I am facing this problem since Ubuntu 7.10!! Funny how things are so different from one distribution to another or even one release to another, even though all are LINUX distributions, with the same basic kernel. As I posted earlier, I did not face problem with Suse 10.3 on this NVIDIA aspect.

I like to use Ubuntu for its simplicity and support, but as you say, we may be out of luck for some more time, unless some of our more learned and experienced Ubuntu users help us out

Churfsan

---

### Post by duncane on 2008-05-24
churfsan,

Thats very interesting... I am also using a VGA cable on a DVI connector on the gfx... I cant think why that would make a difference, but Ive been meaning to get a new DVI cable so I will do that on monday and see how it goes.

Thanks
Duncan

---

### Post by spyckotic on 2008-05-24
I have been dealing with this problem for at least 6 months, possibly longer.  I've been through the last 3 "latest" nvidia drivers, spent countless hours trying to get this working.  If you dig hard enough you can probably find the threads around here. Open Suse was my only choice to have hardware acceleration, and I tried a handful of distro's all resulting in the same problem with the monitor going into stand by and the computer being unresponsive to any keyboard input.  The only thing to do is manually reset the machine and change the drivers back to nv.  These posts concerning this problem pop up from time to time and there is always a ton of suggestions, although nice and very much appreciated they never seem to work.  I was actually just coming back to check up on this situation when I found this thread.  Doesn't seem like much has changed yet.  I do hope this is resolved some day... I do not care much for Open Suse.. but I use it because its the only thing that works.

I just remembered. There may be a connection with this issue and your motherboard bios being outdated.  Everyone having this problem might try to find an updated bios.  Unfortunately there has been no updates for my board... EVER. So I'm hoping there is another solution

---

### Post by churfsan on 2008-05-25
> **spyckotic said:**
> I have been dealing with this problem for at least 6 months, possibly longer.  I've been through the last 3 "latest" nvidia drivers, spent countless hours trying to get this working.  If you dig hard enough you can probably find the threads around here. Open Suse was my only choice to have hardware acceleration, and I tried a handful of distro's all resulting in the same problem with the monitor going into stand by and the computer being unresponsive to any keyboard input.  The only thing to do is manually reset the machine and change the drivers back to nv.  These posts concerning this problem pop up from time to time and there is always a ton of suggestions, although nice and very much appreciated they never seem to work.  I was actually just coming back to check up on this situation when I found this thread.  Doesn't seem like much has changed yet.  I do hope this is resolved some day... I do not care much for Open Suse.. but I use it because its the only thing that works.

I just remembered. There may be a connection with this issue and your motherboard bios being outdated.  Everyone having this problem might try to find an updated bios.  Unfortunately there has been no updates for my board... EVER. So I'm hoping there is another solution

Thanks for sharing your experience. I am trying since Ubuntu 7.10 without success. Mine is MSI motherboard, but I did not really check whether any updates are available for the motherboard BIOS, I will see. As you say, Suse seems to work without any issues for NVIDIA.

I know one guy who got the XFX 8600GT board (same as mine) working with Ubuntu 7.10, including Compiz. I am trying to contact him and get some information; If I make any breakthrough, I will definitely post my solution here.

---

### Post by duncane on 2008-05-26
Well I can confirm I tried a DVI cable and it didnt make any difference.

Also it seems odd that the Nvidia driver works under Suse, but not under Ubuntu.

Im really stumped on this one...

---

### Post by churfsan on 2008-05-26
Looking at so many posts on problems with both NVIDIA and ATI cards, it appears that there are definitely issues with hassle free 3D graphics under Ubuntu, maybe for other linux flavors also. I have recently worked with only Ubuntu and OpenSuse. 

So I end up with Ubuntu on my laptop (works without any issues) and OpenSuse on my desktop (with 3D graphics on NVIDIA without any problems). In fact, IMHO, if you do not need cutting edge grpahics for 3D games, you are best off with Intel graphics, because this usually works out of the box, and no distribution can afford to ignore this segment (on-board graphics). 

We all wish to use Linux (different flavors) as it can do a lot of things better than windows, it is free, and generally hassle-free with virus etc. But IMHO the catch is that it should work with your hardware. If it works out of the box, you are very lucky. Perhaps we can even make it work with help from forums. But if we cannot get it working soon enough, instead of the operating systenm working for us to get our work done, we start working for getting the operating system to work! How many of us have not spent countless hours in frustration to make something work, which should actually work out of the box! But we still wish to use it as so many have worked for it, and it works great (when it gets going !).

As things are different and changing from one distro to another, we become specific to the distro and version (release) when we say whether something works or does not!

As I can see, I think I will stock to OpenSuse for my desktop (with 3D enabled), Ubuntu on desktop (no 3D) and again Ubuntu on my laptop (everything works, including compiz, wireless et al). I will keep checking here for solutions. Perhaps the next Ubuntu version - Intrepid Ibex (!?) will be different!

Thanks to everyone for all the help and suggestions!!!

---

### Post by duncane on 2008-05-26
This problem is the one thing blocking me from moving to Ubuntu full time is 3d games. Many of the games I like playing run fine under Wine (Portal, Oblivion etc), but if I cant get Nvidia driver working then its back to windows... 

I will give OpenSuse a try though.

---

### Post by spyckotic on 2008-05-27
I just wanted to add that I have had no luck with the following distros

PCLinuxOS, Slackware 12, Fedora 8, Linux Mint, and Ubuntu (there may be a couple more, but I don't remember).  I stopped trying distro's after OpenSuse worked.  OpenSuse seems to run a bit slower than I would like it to, even without hardware acceleration, but its the only disto I have got working so far and I don't have the time to try them all.

Also I would be completely happy without compiz and all the desktop effects with Ubuntu if I could just use my video card with the latest drivers.

---

### Post by vandalous03 on 2008-06-09
I'm facing the same situation here...I 've tried almost every possible method with no good results.
This is so disappointing.I have the Gigabyte Nvidia 8600GT 512MB.My monitor turns off after driver installation & reboot.I really like ubuntu and i'm not intending to change the flavor.I used to have an ATi X700 Pro working with the open source drivers.Unfortunately i had to change to the Nvidia card and now i can't enjoy my full eye candy desktop...!I just hope someone makes it possible.I'm using ubuntu since 6.06.
So,do you think that there is a good way to fix this?
Is there a way to access the Nvidia Product/Support/Community so they can help us out?

This is a big problem indeed...!

---

### Post by fmatosqg on 2008-10-23
Hi all, 


Just new in UBUNTU since yesterday, and I got some issues with the NVIDIA driver, now solved.

What happened is I am a long time linux user, mostly Slackware and also Debian (and a bit of Red Hat, a long time ago). And without knowing the proper ubuntu way of installing NVIDIA drivers, I went the NVIDIA way: download the drivers and run the installer. Everything worked ok, until the next reboot. Then, I could use no more the new installed drivers, aparently because of version conflict between libraries and module. But, every time I re-installed the drivers by the NVIDIA way, they worked again - until the next reboot.

After trying to revert to the ubuntu way of installing using apt-get (without success), I tracked down the problem to another version of the nvidia driver co-existing in my drive, and auto-installing in my kernel!!! I could see the /var/log/Xorg.0.log complaining of nvidia drivers not found, and at the same time, it was listed in #lsmod !!! How could that be? 

Inspecting #dmesg, I could see the reason: my kernel had another version loaded, not the one that I installed. BUT listed just the same in #lsmod. 

Then I tried unloading and loading the module:
#modprobe -r nvidia ; modprobe nvidia 
#X

and to my surprise it WORKED! so my solution is putting this modprobe line in /etc/init.d/rc.local, and now I boot everything OK.

Trying to find the bad driver clone in the /lib/modules tree seems to fail. So, where is this little impostor? Does someone understands what just happened here? Is this some sort of 'auto-intelligent-robot' that tries to guess things in the system, or is it an installation problem, or a modprobe.conf misconfiguration? If it is the first, I would like to turn it off at all. Yep, no updates, no guessing, nothing running in the background (I just come from slackware, where thing are veery straighforward and everything is manual). And anyway, if modprobe finds the correct module, why is the wrong one still being installed every time I boot?

---

### Post by churfsan on 2008-11-03
Any luck with anyone with the new version 8.10 Intrepid on NVIDIA drivers?

Thanks

---

### Post by churfsan on 2008-11-07
> **churfsan said:**
> Any luck with anyone with the new version 8.10 Intrepid on NVIDIA drivers?

Thanks
Hello all,

I am writing this to say that I installed Ubuntu 8.10 on the same machine, with NVIDIA 8600 GT. It now works without any problem!! 

Just go to System -> Adminitration-> Hardware Drivers and enable NVIDIA 177 drievr. It will download and install the driver. 

Here there is a small hitch. Sometimes the download progress window stops at 0% only, it is bug, but the download takes place in the background and installs the driver. You need to be patient for about 5 minutes (256 KBPS download speed). 

After that, just check under System -> Administration for a new menu entry "NVIDIA Settings", if so, the driver is installed. If you select the menu item, it will say "Looks like NVIDIA driver is not being used, Update your Xorg.conf file, just run "nvidia-xconfig" from terminal as root". 

Do that, and it will update your xorg.conf file, just restart X, using CTRL + ALT + BACKSPACE, it will logout you out and ask for login again. Just login and you have NVIDIA 3D fully working. 

Try enabling 3D effects and enjoy !!! Ubuntu 8.10 really rocks, especially with 3D enabled.

For all the persons who were kind enough to reply and comment, I would like to thank all of you.

Anyone facing problem with Ubuntu 8.04, I suggest upgrade to Ubuntu 8.10. It will solve many problems.

Thanks once again!!!

---

