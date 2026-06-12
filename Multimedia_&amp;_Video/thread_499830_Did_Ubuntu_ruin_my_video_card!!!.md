---
title: "Did Ubuntu ruin my video card?!?!?!"
date: 2007-07-13
forum: Multimedia &amp; Video
---

### Post by dewdman42 on 2007-07-13
Hi everyone.  I downloaded the last 7.x Desktop Ubuntu today, my first time trying it.  I burned a CD and booted the CD and there I was looking at the ubuntu desktop.  Worked like a charm.  The screen resolution however was set way lower than my monitor.  I have a dual DVI vid card(Matrox) with only one monitor plugged in, the Dell 24inch LCD, which has 1900x1200 or something like that.  Ubuntu was at like 1024x768.  I went to the the menu at the top and saw the item for screen resolution.  When I went into screen resolution there was no option over 1024x768, so I just hit close to get out.

Then I hit the red button in the top left corner to restart the computer.  I pulled the Cd out and let the computer reboot, but when it booted back up, the monitor would not work.  Period.  Like the monitor does not even show the BIOS stuff or anything.  As if the DVI port on the back of my computer is completely dead.  In fact the power button on the front of the monitor shows yellow, which I think is supposed to be power saving mode or something like that...  I have tried to remove the vid card and put it back, completely disconnected power and reconnedted again, everything I can think of that would reset the vid card....if that's even possible...but this vid card no longer displays.  I can hear the computer boot into windows, and if I insert the ubuntu Cd to boot I can watch it boot into Ubuntu by watching the lights on the CD drive and listening to it whir, but it displays absolutely nothing now on the screen during the entire process.

What the heck did Ubuntu do to my vid card?  Is my video card now ruined?!?!?

---

### Post by shavenlunatic on 2007-07-13
1024x768 is the default res when first setting up your video drivers iirc.  I have never heard of a video card being damaged by trying to display too LOW a res (that's not to say it hasn't happened before i guess).

You tried your VDU in both DVI ports?  You tried getting up the monitor test screen (usually by turning it on while the PC is off, should generate some image/text on the screen)

No idea, I doubt it was specifically ubuntu which' broke' your video card.. but ya never know I guess..

---

### Post by southernman on 2007-07-13
> **dewdman42 said:**
> 

What the heck did Ubuntu do to my vid card?  Is my video card now ruined?!?!?

lol Ubuntu did nothing to your card.

You need to run the command:

sudo dpkg-reconfigure xserver-xorg

Answer the questions to the best of your ability (you should know your refresh rates for your monitor and specs of video card prior to this step above), Google if your not sure what specs your video, keyboard, and monitor is.

---

### Post by shavenlunatic on 2007-07-13
> **southernman said:**
> lol Ubuntu did nothing to your card.


sudo dpkg-reconfigure xserver-xorg


he did state that he can't even see the BIOS POST screen.... so that's not likely to be the issue

---

### Post by Gremlinzzz on 2007-07-13
Did ya take out the battery to reset bois try removing ram sticks one might have went bad .does the monitor work on other machines.pull all cards out and put em back.check all plugs.make sure fans work.

---

### Post by dewdman42 on 2007-07-13
Thanks everyone for responding..

I agree...I can't think of any reason why linux or windows or any other OS should be able to "ruin" a video adapter.  nonetheless, Ubuntu was the last thing running before my card ceased to function.  All I can figure is that it tried to send some screwed up refresh rate or some other thing that threw my card into a tizzy.  I have contacted Matrox and they told they don't support Linux.  I don't know what that means.  I am going to be pulling the card out and trying to put into another PC in order to isolate the problem to the card itself for sure.  

Is it possible that something about the way Ubuntu was configuring my vid card, the vid card got confused and jammed up somehow in its own bios memory area?  I don't think there is a battery on this video card or way to reset it that I know of.  I might be able to try to reflash the bios on it.  

The vid adapter is dual.  I tried already to plug my monitor into the 2nd port.  What happens is that it still does not display the bios boot up sequence on the screen for me(the card must only do that to port 0 I guess).  However, I notice that when using that DVI port, the monitor's power button does go to green and stay green.  On the faulty port, the power button on the monitor quickly changes to yellow, which is a powersave mode that indicates the PC is not sending signal I think.  I have already used the monitor test modes and gone through the monitor menus a number of times...there is nothing wrong with the monitor.  

there is nothing else that transpired to cause this.  It could be a totally random fluke coincidence that I was running ubuntu from a booted CD, it worked, but at low resolution, then I rebooted with the CD ejected, to reboot into windows and the monitor stopped working after that.  Never saw a bios screen again.  to me iits pretty obvious that something about the vid driver in ubuntu has thrown my card into a state where it no longer functions.  Possibly a bug in Matrox bios too, but how can I possibly prove that?

