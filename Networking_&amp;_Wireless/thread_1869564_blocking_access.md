---
title: "blocking access"
date: 2011-10-25
forum: Networking &amp; Wireless
---

### Post by silvergoat on 2011-10-25
I have a computer that I will be setting up for public use, but I would like to block content from the computer- mainly adult content, but I also want to block downloads and installations.  How can I accomplish this in Lubuntu?  I know that some modifications may need to be made to the router configuration, but the installation and downloads may be controllable through the O/S.

Any ideas?

Thanks-

EDIT:  I do realize that most people will not be able to install something in Linux.

---

### Post by SteveDee on 2011-10-26
> **silvergoat said:**
> I have a computer that I will be setting up for public use.....but I also want to block downloads and installations...

Probably need a better idea of how this will be used, but here are some ideas. First take a look at my notes here: [http://ubuntuforums.org/showthread.php?t=1866992](http://ubuntuforums.org/showthread.php?t=1866992)

You wont need the rdesktop stuff, but I thought you could populate the user's desktop with icons that load allowable applications (e.g. web browser or whatever).

Remove the desktop panel.

Make the users Home (e.g. /home/user) read only. Check that your apps run, as you may need to make some hidden folders (like /home/user/.config) read/write. The file browser should not be able to download stuff if the target location (/home/user/download) is read only.

---

### Post by silvergoat on 2011-10-26
Looks like there might be some information I can use in that thread....I'll have to test out what limitations there are.

What I was doing is putting a computer in the waiting area for tax season.  I wanted something there for customers to be able to check email or otherwise entertain themselves while they waited, but since I understand that there are always jerks, I wanted to make sure that they couldn't do anything harmful like google donkey play and fill my desktop with offensive materials....I don't even want them to be able to google offensive material, period.

I was advised to check my router for content filtering, but that I should have purchased a firewall instead.  Since I didn't, I'm trying to find other ways to accomplish the same goal.

---

### Post by SteveDee on 2011-10-27
> **silvergoat said:**
> ...I wanted something there for customers to be able to check email or otherwise entertain themselves...

Maybe you just need a web kiosk. If you do a web search for "Linux kiosk" you will find lots of ideas.

Sounds like you need a quick practical solution, rather than an interesting project. If so, don't be limited to Ubuntu. There may be a Linux Appliance you can quickly install based upon some other distro, maybe running from a CD rather than a hard drive.

Here's an interesting article: [http://www.eng.uwaterloo.ca/twiki/bin/view/Linux/LinuxKiosk](http://www.eng.uwaterloo.ca/twiki/bin/view/Linux/LinuxKiosk)

---

### Post by WasMeHere on 2011-10-27
Hi silvergoat,

The following link points to a linux kiosk that is updated recently [[COLOR="RoyalBlue"]_http://webconverger.com/_[/COLOR]]("http://webconverger.com/")

I have tried it and I suggest that you download the iso file and make a boot CD to find out if it is what you need.

Have fun finding out about linux :-)
Olle

---

