---
title: "Mobile broadband not working in 9.10?"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by bhart007 on 2009-11-01
Ok so previously in 9.04 I was able to insert my Sprint PX-500 pcmcia card and within 10 seconds have a Sprint entry in the networking context menu.  I could click on Connect and..well it would connect.

However since upgrading to 9.10, I have to boot with the card inserted before its recognized and when I click on connect it just sits there.. the little animated icon for the connect sequence locks up.  I get no errors or anything.  No I'm not sure which log to tail to see what happening with this procedure and also Im wondering if anyone else is having issues since upgrading?

---

### Post by lidex on 2009-11-01
You might start here;)
[http://www.ubuntu.com/getubuntu/releasenotes/910]("http://www.ubuntu.com/getubuntu/releasenotes/910")

---

### Post by bhart007 on 2009-11-01
Hmm, interesting stuff but unless I missed it I didnt see anyhting about my issue.

---

### Post by lidex on 2009-11-01
Did you have to manually configure in Jaunty? Post the output of these commands:
```
dmesg
sudo lshw -C network
```

---

### Post by bhart007 on 2009-11-01
Man I didnt do a think in 9.04.. I was so surprised to cause I inserted the very first time. and it worked.

---

### Post by lidex on 2009-11-01
I hear you. Sometimes a couple of updates will fix issues like this in a new release. That's why I usually wait a few weeks to upgrade - allow time for the kinks to get worked out.

Can you run the two commands from above in a terminal and post the output here?

---

### Post by pdc on 2009-11-02
there are issues with mobile broadband in 9.10

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146/)

if you can, you might find reinstalling 9.04 gets  you back on the internet

---

### Post by bhart007 on 2009-11-02
I can't recall teh syntax to pipe the output of dmesg to a txt file.  I'd guess I should post the entire string of results but my buffers not big enough.  Here is the second command:

> allanon@apollo:~$ sudo lshw -C network
[sudo] password for allanon: 
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 11
       serial: 00:15:58:0b:63:a3
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5751m-v3.46a ip=10.1.4.104 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s
       resources: irq:16 memory:b0200000-b020ffff
  *-network
       description: Wireless interface
       product: PRO/Wireless 2915ABG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:0b:02.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:67:a3:8c
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
       resources: irq:21 memory:b4001000-b4001fff


---

### Post by lidex on 2009-11-02
> **pdc said:**
> there are issues with mobile broadband in 9.10

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146/)

if you can, you might find reinstalling 9.04 gets  you back on the internet

Looks like that bug encompasses usb dongle type adapters. OP's is pcmcia.

---

### Post by lidex on 2009-11-02
How about this output:
```
lspci
```

---

### Post by bhart007 on 2009-11-03
Sorry for the late reply lidex.. work today was very craptastic ;p

Anyway here's my lspci with the card inserted:

> 
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)
0b:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 8d)
0b:02.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)
0c:00.0 USB Controller: NEC Corporation USB (rev 43)
0c:00.1 USB Controller: NEC Corporation USB (rev 43)


Wow my thinkpad doesnt even see the card.  However "Sprint" is listed under the Available heading after a left click on the network manager applet thingy (sorry I dont know the proper name for it)

---

### Post by lidex on 2009-11-03
Try right-clicking on that "thingy":rolleyes: and selecting "edit connections". Then click on the "mobile broadband" tab. Anything there?

---

### Post by bhart007 on 2009-11-04
Ok right clicking on the NetworkManager (;p), I have the mobile broadband tab, listed inside is Sprint.  If I attempt to edit that connection Im prompted by a window that wanted me to authenticate in order to modify system policies.  I cancelled the window prior to typing all of this thinking I could open it right back up but thats not the case.  Now NM is locked up.  But I remember this same prompt last week, when I entered my password it wasnt accepted.. "access denied".

I remember thinking it was VERY weird because thats the first time I have ever seen a window such as that. And more so I can edit the wired and wireless ones just fine.

---

### Post by lidex on 2009-11-04
Any other info in that message with "access denied"?

Go to "Users and Groups" in the "System>Administration" menu. Unlock it and select your username. Click properties button on right. In the next window select the "User Privileges" tab. Scroll down and place a check in the box next to "Connect to wireless and ethernet networks". Click OK and close. Reboot and try again.

---

### Post by bhart007 on 2009-11-04
"System Policy prevents modification of system settings: an application is attempting to perform an action that requires priviledges. Authentication is required to perform this action"

Details: org.freedesktop.network-manager-settings.system-modify



After entering password:

"Insufficient Privs"


