---
title: "Machine Check Exception"
date: 2011-10-10
forum: Mythbuntu
---

### Post by bah1976 on 2011-10-10
Ok gurus - I've had a 8.04 system running stable for quite awhile, and last night it started rebooting repeatedly on me.  I finally managed to catch this while it boots - can somebody point me in the right direction?  Or, at least confirm that this is likely to be RAM that has gone belly up?  

I've got 4 hours before monday night stuff starts recording...

Oh - and it rebooted before I could do the mcelog --ascii, although I'll keep trying.

---

### Post by bah1976 on 2011-10-10
Not RAM...  That's been replaced.

---

### Post by nickrout on 2011-10-10
> **bah1976 said:**
> Not RAM...  That's been replaced.

Type the error message into google and you will see many hits, most of which I didn't follow up, but you should.

---

### Post by bah1976 on 2011-10-10
So, it's either the video card or driver.  It probably started with the card, but when I tried to update the driver, that failed too.  Nvidia 6200 LE.

Running with gdm disabled, the box stays up.  But mythbackend won't start because the nvidia installation crashed in the middle, and now I've got 

/usr/bin/mythbackend: error while loading shared libraries: /usr/lib/libGL.so.1: invalid ELF header

---

### Post by bah1976 on 2011-10-10
I was able to install the nvidia driver, and get mythbackend started, but I'm not going to try X until the nightly recording schedule is over - in case it bombs like it has every other time...

---

### Post by klc5555 on 2011-10-11
In my experience, spontaneous reboots on a system that has been stable for a long time are usually traceable to a power supply that is falling out of spec in preparation for failing outright. The rebooting happens when the system goes under additional load, like when X and the graphics adapter start up. 

For home built systems, power supplies that come bundled with cases are notoriously poor, and often fail at the 2-3 year point. Unstable power supplies tend to mimic a variety of CPU/memory errors. Failing video cards, on the other hand, tend to lock up systems, requiring hard resets.

---

### Post by Johnb0y on 2011-10-11
> **klc5555 said:**
> In my experience, spontaneous reboots on a system that has been stable for a long time are usually traceable to a power supply that is falling out of spec in preparation for failing outright. The rebooting happens when the system goes under additional load, like when X and the graphics adapter start up. 

For home built systems, power supplies that come bundled with cases are notoriously poor, and often fail at the 2-3 year point. Unstable power supplies tend to mimic a variety of CPU/memory errors. Failing video cards, on the other hand, tend to lock up systems, requiring hard resets.

+1

had something similar a few weeks back, radom rebooting, at one point it wouldnt boot up, i had to remove the power pack - put it back - switch plug points till it came on... then i decided enough was enough, got some RAM replaced (time to do so anyway), and Changed my power supply for a meaty performance one and eveything seems great now.

---

### Post by thatguruguy on 2011-10-11
> **Johnb0y said:**
> +1

had something similar a few weeks back, radom rebooting, at one point it wouldnt boot up, i had to remove the power pack - put it back - switch plug points till it came on... then i decided enough was enough, got some RAM replaced (time to do so anyway), and Changed my power supply for a meaty performance one and eveything seems great now.

This.  Random, repeated reboots can often be traced to a bad power supply.

---

### Post by bah1976 on 2011-10-11
Thanks for the input folks.  A PSU will be my next replacement.  Dumb thing is, I almost bought one when I was picking up the RAM, but I hate paying best buy prices for components (my only local choice) so I didn't.

---

### Post by klc5555 on 2011-10-11
> **bah1976 said:**
> Thanks for the input folks.  A PSU will be my next replacement.  Dumb thing is, I almost bought one when I was picking up the RAM, but I hate paying best buy prices for components (my only local choice) so I didn't.

Nowadays, when I have case-bundled or other cheap power supplies blow, I've gotten to the point where I replace them only with PC Power&Cooling power supplies. A bit pricier to be sure, but in nearly twenty years I've never had one fail.

