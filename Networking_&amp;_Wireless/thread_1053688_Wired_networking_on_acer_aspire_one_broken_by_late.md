---
title: "Wired networking on acer aspire one broken by latest update"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by denden on 2009-01-28
Hi all,

I've just updated my acer aspire one (ubuntu 8.10 desktop) through the update manager gui, it installed new avahi, new kernel, among other things. 

Anyway, i reboot and the wired networking no longer works! Ifconfig still shows it as being there and auto eth0 comes up in the network manager, however it cant connect. DHCP just hangs weather it be through the network manager or using #> sudo dhclient eth0

/etc/network/interfaces had nothing but loopback in it, adding:

auto eth0
iface eth0 inet dhcp

didn't change anything.

Manually booting into the 2.6.27-7 kernel through grub makes everything work fine. 

Any ideas on making 2.6.27-11 work?

---

### Post by dingJam on 2009-01-29
I have a Dell Mini 9 with 8.10 installed (replaced Dell 8.04 version) and the same thing happened to me when I updated via the update manager today.  Like you, I remember seeing the kernel updates among a number of other things.

Wired networking no longer works.  Tried a number of cables and ports to make sure the connection was good but no luck.  Problem began the first time I rebooted after the update, as the actual update was obtained using the previously working wired connection.  

Interestingly wireless is working still...

Looking forward to further comments/suggestions.

---

### Post by gmc on 2009-01-29
I Don't have a solution, but I'm glad to see that I'm not the only one who found the -11 kernel broke the wired network connection. I thought it might have been because I have the proposed/backport repo's enabled.

I'm sure the problem will be corrected shortly, so in the meantime, I'll stick with the -9 kernel.

G

---

### Post by xltrigger on 2009-01-29
I have the same problem on my aspire one. When I reboot after 2.6.27-11 it kills ethernet. It also killed my wifi put reinstalling madwifi-hal fixes that. I don't know how to get my ethernet back.

---

### Post by jon9314 on 2009-01-29
ive got the same problem hope they fix it soon

---

### Post by xltrigger on 2009-01-29
It doesn't look like it is showing up in lspci anymore.

```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
04:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
04:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
04:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
04:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
```

If I remember right this is the same behaviour as before. I've aleady reinstalled once on the machine before. As soon as it updates to 2.6.27=11 I lose my ethernet. Last time it would randomly appear every 9 or 10 boots.

---

### Post by robertcliche on 2009-01-29
Same effect and work-around (Wireless is broken) on my IBM x200 laptop - it uses the Atheros wireless LAN card.

---

### Post by Ekre on 2009-01-30
same prolem on thinkpad r50e. too bad, kernel -9 wont work for me as well. but i dont have any problems with lan, i see all the clients, shares, so on (they see me as well, and they see my pc via VPN), i have problems reaching WAN.
too bad, i dont have any workarounds, so i have to install an another os (accessing WAN is critical for me)

