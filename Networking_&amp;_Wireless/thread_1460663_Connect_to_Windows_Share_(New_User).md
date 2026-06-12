---
title: "Connect to Windows Share (New User)"
date: 2010-04-23
forum: Networking &amp; Wireless
---

### Post by timpeut on 2010-04-23
I am trying to connect to a Windows 7 (64 bit) share through a home network. I am able to see the Windows machine when I view the network through Ubuntu, but when I double click and try and connect to it it prompts for for a username, domain and password. I enter my Windows username (Tim) and password (something with an = in it, I'm not sure if this matters), but I'm not sure what to put in the domain box (because my Windows machine is in a workgroup, not on a domain). I've tried PEUT (the workgroup the Windows machine is on), but this does not work.

I know my way around Windows fairly well, but I've got no clue why this isn't working properly. (I have also tried disabling my firewall)

---

### Post by Morbius1 on 2010-04-23
"Windows Live Sign-In Assistant" : [http://social.technet.microsoft.com/For ... 79a5597527]("http://social.technet.microsoft.com/Forums/en/w7itpronetworking/thread/9c6f1d74-f7f0-4503-94fa-0d79a5597527")

---

### Post by timpeut on 2010-04-23
Wow, thanks a lot for that.

One other thing. I am now trying to automount it when I log on ([https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)) and am using a credentials file.

username=Tim
password=passhas=init

Do I need to escape the = sign somehow that is in my password?

---

### Post by Morbius1 on 2010-04-23
I do not know but I'm guessing it's a problem or you wouldn't be asking the question.

Consider this a bump.:wink:

---

### Post by timpeut on 2010-04-23
> **Morbius1 said:**
> I do not know but I'm guessing it's a problem or you wouldn't be asking the question.

When I try and mount it I get an error about the credential file, so I'm thinking the = sign in my pass is the problem.

---

### Post by pricetech on 2010-04-23
Easiest thing would be to change the windows password and take the = out to see if that helps.

---

### Post by timpeut on 2010-04-24
I ended up getting it working. Turned out I didn't chmod the file properly.

Having an = sign in the password didn't matter. Thanks for all the help.

---

