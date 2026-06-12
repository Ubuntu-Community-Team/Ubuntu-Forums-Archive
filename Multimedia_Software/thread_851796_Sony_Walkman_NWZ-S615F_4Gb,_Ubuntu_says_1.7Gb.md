---
title: "Sony Walkman NWZ-S615F 4Gb, Ubuntu says 1.7Gb"
date: 2008-07-07
forum: Multimedia Software
---

### Post by vs8 on 2008-07-07
I bought this MP3 player the other day and when I plugged it in, guess what Hardy Heron couldn't mount it. I searched the forums and finally got it working thru Pmount. Now the problem is that the MP3 is supposed to have 4Gb of storage capacity, but Ubuntu says it's only 1.7Gb.

Here are the Mp3's specs:

[http://www.google.com/products/catalog?client=opera&rls=en&q=sony+nwz+s616f&sourceid=opera&ie=UTF-8&oe=utf-8&um=1&cid=15137343659016182577&sa=X&oi=product_catalog_result&resnum=1&ct=result](http://www.google.com/products/catalog?client=opera&rls=en&q=sony+nwz+s616f&sourceid=opera&ie=UTF-8&oe=utf-8&um=1&cid=15137343659016182577&sa=X&oi=product_catalog_result&resnum=1&ct=result)

Thank's for any help!:)

---

### Post by vs8 on 2008-07-07
A little bit of help?:(

---

### Post by babiack on 2008-07-11
i have a sony walkman NWZ-S615F 2gb and i have the same problem as you.  it says 1.7 gb of space but i cant even use it for it says the folders in the content can't be displayed.  please somebody help

---

### Post by hansdown on 2008-07-11
Hello,vs8 and babiack. I also have the nwz-s615f mp3. I've not been able to mount mine either because sony insists that windows media player 11 be the default player. I have found something that works for me, which is a low priced rca home stereo with a usb port. It has a one touch record function that loads any cd onto the walkman. One drawback for some, (not me, as I plan to live forever), is that the disk has to play each song through. Hope this helps, as it works great for my purposes.

---

### Post by babiack on 2008-07-13
i dont have enough money to afford anything right now.  im saving up to get a apple ipod.  they seem to work good with ubuntu but for now i am trying to just get this one to work for a little bit longer and so there is no need to get a rca home stereo but if i was going to keep it as my main player i would try and get one but i want to try an apple ipod and see how that goes.

---

### Post by rktesser on 2008-07-22
The space reported for your player is right. The Sony NWZ-S615F has 2 GB of capacity. The model which has 4 GB is th NWZ S616F. Only 1.7 GB is detected because some storage space is used for the system, you can find this information in the manual or in the Sony web site.

I own a NWZ-S616F and also can't mount it *** mass storage device. I've read somewhere else that there's a bug in some component which Ubuntu uses that causes this problem. I tested it in another distribution and the player was mounted.

However, you can use Rhythmbox or Amarok to transfer music to and from your DAP using the MTP protocol.

---

### Post by valmorel on 2008-09-08
Here is how to fix the bug you describe. It sounds scary, but just follow the instructions. After, your Walkman will automount as a UMS device just fine:

[http://kubuntuforums.net/forums/index.php?topic=3096598](http://kubuntuforums.net/forums/index.php?topic=3096598)

---

### Post by rktesser on 2008-09-13
Hi. This is a different device. The Sony NWZ-S61# series of devices, referred in this post should be mounted as mass storage devices. They also support MTP, which is working with HAL+Rhythmbox. 
The problem was that the device reports very large number of sectors and the size of the variable HAL used to store it was too small. One interesting fact is that on 64 bit Linux the bug didn't happen because the value was 64 bit wide.

I don't know if this has been already fixed in Ubuntu but it's already fixed in the Hal Git:
[http://gitweb.freedesktop.org/?p=hal.git;a=commit;h=f7d7779d0fd2438479c9de4b8dd76f986941f0a4](http://gitweb.freedesktop.org/?p=hal.git;a=commit;h=f7d7779d0fd2438479c9de4b8dd76f986941f0a4)

With this fix the device should work. However, I think we will need to wait for a new release of HAL.

Cheers,
RKTesser

---

### Post by valmorel on 2008-09-15
The bug fix in Hal that I posted the link for will work for Walkman series intended to work as mass storage or MTP using Media player. I have mine set up this way and using Gnomad I can transfrer music under the MTP protocol. Gnomad auto-detects it, and can even create playlists on it. It also auto-mounts as a mass storage device, placing an icon on the desktop. Using mass storage protocol allows me to use Gpodder for my podcast management as Gpodder does not yet speak MTP. Using the two different protocols at once causes no problems to the player.
The earlier Sonic Stage specific devices I dont know about.

edit: I have the NWZ-S515 and NWZ-S616F

---

### Post by vs8 on 2008-09-17
This is a problem related to the 32 bit Ubuntu, I've Installed Ubuntu x86_64 and it auto mounts the device. I've done this on two computers, my new PC and my girlfriend's laptop.

For some reason the 64 bit edition is better than the 32 bit version. At least for me it works way better.

---

### Post by rktesser on 2008-10-12
@valmorel:
OK! I've been confused because you cited the UMS protocol instead of the MTP. 
However, I will wait for the new HAL version, which has already been fixed!
Thanks!

@vs8:
Yes! I already said in my previous post that there was no problem in 64 bit versions of HAL.:)
However, I need my version to be 32 bit for work related reasons.

---

### Post by valmorel on 2008-10-13
Yes, it can get a bit confusing. Let me put it this way: with the updated HAL, the Walkman will mount as BOTH mass storage, AND mtp. You just use the appropriate program to access it, say Gnomad2 or Amarok for MTP, or your file manager or maybe Exaile if you want drag and drop.
FYI, this bug is fixed in 64 bit Ubuntu, and does not exist in Puppy Linux or Dreamlinux. Dont know about Fedora or Suse.

---

