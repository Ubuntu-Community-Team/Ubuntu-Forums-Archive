---
title: "Windows workgroup password"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by TruckerDJ on 2010-02-23
Strange networking issue. I have a home network with 1 Vista, 2 XP machines, and this Ubuntu 9.10 machine. The other day the network was working just fine. All machines could access each other with no issues.

Now today all the Windows machines can access shared files on the Ubuntu machine, but the Ubuntu machine can't access the GEOTRUCKERS workgroup. It is asking me for a user name and password, of which there is none.

Anybody have any thoughts or insights into what happened? Or better yet what I need to do to get things going again? 

Thankfully my Network Drive is showing up outside of the Windows workgroup, at least I have access to those files.

PS I am a newbie to Ubuntu. So hopefully this will be an easy fix.

---

### Post by TruckerDJ on 2010-02-23
UPDATE: My windows machines are still accessible on the Ubuntu machine via the few bookmarks I created, and by directly typing the link in the address bar. So actual connectivity is not an issue, it's more an issue of navigation.

It's just a pain that I can't access them directly  by means of Nautilus navigation since the Workgroup has been mysteriously asking for a password all of a sudden.

Is there any way to fix this?

---

### Post by tom4jean on 2010-03-15
Sorry, Don't have the answer. I just want to bump the thread since I was going to start one anyway.
I have the same problem.
I set up my windows workgroup on my desktop to be without a password and it works fine to access it with either windows vista or 7 from a laptop but in Ubuntu 9.10 when I try to open the share and enter my user name leaving the Password blank it keeps asking for the password when there is not one.

---

### Post by TruckerDJ on 2010-03-21
With any luck Ubuntu 10 will address this networking issue and allow my Ubuntu boxes to communicate with the rest of the window$ network.

---

### Post by TruckerDJ on 2010-04-01
No great networking improvements with the latest version of Lucid Lynx (10.04 LTS) Same old same old, as far as not easily integrating into an existing windows network.

I find it strange that running Windows 2K in a Virtual Machine (VMWare) works flawlessly with my existing network while with the Ubuntu (Gnome desktop) it's like pulling teeth to access network resources. At least i know it's not a hardware issue.

---

### Post by bmaring on 2010-04-01
I am having the same issues.  Running ubuntu 9.10 on VMWare under XP -- all the latest level.  Up until about a week ago, was able to browse windows file shares and use windows printers -- both XP and 7.  However, following an update that involved samba, can no longer mount shared files or connect to shared printer.  I have gone through all of the suggested fixes, with no joy.  By the way, the host XP can browse shared files and use shared printer just fine.

It appears that something was messed up in the samba update that went out about a week ago.

---

### Post by 98cwitr on 2010-04-01
How are the security permissions on the GEOTRUCKERS share set? Is 'Everyone' allowed full control?

---

### Post by TruckerDJ on 2010-04-05
> **98cwitr said:**
> How are the security permissions on the GEOTRUCKERS share set? Is 'Everyone' allowed full control?


All shared resources on the GEOTRUCKERS workgroup have permissions wide open. Everyone is allowed full control.

---

