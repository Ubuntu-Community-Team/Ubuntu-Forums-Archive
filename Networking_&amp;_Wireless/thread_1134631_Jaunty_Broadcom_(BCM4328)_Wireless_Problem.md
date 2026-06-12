---
title: "Jaunty Broadcom (BCM4328) Wireless Problem"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by nexusnode on 2009-04-23
Hi all,

appear to be having a problem with my laptop's wireless now I have just installed 9.04.  8.10 also had a problem, but only showed itself when connective to WPA2 networks.  8.04 on the other hand worked flawlessly.  In this version though, the problem appears to have gotten worse - now the network manager can't see my wireless card at all!

So...

The machine is an HP tx1340ea, with a Broadcom BCM4328 network controller.

Its a bit weird, I was actually posting a problem report but then I was going through the steps in various troubleshooting threads to try and give some useful information and it started working!

The sequence of events since I installed it fresh this time round was:
I uninstalled the Broadcom STA wireless driver, restarted, used the switch on the front to turn the wireless card off, restarted, used the same switch to turn it back on, restarted, reinstalled the Broadcom STA wireless driver, restarted.  Hey-presto!  It appears to be working.

It even seems to still work after multiple normal reboots!

Hope this is helpful to someone, if anyone has a logical explanation for this I would also love to hear it!

---

### Post by Ambivalent on 2009-04-23
I have the same issue and what you did fixed it for me as well!

In windows that would have been the first thing I tried... I don't tend to think that way when using Linux...

---

### Post by ataris_kid on 2009-04-23
Thanks a ton dude, I just had the same issue and this worked. Kind of a silly fix.. I'd like to know the logic behind this as well!

---

