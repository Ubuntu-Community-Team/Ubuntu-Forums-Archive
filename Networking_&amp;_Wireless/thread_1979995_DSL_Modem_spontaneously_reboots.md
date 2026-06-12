---
title: "DSL Modem spontaneously reboots"
date: 2012-05-14
forum: Networking &amp; Wireless
---

### Post by Old Newville on 2012-05-14
Hi all,

I'm mystified by poor DSL performance. My modem spontaneously reboots, often at random when there is no traffic coming or going, and almost *always* when I try to complete any large uploads/downloads.

Here are the important details of my dilemma:

I use Ubuntu 10.04 on a Dell Pentium 4 machine for household computing and my freelance writing business. I write with LibreOffice and process photos with GIMP.  I run Windows XP in VirtualBox for compatibility reasons, such as when a client wants me to use an MS Word template. My email software is Thunderbird.

I email my photo files (often 25-30 mb in size) to my clients. I recently sent 5 files, but my modem rebooted each time I clicked "send," so I broke them down and sent them one at a time, and that worked. It took about 30 minutes to send them, but my ISP's advertised upload speed is only 640 kbps. My ISP is CenturyLink. Speed is less important to me at the moment than reliability.

My question is: What causes these reboots? Is it file size? Is it a network hiccup? Do I need to find another ISP? Do I need to replace the modem? Do they intentionally limit the amount of data I can upload?

CenturyLink replaced all the wiring from the phone jack to the street, so that's probably not it. I've been on the phone with CenturyLink techs and they couldn't figure out the problem. I shortened the length of phone wire between the wall and the modem down to less than 2 feet. I have a 50-foot ethernet cable connecting the modem with a wired/wireless router in my home office.

CenturyLink's only competition where I live is from Comcast, and I don't really like them, either.

Does anyone have any ideas about what I should try to do?

---

### Post by praseodym on 2012-05-14
Hi,

does it also "reboot" if connected to the router? How do you connect? Via NetworkManager-applet or via "sudo pppoeconf" if not using the router? Are you member of the group "dip"?

> sudo adduser $USER dip
and login again.

---

### Post by Old Newville on 2012-05-14
Hi,

Thanks for your reply. I just checked, and I am part of the group "dip."

I connect to the 'Net using an ethernet cable connected to a Zyxel 660-R modem and a Level One router. 

We have a couple of wireless laptops running Windows 7 and Ubuntu. The Windows 7 user complains about the same problem, mainly with remote desktop-type connections; and she uses Outlook for email, not Thunderbird.

So, I assume the source is between the router, modem and ISP.

We have a 3 mbps download speed and a 640 kbps upload speed. Download speed is more than enough to play music from Pandora and even to watch movies on Netflix, at times without interruption.

---

