---
title: "HowTo: Stable use of open source bcm43xx modules"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by darkshadow on 2006-06-03
I have figured out how to get the network card to associate with the ap every time which after reading these forums for a month I know alot of people will like this.

My setup is specify everything in the basic network-admin (seriously should allow more advanced settings) then on a clean boot the output of iwconfig should be fine except:
1: The Bit Rate is 11M to fix this just manually run the command
iwconfig $IFACE rate 54M
* only if you want g speeds

2: the Access Point is invalid to fix it just run this command and it will immediatly associate and your network connection will work perfect
iwlist $IFACE scan

Just add those into the init scripts (I used /etc/rc.local) and your network will work at every boot.

---

### Post by towy71 on 2006-06-03
thank you very much  for this, an  elegant solution to a sticky problem :lol:
perhaps the  mods  could make it a sticky ;)

---

### Post by mike_m on 2006-06-03
thanks for the tip, how can i edit my file as root?
(loging is as other user don't work & I just got done setting up as auto login, so I was hopeing to edit from the terminal)

Thanks

---

### Post by Patsoe on 2006-06-03
[QUOTE=mike_m]thanks for the tip, how can i edit my file as root?[/QUOTE]

I think "sudo nano <filename>" in the terminal is what you're looking for. Good luck :)

---

### Post by mike_m on 2006-06-03
thanks, nano worked
but "iwlist $IFACE scan" didn't for me with SMC wifi card.
o-well worth a try :)

---

### Post by Silver-revo on 2006-06-03
So should I do this from a completly CLEAN install or should I take other steps before this?

If there is something I should do please  help me, a week of this is enough.
I assuming at the very least I should get the Firmware again correct?
Also are getting this to work with network manager or how do you select which network you wish to log into. My main purpose for wifi is school where I will rarely know the router or access point info how do you determine which network you want, something like the windows network manager?

---

### Post by toorima on 2006-06-03
Network manager won't connect with rate 54M, just times out, when i try again it connects but with rate 11M. Anyone got it working with 54M and network manager?
btw /etc/rc.local didn't work for me but /etc/init.d/rc.local sets it to rate 54M at boot, but what does that help when network manager won't work with it :(
Don't want to use ndiswrapper but 11M is no fun...

edit: got it to work with 36M which is good enough

---

### Post by mike_m on 2006-06-04
Update! 
Everyone might find this instersing....
today I downloaded Xubuntu 6.06 & installed on a spare HD & on boot the network started right up, Right "out of the box"
Ubuntu 5.10 didn't work that good & even though I upgraded to Ubuntu 6.06 my network wouldn't start auto.

Wonder if a fresh download / install of Ubuntu 6.06 would work "out of the box"?
Maybe I'll try & post back, but first I'll poke around on this Xubuntu 6.06,
seams to run faster on my old Dell :)

---

### Post by Patsoe on 2006-06-05
[QUOTE=Silver-revo]
I assuming at the very least I should get the Firmware again correct?
Also are getting this to work with network manager or how do you select which network you wish to log into. [/QUOTE]
Yes, you'll still need to get the firmware. I didn't get it to work with NetworkManager though - maybe because of WPA issues - but I did get NetworkManager to work with the ndiswrapper driver.

[QUOTE=mike_m]Update! 
Everyone might find this instersing....
today I downloaded Xubuntu 6.06 & installed on a spare HD & on boot the network started right up, Right "out of the box"
[/QUOTE]
Just to add: as you mention it in your signature, this applies to an SMC card I presume? Very happy it's working for you ofcourse, just thought I'd clarify this, since you're posting in a bcm43xx (=Broadcom, not SMC) topic. :)

---

### Post by toorima on 2006-06-05
Thanks to various posts on this forum i now have my broadcom card working with the bcm43xx driver.
WPA works perfectly.
Network manager handles my connections
Speed is only 36 mbit/s but i can live with that.

To get wpa to work create /etc/default/wpasupplicant and put ENABLED=0 in it

---

### Post by shorty0927 on 2006-06-05
I haven't had an occasion to edit a script before...all I know is that it looks a whole lot more complicated than a plain old config file.  Should we type these things in EXACTLY as you have them in your post?  Do we substitute "eth0" for $IFACE or do we put in another line to define our wireless interface elsewhere?

---

### Post by towy71 on 2006-06-11
Still think this should be a sticky

---

### Post by darkshadow on 2006-06-11
shorty0927 yes you should substitute.
I have over time noticed that this does not always work but it has drastically improved the number of successful associations.

---

