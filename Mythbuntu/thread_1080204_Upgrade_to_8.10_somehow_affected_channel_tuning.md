---
title: "Upgrade to 8.10 somehow affected channel tuning"
date: 2009-02-25
forum: Mythbuntu
---

### Post by lofgren on 2009-02-25
Hi people,

**Has anyone found the upgrade from 8.04 to 8.10 has caused tuning issues?**

One of my channels (7 Digital - Melbourne, Australia)won't tune/record since the upgrade.


I recently bought a dual tuner to replace two older cards (Hauppauge Nova-TD-500). Upon reading that it was detected "out of the box" by 8.10, I kicked off the upgrade last weekend.

After a cursory check, I swapped out the old cards, commented out their entries in /etc/modprobe.d/aliases and thought I was done..

A day or so later, I discovered that 7 Digital (Melbourne, Australia) would no longer record. 

Opening the frontend to test on the backend server, I found Mythtv couldnt get a lock the channel. 
Mythfrontend reported that signal was 79% and BE was 65535.

All other channels were around 79% signal strength or higher with a BE of 0.

**tzap managed to get a lock and showed no unc**'s (I've read these are uncorrectable errors), **but had a high BER for this one channel**.

I've had a few late nights this week as you might imagine:- adding /etc/modprobe.d/options file entries such as 
'options dvb-usb-dib0700 force_lna_activation=1' 
and 
'options dib3000mc buggy_sfn_workaround=1' with no joy.

Going through the mythbackend.log file I came across a couple of entries suggesting that perhaps I should run this to remove possible corruption:
'myisamchk -f /var/lib/mysql/mythconverg/*.MYI'

Still no joy.

Finally I gave up, removed all the new options entries, uncommented the old ones for my original cards and stuck them  back in the machine - they were even worse. Neither of them could even get a lock on 7 Digital.

So now, I know it's not the card and I am suspecting something happened during the upgrade.

As an example.. amavis stopped working on this box as the upgrade changed the directory permissions for the directories it uses.

History of the machine:
This machine was installed as Ubuntu 7.10 with mythtv packages added and has been upgraded through 8.04 and now to 8.10.

It runs mail (based on the how-to at [www.flurdy.com](www.flurdy.com)) and is used as a daily desktop to check weather, download torrents etc.

With my confidence high after the 7.10 -> 8.04 upgrade going so smoothly, I didn't bother backing up databases etc this time (stupid I know).

I'd appreciate any info or suggestions and hope it is something simple like the amavis issue.

thanks in advance,
Lofgren

---

### Post by lofgren on 2009-02-26
Can anyone in Melbourne (and or Australia in general) share info on customisations they've used to get the Nova-TD-500 to work properly in their system?

Attacking all angles at once, I guess I'd like to make sure the card is working as best as possible until I find out what setting has changed elsewhere to upset my config.

---

