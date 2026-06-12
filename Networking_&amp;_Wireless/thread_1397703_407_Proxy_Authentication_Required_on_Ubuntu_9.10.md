---
title: "407 Proxy Authentication Required on Ubuntu 9.10"
date: 2010-02-03
forum: Networking &amp; Wireless
---

### Post by James2k on 2010-02-03
Hey Ubuntu Community.

At my college my class have setup a small network between three computers. Two machines are running Windows and the other of course is running Ubuntu. The network has been configured with two sub nets. 192.168.1.x and 192.168.2.x. The network configuration isn't the problem here it's more of something has happened since I made a certain change on the Ubuntu Machine.

Basically were using the Ubuntu machine as a web server and creating a localhost for the other Windows machines to see and access. We basically have these machines setup to test various scripts and what not locally. This has all been successful, like I said the network setup isn't the problem here so I'll get to the point. 

In order to get the Ubuntu machine working correctly we've needed access to the internet to download updates, packages etc but this is OK as we've setup the router 192.168.1.x router to go to the college ethernet port and obtain a IP on the college network, this works and for a while we was able to use commands like sudo apt-get install etc, which we orginally used to get the packages Apache2, PHP 5 etc. Because were using the college network it asks for the college proxy that is set up. This is also fine as we know the details and have set them in Network Proxy and Synaptic to the system.

Everything was working great until I found that the root password for the Ubuntu machine had somehow got lost. The original group that setup the Ubuntu machine said try this and this etc etc but none of the passwords worked and I couldn't change certain things, so I decided to reset the root password using **sudo passwd** and reset the root password, but after doing this I seemed to have screwed up the network settings because now when I try to use Ubuntu software centre or sudo apt-get update or install in terminal I get the error "407 Proxy Authenication Required" and when using Ubuntu Software Centre I either get "Can not authenicate package" or the same 407 error.

I've looked around Google and found some posts related to the issue the Ubuntu machine is having, but none have solved our problem. Like I said everything was working fine until I reset the root password because no one knew it anymore and now the problem occurs described above. The internet and synaptic work fine but when you use Ubuntu software centre or a terminal to download a program or application I get the errors described above.

Can someone help me and tell me what I've stuffed up!
[COLOR=Red]
**Edit:** Just want to add Update Manager works fine too.[/COLOR] 

**Note: Im curretly not at College and won't be till monday so I can't post information on the configuration of specific files unless I know them on hand. I will be able to give the information to you on Monday though**

---

### Post by James2k on 2010-02-08
Bumping.

---

### Post by Sayed Ali on 2010-04-27
I have nearly the same problem, except since I have updated my OS to 9.10 this problem appeared.
someone please guide us what should we do?:confused::-({|=:roll:

---

### Post by pavithran on 2010-06-23
I have exactly the SAME problem !!!

---

### Post by varshacp on 2012-03-05
Hi 

I also have same proble even CLI sudo apt -get udate does not work

---