Good luck.

---

### Post by bah1976 on 2011-10-11
1) It wasn't a case bundle, it was an antec earthwatts supply from a couple years ago.  Not sure if that changes anything or not...
2) I've put in a PSU from a new computer I just built, temporarily, and the errors continue.  So I'm not so sure it's the PSU after all.

In addition to the MCE, I'm getting a CPU frequency error sometimes before it posts.  Do CPUs go bad?  I'm pretty sure it's this one:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103776]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103776")
I read somewhere in my googling in the past 24 hours something about bad capacitors on the MB - any thoughts in that direction?

I really don't want to replace every single piece one at a time - that's money I don't have...

---

### Post by bah1976 on 2011-10-11
frak!  now I'm seeing stuff about cmos batteries and bad contact between cpu & fan.  too many possibilities here...  I'd really appreciate any solid tips.

---

### Post by klc5555 on 2011-10-11
> **bah1976 said:**
> frak!  now I'm seeing stuff about cmos batteries and bad contact between cpu & fan.  too many possibilities here...  I'd really appreciate any solid tips.

When CMOS batteries go bad, the usual symptom is that the PC reverts to default factory BIOS settings between boots. Not really your symptom. 

CPUs don't generally go bad, though they can overheat. Look to see whether the CPU cooler fan is actually running. Go into the "PC Health" screen (or similar section) of your Bios hardware setup and let the machine run there for a while, while you see if the indicated CPU temperature is rising to and above the documented threshold for your CPU. Also check the space >between< the top of the CPU heat sink and the bottom of the CPU fan. Particularly if you have a pet in the house(or if the computer sits near the floor), over time the top of the heatsink can and does get a nearly impermeable layer of pet hair, dust, fuzz and gunk that looks like and works like a little flannel thermal blanket for your CPU, and prevents any of the CPU heat from making it past the heat sink to the fan to be dispersed. This layer of schmutz needs to be gently removed.

Finally, voltage regulation circuitry on the motherboard can and does fail from time to time. But generally in this case the symptom is that the system simply won't boot even to the point of starting the POST, though the lights light and the fans spin. In such a case it's almost always better just to replace the MoBo with one that uses the same CPU and DRAM values rather than attempt a repair. But I don't think this particular failure is your hardware problem.

---

### Post by bah1976 on 2011-10-11
> **klc5555 said:**
> When CMOS batteries go bad, the usual symptom is that the PC reverts to default factory BIOS settings between boots. Not really your symptom. 

CPUs don't generally go bad, though they can overheat. Look to see whether the CPU cooler fan is actually running. Go into the "PC Health" screen (or similar section) of your Bios hardware setup and let the machine run there for a while, while you see if the indicated CPU temperature is rising to and above the documented threshold for your CPU. Also check the space >between< the top of the CPU heat sink and the bottom of the CPU fan. Particularly if you have a pet in the house(or if the computer sits near the floor), over time the top of the heatsink can and does get a nearly impermeable layer of pet hair, dust, fuzz and gunk that looks like and works like a little flannel thermal blanket for your CPU, and prevents any of the CPU heat from making it past the heat sink to the fan to be dispersed. This layer of schmutz needs to be gently removed.

Finally, voltage regulation circuitry on the motherboard can and does fail from time to time. But generally in this case the symptom is that the system simply won't boot even to the point of starting the POST, though the lights light and the fans spin. In such a case it's almost always better just to replace the MoBo with one that uses the same CPU and DRAM values rather than attempt a repair. But I don't think this particular failure is your hardware problem.

The CPU fan is running, and the heat sink is cool to the touch.  There's a little dust on the top of the fins, but not enough to create a thermal barrier.  I will clean it shortly regardless.  However, what I think is the northbridge heat sink, directly on the MB, is warm, and the passive heat sink on the video card is hot - so much so that I couldn't keep my finger on it for more than a couple seconds.  Could a video card that gets too hot cause a reboot?  

