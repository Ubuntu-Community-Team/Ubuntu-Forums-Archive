---
title: "step-by-sep network printer setup, please?"
date: 2009-10-23
forum: Networking &amp; Wireless
---

### Post by searchfgold6789 on 2009-10-23
When I first installed Ubuntu 9.04, it didn't detect or set up any of my networking devices. How do I make it so that the Windows computer accross the room will detect the Lexmark Optra E312 on my Ubuntu machine? Windows recognizes everything just fine...
thanks,
Richie

---

### Post by searchfgold6789 on 2009-10-23
anyone?
[-o<[-o<[-o<[-o<[-o<[-o<[-o<[-o<

---

### Post by walt.smith1960 on 2009-10-23
I wish I could help you with this, I can't.  I do have 3 networked printers but all were network ready.  If it were me I'd investigate a print server, I think. That way you don't have to have the machine to which the printer is attached powered up in order to print.  I don't know how print servers work with Ubuntu, I presume okay. I did try to share a printer attached to a Windows Machine some time ago, (Win98?) and it was not reliable at ALL. I have an HP photosmart and two Brother MFD's and they work great.

---

### Post by mike3244 on 2009-10-23
Do you have network access now? Are you wired or wireless?
Can you print locally on your Ubuntu machine?

---

### Post by watsonsun on 2009-11-02
Hi, I hav a similar problem.  My brother mfc210c is connected to my desktop computer running on  Win7. I also have a notebook that is connected through the same network wireless.  My notebook computer is dual boot.  When on Win7, it can print to the mfc210c attached to my desktop.  When my notebook is on Ubuntu 9.10, I cannot get it to print to this same printer attached my desktop.   It appears to print, and the log says successful,  but nothing happens.  If I connect the mfc210c printer directly to my notebook, it prints successfully, either on Win7 or Ubuntu OS.  Before upgrading to Ubuntu 9.10,  I was able to print successfully when on Ubuntu 9.04.  I am a newbee on Ubuntu.  thanks to all

---

### Post by searchfgold6789 on 2010-05-01
mennnny years later there is no fix for this.
Is there some sort of flashy windows program I can run under Wine and make it work? like, install the printer somehow on the wine thing and then use another wine program to use it to print?

---

### Post by Morbius1 on 2010-05-01
> **searchfgold6789 said:**
> When I first installed Ubuntu 9.04, it didn't detect or set up any of my networking devices. How do I make it so that the Windows computer accross the room will detect the Lexmark Optra E312 on my Ubuntu machine? Windows recognizes everything just fine...
thanks,
Richie
I for one am confused by the original post.

It sounds like you want to access a printer attached to Ubuntu from windows but then you say Windows recognizes it fine. Now you want to use a windows application in wine to detect the printer so you can print to it which implies that you can't print to the Ubuntu attached printer from Ubuntu.

Please clarify.

---

### Post by searchfgold6789 on 2010-05-05
The Windows computer knows the network printer is there, but the print jobs and test pages I send to it aren't coming or showing up in ubuntu. With the wine thing I was just prodding for ideas.

---

### Post by Morbius1 on 2010-05-05
Well I would go through the basics again just in case.

(1) Turn off or temporarily disable any firewall you have on either machine. If you haven't touched the firewall on Ubuntu then you don't need to do anything on the Ubuntu box.

(2) On ubuntu:

Make sure the printer is "shared" and "published" 

_Share_:
Administration > Printing > Right Click the attached printer > Properties > Policies > Check Enabled, Accepting Jobs, and Shared

_Publish_:
Administration > Printing > Server > Settings > Check "Publish Shared Printers connected to this system"

(3) Make sure that CUPS has started:

**sudo service cups restart**

---

### Post by searchfgold6789 on 2010-09-02
I just decided to put it up on the Windows computer and printing to there from ubuntu. The reason why I did not do this originally was because the same thing would happen, only backwards: the Ubuntu system would detect the Windows system network but Windows wouldn't print. I found out that this was a bad driver issue, and I solved the problem by downloading the .deb driver from the Lexmark website for my printer (which I was surprised to find, as someone said that Lexmark had horrible support for Linux) and installing it. Then I set up the printer again and it works beautifully now.
Thanks,
 - search

---

### Post by lswartz on 2010-09-07
> **Morbius1 said:**
> Well I would go through the basics again just in case.

(1) Turn off or temporarily disable any firewall you have on either machine. If you haven't touched the firewall on Ubuntu then you don't need to do anything on the Ubuntu box.

(2) On ubuntu:

Make sure the printer is "shared" and "published" 

_Share_:
Administration > Printing > Right Click the attached printer > Properties > Policies > Check Enabled, Accepting Jobs, and Shared

_Publish_:
Administration > Printing > Server > Settings > Check "Publish Shared Printers connected to this system"

(3) Make sure that CUPS has started:

**sudo service cups restart**

Thank you very much. My wife's new computer uses Ubuntu & I was able to easily use the printer with my Mini 9. She was using 
XP & sharing the printer via samba. A blasted root kit destroyed her system, so after 6 years she got the new computer & Ubuntu.

---

