---
title: "Unable to boot off 14.04 Mythbuntu...."
date: 2014-07-18
forum: Multimedia Software
---

### Post by diyhouse on 2014-07-18
Clearly I am doing something wrong,.. but what I do not know.

I have built a 14.04 DVD from a iso file,... if I load the disk into a PC I can see the file structure.

However if I set my bios to boot direct from 14.04 it just seems to skip the DVD boot option,... if I load 12.04 into player a repeat same process,... install setup appear without any problem.
I have used two iso burn packages both give the same failed result when trying to boot from DVD.

I have reset BIOS to defaults,.. tried both a DVD player, and Blu ray recorder,.. and all combo's with 14.04 fail., I have even removed the Blu Ray player from the h/w setup,.. without success.

What am I doing wrong....

Kind Regards

---

### Post by yancek on 2014-07-18
> 
I have built a 14.04 DVD from a iso file

What does 'built' mean?  The standard method is to 'burn as an image'.  If you have done that correctly, then when putting the DVD in a system running Linux, you would expect to see the various files in the root of the Live system which apparently you can?  Did you verify the download, doing an md5checksum on the iso file?

---

### Post by diyhouse on 2014-07-19
Sorry for confusion,.. I did burn and ISO file to DVD,.... and  all the files can be seen,.. and this morning I have just discovered that my laptop will boot off the 14.04 DVD,....  so now the question becomes what has changed in the way the ISO files are created that my other PC will boot off 12.04 but not 14.04,... 

I am really at a loss here....

---

### Post by gilligan216 on 2014-07-20
the machine in question needs to be told in the bios settings to boot from the cd rom drive. if the drive is a secondary slave, the bios may IGNORE the boot sequence.
one other note, my worst Ubuntu install of 14.04 came from burning the disc image with windows! to get around that i went to puppy lunix, slacko by choice.

---

### Post by diyhouse on 2014-07-21
Understand what your taking about and I can select the "boot device" from either within the BIOS by choosing CDROM,.. or select a "boot menu"  (F12) as the system boots and then choose CDROM. 

Either way works fine with my 12.04 boot disk,.. just not my 14.04 DVD,.... which also works when loaded into my laptop,... so I am really baffled.

Some more Info:-

I can take a 12.04 disk and a 14.04 disk,.. and load the DVD in one of the two players,. ( DVD RW, and a Blu Ray RW ),.. reboot system and it will boot form the 12.04 DVD,.... 
Now this may be a fluke as there will be a boot priority,.... So swapping DVDs around,.... and system still boots from 12.04 DVD,.. ignoring the 14.04 DVD in both cases.

Does anyone have some more thoughts... as I am running a little thin on ideas...

---

### Post by diyhouse on 2014-07-25
well I have run out of ideas now,.. :-( removed all unnecessary disk h/w so just the HD to load and the two DVD readers... and it still fails with 14.04... )

So regret have loaded 12.04 and applied all updates etc,.. that works fine even with extra disks. and I'm still baffled.

love the way remote clients work,.. love-it!

---

