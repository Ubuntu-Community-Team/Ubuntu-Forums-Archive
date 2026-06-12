---
title: "Grub2 - error: no argument specified"
date: 2011-01-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by drs305 on 2011-01-07
Just a heads up if you use a custom menu, have a "search" line, and are using Grub 1.99:

I started getting a Grub2 error message "[COLOR="Red"]error: no argument specified[/COLOR]" when using certain menuentries from a custom Grub2 file I'd been using for quite some time.

After a bit of experimenting I was able to track down the cause for the new error message. In previous versions of grub, the 'search' line was similar to:
> search --no-floppy --fs-uuid --set 857d5af9-23cd-4d9b-908b-cc075e866758


Grub 1.99 doesn't quite like that format, and generates the error message - after which, you may or may not be able to boot. For my Maverick and eariler entries in my custom menu I can continue to boot by pressing any key. For my main Natty entry in the default menu, if I remove the '=root' portion of the 'search' line it balks and won't boot until I fix it.

The new format which eliminates the message is:
> 
search --no-floppy --fs-uuid **--set=root** 857d5af9-23cd-4d9b-908b-cc075e866758


When you look at the line, it actually makes more sense with the new format, as the '--set' option now has a defined parameter attached to it. 

I wouldn't call it a bug, as I consider it an improvement to - or at least tightening of - the code. It's just something to be on the lookout for *if* your custom menuentry includes the 'search' line, or if you go messing about with 10_linux or grub.cfg file and modify a 1.99-generated 'search' line.

Final Note: You don't need a 'search' line in a custom menu in most circumstances...

---

### Post by Quackers on 2011-01-07
You should be a Detective :-)
Detective Chief Grub Inspector!

---

### Post by cecilpierce on 2011-01-07
This is all I have in 40_custom

menuentry 'Alpha ! Unity (sda5)' --class arch --class os {
        insmod ext2
        set root='(hd0,5)'
        linux   /vmlinuz root=/dev/sda5 ro quiet splash nomce
        initrd  /initrd.img
}

---

### Post by drs305 on 2011-01-07
> **cecilpierce said:**
> This is all I have in 40_custom

menuentry 'Alpha ! Unity (sda5)' --class arch --class os {
        insmod ext2
        set root='(hd0,5)'
        linux   /vmlinuz root=/dev/sda5 ro quiet splash nomce
        initrd  /initrd.img
}

And that's all you need. 

One reason I posted was that some users, although probably not as high a percentage of alpha/beta testers, merely copy an existing menuentry and paste it into a custom folder. 

If pasting from natty, it will work, but if the menuentry was posted from an earlier version or pasted from another partition's grub.cfg file, the search line may not be in the correct format.

---

### Post by VMC on 2011-01-07
> **drs305 said:**
> And that's all you need. 

One reason I posted was that some users, although probably not as high a percentage of alpha/beta testers, merely copy an existing menuentry and paste it into a custom folder. 

If pasting from natty, it will work, but if the menuentry was posted from an earlier version or pasted from another partition's grub.cfg file, the search line may not be in the correct format.

That's similar to what I am doing. I copy my own grub.cfg, and found out the old way:

set root='(hd0,6)'

is replaced with a new way and the argument its complaining about is on the tail end 'msdos1':

set root='(/dev/sda,msdos1)'

---

### Post by hogar_pg on 2011-03-25
I got the same error message after cloning my Ubuntu partition from old to new hard drive (it grew from 160GB to 1000GB now). This solution solves it temporarily, but every kernel upgrade or cleanup via Ubuntu Tweak (sorry, I am not Linux guru, I use tools like this), causes same problem. Moreover, I can't boot to Windows partition (not that I use it much, so this is not a big problem) from GRUB. Any idea how to make this permanent? And, anyway, how is this related to Clonezilla (which I used to clone my HDD).

---

### Post by dino99 on 2011-03-25
follow this step by step, into synaptic:

- remove/purge (right click) both grub-pc & grub-common
- reinstall both grub-pc & grub-common

this will remove the old conflicting settings left behind, and you get a clean grub

---

### Post by hogar_pg on 2011-03-25
> **dino99 said:**
> follow this step by step, into synaptic:

- remove/purge (right click) both grub-pc & grub-common
- reinstall both grub-pc & grub-common

this will remove the old conflicting settings left behind, and you get a clean grub

purge = complete removal?

---

### Post by hogar_pg on 2011-03-25
Worked like a charm! 

I just did 
```
sudo update-grub
```
just in any case, before restarting :)

Thanks!

---

### Post by llazarte on 2011-04-11
Thanks a lot!

That was the solution for the error I had after upgrading to Natty Narwhal (beta) in my modified Grub (via 40_custom).

Cheers,
Leonardo

---

### Post by jonnyvinyl on 2011-04-13
Thankyou!!

After upgrading 10.10 to 11.04 i was unable to boot into my windows 7 disk. After checking the grub custom file and trying a few solutions without any luck, i found this one - after adding the extra bit and updating grub it worked no problem.

I had 2 grub errors:

Error: No Argument Specified
Error: Invalid Signature

It seemed to cure both.

Thanks Again, Jonny

---

### Post by agaida on 2011-04-24
Imho i would call it an regression. When you read the documentation -- set [var] ..
var is optional and root is the default setting. It will make no sense to change this behavior. If it's a feature, then the documentation has to be changed.

---

### Post by drs305 on 2011-04-24
> **jonnyvinyl said:**
> Thankyou!!

After upgrading 10.10 to 11.04 i was unable to boot into my windows 7 disk. After checking the grub custom file and trying a few solutions without any luck, i found this one - after adding the extra bit and updating grub it worked no problem.

I had 2 grub errors:

Error: No Argument Specified
Error: Invalid Signature

It seemed to cure both.

Thanks Again, Jonny

This may or may not apply to your situation, but I'll mention it. 

There is one change in Grub 1.99RC that also produces those errors. It's the "set root" section of the search line in the menuentry. 

Old:
> search --no-floppy --fs-uuid [COLOR="Red"]--set[/COLOR] c9101109-b746-464e-b9ec-5c62d9958c8d

New:
> search --no-floppy --fs-uuid **--set=root** c9101109-b746-464e-b9ec-5c62d9958c8d

If you were using a custom menu or copy/pasted an old setting this may trigger those messages, although on my system it complains but eventually booted anyway.

I've written some guides for a couple of the new features in Grub 1.99. I'll be publishing them in a day or two while on vacation.

---

