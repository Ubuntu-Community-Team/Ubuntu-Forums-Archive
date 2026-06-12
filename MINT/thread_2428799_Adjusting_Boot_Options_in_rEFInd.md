---
title: "Adjusting Boot Options in rEFInd"
date: 2019-10-09
forum: MINT
---

### Post by javierdl on 2019-10-09
I am trying to follow this [instructions]("https://www.reddit.com/r/unixporn/comments/3e8ncs/adjusting_boot_options_in_refind/") from a post 4 years ago.
I need to adapt them to Mint.
Where do I get the following entries?:

[LIST]
[*]loader - The one I entered below it's just a guess.
[*]initrd - The one I entered below it's just a guess.
[*]options - Where do I get all the IDs numbers here from?


```
menuentry Mint { 
icon EFI/refind/icons/os_linuxmint.png 
ostype Linux
volume boot
loader /vmlinuz-linux-mint 
initrd /initramfs-linux-mint.img
options "rw root=UUID=33bfccef-ae34-4044-a74a-9d8f9e4fde53 quiet elevator=bfq resume=UUID=f3b2e20c-8e7c-4ab4-8304-68ef1ae3773b resume_offset=1189888" }

```
[/LIST]

Here is an example of the [refind.conf file]("https://github.com/agners/rEFInd/blob/master/refind.conf-sample")


Thanks guys

---

### Post by yancek on 2019-10-09
I've never use rEFind but generally, when looking for the kernel (vmlinuz file) it would be available in the /boot directory of the Mint install and you would need the full path.  Same for the initrd file on the next line.  The UUID's can be obtained by running sudo blkid in a terminal and knowing on which partition the boot files reside.

---

### Post by javierdl on 2019-10-09
You may have never used rEFInd but your leads are right on! 
This already helps me moving forward. I'll look into it.
Thanks a bunch yancek :)

DPC

P.S. I'll come back with my findings...

---

### Post by javierdl on 2019-10-09
Ok,

So for this line here, I'm not too sure what to enter:
The code below is the original from someone else in the [instructions]("https://www.reddit.com/r/unixporn/comments/3e8ncs/adjusting_boot_options_in_refind/").
```

[COLOR=#DEDCD7][FONT=&amp]loader /vmlinuz-linux-ck[/FONT][/COLOR]

```

But in the boot directory the only files with "vmlinuz" are actually called like this: 
```
"vmlinuz-4.15.0-65-generic"
```

As for initrd, is somewhat different too:
Mine looks like this: ```
"initrd.img-4.15.0-65-generic"
```. 
The one in the instructions looks like this: ```
"[COLOR=#E8E6E3][FONT=&amp]/initramfs-linux-ck.img[/FONT][/COLOR]"
```

What do you think?

DPC

---

### Post by oldfred on 2019-10-09
I have only used rEFInd as an emergency boot flash drive. It worked well and found all my installs and offered to boot them.
Do not now remember if I changed any settings in refind.conf or not.

With grub I often add my own boot stanza to boot most current kernel which is just a link in / to most current kernel in /boot.
```
lrwxrwxrwx   1 root root      30 Oct  6 17:14 vmlinuz -> boot/vmlinuz-4.15.0-65-generic
lrwxrwxrwx   1 root root      30 Oct  6 17:14 vmlinuz.old -> boot/vmlinuz-4.15.0-50-generic

```

But it looks like rEFInd just is more like a configfile that loads the grubx64.efi from the ESP. So grub really is booting, rEFInd is just the menu.

I would just use same boot parameters you have in grub.

---

### Post by javierdl on 2019-10-09
Thank you oldfred.
Maybe I should backtrack a bit and explain what is it that I'm trying to do.
As the [instructions]("https://www.reddit.com/r/unixporn/comments/3e8ncs/adjusting_boot_options_in_refind/") explain, their purpose is to "adjust" the boot options in rEFInd. I don't have a problem booting, nor using rEFInd. I just want to hide some of the choices rEFInd shows (as they're unnecessary to me). If I ever need them I can always redit the refind.conf file again.
I am trying to adapt the example someone else posted in the [instructions]("http://instructions") page, to use it for Mint. I suppose once I figured out that one entry, then I should be able to use that info to create another entry for Deepin. The one for Windows should work just as it is in the example I guess.
What do you think now?

---

### Post by oldfred on 2019-10-09
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/) &
[https://askubuntu.com/questions/908677/want-to-view-contents-of-boot-efi-in-xubuntu-dont-have-permissions](https://askubuntu.com/questions/908677/want-to-view-contents-of-boot-efi-in-xubuntu-dont-have-permissions)

The example of rEFInd shows it booting /EFI/ubuntu/grubx64.efi. So then the standard grub parameters are used.

This is from my grub.cfg. I remove quiet splash and add noplymouth to see boot process (and speed boot a bit). And since I have Skylake processor, they suggest the i915.fastboot=1 parameter.

```
        echo    'Loading Linux 4.15.0-65-generic ...'
            linux    /boot/vmlinuz-4.15.0-65-generic root=UUID=c29fc361-ea05-420b-b919-850aeef65dd4 ro  noplymouth i915.fastboot=1
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-4.15.0-65-generic

```

Also in my 40_custom for grub I have several varieties of boot stanza. I am changing to labels from UUID or device. The configfile just uses one grub to call another grub, so I get full menu from second install. I think rEFInd offers many of the same options.

```
menuentry "Ubuntu 18.10 Cosmic  (on /dev/sdb5)" {
    set root=(hd1,gpt5)
    search --set=root --label cosmic --hint hd1,gpt5
    configfile /boot/grub/grub.cfg
}

menuentry "Ubuntu 16.04 Xenial  (on /dev/sda2)" {
    set root=(hd0,gpt2)
        linux /vmlinuz root=/dev/sda2 ro quiet splash
        initrd /initrd.img

```

---

### Post by javierdl on 2019-10-09
There is a second double quotation mark ("") below before the squiggly bracket ({). Is this normal, or a typo? 

```

menuentry "Windows 8.1"" {         
icon \EFI\refind\minimal-theme\icons\os_win.png         
loader \EFI\Microsoft\Boot\bootmgfw.efi}

```

---

### Post by javierdl on 2019-10-09
So far I am assuming that's a typo...unless you tell me otherwise.

Another question:
using blkid I found the UUID #, but in the example in my 1st post at the top, it shows a part of the last line of code: ...
[COLOR=#E8E6E3][FONT=&amp]```
[/FONT][/COLOR]...resume=UUID=f3b2e20c-8e7c-4ab4-8304-68ef1ae3773b resume_offset=1189888"
```

This UUID is not the same as the first showing in the same line of code. Where is it from? Is it the same as PARTUUID from the results of blkid?
You don't have it in your 2nd line of code:
```
...root=UUID=c29fc361-ea05-420b-b919-850aeef65dd4 ro
```
Should I infer that not everyone needs the "resume=UUID="?


[COLOR=#E8E6E3][/COLOR]

---

### Post by oldfred on 2019-10-09
This shows a Windows entry and has no double quote.
[http://www.rodsbooks.com/refind/configfile.html](http://www.rodsbooks.com/refind/configfile.html)

---

