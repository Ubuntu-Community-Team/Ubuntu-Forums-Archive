---
title: "Do I really have to use a Windows burning program?"
date: 2008-11-26
forum: Multimedia Software
---

### Post by SamNSane on 2008-11-26
Okay, it's entirely possible that I'm being a moron, but at least I'm a consistent moron.

I have installed HH on three different physical systems. I have installed II on two different physical systems. All components have eventually worked for me. (Period of about 4 weeks total for testing, finding the apps I want, configuration, customization, etc.)

I have no problem using remote access of several types (both to and from), no problem with any kind of wireless or wired networking, no problem translating and importing data from proprietary Windows platform apps to Open Source apps on the Linux platform.

You would think that I would be able to burn a cotton-picking CD-R or DVD-R disc on at least one of these five systems, wouldn't you? They all have different optical drives. (A couple of them even have TWO different optical drives.)

Nope. I can't burn with brasero or with k3b or with cd creator. I don't even get off the ground trying. Brasero and cd creator tell me there was an error. K3b tells me there's no media in the drive -- after it reads the blank media and tells me what it is! On every single drive on every single system!

Am I just an idiot when it comes to using burning software? Funny. I never had a problem on the Windows side, and I had no problem burning discs back when I tried earlier versions of Ubuntu and Mint and Debian and Red Hat. What's happening with the recent versions?

Do I really have to install wine and imgburn in order to burn a cotton-picking disc in Ubuntu??? Really?

The other issue I have is -- HOW do you burn the contents of hidden directories -- or just back them up to other locations for that matter? So far, the only solution I've found is to rename the danged things to get rid of the . at the front of the name, burn, then rename again.

The only backup that's really working properly for me without stupid workarounds like renaming twice and using wine/imgburn is commercial software called Beyond Compare (recently ported to Linux from Windows). It allows me to include / exclude folders and files by any criteria imaginable. But it isn't burning software.

Somebody, please lend me a little advice!

---

### Post by cariboo on 2008-11-26
Supplying an error log would be helpful. One other thing to try is a different brand of media.

To see hidden directories and files, in any file manager window press Ctrl-h

Jim

---

### Post by snares on 2008-11-26
A lot of time I can burn a cd without going through Braseo or K3B just by using nautilus. At least if its a data cd. Dont do many audio cds anymore.

---

### Post by SamNSane on 2008-11-26
> **cariboo907 said:**
> Supplying an error log would be helpful. One other thing to try is a different brand of media.

To see hidden directories and files, in any file manager window press Ctrl-h

Jim

I appreciate you thinking about trying to help me analyze the problem, but an error log isn't really going to be helpful. There are a number of these threads about the nondescript error messages and logs produced by brasero. The threads here and there across the Internet that resemble my problem are not being solved. And the k3b behavior is just plain insane.

And it's not the media. I've tried 11 (yup, 11) types of CD-R including Verbatim, and 5 different types of DVD-R, as well as a couple of CD-RW brands. These drives ALL work perfectly every time using any Windows burner. They also ALL work perfectly every time using imgburn under wine in Linux.

There's absolutely nothing wrong with the drives or the discs. The problem is either with a clean installation of Ubuntu 8.04.1 and Ubuntu 8.10 or with me. I am a very consistent person. It's possible that I'm doing something to cause the problem, but I can't figure out what it might be.

The systems themselves range from 2-5 years in age and are various brands -- Dell, Panasonic, Toshiba, HP.

I have no problem seeing the hidden files and folders. But the only way I've found to get those hidden items backed up to external media is to rename them (remove the dot). Surely, Linux has to have better tools available than this for the purpose of performing data backups to optical disc?

Is this problem as universal as it appears to be from my admittedly very limited perspective? If so, I would expect to see a LOT of Internet traffic about it.

I'm annoyed that I have to

a) rename everything that's hidden that I want backed up (twice, once to get it backed up, and then once again to get it functional under Linux again), and
b) use wine and a Windows application

to be able to make backups under Linux.

---

