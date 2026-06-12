---
title: "File sharing mess/mystery"
date: 2011-06-09
forum: Networking &amp; Wireless
---

### Post by Chazzer on 2011-06-09
Natty 11.04

"Share files over the network" is what it says when I enter the Personal File Sharing Preferences.

followed by...

"This feature  cannot  be enabled  because the required packages are not installed on your system".

Surely the ability to connect to a local network is a prerequisite component of modern computing just as connecting to the Internet is, or isn't it? Why aren't the required packages installed and indeed what are the required packages? 

This seems to be a large thing to omit from this important release of Ubuntu.

---

### Post by capscrew on 2011-06-09
> **Chazzer said:**
> Natty 11.04

"Share files over the network" is what it says when I enter the Personal File Sharing Preferences.

followed by...

"This feature  cannot  be enabled  because the required packages are not installed on your system".

Surely the ability to connect to a local network is a prerequisite component of modern computing just as connecting to the Internet is, or isn't it? Why aren't the required packages installed and indeed what are the required packages? 

This seems to be a large thing to omit from this important release of Ubuntu.

See this thread: [**_[COLOR="DarkSlateGray"]http://ubuntuforums.org/showthread.php?t=1454194&highlight=sharing[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1454194&highlight=sharing")

---

### Post by Chazzer on 2011-06-10
I have made a little progress by installing the following items...

apache2
libapache2-mod-dnssd

Since having these items on board I can now connect to all my Apple Mac shares but sadly nothing from my Windows machine or another Ubuntu machine. Adding the files to my installation of Kubuntu made no difference at all. That distribution is very cranky indeed. Still, progress is progress.

---

### Post by capscrew on 2011-06-10
> **Chazzer said:**
> I have made a little progress by installing the following items...

apache2
libapache2-mod-dnssd

Since having these items on board I can now connect to all my Apple Mac shares but sadly nothing from my Windows machine or another Ubuntu machine. Adding the files to my installation of Kubuntu made no difference at all. That distribution is very cranky indeed. Still, progress is progress.

There are 2 ways to share files in you situation.  The Apple shares use webDAV, for which you installed with Apache2.  The other shares probably need to be shared using Samba. See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=10837039&postcount=6") for ideas on Samba sharing of Windows and Ubuntu data.

---

### Post by Chazzer on 2011-06-11
Cheers Capscrew. Thank you for this suggestion and for the links you've supplied me with, it's a great help. I have Ubuntu 10.10 running on another machine in my house and it performs far better than 11.04 judging from my experiences this week. Would you recommend sticking with this new release or down grading to the version I trust? I'm so frustrated I'm considering abandoning Natty as unfit for purpose.

---

### Post by capscrew on 2011-06-11
> **Chazzer said:**
> Cheers Capscrew. Thank you for this suggestion and for the links you've supplied me with, it's a great help. I have Ubuntu 10.10 running on another machine in my house and it performs far better than 11.04 judging from my experiences this week. Would you recommend sticking with this new release or down grading to the version I trust? I'm so frustrated I'm considering abandoning Natty as unfit for purpose.

At the present time all of my Desktops and Servers are Ubuntu 10.04.  My laptops are Windows XP and Vista.  I use 10.04 LTS because of the long term support.  I don't think of it being anymore stable though.  Natty is at the beginning of its life and it is expected to have teething problems.  

I have used a LiveCD to demonstrate that Samba performs the same whether it is 10.04 or 11.04.  I have used the same smb.conf file for the last 4 or 5 years.  I don't believe there has been a major change in Samba since version 3. 

The important thing to remember is to configure supporting network services before you even install and configure Samba.  I have no experience Apple OSX at all.  I'm almost sure there is an incarnation of Samba available using an Apple Mac.

I did have an interesting experience the other day that could have major implications if one didn't have extensive experience and understand how to correct it.  I installed  Ubuntu 10.04 Server on a test machine and used tasksel to install Samba (Ubuntu's pre-package of Samba).  This installed winbind.  Winbind should never be installed in a WORKGROUP situation.  I just un-installed it and went on.  But the ramifications are serious.  I would never recommend installing Samba via tasksel for WORKGROUP use.  I think it would be better to install what you specifically need via the apt system.

If you need specific help let me know.

---

### Post by masuch on 2011-09-18
> **Chazzer said:**
> I have made a little progress by installing the following items...

apache2
libapache2-mod-dnssd

Since having these items on board I can now connect to all my Apple Mac shares but sadly nothing from my Windows machine or another Ubuntu machine. Adding the files to my installation of Kubuntu made no difference at all. That distribution is very cranky indeed. Still, progress is progress.

Great, that was what I have been looking for. +1:D

---

### Post by PayPaul on 2011-09-23
> **capscrew said:**
> 

The important thing to remember is to configure supporting network services before you even install and configure Samba.  I have no experience Apple OSX at all.  I'm almost sure there is an incarnation of Samba available using an Apple Mac.

I did have an interesting experience the other day that could have major implications if one didn't have extensive experience and understand how to correct it.  I installed  Ubuntu 10.04 Server on a test machine and used tasksel to install Samba (Ubuntu's pre-package of Samba).  This installed winbind.  Winbind should never be installed in a WORKGROUP situation.  I just un-installed it and went on.  But the ramifications are serious.  I would never recommend installing Samba via tasksel for WORKGROUP use.  I think it would be better to install what you specifically need via the apt system.

If you need specific help let me know.


So how do I configure supporting network services? Are those part of the packages mentioned by the OP and which I have the same problem with. I believe my understand of Samba is that it's a GUI interface which allows better control of file and network sharing.

---

### Post by capscrew on 2011-09-23
> **PayPaul said:**
> So how do I configure supporting network services? Are those part of the packages mentioned by the OP and which I have the same problem with. I believe my understand of Samba is that it's a GUI interface which allows better control of file and network sharing.

The supporting network services I'm talking about is DNS name services.  This needs to be able to resolve the local network hosts to their IP addresses.  By default Ubuntu is not configured for Samba to work.

 How is your network currently setup for IP addressing and hosts resolution?

---

### Post by PayPaul on 2011-09-23
> **capscrew said:**
> The supporting network services I'm talking about is DNS name services.  This needs to be able to resolve the local network hosts to their IP addresses.  By default Ubuntu is not configured for Samba to work.

 How is your network currently setup for IP addressing and hosts resolution?


Where do I go for that? Is there a command line? A sudo?

---

### Post by capscrew on 2011-09-23
> **PayPaul said:**
> Where do I go for that? Is there a command line? A sudo?

More basic than that.  Are you using Network Manager to configure the interfaces (Ethernet or wireless)?  How did you get an IP address when you installed the system?

---

### Post by PayPaul on 2011-09-23
> **capscrew said:**
> More basic than that.  Are you using Network Manager to configure the interfaces (Ethernet or wireless)?  How did you get an IP address when you installed the system?

I am using Network Manager but I can't figure out here how to get an IP address or to allow the DNS services to be enabled. When I checked the box that required Ipv6 I lost my internet connection.

---

### Post by capscrew on 2011-09-23
> **PayPaul said:**
> I am using Network Manager but I can't figure out here how to get an IP address or to allow the DNS services to be enabled. When I checked the box that required Ipv6 I lost my internet connection.

At this point it appears you need to start your own thread.  This thread is about sharing and you really need to deal with IP networking and DNS before you can share anything.

Make the subject something like: IP addressing and DNS help

I'll look for the thread.

---

### Post by PayPaul on 2011-09-23
Thanks for the tip. I'll put in those search terms first and see what comes up. There seems always to be preliminary steps to take. No major newsflash.

---

