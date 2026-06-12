---
title: "UUID in boot menu is wrong after tar restore"
date: 2010-09-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by VastOne on 2010-09-01
I have a Maverick test machine that has 2 partitions for testing and a separate /Home partition.

I did a tar backup of sda5 which is the root of the "good" test playground

I did a successful restore of this tar to sda9 just wanting to flip flop the order in preparation for the Beta and RC testing coming up.

I successfully did a update-grub and it found the sda9 install, but I cannot get it to boot because it is getting the wrong UUID at the boot menu.

grub.cfg shows the correct UUID and I have tried to change it manually editing the boot menu item (e) prior to booting but it will not boot.

I have searched for the last 3 hours on anything like this but have not found a solution.  It just makes no sense that that menu boot menu item would have a totally different UUID, althouhg I know that there have been inherent issues with UUID and it is not an exact science.

Anyone see what I am missing in this? I know there must be a way to edit it and correct it.

Thanks

---

### Post by ranch hand on 2010-09-01
This kind of thing is pretty easy to avoid if you use a custom menu with symbolic menu entries.  For instance , I just installed 10.10 on my second internal.  Put it over the top of Debian Sid.  No need to even change my menu entry.
```

echo "Adding Sid on sda6" >&2 
cat << EOF
menuentry "Sid on sda6" {
    set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 ro quiet
        initrd /initrd.img
}
EOF

```
Copy that to your 40_custom file as many times as you need, edit that to match your installs and it will boot (without splash, you may want that added).  The stuff between the "  " is left strictly up to your lack of discretion.  The first one is what you see in terminal when you update-grub, the second what you see on the screen menu.

---

### Post by VastOne on 2010-09-02
> **ranch hand said:**
> This kind of thing is pretty easy to avoid if you use a custom menu with symbolic menu entries.  For instance , I just installed 10.10 on my second internal.  Put it over the top of Debian Sid.  No need to even change my menu entry.
```

echo "Adding Sid on sda6" >&2 
cat << EOF
menuentry "Sid on sda6" {
    set root=(hd0,6)
        linux /vmlinuz root=/dev/sda6 ro quiet
        initrd /initrd.img
}
EOF

```
Copy that to your 40_custom file as many times as you need, edit that to match your installs and it will boot (without splash, you may want that added).  The stuff between the "  " is left strictly up to your lack of discretion.  The first one is what you see in terminal when you update-grub, the second what you see on the screen menu.

Thanks Ranch Hand

I figured it would be you to respond with as many setups as you have and almost PM'd you on it but instead let the rest of the world enjoy your wisdom..

---

### Post by ranch hand on 2010-09-02
Well it ought to work and then you can take some time to diagnose the other problem.

One thing that you might want to do is save the 40_custom file as 06_custom.  That puts it at the top of the menu and leaves a nice clean 40_custom file for future use.

---

### Post by bcbc on 2010-09-02
The UUID needs to be updated in /etc/fstab as well.

---

### Post by VastOne on 2010-09-02
> **bcbc said:**
> The UUID needs to be updated in /etc/fstab as well.

Right, thats the first of the basics

Thanks

---

### Post by bcbc on 2010-09-02
> **VastOne said:**
> Right, thats the first of the basics

Thanks

well, yes. But there's nothing really complex about what you are doing :)

---

### Post by VastOne on 2010-09-02
> **bcbc said:**
> well, yes. But there's nothing really complex about what you are doing :)

Except when it does not work and no real way to edit it...Nothing much complex there ):P

Edit - and I apologize, I just spent several hours trying to get to the root of the issue (searching) that my eyes and my head hurts.

---

### Post by bcbc on 2010-09-02
I'll remember I'm in the development forum next time before offering advice ;)

PS when I last migrated an install between partitions I just used rsync, poked the fstab, the /etc/initramfs-tools/conf.d/resume (to enable hibernation) and ran update-initramfs -u in chroot. Then update grub, reboot, and voila.

Maybe that will help.

---

### Post by VastOne on 2010-09-02
> **bcbc said:**
> I'll remember I'm in the development forum next time before offering advice ;)

PS when I last migrated an install between partitions I just used rsync, poked the fstab, the /etc/initramfs-tools/conf.d/resume (to enable hibernation) and ran update-initramfs -u in chroot. Then update grub, reboot, and voila.

Maybe that will help.

I do hope you saw my edit update above...:)

And I will look into this method as it was next on my list of trying different methods to create multiple restore points and ease of use.

Thank you..:popcorn:

---

### Post by VastOne on 2010-09-02
> **ranch hand said:**
> Well it ought to work and then you can take some time to diagnose the other problem.

One thing that you might want to do is save the 40_custom file as 06_custom.  That puts it at the top of the menu and leaves a nice clean 40_custom file for future use.

Ranch I created that as 06_custom but it never showed in the menu.

I did run update-grub and maybe that was the issue?

Edit - I am ready to sh*tcan the entire thing...](*,)](*,)

