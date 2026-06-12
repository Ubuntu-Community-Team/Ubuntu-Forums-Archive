---
title: "Moving to Mythbuntu"
date: 2008-08-09
forum: Mythbuntu
---

### Post by OneHundredAndTen on 2008-08-09
I have a box running MythTV. Because of some instability issues, I'd like to replace the MythTV software that I have with Mythbuntu. I have had a look into the installation guide for Myhtbuntu 8.04, and I have a few questions as a result. 

   The Mythbuntu Live disc seems to be great if you are starting from scratch. I am not sure though how to twist its arm into conforming to my current setup. Here are my needs:

   1) My Mythbuntu box will have to have a fixed IP address - no DHCP.
   2) My videos are stored in NFS-mounted drives. Mythbuntu will have to be told about this.
   3) I currently have a MythTV database that I would like to bring into my Mythbuntu installation.
   4) I have a shell-script that I must use in order to tell Mythbuntu how to change channels on my cable box. This script controls an IR device connected to my Mythbuntu box's serial port.

   As far as I can tell, the Mythbuntu installation guide does not contemplate these issues, but I am convinced that Mythbuntu can tackle them. Advice on how to do so would be much appreciated.

---

### Post by volkswagner on 2008-08-09
What you are trying to accomplish is not a problem.  Most of which has been addressed in these forums.  Unfortunately the search function is lacking in ubuntuforms.org so you here asking.

What is causing the instability?  Is it poorly supported hardware in Linux?  You may end up in the same boat, if it is.

Static ip can be accomplished after install by manual configuration, disable roaming mode and enter your ip information in network manager.

Your NFS share path will be entered post install in backend setup for the path of recordings, music, etc.  I believe you can also use symlink in the /var/lib/mythtv/recordings directory pointing to your nfs share.

You will want to use mysqldump to backup and restore to new location.

Save your shell script, and enter the command in the channel changer section for your tuner(s), "channel changer command".  This would be the same for mythtv on any distro.

[http://ubuntuforums.org/showthread.php?t=813314&highlight=mysqldump]("http://ubuntuforums.org/showthread.php?t=813314&highlight=mysqldump")

[http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+share+network+fstab]("http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+share+network+fstab")

---

### Post by nickrout on 2008-08-10
[http://mythtv.org/docs/mythtv-HOWTO-23.html](http://mythtv.org/docs/mythtv-HOWTO-23.html)

---

### Post by OneHundredAndTen on 2008-08-22
> What you are trying to accomplish is not a problem.  Most of which has been addressed in these forums.  Unfortunately the search function is lacking in ubuntuforms.org so you here asking.
>
> What is causing the instability?  Is it poorly supported hardware in Linux?  You may end up in the same boat, if it is.

I am reasonably sure that it is not a hardware issue. My motherboard is an AOpen i915Ga-PLF, with run-of-the-mill Intel hardware; my videocard is based on an NVidia FX 5200, and my capture board is a Hauppauge PVR-150. What happens is that some of my DVDs, which I have ripped to hard drive, just won't play under MythTV - the screen goes blank, mythfrontend takes up all the CPU time, and I have to kill mythfrontend to get the system going again. It is always the same DVDs, which are otherwise fine, for I can play them (outside MythTV) with mplayer or xine. In fact, the only thing that seems to be consistently misbehaving is MythTV, which makes me think that I have configuration problems.


> Static ip can be accomplished after install by manual configuration, disable roaming mode and enter your ip information in network manager.

OK, thanks.

> Your NFS share path will be entered post install in backend setup for the path of recordings, music, etc.  I believe you can also use symlink in the /var/lib/mythtv/recordings directory pointing to your nfs share.
>
> You will want to use mysqldump to backup and restore to new location.
>
> Save your shell script, and enter the command in the channel changer section for your tuner(s), "channel changer command".  This would be the same for mythtv on any distro.

Yes but how do I do that with Mythubuntu? How do I get a terminal window that gives me access to the Linux command line?

Thanks so much for your useful feedback.

---

### Post by tgm4883 on 2008-08-22
> **OneHundredAndTen said:**
> 
Yes but how do I do that with Mythubuntu? How do I get a terminal window that gives me access to the Linux command line?


In mythtv-setup for your card, you enter the location of your channel changing script.  I find it hard to believe that you had to use the command line to change your channels previously.

---

### Post by rhpot1991 on 2008-08-22
> **OneHundredAndTen said:**
> 
I am reasonably sure that it is not a hardware issue. My motherboard is an AOpen i915Ga-PLF, with run-of-the-mill Intel hardware; my videocard is based on an NVidia FX 5200, and my capture board is a Hauppauge PVR-150. What happens is that some of my DVDs, which I have ripped to hard drive, just won't play under MythTV - the screen goes blank, mythfrontend takes up all the CPU time, and I have to kill mythfrontend to get the system going again. It is always the same DVDs, which are otherwise fine, for I can play them (outside MythTV) with mplayer or xine. In fact, the only thing that seems to be consistently misbehaving is MythTV, which makes me think that I have configuration problems.


It sounds like you are using an older version of MythTV.  In which case the internal player doesn't handle dvd's so well.  The newest version handles them much better but you can still get a few problem children.  You can use xine instead of the internal player in such instances: [http://www.mythtv.org/wiki/index.php/Configuring_Xine](http://www.mythtv.org/wiki/index.php/Configuring_Xine)

---

### Post by OneHundredAndTen on 2008-08-23
> In mythtv-setup for your card, you enter the location of your channel changing script.  I find it hard to believe that you had to use the command line to change your channels previously.

Well, I have to install the script itself somehow, for it is not one that Mythubuntu (or Ubuntu, at that) knows about. Anyway, I found out how to get my terminal window. Just in case anyone might be in the same predicament: 

When exiting Mythubuntu, one is left with an Xfce session from which one can open a terminal window to mess at will with Linux. Which is just as well, for this will not only allow me to install my channel changing script painlessly, but also to NFS-mount filesystems where I have most of my videos and to do regular backups of important configuration data.

Thank you guys for your feedback.

---

### Post by tgm4883 on 2008-08-23
> **OneHundredAndTen said:**
> > In mythtv-setup for your card, you enter the location of your channel changing script.  I find it hard to believe that you had to use the command line to change your channels previously.

Well, I have to install the script itself somehow, for it is not one that Mythubuntu (or Ubuntu, at that) knows about. Anyway, I found out how to get my terminal window. Just in case anyone might be in the same predicament: 

When exiting Mythubuntu, one is left with an Xfce session from which one can open a terminal window to mess at will with Linux. Which is just as well, for this will not only allow me to install my channel changing script painlessly, but also to NFS-mount filesystems where I have most of my videos and to do regular backups of important configuration data.

Thank you guys for your feedback.

You never said you needed help installing the script.  You never said that.

---

