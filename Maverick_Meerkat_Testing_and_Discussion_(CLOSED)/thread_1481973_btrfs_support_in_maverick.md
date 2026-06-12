---
title: "btrfs support in maverick?"
date: 2010-05-13
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by pulpo69 on 2010-05-13
any idea if there will be full btrfs support in maverick?

---

### Post by plun on 2010-05-13
Phoronix article about this including facts from ongoing UDS

[http://www.phoronix.com/scan.php?page=news_item&px=ODI0NA](http://www.phoronix.com/scan.php?page=news_item&px=ODI0NA)

---

### Post by pulpo69 on 2010-05-13
thanks plun for the link. i hoped btrfs support to see in maverick.

---

### Post by Starks on 2010-05-13
"Everyone knows it's Butters!"

"That's me!"

---

### Post by Dayofswords on 2010-05-13
> **Starks said:**
> "Everyone knows it's Butters!"

"That's me!"

"I like Hello Kitty Island Adventure a lot more than this stuff."

---

### Post by taavikko on 2010-05-13
Too bad if they wait until 2012 or something to finally include btrfs.

I'm really eager to make the switch from ext4 to btrfs.

Theodore Tso also stated that btrfs is the future.

---

### Post by renkinjutsu on 2010-05-13
icantbelieveitsnotbtr :)

---

### Post by Eclipse. on 2010-05-13
Btrfs is nowhere near ready yet for the masses, its not even feature filled yet.

The Phoronix article is a load of rubbish.

For maverick = installer and bootloader support.
Next LTS = btrfs will be stable, tools for using it will be ready and btrfs will be the default filesystem.

---

### Post by Longinus00 on 2010-05-13
I don't understand what the big problem people have with btrfs support is. If you can't get btrfs up and running in lucid then maybe you shouldn't be playing around with it in the first place.

---

### Post by Eclipse. on 2010-05-13
> **Longinus00 said:**
> I don't understand what the big problem people have with btrfs support is. If you can't get btrfs up and running in lucid then maybe you shouldn't be playing around with it in the first place.

This has always been my thoughts as well for anything like this, there was a guide however for lucid during the development cycle.

---

### Post by xebian on 2010-05-13
Exactly.  btrfs is already supported in lucid

```

/lib/modules/2.6.32-22-generic/kernel/fs/btrfs
/lib/modules/2.6.32-22-generic/kernel/fs/btrfs/btrfs.ko
/lib/modules/2.6.34-020634rc7-generic/kernel/fs/btrfs
/lib/modules/2.6.34-020634rc7-generic/kernel/fs/btrfs/btrfs.ko
```

---

### Post by MacUntu on 2010-05-13
If MeeGo can go "btrfs by default" so can Ubuntu! :D

---

### Post by Eclipse. on 2010-05-14
> **MacUntu said:**
> If MeeGo can go "btrfs by default" so can Ubuntu! :D

I read the mailing list thread last night and I was quite shocked. This suggests that meego is not going to be shipping for a while.

---

### Post by Longinus00 on 2010-05-14
> **Eclipse. said:**
> This has always been my thoughts as well for anything like this, there was a guide however for lucid during the development cycle.

No guide is necessary. Just install btrfs-tools then mkfs and mount like you normally would. You only need a guide if you're trying to test out the btrfs specific features or want to get debugging info when somethings breaks.

---

### Post by ibuclaw on 2010-05-14
> **renkinjutsu said:**
> icantbelieveitsnot
icantbelieveitsnot
icantbelieveitsnot
icantbelieveit**snot**btr :)
Fixed that for you. ;)


