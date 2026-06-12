---
title: "not detecting own network but finds others"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by Kilcaff on 2009-11-02
Hello,

I'm having issue seeing my wireless network on my laptop (HP 6735s).
I can see other networks around my building but not the one sitting 40cm from me!

My adapter is a BCM4312 802.11b/g and my network is running at 802.11b at the moment.

All the drivers seem installed so I can't see why it just isn't seeing my own wireless network.

I'm hoping this can be sorted, especially before I move onto the problems my desktop is having with the wpn311 card...
I've made the move to Ubuntu after wanting to go Linux for a few years but having a failed attempt involving about 6 disks back in early 2000/2001!  So far I'm loving the desktop, speed and tweakablity but this wifi (and some HD output issues on my desktop) are niggling me!

Thanks for any help,
Adam.

---

### Post by t0mppa on 2009-11-02
Check if you have the same issue as in [this thread]("http://ubuntuforums.org/showthread.php?t=1305148").

---

### Post by Kilcaff on 2009-11-02
Well it sounds like that's likely but I get:

lo        no frequency information.

eth0      no frequency information.

eth1      no frequency information.

when I do 'iwlist channe'l and 'nl80211 not found' when 'I try iw reg set'.

---

### Post by Fire_Chief on 2009-11-02
Just to cover all bases...do you have your wireless network set to **not** broadcast the SSID? May want to double check your router or wireless AP's settings to verify that it is broadcasting the SSID (network name).

Cheers!

---

### Post by Kilcaff on 2009-11-02
Well it's definitely the Europe thing as I've changed the router to a channel between 1 and 11 and it's popped up.

As there are other computers connecting though I've had to change it back.

Interestingly whilst it was available it wasn't retrieving an ip address.

It's broadcasting the ssid.

Any ideas how to get it to show the European channels?

---

### Post by Kilcaff on 2009-11-03
Anybody able to help with this?I'm new to Linux so apologies if there's a really simple way of doing this, though after reading a lot of threads it seems there probably isn't!Also, do the passphrases need to be entered in hex?  When I changed the channel to a number below 11 and it did appear on the scan I couldn't get an IP address when I tried to connect with the pass phrase.Cheers!

---

### Post by t0mppa on 2009-11-03
Did you try editing the options file, if the iw command results in problems?

---

### Post by Fire_Chief on 2009-11-03
> **Kilcaff said:**
> do the passphrases need to be entered in hex?  When I changed the channel to a number below 11 and it did appear on the scan I couldn't get an IP address when I tried to connect with the pass phrase.Cheers!

It depends on whether you are using WEP or WPA for your wireless encryption. If using WEP, then yes, the passphrase should be entered in hex. If WPA, then it's just a password entered in regular ASCII format.

---

### Post by Kilcaff on 2009-11-03
> **t0mppa said:**
> Did you try editing the options file, if the iw command results in problems?

I'm a complete novice in most things ubuntu so how do I do this?

I created a text file called options in the directory shown in the thread link above (/etc/modprobe.d) with options cfg80211 ieee80211_regdom=EU in it but it hasn't done anything I can see.  Of course it's just a text file so it may need a different extension or something.  (novice!)

---

### Post by t0mppa on 2009-11-04
You did it all correctly, you can actually change it to a *options.conf* file, so that the system won't warn you all the time about files without an extension in said directory being ignored in future releases. Like I said on the other thread, one user had to add in the other line as well (options mac80211 ieee80211_regdom=64), so you could try that, but this whole options file approach was deemed outdated even on Jaunty, so I wouldn't get my hopes up too high about it.

I did some further research on the matter and tested the iw, which worked perfectly well for me. Was able to change to US limit of 1-11 or to Japanese limit of 1-14 without a problem. When it returns the *nl80211 not found* message, it means that your driver does not support changing the regulatory domain this way.

And that seems to be the case with the Broadcom STA (default driver for the BCM4312 chip) at least and since it's a proprietary, i.e., closed source, driver written by Broadcom, there's not much to be done about it. [b43]("http://linuxwireless.org/en/users/Drivers/b43") might offer better support, so that's one option as well.

---

### Post by epp on 2009-11-04
> **Fire_Chief said:**
> Just to cover all bases...do you have your wireless network set to **not** broadcast the SSID? May want to double check your router or wireless AP's settings to verify that it is broadcasting the SSID (network name).

Cheers!

I have finally (yay!) switched distros back to ubuntu (actually, xubuntu) and am having a similar problem.

With the SSID broadcast disabled (or turned off) at the router, after logging in, it takes the system a good 30 seconds to detect the router and connect to it.  I have enabled WPA2 with a password key and for added security, the NIC of the laptop is the *only* NIC permitted to connect wirelessly to my router.

Yet, when the SSID broadcast is enabled (turned on), the laptop generally has no problems connecting to the router.

Should the SSID broadcast be turned on when using any of the 'buntu distros?  I have used other distros in the past that connected to the same router (with SSID broadcast off) with no issues.

Thanks for any info.

Ed

P.S.  It's good to be back!  ):P

---

### Post by Kilcaff on 2009-11-12
I've been using the cable connection and sorting other things out but still having problems with this.

I can now see and connect to it IF it's on a channel below 11 and unsecured.  I don't know why but I can't get it to obtain an ip address when I use WEP or WPA, and I know the passwords are right.  I'm running 9.04 on my girlfriend's laptop and it's having the same problem.  It times out on the ip address and then shows me a long string as the password so I wondered if I needed to change the passphrase to hex or something?

I don't want to leave it unsecure and now it's pretty important as I don't have enough cables and Vista has committed suicide on my girlfriend's laptop after updating itself.

Any ideas?

---

### Post by epp on 2009-11-12
I'm wondering if it might be your router.  Mine is a Linksys WRT54G, secured connection with WPA and as long as the SSID broadcast is turned on, the laptop connection is live right at login.

---

### Post by Kilcaff on 2009-11-13
It's a pretty old speedtouch st585, I may swap it for the rangemax I have and see if it makes a difference.  All the settings appear right when I put the encryption on, it broadcasts it's name, allows multicast and allows new stations, I've tried WPA-PSK encryption 1 and 2 and both, I found it weird it didn't work with WEP either.

---

