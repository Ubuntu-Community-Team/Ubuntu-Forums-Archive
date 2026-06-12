---
title: "Boot Ubuntu and Windows through PXE"
date: 2012-08-28
forum: Networking &amp; Wireless
---

### Post by darkapec on 2012-08-28
Is there anyway to boot into a linux live distro (pick your favorite) and start a windows installation?

My issue is I have failed and failed at trying to get any version of Windows to boot via PXE. I run a small computer shop and I hate keeping track of all these CD's and carry them everywhere. I have managed to get just about every tool known to computer gurus to run via PXE. 

My goal is to boot a custom made version of Windows 7 that allows me to type in any Retail / OEM  (x64 & x32) key for any version (home, pro, etc). I already have this disk made and I have had great success with it, but there has to be a way to do this diskless. As time goes on I am doing repairs on more and more netbooks and I am tired of always rigging a external cd drive to install windows. 

IDEAS??? Or any methods that you are currently using?

I do not want to make .WIMS for every version. That is a lot of wasted space and if I am doing a reload on a customer machine the installs would likely blue screen due to incorrect drivers.

---

### Post by gnome_nz on 2012-08-29
I struggled for WEEKS with this problem.

And I think you may need to look at a lot of "wasted space".

If the following isn't too clear my email is below.

Part of the problem is that Windows installs (at least the boot process) expects to see a certain file, which would probably throw out all the other things (ie the "pxelinux.0" file that most things can handle isn't liked by Windows, and the Windows stuff isn't liked by anything else - which has caused me much annoyance because until I came up with an answer I either had to be able to do Windows or the other stuff,  not both without breaking a lot of already working systems!)

The only answer I have found so far that lets me boot Windows installs, Linux installs and various tools is to create a custom image of the install you want of Windows, and then pxeboot something like Norton Ghost (use that one coz the boss at work can understand it)/Ghost4Linux etc that can "clone" the image to the target HDD. 

To create the images, you do an install on either a real or virtual machine, do NOT put the key in (unless you have a volume license), and clone/image the disk. Seems it pays to make the partition as small as you can to save space, but at least Ghost manages to turn the empty gigs into a few k (at most) of image file. If you'll use Norton Ghost to install you *must* use it to create the images as well IME.


If you can come up with another way to do this, which works better somehow (the server also has backup CD/DVD images for all variants of XP/Vista/7 and I'd much rather mount each of them via fstab and boot do the install "properly" than waste so much space. 

That said, while there's some other work needs doing (many cases the first boot will toss up a "0x7B" error due to wrong HDD drivers and unless you re-build the images each month you run into "must activate" problems), I can get the install of XP onto a disk in under 5 minutes from power on over a 100M lan, 7 is a little longer as the image is a little larger. Even with booting Falcon 4 over the lan to get to the "Fix 7B" tool in F4's MiniXP, I can still have XP installed MUCH faster than doing it via CD. 

I've had a lot of stress building the system I have, but am willing to share. Right now I can pxeboot to install Win XP, Vista and 7 (still to finish making the images), several variants of Linux (well, all Deb/Ubuntu based), the 32 and 64 versions of Offline Defender,  BitDefender, Falcon4 (as an ISO, still haven't got it or Hirens booting otherwise), DOS (as part of the Ghost setup). If you're interested I'm willing to share my configs etc with you, just email me: kiwi rider 777 at gmail - of course no spaces and a certain symbol commonly on the "2" key.

Now, the reason I came to this site tonight is to find the answer to a problem I am having the perhaps you've fixed.. All  my Ubuntu-based PXE stuff (Ubuntu/TAILS/Zorin/BitDefender) have a certain level of brokeness with the networking. Most can access the network/internet but the network port is "unmanaged". BitDefender cannot access the network at all, which means it cannot update itself. I can get it to work with some playing, but I want others to be able to boot and run this without knowing how to edit "interfaces" and restart the networking. 

Any thoughts?

HTH, and thanks if you can help me.. 
KR

---

### Post by darkapec on 2012-08-29
Well I can start by answering your UBUNTU questions. I am able to boot ubuntu images 2 different ways.

1. directly from the ISO using memdisk and HTTP like so 

