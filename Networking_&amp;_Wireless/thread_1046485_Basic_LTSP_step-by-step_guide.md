---
title: "Basic LTSP step-by-step guide"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by djsephiroth on 2009-01-21
After weeks of searching - Google, these forums, the Edubuntu site, etc. - I have found nothing but bits and pieces of the information I need to set up an Edubuntu thin client lab. Are there any guides that cover every essential step? If not, and if there is someone out there with the knowledge and kindness to clear things up for me before I give up on the FOSS option and recommend the alternative MS solution to my superiors, such efforts will be most appreciated.

First, my network, insofar as it concerns the LTSP lab: a Cisco 2811 router connects to a Cisco CE500 switch connects to my server connects to a cheap Dell switch connects to all the clients (right now there is just one client for testing). There are two NICs in the server: the onboard Realtek and a Linksys 10/100 PCI card. The Realtek is the external connection. The Linksys connects to the Dell switch which then connects to the clients.

I am using 8.10 alternate i386. I hit f4 and then press "Enter" to install the OS on the server. Unlike what I see in the Edubuntu LTSP guide, nothing pops up during the install to ask me which NIC will be the inside (read: connect to the clients) and which one will connect to the outside (read: connect to the internet and our organization's network at large). Install completes, I make a user, I log in, I apply updates via the update manager.

I connect a client to the switch and tell it to boot using PXE. The client sits at "DHCP..." for a good 10-15 seconds, then gives up and boots to its own HDD.

OK, I must have forgotten this: sudo ltsp-update-sshkeys.
No, maybe I forgot to set my internal NIC to a private address (192.168.0.1 in this case).
Nope, I did all that. Nothing. The external NIC gets a DHCP address. The internal NIC is set to 192.168.0.1/24.

So, there you have the current situation. Here are the questions I need answered, assuming there is no clear, complete, and correct guide out there that already answers them:

What are all (every single one, no matter how trivial or purportedly obvious) of the commands necessary to configure the server to accept a connection when the client requests one?

What are all (every single one, no matter how trivial or purportedly obvious) of the commands necessary to install, configure, and start each of the services necessary for LTSP to be up and running and ready for incoming client connections?

Assuming that there is nothing exotic or complicated about my setup (e.g., that I have a server with 2 NICs serving a few clients through a switch 'tween the server and clients), what do I need to do to get Edubuntu on the server and boot clients into a desktop environment? Please be as verbose as possible. Please answer not according to the info given above about my actual system, but about the theoretical setup mentioned at the start of this paragraph.

Answers along the lines of "set up your firewall to accept incoming connections" or "turn on ssh" will not be appreciated. I need a cookbook. I need commands. I will not be offended if you instruct me as one might a ten-year-old. It's actually how I learn best. Answers along the lines of "type 'sudo chroot', then hit enter, then type in your MAC address at this exact location in this specific file, exactly in this order, then reboot; this will cause NumLock to flicker three times" will be greatly appreciated.

Thanks!

Edit: OK, so fixed some things and got the client to boot. Yay! Problem is, it boots to a shell that looks like this: initramfs>, as opposed to a functional desktop environment. Do I just need to chroot into the thin client chroot and install the desktop environment and other software there? What commands and procedure would I use to set that up?

But hey, at least it booted right? One would think so. But no, check this out: after booting once, it does not boot again. The error message is something like this:

<Will try it again and make a note of it later as time permits. Currently it throws some error about not taking or being given control, then something about "nbd" or whatnot.>

I am using a fresh Edubuntu install: f4, install, select eth0 as main interface, stop dhcp attempt, type in manual IP info for eth0, install just about everything from the addon CD, install all updates (all 275 of them... wow). Rebooted after addon CD install and again after the updating process. Still using the same topology.

Also, how do I tell the server explicitly to use eth0 to connect to the internet and eth1 to connect to the clients? It seems to use the wrong NIC to connect to the internet at present.

Edit #2: OK, here's the error thrown by the client:

Starting LTSP service...

nbd0: Receive control failed (-32)

Edit #3:

This seems to cover some of the issues: [http://ubuntuforums.org/showthread.php?t=686966&highlight=ltsp+nbd0](http://ubuntuforums.org/showthread.php?t=686966&highlight=ltsp+nbd0)

I went into my /etc/network and edited the interfaces file to assign the static IP addresses I wanted on the server. 10.10.10.1 is the internal interface on the LTSP network 10.10.10.0/24. 172.16.9.250 is the external interface that connects to the internet (not directly, but through a series of routers, L2 switches, L3 switches, a VPN tunnel, etc.) and resides on subnet 172.16.9.0/24. I commented out the dns-search or whatnot. I added dns-nameserver or whatnot to be 172.16.5.2, which is our internal DNS server that forwards requests to OpenDNS, or to our provider's DNS if OpenDNS fails (ha!).

Would I be correct in assuming that the error about nbd0 has something to do with the thin client not being able to connect to the network storage on the server?

---

### Post by djsephiroth on 2009-02-01
Figured it out on my own, with a bit of help from the Debian documentation and the LTSP site. This is mostly correct, but doesn't cover everything, plus it is slightly outdated: [http://jviz.research.iat.sfu.ca/wiki/index.php?title=LTSP](http://jviz.research.iat.sfu.ca/wiki/index.php?title=LTSP)

---

### Post by haddog on 2009-02-15
Ubuntu 8.04.2 Hardy LTS works "out of the box." Use the Alternate CD iso.

[https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)

It has LTSP server included in the image. Didn't have to config anything.

---

### Post by djsephiroth on 2009-02-19
> **haddog said:**
> Ubuntu 8.04.2 Hardy LTS works "out of the box." Use the Alternate CD iso.
By this do you mean "I have used it" or "it should work as described"?
> 
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)

Read it twice before I even started. It's a really watered-down version of the LTSP5 upstream documentation. Useless.
> 
It has LTSP server included in the image. Didn't have to config anything.
It does have the option to install an LTSP server; however, as noted in the OP, it did not automagically work. 

That said, I figured I should post how I got it working (this explanation does not go into detail because I am very lazy):

I installed a copy of 8.10 x86 using the alternate install CD. I selected the "Install Ubuntu" option to install a vanilla desktop setup. I used autoconfig for the network portion of setup since I knew one eth had to be DHCP, and I was going to mess with the settings anyway post-install. I then went into the Network Configuration and set up two network cards: the internal one (eth1) gets its address and other network info via DHCP; I gave the Linksys (going to the clients' switch) the typical 192.168.0.1/24 (read: IP address 192.168.0.1, subnet 255.255.255.0) address. I then edited dhcpd.conf to serve DHCP from the Linksys (eth0) by using "sudo gedit /etc/ltsp/dhcpd.conf", and (re)started the dhcp server: "sudo invoke-rc.d dhcp3-server (re)start" (can't remember if it was running from the get-go, but I don't think so). I updated the install using the handy auto-update GUI program. I then installed the ltsp package via Synaptic; you could also use "sudo apt-get install ltsp-server-standalone openssh-server" to get the same result. I also installed all the recommended/suggested packages (by "suggested" I guess they meant "needed", since they include things like, oh, pulseaudio for getting sound up and running on the thin clients XD). Restarted. I then used "sudo ltsp-build-client" to create the thin client chroot. I used "sudo chroot /opt/ltsp/i386" to chroot into the ltsp folder, mounted proc using "mount /proc -t proc proc" updated the ltsp chroot with "apt-get update" and then "apt-get upgrade", then exited the chroot using "exit". I then used "sudo ltsp-update-sshkeys" followed by "sudo ltsp-update-kernels" and finally "sudo ltsp-update-image". Works like a charm now.

---

### Post by haddog on 2009-02-20
Good writeup dj. Yes I have used it and am currently replying to this thread from a thin client on the LTSP server. You are correct in that the writeup is thin. I see why you had problems with the LTSP server install. You used ubuntu 8.10. I had problems with 8.10 and trying to do the LTSP server install. The option to install the LTSP server doesn't work on 8.10. 

As my post says "Ubuntu 8.04.2 Hardy LTS works out of the box." After booting from the 8.04.2 alternate cd, I hit F4 and selected "install an LTSP server" as per the instructions. The thin client image was automatically built during the end of the install.

I now remember I did have to edit /etc/network/interfaces. eht1 was not enabled to use a static ip's so the thin clients couldn't connect to the server. I then restarted the dhcp server and all was good. I then went on to apply all updates, installed flash and java.

Regarding sound on the thin clients, it worked 'out of the box' but embedded video audio, such as youtube videos, did not. The simplest way to fix this issue for me was to install the libflashsupport package on the LTSP server:

sudo apt-get install libflashsupport

So while not totally out of the box functionality, I had much less configuration and installation of the LTSP server software to do than you did. Once again. Anyone wanting a quick setup of an Ubuntu LTSP server, I recommend using Ubuntu 8.04.2 over 8.10, at least until the LTSP server install issues are resolved.

---

### Post by djsephiroth on 2009-02-20
> **haddog said:**
> 
So while not totally out of the box functionality, I had much less configuration and installation of the LTSP server software to do than you did. Once again. Anyone wanting a quick setup of an Ubuntu LTSP server, I recommend using Ubuntu 8.04.2 over 8.10, at least until the LTSP server install issues are resolved.
Noted. I plan on using 8.04 on the production rollout, and then Jaunty when it's proven stable. Just goes to show the difference between LTS and non-LTS. I'm glad I figured out how to do it all manually, though. I feel a bit safer in the end.

---

### Post by haddog on 2009-02-20
> **djsephiroth said:**
> Noted. I plan on using 8.04 on the production rollout, and then Jaunty when it's proven stable. Just goes to show the difference between LTS and non-LTS. I'm glad I figured out how to do it all manually, though. I feel a bit safer in the end.

Yep. Definately some differences. I am going to try setting up an LTSP server on 8.10 using your instructions. Thanks! And yes. I do have a good backup image of 8.04.2. G4L works great for backups. And it's open source.

---

### Post by dipeshmehta on 2009-03-07
> **djsephiroth said:**
> 
Edit: OK, so fixed some things and got the client to boot. Yay! Problem is, it boots to a shell that looks like this: initramfs>, as opposed to a functional desktop environment. Do I just need to chroot into the thin client chroot and install the desktop environment and other software there? What commands and procedure would I use to set that up?

Hello,

I have setup LTSP on my running Ubuntu 8.04 Server. I followed steps as per [https://help.ubuntu.com/community/ThinClientHowto](https://help.ubuntu.com/community/ThinClientHowto) 

My problem is similar.  At PXE Boot Client, I get stuck at shell like initramfs>.

Can you (djsephiroth) or anybody please help me what next steps to follow getting out of this.

Dipesh

Edit:  read somewhere in other thread, so I re-booted the server, and then I am getting ldm login screen. BUT I am not able to login at PXE client.  The guide says any user who can login remotely via SSH, can login into LTSP server, but I am not able.

I have tried to again updating ssh-keys, and image but no result.

Dipesh

---

### Post by acesabe on 2009-03-12
Your experiences pretty much mirror mine, although I did get a client booting LTSP system from the 8.10 alternate server install disk (had to manually configure network), there is obviously a lot of work unfinished. The documentation is essentially useless as it appears to be a random mix of ltsp 4.x and 5 documentations, which are markedly different and conflicting. There is some gap between the quick install details and further configuration docus, notably any further config changes to the default ltsp setup do nothing! Customizing client configs using the new location of lts.conf (no longer in /opt/ltsp/i386/etc/) has no effect (supposed to be immediate), can't even see any sign of ldm running anywhere...
Pluggable media does work - but appears on all clients simultaneously, unmounting fails though due to permissions...Sound working out the box is a plus. Reporting 'bugs' get a pretty short responses, so seems pointless....

---

### Post by dipeshmehta on 2009-03-15
Some Progress!!  At PXE client, I am able to LDM login screen, when I issue username/passwd, it gets authenticated (I checked the auth.log) but then the login screen re-appears... there is error message like "unable to start X session --- no "/home/user1/.xsession"" in user's home folder, can any body shed some light please?

Dipesh

---

### Post by djsephiroth on 2009-08-04
dipeshmehta,

Can you let us know how you got from the blank screen to the ldm? I'm trying to set this sort of thing up again, only using 8.04 AMD64 instead of 8.04 i386, and I keep getting this issue. Many thanks!

---

### Post by venkatmangudi on 2009-10-01
> **dipeshmehta said:**
> Some Progress!!  At PXE client, I am able to LDM login screen, when I issue username/passwd, it gets authenticated (I checked the auth.log) but then the login screen re-appears... there is error message like "unable to start X session --- no "/home/user1/.xsession"" in user's home folder, can any body shed some light please?

Dipesh

Dipesh,

I believe that you have to have X session running on the server to be able to serve X to the thin client. Do you have GDM or any other X running?

Hope this helps.

Cheers,
Venkat

---

### Post by Dzingis on 2009-10-06
> **venkatmangudi said:**
> Dipesh,

I believe that you have to have X session running on the server to be able to serve X to the thin client. Do you have GDM or any other X running?

Hope this helps.

Cheers,
Venkat

I'm getting same error as Dipesh, but it's not logical to have X installed on server 'cause I don't use it?

Someone with the same error with solution?

---

### Post by atkuepker on 2009-11-20
I think I'm seeing the same problem that Dipesh is seeing.

Fresh Kubuntu 9.10 install with apt-get LTSP package. Booting to login screen just fine with Diskless Workstation 1420 Terminal.

Authentication works fine based upon auth.log entries. KDE Splash screen runs partway with a couple of the devices starting to appear before the screen goes black for a couple seconds and kicks back out to the login screen.

Here's a sample of the .xsession-error output:

Xsession: X session started for desktop2test at Fri Nov 20 16:27:28 PST 2009
/etc/X11/Xsession.d/80_ltsp-sound: 7: /usr/bin/asoundconf: not found
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
startkde: Starting up...
kdeinit4: preparing to launch /usr/lib/libkdeinit4_klauncher.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kded4.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kconf_update.so
Invalid D-BUS member name 'idle-hint' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'is-local' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'x11-display-device' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'x11-display' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'display-device' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'remote-host-name' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'session-type' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
Invalid D-BUS member name 'unix-user' found in interface 'org.freedesktop.ConsoleKit.Session' while parsing introspection
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kglobalaccel.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kcminit_startup.so
kdeinit4: preparing to launch /usr/bin/knotify4
kdeinit4: preparing to launch /usr/lib/libkdeinit4_ksmserver.so
<unknown program name>(5187)/ KStartupInfo::createNewStartupId: creating:  "desktop2;1258763250;870312;5187_TIME0" : "unnamed app"
kephald starting up
XRANDR error base:  167
RRInput mask is set!!
RandRScreen::loadSettings - adding mode:  117 1280 x 1024
RandRScreen::loadSettings - adding mode:  118 1280 x 1024
RandRScreen::loadSettings - adding mode:  119 1280 x 960
RandRScreen::loadSettings - adding mode:  120 1152 x 864
RandRScreen::loadSettings - adding mode:  121 1152 x 864
RandRScreen::loadSettings - adding mode:  122 1152 x 864
RandRScreen::loadSettings - adding mode:  123 1024 x 768
RandRScreen::loadSettings - adding mode:  124 1024 x 768
RandRScreen::loadSettings - adding mode:  125 1024 x 768
RandRScreen::loadSettings - adding mode:  126 832 x 624
RandRScreen::loadSettings - adding mode:  127 800 x 600
RandRScreen::loadSettings - adding mode:  128 800 x 600
RandRScreen::loadSettings - adding mode:  129 800 x 600
RandRScreen::loadSettings - adding mode:  130 800 x 600
RandRScreen::loadSettings - adding mode:  131 640 x 480
RandRScreen::loadSettings - adding mode:  132 640 x 480
RandRScreen::loadSettings - adding mode:  133 640 x 480
RandRScreen::loadSettings - adding mode:  134 640 x 480
RandRScreen::loadSettings - adding mode:  135 720 x 400
RandRScreen::loadSettings - adding crtc:  115
RandRScreen::loadSettings - adding output:  116
Setting CRTC 115 on output "default" (previous 0 )
CRTC outputs: (116)
Output name: "default"
Output refresh rate: 60
Output rect: QRect(0,0 1280x1024)
Output rotation: 1
XRandROutputs::init
  added output  116
adding an output 0 with geom:  QRect(0,0 1280x1024)
output: "SCREEN-0" QRect(0,0 1280x1024) 0 true false
load xml
connected: 1
looking for current "SCREEN-0"
known "*" has score: 0.125
screen: 0 QRect(0,0 1280x1024)
looking for a matching configuration...
connected: 1
looking for current "SCREEN-0"
known "*" has score: 0.125
found outputs, known: false
activate external configuration!!
registered the service: true
screens registered on the bus: true
outputs registered on the bus: true
configurations registered on the bus: true
kdeinit4: Fatal IO error: client killed
kdeinit4: sending SIGHUP to children.
kwin: Fatal IO error: client killed
Qt-subapplication: Fatal IO error: client killed
kglobalaccel: Fatal IO error: client killed
kded4: Fatal IO error: client killed
klauncher: Exiting on signal 1
kdeinit4: Fatal IO error: client killed
kdeinit4: sending SIGHUP to children.
kdeinit4: sending SIGTERM to children.
kdeinit4: Exit.
Unexpected response from KInit (response = 0).
startkde: Could not start ksmserver. Check your installation.
Error: Can't open display: localhost:11.0
Could not connect to D-Bus server: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-DLODmmRJba: Connection refused
startkde: Shutting down...
kdeinit4_wrapper: Warning: connect(/home/desktop2test/.kde/socket-desktop2/kdeinit4_localhost_11) failed: : No such file or directory
Error: Can not contact kdeinit4!
startkde: Running shutdown scripts...
xprop:  unable to open display 'localhost:11.0'
xprop:  unable to open display 'localhost:11.0'
startkde: Done.
kdeinit4: sending SIGTERM to children.
kdeinit4: Exit.

---

### Post by haddog on 2010-04-02
This thread seems to have died. My Ubuntu 8.04.2 LTSP server is still crankin along. Have thought about upgrading when Lucid is out of beta, but not before doing a full backup using cloezilla of course ;) I believe in if it ain't broke, it ain't broke!

---

### Post by nolo on 2010-05-07
haddog,

When you get your Lucid Thin server up and running, please post an update here.  I'd like to see how it went for you.  Like you, I'm running LTSP on 8.04 LTS.  I did a fresh Lucid LTSP install on a fresh machine.  The install went well, and I can boot newer PC's on it, but my old Dell GX-100's won't boot up on it.  The whole reason I started using LTSP was to wring some extra life out of my old hardware.  I have not found any discussion about whether the older PC's should be able to run on the current LTSP with the current Linux kernel.  So, for now, I'm sticking with what works, 8.04 LTS.

Thanks,
Nolo

---

