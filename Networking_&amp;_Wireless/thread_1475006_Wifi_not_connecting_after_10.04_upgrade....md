---
title: "Wifi not connecting after 10.04 upgrade..."
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by seano33 on 2010-05-06
I updated successfully to 10.04 via wireless, then I download a bass synthesizer via wireless. The next day, today that is, can't get wireless to work. It keeps prompting me for the passphrase, I enter everything correctly, all the other computers in the house have no problem. What happened?

---

### Post by HIcycles on 2010-05-06
I'm having the same problem. I have an ASUS Eee 1000HE, installed Ubuntu NR 10.04, dual booting into Windows7.

I logon to Ubuntu, it searches and connects to WiFi, sits for a few minutes (wifi icon doing it's back and forth thing), and then prompts me for my wifi password. I enter it (correctly), it sits again for a few minutes, and then prompts me again. I tried this both with my wireless router and my cellphone (via wifi tether). Same results.

I boot up into Windows7, and no problems. I can get on the network.

Is there something I'm missing in the configuration? I'm a linux noob.

---

### Post by tmaxx on 2010-05-08
Hey Guys, I am also on the same boat. Exact Problem description.

I have had the same query in a different Forum where some one else is also having the same issue. If you have found any solution please post the same.   

[http://ubuntuforums.org/showthread.php?t=1476551](http://ubuntuforums.org/showthread.php?t=1476551)

Just watch this thread too. Just in case some one posts some response.

I am not sure if the Ubuntu admins are aware of the issue. I do not know the process of informing the admins about this issue. Not seen any threads where it has been acknowledged. Hope some one is aware of this and working on this. 

Kind of little frustrating as i am unable to get into to the Net on Ubuntu now. System kinda becoming useless.

---

### Post by tyling81 on 2010-05-08
I got the same problem after update from 9.10 netbook remix to 10.04.

---

### Post by suryaccnamcse on 2010-05-08
I too am facing similar issue. When I give the key, it just does not accept it and asks again. I have 9.10 and 10.04 installed on the same system. When I restart the system and again try to connect sometimes the wireless connects. It disconnects randomly. When I am in 9.10 there is no issue in connecting to the wireless. 
my wireless adapter is intel pro/wireless 3945ABG which is supported by Ubuntu.

---

### Post by Bill_In_KC on 2010-05-09
I got the same problem after update from 9.10 to 10.04,  Gateway 450SX4 laptop. Worked great before. :(

---

### Post by Daniel9 on 2010-05-09
I'm having the same problem with my wireless connection.  I hope someone comes up with a solution soon as it appears quite a few are having the same or similar situation.

---

### Post by AlmightyBob on 2010-05-09
I've been having this problem since the very first time I ever tried Ubuntu.  I can see the networks but can't connect to any of them, but it works fine in Windows

---

### Post by Barburia on 2010-05-09
I have lucid installed. It connects perfectly but whenever I'm trying to stream a movie on the internet gets disconected. I had the same problem with the Totem Player, whenever I played a movie on it my wifi got disconected but if i use vlc or mplayer the wifi works correctly. Any thoughts?

---

### Post by Chrisco66 on 2010-05-10
My card is RTL8187SE.  There are a few threads open to deal with this.  I thought it was just this card though.  Search for RTL8187SE.  I broke the girl friends msi u100.  Now she has to walk across the room to use the other computer.   Im in the doghouse till i get this fixed..

---

### Post by cg0191 on 2010-05-11
I have this problem also.
I did a new install of 10.04.
After completing the install & logging in to my desktop it tells me there are proprietary drivers available for my wifi (Broadcom BCM4312).
I click to install them.
My WiFi menu shows &quot;device not ready&quot;.
lspci & lsmod clearly show the drivers are installed.

I then plugged in a USB D-Link Wifi dongle.
It shows my secure Wifi network, when I click to connect it gives me the option of WPA only which is wrong.
If I create a new Wifi connection I get the (correct) option of WEP 128bit.
I give the key, it accepts & says 'connected' but attempts to browse web pages or even ping a host fail.

I connected an ethernet cable to my hub & it also does not allow me to browse or even ping.

I though of checking for a mis-configured firewall but there is no mention of it in any menu.

I though of checking DHCP/DNS settings but it to is missing unless i try to change the settings of the wifi connection from &quot;share with others&quot; (what the hell is that?) to DHCP or DHCP with manual DNS setting. Of course that makes the Ethernet connection then break altogether....

This is not release quality software IMHO..
--

HP Mini 110 netbook, 2Gb RAM, 16Gb Solid state drive, booting from Sony 16Gb USB Sony memory stick.

--

UPDATE : My previous comments relate to my use of 10.04 running from a usb stick for testing.
***I accidently found that if I close the lid of the netbook (sleep it) & then reopen the lid (wake it) the wireless network miraculously appears.***
On restart the network was lost requiring clicking system/administration/hardware drivers all over again.
When given the choice of the 'b43' or the 'sta' driver I chose 'sta' (by trial & error).

I just ran the install to my internal SSD drive.
1) Operating system startup time (compared to vista) is sensational!!!!!!!
2) The wireless network appears & I can connect no problem.

Am I a happy camper :)

