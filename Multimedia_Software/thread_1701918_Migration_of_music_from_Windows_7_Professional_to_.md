---
title: "Migration of music from Windows 7 Professional to Ubuntu 10.10"
date: 2011-03-07
forum: Multimedia Software
---

### Post by totalanonymity on 2011-03-07
I have a Windows 7 partition with all my music. I'm a beginning Ubuntu user and I really like it and so would like to have my music in Ubuntu to create playlists and such since I'm spending more time here (in Ubuntu) and will likely spend most of it unless I require a very specific process. As it stands, I've been going back to my Windows partition purely because my playlists are all set up and all my music is in my music player.

How do I migrate the music from that partition to my Ubuntu one without simply copying GBs and GBs of music and taking up twice the space for the same thing?

Please refrain from suggesting an external drive, as I don't have the money for one currently. Please attempt to help out in a way that only requires what is possible with the information provided.

Thank you for any and all help.

---

### Post by aeiah on 2011-03-07
if your windows partition mounted in ubuntu? this will give access to all your windows files. you could also mount bind the windows music folder to your ubuntu home music folder, so it appears as though its in your home directory.

whether you just mount the whole windows drive, or whether you mount the windows drive and then mount bind the music directory doesnt matter so much - you should still be able to point your music player of choice towards your music collection.

---

### Post by totalanonymity on 2011-03-07
How exactly does one go and mount it or mount bind the music directory? As previously stated, I'm really quite new to all this. I know there is a "mount" menu option for my NTFS partition, but I've read somewhere on here in posts that sometimes that wouldn't stay mounted if you powered down the system? I don't know.

Thanks for the reply. :)

---

### Post by ajgreeny on 2011-03-07
Install ntfs-config and it will allow you to set the windows partition(s) as mounted at boot time, according to your wishes.  It is better if you try to keep the windows OS partition unmounted if possible, and only mount the data partition, if it is separate, which is often the case in Win7 I believe.

You could also do it manually by editing the **/etc/fstab** file using ```
gksudo gedit /etc/fstab
```which allows you to edit it as root.  Make sure you have the mount partition needed first with ```
sudo mkdir /media/storage
```Then you would need to add a line to fstab in pattern:-
```
UUID=x#x#x#x#x##x# /media/storage/    ntfs-3g        auto,user,rw 0 0
```The UUID of the windows partition can be found with ```
sudo blkid
```Come back again if this is all too confusing.

---

### Post by totalanonymity on 2011-03-07
To my understanding, the Windows 7 partition is one partition, aside from the recovery sector, as it calls it. How would I be able to mount only, say, my media from the partition and not the rest of it? Is there any possible way to do so?

And yes, the instructions are a bit confusing, for someone as new to this as me.

I, at least, got the UUID part right! Ha.

Also, why the comment on saying it should be unmounted, if at all possible? Is something bad with it being mounted?

---

### Post by ajgreeny on 2011-03-07
> **totalanonymity said:**
> To my understanding, the Windows 7 partition is one partition, aside from the recovery sector, as it calls it. How would I be able to mount only, say, my media from the partition and not the rest of it? Is there any possible way to do so?

And yes, the instructions are a bit confusing, for someone as new to this as me.

I, at least, got the UUID part right! Ha.

Also, why the comment on saying it should be unmounted, if at all possible? Is something bad with it being mounted?
Well done so far.

When I had a windows partition to worry about, I did not mount it by default at boot time, as I felt it would be too easy to mess up the M$ OS files and folders, and even delete them with no problem, if I was not careful.    Much better, as I said, to keep your data folders separate from the OS.

Just so we know what is going on here, can you show the output from the command ```
sudo fdisk -l
```as it will let us see your partition layout much clearer.

---

### Post by FoxEWolf on 2011-03-07
You should have access to your Windows files if you have them on the same drive and mount both partitions at startup, but if you don't the easiest thing to do is to boot into windows and copy all of your music via External Drive (Flash Drive; Firewire Ext HDD) and you should be able to get them that way.

---

