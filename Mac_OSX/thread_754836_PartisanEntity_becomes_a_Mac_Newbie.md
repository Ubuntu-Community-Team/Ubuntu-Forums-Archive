---
title: "PartisanEntity becomes a Mac Newbie"
date: 2008-04-14
forum: Mac OSX
---

### Post by PartisanEntity on 2008-04-14
I received my shiny new MacBook last week and have been using it ever since.

My first impression is a very pleasant one. Visually the operating system is very aesthetic and smooth. The battery times are amazing compared to my old Asus.

I am still trying to get used to the fact that clicking on the x will not quit an application, and that the touchpad only has one button. (As far as the touchpad is concerned, I did set it up for the two-finger-tap solution as well as using my two-button mouse).

I also realised that as an Ubuntu user I have been quite spoilt by the fact that Ubuntu comes with most needed applications pre-installed. Here I was with my MacBook researching office suites, browsers, multi-protocol messengers, etc... reminded me of long gone days.

[LIST]
[*]So my **first** question is: Any tutorials on editing permissions? I would like permissions to be a little tighter, for example, requiring password any time an application is installed (I believe by default only updates require a password).


[*]My **second** question: Firewall? Needed, or like in Ubuntu?


[*]**Third**: Is the MacBook picky concerning what brand of RAM I buy? (I read somewhere something about Apple approved RAM??)
[/LIST]

Thank you and stay tuned for more annoying questions :)

p.s. I am thinking of posting all my questions in this thread for easy reference, as long as it doesn&#8217;t annoy anyone.

---

### Post by shuttleworthwannabe on 2008-04-14
for the Third Q: my reading in forums.notebookreview.com (apple mac osx subforum) is that if you buy from crucial or newegg the compatibility issues are taken care off. Visit the forum and ask Sam, and see what he thinks.

S

---

### Post by wieman01 on 2008-04-14
Shame on you, PE. :-)

And congrats on your new gadget.

---

### Post by PartisanEntity on 2008-04-14
> **wieman01 said:**
> Shame on you, PE. :-)

And congrats on your new gadget.

Hehe, thank you wieman, but in my defence, I had no choice, it was included in the tuition fees of my institute :)

---

### Post by wieman01 on 2008-04-14
> **PartisanEntity said:**
> Hehe, thank you wieman, but in my defence, I had no choice, it was included in the tuition fees of my institute :)
So it was as free as free beer? Good for you! I wouldn't pay a (Euro) cent for a Mac. Haha... Kidding, buddy.

---

### Post by PartisanEntity on 2008-04-14
No way, not free. Part of my tuition fees go towards the price of this MacBook unfortunately.

---

### Post by LaRoza on 2008-04-14
Traitor....

Not all is lost, see my iBook for how to fix Macs.

---

### Post by aysiu on 2008-04-14
> **PartisanEntity said:**
> 
I am still trying to get used to the fact that clicking on the x will not quit an application The way my wife dealt with the first problem was to upgrade her RAM, so she basically just leaves all her frequently used programs running all the time instead of quitting them. I would just make it a regular exercise to press Cmd-Q... think KDE!

> I also realised that as an Ubuntu user I have been quite spoilt by the fact that Ubuntu comes with most needed applications pre-installed. Here I was with my MacBook researching office suites, browsers, multi-protocol messengers, etc... reminded me of long gone days. Don't forget to check out [http://www.opensourcemac.org](http://www.opensourcemac.org)

> 
**Third**: Is the MacBook picky concerning what brand of RAM I buy? (I read somewhere something about Apple approved RAM??) No, not picky at all. Just make sure to get the right specs. NewEgg will be far cheaper than Apple.

---

### Post by Dark Dragoon on 2008-04-14
1) Not a tutorial on editing permissions but maybe this will help. If a program is going to affect all users of the system it should request a password. If you are using the default user account, you may want to create an admin account and change your account to be a standard user, you will then have to enter the admin accounts details if you try to change the programs in the Applications folder, or for anything that affects other users on the system.

2) OS X's firewall settings are located in:-
system preferences > security > firewall
As for whether it's needed, I prefer to have a firewall on my computers.

