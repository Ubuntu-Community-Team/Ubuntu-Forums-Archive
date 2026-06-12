---
title: "Cannot see my Ubuntu shares in XP"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by Kim Siever on 2009-01-26
Hi everyone,

Longtime lurker, first time poster. Go easy on me.

I have been using Ubuntu for about a year now. I am using it to share music and photos (and eventually our printer).

Here's my problem:

1. I can see my Macbook and XP shares in Ubuntu.
2. I can see my Ubuntu and XP shares on my Macbook.
3. I cannot see Ubuntu or Macbook shares on my XP.

I have tried browsing to the shares using Windows Explorer, but they do not show up. I've tried typing the names of the shares into Window Explorer's address bar, but I get an error saying that "Windows cannot find [share name]". I type in the IP address of the shares, and I get the error "Windows cannot find [IP address]". When I click on "View workgroup computers", all I get is a system beep.

I can ping the IP addresses successfully in the commmand prompt. I have ensured that Client for Microsoft Networks, TCP/IP, and File and Print Sharing for Microsoft Networks are installed and checked. I even turned off the XP firewall. I am not using Norton, ZoneAlarm or any similar third-party firewall software. I use AVG for virus protection.

I will be in debt forever to anyone who helps me finally beat this problem, which has been haunting me for months. And my children will love you since they can finally download music to the MP3 players they got for Christmas.

Thanks in advance.

---

### Post by Iowan on 2009-01-26
Are the three machines in the same workgroup? Did you install Samba-server (usually just called Samba) to share FROM Ubuntu? Did you try smb://<IP-of-Windows-box>/<Windows-sharename> in the Location bar on Ubuntu?

---

### Post by Kim Siever on 2009-01-26
Yes, they are all in the same workgroup. Samba is installed.

I don't have a problem connect from Ubuntu to XP. It's the other way around that doesn't work. I can see Ubuntu from my Mac.

---

### Post by Iowan on 2009-01-26
Oops - I'm misreading things again... For some reason, I read all three lines as "I cannot see". So XP cannot (or will not) read from other machines...

---

### Post by cariboo on 2009-01-26
Have you tried setting up a new Network Place in Windows? What version of XP are you using, Home or Pro?

Jim

---

### Post by Kim Siever on 2009-01-27
> So XP cannot (or will not) read from other machines...

Correct.

> **cariboo907 said:**
> Have you tried setting up a new Network Place in Windows? What version of XP are you using, Home or Pro?

Yes, I have. When I try, it says, "Windows requires a share to publish to."

I am using XP Home.

---

### Post by syko21 on 2009-01-27
it might not like viewing them directly but try putting a line like this directly into the address bar of an explorer window (not internet explorer)
```
\\UBUNTU_MACHINE_NAME\SHARE_NAME
```

I don't know how to format that to include a username / pw if it is a locked share, but windows might prompt it from you automatically.

---

### Post by Kim Siever on 2009-01-27
> **syko21 said:**
> it might not like viewing them directly but try putting a line like this directly into the address bar of an explorer window (not internet explorer)

I have tried that, as per my first post, but I may not have made it clear. When I try that, I get a "Windows cannot find [share name]".

---

### Post by Another Monkey on 2009-01-27
Is your Windows firewall allowing file and printer sharing?  This is disabled by default in the standard MS firewall, third party ones will differ; check your documentation.

Have you made sure the firewall on Ubuntu is allowing through the SMB data from Windows?  [This link]("http://ubuntuforums.org/showthread.php?t=190542&highlight=samba+windows+unauthorized+access") explains what to do and why.

If that does not help, then you may have to go through the pain I had in order to get Windows to work (my networking was messed up).  A very helpful site is [here]("http://winhlp.com/wxnet.htm") (fill out the form).

Get a copy of the ["browstat" utility]("http://networking.nitecruzr.net/2005/05/browstat-utility-from-microsoft.html"), open a command prompt and try
```
browstat status
```

You should get something like
```
Browsing is active on domain.
   Master browser name is:....
```

If you see "Browsing is **NOT **active on domain" or "No master browser", then your "Computer browser" service on Windows is either not running or has some other problem.  You need to sort that (see link above).

Back at the command prompt, try this
```
net view
```

Did that list the Ubuntu PC?  A common problem is "error 6118", see my comment about "Computer Browser" above.  If it worked, then try this
```
net view \\ubuntu-pc-name
```

If that does not work, then Windows cannot browse the shares (although it knows the PC is there from the first command).  The error I had was "error 53" and it turned out to be the "iptables" configuration in Ubuntu blocking the SMB data, which is all explained in the first link.

