---
title: "fresh mythbuntu 11.04 with hauppauge pvr.  no IR, no sound, poor picture"
date: 2011-09-25
forum: Mythbuntu
---

### Post by reverendalc on 2011-09-25
i haven't done much with linux for some time... used to maintain a gentoo box for no good reason, and had an "other os" on my ps3... but i was really disappointed with my windows7mediacenter setup, so i decided to throw down on mythbuntu, with limited success...
 
specs are:
HP m7434n htpc
amd dual core 2.6ghz
2gb ram
nvidia 9800gt 1gb
hauppauge hd-pvr 1212
 
the install went smoothly, and i was able to successfully set up the pvr to some extent. the picture is somewhat blurry, very saturated with red, and appears to slow down/speed up. i might add, this is dualbooting on my htpc which also was win7ultMC, where the PVR works fine in every aspect.  cables and whatnot are snug (-;
 
during setup, i was unable to find any usb/IR option for my HP mediacenter remote, though a google search seems to inform me of a usbmceir driver?
 
when setting up the component input of the HDPVR, the sound tab says "build with something to query sound inputs."
 
if i can get this machine working satisfactory, i'd consider turning my 2011whs into a savage backend.
 
i've been, and am continuing to dredge thru wikis, google, and other resources, and i'm sure these are somewhat newbie issues, but if anybody could help me work thru this it would be much appreciated.
 
thanks in advance!

---

### Post by thatguruguy on 2011-09-25
What video drivers are you using?  Do you have VDPAU enabled?

---

### Post by uteck on 2011-09-26
The usbmc remote should work for your HP remote, that is the gnereic MS remote driver and the HP remote is just a re-branded MS one.

---

### Post by Shplad on 2012-05-19
If you used Mythbuntu, the easiest way to configure a remote is through the MCC Mythbuntu Control Centre (graphical or GUI-based) app. That little gem of an app. has an icon for configuring the remote, I think they label it remote in the app. It's really very comprehensive.

You can configure IR remote manually as well, and it's not difficult, but requires a few steps. Start by making 100% sure you know the make and model of your receiver. You may also need the hardware version. To do it manually, you'll probably have to go to a terminal prompt and run "dpkg-reconfigure lirc". That re-runs the initial (text-based) configuration app. for lirc and allows you to select receiver and transmitter (actual remote you hold in your hand).

Suggest you start with Mythbuntu Control Center and report back how things go.


Shplad






> **reverendalc said:**
> i haven't done much with linux for some time... used to maintain a gentoo box for no good reason, and had an "other os" on my ps3... but i was really disappointed with my windows7mediacenter setup, so i decided to throw down on mythbuntu, with limited success...
 
specs are:
HP m7434n htpc
amd dual core 2.6ghz
2gb ram
nvidia 9800gt 1gb
hauppauge hd-pvr 1212
 
the install went smoothly, and i was able to successfully set up the pvr to some extent. the picture is somewhat blurry, very saturated with red, and appears to slow down/speed up. i might add, this is dualbooting on my htpc which also was win7ultMC, where the PVR works fine in every aspect.  cables and whatnot are snug (-;
 
during setup, i was unable to find any usb/IR option for my HP mediacenter remote, though a google search seems to inform me of a usbmceir driver?
 
when setting up the component input of the HDPVR, the sound tab says "build with something to query sound inputs."
 
if i can get this machine working satisfactory, i'd consider turning my 2011whs into a savage backend.
 
i've been, and am continuing to dredge thru wikis, google, and other resources, and i'm sure these are somewhat newbie issues, but if anybody could help me work thru this it would be much appreciated.
 
thanks in advance!

---