### Post by chmorgan on 2009-04-24
I submitted a bug for this issue, [https://bugs.launchpad.net/ubuntu/+bug/365857](https://bugs.launchpad.net/ubuntu/+bug/365857) with the hope that a fix that doesn't require rebooting will be found. I may try out the rebooting technique but I'm not sure that I'm properly uninstalling the driver since I'm using the kubuntu hardware driver manager jockey.

---

### Post by chmorgan on 2009-04-24
From this thread, [http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218) I tried the fix that someone recommended of:

sudo rmmmod ssb
sudo modprobe wl

And bam, the wireless device started showing up in the network management plasmoid and I'm able to connect and use wireless. I don't know how to ensure that this happens after rebooting though.

---

### Post by chmorgan on 2009-04-24
To clarify, this lets wifi work for me but I'm not sure if this is using the "broadcom sta wireless driver" listed in the hardware driver manager, it may be using the default kernel drivers for broadcom chips so it may not be equivalent at all to the originally suggested fix in this thread.

---

### Post by chrono310 on 2009-04-25
Wow, thanks! This worked for me. So many reboots, though...

---

### Post by Matoridi on 2009-04-30
Well.... Deinstalling and reinstalling the driver (after all those reboots) worked for my HP DV2620 laptop!

Thanks nexusnode!

---

### Post by itnet7 on 2009-05-07
Thanks nexusnode! You saved me a call to Dell tech support, I am confirming that this fix works with a Dell XPS 1730 with a BCM4328 802.11a/b/g/n card as well! This is under Jaunty, but it's important to note that I had also tried booting into a live cd environment for 8.10 and it wasn't working by default there as well. 
[This forum post also restored connectivity]("http://ohioloco.ubuntuforums.org/showpost.php?p=7131541&postcount=8"), but yours seems more permanent!

Thanks so much for taking the time and posting this. 

Chris C. 
itnet7 
#ubuntu-us-fl

---

### Post by WolfWitch on 2009-05-18
I had this same problem with a Dell Latitude D430. It was driving me crazy since this is the first time in probably two years I've actually had wireless problems with Ubuntu.

The multiple reboot/on-off wireless switch combinations posted here didn't work for me, but installing b43-fwcutter did the trick. I just installed it via Synaptic, rebooted, and now wireless works flawlessly. No idea why this wasn't a problem in Hardy.(!)

---

### Post by Shmooglypoof on 2009-05-19
Hi I've been having the same problem for quite a while now and the link on Post #6 was great because it enabled the driver so now it is scanning for networks but it won't actually connect to any of my networks.  In the FAQ i followed in Post #6 the command where it started to have errors was this command:

sudo modprobe ndiswrapper

which came right after the: sudo rmmod commands

The error I'm getting is this:

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

I'm kinda a beginner but this error makes me feel like im missing a file. It seems like any solution command someone gives me just has the same outcome error. The same error appears if i do...

sudo modprobe wl 


Additional information:

lsmod: beginning prints
Module                  Size  Used by
wl                   1489748  0 
b44                    35984  0 
ssb                    41220  1 b44
ndiswrapper           193308  0 


lshw -c network: prints

*-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wlan0
       version: 03
       serial: 00:90:4b:44:68:93
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.54+ASUS,03/22/2004, 3.60.7.0 latency=128 module=ndiswrapper multicast=yes wireless

I'm so tired of this problem please help me :o
-Shmoog

---

### Post by plhansen on 2009-05-21
Just another "me too" for another machine: HP Pavilion dv2000.  The multi-restart sequence appears to have worked well here too.  Thanks!

---

### Post by Matoridi on 2009-05-26
I had to reinstall Ubuntu 9.04 on my HP DV2620 laptop (for another problem I created while messing around),

On a hunch, I simply uninstalled the driver, re-booted, re-installed the driver and re-booted again, and this solved my problem more quickly...

---

### Post by dionatan on 2009-07-24
Hown can I uninstall this driver?!

---

### Post by Mechwizard on 2009-07-24
Connect: YES
Connect with WPA-PSK encryption: NO
This seems to be my real problem. In order for my wi-fi to be truly working, I must be able to connect with WPA. No choice.
I here that the regular's are getting WPA encryp and am wondering what type of set-up they are using. I have used native drivers and ndiswrapper( w/ndis recommended driver), both to the same end, no WPA. Wired works great.
Any Ideas on how to get encryption working?

---

### Post by Jeremiah478 on 2009-07-25
This seems to have worked for myself as well.  I followed the sequence and at first I thought it was a fail, but I had in my attempts to get the wireless working installed WICD and removed network manager.  I guess WICD wanted me to actually specify the wireless card (ex 'eth1') in the properties page.  Once I did that it worked no problem.

Thanks again for the help!

---

### Post by Mechwizard on 2009-07-27
> **Jeremiah478 said:**
> This seems to have worked for myself as well.  I followed the sequence and at first I thought it was a fail, but I had in my attempts to get the wireless working installed WICD and removed network manager.  I guess WICD wanted me to actually specify the wireless card (ex 'eth1') in the properties page.  Once I did that it worked no problem.

Thanks again for the help!

Hi Jeremiah478,
  Did this process get WPA encryption working for you?
I didn't remove 'Network Manager' before trying these steps. I Will remove andlet you know if conflict is the issue.

---

### Post by anant29 on 2009-09-08
Hello,

i installed ubuntu on my HP tx1000z a month back. The wifi didnt work out of the box so i looked for a solution on this forum and after mulling over it a few days, the wifi worked after the solutions provided in the following thread. the solution was more like go to 'hardware drivers' deactivate/activate broadcom STA drivers followed with a restart. 

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=703374&page=2](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=703374&page=2)

it was working fine untill a few days back. Some how the wifi stopped showing in the network manager. I tried all the solutions provided around ndiswrapper and the links i had used, that made it work in the first place. But it just wouldnt work.

i am trying to install the broadcom STA drivers provided at ([http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)) following the instructions in readme file. that didnt work.

I have the wifi enabled from the switch, the light is turned on, bluetooth symbol shows up, but lspci command does not return the wifi hardware in the list.

I dunno what to do! i dont even know if my wifi H/W is intact or burned off? none of the solutions seem to rescue. i have been trying to solve this for over a week now. :( please help.

---

### Post by staticextasy on 2009-09-27
You have just saved me man, let me tell you i was going nuts here trying to figure this out, i have tried everything in google, every sticky i could find on forums and stuff and you know what THIS ONE WORKED....


Literally i have spent two hours trying to get my wireless card to work and here this guy says flip a switch restart flip more restart again and install and what the hell it works... 

Sounds like something you do to a soda vending machine

"press 1 once, press 3 twice, press 6 3 times: get all free soda you want"

You have to do it in that same exact order too i tried 3 times before i did it right i guess. Thanks man.

---

### Post by Henery on 2011-09-27
Wow this worked for me too i have been stuck on this issue for a month I ended up upgrading to fix it but 11.04 and 11.10 suck so I reinstalled and found this page!!
I thought the same thing ya right press this reboot bla bla I though but it works thank you so much!
Got my old gnome back!!!!!

---

