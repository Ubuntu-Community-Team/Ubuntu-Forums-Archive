---
title: "Ubuntu workgroup blues"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by hipnerd on 2009-02-24
The players:

My PC: Ubuntu Intrepid Ibex 32-bit
My wife's PC: Windows XP Pro
The odd piece of hardware: Buffalo Link Station NAS/Media Server/Print Server

The goal:

Allow my machine to join a Windows workgroup, access printers an files on both my wife's PC and the Link Station NAS, and share files with my wife.

* * *

I am writing here today as a candid admission of my absolute ignorance. Even after almost three years of using Ubuntu exclusively as my desktop OS of choice and expounding upon its many virtues to complete strangers to the point of annoyance, I am still unable to conquer the most basic of networking tasks.

I have an Ubuntu machine, which as you know, is perfection unto itself. My wife has a box running Windows XP Pro. I want them to interface -- a situation not unlike asking a Mormon missionary to procure a Tijuana hooker with open sores on her lips for a night of tawdry sex and general debauchery.

Luckily for me, Ubuntu's vaunted security features have leapt into action to keep my computer safe. It accomplishes this feat primarily by not allowing me to do anything even remotely relating to sharing files, printers or other information with the XP box. 

Complete non-functionality has proven to be very secure. If I can't connect to her machine, my wife cannot log into my PC and catalog the copious amounts of illegally procured clown-based pornography that I have accumulated over the years. Heck, I don't even need a fancy firewall.

But still, I would like to get this to work. It is a trivial task in Window, and it galls me that I am having this much difficulty with it. To add insult to injury, I recently bought a Buffalo Link Station NAS that also acts as a media server and print server. It runs a version of Linux.

Windows XP Pro can easily find the share offered by the NAS, access files, and print away to the laser printer in this configuration, while my Linux box cannot.

In this scenario, rather than a Tijuana hooker, the Link Station is the popular cheerleader from my high-school who swore she really wanted to go to prom with me, but that she had promised to go with her paraplegic brother instead. Then I saw her making out with the lacrosse captain in front of the punch bowl while I stood awkwardly against the wall fidgeting with a cheap corsage that my mother picked up for me at the gas station. 

Perhaps I've taken the metaphor too far.

In my quest to establish a workable solution to this problem I have uncovered dozens of tutorials -- all purporting to easily establish networking in a Windows workgroup environment via Samba. As far as I can tell, these documents are part of a vast global conspiracy to make me doubt my intelligence and perhaps my sanity, as solution after solution has failed to work.

At this point I am willing to complete scrap my tortured to the point of uselessness samba.conf file and start from scratch. Can anyone point me to a guide that is: 

1) made for my version of Ubuntu and 

2) made for my version of Samba that 

3) actually works?

---

### Post by jonandrews on 2009-02-25
I think you will find what you need on my Ubuntu / XP networking website

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

As well as the networking tutorials, do have a glance at the guide titled 'About Windows Workgroups'

---

### Post by tlois on 2009-02-25
What have you tried?  I was just having some issues with sharing a printer these past two days only to find that Multicast DNS discovery was not clicked in my services settings.  When I wanted to set file sharing, I right clicked and set it to sharing.  On the computer that didn't have it installed yet, when I right clicked to shared it asked me to intall some programs and that was a wrap.  

I think the thing to do is to get your wife to give up Windows!  I got my husband to about a month or two ago- he loves it.  We were able to share files when he had windows- and a printer- I think I did it the same way as described above.  You are using 8.10, right?  I certainly don't remember sharing between Windows and U 8.10 to be too difficult.  

Also, is the printer set to be shared?

---

### Post by Yashiro on 2009-02-25
Try accessing these shares using a Live CD version of Ubuntu or Debian.

Altering smb.conf wont neccesarily change your access to their shares, only their access to yours.
It can also break things if yours is setup as the wins server and such like.

Try the CD approach first. You should be able to see their shares unless something is very broken.

---

### Post by hipnerd on 2009-03-01
> **jonandrews said:**
> I think you will find what you need on my Ubuntu / XP networking website

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

As well as the networking tutorials, do have a glance at the guide titled 'About Windows Workgroups'

OK. Just for the heck of it I reinstalled Ubuntu 8.10 to start with a clean slate, to start with a fresh slate. I did not reformat my /home partition, so there is a possibility that I carried something bad with me from there.

After following the directions in the guide, I joined the same workgroup as my wife's PC. (I renamed my workgroup in smb.conf to match.)

Now when I try to browse for shares, I can see a single, unified workgroup, but I get:

> 
Unable to Mount Location 
Failed to retrieve share list from server.

findsmb gives me this result

>                                 *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.0.75    JOHN-DESKTOP   [BIZNERDS] [Unix] [Samba 3.2.3]
192.168.0.76    PATTI-DESKTOP  [PATTI-DESKTOP] [Windows 5.1] [Windows 2000 LAN Manager]
192.168.0.101   MEDIA-01      +[MEDIA-01] [Unix] [Samba 3.0.21c]


I'm john, my wife is patti and the Buffalo Linkstation is "media-01". I noticed that only my PC actually has the workgroup (Biznerds) listed.

At this point, I'm wondering if something I did while trying to get this working earlier is now working against me. WINS perhaps?

---

### Post by hipnerd on 2009-03-01
After playing around some more, I made these discoveries:

1. My netbook, which is also running Ubuntu, has the exact same problems.

2. In the printer menu, you can browse the shares and find the printer, but it still doesn't work right.

3. If I use the IP address instead of the server name and/or workgroup, it seems to work.

Any ideas why I can't browse shares using names though?

---

