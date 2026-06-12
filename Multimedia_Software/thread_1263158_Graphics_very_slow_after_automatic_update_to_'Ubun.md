---
title: "Graphics very slow after automatic update to 'Ubuntu 9.04, kernel 2.6.28-14-generic'"
date: 2009-09-10
forum: Multimedia Software
---

### Post by UnicycleMan on 2009-09-10
I have a Sapphire Radeon HD 3650 which was working fine with Jaunty until recently. Compiz working well (maximizing windows slow for some reason), Nexuiz very good... Then it mysteriously started running appallingly slowly, even scrolling in 2D or moving windows.

It transpired that one of the frequent updates offered by the Package Manager had installed a new kernel. If I boot the system with 2.6.28-13-generic, everything is hunky dory. Can anyone explain what is going on with the new kernel 2.6.28-14-generic? I'm sure I read somewhere that it might have something to do with i686 support being the default. I have a Pentium 4.

I am now loath to accept any further updates, since it seems they may have unpredictable detrimental effects on my system.

Thanks.

---

### Post by markbuntu on 2009-09-11
I have exactly the same card and have not had any problems with kernel updates because I remove old drivers before installing new ones.

If there is more than one driver version installed on your machine the new kernel will fail to build the fglrx kernel modules because.

You can fix this temporarily by installing the driver again or just the kernel modules.

You can fix this problem permanently by removing all fglrx versions and reinstalling the driver. 

In the future be sure to remove old drivers before installing new ones or you will have this problem with every kernel upgrade.

---

