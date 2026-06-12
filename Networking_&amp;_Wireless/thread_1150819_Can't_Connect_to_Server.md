---
title: "Can't Connect to Server"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by Highlygifted on 2009-05-06
I've recently set up Ubuntu Hardy Heron in the tech lab in school on a custom built computer. Internet is hooked up and everything, and I'm using it to type this out even now. Yet whenever I try to find a Best Server or update, even install simple programs such as VLC or Wine, I'm confronted with the same issue-

W: Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy/Release.gpg](http://archive.linux.duke.edu/ubuntu/dists/hardy/Release.gpg)  Could not connect to archive.linux.duke.edu:80 (152.3.102.53). - connect (111 Connection refused)

 This occurs in the same format for everything I have, which leads me to sit here baffled. I've enabled universe and multiverse and such, but I'm still getting this problem.

 Please and thank you for the help.

---

### Post by tricolorpoa on 2009-05-06
Did you try to resolve these names to an IP address?

```
$ nslookup archive.linux.duke.edu
Server:        x.x.x.x
Address:    x.x.x.x#53

Non-authoritative answer:
Name:    archive.linux.duke.edu
Address: 152.3.102.53

```

---

### Post by Highlygifted on 2009-05-07
How would I go about doing that? I'm a complete newbie to Ubuntu, so precise instructions would be appreciated.

---

### Post by tricolorpoa on 2009-05-07
You can press Alt + F2 keys.. Then a pop-up windows will open and you can run *gnome-terminal*. Then a white screen will open and a prompt will be wainting for your commands...

So you can run the commands above and many others... :popcorn:

---

