---
title: "Graphics problem"
date: 2009-09-25
forum: Multimedia Software
---

### Post by gsxruk on 2009-09-25
Hi all,

I did have another post regarding the issues experienced with an ATI graphics card and which drivers to use.  After a little research I decided to use the proprietary drivers included in Ubuntu.

Something I have noticed, and I have seen this with the open source drivers as well, is that my screen will occasionally show black parts.  It is very difficult to capture a screen shot because when print screen button is pressed the screen refreshes itself and displays correctly (even on the screen shot).  But amazingly, while uploaded the screen shot for the next paragraph it happened again and I was able to get a shot of it (attached screenshot2.png).

Another thing that happens occasionally is part of a window remains on screen after it is closed.  I have managed to get a screen shot of this (attached screenshot.png).

Does anybody else experience issues like this with ATI cards?  Or any other cards?  Is there a fix?

I'm running Ubuntu 9.04 64bit and the card is an ATI Radeon 4890.

Thanks.

---

### Post by apostolis159 on 2009-09-26
I also have a problem with this card. I am using ATI Radeon 4890 too and in the right down corner of the screen there is something like a window which says "AMD Unsupported hardware". It wasn't there when I installed Ubuntu. It came up when I installed the ATI drivers from System>Hardware Drivers...:confused:
Is there a fix or something??
I am using Ubuntu 9.04 x32..

---

### Post by gsxruk on 2009-09-26
On the other post I had someone posted this link:

[http://ubuntuforums.org/showthread.php?p=7996934](http://ubuntuforums.org/showthread.php?p=7996934)

I too have the "AMD Unsupported Hardware" square in the lower right corner of the screen.  I don't quite understand all the talk on the ATI driver issues as they mainly discuss compatibility with "older cards" and don't quite see how this fits in with the 4890.

I decided to live with the square as its not really causing me any problems.  Also, I have downloaded and tried the latest 9.9 driver from AMD and it did not solve the issues I'm describing.  The square does disappear though.

Are you seeing any of the other symptoms shown in the screen shots?

---

### Post by apostolis159 on 2009-09-26
No... Only when I open the Screen Properties the whole system lags..

How did you install the 9.9 drivers?? I am new and its hard to me to use the terminal..

---

### Post by gsxruk on 2009-09-26
I wonder if this issue is related to x86_64 then?

Sorry, I'm not going to provide advice on installing the drivers because I'm no expert either.

If you go here:

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English)

You will find the driver and installation instructions there.  However, this driver will come with its own problems as you will need to remove and re-install with new kernel updates.  See my previous post:

[http://ubuntuforums.org/showthread.php?t=1270967](http://ubuntuforums.org/showthread.php?t=1270967)

---

### Post by apostolis159 on 2009-09-26
I already have the driver downloaded from the ATI site, but i don't know how to install it.. I only use linux 4 days now...

---

### Post by gsxruk on 2009-09-26
OK.  I have posted some instructions below but please don't complain if you follow this and it goes wrong.

1. Go to System-Accessories-Hardware Drivers.
2. Press "Remove" to remove the activated driver.
3. Restart the computer.
4. You should notice that the computer has booted back to its original configuration (open source drivers).
5. Go to Applications-Accessories-Terminal.
6. Navigate to the folder with the downloaded ATI driver.
7. Type the command "sudo sh ./ati-driver-installer-9-9-x86.x86_64.run".
8. Follow the on-screen installer.  I suggest you choose "automatic" when offered between "automatic" and "custom".
9. After the installer has completed run the command "sudo /usr/bin/aticonfig --initial".
10. Restart the computer.
11. Hopefully, you will have successfully installed the driver.

---

### Post by apostolis159 on 2009-09-26
Thank you, I 'll try it when I boot in Linux because now I am in Windows... (dualboot ;))

---

### Post by gsxruk on 2009-09-26
This is now getting worse.  It appears that after the PC has been on for a couple of hours it gets completely mixed up.

See the attached screen shots which show the screen offset to where it should be.  Its really weird, but when this happens, the mouse pointer does not agree with the image on screen and you have to guess where to position the mouse to control the window.

Can anyone offer any help with this?

---

### Post by apostolis159 on 2009-09-26
My system is now working perfectly!!:)
Thank you for your help!

---

### Post by gsxruk on 2009-09-27
Anyone?

---

### Post by gsxruk on 2009-09-27
Just to update anyone that may experience this issue in the future:

This morning I changed the visual effects in appearance to "None".  The PC has been in use all day and while there has been an occasional black part appear, none of the more serious issues described have occurred.

This has at least made the PC more than usable and it now feels stable.

---

### Post by markbuntu on 2009-09-29
The 4890 came out after the 9.5 driver so is not supported by it. You really need the latest driver from ati for it to work properly. Be sure to remove the old driver before installing the new one or you will have problems with kernel updates.

---

