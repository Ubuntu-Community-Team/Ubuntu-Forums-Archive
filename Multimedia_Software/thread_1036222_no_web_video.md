---
title: "no web video"
date: 2009-01-10
forum: Multimedia Software
---

### Post by mcrene on 2009-01-10
Recently I have been having no video playback on the internet.
sites like Break.com give rather odd erratic pictures all over the movie play area.
other sites just download, but offer no playback at all.

searching has shown problems like this, but not quite the same, and trying what worked for them isn't working for me.

any command in terminal gives a response like this
"dpkg: status database area is locked by another process"

I found 2 broken packages in the Synaptic Manager... but have no idea what to do now.

Trying to close the Manager down tells me it will lose the changes I have told it to make... but I can't run the updater because it gives this error
"unable to get an exclusive lock" something about apt-get or another program running, and I should close it.


what is going on here, this is a mess. for a program favoured for not having windows like problems, thats all I have gotten since I installed it. sorry for *** remarks, just my ignorance getting on my own nerves.

thanks for help.

---

### Post by mcrene on 2009-01-10
added:

have tried rebooting, have tried multiple sudo commands (I am very new to linux have no idea what those do, something like the old DOS maybe?)

anyway, every attempt at an update gives the "unable to get exclusive lock" "is another program using it" or something along those lines.

it would be nice to watch a video online... it would also be nice for this program to work properly... I'd settle for video's for now tho.

---

### Post by mcrene on 2009-01-10
some help?

---

### Post by mcrene on 2009-01-10
a recent attempt at using Update Manager gave this msg

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

still no idea what all this means... does anyone anyone anyone? echo echo echo...

---

### Post by tuxxy on 2009-01-10
OPen terminal and run the following command;

```
sudo dpkg --configure -a
```

Then check you have flashplugin-nonfree installed using Synaptic.

---

### Post by mcrene on 2009-01-10
ran the command (had run it before too), nothing came up either time.

I have the flashplugin-nonfree installed, but the Esound Library was not, don't imagine that will solve the lack of visual problem, but marked it for install anyway.

---

### Post by mcrene on 2009-01-10
just stopped by NBC.com and none of the videos there will play for me either.

what is going on here? why can I not get video to work?
why can I not get "exclusive lock" on whatever it is that requires it?

why is this running like crap? I really don't want to resort back to XP, what a let down.

---

### Post by mcrene on 2009-01-11
why can I not watch video on the internet in ubuntu?

---

### Post by hikaricore on 2009-01-11
First you need to calm down a bit.

Please wait 24 to 48 hours before "bumping" your own posts.
There is one reply in this thread and 7 posts by you.  That's too much.

Someone will be more likely to assist you if you don't annoy them all.
Honestly if I came along this thread and had information on your issue I would ignore it.

Please please please just be patient and wait for the volunteers in this community to do their best to assist you.
In the mean time try searching google and the rest of the forums for info relating to your issue.

If you post again in this thread aside from an apology **before anyone else posts** I will close your thread.

---

### Post by pink_fone on 2009-01-11
> **mcrene said:**
> added:

have tried rebooting, have tried multiple sudo commands (I am very new to linux have no idea what those do, something like the old DOS maybe?)

anyway, every attempt at an update gives the "unable to get exclusive lock" "is another program using it" or something along those lines.

it would be nice to watch a video online... it would also be nice for this program to work properly... I'd settle for video's for now tho.

Regarding the exclusive lock, I think you can only run an installer one at a time.  So for example, Update Manager or Synaptic or Add/Remove is running and you issue ```
sudo dpkg --configure -a
``` you're going to get that error.  Close Update Manager or Synaptic or Add/Remove before issuing the command.  

It's just a guess.  I'm no ubuntu expert but you may want to try that.

About the web video, does it give an error?

---

### Post by mcrene on 2009-01-11
If I thought I was bumping for no good reason, I wouldn't have done it. When a thread gets to page 3 or 4 I find it normally doesn't get looked at.
I have searched, a lot, Google, these forums and as many other places as I have been able to find information on "exclusive lock" "dpkg" "is another process using it" and any other error messages I have been given.

That being said, I have been pretty upset about this ordeal and probably come off rather curt, for that I apologize. I was expecting too much from Linux after using only Windoze for years, and when I started having problems I couldn't understand why there is so much hype over Linux. I get that this is new to me, and I can't 'fix things' the way I am used to doing. Again, sorry for my ignorance on this subject and persistant 'bumping' it was not meant to upset anyone. 

Anyway, as for running ony one installer at a time, I have none running (that I know of)
I don't have Update Manager or Synaptic or Add/Remove running. In fact I just tried typing that code into Terminal and I couldn't even type in it, or cut n paste for that matter.

