---
title: "[SOLVED] home network vista to Ubuntu"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by Darrylb on 2009-01-09
First off I am brand NEW to Linux, so i dont have a good knowledge of some of the lingo use in these forums, 

I have installed Ubuntu 8.10 (I removed win xp from the system) on my home desktop computer, and i Love it, My problem is the destop computer has 6 hardrives i use for storage, 
I have two laptops (1 dell, and 1 toshiba) 
Ihad set up a home network with  the 3 machines so i could access the harddrives on the desktop, it worked fine when the desktop was a win xp machine,  

How do i set it up now that it is a Ubuntu Machine so my vista laptops can find it......or is it even possible???? I am totally confused.........but i love it

---

### Post by cabbiinc on 2009-01-10
> **Darrylb said:**
> First off I am brand NEW to Linux, so i dont have a good knowledge of some of the lingo use in these forums, 

I have installed Ubuntu 8.10 (I removed win xp from the system) on my home desktop computer, and i Love it, My problem is the destop computer has 6 hardrives i use for storage, 
I have two laptops (1 dell, and 1 toshiba) 
Ihad set up a home network with  the 3 machines so i could access the harddrives on the desktop, it worked fine when the desktop was a win xp machine,  

How do i set it up now that it is a Ubuntu Machine so my vista laptops can find it......or is it even possible???? I am totally confused.........but i love it

I am told it's possible. I can't seem to get it connected either. But what you can do is try to ping the Ubuntu machine from your Vista machine. In Vista click start>  All Programs> Accessories> Command Prompt. Type ping ###.###.###.# replacing # with your other computers IP address. If you get a ping back there's hope.

Now type "Net use \\###.###.###.# /persistent:yes"
And you should now be able to put the \\###... in a regular window and see the shared files come up. It won't stay there and you'll have to put in the IP address every time, but it's a start, and that's where I've been for a few weeks.

---

### Post by Darrylb on 2009-01-10
> **cabbiinc said:**
> I am told it's possible. I can't seem to get it connected either. But what you can do is try to ping the Ubuntu machine from your Vista machine. In Vista click start>  All Programs> Accessories> Command Prompt. Type ping ###.###.###.# replacing # with your other computers IP address. If you get a ping back there's hope.

Now type "Net use \\###.###.###.# /persistent:yes"
And you should now be able to put the \\###... in a regular window and see the shared files come up. It won't stay there and you'll have to put in the IP address every time, but it's a start, and that's where I've been for a few weeks.

 I was able to Ping the machine running Ubuntu from both laptops, but this string didnt work "Net use \\###.###.###.# /persistent:yes" I dont know much about if anything about Linux YET< I have always ran windows OS in the past because thats what i got when i bought a new machine (started with windows 3.1)  and have been buy books teaching myself as i go,

But i few months back a let my win xp upgrade to service pack 3 and the crap hit the fan, (I run Amd Processors) after the upgrade i was hung in a endless reboot cycle, which ended up blowing my mother board,so i had to rebuild the destop,. The laptops I have both came with Vista home preimun, I hate Vista everything about it,  I was ready to to switch to a MAC when my cousin told me i should give Linux a try  so over the past few weeks i have been downloading different distros and trying them out, some worked some didnt, because i have IDE and Sata drive both in the box,
the 3 that worked the best were Ubuntu, OpenSuse, Mandriva I picked Ubuntu because it seemed easier for me to use and because Book Stores like books a million have more books on using Ubuntu than all the other combined, 
But before i go out and start buying books i may try the Ubuntu server edition out on a spare drive i have laying around and see if that helps with the problems in networking.........That may be over the top.........but it will be a new learning curve LOL

---

### Post by jonandrews on 2009-01-10
Have a look at my step-by-step guides to networking between Windows & Ubuntu.  The guides assume the use of XP, but the configuration of Ubuntu is exactly the same & allows access from Vista PC's.. (and Mac's, and Solaris..)

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

---

### Post by Darrylb on 2009-01-10
> **jonandrews said:**
> Have a look at my step-by-step guides to networking between Windows & Ubuntu.  The guides assume the use of XP, but the configuration of Ubuntu is exactly the same & allows access from Vista PC's.. (and Mac's, and Solaris..)

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

:popcorn:

WOW, that was easy, the only thing i had to do after i followed your instructions, was to install samba and create shares for the drives 

 I did do a re-install of Ubuntu after i read your instructions, only because i had added every peice of software i could find related to networking, servers and so on, (I should have wrote down what i installed so i could remove them but i didnt, so the re-install was easier,  

Thanks a Million:guitar:

---

### Post by cabbiinc on 2009-01-10
You'll want to mark this thread as solved.

---

