---
title: "Won't Boot Anymore After Nvidia Driver Upgrade"
date: 2005-11-21
forum: Multimedia &amp; Video
---

### Post by T0PS30 on 2005-11-21
Big problems!

I decided to try and update my Nvidia drivers... The ones out of the box only allowed 60Hz refresh rates which started to annoy me. 

New drivers means no more Ubuntu for me, can't even boot via recovery mode... (Or don't know how...)

I'm pretty new to all this so be warned. I followed the intrustions from one of the official Ubuntu sites. When deciding between GLX and Legacy I went for GLX since right next to it was a comment from someone with a Geforce 2MX (Like I have) that it wouldn't work with legacy...

I did the sudo terminal command and logged out of Gnome. Hit ctrl alt backspace and then all I had left was a cursor top left of the screen, back backdrop andthe cursor didn't go on and off as usual, it was frozen. No HD sounds either. Left it like that in good faith but had to reboot after a few minutes. Didn't seem it was going anywhere. 

Tried to boot normally - got stuck again on same cursor after the post. 

Tried to boot in recovery mode and I get the same. That's with pressing ctrl D to skip root maintenance. 

So I'm stuck after the post, black screen of death. Can't even get in to my beloved OS anymore :( 

How do I get in?
What do I do to revert the changes?
I guess I needed the legacy drivers hey?!

Any help will be appreciated a lot!

Many thanks, 

Johan a.k.a. T0PS3O

---

### Post by poofyhairguy on 2005-11-21
[QUOTE=T0PS30]Big problems!

I decided to try and update my Nvidia drivers... The ones out of the box only allowed 60Hz refresh rates which started to annoy me. 

New drivers means no more Ubuntu for me, can't even boot via recovery mode... (Or don't know how...)

I'm pretty new to all this so be warned. I followed the intrustions from one of the official Ubuntu sites. When deciding between GLX and Legacy I went for GLX since right next to it was a comment from someone with a Geforce 2MX (Like I have) that it wouldn't work with legacy...

I did the sudo terminal command and logged out of Gnome. Hit ctrl alt backspace and then all I had left was a cursor top left of the screen, back backdrop andthe cursor didn't go on and off as usual, it was frozen. No HD sounds either. Left it like that in good faith but had to reboot after a few minutes. Didn't seem it was going anywhere. 

Tried to boot normally - got stuck again on same cursor after the post. 

Tried to boot in recovery mode and I get the same. That's with pressing ctrl D to skip root maintenance. 