Three interesting links to follow:
Btrfs Guide: [http://ubuntuforums.org/showthread.php?t=1389279](http://ubuntuforums.org/showthread.php?t=1389279)
Btrfs Bug #450260: [https://bugs.launchpad.net/bugs/450260](https://bugs.launchpad.net/bugs/450260)
Btrfs Bug #551055: [https://bugs.launchpad.net/bugs/551055](https://bugs.launchpad.net/bugs/551055)


I am in the middle of revising my guide, am yet to test whether or not Bug #450260 is fixed (as claimed by Vlad) - so if anyone wants to check / test, please fire away. :)

Regards

---

### Post by Slug71 on 2010-05-14
I really hope we get installer/grub support in 10.10. Just put it at the bottom of the filesystem list and mark it as 'Experimental'.
Pleeaassee?

---

### Post by gnomeuser on 2010-05-14
apparently we can port the existing grub1 patch to grub2, however that won't buy us full btrfs support. This naturally is caused by inferior designs in GNU Grub2 which doesn't support the options btrfs needs. 

So it might be a worthwhile community project to do this port and get experimental support in Maverick. I would like to see Canonical do it eventually but for now I think the basics would make a good project for the community.

I'll sign up to help get that work done. Anyone else interested in working on getting the foundation laid?

---

### Post by plun on 2010-05-14
**btrfs by default in Maverick?**

Scott James Remnant blog

[http://www.netsplit.com/2010/05/14/btrfs-by-default-in-maverick/](http://www.netsplit.com/2010/05/14/btrfs-by-default-in-maverick/)

---

### Post by MacUntu on 2010-05-14
> **keybuk said:**
> Hitler was easier to work with than tytso

ROFL, a bit mean. :D

---

### Post by Eclipse. on 2010-05-14
> **Longinus00 said:**
> No guide is necessary. Just install btrfs-tools then mkfs and mount like you normally would. You only need a guide if you're trying to test out the btrfs specific features or want to get debugging info when somethings breaks.

Without being cheeky, good luck with that.

Try it and see if your system boots.


> **plun said:**
> **btrfs by default in Maverick?**

Scott James Remnant blog

[http://www.netsplit.com/2010/05/14/btrfs-by-default-in-maverick/](http://www.netsplit.com/2010/05/14/btrfs-by-default-in-maverick/)

Thanks for that plun, just shows how much crap the phronix article was suggesting like I said earlier.

---

### Post by eyelessfade on 2010-05-14
And now it has hit [slashdot]("http://linux.slashdot.org/article.pl?sid=10/05/14/2055257")

---

### Post by Longinus00 on 2010-05-14
> **Eclipse. said:**
> Without being cheeky, good luck with that.

Try it and see if your system boots.

I'm running btrfs fine. Did anybody say anything about booting btrfs, and even better, what do you gain by booting to btrfs?

---

### Post by eyelessfade on 2010-05-15
> **Longinus00 said:**
> I'm running btrfs fine. Did anybody say anything about booting btrfs, and even better, what do you gain by booting to btrfs?
you can have Slash "/" in btrfs?

I'm not worried about running btrfs fine, I'm worried about data loss. I have no problem with having my system on an experimental file system if there is a clear advantage to it. But my data will have to live on a stable and reliable FS. What would happens if MM change to btrfs, and 3 months after they find out you can lose all data in certain situations? And lets say 1000 newbie people does just that. Every paper this side of Saturn will write about how terrible Linux is.

---

### Post by Slug71 on 2010-05-15
> **plun said:**
> **btrfs by default in Maverick?**

Scott James Remnant blog

[http://www.netsplit.com/2010/05/14/btrfs-by-default-in-maverick/](http://www.netsplit.com/2010/05/14/btrfs-by-default-in-maverick/)

Thanks plun, me likey:P

Just as an option would be fine with me.

---

### Post by ibuclaw on 2010-05-15
> **gnomeuser said:**
> apparently we can port the existing grub1 patch to grub2, however that won't buy us full btrfs support. This naturally is caused by inferior designs in GNU Grub2 which doesn't support the options btrfs needs. 

So it might be a worthwhile community project to do this port and get experimental support in Maverick. I would like to see Canonical do it eventually but for now I think the basics would make a good project for the community.

I'll sign up to help get that work done. Anyone else interested in working on getting the foundation laid?

I wouldn't mind helping you doing that, I have a few things to do first though...

---

### Post by moviemaniac on 2010-05-15
> **plun said:**
> **btrfs by default in Maverick?**

Scott James Remnant blog

[http://www.netsplit.com/2010/05/14/btrfs-by-default-in-maverick/](http://www.netsplit.com/2010/05/14/btrfs-by-default-in-maverick/)
Wait a minute, are we talking about the same BTRFS here? 

Last time I looked people had all sorts of problems getting btrfs to report the right figures for available/occupied disk space and now it's a (slight) possibility this might be the defauls FS?
BTRFS won't be production-ready for years to come and at least for me it is a total waste of time - in the time BTRFS took to get where it is today we've seen much smaller teams roll out various usable and stable file systems. 
Most of BTRFS' features are nearly useless in most everyday scenarios (why spend time on stuff like RAID? RAID is either handled by hardware or by the kernel. We don't need support for it build into the FS - waste of time!) Don't even get me started on limited amounts of hardlinks in a directory (braindead) or SSD optimizations (that's the job of the friggin' controller!).
For me BTRFS suffers from acute featuritis and will still be in development for a long, long time before "really" being usable - we'll see 10 other complete filesystems until that day will come.
Oh, and by "usable" I don't mean geeks who know how to repair their FS when it breaks and I don't mean the average home user - I mean usable as in reliable for years in large datacenters. Just for comparison: I still don't consider EXT4 usable for critical environments - I've seen too many failures. I'm (and so is a buddy of mine who manages large servers and deploys servers for many organizations) still on Reiser3 for my / as it has proven most reliable in all kinds of faults - people pulling plugs or dropping buckets of water nearby servers, power failures and other stuff like that. I've seen XFS, Ext2/3/4 BTRFS and others completely fail in these kinds of situations but have never been let down by Reiser3 which has proven to me to be the most robust FS to date. Speed and new features are one thing - utmost reliability another. I vote for reliability every single time. BTRFS is still years away from being reliable when reading about all the "funny" (for non-affected folk) issues people are having on linux-btrfs.

---

### Post by gnomeuser on 2010-05-15
> **ibuclaw said:**
> I wouldn't mind helping you doing that, I have a few things to do first though...

Actually now it seems that Canonical will be pouring effort into doing this. I doubt it is worth duplicating the effort.

---

### Post by ibuclaw on 2010-05-15
> **gnomeuser said:**
> Actually now it seems that Canonical will be pouring effort into doing this. I doubt it is worth duplicating the effort.

It need not be duplicating, merely helping it move faster. ;)

Do you know which entrance they'll take?
Are they looking to fix grub2's flawed stat() detection, or fix btrfs and the lack of forking out stat()-able device nodes in /dev?

---

### Post by gnomeuser on 2010-05-15
> **ibuclaw said:**
> It need not be duplicating, merely helping it move faster. ;)

Do you know which entrance they'll take?
Are they looking to fix grub2's flawed stat() detection, or fix btrfs and the lack of forking out stat()-able device nodes in /dev?

Fixing Grub is rarely an option, messing with the kernel source is never a good idea without upstreams cooperation and device trees, well they are always known for harmlessness and ease. Sounds like mountains of fun.

My gut says that the grub2 path has least risk, though I am unaware of the actual state of the Grub2 codebase.

---

### Post by seeker5528 on 2010-05-15
> **moviemaniac said:**
> Last time I looked people had all sorts of problems getting btrfs to report the right figures for available/occupied disk space and now it's a (slight) possibility this might be the defauls FS?

I thought that was a bit odd myself.

I could be wrong, but after reading a few different things, it's my interpretation that in the context default doesn't mean it will be *the* default file system on a new install. I think what was intended was that if everything falls into place, the BTRFS devs are happy, the Ubuntu devs are happy, then the stock Maverick install disk would include the option to choose BTRFS for your root file system during the installation.

Later, Seeker

---

### Post by moviemaniac on 2010-05-15
> **seeker5528 said:**
> I thought that was a bit odd myself.

I could be wrong, but after reading a few different things, it's my interpretation that in the context default doesn't mean it will be *the* default file system on a new install. I think what was intended was that if everything falls into place, the BTRFS devs are happy, the Ubuntu devs are happy, then the stock Maverick install disk would include the option to choose BTRFS for your root file system during the installation.

Later, Seeker
Hmmm... the way I read it is that BTRFS *could* become the default FS for 10.10?

See the mentioned blog post: [http://www.netsplit.com/2010/05/14/btrfs-by-default-in-maverick/](http://www.netsplit.com/2010/05/14/btrfs-by-default-in-maverick/)

However I am very positive BTRFS will - if it achieves points 1 and 2 - fail to pass point 3 - there are too many bugs in it right now for it to go through the alpha stage "smoothly".
Don't get me wrong: I'd love to see BTRFS progress into being "the" next FS for linux but with all the work going into stuff nobody (really) needs it's very, very hard to get this FS stable and production-ready not at least because of all the myriads of features which make testing even harder and bugs likelier.

---

### Post by seeker5528 on 2010-05-15
> **moviemaniac said:**
> Hmmm... the way I read it is that BTRFS *could* become the default FS for 10.10?

See the mentioned blog post: [http://www.netsplit.com/2010/05/14/btrfs-by-default-in-maverick/](http://www.netsplit.com/2010/05/14/btrfs-by-default-in-maverick/)

Maybe what they said is exactly as they meant it.

But still he didn't sound too optimistic that it would actually happen...

> I&#8217;d give it a 1-in-5 chance.

Later, Seeker

---

### Post by xebian on 2010-05-15
What exactly are they trying to achieve with it other than being the first offering as default?

Oracle could  not even make it as a default in their Oracle Unbreakable Linux.  Considering btrfs is Oracle's baby, and having more devs on it, what's the chance Canonical has better results?

Btrfs is more suited for demanding enterprise solutions than for a good number of Ubuntu home users imho.

Plymouth is not even that smooth at all.

---

### Post by xebian on 2010-05-15
> **seeker5528 said:**
> Maybe what they said is exactly as they meant it.

But still he didn't sound too optimistic that it would actually happen...



Later, Seeker

Now that I read the links, I think it's more for a good chuckle or laugh to end the UDS.

---

### Post by Slug71 on 2010-05-15
> **xebian said:**
> 

Plymouth is not even that smooth at all.


Blame the video drivers, not Plymouth.

---

### Post by ranch hand on 2010-05-15
> **Slug71 said:**
> Blame the video drivers, not Plymouth.
I have to disagree with you on that.

The way I have plymouth set up the video drivers should have nothing to do with it.  There is no splash although there is text.

I have three nearly identical installs on the same exact hardware as they are all on one drive.  The boot speed is improving.  Depending on the OS it ranges from 25 to 45 seconds and is very consistent.

Shut down is another thing all together.  This has improved too.  It is now running at just under a minute for 2 installs and under 1.25 minutes for the other.

I seriously doubt the video driver has anything to do with telling me that "all system shut down in under 2 seconds" and then proceeding to spend another minute shutting down the file system(s).

Shut down, on the same drive in 9.10 takes under 20 seconds, 9.04 under 25 seconds. 

The main difference is plymouth on 10.10, which is where the "fast" speeds are.  10.04 still struggles to boot in less than 1.25 minutes and I usually have to Alt+Sysreq+b to shut down.  Sometimes not but it takes almost 3 minutes at those times.

I think that libplymouth2 is just bad at its very foundation.  Lets hook some strange new FS to it.  I bet that will help a whole lot.

---

### Post by ranch hand on 2010-05-15
I shut down right after my last post and switched to my main drive and 9.04.  This does include going to bios to turn this drive on.

The time is silly.  More than half was getting out of 10.10.  Thank the gods it was not 10.04.

This speed problem, by the way started exactly when plymouth was introduced in 10.04-testing.  Before that the shut down was really instantanious and my boot speeds were flirting with 20 seconds.

---

### Post by ibuclaw on 2010-05-16
> **ranch hand said:**
> I shut down right after my last post and switched to my main drive and 9.04.  This does include going to bios to turn this drive on.

The time is silly.  More than half was getting out of 10.10.  Thank the gods it was not 10.04.

This speed problem, by the way started exactly when plymouth was introduced in 10.04-testing.  Before that the shut down was really instantanious and my boot speeds were flirting with 20 seconds.

Which actually reminds me of two more problems with btrfs in Ubuntu.

1) Ubuntu's fast shutdown process can leave btrfs in a broken state - I think remounting all devices as read-only before poweroff fixes the problem at the cost of latency.
2) Something is up with btrfs file allocation/retrieval that causes gconf to mysteriously have keys go missing after upgrades of their packages. As far as I know, this only happens in dpkg. Other distributions have not reported this issue ... yet.

---

### Post by MacUntu on 2010-05-16
I guess a VM installation isn't suitable for testing such things?

> **ibuclaw said:**
> Ubuntu's fast shutdown process can leave btrfs in a broken state

I noted that when you do a shutdown via the console it triggers a bug in Thunderbird (fails to save a setting), whereas shutting down via the session applet works just fine.

Might this be connected?

---

### Post by gnomeuser on 2010-05-16
> **ibuclaw said:**
> Which actually reminds me of two more problems with btrfs in Ubuntu.

1) Ubuntu's fast shutdown process can leave btrfs in a broken state - I think remounting all devices as read-only before poweroff fixes the problem at the cost of latency.
2) Something is up with btrfs file allocation/retrieval that causes gconf to mysteriously have keys go missing after upgrades of their packages. As far as I know, this only happens in dpkg. Other distributions have not reported this issue ... yet.

