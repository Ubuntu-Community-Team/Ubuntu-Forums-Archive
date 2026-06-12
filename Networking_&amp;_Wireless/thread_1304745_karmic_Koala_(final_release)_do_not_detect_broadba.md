---
title: "karmic Koala (final release) do not detect broadband usb 3g mobile modem"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by hetx on 2009-10-29
Check if you have the right kernel booted. In a terminal type "uname -r". It should say 2.6.31-14-generic

If not, your menu.lst was not updated properly. This thread will help you with this.

[http://ubuntuforums.org/showthread.php?t=1304704](http://ubuntuforums.org/showthread.php?t=1304704)

---

### Post by dj-toonz on 2009-10-29
3g modems don't work at all in karmic, that's a bummer I know, I'm trying to find a way to remove Karmic from the system & resize Jaunty to use the whole laptop hard drive as I can't undate Karmic because I only have a 3G dongle, there's loads of bug reports about this and it still ain't fixed :(

2.6.31-14-generic is the only kernel the final release comes with, when it was 2.6.31-9 it was working in the beta & RC version but screwed up in newer kernels (if your only using a 3g modem for connection) how can you update the system, You can't. i'm staying with using Jaunty on the laptop till the problem has been sorted out, not going to boot into karmic as I can't even update it

---

### Post by dj-toonz on 2009-10-29
I've got mine working (posting this in Karmic right now) :-), here's how I got mine working. YMMV


right mouse click & use safety remove hardware on the virtual drive  

Then open up a console & type in the below
sudo rmmod usb-storage
sudo modprobe -r option
sudo modprobe -r usbserial
sudo modprobe usbserial vendor=0x12d1 product=0x1001
sudo pppd ttyUSB0

check network-manager & the connection should be there then

---

### Post by John Bean on 2009-10-29
> **wilbuntu said:**
> This was already reported some days before Karmic was launched but nobody managed or were able to get it fixed up to release date. 

That was my understanding as well, but I just booted a live CD of Karmic and I'm typing this message over a Vodafone 3G connection that works just fine. More to the point, the system can see the fake CD drive and MMC slot in the Huwei dongle as well - which is more than can be said of Jaunty.

I think I may just install this properly and investigate, there's more to this than meets the eye.

---

### Post by dj-toonz on 2009-10-30
> **wilbuntu said:**
> Solution #4 may depend on each hardware specification. It's better to collect more information before give it a try. I'll keep in touch.

I've tried it on 5 of the Huwei 3G HSDPA modems and worked on every 1 i tried it with, was a reboot before trying them. tried it from the white egg shaped E220  1 all the way up to a E169

---

### Post by dj-toonz on 2009-10-30
> **wilbuntu said:**
> Are you using a new install of Karmic Koala, the final release? 
Solution #4 do not work for new installs of Ubuntu 9.10 final release.


yep, downloaded yesterday  & put onto a laptop with no other connection i.e wireless, cable & using the connection now a huewi HSDPA vodafone connection & working grand with the way I did it 


Read the other post I've wrote, it's fully in there i'll give you the link

[http://ubuntuforums.org/showthread.php?t=1304717](http://ubuntuforums.org/showthread.php?t=1304717)

---

### Post by John Read on 2009-11-16
Assuming you have installed your Vodaphone (Australia) wireless broadband modem via the Network Manager and are able to get it to "connect" but are still unable to actually connect to any Web sites, etc. then chances are you still have one small step to go. Right-click the Network Manager icon, choose Edit Connections, click the Mobile Broadband tab, click your Vodaphone service (e.g. Vodafone Postpaid), click the Edit button on the right, leave Number set to *99#, set the Username to vodafone, set the password to vodafone, leave APN set to vfinternet, and click the Apply button. You will be asked if it's OK to store some keys on a keyring, choose "At any time" (or somesuch), then you're set.

I find the connection speed I can achieve in Ubuntu 9.10 is several times faster than I could achieve in Ubuntu 9.04 which is just great.

The only hassle I have is that Ubuntu boots so fast that the modem does not have time to find the Vodafone connection and then it won't appear in the Network Manager list. You then have to cold boot again and hope for better luck next time.

Hope this helps.

Regards,

John

---

### Post by j1nn on 2010-01-09
*bump*
i cannot believe it has not been solved.. tell me there is a solution, please!

---

