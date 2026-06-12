---
title: "How do I set the wins name resolution timeout?"
date: 2010-12-18
forum: Networking &amp; Wireless
---

### Post by Marcelo Ruiz on 2010-12-18
Hi,

I am experiencing horrible name resolution problems in Maverick. I believe this problem is related to having the following line in nsswitch.conf:

hosts:          files wins dns

I do use Samba and access windows shares in my network (that's why wins precedes dns. I was wondering if there is any way to setup a wins lookup timeout so it can fail quickly enough to try to perform the lookup using dns.
Thanks!

---

### Post by Marcelo Ruiz on 2010-12-18
mmm... nobody? :o

---

### Post by capscrew on 2010-12-19
> **Marcelo Ruiz said:**
> Hi,

I am experiencing horrible name resolution problems in Maverick. I believe this problem is related to having the following line in nsswitch.conf:

hosts:          files wins dns

I do use Samba and access windows shares in my network (that's why wins precedes dns. I was wondering if there is any way to setup a wins lookup timeout so it can fail quickly enough to try to perform the lookup using dns.
Thanks!


The answer is:  You should not use *wins * in the hosts line in nsswitch.conf.  There are already methods to resolve the NetBIOS names is Samba without resorting modifying the nsswitch.conf file.

Samba (and all Windows hosts) will broadcast their NetBIOS names.  To have Samba check broadcasts first it would be better to modify the smb.conf file.  You can set the name resolution order like this:```

# This is the default order
name resolve order = lmhosts host wins bcast

# This will make cause Samba to look at broadcasts first
name resolve order = **[COLOR="Red"]bcast [/COLOR]**lmhosts host wins 

```

You can see this in the Samba.org documentation [**_here_**]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html").  Look for the section with the heading **[SIZE="2"][COLOR="Blue"]name resolve order (G)[/COLOR][/SIZE]**.  The (G) means that this should be in the global section.

This method is far better.  Why?  This causes Samba to find NetBIOS names.  The other way causes the OS to attempt to do that.  If you try and have the OS lookup NetBIOS names first it will hang.  You do not need to do that for the majority of apps (FF or Chrome, etc.).    

This is a [**_bug that describes_**]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/309539") what I am talking about.

In [**_this Thread _**]("http://ubuntuforums.org/showthread.php?t=1640787")(near the end), Morbius1 uses the technique.

---

### Post by Marcelo Ruiz on 2010-12-20
Hi capscrew!

Thanks for the info. It really makes sense, so I will make the suggested changes!

---

### Post by capscrew on 2010-12-20
> **Marcelo Ruiz said:**
> Hi capscrew!

Thanks for the info. It really makes sense, so I will make the suggested changes!

Please let us know how the changes work out.  I am interested in your success with this.

-Capscrew

---

### Post by Marcelo Ruiz on 2011-01-06
Hi Capscrew,

Sorry for the late reply, but I wanted to be able to try everything before giving you an answer.

In my network I have 3 computers (all set with the same workgroup: WORKGROUP1): WinXP_x86, Ubuntu_x86, Ubuntu_x64. 

Setting the nsswitch in both ubuntu computers with:
```
hosts:          files dns mdns4_minimal [NOTFOUND=return] mdns4 wins
```
and smb.conf with:
```
name resolve order = bcast lmhosts host wins
```
I ended up with this situation:

- WinXP_x86 randomly sees Ubuntu_x86 when going to "view workgroup computers" under My Network Places, but never sees Ubuntu_x64. Sometimes when I refresh the view, it founds nothing for a while, but soon after it shows Ubuntu_x86.

- Ubuntu_x86 cannot sees any computers when going to "Places -> Network", but it can see itself (next to the Windows Network folder). When opening the Windows Network folder, the workgroup folder is displayed, but if I open it, the only computer listed is Ubuntu_x86. After a long time (more than 30 min) when I hit the refresh button, it can see the WinXP_x86 and access it shares.

- Ubuntu_x64 sees all the WinXP_x86 shares when going to "Places -> Network", but it cannot see itself. If I open the Windows Network folder, nothing is displayed.

All the computers can connect to each other if I use their IP address.
Pretty messy, right? Please let me know what you think...
Thanks again!

---

### Post by mateo305ci on 2011-01-06
I'm having the same issue with name resolution (may access shares by IP, but not name). I would be interested to see what the fix is for this...

---

### Post by capscrew on 2011-01-06
> **Marcelo Ruiz said:**
> Hi Capscrew,

Sorry for the late reply, but I wanted to be able to try everything before giving you an answer.

In my network I have 3 computers (all set with the same workgroup: WORKGROUP1): WinXP_x86, Ubuntu_x86, Ubuntu_x64. 

...

All the computers can connect to each other if I use their IP address.
Pretty messy, right? Please let me know what you think...
Thanks again!

Hi Marcelo,

Are the hosts really named *WinXP_x86, Ubuntu_x86 Ubuntu_x64*?  If not, then where I have used *WinXP_x86* or *Ubuntu_x86* please use their host names.

Lets see what is really happening.  To make things a little more simple let's only deal with the hosts *WinXP_x86* and *Ubuntu_x86*.

Please post the results you get from the terminal of the host *Ubuntu_x86* for this (**use the host name**) 
```
smbclient -L WinXP_x86 -d2
```

This should list the shares on *WinXP_x86*.  The -d2 switch raises the debug level so we can see what is going on.  The debug level can be set higher.  I believe you can go up to -d10, but you would never need that level of detail.

Here is what I get when I use the same command.  The Ubuntu host is *rincon *and the XP host is *manila*. I highlighted in green the name mapping between the host name and the IP address ```

cap@rincon:~>smbclient -L manila -d2

[COLOR="Green"]**added interface ip=192.168.1.2 bcast=192.168.1.255 nmask=255.255.255.0**[/COLOR]
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
[COLOR="Green"]**Got a positive name query response from 192.168.1.151 ( 192.168.1.151 **[/COLOR])
Password:
Domain=[MANILA] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        IPC$            IPC       Remote IPC
        print$          Disk      Printer Drivers
        SharedDocs      Disk
        Disks           Disk
        Printer3        Printer   Adobe PDF
        Printer2        Printer   HP LaserJet 2200 Series PCL 5e
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        Printer         Printer   Microsoft Office Document Image Writer
Got a positive name query response from 192.168.1.151 ( 192.168.1.151 )
Domain=[MANILA] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
cap@rincon:~>

```

Hi mateo305ci,

Follow along and  see if this helps you.  Don't post your results here though.  It would be confusing the issue.  I'll address you concerns after I get Marcelo's problems sorted out.

---

