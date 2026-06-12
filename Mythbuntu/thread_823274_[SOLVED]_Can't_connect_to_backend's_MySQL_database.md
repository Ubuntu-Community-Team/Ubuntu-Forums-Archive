---
title: "[SOLVED] Can't connect to backend's MySQL database"
date: 2008-06-09
forum: Mythbuntu
---

### Post by yonkiman on 2008-06-09
This is really a continuation of a previous thread ([http://ubuntuforums.org/showthread.php?t=815329](http://ubuntuforums.org/showthread.php?t=815329)), but I wanted to change the subject to be more accurate since I'm now certain the problem is with connecting to the SQL server on my backend.

I've got one box with frontend and backend (at 192.168.1.104) working fine.  I'm trying to get a new frontend going, which is at 192.186.1.105.  But the 105 mythfrontend.real hangs when it tries to connect.  It can ping 104 OK, but it doesn't connect.  Reasons I'm pretty sure the problem is my backend:
[LIST]
[*] I launched the mythbuntu 8.04 32 bit install CD in frontend mode, and it failed the MySQL database check (Click on "Test MySQL Connection" and got "Failure").  Pinging 192.168.1.104 from a terminal worked, so the networking was there.
[*] I rebooted the same PC into Windows, loaded WinMyth (MythTV Front End for Windows, and it worked OK.  It's my understanding that WinMyth doesn't use the MySQL database, so this seems to indicate that most everything is fine except the MySQL portion.
[/LIST]

Are there any other tests I can do to see where the problem might lie?  Or another way to look at it:  What are the exact steps you need to take to make the backend of a vanilla Mythbuntu 8.04 ***64 bit*** frontend+backend installation available to other frontends?  I emphasized 64 bit, because perhaps that's why I'm having trouble.  The frontends I'm using are all 32 bit...could it be the frontends and backends need to all be 32 or all be 64 bit?

Here are the steps I've already taken to try to resolve this:
[LIST]
[*]Local Backend IP address changed to 192.168.1.104 in MythTV Backend Setup`
[*]Master Backend IP address changed to 192.168.1.104 in MythTV Backend Setup
[*]Commented out the "bind-address" line in /etc/mysql/conf.d/mythtv.cnf
[*]Commented out the "bind-address" line in /etc/mysql/my.cnf
[*]Alternately, tried setting "bind-address" = 192.168.1.104 in /etc/mysql/my.cnf
[/LIST]

One final thought: The MySQL database password I'm using is the one shown in the General setup page of the working Myth frontend on the 192.168.1.104 PC where both front and back ends are working.  I'm sure that's the same password I use for my other front ends, but then again I was sure I wouldn't have this much trouble bringing up an additional front end!  :-)

---

### Post by tgm4883 on 2008-06-09
I really do hate it when people just to conclusions that just because something is 64-bit that it may be where the problem lies.  Please do not believe every critic of 64-bit on the forums, they are just trying to breed longer support for their dying format.  Rest assured, that 64-bit computing is not the problem here. 

On the master backend have you enabled the mysql service in MCC and rebooted the machine?

Have you tried connecting to mysql from the command line on the remote system?

---

### Post by yonkiman on 2008-06-09
> **tgm4883 said:**
> I really do hate it when people just to conclusions that just because something is 64-bit that it may be where the problem lies.  Please do not believe every critic of 64-bit on the forums, they are just trying to breed longer support for their dying format.  Rest assured, that 64-bit computing is not the problem here.

That's what I thought, but it seems like I'm having more trouble with this than most others, so I'm trying to think of what I may be doing differently than most others...

> On the master backend have you enabled the mysql service in MCC

MCC = MythTV Control Center, right?  I'm pretty sure it's enabled (it would be pretty embarrassing if it wasn't), but I haven't looked in a while and I'm at work right now...  Isn't it enabled by default?

> and rebooted the machine?

Oh, have I rebooted the machine... :-)

> Have you tried connecting to mysql from the command line on the remote system?

I don't know how to do that.  Can you point me to an example?

Thanks,
Fred

---

### Post by tgm4883 on 2008-06-09
No it isn't enabled by default, although some of the steps that you did seem to indicate you did it the hard way, i would still try doing it.

Try connecting from the remote frontend command line by doing this 

```
mysql -h hostname -D mythconverg -u mythtv -p 
```

then using the same password that is on your master backend located at ~/.mythtv/mysql.txt

:EDIT:

Oh, and MCC is Mythbuntu Control Centre

---

### Post by yonkiman on 2008-06-10
> **tgm4883 said:**
> On the master backend have you enabled the mysql service in MCC and rebooted the machine?

Well that's embarrassing.  I hadn't, and when I did, it worked - I could access MySQL remotely.  Problem solved.

In my defense, I thought MySQL was already completely on and working by virtue of MythTV working.  I didn't know you needed to enable MySQL in MCC to get it working for external access.

Thank you very much, tgm4883!

---