To throw an additional wrench - when I first booted with this temp PSU, it rebooted on me.  I have 4 sata drives total, 1 boot and 3xraid5.  I had 2 of the raid5 plugged in, expecting it to work degraded, but when it cycled on me, I removed those so it wouldn't get any more corrupt than the past day of rebooting has already done.  So far, it hasn't rebooted.  Could something along that path be an issue?  I'm starting to think I should get A+ certified just to keep my stuff running...

---

### Post by bah1976 on 2011-10-11
PC Health Status report - CPU temp averages 30C.  Occasional spikes to ~45, but only for one "tick" - next update is back below 30.

---

### Post by bah1976 on 2011-10-11
Well, it's not directly related to the three disconnected drives.  I have gdm disabled so I can boot to a console.  When I try to start gdm, it boots.  I'm back to thinking bad video card.  Does that make sense to you, klc5555?

Crap.  While typing this, and running mythfilldatabase from the console, it booted...

It'll sit all day at the console without doing anything.  But as soon as I try to do anything, it croaks.  mythfilldatabase - croak.  startx - croak.  start gdm - croak.

---

### Post by klc5555 on 2011-10-11
Well, I confess that I've had an awful lot of trouble with NVidia 6200 series cards, particularly the fanless ones. But their usual symptom is to freeze the desktop with the last image frozen on the screen, requiring hard reset. Shouldn't cause a reboot, much less from a console. But I suppose it wouldn't hurt to swap in some card on the open source drivers, if you've got an old card sitting around in a junk drawer.

System drive issue maybe? (Stretching a bit here.) Can you do reasonable stuff after booting from an Xubuntu live CD, without accessing the system drive, or does the machine reboot from there, too?

---

### Post by bah1976 on 2011-10-11
Never thought about the live cd...  First time I tried, it booted as soon as the "loading linux kernel" bar finished.  Second time I tried, it went all the way to the live desktop.  my vga connected monitor was ok, but the svideo tv was garbled.  I'm going to try and reset my xorg config and see what happens.

I don't have any spare PCI express video cards - i have a bunch of AGP but that doesn't help.

how would I know if the system drive is having a problem?

---

### Post by bah1976 on 2011-10-11
I've been getting a couple hard freezes as well - so I'm back to thinking that the video is to blame.  What's going to be the best (most pain free) way to replace this?  What kind of card will be the best to try?

---

### Post by klc5555 on 2011-10-11
> **bah1976 said:**
> I've been getting a couple hard freezes as well - so I'm back to thinking that the video is to blame.  What's going to be the best (most pain free) way to replace this?  What kind of card will be the best to try?

It should be an NVidia --ATI with its so-so driver support is still only a "plan B" choice.

If your older machine is still using AGP, then you're limited to an older-style 7400 or 7600 or below. This maybe is not a bad thing as the various 7xxx series all work more reliably than the 6200 ever did (at least for me), and I've been using a 7400 GT (AGP) on a daily basis on one machine for about 4 years. If the machine is PCI-e, then any of the more modern NVidia 8xxx or 9xxx cards ought to work better than fine. No sense spending big bucks on a cutting-edge card for three-year-old hardware. 

I don't trust fanless cards much, but that's just me.

It should just be a plug-n-play switch --you shouldn't even need to reinstall or upgrade the NVidia drivers.

---

### Post by nickrout on 2011-10-12
If you do not have PCI-e then there ARE some PCI nvidia cards that can do vdpau. Hard to find, Sparkle makes some.

---

### Post by bah1976 on 2011-10-12
So, I've replaced the RAM, PSU, and Video card.  It ran fine overnight, but whenever I do anything - it tanks.  I may be back to stretching for a system drive issue.  I still have gdm disabled so it boots to console, and it just locked about 10 seconds into mythfilldatabase.  Besides making the system drive work, what else is it doing? Can I do something like ghost to mirror onto a new system drive?  I've not done this for a linux box before.

