---
title: "Firefox won't play Flash Videos"
date: 2009-01-16
forum: Multimedia Software
---

### Post by druntar on 2009-01-16
I've been looking through the forums and tried a few solutions to this, but can't seem to figure it out. Flash videos played fine up until a few days ago. Now they will play the first 10-20 seconds and then it just stops. As far as I know I only have the Adobe flash plugin installed. Flash games work fine. I've tried reinstalling the plugin and firefox. I'm using 8.10 and Firefox 3. Any help would be greatly appreciated.

---

### Post by gandaran on 2009-01-16
ubuntu; 32-bits or 64-bits?
post the output of **locate libflash**, type in terminal/console

---

### Post by druntar on 2009-01-16
To be honest I don't remember. I have a copy of each, and I've had to reinstall several times because of my incessant tinkering. To make matters worse I'm not sure how to check :( 

As for the command you asked me to enter here goes:

druntar@druntarsdeathbot:~$ locate libflash
/usr/lib/flashplugin-nonfree/libflashplayer.so
/usr/lib/openoffice/basis3.0/program/libflashli.so

---

### Post by gandaran on 2009-01-16
> **druntar said:**
> To be honest I don't remember. I have a copy of each, and I've had to reinstall several times because of my incessant tinkering. To make matters worse I'm not sure how to check :( 

As for the command you asked me to enter here goes:

druntar@druntarsdeathbot:~$ locate libflash
/usr/lib/flashplugin-nonfree/libflashplayer.so
/usr/lib/openoffice/basis3.0/program/libflashli.so
check with this command **uname -a**

---

### Post by druntar on 2009-01-16
Here's what I got from that command. 

druntar@druntarsdeathbot:~$ uname -a
Linux druntarsdeathbot 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

---

### Post by gandaran on 2009-01-16
> **druntar said:**
> Here's what I got from that command. 

druntar@druntarsdeathbot:~$ uname -a
Linux druntarsdeathbot 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux
it's 32-bit and everything looks okay, should work fine with the flashplugin-nonfree, you don't have any other flash installed like gnash or swfdec? 
maybe it's a problem with your video card drivers? try right clicking the flash video window » configurations » disable hardware acceleration or disable compiz if you are running it.

---

### Post by druntar on 2009-01-16
Problem solved. I jumped into IRC, and we were able to determine that for some reason my computer was thinking that my /tmp was too full. I had restarted several times since the problem began, but for some reason after I rebooted again the problem went away. Thanks for the help guys. Just wish I knew what happened. It's really confusing.

---

### Post by kyle0485 on 2009-01-16
I am having the same problem, is there a way to manually empty the /tmp folder?

---

### Post by kyle0485 on 2009-01-16
Problem solved, I did the same as the original poster and just rebooted a lot of times.  Now it seems to work fine.  Would be interested to know why it did that though so I could avoid it happening again.

---

### Post by rhardie on 2009-01-31
I've been having this problem for weeks now.  I have work to do and I don't have time to screw around with this ****.  I'm just about ready to buy a Mac or go back to my PC.

I spend more time fixing my Linux problems than I ever did with any problems I had with Windows.

I've been using Ubuntu for about 2 years now and I can say I'm "just about" fed up with the constant breaking down of the system.

This is absolutely ridiculous to be having these kinds of problems.

---

### Post by MishMich on 2009-02-11
I know what you mean, rhardie.  For ten years now, every couple of years, I do a linux install to see how things are going, and I run it for a couple of weeks, and get sick of it and put it away.  I like ubuntu best, and set up a server and laptop to make use of a couple of old windoze 98 PC's a couple of years ago.  The laptop made a good little music station for playing MP3's at a party two years ago, but fiddling around with the server to get a decent LAMP stack was a pain, when I could put a WAMP stack together without pulling all this downloads in and making the system unstable.  So, I put it away again.  Then my uncle chucked out an old HP 98 PC before Xmas, and off I go again...

I figured I'd set it up so I could browse google groups and facebook without compromising the PC's I use to work on (XP & Vista).  I have to say that the GUI on Vista & MS.Office (& functionality on Office - I need something that I can use EndNote in and hold a 100,000 word thesis in a single document for editing) is light years ahead of anything else.  So, I get a flash button on some facebook games using firefox, and when I click it I am told to download the latest flash, which I do, and unpack it, and nothing changes.  Can I be bothered finding out why something that just works in widoze just won't on linux?  No, life is too short.

So, two new ethernet cards are on their way, and they will go in the linux box and it will become a gateway/firewall that will sit between the internet and my network, and I can use that to close down anything on the network I don't like the look of.  I think Linux will be able to handle that if I don't try and make it do anything else too clever.  I used to be a UNIX systems admin, and I never had the sorts of problems there are with Linux.  OK, you might need to write the driver, but not all of us want to hack the kernel.  Things should just work, and if something doesn't it shouldn't take hours of trawling forums to figure out what is wrong.  Until the point it just works for the relatively unsophisticated user, Linux will not be anything better than geek entertainment.  I pity those souls who forked out for Netbooks running Linux...

Mish

---

### Post by Blackjesus on 2009-05-19
So what what did rebooting fix ?

is there a manual why of doing this ?

---

### Post by Blackjesus on 2009-05-19
> **rhardie said:**
> I've been having this problem for weeks now.  I have work to do and I don't have time to screw around with this ****.  I'm just about ready to buy a Mac or go back to my PC.

I spend more time fixing my Linux problems than I ever did with any problems I had with Windows.

I've been using Ubuntu for about 2 years now and I can say I'm "just about" fed up with the constant breaking down of the system.

This is absolutely ridiculous to be having these kinds of problems.


Yeah man i 2nd that its just 2 much work :/
ive also used Virtual Box , the problems i had with that grrr 
I thinks its time 2 go back 2 Windows
When windows 7 comes out :smile:

---