3) Certain Macs are picky about the type of RAM for example Mac Pros need RAM modules with large heatsinks. As far as I know the MacBook isn't picky about the RAM. I certainly wouldn't buy RAM from Apple, though it's a good idea to buy from a company that guarantees compatibility.

---

### Post by PartisanEntity on 2008-04-14
> **LaRoza said:**
> Traitor....

I promise that Hardy will find a new home, beside OS X, on my MacBook ;)

---

### Post by PartisanEntity on 2008-04-14
> **aysiu said:**
> The way my wife dealt with the first problem was to upgrade her RAM, so she basically just leaves all her frequently used programs running all the time instead of quitting them. I would just make it a regular exercise to press Cmd-Q... think KDE!

I am actually planning on upgrading RAM too, and for that reason as well.

 > **aysiu said:**
> Don't forget to check out [http://www.opensourcemac.org](http://www.opensourcemac.org)

Thanks, been there done that.

> **aysiu said:**
>  No, not picky at all. Just make sure to get the right specs. NewEgg will be far cheaper than Apple.

Good to hear, I saw some offers for RAM here in Vienna, from Crucial or Kingston for about €40/2GB stick, which is not bad.

---

### Post by PartisanEntity on 2008-04-14
> **Dark Dragoon said:**
> 1) Not a tutorial on editing permissions but maybe this will help. If a program is going to affect all users of the system it should request a password. If you are using the default user account, you may want to create an admin account and change your account to be a standard user, you will then have to enter the admin accounts details if you try to change the programs in the Applications folder, or for anything that affects other users on the system.

Thanks for the tip, sounds like a good idea to increase security.

---

### Post by scramasax on 2008-04-15
> **PartisanEntity said:**
> Thanks for the tip, sounds like a good idea to increase security.

It's probably a good idea:

> One should also point out, that if the user privileges are an admin user, it is possible to write to /Applications/ and /Library/, and this access is quite damaging.

