---
title: "MSDOS and Samba"
date: 2010-09-29
forum: Networking &amp; Wireless
---

### Post by Colin R on 2010-09-29
Hi All,

Absolute newbie and having a number of 'senior moments'.

The company I work for has decided to ditch it's 1994 vintage Netware server and replace it with a nice shiny new Ubuntu box.

I have built the new server and installed Ubunto 10.  No problem

I can connect and do everything I need to from Windows 98 and XP.

Problem is that we have a few old MSDOS 6 based PC's that, although they do not do very much, are essential to our operation.

I have tried to connect these PC's to Samba and have had limited success.

I can 'ping' the Ubuntu box so, the networking seems to be OK but I can't seem to get the 'Net Use' commands to work. (Error 53 etc.)

Is anyone who has connected MSDOS 6 to Samba willing to post a step by step idiots guide or, if possible, point me to one.

TIA

Colin R.

---

### Post by capscrew on 2010-09-29
> **Colin R said:**
> Hi All,

Absolute newbie and having a number of 'senior moments'.

The company I work for has decided to ditch it's 1994 vintage Netware server and replace it with a nice shiny new Ubuntu box.

I have built the new server and installed Ubunto 10.  No problem

I can connect and do everything I need to from Windows 98 and XP.

Problem is that we have a few old MSDOS 6 based PC's that, although they do not do very much, are essential to our operation.

I have tried to connect these PC's to Samba and have had limited success.

I can 'ping' the Ubuntu box so, the networking seems to be OK but I can't seem to get the 'Net Use' commands to work. (Error 53 etc.)

Is anyone who has connected MSDOS 6 to Samba willing to post a step by step idiots guide or, if possible, point me to one.

TIA

Colin R.

See if [**_this _**]("http://www.jacco2.dds.nl/samba/dos.html")helps.  It has been ages since I used DOS.  This is just an educated guess.  :-)

---

### Post by Colin R on 2010-09-29
> **capscrew said:**
> See if [**_this _**]("http://www.jacco2.dds.nl/samba/dos.html")helps.  It has been ages since I used DOS.  This is just an educated guess.  :-)

Hi Capscrew,

Thanks for the reply.

I'll take a look at the link.

Colin R.

---

### Post by capscrew on 2010-09-29
> **Colin R said:**
> Hi Capscrew,

Thanks for the reply.

I'll take a look at the link.

Colin R.
Colin,

After I sent you the link, I spent some time thinking about what Netware meant to MSDOS and how OS's have changed from those really old days. 

MSDOS was created in the days when nobody thought about Ethernet  or TCP/IP networking very much.  PC's were stand alone devices.

Netware exploited the lack of networking and built their server products on top of the MSDOS.  Novell provided the networking services for MSDOS along with the other user and data management.  Microsoft finally woke up and added them at the very end with Win3.1.  Imagine that:  A GUI on DOS with networking abilities.  :-)

Remember that MSDOS is a 16bit operating system while win95/98, Win2000,XP, Vista, Win7 and later are either 32bit or 64bit OS's.  Ubuntu is either 32 or 64 bit OS's.  This means lots of ** incompatibility**.  File naming, file size, file permissions.  There is no thought of backwards compatibility to MSDOS here.

The question I think of is:  What is so critical that you have to use MSDOS to interface with it? Is it industrial or a monitoring device (temp/humidity)?  What is the data that needs to transfered over a network?

This is not a trivial update that you are attempting.

-Capscrew

---

### Post by Colin R on 2010-09-29
> **capscrew said:**
> Colin,

After I sent you the link, I spent some time thinking about what Netware meant to MSDOS and how OS's have changed from those really old days. 

MSDOS was created in the days when nobody thought about Ethernet  or TCP/IP networking very much.  PC's were stand alone devices.

Netware exploited the lack of networking and built their server products on top of the MSDOS.  Novell provided the networking services for MSDOS along with the other user and data management.  Microsoft finally woke up and added them at the very end with Win3.1.  Imagine that:  A GUI on DOS with networking abilities.  :-)

Remember that MSDOS is a 16bit operating system while win95/98, Win2000,XP, Vista, Win7 and later are either 32bit or 64bit OS's.  Ubuntu is either 32 or 64 bit OS's.  This means lots of ** incompatibility**.  File naming, file size, file permissions.  There is no thought of backwards compatibility to MSDOS here.

The question I think of is:  What is so critical that you have to use MSDOS to interface with it? Is it industrial or a monitoring device (temp/humidity)?  What is the data that needs to transfered over a network?