---

### Post by Chrisco66 on 2010-05-11
Yup, mine works fine with the network cable, but not with wireless..

---

### Post by Old Codger on 2010-05-11
Like many others, I also cannot connect to my wifi--and I have three routers in the house. I had no problem connecting to any of the three when I ran 9.10, but since upgrading, to 10.4 nothing I've tried works. Such issues related to Linux (name the flavor) upgrades are precisely what keeps folk from converting to Linux OS as an alternative to Windows and Mac OS. Unfortunately, these aren't the only problems I've encountered since trying Ubuntu and other Linux OS, and these issues are precisely what drives some Linux users back to Windows and Mac OS. I currently have two Macs and run Ubuntu on my laptop, along with Mac OS 10.6. If I didn't have Snow Leopard or another OS to fall back on, I'd be screwed right now!

If I'm unable to resolve these problems soon, I'll uninstall Ubuntu and move on to another OS alternative.

---

### Post by cg0191 on 2010-05-17
> **Old Codger said:**
> Like many others, I also cannot connect to my wifi--and I have three routers in the house. I had no problem connecting to any of the three when I ran 9.10, but since upgrading, to 10.4 nothing I've tried works. Such issues related to Linux (name the flavor) upgrades are precisely what keeps folk from converting to Linux OS as an alternative to Windows and Mac OS. Unfortunately, these aren't the only problems I've encountered since trying Ubuntu and other Linux OS, and these issues are precisely what drives some Linux users back to Windows and Mac OS. I currently have two Macs and run Ubuntu on my laptop, along with Mac OS 10.6. If I didn't have Snow Leopard or another OS to fall back on, I'd be screwed right now!

If I'm unable to resolve these problems soon, I'll uninstall Ubuntu and move on to another OS alternative.

If you can plug into an ethernet cable do so & run update manager.
Then unplug the ethernet & try your WiFi again.
Quite likely working after that.

I must say this is the first Linux I have installed that works so well. Really impressed how I could throw it onto a netbook (of all things) & have a fast stable Ubuntu fully installed in a matter of minutes.

Kudos to all concerned at Canonical & those ubuntu people involved.

---

### Post by Chrisco66 on 2010-05-18
cg0191, did that, at least three times.  No help.

---

### Post by Bill_In_KC on 2010-05-18
cg0191, I did that but no new updates were found. I expected to see many bug fixes ready for download but not a single one, is update broken also?

---

### Post by cg0191 on 2010-05-19
> **Bill_In_KC said:**
> cg0191, I did that but no new updates were found. I expected to see many bug fixes ready for download but not a single one, is update broken also?Hi Bill, I suspect something is borked in your system there because there are most certainly post 10.04 updated packages being released, almost daily.

I'm coming to the Linux table as a 'new' user essentially with this release of Ubuntu. I have been trying many distro's over many years. This is the first time for me where a distro has installed in minutes with no issue's & 'just works' in the same way as my beloved Mac's do. Obviously ubuntu is heavily influenced by Mac in its default theme. Apple could learn a lesson from Ubuntu by the way Applications, Places & System menu's are placed right there in the top panel.

I put the windows installer application & disc image on a bootable USB stick. I booted up into the live image where I found that Wifi was not working even though the non-free binary drivers were offered to me.

I plugged in an ethernet cable, ran update & noted updated packages already available.

I then rebooted into Vista, ran the installer to put Ubuntu onto the internal SSD driver of my netbook by completely nuking Vista & installing clean.

At the conclusion of the install/restart I booted into Ubuntu, was offered the non-free binary drivers for my internal Broadcom Wifi (note I chose the 'STA' driver not the other one) & after giving the relevant password etc the WiFi came up & worked.

I then re ran update manager.