I found I had to make it executable and did that and now know I must run update-grub, and even though I see it added during the update, nothing ever shows up on my boot menu.  I tried 06_custom and then 40_custom with the same results...

I will get some sleep now and try to resolve it with a fresh head tomorrow.

Thanks

---

### Post by MacUntu on 2010-09-02
Don't forget to check if '/etc/initramfs-tools/conf.d/resume' contains the new UUID of the swap (if it should have changed).

---

### Post by VMC on 2010-09-02
> **MacUntu said:**
> Don't forget to check if '/etc/initramfs-tools/conf.d/resume' contains the new UUID of the swap (if it should have changed).

I think that's what bcbc was alluding to in post #9. Some never use hibernate so it never shows up.

I think the best thing to do is update grub from the controlling grub partition os.

---

### Post by MacUntu on 2010-09-02
> **VMC said:**
> I think that's what bcbc was alluding to in post #9.

Oops, missed that.

> **VMC said:**
> Some never use hibernate so it never shows up.

Oh, it *does* show up:

[img]http://img.xrmb2.net/images/563342.png[/img]

That's waiting five seconds just because there's a UUID mismatch. :)

---

### Post by ranch hand on 2010-09-02
> **VastOne said:**
> Ranch I created that as 06_custom but it never showed in the menu.

I did run update-grub and maybe that was the issue?

Edit - I am ready to sh*tcan the entire thing...](*,)](*,)

I found I had to make it executable and did that and now know I must run update-grub, and even though I see it added during the update, nothing ever shows up on my boot menu.  I tried 06_custom and then 40_custom with the same results...

I will get some sleep now and try to resolve it with a fresh head tomorrow.

Thanks
If they are executable they should show up after update-grub.

You have two root systems, I would put the same files in both and update grub on both.  See if that helps.  You may be updating the version tht is not supplying grub to the MBR.

Of course you could rub grub-install too as another way to check that.

I use a different grub background on all my installs so that I can tell.  The new ones are easy to spot as they don't have a background.  Not much help in your case as they are clones but thought you may like to know.

Sometimes the FUN can get a bit much.  Try to remember to breath, I have to when I am frustrated and ready to take a hammer to the box.

---

### Post by VMC on 2010-09-02
> **MacUntu said:**
> Oops, missed that.



Oh, it *does* show up:

[img]http://img.xrmb2.net/images/563342.png[/img]

That's waiting five seconds just because there's a UUID mismatch. :)

[COLOR="Silver"]Off-topic, what is that output from, bootcharts? I'm having problems with GDM not starting and maybe that boot log report would help diagnose the problem.[/COLOR]

edit: never-mind. I figured it out.

---

### Post by jerrylamos on 2010-09-02
UUID's?  I don't bother with them.  Based on info from Ranch Hand I put a file like so on whichever Ubuntu that boots up by default:
/etc/grub.d/06_custom
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above
menuentry "Meerkat A3 on sda12" {
set root=(hd0,12)
linux /vmlinuz root=/dev/sda12 ro quiet
initrd /initrd.img
}
menuentry "Meerkat A3fix on sda16" {
set root=(hd0,16)
linux /vmlinuz root=/dev/sda16 ro quiet
initrd /initrd.img
}
menuentry "Meerkat A1 on sda13" {
set root=(hd0,13)
linux /vmlinuz root=/dev/sda13 ro i915.modeset=0 quiet
initrd /initrd.img
}

Make the file executable:
sudo chmod 777 /etc/grub.d/06_custom
Then do:
sudo update-grub
Do:
less /boot/grub/grub.cfg#!/bin/sh
to confirm you got what you wanted, which is the 06_custom entries first followed by all the UUID nonsense.

What's in root's / are vmlinuz and initrd.img pointers to the latest entries in /boot.

This way you can put the bootable images in your desired order with labels that make sense to you, and no UUID nonsense.

Jerry

---

### Post by seeker5528 on 2010-09-02
> **VastOne said:**
> grub.cfg shows the correct UUID and I have tried to change it manually editing the boot menu item (e) prior to booting but it will not boot.

Did you run blkid or by some other method verify that the UUID is what you think it is?

If you tarred the actual device /dev/sda5 and untarred it to /dev/sda9, they would have the same UUID which would be bad.

Assuming this is an extX filesystem, if you need to generate a new UUID you could do...

```
sudo tune2fs -U random /dev/sda9
```

You could use time instead of random if you prefer a time based UUID. 

Depending on how you are doing the backup/restore, if you restored an old system that expected a different UUID that is not being used on another existing partition you could specify the actual UUID after '-U' to set it to the old UUID instead of using 'random' or 'time' to generate a new one.

Whatever the UUID of /dev/sda9 is, you have to edit the fstab on the /dev/sda9 installation to match.

Later, Seeker

---

### Post by VastOne on 2010-09-02
I appreciate everyone's help on this and it certainly has opened many new avenues of knowledge.

Here is why I need to redo everything -


