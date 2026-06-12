---
title: "Kernels to a good home."
date: 2005-10-21
forum: Multimedia &amp; Video
---

### Post by Rinnan on 2005-10-21
It's not clear which forum I should post this, so I will here.

I have created an Ubuntu kernel, out of version 2.6.13, with Con Kolivas's patchset revision 8 (latest non-experimental subversion as of today). The basic purpose of this was to add Unichrome drm/dri support (which comes standard in 2.6.13) and to apply the -ck patchset which improves interactivity under load (so that your music doesn't skip when you have six compiles and a movie playing, and you are running on a 1Ghz machine designed for power consumption efficiency and not for speed).

Basically, I want to offer it to whoever wants it, but I need to find a home for it, because I don't have the bandwidth to offer such a thing. It's huge, although I forget the exact size because I'm not at home right now. This version is compiled for later C3 (specifically, c3-2) CPU's, such as the VIA EPIA Nehemiah M and MII series, and many other VIA's. You probably know who you are if you have such a beast. I will also create VIA Epia Eden series (c3) and of course a -386, -686, and -k7 standard versions. For now, you can use this one, however, as long as you have a CPU that can run code compiled for a Pentium 3, which is nearly every machine out there.

So -- if you have Unichrome and need accellerated 3D, this is the one. If your music is skipping and it's not a hardware problem, or a sound configuration problem, but just because you insist on running with a load average of 8.50, for example ripping multiple DVD's while compiling the latest version of amaroK and six other popular Linux packages at the same time, then you have a personal problem, but I have the same problem, and want to help you feed your addiction. In any case, this is the one. So, who will give these nice kernels a home? Please do not respond just to get me to send you a kernel and then not offer it or torrent it. A small select group of Unichromers however, I will send a copy to right away, as I've already agreed to help them, and because... you know... we Unichromers stick together and all.

THIS IS EXTREMELY EXPERIMENTAL. YOU ARE NUTS -- NUTS!!! -- FOR EVEN THINKING ABOUT RUNNING IT! I take ***NO*** responsibility whatsoever -- for anything at all! But particularly in relation to running this.

The details:

A single .deb file, built with make-kpkg, using an almost standard kernel config file (changed only the settings which changed in 2.6.13 and -ck8 plus processor type, with an eye towards best desktop performance).

Install with "sudo dpkg -i <whatever I called the thing>.deb".  Reboot.  Bob's your uncle.

By installing this and using it, you are LEGALLY, agreeing to nothing at all, because the GPL doesn't require that you do so for simple installation and use -- but on a KARMIC and SPIRITUAL level you are agreeing to report bugs, not go insane with frustation if/when things go wrong, and throw you cat out the window, NOT cursing me for problems but instead, calmly, with the keen eye and mind of an engineer, reporting problems to the best of your technical ability, assisting me in fixing them, and assisting others. In other words, you are agreeing to act exactly like almost all Ubunters always act anyway.

Erik

**UPDATE** -- script to create the new kernel is enclosed. Please test this! It should create a -686 compatible kernel .deb file and source file in your /usr/src/ directory. To run, start a terminal, then:

```
bzip2 -9 ck.me.bz2
chmod +x ck.me
./ck.me
``` 
When it is done, find the right file inside of /usr/src (it will be timestamped, so the name will change) and install it with "dpkg -i <the name>.deb". Then reboot. You can install all four .deb's in fact without hurting anything.

Unless it blows up, which it might.  Experimental and all.

---

### Post by ilans on 2005-10-21
Hello
I send to you a private message

---

### Post by Beej on 2005-10-23
Haven't got a home for it but I would love to have this kernel. Have you found anybody to host it yet?

---

### Post by Rob2687 on 2005-10-23
Put it on like rapidshare or something like that for now. Or why don't you just put up a torrent?

---

### Post by Lem on 2005-10-23
I'll have this hosted for download tomorrow.