After years of trouble shooting & supporting users I always install a major new release 'clean'. I never attempt Mac OS 10.5 -> Mac OS 10.6, Windows XP -> Vista or Ubuntu 9.20 -> Ubuntu 10.04 etc as this is just asking for trouble. Yes, yes, I know all the reasons why Linux package managers should allow this but why give yourself headaches?

I advise backup your data & make a new 'clean' install.

Are we all having trouble with the same Broadcom WiFi chipset or is this something more general? Mine is Broadcom STA driver supporting BCM43** chipsets.

Cheers,
Chris

---

### Post by Chrisco66 on 2010-05-20
So, does anyone know how to fix the wireless without reinstalling?  I tried reinstalling before my first post here, and it did not help.  

I hope people dont just dump the installation because reinstalling with the same operating system will not provide any new drivers.  Mine has updated several times (by cable) and no drivers have been provided for the wireless card.

I guess 10.04 works better on some machines.  My laptop lost the driver for the ATI video.  Had to fix that.  Now, my main machine will not burn disks.  All this stuff worked fine under 9.10.  

Im just tired of fixing the damn things.  If I wanted to spend my day fixing stuff, I would have stayed with windows..

---

### Post by cg0191 on 2010-05-20
> **Chrisco66 said:**
> So, does anyone know how to fix the wireless without reinstalling?  I tried reinstalling before my first post here, and it did not help.  

I hope people dont just dump the installation because reinstalling with the same operating system will not provide any new drivers.  Mine has updated several times (by cable) and no drivers have been provided for the wireless card.

I guess 10.04 works better on some machines.  My laptop lost the driver for the ATI video.  Had to fix that.  Now, my main machine will not burn disks.  All this stuff worked fine under 9.10.  

Im just tired of fixing the damn things.  If I wanted to spend my day fixing stuff, I would have stayed with windows..What happens if you click 'System/Hardware Drivers' ? On my netbook (HP Mini 110) it detected & offered the non-free binaries within seconds.

I believe there is an expert way to force it to install the driver involving something called modprobe but I'd have to google up the exact procedure..

---

### Post by Chrisco66 on 2010-05-20
I didnt try the hardware drivers.  I just didnt think of it.  Ill try it and get back to you.

---

### Post by antiemptyv on 2010-05-20
I'm having the exact problem on my HP Mini 2133:

Freshly installed 10.04.  Upgraded via wired connection.  Rebooted upon prompt.  Installed and activated restricted wireless drivers.  Rebooted upon prompt.  My wireless network and three others are detected.  Upon trying to connect, it seems to attempt to connect, but repeatedly prompts for the password.

iwconfig does not show wlan0 or similar in its output.

---

### Post by Chrisco66 on 2010-05-20
Tried Hardware drivers, no help.  It said "no proprietary drivers are in use on this system".  It will connect to open networks, just not encrypted ones..

---

### Post by cg0191 on 2010-05-20
> **antiemptyv said:**
> I'm having the exact problem on my HP Mini 2133:

Freshly installed 10.04.  Upgraded via wired connection.  Rebooted upon prompt.  Installed and activated restricted wireless drivers.  Rebooted upon prompt.  My wireless network and three others are detected.  Upon trying to connect, it seems to attempt to connect, but repeatedly prompts for the password.

iwconfig does not show wlan0 or similar in its output.Yes I saw this also when I first tried Lucid booted from a USB memory stick. I tried plugging in a DLINK usb Wifi dongle, it too was detected as a RALINK & exhibited the same behavior.

Subsequently I closed the netbook (suspend), reopened it later & suddenly the Wifi was connecting. Maybe this was coincidental..

I'm using WPA2-PSK with AES encryption on my router.

---

### Post by Bill_In_KC on 2010-05-20
> **Chrisco66 said:**
>  It will connect to open networks, just not encrypted ones..
Same going on we me, will not connect to encrypted networks.

---

### Post by Chrisco66 on 2010-05-20
Well, I tried the NDIS thing again.  It would not connect using the Xp driver, so I tried the Win7 driver.  Still nothing.  The problem is, now it wont connect to open networks either.  Shows the wireless icon with an ! on it. I removed the driver with the NDIS installer, and restarted, no help.  

If there is someone here who can talk me through the NDIS installation, I would appreciate it.  I was using the GUI version from synaptic.  I thought it was pretty self explanatory.  That's what I get for thinking..har har

---

