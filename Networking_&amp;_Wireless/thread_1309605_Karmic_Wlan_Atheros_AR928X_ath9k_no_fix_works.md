---
title: "Karmic: Wlan Atheros AR928X ath9k: no fix works"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by Prosis on 2009-11-01
Hello

I've been looking around since yesterday for a fix and tried several fixes to get my wireless ath9k to work on Karmic but in vain

-Tried removing ath from blacklist
-Tried to use wicd

In all cases, the wireless disconnects after something like 10 minutes and I can't reconnect.  None of this happens on Jaunty.

So I can't install Karmic because I can't install the language packages nor use it (and I don't have wires everywhere in the house).  So I'm stuck with Jaunty.

Other than recompiling the kernel with ath9k, is there any other way?

Thanks :(

---

### Post by drpjkurian on 2009-11-01
> **Prosis said:**
> Hello

I've been looking around since yesterday for a fix and tried several fixes to get my wireless ath9k to work on Karmic but in vain

-Tried removing ath from blacklist
-Tried to use wicd

In all cases, the wireless disconnects after something like 10 minutes and I can't reconnect.  None of this happens on Jaunty.

So I can't install Karmic because I can't install the language packages nor use it (and I don't have wires everywhere in the house).  So I'm stuck with Jaunty.

Other than recompiling the kernel with ath9k, is there any other way?

Thanks :(

Hi

Please visit my thread 
[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)
It might help you.

Best of luck
Dr kurian

---

### Post by Prosis on 2009-11-01
Is it supposed to work on the liveCD?  Because it didn't so, I want to make sure that, if I install it again this trick could work. :)

---

### Post by Prosis on 2009-11-03
After doing this, I can't even turn my wireless card on...

Help? :(

---

### Post by Prosis on 2009-11-06
Someone named sebz_ posted a solution that worked fine!

I commented the ath_pci blacklist in /etc/modprobe.d/blacklist-ath_pci.conf.

You check if ath9k (or ath5k) is loaded in /etc/modules

echo ath9k | sudo tee -a /etc/modules

Then you install

linux-backports-modules-karmic and linux-backports-modules-wireless-karmic-generic (and linux-backports-modules-wireless-karmic-generic-pae if you can but I didn't need it)

Reboot and all should be fine! ;)

---

### Post by klotz on 2009-11-06
> **Prosis said:**
> Someone named sebz_ posted a solution that worked fine!

I commented the ath_pci blacklist in /etc/modprobe.d/blacklist-ath_pci.conf.

You check if ath9k (or ath5k) is loaded in /etc/modules

echo ath9k | sudo tee -a /etc/modules

Then you install

linux-backports-modules-karmic and linux-backports-modules-wireless-karmic-generic (and linux-backports-modules-wireless-karmic-generic-pae if you can but I didn't need it)

Reboot and all should be fine! ;)
This seemed to work for me with Karmic Koala on an eeePC 1000HE.  (I assumed "commented" meant "commented out.")

---

### Post by coffeecat on 2009-11-19
> **Prosis said:**
> Someone named sebz_ posted a solution that worked fine!

I commented the ath_pci blacklist in /etc/modprobe.d/blacklist-ath_pci.conf.

You check if ath9k (or ath5k) is loaded in /etc/modules

echo ath9k | sudo tee -a /etc/modules

Then you install

linux-backports-modules-karmic and linux-backports-modules-wireless-karmic-generic (and linux-backports-modules-wireless-karmic-generic-pae if you can but I didn't need it)

Reboot and all should be fine! ;)

Simply installing the two backports-modules worked for me on this Acer laptop with:

```
06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
```It was using ath9k, and still is (presumably a newer version), so I didn't bother with the system file edits. Working so far.... :)

Famous last words. :|

---

### Post by eljacob on 2009-12-01
Hi Prosis,

I was having the same problem with my Sony Vaio X111. I had tried everything I could (installing madwifi, ndiswrapper, turning of WPA, etc) but couldn't fix it.

I installed the 2 backport packages as you said, and it is much better. 

Before the update:

- signal strenght was always between 20% and 65%, even if I was only a couple of meters from the base station
- hundreds off log messages from wpa_supplicant (disconnecting, searching, negotiating, reconnecting)
- needed to kill / restart my connection manually every hour or so.

After the update:

- signal strenght is 100%
- no more error messages on log files
- the connection is stable.

Thank you!

---

### Post by DrawnToScale on 2009-12-02
> **Prosis said:**
> Someone named sebz_ posted a solution that worked fine!

I commented the ath_pci blacklist in /etc/modprobe.d/blacklist-ath_pci.conf.

You check if ath9k (or ath5k) is loaded in /etc/modules

echo ath9k | sudo tee -a /etc/modules

Then you install

linux-backports-modules-karmic and linux-backports-modules-wireless-karmic-generic (and linux-backports-modules-wireless-karmic-generic-pae if you can but I didn't need it)

Reboot and all should be fine! ;)

I also tried the "solution" from drpjkurian, and it also shut down my WiFi.  I then tried the solution you give here.  During the install process, there was a warning message and a suggestion to install one additional package.  At first - my WiFi was working great - but I had to boot in low-graphics mode.  After I installed the additional recommended package - everything was fine.  My WiFi no longer cuts out on me, but I must say that my page load times seem a bit longer.  Anyway - things are MUCH better now.  Thanks for your post.

---

### Post by NikolajSkov on 2009-12-04
> **Prosis said:**
> Someone named sebz_ posted a solution that worked fine!

I commented the ath_pci blacklist in /etc/modprobe.d/blacklist-ath_pci.conf.

You check if ath9k (or ath5k) is loaded in /etc/modules

echo ath9k | sudo tee -a /etc/modules

Then you install

linux-backports-modules-karmic and linux-backports-modules-wireless-karmic-generic (and linux-backports-modules-wireless-karmic-generic-pae if you can but I didn't need it)

Reboot and all should be fine! ;)

Thank you for this, it saved my laptop from getting Windows back. ;)

It work just perfect on my Acer Aspire 5536 with the Atheros 928X ath9k. Now signal strength is about 80% (before it maxed out at about 30%). Now I just need to see if the dropped connections problem goes away.

Cheers,
Nikolaj

---

### Post by scottro on 2009-12-12
For what it's worth, the backports didn't work for me.  What did work was using the wireless-compat drivers.  

[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

It's supposed to be better with the 2.6.32 kernel--with Fedora, using such a kernel, it seemed slightly better, but only slightly.  

Using iperf, which, I freely admit, can miss various other factors.

With Fedora and 2.6.32 kernel, I get about 21 MB/s.  With ArchLinux, though, I get about 40.  

With Ubuntu, with or without backports, I was getting about 1MB or less.  (That's not a typo, just one megabyte.)

Installing the compat-wireless drivers puts it up to around 40.

Apparently, this is a kernel, rather than distribution, issue, that started around the 2.6.29 or 2.6.30 kernel.  

It's the sort of thing that will seriously hurt Linux on netbooks, though one assumes that at least with preinstalled Linux netbooks, they test them before shipping.

---

### Post by omniuni on 2009-12-14
Just finished installing KUbuntu Karmic on an Acer laptop, and I noticed quickly that the wireless kept dropping, and for the most part, would not reconnect. I installed the packages mentioned earlier, and indeed, it seems to have worked! Signal strength is full, so far it has not disconnected, and the speed seems to be pretty stable.

Definitely, a good fix, and an easy one! Thanks!

---

### Post by psymole on 2009-12-15
Hi, I'm having similar issues and i have a coupel of doubts

> Originally Posted by Prosis  View Post
Someone named sebz_ posted a solution that worked fine!

You check if ath9k (or ath5k) is loaded in /etc/modules

echo ath9k | sudo tee -a /etc/modules

Then you install

linux-backports-modules-karmic and linux-backports-modules-wireless-karmic-generic (and linux-backports-modules-wireless-karmic-generic-pae if you can but I didn't need it)

Reboot and all should be fine! 

When says > I commented the ath_pci blacklist in /etc/modprobe.d/blacklist-ath_pci.conf. what exactly was commented.

And in > You check if ath9k (or ath5k) is loaded in /etc/modules

echo ath9k | sudo tee -a /etc/modules It's that command intended to ad ath5k or 9k to the modules files.

Thx,

---

### Post by Taemojitsu on 2009-12-16
ty for this, worked for me (several weeks ago). The listed wireless driver was ath9k before and after, but performance is much improved after this fix. Was trying to check if the text file edits were necessary, but tested by checking the driver instead of by performance and didn't know how to check for a version number for the driver, but as in the previous post my listed signal went up by about 30% and haven't seen the buffer overflow problems was getting before. At most it might have a few seconds of bad ping before going back to normal, whereas with the default Karmic driver would have to reselect the wireless network or even restart my laptop.

---

### Post by freetolio on 2009-12-23
> **Prosis said:**
> Someone named sebz_ posted a solution that worked fine!

I commented the ath_pci blacklist in /etc/modprobe.d/blacklist-ath_pci.conf.

You check if ath9k (or ath5k) is loaded in /etc/modules

echo ath9k | sudo tee -a /etc/modules

Then you install

linux-backports-modules-karmic and linux-backports-modules-wireless-karmic-generic (and linux-backports-modules-wireless-karmic-generic-pae if you can but I didn't need it)

Reboot and all should be fine! ;)

Thanks a bunch. :) This worked like a charm on the AR928X in my Gateway NV5214u.  This is so much easier than all the crap I used to have to go through with the Broadcom chip I had in another laptop.

I previously had all sorts of intermittent connection instabilities (in addition to poor reception) that were worst when downloading lots of packages.  After the fix, I installed Nexuiz to have the install itself serve as a torture test due to its size, and it worked great.  I also did a 7+GB file transfer locally (through an 802.11n router to a wired file server) and the transfer sustained a peak 7.5MB/sec (download) with nothing else going on on.

---

### Post by cordy74 on 2009-12-24
I have tried all of the suggestions in this post and many others and I am at a loss.  I have an Acer Aspire One D150 netbook which is using the Atheros AR5001 wireless card.  At first I could connect to my home network without any problem but my connection speeds were about 10% of what my other laptop is seeing.  Anybody have any suggestions on what to do next?  My internet is blazing fast when I hard wire into my router.  It seems as if Ubuntu just isn't talking to my wifi card like it should.

---

### Post by coffeecat on 2009-12-24
This thread is about the Atheros AR928X chipset using the ath9k driver in Karmic. You have a machine with a different chipset which uses a different driver in a different version of Ubuntu (Hardy - if your personal details are correct).

> **cordy74 said:**
> Anybody have any suggestions on what to do next?

Yes - do a forum search for threads relevant to your situation. Or, have a look at this link:

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

There are links through to specific intstructions for the various current versions of Ubuntu near the top of that page.

---

### Post by Lucien.Malavard on 2010-01-07
> **Prosis said:**
> Someone named sebz_ posted a solution that worked fine!

I commented the ath_pci blacklist in /etc/modprobe.d/blacklist-ath_pci.conf.

You check if ath9k (or ath5k) is loaded in /etc/modules

echo ath9k | sudo tee -a /etc/modules

Then you install

linux-backports-modules-karmic and linux-backports-modules-wireless-karmic-generic (and linux-backports-modules-wireless-karmic-generic-pae if you can but I didn't need it)

Reboot and all should be fine! ;)


Hi, sorry if I'm opening a closed thread. I recently installed Karmic 9.10 netbook remix on a Sony Vaio VPCW126AG (10" netbook) and replaced the Network Manager with WICD. WICD keeps dropping out of WPA2 wireless connections, and worse still, it fails to detect any wireless networks, after the machine wakes up from suspend mode suspend. 

I think this machine has an Atheros wireless chipset judging from Sony's website on the model. Does anyone know if the fix above works for this model here? 

Also what needs to be done at Prosis' step (quoted below), after checking if ath9k or ath5k?

> **Prosis said:**
> 
You check if ath9k (or ath5k) is loaded in /etc/modules

echo ath9k | sudo tee -a /etc/modules



Thanks for your time!

---

### Post by Malakai on 2010-01-18
> **scottro said:**
> For what it's worth, the backports didn't work for me.  What did work was using the wireless-compat drivers.  

[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

It's supposed to be better with the 2.6.32 kernel--with Fedora, using such a kernel, it seemed slightly better, but only slightly.  

Using iperf, which, I freely admit, can miss various other factors.

With Fedora and 2.6.32 kernel, I get about 21 MB/s.  With ArchLinux, though, I get about 40.  

With Ubuntu, with or without backports, I was getting about 1MB or less.  (That's not a typo, just one megabyte.)

Installing the compat-wireless drivers puts it up to around 40.

Apparently, this is a kernel, rather than distribution, issue, that started around the 2.6.29 or 2.6.30 kernel.  

It's the sort of thing that will seriously hurt Linux on netbooks, though one assumes that at least with preinstalled Linux netbooks, they test them before shipping.

Hello everyone! I just wanted to give a shout out to my good and dear friend scottro here! I have been wanting to use Ubuntu full time or as much as possible for a long time on my beloved little Asus 1000he, using the Atheros AR928X. But the wireless would sporadically disconnect, and xfer speeds/signal strength were extremely poor compared to windows 7.

Nothing I tried worked, I could use the netbook online, but any kind of download or xfer speeds were horrible. After following  this post to compat-wireless, and following the instructions on their website to unpack and install the drivers, my wireless on ubuntu is finally working respectively.

I use an ftp server on my main box so I can access all my files both on the netbook at my house over my home wireless G network (WRT54GL w/Tomato OS), and wherever I am around town while connected to the net.

Well even 10 feet away from the wireless router at home, I was getting under 100kb/sec transfer speeds from my main PC to my 1000he. Now with my netbook in its normal location (about 30ft through 3-4 walls on the other side of my house) with the new compat drivers, I am getting 2-2.5MB/sec xfer speeds. 

I used the newest highest version number of compat drivers, from the stable page, and followed the install instructions exactly, note I needed to install patch and patchutils hehe, gentoo base installed packages, or lack thereof. is funny!

Also my bluetooth mouse which worked perfectly in windows 7 (syba connectland bluetooth mouse, 15 dollars at newegg) was constantly disconnecting. It seems that the compat drivers also replaced the stock bluetooth drivers, cuz now my bluetooth mouse is working absolutely perfectly as well.

Again thank you again scottro. I do not actually know you, as I am very new to Ubuntu (8+ year Gentoo user) and its forums; but I was probably less than a day from wiping out my Ubuntu partition and rewriting the MBR on my main hard drive to remove GRUB and thus ubuntu forever. Well at least until eeebuntu 4.0 came out.

Now both of my major complaints about Ubuntu on my 1000he, bluetooth issues and extremely poor wireless performance, have both been solved. And it was quite simple to do, and required less than an hour. I am getting more and more comfortable with Ubuntu, and I can continue to use it and learn more about it, now that my mouse and wireless works properly.

Check.. still downloading a tv series from my main pc (ST TNG season 4... yes I am a geek hehe) currently at 2.3mb/sec. I can get up to (and even a hair over on rare occasions) 3mb/sec with flashfxp or filezilla on windows 7, but this is close enough and more than fast enough for normal internet downloads and file xfers over my wireless g network. Before web pages loaded annoyingly slowly, regular internet downloads were going at sub-1kb/sec (yar dont you hate when a file is downloading at like 254 bytes per second lol!). Now all is fine and perfectly usable.

Thanks again scottro and all the compat-wireless coders/bug testers/ect! Very very nice drivers, hope over time they eventually overtake windows 7. There is a lot to love about Linux nowadays, god its so much nicer looking than it was when I started with Linux many years ago. I was sad that the ever popular Ubuntu just would not work right with the 1000HE when I frequently see that it is supposed to be 1000% compatible with Ubuntu 9.10.


Now the next, and one of the last, things I need to get working right is soe kind of eee power management software. I have tried eee-control and eee-acpi-utilities or whatever, and neither will install or function right.

Gnome itself has the little cpu monitor taskbar applet that allows adjustment of the cpu speed, which is nice and will tide me over till now, but I would prefer a power management interface ala Eeebuntu had. Eeebuntu 3 however had other problems that forced me to not be able to use it on this box. I use this netbook all day for work and i could not have it unstable or breaking on update ala Eeebuntu3 was doing.

Thanks!! Im so happy now, I missed the command line and real package management after using Win7 almost exclusively on all my boxes since the RTM first hit the scene ;)

---

### Post by 2hot6ft2 on 2010-01-23
Thanks Prosis and a thanks to sebz_ the one you got the info from.

I didn't even get enough signal before where I am right now for the internal card to connect. Now it connects and has 47% signal. Much better.:D

I just did blacklisting the ath_pci blacklist in /etc/modprobe.d/blacklist-ath_pci.conf and installed the 2 backports linux-backports-modules-karmic and linux-backports-modules-wireless-karmic-generic.

For those that aren't sure how to do this. Open a terminal
Applications > Accessories > Terminal
and put in
```
gksu gedit /etc/modprobe.d/blacklist-ath_pci.conf
```
Hit Enter
Type in your password and hit Enter
When it opens add "# " before ath_pci blacklist
so it looks like this
> # ath_pci blacklist
Hit Save and close it
Then in the terminal which will still be open put in:
```
sudo apt-get update
```
Hit Enter
After it finishes then use:
```
sudo apt-get install backports linux-backports-modules-karmic linux-backports-modules-wireless-karmic-generic
```
When it finishes you can close the terminal and reboot.

My laptop that I did it on.
HPG60-125NR
Atheros AR5009 (with AR928X)
:popcorn:

---

### Post by adi_sinha2000 on 2010-01-27
> **Malakai said:**
> Hello everyone! I just wanted to give a shout out to my good and dear friend scottro here! I have been wanting to use Ubuntu full time or as much as possible for a long time on my beloved little Asus 1000he, using the Atheros AR928X. But the wireless would sporadically disconnect, and xfer speeds/signal strength were extremely poor compared to windows 7.

Nothing I tried worked, I could use the netbook online, but any kind of download or xfer speeds were horrible. After following  this post to compat-wireless, and following the instructions on their website to unpack and install the drivers, my wireless on ubuntu is finally working respectively.

I use an ftp server on my main box so I can access all my files both on the netbook at my house over my home wireless G network (WRT54GL w/Tomato OS), and wherever I am around town while connected to the net.

Well even 10 feet away from the wireless router at home, I was getting under 100kb/sec transfer speeds from my main PC to my 1000he. Now with my netbook in its normal location (about 30ft through 3-4 walls on the other side of my house) with the new compat drivers, I am getting 2-2.5MB/sec xfer speeds. 

I used the newest highest version number of compat drivers, from the stable page, and followed the install instructions exactly, note I needed to install patch and patchutils hehe, gentoo base installed packages, or lack thereof. is funny!

Also my bluetooth mouse which worked perfectly in windows 7 (syba connectland bluetooth mouse, 15 dollars at newegg) was constantly disconnecting. It seems that the compat drivers also replaced the stock bluetooth drivers, cuz now my bluetooth mouse is working absolutely perfectly as well.

Again thank you again scottro. I do not actually know you, as I am very new to Ubuntu (8+ year Gentoo user) and its forums; but I was probably less than a day from wiping out my Ubuntu partition and rewriting the MBR on my main hard drive to remove GRUB and thus ubuntu forever. Well at least until eeebuntu 4.0 came out.

Now both of my major complaints about Ubuntu on my 1000he, bluetooth issues and extremely poor wireless performance, have both been solved. And it was quite simple to do, and required less than an hour. I am getting more and more comfortable with Ubuntu, and I can continue to use it and learn more about it, now that my mouse and wireless works properly.

Check.. still downloading a tv series from my main pc (ST TNG season 4... yes I am a geek hehe) currently at 2.3mb/sec. I can get up to (and even a hair over on rare occasions) 3mb/sec with flashfxp or filezilla on windows 7, but this is close enough and more than fast enough for normal internet downloads and file xfers over my wireless g network. Before web pages loaded annoyingly slowly, regular internet downloads were going at sub-1kb/sec (yar dont you hate when a file is downloading at like 254 bytes per second lol!). Now all is fine and perfectly usable.

Thanks again scottro and all the compat-wireless coders/bug testers/ect! Very very nice drivers, hope over time they eventually overtake windows 7. There is a lot to love about Linux nowadays, god its so much nicer looking than it was when I started with Linux many years ago. I was sad that the ever popular Ubuntu just would not work right with the 1000HE when I frequently see that it is supposed to be 1000% compatible with Ubuntu 9.10.


Now the next, and one of the last, things I need to get working right is soe kind of eee power management software. I have tried eee-control and eee-acpi-utilities or whatever, and neither will install or function right.

Gnome itself has the little cpu monitor taskbar applet that allows adjustment of the cpu speed, which is nice and will tide me over till now, but I would prefer a power management interface ala Eeebuntu had. Eeebuntu 3 however had other problems that forced me to not be able to use it on this box. I use this netbook all day for work and i could not have it unstable or breaking on update ala Eeebuntu3 was doing.

Thanks!! Im so happy now, I missed the command line and real package management after using Win7 almost exclusively on all my boxes since the RTM first hit the scene ;)

I am sorry for opening up an old thread that has been designated as solved, however it best fits the problem that I have. 

1. Backports dont work for me . I have them installed right now and though my wifi network is stable I can not get speeds more than 100kbps as mentioned above. 

2. Compat wireless - I can compile em succesfully but (theres always a but) on a modprobe on the ath9k I get 

" [1.117716] device-mapper: multipath: version 1.1.0 loaded
 [1.117724] device-mapper: multipath round-robin: version 1.0.0 loaded
 [11.844969] ath: disagrees about version of symbol wiphy_apply_custom_regulatory
 [11.844981] ath: Unknown symbol wiphy_apply_custom_regulatory
 [11.845304] ath: disagrees about version of symbol freq_reg_info
 [11.845313] ath: Unknown symbol freq_reg_info " 

and that is the end of that. I have tried using atleast 4 different tar balls from compat wireless . Same problem each time . 

3. mad wifi - this really will sound weird . it compiles , no errors . I am supposed to add ath_pci , but theres no such module made after the compilation and installation . 

4. Ndiswrapper - well again it does work - with the 64 bit XP and 64 vista drivers (not the windows 7 64 bit) but on loading ndiswrapper in the dmesg I get the error "ndiswrapper (iw_set_auth:1602): invalid cmd 12" though it still loads ndiswrapper thereof . the speed at this point is worse than the ath9k . 


It has been about 2 days , around 20 hours of time wasted and still nothing. 

Any help would be appreciated

---

### Post by yevgeni on 2010-01-28
Using the wireless compat fix worked for me with the ath9k driver.

I encountered build problems, but that was fixed by un- and re-installing my kernel headers. No dropped connection and great speed now!

---

### Post by kd8cgo on 2010-02-12
I just wanted to report that I was having similar problems on my Asus 1000HE netbook, and this fix has worked wonderfully as noted above.  I just ran an iperf on the link through a couple walls in my home to a WRT160nl router and averaged 60.2Mbps over 120 seconds which is 3x faster than my g-only based laptop sitting right next to it - I wasn't expecting the n speeds under Linux, but was pleasantly surprised.  Under connection information in Network Manager the link speed reports as 'unknown' however.

---

### Post by hislordship on 2010-02-21
Hello, sorry for adding to this endless thread that is supposed to be solved. I have absolutely no experience on Linux and just don't manage to follow the instructions given here. Can so. dumb it down for me please?

I have an Acer Extensa 5235 with Atheros AR928x ath9k chipset. The wireless connection is very weak and unstable (it drops sporadically, especially when downloading bigger chunks of data).

Thanks for help

---

### Post by bkratz on 2010-02-21
> **hislordship said:**
> Hello, sorry for adding to this endless thread that is supposed to be solved. I have absolutely no experience on Linux and just don't manage to follow the instructions given here. Can so. dumb it down for me please?

I have an Acer Extensa 5235 with Atheros AR928x ath9k chipset. The wireless connection is very weak and unstable (it drops sporadically, especially when downloading bigger chunks of data).

Thanks for help



This really should be all you need to do---it has worked for a lot of people.

[http://ubuntuforums.org/showpost.php?p=8599246&postcount=5](http://ubuntuforums.org/showpost.php?p=8599246&postcount=5)

---

### Post by hislordship on 2010-02-21
Thank you mate, that's very nice to have replied so fast. I have searched for these packages in synaptic but they are not there. How do you install them?

---

### Post by coffeecat on 2010-02-21
> **hislordship said:**
> I have searched for these packages in synaptic but they are not there.

Have another look - they should be there. The package linux-backports-modules-karmic-generic is in the Main repository, and linux-backports-modules-wireless-karmic-generic is in the Universe repository. In Synaptic, check Settings > Repositories to make sure you have both those repositories enabled. I'd be amazed if they're not.

Also - have you done a package metadata refresh since you installed? You have to have a working internet connection and then click on "Reload" in Synaptic (or 'Check' in Update Manager). If you haven't done an update or refreshed the metadata, the package manager won't know about these packages.

If your Atheros wireless is too unreliable without the backports to do a reliable refresh/update, use an ethernet connection until you've installed the backports packages.

---

### Post by bkratz on 2010-02-21
> **hislordship said:**
> Thank you mate, that's very nice to have replied so fast. I have searched for these packages in synaptic but they are not there. How do you install them?

Sorry I wasn't at the computer, but it looks like coffeecat took it over and gave you the correct information. Thanks go to coffeecat.
When this works (and I am confident that it will) please return and give us an update and remember to mark the thread solved (in the tools above) when it is.


Sorry, I just noticed that you had posted on a thread that was already solved, but return and let us know the outcome.

---

### Post by coffeecat on 2010-02-21
> **bkratz said:**
> Sorry I wasn't at the computer, but it looks like coffeecat took it over

I wasn't intending to muscle in, but this thread is still on my subscribe list. And thanks to you too for linking to one of my posts. It's nice to know that at least one person has taken notice of something I've said. :lol:

It's a pity this backports fix isn't more widely known. I've come across threads from people resorting to madwifi and (shudder) ndiswrapper. The good news is that this chipset will work better out of the box in Lucid, if my experience of Lucid alpha is anything to go by.

---

### Post by hislordship on 2010-02-26
sorry to say..I'm still an absolute beginner with linux and apparantly too daft to fix this myself.

the funny thing is that I've installed a Mandriva Linux and the wireless works perfectly out of the box... I wish I could fix this so I can keep using Ubuntu...

---

### Post by hislordship on 2010-02-26
It's worked! Thank you, I found them! If you ever get to Berlin, you two have a free dinner on my bill!
Dankeschön!

---

### Post by blackened07 on 2010-03-02
It really worked for me too, the connection doesn't dropp anymore, thanks a lot

Regards.

---

### Post by Pernilio on 2010-03-18
> **Prosis said:**
> 

linux-backports-modules-karmic and linux-backports-modules-wireless-karmic-generic (and linux-backports-modules-wireless-karmic-generic-pae if you can but I didn't need it)

Reboot and all should be fine! ;)

It's works!!

I have a Notebook Asus K50IJ with  AR9285 Wireless Network Adapter (PCI-Express)

Thanks

---

### Post by euriconeto on 2010-03-22
Hi All,

I have a similar problem. And a few others too... After completely installing karmic on a HP dv6 2120tx I noticed a few bugs.

1- Wireless doesn't work (the network manager only displays "enable networking" but not "enable wireless). I get no signal at all.
2- My mobile key (a Huawei 3 mobilebroadband from Australia) is recognised, but the appled does not allow me to connect to it.
3- The speakers do not stop working when I plug my headphones.
4- Speakers are doing a weird noise when I turn off the laptop
5- The screen gets buggered when turning off as well (comes back nicely though)

If you know how to help me or need more information in order to help, please give me a step by step on how to get the info you need from the terminal, as I don't know yet how to run these things.

Thanks!
Eurico

---

### Post by narnie on 2010-04-07
Adding the backport packages worked for me for my Acer Aspire One D250-1584

When you first boot your machine, right click on the network manager applet and unselect enable wireless followed by unselecting enable networking. Now you will be able to type into terminal without having to worry about it going down while ur typing in the terminal (but do this step quickly).

With the directions below, we will get these:

[B]linux-backports-modules-karmic and linux-backports-modules-wireless-karmic-generic (and linux-backports-modules-wireless-karmic-generic-pae)
[/B]
This generates a script to download them on any working linux machine. To use it, move to whatever working directory you want to use, then run:

```
$ echo '#!/bin/sh
> wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.31-20-generic_2.6.31-20.58_i386.deb
> wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.31/linux-backports-modules-2.6.31-20-generic_2.6.31-20.22_i386.deb
> wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.31-20-generic-pae_2.6.31-20.58_i386.deb
> wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.31/linux-backports-modules-2.6.31-20-generic-pae_2.6.31-20.22_i386.deb
> wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-karmic-generic_2.6.31.20.33_i386.deb
> wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-karmic-generic-pae_2.6.31.20.33_i386.deb
> wget -c http://us.archive.ubuntu.com/ubuntu/pool/universe/l/linux-meta/linux-backports-modules-wireless-karmic-generic_2.6.31.20.33_i386.deb
> wget -c http://us.archive.ubuntu.com/ubuntu/pool/universe/l/linux-meta/linux-backports-modules-wireless-karmic-generic-pae_2.6.31.20.33_i386.deb' > atheros_fix
```

This makes a new file called atheros_fix

then

```
$ chmod a+x atheros_fix
```

then 
```
$ mkdir atheros
$ mv atheros_fix atheros/
$ cd atheros
$ ./atheros

```

This will download the files into the atheros dir

When this is through, do:

```

$ sudo mv *.deb /var/cache/apt/archives/
$ sudo aptitude install linux-backports-modules-karmic linux-backports-modules-wireless-karmic-generic linux-backports-modules-wireless-karmic-generic-pae


```

Then reboot.

Wireless should be working at this point, but I bet your system isn't up to date cause the wireless hasn't been working. If that is the case, do:
```

$ sudo aptitude update && sudo aptitude full-upgrade
```

Might have to reboot, but you should have a working wireless now.

---

### Post by b.lindahl on 2010-04-26
I had the same problem and got frustrated last night and upgraded from Ubuntu 9.10 to 10.04 but that didn't help much. I guess the upgrade process cleaned out something that wasn't as it should because when I the mentioned linux-backports-modules- for lucid and rebooted, it worked just fine.

So the solution also applies for Ubuntu 10.04 lucid.

Thanks a bunch!

---

### Post by Linxuxslate on 2010-04-26
Not Helping here either.

Sony Vaio PCG-61411L

Realevant line from lspci -v:
```
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```
Wifi does work, I am using it to post this, but I am getting terrible throughput.  A few kb/s, and frequent pauses.  can't even do voice only VoIP.  I am also showing only 1 or 2 bars signal ~30%, and I am in the same room with my router.  I get occasional disconnects, but the throughput is the problem.

It's also the same at a local cafe with free Wifi. 

Tried installing backports, and tried commenting out the line in /etc/modprobe.d/blacklist-ath_pci.conf

Tried each combination of the backports and commenting out the blacklist line.

I have not tried compat-wireless or ndiswrapper.

This is a fresh install of 9.10, and the problem was there before I did updates.  I had to connect wired ethernet to do the updates.

---

### Post by Sean Hayes on 2010-06-03
I'm running Ubuntu 10.04 64 bit. I tried installing the wireless backports module, but then my wireless stopped working completely. I also posted a thread here but never got a response: [http://ubuntuforums.org/showthread.php?t=1477539](http://ubuntuforums.org/showthread.php?t=1477539)

---

### Post by p_jabilgas on 2010-06-03
Good day, to all, want to ask what is the difference between adhoc networking to peer to peer.point to point networking... is it the same functions... thanks...

---

### Post by Sean Hayes on 2010-06-03
> **p_jabilgas said:**
> Good day, to all, want to ask what is the difference between adhoc networking to peer to peer.point to point networking... is it the same functions... thanks...

You should create a new thread, your question is unrelated to this topic.

---

### Post by nirvblakr on 2010-07-28
I have an Acer Ferrari One with an Atheros AR928X wifi adapter.  On the Linux Mint Helena live CD, the wifi was working with no problems so I decided to install the OS.  After installation, the Wifi was working alright and my network was detected.  When I tried opening Firefox, the signal just dropped and the window asking the password to my network keeps popping.  When I enter the password, the icon just does the swirling motion and can't detect my network. 

I then hooked my netbook to a LAN cable and updated everything from there.  After the update and reboot, the wifi worked flawlessly with no problems whatsoever.  Just sharing my experience. ;)

---

### Post by MikeyDL on 2010-07-29
Hi,

I've got the same problem, but when I do an

```
sudo apt-get install linux-backports-modules
```

or 

```
sudo apt-get install linux-backports-wireless-karmic-general
```

I get a "can't find package error message.  I guess it's not part of the 10.04 repository.  Any tips on what repository I need to connect to or add to get this installed on my lappy?

---

### Post by Sean Hayes on 2010-07-29
> **MikeyDL said:**
> Hi,

I've got the same problem, but when I do an

```
sudo apt-get install linux-backports-modules
```

or 

```
sudo apt-get install linux-backports-wireless-karmic-general
```

I get a "can't find package error message.  I guess it's not part of the 10.04 repository.  Any tips on what repository I need to connect to or add to get this installed on my lappy?

Try linux-backports-modules-wireless-lucid-generic

---

### Post by MikeyDL on 2010-07-29
Thanks that seemed to install.  Did a reboot, deleted the auto connect settings, reconnected and testing it out now!

I take it when you run the package it installs those backport drivers as your default network system?

---

