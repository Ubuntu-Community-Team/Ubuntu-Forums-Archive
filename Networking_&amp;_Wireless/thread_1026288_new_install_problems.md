---
title: "new install problems"
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by mcrene on 2008-12-31
I apologize ahead of time if this is a repeat problem. I tried a quick search but am new to this forum and ubuntu. This problem concerns networking, but also a few other things, again sorry if its in the wrong place.

I just installed ubuntu 8.10 on my Dell Insp 9300. WinXP was installed, but ubuntu seems to have removed or overwrote some important files as I can no longer boot to windows anymore. Thats problem #1.
#2 is that I also can not connect to my wireless network here at home. I can see the network, but am unable to log on. Its WEP protected, and I have put the key in multiple times, but it always comes back unable to log on.

#3 I can not mount the HDD which everything is installed on. Error msg is as follow; 
$logfile indicates shutdown (0.0) Failed to mount '/dev/sda2'
Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action.. so on so on.



So here I am, on the wifes macbook trying to get the ole pc working again... sad day.

any and all help is much appreciated.

---

### Post by mbsullivan on 2008-12-31
Hi mcrene,

> I just installed ubuntu 8.10 on my Dell Insp 9300. WinXP was installed, but ubuntu seems to have removed or overwrote some important files as I can no longer boot to windows anymore. Thats problem #1.

Are/were you planning on dual-booting? I assume that you installed Ubuntu onto a different partition or harddrive from where Windows XP was. Now, do you want to take steps to be able to control to which OS you boot?

> #2 is that I also can not connect to my wireless network here at home. I can see the network, but am unable to log on. Its WEP protected, and I have put the key in multiple times, but it always comes back unable to log on.

Make sure that you are using the WEP passphrase dialog with the "shared key" authentication method.

> #3 I can not mount the HDD which everything is installed on. Error msg is as follow;
$logfile indicates shutdown (0.0) Failed to mount '/dev/sda2'
Operation not supported Mount is denied because NTFS is marked to be in use.

You are having trouble because the drive is marked as dirty, and must be properly unmounted before it can be mounted in Linux. You should be able to force it to mount once, and afterwards it will be okay. 

Try running the following command from the terminal:

```
sudo mount -t ntfs-3g /dev/sda2 /media/disk -o force
```

If you have any questions, let me know.
Mike

---

### Post by mcrene on 2008-12-31
> **mbsullivan said:**
> Hi mcrene,
Are/were you planning on dual-booting? I assume that you installed Ubuntu onto a different partition or harddrive from where Windows XP was. Now, do you want to take steps to be able to control to which OS you boot?

[I][B]I was planning on a dual boot, until I had everything working properly than I would lose XP all together. However now it seems XP may be a loss either way. My main concern here is keeping all the pictures/bookmarks/pers files/etc that I have on this HDD
[/I][/B]

Make sure that you are using the WEP passphrase dialog with the "shared key" authentication method.

[B]*I am using just what you mentioned. That being said, I may try things without any security running at all, just to see if it will connect at all*
[/B]
You are having trouble because the drive is marked as dirty, and must be properly unmounted before it can be mounted in Linux. You should be able to force it to mount once, and afterwards it will be okay. 

Try running the following command from the terminal:

```
sudo mount -t ntfs-3g /dev/sda2 /media/disk -o force
```

[B][I]when I ran that code this was the reply
fuse: failed to access mountpoint /media/disk: no such file or directory[/I]
[/B]
If you have any questions, let me know.
Mike

thanks for the quick reply, look forward to getting this running and ridding myself of XP finally.

---

### Post by mcrene on 2008-12-31
Well I fiddled around with my router... changed my security to WPA2 Personal and that seemed to work ok with Ubuntu, the mac is working too so all seems to be ok. I am writing this from Ubuntu right now, so thats one problem down... sadly its the only one fitting for this particular forum. I will continue searching in the other forums and archives.

I'll post up if this thread becomes obsolete by my searching or rectifying the problem either way.

---

### Post by mcrene on 2008-12-31
Well I have access to the HDD now too... not sure how or why, just clickin around and it seemed to work for some reason.

All my files which I was concerned about seem to be there, so its now just backing them all up again and than I may just clean this thing out and start anew.

If anyone knows (back to networking topic sort of)
since I can no longer get into XP, is there anyway to import the Firefox bookmarks I had saved, and the Outlook email accounts I had. I was using Outlook to access my Hotmail account, but can no longer remember all the info required to fill out the Evolution Mail forms to have it access Hotmail... pop#, smtp# and such.

Thanks for the previous information/help, I would think that even with the error code it seems to have corrected the HDD mounting problem, and assisted me in figuring out the network problem.

Tom

---

### Post by mbsullivan on 2008-12-31
> 
since I can no longer get into XP, is there anyway to import the Firefox bookmarks I had saved, and the Outlook email accounts I had.

Assuming you're using FF3 or later, if you find the places.sqlite file on the original drive (by mounting it), then you should be able to import it into Firefox by going to Bookmarks -> Organize Bookmarks -> Import and Backup -> Restore -> Choose File (I think).

From [here]("http://www.lytebyte.com/2008/06/19/understanding-how-and-where-firefox-3-bookmarks-are-saved/"), it seems that the places.sqlite file is located @ : Users –> <User Name> –> AppData –> Roaming –> Mozilla –> Firefox –> Profiles –> (some random characters.default ex 2xd8htj.default) –> Bookmarks.html.

> and the Outlook email accounts I had

Seems like it should be possible. See [here]("http://www.ureader.com/msg/107013778.aspx").

Mike

---

### Post by mcrene on 2008-12-31
well once again the masses have the answer.

ff3 is filled with my old bookmarks for xp ff3.

and I just got finsihed getting evolution to access hotmail.

thanks again folks... really liking this ubuntu OS.

---