And this is after making the change you suggested above. Also I thought I'd try connecting saince making those priv changes.. yeah still no dice :(

---

### Post by lidex on 2009-11-04
Working on it. There are some bugs with network-manager in karmic. User "Viva" did this: *I removed the connection and readded it, only with the "available to all users" box unchecked this time. No more network manager problems since then.*

---

### Post by bhart007 on 2009-11-04
OOO I'll have to give that a shot in the morning.

---

### Post by NotTheVistaVirus on 2009-11-05
Like you 9.04 worked without me lifting a finger with my Vodafone USB bb dongle. Now 9.10 refuses to recognise it. The only internet connection I now have is on my Blackberry. Please provide more info on how to deal with this issue as it's a massive problem for me.

---

### Post by CbrPad on 2009-11-05
Hi, have a look at this post...

[http://ubuntuforums.org/showthread.php?t=1314217](http://ubuntuforums.org/showthread.php?t=1314217)

---

### Post by bhart007 on 2009-11-05
Ok so I tried removing the mobile broadband connection and.. well it didnt work.  I click delete and nothing happens.

---

### Post by bhart007 on 2009-11-05
Wait.. well it finally let me remove it.  I re-added the connection but yeah still no dice.  I wonder tho.. since I didnt have to enter any information initially.. it just worked.  I have no clue what the username/password was for this connection.

---

### Post by Cinszani on 2009-11-06
> **bhart007 said:**
> Wait.. well it finally let me remove it.  I re-added the connection but yeah still no dice.  I wonder tho.. since I didnt have to enter any information initially.. it just worked.  I have no clue what the username/password was for this connection.

I think this is problem with USB ports. Try to remove all the USB devices, plug in only your mobile broadband and reboot system.

---

### Post by bhart007 on 2009-11-06
With my device not being USB?  I'm using a pcmcia PX-500 Pantech card.

---

### Post by bhart007 on 2009-11-06
Ok I looked at a couple bug reports on this whole mobile broadband issue.. one listed a git patch in dev for Lucid.  I wonder if possibly installing this would do any good?

---

### Post by suyog on 2009-11-07
You can always got to terminal and use sudo nm-connection-editor
This allows you to edit/delete/add connections.
I think this bug is very irritating as it's just destroying the ease of use which we had in jaunty. Internet connections have become nightmare now.

There also problem with using Mobile Data USB cards.

You need to use gnome-ppp dialer as Network manager just doesnt work.

---

### Post by lidex on 2009-11-08
OK, my latest find:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check")

How's it going?

---

### Post by suyog on 2009-11-10
Hey , this problem got fixed in latest updates, I am able to just plugin my data USB modem and it connects without any issue.

:-) Enjoy.

---

### Post by dvirdc on 2009-11-10
same here. no problems at all with 9.10 and broadband through usb.
with Intrepid i used to connect with my E71 using GNOME PPP.
i was so happy when i found out that they fixed it in Karmic.
now im just using the network manager :)

---

### Post by bhart007 on 2009-11-10
Well I went through the wifi troublshooting guide as lidex suggested.  Everything was going fine until I hit > sudo pccardctl ident
I get > Socket 0: no product info available

I see that a couple of you guys had luck after this last batch of updates..but it has not resolved my issue.

I can insert the card, network-manager animation halts for about 30 seconds, then I get a popup saying my network is disconnected. *sigh*

---

### Post by lidex on 2009-11-10
Can you post the content of /var/log/messages?

---

### Post by lidex on 2009-11-10
Try running this command:
```
sudo /etc/init.d/pcmcia restart
``` before ```
sudo pccardctl ident 
```

---

### Post by bhart007 on 2009-11-10
Well I do not have a "pcmcia" only "pcmciautils".  And my var/log/messages contains:

