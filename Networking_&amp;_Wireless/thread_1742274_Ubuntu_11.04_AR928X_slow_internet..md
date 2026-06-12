---
title: "Ubuntu 11.04 AR928X slow internet."
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by bearly230 on 2011-04-28
I'm running a Gateway MD2614u laptop.

I just installed 11.04 (clean) and have found my Internet download speed has dropped from 20mb to .86mb.

I have booted into win 7 to confirm I'm still getting normal speeds on this laptop. 

Under 10.x Internet speeds are normal. Only an issue on 11.04.

Any suggestions would be greatly appreciated.

---

### Post by toomuchcomputertime on 2011-04-28
I'm having the same problem, I'm reinstalling 11.04 for the third time due to problems installing programs - perhaps due to the 2 b/s to sometimes 50 kb/s internet speeds I'm getting.

---

### Post by kd8cgo on 2011-04-28
Same problem - Wireless unusable due to slow speeds with AR9285 Wireless Network Adapter (PCI-Express) in an ASUS G73JW laptop.

Bummer.

---

### Post by robertcoulson on 2011-04-28
Had the same problem running 11.04 in virtual box...Thought at first my internet was screwing up...Glad I did not (and will not) install 11.04 on my machine..10.10 works just fine (most of the time).

Robert

---

### Post by deeperDATA on 2011-04-28
I'm downloading 11.04 hoping that it fixes my 10.10 slow internet speed issues. This isn't promising. :(

---

### Post by xd20 on 2011-04-28
I can't use anything before 11.04, since its the first version that supports my graphics card.

But now that I have 11.04 I have this slow speed issue as well, except I'm already on DSL so whenever the speed slows, it's pretty unbearable.

Any solutions?

---

### Post by dineshs on 2011-04-29
Is this related?
[http://peppermintos.net/viewtopic.php?f=39&t=311](http://peppermintos.net/viewtopic.php?f=39&t=311)
What is the result of ```
iwconfig
```

---

### Post by michiganitis on 2011-04-29
Same problem. Since 11.04, internet browsing and downloading is slow as fork!!!! Windows 7 partition still lightening fast. Different computer with Windows 7 and 10.10, both partitions still lightening fast. But 11.04 is like dial-up!!!! (Slight exaggeration.)

---

### Post by bearly230 on 2011-04-29
I checked that out. Didn't make any difference.

---

### Post by nesto1000 on 2011-04-29
I too am having this issue!  :(
It took forever to download chrome onto my Asus A52F laptop! All of my downloads from the software center are so slow.

---

### Post by aport on 2011-04-29
I have the same problem with my Dlink DWA-160, which uses the ar9170usb driver.

I had to switch back to my Ralink adapter and switch to rt2870sta driver, which meant I had to patch NetworkManager to disable background scans again!

What a pain. Something is a bit wrong with these Atheros drivers in the 11.04 kernel.

---

### Post by thomaskw on 2011-04-29
I have the same problem but when the internet runs normal then Ubuntu runs jerky, I thought upgrading to from 10.10 would solve the problem, I was wrong. The only time my PC runs smooth is when I disable all networks.

Ubuntu runs flawless on my Acer Aspire One but runs crap on my 'super' PC. I just deleted it from my PC, I cannot take the disappointment anymore. I mean, counting down the days for the release of 11.04, for what. ](*,) :evil:

---

### Post by mantaor on 2011-05-01
Hi guys,
same problem here. pci-e tplink with AR9285 and ath9k driver correctly installed and working. With win7 and previous ubuntu distro 10.04 and 10.10 the adapter worked like a charm (with win7 it's still working properly, :)) so it's a problem of this particular distro. I tried everything: wicd, various packages and dns but nothing works. please, developers help us

---

### Post by raulv on 2011-05-01
same problem with acer nplify (which is just an atheros).

iwconfig says:

```
 IEEE 802.11bgn  ESSID:"RVSGGSDPDV"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 94:44:52:8B:59:61   
          Bit Rate=104 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:40  Invalid misc:2176   Missed beacon:0
```If it means anything to anyone, please let me know :)

Raul.-

---

### Post by darkblaze on 2011-05-01
I have / had the same issue for my ar928x with natty on an acer extensa 5235. 

Tried lots of different stuff, finally got it to work by updating the firmware of my router (wrt160nl) and setting it to B/G mode only. 

Now everythings fine again.

Speed is fixed now on 54 Mb/s and before it was somewhere 160 - 200 Mb/s but never worked faster than 3 KB/s!

Can someone confirm this workaround?

One more thing: It seems, that by manually limiting the router to a 20 MHz channel bandwidth somehow makes it possible to use the n-capability of the ar928x, but still is slower than limiting also to b/g.

---

### Post by darkblaze on 2011-05-01
> **raulv said:**
> same problem with acer nplify (which is just an atheros).

iwconfig says:

```
 IEEE 802.11bgn  ESSID:"RVSGGSDPDV"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 94:44:52:8B:59:61   
          Bit Rate=104 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:40  Invalid misc:2176   Missed beacon:0
```If it means anything to anyone, please let me know :)

Raul.-

Seeing you also have a high bit rate (104 Mb/s) try my workaround by setting the router to b/g only. You should get a 54 MB/s reading. Maybe that helps?

---

### Post by CozmoK on 2011-05-01
type sudo iwconfig <return>
note the name of wifi card (example eth1)
type sudo iwconfig [name of card] power off <return>

Now test speed.  It appears 11.04 restricts power to Wifi card to save power at the cost of unusable internet!

---

### Post by raulv on 2011-05-01
> **CozmoK said:**
> type sudo iwconfig <return>
note the name of wifi card (example eth1)
type sudo iwconfig [name of card] power off <return>

Now test speed.  It appears 11.04 restricts power to Wifi card to save power at the cost of unusable internet!


This didn't work :(

---

### Post by raulv on 2011-05-01
> **darkblaze said:**
> Seeing you also have a high bit rate (104 Mb/s) try my workaround by setting the router to b/g only. You should get a 54 MB/s reading. Maybe that helps?

I set 2.4gh to "g" only and now i have about 24 mb, so it works.
It's still half of what it should be, obviously, but much better that 3mb :-?

---

### Post by raulv on 2011-05-01
Well, I have been trying a couple of thing and this is what happens:

My ISP gave me a wifi modem (thompson)  to which i attatched a Belkin PlayMax router, so i have two different networks to choose.

no matter what network i select, unless the wlan is set to "b" or "g", it won't go more than 3 mb.
Once the wlan is set to "b" or "g", speed tests show around 20 mbs. Still half of what i'm paying for, though.

This seems to happen to download speed only, since uploading is always fine.

So, ubuntu must have a problem to deal with networks set to "n".

---

### Post by mantaor on 2011-05-01
I don't have "n" router but I have the problem, so....

---

### Post by darkblaze on 2011-05-02
> **raulv said:**
> 

My ISP gave me a wifi modem (thompson)  to which i attatched a Belkin PlayMax router, so i have two different networks to choose.

Once the wlan is set to "b" or "g", speed tests show around 20 mbs. Still half of what i'm paying for, though.



Maybe you get ~20 Mb/s (about half the speed of 54Mb/s) in your wifi because you are running two wifi-networks from two routers? Or what exactly do you mean with "speed tests"? Are the 20 "mbs" 20 Megabytes per second or 20 Megabit per sec?

I meant the iwconfig Bit Rate= xy Mb/s reading should say 54 at your side, if the signal strength is good and no noise.

---

### Post by darkblaze on 2011-05-02
> **mantaor said:**
> I don't have "n" router but I have the problem, so....

What make is your router? SN? There were intermittent routers made, that implemented some homebrewn kind of 802.11n before the standard was fixed.

---

### Post by joaomaradao on 2011-05-02
> **mantaor said:**
> I don't have "n" router but I have the problem, so....
I also don't have a "n" router and have this problem: 2Mb/s on Ubuntu 11.04 and 10Mb/s on Windows 7.
My laptop is an ASUS G51JX with an Atheros AR9285.

---

### Post by mantaor on 2011-05-02
Hi guys,
good news. I solved the problem following the command for ath9k (my driver) from this link
[http://www.ubuntusecrets.it/2011/04/hack-connessione-lenta-su-natty-forse-ho-la-soluzione-giusta-per-voi/?lang=en](http://www.ubuntusecrets.it/2011/04/hack-connessione-lenta-su-natty-forse-ho-la-soluzione-giusta-per-voi/?lang=en)
The author is an italian guy (like me) but the article is in english.
Bye

PS I never touched router setting (DG834Gv3)

---

### Post by tblups on 2011-05-02
Can't wait to go home to test it. Thank you!

---

### Post by yellerKat on 2011-05-02
> **mantaor said:**
> Hi guys,
good news. I solved the problem following the command for ath9k (my driver) from this link
[http://www.ubuntusecrets.it/2011/04/hack-connessione-lenta-su-natty-forse-ho-la-soluzione-giusta-per-voi/?lang=en](http://www.ubuntusecrets.it/2011/04/hack-connessione-lenta-su-natty-forse-ho-la-soluzione-giusta-per-voi/?lang=en)
The author is an italian guy (like me) but the article is in english.
Bye

PS I never touched router setting (DG834Gv3)

Great, this worked for me too! I now remember doing this some months ago before doing a full re-install, but foolishly I didn't make a note of it.

---

### Post by tblups on 2011-05-03
Yes yes yes it definitely works! Thank you again, mantaor, and to Andrea as well, of course!

---

### Post by joaomaradao on 2011-05-03
> **mantaor said:**
> Hi guys,
good news. I solved the problem following the command for ath9k (my driver) from this link
[http://www.ubuntusecrets.it/2011/04/hack-connessione-lenta-su-natty-forse-ho-la-soluzione-giusta-per-voi/?lang=en](http://www.ubuntusecrets.it/2011/04/hack-connessione-lenta-su-natty-forse-ho-la-soluzione-giusta-per-voi/?lang=en)
The author is an italian guy (like me) but the article is in english.
Bye

PS I never touched router setting (DG834Gv3)
Thanks a lot, it also worked here! ;)

---

### Post by deeperDATA on 2011-05-03
I'm confused about this part. I'm not using an Atheros chipset so how do I determine the "alias" for either of my two wireless adapters? Do i just wlan0 because that didn't work for me.

Also, I realized after testing a USB attached wireless adapter in a virtualized Windows 7 guest OS through a Ubuntu host OS that I'm having the same issues. I'm assuming the problem defaults back to how Ubuntu is "operating" the device. Maybe a power or transmission setting that is incorrect but for 2 different wireless adapters it just seems strange.

I was thinking about trying ndiswrapper to see if that would straighten it out.

:confused:

---

### Post by murias002 on 2011-05-04
i installed 11.04 today, in one of my powerfull machines (AMD Phenom 64  quad), but, the performance in 64 bits is so poor.... too heavy, too  mucho disk access, i am not happy. i preferr the previus 10.04 release,  more faster, more powerfull.

my machine has 8 gb dd3 memory.

i wait some day for patches fixing this performance problem, if not fixed, i will be returning to 10.04

---

### Post by sheds on 2011-05-05
I think it's an overall problem. Google instant and flash were working fine before 11.04. I am not very happy either. Seems like it got a lot of gadgets that we seldom use while diminishing performance; not a smart choice if you ask me.

---

### Post by darkblaze on 2011-05-08
Yep! This definitely worked with ath9k! Thanks very much!:popcorn:

---

### Post by cordoval on 2011-05-12
where do I get the ath9k or 5k driver?

url anyone?

Thanks!

Luis

---

### Post by cordoval on 2011-05-12
I tried this guy solution on my asus g73jw with atheros and it did not work, i don't know what to do, or how to examine the speed, please help!

---

### Post by Toten on 2011-05-29
Thanks a lot, too! This works perfectly! Download speed was 30 Kb/s before, now it is 350 Kb/s, like it used to be in Windows.

I have ath9k too.

---

### Post by dennis1200 on 2011-08-05
Could someone post the contents of that italian website - the link is dead. Apparently the issue has been fixed in the newest kernel version 2.6.38-10.46, but I can't download anything that big without wireless!

---

### Post by ALBCODERS on 2011-08-16
> **mantaor said:**
> Hi guys,
good news. I solved the problem following the command for ath9k (my driver) from this link
[http://www.ubuntusecrets.it/2011/04/hack-connessione-lenta-su-natty-forse-ho-la-soluzione-giusta-per-voi/?lang=en](http://www.ubuntusecrets.it/2011/04/hack-connessione-lenta-su-natty-forse-ho-la-soluzione-giusta-per-voi/?lang=en)
The author is an italian guy (like me) but the article is in english.
Bye

PS I never touched router setting (DG834Gv3)

Hi to all I have the same problem but after installing virtualbox with xp 64 bit inside ubuntu 11.04,so the link wich you gave is dead I get 404 error,can you explain here? Thanks! grazie ;)

---

### Post by iUbuntu on 2011-10-20
same here .. I think I will downgrade .. is there a way to downgrade [easily, 1 click ?] to a specific version ?
Infact the entire GUI is slow and clunky !

---

### Post by kaha6uc on 2013-03-28
Please, someone paste the solution here - the link is really dead :(

---

### Post by wildmanne39 on 2013-03-29
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

