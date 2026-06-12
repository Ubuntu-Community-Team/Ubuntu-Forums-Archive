---
title: "[SOLVED] Can't install and use mkisofs, cdrecord instead of genisoimage and wodim!"
date: 2008-07-07
forum: Multimedia Software
---

### Post by mytwobears on 2008-07-07
I spent the better part of yesterday trying to install and use cdrtools and the various elements of it, ie, mkisofs, cdrecord etc. However, it has become abundantly clear to me that this is impossible, at least for the average user.

Clearly, Hardy Heron has been coded to disallow the user the choice to use these tools. Every time I install these programs, whether from the Ubuntu repo. or compiled from source, I am instructed to install genisoimage and wodim instead. The cdrtool programs have been installed in the optional directory by default but Ubuntu keeps telling me that they are not installed and I should install genisoimage and wodim.

This is troubling; I came to linux, open source, and Ubuntu because of the freedom and control espoused, but this is clearly a restrictive and oppressive practice, disallowing the user the ability to choose what packages she wants to use in the operating system she has installed on her computer.

I have searched through the forums and the internet and have tried a number of procedures but have not been able to do two simple things: (1) remove genisoimage and wodim without removing half of my entire system and (2) install the current version of cdrtools and have Ubuntu recognize that they are installed and use them as backends for programs and from the terminal.

Please let me know if there is some way I can do this and please provide detailed directions on how. Thank you so much for your time and help.

---

### Post by mytwobears on 2008-07-11
OK, I solved this issue myself. I had to remove all the hard and sym links that linked the genisoimage and wodim files to mkisofs and cdrecord, then I deleted the files that i removed the links from (ie, genisoimage, cdrecord and mkisofs) from the bin folder, then I moved the mkisofs and cdrecord files that had been installed by default in the optional folder to the bin folder. This allowed me to use mkisofs without it calling genisoimage. To use mkisofs and cdrecord as the defaults in Brasero, I had to delete the genisoimage and wodim files from the Brasero plugin folder.

I was able to make an iso file using mkisofs and use Brasero to burn the image to a blank CD without any errors and I can watch the CD in both Ubuntu and Windows.

Hope this helps someone :).

---

### Post by achim_59 on 2012-12-28
> **mytwobears said:**
> ...

Hope this helps someone :).

Yes, it helps me a lot! I'm using 12.04-LTS, so I can't be sure your approach will work, but it gives me a good idea of what needs to be done.

Thanks for doing the hack work and sharing the results :D

Achim

---

### Post by mc4man on 2012-12-28
This thread should & will be closed shortly, may as well end with some more relevant info.
No hacks needed  - Brandon Snider maintains a ppa for just this
[https://launchpad.net/~brandonsnider/+archive/cdrtools](https://launchpad.net/~brandonsnider/+archive/cdrtools)

---

### Post by overdrank on 2012-12-28
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

