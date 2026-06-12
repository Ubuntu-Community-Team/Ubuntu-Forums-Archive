---
title: "gvfs and Windows permissions"
date: 2012-09-16
forum: Networking &amp; Wireless
---

### Post by inhumangeek on 2012-09-16
I have a Windows XP virtual machine. I want to access some of its folders in order to back up their contents.

I specifically want to connect to 
[FONT="Courier New"]C:\Documents and Settings\emma\My Documents\[/FONT] and
[FONT="Courier New"]C:\Documents and Settings\paul\My Documents\ [/FONT]
I have set each of these up as shared folders within XP, allowing users to change the files.

Using gvfs I can connect to the "paul" one just fine (including writing files), but I cannot do the same with "emma". My Ubuntu username is also paul, I suspect this may be the issue? The specific error message is 
```
gvfs-mount smb://192.168.0.11/emma_itunes
Error mounting location: Failed to mount Windows share
```

I tried to connect to a higher level ([FONT="Courier New"]C:\Documents and Settings[/FONT]) but after I have mounted the folder I cannot descend into either emma or paul (with the same error message).

On the VM, the user paul is an administrator, if that makes a difference. Can anyone please advise the best way to share the VM's folders, no matter who owns them? 

Just to cut short any fstab suggestions - I tried this route originally but I cannot mount the shares at (Ubuntu) boot-time, as the VM will not be live at this point. Which is a shame as in fstab you can add username and password... just thought - is there an equivalent in gvfs I wonder (will research after posting this thread!)

For background info, I have tried doing the backups from within Windows, using SynchToy and xcopy but for some reason it will not push files over the network... plus I want to do as many of my jobs from within Ubuntu rather than Windows; I would like to minimise the amount of admin I have to do within Windows.

Thanks!

---

### Post by inhumangeek on 2012-09-16
Hmm I tried using 
```
gvfs-mount smb://emma@192.168.0.11/emma_itunes
```

But it asks for a password and there isn't one, and when I set a password for emma within Windows it isn't accepted by gvfs.

---

### Post by Morbius1 on 2012-09-16
> Error mounting location: Failed to mount Windows shareDoes emma have access to the shared folder on the WIndows VM itself? Not from the Linux client I mean if emma logs into the Windows VM does she have access to the folder that is shared.

That error is usually not a Samba error but a permissions error on the server.

---

### Post by inhumangeek on 2012-09-17
> Does emma have access to the shared folder on the WIndows VM itself? 

Yes it would appear so. Thanks for helping!

---

### Post by Morbius1 on 2012-09-17
I can't reproduce your problem so let's start with some basics. Please post the output of the following command from Linux:
```
smbtree
```
When it asks you for a password just hit enter.

---

### Post by inhumangeek on 2012-09-18
```
WORKGROUP
	\\XP-VIRTUAL     		
		\\XP-VIRTUAL\paul_itunes    	
		\\XP-VIRTUAL\C$             	Default share
		\\XP-VIRTUAL\ADMIN$         	Remote Admin
		\\XP-VIRTUAL\emma_itunes    	
		\\XP-VIRTUAL\IPC$           	Remote IPC
	\\DEEPTHOUGHT    		deepthought server (Samba, Ubuntu)
cli_start_connection: failed to connect to DEEPTHOUGHT<20> (0.0.0.0). Error NT_STATUS_HOST_UNREACHABLE

```

Thanks.

I should clarify - in my original post, for previty, I said I wanted to connect to "My Documents" in each user's area. Ideally I want to go down deeper, straight into "My Documents\My Music\iTunes" - I want to backup each person's iTunes library. Hence why the two shares are called name_itunes.

---

### Post by Morbius1 on 2012-09-18
And you are using Windows "Simple Sharing" so when you shared the iTunes folder it looked like this?

---

### Post by inhumangeek on 2012-09-18
Yes that's the badger. I used the same method for both paul_itunes and emma_itunes... 

I am inferring from this that there is a less simple method?

---

### Post by Morbius1 on 2012-09-18
There is a less than simple method and I was hoping that you used it only because it would have been the only thing that would come close to explaining your symptoms.

The Simple Sharing method creates a Samba-like guest share where everyone and his Aunt Agnes has access and would in no way exhibit what you are seeing.

What I did was go to a WnXP box and added a new user, then created an iTunes folder and shared it as you saw above. I have no issues accessing that folder. Now this was a real WinXP box not a VM but if you have "bridge mode" enabled for Networking on the VM guest then I don't think it would have made an difference.

I'm trying my best to reproduce this error but I'm at a loss at the moment.

---

### Post by inhumangeek on 2012-09-19
Well thanks for taking the time anyway, at least I know I haven't done anything obviously stupid.

I might try re-installing Windows at some point anyway, hopefully the problem will go away...

Thanks again.

---

