---
title: "Maverick too big for CD"
date: 2010-08-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by wpshooter on 2010-08-21
I notice that the ISOs of daily build for Maverick for both Desktop & Alternate versions are too big to fit on a 700mb CD.

When are they going to fix this ?

Can't do any testing until can burn on a CD.

NO, I don't have a DVD or USB drive.

Thanks.

---

### Post by dino99 on 2010-08-21
hm, ive not tested recently but ive read some packages comments last week saying that devs have made changes to make smaller cd, maybe they have not finished the work yet, why not using an other way instead of burning cd (mini installer)?

---

### Post by Sef on 2010-08-21
Moved to Maverik T and D.

---

### Post by wpshooter on 2010-08-21
> **dino99 said:**
> hm, ive not tested recently but ive read some packages comments last week saying that devs have made changes to make smaller cd, maybe they have not finished the work yet, why not using an other way instead of burning cd (mini installer)?

What is mini installer ?

---

### Post by ranch hand on 2010-08-21
You down load the "minimal install" disk (12 to 15 Mb) and it will boot.  Not much there but a kernel and networking and an installer.

All text based, pretty much like the Alt-install disk, but you download the packages you need.  It is pretty nice.  I always just let it get the least it will and then boot to the install.

Still don't have a gui but I am more comfortable with apt-get and get the desktop after the text log in.

Using the Gnome Desktop instead of the Ubuntu Desktop saves a little space if you are pressed for room.

You could also install 10.04 and upgrade.

---

### Post by ronacc on 2010-08-21
you could also burn it to a DVD or else use a usb stick and either unetbootin ( its in synaptic ) or startup disk creator ( system>admin>startup disk creator) .

---

### Post by ktp on 2010-08-21
> **ronacc said:**
> you could also burn it to a DVD or else use a usb stick and either unetbootin ( its in synaptic ) or startup disk creator ( system>admin>startup disk creator) .

I think DVD and/or USB weren't valid options here.

> **wpshooter said:**
> NO, I don't have a DVD or USB drive.

Thanks.

---

### Post by 23meg on 2010-08-21
> **wpshooter said:**
> I notice that the ISOs of daily build for Maverick for both Desktop & Alternate versions are too big to fit on a 700mb CD.

When are they going to fix this ?

Never. A huge amount of asynchronous uploads happen every day in the development branch, and the QA effort that would be needed to ensure that things fit on a CD on a daily basis would be enormous, and is not feasible especially given that daily images are not even guaranteed to boot at all in the first place. Such an effort is only made for the milestone releases.

If you find that a daily image is oversized, things you can do are:

[list][*] wait a few days
[*] get an older one
[*] get the previous milestone release instead
[*] burn it on a USB disk or DVD
[*] use it for VM testing; VMs don't care about image size.[/list]

---

### Post by ronacc on 2010-08-21
oops didn't notice that .

---

### Post by go7Ul1ai on 2010-08-21
> **ronacc said:**
> oops didn't notice that .

This is why it's usually best to read the OP ^_^

---

### Post by seeker5528 on 2010-08-21
> **lee.jarratt said:**
> This is why it's usually best to read the OP ^_^

Is that like reading tea leaves? 

Slosh him/her around

[img]http://www.pollsb.com/photos/o/29614-tea_cup_ride.jpg[/img]

'Till something spills out

[img]http://images.zaazu.com/img/vomit-boy01-vomit-puke-sick-smiley-emoticon-000652-large.gif[/img]

divinate some meaning from the way it lays. 

You could probably guess from this what OP usually means to me. :p

Later, Seeker

---

### Post by kansasnoob on 2010-08-21
> **23meg said:**
> Never. A huge amount of asynchronous uploads happen every day in the development branch, and the QA effort that would be needed to ensure that things fit on a CD on a daily basis would be enormous, and is not feasible especially given that daily images are not even guaranteed to boot at all in the first place. Such an effort is only made for the milestone releases.

If you find that a daily image is oversized, things you can do are:

[list][*] wait a few days
[*] get an older one
[*] get the previous milestone release instead
[*] burn it on a USB disk or DVD
[*] use it for VM testing; VMs don't care about image size.[/list]

All true, and particularly with this entire rework of ubiquity I'd expect things to be considerably challenging in the near future.

