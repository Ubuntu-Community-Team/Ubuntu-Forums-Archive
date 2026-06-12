---
title: "Atheros AR9285 Wireless"
date: 2009-10-09
forum: Networking &amp; Wireless
---

### Post by Wrathe on 2009-10-09
If you have an Atheros AR9285 wireless card on Ubuntu 9.04 and cannot get it working, this is for you.
 
Ubuntu did not automatically detect my card (AR9285) and spent many hours trying to figure this out. The purpose of this is to show you how to get your Atheros AR9285 Wireless Network Adapter working without those many hours of finding the wrong answers.
 
It is very simple.
 
Download a stable release (I downloaded compat-wireless-2.6.30.tar.bz2) from the following website to your desktop:
[http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/)
 
Open up Terminal and type:
> cd Desktop
tar -xf compat-wireless-2.6.30.tar.bz2
cd compat-wireless-2.6.30
make
sudo make install
sudo make unload(It tells you all this on the website that you download it from.)
 
Restart.
Click on the wireless icon in the top right corner of the screen and logon to your wireless network.
 
Fin! :guitar:
[COLOR=royalblue] [/COLOR]
*_[COLOR=darkred]Edit: Apparently the bleeding edge drivers are faster. I have not tested them though.[/COLOR]_*

---

### Post by t0mppa on 2009-10-09
I guess you missed the part on the page about simply installing the linux-backports-modules-jaunty (replace jaunty with karmic or hardy or whichever version you happen to use) with apt-get or Synaptic, since that's a version of the latest compat-wireless prebuilt by the Ubuntu kernel team.

---

### Post by Wrathe on 2009-10-09
The one that I downloaded was i386 and did not support AMD64.

---

### Post by muryan on 2009-10-09
I really needed your post - It works soooo fine!!!!!!! =) Thank you very very much


> **Wrathe said:**
> If you have an Atheros AR9285 wireless card on Ubuntu 9.04 and cannot get it working, this is for you.
 
Ubuntu did not automatically detect my card (AR9285) and spent many hours trying to figure this out. The purpose of this is to show you how to get your Atheros AR9285 Wireless Network Adapter working without those many hours of finding the wrong answers.
 
It is very simple.
 
Download a stable release (I downloaded compat-wireless-2.6.30.tar.bz2) from the following website to your desktop:
[http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/)
 
Open up Terminal and type:

(It tells you all this on the website that you download it from.)
 
Restart.
Click on the wireless icon in the top right corner of the screen and logon to your wireless network.
 
Fin! :guitar:

---

### Post by g8rjoe on 2009-10-14
> **Wrathe said:**
> The one that I downloaded was i386 and did not support AMD64.
Sorry, noob here.  Worthless as the next.  I followed your instructions, Mr. Wrathe, and I guess I must be missing something here.  I have an Acer notebook with AMD Athlon 64.  Loaded the latest stable release, untar'd it, and followed the sudo commands.  A lot of stuff happened on the term window.  Yet, when I restarted, I did not see the wireless in the top right corner.  

Could I have really screwed up something this simple?  Don't answer that.

Any suggestions?

joe

---

### Post by pcolamar on 2009-10-15
> **t0mppa said:**
> I guess you missed the part on the page about simply installing the linux-backports-modules-jaunty (replace jaunty with karmic or hardy or whichever version you happen to use) with apt-get or Synaptic, since that's a version of the latest compat-wireless prebuilt by the Ubuntu kernel team.


I second t0mppa suggestion, it worked for my HP DV2-1130ef with the Atheros card on Jaunty AMD-64bits edition.

I installed the Jaunty backport module (using an eth0 connection):

*sudo apt-get install linux-backports-modules-jaunty*

and restarted the laptop.

Perfectly working now

-R
Palmer

---

### Post by Wrathe on 2009-10-19
I tried that.  It says:

> Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package linux-backports-modules-jaunty

