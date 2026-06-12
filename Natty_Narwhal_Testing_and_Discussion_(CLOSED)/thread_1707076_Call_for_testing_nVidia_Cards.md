---
title: "Call for testing: nVidia Cards"
date: 2011-03-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by cariboo on 2011-03-14
I just received this email:

> Hi All,

Do you have a *nVIDIA* graphics card? Do you want to help ensure users
have a smooth experience if they choose to use the proprietary drivers?

We are looking for committed volunteers to test nVIDIA proprietary
drivers on a weekly basis. The goal of this testing is to catch
regressions and fix bugs before they reach a major audience.

If you want to be part of the team you will need:

 1. A computer with an nVIDIA (GeForce 7 or newer) graphics card
 2. A spare partition on that system
  * If you don't have a spare partition you can easily create one.
 3. One hour of your time per week
 4. An Internet connection

If you want to take part in this adventure, go to:
  [https://wiki.ubuntu.com/X/Testing/ProprietaryDrivers/Natty/WeeklyProgram](https://wiki.ubuntu.com/X/Testing/ProprietaryDrivers/Natty/WeeklyProgram)
and follow the detailed instructions.

No time to lose, the first results will analysed by Wednesday!

We will coordinate testing in #ubuntu-testing on freenode. Please, go
there often to see what others are testing or what needs to be tested.

Thanks for helping making Ubuntu even better!

P.S. This project is to test the proprietary drivers. If you're
interested in testing the free drivers, we don't need installation
testing but help is always welcome. Check how at the Ubuntu X team page [1].

[1] [https://launchpad.net/~ubuntu-x-swat](https://launchpad.net/~ubuntu-x-swat)

-- Jean-Baptiste irc: jibel 

---

### Post by squaregoldfish on 2011-03-15
Oddly, the instructions linked to also state that they're looking for ATI users too. I wonder why the email only mentioned nVidia.

Steve.

---

### Post by gnomeuser on 2011-03-15
Could we get the title changed to something like "Call for testing: nVidia and ATI Cards on proprietary drivers" and made sticky. It seems like a worthy cause.

---

### Post by MacUntu on 2011-03-15
Why hasn't this been posted to ubuntu-announce/ubuntu-devel?

---

### Post by ratcheer on 2011-03-15
I used to be on that team (for Lucid, I think). Also, I'm supposed to be getting a new nVidia 430GT card any day now. It could be fun to participate again.

Tim

---

### Post by dnewkirk on 2011-03-15
I just install natty to help test the nvidia drivers, and after a slight hiccup with attempting to use XFS instead of ext4 (aborted and used the default install essentially), the install went smoothly. So far, the nvidia drivers are working fantastic on this machine, no issues whatsoever. Pretty impressive (upcoming) release to be honest, Unity and all.

---

### Post by vishalrao on 2011-03-16
Wooo, awesome, great to see some love given to the proprietary drivers, unlike certain other F-*@%$@#& distros that shall remain unmentioned :lolflag:

I won't be able to participate as a "committed volunteer" due to time constraints, but I can do as a "casual volunteer" - will spend time on this during weekends and maybe report bugs to Launchpad.

I have an NV 8800GT/512mb on my desktop and an onboard "GeForce 6150 Go" on my HP Pavilion tablet.

---

### Post by vishalrao on 2011-03-17
Just updated a few hours ago, and everything is mostly stable.

Some compiz crash when selecting/deselecting either the "coverflow/ring switcher" plugin, though the actual effects work fine :)

Plymouth logo does not show (just dots) during shutdown, but all else is fine.

Loving the wobbly window animations and the nvidia settings applet UI is way better including I think proper VSync=ON everywhere, so the compiz effects have no tearing.

Natty is looking to be, again, the sweetest Ubuntu release yet!

---

### Post by webme on 2011-03-17
> **vishalrao said:**
> 
so the compiz effects have no tearing.


Is it something different in speed compared to the "regular" Natty (from the new NVIDIA point of view)?

---

### Post by vishalrao on 2011-03-17
I won't be able to reliably do a speed comparison even if I ran any demos/benchmarks it would just be a single reference point - for such stuff, I bet we will get the info from sites like phoronix :-)

---

### Post by webme on 2011-03-17
> **vishalrao said:**
> I won't be able to reliably do a speed comparison even if I ran any demos/benchmarks it would just be a single reference point - for such stuff, I bet we will get the info from sites like phoronix :-)
No, I mean with your eyes, not like a benchmark, I was wondering if this new NVIDIA drivers could be the ending of flickering and tearing  in Compiz animations!

---

### Post by vishalrao on 2011-03-18
Oh :) Well my eyes could be playing tricks on me, but the tearing is definitely noticeably reduced, if not altogether eliminated!

---

### Post by thiebaude on 2011-03-18
No problems with my nvidia 8400 gs on Ubuntu 11.04

---

### Post by MacUntu on 2011-03-19
> **thiebaude said:**
> No problems with my nvidia 8400 gs on Ubuntu 11.04

Please read the first posting and follow the instructions. Posting any results here is a waste of your time.

---

### Post by dino99 on 2011-03-19
if user dont install video=all, then xorg.log complaint about those missing driver not installed. This is only warnings but they might not exist if user like me dont care about unneeded drivers such as nv or vesa for example.

---

### Post by theanswriz42 on 2011-04-03
Doesn't seem to be working with my Nvidia 330m card

---

### Post by cariboo on 2011-04-03
@theanswriz42 Did you follow the instructions on the QA page, and fill in all the reports?

Saying it doesn't work here, doesn't help very much.

---

### Post by theanswriz42 on 2011-04-03
> **cariboo907 said:**
> @theanswriz42 Did you follow the instructions on the QA page, and fill in all the reports?

