---
title: "Unable to burn double layer dvds with growisofs"
date: 2007-04-03
forum: Multimedia &amp; Video
---

### Post by fejimush on 2007-04-03
The following command lines:

growisofs -dvd-compat -speed=2 -Z /dev/hda=my_pics.iso

or... 

sudo growisofs -dvd-compat -speed=2 -Z /dev/hda=my_pics.iso

Yield:
Executing 'builtin_dd if=my_pics.iso of=/dev/hda obs=32k seek=0'
/dev/hda: splitting layers at 1844064 blocks
:-( unable to SEND DVD+R DOUBLE LAYER RECORDING INFORMATION: Input/output error

I am using a:
NEC 16X DVD±R DVD Burner IDE Model ND-3540A

It seems this drive supports DL.   ([http://www.trustedreviews.com/storage/review/2005/05/25/NEC-ND-3540A-DVD-Writer/p1](http://www.trustedreviews.com/storage/review/2005/05/25/NEC-ND-3540A-DVD-Writer/p1))

The media is Memorex Double Layer DVD+R media.

I suspect the problem is related to Ubuntu not recognizing the DL media.   When I insert a normal blank DVD I can write to it just fine.

Any help would be greatly appreciated.  

Thanks,
fej

---

### Post by fejimush on 2007-04-04
I ended up scp'ing the files to my laptop (with Windows) and burned it there.   It would be really nice to figure out why it's not working in Ubuntu.  I know this drive will burn double layer dvds under Windows.

Any help or advice is greatly appreciated.

thanks,
fej

---

### Post by phidia on 2007-04-04
Don't know much about dual layer burners in linux but I would check the HCL at linuxquestions. [http://www.linuxquestions.org/hcl/](http://www.linuxquestions.org/hcl/)

Added: That drive _is_ listed there [http://www.linuxquestions.org/hcl/showproduct.php?product=2897&cat=346](http://www.linuxquestions.org/hcl/showproduct.php?product=2897&cat=346)
and it appears it worked in debian unstable.

sorry I'm not much help.

---

