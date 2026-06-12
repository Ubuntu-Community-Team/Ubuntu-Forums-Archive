---
title: "Weird Internet behavior!"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by wishingstar on 2010-02-08
Ok, I hope this is posted in the right section!

I've been an Ubuntu user since Jaunty, and i gotta say, i'm really impressed, especially with the great Karmic! However, ever since my first ubuntu installation, i've had a very awkward problem: My internet does not open any of the following websites:

rapidshare.com
megaupload.com
urbandictionary

I don't know if there are other websites i wouldn't be able to access, but those are the main ones i use frequently, now here's what i tried so far (nothing worked):

1- Use a different browser (none of firefox, opera or konqueror worked)
2- Edit the etc/hosts file
3- add a line in the etc/hosts.allow file

It seems so stupid to have to power on a virtual machine to download a rapidshare file!

Please HELP!! I'm getting desperate!

wishingstar

---

### Post by Iowan on 2010-02-08
I've seen some unusual causes for specific websites failing to load (if I can remember them): NIC driver, ACPI, and even MTU have been cited as reasons.

---

### Post by wishingstar on 2010-02-09
Thanks for responding, Iowan, but i really have no idea what those terms mean, or how to solve the problem if they turn out to be the reason

Please help!

---

### Post by Iowan on 2010-02-09
[This ]("http://ubuntuforums.org/showthread.php?t=1376506") thread goes through the process of checking [MTU]("http://en.wikipedia.org/wiki/Maximum_transmission_unit"). [ACPI]("http://en.wikipedia.org/wiki/Acpi") is a GRUB option - I'm not familiar with GRUB2.

---

### Post by wishingstar on 2010-02-11
Thanks for the link Iowan! i'll check it out and let you know :)

---

### Post by Grenage on 2010-02-11
I would look at trying alternative DNS servers first.

---

### Post by wishingstar on 2010-02-11
Thanks for the reply, Grenage, but could you please tell me how to do that, I'm not that knowledgeable in all things ubuntu yet :)

*crossing fingers: please let there be a gui method to do this*

---

### Post by Iowan on 2010-02-11
If you get IP address via DHCP, you can add your preferred nameservers to the "prepend" line in */etc/dhcp3/dhclient.conf*. You can use a graphical editor (**gksudo gedit /etc/dhcp3/dhclient.conf**)and pretend it's a GUI. ;) 
It is also possible to add nameservers to Network Manager (GUI!) - [here]("https://store.opendns.com/setup/device/ubuntu/") is a How-To.

---

### Post by joberly on 2010-02-11
FYI, you can try it out with Google's DNS servers.

They are:
8.8.8.8
8.8.4.4

---

### Post by wishingstar on 2010-02-14
Alright guys, this is officially driving me insane!

I've tried everything you suggested, both on this page and the link you gave me Iowan (thanks to all of you for the help)

Nothing worked!!

And what's even more insane is that the XP in the virtual machine connects to these sites, no problem! and it shares an internet connection through ubuntu! (i'm using NAT by the way)...strange!

thanks for the help though! any other suggestions would be appreciated :)

---

### Post by Grenage on 2010-02-14
Assuming that you are using Firefox, under preferences/network settings, try selecting 'no proxy' instead of 'use system setting'.  It's unlikely to make any difference, but I've seen it get confused before.

---

### Post by wishingstar on 2010-02-24
Well, sorry for not getting back to you quickly, I was sick last week. Anyways, I've tried everything suggested, and so far nothing! it's driving me crazy.

I decided to do a little experiment yesterday, I installed vmware on windows, then i installed Karmic as the guest, and voila! Rapidshare just loaded in 1 second!

BUMP!

---

### Post by wishingstar on 2010-04-13
Ok, so i gave up trying after last time, and started accessing rapidshare and the other sites via VM, it worked well. Now this is where it gets really weird:confused:

I installed the ubuntu update for April 9th, and suddenly the morning of April 10th I was able to access rapidshare!!! Alas, though, it only lasted a day as I was no longer able to do so at the next update !!

I hope that give you an idea why it was all happening, it seems that one update solved the problem and then the next one reestablished the same issue!

For now, I am managing this through VM, but it would be really nice if i could just use the Koala for everything :)

Great job everyone! and thanks for all the replies :)

---