I ran fedora on btrfs for a couple of months back in the 11 era, I never saw the last one. However it may be a new problem, I am sure that the nice btrfs people will help investigate. With the interest in btrfs from meego and other players it would serve them well to have a good opt in test case such as Ubuntu to shape up the safe operating conditions.

---

### Post by ibuclaw on 2010-05-16
> **gnomeuser said:**
> I ran fedora on btrfs for a couple of months back in the 11 era, I never saw the last one. However it may be a new problem, I am sure that the nice btrfs people will help investigate. With the interest in btrfs from meego and other players it would serve them well to have a good opt in test case such as Ubuntu to shape up the safe operating conditions.

It's most noticeable when GNOME theming goes missing / reverts back to the ugly gnome defaults.

I only came to realise it manifested in gconf itself when I ran into [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/542883](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/542883)

See the screenshot especially.

As a workaround, I think running:
```
sudo update-gconf-defaults
```
or
```
sudo gconf-schemas --register-all
```
Resolves it.

I will have to get a btrfs installation up and running again soon...


Jdong actually managed to capture this in a snapshot, and compared the working and failing gconf directories. diff reported that there was no difference between the two.

---

### Post by MacUntu on 2010-05-16
I'm now running a btrfs system in a VM. Ureadahead doesn't like btrfs, but at least it doesn't seem to slow down the boot process. :)

