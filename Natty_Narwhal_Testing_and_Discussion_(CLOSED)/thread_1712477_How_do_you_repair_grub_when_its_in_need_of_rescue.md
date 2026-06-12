---
title: "How do you repair grub when its in need of rescue?"
date: 2011-03-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Vigh on 2011-03-22
How do you repair grub when its in need of rescue? I've been doing some alpha testing, and all has been going well, but occasionally the bootloader seems to completely die and I have to do a fresh install. 

I have got messages like- unknown filesystem
-grub rescue>
-unknown disk chunk size

going to try the new daily build

also in terms of computer programming, what is the easiest language to learn/design software to use in Ubuntu, I would love to try and start to learn programming, are there books on the subject which I could purchase even? I have heard python is a good one

---

### Post by VMC on 2011-03-22
> **Vigh said:**
> How do you repair grub when its in need of rescue? I've been doing some alpha testing, and all has been going well, but occasionally the bootloader seems to completely die and I have to do a fresh install. 

I have got messages like- unknown filesystem
-grub rescue>
-unknown disk chunk size

going to try the new daily build

also in terms of computer programming, what is the easiest language to learn/design software to use in Ubuntu, I would love to try and start to learn programming, are there books on the subject which I could purchase even? I have heard python is a good one
Python would be a great choice. When I use to program, 'C' was the language of choice. I used AWK for short scripts.

Regarding the bootloader. Use Boot_info_script [see my blue link]. Then output RESULTS.txt file back here.

---

### Post by cariboo on 2011-03-22
To answer your question you boot from the live CD and chroot your install, to do so open a terminal and type the following commands:

[LIST=1]
[*]sudo mount /dev/sdxX /mnt
[*]sudo mount -o bind /dev /mnt/dev
[*]sudo mount -o bind /sys /mnt/sys
[*]sudo mount -o bind /proc /mnt/proc
[*]sudo chroot /mnt
[/LIST]

In the first command /dev/sdxX = the partition your Natty install is on

Once at the prompt type:

```
grub-install /dev/sda
```

then

```
update-grub
```

Once the above commands have completed, press Ctrl-d twice, then reboot.

---

### Post by kansasnoob on 2011-03-22
> **Vigh said:**
> How do you repair grub when its in need of rescue? I've been doing some alpha testing, and all has been going well, **[COLOR="Red"]but occasionally the bootloader seems to completely die[/COLOR]** and I have to do a fresh install. 

I have got messages like- unknown filesystem
-grub rescue>
-unknown disk chunk size

going to try the new daily build

also in terms of computer programming, what is the easiest language to learn/design software to use in Ubuntu, I would love to try and start to learn programming, are there books on the subject which I could purchase even? I have heard python is a good one

It really depends on what you've just done to make it die. The Boot Info Script can be very helpful:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

But 99% of the time it has to do with the last user action, like a kernel update, package update, etc. We'd need a much more detailed explanation of just what goes wrong and when :D

---

### Post by Vigh on 2011-03-22
yeah ive just done another fresh install at this stage and it seems to be working with the current daily build, didn't do anything special, just had alot of programs open all at once, like skype, mozilla, evolution etc. it locked up and grub was broken, it is possible that I may have done a partial upgrade by accident which could have broken it, thanks for the tips anyway, if I have any more boot problems I will follow your instructions to repair it

regards
ant

---

