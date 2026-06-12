---
title: "shutdown and restart hang if CIFS filesystem mounted"
date: 2011-04-26
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by glentrobfc on 2011-04-26
My fstab file contains 2 nfs mounts and 1 cifs mount.  If I automount the cifs filesystem as in the attached fstab, an attempt to shutdown or reboot hangs requiring power cycle | power button held  >5 seconds.
If I use noauto AND do not have done a sudo mount, i.e., df does not indicate the CIFS filesystem (/mnt/sharon-work) then either shutdown or reboot takes about 15 seconds.  If the CIFS filesystem is mounted, however, the system hangs indefinitely.  Note, I have tweaked the user and passwords in the attached copies of fstab.

---

### Post by grwilmoth on 2011-04-26
Do you use wifi? I've always had this problem with my laptop. I always thought the problem is that the wifi disconnects prior to dismounting the network shares and it ends up having a communication problem. As a result, linux can't properly dismount network shares and it hangs. My desktop computers have never had this problem, being connected by ethernet.

I'm not 100% positive on this, but no one had responded to your question, so hopefully this sheds some light on the subject. I've never really bothered to devise a workaround. I just run 'sudo umount -a' before before i shutdown and it turns off promptly.

---

### Post by glentrobfc on 2011-04-27
Yes,  I am using wifi.  This is an hp mini 210-1010NR netbook.  It multi boots Mint 10, Mint LMDE, Windows 7 and Natty.  I have also had fuduntu on it (in the partition that now has Natty).  None of the other linux versions have had the problem.  At first I thought it might have been the nfs mounts, but using noatuo in fstab and making sure that the 2 nfs mounts were not mounted still had the problem.  Using noauto and mount/umount on the CIFS mount enables or disables the hang on shutdown.  If I could figure out how to get the automounter to work on the CIFS mount I would try that, however, I have been unsuccessful (anything I try hangs at the first mount access).  I can get the NFS mounts to automount, but not the CIFS mount.  If I have any luck on the CIFS mount today, I will report back as to whether that cured the issue or not.  I have attached the auto.master and the auto.nfs files.    I am using the STA driver for wifi and wpa-2 psk.  I have left it at wpa-2 psk because I am running on an active home wireless network and my spouse is doing work on it with a windows machine, which I want to keep isolated/private.  I will hook up this netbook on my wired netbook later this morning and repeat the experiment reporting back on whether it hangs or not.

---

### Post by glentrobfc on 2011-04-27
I tried the wired versus wireless experiment.  It hangs with wireless (screenshot2) and does not with wired (screenshot1).

---

### Post by tekstr1der on 2011-04-27
Perhaps you're experiencing this age-old bug?
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/211631](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/211631)

Sounds like what you are describing. Been there myself and gave up on cifs a while back for this and performance reasons. nfs and gvfs are much speedier with less headaches.

---

### Post by glentrobfc on 2011-04-27
Good insight - yes this does appear to be exactly the referenced bug that now apparently has been present through lots of releases over 3 years and is clearly there in the about (tomorrow) to be released 11.04.

Good Grief.

---

### Post by glentrobfc on 2011-04-27
For everyone's 'what it's worth department'.  The same netbook on the same network with essentially the same fstab (at least for nfs and cifs mounts) on Linux Mint 10 (Gnome) shuts down just fine with the CIFS filesystem mounted.  See attached screenshot.

---

### Post by grwilmoth on 2011-04-28
Interesting. I figured Linux Mint would most likely contain the same issue. 

But yeah, I remember finding that bug report a long time ago. I've literally been waiting 3 years for them to fix this, but I'm no longer holding out hope. It seems like a rather important bug for them to ignore. I would have thought that auto-mounting/dismounting network folders with CIFS would be a commonly used feature. I'm thinking of just switching to NFS like tekstr1der mentioned.

---

### Post by Morbius1 on 2011-04-28
If you really really want to automount the remote samba share and can live with a mount point in a very unusual place then I would suggest taking it out of fstab and using this instead:
```
gvfs-mount smb://192.168.1.100/work
```If you run that command from a terminal it will mount the remote share to:
> /home/your-user-name/.gvfs/work on 192.168.1.100It's in a hidden directory as you can see but you could create a symlink to the desired folder:
```
sudo ln -s /home/your-user-name/.gvfs/"work on 192.168.1.100" /mnt/sharon-work
```gvfs works in userspace so when you shut down, the user is logged off ( and the mount is unmounted ) before the rest of the fstab mounts are unmounted and before the network is brought down.

Anyway if you can live with all that you have two choices:

[1] Put the gvfs-mount command in your start up applications, Or

[2] Use gigolo: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

Gigolo has a couple of advantages:

- It's a GUI ( if you think that's an advantage :wink: )
- It has a far more sophisticated method of automounting in that it will poll the network at user specified intervals and mount only when the remote box is up and running and the share is available.

---

