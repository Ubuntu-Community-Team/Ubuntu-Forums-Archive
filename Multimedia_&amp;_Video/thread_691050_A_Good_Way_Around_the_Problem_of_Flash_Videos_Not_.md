---
title: "A Good Way Around the Problem of Flash Videos Not Playing or Crashing Your Browser"
date: 2008-02-08
forum: Multimedia &amp; Video
---

### Post by Mr. Dave on 2008-02-08
Hi
I'm a complete and utter newbie when it comes to Ubuntu or any other version of Linux - This is my first posting on this forum - I still use Windoze XP, but am now beginning to take a real interest in Ubuntu as I am NOT going anywhere near Vista or any other new iterations of Windoze - XP has served me well but if and when it becomes obselete that is the time there will be a parting of the ways between myself and Micro$oft.  The laptop I'm making this posting on came with Vista Home Premium pre-installed and after getting first-hand experience of what a tiresome and utterly dreadful piece of bloatware it was, I formatted the hard drive and installed XP, considering myself lucky to have been able to.  I have a feeling there are probably going to be a lot of people like me out there, who will be making the exodus from Micro$oft in the years to come, for much the same reasons.
 Anyhow, to get to the point, I have a spare desktop machine that I've recently installed with the 32-bit flavour of Ubuntu 7.1.  I know there is going to be a pretty huge learning curve for me as even though thisis a GUI-based OS, it really is very different to Windoze isn't it? (not that that's a bad thing)
The first real issue I came across was getting the machine to play a DVD, which was the beginning of what can only be called in plain English, 'a right carry-on'...   When I put a disk in the drive,  the OS would open Totem Movie Player, which would tell me I was missing a plugin and refused to play the DVD.  I then clicked the button to 'get the missing plugin' but got a message telling me the site was unavailable or had moved etc.  So I then went to the 'add/remove' thingy on the programs menu and selected 'All Programs' in the hope that something suitable would turn up.
I ended up going through quite a lot of stuff before I got a working solution, but I have to say I ended up wasting HOURS before I got there, and unfortunately the forum just added to my confusion; it just seemed too fragmented and what seemed to work for one person wasn't what would work for another - it wasn't that anyone was at fault or to blame for anything - I downloaded lots of codecs from add/remove, I tried Xine & Mplayer, but didn't start to get any real sense out of the machine until I installed VLC Media Player, which I must say is totally excellent.  I set it up using the removable drives menu so that when I insert a pre-recorded DVD, it now plays, with no complications or messing about.  It works just as well,- in fact better with all those options it has, especially the graphic equalizer- as 'Power DVD 5' does in my XP machines.  Problem solved,kewl!.
The next headache was caused by Flash videos, or I should say the complete lack of Flash videos.  I'm using Firefox BTW.  I would go to 'You Tube', select a Video to play and the part of the screen where the video is meant to be would remain dark grey, then a few seconds later the browser would lock up and refuse to respond to either the mouse or the keyboard, leaving me no choice but to press the machine's reset button; I did this quite a few times over the next hour or so.  Before crashing, the browser gave me an odd sense of deja vu, as it told me I needed more plug-ins to be able to view SWF videos.  When I clicked on the button I was given the choice of installing either Adobe Flash, or 'Gnash'.  Installing either or both of these did not provide me with the result I'd hoped for, in fact it provided no result at all; within seconds of clicking a video thumbnail in You Tube the browser promptly crashed again leaving me again with no option but to push the reset button.  I also tried installing the 'Ubuntu  Restricted Extras' from the Add / Remove  menu, although I wasn't sure what the point of this would be as it did say that this would amongst other things, install Adobe Flash , which I'd already tried.  Then I remembered I'd noticed something about VLC player having a Mozilla Plug-in and I have to say, I'm really not sure if it was the instruction I found that I wrote into the terminal to activate it, or if it was because i had uninstalled everything else that claimed to be able to  play Flash videos, but I then opened the browser and in 'preferences'  I was able to set it so that VLC player handled all media files and  lo and behold! I now have flash videos playing normally!!    So the moral of the story seems to be don't bother trying to download flash, gnash (maybe the fact they rhyme with 'crash' should have told me something)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     or this or that codec, restricted or not, just get VLC Media Player and it would appear to take care of all your video requirements in a straightforward and uncomplicated way, which is a lot more than I can say for any of the other applications or plug-ins I tried.  Now obviously my problems could well be attributed to my inexperience with Ubuntu, but after I'd done a Google search on Ubuntu and Flash Video problems, it certainly appears to be a recurring theme, so as far as I can say in my very limited experience with Ubuntu, VLC is without doubt the way to go.

---

### Post by kpkeerthi on 2008-02-08
Sorry about the problems you have been having. vlc does not play flash. It appears to me that you still have flashplugin installed.

Type ```
about:plugins
``` in firefox's address bar and that should tell who takes care of flash content.

---

### Post by Mr. Dave on 2008-02-09
Hi 
And thanks for the reply.  I don't want to start an argument with you but VLC does play Flash content! even before I managed to get it streaming straight off the page like i can in XP, the one media player that would work when I downloaded and then tried to play back the flash videos was VLC too!  I'm not near that machine at the moment so I can't check the version number but I did find this on the VLC Wiki which would seem to support what I've just said.
[http://wiki.videolan.org/Flash_Video](http://wiki.videolan.org/Flash_Video)
nevertheless I'll try doing what you've suggested out of interest to see if there is still is any traces of Flash left in there but I did make sure that I had no flash gnash or anything else in that machine, I even removed Totem with the Synaptic package manager.  The VLC site does mention it's mozilla plug-in that claims to be able to play most kinds of media you'd encounter on the internet. 
I'd like to try out the 64 bit Ubuntu on my Opteron 185-based desktop, but from what I've been reading it's quite complicated when it comes to using media players again as they're all 32 bit. Oh well onward and up the learning curve, it certainly is a steep climb

---

### Post by kpkeerthi on 2008-02-12
Great. I didn't know that. :)

For the benefit of others, can you put in a few simple steps what needs to be done as it is quite hard to find out from your rather long post.

Cheers.

---

### Post by arjanito on 2008-03-31
Hi there.completely remove Gnash and Flash Player.Then install Flash Player again .Works fine for me.

---

### Post by Prefix100 on 2008-03-31
Yeah I love vlc,

I've said it before and I will say it again, the best media player in existence.

Also, I can sympathize with your reasons for moving to Ubuntu - its the exact same reason I moved - Vista.

---

