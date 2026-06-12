---
title: "Problems connecting to Windows 7"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by AmrH on 2009-11-15
Whenever I try to connect to Windows 7 PC by going to network places then Network, it tells me that it failed to retrieve share list from server. Also when I try to connect via SAMBA, it gives my the same problem. Any solution for that? I mainly wanna print to the printer connected to Win7 and I can't do it.

---

### Post by dmizer on 2009-11-15
Please see the 6th link in my sig.

---

### Post by AmrH on 2009-11-15
I'm going to try you tutorial right now, and I will give feedback.

EDIT: Your tutorial worked like a charm. The Win7 PC appears now in my network; however, when I enter the username and password, it still tells me to enter them again and again. I have tried changing the password on the windows machine and tried again, but couldn't connect. Is there a solution for this problem?

---

### Post by dmizer on 2009-11-15
What is the output of:
```
sudo iptables -L
```

---

### Post by AmrH on 2009-11-16
> Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

That's what I use when trying to connect:

User: Amr (My Account on the Windows Machine)

Domain: WORKGROUP

Password: (my password)

---

### Post by Lagos on 2009-11-16
I have the same exact problem. I can see the windows7 computer on the network, however if I try to access it I get a dialog box asking for name and password that never authenticates. 

However If I reboot into XP, I get the same dialog box, enter in my user name/password and it logs me in and allows me to brows the shares just fine.

Here is the output of mine, which I believe shows no firewall running, right? 

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

---

### Post by dmizer on 2009-11-16
> **AmrH said:**
> (My Account on the Windows Machine)

If this is different than your account on your Ubuntu machine, this is why you're having a problem. Ubuntu has difficulty with sending usernames that are not on the system. You need to either add your Ubuntu account name to the Windows box, or allow guest access.

If neither of those are an option, then you'll probably need to mount the share with CIFS as outlined in the 2nd link in my sig.

---

### Post by gwu777 on 2009-11-16
Here is what worked for me...

Change the setting in windows 7 for the connexion encryption from 128bit to 40 to 56bits in the network center, advanced settings...

I now have access to my windows7 pc ok. Is the problem that ubuntu doesn't support this encryption yet or that I haven't set it up correctly. Mind you I haven't setup anything, just an out of the box install!

Cheers! :)

---

### Post by gwu777 on 2009-11-16
> **dmizer said:**
> Ubuntu has difficulty with sending usernames that are not on the system.

Have more faith!!! Ubuntu does the job fine ;):P

---

### Post by AmrH on 2009-11-16
I've tried all the above suggestions. My account is the same as on the Win machine, the only difference is the password. I created another account on both machines, and still doesn't work. I've turned Guest account on and tried to log in, and still doesn't work. I adjusted the network encryption, and no response. I've noticed something by the way. In Ubuntu, when I try to open the $printer share, it asks for authentication and I enter my Ubuntu's user and pass, and still doesn't work!

Edit: Right now I've tried connecting to a WinXP box in my network, and it worked fine. Even though the box is pass protected, it didn't ask me for a pass!

---

### Post by Lagos on 2009-11-17
> **AmrH said:**
> I've tried all the above suggestions. My account is the same as on the Win machine, the only difference is the password. I created another account on both machines, and still doesn't work. I've turned Guest account on and tried to log in, and still doesn't work. I adjusted the network encryption, and no response. I've noticed something by the way. In Ubuntu, when I try to open the $printer share, it asks for authentication and I enter my Ubuntu's user and pass, and still doesn't work!

Edit: Right now I've tried connecting to a WinXP box in my network, and it worked fine. Even though the box is pass protected, it didn't ask me for a pass!

This is also my experience from trying the fixes listed above. The login name and password on the windows7 machine is the same as the ubuntu laptop, yet the i just get stuck in an endless loop that will not authenticate.

---