I also downloaded  linux-backports-modules-jaunty-generic_2.6.28.11.15_amd64.deb It says:

> Error: Dependency is not satisfiable: linux-backports-modules-2.6.28-11-generic

(I just tried that since I had to reinstall Ubuntu.)
The way I did it worked fine for me.

---

### Post by amightyo on 2009-10-23
WLAN
run this command and wlan will work
Code:
```

sudo apt-get install linux-backports-modules-jaunty
```

A solution posted by User (KoKuToru)
[http://ubuntuforums.org/showthread.php?t=1204735](http://ubuntuforums.org/showthread.php?t=1204735)

It worked for me:)

---

### Post by jord_hollebekkers on 2009-10-25
i registered this account 1 minute ago just to thank you! it worked and ive been trying for ages!

---

### Post by emmccre on 2009-10-28
I spent hours trying to figure out my wireless issues using other advice about installing the linux-backports files, and since I had no internet connection whatsoever, this was amazing!  It worked perfectly and took only a few minutes, and I am very glad you posted this... I am not exactly a linux nube, but I am used to it working without me having to mod it, so anyway, thanks again so much.  Definitely recommend this for EeePc users...

---

### Post by katiejo225 on 2009-11-05
[quote=Wrathe;8127935]I tried that.  It says:

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package linux-backports-modules-jaunty 			 		


That is exactly what it is saying to me too that it couldn't find package linux-backports-modules-jaunty..... I am soooo new to this that I am sure it is something on my end. I just got an Asus EEE PC 1005 with XP, and wanted to try this whole Linux thing out to prove to my nerdy bf that I can at least appear to know what I am doing with computers :P Anyhow, I downloaded UNR from Wubi-install.org and everything went fine except it does not recognize my wireless connection as it does when i switch back to xp. It took me forever to figure out what in the world a terminal was so i could enter all these codes into it, but I figured it out! But nothing has worked to make it see my wireless card. So can anyone help me out?? I don't know what to do next?? Please dumb down your answers as much as possible, thank you!!!

---

### Post by Degenetron on 2009-11-12
Finally! It works :) Used the command in the second post here with karmic and it installed fine. after a reboot the wireless was up and running. Thanks a lot :)
```

sudo apt-get install linux-backports-modules-karmic
```

---

### Post by dummiebeginner on 2009-11-13
It worked for me too with an Atheros AR5700EG in Karmic.

A million thanks!!!

---

### Post by mykeecdn on 2009-11-15
Thank you Wrathe, your instructions were just what I needed - I could not use Synaptic since I had no networking (my onboard eth wasnt working either) so I just downloaded the files, dumped over using a USB key, and it worked great!

Thanks again for helping the community!

/\/\ike

---

### Post by jeannacav on 2009-11-19
> **Wrathe said:**
> If you have an Atheros AR9285 wireless card on Ubuntu 9.04 and cannot get it working, this is for you.
 
Ubuntu did not automatically detect my card (AR9285) and spent many hours trying to figure this out. The purpose of this is to show you how to get your Atheros AR9285 Wireless Network Adapter working without those many hours of finding the wrong answers.
 
It is very simple.
 
Download a stable release (I downloaded compat-wireless-2.6.30.tar.bz2) from the following website to your desktop:
[http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/)
 
Open up Terminal and type:
(It tells you all this on the website that you download it from.)
 
Restart.
Click on the wireless icon in the top right corner of the screen and logon to your wireless network.
 
Fin! :guitar:
Thank you wrathe,

I know how much time you saved me and I appreciate the help.
I had to download it from this acer 5515 which worked seamlessly at the install, and transfer it with a flash stick to the new acer 5517 which has (had) neither wired or wireless.

I now have the leisure to get the wired part fixed. 
But later for that.
First... thank you a lot.

jeanna

---

### Post by jeannacav on 2009-11-20
> **Wrathe said:**
> If you have an Atheros AR9285 wireless card on Ubuntu 9.04 and cannot get it working, this is for you.
 
