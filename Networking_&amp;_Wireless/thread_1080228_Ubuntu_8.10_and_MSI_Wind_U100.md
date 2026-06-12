---
title: "Ubuntu 8.10 and MSI Wind U100"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by Shibblet on 2009-02-25
I have an MSI Wind U100 with a Realtek RTL8187 Wireless adapter built in.

I have spent the last DAY trying to get Ubuntu to even notice that I have a wireless adapter.  Finally after reading through the forums, Ubuntu notices that there is a wireless adapter.  

But now I have a second problem.  I can't connect to my router.  I enter the WPA Personal password, and it comes back to ask me to enter the password again, only it has changed the password to a string of random characters.

Can anyone help me with this?  I don't want to go back to Windows, but I might not have any other choice here.  An OS without internet is a console.

---

### Post by Shibblet on 2009-03-03
Well, I don't know what the situation was, but I finally figured out the problem.

This is referenced a million times in many different threads, but I will throw it up here again.

[[COLOR="RoyalBlue"]http://forums.msiwind.net/debian/rtl8187se-drivers-for-ubuntu-and-deb-packages-t4954.html[/COLOR]]("http://forums.msiwind.net/debian/rtl8187se-drivers-for-ubuntu-and-deb-packages-t4954.html")

Make sure you download the appropriate driver for your kernel!!!  This is ABSOLUTELY NECESSARY.  After installation, everything worked amazingly well!

---

### Post by roynux on 2009-03-05
At the time of writing, the driver for the currenct kernel with normal updates is

> linux-rtl8187se-modules-1023.2@2.6.27.11.14.deb

and not the one on the top of the post with "Intrepid, official release".

---