### Post by cg0191 on 2010-05-20
> **Chrisco66 said:**
> Well, I tried the NDIS thing again.  It would not connect using the Xp driver, so I tried the Win7 driver.  Still nothing.  The problem is, now it wont connect to open networks either.  Shows the wireless icon with an ! on it. I removed the driver with the NDIS installer, and restarted, no help.  

If there is someone here who can talk me through the NDIS installation, I would appreciate it.  I was using the GUI version from synaptic.  I thought it was pretty self explanatory.  That's what I get for thinking..har har

The sticky at the top of the forum [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

 When I first bought my HP Mini 110 netbook (model 1081TU) it had a highly proprietary Linux on it called Mi. It was apparently based on Ubuntu 9.x

The onboard Wifi worked.
It could be switched on/off using a small slider switch on the front next to the slider for the power on/off.

HP pointed the distro to their proprietary repositories but has decommissioned that server or otherwise taken it off line (thanks so much HP). I tried fiddling with the distro to try to point it at the main Ubuntu repositories in the hope of  'converting' it to a full generic (updateable) Ubuntu. Of course this broke the distro horribly..
HP do not supply an install disk (thanks again HP) & attempts to reinstall from the hidden partition contained on the SSD failed so I had no choice but to nuke the installation. 

At the time I was overseas with no access to a sufficiently broadband connection to be able to get a full Ubuntu ISO to try out so in desperation I installed Vista (yuck).

Vista detected the onboard Wifi as Broadcom chipset, installed a driver (hooray!) but when trying to connect to a network always showed the onboard Wifi as 'disabled'. Flicking the slider switch to turn it on did nothing. I scoured the internet for XP, Vista or Win7 broadcom drivers but found nothing newer than the installed Micro$oft supplied driver. Going to the Broadcom website for drivers just shows a lot of marketese & points you back to Micro$oft (thanks a lot Broadcom).

The onboard Wifi never worked under Windoze. 

So back home in Australia I download Ubuntu 10.04 put it on a USB memory stick & boot it.
It detects the Broadcom chipset & advises me to install non-free binary drivers. I note that it was offering me two (2) drivers. One called 43 & one called sta. I tried both, the sta driver seemed to work. Under Ubuntu I saw the Wifi stubbornly listed as 'inactive'. Grrr!!

I stuck a usb Dlink Wifi in which was detected as Ralink chipset & showed my wifi network but like you guys, it refused to make an encrypted connection. Double Grr!!

At this point, while still booted from the memory stick I connected an ethernet cable, ran an update which installed lots of new packages but did not fix my Wifi problem. During subsequent fiddling about I removed the Dlink USB Wifi dongle closed the netbook (suspend) & reopened it and to my amazement I saw the onboard Wifi activate.

A soon as I saw this working I elected to run the 'Install to Hard disk' (or whatever it is called).
At this point Vista was completely nuked & Ubuntu 10.04 now resides on the Internal SSD drive.

Its hard to be precise as to what happened because during this time Im fiddling around a bit, this is the best I can remember.

This is the **first time** I've had the built in Wifi working on any operating system since I purchased the machine with its dinky custom Linux was on it.

The lesson I have learned is before purchasing any laptop/netbook research carefully the chipset & boycot any containing Broadcom chips as this company (they're not alone) does not support their hardware with new or updated drivers.

Cheers
Chris

---

### Post by cg0191 on 2010-05-20
Since its working for me I must bow out but before I do I took a look at the bug database for Ubuntu & dont find any thing special being reported for Lucid in regards to Wifi.

I did see a detailed answer that described how to enable the backports of wireless modules & firmware in your repositories. Maybe that could help get your Wifi going agin?

[https://answers.launchpad.net/ubuntu/+question/111578](https://answers.launchpad.net/ubuntu/+question/111578)

I see there is a website listing Wifi chipset's under Linux. Probably a good idea to identify **exactly** what chipset you have :

[http://www.linuxwireless.org/en/users/Drivers](http://www.linuxwireless.org/en/users/Drivers)

If all else fails log it as a bug and someone from much higher up the food chain than me will get back to you.

Cheers
Chris

---

### Post by Chrisco66 on 2010-05-25
Does anyone know of a mini-pci wireless card that is supported by linux?  In other words not one of the "problem" broadcom, or realtek cards?

Im so tired of playing with this damn card.  I will never buy any device that has parts made by these two crappy vendors..

---

### Post by cg0191 on 2010-05-25
> **Chrisco66 said:**
> Does anyone know of a mini-pci wireless card that is supported by linux?  In other words not one of the "problem" broadcom, or realtek cards?

Im so tired of playing with this damn card.  I will never buy any device that has parts made by these two crappy vendors..

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by Chrisco66 on 2010-05-26
cg, thanks for the link.  I have seen this page before.  The problem is that not enough people (myself included) keep the page updated.  

My other laptop uses an Atheros card, and it has never given me one bit of trouble.  Im going to look for an Atheros mini pci card that wont cost me a fortune.  

I have never had any luck with ndis wrapper, but if I cant find a card, Ill try that again.  

Thanks again..

---

### Post by LastNerve on 2010-05-26
I have the exact same problem! At least now I know that I'm not  the only one the malevolent penguin is trying to drive insane.  
 

 Fresh install: Ubuntu netbook remix 10.04 on an Acer Aspire One 532h.
 

 I try to connect to a WPA2 home wifi network, and it just won't accept the password. It's the weirdest problem. I don't even know where to begin to troubleshot this crap. Updates didn't help one bit, neither did switching to Wicd network manager. ](*,) :x :sad: :cry: :-&

---

### Post by b k on 2010-05-26
> **LastNerve said:**
> I have the exact same problem! At least now I know that I'm not the only one the malevolent penguin is trying to drive insane. 
 
 
Fresh install: Ubuntu netbook remix 10.04 on an Acer Aspire One 532h.
 
 
I try to connect to a WPA2 home wifi network, and it just won't accept the password. It's the weirdest problem. I don't even know where to begin to troubleshot this crap. Updates didn't help one bit, neither did switching to Wicd network manager. ](*,) :x :sad: :cry: :-&
 
If you are set up to autologin into your user account on bootup and your symptoms are similar to post #10 of this link [http://ubuntuforums.org/showthread.php?t=1489883](http://ubuntuforums.org/showthread.php?t=1489883) , try the solution at end of post #3 of the same link.
 
If that fails to work, you could try playing around with the router's authmode and encryption (if you have administrative access to the router) - try WPA2-psk(WPA2 personal) with AES encryption.
 
Hope the info is of some help.

---

### Post by cg0191 on 2010-05-27
> **Chrisco66 said:**
> cg, thanks for the link.  I have seen this page before.  The problem is that not enough people (myself included) keep the page updated.  

My other laptop uses an Atheros card, and it has never given me one bit of trouble.  Im going to look for an Atheros mini pci card that wont cost me a fortune.  

I have never had any luck with ndis wrapper, but if I cant find a card, Ill try that again.  

Thanks again..
Ok, you're welcome.
Dont forget this exhaustive list here :
[http://www.linuxwireless.org/en/users/Drivers](http://www.linuxwireless.org/en/users/Drivers)

---

### Post by Chrisco66 on 2010-05-27
I guess I spoke too soon.  Now, my Atheros card will connect, but it is very slow.  There was a command to turn the speed up to 11 Mb/s.  From what I read on another thread, (that I cant find) for some reason the default is 1 Mb/s.  Does anyone know the command?  I tried the backport kernel from synaptic.  Didnt seem to make a difference at all.

Im so glad I "upgraded" to 10.04.  Maybe next time Ill upgrade to DOS.  I seem to be spending more time in terminal anyway.  Im an unhappy camper..

---

### Post by Chrisco66 on 2010-06-03
I just reinstalled 9.10 on my laptop and netbook.  Amazing, no wireless problems, or video problems with the old version.  

I dont know if they are trying to keep Ubuntu off the older hardware.  If that is the case, then maybe Ill upgrade to Vista.  Yes, Im joking.  Its just sad, 9.10 was almost perfect, 10.04 is a mess.  

But, you cant beat the price I guess..

---

### Post by Bill_In_KC on 2010-06-04
I think I will also reinstall 9.10, it worked great with my older gateway laptop. No problems with the WiFi card or video. I think 10.04 is not ready for me, what a shame. All the older versions worked great on my older equipment. At one time my Gateway laptop had XP on it but 9.10 ran a lot better without the BSOD I had with XP.

---

### Post by cg0191 on 2010-06-05
> **Bill_In_KC said:**
> I think I will also reinstall 9.10, it worked great with my older gateway laptop. No problems with the WiFi card or video. I think 10.04 is not ready for me, what a shame. All the older versions worked great on my older equipment. At one time my Gateway laptop had XP on it but 9.10 ran a lot better without the BSOD I had with XP.
Make sure your router is set to use WPA2-PSK. That's very important.
If no joy then please help yourself & others by taking a moment to file a bug report.
I have found that they do action your bug's & will help you find a solution.
Try it!

---

### Post by Frederik Seidelin on 2010-06-06
The problem is WPA2 encryption, but don't go ahead and change the encryption to WEP or something insecure. :-) My temporary workaround is toggling the wireless card (Fn+F2 on my Eee 1000) off and back on, trying to connect, then rinse and repeat if still failing, until it connects.

Needless to say, this is not a viable solution. After Googling the problem didn't turn up much, I tried Ubuntu Forums (which really is the place one should go to first; there's nearly always a solution). I stumbled upon [thread=1476007]_Ubuntu 10.04 using the Ralink RT2860 WiFi chipset (e.g. EeeBox  B202)_[/thread]. I haven't tried it myself, but I've seen the guide linked to quite a few times. I will try it tomorrow.[B] :-)
[/B]

---

### Post by captomer on 2010-06-06
I have similar problem. I am using Medion akoya 1210 with RaLink RT2860 wireless adapter. I can connect to unsecured/open network but on protected / secured network, network-manager keeps asking me pass-phrase despite typing it correctly. Any clue on how to handle this problem?

---

### Post by caporaso on 2010-06-06
A similar post recommends upgrading the kernel to fix this:

[http://ubuntuforums.org/showthread.php?t=1470892](http://ubuntuforums.org/showthread.php?t=1470892)

Has anyone here tried this? Can anyone point me to a page that shows how to do the kernel upgrade? It doesn't look like it's available yet in the repositories (or at least the default ones...).

---

### Post by Chrisco66 on 2010-06-10
Even after reinstalling with 9.10, my wind u100 still wont connect without a battle.  It asks for the password at least twice before it connects.  When it does connect, it will drop out after 5 or 10 minutes.  

I am looking for a replacement.  Maybe fedora?  pclinux wont install on the wind.  

Where are the drivers that work?

---

### Post by cg0191 on 2010-06-10
> **Chrisco66 said:**
> Even after reinstalling with 9.10, my wind u100 still wont connect without a battle.  It asks for the password at least twice before it connects.  When it does connect, it will drop out after 5 or 10 minutes.  

I am looking for a replacement.  Maybe fedora?  pclinux wont install on the wind.  

Where are the drivers that work?
I suggest there is some kind of compatabilty problem with the encryption used by some WiFi router/Wifi Card combinations. I to saw this behavior until I reloaded the hardware driver & configured my router to WPA2-PSK. Then it all suddenly worked flawlessly.

 I did a brief research of this. According to some users a regression allegedly came in the change from 9.04 to 9.10 & apparently still persists in 10.04.

I say 'apparently' because it works fine for many folks with the same WiFi chipset.

I respectfully request those affected take 5 minutes of their time to report this as a bug. I have seen the ubuntu bug squashers are quite responsive & helpful.  Not only will you help yourself but you will help anybody else experiencing same problem. The whole idea of open source is everybody pitches in to help. The software you use is free of charge, you can help the effort by submitting concise logical bug reports.

If you think its a bug complaining here will do nothing.

Sent from Ubuntu 10.04 on Hp Mini 110 netbook with Broadcom Wifi onboard.

---

### Post by cdaggerfall on 2010-06-11
Having the same problem, and for info, this was a problem in 9.10 early on. Its not a problem for everyone though, as some laptops/netbooks seem to work fine and some dont. I have a Sony VAIO NR series that was running 9.10 fine on WiFi and after upgrade it worked for a little bit, then stopped, giving me the "Authentication required by wireless network" message. As i said, this happened to me also after 9.10 came out. I stopped using ubuntu for awhile after that, then tried 9.10 again a few months later and never had the problem until upgrading today. Neway, any help would be appreciated.

---

### Post by anechoic on 2010-06-11
if for some reason you lose connectivity after updating to 10.04
do this:
plug in via ethernet to the back of your router
go to System/Administration/Hardware Drivers
uninstall the WiFi driver ('Broadcom STA wireless driver' in my case)
then re-install the driver
wait for it to finish completely
leave the Ethernet plugged in for now
then go to the WiFi icon in the panel
select your network
and it should just work now
hope this helps someone

---

### Post by cg0191 on 2010-06-11
> **anechoic said:**
> if for some reason you lose connectivity after updating to 10.04
do this:
plug in via ethernet to the back of your router
go to System/Administration/Hardware Drivers
uninstall the WiFi driver ('Broadcom STA wireless driver' in my case)
then re-install the driver
wait for it to finish completely
leave the Ethernet plugged in for now
then go to the WiFi icon in the panel
select your network
and it should just work now
hope this helps someone
I can confirm this works. Don't know why but it does.

---

### Post by john8791 on 2010-06-11
My Zonet 2500 usb adaptor (Ralink) does not work with 10.04 with WPA2 enabled.  Only works with no security.  Frustrated, I installed Linux Mint and it doesn't work either.  I enjoy Linux but just don't have time to spend countless hours chasing my tail.

---

### Post by Chrisco66 on 2010-06-12
cg0191, I did update the bug report.  When I found the bug, its status was fixed.  I can only update with my information and wait.

I really dont like the idea of changing my router settings.  I am satisfied that the problems are with the computers, since it started after upgrade.  I might try some changes just to see. I might find something by accident.

Its strange that two computers with cards from two manufacturers are not working.  Even after reinstalling 9.10, they are better, but not nearly as fast as they were.  

Ill keep looking.  The only alternative is to go back to windows..

---

### Post by abdusamed on 2010-06-14
GOIGN TO KEEP IT SUPER SIMPLE..i can create UNSECURED network on ubuntu  and share it. vista detects it and works!! but if i create either in  vista machine or ubuntu machine a wireless which is secured with any  type of encryption..NONE of the machine seems to connect to it though  they detect a secured network. Vista keeps on saying that the key enter  is invalid and on ubuntu machine.. trying to connect to vista secured  network.. ubuntu doesn't do anything!!! WHAT UP WITH IT!

---

### Post by 10dollarNOOBIE on 2010-06-14
i have HUAWEI USB Modem  3g, and its working nicely in my ubuntu9.10 but after upgrading it doesnt seem to be recognize by the network manager. I installed 10.04 via wubi is that the problem? i cant update without internet how can i enjoy this new version :(

---

### Post by cg0191 on 2010-06-14
> **abdusamed said:**
> GOIGN TO KEEP IT SUPER SIMPLE..i can create UNSECURED network on ubuntu  and share it. vista detects it and works!! but if i create either in  vista machine or ubuntu machine a wireless which is secured with any  type of encryption..NONE of the machine seems to connect to it though  they detect a secured network. Vista keeps on saying that the key enter  is invalid and on ubuntu machine.. trying to connect to vista secured  network.. ubuntu doesn't do anything!!! WHAT UP WITH IT!

You should check your WiFi router is set to 

Allow Broadcast of SSID : Yes
Security : WPA2-PSK (Wi-Fi Protected Access 2 Pre-Shared Key)
Encryption : AES

Make a careful note of the exact pass-phrase that you set in the router. It is cAsE sEnSiTiVe!


Since you gave no details of your hardware (ahem) I advise you start your Ubuntu machine and wait a few moments for it to detect the wireless network. It should be the SSID that you set in the router. Give the pass-phrase & wait for the authentication to complete.

FWIW the onboard Wifi of my Netbook never ever worked under Windoze XP or Vista but activated & works just fine under Ubuntu. So anyone that tells me they are 'going back' to Windoze just makes me laugh.

When I first tried booted from the Live CD image It was troublesome but after I ran the install to hard-drive it worked. I plugged in an ethernet cable ran update, removed the wireless driver & let Ubuntu redetect. Working.

---

### Post by TomDoe on 2010-06-14
Im sorry if this is covered in another thread, I tried to search for answers here but had no luck.

I installed Ubuntu Netbook Remix 10.4 on Acer Aspire One A150,
but I ran in to a problem.
Every now and then I loose connection to the net, it takes a minutte, then its back again.
Do I need another driver for it? If so; how do I get it?
Im fresh to linux so you'll probably have to spoon feed me the answer.

Thanks in advance for your patience and time with a linux noob trying to make a transition from MS

---

### Post by cg0191 on 2010-06-14
> **TomDoe said:**
> Im sorry if this is covered in another thread, I tried to search for answers here but had no luck.

I installed Ubuntu Netbook Remix 10.4 on Acer Aspire One A150,
but I ran in to a problem.
Every now and then I loose connection to the net, it takes a minutte, then its back again.
Do I need another driver for it? If so; how do I get it?
Im fresh to linux so you'll probably have to spoon feed me the answer.

Thanks in advance for your patience and time with a linux noob trying to make a transition from MS

Hi!
If you have intermittant connection problems it is likely to be 2 things :

1) Weak signal : install a bigger antennae on your outer or move your netbook closer to the router.

2) Interference : There may be neighbouring WiFi networks near you on the same channel as  you. Log in to your WiFi router and change the channel to a different one.

Take care ):P

