---
title: "Cisco Aironet 350 with airo-wpa driver and Network Manager"
date: 2010-06-20
forum: Networking &amp; Wireless
---

### Post by tenwiseman on 2010-06-20
Folks, I&#8217;ve been playing around with an ancient Cisco Aironet 350 Series PCMCIA 802.11b wireless card, and now have a useable setup using WPA encryption and Network Manager on Ubuntu 10.04.

This is not an ndiswrapper solution, but one using a driver developed at [http://gna.org/projects/airo-wpa/](http://gna.org/projects/airo-wpa/)

A couple of things to note

[INDENT]1) To get this alternative driver working, you will have to compile it
2) The driver doesn&#8217;t autoswitch between WPA and WEP encryption modes[/INDENT]

Also you may have to work around a small bug &#8211; but possibly be able to help fix it?

Interested? Read on ):P


My card (AIR-PCM352) had been previously flashed using a Cisco utility in Windows XP, with the last available firmware for the device &#8211; version 5.60.22. You will have to do similar. I'm not sure if this flash operation can be done in Linux.

[SIZE="4"]Checking the Current Driver[/SIZE]

There is an included driver for this in Ubuntu 10.04, using the following files

[INDENT]**Modinfo &#8211;n airo**
/lib/modules/2.6.32-22-generic/kernel/drivers/net/wireless/airo.ko

**Modinfo &#8211;n airo-cs**
/lib/modules/2.6.32-22-generic/kernel/drivers/net/wireless/airo_cs.ko[/INDENT]

If it is installed correctly you should be able to do a scan of local networks and it will tell you the encryption scheme in use. The following command should let you do that.

[INDENT]**iwconfig**

**sudo iwlist eth0 scan**[/INDENT]

Note that it may be eth1 if you have another network adaptor in your computer. Ignore the wifi0 interface, it doesn&#8217;t do us much for the following trip.

---
[INDENT]
BTW, The following location contains &#8216;files&#8217; with information about the current configuration of the card.

/proc/drivers/aironet/eth0

e.g. /proc/drivers/aironet/eth0/Status &#8211; contains info like firmware version.[/INDENT]

---

Now the interesting thing about the above driver is that it does show the reception of WPA encrypted access points and reportedly WPA2 &#8211; though I can&#8217;t test this here. 

However, sadly that was all! I couldn&#8217;t get this version of the driver to work at all with WPA.

Boo. Maybe there is some voodoo that may make it work somewhere else, but I did check out the source from the kernel and couldn&#8217;t find much WPA goodness in it :mad:


[SIZE="4"]The airo-wpa Driver[/SIZE]

:) I found that almost wholesome goodness in the source at the following URL

[INDENT][http://svn.gna.org/viewcvs/airo-wpa/branches/kernel/](http://svn.gna.org/viewcvs/airo-wpa/branches/kernel/)[/INDENT]

So grab yourself a copy of **airo.c**, **airo_cs.c**, **Makefile** and **airo.h** and place them in a directory ready for some modification and compiling work.


[SIZE="4"]Patching[/SIZE]

Now, these files will need a little bit of patching to play nicely with 10.04

In **airo_cs.c** there currently is (for rev 16) a line that contains
 
[INDENT]**pcmcia_parse_tuple(link, &tuple, &parse)**[/INDENT]

Remove the link parameter, leaving this,

[INDENT]**pcmcia_parse_tuple(&tuple, &parse)**[/INDENT]

Now the Makefile also needs a little modification

The line

[INDENT]**obj-m := airo.o**[/INDENT]

change it to

[INDENT]**obj-m := airo.o airo_cs.o**[/INDENT]


[SIZE="4"]Compiling[/SIZE]

From terminal in that directory, issue the following command to compile and create two new modules airo.ko and airo_cs.ko

[INDENT]**make all**[/INDENT]

You will notice one warning for airo_cs.c about DEBUG something. Just ignore that. If you have other issues like errors then you can do the following command to clean up before another make attempt.

[INDENT]**make clean**[/INDENT]


[SIZE="4"]Installing [/SIZE]

Firstly the inserted card should be stopped, and drivers removed.

The following command will tell you the socket number for your card (0 or 1)

[INDENT]**sudo pccardctl ls**[/INDENT]

Run the following (with your socket number, mines 1) to stop the card and remove the old driver so we can replace files.

[INDENT][B]sudo pccardctl eject 1
modprobe &#8211;r &#8211;v airo_cs[/B][/INDENT]

Make a backup copy (somewhere outside the /lib directory) of the current airo.ko and airo_cs.ko files at

[INDENT]/lib/modules/2.6.32-22-generic/kernel/drivers/net/wireless[/INDENT]

And replace them with the new ones you created.

Create a new file **/etc/modprobe.d/install-airo.conf** with the following line in it.

**install airo /sbin/modprobe -&#8211;ignore-install airo wpa_enabled=1**

Now restart your machine.


[SIZE="4"]Testing[/SIZE]

With some luck you should now find that Network Manager finds WPA networks and accepts passkeys to be entered. If so, you are almost good to go.

If not, then check that the interface **eth1** is not mentioned in **/etc/network/interfaces** and that the last line in **/etc/Network Manager/nm-settings.conf** looks like

[INDENT][B][ifupdown]
managed=true[/B][/INDENT]

You should not need to do anything to the setup of wpa_supplicant.

[SIZE="4"]The Bug[/SIZE]

However, it might not be that straightforward.

For me, although every other network machine in this house was able to be pinged by this machine, this did not include the internet router &#8211; unfortunately leading to no internet access!

:confused:

I got repeated &#8216;bad mic on RX&#8217; messages in the **/var/log/syslog **file when the ping command failed. Boo #2 

:)