*edit* I should add that it didn't reboot in the middle of mythfilldatabase - it locked and required a hard reset.

---

### Post by klc5555 on 2011-10-12
Since the machine rebooted on you at least once after booting from a liveCD with no system drive in play, the odds are not good that it's a system drive issue.

With PSU, RAM, and Video card already replaced, and with no demonstrable heat, cabling, RAM/card seating or other mechanical problems, about the only reasonable user-replaceable items you have left (without requiring actual electronic surgery that most home shops are not equipped for anyway) are the CPU or the motherboard. If compelled to guess, I'd say it was more likely that some passive electrolytic was breaking down on the motherboard than that the CPU was experiencing a degradation that was not a complete failure. But at this point it's all just guess work.

---

### Post by bah1976 on 2011-10-12
I hate that answer, but if that's what it takes.  Don't hate the messenger though - I appreciate the help.

---

### Post by bah1976 on 2011-10-12
Wow - didn't think finding a cheap AM2 replacement board would be that tough.  I don't really want to risk used/ebay since I'm already battling an unknown issue.  This look ok, compatibility-wise?
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813157204]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813157204")

or

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813157226]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813157226")

---

### Post by klc5555 on 2011-10-13
I don't much about currentish AMD boards --I've refused to use non-Intel boards for about 7 or 8 years.

However, since you've doubtlessly matched the board to your processor, as long as you're getting a board that's also compatible with your RAM speed and RAM pin configuration, you should be all right.  

