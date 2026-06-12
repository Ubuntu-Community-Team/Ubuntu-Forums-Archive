---
title: "Failed to open DVR device /dev/dvb/adapter1/dvr0 : Cannot allocate memory"
date: 2012-01-22
forum: Mythbuntu
---

### Post by ubnewbie2 on 2012-01-22
I have been getting zero byte recordings, and have managed to find the mythbackend log of the error.  I have added the into to the RFH thread above  

[http://ubuntuforums.org/showpost.php?p=11631294&postcount=58](http://ubuntuforums.org/showpost.php?p=11631294&postcount=58), 

but, for this specific error, I found this thread on the mythtv users mailing list

[http://www.gossamer-threads.com/lists/mythtv/users/226072](http://www.gossamer-threads.com/lists/mythtv/users/226072)

about failing to open the 3rd DVB device (I have three too) with this same error.

I don't understand it well enough to know what to do next.  I think it's saying that adding memory won't help.  It talks about removing modules, but what/how?  Should I just remove a tuner, and run with 2?

Any help will be much appreciated.

---

### Post by ian dobson on 2012-01-22
Hi,

Maybe try increasing the amount of memory allocated for internel kernel structures:-

```
vmalloc=nn[KMG]	[KNL,BOOT] Forces the vmalloc area to have an exact
			size of <nn>. This can be used to increase the
			minimum size (128MB on x86). It can also be used to
			decrease the size and leave more room for directly
			mapped kernel RAM.
```

This is a kernel command line parameter that you need to set in your boot loader (grub/grub2).

Also see [http://www.mythtv.org/wiki/Common_Problem:_vmalloc_too_small](http://www.mythtv.org/wiki/Common_Problem:_vmalloc_too_small)

Regards
Ian Dobson

---

### Post by ubnewbie2 on 2012-01-22
> **ian dobson said:**
> Hi,

Maybe try increasing the amount of memory allocated for internel kernel structures:-

```
vmalloc=nn[KMG]	[KNL,BOOT] Forces the vmalloc area to have an exact
			size of <nn>. This can be used to increase the
			minimum size (128MB on x86). It can also be used to
			decrease the size and leave more room for directly
			mapped kernel RAM.
```

This is a kernel command line parameter that you need to set in your boot loader (grub/grub2).

Also see [http://www.mythtv.org/wiki/Common_Problem:_vmalloc_too_small](http://www.mythtv.org/wiki/Common_Problem:_vmalloc_too_small)

Regards
Ian Dobson

I just read that.  A couple of problems, I have no  /boot/grub/menu.lst,  and also in that mythtv list thread he says

> The kernel panic is caused by grub wanting to put the initrd at the top of 
memory, then when you ask for more space in the kernel with vmalloc that 
pushes the initrd out past the end of RAM which is a bad thing. Not using 
the initrd didn't work for me either. So you tell grub that there is less 
RAM than you actually have and it will put the initrd in a more satisfying 
place. 

I added an "uppermem 524288" line before the kernel line in my 
/etc/grub.conf and then was able to add "vmalloc=148m" (default is 128m, 
148m is a random selection larger than 128m that happens to work for me) to 
the end of the kernel line without causing any panic. 


which really worries me. Seems it is risky to increase vmalloc and what would I do if the kernel panics?  I probably wouldn't know how to get my system booting again.

---

### Post by ubnewbie2 on 2012-01-22
OK, did some reading on Grub 2, and managed to unhide the grub menu.  I then manually edited the boot entry to add   vmalloc=192M , figuring if it panics I just reboot.

Happily it booted normally, so now we wait and see if I have fixed the 0 byte recordings.

Thanks very much!!

---

### Post by ian dobson on 2012-01-22
Hi,

So you edited the commandline during boot? If so this is only a temporary change, the next time you boot you'll need to add the option again or edit /etc/default/grub then run update-grub.

I can't help you much more than this, I'm still using grub1 and haven't got my brain around grub2.


Regards
Ian Dobson

---

### Post by ubnewbie2 on 2012-01-22
> **ian dobson said:**
> Hi,

So you edited the commandline during boot? If so this is only a temporary change, the next time you boot you'll need to add the option again or edit /etc/default/grub then run update-grub.

I can't help you much more than this, I'm still using grub1 and haven't got my brain around grub2.


Regards
Ian Dobson

No worries.  I just figured by trying it temporarily, if I freaked out the kernel, a simple reboot would put it back to normal.  Now I know it works, I'll edit it into grub permanently, yes.

Thanks again.

---

### Post by ian dobson on 2012-01-23
Hi,

So vmalloc did it for you. If so maybe mark the thread as solved.

No problems, I like helping when and where I can.


Regards
Ian Dobson

---

### Post by ubnewbie2 on 2012-01-23
> **ian dobson said:**
> Hi,

So vmalloc did it for you. If so maybe mark the thread as solved.

No problems, I like helping when and where I can.


Regards
Ian Dobson

vmalloc worked in that it accepted the new value and the kernel didn't panic the way that other thread found.

As for the zero byte recordings, well last night was the first night in ages without any problems.  I'll let it go a few more nights before claiming it is solved for me :), but it is looking very good

---

### Post by ubnewbie2 on 2012-01-25
My 0 byte recordings have stopped overnight and haven't come back for 3 days.  Very good sign! :)

Marking thread as solved

---

