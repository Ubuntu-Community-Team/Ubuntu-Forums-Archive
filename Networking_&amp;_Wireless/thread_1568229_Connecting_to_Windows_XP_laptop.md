---
title: "Connecting to Windows XP laptop"
date: 2010-09-04
forum: Networking &amp; Wireless
---

### Post by scyntax on 2010-09-04
After many hours of searching forums, help files, turning on/off firewalls, etc, I need someone far smarter than myself to help me connect to the above machine. I also looked into Samba and do not understand how to use it. It is installed on my Linux laptop, but I have no idea how to access it. I'm hoping that connecting to my Windows laptop is a fairly simple process. Thank you.

---

### Post by BkkBonanza on 2010-09-04
First, how are you physically connected? A direct cable or via a router?

Which way do you want to go for Samba? Get access to files on the Windows laptop, or allow access from the laptop to files on the Ubuntu machine?

This info will help with what direction to go.

---

### Post by scyntax on 2010-09-04
Thanks for the quick reply. I'm connecting wirelessly through a router. I would like the Windows machine to access files on the Linux machine.

---

### Post by BkkBonanza on 2010-09-04
Probably your first step is to make sure the systems can talk to each other.
On Ubuntu open a terminal and type **ping IP** where IP is the IP or hostname of the Windows system.
If this doesn't work then you know you have network or firewall issues.
You should see a repeated list of success messages with times. If it just sits there or outputs an error, then the link isn't being made.

You can also repeat this test on the Windows system. Sometimes one direction is blocked and the other not.

---

### Post by scyntax on 2010-09-05
Pinging from both machines is successful. Perhaps I am looking in the wrong place for the Windows machine. I click on Network in Places and then click on Windows Network. Is this the right place?

---

### Post by BkkBonanza on 2010-09-05
That's right. You should be able to see it there but I've noticed that often it doesn't get enumerated properly. I usually have to type in the address to get to windows machines. 
eg.
smb://192.168.1.3/

Not sure why that is but probably some setting related to workgroups/domains or browseable options.

Once you get it by address you can save it as a bookmark.

---

### Post by scyntax on 2010-09-05
You were right,it doesn't get enumerated properly. typing in the address got me right to the machine. However, i am unable to copy a file into the SharedDocs folder. When I open this folder, the Paste option in greyed out. If I try to copy it to the screen showing all the folders on the Windows machine, I get this error: There was an error copying the file into smb://192.168.1.8. Operation not supported by backend. So, with your help, I am making progress.

---

### Post by BkkBonanza on 2010-09-05
Hmmm. I don't know what that error means. I've had "permission denied" type errors where you had to have more access rights. This may be related to the screen you had not being a suitable destination maybe.

Have a look at the share permissions on the Windows machine. If it isn't "read and write" for "all" users (forget the terms they use there) then that's likely it. Try using a share that has no access restrictions to test.

---

### Post by scyntax on 2010-09-05
Eureka! You, my friend are a genius :KS.  Your "permission denied" comment brought it all together. Once I changed the attributes on the Windows side to "allow network users to change my files", I was able to copy over the file. Thanks very much for your assistance! ):P

---

### Post by BkkBonanza on 2010-09-05
Great! Glad to help.

I'm sure there's a setting to make it browseable.

---

### Post by BkkBonanza on 2010-09-06
See this thread for things to try to solve the browsing issue.
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