Ubuntu did not automatically detect my card (AR9285) and spent many hours trying to figure this out. The purpose of this is to show you how to get your Atheros AR9285 Wireless Network Adapter working without those many hours of finding the wrong answers.
 
It is very simple.
 
Download a stable release (I downloaded compat-wireless-2.6.30.tar.bz2) from the following website to your desktop:
[http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/)
 
Open up Terminal and type:
(It tells you all this on the website that you download it from.)
 
Restart.
Click on the wireless icon in the top right corner of the screen and logon to your wireless network.
 
Fin! :guitar:

OK fin,

Here is the continuation.
I got this to work last night.
Then using the wireless, I used the update manager.
I had to restart and when I did...
Then it- the wireless- broke.

I can now get the wired to work (I think this was a fix available from the update manager) but the wireless is not allowed.

I am supplying some terminal information.
I decided to run through the same paces that I did yesterday to get this stable file installed, since when it was freshly installed, it worked.


--------------------
...~/Desktop$ cd compat-wireless-2.6.30
...~/Desktop/compat-wireless-2.6.30$ make
make: Nothing to be done for `all'.
...~/Desktop/compat-wireless-2.6.30$ make install
FATAL: Could not open /lib/modules/2.6.28-16-generic/modules.dep.temp for writing: Permission denied
make: *** [uninstall] Error 1
--------------------

So, I think I am against a wall, here.
But, I think there is a solution somewhere...

Also, the only difference I could see in the bios between these 2 machines (as far a internet goes) is this 5517 has the Atheros network Boot agent, and the 5515 has the Realteck boot agent. Maybe that makes a difference??

down this page, someone did a linux-backports-modules install or something.
When I do that I get:

-------------
~$ apt-get install linux-backports-modules
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
--------------
ummmm I dunno.
I am getting permissions denied for regular things too. I am beginning to be alarmed.



thanks,

jeanna

---

### Post by t0mppa on 2009-11-20
Permission denied is just a message saying that you can't accomplish whatever you tried to do with your normal user account, i.e., you need the elevated privileges of root account and thus have to use *sudo* in front of the command.

---

### Post by Wrathe on 2009-11-20
I think the backport will work if the system is up to date.

---

### Post by neoanderthal on 2009-11-20
Can anyone confirm that the AR9285 actually works continuously after either method (backports or the OP solution)? I have a Toshiba NB205, and every linux distro I've tried (Moblin 2.1, OpenSuSE 11, SLED 11.1, Fedora 11, Debian 5, Ubuntu 9.04) drops my wireless connection like a hot potato; the card will connect, then drop after a variable amount of time, reconnect, drop again... ad nauseum. It works fine under the various and sundry Windows variants, but I'd rather run something else other than Windows on it if possible.

---

### Post by jeannacav on 2009-11-20
> **t0mppa said:**
> Permission denied is just a message saying that you can't accomplish whatever you tried to do with your normal user account, i.e., you need the elevated privileges of root account and thus have to use *sudo* in front of the command.

thank you t0mppa,
What is alarming me is that after I get that message, I am NO LONGER able to type anything.
I got around it one time by ignoring the 'sudo' and just giving the command, but it only worked that one time.

If you have any ideas on how to get me to work as the sudo, please let me know.

@Wrathe,
It was the backports command that made me use the sudo. I had to give up at that point.

BTW would you do me a favor and change the [solved] back to [ubuntu] until this wireless problem gets fixed?

I ask that because this thread is really a precursor for what needs to follow. = the fix, and the programmers who can fix this need to not ignore it, which they might do if they see the [solved] label. thanks.

@neoantherthal,

In fact, it seems to be doing that here as well.
There is a light that blinks throughout the booting process, but cuts out after the boot is finished.
But that said, I did have the wireless working **_until I added the latest updates and rebooted. Since then it has never stayed connected after boot._**



thank you,

jeanna

---

### Post by t0mppa on 2009-11-21
> **jeannacav said:**
> thank you t0mppa,
What is alarming me is that after I get that message, I am NO LONGER able to type anything.
I got around it one time by ignoring the 'sudo' and just giving the command, but it only worked that one time.

If you have any ideas on how to get me to work as the sudo, please let me know.

Can't type anything after the *permission denied* message? That sounds very odd. Or did you mean after using sudo? If the latter, using sudo prompts you for your password, which isn't printed on the screen for obvious safety reasons.

Since it actually prints nothing (not even *'s, so anyone else watching over your shoulder can't figure out how long your password is) on the screen when you're typing in your password, it might seem like you're unable to type anything, but once you've typed your password and press enter, it continues doing its job, granted your password was correct.

> **jeannacav said:**
> @Wrathe,
It was the backports command that made me use the sudo. I had to give up at that point.

BTW would you do me a favor and change the [solved] back to [ubuntu] until this wireless problem gets fixed?

I ask that because this thread is really a precursor for what needs to follow. = the fix, and the programmers who can fix this need to not ignore it, which they might do if they see the [solved] label. thanks.


This isn't a forum read actively by programmers, at least not in the role of fixing things reported broken here. If you want to file a bug report, you should go to [Launchpad]("https://launchpad.net/ubuntu") instead.

This forum simply consists of helpful people who spend some of their free time helping others to get things working, none of whom (as a rule of thumb, of course they might be some exceptions) has any official ties to Linux, Ubuntu or the packages used in it. To have a solved tag in this thread simply means that since this is a guide, it isn't a problem left unsolved.

---

### Post by jeannacav on 2009-11-21
> **t0mppa said:**
> Can't type anything after the *permission denied* message? That sounds very odd. Or did you mean after using sudo? If the latter, using sudo prompts you for your password, which isn't printed on the screen for obvious safety reasons.

Since it actually prints nothing (not even *'s, so anyone else watching over your shoulder can't figure out how long your password is) on the screen when you're typing in your password, it might seem like you're unable to type anything, but once you've typed your password and press enter, it continues doing its job, granted your password was correct.

Thank you.
Perhaps I stopped before finishing. I will try again.


> This isn't a forum read actively by programmers, at least not in the role of fixing things reported broken here. If you want to file a bug report, you should go to [Launchpad]("https://launchpad.net/ubuntu") instead.

This forum simply consists of helpful people who spend some of their free time helping others to get things working, none of whom (as a rule of thumb, of course they might be some exceptions) has any official ties to Linux, Ubuntu or the packages used in it. To have a solved tag in this thread simply means that since this is a guide, it isn't a problem left unsolved.

Oh I see.
I love people helping people, so that is wonderful.
I have used launchpad, so now I see the distinction.

Thank you,

jeanna

---

### Post by fungiblename on 2009-11-24
Thank you Wrathe! I can now get 100% signal strength on my Asus 1005HA (I would never get above 70-80%, even 3 feet from a router) - however, for my particular machine, I needed to use the "bleeding edge" drivers. See 
[http://ubuntuforums.org/showpost.php?p=8376514&postcount=5](http://ubuntuforums.org/showpost.php?p=8376514&postcount=5) 

To all the posters who had good luck with the backports, I'm happy for you, but they did not work on WPA networks for me. WEP was slightly better - although I would even lose a wireless connection from my MacBook (sharing a 3G card from the MacBook in a remote area) with the machines almost touching; only unsecured networks were problem-free. Now (fingers crossed) everything seems to be working as it should.

---

### Post by gradyjohnson on 2009-12-03
I have the same problem with my Atheros AR9285 Wireless card on Ubuntu 9.4 and would love to use one of the methods here. Unfortunately my eth0 (AR8132) is misidentified by 9.4, so I don't have the option of using "sudo apt-get install linux-backports-modules-jaunty". I tried the original post by Wrathe. I successfully downloaded the file on my other computer, then copied it to my laptop. I did the make, make install, and make unload. After a restart I didn't think it worked because it took several minutes, then a list of available wireless networks poped up. Fantastic!! I have been working on this for a couple of days. Now to get the wired network up. But the wireless was the most important!
Thanks Wrathe!
Update 1:  After being able to apply all the updates from 2.6.28-11 to 2.6.28-16 using the wireless network, my wired eth0 started working!
Update 2: (12-4-09): After I updated the kernel to 2.6.28-16, the wired connection worked but the wireless stopped working. So I re-installed Ubuntu 9.4. Then again I had no networking. I went through the compat-wireless-2.26.30 procedure again, and wireless worked. Using the wireless network I installed available Ubuntu 9.4 upgrades, which brought my kernel up to 2.6.28-17. I restarted the system, and wired worked but wireless no longer worked. So I went through the compat-wireless-2.26.30 procedure again, and now wireless is working. So now both wired (eth0) and wireless are working. I am going to keep the compat-wireless-2.26.30 package handy in case I need it again after updating Ubuntu 9.4, because I like 9.4 a lot better than 9.10.

---

### Post by jeannacav on 2009-12-03
People have asked me about my kernel.

It might make a difference...


And it might not.
Mine wireless worked for a while, but even though I have 100% signal, I cannot get on today. My system has tried 7 or 8 times.

There is something wrong here, but I guess it is hard to find... or solve.

jeanna

---

### Post by maq21 on 2009-12-07
I had ubuntu 9.04 and the wireless was working ok on kernel 2.6.28-15 but after updating the kernel to 2.6.28-16 and 2.6.28-17 the wireless did not work, when I made "lspci | grep -i wireless " it did not show any thing so I modefied the menu.list in the /boot/grub to boot using the kernel 2.6.28-15 and it worked again, I cannot work on the new kernels. 
Do u have any ideas ???

---

### Post by tenfishsticks on 2009-12-16
Hi, Wrathe.

i just created a page on the Ubuntu Support pages for this wifi card.  Please look it over and see if you approve!

You can find it here: [https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285](https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285)

---

### Post by svtfmook on 2009-12-17
i'm still having problems with my wifi AR9285 on studio 9.10 64bit.

out of the box, it recognised my wifi card.  however, when i enable it, it is requiring my to enter an ssid and configure ip/dns/etc.  my wifi access point will not show up in wifi radar.

i've tried this solution as well as the backports.  but when i try backports and this solution, i don't even see a wifi adapter under network.

what else could i try and/or what could i be missing?

---

### Post by vinny.usestrict on 2009-12-18
> **t0mppa said:**
> I guess you missed the part on the page about simply installing the linux-backports-modules-jaunty (replace jaunty with karmic or hardy or whichever version you happen to use) with apt-get or Synaptic, since that's a version of the latest compat-wireless prebuilt by the Ubuntu kernel team.

For Ubuntu 9.10, linux-backports-modules-karmic didn't work. After *make*ing and installing the new drivers, it works at 100%. I definitely recommend installing the drivers from linuxwireless.org.

---

### Post by dizzyhaha on 2010-01-22
i got to this point:

Download a stable release (I downloaded compat-wireless-2.6.30.tar.bz2) from the following website to your desktop:
[http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/)

downloaded and extracted it, but  am not quite following the instructions on the linux wireless site:

code:

cd /path/to/compat-wireless-2.6.32-rc5
./scripts/driver-select <driver-name>
make
sudo make install

the last part makes no sense to me.  i am using comwireless-2.6.30, so i
 can figure out to sub in that name in the code, but i am lost starting 
with the period, and getting errors.  what is the <driver name> that i'm looking for??

---

### Post by gromiko on 2010-03-12
Hi all.
I just wanted to share my success, thanks to all of you who started this thread and got me on the right track. I have an Asus UL30A with an intermittent signal.
So I went to the stable site and got the latest.
[http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.33/compat-wireless-2.6.33.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.33/compat-wireless-2.6.33.tar.bz2)

This is the only one that worked for me since I have a x86_64 system. I had to connect with an ethernet cable but it was worth it since I just followed the simple steps and now it seems to work perfectly.

Kudos to all that came before me.

Notes: Ubuntu 910 64 Bit system and Atheros AR9285 wlan card.

---

### Post by petar258 on 2010-03-27
on 32-bit ubuntu 8.10 this works, BUT if use torrent(with high speed) computer freezes randomly
looks like more work needed on drivers

---

### Post by timjayko on 2010-04-09
thanks gromiko I have been running different ath9k drivers and wifi on my sony vaio VPCCW21FX has been very slow... also in a 64 bit intel system.  those drivers you recommended have improved my wifi web browsing exponentially!

---

### Post by bostoncraig on 2010-04-19
I just wanted to share this.  I was pulling my hair out.  Well, I don't have much, but you get the point.

I have a compaq cq-60 615dx w an Atheros AR9250

Wireless worked when booted in windows.  But I couldn't get it to work with any of the backports-modules when I booted to Karmic.

I tried the versions in Synaptic.  I tried building my own.  I was ready to *attempt* [to compile my own kernel]("http://http://www.ubuntux.org/node/9016") when I ran across a message somewhere from an eee user stating they had to enable wireless in bios.  I looked, just to cross it off the list.  When I set the boot options to allow network booting on startup with my backport-modules installed... VIOLA!  :guitar:
(maybe it starts the card earlier in the boot??  But, it worked for me.)
I just wanted to share this, to maybe save some headaches for those of you who, like me, couldn't see results following every lead possible.

-Craig in Boston

---

### Post by rsisto on 2010-04-19
Dear timjayko, I tried the solution you said worked for you, but I'm still having issues with my wifi.. It is really slow and works intermittently... Could you please post the steps for installing the driver for a newbie? I thought I installed it correctly, but it had no effect on the behavior..
Thanks in advance,
Ubuntu newbie.

PS: I have a VPCCW21FX, ubuntu 9.10 freshly installed ( Linux rafael-laptop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux )

---

### Post by bknecht on 2010-04-25
I have the same problem. The Wireless works sometimes, but only very slow and very often the speed goes down to absolute 0. I hoped the bleeding edge drivers would change that, but I still have to wait forever for pages to load completely.
I checked if the new drivers were loaded with modprobe -l and it looked okay. I also tried Karmic's and Lucid's backport modules but they did not have any effect either.
Wired internet works like a charm and I already tried all the common IPv6 stuff you can find everywhere on the internet. It's definitely not a DNS problem.

I'm thinking about putting Windows on my machine to test if the Wireless card is broken and if not, I'll probably just stay with it. I had it with those problems.

---

### Post by capo1949 on 2010-06-12
Hi All

I have an acer inspire one, with ubuntu 10.04 netbook installed. My wireless connection is disabled.

Which compat-wireless tarball do I install? There is a choice of 3
My kernel is 2.6.32-22 generic

Some help would be greatly appreciated
Graham

---

### Post by bknecht on 2010-06-13
I usually download the bleeding edge compat-wireless driver regularly and compile it for my current kernel.
However this does not solve my issues at all, even though it's the newest open-source drivers you can get as far as I can tell, without risking having additional bugs because of a bad commit from the developers.

I still didn't get around to install Windows...

---

### Post by capo1949 on 2010-06-13
hi
So which one do I use for my kernel?
thanks
graham

---

### Post by ivantopo on 2010-06-30
rsisto, I have the same VAIO and had the same problem with ubuntu 10.04 and the 2.6.32-22-generic kernel... i tried everything and the only thing that worked was to compile and install compat-wireless-2.6.35-rc2... i know this is not intented for the kernel i have but this solved the issue for me!! i downloaded from linuxwireless and the run the default process: driver-select, make, make install, make unload, /etc/init.d/networking restart and the modprobe ath9k and it worked like a charm!!! the only remaining issue is that after computer restarts the problem comes again, i re-install the module and it works again!... i'm suspending rather than shutting down until i found a solution for that but my wifi is Ok!.

---

### Post by bknecht on 2010-07-01
ivantopo you're a genius. I tested it and my wifi connection is A LOT better (faster) and more stable than before.
However I experience the same problem as you do, where the installation seems to become invalid after a reboot.

I guess I'm going to write a script that installs the new driver more or less automatically every time I restart. Or there is a better fix maybe?

---

### Post by ericn231 on 2010-09-24
Just got a new Lenovo G560 laptop which is a wonderfully fast machine (when it's not running windows 7, of course).  I had the problem of inability to connect via wireless, it would attempt to connect to my network but kept asking for the password.

I got it working today by obtaining the 32 bit XP driver from atheros.cz and running that through ndiswrapper.  It even works after rebooting. Yay!

Hope this helps others...

---

### Post by sertaconal on 2011-01-23
It's worked!! but i have an another compat pack.
My System is Sony Vaio VPC EB1S1E and i have 2.6.32-27-generic..
Wireless : AR9285..
First of all download " [compat-wireless-2.6.35-rc2.tar.bz2]("http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.35/compat-wireless-2.6.35-rc2.tar.bz2") " and copy / paste your Desktop..
After THERE WRITE IN TERMINAL step by step
```

