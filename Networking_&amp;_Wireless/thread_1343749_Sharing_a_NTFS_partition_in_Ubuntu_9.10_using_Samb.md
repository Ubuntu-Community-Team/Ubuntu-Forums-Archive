---
title: "Sharing a NTFS partition in Ubuntu 9.10 using Samba"
date: 2009-12-02
forum: Networking &amp; Wireless
---

### Post by lucast on 2009-12-02
I have a computer which I am dual booting:

Drive 1 - Partition 1: Windows XP 64bit Professional (ntfs)
Drive 1 - Partition 2: Ubuntu 9.10 (ext4)
Drive 2 - Partition 1: My documents (ntfs)

I want to share all my documents on Drive 2 on my home network.  The drive is mounted as /Windows/D/ and I am able to read and write files to the drive in Ubuntu

I have been doing some research and some say that I need to make changes to my FSTAB, install the SAMBA GUI, install the NTFS tool to make the drive writable, add users to a Samba users file.

The Ubuntu documentation says to right click on the folder, click on sharing (install the software if prompted) and thats it.  But it always gives me an error saying that it can't add the permissions to the folder.

All my computers are in the workgroup "Workgroup"

There seems to be many different ways/opinions to do this but none seem straight forward.

Im fairly new to all this and would like a step by step guide to sharing my NTFS partition in Ubuntu 9.10 and also not require a password to access the share from another machine.

Any help would be much appreciated.

---

### Post by lucast on 2009-12-03
Any ideas anyone?

---

### Post by becatcho on 2009-12-13
I have the same problem any idea?

---

### Post by ubername on 2009-12-13
Have you tried making sure that the drive is shared in Windows ( I can't remember if you can share entire drives in wondows, but if not, maybe you could create a 'top' folder on the drive with everything else in it?

Once shared in Windows it should appear in you list of shares on the computer(s) in linux samba.

BTW, some people (myself included) are having problems with SAMBA at  the moment. Not everyone, otherwise there would be a lot more noise on these forums, but a few. Therefore if you are new to this and it is not behaving how the documentation suggests, it may be that you are having the same problems(!)

FWIW, the SAMBA GUI and the ability to read/write NTFS come as standard in 9.10 - the documentation referring to installing that is out of date. Also samba users are set up by default. The main documentation which says 'right click and select share' really does do the trick, at least for native linux (ext type) file systems.
You might find system-config-samba (from Synaptic) useful at least to let you see what your settings are.

---

### Post by deathbyswiftwind on 2009-12-13
I had a similar problem with this. Samba doesnt like to share ntfs unless the owner of that partition is root. All I had to do to fix it was mark it as the owner being root with full read/write access and it worked hopefully youll have the same luck!

---

### Post by lucast on 2009-12-13
I have actually had some luck and its all working now :-)

Please see this other post of mine where I managed to get an answer that worked:

[http://ubuntuforums.org/showthread.php?t=1346905]("http://ubuntuforums.org/showthread.php?t=1346905")

---