### Post by AlecJ on 2009-02-26
I have had major problems with 8.10, I gave up way before you have by the sounds of it, once you clear the tuning issue then there is the numbering problems, all channels have a 7 digit number, not just 1,2,3 etc. Then the lockup's and freezes? bad time keeping 5 min's or more.
I started again with 8.04, all remote frontends work without problem, the backend is stable and with all the updates it has the same functions as 8.10. It found my 2 USB DVB-t and Nova-T-500 Plus the single cards, And my DVB-S (but as every (mey-be me) can't sepetate the channels, tries to tune a DVB-t to a DVB-s channel)

I have had the same problems with 8.10 across the board, Ubuntu 8.10 STILL can't see my SMB network, you have to navigate with I.P address's.
I learnt from this:- If it ain't broke don't fix it!
Wonder what joy's 9.04 will bring?

---

### Post by lofgren on 2009-02-26
Thanks for your info Alec. Doesn't sound like fun.

Your cards are "Nova-T-500" right?  Not the newer Nova-T**D**-500's?

---

### Post by AlecJ on 2009-03-02
Correct, it has just 1 uhf input not 2, Mythbuntu calls it :-
DiBcom 3000MC/P  Subtype: DVB-T
I get 2 entries like this from the card.

I ordered a card at the start of this project that was sold as a Nova-T-500 but it had 2 UHF's and was not compatible, I just returned it.

---

### Post by dibuntux on 2009-03-20
I have exactly the same issue (card is Hauppage too) with an entire MUX. See my post:

This happen with 8.10 and 9.04 alpha 6.1

 partial lock - sometimes - on one DVB-T network
I really cannot trace this out. I can lock to all networks but one, RAI (national gov. tv in Italy).

Sometimes it works, sometimes it does not. I tried with an amplifier, and signal passed from 61% to 64%, but it is not dependent on % signal; other networks work with just 58%.

I get the signal % at 64, partial lock and BE 65535 and the window that tells you "you should have got a signal lock by now..."


using scan, i get a lock on all networks, which BTW are transmitted from a repeater in the same location, but on the RAI networks I get

Warning: filter timeout pid 0x0011

Other days, it just works; BE is still high but I have a lock. I tried with longer timeouts, but it is the same.

Any suggestions?

My system: Mythbuntu 8.10
Athlon 1700+ 512MB SDRAM PC133
Nvidia 5200 256 MB
Hauppauge HVR 1110 DV-T
SkyStar 2.6 DVB-S

---

### Post by lofgren on 2009-03-23
Hrm.. I agree about the signal strength. I don't think it is that.
I was getting a figure up in the 70's (same as most other channels), but still the high error rate.
You seem to be getting a bit further than me though. I can only lock when I scan and it still shows a very high error rate. I don't even have it work sometimes.

Did yours work with 8.04?



I had all but given up.

My box is a P4, which runs a bit hot in a Dell GX-270 case.
I need to move it to a bigger case with more fans - which means upgrading the motherboard etc too because the DELL is so customised that pci boards mould around the slimline power supply and there is no room for additional fans.

So.. with the channel tuning not working properly, I just figured I would rebuild with 8.04 (it is LTS afterall) in the new case and compile the drivers in for the Nova-TD-500.

Remembering that when I put my old cards back in, they couldn't tune the channel I am having trouble with either. Hence me attributing the issue to 8.10 and some setting or package config.

Other avenues..
My aerial is a relatively new hybrid (analogue-digital), but I thought I might re-terminate a couple of the connectors just in case. I got a decent crimper from work, so I might replace the screw-on f-connectors with some crimped ones - at least on my mythtv cable run.

In the mean time.. I have been lucky. There is only one show my wife watches on that channel this season ;)

---

### Post by dibuntux on 2009-03-24
1st: do not give up! 
2nd: 7.10 was working (as I remember), 8.04 is the same. And so it is 9.04 Alpha 6.1... So if it is Mythbuntu version related, either wait for 9.04 final or try 7.10 (but it's on Myth 0.20, quite different from .21).

As for your antenna: is fine - I watch channel with 58% signal with no problem at all on my HVR1110. It is just that RAI network that gets BE 65535; BTW, the number is strange, is the maximum possible for a 16 bit integer. So I'm inclined to think it is an SW error, since the signal is strong enough, compared to other channels. It may be something in the ID of the network that the driver does not understand...

Hope this helps

---

### Post by klc5555 on 2009-03-24
> **dibuntux said:**
> 1st: do not give up! 
2nd: 7.10 was working (as I remember), 8.04 is the same. And so it is 9.04 Alpha 6.1... So if it is Mythbuntu version related, either wait for 9.04 final or try 7.10 (but it's on Myth 0.20, quite different from .21).

As for your antenna: is fine - I watch channel with 58% signal with no problem at all on my HVR1110. It is just that RAI network that gets BE 65535; BTW, the number is strange, is the maximum possible for a 16 bit integer. So I'm inclined to think it is an SW error, since the signal is strong enough, compared to other channels. It may be something in the ID of the network that the driver does not understand...

Hope this helps

I don't know whether this will help, but about 7 months ago (on 7.10, but Mythtv 0.21, master backend machine) I had some serious intial difficulty adding a new remote machine, slave backend onto my setup. After the slave machine was finally added successfully, I gradually began to notice there was a group of strong digital stations that the master backend could no longer lock on to (with a pcHDTV-5500 card).

After swapping hardware in an out, deleting and readding the cards in the backend setup, and doing a couple of complete 7.10 reinstalls on the master backend to no effect, it dawned on me the only thing I hadn't swapped out was the mythconverg database, which I had dutifully restored from my current backup after each reinstall. Dropping mythconverg and restoring from an older backup, I discovered the cards tuned properly again. The whole problem was database corruption.

In short, could it be that your mythconverg brought up through the upgrade is corrupted with respect to your tuner card and channel settings? If you backed up a couple of copies of your current mythconverg (to be safe) and then dropped your current mythconverg, created a new blank one and then do a backend setup as though this were a completely new system, I wonder whether you'd discover that your cards would tune properly. Or if you have retained older copies of your mythconverg from before the upgrade process, one of these older backups might be tried.

If there were no improvement, you could just restore your original mythconverg from the backups, and everything would be as it was. But if your hardware now worked properly, set up on the clean mythconverg, you'd be left with the problem of just restoring the mysql fields pertaining to your current recordings (which I'm not sure how to do), or adding your recordings into your new uncorrupted mythconverg using something along the lines of the myth.rebuilddatabase.pl script.

Hope this helps.

---

### Post by dibuntux on 2009-03-24
I once deleted the source, card & channels and started back & it worked. So I thought that was it. But then, suddenly, the problem arose again, with no change to the dB. So it is something transmitted from those channels that screw up reception (BE 65535, partial lock).

So... do not know what to try... Thanks anyway

---

### Post by klc5555 on 2009-03-25
> **dibuntux said:**
> I once deleted the source, card & channels and started back & it worked. So I thought that was it. But then, suddenly, the problem arose again, with no change to the dB. So it is something transmitted from those channels that screw up reception (BE 65535, partial lock).

So... do not know what to try... Thanks anyway

You don't need to actually have changed the database: even a dirty shutdown or bad reset button restart is frequently enough to corrupt mythconverg. It's the fragile achilles heel of the whole  myth setup, which is why the manual spills so much virtual ink over the backup process.

Anyway, good luck! Hope you find the problem! :)