### Post by Lagos on 2009-11-17
> **dmizer said:**
> If this is different than your account on your Ubuntu machine, this is why you're having a problem. Ubuntu has difficulty with sending usernames that are not on the system. You need to either add your Ubuntu account name to the Windows box, or allow guest access.

If neither of those are an option, then you'll probably need to mount the share with CIFS as outlined in the 2nd link in my sig.

Thank you for your help. Even though my issues is still not resolved, its good to know someone who has a good grasp on things is trying to help! 

I haven yet tried mounting the share, but I will try that next.

However I wanted to ask, have you ever tried filing bug reports for the issues you found and your proposed work arounds?

---

### Post by dmizer on 2009-11-17
> **Lagos said:**
> However I wanted to ask, have you ever tried filing bug reports for the issues you found and your proposed work arounds?

I have only filed bug reports on the problems I've personally encountered. Since I've not had a Windows computer in my network for probably 4 years or so now, I also haven't used Samba in my network.

All of what goes into my howto's and all the information I know about Samba is what I've gathered by trying to help others with their problems.

Try logging into the Windows share with "guest" as the user name.

---

### Post by Lagos on 2009-11-17
> **dmizer said:**
> I have only filed bug reports on the problems I've personally encountered. Since I've not had a Windows computer in my network for probably 4 years or so now, I also haven't used Samba in my network.

All of what goes into my howto's and all the information I know about Samba is what I've gathered by trying to help others with their problems.

Try logging into the Windows share with "guest" as the user name.

Still the same problem. Used guest with no password and then I tried guest with my normal user password. The dialog box just keeps popping back and doesn't authenticate. 
I did a google search and noticed other people had reported the same problem in the past. 

What do you use instead of samba to network the linux machines?

---

### Post by dmizer on 2009-11-17
> **Lagos said:**
> What do you use instead of samba to network the linux machines?
I use NFS. The howto I use is located in the 4th link in my sig.

---

### Post by AmrH on 2009-11-17
Seems like we're never gonna be able to connect to Windows 7. Hope this can be fixed soon!

---

### Post by dmizer on 2009-11-17
> **AmrH said:**
> Seems like we're never gonna be able to connect to Windows 7. Hope this can be fixed soon!

My Karmic test box can connect and view shares on my Win7 test box without problems. There is a configuration issue somewhere. If you're using the default /etc/samba/smb.conf file, you've followed my howtos, and you still can't get connected ... the problem is most likely on your Win7 box.

---

### Post by dmizer on 2009-11-17
> **Lagos said:**
> This is also my experience from trying the fixes listed above. The login name and password on the windows7 machine is the same as the ubuntu laptop, yet the i just get stuck in an endless loop that will not authenticate.

As odd as it may seem, you may have better luck if you have different logins on your Ubuntu and Win7 machines.

---

### Post by AmrH on 2009-11-17
I've to say also that these are my sharing settings in Win7:


[IMG]http://img252.imageshack.us/img252/2938/sharingsettings.png[/IMG]

---

### Post by dmizer on 2009-11-17
I suggest changing "HomeGroup connections" to:
> Allow Windows to manage homegroup connections (recommended)

---

### Post by AmrH on 2009-11-30
I did so; however, it still doesn't wanna work. The authorization box goes into an infinite loop. I hope this problem would be fixed one day.

---

### Post by dmizer on 2009-11-30
> **AmrH said:**
> I did so; however, it still doesn't wanna work. The authorization box goes into an infinite loop. I hope this problem would be fixed one day.

Try these suggested fixes: [http://ubuntuforums.org/showpost.php?p=8395627&postcount=249](http://ubuntuforums.org/showpost.php?p=8395627&postcount=249)

---

### Post by AmrH on 2009-12-06
> **dmizer said:**
> Try these suggested fixes: [http://ubuntuforums.org/showpost.php?p=8395627&postcount=249](http://ubuntuforums.org/showpost.php?p=8395627&postcount=249)

Still not working!!!!! I really don't know why is that happening to me!!

---

