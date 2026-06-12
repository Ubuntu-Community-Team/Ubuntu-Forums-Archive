---
title: "Can See Ubuntu Machine from XP But Can't Connect"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by wacole on 2009-01-28
I am running XP SP3 on machine 1 and Ubuntu 8.04 on machine 2.  NetBEUI runs on my network along w/TCP/IP.  

I use a workgroup not a domain.

When looking at the XP machine from the Ubuntu machine I can see XP, can connect and can exchange files.

When looking at the Ubuntu machine from the XP machine I can see the Ubuntu machine but when trying to connect, receive the dialog box "\\Ubuntumachine is not accessible.  You might not have permission to use this network resource. ..."

I have used the excellent thread [http://ubuntuforums.org/showthread.php?t=1051578&highlight=xp+shares](http://ubuntuforums.org/showthread.php?t=1051578&highlight=xp+shares) which helps confirm what does work but doesn't seem to help with this particular problem.

Here's the output from ipconfig /all:
C:\Documents and Settings\Administrator.PEEVES>ipconfig /all



Windows IP Configuration


[FONT="Fixedsys"]
        Host Name . . . . . . . . . . . . : peeves

        Primary Dns Suffix  . . . . . . . :

        Node Type . . . . . . . . . . . . : Unknown

        IP Routing Enabled. . . . . . . . : No

        WINS Proxy Enabled. . . . . . . . : No



Ethernet adapter Local Area Connection:



        Connection-specific DNS Suffix  . :

        Description . . . . . . . . . . . : Intel(R) PRO/100 VE Network Connecti

on

        Physical Address. . . . . . . . . : 00-0C-F1-79-10-0C

        Dhcp Enabled. . . . . . . . . . . : No

        IP Address. . . . . . . . . . . . : 192.168.1.102

        Subnet Mask . . . . . . . . . . . : 255.255.255.0

        Default Gateway . . . . . . . . . : 192.168.1.1

        DNS Servers . . . . . . . . . . . : 192.168.1.1
[/FONT]

Thank you very much for any advice that can be offered.  I've reached the end of my skill set.

Bill Cole

---

### Post by Iowan on 2009-01-28
Did you install Samba (more specifically, the server)? 
Have you generated a Samba user/password?

---

### Post by wacole on 2009-01-29
Thanks.  When I upgraded from 6.04LTS, I assumed that Samba was installed at that time as I can access all of my network [2 linux, 2 W2K, 2XP] from Ubuntu.  The only problem is when attempting access to my Ubuntu machine from XP.  [I can see my XP machine from Ubuntu, can copy files from XP to Ubuntu, but I can't copy files from Ubuntu to XP.]

As to the password, I'm not sure.  There may be something there because the only password that I recall generating for the Ubuntu machine is the login.  I'll look into a Samba password and report back.

Thanks very much for the pointers.

---

### Post by wacole on 2009-01-29
Checked my Samba password for my main login using the gtk tool **system-config-samba**.  Using this tool I made sure that the password for my main login was the same as what Ubuntu expected.  Then tried to access a Ubuntu share from XP.  Same problem ... XP "\\*server* is not accessible. ...." [I also installed SWAT and can't see anything amiss in the Samba config file ... I just don't know enough!]

At this point I'm just throwing darts blindfolded.  There must be a better - more methodical - way to go about troubleshooting this.

Thanks again,

---

### Post by sysadmn62 on 2009-01-29
> **wacole said:**
> Thanks.  When I upgraded from 6.04LTS, I assumed that Samba was installed at that time as I can access all of my network [2 linux, 2 W2K, 2XP] from Ubuntu.  The only problem is when attempting access to my Ubuntu machine from XP.  [I can see my XP machine from Ubuntu, can copy files from XP to Ubuntu, but I can't copy files from Ubuntu to XP.]

As to the password, I'm not sure.  There may be something there because the only password that I recall generating for the Ubuntu machine is the login.  I'll look into a Samba password and report back.

Thanks very much for the pointers.

Are you sure samba client AND server are installed, and that the server is running?  The Ubuntu -> Xp path uses client tools, but Xp -> Ubuntu requires the server.  I believe if you're able to use SWaT, the server is running, but it wouldn't hurt to check.  Also, if you're able to see Ubuntu from XP, it might mean the server is running, or it might be that attaching as a client is enough to make you visible - I don't know.

---

