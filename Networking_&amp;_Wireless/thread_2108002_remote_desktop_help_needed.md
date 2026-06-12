---
title: "remote desktop help needed"
date: 2013-01-23
forum: Networking &amp; Wireless
---

### Post by bill-lancaster on 2013-01-23
I have two pcs each runing Kubuntu 12.10 and connected to the same router (both wirelessly).

I have looked at krdc (because it was available on the start menu!), entering the ip address of the other computer using vnc produces "server not found".  Entering the ip address under rdp just gives me a blue screen.

I don't really know wht I'm doing so any help would be appreciated.

---

### Post by bill-lancaster on 2013-01-24
OK, have learned a bit more.

I installed krfb on the 'remote' pc and set it up.

Then using KRDC on the 'local' machine I achieved remote control of the desktop.

It all worked well but was slow and is not practical for every day purposes so I'll now see if I can fit in a second monitor somewhere.

---

### Post by jonobr on 2013-01-24
remote desktops etc chew a lot of bandwidth and tend to be slow.

I would recommend trying as much remote administration as possible using ssh.
You can see what this is like on the [terminal]("https://help.ubuntu.com/community/UsingTheTerminal")

Of course there will be stuff you cannot avoid, but again, if your doing routine stuff
(copying files, moving stuff around, administering applications on the remote machine) then using CLI is the way to go in my opinion.

---

### Post by ahallubuntu on 2013-01-24
I have been using remote desktop for years in Ubuntu.  (I also use ssh directly sometimes.)  Yes, remote desktop takes more bandwidth, but setup properly it can be much easier to use than ssh.  I would never want to give it up.

One trick to improve performance: limit the color to 8 bits.  (Easy to do in Gnome with vinagre, no idea how to do it with whatever you are using in KDE.)  That reduces the amount of data transferred and should speed up the responsiveness.  Of course, 8 bit color looks terrible so it's not a replacement for an every-day screen access but for doing admin it works fine.

---

### Post by sudodus on 2013-01-24
You can also run GUI programs using
```
ssh -X user@server
```

---

### Post by jonobr on 2013-01-24
When rdp to windows I would always set the target to low colors, black background and as minimal as possible,

---

