---
title: "What is the status of TRIM support in 10.10"
date: 2010-08-31
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by zaphod777 on 2010-08-31
My next laptop will most likely have a SSD I was wondering if 10.10 now has trim support and if you needed to do anything special to get it to work out of the gate.

---

### Post by andrewabc on 2010-08-31
The kernel that comes with 10.10 has TRIM support.
As to whether it will automatically work by default I don't know.

I also don't know if it will align properly when installing or partitioning.

These are things that don't seem to have concrete answers or have been verified.

Which sucks because I have 2 SSD, and will be getting many more at the end of the year.

---

### Post by zaphod777 on 2010-08-31
I was also under the impression that it needed a non-journaled filesystem for TRIM support. so the journaling would need to be turned off in EXT4.

What is the best SSD for a laptop? Well most bang for the buck. I have been looking at the 80 GB Intel X25-M it seams to beat the 40 GB Intel X25-V in most tests. I think any bigger than that will be too expensive plus I plan on swapping the CDROM bay with a big 500GB SATA drive anyway and mounting "/home" on that and just using the SSD for the OS. So I think 40GB is enough but the performance looks betteron the 80GB I guess it has somthing to do with how it uses free space. 

[http://www.anandtech.com/show/2968/intel-s-x25-v-kingston-s-30gb-ssdnow-v-series-battle-of-the-125-ssds/1](http://www.anandtech.com/show/2968/intel-s-x25-v-kingston-s-30gb-ssdnow-v-series-battle-of-the-125-ssds/1)

---

### Post by ronacc on 2010-08-31
there is a spec from back in Karmic that addresses this but I can't find if it was actually implemented , If an ssd was the installation target ,journaling on ext4 would be off , no swap would be used and trim would be active .

---

### Post by zaphod777 on 2010-08-31
Hopefully it has made it in or 10.10 has it as I can only see the price coming down on SSD plus as more people start chasing that boot up time they will be buying a lot more of them.

---

### Post by ronacc on 2010-08-31
I just got a 64gb ssd on sale and stuck it in a desktop to play with , 7 seconds grub to login screen .

---

### Post by zaphod777 on 2010-08-31
> **ronacc said:**
> I just got a 64gb ssd on sale and stuck it in a desktop to play with , 7 seconds grub to login screen .

Now that's what I'm talking about!

---

### Post by andrewabc on 2010-08-31
Well there are several choices when it comes to SSD.

You can get 2009 based Indilinx really cheap. 64gb is approaching $100. I got 64gb ocz vertex for $130 last month (vs $200 October 2009). Other older 64gb Indilinx equivalent controllers are near or below [$100](http://ncix.com/products/index.php?sku=50540), which would be great for SATAI limited laptops, or older desktops that don't need fastest SSD.

Sandforce is best SSD out there now. 60gb will soon be $150 (some are less than that).

4th quarter this year intel will have new SSD, and supposedly new Indilinx controller, and a bunch of other controllers.

Hopefully 10.10 has proper SSD support. But I'm skeptical based upon it not having any for 9.10 or 10.04. I got first 64gb ssd October 2009.

The 30gb-40gb are really only good for dedicated web browsing machines, or as long as desktop or laptop that has easy access to internal/external HDD. Without the extra HDD space to store data, the 30gb models are quite small. But if all you need is 4gb ubuntu install+ 10gb for apps/data, then that is fine. Anandtech I think said you don't want more than 80% on drive at any time, and I think that 50% would be lots. Less space used faster it will stay.

> 7 seconds grub to login screen
Yep, when BIOS loading and stuff takes longer than to load OS, that is nice.

My biggest concern for SSD is that ubuntu gets alignment correct. No reason for TRIM to not be enabled by default. Whether they disable other features such as journalling etc in filesystem is minor compared to alignment + TRIM.

---

### Post by Nullack on 2010-08-31
My new system has a 240GB SSD but thats reserved for Win 7 64bit.

FOSS just doesnt seem to be ready for TRIM across the whole stack.

---

### Post by pookiebear on 2010-08-31
> **andrewabc said:**
> The kernel that comes with 10.10 has TRIM support.
As to whether it will automatically work by default I don't know.

I also don't know if it will align properly when installing or partitioning.

These are things that don't seem to have concrete answers or have been verified.

Which sucks because I have 2 SSD, and will be getting many more at the end of the year.


someone install the alpha and try it out. I am about to order a SSD drive if it works. :)

---

### Post by del_diablo on 2010-08-31
> **Nullack said:**
> FOSS just doesnt seem to be ready for TRIM across the whole stack.

TRIM is just a buzzword.
You do not see MAC's with SSD's flauting about it do you? They do however have the needed optimization, as do Linux.

---

### Post by plun on 2010-08-31
> **Nullack said:**
> My new system has a 240GB SSD but thats reserved for Win 7 64bit.

FOSS just doesnt seem to be ready for TRIM across the whole stack.

For sure it does.....

Bought an Intel X25, 80GB in June and it works just fine.

The 2.6.35 kernel supports TRIM but I also disabled journaling

Followed this guide:
[http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/](http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/)

Nice performance...:D

[[IMG]http://img801.imageshack.us/img801/4580/snapshot31.th.png[/IMG]](http://img801.imageshack.us/i/snapshot31.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by vishalrao on 2010-08-31
I have 2 Crucial M225 model SSDs (IndiLinx Barefoot controller based) - 128 GB (since Dec 2009) for my desktop and 64 GB (since May this year) in my laptop. Their 1916 firmware has "GC" (garbage collection) so no need for TRIM (I believe)... I dont think I bothered to check about alignment during partitioning/formatting (I used to run Win7 now just Ubuntu)... speed check via "hdparm -t /dev/sdX" seems fine... GRUB-to-login has been 10 seconds on Karmic. Current Maverick with Lucid GRUB does it in about 8 seconds. Have always been running EXT4.

(edit: I havent done anything special to avoid extra-writes to extend drive life, like turning off journaling or disabling swap - I did add "noatime" to the ext4 mount options)

But really, staying closer on topic. I think we have to wait for BTRFS and its SSD-mode - by then who knows what various controllers/firmware with their own quirks will be out there.

---

### Post by vishalrao on 2010-08-31
Mine:

[[IMG]http://img830.imageshack.us/img830/6799/ssdbenchb.png[/IMG]](http://img830.imageshack.us/i/ssdbenchb.png/)

---

### Post by Nullack on 2010-08-31
Its not a buzzword, its an important feature for ssd's

To say TRIM is supported is to say, Im ok with loosing journalled file system support

That aint ok in my book

---

### Post by plun on 2010-08-31
> **Nullack said:**
> 
To say TRIM is supported is to say, Im ok with loosing journalled file system support

That aint ok in my book

Ok.... If I enable journaling again I loose 30-60MB/s

Boot-times around 10 seconds.

"Living on the edge".....:D

---

### Post by recluce on 2010-08-31
As far as I understand it, the only thing needed for TRIM support is the 2.6.35 kernel. In other words, if you use the Ubuntu kernel ppa, you can backport TRIM support into Lucid as well.

Alignment and such: as with "advanced format" magnetic drives, some thought has to be given to partitioning (especially alignment).

As to FOSS not being ready for SSDs: I call FUD!!!

Good SSDs: Intel (all current models), Sandforce based SSDs (OCZ Vertex 2 and especially some new G.Skill SSDs).

---

### Post by andrewabc on 2010-08-31
> **pookiebear said:**
> someone install the alpha and try it out. I am about to order a SSD drive if it works. :)

SSD do work with linux, mine has worked fine since October and that is using old firmware. Whether ubuntu 10.10 will detect SSD and do stuff to optimize experience is the question.

TRIM is needed to whoever said TRIM is a buzzword.

Also, instead of testing with alpha, the beta will be released in 2 days so if someone can do fresh install and see if TRIM enabled and if it aligns properly that would be great.

Using command line and howtos to properly align sucks as when I did that in October 2009 it took about 6 hours to figure everything out.

Although with my newest SSD I didn't even check alignment, so who knows.

EDIT:
[Please sync GParted version 0.6.2 from Debian unstable - current package in Ubuntu 10.10 beta contains 2 important bugs](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/624251)
everyone go to that bugreport and select "affects me". Sadly this has not been fixed before beta released.

---

### Post by Nullack on 2010-08-31
TRIM support requires special configs in limited situations only - it's not present across the whole stack. That means, you need specific file systems, specific settings etc, certain kernel versions or higher etc.

Here's some info:

[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=18f0f97850059303ed73b1f02084f55ca330a80c](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=18f0f97850059303ed73b1f02084f55ca330a80c)

Kernel commit

And for EXT4:

discard         Controls whether ext4 should issue discard/TRIM 
nodiscard(*)            commands to the underlying block device when blocks are freed.  This is useful for SSD devices and sparse/thinly-provisioned LUNs, but it is off by default until sufficient testing has been done.

Some other filesystems dont support trim.

---

### Post by antiram on 2010-09-01
> **vishalrao said:**
> I have 2 Crucial M225 model SSDs (IndiLinx Barefoot controller based) - 128 GB (since Dec 2009) for my desktop and 64 GB (since May this year) in my laptop. Their 1916 firmware has "GC" (garbage collection) so no need for TRIM (I believe)... 

But really, staying closer on topic. I think we have to wait for BTRFS and its SSD-mode

don't wait, the wearout with indilinx based ssds is very high without trim. a user in a german forum had 10-15 cycles/day wearout without trim and 2-3 cycles/day after adding "discard" mount option to fstab.

eg. use the stable 2.6.35.3 based kernel ppa
[https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa)
or the wiper.sh script as daily cronjob for kernel < 2.6.33

you can check the wearout with smartctl -a /dev/sda. Average_Erase_Count is ID=208, if the crucial ssd is not in the list of supported drives.

other changes are not needed or outdated (on newer installations, older installs need the alignment thing) or only freaky tuning. But ok, other people have to rebuild the whole X stack for 3 fps more...

---

### Post by vishalrao on 2010-09-01
> **antiram said:**
> don't wait, the wearout with indilinx based ssds is very high without trim.

thanks! i'll add the discard mount option. avg_erase_count raw value is 512 according to smartctl :D other columns (like value, worst, thresh) are either zero or blank.

---