---

### Post by TomDoe on 2010-06-14
Thanks for the answer mate.
I've got 80% strengh on the signal from the router so I'm guessing thats not the problem.
I try to change the channel and see if that works, but isnt it strange that the laptop with Ubuntu is the only machine having problems with signal dropping?
I've got 2 other laptops and 2 phones connected and non of those loose signal.
Hmmmm.. I'll try the channel change when I get home but if anyone else has any suggestions, feel free to add them.

---

### Post by tjololo on 2010-06-14
I had the same problem as you all on computer A, but not on computer B
As cg0191 nicely said in a earlier post. Putting the algorithm on my router to AES works great.


I have two routers at home (both linksys wrt54g, but different version). I setup both of them to use wpa2-psk, one with TKIP+AES algorithm the other with only AES, other than that no difference in the setup (except SSID and channel).
The one with TKIP+AES did only work on computer B (NOT on computer A).
The router with AES worked on both of my computers (A and B).

After doing this I switched the algorithm settings on my two routers, just to be certain it wasn't just the routers fault).
The result after testing with the algorithm switched was:
TKIP+AES only computer B.
AES both of my computers.

So changing the algorithm to [COLOR="Lime"]AES[/COLOR] was the solution to the problem for me. As my little experiment shows;)

--
tjololo

