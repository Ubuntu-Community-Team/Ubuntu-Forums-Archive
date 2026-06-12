---
title: "Mythbuntu Control Centre Problems In Hardy? Complain here!"
date: 2008-07-25
forum: Mythbuntu
---

### Post by laga on 2008-07-25
Hello,

we'll be doing another Stable Release Update (SRU) for the mythbuntu-control-centre package to fix some outstanding issues shortly.

To do this efficiently, we need *you* to tell us what problems you're having with the Control Centre.

I've already fixed two outstanding bugs.

[LIST]
[*] "optimize database" button not working [(#224780)](https://bugs.launchpad.net/ubuntu/+source/mythbuntu-control-centre/+bug/224780)
[*] can't disable automatic login [(#233904)](https://bugs.launchpad.net/ubuntu/+source/mythbuntu-control-centre/+bug/233904)
[/LIST]

These fixes will be included in the SRU.

If you know about any other issues, please post them in this thread or, preferably, in the [bug tracker](https://bugs.launchpad.net/ubuntu/+source/mythbuntu-control-centre).

The second bug has been present since Mythbuntu 7.10, but nobody bothered to report it until 8.04 (or it escaped our attention before). I hope this doesn't happen again :)

**Please note:** We can only add bug fixes to Stable Release Updates. If you would like to request a new feature, please file a wishlist bug in the [bug tracker](https://bugs.launchpad.net/ubuntu/+source/mythbuntu-control-centre) and we'll look into adding it to the next Mythbuntu release.

Regards,

Michael

---

### Post by laga on 2008-07-26
*bump*

---

### Post by axelsvag on 2008-07-26
Sounds good but MCC works fine for me. The suggested update seemed relevant. Maybe a choice where you could choose your htpc chassi and all relevant software to make it work. For example the antec fusion v1 or antec fusion 430 etc. That could be nice to have remote, lcd and other things configured automatically. Maybe an advantage ove the microsoft maffia.

---

### Post by anonymousdog on 2008-07-26
The only problems I've run into with MCC have to do with Diskless Client support.  I'm attaching my QAD notes that outline what I had to do to get image creation and network services working (with as much work as possible done with MCC -- avoiding shell operations if possible).  The notes are based on my first attempt to get PXE boot going for Mythbuntu; so, I haven't gone back over the process to confirm my notes: There may be some errors or omissions.

Most of these issues are covered in the beta testing thread.  It'd be sweet if they were all addressed in the next commit because the system is awesome!  I'm writing this from a diskless client right now :biggrin: (I wish the wife were more impressed :rolleyes:)

First off, let me say that the developers have done an **astounding** job of making this very complex configuration task accessible to the average user (well, maybe power user...PXE/Etherboot is an under-utilized, seldom understood technology) and as a part of the pre-existing, very user-friendly, primary GUI tool for administering the distribution.  That's quite an accomplishment!

Very minor gripe: It would be more intuitive if the "Terminal" button (in the MCC Diskless Client "tab") launched a chrooted shell logged in with the credentials of the image's intended autologin user (rather than root).  It's trivial to su to another user for ops that don't require root access, but it's not immediately obvious that doing so might be a good idea for normal file edits and such.  If the operator is used to doing xterm ops in Ubuntu/Mythbuntu, (s)he is used to using sudo for root ops anyway; so, it would more closely emulate the host environment.  I'd have to test again, but I think MCC operations on the image also change touched files' ownerships to root:root too.

[notes]
Diskless Client support config on Mythbuntu 8.04.1

Prerequisites:

Backend (and image-hosting) Server(s) on static IP.

MythTV setup for network access (including pointing to a non-loopback address in backend setup).

Update the server with synaptic.

Then, still in synaptic, force version on mythbuntu-control-centre to the ~hardy2 fixes release; it will report this as a downgrade, but it clearly is not.  It has some needed fixes without which it won't install unsigned packages, and the client image will not be completed.  (If you run the MCC to make the image, it should take a "long time" in the 10-20 minute range to DL all the packages, construct the image, and compress it (YMMV).  If it's shorter, it probably didn't work.  The ~hardy2 version should produce an error message on error (the "standard" version doesn't).
	A good way to test successfull image completion is to mount the image in the diskless server's MCC and try to run the MCC chrooted in the image (all in the server's MCC GUI).  If it runs, that's a good sign.

We need to setup (what looks like a process involved in NFS) nbd-server, called Disk server in the Services Settings GUI, a service for the Linux Network Block Device client, to serve local files as block devices to network clients. I think it gets installed with NFS or the initial diskless client role setup, but it doesn't get configured with that or with the script that sets up the tftp server and other inetd services.
	It requires a default config file that we generate with 'sudo dpkg-reconfigure nbd-server'.  Answer the questions in the ncurses interface: probably one server on port 2000 exporting /opt/ltsp/images/i386.img (or <otherarchitecture>.img).  The resulting /etc/nbd-server/config file should end up something like:```

[generic]
# If you want to run everything as root rather than the nbd user, you
# may either say "root" in the two following lines, or remove them
# altogether. Do not remove the [generic] section, however.
	user = nbd
	group = nbd

# What follows are export definitions. You may create as much of them as
# you want, but the section header has to be unique.
[export]
	exportname = /opt/ltsp/images/i386.img
	port = 2000

```

It looks like the tftpd service gets setup properly during the upgrade role/create image process somewhere.  I only had to restart the openbsd-inetd service before PXE would load an image from tftpd.

The same is not true of the DHCP server.  dhcp3-server's default config file is unsuitable for this application.  Make the /etc/ltsp directory and move the sample dhcpd.conf file from /usr/share/doc/ltsp-server/examples/dhcpd.conf to /etc/ltsp/dhcpd.conf and edit the subnet config for your network.  The bootp stuff will just work, and dhcpd knows to use this config file instead of /etc/dhcpd.conf. Start the dhcp server (after taking down other(s) on the lan).


Setup the Server in MCC to Boot Diskless Clients:

So, enable the "Diskless Server" and "Add DHCP server" roles in the MCC, endure the package changes and return to the MCC. Click the new "Diskless Server" shortcut in the MCC sidebar to do the Server Preparation.  Select CPU architecture of your clients, probably i386.  Check "Allow unsigned packages" (this is the bit that doesn't work in the standard MCC), and click "Build Image".  Then click Apply (and choose Apply? or whatever the second ack is).  Endure the very long image creation process that includes lots of apt-get package retrieval and installation into the image (as well as squashfs creation, and lots of other heavy lifting we can thank the developers for automating for us).

Make as many changes to the image as possible (so they aren't made from the diskless client) via the server's MCC interface to the image's MCC (or an xterm chrooted on the image).  Do apt-get updates and upgrades here, not on the client (with the exception of hardware peculiars, e.g., nvidia binary drivers).  Definitely redo the MythTV configuration in the chrooted MCC as it had a loopback IP in the setup (even though the backend had already been setup with non-loopback address and other networked frontends had accessed it).  Also use a chrooted terminal to edit the /etc/lts.conf file to include ```
[defaults]
``` as the first uncommented line.

It also seems that "commit changes"'s shell never closes (is this due to the --hold command line option?); once it gets to "nothing to do" (or something similar), "x" it out.  You have to run this command every time you update or change the base image's packages or kernel for sure (not certain about other ops [i.e., MMC or terminal chrooted on image]).

Each machine maintains its changes from the image in an ltsp cache (on the diskless client server) at /var/cache/mythbuntu-diskless/overlay/MACADDRESS/.  There is very real potential for apt-get to get hosed up pretty bad if you were to run it routinely from the diskless client side.  It's MUCH, MUCH better to run it from the MCC via the image's terminal (a chroot environment shell rooted in the tftp image).  Only install drivers and such (unique to a machine) from the diskless client side.  You can delete the overlay files in the cache directory MACADDRESS subdirectory) to put a diskless client back to standard configuration.
[/notes]

---

### Post by laga on 2008-07-27
> **anonymousdog said:**
> I'm attaching my QAD notes that outline what I had to do to get image creation and network services working (with as much work as possible done with MCC -- avoiding shell operations if possible).


Thanks, that's exactly what I've been looking for!

> 
Very minor gripe: It would be more intuitive if the "Terminal" button (in the MCC Diskless Client "tab") launched a chrooted shell logged in with the credentials of the image's intended autologin user (rather than root).


That's a good idea. It'd be safe to assume that the user with UID 1000 is the correct user since that's the first 'real' user added to the system (when the image is created).

> 
I'd have to test again, but I think MCC operations on the image also change touched files' ownerships to root:root too.


I'm not sure what you mean - are you talking about file permissions on /opt/ltsp/images/i386.img?


> 
Then, still in synaptic, force version on mythbuntu-control-centre to the ~hardy2 fixes release; it will report this as a downgrade, but it clearly is not. 


This will be fixed soon. ~hardy2 was in the Ubuntu archives, but the Mythbuntu disks were built from a PPA which was holding older code with a newer version number. D'oh!

> 
We need to setup (what looks like a process involved in NFS) nbd-server,


That's interesting. NBD should have been set up by ltsp-update-image in /etc/inetd.conf. Here's an entry from my inetd.conf:

```

2000    stream  tcp nowait  nobody /usr/sbin/tcpd /usr/sbin/nbdrootd /opt/ltsp/images/i386.img

```

Do you have that line? With that configuration, it's not necessary to create a configuration file anymore.

> 
I think it gets installed with NFS or the initial diskless client role setup


It's pulled in by ltsp-server (which is pulled in by mythbuntu-diskless-server). 


> 
It requires a default config file that we generate with 'sudo dpkg-reconfigure nbd-server'.  


In inetd.conf, nbdrootd is used which is a wrapper around nbd-server: ```

/bin/nbd-server 0 $1 -r -C /dev/null > /dev/null 2>&1
```

As you can see, it points the config file to /dev/null. So we need to work out what went wrong with ltsp-update-image or inetd for you :)

> 
I only had to restart the openbsd-inetd service before PXE would load an image from tftpd.


That's interesting as well. I'll tray to reproduce this behavior.


> 
The same is not true of the DHCP server.  dhcp3-server's default config file is unsuitable for this application.

That's true. However, if you click the "Add DHCP server" checkbox in the "System roles" tab, it should give you a good config. I wonder why it didn't work for you?


> 
as well as squashfs creation, and lots of other heavy lifting we can thank the developers for automating for us.


I guess this is a good time to mention that mythbuntu-diskless is built on top of LTSP :) It's basically just a plugin to ltsp-build-client which installs the necessary packages and does some customization.

> 
Make as many changes to the image as possible (so they aren't made from the diskless client) via the server's MCC interface to the image's MCC (or an xterm chrooted on the image).  Do apt-get updates and upgrades here, not on the client (with the exception of hardware peculiars, e.g., nvidia binary drivers). 


Right :)

> 
Definitely redo the MythTV configuration in the chrooted MCC as it had a loopback IP in the setup

That's odd! 

> 
Also use a chrooted terminal to edit the /etc/lts.conf file to include ```
[defaults]
``` as the first uncommented line.

True. That's a problem in the ltsp-build-client plugin and will be fixed in a separate SRU.

> 
It also seems that "commit changes"'s shell never closes (is this due to the --hold command line option?); once it gets to "nothing to do" (or something similar), "x" it out.


That's intentional (but everybody is criticising me for that decision ;)) I wanted the window to stay open so that users can inspect the output if errors happen. I could add a message saying "You may now close this window". Do you have any better ideas?

> 
You have to run this command every time you update or change the base image's packages or kernel for sure (not certain about other ops [i.e., MMC or terminal chrooted on image]).

You need to "commit changes" every time you make a change to the chroot and want them to show up on your client. (Of course, changes might be masked by the client's overlay directory, but that's a corner case ;))

> 
Each machine maintains its changes from the image in an ltsp cache (on the diskless client server) at /var/cache/mythbuntu-diskless/overlay/MACADDRESS/.  There is very real potential for apt-get to get hosed up pretty bad if you were to run it routinely from the diskless client side.


Yes, that's probably the biggest downside.


Thanks for your notes - you did a pretty good job at summarizing the whole thing. Would you like to contribute a thing or two to the diskless documentation? That'd also motivate me to commit my changes to the documentation tree ;) In any case, your notes would make a good addition to the wiki.



You had to do quite a few things manually, so I'm wondering if the NFS setup work out of the box. Did you have to edit /etc/exports?

---

### Post by laga on 2008-07-27
> **laga said:**
> 
That's true. However, if you click the "Add DHCP server" checkbox in the "System roles" tab, it should give you a good config. I wonder why it didn't work for you?


It doesn't work because it's a bug. Oops. I'll fix it..

---

### Post by mrand on 2008-07-28
> **laga said:**
> Hello,

we'll be doing another Stable Release Update (SRU) for the mythbuntu-control-centre package to fix some outstanding issues shortly.

To do this efficiently, we need *you* to tell us what problems you're having with the Control Centre.

I've already fixed two outstanding bugs.

[LIST]
[*] "optimize database" button not working [(#224780)](https://bugs.launchpad.net/ubuntu/+source/mythbuntu-control-centre/+bug/224780)
[*] can't disable automatic login [(#233904)](https://bugs.launchpad.net/ubuntu/+source/mythbuntu-control-centre/+bug/233904)
[/LIST]

These fixes will be included in the SRU.

If you know about any other issues, please post them in this thread or, preferably, in the [bug tracker](https://bugs.launchpad.net/ubuntu/+source/mythbuntu-control-centre).

The second bug has been present since Mythbuntu 7.10, but nobody bothered to report it until 8.04 (or it escaped our attention before). I hope this doesn't happen again :)

**Please note:** We can only add bug fixes to Stable Release Updates. If you would like to request a new feature, please file a wishlist bug in the [bug tracker](https://bugs.launchpad.net/ubuntu/+source/mythbuntu-control-centre) and we'll look into adding it to the next Mythbuntu release.

Regards,

MichaelHowdy Michael,

I assume you've already looked over the bugs in launchpad?  I guess [Bug #231281]("https://bugs.launchpad.net/mythbuntu/+bug/231281") might be a cross between a bug and a feature enhancement - depends on what was originally intended.  Hmm... I just noticed that I filed it under mythbuntu rather than mythbuntu-control-centre.  Shall I change the project?  I suspect this is a VERY common mistake.  Looking closer, I see they seem to be different kinds... mythbuntu looks to be project level, while mythbuntu-control-centre is source level?  Does that matter?

I just added another minor-ish theme related bug that I forgot to report a few weeks ago: [Bug #252628]("https://bugs.launchpad.net/ubuntu/+source/mythbuntu-control-centre/+bug/252628") If you need help testing or reproducing, let me know.

Thanks for your hard work on mythbuntu.  While I could setup mythtv without mythbuntu, I don't have a lot of spare time and would prefer to not have to deal with every little thing right now.

[INDENT]Marc[/INDENT]

---

### Post by laga on 2008-07-28
> **mrand said:**
> I guess [Bug #231281]("https://bugs.launchpad.net/mythbuntu/+bug/231281") might be a cross between a bug and a feature enhancement - depends on what was originally intended.  Hmm... I just noticed that I filed it under mythbuntu rather than mythbuntu-control-centre.  Shall I change the project?  I suspect this is a VERY common mistake.  Looking closer, I see they seem to be different kinds... mythbuntu looks to be project level, while mythbuntu-control-centre is source level?  Does that matter?


Oops, I missed that one - probably because I tend to ignore everything involving "lirc" ;) yeah, "mythbuntu" is the project. If you want to file a bug against the source package, click on "also affects distribution", choose Ubuntu and enter the package name.

> 
I just added another minor-ish theme related bug that I forgot to report a few weeks ago: [Bug #252628]("https://bugs.launchpad.net/ubuntu/+source/mythbuntu-control-centre/+bug/252628") If you need help testing or reproducing, let me know.


Foxbuntu is already looking into that one. Yay :)


These will most likely be fixed in intrepid then - I'm not sure if I want to do *another* SRU since these are quite annoying ;)

Thank you for your kind words,

-- Michael

---

### Post by mrand on 2008-07-28
> **laga said:**
> Oops, I missed that one - probably because I tend to ignore everything involving "lirc" ;) yeah, "mythbuntu" is the project. If you want to file a bug against the source package, click on "also affects distribution", choose Ubuntu and enter the package name.

It isn't so much about what I want... what do you guys prefer?

  Marc

---

### Post by laga on 2008-07-28
> **mrand said:**
> It isn't so much about what I want... what do you guys prefer?

  Marc


I like both - so that I can see what bugs are there in Mythbuntu and what bugs are against the source packages themselves.

---

### Post by Titus A Duxass on 2008-07-29
Hi,
My two eurocents worth:

I have many problems with nvidia setup, I connect my 32" LCD Tv via DVI/HDMI and the xserver keeps resetting itself on boot.

It also resets my keyboard to US (I need De).

The Remote control area appears to be a nonstarter no matter which Hauppauge remote I select.

Other than the above I have no major problems.

---

### Post by Chuckels550 on 2008-07-31
Be nice if the Remote Control screen worked, though I suspect that my efforts trying to fix it on my machine has totally buggered it and my LIRC set-up.  My LIRC remote hasn't worked since the upgrade to 8.04.  I use the Hauppauge TV card.

Be nice if the spelling of 'Advanced Mangement' was finally fixed.

Be nice if the switch back from one of the Advanced Mangement tools to the MCC worked the first time instead of the second or third time.  I discovered that when it didn't work that I could just press enter and the tool I closed would be launched again.  Then I could close it - a few times of this and the MCC would finally appear.

---

### Post by anonymousdog on 2008-08-01
Sorry about the delay in replying...actual work preempting my fun :(

> **laga said:**
> That's a good idea. It'd be safe to assume that the user with UID 1000 is the correct user since that's the first 'real' user added to the system (when the image is created).
That makes perfect sense as a default; maybe a MOTD that explains other su/sudo options in case 1000 isn't the needed UID (to handle corner cases).

> **laga said:**
> I'm not sure what you mean - are you talking about file permissions on /opt/ltsp/images/i386.img?
Yes...permissions in the unsquashed file system that end up in the img file.

> **laga said:**
> This will be fixed soon. ~hardy2 was in the Ubuntu archives, but the Mythbuntu disks were built from a PPA which was holding older code with a newer version number. D'oh!
It looked like a repo problem, but, being a Red Hat man, I haven't used apt-get in a few years and forgot how to quickly check out the "why".

> **laga said:**
> That's interesting. NBD should have been set up by ltsp-update-image in /etc/inetd.conf. Here's an entry from my inetd.conf:

```

2000    stream  tcp nowait  nobody /usr/sbin/tcpd /usr/sbin/nbdrootd /opt/ltsp/images/i386.img

```

Do you have that line? With that configuration, it's not necessary to create a configuration file anymore.
Yes, that (IIRC) was there; I created the config file because I expected to see it there.  Maybe the wiki doc could mention this specifically.

> **laga said:**
> In inetd.conf, nbdrootd is used which is a wrapper around nbd-server: ```

/bin/nbd-server 0 $1 -r -C /dev/null > /dev/null 2>&1
```

As you can see, it points the config file to /dev/null. So we need to work out what went wrong with ltsp-update-image or inetd for you :)
I have no such entry in /etc/inetd.conf.  I have:```
tftp           dgram   udp     wait    root  /usr/sbin/in.tftpd /usr/sbin/in.tftpd -s /var/lib/tftpboot
9571           stream  tcp     nowait  nobody /usr/sbin/tcpd /usr/sbin/ldminfod
9572			stream  tcp 	nowait 	nobody /usr/sbin/tcpd /usr/sbin/nbdswapd
2000               stream  tcp            nowait  nobody /usr/sbin/tcpd /usr/sbin/nbdrootd /opt/ltsp/images/i386.img
```

> **laga said:**
> That's interesting as well. I'll tray to reproduce this behavior.
It may have been the dhcpd server not configured correctly at the time.  I fixed the config on that restarted inetd in the same PXE boot attempt-diagnosis-intervention cycle: I wouldn't do that at work, but it's a hobby project, so I'll take shortcuts.  Again, this may be an error/omission of the type I suspected might be present.

> **laga said:**
> I guess this is a good time to mention that mythbuntu-diskless is built on top of LTSP :) It's basically just a plugin to ltsp-build-client which installs the necessary packages and does some customization.
Hey, man, I don't care that you didn't have to reinvent the wheel ;).  Actually, I'm way more impressed that you didn't!...and, instead built off the work of existing projects already partially suited for the complete task.  That speaks of a prudent, experienced, humble development team.  Cudos!, regardless of how much work is "borrowed"!

> **laga said:**
> That's odd!
And only caught because I had read the beta-testers thread first.

> **laga said:**
> True. That's a problem in the ltsp-build-client plugin and will be fixed in a separate SRU.
Good. That's a drag that such a simple way of obtaining expected behavior isn't the default.

> **laga said:**
> That's intentional (but everybody is criticising me for that decision ;)) I wanted the window to stay open so that users can inspect the output if errors happen. I could add a message saying "You may now close this window". Do you have any better ideas?
I'd have to be a real Mythbuntu guru to classify any of *my* ideas as "better".  It did have me wondering what was going on though (mostly since the process is so lengthy that it's hard to tell when it's over).  The ideal solution (for my money) would be to redirect output to a log file and use error handling in the script to prompt the user to view the log file (or save it to a more familiar location) only if there is an error.  Otherwise, the script could just exit 0.

> **laga said:**
> Thanks for your notes - you did a pretty good job at summarizing the whole thing. Would you like to contribute a thing or two to the diskless documentation? That'd also motivate me to commit my changes to the documentation tree ;) In any case, your notes would make a good addition to the wiki.
Again, these were my "quick 'n dirty" notes to walk me back through redoing the process and confirming results.  Maybe we could just link to that entry from the wiki until the results are more confirmed?  I'm happy to contribute, but results might be slow due to my working 60+ hour weeks lately.

What's my next, best task for contributing?

> **laga said:**
> You had to do quite a few things manually, so I'm wondering if the NFS setup work out of the box. Did you have to edit /etc/exports?That file looks familiar, but I don't think I had to edit it.  I'm betting that, when I go back over this, I'll find that all is set up fine but for the [defaults] entry in lts.conf (on the image) and that the ltsp setup doesn't create the /etc/ltsp/dhcpd.conf file.  Both of those seem like straight forward fixes, and would take diskless-client-support setup from "fiddly" to "dead simple".

---

### Post by Dilligaf on 2008-08-04
I don't know if this is the right place. Videos will not play from Mythweb. Recorded TV plays fine, DVD rips come up with the error "The requested URL /mythweb/data/video//mnt/server_E/25TH_HOUR was not found on this server."

Mike

---

### Post by laga on 2008-08-04
> **Dilligaf said:**
> I don't know if this is the right place. Videos will not play from Mythweb. Recorded TV plays fine, DVD rips come up with the error "The requested URL /mythweb/data/video//mnt/server_E/25TH_HOUR was not found on this server."

Mike

Filing a bug report against MythWeb would be better:

[http://bugs.launchpad.net/ubuntu/+source/mythplugins/](http://bugs.launchpad.net/ubuntu/+source/mythplugins/)

---

### Post by anonymousdog on 2008-08-05
laga,

What's my next, best step toward contributing (with an eye toward that documentation)?

A

---

### Post by Dilligaf on 2008-08-05
Done: [https://bugs.launchpad.net/ubuntu/+source/mythplugins/+bug/255116](https://bugs.launchpad.net/ubuntu/+source/mythplugins/+bug/255116)

Mike

---

### Post by laga on 2008-08-06
> **anonymousdog said:**
> laga,

What's my next, best step toward contributing (with an eye toward that documentation)?

A


I've outlined a few points here:

[http://wiki.mythbuntu.org/mythbuntu/contributing/documentation](http://wiki.mythbuntu.org/mythbuntu/contributing/documentation)

Dilligaf: Thanks for creating that bug report!

---

