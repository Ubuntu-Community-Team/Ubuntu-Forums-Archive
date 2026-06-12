---
title: "Can't install broadcom wireless driver"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by Xarver on 2010-02-08
Hello everyone!
My wireless card requires a proprietary driver to function. The problem is I can not install this driver from Hardware Drivers.
Why? I have no internet access, so how can I install a wireless driver? For some reason I can not use wired internet on any OS. (windows 7, kubuntu, etc.) Only wireless works on 7.
Problem is since I don't have Internet I can't install the internet driver ironically... I use a Broadcom wlan 802.11b/g

---

### Post by bkratz on 2010-02-08
> **Xarver said:**
> Hello everyone!
My wireless card requires a proprietary driver to function. The problem is I can not install this driver from Hardware Drivers.
Why? I have no internet access, so how can I install a wireless driver? For some reason I can not use wired internet on any OS. (windows 7, kubuntu, etc.) Only wireless works on 7.
Problem is since I don't have Internet I can't install the internet driver ironically... I use a Broadcom wlan 802.11b/g

Depending on your exact Broadcom device (which you can find out with lspci in the terminal) you may be able to get what you need from this thread.

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by Xarver on 2010-02-08
Hardware drivers doesn't work because I have no Internet at all on Kubuntu...

---

### Post by cwbar_1 on 2010-02-08
Insert the live CD (DVD) navigate to 
/pool/restricted/b/bcmwl-kernel...
Double click the file to start the install process.  
This will fail, but will give you the name of 3 additional files
needed.  Take note of these files and go to 
/pool/main/ to find and install these files
first.  Then install the bcmwl-kernel package in restricted.
That's it.... Restart and choose your network.

---

### Post by Xarver on 2010-02-08
Wait do you mean I mount the harddrive and go through those files?
_**Nevermind I see what you mean. Going to try.**_

---

### Post by bkratz on 2010-02-08
> **Xarver said:**
> Hardware drivers doesn't work because I have no Internet at all on Kubuntu...

Look carefully at that thread it gives methods with no internet access.

---

### Post by SoFl W on 2010-02-08
Try this thread for notes:
[http://ubuntuforums.org/showthread.php?t=759100](http://ubuntuforums.org/showthread.php?t=759100)

---

### Post by Xarver on 2010-02-08
> **bkratz said:**
> Look carefully at that thread it gives methods with no internet access.
I'm on kubuntu so those instructions confuse me.

When I did what cwbar said it showed up in hardware drivers but when I click activate on it it doesn't do anything but sit there.
I know it's the correct driver because I've used it before.

---

### Post by cwbar_1 on 2010-02-08
If the method I posted worked correctly, you should not have to go to hardward drivers again to activate the sta wireless driver. (it should be loaded automatically)  To clarify.  Start your computer into Kubuntu.  Insert the live cd.  Open the cd to view the files.  Under the folder "pool" you should find 2 folders, main and restricted.  The sta driver is in the "restricted>b" folder.  The 3 additional files needed are in the alphabetical folders in the "main" folder.  If you double click on the bcmwl.....package in "restricted" the system will attempt to install the package, but will be unable to.  But, it will tell you the names of the other files in "main" you need to install first. Hint..(fakeroot in "main>f", dpkg in "main>d"......

---

### Post by Xarver on 2010-02-08
It doesn't work though. :(

---

### Post by cwbar_1 on 2010-02-08
If you left click on the network manager icon, do any wireless networks show?  If you right click on the network icon, is enable networking and enable wireless checked?

---

### Post by Xarver on 2010-02-08
There is no enable networking; only enable wireless. I'm on KDE btw.
Yes enable wireless is checked, no wireless networks show though.
And wireless is fine on windows 7.

---

### Post by cwbar_1 on 2010-02-08
Is your network a "hidden" network?  What wireless encryption is your router set up for?  When you right click the network icon, do you have a choice to "create a new wireless network?"

---

### Post by Xarver on 2010-02-08
No it's not hidden. It's shown on 7.
It's WEP encryption. I have the option to create one but I don't think it would work. There are over 5+ public wireless networks that should be shown that are public.

---

### Post by cwbar_1 on 2010-02-08
Last questions, then I'm out of suggestions.  Were you able to access wireless using the live cd through the hardware drivers?  (before you installed Kubuntu) And, have you restarted your computer?

---

### Post by Xarver on 2010-02-08
Yes I restarted it. And I didn't check on the kubuntu cd, but the drivers worked on an ubuntu cd.

---

### Post by cwbar_1 on 2010-02-08
Sorry I couldn't help.  The method for installing using the cd's sub-folders has always worked for me.  (I have a PPOE connection through a wireless router and have never been able to get internet through a cable connection.)

---

### Post by Xarver on 2010-02-08
Aww anyone else got advice?

---

### Post by Xarver on 2010-02-10
Bump... please help.

---

### Post by Xarver on 2010-02-11
Bump.... How can I get this working :(

---

### Post by Xarver on 2010-02-12
hellooo?

---

### Post by Xarver on 2010-02-13
bump...

---

