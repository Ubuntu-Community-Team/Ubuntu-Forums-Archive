---
title: "ATI, Legacy Cards &amp; 9.04 - HELP!"
date: 2009-05-07
forum: Multimedia Software
---

### Post by Megamanic on 2009-05-07
Ok, let me tell you what I want to do & what I think is happening then if anybody can jump in & correct me that would be great.

I have an oldish laptop (HP nx6125).  Updating is not an option for the forseeable future.  I want to move over 100% to Linux & have a preference for Ubuntu Studio because I used to do a bit of home recording back in the early '90s and I have a video camera so I figured this would give me plenty to play with.

Anyway I grabbed the 9.04 AMD64 iso and it installed pretty much flawlessly I read that I should add NOACPI and vga=787 to the command line parameters which fixes a blackscreen on install which I can also vouch gets fixed if you depress the little button the computer uses to tell when the screen is down.  Good first impression.  Set up the repository to a local peer in WA to cut down on my bandwidth bill added open office & a couple of other applications.  Better at detecting my scanner than Windows XP. Contentment.

Now I hit trouble.  I'm a bit of a gamer.  Nothing too crazy but I do want to play Civilization IV with all of the expansions & Warhammer "Dawn of War" & Neverwinter Nights 1 (Not online, just locally)  So nothing beyond my machine's comfort zone.  Warhammer's probably the biggest resource hog but I played quite a bit of that on XP a little while ago & bougt "Soulstorm" recently so I planned to give it another go when I hit Ubuntu based on the Wine AppDB ratings.

First problem.  The AppDB ratings only apply if you have an NVIDIA card not the ATI on my laptop.  Straight up I'm probably getting around 0.75 fps in Soulstorm with the open source default driver - probably partly a Compiz issue I think as well.  So, I have a cunning plan & install the ATI driver using Add/remove in Ubuntu.  Big mistake.

This hoses my system because (I think) it installs the latest ATI 9.4 fglrx which doesn't work with my legacy graphics card.  Then I find (happy happy joy joy) that fixing the xorg.conf is beyong my meagre command-line skills.

I have to reinstall Ubuntu Studio from scratch.  Trying to "fix the graphics" fails.  Trying to repair the installation fails (might have been the blackscreen issue but too late to prove that now) and I'm back where I was a couple of days ago.

That's the background.  I've done some reading around and this is a summary of what I think I know about this sort of problem.  If any of this is wrong please correct me:

1) The last version of the Radeon driver that will work with my card is 9.3
2) The 9.3 driver probably won't work on Ubuntu 9.04 but some people seem to have done this
3) I might be able to tweak my xorg.conf to maximise the performance of the open driver enough to be as good as the proprietory driver
4) 3 is hard
5) I need to back up my xorg.conf better :)
6) Even 5 might not help if fglrx gets badly hosed

Anyway, my questions:  
1) Is there a howto that would help me get the 9.3 driver working on 9.04?
2) If not what's the actual reason why it breaks in 9.04 vs 8.10?  What changed?
3) Is a fix on anybody's radar?  How likely?  How long?
4) How good is the open driver for oldish ATI cards like mine?
5) What sort of changes would I have to do to my xorg.conf to make it work?  Even some general parameters would be good for me to start playing with.
6) Is there a place where working xorg.conf files are kept for reference?
7) If not is there a suitable wiki that we could hijack for this?  I know it's hard to share xorg.confs between desktop computers because there's so much potential variation in keyboard, mouse, screen & graphics card but laptops have a pretty much fixed configuration so any  nx6125 owner's xorg.conf would work on any nx6125 plus or minus a USB mouse.  Maybe it would be more manageable to index sections of xorg.conf by graphics card, mouse etc so you can go there & get working suggestions for each section as you assemble your xorg.conf - configuring X remains one of the biggest obstacles for newbies.  It was in 1998 when I first tried RedHat and it has been every time I've installed Linux subsequently.  Having a wiki where we can post working conf files & collaborate on optimizing them seems like a good idea so we can "open-source" the difficult bits of getting our system running.  If we used the wikiedia style wiki I could "watch" pages to do with my hardware configuration & see what developments are being made.

Oh, and while we're at it how do I find & run the GL Gears application to test my 3D performance?  What package do I have to install?

Thanks in anticipation.

---

### Post by EvilRick on 2009-05-10
[http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.17&lang=English&rev=9.3&ostype=Linux%20x86](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.17&lang=English&rev=9.3&ostype=Linux%20x86)