### Post by SamNSane on 2008-11-26
> **snares said:**
> A lot of time I can burn a cd without going through Braseo or K3B just by using nautilus. At least if its a data cd. Dont do many audio cds anymore.

Yes, thanks. I've tried that, too. That's what I was referring to when I mentioned "cd creator". I might have the name wrong. But it gives me exactly the same nondescript error as brasero.

---

### Post by psyke83 on 2008-11-26
Without providing logs or filing bugs, you're expecting no more than a miracle. Do you realize this forum is populated primarily with fellow users, and the developers who are capable of fixing such problems will most likely never see your posts (or take interest without a bug already filed)?

Instead of taking the time to compose these posts, why don't you file a bug about your issue? You can:

[LIST]
[*]Launch brasero from the terminal to check for debug output
[*]Check your "dmesg" and "hdparm -i /dev/sdc0" logs for drive and DMA information
[*]Do yourself a favour and restrict yourself to CD-RW media... unless you like to make your own drink coasters... ;)
[/LIST]

---

### Post by herteljt on 2008-11-26
I may be way off base (but you said you wanted suggestions) There is a user privilege dealing specifically with accessing cd-roms. When I upgraded to 8.10 some privileges had been changed (However, they were with a mounted hard drive not cdrom drives.)

---

### Post by doas777 on 2008-11-26
i can burn cds and dvds on every version of ubuntu I've tried thus far.

---

### Post by SamNSane on 2008-11-26
> **psyke83 said:**
> Without providing logs or filing bugs, you're expecting no more than a miracle. Do you realize this forum is populated primarily with fellow users, and the developers who are capable of fixing such problems will most likely never see your posts (or take interest without a bug already filed)?

Instead of taking the time to compose these posts, why don't you file a bug about your issue? You can:

[LIST]
[*]Launch brasero from the terminal to check for debug output
[*]Check your "dmesg" and "hdparm -i /dev/sdc0" logs for drive and DMA information
[*]Do yourself a favour and restrict yourself to CD-RW media... unless you like to make your own drink coasters... ;)
[/LIST]

Good points all. I'm mostly looking for commiseration. I'm experienced enough to know that what I'm seeing is not coincidence. I'm too pressed for time by serious work pressures right now to try to do any real diagnostic work. It's hard for me to believe that I can see this issue on five separate system installations of the two most recent versions of Ubuntu with such varied hardware without it being a widespread issue.

When time allows I'll go to launchpad and try to find out whether the bug (if that's what it is) has been registered.

In the meantime, I do have a solution. It's just that it irks me to have to use the Windows application. I do have to say that imgburn is about the best burning application I've ever seen. I just don't like using it under wine. I'd rather use a "native" burner.

---

### Post by SamNSane on 2008-11-26
> **herteljt said:**
> I may be way off base (but you said you wanted suggestions) There is a user privilege dealing specifically with accessing cd-roms. When I upgraded to 8.10 some privileges had been changed (However, they were with a mounted hard drive not cdrom drives.)

Good point, and one of the first things I checked, even though the error message should say something about not being allowed or permissions or some such if this were the problem. But that wasn't it.

---

### Post by doas777 on 2008-11-26
> **SamNSane said:**
> Good points all. I'm mostly looking for commiseration. I'm experienced enough to know that what I'm seeing is not coincidence. I'm too pressed for time by serious work pressures right now to try to do any real diagnostic work. It's hard for me to believe that I can see this issue on five separate system installations of the two most recent versions of Ubuntu with such varied hardware without it being a widespread issue.

When time allows I'll go to launchpad and try to find out whether the bug (if that's what it is) has been registered.

In the meantime, I do have a solution. It's just that it irks me to have to use the Windows application. I do have to say that imgburn is about the best burning application I've ever seen. I just don't like using it under wine. I'd rather use a "native" burner.


you have my sympathy. There are some things I've never been able to get working right, and it can be very frustrating. 

good luck,
franklin

---

### Post by SamNSane on 2008-11-26
> **doas777 said:**
> i can burn cds and dvds on every version of ubuntu I've tried thus far.

