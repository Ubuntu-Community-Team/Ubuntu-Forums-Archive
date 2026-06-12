---
title: "One of my Natty installs disappeared from grub menu"
date: 2010-12-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quackers on 2010-12-22
I ran updates on one of my Natty installs (username mdnatty64) and all was ok after a reboot.
So I went to the other Natty install and ran the updates on that one (username nattyalpha) and rebooted. The grub menu didn't mention the mdnatty64 installation, but as one of the updates was grub related I wasn't too concerned and when the system booted I ran sudo update-grub.
It's gone :o
I enclose screenshots and as you can see, the installation is clearly visible in the gparted screen (obviously the one not mounted).
Now I'm wondering if I dare shutdown! 
Curious

---

### Post by coffeecat on 2010-12-22
That's an odd one. I've got two Nattys on this machine. I've just updated one - there was a grub update - and I didn't get this. But the other Natty hasn't been updated for a couple of days so I don't know whether that makes any difference. I'll update the other Natty later and see what happens.

The main difference with my setup is that I'm using my Maverick grub as my master menu at the moment, with entries for Natty (and other distros) in 40_custom. When I updated just now, I wasn't hit by [this]("http://ubuntuforums.org/showthread.php?t=1650296"), although I experienced that about a week or so ago. All very weird.

The only (temporary) solution I can suggest is to make 40_custom executable in the Natty you can reboot into and add an entry for the other Natty, and then run update-grub again to get your custom entry into grub.cfg. That, at least, keeps you going until this blows over.

So that you don't have to edit your 40_custom every time there's a kernel upgrade, this is my little trick. A sample entry from my maverick 40_custom:

```
menuentry "Ubuntu Natty Alpha on sda11" {
    insmod ext2
    set root=(hd0,11)
    search --no-floppy --fs-uuid --set 2deb5380-fa08-45bd-8405-7e74b5a88c25
    linux    /vmlinuz root=UUID=2deb5380-fa08-45bd-8405-7e74b5a88c25 ro   quiet splash
    initrd    /initrd.img
}
```You can see that I'm referencing the symlinks vmlinuz and initrd.img in the root of the filesystem that are updated every time there's a kernel update.

---

### Post by Quackers on 2010-12-22
Very nice :-)
It may come that I need such an entry. I'll risk rebooting and see what happens.
If I can think of a good way to do it I may get rid of 2 of the grubs and just have one doing everything. I need to be careful though, as only one drive is bootable in the bios.

---

### Post by Quackers on 2010-12-22
I booted up Maverick for the first time in a month :-)  When the updates were run it used up 600MB more than it used to! That's almost a new system :-)
Anyway, both Natty installs are seen from there.
So I rebooted the Natty that is still showing in grub and ran sudo update-grub again and now the other Natty is back! :-)
Some skullduggery is going on here :-)

---

### Post by coffeecat on 2010-12-22
> **Quackers said:**
> Some skullduggery is going on here :-)

I've got another theory. :) I believe this is the first moody operating system in history. During the great python update of a week or so ago, my two Natty installs were  displaying different behaviours with all the breakages but were both up-to-date. I think they decided how they felt on boot-up and reacted appropriately. You could try:

```
sudo apt-get purge sulk
```Whatever - I updated the other Natty and I didn't get anything missing from grub.cfg in that one either.

Or perhaps both of mine are feeling good at the moment. Someone's been at my vintage port and I'm sure I heard the muted strains of 'Nelly Dean' from inside the computer case earlier. :-k

---

### Post by Quackers on 2010-12-22
I think you may be right!
There was a distinct smell of alcohol from the laptop this morning.
And it doesn't type properly any more :-)

TBH I think Natty, in its current state of flux, is very moody. As you say, it depends on how it feels as to what you get when it's booted. Quite hit and miss at times.

Cherry Mistmas to you :-)

---

### Post by coffeecat on 2010-12-22
> **Quackers said:**
> Cherry Mistmas to you :-)

And a Natty Yew Near! [ATTACH]179142[/ATTACH]

---

### Post by ratcheer on 2010-12-22
Here is a suggestion. I am having a repeated problem with my Maverick installation not being detected when update-grub runs in natty. I had opened a bug report and was told that update-grub no longer plays back the journal of the other installations. Therefore, before updating grub, I run "sudo fsck /dev/sda2" (sda2 is where my Maverick is installed. Then, grub detects and configures my Maverick.

This might also help with detecting your other natty installs.

My problem is that, even when I cleanly terminate all running apps and do a clean restart, Maverick is for some reason leaving orphan inodes. The fsck cleans them up, then update-grub detects Maverick. Otherwise, it bypasses the unclean partition.

Even though they accepted my bug as a valid problem, they state that it will not be fixed because automatically playing back the journal causes other problems. See [https://bugs.launchpad.net/ubuntu/+source/os-prober/+bug/683355](https://bugs.launchpad.net/ubuntu/+source/os-prober/+bug/683355)

Tim

---

### Post by Dr. Tyrell on 2011-01-21
[http://art.ubuntuforums.org/showpost.php?p=10385031&postcount=3](http://art.ubuntuforums.org/showpost.php?p=10385031&postcount=3)

---

