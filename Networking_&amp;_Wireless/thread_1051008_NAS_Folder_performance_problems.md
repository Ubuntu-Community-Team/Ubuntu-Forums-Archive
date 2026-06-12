---
title: "NAS Folder performance problems"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by mike984 on 2009-01-26
I have a Synology DS108J NAS drive on a gigabit LAN and works fine and the performance is as expected except with a folder that contains 3,030 media files.  When I use Nautilus to open this folder, it takes no less than 28 minutes to display the list of files.  If I access the folder using a Windows computer, it appears instantly.  

Once Ubuntu has the list of files, it plays the media files fine.

Displaying another folder and returning to that large folder will require the long wait again.

I turned set all the preview options to 'Never' in Nautilus Edit>Preferences>Preview

The Synology drive is at the latest firmware as well and I am using Ubuntu 8.10

Is there anything I do to speed this up?

---

### Post by dmizer on 2009-01-26
I suggest you disable thumbnail preview in Nautilus.

More discussion on this issue here: [http://ubuntuforums.org/showthread.php?p=6453646#post6452255](http://ubuntuforums.org/showthread.php?p=6453646#post6452255) in my conversation with moTaro.

---

### Post by mike984 on 2009-01-27
I made sure all the previews were off and still takes 30 minutes to display the folder. 

I don't know what else I should be checking.

---

### Post by dmizer on 2009-01-27
Is it possible for you to post the exports file from the NAS?

Also, please post your mount command from /etc/fstab.

---

### Post by mike984 on 2009-01-28
Your reply gave me a clue that the entry might need to be in fstab.

The fix was to include the following in fstab:

[FONT="Courier New"]//192.168.10.15/diskstation /mnt/diskstation cifs username=xxxx,password=xxxx,_netdev,uid=xxxx,gid=users  0 0[/FONT]

Before, I was using nautilus to just navigate to it using:

[FONT="Courier New"]nautilus smb://192.168.10.15/diskstation[/FONT]

Since I put the entry in fstab and navigate to /mnt/diskstation, the speed is as expected.

To help me learn, can anyone explain why this is faster now?  I suspect it might have something to do with Samba and CIFS (the format of the drive).

---

### Post by dmizer on 2009-01-28
Nautilus doesn't cache the network drive contents. Each time you access the drive, Nautilus reloads the content. If you mount the drive, your computer is caching the content locally.

---

