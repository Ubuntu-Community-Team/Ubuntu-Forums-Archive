---
title: "Trouble getting samba to talk to win vista"
date: 2011-08-18
forum: Networking &amp; Wireless
---

### Post by jb0nez on 2011-08-18
Hi there,
Just installed 11.04. Installed samba. Using the GUI tool I set up a share. I made sure my workgroup = workgroup to match the widoes system. On the windows machine, my ubuntu system doesn't show up in the network browser. So I ran \\191.168.0.69 (IP of Ubunut machine) and at the username and password prompt I entered my ubuntu username and pass; it then says Logon Unsuccseful. Then it puts my windows system name into the login box and offers to let me log in again:
WINVISTA\username

So I tried with that username and my ubuntu username and same thing, logon unsuccesful.

From the ununtu side, when I go to Network -> Windows Network -> Workgroup I see the WINVISTA machine. I double click it and it give me a listing of the shared folders. When I double-click one, say, Public, I am presented with a login screen with username, workgroup, and password. I use a username and account from the windows system and it just gives me the login screen again. However, if I use a different account name and password from the system, it works ok, I can see the files. I don't understand why the main account for the system doesn't work. But at least I can get to my files.

My main problem is why I can't do the reverse, log in to my Ubuntu share from my windows system. I of course suspect operator error, but I don't know what that error is. I've confirmed smbd -f is running. Any suggestions?

Just for testing I am trying to run smbd with the -l option, but everytime I kill smbs, another one restarts instantly, and when I try to run sudo smbd -l /var/log is just gives me another command prompt, and smbd will still be running as smbd -F. I can't find the rc script that starts it either. What's the proper way to stop a service then restart it with a different command line paramater?

---

### Post by papibe on 2011-08-18
Let's tackle the first problem (server not accessible by name). The process that broadcast the server name is called nmbd. Check is your server is running it.
```
$ ps aux | grep mbd
root       678  0.0  0.2  15332  3912 ?        Ss   Aug16   0:00 smbd -F
root       720  0.0  0.0  15332  1188 ?        S    Aug16   0:00 smbd -F
root      1011  0.0  0.1   8672  1624 ?        Ss   Aug16   0:01 **[COLOR="Red"]nmbd -D[/COLOR]**
pablo     4099  0.0  0.0   3328   868 pts/1    S+   21:19   0:00 grep --color=auto mbd

```
If your server is not running it, there's a chance that is because of this [bug]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/572410"). I believe it can be solve updating/upgrading your systemm, but if not, there's instructions to solve it (read the comments). 

After fixing that, check again if nmbd is running and try accessing your server from Windows 7 (it may required to refresh or restart).

Regards.

---

### Post by papibe on 2011-08-18
Try this format when connecting to the shares from Windows7:
```

username:    UbuntuServerName\ubuntu_username
password:    ubuntu_username's_password
```
(Replace with the appropiate values)
Regards.

---

### Post by jb0nez on 2011-08-19
Oh, these are great suggestions, thanks!! When I get home I'll check into both and update with my results.

---