While I like boards with onboard video (particularly since the first board's video chip could easily do HD), I also from time to time wish some of my Myth machines supported 6 SATA devices (like the second board) rather than 4, so I don't know which of the boards I'd choose if confronted with your choice.

---

### Post by nickrout on 2011-10-13
> **klc5555 said:**
> I don't much about currentish AMD boards --I've refused to use non-Intel boards for about 7 or 8 years.

However, since you've doubtlessly matched the board to your processor, as long as you're getting a board that's also compatible with your RAM speed and RAM pin configuration, you should be all right.  

While I like boards with onboard video (particularly since the first board's video chip could easily do HD),

I don't think so, that chipset does not do vdpau

[http://us.download.nvidia.com/XFree86/Linux-x86/280.13/README/supportedchips.html](http://us.download.nvidia.com/XFree86/Linux-x86/280.13/README/supportedchips.html)

---

### Post by klc5555 on 2011-10-13
> **nickrout said:**
> I don't think so, that chipset does not do vdpau

[http://us.download.nvidia.com/XFree86/Linux-x86/280.13/README/supportedchips.html](http://us.download.nvidia.com/XFree86/Linux-x86/280.13/README/supportedchips.html)

OK. But VDPAU isn't necessary for HD, unless the CPU is only marginal. I confess I don't use VDPAU myself on any of my myth machines. I'm also at somewhat of a disadvantage, not having a feel for the capability of current AMD CPUs. Are AM2's HD-marginal CPUs?

However, the OP's machine is running 8.04, implying MythTV 0.21, and so may well have never had VDPAU enabled anyway since that feature was only fully implemented with 0.22.

But you're right that if VDPAU is a must, then there's no real advantage to the first motherboard's imbedded video. Might as well have the 6 SATA risers on the second board.

---

### Post by bah1976 on 2011-10-13
Yep, 8.04, .21, and no vdpau.  frankly, I'm not entirely sure what it is. :)  I went with the second board for more flexibility, and I had a $10 newegg credit from a drive that went on sale a week after I bought it, so the cost ended up being the same.  My CPU is a brisbane 4400+, 2-core 2.3 ghz, if memory serves me right.

So - the natural next question - what will I have to do when I swap MB?  Is it PnP also?  I've never replaced a MB in a linux box.

Thanks again guys - this forum is the best.

---

### Post by klc5555 on 2011-10-14
Motherboard replacement on a Linux box is straightforward compared to the annoyance it presents on a Windows machine. Mainly because unlike Windows, Linux should still boot normally after the swap, unless some fearsomely streamlined and hardware-tweaked kernel was in use --not normally the case in a Myth machine, or unless the OS got severely corrupted by all the spontaneous rebooting, a slightly more serious possibility. 

Assuming all the mundane mechanical stuff is done, i.e. CPU & cooler moved to new board, RAM moved to new board, new board properly mounted on its case standoffs; 24-pin power, panel switches and ports, CPU fan & sensor, and all other motherboard electrical connections are in place; and a system drive and video card are connected, the unit can be fired up. If it makes it to a bios screen and the drive is detected, you can fiddle around in the hardware setup if you wish, or proceed with booting.

Depending on where the system drive was connected to the old MB as opposed to the new one, GRUB may get confused as to where the system drive is located. If so the system drive gets reconnected or you boot from a CD and redirect GRUB to the right location. Otherwise, the OS should boot mostly normally. 

X should initialize, the NVidia driver should load fine, Alsa may have to be reconfigured depending on current hardware and you may have to configure (or possibly even compile) audio chipset drivers. Mythbackend should not be able to start on its own because of the changed and incomplete hardware --if it does start, kill it.

Once all the old peripheral hardware (i.e. TV tuners) is in place and is found by the OS, and the non-system drives are all mounted in the correct directories in the file system, then you will likely have to run mythtv-setup at least to confirm whether the tuners are being assigned correctly, or re-add them if they are not.

That is pretty much all there is to it.

---

### Post by bah1976 on 2011-10-14
So, since the replacement MB won't be here until monday, I have an unrelated mythbackend question - if I were to set up a mythbackend in a vmware virtual machine on my laptop, using the hdhomerun that I have, and recording to the NAS that is part of the configured storage group on the dead backend, would it be able to run without mysql?  Or could I temporarily move the database or something?  I know I can torrent anything that I miss, but it's the principle of the thing.  

My slightly longer term plan is to compile vmware server into the slackware/unraid kernel that's running my nas, and make a primary backend VM, but I haven't gotten there yet.  There's some detailed directions that I don't have time to follow right now to make vmware server work, otherwise I'd just set that up now.  Hmm...  Talking this out, maybe I'll just make a vmware workstation primary backend, and then later move it to the unraid kernel.  So, my updated question is - how would I go about telling my dying backend to be a secondary, and make a new one (vm) be the primary?  I havne't looked yet, since this is all coming out while I type - is there documentation on how to do that?

And a follow-up question - if I'm going through all this anyway, what advantages would there be to upgrading to current mythbuntu in the process?  Might be too many changes at once to troubleshoot, I may do the upgrade later.

---

### Post by klc5555 on 2011-10-14
Can't comment on much of that: I haven't used VMWare since the '90s. And what? Your laptop isn't running Ubuntu anyway? Is that even possible?

Anyway, why get fancy just for the weekend? If you know basically what you intended to record, and if you can configure a new backend on this laptop that will access the HD Homerun (at whatever Mythtv version: the myth trappings and metadata don't matter here --you just want to end up with recordings files at the end, and these will be consistent across mythtv versions) then you should be in business.

You would install & set up a new mythtv with a brand-new unblemished mythconverg on this laptop, set up and record the necessary stuff (to whatever kind  of internal/external drive) and then, when the original machine is restored, you'd copy the laptop-recorded files over to the original machine's storage group. And since the original machine still uses Myth 0.21 (thank God) you still have the option of using the script myth.rebuilddatabase.pl to add the laptop recordings to the original machine's mythconverg. (This script has since been torched in myth 0.24 without a replacement.) When the recordings files have been added to the old machine, then uninstall the laptop's myth installation.

If the laptop is running some kind of Ubuntu (whatever version) you'd need 3 packages: mythtv-common, mythtv-backend, and mythtv-frontend (plus the usual dragged-along dependencies) for that Ubuntu version.

I had to use this sort of procedure a couple of years ago when the MB on my primary backend blew and I needed to quickly turn a secondary to a primary to avoid missing recordings while waiting for parts.

If you wish to upgrade versions, you may wish to wait until you have your hardware difficulties solved, then make the LTS jump from Mythbuntu 8.04 to 10.04. And then wait for 12.04, which ought also to be an LTS version if Canonical does the every second year thing again. Do your Mythtv research first though: recent versions of Mythtv seem to be almost as notable for the features that have been removed as they are for the features that have been added.

---

### Post by thatguruguy on 2011-10-14
> **klc5555 said:**
> 
If you wish to upgrade versions, you may wish to wait until you have your hardware difficulties solved, then make the LTS jump from Mythbuntu 8.04 to 10.04. And then wait for 12.04, which ought also to be an LTS version if Canonical does the every second year thing again. Do your Mythtv research first though: recent versions of Mythtv seem to be almost as notable for the features that have been removed as they are for the features that have been added.

12.04 will be the next LTS. In fact, I believe that Mythbuntu 11.10 (the Mythbuntu which came out yesterday) will be the last one released on the standard 6-month Ubuntu release schedule.  From 12.04 on, new versions of Mythbuntu will only be released on the LTS release schedule, which is every two years.

---

### Post by nickrout on 2011-10-14
> **bah1976 said:**
> So, since the replacement MB won't be here until monday, I have an unrelated mythbackend question - if I were to set up a mythbackend in a vmware virtual machine on my laptop, using the hdhomerun that I have, and recording to the NAS that is part of the configured storage group on the dead backend, would it be able to run without mysql?  Or could I temporarily move the database or something?  I know I can torrent anything that I miss, but it's the principle of the thing.  

My slightly longer term plan is to compile vmware server into the slackware/unraid kernel that's running my nas, and make a primary backend VM, but I haven't gotten there yet.  There's some detailed directions that I don't have time to follow right now to make vmware server work, otherwise I'd just set that up now.  Hmm...  Talking this out, maybe I'll just make a vmware workstation primary backend, and then later move it to the unraid kernel.  So, my updated question is - how would I go about telling my dying backend to be a secondary, and make a new one (vm) be the primary?  I havne't looked yet, since this is all coming out while I type - is there documentation on how to do that?

And a follow-up question - if I'm going through all this anyway, what advantages would there be to upgrading to current mythbuntu in the process?  Might be too many changes at once to troubleshoot, I may do the upgrade later.

Yes you can run the backend in a virtual machine. You do need mysql though, it is fundamental to the backend, and the frontend.

Simply backup the database on the old machine and restore it in the virtual machine.

---

### Post by ari.maidana on 2011-10-15
I'm having a similar problem. This is what happened:
My machine entered an infinite reboot cycle. It turned out to be the power source, so I replaced it. The machine started to boot normally again, but this two things happened:
- Trying to install a 64-bit version of Ubuntu resulted in a kernel panic.
- 32 bits runs ok for a while, but eventually a kernel panic happens.

```

This is my /var/log/mcelog, but I don't know how to interpret it:
 mcelog: failed to prefill DIMM database from DMI data
Kernel does not support page offline interface
Hardware event. This is not a software error.
MCE 0
CPU 0 BANK 0 
TIME 1318549546 Thu Oct 13 20:45:46 2011
MCG status:
MCi status:
Uncorrected error
Error enabled
Processor context corrupt
MCA: BUS Level-0 Local-CPU-originated-request Generic Memory-access Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_HARD_TYPE BQ_ERR_HARD_TYPE
timeout BINIT (ROB timeout). No micro-instruction retired for some time
STATUS b200004000000800 MCGSTATUS 0
MCGCAP 806 APICID 0 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 23
Hardware event. This is not a software error.
MCE 1
CPU 0 BANK 5 
TIME 1318549546 Thu Oct 13 20:45:46 2011
MCG status:
MCi status:
Uncorrected error
Error enabled
Processor context corrupt
MCA: BUS Level-3 Generic Generic Other-transaction Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_AERR2_TYPE BQ_ERR_AERR2_TYPE
received parity error on response transaction
MCE is observed
STATUS b200001024000e0f MCGSTATUS 0
MCGCAP 806 APICID 0 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 23
Hardware event. This is not a software error.
MCE 2
CPU 1 BANK 5 
TIME 1318549546 Thu Oct 13 20:45:46 2011
MCG status:
MCi status:
Uncorrected error
Error enabled
Processor context corrupt
MCA: BUS Level-3 Generic Generic Other-transaction Request-did-not-timeout Error
BQ_DCU_READ_TYPE BQ_ERR_HARD_TYPE BQ_ERR_HARD_TYPE
received parity error on response transaction
MCE driven
STATUS b200001010000e0f MCGSTATUS 0
MCGCAP 806 APICID 1 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 23
```

I think the faulty PSU probably damaged some component, but I don't know which one. I ran a memcheck for 2 hours but it didn't show any error.

---

### Post by bah1976 on 2011-10-18
ok folks - looks like the MB was the problem, I'm stable now.  But I've f'd something up in the meantime.  When I thought the problem was video, I put a new vid card in and tried to update nvidia drivers.  I'm now back to the original video card, and I can't get x to work.  In fact, I've made it worse.  myth backend won't start anymore - 'error while loading shared libraries: /usr/lib/libGL.so.1: invalid ELF header' pops up.  I think I need to
1) go back to original nvidia driver
2) fix shared libraries
3) maybe they're the same thing?
I also haven't figured out the new audio driver yet - but I'm still trying that myself.  Maybe that's part of this as well?

I'm not sure where to go from here - any tips?

Thanks,

---

### Post by nickrout on 2011-10-18
What video card are you using?

what drivers are you using?

The supported cards for each set of nvidia drivers are listed in the readme which is installed with the drivers.

---

### Post by bah1976 on 2011-10-18
Ok, so now I got the driver to load.  I installed NVIDIA-Linux-x86_64-71.86.04-pkg2.run from nvidia, and I have a 6200 LE.  I've got better video quality, buy my twinview isn't working, and when gdm starts (the first time only), I get a "failed to initialize hal" error.  There's lots of those in google, and I'm sorting through - no resolution yet.

I'd even be ok if I could make the tv-out be the primary, with the vga secondary desktop screen (with the xfce logo).

So I'm down to two issues - 
1) twinview/swap primary display / hal error
2) line out audio doesn't seem to work.  New MB has a digital out, and I'm guessing that's the one that functions, although I don't have a connection to see.  I think I have to remember how alsa works - it's been awhile since I've touched this stuff.

