---
title: "NAS device setup help needed"
date: 2011-04-03
forum: Networking &amp; Wireless
---

### Post by styleruk on 2011-04-03
Hi

I have Ubuntu 10.10 64bit edition.  I bought a NAS device recently ([http://www.maplin.co.uk/Media/PDFs/NS347%20feature.pdf](http://www.maplin.co.uk/Media/PDFs/NS347%20feature.pdf))
 and though I plug it into my router and pick it up no problem with the disk it came with, I can't seem to set it up to work with a new drive.  To do this I would need to access the front end and can't seem to find that.  I'm sure it's my inability to work linux networking, can anyone assist?  The drive works fine as a usb drive.
This is what I have done so far...

1) Plug into network and easily browse the disk.
2) Plug in new hard disk, can't find disk.
3) try to log into the NAS...
Try http:\\192.168.0.3 (that was the ip that the previous owner had)....nothing.
4) guessing that i have to change my ip to suit the ip of the NAS
sudo ifconfig eth0 192.168.0.1
...Still nothing.
/etc/init.d/networking restart
...give feedback of...
 * Reconfiguring network interfaces...
 Ignoring unknown interface eth0=eth0.
...still nothing.
5) turn off network connections and turn them on again via small icon in top right, still nothing.
6) Reset NAS, this apparently sets the ip to 169.254.0.1 and netmask to 255.255.0.0
do all above to reset my ip to suit 169.254.0.2...nothing.
No idea how to set mask, tried with ...
sudo ifconfig netmask eth0 255.255.0.0
...still no good

I'm now at a loss

Regards
Simon

---

### Post by styleruk on 2011-04-15
WOW, nobody answered.

---

### Post by styleruk on 2011-04-15
Ok, this is driving me to despair.  I'm actually going to give up on this one and start again somehow.

My task was to have a hard disk that everyone in the house can access and store music and video, so I bought a NAS on ebay, it came with a 40gb hard disk that works.  Plug it in and works fine, however, I want to fit a bigger drive in and that means logging into it...forget it, impossible, as it's set on a different subnet and IP address, I can't change that at all.
I can find the new hard disk but can't access anything on it, I've formatted it as fat32, it does not even work as a USB drive...the old drive...fine.

I have no idea,so will sell it on ebay and give in.

Think I'll buy a cheap pc for 50quid, stick that on my network.  Seems the easiest way.

That's it, even though nobody had a suggestion, I've given up.

---

### Post by joberly on 2011-04-15
Are you sure the device's networking capability still works? Plug it into your router, then go to your router's control panel webpage, and see if it lists the device as even connecting to the network (and it will show you the IP it has). That would be step 1 to ensure it even has network connectivity.

Seeing as this is an IDE only device and came with a 40gb drive, it's fairly old already.

---

