---
title: "Flash"
date: 2009-01-30
forum: Multimedia Software
---

### Post by jake amrani on 2009-01-30
I've installed Ubuntu 7.10 on my PS3 to watch videos online.  Firefox is working fine, but when I try to install Adobe Flashplayer, I get the i386 wrong architecture message.  I've installed all the updates, but it wouldn't let me upgrade to 8.04.  What should I do next.  PS-I'm computer illiterate.

---

### Post by DeMus on 2009-01-30
> **jake amrani said:**
> I've installed Ubuntu 7.10 on my PS3 to watch videos online.  Firefox is working fine, but when I try to install Adobe Flashplayer, I get the i386 wrong architecture message.  I've installed all the updates, but it wouldn't let me upgrade to 8.04.  What should I do next.  PS-I'm computer illiterate.

Just give some details about which version Ubuntu you have (32 or 64 bits) and which Flashplayer you tried to install. Show the website wit the right link please.

---

### Post by jake amrani on 2009-01-31
How do I find out if I have the 32 or 64 bit version?  I was trying to install Adobe Flashplayer 10 for Ubuntu i386.deb.  I read about the problems with the new version of flash, so I tried downloading Flashplayer 9 from Adobe's archives, but Ubuntu wouldn't open that either.  When I try to upgrade to Ubuntu 8.04, it stops halfway through the installation and says, "Csnnot install Desktop".  Did I mention that I was computer illiterate?

---

### Post by jake amrani on 2009-01-31
When I tried sudo apt-get install-flashplugin-nonfree, it said "plugin non found".  I also tried [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb).  That wouldn't work either.

---

### Post by jake amrani on 2009-01-31
Sorry, that was [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2i386.deb).  Not a very good typist either.

I was trying to download Flash directly from Adobe's website.

---

### Post by reahjw6 on 2009-01-31
If you want to install the flashplugin go to system>applications>synaptic
Type flashplugin-nonfree and mark for install.
Reah.

---

### Post by jake amrani on 2009-01-31
Flashplugin-nonfree isn't in there.

---

### Post by m_duck on 2009-01-31
From the terminal, the code you want is```
sudo apt-get install flashplugin-nonfree
```You had an extra hyphen in there.

Also, to find out which version you are using enter the following in terminal```
uname -m
```i386 etc will mean 32-bit and x86_64 is 64-bit (I think uname -r will show either i386 or amd64, the latter being 64-bit).

EDIT: Apologies, I didn't read your post properly regarding the PS3 part...

---

### Post by redroad55 on 2009-01-31
read this thread..post#6 
 [http://ubuntuforums.org/showthread.php?t=1055259](http://ubuntuforums.org/showthread.php?t=1055259)

---

### Post by gandaran on 2009-01-31
jake amrani
there is no adobe flash plugin for your PS3, adobe hasn't made one for PowerPC computers (if I'm not wrong PS3 is PowerPC not Intel), you have to use gnash flash plugin look for it in synaptic and install

---

### Post by jake amrani on 2009-01-31
When I entered "uname -m" in Terminal it spit back, "ppc 64". 64 bit?

I looked in Synaptic, no gnash flashplugin.

Any other thoughts?

---

### Post by redroad55 on 2009-01-31
It is just listed as gnash ..click on it and it will give you description below

---

### Post by jake amrani on 2009-01-31
It's not there.  It goes from "gksu" to "gnome-accessability-themes".

---

### Post by redroad55 on 2009-01-31
when you open synaptic the box on left must have all selected .. also under settings tab at top of page > repositories ..you must not have the repositories needed in software sources if you are not getting gnash as a choice .. If you need help in doing that post back with what you have listed as repositories in software choice .. applications>system>administration>software sources..under ubuntu tab all should be checked and under third party , list what you have

---

### Post by jake amrani on 2009-01-31
Under the Ubuntu tab, nothing is checked and under the Third Party tab only cdrom:Xubuntu is checked.

---

### Post by redroad55 on 2009-01-31
check all under ubuntu tab except source code then close and your list should update .. then check synaptic again, post back

---

### Post by jake amrani on 2009-01-31
Gnash is there now.  Thanks. How do I install it?

---

### Post by redroad55 on 2009-01-31
in synaptic check gnash and hit apply and you should be good..Post back with results and or questions .. best to you

