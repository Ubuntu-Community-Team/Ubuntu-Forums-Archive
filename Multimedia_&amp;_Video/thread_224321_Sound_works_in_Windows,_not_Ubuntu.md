---
title: "Sound works in Windows, not Ubuntu"
date: 2006-07-27
forum: Multimedia &amp; Video
---

### Post by adambullock on 2006-07-27
(Ahead of time, you can skip to the "HERE'S THE BEEF" section if you want...

Ok, a little introduction. I *have* searched around these boards and havn't been able to fix this problem yet. So if you're one of those people who like to read posts and respond just by saying "duh, do a search", then please just keep it to yourself. Sorry to sound rude (especially in my first post!) but I *really* hate that. 
I *am* a completely new Ubuntu user, and although I would not call myself a computer expert by any means, I certainly think I know more than average. I got Flash installed in Firefox on Linux, which was NOT an easy task (someone really needs to work on making that easier, BTW, if we're ver going to "convert" many people from Micro$not to Linux...took me over an hour),I built the PC I'm on, (well kinda, it's sorta a Frankenstein Dell), I have networked, etc. Now that you know where I'm comming from, here's the deal (and please keep in mind that while I have some experience, my Linux knowledge is VERY limited)

HERE'S THE BEEF:

I have Windows XP and Ubuntu both installed. Sound and video are perfect in XP, there is NONE in Ubuntu. I read a "comprehensive sound problem guide" at [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) but to no avail.
My sound card is listed as a "Crystal WDM MPU-401 Compatible" in windows, and it's built into/onto the mboard. 
So, here's the question: WHAT do I do NOW?


I really like Ubuntu, and although I'm quite frustrated at the moment (mp3 support, DVD support being WORKABLE but an issue, freaking FLASH not even installing easily) I really want to keep it up to the point that I can ditch Microsoft alltogether. Someone, PLEASE HELP!
Oh, and there's also and issue with one of my network cards that is NOT a problem in Windows...but thats's a different forum, right? :)
Anyone willing to "take me under their wing"?

---

### Post by LordRaiden on 2006-07-27
Not familiar with your soundcard at all. If you know the manufacturer have a look here, [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/). If it is not listed, you are out of luck. You'd have to file a bug report and ask that your card get supported as a feature request.

---

### Post by darkhatter on 2006-07-27
modprobe snd-cs4236

try that command just hit alt+F2 and then copy and paste it, another person did that on fedora core 2 and it worked for him, after that you then need to unmute it by hitting the sound option thing in gnome or kde, and unmuting it.
sorry if that wasn't helpful message me again and I'll help you

---

### Post by darkhatter on 2006-08-03
I'm sorry I didn't respond to your pm.

I'm not sure what to do about that maybe the ubuntu kernel doesn't have the driver installed

and I made a mistake open a konsole and type that command in and tell us what is says, sorry about that

and about your internet is it dhcp (you are given a IP), or is it adsl

---

### Post by itendsnow on 2006-08-03
Also quick note, if you are using more than 2 speakers, open up the volume control and select it so you can see Front, Surround, Center, Side, and turn them all up.

---

### Post by adambullock on 2006-08-04
All I know is I have a dynamic (not static) IP. It's Time Warner's ASDL. I'm so stuck I don't know what else to try; i've spent hours on this to no avail. Also, I looked at this forum: [http://www.ubuntuforums.org/archive/index.php/t-186914.html](http://www.ubuntuforums.org/archive/index.php/t-186914.html)
which describes my pc perfect (a Dell Optiplex GX1) and tried what tiger338 suggested, but i couldn't edit that file, it was set as rread only. I realize some of you are totally rolling your eyes at this, but as I admitted, I am BRAND new to linux....and it's weird to me! For example, I had a power flash yesterday, and when my pc re-booted into linux, the screen size had changed, and I couldn't get it back. So I shut down and booted into Windows and it was normal! Then, guess what...yep, back into ubuntu and it was back to normal. W>T>F? But forget the screen...someone PLEEEEASE help me with my sound!
-Adam

---

### Post by darkhatter on 2006-08-04
my dad is a linux expert so I got most of my help from him so I'm not rolling my eyes at all. I have no idea how you set-up adsl in ubuntu but to do it in slackware you use adsl-setup (non-gui).

its some what confusing but tell me if you have that command on ubuntu I'm in slackware, I only use the kubuntu live-disk.

---

### Post by royskie on 2006-08-05
hello adam,

I'm a fellow noob.  Not that I'm acting as an expert, i'm basing my answer from experience.......I was just wondering if you already have checked all controls for sound?  Double click on the speaker icon, which should launch the volume control window, then click on EDIT and then PREFERENCES.  Put a check mark on everything in there then close the small windows.  Back on the volume control window, see if the MASTER MONO is unmuted.

---

### Post by adambullock on 2006-08-05
I DID IT!!!!

Ok, I'm going to explain, step by step, in as "basic" a way I can, how I did this. Basically, I just did what was outlined by tiger in [http://www.ubuntuforums.org/archive/.../t-186914.html](http://www.ubuntuforums.org/archive/.../t-186914.html)   but I first had to figure out HOW to do that, since I'm totally new at Linux, ubuntu, etc. So, for anyone that had/das the same problem as me, on a Dell Optiplex GX1, this is what worked for me:
1) Open a terminal by going to Applications>Accessories>Terminal
2) Get to the root directory with permission to edit the /etc/modules file by typing "sudo -i"
3) To open and edit the /etc/modules file, type "nano /etc/modules"
This will open up a text editor and (obviously) the /etc/modules file. Than, I simply...
4) Enter "snd-cs4236" on a blank line underneath everything that's already typed.
5) Hit Ctrl-X to exit.
6) It will ask you if you want to save the changes, I *think* you just hit "Y" and it saves and exits at the same time.
7) Reboot
(note....between 5 and 7, I opened the file again using "nano /etc/modules" just to make sure it saved correctly; it did for me)
8) Log back in to ubuntu
9) Do the dance of joy now that you have sound working!

