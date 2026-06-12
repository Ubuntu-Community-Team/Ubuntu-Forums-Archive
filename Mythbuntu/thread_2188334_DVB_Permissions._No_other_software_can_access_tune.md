---
title: "DVB Permissions. No other software can access tuner adapter"
date: 2013-11-16
forum: Mythbuntu
---

### Post by TheYetiWakes on 2013-11-16
I've built a single box HTPC which is running Mythbuntu (originally unbuntu 13.10 which I converted to mythbuntu) to use its backend for TV tuner duties with the plan of putting XBMC over the top.  Everything on the backend setup went smoothly and mythtv front end loads up and its all talking to one another.  I then installed the DVB-S2 TV tuner card, a TBS 6920.  I used the latest drivers from TBS and followed their instructions. Again everything went relatively smoothly and in the mythtv backend setup I successfully added the card, scanned for channels and had the live tv feed working in the frontend.    

However, on reboot I cannot get anything other than the frontend  to now open the DVB adapter, including mythtv backend.  It fails to open the card and won't rescan. I setup the Myth PVR client in XBMC and it connects to the database but reports that is waiting for the PVR client to start (everything is enabled and live tv setup).  Back in terminal I tried loading a channel with mplayer and get an error that it failed to open /dev/dvb/adapter0/frontend0. ERRNO 16

Checking the permissions for the adapter it seems to be set to root:root and I may be way off but have a feeling this is something to do with the problem.  I tried changing the permissions with the chmod 666 which did change them but on reboot they change back.  ~However, even with this changed or if I swap to root it still reports that it failed to open the card though.  Im wondering if something is already loading at bootup and stopping this before I get a chance to swap permissions?

Hunting around on the net I found a couple of links about Udev creating DVB permissions incorrectly:
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/993868](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/993868)

but im starting to get a bit lost here with scripts for rules and whatnot.  

The card is there and works in mythtv frontend but something is stopping anything else accessing the adapter including the backend setup.  Any suggestions please?

---

### Post by khPWXxF on 2013-11-16
I've not used your tuner, but you say:

> [COLOR=#000000] I cannot get anything other than the frontend to now open the DVB adapter, including mythtv backend.[/COLOR]

This is confusing.  The frontend gets the signal from the backend via your LAN or loopback.  LiveTV is not really live - it's a record and immediate playback.

Do these posts help?

[http://chrisdjscott.com/other/mythtv/backend](http://chrisdjscott.com/other/mythtv/backend)
 
[http://www.mythtvtalk.com/dvb-s-card-works-kaffeine-but-not-mythtv-13676/](http://www.mythtvtalk.com/dvb-s-card-works-kaffeine-but-not-mythtv-13676/)

Also, some tuners (eg Hauppauge) need to load firmware and will only reload after a cold boot (ie power off box at mains plug) so might have a stale configuration.
  
Best wishes
Phil

---

### Post by TheYetiWakes on 2013-11-16
Thanks for the links. The posts aren't really what im experiencing though. It worked fine with mythtv on the initial setup.   I installed the driver (and the firmware as mentioned in your first link) as root as instructed and everything worked ok.  After a reboot the card is still detected by everything but they won't open it to use it.  Even in mythtv backend when I go into capture cards menu it shows the card being located at dev/dvb/adapter0 but also text that due to unknown error it can't open it.  There is im assuming something about the front end setup that has the right permissions to still access and use the card.  

Same with mplayer.  Its not saying there is no card but just it cannot open frontend0 on adapter0.

I've found a similar problem here:

[http://ubuntuforums.org/showthread.php?t=1295586](http://ubuntuforums.org/showthread.php?t=1295586)

I'm not near the HTPC at the moment to experiment further but looks like it could be something along these lines.  Either that or the tuner is being used by something at bootup (mythtv frontend?) and its stopping anything else accessing it?

---

### Post by TheYetiWakes on 2013-11-22
Well just to say i've played around with permissions and all sorts to get this sorted with no joy.  

Deleting the card from MythTV backend makes it useable again  in all other apps and the backend itself finds it straight away if i wish to reinstall a capture card.  But as soon as it does the front end seems to lock in its use and makes it unavailable and if I try accessing it with any other prog (including the backend) I get either already in use errors lack of permissions problems.  

In the end I deleted it again and installed Tvheadend instead.  It detected it straight away, the PVR front end with XBMC worked straight out of the box and I had it all configured within an hour, plus all other apps can still access it. Wish I had gone this way from the start.  I would have skipped mythbuntu and either gone a normal ubuntu desktop or even OpenElec with TVheadend. So much simpler.

---

### Post by drifting on 2013-11-26
Interesting.
I have just installed two TBS cards a 6982 DVB-S & 6280 DVB-T
Problem I had was constant tuners are in use, yet with scan then play via mplayer they work fine? Now by accident I stopped the backend and thought about starting it verbose, but instead of doing a sudo service mythbackend stop & Start I just mytbackend on it's own. Tuners now work in Myth? , did try starting as a service and the tuners are all busy again? not sure that my problem is related to yours, so will probably make another post.

---