---

### Post by dibuntux on 2009-03-26
Thanks for your reply, but it is not a dB problem. It does the same even on a freash install. It just does not tune anymore on that network...

---

### Post by dibuntux on 2009-03-26
I found this on another forum:

just in case anyone else is struggling to tune one of these adapters.

It wasn't a myth 0.21 problem. dvbtune wouldn't lock channels either.

It looks to be a problem with newer v4l-dvb modules that ship with Ubuntu 8.04.

Hardy includes drivers and firmware but the volar a808 just won't tune properly. I've tried replacing the firmware with older files and still no good. I've also tried the latest v4l-dvb drivers and it doesn't help.

I installed a test box with Mythbuntu 7.10 and the tuner works perfectly. The firmware file isn't supplied with 7.10, but after copying it in the tuner found all channels and plays them back flawlessly in Mythtv.

One solution at the moment would be to install Mythbuntu 7.10 and then upgrade Myth to 0.21 from backports.

I'll submit a bug report (probably for Ubuntu 8.04 as that's where I know the problem to exist)


So it seems a v4l-dvb problem - but it's still here from 8.04 to 9.04 !!

---

### Post by dibuntux on 2009-03-26
OK, some more info to the puzzle... indeed there are problems with HVR 1110:
this is from a bug fixes in kernel 2.6.24 link:
[https://launchpad.net/ubuntu/hardy/+source/linux/2.6.24-3.5](https://launchpad.net/ubuntu/hardy/+source/linux/2.6.24-3.5)

after a long list you see a line:

 V4L/DVB (6746): saa7134-dvb: fix tuning for WinTV HVR-1110

So, there was something to fix... and it was fixed... but now it does not work anymore!

Any help?

---

### Post by lofgren on 2009-04-07
I haven't spent any more time on this yet, but that seems more inline with my issue.

It also explains why putting the old cards back in still failed to lock onto that channel.

However.. Mine was 8.04 when it was working, not 7.10, so that part of the puzzle doesn't fit.

---

### Post by dibuntux on 2009-04-07
More fuel to the fire: now it works.

What I did? I bought a fantastic case, the Silverstone LC10E, and a modern Power supply from Corsair.

Installed all the old stuff into the new case, with the new PS, and it worked. 
One hint: all small cables, like Power LED, Disk activity, USB, etc. are passed through the supplied toroidal EMI absorber.
Also going from a noname chinese PW to a Corsair probably improved on EMI.

Bit error is still High, at something between 1000 and 13000, but I lock the MUX no problem.

This could explain why it worked on all MUXs and not that one: a spurious freq. interference with that MUX.
Bottom line, use good stuff and EMI protections.

Let's see how long it lasts to confirm it solved...

---

### Post by lofgren on 2009-04-07
Good luck!
Could be something in it.. my case is open because it is a compact DELL case where the pci riser board wraps around the power supply and there is no room for additional fans in the box.. The P4 got pretty hot over summer here in AUS. 
I am planning on upgrading the case and MB to increase airflow and reduce noise - hopefully I get similar results ;)

But it was like that before I upgraded 8.04 to 8.10, so it doesn't explain why it stopped working and wouldn't work with the old cards back in place.

cheers,
Matt

---

### Post by dibuntux on 2009-04-08
From my experience, I learned to avoid riser card at all costs. At bus frequencies, having two more connections, unwanted impedance & capacity, is for sure cause of interference. So give it a try with another case.

And, yes, it is strange that it was working with 8.04 and then not... you know intermittent problems are the worst.

Anyway I wish you good luck!

---