Please note, this was done on an older machine, a frankenstein-ish Dell Optiplex GX1 with onboard sound. I have NO idea how this would work on any other system, but it worked for me. Furthermore, unless it's about EXACTLY what I did, unfortunately I couldn't help ANYONE with any other type of sound problem at this time because...well, I'm a complete noob. But if you're having sound problems on the same kinda system as me, give this a shot! Now, if anyone wants to help me figure out why one of my network cards isn't working in ubuntu but it does in windows.....look for a new thread soon!
-Adam
p.s.- thanks to everyone for not making smarta$$ comments about me not knowing how to edit a file or whatever and just being plain helpful.

---

### Post by Linux4HumanBeings on 2006-08-05
I have the same problem but on Step 2(2) [Get to the root directory with permission to edit the /etc/modules file by typing "sudo -i"] It says Permission denied and it doesnt give me acces. My sound isnt working but my speakers are on.Help Anyone

---

### Post by adds2one on 2006-08-05
Hi Adam,

I'm a relatively new Linux user as well, though an experienced PC user.

At the beggining of your post you said that it took you an hour to install flash in Ubuntu. You wished for a faster easier way. 

It's your lucky day. Check out Automatix, it is a program that you can run from Gnome and select things like multimedia codecs, flash compatibility in Firefox etc. It is just as easy as anything you have ever done in Windows.

To install Automatix follow the instructions here:

[http://getautomatix.com/wiki/index.php?title=Installation](http://getautomatix.com/wiki/index.php?title=Installation)

Just type exactly what it says and you will have it done in 5 minutes. The whole point of Automatix is to make the initial set up of your Ubuntu system easy. 

When you have finished installing it you can find it in Applications->System Tools and can run it from there. Check out all the useful stuff it will install and configure for you!

You can also uninstall Automatix anytime you want.

One note, at the end of using Automatix it will ask you if you want to replace your sources.list file. Just say OK.

Hope that helps and welcome to Ubuntu!:D

---

### Post by adambullock on 2006-08-05
after you type "sudo -i" and hit enter, you will have to enter your password; the same password you use to log in (as long as there is only one user, hopefully you, on your system, and you are the administrator). If you hit enter twice, it will say access denied.

---

### Post by quantboy on 2006-08-15
adambullock- you're the greatest.  This post just fixed the same "No sound" problem on my Dell Optiplex GX1.  

Also- to the previous poster who had the problem with the file permission- you can also try: su root 
and then type in the root password.  Should work the same to give you root permission. 

Now, after the reboot, I can see the speaker icon on the top menu bar. 

Now onto my next problem- why mp3's won't play...

---

### Post by exmatelot853 on 2006-08-16
Hi Adam,

Excellent solution to exactly the same problem I had with a similar FrankenDell GX1 PII 400. Automatix comes highly recommended, go to their website where there is an automatic install script as well, couldn't be easier.

Nice job.

exmatelot853

---

### Post by munkedal on 2006-08-18
4) Enter "snd-cs4236" on a blank line underneath everything that's already typed.

In step 4, where did you get the "snd-cs4236"?  I, also, cannot get any sound but I am running a HP computer.  I assume I would need a different code.
Can anyone help?

---

### Post by Andrew Booth on 2007-06-10
> **adambullock said:**
> 1) Open a terminal by going to Applications>Accessories>Terminal
2) Get to the root directory with permission to edit the /etc/modules file by typing "sudo -i"
3) To open and edit the /etc/modules file, type "nano /etc/modules"
This will open up a text editor and (obviously) the /etc/modules file. Than, I simply...
4) Enter "snd-cs4236" on a blank line underneath everything that's already typed.
5) Hit Ctrl-X to exit.
6) It will ask you if you want to save the changes, I *think* you just hit "Y" and it saves and exits at the same time.
7) Reboot
(note....between 5 and 7, I opened the file again using "nano /etc/modules" just to make sure it saved correctly; it did for me)
8) Log back in to ubuntu
9) Do the dance of joy now that you have sound working!

These worked for me on my GX1 with an integrated Crystal WDM soundcard. I can now actually enjoy my system because I have sound now. ;)

---