---

### Post by jake amrani on 2009-01-31
Gnash now appears with a green box in Synaptics.  I kept getting the Javascript/old Adobe Flash message from YouTube, so I also hit apply on Mozilla gnash plugin.  That box is green now, too.  I don't get the Java/Adobe message from Youtube, but I don't see any video, either.  What did I do wrong?

---

### Post by jake amrani on 2009-01-31
Do I need to hit Apply for gnash-cygnal and gnash-tools, as well?

---

### Post by whaevr on 2009-01-31
Well you can try using this userscript for the greasemonkey extension for firefox.

It allows you to watch youtube videos with the mplayer-plugin instead of flash. So you'll have to have mplayer and if theres another package for it the mplayer-plugin installed on your system.

I don't know if it will work for what your looking for but heres a [link](http://userscripts.org/scripts/show/7175)

If it does work this is just a fix for youtube..not flash in general.

---

### Post by redroad55 on 2009-01-31
no ..don't install anything else yet i'll be right back..

---

### Post by redroad55 on 2009-01-31
go to this link and copy and paste to get these repositories set up on your machine choosing your particular install ,8..04 or etc.

[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)

post back when your done..

---

### Post by redroad55 on 2009-01-31
just to make sure what version of ubuntu are you currently running
> Under the Ubuntu tab, nothing is checked and under the Third Party tab only cdrom:Xubuntu is checked.
this has me puzzled??
> I've installed Ubuntu 7.10 on my PS3 to watch videos online. Firefox is working fine, but when I try to install Adobe Flashplayer, I get the i386 wrong architecture message. I've installed all the updates, but it wouldn't let me upgrade to 8.04. What should I do next. PS-I'm computer illiterate
then there is this
> When I entered "uname -m" in Terminal it spit back, "ppc 64". 64 bit?
so before we can go further I have to be certain of version ..How did you install and from what source?

---

