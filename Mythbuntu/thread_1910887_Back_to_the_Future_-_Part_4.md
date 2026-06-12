---
title: "Back to the Future - Part 4"
date: 2012-01-17
forum: Mythbuntu
---

### Post by jlp_engineer on 2012-01-17
I need drivers from the future, but I want to use them in the past...

OK, well maybe not quite...let me explain.

I have been an enthusiastic supporter of Mythbuntu for years.  I started with version 8.10 back in 2008.  I had three PVR-150's on an Intel WASP 875 based system, with a 3.2GHz P4, with 2 Gigs of memory that I bought for about 250 bucks.  Not too bad for a media server on the cheap.  Time rolls on, and the system does well for almost 3 years.  Along comes the Missouri river floods of 2011.  Since my home was located less than a mile from the river, and flood waters ended up only a few hundred yards from my front steps, we had to remove a lot of stuff from our house, which included the server running Mythbuntu.  

Fast forward several months later...

I decided to re-install the server, add some digital tuners, and start over with clean installs of Mythbuntu 11.10. 

Problem 1 - Version 11.10 will not boot on the Intel WASP 875 board I have (Locks up on "Kernel Thread Helper".  Went back to version 11.04.  Problem solved for the moment.  

Problem 2 - Since the Intel WASP board has five PCI slots, I filled them up with three PVR-150's, one pcHDTV HD-5500, and one ATi HDTV Wonder card.  One or more of the PVR-150's would not work or worked unreliably.  Turned out to be a bad PVR-150.  Casualty of the move due to the flooding, I guess.  Replaced card...problem solved. 

Problem 3 - I successfully installed version 11.04, and began setting up the tuners, and to my surprise, scanning for channels with the analog tuners no longer worked.  But scanning for digital channels worked fine.  OK, so I had to set up the analog channels in the channel editor manually.  Problem solved.

Problem 4 - When I watched live TV with one of the PVR-150's, the default channel would appear.  I could even change channels up and down without trouble.  However, when I switched inputs to one of the other PVR-150's, I would get distorted video, stutters, and sometimes a blank screen, followed by an error moments later about video frame buffering failed too many times or something about a jump program file buffer.  Went back in time to version 10.10, same issues.  Went back to 9.10, same thing.  Only when I loaded version 8.10, did this issue go away.  Problem solved. 

Problem 5 - I then loaded up one of the Zotac MAG ION based systems I have been planning on using as a frontend for about a year.  Once I loaded up version 8.10 on it, I learned two things.  The ION chipset is not recognized at all...by anthing, and VDPAU, which I planned on utilizing, was not incorporated into MythTV until version 0.22.  Problem - not resolved. :cry:

So now I am stuck with a frontend I cannot use because the software I loaded is so old it will not properly recognize the video chip.  Even if I somehow managed to load the latest drivers, MythTV version 0.21 does not support VDPAU, so it really doesn't matter. ](*,)

What is your opinion?  :-k

Should I wait for the channel changing issue in 11.04 to be resolved, and then load up everything with 11.04?  This seems less and less likely everyday, since analog support seems to be atrophying due to lack of attention and the belief that it will no longer be necessary due to the switch to digital.  Well, some of us "farm boys" in the rural areas have still analog cable, and will for a long time, so analog support is still important, at least to me. :neutral:

Should I wait for the next release of Mythbuntu, and hope that the boot issue with my servers is resolved? [-o< I have two Intel WASP based systems now.  During my troubleshooting, I split up the analog and digital tuners.  Made sense at the time.  But now I have more money invested in hardware, that I may not be able to use going forward.  I really don't want to shell out 1000's of dollars, on new servers, new tuner cards, etc.  That would be a hard sell to the wife. [-(

Can I run version 10.10 Mythbuntu on backends that are running version 8.10, or am I going to get a data base schema error? :???:

Or should I just install the flux capacitor and get the server up to 88 miles per hour??? :)

---

### Post by klc5555 on 2012-01-18
Mythbuntu 10.10 runs Mythtv 0.23.1.  Mythbuntu 8.10 ran Mythtv 0.21. Trying to connect the two either ends the universe, or worse, gives you a protocol mismatch error.


Perhaps the most workable solution will be not to use Mythbuntu at all on the remote machine, but rather to try a combination of Xubuntu + Mythtv.

Though version-mismatched hybrid Mythtv+Ubuntu systems **_*are not supported*_**, it is known that the .deb files for particular versions of Mythtv will install and function on a narrow range of Ubuntu releases.

In your case, it might be worthwhile to determine the **earliest** Xubuntu release that properly supports your hardware. This would appear to be (hopefully) Xubuntu 10.04 (or possibly 10.10, or 11.04.) You would install and run this Xubuntu version on your remote machine, in tandem with a correct earlier version of Mythtv.

If you have decided to keep your backends on 8.10 for the sake of the tuners, this means Mythtv 0.21, protocol 40. It is known that the Mythtv 0.21 .deb packages from Ubuntu 9.04 run fine on Xubuntu 10.04. For a couple of months I was also running a laptop remote frontend on Xubuntu 11.04 but with Mythtv 0.21 connecting to an old backend running Mythbuntu 9.04. 

However, Mythtv 0.21 debfiles from 9.04 are hard to find, given the Ubuntu community's predilection for sweeping older versions from the face of the earth. I have never tried using the older 0.21 debs from Ubuntu 8.04 or 8.10. There may be issues with these older debs on Xubuntu 10.04 or later. And, of course, this is **Not Supported**, but at this point, what do you have to lose?

Find the 3 critical mythtv .deb packages: mythtv-common, mythtv-frontend, and mythtv-backend for Mythtv 0.21. If your Xubuntu machine is intended to be a remote frontend only, you will not need to install mythtv-backend (and the machine will run better without it).   Use gdebi or similar to install the 2 (or 3) mythtv 0.21 packages onto your installation of Xubuntu. There will be 3 or 4 little dependency packages that will need to be dragged along and installed also.

If your Xubuntu machine is a remote frontend-only machine, open a prompt, run "mythfrontend" and configure the resulting screens to connect to your master backend. Voila! 

If your Xubuntu machine is also a slave backend (and you accordingly installed the debfile "mythtv-backend"), you begin configuring this slave backend to connect to the master backend by running "sudo mythtv-setup".

If this hybrid setup is functioning, you lock the two (or 3) mythtv packages in synaptic, so that the upgrade mangler doesn't try to upgrade them on a daily basis. You can also add the window dressing packages such as the mythtv 0.21 extra themes, and plugins.

Good luck!

---

### Post by jlp_engineer on 2012-01-18
I think I would rather see if the analog channel change bug will be fixed in 0.24.x any time soon.   That might be worth waiting for.  Does anyone know if the analog channel change issue (the one that is in the bug tracker [http://code.mythtv.org/trac/ticket/9177]("http://code.mythtv.org/trac/ticket/9177") ) is the same as what I am seeing?  

My issue doesn't have anything to do with HD content or digital tuners, since the PVR-150's are all isolated in their own backend.  I have read a few of the MythTV bug reports and they seem to be ONLY linked to a combination of analog and digital tuners, but maybe I am thinking about only the work-a-round.  It also seems that my issue is not quite the same, since the first tuner that comes online, which is an analog SD tuner (the aforementioned PVR-150) tunes the first channel just fine, and any subsequently tuned channel.  My issue only happens when I switch to a different analog tuner.  Also, tuning with a digital tuner first does not provide a work-a-round to my issue.  I am wondering if I should submit some logs or data to the ticket, if my issue is related.  

If there is another cause for this issue, can someone provide a link to the possible causes? :confused:

If I could find the source code for v0.21, I might even take a look at it myself, to see if I could fix it in 0.24.  I am no programmer, but I have customized some C code and done some assembler many years ago, and I am stubborn when I am working on an issue (not my best quality). [-(

---

### Post by klc5555 on 2012-01-18
By all means contribute to the ticket, if you have relevant data --it doesn't look like there's been activity on it for 7 months or so.

Source code back to Mythtv 0.10 is, of course, available here: [ftp://ftp.osuosl.org/pub/mythtv/old_releases/](ftp://ftp.osuosl.org/pub/mythtv/old_releases/)

With the operational life of most PC hardware set at 3-6 years before obsolescence, it's probably futile to sit back and just not use your hardware for a very appreciable chunk of time in the hope of a particular Mythtv analog bug being fixed prior to or even with the release of Mythtv 0.25. Analog tuner issues (like scan) are bound to attract ever less attention over time as these devices become increasingly less current. And in 3 years who knows whether a Zotac MAG Ion box will still be considered worth the electricity needed to fire it up. So I'd recommend solutions that get your hardware in use sooner, rather than later. Even if not perfectly.

Just my 2 cents.

---

### Post by nickrout on 2012-01-18
I would add that you may get more knowledgeable responses on the mailing list (not trying to demean klc555, but there are far more knowledgeable people there, including developers.)

---

### Post by jlp_engineer on 2012-01-18
> **klc5555 said:**
> By all means contribute to the ticket, if you have relevant data --it doesn't look like there's been activity on it for 7 months or so.

Thanks - I will do that.  Who knows, maybe it will be just what they need. :-)

---

### Post by jlp_engineer on 2012-01-18
> **nickrout said:**
> I would add that you may get more knowledgeable responses on the mailing list (not trying to demean klc555, but there are far more knowledgeable people there, including developers.)

Nick - Thanks for the suggestion.  I believe I will do just that.  Just to see what comes back.  There is bound to be someone else out there stuck in "Analog Land" like I am.

---

### Post by heshoots67 on 2012-01-18
Do you have Flood Insurance.

---

### Post by jlp_engineer on 2012-01-19
> **heshoots67 said:**
> Do you have Flood Insurance.

Yes, but flood insurance only pays if you have flowing water damage (above ground) to your home.  Most of the trouble homes in our area had was due to ground water flowing up through the cracks in the basement cement.  There is no insurance that I am aware of that pays for that.  :(

---