If you read that link, you'll see that ATI has moved your card to "legacy" support.  I don't think there's anything that the distros can do.  The fix will have to come from ATI, which I doubt it does.  I had installed 9.04 without doing my homework and ended up going back to 8.10.  I have an X800 Pro myself and I feel your pain.

"glxgears" and "fgl_glxgears" will test your 3D performance.  I don't think "fgl_gears" will work in 9.04 since your card won't support fglrx with the default drivers.

---

### Post by Yellow Pasque on 2009-05-10
The 3D performance of the open-source drivers isn't nearly as good as the fglrx driver (but 2D performance and stability are generally better).

> If not what's the actual reason why it breaks in 9.04 vs 8.10? What changed?Catalyst 9.3 won't work in Jaunty because it uses Xserver 1.6.x

> Oh, and while we're at it how do I find & run the GL Gears application to test my 3D performance? What package do I have to install?

glxgears is not a real good benchmark. Nevertheless, it's in the mesa-utils package, which should be installed by default. Just type *glxgears* in the terminal.

---

### Post by Megamanic on 2009-05-10
> **Temüjin said:**
> The 3D performance of the open-source drivers isn't nearly as good as the fglrx driver (but 2D performance and stability are generally better).

Yeah, 2D's fine but I want my Civilization IV !!!

> **Temüjin said:**
> Catalyst 9.3 won't work in Jaunty because it uses Xserver 1.6.x
Ah, that makes sense.  Thanks for that.  Looks like I'm going to be burning my 8.10 Ubuntu Studio image tonight & reinstalling :(

Is there anyway I can mark the XServer packages as "do not update"?  Otherwise is it going to be like "Windows update" forever offering me an update that I don't want to install with the attendant risk that one day I'll sleepily click on the OK button & hose my system...

> **Temüjin said:**
> glxgears is not a real good benchmark. Nevertheless, it's in the mesa-utils package, which should be installed by default. Just type *glxgears* in the terminal.
I know it's not the greatest benchmark but it's just I couldn't see the option & I'm enough of a newbie not to be able to find it.  The penguin racing game just tears up all over the screen & I can't se a thing

---

### Post by Yellow Pasque on 2009-05-11
Ubuntu 8.10 won't get Xserver 1.6, so no need to lock it, but if you really wanted to, you could do that in Synaptic ('Package' menu, 'Lock Version')

---

### Post by Megamanic on 2009-05-11
> **Temüjin said:**
> Ubuntu 8.10 won't get Xserver 1.6, so no need to lock it, but if you really wanted to, you could do that in Synaptic ('Package' menu, 'Lock Version')

Excellent, thank you.

Given that we're relying on ATI to add support for a "legacy" driver (unlikely) is anyone applying pressure to ATI to hand over documentation of the legacy stuff to the community so the XOrg folk can improve the open source driver?  I mean if the tech is so old they don't want to include it it shouldn't be a huge state secret anymore & they could get kudos with the open source community for very little effort on their part.

Ideally of course they'd open-source catalyst, which is highly unlikely.  Secondly they could open-source the stuff they've just deleted from catalyst which might not be much help or even practical.  The third option that I'm suggesting is that they publish the interface specs and internal documentation of the legacy graphics cards.  That would make writing an open-source driver much easier without "giving away the house"  Also, somewhat ironically it would mean you'd have better support for a 4yo card than a 1yo one but would set a useful precedent for future handling of legacy hardware.

---

### Post by ssri on 2009-05-11
> **Megamanic said:**
> Excellent, thank you.
Ideally of course they'd open-source catalyst, which is highly unlikely.  Secondly they could open-source the stuff they've just deleted from catalyst which might not be much help or even practical.  The third option that I'm suggesting is that they publish the interface specs and internal documentation of the legacy graphics cards.

Well, ATI released 3D documentation for R6xx/R7xx series this past week, along with R5xx's couple of months ago.  We have to realize that it is highly unlikely there is an army of devs working night and day on bringing up the opensource drivers up to speed fairly quickly.  All we can do is just sit and wait.  I just wish that ATI/AMD waited till the opensource drivers were close or matched the performance of their proprietary drivers before axing a good number of their recent cards/chips.

---