It's based on a .13 kernel, which i've found doesn't support my wireless card. (Netgear WG311v2)
I'm going to try to implement what Rinnan has done on the standard Ubuntu kernel.

---

### Post by Rinnan on 2005-10-23
Here's a "YouSendIt" link to it, will last a week. Or I can YouSendIt again to whoever wants it. The reason I don't put up a torrent is because this won't follow a torrent pattern of downloads. Torrents work best when you have many, many downloaders downloading the file at the same time. This file will probably be wanted by at most a few hundred, scattered evenly in time. Otherwise, it would all come down to the seeder (me). But my machine is up and down, testing various kernels. I wouldn't make a good seeder, especially a good *first* seeder.  Of course, anyone who wants to, may seed it.  Anyone at all!  hint, hint... :D

[http://s38.yousendit.com/d.aspx?id=372PGC0TW6SAO1NGDBOWE8X04G]("http://s38.yousendit.com/d.aspx?id=372PGC0TW6SAO1NGDBOWE8X04G")

Still working on that script. It will do everything for you, and build it on your own machine. You just pick a .config file (or provide your own), which I'll include in several exciting flavors. So I'm guessing about 5 .config files with the script, for a total of about 100K, so that will be easier.

**Update:  version 0.001alpha is being tested tonight (it takes all night to run).  Will upload tomorrow if it doesn't format my harddrive.**

---

### Post by Rinnan on 2005-10-24
[quote=Lem]I'll have this hosted for download tomorrow.

It's based on a .13 kernel, which i've found doesn't support my wireless card. (Netgear WG311v2)
I'm going to try to implement what Rinnan has done on the standard Ubuntu kernel.[/quote]

Lem, once I get this script to work, I will create a variant for you that builds the Unichrome drivers on top of the standard Ubuntu (-686) kernel.

For now, can you confirm that everything works (except Unichrome 3D) on your existing kernel, and that kernel is -686?

(you can install the -686 kernel using Synaptic, "linux-image-686")

---

### Post by Lem on 2005-10-24
I have 686 kernel running on my main machine at the moment. (M10000)

For Epia users with the fanless 'Eden' CPU models, the 686 kernel doesn't work, due to a lack of cmov support with this CPU.

---

### Post by ubunxpm on 2005-10-24
Hello, I am am using the 2.6.13-k7 and have a few questions about this new kernel.

1) Should I wait until you put together -k7 version of this new ck kernel?
2) If I try to install 386 version and something goes wrong can I still go back and boot with original .13-k7?
3) Is this new kernel compiled with the unichrome project's via driver for unichrome igp or ubuntu's original?

And thank you Rinnan for doing this and helping lots of newbies using unichrome get their hardware working properly...

---

### Post by Rinnan on 2005-10-24
[QUOTE=ubunxpm]Hello, I am am using the 2.6.13-k7 and have a few questions about this new kernel.

1) Should I wait until you put together -k7 version of this new ck kernel?
2) If I try to install 386 version and something goes wrong can I still go back and boot with original .13-k7?
3) Is this new kernel compiled with the unichrome project's via driver for unichrome igp or ubuntu's original?

And thank you Rinnan for doing this and helping lots of newbies using unichrome get their hardware working properly...[/QUOTE]

1)  If you are already running a 2.6.13 kernel, you already have Unichrome support (right?  Did it work?).  What my kernel gives you, other than that, is the "ck-patches", which gives you better interactivity at the price of a less-tested and probably less well supported and understood (around here) kernel than the standard one.  What does this mean?  It means you can put your system under higher load or unusual load patterns and still get a responsive system.  It also includes some patches for better swapping (for a desktop, not a server), and other patches designed to improve the Desktop Linux users life.  

It's very experimental however and I have had some problems with it.  

If everything works (you've got 3D, your music never skips, you don't get hit with bad behavior such as, after leaving your machine alone for a long time, does it take FOREVER to become usable again, and just sits there for a minute or two just sluggishly doing very little?)  If all is OK -- DON'T CHANGE ANYTHING (unless you are just a tinkerer at heart and can't resist).  The Ubuntu standard kernel also has patches to improve desktop behavior, since Ubuntu is primarily a desktop OS.

