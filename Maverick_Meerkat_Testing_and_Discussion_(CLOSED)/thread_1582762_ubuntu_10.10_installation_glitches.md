---
title: "ubuntu 10.10 installation glitches"
date: 2010-09-26
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by doctorstupidmd on 2010-09-26
I have been running 10.04 successfully for a very long time.  When i decided to update to the beta 10.10 via the update manager, upon restarting the new version, there was only a terminal interface with which i could login.  the old version of the kernel was still in gurb, i believe the headers were deleted during the update... so it wasnt working either.  i had to reinstall windows and 10.04 over it, which was very frustrating.  

       Ill probably be sticking with 10.04 for a while, unless there is an explination for this? i havent read anything, and i didnt see it in the known issues box.  does anyone have any solutions how i could do it safely? i think it is a graphics card issue, as when i started the new OS with limitations, it booted successfully, but there was virtually nothing running correctly

---

### Post by Sef on 2010-09-27
Moved to MMTnD.

---

### Post by mörgæs on 2010-09-27
Can you do a clean install of 10.10?

---

### Post by TonKi on 2010-09-27
Try removing the xorg.conf

Login and 
sudo rm /etc/X11/xorg.conf
reboot

---

### Post by andrewabc on 2010-09-27
Another thread was made where someone updated, and it was using old kernel and stuff, and still thought it was 9.10.