---

### Post by nickrout on 2011-10-19
bad move, you are far better off with the ubuntu package for nvidia.

---

### Post by bah1976 on 2011-10-19
I am more than willing to switch back - if you haven't figured it out by now I know just enough to be dangerous.  Can you provide some guidance?

---

### Post by nickrout on 2011-10-19
> **bah1976 said:**
> I am more than willing to switch back - if you haven't figured it out by now I know just enough to be dangerous.  Can you provide some guidance?

I thought the 6200 ran a legacy version of the nvidia driver, but the nvidia site tells me the current 285 version should work. It's the 5200 that requires the legacy driver.

Simply running the "hardware drivers" utility should install the correct drivers, but hey you have the drivers working now, perhpas leave it as it is. If it ain't broke don't fix it.

For audio, run alsamixer and see what jumps out at you, your utput device may be muted.

In mythtv go to general settings and about page 4 is the audio settings, choose "scan for audio devices" then run through the options and find the llikely one, choose it. 

If none of that works give us the output of the following commands:```
aplay -L
aplay -l
ls /proc/asound -l

```

That'll do for a start.

---

### Post by bah1976 on 2011-10-19
I think I'm good on video now - thanks for the pointers.  For the record, I ended up loading the 285 driver from nvidia, and then I was able to configure the twinview clone setup in nvidia-settings.

