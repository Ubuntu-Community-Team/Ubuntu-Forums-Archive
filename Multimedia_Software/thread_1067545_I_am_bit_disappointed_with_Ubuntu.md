---
title: "I am bit disappointed with Ubuntu"
date: 2009-02-12
forum: Multimedia Software
---

### Post by UNME on 2009-02-12
Hi All,

I am having two machines one with OpenSuse and other with Ubuntu.

I wanted to have the restricted formats support for totem in ubuntu.

First hurdle was so many dependencies to be downloaded (this machine is not connected to internet so get all files from other machines with me).


But in OpenSuse 11.2  I got one package and thats all (here I installed VLC player).
Though it is using RPM but I was amazed with ease with which things were done.

Okay folks my ubuntu machine is still not able to play MP3, wmv and other restricted formats.

How to get all dependencies and packages required to get it worked.

Thank you :popcorn:

---

### Post by wolfen69 on 2009-02-12
you probably want [Medibuntu packages]("http://packages.medibuntu.org/"). you can download the .debs and click to install them.

---

### Post by UNME on 2009-02-12
wolfen69 first awesome signature and thanks,

I am looking for package for Intrepid totem player.
I can switch to other players also but I need package for restricted format and also codecs.

Can you suggest one of the packages there.

I guess mplayer and real are available but do we need restricted format packs for them.

Thanks :KS

---

### Post by Open-SuSe-A-Me on 2009-02-12
just install all of the gstreamer packages, but it may be a pain in the buttocks if you dont have internet

---

### Post by wolfen69 on 2009-02-12
can you bring your computer somewhere  there is internet? you could then set it up and be done. otherwise i think it is going to be difficult.

---

### Post by naseemahmadkhan on 2009-02-12
first of all i am sorry to be out of context but being first time user of ubuntu forum i am not able to give a new post. 

My problem is i recently installed ubuntu 6.06 on my dell inspiron 1525. when i look in lspci |grep -i ethernet it shows driver installed but when i run /etc/init.d/networking command it says 
SIOCSIFADDR: No such device eth0
eth0: ERROR while getting interface flags: No such device

my movtive is run internet. 

i am running ubuntu in dual mode with windows vista. it is working good in vista.


Please help so that i can continue using obuntu.

---

### Post by mcduck on 2009-02-12
> **UNME said:**
> 
But in OpenSuse 11.2  I got one package and thats all (here I installed VLC player).

There's your explanation, and also your solution (if you are no willing/able to connect that computer to the net.)

VLC includes it's own codecs for everything, which means it doesn't depend on other packages to provide them like Totem does. Install VLC in Ubuntu as well. ;)

---

### Post by servlet on 2009-02-12
I am having the same problem. some one please look at the thread and help me before I get frustrated.

[http://ubuntuforums.org/showthread.php?t=1067584](http://ubuntuforums.org/showthread.php?t=1067584)

---

### Post by UNME on 2009-02-13
Thanks to all of you,

[@mcduck]I went to vlc website, that too directed me to dapper.
In dapper the missing point is you have to install endless dependency. sometimes few packages req older files.

Ex. A.2.3 will req B.4.3 but in Ubuntu we will have B.4.4 and we will get problems.

[@ALL Ubuntu communtiy]

I am talking like an end user: Why shall someone waste time in Installing and finding depedency. Why can't we have files wrapped in one shell that can be opened by synaptic to spill files to correct location.

I saw somewhere written "that is window way and Ubuntu use advance setup thru internet or live CD" but say I got a CD burned from ISO file and installed the OS in a system with no Internet ... window way will work here.

I tell you what customer said "Sir, I will shell $500 for OS + $300 for aplication if It is one time investment and will get stable features. I thought on this, and questioned myself "Is Ubuntu thinking this way".

NO USER is used to any OS (so those who say people look linux windows way, are wrong). Example: If today Google comes up with OS I am sure it will be competing with Microsoft upfront (chrome, gmail, orkut are examples).

Point is to simplify things and follow what people want.

One thing is people will accept Ubuntu if it can have a all dependecies wrapped together.

I love linux and also ubuntu but think practically windows way seems simple even today.:popcorn:

Note: this is my view, and I love to make grammatical mistakes, thank you.

---

### Post by mc4man on 2009-02-13
Your comparing apples to oranges.

With linux you have available tens of thousands of applications, 99.99% of which are provided for your use for free. 
All that's required on your end for 'easy' installation is to have an internet connection and occasionally apply some of your own effort. (beyond what's provided by default

Anything that's not provided by default in windows you'll have to buy or steal ( unless it's freeware which requires a connection

Even when you don't have an internet connection free apps are available that will take care of acquiring what you need.

In the absence of looking for and using these 'helper' apps you could simply use the live cd you installed with on the  machine without a connection. Simply boot up to that live cd on any  pc with a connection and install what you want. 

All the required packages will be in  /var/cache/apt/archives, all you need to do is copy the archives folder, transfer to the other machine's desktop and run one simple command to install everything in there.

---

### Post by UNME on 2009-02-13
Not comparing linux to windows, comparing linux to linux.
Also trying to find good points in other OS (say windows) and asking our dev teams here to incorporate it in our own system (linux).

Few things we need in Ubuntu:

1) A IDE like visual studio (I know it cost but a worth buy) (also I think carbon for c in MAC), certainly good debugger is required. 

2) A time has come when we should have all distros comply some common standards. yes we comply to posix and have framework like cups but still we need to come with our DDK (am I missing something is DDK still there)

Also, we need to understand people are ready to shell $300 (people means majority and not all of us) and buy crap because that crap is simple.

We have genuine applications we need to make them simple and refined and then give them to people accross the world.

To get the Best hybrid, start comparing apple to orange :KS

---