> 
Nov 10 14:43:13 apollo kernel: [17316.712052] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
Nov 10 14:43:13 apollo kernel: [17316.712228] pci 0000:0c:00.0: PME# supported from D0 D1 D2 D3hot
Nov 10 14:43:13 apollo kernel: [17316.712238] pci 0000:0c:00.0: PME# disabled
Nov 10 14:43:13 apollo kernel: [17316.712407] pci 0000:0c:00.1: PME# supported from D0 D1 D2 D3hot
Nov 10 14:43:13 apollo kernel: [17316.712417] pci 0000:0c:00.1: PME# disabled
Nov 10 14:43:13 apollo kernel: [17316.712629] ohci_hcd 0000:0c:00.0: enabling device (0000 -> 0002)
Nov 10 14:43:13 apollo kernel: [17316.712646] ohci_hcd 0000:0c:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 10 14:43:13 apollo kernel: [17316.712722] ohci_hcd 0000:0c:00.0: OHCI Host Controller
Nov 10 14:43:13 apollo kernel: [17316.712839] ohci_hcd 0000:0c:00.0: new USB bus registered, assigned bus number 6
Nov 10 14:43:13 apollo kernel: [17316.712873] ohci_hcd 0000:0c:00.0: irq 16, io mem 0xb8000000
Nov 10 14:43:13 apollo kernel: [17316.798308] usb usb6: configuration #1 chosen from 1 choice
Nov 10 14:43:13 apollo kernel: [17316.798346] hub 6-0:1.0: USB hub found
Nov 10 14:43:13 apollo kernel: [17316.798359] hub 6-0:1.0: 1 port detected
Nov 10 14:43:13 apollo kernel: [17316.798489] ohci_hcd 0000:0c:00.1: enabling device (0000 -> 0002)
Nov 10 14:43:13 apollo kernel: [17316.798499] ohci_hcd 0000:0c:00.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Nov 10 14:43:13 apollo kernel: [17316.798553] ohci_hcd 0000:0c:00.1: OHCI Host Controller
Nov 10 14:43:13 apollo kernel: [17316.798594] ohci_hcd 0000:0c:00.1: new USB bus registered, assigned bus number 7
Nov 10 14:43:13 apollo kernel: [17316.798614] ohci_hcd 0000:0c:00.1: irq 16, io mem 0xb8001000
Nov 10 14:43:13 apollo kernel: [17316.882169] usb usb7: configuration #1 chosen from 1 choice
Nov 10 14:43:13 apollo kernel: [17316.882250] hub 7-0:1.0: USB hub found
Nov 10 14:43:13 apollo kernel: [17316.882271] hub 7-0:1.0: 1 port detected
Nov 10 14:43:18 apollo kernel: [17320.960036] usb 6-1: new full speed USB device using ohci_hcd and address 2
Nov 10 14:43:18 apollo kernel: [17321.165911] usb 6-1: configuration #1 chosen from 1 choice
Nov 10 14:43:18 apollo kernel: [17321.169014] cdc_acm 6-1:1.0: ttyACM0: USB ACM device 

This this bit is from the moment I inserted the card.

Seems like something is being found.. however whats the PME# disabled mean?

---

