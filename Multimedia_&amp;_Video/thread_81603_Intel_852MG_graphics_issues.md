---
title: "Intel 852MG graphics issues"
date: 2005-10-24
forum: Multimedia &amp; Video
---

### Post by whitty on 2005-10-24
First of all, i'd like to say hi, my name is Alex!

I'm extremely happy right now because i just set up my laptop to dual-boot successfully, and wireless worked out of the box!

Unfortunately though, even after reconfiguring X server (it didn't work at all to begin with) I can't seem to hit a graphics mode of 1024x768. This is my laptop's native res, and i'll just about die for extended periods of 800x600. Unfortunately, I think the reason x didn't work to begin with was that it wasn't allowed to use 8x6 or 6x4 modes, and 10x7 just didn't work.

Perhaps a graphics driver update will help, but i'm too new to linux to even know how to do that! Any guidance as to how to do this or perhaps an alternate cause would be extremely appriciated:) 

System info:
Gateway 400VTX notebook
Intel 852MG graphics chipset
Ubuntu 5.10

Support page (for more info):
[http://support.gateway.com/s/Mobile/Gateway/400VTX/3501331sp47.shtml](http://support.gateway.com/s/Mobile/Gateway/400VTX/3501331sp47.shtml)

Thanks a lot!

p.s. I used the search, and couldn't find anything such as this, sorry if it exists. Also, if you need any further info straight off the system, I'd love to inform you, but i'll probably need to be told how. Thanks, Alex!

---

### Post by whitty on 2005-10-25
UPDATE: Sorry to be a bother, but after a bunch of searching I found out that since I own a gateway, i'm just screwed. Last time I buy one of these $@^!bricks.

---

### Post by genti on 2006-08-23
You are not alone man.

I have the same problem.

When I try #915resolution -f /etc/default/915resolution
I get a "Bus error"
This is not mentioned anywhere.

I asked once Gateway for the max supported CPU in the motherboard. I am not 100% sure but the reply I got was about adding more ram and maximum storage...
Not cool Gateway not cool...

---

### Post by whitty on 2006-08-24
not to perpetuatea thread revival, but yeah. Nothing i could do to that thing worked. Lo and behold the power regulation circuitry in it just went kaput in april and I had to get a new laptop. What did i get? a gateway. WOO WOOO! This thing's a friggen powerhouse though - ati M.X600w/256MB, athlon 64 4000+, gig of ram. This time around there was no room for gateway to screw it up, it's all third party super duper components. Luckily this one runs ubuntu flawlessly. Wireless was odd, but i worked it out. It's an MX7525 btw.

---

### Post by omegac on 2007-07-18
> **whitty said:**
> not to perpetuatea thread revival, but yeah. Nothing i could do to that thing worked. Lo and behold the power regulation circuitry in it just went kaput in april and I had to get a new laptop. What did i get? a gateway. WOO WOOO! This thing's a friggen powerhouse though - ati M.X600w/256MB, athlon 64 4000+, gig of ram. This time around there was no room for gateway to screw it up, it's all third party super duper components. Luckily this one runs ubuntu flawlessly. Wireless was odd, but i worked it out. It's an MX7525 btw.

What is the method for getting my wireless on my Gateway mx7525 to turn on so that i can get the driver to load. I also found that my dvd/cd led on the front panel doesnt indicate any more but the HDD led still does, how about the one on your MX7525? 

Are you able to talk with Gateway about the linux issues? 


Keep IT free. :) :guitar: :)

---

### Post by whitty on 2007-07-19
Actually, that still happens sometimes on my laptop. Assuming you're using the bcm43xx drivers instead of ndiswrapper, your best bet is to try

sudo rmmod bcm43xx
sudo modprobe bcm43xx

a lot. A lot of times if I have an issue, that will work it out. Also, use the hardware button (Fn-F2) to turn the card on or off - if it's off, and Fn-F2 doesn't durn it on, rmmod it or modprobe it and see if it works then.

Post back if that doesn't really help.

---

### Post by genti on 2007-07-19
Gateway will never listen to Linux questions and for that reason I am not getting any computers from them.

This thread is not about wireless, to get wireless working, you can try to load a native driver depending on the chip, or use ndiswrapper.

---

