---
title: "Flash not playing on ANY browser"
date: 2009-01-31
forum: Multimedia Software
---

### Post by rhardie on 2009-01-31
I've been through all of the threads and posts and not found any real solution YET.  Many others have experienced the issue as well.

Firefox or Epiphany do not show videos on YouTube or other web sites.  The Flash loads for 2 seconds and hangs up.

We are continuously jumping through our "O" ring with the same negative results and I'd like to kill this issue and bury it -- need someone's assistance.

Given that these are two different browsers, I would expect the common denominator most likely would be:

a) Adobe Flash 10
b) Ubuntu
c) Adobe and Ubuntu don't play well together

I have removed, system restart and reinstalled:

Firefox 3.0.5 twice
Adobe Flash 10 twice
The various plug ins that are called for

SYSTEM:

AMD Phenom 9500 (64 Bit)
3 GB RAM
Ubuntu 8.10 32 bit
Video Nvidia 8400 GS
Firefox 3.0.5 (no flash blockers are installed)

Can anyone point me toward a real solution that is proven to work?

Thanks in advance

---

### Post by whaevr on 2009-01-31
Might sound like a dumb suggestion but only thing I could think of is:

are you downloading 64 bit version of the flash plugin..?

Run firefox through terminal and go to youtube and see what happens in the terminal.

---

### Post by alexmaco on 2009-01-31
Well, I had a similar problem on hardy x64 (still using it). I couldn't get the flash plugin I downloaded from adobe.com to run. The only thing that worked was installing flashplugin-nonfree from the repositories (as well as nspluginwrapper of course because the version in the repos, although labeled as 10.0... is actually the 32-bit 9.0.124 version).

---

### Post by whaevr on 2009-01-31
So your still using a 64-bit Os then? I know the 64-bit flash plugin works-I'm using it.

Heres instructions from the adobe website on how to install flash 64 on linux [LINK](http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html)

---

### Post by rhardie on 2009-01-31
I am running 32 bit Adobe Flash on a 32 bit OS.

I rebuilt my system and converted from a 64 bit OS to 32 bits due to lack of compatibility of some applications I needed to run.

Just to be on the safe side, I'm going to double check the Flash for 32 bits.  Sometimes it is the things that you THINK that you know are OK that are the issue.

Thanks for the thought.

Come Hell or high water, we are putting an end to this bug-a-boo.  :-)

I'm extremely busy and I may just hire someone to fix the problem.  I'm gonna have to hire someone anyway for a new project so what the heck.

---

### Post by gandaran on 2009-02-01
> **rhardie said:**
> I am running 32 bit Adobe Flash on a 32 bit OS.

I rebuilt my system and converted from a 64 bit OS to 32 bits due to lack of compatibility of some applications I needed to run.

Just to be on the safe side, I'm going to double check the Flash for 32 bits.  Sometimes it is the things that you THINK that you know are OK that are the issue.

Thanks for the thought.

Come Hell or high water, we are putting an end to this bug-a-boo.  :-)

I'm extremely busy and I may just hire someone to fix the problem.  I'm gonna have to hire someone anyway for a new project so what the heck.
check your /tmp directory, it could be full due to disk space (how much free space do you have on the root partition ), delete the downloaded videos files or just reboot to clear the temporary files, now try again the flash videos.

---

### Post by rhardie on 2009-02-03
I've been away a few days ...read the post... cleaned out the temp folder (which was not full)...helped a bit..I don't think it's flash related but it may be.  I can play videos but they are jerky and useless.  Even Firefox is slow to move from tab to tab and update pages.  I've noticed that as well.

Another forum contributor suggested that Flash was crashing core 4, which seems to be the case.  Now WHY is the next question.

Note added later:  Here is an interesting site that appears to discuss the issue:

[http://ninjamurai.com/blog/2009/01/04/adobe-flash-10-locks-up-browsers/](http://ninjamurai.com/blog/2009/01/04/adobe-flash-10-locks-up-browsers/)

---

### Post by rhardie on 2009-02-03
I'm not sure if this is a fix or not...but Flash is working now and it runs at normal speed.

I looked in Synaptic and found Macromedia flash packages installed so I uninstalled them; afterward, Flash videos played just fine on several YouTube videos.

It would make sense that possibly Flash got confused and had some conflicts.

---

### Post by x C0MMAND0 x on 2009-02-03
I have ran into that problem before and this is what I have found.  Run the following codes with all browsers CLOSED.

```
sudo apt-get purge flashplugin-nonfree 
```

```
sudo apt-get install flashplugin-nonfree
```

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

```
exit
```

This is a very simple solution, but it has always worked for me.  I also have a 64 bit OS and have ran into the exact problem.

---

### Post by rhardie on 2009-02-04
That is good, useful information (the command line solution just above).

I shut my system down last night, came back in and powered up and went to the sites that were not working.  Everything appears to be working find.

Also, I am noticing that my 4 cores are swapping out the load for Flash.  In other words, sometimes CPU4 is running 100%, then later another CPU does...and when Flash is not running, all CPUs are at low usage and evenly manage the work load.

I would say my issue is SOLVED.

---

