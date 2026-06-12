---
title: "Network problem after reinstall: failed applet, lost connection, can't apply settings"
date: 2010-03-26
forum: Networking &amp; Wireless
---

### Post by markling on 2010-03-26
I can't reapply my network settings since they were lost after a re-install.

This appears to be a problem with a few things:

1. Network application failure after OS reninstall
2. Network settings lost from home folder backup
3. Can't apply new network settings

I reinstalled Ubuntu 9.10 from a USB stick after encountering this error:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/534012](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/534012)

I performed a clean install, erasing all data from the hard disk. It generated the following problems:

1. Network application failure after OS reninstall

After install, on reset, the following error appears:

"The panel encountered a problem while loading
OAFIID: GNOME_NetstatusApplet
Do you want to delete the application from your configuration?"

Even if I select <DELETE> the same error reapears on restart.

2. Network settings lost from home folder backup

I copied my backed-up home folder back onto my computer. My network connection settings have not reappered. Bizarely, some old network settings for an ISP I haven't used for six months have been reinstated. (The backup was from a few weeks ago. I had not deleted the old connection. But the new connection was present and correct when I made the backup).

3. Can't apply new network settings

On trying to manually enter the network settings, I find that I cannot select <APPLY> in the dialogue box because the option stays shaded out and unselectable.

The result is that I am unable to connect to the internet.

---

### Post by mikewhatever on 2010-03-26
> **markling said:**
> 
3. Can't apply new network settings

On trying to manually enter the network settings, I find that I cannot select <APPLY> in the dialogue box because the option stays shaded out and unselectable.

The result is that I am unable to connect to the internet.

Usually, the <Apply> button is grayed out, because the program is expecting more data. What network settings are you entering?

---

### Post by markling on 2010-03-26
I entered SSID, MAC address, MTU as default (automatic), selected appropriate wireless security with password and left IPV4 and IPV6 settings as default (automatic and ignore, respectively).

The only thing i didn't enter was BSSID. Because I don't know what it is. If, however, i give it a value (same one as SSID, say) - it makes no difference. Still can't click the apply button.

The only other field that I can see hasn't got anything in it is the DHCP Client ID in the IPV4 settings. But as these are selected to automatic, this is perhaps not needed (I don't know what it is anyway).

cheers

mark.

---

### Post by markling on 2010-03-27
I've cracked it.

And network management is now better than its ever been.

All I had to do was get the network manager applet to appear on my panel (i.e. the button bar across the top of the desktop screen). It now connects automatically to my wireless network.

An important note: The network management applet disappeared from my panel when I upgraded Ubuntu one or two distributions ago. I have had problems with networks ever since. Roaming was so unlikely I thought Ubuntu wasn't capable of it. Network settings disappear whenever I reinstall or upgrade. In short, its been a blooming nightmare.

It turns out that all I had to do to get the network manager back was:

- Right click on the panel (button) bar that runs across the desktop
- Select <Add to panel>
- Type "notification area" in the search box
- Add the notification area application.

And Bingo. I do suspect, with some relief, that i might even now be able to get wireless roaming working without any trouble. I can for the first time ever see all available wireless networks in Ubuntu.

I still have problem 1. Network application failure after OS reinstall. I shall probably post separately about this.

A minor issue identified re. 3. Can't apply new network settings: I was not entering the MAC address correctly - i.e. it should be with colons - e.g. 4F:0B:F5...etc (I was typing it exactly as it appeared on the back of my netgear router - i.e. without colons) , and this may have been what prevented the <APPLY> button being available in the network connections dialogue box. But I do suspect the network manager makes all this rooting around in the dark unnecessary. Shame it disappeared and never came back.

---

### Post by mikewhatever on 2010-03-28
Cool, thanks for updating.:)

---