Until 8.04 and 8.10 that was true for me, too. It was also true for me in Linux Mint and Red Hat / Fedora.

I wonder if this has something to do with the fact that I've enabled the backport repository. Hard to believe, but I guess it's possible. I haven't done anything else out of the ordinary.

---

### Post by SamNSane on 2008-11-26
> **doas777 said:**
> you have my sympathy. There are some things I've never been able to get working right, and it can be very frustrating. 

good luck,
franklin

You're mighty right. As frustrations go, this is pretty minor. It's just that the failure of such a very basic functionality in such an (otherwise) impressive user environment is  -- almost so absurd as to be grotesque.

As I said, it's entirely possible that this issue has been caused by me. I've seen many situations where experienced people (I've been using computers in my work every day since 1964.) can wreak havoc when wandering into a new environment. People who are experienced are used to exercising a great deal of control over many different elements of their working environment. Sometimes they unwittingly do "witless" things.

However, that's not usually a problem for me. I have to admit that this one has me stumped so far. On the other hand, I haven't really expended more than the tiniest bit of effort to deal with it. I'm just very, very surprised to find this little roadblock on every installation of Ubuntu from 8.04 onward.

I'm going to keep this thread bookmarked. When I get time to investigate and (I hope.) find a solution, I'll return to post it. If it was me being dumb -- and I don't doubt it for a second -- we'll all have a good chuckle about it.

---

### Post by bford16 on 2008-11-26
I had trouble burning a CD-R at first with Intrepid. Somehow I just did things in the wrong sequence. Once I got the steps figured out, burning with Brasero was even smoother and faster than before.  I did a 600 MB Xubuntu 8.10 install disk in about five minutes with no errors!  That used to take me about 15 minutes with Hardy. I find it extremely odd that you are having problems with ALL of your machines, ALL of your discs, and ALL of your software.  No offense, but I suspect user error here.  Especially since the Windows software works under Wine.  Looking forward to your error logs and experiment logs.

---

### Post by SamNSane on 2008-11-26
> **bford16 said:**
> I had trouble burning a CD-R at first with Intrepid. Somehow I just did things in the wrong sequence. Once I got the steps figured out, burning with Brasero was even smoother and faster than before.  I did a 600 MB Xubuntu 8.10 install disk in about five minutes with no errors!  That used to take me about 15 minutes with Hardy. I find it extremely odd that you are having problems with ALL of your machines, ALL of your discs, and ALL of your software.  No offense, but I suspect user error here.  Especially since the Windows software works under Wine.  Looking forward to your error logs and experiment logs.

What? Am I supposed to dance naked around a bonfire whilst strangling a chicken before inserting the blank disc? ;)

Trust me, not anything that anyone on this planet ever wants to witness.

If there is a user component to this, it's something a little more arcane than the sequence in which the writing procedure is selected, media is inserted, files are chosen, etc. I've tried the obvious sequential voodo practices. And if it is something along those lines, then we're talking about a very badly designed user interface.

The problem may very well have something to do with the way I have enabled repositories and performed updates before ever proceeding with any attempts to burn images or data to disc. I didn't alter configuration procedures between systems because I couldn't believe that just one little part of the system could fail consistently like this because of ordinary installation procedures.

I've used brasero, k3b, serpentine, and other burning software many times with no trouble in earlier versions of Ubuntu and in other Linux distros. Something material has changed. It could be something that happens primarily on notebook systems, or to people who perform certain specific software installations and/or update from specific repositories, but it's not just simple PEBKAC.

Unfortunately, though I have a little time on my hands at the moment, I'm not really in a mood to fiddle around trying to troubleshoot a very simple feature that just should have worked on all of these installations. But you can be certain that the next Ubuntu installation I do will include an attempt to burn with brasero before a single change (including updates) is made to the installed image.

---

### Post by SamNSane on 2008-11-27
I promised to report anything I learned. This isn't much, but it's about all I care to do under the circumstances.