Sound - The old board had the 6-plug setup only, the new board has a digital rca & optical outs as well as the 6-plug.  The IDEAL scenario would be to have the digital out as well as the stereo out, since this feeds both the receiver and a modulator to go to the upstairs TV over coax.  The old board used to display all 6 channels when I went into alsamixer, now all I've got is Master and PCM - both of which are at 100%.  I've tried playing something in VLC and I have no sound there either.  I haven't gotten the speaker-test utility to work either - I'm not 100% sure what options I need to do.

```
bruce@MythTV-BE:~$ aplay -L
default:CARD=SB
    HDA ATI SB, HDA Generic
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, HDA Generic
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, HDA Generic
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, HDA Generic
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, HDA Generic
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, HDA Generic
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, HDA Generic
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=SAA7134
    SAA7134, SAA7134 PCM
    Default Audio Device
default:CARD=SAA7134_1
    SAA7134, SAA7134 PCM
    Default Audio Device

```

```

bruce@MythTV-BE:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

bruce@MythTV-BE:~$ ls /proc/asound -l
total 0
dr-xr-xr-x 4 root root 0 2011-10-19 12:02 card0
dr-xr-xr-x 3 root root 0 2011-10-19 12:02 card1
dr-xr-xr-x 3 root root 0 2011-10-19 12:02 card2
-r--r--r-- 1 root root 0 2011-10-19 12:02 cards
-r--r--r-- 1 root root 0 2011-10-19 12:02 devices
-r--r--r-- 1 root root 0 2011-10-19 12:02 hwdep
-r--r--r-- 1 root root 0 2011-10-19 12:02 modules
dr-xr-xr-x 2 root root 0 2011-10-19 12:02 oss
-r--r--r-- 1 root root 0 2011-10-19 12:02 pcm
lrwxrwxrwx 1 root root 5 2011-10-19 12:02 SAA7134 -> card1
lrwxrwxrwx 1 root root 5 2011-10-19 12:02 SAA7134_1 -> card2
lrwxrwxrwx 1 root root 5 2011-10-19 12:02 SB -> card0
dr-xr-xr-x 2 root root 0 2011-10-19 12:02 seq
-r--r--r-- 1 root root 0 2011-10-19 12:02 timers
-r--r--r-- 1 root root 0 2011-10-19 12:02 version

```

What's next?

---

### Post by nickrout on 2011-10-19
What devices are shown when you scan for audio devices in mythtv|general? (I assume you ARE using mythtv 0.24.1, if you are using 0.23, come back for support when you are running a current version. Google mythbuntu-repos to update)

---

### Post by bah1976 on 2011-10-19
You know what they say about asumptions... :)  Try .21  :shock:

Let's take myth out of it for the moment - I can't even get it to work outside of mythfrontend.  Can you help there?

---

### Post by bah1976 on 2011-10-19
Ok folks - I am officially a freaking idiot.  *cough* I had the miniplug in the wrong jack on the MB.  *cough*

Doesn't get me digital sound, but I'm back to where I was before the MB swap - which is good enough for me...

---

### Post by nickrout on 2011-10-19
> **bah1976 said:**
> Ok folks - I am officially a freaking idiot.  *cough* I had the miniplug in the wrong jack on the MB.  *cough*

Doesn't get me digital sound, but I'm back to where I was before the MB swap - which is good enough for me...

LOL reminds me of spending ages trying to work out why a computer had no network come up on boot, again the ethernet cable wasn't plugged in to computer!

---

