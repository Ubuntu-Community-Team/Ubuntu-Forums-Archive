---
title: "How I fixed my &quot;invalid VPN secrets&quot; problem"
date: 2009-07-16
forum: Networking &amp; Wireless
---

### Post by Roadcrew on 2009-07-16
How I resolved 'invalid VPN secrets'

Originally I had 8.10 installed with vpn & wireless working just fine. Updated to 9.04. vpn broke, wireless was less than ideal working about 80% of the time. 

Wiped the drive and did a brand new clean install of 8.10. Initially vpn would work for one configuration. I need 2 separate connections. Somewhere along the way I screwed up and responded to always allow to the keyring prompt and promtpy broke my only working vpn connection. Crap. Google time. 

I tried the usual combination of sequences configuring a pptp vpn connection. domain\userid, userid@domain_name for the User name, leaving the password blank, not blank, NT domain blank not blank,  various combinations of pap, chap, mschap, mschapv2, stateful encryption allowed, gconf-editor vpn setting inclusion of refuse-eap=yes, several incantations and burnt offerings all to no avail. I googled for several days and at no time did I ever find a clue that resolved the problem. This is a deal breaker for me because I need a vpn connection. I'd rather have the 2 connections but one working connection to my work domain I can live with. 

If you intend to follow this process you WILL need the iso for the alternate install burned on a cd (there are methods you can use to mount the iso without buring a cd, but thats outside the scope of this post). A live cd iso burned to disc will not work. 

Warning
If you do not have the alternate install disc for 8.10, once you remove the packages, you will not have wireless or an ethernet connection. 

The process I used:
In Synaptic Package Manager I made sure that the Third-Party Software respository for
 [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) intrepid was unchecked. 
 
I marked for complete removal in Synaptic Package Manager the following packages :
(Just removing the packages is not enough. I had to do a Complete Removal.)
  network-manage
  network-manager-gnome
  network-manager-pptp
  pppconfig
  pppoeconf
  pptp-linux
  wvdial
  ppp

 Once everything was unistalled, I re-booted.
 I inserted the Intrepid Alternate Install cd

 from the cli I entered the following

	sudo apt-cdrom add
	sudo aptitude update


Somewhere in the process I got a prompt message about loading the cd in the Package manager or doing an upgrade. I selected the option to start the Synaptic Pakage Manager. This prompt does not occur once you have an operational network, not on my machine anyway. This a grey area for me. I'm not really sure what caused the prompt to appear, since the prompt does not appear on subsequent mounts of the cd. 

I then re-installed the packages that I removed that were available on the alternate cd. If I remember, all but the network-manager-pptp package was available. Not a problem. Once the packages were re-installed I rebooted again. I notice this time I had the nm-applet icon in the tray. reconfigured my wireless connection and connected. Ran Update Manager and got the latest and greatest network-manager and relavent updates. Reboot, just because. 
Notice that the wireless connection wasn't auto-connecting, so I brought up Network Connection configuration gui, clicked the wireless tab, highlighted and edited the wireless configuration in question and made sure the Connect Automatically was checked. (which it wasn't)
Now on to the VPN setup 
Brought up the Synatic Package Manager and install network-manager-pptp .
re-booted once.

Left clicked nm-applet in tray, VPN Connection > Configure VPN. Clicked Add button. I selected pptp protocol and clicked Create.. button. Supplied a value in Connection Name:, checked Connect Automatically, entered my value for the Gateway:, entered domain\userid value for the UserName:,
left password blank, left NT Domain: blank, clicked Advanced button.
Unchecked pap, chap. Left the remaining authentication methods checked. Checked Use Point-to-Point encryption, checked Allow stateful encryption, clicked OK button.
 
Then I Alt-f2-ed and enter gconf-editor.expanded system, expanded networking, expanded connections, found the vpn connection and then right clicked on the key=value sets side of the screen (right side) and selected New Key..For the name I entered refuse-eap, tabbed to type and selected String, tabbed to value field and entered Yes. Clicked ok and closed gconf-editor.

Tried the vpn connection I just defined and whoo hoo its working again. Repeated the process for defining a second VPN connection and it also works. 

No more Invalid VPN secrets.


Hopefully this is of use to someone experiencing this problem.

---

### Post by T3kG33k on 2009-11-04
Are you seeing any issues in 9.10?

---

### Post by derrek.cooper on 2009-11-28
this invalid vpn secrets is driving me bonkers. I upgraded from 9.03 to 9.10 and my vpn worked fine. But, I was having other issues with the upgrade so I did a fresh install and now I get this nightmare error constantly.

Without vpn, makes my netbook almost worthless..

---