---

### Post by gnomeuser on 2010-05-16
> **ibuclaw said:**
> 

Jdong actually managed to capture this in a snapshot, and compared the working and failing gconf directories. diff reported that there was no difference between the two.

Now that is fun, I have never seen that on Fedora that I can remember. But boy is that odd.

---

### Post by Slug71 on 2010-05-31
So far an A2 target. :P

[https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-btrfs-support](https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-btrfs-support)

---

### Post by Longinus00 on 2010-05-31
btrfsck currently doesn't actually fix errors. Is that important to people?

---

### Post by kansasnoob on 2010-05-31
All things considered it's a definite maybe :guitar:

---

### Post by kansasnoob on 2010-05-31
How many people had trouble with ext4?

Every time I try ext4 I end up with some sort of trouble, that is actual data loss.

Ext3 works flawlessly for me:)

Newer is not always better.

---

### Post by ranch hand on 2010-05-31
I installed 9.04 on ext4 and have used it since that time on anything that will take it.  I like it much better than ext3 and have had no trouble with it at all.

I have heard about data loss but not from a creditable source before.  I will now have to be on the look out for this to crop up.

---

### Post by Starks on 2010-05-31
I may reformat my home partition as ext3. Extent-less ext4 isn't providing me with the backwards compatibility I was hoping for. Yes, I can get such a partition to read on Windows, but I have to fsck from a live-usb before using Linux again.

---

### Post by ibuclaw on 2010-05-31
> **Longinus00 said:**
> btrfsck currently doesn't actually fix errors. Is that important to people?

Not really... but Btrfs stores checksums of all data by default. And will print a message in the kernel log if a file you are trying to access doesn't match the said checksum (the file has become corrupt).

Because of this, I have comfort in knowing that if something does happen, I'll know before it can strike hard. ;)

---

### Post by gnomeuser on 2010-06-01
> **Longinus00 said:**
> btrfsck currently doesn't actually fix errors. Is that important to people?

Well that is important naturally, however not critically so, once we have to run fsck to recover we generally failed anyways and recovery is far from a certainty anyways.

I am not sure we would like to ship without it but it could be done if needed. We can always add the functionality in an update as it becomes available. It would hinder using btrfs by default though I would think if we were forced to pick that path.

Important yes, but I care more about btrfs being carefully written and tested so to not need it. We have a good few months to ensure this via larger scale testing following Alpha 2 provided we make every milestone on the way there. 

Come release day I am feeling very good about btrfs being in a good shape and so are others, my netbook e.g. runs MeeGo 1.0 which defaults directly to btrfs and it is not a problem at all so far.

---

### Post by ibuclaw on 2010-06-01
Well, I've had to upgrade my system from Karmic to Lucid after hitting a showstopping seg fault in qemu's sparc emulator. :)

Being a stable btrfs system (I use it mostly for playing games) - it wasn't without it's errors.

udev left itself in an unconfigured state which borked the do-release-upgrade process. :D

Word of advice - if you are stuck in a tty, and need to connect to your wireless WPA router

Remember 3 key commands:
```

  wpa_passphrase "MY SSID" topsecret_password > /etc/wpa_supplicant.conf
wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf & disown
dhclient & disown

```
Note the space indentation for "wpa_passphrase", that prevents it being written to the .bash_history log.

Wonder how long till I switch it to Maverick ...

---

### Post by MacUntu on 2010-06-01
Note: if the network-manager is running, you need to stop it first (in Lucid that's 'sudo stop network-manager'), else your system will go haywire. :D

---

### Post by H3g3m0n on 2010-06-25
Worth watching here: [https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-btrfs-support](https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-btrfs-support)

Hopefully when alpha3 is out, the Grub2 changes can be backported to 10.04 so I can start using it (actually I already have it running on my server, but only on storage partitions).

Right now I just can't be bothered with screwing around to the extent required to get my fs booting from it (if I had enough time and could be bothered to do all that kind of stuff I would be on something like Arch, where it's all tweakable).