```
vastone@vastone-955phenom:~$ sudo blkid
[sudo] password for vastone: 
/dev/sda5: UUID="62a065f5-12f3-45b4-9d5b-ea688ab9dd54" TYPE="ext4" 
/dev/sda6: UUID="55b53bfe-b276-4a39-9c8c-141a33bfffaf" TYPE="swap" 
/dev/sda7: UUID="c010b681-0756-4740-aa37-11519e64f737" TYPE="ext4" 
/dev/sda8: UUID="92714db2-b4a6-4464-814f-117a957df0af" TYPE="ext4" 
/dev/sda9: UUID="4af3cf7f-e77f-45dc-a718-e31fae0e2806" TYPE="ext4" 

```

My setup - sda7 is my prime test partition.

I did a tar backup of sda7 and restored to sda9 

sda9 just so happens to be the first boot device and is where grub lives and the MBR. So when I restored to sda9,  grub was and is working from the restore of sda7, but since I cannot boot to any OS on sda9 I am stuck in a loop of nothing working and not able to run update-grub from the "correct" OS.

I was able to go in and manually edit grub.cfg on sda9 /etc/grub and was able to start the boot of the sda9 kernel but I received an immediate kernel panic and due to an uncontrollable and possible permanent twitch in my left eye lid, that was the final straw.  

I think the source of this may have gone back to a few months ago when I wanted to test a separate boot partition and created it.  Even though I have since removed it, I still have weirdness in my partitions that I have never seen before when deleting and creating new ones.

I am going to try rsync next and FSarchiver looks interesting too, so I am moving on with a shred of sanity still intact. 

Ultimately I will completely format this drive and start from total scratch, most likely when Maverick is released and all the fun begins again.

Again, Thanks!

---

### Post by VastOne on 2010-09-02
> **seeker5528 said:**
> Did you run blkid or by some other method verify that the UUID is what you think it is?

If you tarred the actual device /dev/sda5 and untarred it to /dev/sda9, they would have the same UUID which would be bad.

Assuming this is an extX filesystem, if you need to generate a new UUID you could do...

```
sudo tune2fs -U random /dev/sda9
```

You could use time instead of random if you prefer a time based UUID. 

Depending on how you are doing the backup/restore, if you restored an old system that expected a different UUID that is not being used on another existing partition you could specify the actual UUID after '-U' to set it to the old UUID instead of using 'random' or 'time' to generate a new one.

Whatever the UUID of /dev/sda9 is, you have to edit the fstab on the /dev/sda9 installation to match.

Later, Seeker

Thanks seeker, I made sure the UUID was different right away and tune2fs is what I used.

Appreciate it!

---

### Post by VastOne on 2010-09-02
OK,  I am going to mark this as closed now...because I did resolve it.

Interestingly, until I completely blew up my drives and in the eleventh hour ready to format, I tried one more thing with FSarchive and got it to work.  

Somehow the drive was sentient, I just know it, and realized that until a restore was really important, it would allow it...

I am now on the partition I want with the setup I want and learned a hell of a lot on the way there.

Still have the twitch in the eyelid, but I think I can live with it..

---

### Post by ktp on 2010-09-02
> **VastOne said:**
> I am now on the partition I want with the setup I want and learned a hell of a lot on the way there.

Still have the twitch in the eyelid, but I think I can live with it..

nicely done...and the "twitch" is just a reminder so you never forget the next time you hit this.

---

### Post by VinDSL on 2010-09-02
> **VastOne said:**
> Somehow the drive was sentient, I just know it, and realized that until a restore was really important, it would allow it...LoL!  Anthropomorphism...

Perhaps it was talking to you, the whole time, but you were too cranky and tired to listen!?!?!  ;)

---

### Post by VastOne on 2010-09-02
> **ktp said:**
> nicely done...and the "twitch" is just a reminder so you never forget the next time you hit this.

Thanks...(I think) :p

> **VinDSL said:**
> LoL!  Anthropomorphism...

Perhaps it was talking to you, the whole time, but you were too cranky and tired to listen!?!?!  ;)

Classic..and yes I was a bit tired and cranky in the end, feel now like I could sleep for a week.  I do not mind the issues, that is why we are here, but not knowing the cause is what drives me nuts...):P

---

### Post by ktp on 2010-09-03
> **VastOne said:**
> I do not mind the issues, that is why we are here, but not knowing the cause is what drives me nuts...):P

you are perfect QA then =)

---

### Post by VinDSL on 2010-09-03
> **VastOne said:**
> I do not mind the issues, that is why we are here, but...Agreed!

I find stress exhilarating.  If I'm not surrounded by chaos and mayhem, I'll create it for myself.  LoL! 

I love the feeling that I get, in the pit of my stomach, when I can't figure something out.  And, it's always anticlimactic when I fix it.

Probably some sort of deep-seated psychological disorder...

The funny thing is, I've made a living out of it.  I maintain and repair million-dollar industrial production machinery.

What better hobby than writing code, and trying to break Ubu, in my spare time?!?!?

---