```

LABEL BOOTCD
    menu label Ubuntu x32 Live
    MENU DEFAULT
    kernel memdisk
    append raw iso
    initrd http://192.168.1.145/apache/linux/x32/ubuntu/ubuntu32.iso

```2. The faster and most reliable way is creating a loop mount of the ISO in FSTAB to a directory in TFTPBOOT like so:
```
/tftpboot/Kratos/linux/ubuntu-11.04-desktop-i386.iso /tftpboot/Kratos/linux/x32/ubuntu/11.04 udf,iso9660 user,loop 0 0

```then mount all with 
```
sudo mount -a 
```then adding the following to /etc/exports:
```
/tftpboot/Kratos/linux/x32/ubuntu/11.04/ *(ro,sync,no_wdelay,insecure_locks,no_root_squash,insecure)
```then update with 
```
*sudo exportfs -a*
``` and booting via:
```
LABEL Ubuntu Livecd 11.04
MENU LABEL Ubuntu 11.04 x32
KERNEL Kratos/linux/x32/ubuntu/11.04/casper/vmlinuz
APPEND root=/dev/nfs boot=casper netboot=nfs nfsroot=192.168.1.145:/tftpboot/Kratos/linux/x32/ubuntu/11.04 initrd=Kratos/linux/x32/ubuntu/11.04/casper/initrd.lz quiet splash --

```I have not had any issues with networking using either of the methods above. As this will simply boot the normal "Live cd" and allow you to install from there or run the LIVE version. 