Also having a 2ndary partition just for /boot kind of defeats the point of it in my mind, that kind of thing should be what subvolumes is for (not to mention I hate resizing/moving partitions, I have had 2x 300gb drives loose everything doing that, nothing majority important but still annoying, having backups wasn't feasible back then since if I had more drives, I would have more stuff on them, although now I'm on 1 and 2TB drive and have over a TB free on the 2TB to copy the entire drives across, but copying a whole TB worth of data is time consuming.).

As to the missing features, they don't matter provided the current implementation does at least as much as the current filesystem. The basic filesystem structure has been locked in. New features will be added later.

I doubt we will see it by default in 10.10 but it would be nice as a secondary choice that works without needing a bunch of tweaks.

---

### Post by The Cog on 2010-06-25
> **ranch hand said:**
> I installed 9.04 on ext4 and have used it since that time on anything that will take it.  I like it much better than ext3 and have had no trouble with it at all.

I have heard about data loss but not from a creditable source before.  I will now have to be on the look out for this to crop up.

I suppose you have no reason to think me creditable, but I claim 7 fatal filesystem corruptions out of 7 installs with ext4. Four installs were Jaunty, and after they crashed I reinstalled to jfs, no problems since. Six months later, three installs of Karmic. After they crashed I reinstalled to jfs, no problems since.

The shortest install lasted less than an hour. Immediately after installing, I copied /opt (containing two copies of j2sdk, one googleearth and two firefox) from another partition. Immediately after the copy finished, I did ls -l and spotted the two j2sks and rm -rf'd the older one. The machine crashed partway through and couldn't reboot. 

The longest lived one lasted about 4 months.

Come Lucid, I didn't even feel like trying ext4 again. The one thing I can't understand is that I don't see hordes of people complaining.

---

### Post by ranch hand on 2010-06-25
I have trouble not believing folks when they say they have problems.  Plymouth pretty much has me shut out of 10.04 but works for most, I would say, just fine.

I am using as my primary use stable OS an install of 9.04 that is from the RC ISO, installed at that time and running without flaw sense that time.  It is on ext4.

One thing that I do know for sure is that if I was having the experience you are with ext4 I would surely not have it on my box.

---

### Post by Longinus00 on 2010-06-25
> **The Cog said:**
> The one thing I can't understand is that I don't see hordes of people complaining.

That usually means you should reevaluate where what the root of the problem is.

---

### Post by The Cog on 2010-06-25
> **Longinus00 said:**
> That usually means you should reevaluate where what the root of the problem is.

Yes, but this is two different releases of Ubuntu on 3 different machines - different hardware, (desktop, laptop, netbook), different graphics (nvidia, ati, intel), intel and amd cpus. The one common thing is that in the last year, they all crashed and died on ext4, and never crashed on jfs.

The only unusual thing I can think of is that they were all multi-boot so they were all installed with manual partitioning, and other partitions contained a mixture of fat, ntfs and jfs. Whatever the reason, I'm convinced that ext4 has some kind of problem that can cause the os to crash and corrupt the disk.

I look forward to trying btrfs.

---

### Post by ranch hand on 2010-06-25
This really does interest me more and more.

Are you running 32 or 64 bit?  I have one 32 bit install of 10.04 but everything else is 64 bit.  I only have two ext3 installs (8.04 and PhatDebian).

They are all Linux and currently all Debian or Ubuntu (one Debian respin and a couple Ubuntu respins).

This is definately a multi boot box, all installed manually.  There is no fat or ntfs allowed to come in contact with it so that is different.

I find the ext4 as stable or more so than the ext3 which is why I really like it.  Obviously your experience is vastly different.

I think this is just kind of neat.  Almost too much like FUN.

---

### Post by The Cog on 2010-06-27
All 32 bit. I would go 64 but I'm too lazy to bother with any incompatibilities unless there's a good reason. 

I don't really know why I use jfs instead of ext3, except that when I first tried it, it seemed to mount and fsck faster. I never really used ext3 much because before that, I used reiserfs - I think Mandrake defaulted to reiser.

---

### Post by zaphod777 on 2010-06-28
I have never had any problems with EXT4 and for the most part I don't see to many people in the forums with problems either. Aside from the performance hit I have read about for sql related stuff.

I am really excited for the data depup features of btrfs though. Just imagine what it could do on a file server. 

I am also liking the snapshots feature. If an update or change borks your system just roll back to the last snapshot. 

I will wait until the official Maverick release to try it but I am very excited.

---

### Post by ibuclaw on 2010-06-28
> **zaphod777 said:**
> I have never had any problems with EXT4 and for the most part I don't see to many people in the forums with problems either. Aside from the performance hit I have read about for sql related stuff.

I am really excited for the data depup features of btrfs though. Just imagine what it could do on a file server. 

I am also liking the snapshots feature. If an update or change borks your system just roll back to the last snapshot. 

I will wait until the official Maverick release to try it but I am very excited.

I don't believe there is a rollback feature (yet) - with the exception of just manually copy+paste the affected files.

What is more interesting is that you can have multiple subvolumes with multiple operating systems installed on them. ;)

Take for example, the following filesystem structure.
```

/dev/sda -> btrfs
---/
-------/debian
-------/debian-unstable
-------/home
-------/ubuntu-lts
-------/ubuntu+1

```

If I wanted to boot Debian, in pseudo grub code, you'd have the following:
```

set root='(hd0)'
linux   /vmlinuz root=/dev/sda ro quiet splash rootflags=subvolume=debian

```

And in /etc/fstab of the /debian subvolume:
```

/dev/sda    /       btrfs    defaults,subvolume=debian    0    1
/dev/sda    /home   btrfs    defaults,subvolume=home      0    2

```

Ditto for all other installed operating systems. :)

---