Saying it doesn't work here, doesn't help very much.

I didn't, but I'll check it out.

Cheers

---

### Post by Dlambert on 2011-04-04
Doesn't work at all, wont even boot. Gts 450, i do not want open source drivers.

---

### Post by defconoii on 2011-04-15
video remains choppy when playing quakelive with compiz effects enabled, when logging into ubuntu classic no effects the issue is fixed

---

### Post by Flymo on 2011-04-18
No luck with our laptop - nVidia GeForce Go 7600 mobile graphics with intel T5600 cpu & 2GB RAM,

Natty Live CD  <eventually>  boots into what looks like Gnome - no Unity, anyhow.  

"Additional Drivers" reports that there is nothing.

Same result with both AMD64 & i686 ISOs.  Same i686 CD boots fine on Celeron 540 laptop with intel X3100 graphics.

T5600 laptop has had Compiz running on each Ubu release since 7.10. Weird.

Ben

---

### Post by jdrodrig on 2011-04-20
> **cariboo907 said:**
> I just received this email:

I just don't get it, developers don't have time to post this message themselves in UBUNTUFORUMS? Passing down emails is not an efficient way of doing this.

---

### Post by cariboo on 2011-04-20
> **jdrodrig said:**
> I just don't get it, developers don't have time to post this message themselves in UBUNTUFORUMS? Passing down emails is not an efficient way of doing this.

I just forwarded the email, to get more people involved, normally it's just people that subscribe to the ubuntu-devel mailing list that would have seen the notification.

---

### Post by 3rdalbum on 2011-04-20
> **Flymo said:**
> No luck with our laptop - nVidia GeForce Go 7600 mobile graphics with intel T5600 cpu & 2GB RAM,

Natty Live CD  <eventually>  boots into what looks like Gnome - no Unity, anyhow.  

"Additional Drivers" reports that there is nothing.

You might need to update the package list. (go into Synaptic Package Manager and click the Reload button).

> Same result with both AMD64 & i686 ISOs.  Same i686 CD boots fine on Celeron 540 laptop with intel X3100 graphics.

T5600 laptop has had Compiz running on each Ubu release since 7.10. Weird.

Ben

Not weird. Unity only works with 3D acceleration. Intel 3D drivers come with Ubuntu because they are open-source. Your Nvidia card has a preinstalled 2D driver in Ubuntu, but no 3D by default so Unity won't run yet. If you update your package list, Additional Drivers will offer the experimental Nouveau 3D acceleration and the Nvidia binary driver.

Nouveau 3D works okay for Unity, but I had a couple of problems with it.

---

### Post by IanW on 2011-04-21
[Phoronix]("http://www.phoronix.com/scan.php?page=news_item&px=OTM1NA") are reporting a new Nvidia blob in the 173 series.

173.14.30 adds support for xserver 1.10 & kernel 2.6.38, but is not yet in the repos.

---

### Post by ratcheer on 2011-04-21
> **IanW said:**
> [Phoronix]("http://www.phoronix.com/scan.php?page=news_item&px=OTM1NA") are reporting a new Nvidia blob in the 173 series.

173.14.30 adds support for xserver 1.10 & kernel 2.6.38, but is not yet in the repos.

I saw it in the Natty change notifications, this morning. If its not already available, it should be very soon.

Tim

---

### Post by ds_shellback on 2011-04-24
Hi,

Reading #24 this infers that you can't try Unity in live mode?

I tried and installed 11.04 on an Intel graphics system but when I tried the live CD on another system with an nVidia FX5200 Graphics Card all I got was the Gnome desktop! Do I need to install it on this machine before I can get unity?

Why is the nv driver not loaded from the live CD?

---

### Post by rondackcpu on 2011-04-24
My computer has a PNY GeForce5200 video card in it -- old, maybe ancient -- and it will not boot the ISO I downloaded as recently as today.  The complaint as the ISO is trying to boot is that it cannot find the 5200 chip.  Other posters indicate that they have been able to install Natty on machines with the 5200.

Any ideas why mine will not boot the ISO and therefore not install Natty?  Is this the end of the line for that video card?  Maverick runs nicely on that machine with dual monitors.

Any ideas would be appreciated.

CRS

---

### Post by cariboo on 2011-04-24
You could try enabling nomodeset from the Live CD menu. Press the any key when you see the initial screen, then press F6 and select nomodeset. Press esc and then press enter.

---

### Post by ds_shellback on 2011-04-24
Mine boots the ISO ok with the FX5200, but always shows the Gnome desktop - _NO_ Unity :(

---

### Post by cariboo on 2011-04-24
This thread wasn't started for people with graphics problems, it is asking people to test the nouveau drivers following a certain procedure, as linked to in the first post. If you have a problem with nVidia graphics, please start a new thread.

---

### Post by matthewbpt on 2011-04-25
> **cariboo907 said:**
> This thread wasn't started for people with graphics problems, it is asking people to test the nouveau drivers following a certain procedure, as linked to in the first post. If you have a problem with nVidia graphics, please start a new thread.
> P.S. This project is to test the proprietary drivers. If you're
interested in testing the free drivers, we don't need installation
testing but help is always welcome. Check how at the Ubuntu X team page [1].

It's not asking people to test the nouveau driver, it's asking them to test the proprietary driver.

---

### Post by defconoii on 2011-04-25
multi-monitor support is broken on the nvidia 9600GT, with no panel, no unity, fullscreen apps wont fullscreen, any idea if this will be fixed before release?

---

### Post by cariboo on 2011-04-26
> **matthewbpt said:**
> It's not asking people to test the nouveau driver, it's asking them to test the proprietary driver.

You're right, that's what I get for answering a post, after I've been up all night. :)

---