[http://daringfireball.net/2007/04/interview_dino_dai_zovi](http://daringfireball.net/2007/04/interview_dino_dai_zovi)

Now if you look in [COLOR="SeaGreen"]/System/Library/CoreServices[/COLOR] (or in [COLOR="SeaGreen"]/usr/bin[/COLOR] for the matter of that -- however, that's hidden in the file browser under OS X (presumably to stop Justin Long types [shooting themselves in the foot](http://digg.com/apple/Man_deletes_usr_blames_Apple_for_his_mistake)) ) you'll see that the UID is root and the GID wheel.  However, everything in [COLOR="SeaGreen"]/Applications[/COLOR] has the group "admin".  It makes for convenience, but it is a little questionable from the P.O.V. of security.

For a brief guide to security see here:

[http://www.macgeekery.com/tips/security/basic_mac_os_x_security](http://www.macgeekery.com/tips/security/basic_mac_os_x_security)

For a comprehensive one, here:

[http://www.nsa.gov/snac/](http://www.nsa.gov/snac/)

---

### Post by PartisanEntity on 2008-04-15
Another question:

Scenario: I have not yet set a region for the built in DVD player, hence every time I insert a DVD to watch, I am greeted by a wizard to help set the region code.

Issue: I do not want to set a region as I use VLC to watch DVD's and VLC doesn't complain about region codes.

How can I tell the wizard to stop showing up and just live with it?

---

### Post by handy on 2008-04-15
> **PartisanEntity said:**
> Another question:

Scenario: I have not yet set a region for the built in DVD player, hence every time I insert a DVD to watch, I am greeted by a wizard to help set the region code.

Issue: I do not want to set a region as I use VLC to watch DVD's and VLC doesn't complain about region codes.

How can I tell the wizard to stop showing up and just live with it?

PE, this site is the best I have found regarding flashing the firmware on Mac optical drives:

***_[http://forum.rpc1.org/viewtopic.php?t=43012&postdays=0&postorder=asc&&start=0&sid=d912bd1729791af5bb0cd2710a976411](http://forum.rpc1.org/viewtopic.php?t=43012&postdays=0&postorder=asc&&start=0&sid=d912bd1729791af5bb0cd2710a976411)_***

[I]**[Edit:]**  You will find that if you use DVD's from different zones that you will need to flash your optical drives ROM, so that it becomes zone less, all the information is at the site I linked to. 

Also, I agree with the following post, (the free) Perian codec pack, includes a huge number of formats that it supports for use with Quicktime, & the free part of Flip4Mac is occasionally useful too.  I too use VLC, but occasionally QT is useful or necessary.
[/I]

---

### Post by Dark Dragoon on 2008-04-15
> **PartisanEntity said:**
> Another question:

Scenario: I have not yet set a region for the built in DVD player, hence every time I insert a DVD to watch, I am greeted by a wizard to help set the region code.

Issue: I do not want to set a region as I use VLC to watch DVD's and VLC doesn't complain about region codes.

How can I tell the wizard to stop showing up and just live with it?
If you go to:-
System Preferences > CD's & DVD's 
And set the "When you insert a video DVD:" option to either be VLC or ignore, does it still ask to set a region?


On a mostly unrelated note, as QuickTime is used be various other programs such as Safari and FrontRow, it's often worth installing a couple of codec packs for it, namely [Perian]("http://perian.org/") and [Flip4Mac]("http://www.flip4mac.com/").

---

### Post by PartisanEntity on 2008-04-17
This is freaking me out, I am in class right now, and someone keeps launching applications for me. I do have security enabled.

What else could it be ?

---

### Post by wieman01 on 2008-04-17
Your alter ego?

---

### Post by PartisanEntity on 2008-04-17
> **wieman01 said:**
> Your alter ego?

pffft that's sleeping right now

But it turns out a friend was playing around with an iRemote, I turned IR off, phew I thought it was more serious that that.

---

### Post by PartisanEntity on 2008-04-23
I just plugged my external storage HDD into my MacBook and realised that my main EXT3 partition did not mount, only my FAT32 partition mounted.

I tried reading through the forum here, but it seems from my understanding that OS X doesn't read from EXT3, only EXT2?

---

### Post by aysiu on 2008-04-23
> **PartisanEntity said:**
> I just plugged my external storage HDD into my MacBook and realised that my main EXT3 partition did not mount, only my FAT32 partition mounted.

I tried reading through the forum here, but it seems from my understanding that OS X doesn't read from EXT3, only EXT2?
It doesn't. And I've tried the plugin for Mac that supposedly gives you read/write capabilities for Ext3, but it didn't work and ended up making my wife's Macbook Pro magically reboot when launched, so I removed it immediately.

---

### Post by PartisanEntity on 2008-04-23
> **aysiu said:**
> It doesn't. And I've tried the plugin for Mac that supposedly gives you read/write capabilities for Ext3, but it didn't work and ended up making my wife's Macbook Pro magically reboot when launched, so I removed it immediately.

Damn this is very annoying. Thanks for the info aysiu.

I guess converting from EXT3 to FAT32 without data loss would be an 'Eier legende Wollmilchsau' as we say in German.

---

### Post by PartisanEntity on 2008-04-25
So in an effort to install Hardy next to Leopard on my MacBook, I first installed REFIT, and then using the Disk Utility on the OSX  CD/DVD, I created a new partition.

I then popped in the Hardy CD, booted to the live desktop and went through the installation. I used the partition I had made earlier to create an area for Hardy and another area for the swap partition.


The install went ahead and completed successfully, I then restarted and at the REFIT window I selected the Linux partition to boot from.

I then however saw a black screen with a message along the lines of "No bootable device found - please insert CD and press any key".

Leopard loads fine, but either REFIT or perhaps BOOT CAMP cannot load Hardy. (Or is it something else?).

Anyone know what I  might have done wrong?

---

### Post by handy on 2008-04-25
> **PartisanEntity said:**
> So in an effort to install Hardy next to Leopard on my MacBook, I first installed REFIT, and then using the Disk Utility on the OSX  CD/DVD, I created a new partition.

I then popped in the Hardy CD, booted to the live desktop and went through the installation. I used the partition I had made earlier to create an area for Hardy and another area for the swap partition.


The install went ahead and completed successfully, I then restarted and at the REFIT window I selected the Linux partition to boot from.

I then however saw a black screen with a message along the lines of "No bootable device found - please insert CD and press any key".

Leopard loads fine, but either REFIT or perhaps BOOT CAMP cannot load Hardy. (Or is it something else?).

Anyone know what I  might have done wrong?

You probably have to synchronize the drives with REFIT I think.  I did long enough ago not to be able to give you the details, but it is not hard to do, & happens very quickly.

Have a look at the [***_REFIT site_***]("http://refit.sourceforge.net/") for the details?

---

### Post by PartisanEntity on 2008-04-25
You are right, all I had to do was resync rEFIt and I was able to log into Hardy. Thanks.

---

### Post by andrewjoy on 2008-04-27
As for question 3 Corsair do mac ram and its quite a good price.

[http://www.scan.co.uk/Products/Products.ASP?CatID=22&FilterCategories=516&Thumbnails=yes](http://www.scan.co.uk/Products/Products.ASP?CatID=22&FilterCategories=516&Thumbnails=yes)

£59 for 4GB not bad at all

---

### Post by PartisanEntity on 2008-04-28
I am trying to use the Disk Utility on the Mac OS X installation CD to create a 10gb FAT partition but I keep getting the error message: 

> mediakit reports no such partition

Anyone know what the problem is?

---

### Post by handy on 2008-04-28
> **PartisanEntity said:**
> I am trying to use the Disk Utility on the Mac OS X installation CD to create a 10gb FAT partition but I keep getting the error message: 

Anyone know what the problem is?

I have very recently used gparted to resize existing & create & move both new & existing partitions on my iMac.  

I how have FAT32, HFS+, EXT3, 2 x JFS & Linux Swap.

I used the gparted on the Ubuntu 7.10 live CD.

I first tried Knoppix, & it's  Qparted, which could not access the iMac's disk, then I tried the Linux System Restore CD, which also could not (or I could not ;-) ) do the job, then I tried the Gutsy liveCD & it worked like magic!

Also, PE, you can use the Mac's Disk Utility from inside of Leopard to resize itself & create new partitions.  I personally prefer not to do it that way.

---

### Post by MONODA on 2008-04-29
what institute is it? Ill be sure not to go there;). Anyway good luck with your partial switch.

---

### Post by PartisanEntity on 2008-04-29
> **handy said:**
> I have very recently used gparted to resize existing & create & move both new & existing partitions on my iMac.  

I how have FAT32, HFS+, EXT3, 2 x JFS & Linux Swap.

I used the gparted on the Ubuntu 7.10 live CD.

I first tried Knoppix, & it's  Qparted, which could not access the iMac's disk, then I tried the Linux System Restore CD, which also could not (or I could not ;-) ) do the job, then I tried the Gutsy liveCD & it worked like magic!

Also, PE, you can use the Mac's Disk Utility from inside of Leopard to resize itself & create new partitions.  I personally prefer not to do it that way.

Hey handy,

So gparted on the Live CD can read and edit hfs+ partitions?

I am asking because I tried two things that did not work when I was installing Hardy on the MacBook:

a) I tried my gparted live cd which didn't load for some reason.

b) The partitioner in the Hardy installation script also could not read the hfs+ partition which is why I was forced to use the Disk Utility to free up some space and then use the Hardy live CD to install Hardy and make the respective partitions for it.

I'll try gparted on the Hardy live cd once I get home, I hope this works as I would really need a shared FAT32 partition to move files easily between Leopard and Hardy.

---

### Post by handy on 2008-04-29
> **PartisanEntity said:**
> Hey handy,

So gparted on the Live CD can read and edit hfs+ partitions?

I am asking because I tried two things that did not work when I was installing Hardy on the MacBook:

a) I tried my gparted live cd which didn't load for some reason.