I was able to find a video I could watch, a linked vid from YouTube, but it looked like crap (could have been low quality) the time was 00:00 the whole time, and the movement bar stayed at the start.

thank you for the continued help.

---

### Post by hikaricore on 2009-01-11
No harm done. It sounds that something is wrong in a few areas.

Either there is an issue with Flash or there is an issue with your sound.

I had a similar experience on my flatmate's system where flash videos would not play and it ended up being a sound issue which I couldn't only fix by a reinstall and much tweaking (long story).

The fact that you can't type anything into a terminal also bothers me.
Is this a terminal that you just opened?  Or one that you've used before this?

Open a new terminal and type the following:
> pidof apt-get dpkg synaptic update-manager adept

If this returns any number then a package manager is running and possible crashed, you will need to close it or maybe reboot for this to be resolved.

---

### Post by hikaricore on 2009-01-11
No harm done. It sounds that something is wrong in a few areas.

Either there is an issue with Flash or there is an issue with your sound.

I had a similar experience on my flatmate's system where flash videos would not play and it ended up being a sound issue which I couldn't only fix by a reinstall and much tweaking (long story).

The fact that you can't type anything into a terminal also bothers me.
Is this a terminal that you just opened?  Or one that you've used before this?

Open a new terminal and type the following:
> pidof apt-get dpkg synaptic update-manager adept

If this returns any number then a package manager is running and possible crashed, you will need to close it or maybe reboot for this to be resolved.

---

### Post by mcrene on 2009-01-11
correction:
I can type in Terminal, however when I typed the "sudo dpkg --configure -a" command it asked for my password, but this time I couldn't type anything. nothing came up, no matter which buttons I pressed. 

when I tried the 
"pidof apt-get dpkg synaptic update-manager adept "
command, nothing came up.

The YouTube video that did work gave sound no problem, but I couldn't move forward/back in the movie, pause or restart it.
NBC video's are just a blank white where the video should be.
Break.com videos are erratic all together, I'll post a pic of what comes up, but the pic only shows one clip. The actual video portion of the screen changes, the white square in the vid moves all over, and the words move a little side to side.

Well I am unable to upload any pictures. Seems any flash uploaders don't want to work either.

Kinda lost now, not sure what else to say about whats wrong. If any info is needed let me know, I'll get it.

---

### Post by hikaricore on 2009-01-11
When entering a password into a terminal there will be no characters shown, not even stars.
You just need to type the password and press enter.  This is a security feature.

It doesn't mean you can't type in the terminal it just means you can't see it.

I have no idea what you mean bout flash uploaders, lets stick to the topic at hand.

---

### Post by mcrene on 2009-01-11
the password being invisible I knew about, but when I typed in my password it wouldn't accept it. checked CAPS, tried again, nothing. Ended up rebooting and it worked first time, no idea, but thats done.

either way, the command you told me to try, gave no response. I would take that to mean there are no other package managers running as you mentioned.

as for the flash uploader, sorry I figured it was another flash related problem. The picture site I use to upload too, like Hi5.com uses what I presume to be a flash program to show a "My Computer" like visual of where I want to upload my pictures from, as opposed to the "Browse" feature of older sites.


anyway, you mentioned a re-install to fix the problems you had. Is this a full re-install of Ubuntu, as I recently did that (5 days ago, after screwing up my previous install)
Or perhaps just an install of Firefox and related programs?
thanks again.

---

### Post by hikaricore on 2009-01-11
Honestly if your system is a fubared as you make it sound, you may at least consider a reinstall.

Something along the way has gone terribly terribly wrong.

If you're using Intrepid I might suggest you try out Hardy as it's more stable, if you're using Jaunty for some ungodly reason then you should try out either Hardy or Intrepid.
I'm not saying your problems are insurmountable by any means, but it sounds like somewhere you've broken something quite massively and it may be just easier to go back to the basics.

This is not a conclusion I ever reach lightly so by all means make the decision for yourself.
Hopefully someone can assist you further but I'm afraid at the moment it can't be me.

---

### Post by mcrene on 2009-01-11
no believe me I appreciate the advice.

but I am not sure about what you mean by Hardy vs Intrepid vs Jaunty?

I downloaded the latest version of Ubuntu that I could, this is my first time using it so I am an unaware as to what name it goes by.

---

### Post by mcrene on 2009-01-11
huh, off topic again, but now Pigen or whatever the MSN Messanger is here will not let me log in. Something about my network address book being unavailable.

me thinks yet another reinstall is in the works soon. this will be the 3rd in just over a week.

---

