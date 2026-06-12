---
title: "Remote Desktop from Ubuntu to Windows 7 connection help"
date: 2010-09-24
forum: Networking &amp; Wireless
---

### Post by crazymao on 2010-09-24
ok so im trying to remote desktop to my windows 7 computer from my ubuntu laptop. i have tried the following command:

rdesktop -u USERNAME -d HOSTNAME IP -g WxH but i get an error saying unable to connect

i am a noob so give me a break on the stupid questions :)
1. am i supposed to run something on windows to allow ubuntu to connect? (i already enabled remote desktop)
2. i am confused on which ip im supposed to use, ipconfig gives me a different ip than what for example whatsmyip.com gives me and according to my research theyre supposed to be the same :confused:
3. any noob friendly help/guides on this topic will be appreciated

yes i did research but i did not find an answer

thanks alot

---

### Post by dallasWolf on 2010-09-24
Use the IP address you get from the ipconfig command on your windows 7 computer.

example:

rdesktop 192.168.1.75

Then, you will be asked for your login Credentials. 

NOTE: If you are login in as Administrator make sure the 'A' is upper case.

---

### Post by CharlesA on 2010-09-24
What error are you getting when trying to connect via RDP?

I've had no problems connecting to a Win7 box using the RDP client in Ubuntu.

---

### Post by crazymao on 2010-09-24
thanks this shows more promise but its doing something for a few seconds and then says 
ERROR: IP: unable to connect

---

### Post by pricetech on 2010-09-24
Windows 7 what version ?  (Pro, Home, etc.)  Some don't support RDP.  remote Assistance is not the same thing.

In Pro, and presumably above, Make sure you choose "Allow connections from computers running any version of Remote Desktop"

If you're on the same subnet, use the IP address you got from ipconfig.

---

### Post by CharlesA on 2010-09-24
> **pricetech said:**
> Windows 7 what version ?  (Pro, Home, etc.)  Some don't support RDP.  remote Assistance is not the same thing.

In Pro, and presumably above, Make sure you choose "Allow connections from computers running any version of Remote Desktop"

If you're on the same subnet, use the IP address you got from ipconfig.

The "Home" versions of Windows don't support RDP: XP Home, Vista Home Premium, Windows 7 Home Premium/Windows 7 Starter.

But yeah, You need to select the "Allow connections from computers running any version of Remote Desktop (less secure)."

Otherwise, you'll get an error that says: "Connection reset by peer"

---

### Post by crazymao on 2010-09-24
> **CharlesA said:**
> The "Home" versions of Windows don't support RDP: XP Home, Vista Home Premium, Windows 7 Home Premium/Windows 7 Starter.

But yeah, You need to select the "Allow connections from computers running any version of Remote Desktop (less secure)."

Otherwise, you'll get an error that says: "Connection reset by peer"

that would explain it, I'm running home, thanks alot

---

### Post by pricetech on 2010-09-27
I hate "home" versions.  Gut the silly thing and sell it to non technical people who typically need the most help provided by the stuff left out.

---

### Post by andersja on 2010-11-04
Consider using Gitso for cross-platform as well as Ubuntu-to-Ubuntu support. I use it regularly and it works very well: 
[http://code.google.com/p/gitso/](http://code.google.com/p/gitso/)

---

### Post by elperrillo on 2011-03-09
Use this guide, it worked for me:

[http://geekyprojects.com/tutorials/how-to-use-the-real-windows-remote-destop-in-ubuntu/](http://geekyprojects.com/tutorials/how-to-use-the-real-windows-remote-destop-in-ubuntu/)

---

### Post by ahmedipa on 2012-09-27
[QUOTE=elperrillo]Use this guide, it worked for me:

[http://geekyprojects.com/tutorials/h...top-in-ubuntu/](http://geekyprojects.com/tutorials/h...top-in-ubuntu/)[/QUOTE]

thank you brother for your post 

but I face the problem 

I have three hard drives 

C:// for windows 7 pro

D:// for ubuntu 12.04

E:// for my files 

--------------------------------------------------------

I face this problem as attached

I found this video it is similar to your post 

[http://www.youtube.com/watch?v=0iivW21urSM](http://www.youtube.com/watch?v=0iivW21urSM)

---