### Post by lidex on 2009-11-10
> however whats the PME# disabled mean? 
Not sure but it's not relevant here. Have you seen this guide?
[http://www.sprint.com/assets/downloads/linux/pdfs/Sprint_Mobile_broadband_Setup_Guide_for_Linux.pdf]("http://www.sprint.com/assets/downloads/linux/pdfs/Sprint_Mobile_broadband_Setup_Guide_for_Linux.pdf")

---

### Post by bhart007 on 2009-11-10
Im actually following that right now.. it seems I didnt have Gnome-ppp installed.  And wow.. ok so if I auto-detect my "modem" on Gnome-ppp it finds an ACM device.  Entered the phone number of #777, a fake user/pass and the bloody thing connected.  Network-manager shows nothing but gnome-pp says its connected, pulled an IP, however I can't refresh this page or pull up any others.  Status is idle.

So.. I'd venture to say that maybe network-manager is screwed.. thoughts?

---

### Post by lidex on 2009-11-10
Firefox may be looking to network-manager.
[http://nicokun.wordpress.com/2009/04/27/whos-to-blame-network-manager-vs-applications/]("http://nicokun.wordpress.com/2009/04/27/whos-to-blame-network-manager-vs-applications/")
[http://www.nicnocquee.com/blog/?p=477]("http://www.nicnocquee.com/blog/?p=477")

*I've got 28 tabs open in Firefox right now. Hopefully we can resolve it soon*8-[

---

### Post by bhart007 on 2009-11-11
Think that would affect Chromium?  That's what Ive been using this whole time ;p

I did check however and the user account that Im using does have rights to connect to the internet via modem..

---

### Post by bhart007 on 2009-11-11
I found a thread here: [http://ubuntuforums.org/showthread.php?t=1320420](http://ubuntuforums.org/showthread.php?t=1320420) stating their Huwnei (sp?) usb broadband adapter started working in the proposed kernel update.. so here goes!

---

### Post by bhart007 on 2009-11-11
Hmm ok this sucks.. updated to the 2.6.31-15-generic kernel and still no dice :(

It also appears according to lsmod that no drivers are loading up for the card.. however its correctly identified in lsusb.

---

### Post by Pete051 on 2009-11-11
Hmmm tell me about it, what baffles me is why wireless works more or less if I'm within 2m of the modem more then than that and it tends to disconnect. The other mystery is iwconfig tells me Link Quality=<some figure>/70, it used to be out of a 100 and Bit Rate can be anywhere between 8 and 54Mb/s.
Fedora is starting to look attractive :(

---

### Post by bhart007 on 2009-11-11
My threads focused on the 3g CDMA cards versus regular wifi but yeah Ive heard numerous wifi related issues with Karmic as well.  Luckily mine works perfectly.

---

### Post by lidex on 2009-11-11
> **bhart007 said:**
> Im actually following that right now.. it seems I didnt have Gnome-ppp installed.  And wow.. ok so if I auto-detect my "modem" on Gnome-ppp it finds an ACM device.  Entered the phone number of #777, a fake user/pass and the bloody thing connected.  Network-manager shows nothing but gnome-pp says its connected, pulled an IP, however I can't refresh this page or pull up any others.  Status is idle.

So.. I'd venture to say that maybe network-manager is screwed.. thoughts?

And that's using Chromium? Did you try anything else(browser, torrent, email client)?

---

### Post by bhart007 on 2009-11-11
yeah... I fell in love with Chrome and when I found out it'd work on ubuntu I was like WOOT.

And well.. no  come to think of it...i didnt try anything else.  I'll be on it in the Am.

---

### Post by suyog on 2009-11-12
Yes, Chrome dev version is fantastic, I am using it since it become available for linux. Only think I miss is Bookmark sync.
Not sure when it will be available in Linux as its available in Windows.

---

### Post by bhart007 on 2009-11-13
Ok so for some reason gnome-ppp works in Firefox.  Connects fine, however no connection details, signal strength or practically any other information kinda blows.  But hey at least I know I can get online remotely now.


So with all the posts concerning both wifi and mobile broadband, and as large as the Ubuntu community is I'm really surprised this network-manager issue(s) haven't been worked out yet.
(Im not b!tching cause I <3 Ubuntu)

I had to reboot with the card inserted before I could connect.

---

### Post by lidex on 2009-11-13
Yeah. Would seem to be a network-manager issue then, at least with that card. Here are some links you may find of interest. The first one takes you to the PPA for daily trunk builds for nm. If you're feeling adventurous you can use that repository to get bleeding-edge nm updates.

[https://edge.launchpad.net/~network-manager/+archive/trunk?field.series_filter=karmic]("https://edge.launchpad.net/~network-manager/+archive/trunk?field.series_filter=karmic")
[https://wiki.ubuntu.com/NetworkManager/Hardware/3G]("https://wiki.ubuntu.com/NetworkManager/Hardware/3G")
[http://forum.nginx.org/read.php?26,18242,20367]("http://forum.nginx.org/read.php?26,18242,20367")
[http://www.pcmag.com/article2/0,2817,2087011,00.asp]("http://www.pcmag.com/article2/0,2817,2087011,00.asp")

---

### Post by bhart007 on 2009-11-13
I smell Win! Thanks lidex!

ill keep the thread updated.

---

### Post by bhart007 on 2009-11-13
lidex... dude,  So with these "zero-day" updates.. I assume after scrolling all the way to the bottom of a particular package I should be able to install the debs correct?

For example, I expanded  network-manager - 0.8~a~git.20091112t160951.16c18a0-0ubuntu1~nmt1~karmic

And at the bottom there are debs for:

Built packages
libnm-glib-dev network management framework (GLib interface)
libnm-glib2 network management framework (GLib shared library)
libnm-util-dev network management framework (development files)
libnm-util1 network management framework (shared library)
network-manager network management framework daemon
network-manager-dev network management framework (development files)

Then of course a long list of packages below that.. Im guessing in order to make use of this bleeding-edge update I need to install all of the packages listed there.. amiright?

---

### Post by lidex on 2009-11-13
Actually you'll want to add that repository to your software sources and update the packages as you normally would with update manager or synaptic.

---

### Post by lidex on 2009-11-13
Click on the green link "Technical details about this PPA" for info on adding this PPA

---

### Post by jacklsw2008 on 2009-11-14
i felt quite disappointed with ubuntu 9.10. i thought they would be improving on many features but there are always some issues popping out again. i could use the mobile broadband while testing on live cd. but after i installed 9.10, the network manager won't show mobile broadband connection even though i have plugged in my huawei e220

---

### Post by suyog on 2009-11-15
Hey , its broken again. I guess new updates messed up.
Its so horrible, What the developers are doing?
Someone should put their hands up and fix this, dont play around with normal users.

But I am really disappointed with 9.10 so many show stopper bugs and changes which have not been communicated well. I guess they should stop releasing versions every 6 months and try to make quality product in 2 years. 
Thats needed if you want to take Ubuntu to normal human beings not just geeks.

I am going to try latest build of Network Manager and give a try.

---

### Post by lidex on 2009-11-15
suyog:
You can always go back to 9.04;)
This is exactly why I'll give it a few months before upgrading. On the other hand I think the glass is half full. You may be having issues with one piece of hardware but there are thousands more that work perfectly. Not bad for free. You can't tell me MS gets it all right -- and *after* they take your money.

---

### Post by bhart007 on 2009-11-15
> **lidex said:**
> Click on the green link "Technical details about this PPA" for info on adding this PPA

AHHH ok gotcha.. I had been looking for an actual synaptic source line but couldnt find it.

Giving it a shot now.

---

### Post by bhart007 on 2009-11-15
Ok fou8nd the url.. added it into my Repos and updated all modules involved with network-manager.  The libs too, still doesnt work.  Hmm I'll def be keeping an eye on them though ;p

---

### Post by suyog on 2009-11-16
@lidex,I wont go back to 9.04 as I also know things will be fixed.
But my point was this release had so many show stopper bugs and how they didnt fix those? Also being free can not be excuse.

Again I will say that geeks will struggle and get things going but normal users just wont give damn and wont come back to linux if they have such experience. I am pained to see that I recommended 9.10 to my friend, convinced him and he also has disaster.

It does damage reputation of Linux.

---

### Post by John Read on 2009-11-16
Assuming you have installed your Vodaphone (Australia) wireless broadband modem via the Network Manager and are able to get it to "connect" but are still unable to actually connect to any Web sites, etc. then chances are you still have one small step to go. Right-click the Network Manager icon, choose Edit Connections, click the Mobile Broadband tab, click your Vodaphone service (e.g. Vodafone Postpaid), click the Edit button on the right, leave Number set to *99#, set the Username to vodafone, set the password to vodafone, leave APN set to vfinternet, and click the Apply button. You will be asked if it's OK to store some keys on a keyring, choose "At any time" (or somesuch), then you're set.

I find the connection speed I can achieve in Ubuntu 9.10 is several times faster than I could achieve in Ubuntu 9.04 which is just great.

The only hassle I have is that Ubuntu boots so fast that the modem does not have time to find the Vodafone connection and then it won't appear in the Network Manager list. You then have to cold boot again and hope for better luck next time.

Hope this helps.

Regards,

John

---

### Post by bhart007 on 2009-11-17
Well today a newer pre-release for Network-Manager came out.. version 0.8~a~git.20091117t004859.1151ac2-0ubuntu1~mnt1~karmic


Installed.. rebooted and now the NM swirly applet does not lockup, however it still doesn't connect.

Baby steps.. getting closer I'd reckon.

---

### Post by petermoffat on 2009-11-17
Try updating the firmware of your modem, I just did and it works.

link in this thread:

[http://ubuntuforums.org/showthread.php?p=8334794#post8334794](http://ubuntuforums.org/showthread.php?p=8334794#post8334794)

---

### Post by bhart007 on 2009-11-19
No help.. seems Sprint isnt making firmware for the PX-500 anymore :(

---

### Post by bhart007 on 2009-12-04
Update, since Ive had the daily networkmanager updates ever since my last reply to this thread the px-500 card STILL does not work in anything other than wvdial.  Fairly disheartening at best.

---

### Post by suyog on 2009-12-05
@bhart007, I have also added network manager PPA and it updates daily but no luck with Network Manager and my Huawei modem.
I can connect with wvdial and gnome-ppp very easily.

What the hell Ubuntu developers are doing? Why they just dont fix these sooo serious issues?

Anyone is listening here? I am getting frustrated with Ubuntu 9.10
Its just like downgrade not promised upgrade from 9.04.

---

### Post by bhart007 on 2009-12-21
I've been wondering myself.. it worked so perfectly in 9.04, I also do not understand what exactly took such a wrong turn as to break it in 9.10..

I had assumed back closer to 9.10's release that there were bigger fish to fry.. but now some almost 2 months later and still nothing.

Mine also works using wvdial.. but thats really not the point is it?  I love Ubuntu and I know the devs and all the contributors put in alot of hard work.  But it's things like this that appear to go un-noticed.  Also back when my thread first started and I had submitted a bug report.  Like 2 weeks later I was told that my bug was a duplicate of another except I didnt have rights to view the other bug.  A serious WTF moment right there.

I can only hope that this is fixed in the next release.

---

### Post by alexfish on 2009-12-21
> **bhart007 said:**
> I've been wondering myself.. it worked so perfectly in 9.04, I also do not understand what exactly took such a wrong turn as to break it in 9.10..

I had assumed back closer to 9.10's release that there were bigger fish to fry.. but now some almost 2 months later and still nothing.

Mine also works using wvdial.. but thats really not the point is it?  I love Ubuntu and I know the devs and all the contributors put in alot of hard work.  But it's things like this that appear to go un-noticed.  Also back when my thread first started and I had submitted a bug report.  Like 2 weeks later I was told that my bug was a duplicate of another except I didnt have rights to view the other bug.  A serious WTF moment right there.

I can only hope that this is fixed in the next release.

Hi 

Try This
..................................................................................................

**Add in /etc/modprobe.conf:**           

**[B]options usb-storage delay_use=1 (or 10, or other) 5 is a good bench mark**[/B]

 From The log file Viewer You Can Check If There is A connection to The Secondary Server Which is The one to look for , if only see primary then your only connected locally
 

Adjust the Value Till it Looks Like This

 pppd[5064]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded. 
  pppd[5064]: pppd 2.4.5 started by root, uid 0 
  pppd[5064]: Using interface ppp0 
  pppd[5064]: Connect: ppp0 <--> /dev/ttyUSB0 
 pppd[5064]: CHAP authentication succeeded 
 pppd[5064]: CHAP authentication succeeded 
  pppd[5064]: Could not determine remote IP address: defaulting to 10.64.64.64 
  pppd[5064]: local  IP address 10.93.26.111 
  pppd[5064]: remote IP address 10.64.64.64 
 [COLOR=Navy]pppd[5064]: primary   DNS address 10.203.129.68 
 pppd[5064]: secondary DNS address 10.203.129.68[/COLOR]

If Connection Only Reaches The Primary Server Unplug The Device And Plug It in again  / if You don't need The Browsers Just  minimise it

[SIZE=2][COLOR=Navy]With GPRS,  you don't pay for your online time per-minute, you pay for            the amount of data you transfer.
[/COLOR][/SIZE] 
Slow Server
  try connecting To An Open Server,  setup etc at own risk
..........................................................................................................................................................
Also you could try the usb_modeswitch look here 

                                                                                                                [SOLVED]                          [Ubuntu 9.10 mobile broadband can't connect]("http://ubuntuforums.org/showthread.php?t=1331660")             ([IMG]http://ubuntuforums.org/images/misc/multipage.gif[/IMG]  [1]("http://ubuntuforums.org/showthread.php?t=1331660") [2]("http://ubuntuforums.org/showthread.php?t=1331660&page=2"))

                                 
[COLOR=Navy]
[/COLOR]

---

### Post by bhart007 on 2009-12-22
Shuttleworth's spare room.. ROFL.


Are you saying to create a modprobe.conf?  Becuase I don't have one already..

---

### Post by alexfish on 2009-12-22
> **bhart007 said:**
> Shuttleworth's spare room.. ROFL.


Are you saying to create a modprobe.conf?  Becuase I don't have one already..

Try This

sudo gedit /etc/modprobe.conf

my setting is

options usb-storage delay_use= 2

---

### Post by suyog on 2009-12-22
Why Developers are not fixing this? almost 2 months since 9.10 has been released and i am not able to connect to internet with my huawei modem.
I am thinking of going back to 9.04

---

### Post by alexfish on 2009-12-24
> **suyog said:**
> Why Developers are not fixing this? almost 2 months since 9.10 has been released and i am not able to connect to internet with my huawei modem.
I am thinking of going back to 9.04

Hi

Have you Been using a wireless connection on the same system 

 if so , remove your card and delete all mobile connections 

  if  the wireless card  is enabled whilst using the mobile connection there will be problems  , 

if so delete the mobile connection , disable or remove the wireless card

  reboot , insert the dongle and make a new connection

    Here is a good guide to read
   
			 			[Mobile Broadband  can't connect]("http://ubuntuforums.org/showthread.php?t=1331317") 			([IMG]http://ubuntuforums.org/images/misc/multipage.gif[/IMG]  [1]("http://ubuntuforums.org/showthread.php?t=1331317") [2]("http://ubuntuforums.org/showthread.php?t=1331317&page=2"))


Have a look at page two

---

### Post by suyog on 2009-12-28
@alexfish, I have tried almost all things but still not able to connect via network manager. I can connect without any issues via gnome-ppp and wvdial. There have been number of updates to Network Manager and linux Kernel but issue seems to be still there.
I don't know what developers are doing with this as it's huge show stopper bug for many users like me for whom only way to connect to internet is via USB Modem.

Hey and I liked your quote "two tins are better than iphone".

---

### Post by alexfish on 2009-12-28
> **suyog said:**
> @alexfish, I have tried almost all things but still not able to connect via network manager. I can connect without any issues via gnome-ppp and wvdial. There have been number of updates to Network Manager and linux Kernel but issue seems to be still there.
I don't know what developers are doing with this as it's huge show stopper bug for many users like me for whom only way to connect to internet is via USB Modem.

Hey and I liked your quote "two tins are better than iphone".

hi 

Have you tried to downgrade the network manager ie : the version on the Live Cd

  or the version use in 9.04

  Try Force install / 

  reason been , I have checked both of these 

Plugin /usr/lib/pppd/[COLOR=Navy]2.4.4/nm-pppd-plugin.so[/COLOR] loaded.

 pppd[26819]: [COLOR=Navy]pppd 2.4.5[/COLOR] started by root, uid 0

 pppd[26819]: Using interface ppp0

  will be back with the versions /   

link to / re appelet   [http://projects.gnome.org/NetworkManager/](http://projects.gnome.org/NetworkManager/)

versions 9.04 = Networkmanager applet 0.7.0.100
versions 9.10 after upgrade = 0.7.996/

---

### Post by alexfish on 2009-12-28
These are the different Reading You can get  in the log file viewer / messages

Dec 29 04:13:24 alexfish-desktop pppd[1851]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Dec 29 04:13:24 alexfish-desktop pppd[1851]: pppd 2.4.5 started by root, uid 0
Dec 29 04:13:24 alexfish-desktop pppd[1851]: Using interface ppp0
Dec 29 04:13:24 alexfish-desktop pppd[1851]: Connect: ppp0 <--> /dev/ttyUSB0
Dec 29 04:13:24 alexfish-desktop pppd[1851]: CHAP authentication succeeded
Dec 29 04:13:24 alexfish-desktop pppd[1851]: CHAP authentication succeeded

[COLOR=Red]Dec 29 04:13:24 alexfish-desktop [COLOR=Navy]kernel: [  115.133176][/COLOR] PPP BSD Compression module registered[/COLOR]

[COLOR=Red]Dec 29 04:13:24 alexfish-desktop [COLOR=Navy]kernel: [  115.156035][/COLOR] PPP Deflate Compression module registered[/COLOR]

Dec 29 04:13:31 alexfish-desktop pppd[1851]: Could not determine remote IP address: defaulting to 10.64.64.64
Dec 29 04:13:31 alexfish-desktop pppd[1851]: local  IP address 10.91.40.155
Dec 29 04:13:31 alexfish-desktop pppd[1851]: remote IP address 10.64.64.64
Dec 29 04:13:31 alexfish-desktop pppd[1851]: primary   DNS address 10.206.65.68
Dec 29 04:13:31 alexfish-desktop pppd[1851]: secondary DNS address 10.206.65.68


.................................................................................................................................

Dec 29 04:16:27 alexfish-desktop pppd[2428]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Dec 29 04:16:27 alexfish-desktop pppd[2428]: pppd 2.4.5 started by root, uid 0
Dec 29 04:16:27 alexfish-desktop pppd[2428]: Using interface ppp0
Dec 29 04:16:27 alexfish-desktop pppd[2428]: Connect: ppp0 <--> /dev/ttyUSB0
Dec 29 04:16:27 alexfish-desktop pppd[2428]: CHAP authentication succeeded
Dec 29 04:16:27 alexfish-desktop pppd[2428]: CHAP authentication succeeded


Dec 29 04:16:34 alexfish-desktop pppd[2428]: Could not determine remote IP address: defaulting to 10.64.64.64
Dec 29 04:16:34 alexfish-desktop pppd[2428]: local  IP address 10.91.42.1
Dec 29 04:16:34 alexfish-desktop pppd[2428]: remote IP address 10.64.64.64
Dec 29 04:16:34 alexfish-desktop pppd[2428]: primary   DNS address 10.206.65.68
Dec 29 04:16:34 alexfish-desktop pppd[2428]: secondary DNS address 10.206.65.68

spot the difference this is Ubuntu 9.10 

First output 

 is where  part of the storage is manualy detached internaly on the device / ie I placed a piece of paper over the contacts in the case

the second 

is where the device is in the original state  /

  the mode switching is not working  

  Question 1 . does the problem lay with the hsdpa after the connection is made
  

   if you have a device manager  check the device .. this one is a HSDPA

   is the switching of the device working 100% ?

---

### Post by suyog on 2010-01-02
@alexfish, could you please tell me in detail how can i downgrade network manager to 9.04 version?
Infact i tried to use latest daily version of network manager hoping to resolve this issue. I updates almost everyday but no use.
:(

---

### Post by lidex on 2010-01-02
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

[https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting]("https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting")

---

### Post by suyog on 2010-01-04
Heyyyy Its working with Huawei Modem. I can simply use Network Manager.

:)

---

### Post by jamesvar_70 on 2010-01-05
Haapy new year,

i could use the mobile broadband while testing on live cd. i was using 8.10 and my huawei e220 was working fine with the network manager. I did a fresh install of 9.10, i found the huawei e220 is mounted as cdrom (strangely i found the mounted icon on my desktop for the first time)  the network manager won't detect it if i try to add the connection. 

Now i did a trick, i remove the modem (but still the mounted icon remain on the desktop) then i reinsert it, now i have two icons for the modem and now the NM will detect it and i can connect it to the net. If i go for a reboot i will end up with the same story and i need to first delete the first set-up ( as earlier noted there are access denied problems it wont allow you to modify but you can delete it and go for a new setup)

there were problem with firefox and empathy not detecting the NM status but now i could get past that with the update. also there was some problem when i try to play VCD with xine the connection breaks. i identified the reason as xine was trying to access cdrom and that device is my huawei e220, and xine breaks down also the connection.

i got my cdrom parameters changed and now the huawei e220 is mounted as cdrom2 but i have to unplug it each time for a connection 

any solution 

sorry for the long mail but i hope i have described the problem well

thanks

james

---

### Post by lidex on 2010-01-05
Have you walked through the troubleshooting guides?

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

[https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting]("https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting")

---

### Post by jamesvar_70 on 2010-01-05
Thanks lidex for your reply

i have gone through the links mentioned by you shall i list down my problems

1. Is it the right thing to appear huawei e220 as cdrom (cdrom2 after my modification) on my desktop.
2. why the modem fails to be recognized by the network manager during the boot (though it is already mounted)
3. when i remove the modem and plug it again NM recognise it.
4. in the NM i need to delete the earlier set up to get a fresh set up and connection.
5. do i need to change my fstab to get rid of my mounting problem ( i am only a user not an expert may be a silly qn :).
in 8.10 i did not experience it

thanks

---

### Post by alexfish on 2010-01-06
> **jamesvar_70 said:**
> Thanks lidex for your reply

i have gone through the links mentioned by you shall i list down my problems

1. Is it the right thing to appear huawei e220 as cdrom (cdrom2 after my modification) on my desktop.
2. why the modem fails to be recognized by the network manager during the boot (though it is already mounted)
3. when i remove the modem and plug it again NM recognise it.
4. in the NM i need to delete the earlier set up to get a fresh set up and connection.
5. do i need to change my fstab to get rid of my mounting problem ( i am only a user not an expert may be a silly qn :).
in 8.10 i did not experience it

thanks

Hi

you do not Need fstab for these devices

I have done a fresh Clean  install of Ubuntu 9.10 and done Kernel  updates in sequence

Note 1 : prior to booting Remove All Net Cables and Wifi from Computer

1 . install Fresh Ubuntu 9.10 Re Kernel -14 

2. install the usb mobile broadband from the network manager ; success

3. get the updates ,But do not Run Updates on system Yet

4 . install Ubuntu Tweak

5 .1  for each Kernel upgrade  etc  : 5.2 leave The Dongle in  and disconnect from the network manager

6 . from the network manager delete the mobile connection 

7. safely remove the device 

8. clean up the system with Ubuntu Tweak

9. power down   and reboot without the dongle , reboot again  , insert the dongle and 

make new connection with the network manager . any files or devices showing on the desktop  Just Right click and safely remove 

10. Remember whist using these devices keep wifi  and auto wired  connections OFF

11. Install only One Mobile device at a time , if you change the device repeat the above at 5.2

12 . If you interchange the connections and have problems repeat the stages mentioned

14 . if there is a Kernel version Which Works Best With Your Device Make A note of it

15 . OH and  Please remember Ubuntu 9.10 is not an LTS release

---

### Post by jamesvar_70 on 2010-01-07
Hi,

thanks alexfish for the very detailed reply.

now the situation is like this

if i start with a hard start NM recognize modem am able to connect and firefox, empathy connects to the net

but if for some reason if i opt for a soft restart option the NM fails to recognize the modem.

otherwise things are all seems ok now

i think when it goes for restart option the modem is not geting unmounted cleanly may be thats the issue.

at this stage i am bit reluctant to go for a cleanup let me fight it out this way until i get a better solution

thanks a lot

bye

---