[10.10 thinks it's 9.10..... ](http://ubuntuforums.org/showthread.php?t=1578787)

Anything in this thread sound familiar to your problem?

---

### Post by doctorstupidmd on 2010-09-27
thanks guys, 

  actually when i tried to format the drive and install 10.10 freshly, the installation kept getting stuck at about 80% (estimating) it would say "ready when you are" in the output line. very bizarre.  it would get stuck there for hours so eventually i gave up cause i needed some kind of OS.  
 

tonKi, would i enter that into the terminal of 10.04 that im running right now before i upgrade, or would i enter it into the command interface i get when 10.10 was booting? (like i said i could successfully log in with it, i just got the "user@domain: " prompt   sorry if thats a noob question haha

andrewabc, yeah i think tonKi has something, the problem you brought up might be related, but with different symptoms.  

maybe i should just wait for the actual release, there a billion damn threads about similar issues with nvidia cards... any clue as to if the release will support an nvidia GM 8600?

---

### Post by efflandt on 2010-09-27
When you said "i had to reinstall windows and 10.04 over it, which was very frustrating." does that mean that you were trying to upgrade a Wubi install within Windows (not sure if that is sorted out)?  Although, you later said you tried to format the drive and install 10.10 freshly.

I guess the first question would be can you successfully boot 10.10 beta CD to a live system?  If that works at least the default nouveau video should work.

If you were using proprietary nvidia drivers before you tried to upgrade, not sure how that shakes out, especially if manually installed instead of a regular Ubuntu package.  In 10.04 my GT220 video was using nvidia v195.something, and in 10.10 beta (just downloaded/fresh installed Saturday) it is v256.53 (both activated from Hardware Drivers).

---

### Post by doctorstupidmd on 2010-09-27
i installed windows as a whole and then partitioned it half and half. (no wubi).  im not 100% sure i was able to load 1010 from cd.. there were a bunch of things i tried.  if i remember correctly it did boot from cd, but when i tried to install it from the icon on the desktop, it once again froze during install.  

i suppose i can try booting 10.10 from cd right now to make sure

---

### Post by doctorstupidmd on 2010-09-27
yeah.. i just successfully booted from cd with 10.10.... the graphics where working to some extent.  it informed me that restricted drivers were available for the video card (it did so on 10.04 and worked fine) but this time it wouldnt let me install them.  why do the graphics work now.. but not if i do a fuil upgrade?

---

### Post by kansasnoob on 2010-09-27
Well, in most situations you should never have to reinstall Windows because an Ubuntu upgrade failed, but before commenting much further I should know if you're using Wubi or performing an actual dual-boot?

With or without Windows I always like to multi-boot with at least one stable Linux/Debian based OS on my machine.

I tend to carry things to an extreme because I do a lot of strange testing:

> lance@lance-desktop:~$ sudo blkid
[sudo] password for lance: 
/dev/sda1: LABEL="Maverick" UUID="b7a0df33-53e4-4f0d-856b-0da92ff0d743" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: LABEL="Karmic" UUID="1332b9d0-cf18-4299-9094-12acbdac91ad" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: LABEL="Lucid" UUID="d252929b-949d-432e-a18c-18f9ae770d28" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: LABEL="Backups" UUID="594c3d40-2791-4c0a-8644-d9812545da2d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: LABEL="Pictures" UUID="8a3f6c83-cb52-4caf-96b8-5faf2c830453" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: LABEL="Downloads" UUID="05289ee4-d681-4806-b6fd-aefd784f9323" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: LABEL="Documents" UUID="571cfad8-68c7-4703-883e-c0baa2a381d4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda9: UUID="80627269-1ccd-4774-b4ea-a5ef8824ffaa" TYPE="swap" 
/dev/sda10: LABEL="Isadora" UUID="f223fe5d-3acb-4d96-950c-62661ad8714b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda11: LABEL="Squeeze" UUID="0eec2831-7805-437e-a06e-e18ab3268e6a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda12: LABEL="Pure Gnome" UUID="f6062e12-09f1-4f19-b6c2-ad58812d6794" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda13: LABEL="Peppermint" UUID="720d719e-e571-4bdd-aac9-718f0ffe2266" TYPE="ext4" 
/dev/sda14: LABEL="LL to MM test" UUID="c703501f-1f50-465f-8eb7-9f20cbd3485a" TYPE="ext4" 
/dev/sda15: LABEL="LMDE" UUID="22eefad4-870e-4191-87c9-57f4e756411d" TYPE="ext4" 
/dev/sda16: LABEL="vacant" UUID="ed84364c-7f7d-4492-8275-eed0c88b1e3b" TYPE="ext2" 
/dev/sda17: LABEL="vacant" UUID="850462c4-a56d-458f-8316-8174e6bc5230" TYPE="ext2" 
/dev/sdb1: LABEL="Maverick Test" UUID="3f034d3f-00f4-437c-9514-febbcd52c407" TYPE="ext4" 
/dev/sdb5: UUID="5a66ab05-104c-4625-9429-6d143d2519b6" TYPE="swap" 


That would be major overkill for most people, but first of all describe your installation. An easy way to do so would be to post the output of the Boot Info Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I personally think that Wubi installs should default to only allowing security updates.

I'd never try a distro-upgrade in Wubi, but that's just my opinion :)

---

### Post by kansasnoob on 2010-09-27
> **doctorstupidmd said:**
> i installed windows as a whole and then partitioned it half and half. (no wubi).  im not 100% sure i was able to load 1010 from cd.. there were a bunch of things i tried.  if i remember correctly it did boot from cd, but when i tried to install it from the icon on the desktop, it once again froze during install.  

i suppose i can try booting 10.10 from cd right now to make sure

Sorry, I'd begun my reply before you'd posted that :(

I need to run some errands but I'll be back.

---

### Post by doctorstupidmd on 2010-09-27
well because all i had on my system.. (there was no more grub) was a command interface i thought it was best to reinstall windows so i could make a cd with ubuntu on it, as i had none.  there may have been a way to fix it, but im really busy with schoolwork and panicked when i didnt have anything that would boot well. 

       as of right now i have 10.04 working perfectly installed on a partition. its about 50-50 with win 7.  im convinced its a graphics issue based on what ive gotten and many other threads.  i can wait for the stable release if necessary, 10.10 isnt all that different, i was just looking forward to the faster boot time haha

---

### Post by kansasnoob on 2010-09-27
Since you're not using Wubi (good move IMHO) the first thing you should know is that every drive has a four "4" primary partition limit. This means you must create the 4th partition as an "Extended" partition.

An extended partition can contain many logical partitions, it varies between IDE and SATA drives, and I don't quite understand the limits, but you'd be unlikely to meet those limits :)

The second thing to consider is how many partitions Windows is using by default. Typically for XP it's only one, for Vista still one, for Win7 probably two. But if it's a "branded" disc all bets are off!

Just boot your Ubuntu disc and while you're making sure it works as a Live CD/DVD check out Gparted/Partition Editor in System > Administration. **Remember you're only looking!**

While it's fine to resize XP with Gparted I personally would NEVER resize Vista or Win7 with anything but it's own tools! I'm very serious about that!

Gparted provides a really good visual of what you have:

[ATTACH]170651[/ATTACH]

While the sizes there are odd compared to what you'd see with a Windows/Ubuntu multi-boot you can see that I have three primaries and one extended w/many logical partitions.

There are a gazillion ways to set that up! The next time I set mine up I'll do it differently! When you test you learn, as you learn you find better ways, more better ways, and still better ways to do things :)

And sometimes you try things that are just plain stupid :(

I've tried many things that ended up being beyond stupid :redface:

But for a long time what I did was create a separate "/home" partition so if an upgrade hosed things I could reinstall using "manual/advanced partitioning" and choosing to only format "/" while choosing to "use" "/home" w/o formatting it.

Later I decided to start testing the newer releases so I'd create something like:

Windows>-<Hardy/>-<Hardy/home>-<Intrepid/>-<Intrepid/home>-<SWAP

Does any of this make sense at all?

This guide helped me a lot:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

I hope I'm not just creating more confusion :)

---

### Post by kansasnoob on 2010-09-27
> **doctorstupidmd said:**
> well because all i had on my system.. (there was no more grub) was a command interface i thought it was best to reinstall windows so i could make a cd with ubuntu on it, as i had none.  there may have been a way to fix it, but im really busy with schoolwork and panicked when i didnt have anything that would boot well. 

       as of right now i have 10.04 working perfectly installed on a partition. its about 50-50 with win 7.  im convinced its a graphics issue based on what ive gotten and many other threads.  i can wait for the stable release if necessary, 10.10 isnt all that different, i was just looking forward to the faster boot time haha

OK, regarding grub and/or restoring Windows boot. It's easy peasy!

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

But if you have no Windows disc I've written a bit about that, I also prefer using a "limited" chroot to determine the version of, and restore grub:

[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

This summer has been a real bear for me but hopefully in the next few months I'll be able to rewrite that so it makes more sense.

There is an ongoing graphics issue with Maverick:

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/640807](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/640807)

Remember what it says at the top of this page:

**Ubuntu Maverick Meerkat is in development, use only for testing purposes!!!**

---

### Post by doctorstupidmd on 2010-09-28
thanks for all your help everybody, i think im just going to wait untill it actually comes out, and maybe even some time after that, to make sure they fix the graphics issues

---