I managed to get my networking and shares working last night, so this is all fresh in my mind.

---

### Post by Kim Siever on 2009-01-27
> **Another Monkey said:**
> Is your Windows firewall allowing file and printer sharing?  This is disabled by default in the standard MS firewall, third party ones will differ; check your documentation.

Yes. In fact, I even restored the firewall to default settings and rechecked the File and Printer Sharing checbox.

> **Another Monkey said:**
> Have you made sure the firewall on Ubuntu is allowing through the SMB data from Windows?  [This link]("http://ubuntuforums.org/showthread.php?t=190542&highlight=samba+windows+unauthorized+access") explains what to do and why.

Would that be different from the SMB data from Mac OS X?

> **Another Monkey said:**
> If that does not help, then you may have to go through the pain I had in order to get Windows to work (my networking was messed up).  A very helpful site is [here]("http://winhlp.com/wxnet.htm") (fill out the form).

I filled out all the applicable form fields, but nothing happened when I pressed "Shoe relevant chapters". Am I doing something wrong?

> **Another Monkey said:**
> Get a copy of the ["browstat" utility]("http://networking.nitecruzr.net/2005/05/browstat-utility-from-microsoft.html"), open a command prompt and try
```
browstat status
```

You should get something like
```
Browsing is active on domain.
   Master browser name is:....
```

If you see "Browsing is **NOT **active on domain" or "No master browser", then your "Computer browser" service on Windows is either not running or has some other problem.  You need to sort that (see link above).

I did get an error. Which link helps me with this? I tried both of the links above and did not see anything to get Computer Browser Service running.

> **Another Monkey said:**
> Back at the command prompt, try this
```
net view
```

Did that list the Ubuntu PC?  A common problem is "error 6118", see my comment about "Computer Browser" above.  If it worked, then try this
```
net view \\ubuntu-pc-name
```

If that does not work, then Windows cannot browse the shares (although it knows the PC is there from the first command).  The error I had was "error 53" and it turned out to be the "iptables" configuration in Ubuntu blocking the SMB data, which is all explained in the first link.

When I try to run this, it says the workstation service has not been started.

Thank you so much for taking the time to help me with this. I should mention that I am an intermediate computer user, and have no formal training in networking or hardware servicing.

---

### Post by Kim Siever on 2009-01-27
> **Another Monkey said:**
> Have you made sure the firewall on Ubuntu is allowing through the SMB data from Windows?  [This link]("http://ubuntuforums.org/showthread.php?t=190542&highlight=samba+windows+unauthorized+access") explains what to do and why.

Hmmmm. I don't see a firestarter directory in /etc/ and nothing when I search, so I'm not sure this link will help much.

---

### Post by Kim Siever on 2009-01-27
I sort of got it working.

If I type "NET START WORKSTATION" into the command prompt, I can view all computers on the workgroup.

When I restart the computer, however, I can no longer view the computers, and I have to enter "NET START WORKSTATION" into the command prompt.

Does anyone know how I can keep it running?

---

### Post by Noour on 2009-01-27
I think it s because of the difference NetBEUI versus TCP/IP sharing

One old link where they suggest Remove NetBEUI

From [http://oreilly.com/catalog/samba/chapter/book/ch03_01.html](http://oreilly.com/catalog/samba/chapter/book/ch03_01.html)

Second for more recent OS [there were some changes :D ]

[http://www.ezlan.net/netbeui.html](http://www.ezlan.net/netbeui.html)

NetBEUI is simple protocol that is based on local computers names (no IPs addresses like TCP/IP).

---

### Post by Kim Siever on 2009-01-28
I got it working using Computer Management, and made sure the Workstation service was set up to start automatically.

Thanks everyone for your help. You helped point me in the right direction.

---

### Post by Another Monkey on 2009-01-28
Hi Kim,

I was going to write a long reply and then noticed you last post.  Glad to see you got it working (Windows networking seems to be a black art at times!)

Might be best to mark this thread as "[SOLVED]" so people know (and other can find tips on what to do).

aM

---

### Post by Kim Siever on 2009-01-28
> **Another Monkey said:**
> Might be best to mark this thread as "[SOLVED]" so people know (and other can find tips on what to do).

How would I do that exactly? When I tried to edit original post, I didn't see an option to edit the subject.

---

### Post by Iowan on 2009-01-28
Until the forum started having some stability issues, there was a medal to give thanks to those posts you found useful, and under Thread Tools (near first post on page) was an option to "Mark Thread as Solved".  Both features are currently disabled - time will tell if they return.

---

