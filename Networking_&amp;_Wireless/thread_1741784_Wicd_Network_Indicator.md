---
title: "Wicd Network Indicator"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by biomedtek on 2011-04-28
I use Wicd 1.7.0 to manage my wired/wireless network connections and it  worked well with Ubuntu 10.10. Now that I upgraded to 11.04 the wireless  indicator does not show up on the top bar, even though the wireless is  connected and working. I have no way to see my connection, or view  available wireless connections. I looked through system settings, but  don't see any options for selecting what shows up on the top bar. Can  anyone help?

---

### Post by drpjkurian on 2011-04-28
Hi It appears to be a bug. See this [post]("http://http://www.gossamer-threads.com/lists/gentoo/user/220857")

---

### Post by drpjkurian on 2011-04-28
Hi
By the way i did some googling
Check out the 14th post of this [thread]("http://ubuntuforums.org/showthread.php?t=566965&page=2")

---

### Post by biomedtek on 2011-04-28
I didn't see the relevance to thread 14, I already have Wicd installed.

---

### Post by drpjkurian on 2011-04-29
I thought this might help
> In GNOME, to get the tray icon to automatically appear at boot, go to System > Preferences > Sessions. In the "Startup Programs" tab, click the "New" button. Give it a name ("Wicd" works fine). 


---

### Post by biomedtek on 2011-04-29
I can try that, but I don't think that there even is a "sessions" under preferences anymore in 11.04. I can't verify that right now because I'm in work on a windows computer.

---

### Post by drpjkurian on 2011-05-01
Well I am in Lucid. There is startup application directly given in preferences

---

### Post by Dale61 on 2011-05-01
Look under Applications > Internet, then right click and add the launcher to the panel.

Worked for me.

---

### Post by ricerider1 on 2011-05-06
Also you may need to check the properties for the command wicd-gtk ~~notray. This is how mine was and I simply cut out the ~~notray. You do this by right clicking on Applications, left click on edit menus, and left click on Internet and wicd should show in the column to the right where you can right click and go to properties or just left click and a properties box will become available next to it. Also to show it in the Internet menu you will need to put a check in the box if that is not already the case. 
     Have a great weekend everyone!

---