b) The partitioner in the Hardy installation script also could not read the hfs+ partition which is why I was forced to use the Disk Utility to free up some space and then use the Hardy live CD to install Hardy and make the respective partitions for it.

I'll try gparted on the Hardy live cd once I get home, I hope this works as I would really need a shared FAT32 partition to move files easily between Leopard and Hardy.

Yep, GParted will shrink an HFS+ partition, but it can't make it bigger again (at this stage anyway ;-)).  GParted on LiveCD will solve your problem for sure, I have been doing a LOT with it lately on my iMac, so I'm talking from experience, not books. :-)

Cheers,

handy

---

### Post by PartisanEntity on 2008-04-29
Thanks handy, gparted on the Live CD worked nicely, but I have a new problem, now that I have a FAT32 partition, rEFIt will only give me the option to load Mac OS X or Windows (it thinks the FAT32 partitions is Windows even though it's empty).

Even after resyncing rEFIt it doesn't show Linux as one of the available OS's.

Anyone have any idea why it's doing this ?

---

### Post by PartisanEntity on 2008-04-29
Just to clarify what is happening, screenshot.png shows the current set up, and screenshot-1.png shows what I would like to have. But when I apply the set up from screenshot-1.png then refit removes Linux as an option and offers me to boot either from OSX or from the empty FAT32 partition.

---

### Post by handy on 2008-04-29
I don't know PE?

I had a problem at one stage with rEFIt not wanting to boot Arch, so I reordered my partitions so that they were in numerical order & it worked!

Which is a little bit difficult for you, as you have data in your Linux boot partition & it is number sda4; OS X can only see the first 4 partitions, & the way it works is that you need both the partition with GRUB & your FAT32 shared data partition inside those first 4 (if you had windows it has to be in the first 4 too).

I can't guarantee that reordering your partitions will work, I have not read it anywhere, but it did work for me & I have 6 partitions.

***[Edit:]** PE, I am creating a post on the Arch forum which is gradually building up details with regards to installing Arch on my iMac.  You may find some of it interesting?  The link follows, it is **Post 5**:* 

***_[http://bbs.archlinux.org/viewtopic.php?id=35355](http://bbs.archlinux.org/viewtopic.php?id=35355)_***

---

### Post by PartisanEntity on 2008-05-01
Thanks very much for the info handy, to be quite honest I still don't understand the theory behind it :)

---

### Post by handy on 2008-05-02
> **PartisanEntity said:**
> Thanks very much for the info handy, to be quite honest I still don't understand the theory behind it :)

Apple are now using the new [***_GUID partition table, or GPT_***]("http://developer.apple.com/technotes/tn2006/tn2166.html").  The document I linked to does not go into the fact that Apple has chosen to limit the number of partitions that can be booted from or that OS X can see to 4 on the internal drive.  Though in useful reality it is only 3, due to the existence of the EFI system partition (ESP) which is only 200Mb in size & is not used for anything at the moment. That said, we should not remove the ESP as it is not really a FAT32 file system & we could have quite some difficulty replacing it if in the future Apple requires its existence for whatever reason.  

So with OS X on 1 of these 3 partitions, we are left with only 2 partitions that we can either boot from e.g. Windows & Ubuntu on either/both sda3 & sda4, or alternately, 2 partitions that we can use in a fashion such as the following: Ubuntu & it's boot loader GRUB on sda3, & sda4 being a FAT32 partition that is mutually accessible by both OS X & Ubuntu.

As a further example, it would be possible to have a FAT32 partition on sda3, & a Linux or BSD based OS on partition sda4 which had GRUB on it, which was also operating as the boot-loader for other Linux or BSD based OS's on partitions sda5 & sda6 which OS X can't see, even though all of these OS's can access the FAT32 partition sda3 to share data. 

Any swap partitions would also be set to be outside of the the first 4 crucial partitions.  I don't remember what the limit is on the number of partitions that it is possible to install on the internal OS X drive.

As far as rEFIt & ordering the partitions numerically is concerned, I don't understand it either.  It may not be the reality of the situation I experienced.  Though my Arch installed drive never changed from being sda3, so I don't know how it could have possibly interfered with GRUB, & it would not boot until after I rearranged the drives in numerical sequence?

Maybe I will take it up with the rEFIt developer one day?  :-)

---