got a workaround:
just tried to ping hup.hu, which one doesnt work. just asked my collegue to resolve its ip for me, then tried to ping that ip. that worked. so something wrong with name resolving. 
just opened /etc/network/interfaces, deleted everything related to eth0 and then manually added everything, again (NetworkManager f'ked up everything)
now its working as intened.

still sorry for my crappy english.

---

### Post by Tuliku on 2009-01-30
Same issue on a Toshiba NB100.
Kernel .11 killed my wired connection, rebooted now in the .9 kernel and all is working smoothly like before...

Updating now some packages, lets see if it works.

---

### Post by Tuliku on 2009-01-30
Just updated ubuntu using synaptic package manager, and installed the latest kernel (.11) again, and after restart, wired networking was again not functioning.

Going back to .9 and will wait for a fix....

---

### Post by Line on 2009-01-30
Hi!
My Acer Aspire one wired/wireless stopped working after update to
How is it possible to go back to this kernel .9?

---

### Post by Tuliku on 2009-01-30
During start up when grub load,s i have a 3 second choice to choose to load the menu, and there you can choose it.

Or you can edit the menu.lst in /boot/grub/ and then at "load at default 0" change the 0 into 2 (that should be the .9 version)

---

### Post by Cuppa-Chino on 2009-01-30
mine (networking on the other computer) is completely killed, neither -7 -9 or -11 work.... pretty clueless

---

### Post by Ekre on 2009-01-30
> **Cuppa-Chino said:**
> mine (networking on the other computer) is completely killed, neither -7 -9 or -11 work.... pretty clueless

i had that too, tried with all available kernels. then just cleared /etc/network/interfaces (for eth0) and then write back my settings (manually, NetworkManager just did something wrong) and now its fine. maybe thats help.

---

### Post by Cuppa-Chino on 2009-01-30
> **Ekre said:**
> i had that too, tried with all available kernels. then just cleared /etc/network/interfaces (for eth0) and then write back my settings (manually, NetworkManager just did something wrong) and now its fine. maybe thats help.

will try, although I use wicd.... but worth a shot

---

### Post by jon9314 on 2009-01-30
> **Ekre said:**
> same prolem on thinkpad r50e. too bad, kernel -9 wont work for me as well. but i dont have any problems with lan, i see all the clients, shares, so on (they see me as well, and they see my pc via VPN), i have problems reaching WAN.
too bad, i dont have any workarounds, so i have to install an another os (accessing WAN is critical for me)

got a workaround:
just tried to ping hup.hu, which one doesnt work. just asked my collegue to resolve its ip for me, then tried to ping that ip. that worked. so something wrong with name resolving. 
just opened /etc/network/interfaces, deleted everything related to eth0 and then manually added everything, again (NetworkManager f'ked up everything)
now its working as intened.

still sorry for my crappy english.

that was the problem now it works better than before it broke(the applet can see my wired connection)

---

### Post by 5BallJuggler on 2009-01-30
If you are still having problems try this.

[http://ubuntuforums.org/showthread.php?t=1054629](http://ubuntuforums.org/showthread.php?t=1054629)

---

### Post by xltrigger on 2009-01-31
> **5BallJuggler said:**
> If you are still having problems try this.

[http://ubuntuforums.org/showthread.php?t=1054629](http://ubuntuforums.org/showthread.php?t=1054629)

This thread is supposed to be about wired ethernet not working after the update. I have the solution for wireless that works for me. I use the latest snapshot of madwifi-hal. I have to recompile it for the new kernel each time the kernel updates. I am kewl with that. I need to know why 11 kills my wired ethernet and what I can do to fix it.

---

### Post by eclectus on 2009-01-31
I was also able to get wireless working again in -11 by reinstalling madwifi-hal on my Acer AspireOne, as well as roll back successfully to the -9 version.  No luck getting wired ethernet to work yet, even without network-manager in the loop.

---

### Post by rox_lukas on 2009-02-01
Same problem here after upgrade to .11
BTW, madwifi works just fine with this kernel (of course it needs to be recompiled).

```
root@mikrus:/# ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:1e:68:d5:bd:aa  
          inet6 addr: fe80::21e:68ff:fed5:bdaa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:1308622770 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 

root@mikrus:/# ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:1e:68:d5:bd:aa  
          inet6 addr: fe80::21e:68ff:fed5:bdaa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:1325399985 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 

root@mikrus:/# ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:1e:68:d5:bd:aa  
          inet6 addr: fe80::21e:68ff:fed5:bdaa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:1342177200 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 

root@mikrus:/# lspci | grep Realtek
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev ff)

```

Did you notice the "dropped" counter? It increases rapidly. Maybe a different kernel module would be able to use the ethernet adapter properly?

EDIT: what I found on google suggests we should use r8101 module instead of r8169. It is not compiled in ubuntu stock kernel, neither as a module. I will try compiling the module tomorrow to see if it works.

---

### Post by menachem on 2009-02-01
I have an Acer Aspire One running Kubuntu Intrepid. I use Wicd for network connectivity. I have this same problem as well. With kernel 2.6.27-11, I can't get my wired connection to work. With kernel 2.6.27-9 my wired connection works fine.

Has anybody created a bug report for this? If so, can they post a link?

---

### Post by kiyolee on 2009-02-01
If wired network becomes broken after installed -11, I have tried one thing that helped to fix that after rebooting back to -9. Click on the NetManager icon and select Edit Connections. Then delete "Auto eth0" (or maybe "Auto Ethernet"). Logout and log back in (or may need to reboot).

---

### Post by IMS500 on 2009-02-01
Same problem here.
2.6.27-7  Wired and Wireless works
2.6.27-9  Wired and Wireless works
2.6.27-11 Wired and Wireless DO NOT WORK!

---

### Post by DavidFourer on 2009-02-01
> **denden said:**
> Hi all,
...
Manually booting into the 2.6.27-7 kernel through grub makes everything work fine. 
Any ideas on making 2.6.27-11 work?
***Solved--see thread [http://ubuntuforums.org/showthread.php?p=6669744#poststop](http://ubuntuforums.org/showthread.php?p=6669744#poststop) 

I have the same problem on Dell Inspiron 6000.  Upgraded from 8,04 to 8.10 this afternoon and no internt access.  I have no recent kernels (2.6.27...) on my system.  The old old kernels (2.6.24...,2.6.14 ??) don't help, which makes me suspect network-manager.  I would love to get any kind of patch to get on line so I can download stuff or at least use my home computer.  Possibly I can run some alternative to network-manager, if it's installed--as I can't download anything.  I'm afraid I'm screwed if I can't get on line some how. 

I have enough know-how to edit a config file or read a log file if I know what I'm looking for.

I booted from an old Ubuntu Live CD and got a connection, opened the network manager and got some info:
eth0, 100 bps driver b44, plus I wrote down the IP address, broadcast address, Subnet mask, default route, primary dns, secondary dns, hardware address.  

Maybe I can set up an internet connection with that info without using the network-manager, which seems to be causing the problem.  

I also tried using synaptic package manager to remove and re-install the network-manager, which did not help.  

Wireless roaming appeared in network manager at first, but now it shows nothing I rarely get a connection anyway.  The broadcom driver is installed but I so seldom got it working that I gave up on it long ago.

And I ordered an installation CD by mail to do a fresh install, if nothing else works, but I really want to avoid that.

Thanks for any suggestions
David, Chicago, IL

---

### Post by endesign on 2009-02-02
I have this problem too - using -9 kernel to write this.

---

### Post by warren94 on 2009-02-02
I had this problem, for four days, then i reverted back to .7, then guess what, nothing!
so i re-installed linpus and ubuntu!

then ,i  cannot get .9, so i am running .7


but its all good at the momebt in . 7,

---

### Post by dragonmojo on 2009-02-03
If editing the /etc/network/interfaces will work, I'm trying it. However, being the n00b I am, I cannot seem to save this file due to lack of necessary permissions.

I have a Dell Mini9 w/Intrepid Ibex, latest updates, no wired network connection anymore.

---

### Post by 5BallJuggler on 2009-02-03
> **dragonmojo said:**
> If editing the /etc/network/interfaces will work, I'm trying it. However, being the n00b I am, I cannot seem to save this file due to lack of necessary permissions.

I have a Dell Mini9 w/Intrepid Ibex, latest updates, no wired network connection anymore.

Try opening the file from a terminal with 

**sudo gedit /etc/network/interfaces**

when you close it, it should allow you to save.

---

### Post by ThatGuy07 on 2009-02-04
Acer aspire one having the same problem. im booting from 9 for now,

someone asked about a bug report and a link, anyone got some info on that?

---

### Post by Wolfhere on 2009-02-04
> **denden said:**
> 
/etc/network/interfaces had nothing but loopback in it, adding:

auto eth0
iface eth0 inet dhcp

didn't change anything.



Try editing the interfaces file to:

auto eth0 inet dhcp

I had lost wired and wireless was working following the kernel upgrade. The auto eth0 line showed up at the end of the interfaces file after the my entry for static assignment (so samba would work). I had the same issue as we all have when upgrading from 8.04 to 8.10. And editing the interfaces file fixed it then also. Apparently, this kernel upgrade replicates the same issue.

---

### Post by clcoyle on 2009-02-04
> **Wolfhere said:**
> Try editing the interfaces file to:

auto eth0 inet dhcp

I had lost wired and wireless was working following the kernel upgrade. The auto eth0 line showed up at the end of the interfaces file after the my entry for static assignment (so samba would work). I had the same issue as we all have when upgrading from 8.04 to 8.10. And editing the interfaces file fixed it then also. Apparently, this kernel upgrade replicates the same issue.


I'm still using 8.04, and in the process of trying to get my windows mobile device to sync up using SynCE , I did the apt-get update and got this problem.    

I notice a couple of things, though.   One is that none of these fixes fix mine, and it isn't the eth0 that is broken - I can ping the gateway, the DNS, my router, and my xp machine downstairs just fine.  I just can't get on the internet.  

Now, just WTH is up with that??

I wish I was just a little smarter and less of a n00b.  I don't even know how to lick my wounds, reverse this mess, and wait for sunny days.   

](*,)

---

### Post by rox_lukas on 2009-02-07
I have done a  BIOS upgrade from 3301 version to 3309 in attempt to solve loud cooler issues, and I am surprised to notice that this also fixed wired networking problems with kernel 2.6.27-11.

EDIT: False alarm :( Wired net is again gone after reboot :( I keep wondering why it worked for this one time. I did not do anything out of ordinary...

---

### Post by kitchensink on 2009-02-07
I have the same issue,  cannot connect to wired network after the latest update on my acer aspire one.  I have edited the file /etc/network/interfaces to add 'auto eth0 inet dhcp'.   Can some one please help.  I have updated to bios 3309...


Thanks

---

### Post by dgrafix on 2009-02-07
Same problem on my aspire one. Wired network, sound and mic all gone :(

Running Ubuntu eee

---

### Post by jcwill on 2009-02-07
> **rox_lukas said:**
> I have done a  BIOS upgrade from 3301 version to 3309 in attempt to solve loud cooler issues, and I am surprised to notice that this also fixed wired networking problems with kernel 2.6.27-11.

I tried the bios update to 3309 and my wired connection is still fried in 2.6.27-11.

---

### Post by pib712 on 2009-02-07
Same problem for me too. For anyone who doesn't know, you can sort it with *sudo pico /boot/grub/menu.lst*, commenting the first two boot options (both for the .11 kernel version), saving and rebooting.

---

### Post by delboy1 on 2009-02-07
> **pib712 said:**
> For anyone who doesn't know, you can sort it with *sudo pico /boot/grub/menu.lst*, commenting the first two boot options (both for the .11 kernel version), saving and rebooting.

Sorry, could you explain that for us linux noobs. What does "commenting the first two boot options" mean

---

### Post by DavidFourer on 2009-02-07
> **kitchensink said:**
> I have the same issue,  cannot connect to wired network after the latest update on my acer aspire one.  I have edited the file /etc/network/interfaces to add 'auto eth0 inet dhcp'.   Can some one please help.  I have updated to bios 3309...
Read through this thread and see if it is what you need.  I got mine working, buy turning off Network Manager, and setting the IP address and Route (default gateway) address by other means.
[http://ubuntuforums.org/showthread.php?p=6669744#poststop]("http://ubuntuforums.org/showthread.php?p=6669744#poststop")

---

### Post by dragonmojo on 2009-02-09
> **pib712 said:**
> Same problem for me too. For anyone who doesn't know, you can sort it with *sudo pico /boot/grub/menu.lst*, commenting the first two boot options (both for the .11 kernel version), saving and rebooting.

I did not know that, and after days of frustration trying all the suggestions, your solution to comment out the latest updates *worked*. Many thanks!!
:)

---

### Post by Flashfox on 2009-02-18
> **delboy1 said:**
> Sorry, could you explain that for us linux noobs. What does "commenting the first two boot options" mean

First and foremost "caveat emptor". I am not responsible if you mess-up the file.

I am also a NOOB, but here is what I learned and did on my Acer Aspire ONE:

To edit both entries, start terminal and enter "sudo pico /boot/grub/menu.lst"

Scroll to where you see something like: "title  UBUNTU 8.10, kernel 2.6.27-11-generic".

Add "## " (that's crosshatch, crosshatch space) to the beginning of each line. 

Continue to add the "## " before each line (title, root, kernel, initrd) for the two -11 generic entries. One is (recovery mode)

Do NOT change anything when you see -9 or -7 entries. I had no -9 so I reverted to -7.

To save, press and hold <Ctrl> then press the letter o (WriteOut) to save the file.

After the reboot, Ubuntu started using the -7 code and I regained wired Ethernet access.

Here is what the first edit looks like:

## title   Ubuntu 8.10, kernel 2.6.27.11-generic
## root    ()/ubuntu/disks
## kernel  /boot/vmlinuz-2.6.27-11-generic root=UUID=504823AE48239$
## initrd  boot/initrd.img-2.6.27-11-generic

Mind you, your screen might be different as I installed Ubuntu within Windows XP. However, my goal was to show you how to comment out a line using the ##.

---

### Post by worldsayshi on 2009-03-27
> **ThatGuy07 said:**
> Acer aspire one having the same problem. im booting from 9 for now,

someone asked about a bug report and a link, anyone got some info on that?

Bug report here: [URL="https://bugs.launchpad.net/ubuntu/+source/linux/+bug/326891"]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/326891
[/URL]

Here's a related ubuntuforums-thread: [http://start.ubuntuforums.org/showthread.php?t=1017057]("http://start.ubuntuforums.org/showthread.php?t=1017057")

---

### Post by truant on 2009-04-06
Bah.  Stock kernels are for people who don't have tiny laptops with limited resources.  Suggest y'all go and get sickboy's custom kernel debs from [http://aspireonekernel.com/](http://aspireonekernel.com/)

Download, install, job done.  Networking, sound, even the wifi led works flawlessly.  Faster boot times too, by quite some margin from the generic kernel.  Am using these + intrepid + mintlinux for maximum tinycomputer slickness.

Oh, would also recommend [http://wicd.sourceforge.net](http://wicd.sourceforge.net) as replacement for Network Manager.  Much nicer.

---

