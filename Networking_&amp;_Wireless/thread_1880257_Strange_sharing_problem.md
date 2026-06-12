---
title: "Strange sharing problem"
date: 2011-11-13
forum: Networking &amp; Wireless
---

### Post by joalin on 2011-11-13
Hi, I have recently started using Ubuntu, and finally decided to install Ubuntu from scratch in my desktop pc. Most things work now, but I've got this strange sharing problem.

From my Ubuntu desktop, connected on a wired connection, I can see my windows WORKGROUP, with all other pcs and settop boxes, and I can access them all, but my shared disk at the Ubuntu desktop can't be seen, neither the desktop at all. I've tried to change from DHCP to manual, without luck, and I have checked the smb.conf that it's WORKGROUP, and also checked I have some folders and a disk shared, but still I cant see it at all. What am I doing wrong?

They are all on the 192.168.1.XXX subnet and in same workgroup, connected to same router. Please give me a few hints what to do.

Some other questions. I can just see the shared symbol when I'm logged in as root, not else, but I get an error 255 usershare returned when I try to share it with my other user, but it's not a big deal to me if the disk is always shared nevertheless...

best regards Joacim

---

### Post by Paddy Landau on 2011-11-13
Hi Joacim

The tool you need is Samba -- you seem to already know that.

Please check that you have both [FONT=Fixedsys]system-config-samba[/FONT] and [FONT=Fixedsys]nautilus-share[/FONT] installed.

Stay with DHCP; you don't need manual.


[LIST]
[*]Check that every computer and device attached to the network has a different name. In Ubuntu, the name is in both /etc/hostname and /etc/hosts. Reboot if you change those.
[/LIST]

[LIST]
[*]Ensure that the folder you chose to share is indeed shareable (check the folder's settings). Do other computers need to log in to access your Ubuntu's shared folder, or do you want it available to anyone on your network?
[/LIST]

> **joalin said:**
> Some other questions. I can just see the shared symbol when I'm logged in as root...
Please, please, do not log in as root! This is not supported on these forums. If you need to do anything as root, temporarily gain root privileges with sudo (for the command line) or gksudo (for any GUI program).

Your [FONT=Fixedsys]smb.conf[/FONT] may need configuring, because the default set-up of Samba can be faulty. If the above changes do not work, post back here.

---

### Post by capscrew on 2011-11-13
> **joalin said:**
> Hi, I have recently started using Ubuntu, and finally decided to install Ubuntu from scratch in my desktop pc. Most things work now, but I've got this strange sharing problem.

From my Ubuntu desktop, connected on a wired connection, I can see my windows WORKGROUP, with all other pcs and settop boxes, and I can access them all, but my shared disk at the Ubuntu desktop can't be seen, neither the desktop at all. I've tried to change from DHCP to manual, without luck, and I have checked the smb.conf that it's WORKGROUP, and also checked I have some folders and a disk shared, but still I cant see it at all. What am I doing wrong?

They are all on the 192.168.1.XXX subnet and in same workgroup, connected to same router. Please give me a few hints what to do.

It looks like you need to setup the Samba host NETBIOS name explicitly.  If the hostname is less than 15 characters you should use that.  To find the hostname you can use this command from the CLI```
hostname 
```
Edit the /etc/samba/smbconf file.  Add this to the [global] section of the file (use the real hostname instead of <hostname>)```
netbios name = <hostname>
name resolve order = bcast
```

You need to edit the file as root.  You can use gedit using sudo like this from the CLI ```
gksudo gedit /etc/samba/smb.conf
``` 

For a complete explanation of this see [**_[COLOR="DarkSlateGray"]here [/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1879527")starting with post #4.> 

Some other questions. I can just see the shared symbol when I'm logged in as root, not else, but I get an error 255 usershare returned when I try to share it with my other user, but it's not a big deal to me if the disk is always shared nevertheless...

best regards Joacim
This might be due to the way you setup the usershare.  You should not create usershares as the root user.

Edit: Sorry Paddy, I didn't see your post.  To the OP; both Paddy Landau and I are pointing you to the same resolution.

---

### Post by joalin on 2011-11-13
Thanks alot guys for your excellent help, both Paddy and Capscrew. 

It worked by changing the hostname which was terribly long. I also unshared the disk as root and shared it as a normal user, and suddenly it worked.
 I've spent all saturday and sunday without getting it to work, and when you helped me in the right direction it seemd so easy! Thanks again! 

and yes, I'll keep away from root in the future it's just that it's hard when you dont know the terminal syntax being a noob :-)

---

### Post by Paddy Landau on 2011-11-14
Glad you got it solved. Capscrew is excellent at getting Samba to work.

Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

