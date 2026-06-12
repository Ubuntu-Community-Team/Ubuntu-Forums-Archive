---
title: "How I fixed network browsing and got rid of “The folder contents cannot be displayed”"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by chelrob on 2009-03-03
From the Ubuntu Desktop clicking > Places > Network > MSHOME returns an error &#8211; &#8220;The folder contents cannot be displayed&#8221;.

I have a Dell Inspiron 530n that came preloaded with Ubuntu Desktop, 7.10.  I remember network browsing was working out of the box and don&#8217;t really recall when it stopped working.

I run my Ubuntu Desktop headless and use VNC to access the desktop.  The machine&#8217;s primary function is to be a file server for my home networking needs.

I have searched the Internet high and low for a solution to this problem but mostly have found lots of threads spinning out of control in too many directions, while offering no real insight to solving this problem.

People are suggesting this is a Nautilus bug.   People are insisting this is a Samba issue&#8230; I have news for you&#8230; Samba does not have to be installed to browse Windows networks from the Ubuntu Desktop.  Samba is only required if you want Windows machines to see the Ubuntu Desktop&#8217;s shared folders.

Thanks to a bad upgrade I recently used my Dell factory restore DVD to reset the system back to factory defaults.  Upon completion network browsing was working again.  I could go to > Places > Network and see both Windows workgroups on my network and access the shares on every PC, XP and Vista.  Even password protected Vista shares are working.

Next I listed out the things I always do to this machine after a fresh Ubuntu reload:

1.	Change the network config from roaming mode to static IP.
2.	Install openssh
3.	Setup VNC with resumable sessions.
4.	Install and configure samba for Windows file sharing.

I didn&#8217;t have to go past step 1 to break network browsing and bring back the error message noted at the start of this article.
I changed my network config to static IP, rebooted and sure enough it was broken.

As it turns out changing to static IP didn&#8217;t break the network browser&#8230; it was the simple act of adding my Windows workgroup name to the General tab > Domain name, under network settings that caused the problem.  Deleting the name and leaving the field blank, followed by a reboot restored my network browser and the problem was solved.

Go to > System > Administration > Network > General tab and delete the Domain name.  Reboot and try > Places > Network again.  If your Windows PCs have file sharing enabled you should be able to access their shared folders now.

Hope this helps.
-	Peace

---

### Post by abalakersky on 2009-03-11
This would be a great information, if I could figure out how to do this in 8.10.
For some reason I don't have System > Administration > Network > General. In fact I don't have System > Administration > Network.
So, would you happen to know where in 8.10 is that setting? I cannot find for the life of me :)

Thanks,

---

### Post by capscrew on 2009-03-12
> **abalakersky said:**
> This would be a great information, if I could figure out how to do this in 8.10.
For some reason I don't have System > Administration > Network > General. In fact I don't have System > Administration > Network.
So, would you happen to know where in 8.10 is that setting? I cannot find for the life of me :)

Thanks,

The Network Manager applet along with all of the Nautilus libs have been fundamentally changed from 7.10 to 8.10.  The old gvfs (gnome virtual file system) is now GIO.

I run 7.10 as a desktop for the above reasons.  The 8.04 Hardy version is a little of both and by now is a known quantity.

You should be looking for 8.10 (Ibex) specific solutions for your problems in thsi area.

---

### Post by amadeus266 on 2009-03-12
> **abalakersky said:**
> This would be a great information, if I could figure out how to do this in 8.10.
For some reason I don't have System > Administration > Network > General. In fact I don't have System > Administration > Network.
So, would you happen to know where in 8.10 is that setting? I cannot find for the life of me :)

Thanks,

Try left clicking on the network icon on the panel. It should bring up a menu. select manual configuration and network manager will open. click unlock and enter your password, the you can click on the general tab and make your changes.

---

### Post by chelrob on 2009-03-12
Thst's only going to work if he's already been to the general tab and entered a windows worgroup name in the domain field... it looks to me like he has never done that.

The domain field is blank by defualt.

---

### Post by abalakersky on 2009-03-12
Thanks amadeus266, unfortunately the problem with 8.10 is that Network Manager has changed. There is no General tab anywhere in there, and for that matter no Domain configuration there either. I am still searching for the way to fix browsing, but so far none of the couple of "fixes" that sprung up on forums had any affect on my 8.10 based netbook (EeePC 1000).

Thanks,

---

### Post by Nevon on 2009-03-12
I've had the same problem for months now, and so far I haven't been able to find a fix anywhere.

---

### Post by dmizer on 2009-03-12
In Ibex (8.10), you can install the package called "network-manager-gnome". Then uninstall NetworkManager.

Be forewarned, this move could make wireless more difficult to manage and will remove the network configuration tool from your system tray. But, rather than using NetworkManager, you can try some of the other wireless manager tools avalable like wicd.

---