I have found a somewhat more reliable method to boot windows via pxe then the way you mentioned via [http://www.ultimatedeployment.org/win7pxelinux1.html](http://www.ultimatedeployment.org/win7pxelinux1.html)

That link will show you a way to boot windows via PXE and you will not have the issues with the activation timer running out and you wont need ghost to start the imaging process.  

But again that method would require me to do those steps for every single version of Windows 7 (starter, home, pro, server all in x32... then all in x64... all in OEM... then all in Retail) do the math. That is at least 16 different versions of windows 7, with an install size of 10-20gb (with the exception of starter) brings the grand total to 150+ gb of wasted space. Not to mention A LOT of wasted time creating all of these images. 

My goal is to simply be able to boot a custom ISO of windows 7. It doesnt necessarily have to stay in ISO form, but I need the installation process to remain unmodified. So upon booting it it will ask for the KEY etc. This will allow me to have 1 installation that will accept all keys and install the corresponding version. 

Space is not an issue exactly, I do have a 8tb raid... but my primary drive is a 64gb SSD and I would much rather have all TFTPBOOT data stored on this drive, it makes for much faster transfer speeds. 

So my idea is... I boot into knoppix / or ubuntu / or DSL / or whatever and from there I am able to mount my custom ISO of windows... this is where I am stuck. Is there any utility? Maybe wine? that would allow me to run the windows installation. I would assume that if I am able to run the installer it would detect the actual hardware of the system and allow me to install to the computers hard drive? 

I may have answered my own question. I will install wine on mfsbsd and see how it goes. 

and thank you for your response gnome, hopefully I helped answer your question

---

### Post by darkapec on 2012-08-29
> **gnome_nz said:**
> 
Now, the reason I came to this site tonight is to find the answer to a problem I am having the perhaps you've fixed.. All  my Ubuntu-based PXE stuff (Ubuntu/TAILS/Zorin/BitDefender) have a certain level of brokeness with the networking. Most can access the network/internet but the network port is "unmanaged". BitDefender cannot access the network at all, which means it cannot update itself. I can get it to work with some playing, but I want others to be able to boot and run this without knowing how to edit "interfaces" and restart the networking. 

I will double check this tonight. I do not recall if was "unmanaged" or not. But if my setup is working correctly I will let you know and you can either resetup using the methods I mentioned earlier or maybe updating to the latest version of 12.04.01 will help.

---

### Post by gnome_nz on 2012-09-03
> **darkapec said:**
> Well I can start by answering your UBUNTU questions. I am able to boot ubuntu images 2 different ways.

2. The faster and most reliable way is creating a loop mount of the ISO in FSTAB to a directory in TFTPBOOT like so:
```
/tftpboot/Kratos/linux/ubuntu-11.04-desktop-i386.iso /tftpboot/Kratos/linux/x32/ubuntu/11.04 udf,iso9660 user,loop 0 0

```<snip>

[/CODE]then adding the following to /etc/exports:
```
/tftpboot/Kratos/linux/x32/ubuntu/11.04/ *(ro,sync,no_wdelay,insecure_locks,no_root_squash,insecure)
```then update with 
```
*sudo exportfs -a*
``` and booting via:
```
LABEL Ubuntu Livecd 11.04
MENU LABEL Ubuntu 11.04 x32
KERNEL Kratos/linux/x32/ubuntu/11.04/casper/vmlinuz
APPEND root=/dev/nfs boot=casper netboot=nfs nfsroot=192.168.1.145:/tftpboot/Kratos/linux/x32/ubuntu/11.04 initrd=Kratos/linux/x32/ubuntu/11.04/casper/initrd.lz quiet splash --

```I have not had any issues with networking using either of the methods above. 


My setup is much like yours with the exception of not having had "user" in the fstab and I have a "fsid=x" in each of the lines in exports. Have tried one distro with your settings, still the same (this affects Ubuntu, Mint, Zorin, Tails and most importantly BitDefender - unless you can suggest an alternative AV product to use in its place? (Not counting Windows Defender Offline which I boot from ISO ok)


> I have found a somewhat more reliable method to boot windows via pxe then the way you mentioned via [http://www.ultimatedeployment.org/win7pxelinux1.html](http://www.ultimatedeployment.org/win7pxelinux1.html)

That link will show you a way to boot windows via PXE and you will not have the issues with the activation timer running out and you wont need ghost to start the imaging process.  

But again that method would require me to do those steps for every single version of Windows 7 (starter, home, pro, server all in x32... then all in x64... all in OEM... then all in Retail) do the math. Yeah, have done... My setup uses the following sizes (each is an "installed" image) :

```
-rw-r--r-- 1 root root 3.3G Sep  3 08:53 v_biz_64.GHO
v_bizn64.GHO     3.0G   
v_hmbs64.GHO   3.0G   
vhmbsn64.GHO   2.7G  
v_hmpr64.GHO    3.8G  
v_ult_64.GHO       3.8G
w7_64bit.gho        3.4G    
w7_hp_64.gho       3.6G        
xp_home.gho        476M      
xp_pro.gho            1.3G        

```While each file is in the region of 3g (with the strange exception of the XP Home - hope I have a backup somewhere!), they tend to work quite well.. I think... (Getting a 0xc...225 error off one of the W7 ones right now.. Dammit!).  Some of these are clones made from a 80G HDD (all the x64 ones) - Ghost has a fairly decent compression algorithm, and when it works (at least with the XP ones) I can have Windows fully installed inside of 30 minutes - but I have to run a tool from Falcon 4 to fix the 0x7B error that's invariably thrown up when I install on different hardware to the machine/VM I created the images in.  That's on a 100M network - by the time it's deployed I expect at least some of our LAN will have Gig, so should be a lot faster.

Like you I work in a small (very!) PC repair shop, and am building a netboot (among other things)  server to help deal with the strangeness of the CD's (They go missing, we burn some more, then the missing ones re-appear - think the young part-time trainee is taking some home with him then bringing them back sometime later)

> 
That is at least 16 different versions of windows 7, with an install size of 10-20gb (with the exception of starter) brings the grand total to 150+ gb of wasted space. Not to mention A LOT of wasted time creating all of these images. Heh. Space... Not so much.. But time? Been pulling some very long hours doing this.. 

> My goal is to simply be able to boot a custom ISO of windows 7. It doesnt necessarily have to stay in ISO form, but I need the installation process to remain unmodified. So upon booting it it will ask for the KEY etc. This will allow me to have 1 installation that will accept all keys and install the corresponding version. 
I need to be able to do XP and Vista as well as 7, plus of course various other tools. Getting a "proper" installer (or at least some sort of PE) could be nice, esp for things like XP's "Repair Install" (why oh why didn't the twits at MS keep that in Vista/7? So helpful sometimes!), but then if we're going that far we'll probably just pull the HDD and run it in a different machine.

Now... To your idea... I have a file named "w98se-netboot.ima" which I've slightly modified to handle Ghost.. You should be able to find the original with Google.. It IS Windows 98 based and I am not sure how you can get a XP/Vista/7 equiv of the old "command.com" but this maybe could help you? Get that running, point it to a NFS (or other) share.... ?

Simple to boot :
```

        KERNEL memdisk
        append initrd=path/w98se-netboot.IMA

```> So my idea is... I boot into knoppix / or ubuntu / or DSL / or whatever and from there I am able to mount my custom ISO of windows... this is where I am stuck. Is there any utility? Maybe wine? that would allow me to run the windows installation. I would assume that if I am able to run the installer it would detect the actual hardware of the system and allow me to install to the computers hard drive? I suspect/believe that WINE is a kind of VM system, so you may have some issues with the hardware, or even seeing the HDD itself right (not played with it much). If it works though, please let me know! I could simply mount the CD/DVD images like we do above and go from there... Hrm... Mebbe I should give it a whirl myself...  <buggers off to play with configs... >

Ok... Not quite but this may be of use to you... Tried using that W98 thingy above, and creating a share of the Win7 DVD (32 bit). The "setup.exe" on the CD requires a running windows to run.. So will need to approach from some other angle.. 

This method won't work for XP as it needs to reboot and read from the CD a second time before it continues (and I tried copying i386 elsewhere - really painful process and as you'll understand don't really want to sit around nursing an install through each and every little step!), but maybe we're heading somewhere in the right direction for Vista and 7?

Would be interesting to see your thoughts on this...

> and thank you for your response gnome, hopefully I helped answer your questionNo probs. Thanks for your help as well..

---

### Post by darkapec on 2012-09-03
> My setup is much like yours with the exception of not having had "user"  in the fstab and I have a "fsid=x" in each of the lines in exports. Have  tried one distro with your settings, still the same (this affects  Ubuntu, Mint, Zorin, Tails and most importantly BitDefender - unless you  can suggest an alternative AV product to use in its place? (Not  counting Windows Defender Offline which I boot from ISO ok)

I booted one of my mine and I now see what you mean. My ubuntu boots into an "unmanaged" network environment... however the internet still works just fine. So in theory it shouldn't matter if its being managed or not as long as its working, correct?

I assume because it is netbooted that is just the default behavior, but the network connection should still work without any adjustments. 

Must just have to do with the way it is booted, I mean the network connection is in use before the kernel is even loaded, so it must just be using the generic PXE boot driver. 

> 
Now... To your idea... I have a file named "w98se-netboot.ima" which  I've slightly modified to handle Ghost.. You should be able to find the  original with Google.. It IS Windows 98 based and I am not sure how you  can get a XP/Vista/7 equiv of the old "command.com" but this maybe could  help you? Get that running, point it to a NFS (or other) share.... ?

This might work, however I tried doing something similar with miniXP and it works with XP, but it does not work with windows 7, I assume because when you run the setup from within windows it thinks you want to "upgrade" and it is not possible to upgrade from xp to 7. 

> I suspect/believe that WINE is a kind of VM system, so you may have some  issues with the hardware, or even seeing the HDD itself right (not  played with it much). If it works though, please let me know! I could  simply mount the CD/DVD images like we do above and go from there...  Hrm... Mebbe I should give it a whirl myself...

WINE does not do anything virtual or emulate anything, it is simply allowing you to run windows libraries on linux... that being said I also think this would not work. At this point in the game it will not even the setup .exe from a windows 7 disk. So this option will take a lot of tinkering and probably will not be a sound. Simply because I doubt it would properly detect all the different computer hardware I would be using it in. 


> Ok... Not quite but this may be of use to you... Tried using that W98  thingy above, and creating a share of the Win7 DVD (32 bit). The  "setup.exe" on the CD requires a running windows to run.. So will need  to approach from some other angle.. 

Did you try running the setup.exe from inside the sources folder? The setup.exe in the root directory is for upgrades. 

> This method won't work for XP as it needs to reboot and read from the CD  a second time before it continues (and I tried copying i386 elsewhere -  really painful process and as you'll understand don't really want to  sit around nursing an install through each and every little step!), but  maybe we're heading somewhere in the right direction for Vista and 7?

Yes indeed that would suck, but I have been able to install XP via netboot in the past, and 90% of my clients have moved to Windows 7, so I am more concerned with windows 7 right now, then I intend to go back and deal with XP. Also because there are only 4 versions of XP I have no problem creating .WIMS and booting them via FOG. I just dont want to create tons of .WIMS for vista and 7. 

As horrible as this sounds... I think I have a solution, I will recreate the Windows 7 installation process as follows...
1. you netboot a script
2. the script will ask which version of windows you would like to install
3. after selecting version it will copy the contents of sources or i386, depending on which version of windows, to the local drive of your choosing
4. Once copied to the local drive, machine will reboot and load a custom windows setup from the local drive. The install will then complete as usual. 

I believe the above will work very similar to your ghost method, only difference is I should be able to do it with less space and avoiding the issue you were having with the activation timer running out 30 days after image creation. 

Give me a week or so to tinker with this and If I am able to get it to work I will be more then happy to share my ways.

---

### Post by ppatrick on 2013-03-20
Probably not the answer you might expect in an Ubuntu forum but 
you can easily do what you want with **Serva**.

see here
[http://vercot.com/~serva/an/WindowsPXE1.html](http://vercot.com/~serva/an/WindowsPXE1.html)

---

### Post by darkapec on 2013-03-20
> **ppatrick said:**
> Probably not the answer you might expect in an Ubuntu forum but 
you can easily do what you want with **Serva**.

see here
[http://vercot.com/~serva/an/WindowsPXE1.html ]("http://vercot.com/~serva/an/WindowsPXE1.html")

Not a bad option, however I do not want to use a windows machine to do this and I am definitely not interested in setting up a windows server. Due to additional cost and migrating everything over to a virus ridden windows box. However if your suggesting there is a way for me to setup a temporary windows box, make all of my images, then transfer them over to FOG and having my current Linux server handle the images from there? That would be a fantastic and very reasonable solution to this ongoing problem. I am going to look into using Serva images on fog and report back. Thanks for your help ppatrick

---

### Post by ppatrick on 2013-07-17
1) With Serva you do not need an MS Server
2) Fog installs images; Serva is a RIS/WDS alternative that installs MS distributions exactly as RIS and WDS do; no HDD images.

Probably in your case Serva deserves to be run in a VM within your Linux system,
you'll save a lot of time with Serva.

---

