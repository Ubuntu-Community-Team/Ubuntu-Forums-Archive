---
title: "Browsing to QNAP NAS"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by hugoread on 2010-10-16
Hello All,

I have a Windows network at home and a QNAP NAS that serves all my files to a couple of PCs and laptops.  I've recently installed Ubuntu on a laptop and love it for various reasons (my wife loves the speed for example, Windows was running like a dog).

I've had a few issues sorting odd things out (full screen flash for example) but I'm now running well.

However, I have one problem I just can't work out.  All my files are on a QNAP UNIX NAS that makes all the files available to my Windows PCs via Samba shares.  On the Ubuntu laptop I can also access the files no problem by simply going to Places -> Network and the Samba network is just there, allowing me to access my files.  BUT, if I'm using my email for example (Gmail) and I want to add an attachment to an email, then I have to BROWSE for the file I want.  The browsing doesn't give the network as an option (only the folders on the local drive), so I can't navigate to the NAS to attach the file.

I've searched the forum for an answer to the problem and tried a few things that have been suggested, the obvious being to create a folder in /media and then make that folder a link to the network folder, but to no avail.

Is there no way of just browsing by absolute path to find the network files without having to map drives?  Or if not, what should I be doing?  I would have thought this would be really simple but it seems to have stumped me for some reason.

Thanks for any help,
Hugo Read.

---

### Post by joberly on 2010-10-16
You can setup the Ubuntu boxes to permanently mount the network shares [during startup via fstab]("http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/")

This way you can always navigate to /media/WHATEVER and see your NAS shares.

---

### Post by hugoread on 2010-10-28
Hello,

I've permanently mounted my NAS samba shares by editing fstab successfully and can navigate through the shares, all fine.  I can bookmark a favourite folder in the shares too, which is necessary and all well and good.

However, what I can't do is create a shortcut to favourite files (sorry, Windows terminology I know, but as an english language phrase, that's what I'm trying to do, create a shortcut to a file.  Symbolic link isn't really plain english!).

I've tried simply right clicking on one of the files in question and seletecting 'make link', but I just get an error message saying 'target doesn't support symbolic links'.

Surely there's some way of creating 'shortcuts' in my Places menu or on my desktop to my favourite network files?

Help much appreciated,
Hugo.

---

