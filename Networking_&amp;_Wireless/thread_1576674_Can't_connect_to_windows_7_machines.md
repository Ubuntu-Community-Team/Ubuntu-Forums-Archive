---
title: "Can't connect to windows 7 machines"
date: 2010-09-17
forum: Networking &amp; Wireless
---

### Post by DoocesWild on 2010-09-17
I may be missing something very easy here, but I have a fresh install of Ubuntu 10.04 64 bit (I have also tried 10.04 32 bit) and I cannot connect to my windows machines.  I can't connect by going to the network window, or by connect to server via ip.  Basically, I can see the windows machines but then I double click it, and it asks for the credentials.  I'm the admin of all of the machines, and I only have one login to my windows machine, which is my name First Last.  I am entering this, and my password (which I'm sure is correct) and click "Connect".  It thinks for maybe a half second, then presents me a blank credentials box, wanting me to start over.

I can connect to my Macbook without any troubles.

I'm using an Acer AspireRevo 1600, wired connection.

---

### Post by DoocesWild on 2010-09-22
Does nobody have any sort of information for me?  I also can't connect to windows 7 through a live install of XBMC, or a virtual machine install of Ubuntu.  

This is obviously a windows issue, since I can easily connect to my mac, but I don't know where else to try.  I've been looking for an answer in the forums, but everything I can find points me to older versions of Ubuntu, with walkthru's I can't follow because everything's different.

I thought maybe changing my login name to just Firstname instead of Firstname Lastname may help, thinking maybe the space would cause some friction.  

I also tried right clicking a folder in W7, going to the sharing properties, and creating a share for Everyone.  Still no luck.  Thanks!

---

### Post by sikander3786 on 2010-09-22
Are you sure are using "Workgroup" with Windows 7 and not the "Homegroup". Homegroup is meant for machines with Windows 7 only, not even Windows XP. And both Ubuntu and Windows boxes are in the same Workgroup?

Also try to disable password protected sharing in Windows in Network and Sharing Center.

---

### Post by DoocesWild on 2010-09-25
> **sikander3786 said:**
> Are you sure are using "Workgroup" with Windows 7 and not the "Homegroup". Homegroup is meant for machines with Windows 7 only, not even Windows XP. And both Ubuntu and Windows boxes are in the same Workgroup?

Also try to disable password protected sharing in Windows in Network and Sharing Center.

When you make a homegroup, are you forfeiting the workgroup?  Because it tells me on my W7 machine that I'm part of the workgroup PRIMETIME.  Which is what I can see in Ubuntu, click on in Ubuntu, and fail to connect to.

Edit:  However, I have not specifically set Ubuntu to be a part of PRIMETIME.  How would I do this?

Edit 2:  I figured out how to put them into the same network, and have removed the password as suggested, still no connections.

---

### Post by OmahaJB on 2010-11-19
I found that this seems to be the answer to our question.
 
refer to:  [http://www.7tutorials.com/how-change-workgroup-ubuntu-linux-work-windows](http://www.7tutorials.com/how-change-workgroup-ubuntu-linux-work-windows)

---

