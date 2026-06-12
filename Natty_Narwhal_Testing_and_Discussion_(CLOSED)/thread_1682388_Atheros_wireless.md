---
title: "Atheros wireless"
date: 2011-02-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by teachop on 2011-02-05
Anybody seeing things like this in dmesg.  My wireless isn't working yet in Natty, it did in prior versions going back.  This stuff fills the log, and it causes the computer to bog down, so much the mouse gets jerky!  If I go to Flight Mode, the mouse returns to normal.  Here are the messages:

[ 9802.523606] ath5k phy0: gain calibration timeout (2422MHz)
[ 9803.037864] ath5k phy0: gain calibration timeout (2427MHz)
[ 9803.559724] ath5k phy0: gain calibration timeout (2432MHz)
[ 9804.080083] ath5k phy0: gain calibration timeout (2437MHz)
[ 9804.590107] ath5k phy0: gain calibration timeout (2442MHz)
[ 9805.098154] ath5k phy0: gain calibration timeout (2447MHz)

etc... on and on.  Any ideas how to tackle this?
(using an Acer Aspire 3100 + 32bit Natty alpha 2)

---

### Post by Peter09 on 2011-02-06
I get this s well.

---

### Post by teachop on 2011-02-06
Launchpad bug #610440 seems to be the same.  If it is, this has been going on before Natty, although my particular laptop didn't have this problem before now.

Does Atheros wireless work for anybody?  I would think this problem has to be rare, since it makes a laptop not very useful.  I am continuing to test other aspects of Natty with the ethernet connected in Flight Mode.

---

### Post by buzzmandt on 2011-02-06
Atheros working great for me, i have two laptops using atheros and my GF has one as well.  3 outta 3 working here.

> 02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by zweiundzwei on 2011-02-06
When I try to connect to a wireless network my computer freezes -- is that the same issue? I'm using an Asus Eee 1001P with AR2427 Wireless Network Adapter (driver in use: ath9k)

---

### Post by odysseusjak on 2011-02-06
Mine sort of works. It connects fine but it's like it's being choked with regards to through-put. That is to say, it downloads in BYTES. Rarely does it get to kBs. On my 10.10, it works great! But not with 11.04.

I have theme on the same laptop. Acer Aspire 4730Z. Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express)(rev 01)

---

### Post by andbia on 2011-02-07
It is so frustrating... I have a Atheros AR928X and i haven't been able to get online since Ubuntu Lucid 10.04. 