### Post by redroad55 on 2009-01-31
I found this [https://wiki.ubuntu.com/PowerPCFAQ#Flash,%20Flash%20video%20and%20Gnash]("https://wiki.ubuntu.com/PowerPCFAQ#Flash,%20Flash%20video%20and%20Gnash")
and this for future reference
[https://wiki.ubuntu.com/PowerPCFAQ#head-8d764a92cbe82911913d972b8189698f9f04e6f3]("https://wiki.ubuntu.com/PowerPCFAQ#head-8d764a92cbe82911913d972b8189698f9f04e6f3")
post back your thoughts

---

### Post by jake amrani on 2009-01-31
OK.  I installed the Medibuntu repositories and the keyring.  What do I do now?

---

### Post by jake amrani on 2009-01-31
I found instructions for installing Linux onto a PS3 on Youtube.  I donwloaded Xubuntu (Ubuntu 7.10) onto my PC, burned it to a disc in ISO format, and installed it onto my PS3 after partitioning the hard drive.

---

### Post by redroad55 on 2009-01-31
***DISREGARD THIS POST.. 8.04 is not ported for PS3 but 8.10 is*** just for reference this link will give you a place to download 8.04 which is the lts (long term support) supported thru 2011..Is the ps3 your only computer or a project? down load the 8.04 image the 32bit version in this case will run better although your machine is 64bit it appears..let me no how you feel about fresh install otherwise I will walk you through whats next with a little uncertainty of the final outcome mostly because not quite sure what you've done up until my post..but none the less it would be good to have the 8.04 I386 32bit to fall back on if we get in trouble
[https://wiki.ubuntu.com/PowerPCDownloads]("https://wiki.ubuntu.com/PowerPCDownloads")
It looks like they are giving you only one choice for 8.04 desktop that should be 32bit
let me know what you want to do next I'll be up for a couple more hours working on another project and back tomorrow around 8:00 EST

---

### Post by jake amrani on 2009-01-31
Wasn't too crazy about the new install, mostly because I don't know how to get the old one off.  I'm running the upgrade to 8.04LTS with the Update Manager.  It's working now that you told me to check all the boxes under the Ubuntu tab and I ran all the updates.  It says it'll take an hour.  I'll put up a post when it's done.  Look forward to hearing from you tomorrow.  Thanks for all your help.

---

### Post by redroad55 on 2009-01-31
no problem ..from there will get you streaming..talk to you soon..best to you..

---

### Post by jake amrani on 2009-01-31
Maybe not.  After the restart the system won't boot.  It loads the kernel, then says "Booting system" and the PS3 makes a lot of noise but nothing happens.  Yikes!

---

### Post by redroad55 on 2009-02-01
**** sorry this is what you want ****
[http://psubuntu.com/wiki/InstallUbuntu]("http://psubuntu.com/wiki/InstallUbuntu")
 [http://psubuntu.com/youtube-on-psubuntu/]("http://psubuntu.com/youtube-on-psubuntu/")
 [http://psubuntu.com/intrepid-ibex-released/]("http://psubuntu.com/intrepid-ibex-released/")
It seems that 8.04 lts is not ported for your ps3 but 8.10 is ..best to you..hope this helps ..post back with results..

---

### Post by jake amrani on 2009-02-01
Downloading 8.10 now.  It takes 2 hours.  Do I have to do anything to remove what's in there now, or do I just put the new cd in and tell ps3 to load the new OS?

---

### Post by redroad55 on 2009-02-01
Hi, I assume you still have your XMB native OS
    > You will not be erasing anything from your PS3s native operating system (XMB), but you need to let go of some 10GB of disk space
     Follow this link and if you have anything different post back
    [http://psubuntu.com/wiki/SetupPS3]("http://psubuntu.com/wiki/SetupPS3")
     >     *  Go to [System Settings] > [Format Utility].
    * Select "Format Hard Disk" and click [Yes].
    * Choose [Custom] and [Allot 10GB to the Other OS].
    * Select [Quick Format] and confirm with [Yes].


Formatting will take a few seconds. Press X to restart the system.

Log in (you need to hit the PS button on your controller if it's deactivated after restart)

---

### Post by jake amrani on 2009-02-01
The game OS is still working.  I assigned 10GB to the other OS when I partitioned the hard drive for Ubuntu 7.10.  Do I have to do anything to uninstall 7.10 before I put the new cd with 8.1 in the machine?

---

### Post by redroad55 on 2009-02-01
You should be able to reformat "the other OS " the same way clearing it for fresh install..
  >     *  Insert the disk you burned into the PS3. And connect the keyboard and mouse.
    * Go to [System Settings] > [Install Other OS].
    * Select "Other OS" and hit "Yes" to restart the system.

This is the important step
     > Make sure you have updated your Other OS in the XMB menu. Intrepid will not install using an old Other OS.
Start up the PS3s XMB system (if in kboot/terminal write: "ps3-boot-game-os" or "boot-game-os").
With the Intrepid disk loaded, go to [Settings > System Settings > Install Other OS]. The otheros.bld file will be detected on the disc. Hit [Start] to update your Other OS.

Go to Default System and switch from PS3 to "Other OS".

Then this step and your on your way

    > Loading the installer

With the Ubuntu disk loaded and OtherOS activated, start up your console, and wait for the installer to begin.

You will be greeted by two penguins and some lines of text. After a few seconds the terminal will display:

This is an Ubuntu installation CDROM
built on 20081030.
&#8230;
If in doubt, just press Enter.

kboot: _

Pressing Enter will start the installation with the kernel loading the system. Never mind the usb error message(s), just let the installer start up.

---

### Post by redroad55 on 2009-02-01
Had to edit above post reread if you have not already

---

### Post by digitalis_vulgaris on 2009-02-01
Welcome to Opera users... this is the easest solution for now.

---

### Post by jake amrani on 2009-02-01
Did all that.  The system couldn't find my wireless, so I skppied that step and elected to set it up later.  Now it's hung up on the partitioning.  I thought I did that on the ps3.  Ubuntu 7.10 didn't do this.  It's asking me to select a partition to modify.  It says, 
              
             Guided partitioning
             Help on partitioning

             /dev/ps3da - 10.7 GB Unknown
                  #1 primary  10.7 GB  f ext3   /

             Undo changes to partitions
             finish partitioning and write changes to disc

---

### Post by redroad55 on 2009-02-01
You did thats why it shows as #1 partition .. choose guided and make sure your choice for partition is the ext3 partion that already is there ..keep the size the same as you have and go..one quick question the image you downloaded is from this link ,right??
[http://psubuntu.com/intrepid-ibex-released/]("http://psubuntu.com/intrepid-ibex-released/")
the reason its different is this is an alternate insall image where as the 7.10 is the live cd..all is good just make sure you choose the ext3 partition as your target ..

---

### Post by jake amrani on 2009-02-01
Yes, I downloaded from the link you provided.  When I select Guided, the next screen says, 

Partitioning method:

Guided - resize /dev/ps3da1 and use freed space
Guided - use entire disk
Guided - use entire disc and set up LVM
Guided - use entire disc and set up encrypted LVM
Manual

I don't see any way to select ext3.

---

### Post by redroad55 on 2009-02-01
I have to go now until 4:30 be back then here are 2 links to keep you busy until then
[http://psubuntu.com/wiki/SetupPSUbuntu]("http://psubuntu.com/wiki/SetupPSUbuntu")
 [http://psubuntu.com/forums/viewtopic.php?f=4&t=765]("http://psubuntu.com/forums/viewtopic.php?f=4&t=765")

Post back and I'll look for you later

---

### Post by redroad55 on 2009-02-01
ok ..choose guided- resize /dev/ps3da1 and resize making it 1/2 of your hd so approx. 10gb then it will give you your 10gb as free space then choose free space  for your target and you should be good .. I'll be here for another 10 mins. for a quick post otherwise 4:30..best to you..

---

### Post by jake amrani on 2009-02-01
It says, " Because of an unknown reason it is impossible to resize this partition."

---

### Post by jake amrani on 2009-02-01
If I click on "#1 primary 10.2 GB B ext3", it says:

Partition settings:
Use as:          do not use

Bootable flag:   on

Reseize the partition (currently 10.2 GB)
Copy data from another partition
Erase data on this partition
Delete the parttion
Done setting up the partition

Should I erase the data or just resize the partition?

---

### Post by jake amrani on 2009-02-01
I clicked resize and got the same "It's impossible to rezise" message.

---

### Post by redroad55 on 2009-02-01
we will have to go back to this making sure all steps are correct
> Set up your PS3 to run Linux

You will not be erasing anything from your PS3s native operating system (XMB), but you need to let go of some 10GB of disk space.

What you need

    * An Ubuntu version for PS3 burned on a CD (these instructions are based on either the standard Ubuntu&#8734; or more lightweight Xubuntu&#8734; releases). For information on how to burn iso files to a cd, see this page&#8734;.
    * A USB keyboard and mouse. Wireless and bluetooth input devices should work fine (with a dongle).
    * A USB stick or external hard disk (if you want to backup files and saved games on your PS3).


Formatting the PS3 hard disk
The first thing you need to do is to format the PS3s hard disk to make room for a second operating system (called Other OS). Your user profiles and account information will remain on the XMB, but remember to back up any saved games or media files you want to restore after formatting the PS3 using a USB stick or an external hard disk. Your game saves are located under Game > Saved Data Utility.

All downloaded games you paid for can be downloaded again without having to pay for them. They'll be in your account history in the PS Store.

    * Go to [System Settings] > [Format Utility].
    * Select "Format Hard Disk" and click [Yes].
    * Choose [Custom] and [Allot 10GB to the Other OS].
    * Select [Quick Format] and confirm with [Yes].


Formatting will take a few seconds. Press X to restart the system.

Log in (you need to hit the PS button on your controller if it's deactivated after restart).

Installing Other OS

    * Insert the disk you burned into the PS3. And connect the keyboard and mouse.
    * Go to [System Settings] > [Install Other OS].
    * Select "Other OS" and hit "Yes" to restart the system.



> Make sure you have updated your Other OS in the XMB menu. Intrepid will not install using an old Other OS.
Start up the PS3s XMB system (if in kboot/terminal write: "ps3-boot-game-os" or "boot-game-os").
With the Intrepid disk loaded, go to [Settings > System Settings > Install Other OS]. The otheros.bld file will be detected on the disc. Hit [Start] to update your Other OS.

Go to Default System and switch from PS3 to "Other OS".

Loading the installer

With the Ubuntu disk loaded and OtherOS activated, start up your console, and wait for the installer to begin.

You will be greeted by two penguins and some lines of text. After a few seconds the terminal will display:

This is an Ubuntu installation CDROM
built on 20081030.
…
If in doubt, just press Enter.

kboot: _

Pressing Enter will start the installation with the kernel loading the system. Never mind the usb error message(s), just let the installer start up.

ok ..I'll be back later..best to you

---

### Post by jake amrani on 2009-02-01
I did not format the disk again.  I will try again from the beginning.

---

### Post by redroad55 on 2009-02-01
If you choose delete patition it should leave you with the 10gb of free space .. that should allow you to install on the 10gb of free space.. if for some reason it won't let you it will have to wait until I get back .. My wife is waiting ..talk to you in awhile

---

### Post by jake amrani on 2009-02-01
I did the install from the beginning and re-formatted the disc this time.  I've got Ubuntu 8.04 and Firefox working.  I've got gnash and the Mozilla flash plugin installed.  Under Tools it says that gnash swf is applied.  I can watch videos on Youtube after installing an add-on that the machine recommended.  But I can't seem to get video from sites like AOL, usanetworks or abc.com.  I know we're close.  BTW - tell your wife I thank her for her patience and you for your help.

---

### Post by redroad55 on 2009-02-01
Great .. Your 0n your way .. On streaming other video you may need real player .. I think first make sure you have medibuntu repository available in previous install and then ..
> Playing Restricted Formats

Follow these steps to play most common multimedia formats, including MP3, DVD, Flash, Quicktime, WMA and WMV, including both standalone files and content embedded in web pages.

Ubuntu 7.10, 8.04, and 8.10

Synaptic

    *

      Go to Applications &#8594; Add/Remove...
    *

      Set Show: to All available applications
    *

      Search for ubuntu-restricted-extras and install it. Note that there is also xubuntu-restricted-extras (for Xubuntu) and kubuntu-restricted-extras (for Kubuntu.) 

check out this  [https://help.ubuntu.com/community/RestrictedFormats#Synaptic]("https://help.ubuntu.com/community/RestrictedFormats#Synaptic")

You've done well.. Post back on your progress with the rest and will see what we can do .. Best to you .. My wife is as sweet as they come .. best thing that ever happened to me

---

### Post by jake amrani on 2009-02-02
Got home late last night.  I live in Phoenix, poor Cards.  I'll have to re-install Medibuntu.  It's gone since I reformatted the disc for 8.10.  I'll also go through the other links you sent.  I'll post again this evening and let you know how it works.  Thanks again for all your help.

---

### Post by redroad55 on 2009-02-02
That's kinda funny but not I live about an hour away from Pittsburg .. So I guess I was aiding the enemy ..HaHaHa ..Talk to you later .. Best to you

---

### Post by jake amrani on 2009-02-02
OK, here we go again.  I installed Medibuntu and the keyring.  When I try to add the ubunut restricted extras, this is what I get:

Cannot install 'ubuntu-restricted-extras'

This application conflicts with other installed software. To install 'ubuntu-restricted-extras' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

I don't know what to do in synaptic package manager.

---

### Post by redroad55 on 2009-02-02
Hey how are doing ?..in synaptic go down to the restricted pkg for ubuntu select and apply and it should tell you the conflicts and tell you what is needed..Post back with results..Best to you

---

### Post by redroad55 on 2009-02-02
If you have any issues double check your software sources > third party Medibuntu is 8.10 rather than 8.04 then check update tab > making sure unsupported (backports) is checked..Post back.. Best to you.. I'm done for tonight it's 12:00 here..Talk to you Today/Tomorrow

---

### Post by jake amrani on 2009-02-03
Thanks.  It's resolving the conflicts in Synaptic manager now.  The unsupported backports was not checked.  That's next.  One other issue, if you don't mind.  How do I get it to automatically connect to my wireless internet?  I have to tell it to connect to the hidden wireless each time I boot.

---

### Post by redroad55 on 2009-02-03
Hey..this is what I found on wifi for PS3...read thru and if you have any questions post back..best to you

> Before you start notice that you will need at least temporary internet access in order to download rpm2cpio

1) Download the necessary files to patch the kernel. The link is here&#8734; The files you need are:
initrd.img-2.6.24
kernel-2.6.24-20080131.ppc64.rpm
Download them to an external drive that you can then copy into Ubuntu. Next you will need the correct bootloader. If you followed the install instructions on the site then you already have the correct bootloader. Otherwise download and install the bootloader here&#8734;
2) If you're following a fresh install procede to step 3. If you updated the kernel at anytime make sure that you boot into the old kernel. To do this restart the PS3 and at kboot: type
kboot: old
and hit enter. You should now be booted into the old kernel.
3) Ok once your inside ubuntu, copy the files initrd.img-2.6.24 and kernel-2.6.24-20080131.ppc64.rpm to the desktop.
4) If you have rp2cpio skip to step 5. Otherwise you will need to download rpm2cpio and this is the part where you will need a wired connection. If you are connected to the internet go into the Synaptic Package Manager (note for noobs: this is where you can download pretty much anything and everything) and search for rpm2cpio. Click on it and download it.
5) Once you have rpm2cpio, go into the terminal and type:
rpm2cpio kernel-2.6.24-20080131.ppc64.rpm | cpio -idmv
another noob note: make sure you specify the directory that the file is at. For example if it is on the desktop and my username is john I believe the appropriate command is:
rpm2cpio /home/john/desktop/kernel-2.6.24-20080131.ppc64.rpm | cpio -idmv
6)That should extract the files somewhere either the desktop or your home folder. Now manually copy vmlinux-2.6.24, initrd.img-2.6.24 and config-2.6.24 to /boot and 2.6.24's modules to /lib/modules.
7) Now add the following line to /etc/kboot.conf like this (line beginning with test)

test='/boot/vmlinux-2.6.24 initrd=/boot/initrd.img-2.6.24 root=UUID=48124dc5-2c8f-43d0-a210-0b6549ffde56 quiet splash'

The value "48124dc5-2c8f-43d0-a210-0b6549ffde56" have to be changed according to your PS3.

8) Now run 'sudo update-initramfs -k 2.6.24 -u' and 'sudo depmod -a' in terminal
9) Now restart the system.
10) In order to load the system with the new kernel you&#314;l have to type "test". If you don't want to write test all the time you can edit kboot.conf and set "test" as the default value.
11) Now enter the network manager at the top right corner of the desktop and see if the wi-fi drivers are working. You should see an option that says wireless connections if its working.


---

### Post by jake amrani on 2009-02-03
rpm2cpio doesn't appear in my synaptic update manager.  My internet works; I just have to manually tell it to connect each time I boot.

I've downloaded Medibuntu, updated the restricted extras and added the backports, but still not video.  What's next?

My ex-wife and kids lived in Erie for 2 years.  Are you near there?

---

### Post by jake amrani on 2009-02-03
In Add/Remove, I see MPlayer, Gnome MPlayer, VLC Mediaplayer, KPlayer, Dragon Player, Kaffeine, gxine and Miro Internet TV.  Do I need to install one of these?

---

### Post by redroad55 on 2009-02-03
Hey , vlc is my favorite for video and probably the most stable ..if you are currently ok with the wifi you have and it connects that's good news ..I will look into what is needed for better way to connect with your ps3 ..synaptic is going to be your best choice for adding anything to your machine because it will keep you, for the most part, from adding something that would make your system unusable .. The ps3 has some limitations to overcome and because I don't have one here to test on will have to take it slow to get everything you want to work well for you..In the morning I'll come back with some recommendations for a good video set up for you..My wife and I live SE of Erie about an hour out in the country in a hemlock forest, with broadband of course..Best to you talk to you tomorrow .. Best to you

---

### Post by jake amrani on 2009-02-04
Just for kicks, I tried vlc, mplayer and mplayer with gnomeplayer.  No luck.  I removed each after testing on Yahoo and aol.

FYI - The pictures are awesome and the web pages load in a much more user friendly format with Ubuntu 8.10 and the PS3 compared to 7.10.  I'm sure the video will be great when we get that figured out, too.

Thanks again for your patience and persistence.

---

### Post by redroad55 on 2009-02-04
Hey, So refresh me with where you are now..Have you got Gnash plugin for Firefox installed? and Are you streaming Utube ? Post back..Best to you

---

### Post by jake amrani on 2009-02-04
I do have gnash plugin for Firefox installed.  I can get video from YouTube, but from nowhere else.

Did you notice our thread has 800 views?  There must be a lot of other people out there with the same issue, but no solutions.

---

### Post by redroad55 on 2009-02-04
ok here we go  paste this in terminal:

 > sudo apt-get install alsa-oss faac faad gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libavcodec-unstripped-51 libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar 
 
> Note: as you are installing Sun Java you will be asked to accept an end-user license agreement (EULA) before the installation of the Sun Java packages begins. Press the tab key on your keyboard (above the caps lock key), followed by the enter key to accept the EULA and complete the installation.

this is the quickest way to install what we need .. Post back .. best to you

---

### Post by redroad55 on 2009-02-05
To the moderator this thread should have a Ps3 tag or read " Flash for PS3" .. just flash brings a lot traffic these days .. Don't want people to waste their time here if they don't have a PS3

---

### Post by jake amrani on 2009-02-05
Cut and pasted it into Termianl.  Here's what I got back:

E: Couldn't find package gstreamer0.10-pitfdll

---

### Post by jake amrani on 2009-02-05
Actually, this is everything it spit back:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-ffmpeg is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-plugins-bad-multiverse is already the newest version.
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-ugly-multiverse is already the newest version.
E: Couldn't find package gstreamer0.10-pitfdll

---

### Post by redroad55 on 2009-02-05
make sure the Multiverse and Universe repositories are enabled, although they should be enabled by default in the latest versions of Ubuntu. To make sure they are, or to choose a local server for downloads, navigate to "System > Administration > Software Sources" and tick whichever sources you wish to use, perhaps including unofficial updates (backports) in the "Updates" tab, as that will enable you to receive newer versions of some applications. Attempt to paste the above in terminal again and run..If it stops again go to synaptic and install each there until complete..

next:> sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin

and then:> sudo apt-get install gnome-mplayer gecko-mediaplayer

this should give you everything you need to stream most media..Post back with results ..Best to you

---

### Post by jake amrani on 2009-02-06
I can't find the gstreamer pitfdll anywhere.  I tried skipping it and entered this into Terminal:

jake@ubuntu:~$ sudo apt-get install alsa-oss faac faad libavcodec-unstripped-51 libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libavcodec-unstripped-51 is already the newest version.
libmp3lame0 is already the newest version.
libmp3lame0 set to manually installed.
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

So, the two things I don't already have are the gstreamer pitfdll and Java.  I didn't try to go any further.

---

### Post by redroad55 on 2009-02-06
this will effect some applications only a few ..let's goahead with the rest of the installs and then test ..post back

---

### Post by redroad55 on 2009-02-06
run this 

 > sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
and then

> sudo apt-get install gstreamer0.10-pitfdll sun-java6-fonts sun-java6-jre sun-java6-plugin 

Post back..Best to you

---

### Post by jake amrani on 2009-02-07
The first one went through without a problem.  Here's what I got when I tried the second, and then when I tried the second without the gstreamer 0.10 pitfdll:

jake@ubuntu:~$ sudo apt-get install gstreamer0.10-pitfdll sun-java6-fonts sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gstreamer0.10-pitfdll
jake@ubuntu:~$ sudo apt-get install sun-java6-fonts sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

It's really hung up on that gstreamer file and Java.

---

### Post by redroad55 on 2009-02-07
For the time being have you done this step:

> sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin 

and this:

> sudo apt-get install gnome-mplayer gecko-mediaplayer

if so test streams from those places you prefer .. I'll work onthe java canidate..Post back ..best to you

---

### Post by jake amrani on 2009-02-07
Did both.  Still no video:(

---

### Post by redroad55 on 2009-02-07
when you say no video .. you've lost utube stream? more detail..Post back

---

### Post by jake amrani on 2009-02-07
I still have video on youtube.  On Yahoo, the video screen fill with a message that says that everything (CNTRLS, ID, etc) is undefined.  On aol, the video screen stays black.

---

### Post by jake amrani on 2009-02-07
Does mediatomb help us:

[http://linuxowns.wordpress.com/2008/04/28/stream-media-from-ubuntu-to-your-ps3/](http://linuxowns.wordpress.com/2008/04/28/stream-media-from-ubuntu-to-your-ps3/)

---

### Post by redroad55 on 2009-02-07
on aol and yahoo what are you trying to do video related ..not clear on this .. also currently under add ons in your firefox browser what is listed under plugins .. In synaptic I don't understand why this pkg.is not there "gstreamer0.10-pitfdll" look again and also for "java-package" if there install,if not go back to software sources ,,make sure everything on first tab is checked except source code and under third party list all checked listings..Post back

---

### Post by jake amrani on 2009-02-08
On Yahoo, I am clicking on video news stories; nothing happens.  If I go to aol videos and click on a video, I get a black screen with play and pause buttons, but the buttons don't work.

Under Firefox Plugins, I have Default, DivX, gecko mediaplayer, IcedTea, QuickTime, RrealPlayer, SWF, and Windows Media Player.

Under Software Sources Third Party, those checked are archive ubuntu intrepid main, universe and multiverse and the updates and medibuntu.

Although unsupported backports is checked under updates, it is not checked under third party.

---

### Post by redroad55 on 2009-02-08
Did you have any success with "gstreamer0.10-pitfdll" and "java-package" in synaptic.. Is it showing up ? Post back

---

### Post by jake amrani on 2009-02-08
"gstreamer0.10-pitfdll" and "java-package" do not appear in Synaptic.  Is there anywhere I can download them?

---

### Post by redroad55 on 2009-02-08
First ,under "Java" in synaptic what do show ? Second there is a question as to why these pkgs. don't show up in synaptic ..My current thoughts are since the 8.10 version was a build specifically for ps3 it might be they don't show up because they won't work..this link shows how they got java but I'm not certain about it yet , looks promising both the app and "java"
[http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=302]("http://ps3mediaserver.org/forum/viewtopic.php?f=3&t=302")
[http://ps3mediaserver.blogspot.com/]("http://ps3mediaserver.blogspot.com/")
[http://code.google.com/p/ps3mediaserver/]("http://code.google.com/p/ps3mediaserver/")
Post back

---

### Post by jake amrani on 2009-02-08
This is what comes up under Java:

javacc
java2html
sun-java6-javadb
libcommons-jxpath-java
javacc-doc
sun-javadb-common
sun-javadb-client
libcommons-beanutils-java
sun-java6-jre
sun-java5-jre
libnb-java2-java...it goes on for another 100 or so.  Just no "java package".  Java common is checked.

I'll check the 3 links you sent.

---

### Post by jake amrani on 2009-02-08
Looked at the 3 links you provided.  The first was over my head.  The other 2 refer to ps3 media server, but I don't know how to install that.

---

### Post by redroad55 on 2009-02-08
Ok ..I must warn you this next step is risky but if you feel you are not up to say this guide, it would be the "Linux self extracting binary file "..
[http://www.java.com/en/download/help/5000010500.xml#100]("http://www.java.com/en/download/help/5000010500.xml#100")
then we have no alternative but to try synaptic with these pkgs.

                   1)sun-java6-bin
                   2)sun-java6-fonts
                   3)sun-java6-jre
                   4)sun-java6-plugin

so check these and hit apply and allow any other suggested pkgs. to be installed and cross your fingers..Post back with any results and or questions..best to you

---

### Post by jake amrani on 2009-02-09
Sorry, I don't mean to be a pain, but I don't know how to do what's described in the link.  My synaptic doesn't have sun-java6-bin or sun-java6-plugin.

---

### Post by redroad55 on 2009-02-09
No problem .. I will write up a step by step tomorrow and post back

Hang in there..Best to you

---

### Post by redroad55 on 2009-02-10
Hey I'm really swamped here .. I'll be able to get you what you need tomorrow .. until then .. Best to you

---

### Post by jake amrani on 2009-02-10
Thanks.

---

### Post by redroad55 on 2009-02-11
Hey, So currently at your house what is your network besides thePS3 ?

---

### Post by jake amrani on 2009-02-22
Sorry, I've been out of town.  I have 3 other computers that are all Windows, 2 XP and one Vista.  The PS3 is hooked up to my TV.  That's why I was trying to get this running on the PS3.  I may just  have to try Windows on the PS3.

---

### Post by VidiotGeek on 2009-05-24
> **DeMus said:**
> Just give some details about which version Ubuntu you have (32 or 64 bits) and which Flashplayer you tried to install. Show the website wit the right link please.

The PlayStation 3 has a PowerPC based processor, not x86, which is why it gives you the "wrong architecture" error message. You will have to install gnash using the package manager, look for "mozilla-plugin-gnash".

More info about the project here: [http://www.gnu.org/software/gnash/](http://www.gnu.org/software/gnash/).

**[EDIT] **
Sorry, such a n00b myself, didn't fully explore the thread before posting...

---