---

### Post by bazzal1941 on 2010-06-15
There is a problem with 10.04 and WPA connection for machines with RT chips.
This is a very good explanation of how to fix it. I have successfully used it on two eee machines.

[http://http://ubuntuforums.org/showthread.php?t=1476007]("http://http://ubuntuforums.org/showthread.php?t=1476007")

---

### Post by cg0191 on 2010-06-15
> **bazzal1941 said:**
> There is a problem with 10.04 and WPA connection for machines with RT chips.
This is a very good explanation of how to fix it. I have successfully used it on two eee machines.

[http://http://ubuntuforums.org/showthread.php?t=1476007](http://http://ubuntuforums.org/showthread.php?t=1476007)

Even though the problem went away for me I have been following this thread in case I get it back again  :popcorn:

The comment here [https://bugs.launchpad.net/ubuntu/+bug/572777](https://bugs.launchpad.net/ubuntu/+bug/572777) tallies with my experience. I noticed also closing my Netbook (suspend) & opening it caused the wifi to start working as it should. I am using 32 bit 10.04 though.[INDENT]"Solution:
Sure enough, on my 64bit install I went into suspend mode, came out,  and immediately connected via wireless on WPA2!  I tested this a few  times, and if it did not connect, doing the


sudo rmmod wl
*wait a few seconds*
sudo modprobe wl"
[/INDENT]My crummy Wifi here is G whereas it seems like the people having the worst problem are those on N Wifi.
Further reading on that bug thread seems to indicate that a newer version of wpasupplicant & its dependant libraries resolves the problem. The easiest way to get the newer packages is to get them from debian :[INDENT]"Go to to Debain Packages Organization and manually download (watch your  arcitecture - i386 for 32-bit installs, AMD64 for 64-bit installs, etc,  etc - do not use ia64 for standard 64bit installes - that specifically  for the Intel Itanium CPU & will cause very large  problems/headaches)


wpasupplicant (here: [http://packages.debian.org/sid/wpasupplicant](http://packages.debian.org/sid/wpasupplicant)  ),


libpcsclite1 (here: [http://packages.debian.org/sid/libpcsclite1](http://packages.debian.org/sid/libpcsclite1)  ) &


libssl0.9.8 (here: [http://packages.debian.org/sid/libssl0.9.8](http://packages.debian.org/sid/libssl0.9.8)).


Once all three are downloaded, install the two library packages first  with kpackagekit (for kubuntu - use gdebi for Ubuntu)  then  wpasupplicant.  When done, reboot & you should have working wireless"


[/INDENT]Im very disappointed to see the Ubuntu dev's stubbornly leaving this bug at 'medium' priority despite many many people reporting problems. Seems ubuntu development is more focused on making it look pretty nowadays..

maybe I should switch to Debian Sid as they have more up to date 'WORKING" software..hmmm? I lose the faster booting but gain a more up to date system methinks..

Gonna try installing the newer wpasupplicant on my Netbook here to see if it improves or breaks anything.

UPDATE : Packages installed without pain. Working.

---

