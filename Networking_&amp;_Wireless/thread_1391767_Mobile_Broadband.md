---
title: "Mobile Broadband"
date: 2010-01-27
forum: Networking &amp; Wireless
---

### Post by Odense on 2010-01-27
I have an USB (Huawei 1751) modem for mobile broadband. I had it up and running in Ubuntu 9.10 but I had to clear the computer for various reasons.
I have decided to only use LTS versions so for the reinstall I have used Ubuntu 8.04 LTS.

I have downloaded and installed usb_modeswitch and can see that the modes IS changed to the right value.

After that I wanted to add a new mobile broadband connection in the network connections wizzard - but cannot see any settings for mobile broadband. I am sure it must be possible - but where is this function hidden in version 8.04 ?

---

### Post by chewearn on 2010-01-27
If my memory served, I think the network manager in 8.04 is too old and not supporting mobile broadband.

---

### Post by alexfish on 2010-01-27
hi

Lets find out if the modem is detected and which  tty(piping) it should show ttyUSB(n)


from the terminal

Code:

dmesg | grep -e "modem" -e "tty" 


then try follow this guide

                                  [B][I][Ubuntu Linux on the Move]("http://www.pcurtis.com/ubuntu-mobile.htm")

also these threads  Read first ( if you can connect with gnome ppp or wvdial then I would tend to stay with them)
[/I][/B]          [http://ubuntuforums.org/showthread.php?t=797059&highlight=gsm+hardy](http://ubuntuforums.org/showthread.php?t=797059&highlight=gsm+hardy)
[http://ubuntuforums.org/showthread.php?t=858032&highlight=gsm+hardy](http://ubuntuforums.org/showthread.php?t=858032&highlight=gsm+hardy)                     
   [http://ubuntuforums.org/showthread.php?t=1368645](http://ubuntuforums.org/showthread.php?t=1368645)

---

### Post by Odense on 2010-01-29
Thank you alexfish and chewearn :p
Too much to read for my taste 
I capitulated and upgraded to version 9.10 in order to get a network manager that includes mobile broadband

---