I keep looking for more updates to ubiquity but nothing since the 15th :(

I'd bet that Evan Dandrea is almost literally pulling his hair out about now.

---

### Post by kansasnoob on 2010-08-21
> **seeker5528 said:**
> Is that like reading tea leaves? 

Slosh him/her around

[img]http://www.pollsb.com/photos/o/29614-tea_cup_ride.jpg[/img]

'Till something spills out

[img]http://images.zaazu.com/img/vomit-boy01-vomit-puke-sick-smiley-emoticon-000652-large.gif[/img]

divinate some meaning from the way it lays. 

You could probably guess from this what OP usually means to me. :p

Later, Seeker

I needed a laugh, thanks for that.

---

### Post by jerrylamos on 2010-08-21
> **ktp said:**
> I think DVD and/or USB weren't valid options here.

I've burned oversize CD images to DVD which worked fine.  Only problem, the DVD was a r/w, and Ubuntu wouldn't erase and use it again.  Ubuntu will do CD r/w O.K.

Other dodge as mentioned in this thread would be to install an Alpha2 image and update it.  Problem with that I had recently is the updates started to fail because of some screw up in what package depended on what level of what other package.  So I did have an older Alpha3 CD laying around and installed that, with a whole lot of trouble.  I've got an IDE and a SATA drive.  Install and Grub disagree on which one of them is /dev/sda.  Messy.  Yes there's a launchpad bug written with no action (expected).

Sometimes I install the .iso to a 1 GB partition and run it as if it is a CD.  Oversize would fit on that.

Patience, Hortense.

Jerry

p.s. Alpha 3 hangs on this pc every so often.  Read the "Sticky" about xorg.  So I drop back to an Alpha 2 partition which hasn't hung (yet).

---

### Post by ronacc on 2010-08-21
> **jerrylamos said:**
>  Install and Grub disagree on which one of them is /dev/sda.  Messy.  Yes there's a launchpad bug written with no action (expected).


Jerry
.

I filed on that a while ago but don't see my bug now , probably duped with the one you found , After bitching about gparted and install calling drives by different letters for a long time I gave up and solved the problem by labeling my partitions and drives with distinctive names .

---

### Post by recluce on 2010-08-21
> **jerrylamos said:**
> I've burned oversize CD images to DVD which worked fine.  Only problem, the DVD was a r/w, and Ubuntu wouldn't erase and use it again.  Ubuntu will do CD r/w O.K.


DVD/CD writing is a mess in Ubuntu. Search the forum for "cdrtools" to learn more about the issues. Install the original cdrtools and you should be well rid of the problem.

---

### Post by sparker256 on 2010-08-22
> **wpshooter said:**
> I notice that the ISOs of daily build for Maverick for both Desktop & Alternate versions are too big to fit on a 700mb CD.

When are they going to fix this ?

Can't do any testing until can burn on a CD.

NO, I don't have a DVD or USB drive.

Thanks.

[http://cdimage.ubuntu.com/releases/maverick/alpha-3/](http://cdimage.ubuntu.com/releases/maverick/alpha-3/)

Then update.

Bill

---

### Post by scradock on 2010-08-22
@recluse

Searching this forum for "cdrtools" gives only the current thread. Would you care to give another clue or two?

---

### Post by ktp on 2010-08-22
maybe this thread helps for "cdrtools"

[http://wwww.ubuntuforums.org/showthread.php?t=1336278&page=3](http://wwww.ubuntuforums.org/showthread.php?t=1336278&page=3)

---

### Post by scradock on 2010-08-22
> **ktp said:**
> maybe this thread helps for "cdrtools"

[http://wwww.ubuntuforums.org/showthread.php?t=1336278&page=3](http://wwww.ubuntuforums.org/showthread.php?t=1336278&page=3)

Thanks

---

### Post by cascade9 on 2010-08-22
Easiest solution to this is to get 800MB CD-Rs.

---

### Post by LiquidMeson on 2010-08-22
1: Download Iso
2: Drag Iso to usb stick
3: ?????
4: Win

---

### Post by kansasnoob on 2010-08-22
I'm just waiting for an update in ubiquity :D

ATM it pretty well stinks. No grub-install options at all that I've seen, using a VM to test ATM falls far short of telling the whole story.

The furthest I've gotten with a "manual install" to actual partitions is selecting locale (Chicago) and then things slow to a crawl. Then it finally fails with the message "Ready when you are".

It almost seems that "installation options" are running in an incorrect order. 

This is why I mentioned recently that I think many devs must do their testing only in a VM. I can still install the daily iso in VirtualBox but that is truly "virtual".

Not much point in even trying until the ubiquity changelog shows something beyond Aug 15th ;)

---

### Post by slumbergod on 2010-09-21
I wanted to download a daily maverick minimal cd image (>20Mb) to play around with in virtualbox but I can't find one. Is a minimal cd image only released after the final official release for each ubuntu version?

---

### Post by ranch hand on 2010-09-21
> **slumbergod said:**
> I wanted to download a daily maverick minimal cd image (>20Mb) to play around with in virtualbox but I can't find one. Is a minimal cd image only released after the final official release for each ubuntu version?
This is what you are looking for;
[http://cdimage.ubuntu.com/netboot/maverick/](http://cdimage.ubuntu.com/netboot/maverick/)

---

### Post by slumbergod on 2010-09-21
Thanks. Possibly. I will give it a whirl tonight and see.

---

### Post by slumbergod on 2010-09-21
Yes, it will be perfect. If only it wouldn't hand downloading the binutils-static-udeb. Actually, the same thing happened with the lucid minial cd in virtualbox so I can't blame the netinst image.

---

### Post by PGHammer on 2010-09-22
> **kansasnoob said:**
> All true, and particularly with this entire rework of ubiquity I'd expect things to be considerably challenging in the near future.

I keep looking for more updates to ubiquity but nothing since the 15th :(

I'd bet that Evan Dandrea is almost literally pulling his hair out about now.

The *oversized live CD* problem is not new; it's not even 'buntu-exclusive.

I've seen this before with 'buntu (in fact, at some stage with every build back to Jaunty) and with openSuSE's live CD's also (back to 11.0); it's also why I shifted mostly to DVD+RW for non-VM-based testing (the only exception is for Internet-based installation testing, which can still use CD-RW, due to the extremely-small ISO size).

I'm getting ready to grab a new daily for more testing.

---

