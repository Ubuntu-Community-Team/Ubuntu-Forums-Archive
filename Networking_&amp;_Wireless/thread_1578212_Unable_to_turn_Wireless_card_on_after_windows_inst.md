---
title: "Unable to turn Wireless card on after windows install"
date: 2010-09-20
forum: Networking &amp; Wireless
---

### Post by Barbellion on 2010-09-20
Hi,
 
Just switched to Ubuntu (whoop!), but after install I can't use my wireless card. The terminal tells me the network status is disabled, and help says I then need to turn my card "on", but pressing my wifi card button does nothing and it remains red (off).
 
I know there can be problems with drivers, but I'm not up to speed on how to deal with this in Ubuntu.
 
My laptop is a Compaq Presario CQ40 401AU and I think my wifi card is a [Realtek Family PCI-E]("http://ubuntuforums.org/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-75798-1&lc=en&dlc=en&cc=emea_africa&product=3911221&sw_lang=&os=4062"), though I don't know how to get any more detailed info than that (though of course will if someone can point me!).
 
Any guidance appreciated.
 
Cheers :)

---

### Post by anubhavrocks on 2010-09-20
Can you try:
sudo rfkill unblock all
sudo rfkill unblock wifi

Also check the manpage for rfkill:
man rfkill

---

### Post by Barbellion on 2010-09-20
"sudo rfkill unblock all" and "sudo rfkill unblock wifi" dont seem to do anything and "man rfkill" refers me to the undocumented manpage. :(
 
Does the status "Disabled" mean the drivers and all that are alright? 
 
Incidentally, the wifi on/off button is on the same board as the power on off, which is working.

---

### Post by anubhavrocks on 2010-09-20
See if you find this helpful:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by Barbellion on 2010-09-20
Thanks for that - Following through to section 4.3.5, it looks like my drivers are ok and communicating. Just disabled... 
 
The help of 4.3.5 isn't floating the boat though
a) The laptop testing team website doing exist anymore and the new project doesn't have my laptop listed. 
b) I didn't turn the wireless off in Windows before I did the Ubuntu install. But maybe it happened as part of the wiping process? I'm not running a dual boot so I can't exactly nip back into windows to see how it's going...
 
Is it common to have this happen?
 
I've only found things online about installing the drivers in other versions of linux, but that's quite a different problem.

---

