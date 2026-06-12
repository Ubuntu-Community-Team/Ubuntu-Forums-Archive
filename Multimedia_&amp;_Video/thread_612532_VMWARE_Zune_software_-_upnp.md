---
title: "VMWARE Zune software - upnp?"
date: 2007-11-14
forum: Multimedia &amp; Video
---

### Post by twistedneck on 2007-11-14
New Zune software has wireless sync. cool!

problem is, VMplayer XP wont broadcast the proper signals to allow the Zune to find it.  Zune finds the network just fine, but can't make it through ubuntu to VMWARE XP - zune software.

Darn it!  i refuse to switch to vista.


how can i get this wireless sync working, what am i missing?

---

### Post by x64Jimbo on 2007-11-14
Is your VMWare guest OS configured to bridge to the network or NAT? If it's bridged and the firewall is turned off, it should be able to find it.

---

### Post by Zune-Online.com on 2007-11-14
Hi,

I used Zune wireless syncing over my Vista installation which runs with a bridged IP on VMware on top of Linux (Debian amd64).

I still haven't tried it with XP on VMware but I don't think its a Windows problem. I suppose you use NAT, not bridged IP, and Zune Software can't communicate correctly with the player (they are not in the same subnet).

These videos show Vista on Debian :
[http://www.zune-online.com/news/zune/videos-89-wireless-sync-setup.html](http://www.zune-online.com/news/zune/videos-89-wireless-sync-setup.html)
[http://www.zune-online.com/news/zune/videos-10-12-wireless-sync-in-action.html](http://www.zune-online.com/news/zune/videos-10-12-wireless-sync-in-action.html)

---

### Post by twistedneck on 2007-11-14
> **Zune-Online.com said:**
> Hi,

I used Zune wireless syncing over my Vista installation which runs with a bridged IP on VMware on top of Linux (Debian amd64).

I still haven't tried it with XP on VMware but I don't think its a Windows problem. I suppose you use NAT, not bridged IP, and Zune Software can't communicate correctly with the player (they are not in the same subnet).

These videos show Vista on Debian :
[http://www.zune-online.com/news/zune/videos-89-wireless-sync-setup.html](http://www.zune-online.com/news/zune/videos-89-wireless-sync-setup.html)
[http://www.zune-online.com/news/zune/videos-10-12-wireless-sync-in-action.html](http://www.zune-online.com/news/zune/videos-10-12-wireless-sync-in-action.html)


Awesome Zune-Online.com!!!! 

I'll try that tonight, and yes I'm using the default NAT and not bridged IP.   Thanks a ton.

---

### Post by Zune-Online.com on 2007-11-14
I also tried Wireless sync with Windows XP on VMware. It works fine too.

I don't know if thats true, but I read somewhere you need the PC to be connected to the Access Point via ethernet cable and not via Wifi to work with Zune. I believe that doesn't makes sense but I can't verify it since I don'ts have a Wifi card on my PC; its always connected to my ADSL Access Point via eth cable.

Kostas

---

### Post by twistedneck on 2007-11-14
I'll update tonight after it try it out.. 

in addition, this would mean the zune can properly communicate with zune software via vmware and ubuntu and the xbox360 - allowing for sharing of the music collection over the xbox360.

---

### Post by carnagex420x on 2007-11-14
I also have an XP VM using NAT and i got no sucess. can one of the vmnet device be sutup to do this? I dont know details on how vmnets can be used or configured so...just a thought.

---

### Post by twistedneck on 2007-11-14
Success!

one simple mouse click on the network options of vmplayer  'bridged ip' and that was it.. done. zune sync's wireless just fine.

its actaully a pretty cool feature too..   and you dont have to have it plugged into an ac charger like originally thought.

thanks very much Zune-Online.com!

---

### Post by x64Jimbo on 2007-11-15
I guess my post was invisible or something :P
Just kidding! I am glad the solution was found.
Now, about that Microsoft product you're using... 
j/k again...

---

### Post by carnagex420x on 2007-11-15
im not a noob but i cant get my bridged netwok to in xp...idk wat im missing, my firewall is off, and i changed the vm setting. ?

---

### Post by x64Jimbo on 2007-11-15
You can't change the setting, or changing the setting didn't help?
Can you ping the virtual machine's IP from another machine on the network? You can get the XP machine's IP by typing "ipconfig" in a CMD window.

---

### Post by carnagex420x on 2007-11-15
I dont have a Default Gateway and i cont ping my linux host. (destination host unreachable) i also dont think im on the same subnet...

I read that you need to setup a bridged network before installing the VM. However there is a configuratior editor setting for this    somewhere.

---

### Post by twistedneck on 2007-11-15
> **x64Jimbo said:**
> Is your VMWare guest OS configured to bridge to the network or NAT? If it's bridged and the firewall is turned off, it should be able to find it.

x64Jimbo..  wow.. i didn't even see this post when i scrolled down too fast! you deserve cred my man.. thanks!

little warning, the samba shares might change address slightly when you go from NAT to bridged.  Mine did and i had to delete my library and device databse files from the zune folder.. and re-sync everything.  with usb1 that took a long time.  but its done now!  (you also have to re-link your zune to your software).


thanks all.

---

### Post by twistedneck on 2007-11-15
> **carnagex420x said:**
> I dont have a Default Gateway and i cont ping my linux host. (destination host unreachable) i also dont think im on the same subnet...

I read that you need to setup a bridged network before installing the VM. However there is a configuratior editor setting for this    somewhere.


i did not setup a bridged network first.. there is this one problem some people get.  might help you.

[http://scottbarnham.com/blog/2007/08/23/vmware-on-ubuntu-linux-with-bridged-network-to-xp/](http://scottbarnham.com/blog/2007/08/23/vmware-on-ubuntu-linux-with-bridged-network-to-xp/)

"This led to the answer on Launchpad - the problem was the network card. Apparently some network cards optimise by discarding packets they have already seen. Because the networking is effectively between two machines on the same network card, some of the data was getting lost.

The solution is to disable these settings on the Ethernet card using:

ethtool -K eth0 sg off rx off tx offor

ethtool -K eth0 sg off rx off tx off tso offdepending on the settings supported by your network card."

---

### Post by carnagex420x on 2007-11-15
Thanx, ill give it a try wen i get home

---

### Post by carnagex420x on 2007-11-15
No luck. both commands exectuted fine in the terminal, but the xp VM acted the same, and got same address as before

---

### Post by carnagex420x on 2007-11-15
I just saw this in the VMWare documentation:



Bridged networking is set up automatically if you select Use bridged networking in the 
New Virtual Machine wizard or if you select the Typical setup path. [B]This selection is 
available on a Linux host only if you enable the bridged networking option when you 
install Workstation.[/B] You can set up additional virtual bridges for custom configurations 
that require connections to more than one physical Ethernet adapter on the host 
computer. Linux and Windows hosts can use bridged networking to connect to both 
wired and wireless networks.
i ran vmware_config.pl and reconfigured my networks but i still cant get it. WTF am i doin!?!

---

### Post by twistedneck on 2007-11-16
Ok, when you do bridged can you surf the net?  what happens in vmware xp when you go to a cmd prompt and hit ipconfig? i assume still nothing.   

does it work properly in NAC mode?

or - do you have some type of static ip setup on your router? if so you have to type in the virtual mac address on the virtual card that vmware creates.

---

### Post by carnagex420x on 2007-11-16
OK, after alot  of failed configurations and some dhcp.conf problems i finialy got my bridged network to work. I can cannect to the internet and detect my router in ZMP. My Router is 192.168.11.1 and my DG is 192.168.2.1. My IP is also on the .**2**.7 subnet. i can ping my router (.11.1) but not other XP machine (.2.4). ?????????? i saw something about sending a sucessful broadcast and then having everything work.

---

### Post by carnagex420x on 2007-11-16
ALSO, when i connect throu a wired connection ( ISP>ROUTER>MAC MINI "internet sharing"(WLAN2LAN)>SWITCH>CLIENTS) when i connet through the MAC i get assigned a .2.2 again with a .2.1 DG. i dont have a firewall on the MAC BTW. i can connect to the internet but i didnt try pinging my XP machine. NO IDEA.

---

### Post by carnagex420x on 2007-11-17
ALSO, when i connect throu a wired connection ( ISP>ROUTER>MAC MINI "internet sharing"(WLAN2LAN)>SWITCH>CLIENTS) when i connet through the MAC i get assigned a .2.2 again with a .2.1 DG. i dont have a firewall on the MAC buti have MAC address filtering andi already added the cards. i can connect to the internet but i didnt try pinging my XP machine. STILL NO IDEA.

---

### Post by carnagex420x on 2007-11-17
OK, after allot of confusion i stopped and came up with a better idea. Considering mine network setup i sat for a min. and realized..I have another router...i also have an extra plug, so i just used my other router as the access point since its in my room w/ me i will have excellent service and it will me private (mostly) since its not connected online. i connected ubuntu to the router, started my bridged VM and next thing i know I have successfully synced in NO TIME. THANX FOR THE HELP THOUGH!

---

### Post by x64Jimbo on 2007-11-17
Glad you got it all resolved! Thanks for sharing your solution, too!

---

### Post by twistedneck on 2007-11-17
ONe more update.. its much better for zune software and sharing if you make sure that your 'my documents' on the shared vmware box is the samba share that zune uses.. 

in addition, change your security in the smb.conf file from secruity = user to security = share..  all my problems solved now too! love this board.

---

### Post by carnagex420x on 2007-11-19
Right after i got it to work, i tried installing Backtrack 2, to a USB and overwrote the begining of my drive. After installing a fresh 7.10 my bridged network doesnt work again. For some reason the zune has brought down my network, it did it before and it just happened again. when i have a bridged connection set i get a 162.240.78.6 IP and a 255.255.0.0 SN MASK. i have to have something in VMWARE configured wrong because i cannot get out.

---

### Post by x64Jimbo on 2007-11-19
Did you re-run the configuration script after reinstalling. 
Also, why did you reinstall the whole system? Why not just fix GRUB?

---

### Post by carnagex420x on 2007-11-20
i didnt overwrite my MBR i overwrote /bin /etc/ and /home so i got 4% on the ubuntu splash screen. but nehow, i narrowed it down to my wireless card...If i use a bridged connection with my wired connection i am set. i can scan networks but i cannot connect. With the wired connection UNplugged  i can again scan and see my router but cannot connect. i have vmnet0 set on my wireless device and it fails on that and bridged mode.

---

### Post by carnagex420x on 2007-11-20
I think i found the answer on this forum ...... [http://ubuntuforums.org/showthread.php?t=574427&page=2]("http://ubuntuforums.org/showthread.php?t=574427&page=2")
Ill have to try it later on.

---

### Post by carnagex420x on 2007-11-20
F*cking Sweet It Works, I Love This Community!                   Thanx!

---

### Post by carnagex420x on 2007-11-22
If the Zune has WiFi *b* doesnt it have the same transfer rate as USB 1.0 at 12Mb/s?

---

### Post by x64Jimbo on 2007-11-23
correctamundo, my friend.

---

### Post by twistedneck on 2007-11-25
Is it still true that vmware does not support USB 2.0?  I thought that was a temporary thing..   I run 1.0.2 version and its USB 1.0 only.

BTW, as much as i appreciate what microsoft was doing with the new zune software - written this time from scratch and for the zune not just media player running a zuned up 'urge' software, it sucks.

no control over multiple album art, forced individual album for each song on compilations, no manual control over meta tags in the zune soft, many many other bugs.. not well done at all - looks cool though.

---

### Post by x64Jimbo on 2007-11-26
> **twistedneck said:**
> not well done at all - looks cool though.
This is true of most Microsoft software.

---

### Post by twistedneck on 2007-11-26
its atually not as bad as first thought..

the only place new zune 2.0 has issues is with downloaded songs ala souldseek, etc..

and there is a fix, make sure to add the column 'albumartist' to the main view- its an unseen metatag that causes albums to be scattered across multiple songs because this metatag is different.

to make it faster you can use a third party program to edit the metadata and then re-do your library.

---

### Post by x64Jimbo on 2007-11-27
Weird that my Linux music management programs are actually more proficient at sorting my music than a music program whose designers were paid.

---