So I'm stuck after the post, black screen of death. Can't even get in to my beloved OS anymore :( 

How do I get in?
What do I do to revert the changes?
I guess I needed the legacy drivers hey?!

Any help will be appreciated a lot!

Many thanks, 

Johan a.k.a. T0PS3O[/QUOTE]


ok. you need one command. At the grub screen pick the option that has the word "recovery" in it. Then when it puts you on the command line, use this command:

> sudo dpkg-reconfigure xserver-xorg

Pick the "NV" driver early on and things WILL work (its the open source driver, but I have a Gefore2 MX and I CAN'T get the official Nvidia driver to work well to save my soul so lets just do what works). Also at one point you can specify what refresh rates you want.

Hope this helps.

---

### Post by T0PS30 on 2005-11-21
Thanks! 

But you have me lost... On the multi boot menu (I guess that's what you call 'grub screen') I already tried the one with 'recovery' in it. it did it's post with all the [ OK ] 's in text form, as oppose to the standard post in grafical form below the brownish Ubuntu logo. 

Towards the end it prompts for the root maintenance password or whatever it's called, which I skipped with ctrl-d since my own password nor a mere 'enter' wouldn't work. 

When it's done with the post I just get stuck on my non-blinking cursor. 

I'd better triple check I did choose what you suggest but I;m pretty sure I have... OK off now to reboot and double-check... Cheers.

---

### Post by T0PS30 on 2005-11-21
Below the three Ubuntu boot options and the XP option it indeed had a few lines telling me about hitting c for command like and pronto, there was grub. 

Typing your suggestion however resulted in error 27, unrecognized command. Though when I look at it again I might have typed

 sudo dpkg -reconfigure xserver-xorg //1 space too many...

Let's try again...

Tried again and triple checked the spelling but Grub won;t have my sudo command at all. Error 27 is all I get at that command line thing. I'm not entirely sure I was doing that in the right place though, I merely pressed 'c' to enter command line, it didn't 'boot'/post at all. Can you really edit the configuration when it hasn't even loaded a thing yet?

When I boot and get the Grub bootloader I get these options:

- Ubuntu kernel 2.6.12-9386
- Ubuntu kernel 2.6.12-9386 (recovery mode)
- Ubuntu memtest386+
Other
- Win XP

"Some text here about using the arrows to choose or press 'e' to edit commands or 'c' for command line."

Again, first two options take me to a dead end, all black screen when the first screen would normally load. 

Any ideas?

---

### Post by BoyOfDestiny on 2005-11-21
[QUOTE=T0PS30]Below the three Ubuntu boot options and the XP option it indeed had a few lines telling me about hitting c for command like and pronto, there was grub. 

Typing your suggestion however resulted in error 27, unrecognized command. Though when I look at it again I might have typed

 sudo dpkg -reconfigure xserver-xorg //1 space too many...

Let's try again...

Tried again and triple checked the spelling but Grub won;t have my sudo command at all. Error 27 is all I get at that command line thing. I'm not entirely sure I was doing that in the right place though, I merely pressed 'c' to enter command line, it didn't 'boot'/post at all. Can you really edit the configuration when it hasn't even loaded a thing yet?

When I boot and get the Grub bootloader I get these options:

- Ubuntu kernel 2.6.12-9386
- Ubuntu kernel 2.6.12-9386 (recovery mode)
- Ubuntu memtest386+
Other
- Win XP

"Some text here about using the arrows to choose or press 'e' to edit commands or 'c' for command line."

Again, first two options take me to a dead end, all black screen when the first screen would normally load. 

Any ideas?[/QUOTE]

I'm a little lost here... Ok what happens when you do the top option. It just tries to login but give you a couple of screens that say x can't start. This should drop you at command line right?

Put your normal username and pass
then run sudo dpkg-reconfigure xserver-xorg

If something else happens, try ctrl + alt + F1 (that should take you to a console prompt, and do the steps I listed above)

Good luck!

---

### Post by T0PS30 on 2005-11-21
[QUOTE=BoyOfDestiny]I'm a little lost here... Ok what happens when you do the top option.[/QUOTE]

It will start loading as normal, I get the back background with brown/gold  post info with the [ok]'s etc. under the Ubuntu logo and when normally the GUI would start I get nothing but pitch black. Dead. No sound from my machine 'thinking' - no nothing. 

[QUOTE=BoyOfDestiny]It just try and login but give you a couple of screens then say xorg can't start. This should drop you at command line right?[/quote]

No. The only way for me to get to the *a* command line is when it present me the options but instead of choosing one I press 'c' which takes me that very instant to the command line. 

The only way for it to prompt me for a password is when I take option two, the recovery mode. Towards the end of loading all kernel stuff like the system clock, usb devices etc. it will ask me for a root password for maintenance. Not a username. It says I can skip entering that password with ctrl+d which I do because none of my passwords work. 

[QUOTE=BoyOfDestiny]Put your normal username and pass
then run sudo dpkg-reconfigure xserver-xorg[/quote]

The only command line I can get to (which is the grub one that calls says something about BASH-like commands being supported before the prompt) returns error 27 when I enter that command (or all it's variations I could think of spelling wise). 

[QUOTE=BoyOfDestiny]If something else happens, try ctrl + alt + F1 (that should take you to a console prompt, and do the steps I listed above)

Good luck![/QUOTE]

I'll try that but have no clue where. So I'll hammer away.. Back in a few mins...

---

### Post by az on 2005-11-21
You set a root password, didn't you?  When there is no root password set, you are not asked for one and are dropped into the shell.

Do you remember it?


Nevermind.

Do you still have your install cd?

Boot it and let it detect all you discs and stuff.  There is a rescue mode, but I do not know where it drops you.  Just hit enter at the beginning.  Once your disks are detected, hit CTRL-ALT-F2 and enter the shell

type this:

mkdir mnt
mount /dev/hda5 /mnt 

(I assume that hda5 is your linux install.  Put in the correct device!)

chroot /mnt
dpkg-reconfigure xserver-xorg
reboot

---

### Post by T0PS30 on 2005-11-21
I tried CTRL ALT F1 on the normal boot option which changes the way the post is presented but the end result is the same. Dead end. 

The very last post result I can see starts with "HP Linux Printing[...]" then when it's supposed to move to the GUI it dies gracefully. 

Azz... Thanks for joining in! No, I didn;t set a root password. Probably shoulda, woulda coulda but that's hindsight for you. 

Yes I have a install cd. So now it's ctrl alt f2 huh? Will try. 

I had an icon on my desktop that said hda8 - I guess that's my disk. 

What is this reconfigure xserver command going to do anyway? Reset everything back to square one or just my video adapter issues?

---

### Post by BoyOfDestiny on 2005-11-21
[QUOTE=T0PS30]I tried CTRL ALT F1 on the normal boot option which changes the way the post is presented but the end result is the same. Dead end. 

The very last post result I can see starts with "HP Linux Printing[...]" then when it's supposed to move to the GUI it dies gracefully. 

Azz... Thanks for joining in! No, I didn;t set a root password. Probably shoulda, woulda coulda but that's hindsight for you. 

Yes I have a install cd. So now it's ctrl alt f2 huh? Will try. 

I had an icon on my desktop that said hda8 - I guess that's my disk. 

What is this reconfigure xserver command going to do anyway? Reset everything back to square one or just my video adapter issues?[/QUOTE]


I can't believe google is this great...

[http://static.flickr.com/17/19949476_4472131b17.jpg](http://static.flickr.com/17/19949476_4472131b17.jpg)

A nice screen cap of dpkg-reconfigure xserver-xorg in action.

Anyway, don't forget my post about reinstalling and  putting /home on a seperate partition... You would be back up and running... 

Also, somewhat unrelated, but what CPU do you have? If you use the i686 (or k7 etc) kernel you should get a performance boost, plus the 386 kernel as far as I know cannot see a gig of ram...

When you get back into Ubuntu, run synaptic, search for linux-image, choose the package for your cpu...

---

### Post by T0PS30 on 2005-11-21
Thanks for the image, I hope I get to such a screen soon!

I tried azz' suggestions, here's my 'report':

Booted with install cd and continued with the install until it loads the hard disks. Pressed ctrl alt f2 and indeed I got to a command line interface which introduced itself as BusyBox. 

Did the mkdit mnt but when I did the mount command it came up with a mount error, that an invalid argument was supplied. 

I tried cd /dev and did ls h* which confirms hda8 exists. But cd /dev/hda8 gives me an error saying 'can't cd to' that folder. 

I tried the previously suggested sudo dpkg etc command to no avail. Without the sudo it perfomrs a little bit better but it then says xserver-xorg is not fully installed. 

So it seems the installation is phooked, judging by that I can't access hda8, right?

I do have a spare partition so I'll try BOD's suggestion tomorrow. Before I do that, is there any way of backing up my FireFox bookmarks considering I can access /dev on the command line (but not /hda8)? 

Also, I expected Ubuntu to see my other hard drive which is used by XP (I think FAT32) to store my music and videos. But Ubuntu didn't recognise it. 

Now I'm about to re-install, can you point me to the definitive tutorial on sharing a current disk with Win? (I've seen a few tutorials on this subject around, just wondering which you think will work best.)

I'll check back here tomorrow before doing so, any last minute efforts to solve this without a new partition installation will be much appreciated. 

BTW I have an Athlon Thunderbird 1400 on an Asus can't remember motherboard with an MSI ViVo Geforce 2 card of sorts. Can't even remember whether I have 7something or 1gig ram. I didn;t know there were different kernel's for different systems. Which one should I choose? I guess I;ll have ot make a new cd then...

---

### Post by BoyOfDestiny on 2005-11-21
[QUOTE=T0PS30]Thanks for the image, I hope I get to such a screen soon!

I tried azz' suggestions, here's my 'report':

Booted with install cd and continued with the install until it loads the hard disks. Pressed ctrl alt f2 and indeed I got to a command line interface which introduced itself as BusyBox. 

Did the mkdit mnt but when I did the mount command it came up with a mount error, that an invalid argument was supplied. 

I tried cd /dev and did ls h* which confirms hda8 exists. But cd /dev/hda8 gives me an error saying 'can't cd to' that folder. 

I tried the previously suggested sudo dpkg etc command to no avail. Without the sudo it perfomrs a little bit better but it then says xserver-xorg is not fully installed. 

So it seems the installation is phooked, judging by that I can't access hda8, right?

I do have a spare partition so I'll try BOD's suggestion tomorrow. Before I do that, is there any way of backing up my FireFox bookmarks considering I can access /dev on the command line (but not /hda8)? 

Also, I expected Ubuntu to see my other hard drive which is used by XP (I think FAT32) to store my music and videos. But Ubuntu didn't recognise it. 

Now I'm about to re-install, can you point me to the definitive tutorial on sharing a current disk with Win? (I've seen a few tutorials on this subject around, just wondering which you think will work best.)

I'll check back here tomorrow before doing so, any last minute efforts to solve this without a new partition installation will be much appreciated. 

BTW I have an Athlon Thunderbird 1400 on an Asus can't remember motherboard with an MSI ViVo Geforce 2 card of sorts. Can't even remember whether I have 7something or 1gig ram. I didn;t know there were different kernel's for different systems. Which one should I choose? I guess I;ll have ot make a new cd then...[/QUOTE]

I guess k7, I believe Athlon is k7 =). 

Anyway, simplest suggestion: 
Download a livecd like kanotix, and if you have a usb key handy, copy out your firefox stuff, should be somewhere in /home, The folder (for me) is .mozilla and contains firefox and all it's goodies.

Good Luck!

---

### Post by az on 2005-11-22
[QUOTE=T0PS30]
I tried cd /dev and did ls h* which confirms hda8 exists. But cd /dev/hda8 gives me an error saying 'can't cd to' that folder. [/QUOTE]

Your install is not on /dev/hda8.  That is my guess.

You instal is not hosed.  It is about tenty seconds away from being fixed.

You just have to wait for the correct twenty seconds, I guess.

You have an X problem.  It is on little thing to fix.

I will boot the installer and play in rescue mode and report back in five minutes.

Wait.

---

### Post by az on 2005-11-22
Okay.  If you boot your Breezy cd and type "rescue" at the prompt you get into rescue mode.  It will go through the steps of deteting everything and the final question will be which partition to mount as root?

The partitions will be displayed in a devfs style, so you will have to know which partition is your linux install?

I did not try to pick the wrong partition (like my swap) so I do not know what will happen if you do.  Worst case, you will have to reboot and try again.

Anyway, once you are in, run

dpkg-reconfigure xserver-xorg and reboot. 



P.S.  And no, setting a root password is not a good thing.  If you did not have a root password set, you would be able to use the recovery mode you have in grub.

---