I use Lucid now because i have tried _E V E R Y T H I N G_ and it is down right impossible to get a connection with my wireless device on Ubuntu Maverick 10.10 and the same problem is here on Ubuntu Natty 11.04. I use WPA2 and the wireless refuse to connect, says all the time it is wrong password which it aint :(

---

### Post by bwallum on 2011-02-07
I use MAC address filter on my router to only allow machines access that I know. WPA2 on for good measure. I have to access my router and manually enable the MAC address of a new nic if I want it to work.

Open a browser and type in the url. A common one in the UK is 192.169.1.254. Your router manual should tell you the default url.

I'm bald from the amount of hair tugged out before I got wise to this one.

---

### Post by coffeecat on 2011-02-07
> **andbia said:**
> It is so frustrating... I have a Atheros AR928X and i haven't been able to get online since Ubuntu Lucid 10.04. 

I use Lucid now because i have tried _E V E R Y T H I N G_ and it is down right impossible to get a connection with my wireless device on Ubuntu Maverick 10.10 and the same problem is here on Ubuntu Natty 11.04. I use WPA2 and the wireless refuse to connect, says all the time it is wrong password which it aint :(


I'm sorry to hear that. I have the Atheros AR928X wireless on my Acer laptop and it works just fine with WPA2 in both Maverick and Natty. My (Netgear) router is N-capable and I did have some odd issues when the router was using 802.11N. Solved when I set the router to 802.11g only. What router do you have and are you using 802.11n or g?

(I thought I posted earlier, but perhaps I clicked on preview and not submit. If a similar post to this appears as well, then the forum server problems have reappeared. :|)

---

### Post by bwallum on 2011-02-07
My experience exactly having just installed Maverick on a Fujitsu Siemens with Ath5k driver. Tried downloading the latest wireless drivers, all to no effect. 

I have experienced this before but my memoryof the detail fades. When I get a choked Windows machine I turn the wireless network off using XP/Vista/7 default utilities. (...because most are virus ridden and shutting down networking helps the process of data rescue). Once Ubuntu is loaded then calm is restored but sometimes wireless networking doesn't work.

Do you know of any eeprom programming (firmware) that Windows resorts to when you ask it to shut down wireless networking that perhaps Ubuntu doesn't cover?

---

### Post by david stevenson on 2011-02-08
I looks to me like several different problems in the above posts, but to the original post, I have the same problem with "ath5k phy0: gain calibration timeout" and posted a bug #714300 for this.
I found a kernel bug [https://bugzilla.kernel.org/show_bug.cgi?id=27382](https://bugzilla.kernel.org/show_bug.cgi?id=27382) which looks like it is actively being worked on.
David

---

### Post by teachop on 2011-02-09
> **david stevenson said:**
> I found a kernel bug [https://bugzilla.kernel.org/show_bug.cgi?id=27382](https://bugzilla.kernel.org/show_bug.cgi?id=27382) which looks like it is actively being worked on.
David

I am glad they are working on it.  It is a show-stopper for my old laptop.

---

### Post by bwallum on 2011-02-10
```
uname -r
```returns> 2.6.35-26-generic```
sudo apt-get install linux-backports-modules-compat-wireless-2.6.36-maverick-generic
```returns
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 linux-backports-modules-compat-wireless-2.6.36-maverick-generic : Depends: linux-backports-modules-compat-wireless-2.6.36-2.6.35-26-generic but it is not installable
E: Broken packagesI got the install info from[HTML]http://wireless.kernel.org/en/users/Download?highlight=%28ath5k%29[/HTML].Can anybody spot why I'm not able to install compat-wireless?...."not installable"??

---

### Post by Harry33 on 2011-02-10
> **bwallum said:**
> ```
uname -r
```returns```
sudo apt-get install linux-backports-modules-compat-wireless-2.6.36-maverick-generic
```returns
I got the install info from[HTML]http://wireless.kernel.org/en/users/Download?highlight=%28ath5k%29[/HTML].Can anybody spot why I'm not able to install compat-wireless?...."not installable"??

This is Natty development discussion forum.
Obviously you have Maverick.

---

### Post by bwallum on 2011-02-10
You're right, I didn't check the forum, just found a thread that fitted. Apologies for any inconvenience.

---

### Post by teachop on 2011-02-12
The latest Natty kernel has updates for athk5 driver, but this problem still exists.  No wireless for me.

---

### Post by vishalrao on 2011-02-12
Just tried on an Acer laptop with ath9k which doesnt seem to work. I'm using Kubuntu natty a2 with WPA2 personal and havent looked at the logs or anything... will twiddle my thumbs waiting for a package update down the line...

---

### Post by bwallum on 2011-02-13
Apologies for returning to this thread again but I have just solved my ath5k problem in Maverick Desktop 32 bit and thought you might like to have a go in Natty.

[http://ubuntuforums.org/showthread.php?t=1686282](http://ubuntuforums.org/showthread.php?t=1686282)

In summary (following chili555):-```
sudo rmmod -f ath5k
sudo modprobe ath5k nohwcrypt=1
```If that fixes the problem write a configuration file to apply the fix at boot.

```
gksudo gedit /etc/modprobe.d/ath5k.conf 
```Add a single line: ```
options ath5k nohwcrypt=1
```Proofread, save and close gedit. Now, on boot, the parameter should be applied automatically.

---

### Post by yellerKat on 2011-02-15
Thanks bwallum; that worked a treat for my ath**9**k! And thanks to chili555 in the [referenced thread]("http://ubuntuforums.org/showthread.php?t=1686282") as well!

---

### Post by andbia on 2011-02-16
I have a Packard Bell TJ75 with Atheros AR928X (Rev 01) using ath9k driver. Router with WPA2 and 802.11g only.

My problem is this, since the release of maverick i haven't been able to connect to any wireless network. I am able to see them but not connect. Well actually i am able to connect 1 out of 50 times, but that results in a speed of 1b/s until the connection dies by itself after around 1min. On the other hand Lucid works fine for me with no issues at all.

I spent 5h yesterday evening trying to solve my wireless issues. I installed both Ubuntu Maverick 10.10 64bit and Ubuntu Natty 11.04 64bit, and tried every single solution/tip my mighty google-search-skill could find. I think i tried most things that have been said, including the above tip in this thread.

So the conclusion is (based on my situation):
[LIST]
[*]Using either kernel 2.6.35, 2.6.36, 2.6.37, 2.6.38 with updates don't make any difference.
[*]Compiling newest compat-wireless didn't work.
[*]Any hack, blacklist etc didn't solve anything.
[*]Couldn't get ndiswrapper or madwifi to work.
[*]Using another distribution that uses kernel 2.6.35+ don't work either.
[/LIST]

The problem seems to relate to newer kernels since it works perfectly on older. The solutions i have tried might work on 32bit installs, since i only use 64bit i don't know.

TL;DR – test a lot->don't work->patience running out->rage quit->calm down->try again->nothing works->crying myself to sleep

---

### Post by teachop on 2011-02-16
> **bwallum said:**
> ```
sudo rmmod -f ath5k
sudo modprobe ath5k nohwcrypt=1
```
This does not have any effect on my original problem, unfortunately.

---

### Post by teachop on 2011-02-17
For a temporary solution, I blacklisted ath5k and plugged in an older usb wifi adapter, and it works fine.  I can continue with natty testing this way, until I see some new version of the driver come along.

---

### Post by bwallum on 2011-02-19
One of the things I found confusing was the version of compat-wireless relative to the kernel version. In my case I was running linux kernel 2.6.36-26 generic and could only load linux-backports-modules-compat-wireless-2.6.37-2.6.35-25-generic. However, it worked.

What version of linux-backports-modules-compat-wireless are you running on which linux kernel?

---

### Post by odysseusjak on 2011-02-22
As I have stated elsewhere, I have an Acer Aspire 4730Z. It works GREAT with 10.04 and 10.10. However, when testing 11.04, the wireless card slows to a crawl. It connects fine but it's like it's being choked with regards to through-put. That is to say, it downloads in BYTES. Rarely does it get to kBs. On my 10.10, it works great! I download at over a meg (sometimes two!). But not with 11.04. It's worse than being on dial-up!

I dual boot between 10.10 and 11.04 on the same laptop. The wifi card in question is a Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express)(rev 01). The only thing I can think of is the kernel. Both are running different ones so I'm thinking the issue is with the one(s) used in 11.04. In 11.04 I'm using kernel 2.6.38-4.

Any thoughts or suggestions? I have looked the forum over and can't seem to find any help.


Thanks.

---

### Post by zenarcher on 2011-02-22
My Atheros wireless doesn't seem to have the issue you're having there.  But, what I do have with it is that after a short time, my wireless shuts off and I have the screen pop up wanting to me to enter my WPA key again.  If I do, I just get the message, "Configuring network" and nothing more.  As soon as I reboot the system, the wireless starts right back up normally and will be fine until it shuts down again.

Regards,
zenarcher

---

### Post by cariboo on 2011-02-22
Merged two threads on the same subject.

---

### Post by odysseusjak on 2011-02-22
> **cariboo907 said:**
> Merged two threads on the same subject.

Cariboo907, I don't think these issues are the same, thus the reason for me starting a new thread. I can connect but my download speed is hindered.

---

### Post by bwallum on 2011-02-22
> **odysseusjak said:**
> ....I can connect but my download speed is hindered.
What version of linux-backports-modules-compat-wireless are you running and on which linux kernel?

---

### Post by odysseusjak on 2011-02-22
> **bwallum said:**
> What version of linux-backports-modules-compat-wireless are you running and on which linux kernel?

As I noted above, the kernel is 2.6.38-4. I don't think I have the backports-module but I'll have to check when I get home to be certain.

---

### Post by bwallum on 2011-02-22
> **odysseusjak said:**
> As I noted above, the kernel is 2.6.38-4. I don't think I have the backports-module but I'll have to check when I get home to be certain.

It appears you need compat-wireless-v2.6.38-rc4-1
[http://git.kernel.org/?p=linux/kernel/git/mcgrof/compat-wireless-2.6.git;a=summary](http://git.kernel.org/?p=linux/kernel/git/mcgrof/compat-wireless-2.6.git;a=summary)

---

### Post by odysseusjak on 2011-02-22
But why? Why isn't this built into the kernel? I haven't had to do this previously so why do I need to do it this time?

---

### Post by bwallum on 2011-02-22
> **odysseusjak said:**
> But why? Why isn't this built into the kernel? I haven't had to do this previously so why do I need to do it this time?I don't know, possibly because you are running a development version? Ubuntu is a moving feast and if you run at the front developmental end expect to do some work. If you want stability then try Lucid. If you want to be front endish then follow the normal releases when they are ready. 

Some work then? wireless-compat is kernel specific and you need to keep it in tune with the linux kernel. You might be able to find it in the development repositories. Do you have the development repositories as a software source? I guess you might as you are running on the development kernel. Using synaptic look for linux-backports-modules-compat-wireless and find the appropriate version. Install it and see if you get a better connection.

A lot usually happens prior to release and you can pretty much bet your hat that this issue will be resolved. In the interim...

Let us know how it goes?

---

### Post by odysseusjak on 2011-02-22
Thanks for the reply. It's very informative.

Concerning the expectation: I understand that I'm running an early development release and I can expect to have issues. I've been trying the dev releases every time they come out so I can help with issues. My questions were from that standpoint. I've never had to do this before so I was wondering what the reasons were thia time around.

I'm sorry if I was any trouble. Just trying to help out.

---

### Post by odysseusjak on 2011-02-22
Thanks for the reply. It's very informative.

Concerning the expectation: I understand that I'm running an early development release and I can expect to have issues. I've been trying the dev releases every time they come out so I can help with issues. My questions were from that standpoint. I've never had to do this before so I was wondering what the reasons were thia time around.

I'm sorry if I was any trouble. Just trying to help out.

---

### Post by bwallum on 2011-02-22
> **odysseusjak said:**
> Thanks for the reply. It's very informative.

Concerning the expectation: I understand that I'm running an early development release and I can expect to have issues. I've been trying the dev releases every time they come out so I can help with issues. My questions were from that standpoint. I've never had to do this before so I was wondering what the reasons were thia time around.

I'm sorry if I was any trouble. Just trying to help out.
That's good and apologies if I broke into a rant. No offence intended. Back to topic how did you get on with linux-backports-modules-compat-wireless?

---

### Post by odysseusjak on 2011-02-22
I guess I don't know what I'm doing. I don't find 'linux-backports-modules-compat-wireless' in synaptec.

---

### Post by bwallum on 2011-02-23
> **odysseusjak said:**
> ... I don't find 'linux-backports-modules-compat-wireless' in synaptec.
Try navigating to System>Administration>Update Manager. Look for the Settings button at the bottom left of the Update Manager window, left click and the Software Sources window opens. Look for the Updates tab and make sure all four boxes are checked under the 'Ubuntu updates' section. While you are in the Software Sources window, under the Ubuntu Software tab, check that at least the first four repositories in the' Downloadable from the Internet' section are checked. 

Close the Software Sources window.

In the Update Manager window click on the Check button and make sure you are fully updated.

Close Update Manager and open Synaptic Package Manager. Search for compat-wireless. 

Did you find anything?

---

### Post by zweiundzwei on 2011-02-23
I cannot find the package either, even when checking all options as you said in synaptic.

---

### Post by odysseusjak on 2011-02-23
> **bwallum said:**
> Did you find anything?

Thanks again for the help.

Unfortunately, no, I didn't find anything. I have all four checked in both locations but did not find compat-wireless anywhere.

---

### Post by bwallum on 2011-02-23
> **odysseusjak said:**
> ...
Unfortunately, no, I didn't find anything....
OK we will have to install it. 

Please read the note that kernel headers must be installed and the path as described here:- [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

In summary the important bit from the above ***starts*** here > **Requirements for bleeding edge**

 You need two things: 

[LIST]
[*]A Kernel >= 2.6.24
[*]Your kernel headers installed
[/LIST]
Please be *very sure* you have your kernel headers installed before reporting any sort of build issues with this package. This *usually* will mean having this symlink point to a valid directory with kernel headers in it: 

/lib/modules/`uname -r`/buildThe  exception to this is if you are building the package targeting a kernel  you are not running. Users doing this should read the [Building for external kernels]("http://wireless.kernel.org/en/users/Download#Building_for_external_kernels") section. 
Additionally,  the kernel you're building for needs a valid ".config" file, if it  isn't present compat will assume you have PCI, USB and PCMCIA built into  your kernel and if not, fail building. 
 
**Recommended**

 We recommend these the following userspace applications to be installed: 

[LIST]
[*][wireless-regdb]("http://wireless.kernel.org/download/wireless-regdb/")
[*][CRDA]("http://wireless.kernel.org/en/developers/Regulatory/CRDA")
[*][iw]("http://wireless.kernel.org/en/users/Documentation/iw")
[*][rfkill]("http://wireless.kernel.org/en/users/Documentation/rfkill")
[/LIST]
You can download compat-wireless from here:- [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

EDIT I forgot to add that you will be building compat-wireless on your system and will need to install 'build-essential' from synaptic.

---

### Post by bwallum on 2011-02-23
If you have decided to try compat-wireless and have not compiled code on your machine before it can be quite daunting.

Essentially this is what we do

Install build-essential using Synaptic Package Manager
Download the compat-wireless source code
Check that we have linux kernel headers installed (you most likely will have)
Unpack the source code to a directory, compat-wireless on your Desktop would be a suitable folder. You should see a README file, always worth a look.
Open a terminal and navigate to the unpacked folder e.g. 'cd Desktop/compat-wireless'
Run the command 'make'
If all is well run the command 'sudo make install'
Then 'sudo reboot' 

Thats you. compat-wireless should now be available in synaptic. It is easy to uninstall which you might like to do when compat-wireless becomes mainstream Ubuntu.

---

### Post by david stevenson on 2011-02-24
Well I have tried compat-wireless but still no connection. 
I am now not sure where the problem is, originally the working ath5k  in 10.10 has been updated to a non working one (for me) in 11.04, hence my bug #714300. 
It looks to me that  compat-wireless replaces that kernel module with the latest from the kernel tree ie the same one that just failed.
Can any one confirm this.
David

---

### Post by bwallum on 2011-02-26
I'll upgrade to 11.04 and see if I can reproduce. I will be a while.

---

### Post by david stevenson on 2011-02-26
Well it did connect once, but will not today.
So I guess the original problem is changed to a new one. 
Would still like to get back to 10.10 performance, fast connect and no dropping.

---

### Post by bwallum on 2011-02-27
> **david stevenson said:**
> Well it did connect once, but will not today.
So I guess the original problem is changed to a new one. 
Would still like to get back to 10.10 performance, fast connect and no dropping.

run these two commands in a teminal, one after the other:-```
sudo rmmod -f ath5k
sudo modprobe ath5k nohwcrypt=1
```

Does that fix the problem? If so follow #18 and make the above fix permanent.

---

### Post by macrules on 2011-04-08
> **bwallum said:**
> Apologies for returning to this thread again but I have just solved my ath5k problem in Maverick Desktop 32 bit and thought you might like to have a go in Natty.

[http://ubuntuforums.org/showthread.php?t=1686282](http://ubuntuforums.org/showthread.php?t=1686282)

In summary (following chili555):-```
sudo rmmod -f ath5k
sudo modprobe ath5k nohwcrypt=1
```If that fixes the problem write a configuration file to apply the fix at boot.

```
gksudo gedit /etc/modprobe.d/ath5k.conf 
```Add a single line: ```
options ath5k nohwcrypt=1
```Proofread, save and close gedit. Now, on boot, the parameter should be applied automatically.

AWESOME! worked for me! thank you very much!
can this be reported to the 11.04 devs?

---

### Post by odysseusjak on 2011-04-08
> **macrules said:**
> AWESOME! worked for me! thank you very much!
can this be reported to the 11.04 devs?

Worked for me on my ath9k card!

---

### Post by Gerhard Maag on 2011-04-10
I have a DWA-552.  Worked acceptably in 10.10.  Choked in Natty.  This fix worked for me.  Changed the parameters to ath9k.  Getting speeds I never had before!  Thanks.

---

### Post by theanswriz42 on 2011-04-16
The wireless networking still seems to pause even with the ath9k change on my system, sadly.

---