This is not a trivial update that you are attempting.

-Capscrew

Hi Capscrew,

Thanks for the input.

When I first started working with computers (IBM, Nov 1967) nobody bought a machine just for one person to use.  That didn't happen until 1982/3 when the IBM PC was launched and one of the first wish list items was for some kind of networking.

The first (I think) PC OS that had any kind of built in networking was CPM.  

Very bad history lesson over...

The system that I am responsible for was written by myself using Clipper and is primarily accounting for eight companies and stock control for four.
Additionally, it also has a fully integrated EPOS System built in.

Other functions range from the mundane (eg:printing bar code labels) through remote comms to management reporting etc.

Personally, I would like to ditch the MSDOS PC's but, management are reluctant to buy new machines that will only spend 10 minutes or so per day priting labels etc.

Another complication (which I am sure that I can get around) is that most of the MSDOS PC's are 'diskless' and rely on Boot Roms to connect to the network.

I suppose that I should remind them that the latest version of the software will only run on Windoze :)
Doesn't get me past the immediate problem but, it's a get-out.

---

### Post by capscrew on 2010-09-29
> **Colin R said:**
> Hi Capscrew,

Thanks for the input.

When I first started working with computers (IBM, Nov 1967) nobody bought a machine just for one person to use.  That didn't happen until 1982/3 when the IBM PC was launched and one of the first wish list items was for some kind of networking.

The first (I think) PC OS that had any kind of built in networking was CPM.  

Very bad history lesson over...

Just to add to that.  My first machine was a DEC Rainbow.  It was CPM.  Then I purchased a Compaq 386 which became my server.  It became a Novell Netware 286 host running IPX about one week after I got it.  At first it ran ARCnet rather than Ethernet.  I used Netware until 4.11.  It got to expensive for what we were doing.  

It sounds like we have had similar experiences.> 

The system that I am responsible for was written by myself using Clipper and is primarily accounting for eight companies and stock control for four.
I was the Sysadmin.  My brother was the developer and we started with DBase III.  Later he converted to Clipper.  He still runs a complete medical practice with it (his own).  He runs it in a DOS window on Vista or Win7.  It works great.  The app runs from the server which is Win2003RC3.> 

Additionally, it also has a fully integrated EPOS System built in.

Other functions range from the mundane (eg:printing bar code labels) through remote comms to management reporting etc.

Personally, I would like to ditch the MSDOS PC's but, management are reluctant to buy new machines that will only spend 10 minutes or so per day priting labels etc.

Another complication (which I am sure that I can get around) is that most of the MSDOS PC's are 'diskless' and rely on Boot Roms to connect to the network.
We keep an ancient 386 host in case something needs recoding and then recompiling (that's real backwards comparability).> 

I suppose that I should remind them that the latest version of the software will only run on Windoze :)
Doesn't get me past the immediate problem but, it's a get-out.

Check out the link and see if it will work for you.  I was concerned that DOS was older that you were.  :-)  Now I see that you will understand the information there.

I think you should look at running in a DOS window.  I can tell you that Clipper will run in a DOS window for sure.  This includes talking to both shared and networked printers.  You can PM me if you want to about the details.

---

### Post by SeijiSensei on 2010-09-30
I think you want the **MS Lan Manager** client that appears in the list Capscrew posted.  I used to have a copy of this on my server, but a quick scan this morning shows I must have deleted it some time in the past. Luckily for you it's still freely available from Microsoft at:
[ftp://ftp.microsoft.com/BusSys/Clients/LANMAN/](ftp://ftp.microsoft.com/BusSys/Clients/LANMAN/)

Another option is to keep the Netware stack on the DOS machines and try using [mars_nwe]("http://www.linux.org/apps/AppId_6081.html"), a NetWare server clone for Linux, on the Ubuntu box.  That would work for file-serving though not, obviously, TCP/IP networking.  For that you'd need the TCP/IP stack for NetWare clients.

Another strategy might be to migrate the DOS machines to something capable of running Linux, then using [dosemu]("http://www.dosemu.org/") to run the DOS apps. 

I started a company in 1994 that aimed at helping organizations integrate their then-existing network facilities with the Internet.  I even wrote a book chapter on the subject with detailed instructions on using the NetWare TCP/IP stack, Trumpet Winsock, all that good stuff.  After Windows 95 appeared, though, the writing was on the wall as far as NetWare was concerned.  Suddenly you could network Windows computers without Novell.  In a year or two the expertise we had built up became irrelevant, though we continued to build Linux firewalls and servers for clients migrating to the brave new world of the Internet.

---

### Post by Colin R on 2010-09-30
> **capscrew said:**
> 
Check out the link and see if it will work for you.  I was concerned that DOS was older that you were.  :-)  Now I see that you will understand the information there.