2)  Yes, it'll just add it to the grub menu.  Just hit the escape key quickly right before Linux boots and you will be able to choose any other kernel that you've already installed.

3)  This new kernel just includes the standard Unichrome driver that came with 2.6.13 vanilla, I forget the version but it's only slightly older than CVS, so it's probably a good bet.

---

### Post by ubunxpm on 2005-10-24
I apologise for the confusion. mine is not the .13   it is 2.6.12-9-k7
Since I am using a laptop and did not experience the problems you have listed above (and not interested in tinkering), don't you think I should stay with this kernel and just get the new unichrome drivers and dri package?
But do I still have to compile the kernel with the new drivers?

---

### Post by Rinnan on 2005-10-25
In that case I think you are very right.  I recommend that you follow [this post]("http://www.ubuntuforums.org/showthread.php?p=429867#post429867") exactly.  That will get you what you want.

If you have any questions, just ask.

Just to clarify, when I say, "build your own kernel", I mean build an exact duplicate of your existing kernel. The reason why is because it seems that the unichrome-drm script mentioned in there needs the full source tree (not just the headers), and needs it to have already been fully built. So, a pain, I know, but it needs to be done until a new script is written. There's no thinking involved though -- just copy the existing kernel config file right over! No reason to change the config. (you may have to change your Processor type however, unless there's a config specifically for the k7)

Then use the drm script, restart X, and that's it.

Erik

---

### Post by Knowles on 2005-10-27
I am quite new to this put I have a unichrome intergrated card and I currently run the 2.6-12-9-k7 kernel. I have dri working but I lack 3d acceleration, now I ran the script however I could not see a time stamped .deb file in /usr/src/ anywhere. I however just booted up the kernel and like i guessed had not had 3d acceleration enabled. Is there a possibility of somebody telling me what I am doing wrong. I believe theuse of the shell script worked as I got Done! at the end of it

---

### Post by Rinnan on 2005-10-27
Oh dear, I need a little more info.  What did you get in the 20 or so lines before the "done"?  

This message is for everybody:  If you want to help me debug my script, I am grateful so lets do it, but if you just want things to work and not bother with the script, then I can gmail all the working .deb's to you.

Knowles, if you don't know the lines, is it possible for you to rerun the script such:

./ck.me 2>&1 > torinnan.out

which will create a file, "torinnan.out" which you can then send to me (at my gmail e-mail account, I am "thepurr"), and I will diagnose.

---

### Post by Knowles on 2005-10-28
[QUOTE=Rinnan]Oh dear, I need a little more info.  What did you get in the 20 or so lines before the "done"?  

This message is for everybody:  If you want to help me debug my script, I am grateful so lets do it, but if you just want things to work and not bother with the script, then I can gmail all the working .deb's to you.

Knowles, if you don't know the lines, is it possible for you to rerun the script such:

./ck.me 2>&1 > torinnan.out

which will create a file, "torinnan.out" which you can then send to me (at my gmail e-mail account, I am "thepurr"), and I will diagnose.[/QUOTE]

ok thanks i will try that

---

### Post by Bazon on 2006-03-05
Hello everyone!

I'm a Ubuntu Newbee and my main goal in this case is to view videos on my Via Epia M 6000 Board.

So how do I manage this best?

Is DRI support the same as mpeg hardware accelaration support?

Do I have to compile a specific version of mplayer or so to do this?
Or is it enough to use just the patched kernel?

Do I need to [compile it myself ](https://wiki.ubuntu.com/ViaEpiaDriHowto)or can I download it from anywhere (is there a home for them found now?)

I would be happy for any help!

Thanks,
Bazon


PS:
I opened [a new thread](http://ubuntuforums.org/showthread.php?t=140376) with a more general question and tried to delete this post to avoid crossposting, but i didn't suceed in deleting tihs post, sorry....

---