### Post by Megamanic on 2009-05-11
> **ssri said:**
> Well, ATI released 3D documentation for R6xx/R7xx series this past week, along with R5xx's couple of months ago.  We have to be realize that it is highly unlikely there is an army of devs working night and day on bringing up the opensource drivers up to speed fairly quickly.  All we can do is just sit and wait.  I just wish that ATI/AMD waited till the opensource drivers were close or matched the performance of their proprietary drivers before axing a good number of their recent cards/chips.

That's good of them - that's as much as I was hoping for actually.  Just knowing that the information is "out there" for the Xorg people to use is good enough.  I'm realistic enough to know that driver writing is very hard & people aren't being paid to do this stuff.  I remember vaguely that Shuttleworth had set up a site where you could contribute to getting bugs in linux fixed.  Is the ATI driver issue there so I can add my 5c

---

### Post by markbuntu on 2009-05-11
Ati has a few full time employees working on the open source ati and radeon drivers alongside the people in the community. accelerated 2D is working for all cards and 3D for everything up to the RV500. 3D for the RV600 (3xxx series) and RV700 (4xxx series) is expected in a few months. There is continuous improvements in the open source drivers but not necessarily in the distros.

That said, a lot of people using older cards with the latest open source ati and radeon drivers report very good performance, sometimes superior to the proprietary driver.

FYI, ATI has also dropped all those cards from future windoze drivers as well. They will be providing some bug fixes for past windoze distros but nothing new. According to them they will not be supporting those cards in any OS released after Feb/09. 

In other words, no new drivers for W7 for those cards Keep an eye out for a lot of very cheap used pcs and graphics cards when w7 comes out.

We get always improving open source drivers, they get nothing.
That is something to feel good about.

---

### Post by crchtiger on 2009-05-11
i have an onboard ati X1200 and when i tried to upgrade to jaunty i received a warning that the drivers i am using (restricted) are no longer supported
now i am wondering if i should go ahead and give it a try to upgrade and see what happens or install an nvidia 8400 GS card that i have around here
any suggestions?

---

### Post by Thanatios on 2009-05-11
Correct me if I'm wrong, but after reading this I kind of realized that the 2 days I've spend trying to get my Nvidia Riva TNT2 videocard to work was a waste of time..

And come to think of it, that I wanted to get it to work with a dual screen using an old on-board intel videocard.

Well, it does make me wonder, if its possible to get that to work on Ubuntu 8.04 with compiz on 1 screen? 

Just a question

---

### Post by Megamanic on 2009-05-12
> **markbuntu said:**
> Ati has a few full time employees working on the open source ati and radeon drivers alongside the people in the community. accelerated 2D is working for all cards and 3D for everything up to the RV500. 3D for the RV600 (3xxx series) and RV700 (4xxx series) is expected in a few months. There is continuous improvements in the open source drivers but not necessarily in the distros.Thanks for that - even better than I hoped.

> **markbuntu said:**
> That said, a lot of people using older cards with the latest open source ati and radeon drivers report very good performance, sometimes superior to the proprietary driver.Now, I've seen this meme before but I've not found any evidence in the form of xorg.conf parameters.  Is there a website where you can get suggestions?  I'm really wary of monkeying around with my x configuration.  That's been the biggest source of pain for me over the last ten years of playing with Linux on & off.  Also, given what happened when I accidentally installed the 9.4 fglrx on my system you can understand why I want to avoid it if I can.  Especially given that we're talking about a laptop there should be one x configuratiion that will work on the whole production run.  All I have to do is find it.  Oh, another thing - because it's a laptop keyboard the way I get to the Printscreen key is to use the FN key & that doesn' work because I guess I've got the wrong keyboard specified so I can't use the ALT PRTSCRN various character invocations to kill my x session if it blows up so I can't experiment as easily as I'd like...

---

### Post by night-wing on 2009-05-12
> **markbuntu said:**
> According to them they will not be supporting those cards in any OS released after Feb/09. 


But my ATI X1250 is one of the legacy cards listed above and it works great in Windows 7!

---

### Post by Megamanic on 2009-05-12
> **night-wing said:**
> But my ATI X1250 is one of the legacy cards listed above and it works great in Windows 7!

Yep, and AFAIUI you´ve given M$ the right to delete any file on your computer they choose to by clicking through the EULA - good luck with that.

---

### Post by Visserys on 2010-03-22
If you want to get the legacy cards to work on ubuntu 9.04 such as the x1400, follow this guide. It works on my ATI x1400(r500) card.

[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

It WORKS only on Ubuntu 9.04 not anything higher then that(9.10, 10.04)

Hope it helps

---