Older than me.... Not even close..:P

> I think you should look at running in a DOS window.  I can tell you that Clipper will run in a DOS window for sure.  This includes talking to both shared and networked printers.  You can PM me if you want to about the details.

Thanks but, not necessary.  I already run my clipper apps in full screen mode on XP/98 and, so far, in a window on Vista/Win7.  Bit of a 'frap' on the latter two but, it works.
That's the reason for the windows based re-write..

Going to take a look at the link just now.  If I get it sorted, I'll post the results.

TNX
Colin R.

---

### Post by Colin R on 2010-09-30
> **SeijiSensei said:**
> I think you want the **MS Lan Manager** client that appears in the list Capscrew posted.  I used to have a copy of this on my server, but a quick scan this morning shows I must have deleted it some time in the past. Luckily for you it's still freely available from Microsoft at:
[ftp://ftp.microsoft.com/BusSys/Clients/LANMAN/](ftp://ftp.microsoft.com/BusSys/Clients/LANMAN/)

Yep, that's the one I thought would do it.  Time to roll the sleeves up.

> Another option is to keep the Netware stack on the DOS machines and try using [mars_nwe]("http://www.linux.org/apps/AppId_6081.html"), a NetWare server clone for Linux, on the Ubuntu box.  That would work for file-serving though not, obviously, TCP/IP networking.  For that you'd need the TCP/IP stack for NetWare clients.

Interesting thought.  Might be worth a look if I get myself stuck again.  I only need File Serving via IPX.  TCP/IP on the MSDOS based PC's is not required.

> Another strategy might be to migrate the DOS machines to something capable of running Linux, then using [dosemu]("http://www.dosemu.org/") to run the DOS apps. 

The MSDOS boxes are, presently, diskless 486 SX25's.  Dinosaurs by any definition.

> I started a company in 1994 that aimed at helping organizations integrate their then-existing network facilities with the Internet.  I even wrote a book chapter on the subject with detailed instructions on using the NetWare TCP/IP stack, Trumpet Winsock, all that good stuff.  After Windows 95 appeared, though, the writing was on the wall as far as NetWare was concerned.  Suddenly you could network Windows computers without Novell.  In a year or two the expertise we had built up became irrelevant, though we continued to build Linux firewalls and servers for clients migrating to the brave new world of the Internet.

Agreed, Win95 was the death knell, certainly for small installations, for Novell although larger Novell sites could see it off quite easily.
What killed Novell for sure was NT Server and the sheer marketing power of MS.  It gave MS the ability to provide scaleable networking solutions. (I hate that word(solutions)).


Colin R.

---

### Post by Colin R on 2010-10-07
OK, 1st up is that MSLanMan for DOS did the trick quite nicely.

Now I have another issue..:confused:

Performance using an old P75 pentium with 16Mb RAM + a 10Mb NIC is pretty decent when running my programs with 1 notable exception.

This might take a little explaining so, bear with me.

The main program being used is an old MSDOS based accounting/Stock/Invoicing system that (on this PC) wil be used for Invoicing/Stock Enquiries.
Performance in the Invoicing routines is pretty decent and is not an issue/
Stock Enquiries, however, seem a little sluggish and take several seconds to perform some simple tasks.  The same PC, when connected to the Novell network(with no changes other than the network log-on), has excellent performance all round.

Another routine that is VERY disappointing is in the Utilities section (Sort Files and Re-Index).  
Normally, this would not be an issue but, 1 MSDOS pc on the network is responsible for scheduled remote comms (via PC-Anywhere to external depots) and, after collecting/processing external data, has to re-build all the indexes.
The Novell system has worked flawlessly for years and this particular routine takes about 16 minutes.
The same routine on the Linux box takes 'forever'.

Now, I'm not doing anything particularly clever at this point, just using the standard Clipper calls to copy the files to a TMP directory, re-build the indexes (on the copies) and, if succesful, copy them back to the DBF directory (the indexes are copied to a NTX directory.

Sorry for the length of this post and the odds are that I have either overlooked something basic or done something 'stupid' but, does anyone have any ideas why the performance is an issue on the Linux box?

---