The workaround was simple though. Either issue the following two commands from a terminal,

[INDENT]
[B]sudo pccardctl eject 1
sudo pccardctl insert 1[/B][/INDENT]

Or physically remove and reinsert the wireless card. Whatever, you should have full router and internet access after the card restarts.

And BTW I didn't code any of this! Refer back to the airo-wpa source website and pay your kudos to those guys!

And that&#8217;s it! Enjoy. :guitar:

---

### Post by fmjrey on 2010-09-08
I followed your instructions but the new drivers failed, here are the messages
```
Sep  8 17:03:36 silver kernel: [   68.556026] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0
Sep  8 17:03:36 silver kernel: [   68.556035] pcmcia_socket pcmcia_socket0: cs: memory probe 0xfa000000-0xfbffffff: excluding 0xfa000000-0xfa1fffff 0xfae00000-0xfaffffff
Sep  8 17:03:36 silver kernel: [   68.561186] pcmcia 0.0: pcmcia: registering new device pcmcia0.0
Sep  8 17:03:36 silver kernel: [   68.597238] airo_cs: Unknown symbol init_airo_card
Sep  8 17:03:36 silver kernel: [   68.597932] airo_cs: Unknown symbol stop_airo_card
Sep  8 17:03:36 silver kernel: [   68.598773] airo_cs: Unknown symbol reset_airo_card
```

Any idea how to solve this?
I've installed the packages build-essential and linux-headers corresponding to my kernel:
```
$ uname -a
Linux silver 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:24:04 UTC 2010 i686 GNU/Linux
$ aptitude show linux-headers-`uname -r`
Package: linux-headers-2.6.32-24-generic
State: installed
Automatically installed: yes
Version: 2.6.32-24.42

```

---

### Post by tenwiseman on 2010-09-08
Hmmm. Bit difficult at the moment to check this, as the configured system is now installed elsewhere.

However, double check that both newly compiled versions of airo.ko and airo_cs.ko are truely in the directory

[INDENT]**/lib/modules/2.6.32-{xx}-generic/kernel/drivers/net/wireless **[/INDENT]

and are at the same locations as returned by the modinfo command as the previous ones were (see start of my post).

Then do a 'depmod -n | more' and search that the mentioned dependancies for airo_cs.ko haven't got directed elsewhere.

In that output should be these lines

```

kernal/drivers/net/wireless/airo.ko:
kernal/drivers/net/wireless/airo_cs.ko: kernal/drivers/net/wireless/airo.ko kernal/drivers/net/wireless/pcmcia.ko kernal/drivers/net/wireless/pcmcia_core.ko

```

Report back your findings, and I'll see if I can steal the original hardware setup back from my next door neighbour ...

:popcorn:

---

### Post by ArconsII on 2010-09-08
I followed  your directions. I can scan for networks, but can't connect to any (even unencrypted.) nm-applet has all the wpa encrypted networks greyed out for some reason as well.

I'm using Linux Mint 9, which might make a difference....

Thanks for posting this guide!

---

### Post by fmjrey on 2010-09-09
tenwiseman: thanks for helping.
I've checked as you said and everything seems fine.
However even after reverting to the original airo.ko and airo_cs.ko files, I still get these kernel messages about unknown symbols. See attached files produced after reverting to original .ko files.
So I'm not sure this is related to your hack.
If anyone want to try this hack, please check dmesg output before touching your system and see if you can see the same unknown symbol messages.

---

### Post by Renegade Slim on 2010-09-09
I'm such a newb.  I put all four files in a freshly made folder, either edited or left unedited, entered "make all" into the terminal and got a whole lot of errors about the airo.c file.  It also makes a built-in.o instead of the two .ko files.  Am I supposed to enter anything other than "make all" into the terminal? 

I just started using linux a few days ago and I'm madly in love with everything about it, the terminal, the customization, the speed - I just can't get WPA to work. :-k.

I'm running Ubuntu 8.10 (OpenGEU) kernal 2.6.27-17, if it matters.

I have a Ubuntu 10.4 disk sitting around so I'll try compiling from there but I Really Really want O:GEU's Enlightenment. :-({|=

---

### Post by Renegade Slim on 2010-09-09
Installed the new Ubuntu and tried it out.  Connected to WPA protected wireless.  One note, for anyone trying this, tenwiseman's

> **install airo /sbin/modprobe &#8211;ignore-install airo wpa_enabled=1**should be [B]install airo /sbin/modprobe --ignore-install airo wpa_enabled=1

[/B]There has to be double hyphens in front of ignore-install or this fix won't work.

Anyways, know a way to get this working on an older Ubuntu?

Edit: Forget it, Lucid is faster by far than Intreped.  I guess substituting that newer airo.c file for one of the older ones and including the patch mentioned would have done the trick, but why bother.

Tenwiseman, you totally just saved a new linux convert from burning all of his Live CDs and just dualbooting XP service pack 2 with service pack 3.  Thanks! \\:D/

PS.  This worked for my obscure aironet card with a hardware id ending with a504.  It's listed as a generic Cisco Aironet card with no real identification number ala Ten's Aironet 350.

---

### Post by jacksonpollack on 2011-03-10
No one's probably going to read this now, but...

I have an Aironet card and I can't connected to WPA encrypted networks on a Thinkpad T40. 

Like Renegade Slim I get a ton of errors when I try to compile the 4 downloaded files... How can I solve that problem?

---