AS I said before, I can hear windows login me in with the windows startup sounds, etc.  If I try to boot from the ubuntu Cd, I can watch the Cd spin, presumbly booting up ubuntu.  But I see nothing on the monitor.  I've tried powering off the monitor and powering it on again, etc..at least 20 times.

---

### Post by Gremlinzzz on 2007-07-13
I was referring  the mobo battery.if you take it out for awhile its should reset the bois. mobo---motherboard. maybe a long shot but try Darik's Boot and Nuke
[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

---

### Post by dewdman42 on 2007-07-13
Yea right.  erasing my Hard drive is not exactly what I had in mind.

---

### Post by kevinlyfellow on 2007-07-13
> **dewdman42 said:**
> Yea right.  erasing my Hard drive is not exactly what I had in mind.

That shouldn't erase your hard drive, just the bios information (not stored on a harddrive)

---

### Post by dewdman42 on 2007-07-13
From the referenced website:

[INDENT]"Darik's Boot and Nuke ("DBAN") is a self-contained boot floppy that_** securely wipes the hard disks**_ of most computers. DBAN will automatically and completely delete the contents of any hard disk that it can detect, which makes it an appropriate utility for bulk or emergency data destruction.

DBAN is a means of ensuring due diligence in computer recycling, a way of preventing identity theft if you want to sell a computer, and a good way to totally clean a Microsoft Windows installation of viruses and spyware. DBAN prevents or thoroughly hinders all known techniques of hard disk forensic analysis."[/INDENT]

??

Also, I don't thnk I want to erase my PC's bios just yet either.  I doubt the PC bios is the problem, though you never know.  Is it possible for ubuntu to change my bios settings?

---

### Post by Gremlinzzz on 2007-07-13
Taking out mobo battery wont erase your hard drive just reset your bios but the link to Darik's Boot and Nuke program will. i figured you blamed ubuntu its a sure fire way to remove it.

---

### Post by dewdman42 on 2007-07-13
As i explained in my first post.  Ubuntu was never installed on my HD.  I booted and ran it from the CD only.

---

### Post by OzzyFrank on 2007-07-13
First off, I don't think even mailcious software can break hardware, but then I am no expert. I would venture that it is actually much more likely it is an unfortunate coincidence you ran the Live CD while hardware was failing of its own accord. I had this with Edgy when I couldn't figure out why I was having so much trouble with the system and drive errors... well it turned out I had decided to install Ubuntu on a drive that was failing, but the symptoms were there before, as I just used it for simple backups. When I got S.M.A.R.T. errors upon boot, I knew it couldn't be Ubuntu, but had to be a dying drive.

As for the BIOS, I doubt resetting it will fix anything. But yeah, it won't wipe any hard drive data, so you can always try it.

I suggest trying the card in another PC, and also hooking up another monitor to your PC with that card (I just had ANOTHER monitor die, so it happens).

---

### Post by tgalati4 on 2007-07-14
Try unplugging the computer for 10 minutes.  Sometimes the video cards need a cold reset to get the graphics processor running properly.

---

### Post by dewdman42 on 2007-07-14
10 minutes unplugged is something I haven't tried yet.  I will try that.

As for it being just a coincidence, that is mighty suspicious to me.  Interesting that it happened to you with Ubuntu also.  ;-)

---

### Post by OzzyFrank on 2007-07-14
Yeah, as a technician who values things like causality and logic, it has almost pained me to see things fix themselves up after "a good night's sleep". I mean some serious Windows errors and stuff... that had to be CAUSED by something (besides a lack of sleep, hehe!). Even turning it all off for 2 hours... no good... a full night's sleep... bingo! I mean, when things go back to normal it is great and all, but gives me a brain ache! Hehe...

As for it being "interesting" that it happened "with" Ubuntu for me as well... that's about all it is. I'm sure the drive would have come up with the SMART error earlier if I used it more for backing up before turning into my Ubuntu drive. Got a new drive, no problems. To imply Ubuntu had anything to do with it... well, I may as well blame it on the alignment of the stars, the Dark Side of the Force, or "bad mojo", hehe. I certainly wouldn't come here to advertise my superstition, just like I hate admitting I've let PCs have a nice long nap to fix things up, hehe.

---

### Post by shavenlunatic on 2007-07-16
I think you're getting a little "Conspiracy Theorist" with you believing it's Ubuntu which killed it.. i'd place money on the fact that it was about to die anyway

---

### Post by autie07 on 2008-05-03
Sadly I have to disagree with most who pose that Ubuntu may have not fried or compromised the video card, around july last year the exact thing happened to me, I have a laptop so I left my tower as is hoping that as soon as I reboot it later it will just go away.

Flash forward to may 2008.... still NADA, and I switched the vid card and hurraay it works... but then it froze setting the res again, and as it got a forced reboot, zap... no more video signal...

My screen is brand new, no problems with it at all... just that stupid card problem with this ubuntu.

---

