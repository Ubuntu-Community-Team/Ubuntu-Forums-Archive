---
title: "Laptop can access the internet at home but not at work -- why?"
date: 2011-09-29
forum: Networking &amp; Wireless
---

### Post by HangukMiguk on 2011-09-29
Having a really weird problem, and it only first started on Monday.

I take my laptop with me to my office.  At the office, there are 3 different networks for my building, all of which I have the encryption key for, all of which are connected to the Internet.  I cannot access the internet on any of them.  There was an open network nearby that I used to access the internet from work.  That was working for several weeks, then after about 5 minutes online Monday morning, I could no longer access the Internet on that one either.

I can successfully connect to all of these networks, and pull valid IPs for each of them.  But I cannot access the Internet from these networks.  I know they are connected to the Internet for two reasons:

1) My coworkers can access the Internet from these networks on their computers.
2) There was a desktop at my desk running Windows 7, which I used to prove that I could connect to these networks and access the Internet.  The only flaw is that this desktop shuts itself off every 3-5 minutes, so it's useless except to prove my point.

I can access the Internet perfectly fine at home, however, not at work, where I need the Internet.  I talked to the IT guy at work, and he stood there scratching his head at my laptop, asking what kind of virus I downloaded that caused my desktop to look like this (Linux -- apparently he's not that great at his job), stared at my screen like a monkey doing a math problem, I advised him that the desktop can access the internet, but it shuts itself off.  He, without saying another word to me, unplugged the desktop, carried it out of the office, and I haven't seen him since.  That was Tuesday, tomorrow will be Friday, and for an entire week, I have been without internet at work.

I have no clue what to blame for this mess, and apparently will get no help from the tech department at my job.

Any ideas?

---

### Post by WasMeHere on 2011-09-29
Maybe the LAN configuration has been changed, so that the attached computers must be matched to a list item in order to be allowed to use the LAN server(s), the internet or both. Such changes can happen during upgrading of the network and it is common that companies improve the internet security. Maybe the system scans and 'whitelists' the Windows computers automatically, but it cannot handle a linux computer, or maybe a home computer is no longer supposed to be attached.

Encryption (if WLAN) may be introduced or changed, and your computer must be adjusted to it.

Can you ask your boss or an IT guy for help to get internet access again?

---

### Post by HangukMiguk on 2011-09-29
He is Linux retarded, so trying to get him to try to do it for me is pointless.

Wouldn't a whitelist be based on MAC addresses?  Because if so, the NICs being used are D-Link USB wireless dongles for all the computers in the office, my "desktop" was no exception.  So, thinking it was a whitelist issue, I've also plugged it into my computer, and tried connecting through that, but I experience the same issues, so I don't think it's even a whitelist issue.

I've even tried cloning that MAC address to no avail.

---

### Post by 2F4U on 2011-09-29
Is your company using a proxy server that has to be configured in the web browser?

---

### Post by WasMeHere on 2011-09-29
> **HangukMiguk said:**
> ...trying to get him to try to do it for me is pointless.

Maybe you can convince your boss that you do your job much better with internet access, and then he will help you to get a working connection either with a Windows computer or with your own one.

> Wouldn't a whitelist be based on MAC addresses?  Because if so, the NICs being used are D-Link USB wireless dongles for all the computers in the office, my "desktop" was no exception.  So, thinking it was a whitelist issue, I've also plugged it into my computer, and tried connecting through that, but I experience the same issues, so I don't think it's even a whitelist issue.

I've even tried cloning that MAC address to no avail.

Yes, it is common to use the MAC address, but other methods can also be used for identification. Someone at your company/institution should know, or a consultant if IT is out-sourced to another company. Can you or your boss find him/her?

---

### Post by HangukMiguk on 2011-09-30
Well, I called him today to see what was up, and he said "I'm replacing a part (I'm assuming the power supply) in your desktop and will bring it back to your today."

My desk is still devoid of a working computer.

---

### Post by HangukMiguk on 2011-09-30
> **2F4U said:**
> Is your company using a proxy server that has to be configured in the web browser?

Not to my knowledge, I was able to use Google Chrome freshly installed on a Windows 7 box without doing anything to it but installing it.

On top of that, coworkers are accessing Yahoo Messenger and the like as well.

---

