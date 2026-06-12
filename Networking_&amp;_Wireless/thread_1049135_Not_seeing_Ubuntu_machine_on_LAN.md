---
title: "Not seeing Ubuntu machine on LAN"
date: 2009-01-24
forum: Networking &amp; Wireless
---

### Post by oldcelt on 2009-01-24
I'm totally new to Ubuntu and I've tried to find my problem in the forums.  However, I seem to have the opposite problem to others who've asked questions.

My LAN is a Windows Network and from the Ubuntu machine I can see and read folders on the Windows machines (XP Pro by the way).  However, from the Windows machines I cannot see the Ubuntu machine.  Furthermore, the Ubuntu machine shows the $Share disks which should not be visible on the network!

I guess I'm missing a setting or two somewhere?

Ken  :confused:

---

### Post by sanderj on 2009-01-24
Have you shared anything on the Ubuntu machine? Using Nautilus, right click on a directory and select Sharing Options. Then choose what you need to choose. 

After a while you should see that share on your SMB/Samba/Windows LAN.

HTH

---

### Post by oldcelt on 2009-01-25
Thanks for that.

I had set up sharing on two folders.  I've now realised that the Ubuntu machine created its own workgroup called "Workgroup" which I wasn't expecting.  Now I've realised that, I can find the Ubuntu machine from the Windows boxes ok.   However, I really would like it to be part of my existing workgroup.  Is it possible to change it over and, if so, how please?

The other thing I don't like is to see the administrative shares (e.g. Home$) from the Windows boxes being displayed on the Ubuntu machine.  Can I do something about that?

Ken

---

### Post by jonandrews on 2009-01-25
Have a look at my Windows / Ubuntu networking guides, which includes a guide to sort out the workgroup issue.

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

---

### Post by Iowan on 2009-01-25
[Here]("http://ubuntuforums.org/showthread.php?p=6611650&postcount=4") is a method to edit workgroup on Ubuntu.

---

### Post by oldcelt on 2009-01-26
> **jonandrews said:**
> Have a look at my Windows / Ubuntu networking guides, which includes a guide to sort out the workgroup issue.

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

Many thanks for that - perfect answer.

Ken

---

