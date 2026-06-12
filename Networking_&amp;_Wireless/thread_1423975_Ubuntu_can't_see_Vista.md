---
title: "Ubuntu can't see Vista"
date: 2010-03-07
forum: Networking &amp; Wireless
---

### Post by rleggett on 2010-03-07
Trying to set up network sharing between Ubuntu 9.10 and Vista.  I already did this with a wired Ubuntu 9.10 desktop and my Vista laptop but for some reason my Ubuntu 9.10 wireless and Vista wireless aren't as easy.  They are all on the same workgroup "MAGIC" and I can see my ubuntu shares on the Vista computer but can't see the Vista shares on the ubuntu computer. In ubuntu I go to network>windows network>MAGIC but it times out at the MAGIC workgroup part and says 'unable to mount'. I have already been here and tried all that I could find that's relevant to my problem:
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)
but no luck
I also checked and there isn't a firewall that's in the way.  Any help?

---

### Post by sikander3786 on 2010-03-07
I don't really know what is happening.

Yet I had this problem some time ago. I didn't had password protected my Windows and Ubuntu was unable to connect to it. Have you set up a password on your Windows Install?

---

### Post by rleggett on 2010-03-07
Nothing is password protected for my network beyond connecting to it with WEP.  I am able to connect to the internet and I can see that there is a workgroup named 'MAGIC' but as soon as I try to connect to the workgroup, it appears to timeout and says 'cannot mount workgroup'.

---

### Post by sikander3786 on 2010-03-08
> **rleggett said:**
> Nothing is password protected for my network beyond connecting to it with WEP.  I am able to connect to the internet and I can see that there is a workgroup named 'MAGIC' but as soon as I try to connect to the workgroup, it appears to timeout and says 'cannot mount workgroup'.

The only solution I can think of is to set a password on you vista install or edit Group Policy on Windows machine and set it to allow blank passwords.

Check this one out.

[http://www.pcwindowstips.com/2007/09/05/how-to-allow-network-access-using-a-blank-password-in-windows-vista/](http://www.pcwindowstips.com/2007/09/05/how-to-allow-network-access-using-a-blank-password-in-windows-vista/)

---

