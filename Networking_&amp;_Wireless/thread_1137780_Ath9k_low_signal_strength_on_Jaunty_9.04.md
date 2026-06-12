---
title: "Ath9k low signal strength on Jaunty 9.04"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by ngfrazier on 2009-04-25
Hello all,

First, let me say that I am very, very pleased with Ubuntu. God bless all of those who have contributed to making Linux what it is today. It *just* works!:P

However, wireless seems to be a continuous work-in-progress.:( I have an Atheros AR928x pcie wifi in my Dell Mini 9 running the latest Netbook Remix and the wireless signal is simply abysmal. I have other laptops, so I know my signal is good, but from my bedroom (less than 10 ft from my WRT54G tomato-based router), I get about 25%-35% signal strength. 

What can I do?:confused:

I've installed the "linux-backports-module" and even tried the compat-wireless, but nothing seems to improve the signal strength.

---

### Post by SLEEPER_V on 2009-04-26
i seem to be having the same problem, but with a rosewill external card (usb dongle).  Windows picks it up great, 90%, but the Tu only hits 20%-30%, with lots of dropped signals.

---

### Post by ngfrazier on 2009-04-26
I tried but could not get ndiswrapper to work. Is anyone using the Windows drivers on Ubuntu?

---

### Post by freehood on 2009-04-27
> **ngfrazier said:**
> Hello all,

First, let me say that I am very, very pleased with Ubuntu. God bless all of those who have contributed to making Linux what it is today. It *just* works!:P

However, wireless seems to be a continuous work-in-progress.:( I have an Atheros AR928x pcie wifi in my Dell Mini 9 running the latest Netbook Remix and the wireless signal is simply abysmal. I have other laptops, so I know my signal is good, but from my bedroom (less than 10 ft from my WRT54G tomato-based router), I get about 25%-35% signal strength. 

What can I do?:confused:

I've installed the "linux-backports-module" and even tried the compat-wireless, but nothing seems to improve the signal strength

Same issue here with Atheros AR928x also. I wanted to add that it seems that "txpower 20dBm" seems to be the max configureable :-/

---

### Post by juliobahar on 2009-05-02
I'm also experiencing the same problem with my Atheros AR242x wireless device running on this otherwise marvelous distribution of ubuntu (Jaunty). Hope to hear some feedback soon.

Ah by the way, the signal doesn't pick up to 100% as it used to do under Intrepid when I bring my accesspoint close to my computer.

---

### Post by juliobahar on 2009-05-02
> **ngfrazier said:**
> Hello all,

First, let me say that I am very, very pleased with Ubuntu. God bless all of those who have contributed to making Linux what it is today. It *just* works!:P

However, wireless seems to be a continuous work-in-progress.:( I have an Atheros AR928x pcie wifi in my Dell Mini 9 running the latest Netbook Remix and the wireless signal is simply abysmal. I have other laptops, so I know my signal is good, but from my bedroom (less than 10 ft from my WRT54G tomato-based router), I get about 25%-35% signal strength. 

What can I do?:confused:

I've installed the "linux-backports-module" and even tried the compat-wireless, but nothing seems to improve the signal strength.

I had the same problem, but it seems that I've partially solved it using this info that I've got from launchpad (thanks to Alex):

Install those 2 packages:

1-linux-backports-modules-jaunty
2-wicd

Reboot... and inform us of your results

Hope it works

---

### Post by ngfrazier on 2009-05-03
> **juliobahar said:**
> I had the same problem, but it seems that I've partially solved it using this info that I've got from launchpad (thanks to Alex):

Install those 2 packages:

1-linux-backports-modules-jaunty
2-wicd

Reboot... and inform us of your results

Hope it works

I had already installed the backports-module--it certainly helps. I just installed WICD. Excellent program; however, it doesn't seem to improve the signal (which I assume is a driver issue anyway).

Cheers

---

### Post by mrtbone on 2009-05-04
This solved my issue on my asus p5n32-sli onboard wifi!!
I had 14-15% before installing the modules mentioned above and now i get 65-75%


Thanks a lot!

---

### Post by KaiO on 2009-05-05
I have a fresh install of Kubuntu 9 and with KNetworkManager I had, at best, a sluggish wifi connection with my Atheros card (D-Link).
I was unable to use ICA (citrix), kopete etc.
But this solution took care of it!

>Install those 2 packages:
>1-linux-backports-modules-jaunty
>2-wicd

THANKS!

---

### Post by Atrophy on 2009-05-06
I had a similar problem in Intrepid that I solved the same way (without WICD, which i've discovered is nice). running "sudo apt-get install linux-backports-modules-jaunty" definitely fixed this for me.

Edit: I should say this wasn't a matter of signal strength for me. Rather it was going from absolutely no wireless at all, to working wireless (WOOT).

---

### Post by mrtbone on 2009-05-08
> **mrtbone said:**
> This solved my issue on my asus p5n32-sli onboard wifi!!
I had 14-15% before installing the modules mentioned above and now i get 65-75%


Thanks a lot!

And now my USB stops working after a while... Hmm. This is a stopper for me using ubuntu. On the previous distribution I used hours to try to fix the issue, but to no use. Now the issue is back in this new version after doing the installs needed for a reliable wifi connection. I guess my dream of getting rid of the other operating system is never going to be a reality.

---

### Post by forcecore on 2009-05-14
i tried to install backport modules but even close to router max signal is 82% what i get, is that possible that default ubuntu driver is still running and backported module is still offline,??? how to check?

---

### Post by pschulam on 2009-06-22
I have an Atheros AR5008 and was having problems with 9.04 as well.

Installing linux-backports-modules-jaunty along with wicd did the trick. No longer losing the signal and the strength is much greater.

Thank you very much for the tip.

--
Peter

---

### Post by jgull8502 on 2009-06-22
I have been experiencing very flaky wireless Internet with my ar242x on the eee pc. Sometimes it takes quite a while for a page to load. I'm not sure my issue is related to the one in this thread; however the signal strength is pretty low on this laptop compared to my Dell. I installed madwifi and it didn't seem to help much. Right now I'm trying this backports-jaunty package. 

Does anyone have any suggestions? Should I re-enable ath9k in order for the backport trick to work?

---

### Post by jgull8502 on 2009-06-22
Well, I after installing the backports, I tried both the ath5k (apparently 9k doesn't work for me) and madwifi. ath5k seems to work marginally better with less delays when "looking up" pages. They still happen sometimes though.

---

### Post by newbuntu9 on 2009-07-15
> **juliobahar said:**
> I had the same problem, but it seems that I've partially solved it using this info that I've got from launchpad (thanks to Alex):

Install those 2 packages:

1-linux-backports-modules-jaunty
2-wicd

Reboot... and inform us of your results

Hope it works

I have the same experience.
My computer is an Asus laptop with an Atheros AR928X wireless card.
If I boot using Ubuntu 8.10 live CD, my wireless adapter works perfectly.
If I boot using the installed Ubuntu 9.04, the wireless adapter is seen but I cannot use it to connect anywhere.

The problem is that my wired network adapter is also not working... so I am having to boot in Vista to gain access to the Internet.
My plan is to connect to the Internet using Vista, download linux-backports-modules-jaunty and wicd, copy them onto a USB stick and install from there in Ubuntu...

My question: Does anybody know how to install linux-backports-modules-jaunty and wicd from a USB stick?

Thanks

---

### Post by David_UK on 2009-08-08
> **Atrophy said:**
> ... running "sudo apt-get install linux-backports-modules-jaunty" definitely fixed this....

Yep, doing just this took me from 15% to 80% signal (similar to Win2000).

---

### Post by CookieTrain on 2009-10-22
Thx a mil. I have an Aspire 5738z, installing backports and wicd seems to have fixed this problem for me.  Thx Ubuntu community, u r awsum!

---

### Post by angelsguitar on 2009-11-01
Hi all!

I know this post is about ath9k on Jaunty, but wanted to ask:  Anyone out there using karmic already? Do the low signal problem persists?  At least on my machine I'm using karmic and the low signal problem still is there.  Haven't installed the backport modules yet.

Edit: Well, just installed the linux-backports-modules-wireless-karmic-generic (what a huge name for a package!!).  My signal went from 12-14% (before installing the package) to 50-54% (after installing the package and rebooting), using the laptop on the same spot.  So I can confirm that karmic suffers from the same problem, but the fix also works (at least in my computer)

---

### Post by superfar on 2009-11-02
Hi,

Can someone explain how the linux-backports-headers works to get the card working??

I have an AR5008 card and its seen in Ubuntu 9.04, I just have no networks available when using the network manager and with a iwlist scanning, I get No Scan Results.

Thanks in advance :-)

---

### Post by pablo atheist on 2009-11-27
> **juliobahar said:**
> Install those 2 packages:

1-linux-backports-modules-jaunty
2-wicd

Reboot... and inform us of your results

Hope it works

thank you very much! works perfect with an atheros ar9285 on ubuntu 9.10

---

### Post by bean1945 on 2009-11-27
I used the back port fix and my signal strength increased as did my transmissions speeds.

---

### Post by Rook777 on 2009-12-26
Installing linux-backports-modules-jaunty and wicd worked perfectly for me.  I went from having a very crappy signal (mostly not even connecting) to having a great connection with very fast speed.  Thank you very much.  This made me a very happy man.

---

### Post by gunbladeiv on 2009-12-30
it work on karmic too. 
package you need to install is:

1) linux-backports-modules-karmic
2) wicd

But I'm not sure if it working with the default gnome-network-manager as well, cuz I tried with wicd on the first place. If it's the modules problem, then it will also working with the default network manager as well. If anyone got info about this, please do share. 

Thanks and Good Luck.

---

### Post by angelsguitar on 2009-12-30
> **gunbladeiv said:**
> it work on karmic too. 
package you need to install is:

1) linux-backports-modules-karmic
2) wicd

But I'm not sure if it working with the default gnome-network-manager as well, cuz I tried with wicd on the first place. If it's the modules problem, then it will also working with the default network manager as well. If anyone got info about this, please do share. 

Thanks and Good Luck.

I can confirm it works with network manager as well

---

### Post by davros0 on 2010-03-14
"sudo apt-get install linux-backports-modules-jaunty"
Worked like a charm thanks a lot. 58% signal boosted to 98%. I appreciate the help.

---

