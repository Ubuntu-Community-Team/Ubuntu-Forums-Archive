---
title: "Installing Creative Soundblaster driver"
date: 2008-03-10
forum: Multimedia &amp; Video
---

### Post by bharkins on 2008-03-10
On a new Ubuntu Gutsy install on the desktop, the Creative sound card (XFi model) was not detected. I downloaded the driver XFiDrv_Linux_US-1.04, placed in Home folder. How do I proceed to install the driver?

---

### Post by Shazaam on 2008-03-10
What kind of file is it and have you extracted it? It sounds like a source file so have you installed build-essential from the cd yet?

Three ways to install build-essential-
1. Put the Ubuntu disk in. Go to System>Administration>Software Sources. When it asks you for a password enter the password you use to log in. Unmark (uncheck) everything but "cd/rom". It will then pop up a box telling you to reload your sources list. Do it. Then go to System>Administration>Synaptic Package Manager. If it asks you for a password do the same as before. Find build-essential, make sure it's checked for installation and then hit apply.
2. If you have a working Gutsy internet connection go to Synaptic>Settings>Repositories and make sure everthing IS checked (except cdrom) and click Reload. Once that is done find and install build-essential.
3. Go to Software Sources (Repositories) as in step 1, make sure everthing but the cdrom is checked. Then go to Applications>Accessories>Terminal. Once that opens type this in terminal.......
```
sudo apt-get update
```
Enter your login (user) password. This will update your sources list.
Once that is done type this in.....
```
sudo apt-get install build-essential
```
This will install build-essential.
Then you can install the Creative drivers per their README or INSTALL file once you have unpacked/extracted it.

---

### Post by bharkins on 2008-03-11
> **Shazaam said:**
> What kind of file is it and have you extracted it? It sounds like a source file so have you installed build-essential from the cd yet?

Three ways to install build-essential-
1. Put the Ubuntu disk in. Go to System>Administration>Software Sources. When it asks you for a password enter the password you use to log in. Unmark (uncheck) everything but "cd/rom". It will then pop up a box telling you to reload your sources list. Do it. Then go to System>Administration>Synaptic Package Manager. If it asks you for a password do the same as before. Find build-essential, make sure it's checked for installation and then hit apply.
2. If you have a working Gutsy internet connection go to Synaptic>Settings>Repositories and make sure everthing IS checked (except cdrom) and click Reload. Once that is done find and install build-essential.
3. Go to Software Sources (Repositories) as in step 1, make sure everthing but the cdrom is checked. Then go to Applications>Accessories>Terminal. Once that opens type this in terminal.......
```
sudo apt-get update
```
Enter your login (user) password. This will update your sources list.
Once that is done type this in.....
```
sudo apt-get install build-essential
```
This will install build-essential.
Then you can install the Creative drivers per their README or INSTALL file once you have unpacked/extracted it.

I did all that earlier. When I click Installer, and select to Run or Run in Terminial, nothing happens. That's why I posted this topic. 

By the way, I find that the SB X-Fi driver is only for 64 bit. I don't know if Creative will offer 32 bit. It seems odd to me that they start with the 64 first.

---

### Post by krylon on 2008-03-11
Search the forum for OSS on X-Fi

---

### Post by bharkins on 2008-03-13
> **krylon said:**
> Search the forum for OSS on X-Fi

That returned no items. Do you have a specific thread on the topic?

---

### Post by krylon on 2008-03-13
> **bharkins said:**
> That returned no items. Do you have a specific thread on the topic?

I assisted someone in this thread, starting at post #6.

[http://ubuntuforums.org/showthread.php?t=690490](http://ubuntuforums.org/showthread.php?t=690490)

I assume you have 64bit Ubuntu since you are trying Creative's Beta driver (64bit only).

---

### Post by bharkins on 2008-03-14
> **krylon said:**
> I assisted someone in this thread, starting at post #6.

[http://ubuntuforums.org/showthread.php?t=690490](http://ubuntuforums.org/showthread.php?t=690490)

I assume you have 64bit Ubuntu since you are trying Creative's Beta driver (64bit only).

I do not have 64bit Ubuntu, nor the hardware to support it (just 32 bit machine). I have another post inquiring about other 32 bit sound cards that can be compatible with Vista and Ubuntu.

---