cd Desktop
tar -xf compat-wireless-2.6.35.rc2.tar.bz2
cd compat-wireless-2.6.35.rc2
make
sudo make install
sudo unload

```i hope it'll fix your problems.. thax alot to ivantopo for helping find right compat

---

### Post by ltuure on 2011-03-02
I'm still experiencing the same problem about the wlan being sticky again after reboot and I wouldn't like to compile the drivers every time again. Any ideas?

---

### Post by bknecht on 2011-03-02
Upgrading to the newest version of Ubuntu solved the problem with the wireless. However the newest version doesn't support my graphic card anymore, so I'm still stuck with installing the driver every single time I turn on my machine and want to go on the internet.

Let's hope 11.04 brings salvation.

---

### Post by sourish4c on 2011-03-29
dear Wrathe... i spent hours trying to figure out my wireless issues.. but was not getting success... You'r post helped me a lot to solve the same.. Right now my wifi is working absolutely fine... I only registered my account some time back to thank you... Thanks a lot and keep up the good work..

---

### Post by FrostyC on 2011-06-18
> **t0mppa said:**
> I guess you missed the part on the page about simply installing the linux-backports-modules-jaunty (replace jaunty with karmic or hardy or whichever version you happen to use) with apt-get or Synaptic, since that's a version of the latest compat-wireless prebuilt by the Ubuntu kernel team.

Yeah... Get something to connect to the internet from the internet on the same laptop....

That kind of defeats the purpose...

---

### Post by testing2007 on 2012-05-29
> **Wrathe said:**
> If you have an Atheros AR9285 wireless card on Ubuntu 9.04 and cannot get it working, this is for you.
 
Ubuntu did not automatically detect my card (AR9285) and spent many hours trying to figure this out. The purpose of this is to show you how to get your Atheros AR9285 Wireless Network Adapter working without those many hours of finding the wrong answers.
 
It is very simple.
 
Download a stable release (I downloaded compat-wireless-2.6.30.tar.bz2) from the following website to your desktop:
[http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/)
 
Open up Terminal and type:
(It tells you all this on the website that you download it from.)
 
Restart.
Click on the wireless icon in the top right corner of the screen and logon to your wireless network.
 
Fin! :guitar:
 
*_[COLOR=darkred]Edit: Apparently the bleeding edge drivers are faster. I have not tested them though.[/COLOR]_*
 
I had encounter the question last night, I help It could be solved by it.

---

