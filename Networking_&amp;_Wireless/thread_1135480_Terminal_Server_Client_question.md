---
title: "Terminal Server Client question"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by Fred61 on 2009-04-24
One of my jobs, is to manage and check in remotely on 5 seperate Small Business Servers.

Windows remote desktop works on all 5
Ubuntu Terminal Server Client only works on 4

On the 5th one, I can see the login screen partially formed sometimes completely but it then disconnects and returns a connect reset by peer error.

I've tried both the RDPv5 and just the RDP modes both give the same results.

Currently to by pass having to restart my system in Windows, I log in to one of the other servers then remote desktop into #5

Anyone have any suggestions? I am a new convert trying my best to free myself and my clients from a Microsoft world.

Thanks

Fred

---

### Post by Fred61 on 2009-04-28
Shameless bump as I'm still at a loss as to why one of the servers does not work yet the other four do.

---

### Post by Trev2HI on 2009-04-28
You might want to check out Gnome-RDP. I have had much better luck with this client. Upgrading to Jaunty did seem to break it, however, and I have yet to search for an updated version. If you are using Intrepid you should just be able to use

sudo apt-get install gnome-rdp

Hope this helps.

-T

---

### Post by Fred61 on 2009-04-28
Thanks I did the Apt get just to check, I am already running the latest version of Gnome-rdp

Fred

---

### Post by Trev2HI on 2009-04-29
So you have the same problem using both Ubuntu Terminal Server Client and Gnome-RDP? 

Have you tried restarting the server that you are having a problem connecting to? You might try deleting and recreating the RDP-tcp connector in Terminal Services Configuration prior to restarting.

---

### Post by Fred61 on 2009-04-30
Yes same problem with both..

Yes I have restarted the problem server.. It is a windows SB server so after about a month it's leaked enough memory to warrant a restart.

I guess as a last resort I could un-install and reinstall the terminal service but it is currently working with MS remote desktop, and I'm not sure the end-user still has the SBS disk.

Currently up grading my desk top to Jaunty 

Thanks for the advice

Fred

---

### Post by Trev2HI on 2009-04-30
I doubt reinstalling Terminal Services will do you any good. Deleting and recreating the connector might.

I would also suggest checking your server Event Log for clues if you have not already.

-T

---