I got lucky this morning and had a little time to look at one of my own systems running 8.04.1 which is having this problem. I tried just a straight, uncomplicated data project write to DVD-R using brasero, and it succeeded, albeit with an error statement at the end of the session, to wit:

```

Session error : the disc could not be mounted (max attemps reached) (brasero_burn_record burn.c:2384)

```

I then tried the backup procedure which really matters -- the one that includes e-mail / calendar / etc. To perform this backup I first have to go into /home/user and rename the hidden files and folders that I wished to have backed up. These include the .mozilla and .mozilla-thunderbird folders. And that's probably where the problem lies. When I try to write this data set to DVD-R the session, after much huffing and puffing, fails with:

```

BraseroGrowisofs stderr: /dev/scd0: "Current Write Speed" is 16.4x1352KBps.
BraseroGrowisofs stderr: :-? the LUN appears to be stuck writing LBA=1c0h, keep retrying in 23ms
BraseroGrowisofs stderr: :-? the LUN appears to be stuck writing LBA=1c0h, keep retrying in 23ms
BraseroGrowisofs stderr: :-? the LUN appears to be stuck writing LBA=1c0h, keep retrying in 23ms
BraseroGrowisofs stderr: :-? the LUN appears to be stuck writing LBA=1c0h, keep retrying in 23ms
BraseroGrowisofs stderr: :-? the LUN appears to be stuck writing LBA=1c0h, keep retrying in 23ms
BraseroGrowisofs stderr: :-? the LUN appears to be stuck writing LBA=1c0h, keep retrying in 23ms
BraseroGrowisofs stderr: :-? the LUN appears to be stuck writing LBA=1c0h, keep retrying in 23ms
BraseroGrowisofs stderr: :-? the LUN appears to be stuck writing LBA=1c0h, keep retrying in 23ms
BraseroGrowisofs stderr: :-? the LUN appears to be stuck writing LBA=1c0h, keep retrying in 23ms
BraseroGrowisofs stderr: :-? the LUN appears to be stuck writing LBA=1c0h, keep retrying in 23ms
BraseroGrowisofs stderr: :-? the LUN appears to be stuck writing LBA=1c0h, keep retrying in 23ms
BraseroGrowisofs stderr: :-? the LUN appears to be stuck writing LBA=1c0h, keep retrying in 23ms
BraseroGrowisofs stderr: :-? the LUN appears to be stuck writing LBA=1c0h, keep retrying in 23ms
BraseroGrowisofs stderr: :-? the LUN appears to be stuck writing LBA=1c0h, keep retrying in 23ms
BraseroGrowisofs stderr: :-? the LUN appears to be stuck writing LBA=1c0h, keep retrying in 23ms
BraseroGrowisofs stderr: :-? the LUN appears to be stuck writing LBA=1c0h, keep retrying in 23ms
BraseroGrowisofs stderr: :-? the LUN appears to be stuck writing LBA=1c0h, keep retrying in 23ms
BraseroGrowisofs stderr: :-? the LUN appears to be stuck writing LBA=1c0h, keep retrying in 23ms
BraseroGrowisofs stderr: :-? the LUN appears to be stuck writing LBA=1c0h, keep retrying in 23ms
BraseroGrowisofs stderr: :-? the LUN appears to be stuck writing LBA=1c0h, keep retrying in 23ms
BraseroGrowisofs stderr: :-? the LUN appears to be stuck writing LBA=1c0h, keep retrying in 23ms
BraseroGrowisofs stderr: :-? the LUN appears to be stuck writing LBA=1c0h, keep retrying in 23ms
BraseroGrowisofs stderr: :-? the LUN appears to be stuck writing LBA=1c0h, keep retrying in 23ms
BraseroGrowisofs stderr: :-[ WRITE@LBA=1c0h failed with SK=3h/ASC=72h/ACQ=01h]: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 1
	message	= "Unhandled error, aborting"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
BraseroGrowisofs stderr: /dev/scd0: flushing cache
BraseroGrowisofs Called brasero_job_set_progress (1.000000)
BraseroGrowisofs called brasero_job_set_current_action
Session error : Unhandled error, aborting (brasero_burn_record burn.c:2384)

```

