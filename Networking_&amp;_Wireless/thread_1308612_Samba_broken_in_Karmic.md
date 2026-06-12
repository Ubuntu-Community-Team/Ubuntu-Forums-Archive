---
title: "Samba broken in Karmic"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by mendieta on 2009-10-31
Hi

I spent a good couple hour today Googling around once I realized my home Samba shares (between Kubuntu machines) were broken, as a result of upgrading to Karmic (they were ok in Jaunty).

Once I concluded this was a real bug, I thought "hell, this must be hitting a lot of people", and sure enough, lots of post but no workarounds. 

I decided to add the "proposed" updates, refreshed the sources, and there they were, a bunch of updates for samba. I got them all, and samba is working again :D

I thought I'd share.

Keep in mind these proposed updates are not very safe in general, so if you try this please un-check that repository after the fix. Otherwise, these packages will becomes regular updates after some testing.

Cheers!

---

### Post by potam on 2009-11-01
Could someone please post the original smb.conf file? I screwed up mine :(

---

### Post by headvampyre@hotmail.co.uk on 2009-11-01
[global]
  workgroup = domain/workgroup here
  netbios name = your server name here
  unix password sync = yes
  map to guest = bad password
  guest ok = yes
  logon home = \\%L\%U
  logon drive = drive you want to logon to here e.g S:
  logon script = logon.cmd
  server string = Samba Server

[homes]
  comment = Home Directories
  path = /home
  read only = no
  browseable = yes
  guest ok = no

[shared folder]
  comment = shared folder
  path = to your shared folder
  read only = no
  browseable = yes
  guest ok = yes

---

### Post by 3rdalbum on 2009-11-01
If Samba was broken, it wasn't broken for everyone. It's been running beautifully here since Karmic Beta.

---

### Post by potam on 2009-11-01
> **3rdalbum said:**
> If Samba was broken, it wasn't broken for everyone. It's been running beautifully here since Karmic Beta.

For me I can see other shares and connect to them. I can create a share, but nobody can connect to it, not even me.

Edit: I noticed this is due to my encrypted home folder. I created a [separate thread]("http://ubuntuforums.org/showthread.php?t=1309334") for this problem.

---

### Post by mendieta on 2009-11-01
> **3rdalbum said:**
> If Samba was broken, it wasn't broken for everyone. It's been running beautifully here since Karmic Beta.

I see, thanks! I just saw several posts saying exactly the same: it was working in Jaunty and broke with the Karmic upgrade. Did you upgrade or have a clean install? 

In any case, I am glad things are working again here.

---

### Post by fonque on 2009-11-11
mendieta, Thank you! 
I just upgraded to karmic today and it broke samba for me as well.
Thanks for the fix.

---

### Post by aabate58 on 2009-11-12
> **mendieta said:**
> Hi

I spent a good couple hour today Googling around once I realized my home Samba shares (between Kubuntu machines) were broken, as a result of upgrading to Karmic (they were ok in Jaunty).

Once I concluded this was a real bug, I thought "hell, this must be hitting a lot of people", and sure enough, lots of post but no workarounds. 

I decided to add the "proposed" updates, refreshed the sources, and there they were, a bunch of updates for samba. I got them all, and samba is working again :D

I thought I'd share.

Keep in mind these proposed updates are not very safe in general, so if you try this please un-check that repository after the fix. Otherwise, these packages will becomes regular updates after some testing.

Cheers!

Thank you, I was having a helluva time with samba, and your suggestion worked!  Samba is working as it should now.

Thanx man!
-Al

---

### Post by wally the duck on 2009-11-17
Broken for me, too... two clean Karmic installs on two different machines; broken on both. The 'proposed updates' did NOT fix the issue.
Basically: set a folder as 'shared' and the little colored arrow icons show up above the folder in Nautilus. Restart the computer and they are gone... and the folder is not seen on the other machines on the network. The folder is still set as a shared folder, but not seen.
You can 'connect to...' with the computer name manually, however.

---

### Post by dmizer on 2009-11-17
> **wally the duck said:**
> Broken for me, too... two clean Karmic installs on two different machines; broken on both. The 'proposed updates' did NOT fix the issue.
Basically: set a folder as 'shared' and the little colored arrow icons show up above the folder in Nautilus. Restart the computer and they are gone... and the folder is not seen on the other machines on the network. The folder is still set as a shared folder, but not seen.
You can 'connect to...' with the computer name manually, however.

Please see the 6th link in my sig.

---

### Post by IConrad01 on 2009-11-19
> 
Please see the 6th link in my sig.
__________________  The fix suggested for karmic had absolutely no impact on my problem.  I had a fully operational Samba configuration on Jaunty; since upgrading to Karmic I have had no functionality.  I can navigate path shares via smb:// -- but it is mind-numbingly slow, and doesn't see the files in the directories.

Is there another resource that can actually address this problem?

---

### Post by dmizer on 2009-11-19
> **IConrad01 said:**
> The fix suggested for karmic had absolutely no impact on my problem.  I had a fully operational Samba configuration on Jaunty; since upgrading to Karmic I have had no functionality.  I can navigate path shares via smb:// -- but it is mind-numbingly slow, and doesn't see the files in the directories.

Is there another resource that can actually address this problem?

You should try _**all**_ the fixes suggested. If you still have a problem after that, then post back and I'll help you work through it.

---