### Post by zaphod777 on 2010-06-28
> **ibuclaw said:**
> I don't believe there is a rollback feature (yet) - with the exception of just manually copy+paste the affected files.

What is more interesting is that you can have multiple subvolumes with multiple operating systems installed on them. ;)


I just heard the rollback might be a feature in the end. But data dedup is the future.

I just wonder how granular it will be some of the commercialy available dedup systems will actually cut the file down into 8 byte sections (not sure exact size) and then compare those. So if you have the same MS word file but only modified a few lines and saved it as a new file only the small changes get recorded not the whole new file. 

This is really a next generation file-system Mac and MS don't have anything on these features. How old is NTFS now going on 10 years old or something like that?

---

### Post by Longinus00 on 2010-06-28
btrfs does not currently have data deduplication. It is a planned feature along with fsck.

---

### Post by Blue Beard on 2010-07-01
I have been using btrfs in 10.10

Create a subvolume for your project which you use like a directory.

Create snapshots periodically.

I doubt if I can do without the quick recovery this feature provides.

See [https://help.ubuntu.com/community/btrfs#Snapshots&Subvolumes](https://help.ubuntu.com/community/btrfs#Snapshots&Subvolumes)

---

### Post by Blue Beard on 2010-07-13
The basics are in place and work well for Btrfs.

There is a LOT of work going on wrt the enhancements that Btrfs can provide.

It is up to us to test and give qualified feedback to the developers.  Bitching doesn't help!

The snapshot/rollback capability is the most immediate benefit.

The integrated fault-tolerance that will come with RAID 5&6 in August is the next greatest benefit.

The only advantage of Btrfs over Ext* is reliability and advanced features.

---

### Post by donniezazen on 2010-07-15
The installation of btrfs from Alpha2 ISO was easy and without any problem.> The file transfer is really slow in btrfs file system. Do you have the same problem? It took me 25 minutes to copy 4.5 GB of music from my home folder to a flash drive.

---

### Post by zaphod777 on 2010-07-15
> The file transfer is really slow in btrfs file system. Do you have the same problem? It took me 25 minutes to copy 4.5 GB of music from my home folder to a flash drive.

If you are using USB 1.1 that sounds about par but if it is USB 2.0 there might be an issue for you.

---

### Post by donniezazen on 2010-07-15
> **zaphod777 said:**
> If you are using USB 1.1 that sounds about par but if it is USB 2.0 there might be an issue for you.

I think it's issue with btrfs file system. My other ext4 file system works pretty fast.

---

### Post by zaphod777 on 2010-07-15
> **soham_1207 said:**
> I think it's issue with btrfs file system. My other ext4 file system works pretty fast.

Sounds like a bug then. You should file a bug report in launchpad.

---

### Post by Starks on 2010-07-16
Does GRUB2 support booting btrfs yet?

---

### Post by kahping on 2010-07-16
> **Starks said:**
> Does GRUB2 support booting btrfs yet?

Not yet

[https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-btrfs-support](https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-btrfs-support)

---

### Post by gnomeuser on 2010-07-16
> **kahping said:**
> Not yet

[https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-btrfs-support](https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-btrfs-support)

Ironically the GPL itself is preventing completely good open code to be used.. if it wasn't such a tragedy I would laugh at exactly which freedom is being protected here.

---

### Post by kahping on 2010-07-16
> **gnomeuser said:**
> Ironically the GPL itself is preventing completely good open code to be used.. if it wasn't such a tragedy I would laugh at exactly which freedom is being protected here.

I don't follow licensing issues closely, but it's a GLPv2 vs GPLv3 problem if i understand correctly? It's regrettable but at least they're both GPL so hopefully things get sorted out soon

---

### Post by cybersnoop on 2010-07-17
I've actually had a bad experience with btrfs. Ran Maverick for 10 days on my SSD with ssd and compress mount options on a fresh install and it was very nice and speedy.

But on the 10th day when I started running out of disk space (SSDs are still small and I had experimented with btrfs snapshots too) strange kernel messages started to appear and before I could find out what they meant even checksum errors were all over the place and my ecryptfs got damaged.

I've contacted the lead developper and send my kernel logs and details. He will look in to it, but in the current state it seems it's pretty easy to kill your filesystem, which is not what you want in a release.

Anyway, I knew I was testing, had backups and reinstalled everything on ext4 now.

---

### Post by gnomeuser on 2010-07-17
> **cybersnoop said:**
> I've actually had a bad experience with btrfs. Ran Maverick for 10 days on my SSD with ssd and compress mount options on a fresh install and it was very nice and speedy.

But on the 10th day when I started running out of disk space (SSDs are still small and I had experimented with btrfs snapshots too) strange kernel messages started to appear and before I could find out what they meant even checksum errors were all over the place and my ecryptfs got damaged.

I've contacted the lead developper and send my kernel logs and details. He will look in to it, but in the current state it seems it's pretty easy to kill your filesystem, which is not what you want in a release.

Anyway, I knew I was testing, had backups and reinstalled everything on ext4 now.

I've been getting some disturbing messages from ecryptfs on ext4 when running out of space as well (though on a 330GB HDD). It is possible that the problem may not be btrfs.

---

### Post by cybersnoop on 2010-07-17
> **gnomeuser said:**
> I've been getting some disturbing messages from ecryptfs on ext4 when running out of space as well (though on a 330GB HDD). It is possible that the problem may not be btrfs.

Thanks for your concern, but it was definitely btrfs talking about checksums in the kernel logs. The ecrypts came later on, but afaik that could not cause the underlying filesystem to corrupt.

---

### Post by lexiii on 2010-07-20
I've just converted a ext4 Partition to btrfs. Seems everything is working. But I'm a bit helpless about compression.

This is how I mounted the Partition:
sudo mount -o btrfs /dev/sda7 /media/files

Is it compressed that way? I want the partition to mount on startup, so I've added the following line to fstab:

/dev/sda7 /media/files btrfs rw,user,compress 0 0
It mounts, but I have no idea if it's compressed.

How can I see the compression ratio of a file? Also I have no idea how much space is left on the Partition. df tells me 100% is used.

I only have Media Files on that Partition and I've got the feeling that everything works a bit faster than it did on ext4

---

### Post by Shishimaru on 2010-07-22
I've tried to convert ext4 in btrfs on my Lucid some weeks ago thanks to the HowTo that I found here (so,I had to patch my GRUB2).
Then,I tried to install a daily build of Maverick on another partition,and of course a separate /boot,but that doesn't work to me. I had first to install btrfs-tools and then I could install it with btrfs. But,even if I have GRUB2 with the patch,Maverick doesn't boot :(
Seems that there's something wrong with con configuration of the kernel,or I don't know what... A problem with initramfs for sure! And I can't update it.

---

### Post by Blue Beard on 2010-07-22
> **lexiii said:**
> 
How can I see the compression ratio of a file? Also I have no idea how much space is left on the Partition. df tells me 100% is used.
I only have Media Files on that Partition and I've got the feeling that everything works a bit faster than it did on ext4

To get all btrfs partition usage:

df -t btrfs -h 

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             922G   64G  858G   7% /

I believe you can only get actual file size and not compression ratio unless you compare to the same file on a non-compressed partition.

---

### Post by ibuclaw on 2010-07-23
> **Blue Beard said:**
> To get all btrfs partition usage:

df -t btrfs -h 

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             922G   64G  858G   7% /

I believe you can only get actual file size and not compression ratio unless you compare to the same file on a non-compressed partition.

This has been somewhat fixed in the more recent btrfs utils and the 2.6.34 kernel.

IIRC, the command should be:
```
btrfs filesystem df
```

---

### Post by Blue Beard on 2010-07-23
> **ibuclaw said:**
> This has been somewhat fixed in the more recent btrfs utils and the 2.6.34 kernel.

IIRC, the command should be:
```
btrfs filesystem df
```

The only difference I see is more detail:

$ btrfs filesystem df /
Data: total=80.01GB, used=63.05GB
Metadata: total=1.38GB, used=441.33MB
System: total=12.00MB, used=16.00KB

---

### Post by Shishimaru on 2010-07-23
Someone was able to install with btrfs on maverick?

---

### Post by anders_c_ on 2010-07-23
> **Blue Beard said:**
> The only difference I see is more detail:

$ btrfs filesystem df /
Data: total=80.01GB, used=63.05GB
Metadata: total=1.38GB, used=441.33MB
System: total=12.00MB, used=16.00KB

I think the "total=80.01GB, used=63.05GB" shows the compression
> 
Someone was able to install with btrfs on maverick?

Yes, worked just fine with the daily-live from july 22, I made the a ext2 partition for /boot

---

### Post by Shishimaru on 2010-07-23
> **anders_c_ said:**
> I think the "total=80.01GB, used=63.05GB" shows the compression


Yes, worked just fine with the daily-live from july 22, I made the a ext2 partition for /boot
Me too,but it doesn't work :( My GRUB is patched like this guide says [http://ubuntuforums.org/showthread.php?t=1389279](http://ubuntuforums.org/showthread.php?t=1389279) is GRUB's fault? The Maverick can't boot well!

---

### Post by Blue Beard on 2010-07-23
> **anders_c_ said:**
> I think the "total=80.01GB, used=63.05GB" shows the compression


Yes, worked just fine with the daily-live from july 22, I made the a ext2 partition for /boot

"total" is storage allocated to subvolume and is not related to compression.

The other numbers are overhead associated with the metadata.

See [http://www.mail-archive.com/linux-btrfs@vger.kernel.org/msg05415.html](http://www.mail-archive.com/linux-btrfs@vger.kernel.org/msg05415.html)

---

### Post by ibuclaw on 2010-07-23
> **Shishimaru said:**
> Me too,but it doesn't work :( My GRUB is patched like this guide says [http://ubuntuforums.org/showthread.php?t=1389279](http://ubuntuforums.org/showthread.php?t=1389279) is GRUB's fault? The Maverick can't boot well!

Did the patch apply properly when you ran it? Would you have been able to tell the difference?

Also, being able to diagnose which stage in the boot process which fails would help also. Try booting into recovery mode, that should give you a more verbose reading.

Tbh, that is a guide for Lucid users really. Maverick is supposed to be able to support Btrfs pretty much out the box.

---

### Post by psyke83 on 2010-07-23
> **ibuclaw said:**
> Did the patch apply properly when you ran it? Would you have been able to tell the difference?

Also, being able to diagnose which stage in the boot process which fails would help also. Try booting into recovery mode, that should give you a more verbose reading.

Tbh, that is a guide for Lucid users really. Maverick is supposed to be able to support Btrfs pretty much out the box.

AFAIK, there's absolutely no need to patch GRUB2 (or do anything in Part 1 of your guide) for Maverick. I recommend that you put a disclaimer in your guide for Maverick users not to follow the installation steps (since the alternate and live installers can work with btrfs directly). 

Part 2 onwards would still be useful, though.

---

### Post by Shishimaru on 2010-07-23
Maverick's GRUB2 can work without patches? :o
Btw,after I try to boot it,the only thing appears after some messages is a "(initramfs)". Seems that there's something wrong with this.

---

### Post by psyke83 on 2010-07-23
> **Shishimaru said:**
> Maverick's GRUB2 can work without patches? :o
Btw,after I try to boot it,the only thing appears after some messages is a "(initramfs)". Seems that there's something wrong with this.

Easy now...

GRUB2 in Maverick doesn't require patching to recognise btrfs partitions, but it still can't boot from a btrfs partition. You still need to create a separate /boot partition with a supported filesystem.

---

### Post by ibuclaw on 2010-07-23
> **psyke83 said:**
> AFAIK, there's absolutely no need to patch GRUB2 (or do anything in Part 1 of your guide) for Maverick. I recommend that you put a disclaimer in your guide for Maverick users not to follow the installation steps (since the alternate and live installers can work with btrfs directly). 

Part 2 onwards would still be useful, though.

Disclaimer added.

---

### Post by Blue Beard on 2010-07-23
> **Shishimaru said:**
> Someone was able to install with btrfs on maverick?

I just downloaded today's daily-build.
The fresh install was normal except selecting manual partitioning.

I created a 48 MB ext2 /boot, a btrfs / and a swaparea.

Worked without problem.


~$ sudo btrfs filesystem sho /dev/sda5

failed to read /dev/sr0
Label: none  uuid: 240c3b91-129e-4b8c-b0b0-752a6e867150
	Total devices 1 FS bytes used 2.41GB
	devid    1 size 231.89GB used 5.04GB path /dev/sda5

Btrfs Btrfs v0.19
~$ btrfs filesystem df /
Data: total=3.01GB, used=2.19GB
Metadata: total=1.01GB, used=219.77MB
System: total=12.00MB, used=4.00KB
~$ df -h -t btrfs
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             232G  2.7G  230G   2% /
~$ df /boot
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1                43179     38018      2857  94% /boot

~$ uname -a
Linux btrfs 2.6.35-10-generic #15-Ubuntu SMP Thu Jul 22 11:10:38 UTC 2010 x86_64 GNU/Linux

---

### Post by psyke83 on 2010-07-23
> **ibuclaw said:**
> Disclaimer added.

Thanks! Great work with the guide, too.

---

### Post by Shishimaru on 2010-07-24
Tried Kubuntu Alpha2 and the actual Daily Build... The installer crashes on the "update-grub" in both the ISOs! :-/
I use tu work on the Gnome desktop,but I wanted to try,just to try,the K Desktop Environment.

edit: the same thing with Ubuntu! It says that I can't install GRUB in the MBR!!

---

### Post by Blue Beard on 2010-07-24
> **Shishimaru said:**
> Tried Kubuntu Alpha2 and the actual Daily Build... The installer crashes on the "update-grub" in both the ISOs! :-/
I use tu work on the Gnome desktop,but I wanted to try,just to try,the K Desktop Environment.

edit: the same thing with Ubuntu! It says that I can't install GRUB in the MBR!!

Are you creating a ext2 /boot partition?
Btrfs can not be booted directly yet.

---

### Post by Shishimaru on 2010-07-24
> **Blue Beard said:**
> Are you creating a ext2 /boot partition?
Btrfs can not be booted directly yet.
Yes I know. In fact,I did the same with Lucid time ago! I tried to install GRUB in the MBR (/dev/sda). Did I do it wrong?

---

### Post by HeadHunter00 on 2010-07-24
here's a tip: DONT DO IT
btrfs is still not stable yet. plus there aren't too many speed improvements, there are mostly extra features that are meant for server usage. if you want to, you can do the disloyal thing to ubuntu and use it in fedora instead if you want it so bad. but i highly recommend you not to get so impatient and wait for btrfs's stable release.

---

### Post by Shishimaru on 2010-07-24
I already know. It's just for testing,in a separate partition.

---

### Post by crjackson on 2010-07-24
> **kansasnoob said:**
> How many people had trouble with ext4?

Every time I try ext4 I end up with some sort of trouble, that is actual data loss.

Ext3 works flawlessly for me:)

Newer is not always better.

ext2, 3, and 4 all work flawlessly for me on all 12 systems.

---

### Post by Blue Beard on 2010-07-25
> **Shishimaru said:**
> Yes I know. In fact,I did the same with Lucid time ago! I tried to install GRUB in the MBR (/dev/sda). Did I do it wrong?

If you do a fresh install with the current daily-install, you do only one deviation from a regular install --- manually partition the entire hard drive.

In this manual partitioning you make three partitions:

[LIST=1]
[*]Create an ext2 partition of 150 MB mounted as /boot
[*]Create a btrfs partition mounted as / - (leave room for swap)
[*]Create a swap partition
[/LIST]

No other steps are required.

---

### Post by Blue Beard on 2010-07-25
> **crjackson said:**
> ext2, 3, and 4 all work flawlessly for me on all 12 systems.

I experienced data loss with ext4.

I have had no data issues with btrfs to date; however: I leave lots of free space.  There was/may still be an issue with full drives.

My interest is in the features ext3 and ext4 can not do:

[LIST=1]
[*]Snapshots/Subvolumes which are the foundation of many features
[*]The ability to handle multiple disk drives
[/LIST]

The most common feature facilitated by snapshots is software rollback.

Using subvolumes you can separate you system data from your user data.  Using other subvolumes you can run multiple operating systems using common home subvolume.

The problem that I see is that there are too many possibilities which may confuse people on how to use btrfs.

The Ceph project (uses btrfs) creates very large information stores as a Storage Area Network (SAN) replacement.

---

### Post by Shishimaru on 2010-07-25
> **Blue Beard said:**
> If you do a fresh install with the current daily-install, you do only one deviation from a regular install --- manually partition the entire hard drive.

In this manual partitioning you make three partitions:

[LIST=1]
[*]Create an ext2 partition of 150 MB mounted as /boot
[*]Create a btrfs partition mounted as / - (leave room for swap)
[*]Create a swap partition
[/LIST]

No other steps are required.
I agree. And this is the only way I do. And there's still that strange problem with GRUB.

---

