---
title: "trouble automatically reconnecting to wireless network after restarting router"
date: 2009-08-19
forum: Networking &amp; Wireless
---

### Post by frozenbears on 2009-08-19
I'm setting up a netbook (Dell Mini 9) that needs to be able to automatically reconnect to the wireless network it's using if the router is temporarily down, or restarted.  I'm running Ubuntu 8.0.4.  

It "sort of" works.  Here's the deal –– when the router is off, the network manager icon in the system tray does it's little circling motif, and then one of two things seems to happen:

(1) It displays the "authentication required by wireless network" dialog, along with the required wireless key, which it already knows about.  Once the router is back online, if I click OK, it will reconnect.  It won't do so automatically.

(2) On a few occasions, it totally hangs the UI.  By this, I mean that nothing in GNOME is responsive, terminals (mostly) refuse to accept keyboard input, and even CTL-ALT-DELETE is unresponsive.  Necessitates a hard reboot.  

I imagine the crashing is perhaps a driver issue, but I have no idea why it would ask for authentication.  It already has the WPA key, and that data doesn't need to be re-entered in order for it to successfully reconnect, I just have to click OK.  This is a big problem – I'm looking to deploy this netbook, and similar ones, in an environment where it needs to function without human supervision for long periods of time, and where a sudden loss of network access (without eventually resolving itself) would be unacceptable.  I've got hamachi on there, and I'm going to need to be able to SSH into the machine from time to time without having to worry about calling someone and asking them to reboot the machine or fuss with a dialog box.  

Any suggestions?  I'd be happy to provide more info if this isn't sufficient.

Thanks, all.

---

### Post by scrappitydoo on 2010-02-02
I want to do exactly the same thing!!

My netbook is unsupervised, so when WIFI get interrupted -- instead of throwing up an "Authentication require by wireless network" dialog -- I'd like my computer to automatically reconnect.

Have you figured this out? I may end up having someone write me something custom...

[email]scott@bitstar.com[/email]

---

### Post by bpsimons on 2010-02-09
I'd also like to see a solution to this problem. I have a machine that I'd like to keep connected to a wireless network whenever the connection is available. As soon as the connection drops off for a few minutes though, the machine throws up a password dialog and waits for user input. Is there a proper way around this behavior? I'm about to code up something ugly and evil.

---

### Post by scrappitydoo on 2010-02-10
Well I found a solution... I found a great alternate Network Manager called [WICD]("http://wicd.sourceforge.net/") which I downloaded through the synaptic package manager, and installed over my the default network manager. It does not display the dialog anymore, just keeps looking to reconnect in the background. 

I find it to work better in several areas, so anyone having problems with connecting or dialog boxes or having to input passwords everytime they reboot should definitely give WICD a shot. And it's easy to go back if you don't like it...

---

