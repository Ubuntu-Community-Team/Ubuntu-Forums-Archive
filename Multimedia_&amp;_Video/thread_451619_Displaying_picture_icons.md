---
title: "Displaying picture icons"
date: 2007-05-22
forum: Multimedia &amp; Video
---

### Post by pluto1111 on 2007-05-22
I'm running Ubuntu 6.10 and have set up a separate user account for my wife. I then created a group called pictures, and assigned my wife and myself to this group.   Inside my wife's account, I created a symbolic link to a folder on my desktop called pictures so we can both access and share our pictures.  However, I'm running into 2 problems: 1 - if I load the pictures onto the computer (via compact flash), my wife cannot view the newly created folder with the pictures inside (it's locked) due to the default group being my user account name, not pictures (the shared group).  The same thing happens if my wife loads the pictures onto the computer under her account, the folder is locked for me.  At this time, I have to manually assign the  folder and all the files inside to the pictures group.  I'm wondering if there is an easy way to automate the process so "pictures" is the default group for both of us, or if anyone has a better idea of how to make this easier?  

The 2nd issue I discovered is the actual picture thumbnail is not displayed, rather the generic picture icon, when viewing the contents of the folder.  This is happening only inside my wife's account on a folder I loaded first onto my desktop, then changed the group to pictures (our shared group).  I discovered when the file is renamed, the actual picture image is then displayed as the icon, but this is the only way I've discovered to display the actual picture for the icon.  I checked the Any suggestions?

Thanks.

---

### Post by reclusivemonkey on 2007-05-22
> **pluto1111 said:**
> I'm running Ubuntu 6.10 and have set up a separate user account for my wife. I then created a group called pictures, and assigned my wife and myself to this group.   Inside my wife's account, I created a symbolic link to a folder on my desktop called pictures so we can both access and share our pictures.  However, I'm running into 2 problems: 1 - if I load the pictures onto the computer (via compact flash), my wife cannot view the newly created folder with the pictures inside (it's locked) due to the default group being my user account name, not pictures (the shared group).  The same thing happens if my wife loads the pictures onto the computer under her account, the folder is locked for me.  At this time, I have to manually assign the  folder and all the files inside to the pictures group.  I'm wondering if there is an easy way to automate the process so "pictures" is the default group for both of us, or if anyone has a better idea of how to make this easier?

I've never quite understood why Ubuntu doesn't make the main/default group for all users "users". For you and your wife, go to System --> Administration --> Users and Groups. From there, click on the respective users, and then "Properties" on the "Main Group" section, choose "users". This should fix that issue; from the sounds of it you have a clear idea of users/groups/permissions; you're just being thwarted by Ubuntu's screwy defaults!

Now all you have to do is swap the group permissions. I am suggesting this way rather than using the group "pictures" as it may be you and your wife want to share more than just pictures, and by using the "users" group, you should be able to manage this. If this doesn't solve your issues, please post back.

---

### Post by pluto1111 on 2007-05-25
Thanks for your help, problem solved!

---