The two 8.10 installations I did for a friend on a Toshiba and an HP were also failing to write for him, as I reported. When I called him to compare notes he said that brasero was complaining about folders being too many levels down and asking if he wanted to include them anyway. He has been answering yes, and then watching the burn fail. I had him try a burn without the renamed .mozilla and .mozilla-thunderbird folders, and it succeeded -- with exactly the same error message at the end of the session as I saw this morning.

So...on 8.04.1 I see no warning at all from brasero, and the job fails. On the 8.10 installations there are warnings about folders too many levels deep from brasero when setting up the session, you tell it to go ahead and burn the folders, and then the job fails.

On both versions of Ubuntu we get the max attemps message at the end of the session even when we succeed in a simple burn with just a few folder levels.

The wine/imgburn combination on all systems with both versions of Ubuntu works just fine, with a burn and verification taking less time than the "successful" burn without verification under brasero. The fact that the burn is successful is confirmed by MD5SUM, file by file.

I had tried k3b on two systems using a very fast external Sony usb writer, and it kept telling me that there was no media in the drive, even as it was showing me exactly what media I had in the drive in another pane of the application window. Weird.

I've satisfied myself that the user interface for brasero isn't going to let me write data the way I need to write it. I've satisfied myself that k3b doesn't like something about my primary system. I'm sure there are  workarounds, but I have a working solution with wine/imgburn, and I have better things to do than play around with burning apps. When brasero and/or k3b put the settings I need in the user interface, I'll try using the native apps again.

The funny thing is that I am certain that I was burning this same type of data to disc in earlier versions of this distro. I wonder if the developers have done something to make the burns more standards-compliant by default? If so, I can't imagine why they would force the issue, since both modern Linux and Windows can read these discs just fine. It's good to be standards-compliant. It's also good to have choices.

One other observation. During use of brasero, the writer's speed "hunts" all over the place. It sounds like I'm writing new firmware to a RAID controller or something. High speed, low speed, high speed... Under wine/imgburn the drive just chugs through the session at a moderate pace.

That's about all the motivation I can muster for now. If I didn't have a working solution for burning I'd be all over it like white on rice at launchpad. As it is, I'll get around to it eventually if attitude and time permit.

Thanks for your consideration, everyone.

---

### Post by psyke83 on 2008-11-27
SamNSane,

Really, that information belongs to a bug report. By all means, throw it out to the forums as well (perhaps someone will offer a solution that works), but the forums should always be secondary.

Nevertheless, some quick googling gives the impression that your issue may be caused by DMA problems, or driver conflicts due to the PATA and SATA drivers vying to control the same device. 

Your issue will never get fixed until somebody successfully cajoles you into filing that bug... :P

---

### Post by SamNSane on 2008-11-27
> 
Really, that information belongs to a bug report. By all means, throw it out to the forums as well (perhaps someone will offer a solution that works), but the forums should always be secondary.

Nevertheless, some quick googling gives the impression that your issue may be caused by DMA problems, or driver conflicts due to the PATA and SATA drivers vying to control the same device.

Your issue will never get fixed until somebody successfully cajoles you into filing that bug... :P 


<whining>Oh, man! You're so strict!</whining>

I'll try to get around to it some time today or tomorrow. All I really want to do today is eat tacos and drink tequila.

What? Isn't that what everybody does on public holidays?

---

### Post by miesnerd on 2008-12-01
> **SamNSane said:**
>  All I really want to do today is eat tacos and drink tequila.

What? Isn't that what everybody does on public holidays?

No, that's what I want to do constantly. Ugh.
Moving away from Tequila and tacos, have you tried a different version of linux that allows you to operate as root and see if that works? You could quickly run something like DSL which allows (i believe) you to be root and see if it'll let you write to a cd. Also, puppy might be a good one to check into in this regard. If those distros work, you affirm what you already know (its not the hardware--works on the windows side) and you learn its not a linux kernel thing. After that, its just a matter (imo) of filing a bugzilla report with ubuntu and detailing all of it.

