---
title: "Samba 3.4.0 in *buntu 9.10 does not work, when is the repo updated?"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by Redsandro on 2009-11-04
A lot of users complain smb:// links in nautilus are not working, pyneighborhood in Xubuntu is not working, fusesmb is not working, smbclient is not working, etc.

Apparently, samba 3.4.0 that came with *Buntu 9.10 is just buggy. Restoring 9.04 makes it work again.

Some people say you only have this problem if you have a Windows 7 machine in your network, and some say the issues are fixed with Samba 3.4.3. (not verified by me).

Other evidence samba is broken on 9.10:
Gigolo (gvfs) does work.
XBMC's built-in samba protocol works.

Aren't there a million people with similar problems? Shouldn't the fixed or backpatched version be available as a recommended update by now?

---

### Post by Mal Bridgeman on 2009-11-04
[COLOR="DarkRed"]Mine is foobar'ed but I put it down to my own numptiness ;)
Mal[/COLOR]

---

### Post by weedwacker on 2009-11-04
Samba in 9.10 is definitely messed up. It even messes up samba to another machine running 9.04. And neither can see my Windows XP Pro machine.

But good 'ol Windows can see both Ubuntu machines and can access shared folders.

Sometime my Ubuntu machines can see each other and most times not.

I have been trying many things over the last three days and na da.

Sorry to say that 9.10 is buggy with samba.:(

This from smbclient -L <hostname> (my Ubuntu 64 bit Karmic to the Win XP Pro:

hp64@hp64-desktop:~$ smbclient -L salslaptop
Enter hp64's password: 
Connection to salslaptop failed (Error NT_STATUS_BAD_NETWORK_NAME)

---

### Post by Redsandro on 2009-11-04
I learned about a **partial** fix!



[SIZE="3"]**(x)ubuntu** <-> **(x)ubuntu**[/SIZE] fix

> **lakerssuperman said:**
> I was having trouble seeing my shares.  I would look under problem #3 in this thread.  You have to uncomment a line in your smb.conf file and rearrange the ordering of that line.  Once I did that I could see all my computers and shares.

[http://ubuntuforums.org/showthread.php?t=1169149&highlight=samba+browsing]("http://ubuntuforums.org/showthread.php?t=1169149&highlight=samba+browsing")

Change this:
";   name resolve order = lmhosts host wins bcast"

To this:
"name resolve order = lmhosts wins bcast host"

And then issue:
'sudo /etc/init.d/samba restart' from a terminal



[SIZE="3"]**(x)ubuntu** -> **Windows 7**[/SIZE] fix

Use **regedit.exe** to change the Lanmanager compatibility:

```
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\LmCompatibilityLevel = 2
```
**LmCompatibilityLevel** = REG_**DWORD** value **2**

See [http://technet.microsoft.com/en-us/library/cc960646.aspx](http://technet.microsoft.com/en-us/library/cc960646.aspx)



[SIZE="3"]**Windows 7** -> **(x)ubuntu**[/SIZE] fix

None that we mortals have any control of as far as I know. :cry:
We must all kill angels on the graveyard until the Ubuntu-gods decide to put samba 3.4.3 in the repo's. :(

---

### Post by fgluck on 2009-12-15
Simple network, 3 XP systems and one Ubuntu Karmic Koala and one Windows 7 system. Everything worked perfect on previous version of Ubuntu. When I upgraded from Jaunty to Karmic the Samba world quit working :( & :?

Now, only the Windows 7 system can access the shares on Ubuntu. All of the XP systems can see Ubuntu and the directories that are shared and add it to their network places.

When the XP systems try to access the shares on Ubuntu, an error is thrown and the XP systems complain about not having permissions. Again -- the Windows 7 system works perfectly.

Really, really really need to fix this.

zzyzx

---

