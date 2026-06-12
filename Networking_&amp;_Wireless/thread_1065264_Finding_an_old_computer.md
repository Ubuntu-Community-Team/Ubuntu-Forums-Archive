---
title: "Finding an old computer"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by Jimmmac1 on 2009-02-09
Good evening.  

I just over the weekend installed Ubuntu 8.10 on my main computer, replacing Xandros desktop.  I also have another computer right next to my main computer which is running Xandros 3.  I usually keep it shut off to save electricity, but decided to turn it on tonight.  Next weekend I might just attach a monitor to it and install Ubuntu 8.10 on it.  But I would like to take a look at it to see what there is on it. I used to rdesktop to the old computer, enter a password and I was on it. Now I need to find it, find out it's ip address and rdp over to it.  And of course there is my router.  We have a cable modem attached to a wireless lan. My main computer and the Xandros box are directly wired to the wireless lan box, which is directly wired into the cable modem.  Well anyway, the wireless lan box wants a user name and password.  I only remember the password, so I will probably have to call up Linksys to get into the thing.  What I need help with is getting into the old computer.  It does not show up on a network. Any help offered would be very much appreciated.  Thanks.

Jim

---

### Post by toasty_ghosty on 2009-02-09
Do you just need to know the password and username?

If so, you can easily wipe all the settings (including passwords and username) by holding the reset button for 10 seconds or so, and then pull the  cord and reset the thing. After that, all the settings are stock. Log on to the thing and the username is "admin" without a password.


Hope thats helps!

---

### Post by Gramps on 2009-02-09
I'd probably would boot it with the Ubuntu Live CD then try and burn the files that I wanted to a CD, or transfer them to a usb drive or thumb drive.

---

### Post by dmizer on 2009-02-09
I suspect that you'll have very little choice but to connect a monitor to it and take a look at it that way. Since it has been off for so long, it may be hanging during boot because the clock is off or the BIOS battery died.

---

### Post by Jimmmac1 on 2009-02-10
Hi all

Thanks for your responses.  I connected the monitor keyboard and mouse and am now transferring files to a second hard drive on the old computer.  Now I would like to see it from some kind of file manager.  For instance, I have Nautilus, PC File Manager and Dolphin and I am not seeing this computer from any of these.  If I turn this thing on, I want to be able to see all drives on my computer and all drives on the other computer on a file manager.  So I can transfer files back an forth between the two.  Any ideas?  Thanks again.

Jim

---

### Post by dmizer on 2009-02-10
> **Jimmmac1 said:**
> Now I would like to see it from some kind of file manager.

You will need to set the Ubuntu computer up as a file server. There are two or three ways you can do this depending on what kind of computers are on your network.

If you will have Windows computers on your network, you will have to set the computer up as a Windows server. Please see the First link in my sig for that. To make Windows shares viewable from another Linux computer, please see the second link in my sig.

If your network is only Linux computers, please see the fourth link in my sig for how to share and view network shares.

If you have a variety of operating systems, you might have more luck with the fifth link in my sig.

---

### Post by Jimmmac1 on 2009-02-12
Hi dmizer

Thanks for the help.  What I think I will do is simply take out the one big drive on the old computer and get an enclosure for it.  I just wanted to see my Xandros computer, which I can through the RDP browser.  I guess I can ftp to it if necessary.   Thanks again.

Jim

---

### Post by dmizer on 2009-02-12
> **Jimmmac1 said:**
> Hi dmizer

Thanks for the help.  What I think I will do is simply take out the one big drive on the old computer and get an enclosure for it.  I just wanted to see my Xandros computer, which I can through the RDP browser.  I guess I can ftp to it if necessary.   Thanks again.

Jim

This is unlikely to give you satisfactory results. NAS devices (an enclosure) are notoriously bad with Linux and CIFS. If you DO decide that this is the way to go, be sure to do some serious research on Linux compatibility before purchasing one.

---