---

### Post by SamNSane on 2008-12-02
> **miesnerd said:**
> No, that's what I want to do constantly. Ugh.
Moving away from Tequila and tacos, have you tried a different version of linux that allows you to operate as root and see if that works? You could quickly run something like DSL which allows (i believe) you to be root and see if it'll let you write to a cd. Also, puppy might be a good one to check into in this regard. If those distros work, you affirm what you already know (its not the hardware--works on the windows side) and you learn its not a linux kernel thing. After that, its just a matter (imo) of filing a bugzilla report with ubuntu and detailing all of it.

I'm not thinking that this is a permissions problem, though I suppose anything is possible. In any event, I'm a little squeamish about operating as root, but I might try this tactic if I think that further examination of the problem warrants it.

I had planned to file a bug report, but other issues with greater immediate priority have hit me pretty hard the past few days. In my perusal of launchpad I found a few bug reports that might be fairly closely allied with my own problems. I'm going to need a little chunk of time to do a decent job of looking into it.

In the meantime, it's funny just how well imgburn under wine does this job for me. With a working, albeit slightly cobbled-together feel to it, having a satisfactory way to do the job kind of lowers the motivation to go after the "bug", if that's what it is.

But, I'll try to develop a more community-spirited attitude about it as soon as I can put a little time together.

;)

Thanks again for your concern and help.

---

### Post by aeiah on 2008-12-02
seems like they're talking about your problem here:
[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/200337](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/200337)

there are a couple of solutions posted there but nothing is proven to work universally. i suggest trying:

1. burn at the slowest speed. some drives are reporting that they're faster than they are. im guessing you've tried this though as its pretty obvious.

2. update everything related to burning. stuff like growfs and such.

3. edit the grub menu.lst file as described so ubuntu doesnt assume your drive is sata or whatever

4. update kernel. if you have closed source drivers you'll need to reinstall these. make sure you backup your xorg and nvidia-settings or whatever if this is gonna be an issue

5. manually compile a new kernel as described at the bottom.

personally i wouldn't go as far as number 5 unless i was prepared to bork my system. what with imgburn working under wine for the time being.

---

### Post by SamNSane on 2008-12-03
> **aeiah said:**
> seems like they're talking about your problem here:
[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/200337](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/200337)

there are a couple of solutions posted there but nothing is proven to work universally. i suggest trying:

1. burn at the slowest speed. some drives are reporting that they're faster than they are. im guessing you've tried this though as its pretty obvious.

2. update everything related to burning. stuff like growfs and such.

3. edit the grub menu.lst file as described so ubuntu doesnt assume your drive is sata or whatever

4. update kernel. if you have closed source drivers you'll need to reinstall these. make sure you backup your xorg and nvidia-settings or whatever if this is gonna be an issue

5. manually compile a new kernel as described at the bottom.

personally i wouldn't go as far as number 5 unless i was prepared to bork my system. what with imgburn working under wine for the time being.

Oh, man. The weirdness just keeps rolling along. I'm not going to rant. I'll just summarize briefly what happened today.

I girded my loins for battle with brasero and the optical disc writer on my main system. I checked out the bug report at the link you posted, and I prepared to gather data to send to launchpad.

.
.
.

And brasero worked. Oh, it still gives the attemps error at the end of the burn, but that's the only sign of trouble. It stopped complaining about "too many directory levels", and the speed of the drive has stopped hunting. I did MD5SUM checks of the disc contents against the files on the hard drive. Perfect burns. 4 DVDs full of data so far without a failure.

The only thing that has changed on the system is a few updates, some from upstream, over the last couple of days. One of them was a hal update. But I just don't know.

I'll be happy if it really is a fix. I still kind of expect burning to stop working. But if it continues to work for a week or so I guess I'll be able to dispense with wine and imgburn.

Weird.

Oh, and brasero started working on a desktop system that got the updates, too. (I've only tested it with a single CD burn, but brasero wouldn't burn a CD on that system last week.) I guess I've got to test the other systems now.

---

