---
title: "Internet Problems"
date: 2010-01-12
forum: Networking &amp; Wireless
---

### Post by volatilepyro on 2010-01-12
I'm running Karmic alongside 7 and vista. I don't do anything with vista but I use 7 and ubuntu. My laptop is an Acer Aspire 5532. Every time I get more than one program running at once the Internet will crash. Can anyone toss me some ideas??? Also my connection will never go more than like two to three bars of connection and that's if I'm lucky.

---

### Post by quixote on 2010-01-13
Do you get a stronger connection in win7, or is it always just a couple of bars?  Did this problem start after you upgraded to Karmic, or did you have it with Jaunty as well?  Also, what are the specs on that laptop, ie how much system memory?  Is it Broadcom wireless or something else?

It sounds like an odd problem, but maybe with a bit more data we can see if there's an answer.

---

### Post by volatilepyro on 2010-01-14
It's got built in wireless and yeah it works great on the 7 side. It has a 64 bit processor, 3 gig memory, and 160 gig hdd. I never used jaunty. I'm pretty much as green as they come to ubuntu.

---

### Post by quixote on 2010-01-14
With that amount of memory, and the fact that it's fine on Win7, it's not a lack of memory.  That it works at all in karmic means the wireless is basically set up correctly, but sounds like it somehow doesn't have enough memory. :confused:

I'm not aware of any system or wireless settings that could increase some kind of buffer or allocated memory -- if that's even the problem -- so what we need is someone with more knowledge to jump in!  As I said, it's a bit of an odd problem.  I run 64-bit karmic myself (Intel wireless, weird Motorola cablemodem/router).  

Is there a way you can edit the title to add "wireless drops connection"? 

Also, any data you can add about your wireless setup might help.  Broadcom, Intel, other wireless in the computer?  Type of router?

---

### Post by volatilepyro on 2010-01-14
Alright well I also have vista here but I never use it. I almost started it up but I decided against it so I shut it back down. That much windows might be the memory problem but I don't know how to get rid of it just short of wiping the hard drive. At my house I use an at&t modem but at school I use theirs and at my father's house he uses a linksys but it happens the same everywhere. Overall I want vista gone no matter what and I'd rather not have to wipe my hard drive but I do have 7 on disc and ubuntu on a flashdrive so I suppose I could but you know.

---

### Post by quixote on 2010-01-14
The fact that ubuntu is on a flash drive is probably the issue.  Access times are much slower than on an HD.  The Win7, I gather is on an external HD, so that may explain why it doesn't have this problem.  An external HD is usually slower than internal because of the USB connection bottleneck, but still a good bit faster than flash.  So I imagine what happens when you open more than one program in ubuntu is the poor little flash drive is juggling as fast as it can but can't keep up.

I'm sure there's some way to tell a connection to wait longer for the required handshakes, but I don't know what it is.  The keywords to search for might be any or all of "Invilink latency buffer maintain connection". (Without quotes.)  Something like that. 

On a side note: you don't have to wipe the hard drive to install ubuntu.  Assuming you have space on it, you could make two partitions in the free space.  One 5-10GB for the / (=root, =system) partition, and one as large as the disk will allow for /home.  Install ubuntu into your new root partion, and you'll have a multiboot system.  It can be set to boot into ubuntu by default.  You can mount the "My Documents" folder, or the whole partition, as a data partition under ubuntu and have access to the files you created under Windows.  Vista will still be occupying space, but other than that unless you boot into it, it's not using system memory or doing anything.  If you think you might want to do this, I'll dig up the link to the best instructions I've found, which are buried somewhere in my hundreds of bookmarks.

---

### Post by lrcaballero on 2010-01-14
Look into this thread: [COLOR=blue]Wireless problems - ath9k on Ubuntu 9.10[/COLOR], see if this helps you.
 
Luis

---

### Post by volatilepyro on 2010-01-15
No I mean I have it available to install, I don't run it from the drive. All the operating systems are on my hard drive.

---

### Post by quixote on 2010-01-15
Ircaballero: I don't find anything searching the forums either with the whole phrase in blue or even just "ath9k" "Ubuntu 9.10".  Could you provide a link?

---

### Post by quixote on 2010-01-16
[Another report]("http://ubuntuforums.org/showthread.php?p=8672748") has come up about dropped wireless connections in an Acer after the Karmic upgrade.  I wonder if it might be a similar problem?  Some bug in the upgrade that affects Acers?  :(

---

### Post by volatilepyro on 2010-01-18
All right it seems that I've fixed this problem. I just installed the packages linux-backport-modules-wireless-karmic and the -generic version as well and now I have like full signal and I actually had two tabs up at once with no signal drop.

---

### Post by quixote on 2010-01-18
Glad to hear you have a solution, and thanks for sharing it!

---

### Post by volatilepyro on 2010-01-19
All right well that's fixed but now I can't connect to anything short of the start page of firefox on my school's server. I think it has something to do with their firewall because on 7 I can't download any add ons for firefox. Are there any packages or anything I could install to bypass this and allow me to actually use ubuntu at school???

---

### Post by quixote on 2010-01-20
There are ways around firewalls using tunneling and ssh or ??  It's not something I know anything about, and it's a different topic than the rest of this thread.  I'd suggest starting a new one with that question.

---

