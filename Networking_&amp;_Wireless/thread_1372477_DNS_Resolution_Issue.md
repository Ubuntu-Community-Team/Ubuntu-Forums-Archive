---
title: "DNS Resolution Issue"
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by Neytiri on 2010-01-04
Hi Guys,

Sorry to interject on this thread, but I do feel it appropriate to my situation and wonder if there is a wider issue with this version of Ubuntu??  Yesterday I made my first transition to open source OS Ubuntu v9.10 and all went well with the installation and dual boot with XP. I'm obviously green around the ears with Ubuntu having been a XP windows user, however I too am having great difficulty in connecting to the internet (ethernet- desktop) similar to that of 'Xirb' frustrations. In all other respects of the Ubuntu Operating System things seem well!

In my case I am able to ping both from the router to Ubuntu and visa versa, also able to ping from Ubuntu to other external IP's with 100% success, however I just cannot get the installed Firefox to connect to any websites?

Just a couple of perculiarities that has happened. momentarily I was able to connect to Google.co.uk at the beginning (after installation) and then shortly after I got 'problem loading page', and even stranger I was able to do a search through google on any subject and get listed headings etc, but again could not link to any of the webpages from those headings. After a short while the Google search facility just stopped functioning.

The XP side of this computer is able to connect to the internet, as well as two of the family computers through the router (192.168.1.1.) so I dont see the router as the issue........I am beginning to think that may be Firefox has something to do with this?

Perhaps someone could advise what the firefox settings should be and whether any changes in about:config need to take place!

My apologies if I incorrectly posted here or whether I should have created another thread?

Not the kind of introduction to Ubuntu I was expecting :sad: , but hey appreciate the fact of all the skill and work that has been done freely to produce such operating systems and the support you peeps give.

Many thanks
N

---

### Post by SecretCode on 2010-01-04
Neytiri, can you also do the ping and nslookup tests I wrote a few posts up? Plus the output of _ifconfig_.

---

### Post by Neytiri on 2010-01-04
Thanks for response SecretCode....................I have taken a desktop screen shot of ifconfig -a, route -n, nslookup? ping from network tool, and firefox browser to reflect status. 

[Screenshot ubuntu__.jpg]("http://ubuntuforums.org/attachment.php?attachmentid=142421&stc=1&d=1262624891")

As you may see I am able to ping network addresses from Ubuntu. The strange thing again on opening Firefox this time, my home page Google appeared, but it was short lived as I could not go any further.........sniffle!! Ended up with 'problem loading page'.

All other current PC's are hard wired connected to the router and working fine on the internet. Done the usual reboots including router etc but still Ubuntu refuses to play ball. Ubuntu can still connect to the router and visa versa.

Let me know if you need anything else....If you can shed any light I would be very grateful.

Best
N

---

### Post by Neytiri on 2010-01-04
Well this is interesting.............

I can ping 100% [www.google.com]("http://www.google.com") from Network tools, but I cannot ping [www.cisco.com]("http://www.cisco.com").
I can access both websites via firefox when I enter the actual IP numbers. However it will not work when I type [http://www.cisco.com](http://www.cisco.com) or google or any other named website. Once connected via IP numbers you have mentioned I can connect to some of the site links albeit a little slow, but as I have not updated flash etc as yet, some of those pages have not always responded. 

A little bit of progress me thinks.

Appreciate your responses SecretCode.

N

PS> sorry Xirb :lolflag:

---

### Post by ugm6hr on 2010-01-04
Separated from hijacked original thread: [http://ubuntuforums.org/showthread.php?p=8609630#post8609630](http://ubuntuforums.org/showthread.php?p=8609630#post8609630)

---

### Post by doas777 on 2010-01-04
I'm inclinded to blame your router, since it appears to be proxying DNS queries. how long has it been since you powercycled it?

a couple things to try, would be to specify another DNS server address in your router, or in your client. I often use 4.2.2.1

---

### Post by pricetech on 2010-01-04
A copule more DNS addresses:

208.67.222.222  and  208.67.220.220

That's Open DNS

---

### Post by shairozan on 2010-01-04
I second Doas' statement, looks like the DHCP settings on the router have it using...itself for DNS resolution. If you login and change the settings to use the Open DNS Servers (those recommended by pricetech in the previous post) then it should solve the problem going forward.

---

### Post by SecretCode on 2010-01-05
Can you, from the ubuntu command line, successfully
```
wget www.cisco.com
wget www.google.com
```
Each should result in *'index.html' saved* or something similar.

---

### Post by Neytiri on 2010-01-06
Hi, 
   
  Well peeps I am up and running with internet connection and wish thank SecretCode and others for providing assistance to me. Sadly though my first experience with Ubuntu installation got off to a rocky start with internet issues, but then this was coupled with another experience of being treated like a kid by Ubuntu Forum Staff for inadvertently hijacking a thread and then given a ‘warning’……well guys, even though I am not disputing my unintentional wrongfulness I don’t need this hassle or even like being treated like a pet animal! …..so I deal with it by walking away.
   
  Anyway for your info I like the Ubuntu system and will use and evolve with open software. Thanks again to Secretcode and others.
   
  Permanently signing off this forum…..
   
  N

---

