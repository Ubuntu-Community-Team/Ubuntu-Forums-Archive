---
title: "Sharing media to the Xbox 360"
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by fuzzman54 on 2009-07-14
I know you're supposed to check around on Google and forums to try to find your answers before posting your own thread, but I can't find anything to help.

 I know there are programs out there to share to the 360, but I'm new and I can't seem to set them up properly by myself yet. I've tried Ushare but I can't get my 360 to recognize the computer when I'm running it. I think that the problem might be that I don't know what to put into the configuration file under the network connection because I'm using a laptop and using a wireless connection to my router.

 In Windows all I had to do was set Windows Media Player to share the folders and the 360 found the computer immediately. I tried just running a version of Windows Media Player under Wine but you have to add a key to the registry and I pasted they key into the Wine registry but it still didn't work.. But yeah.. Uh.. Please help! And please don't suggest any programs that aren't free or are trials because I only switched to Ubuntu because everything is free and opensource. And i'm running Jaunty if that helps.

---

### Post by junitZ on 2009-07-16
I want to send everything regarding windows to a smelly pit in hell, so... I'm trying to run my main computer @ home, along with my lovely TB of music & movies to play nice with my Xbox360 as well....

Any suggestions will be appreciated. :P

-----------

oh fuzz.... back when I was using windows, i tried winamp remote instead of WMP. it worked, kinda... but the quality decreased and the latency increased by a million!!
it seems Winamp Remote converts any type of file to one fully compatible to the 360. With a high-speed connection and a good router/config it might work properly but in my case....

---

### Post by junitZ on 2009-07-16
crap. i dunno how to delete double posts. >_<  sorry....  :(

---

### Post by fuzzman54 on 2009-07-16
I'm still looking around for a good solution to this but I'm not really finding anything. Everyone recommends TwonkyMedia Server so I tried it and it is pretty badass, but it isn't free.. It only comes with a thirty day trial, but if you want a quick-fix for now junitZ, I'd go get that.. I read in a few places that the part of the program that checks on the subscription is in "/bin/.tv" but when I look in "/bin" ".tv" isn't there..

---

### Post by PeEllAvaj on 2009-07-16
I have found ushare to work great, with the exception that you have to reboot ushare in order to update the shared file list.

I have noted that sometimes I have to run */etc/init.d/ushare start* twice.

Here are the configuration options from my installation, located at /etc/ushare.conf
USHARE_NAME=Lyra                  
USHARE_IFACE=eth1                                           
USHARE_PORT=       
USHARE_TELNET_PORT=                  
USHARE_DIR=/super/video/
USHARE_OVERRIDE_ICONV_ERR=
ENABLE_WEB=
ENABLE_TELNET=
ENABLE_XBOX=yes
ENABLE_DLNA=

---

### Post by fuzzman54 on 2009-07-17
I can't get ushare to work.. Does your 360 have the NXE? Maybe it doesn't work on that? Maybe it doesn't work from a laptop? Maybe I'm really stupid and can't do it right..

---

### Post by PeEllAvaj on 2009-07-17
My XBox does have the NXE, but it worked before that.  Let's start at the beginning, are both of the devices on the same subnet? Wireless routers sometimes separate the wireless network from the wired network.

How did you install ushare, what does it say when you run /etc/init.d/ushare start?

---

### Post by fuzzman54 on 2009-07-17
I installed it using the Synaptic Package Manager, and they're both on the same network.

---

### Post by junitZ on 2009-07-23
I'm such a noob I downloaded ushare and i dunno how to get to open it? i even tried copying/pasting some commands i've seen in this forums and i keep getting acces denied and/or error messages.

i'm not @ home,so i can't paste them here, but i will as soon as i get there...

:(

---

