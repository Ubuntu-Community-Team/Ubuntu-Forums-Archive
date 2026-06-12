---
title: "Telkomsel Flash USB modem not working on Ubuntu 12.04"
date: 2012-07-22
forum: Networking &amp; Wireless
---

### Post by michael2009 on 2012-07-22
I have a Sony Vaio laptop model VGN-FS115Z running a dual-boot system with Windows XP Pro SP3 and Ubuntu 12.04. Both systems have full wireless connectivity and display local wireless networks in range. However, the problem I have is with a Telkomsel Flash wireless USB dongle that works with Windows but not with Ubuntu. The dongle includes setup and installation files, and I know that the install file is an .exe file, which only works with Windows in my experience.

I am currently in Indonesia, and the Telkomsel USB is an Indonesian product, so I am hoping some Ubuntu users in Indonesia have a workaround for this issue. Any help is greatly appreciated :)

---

### Post by barakatax on 2012-08-01
Hi,

Follow the step here: 
 [FONT=&quot][http://ubuntuforums.org/showthread.php?t=1969322&page=2](http://ubuntuforums.org/showthread.php?t=1969322&page=2) [/FONT]
  
I am also using Telkomsel Flash with Prolink PHS-301 USB Modem.
Luckily, the ID vendor and ID product same with the tutorial
([FONT=&quot]vendor=0x1c9e product=0×9605)[/FONT].
So, just copy and paste the commands then it works!



Cheers ...

---

### Post by michael2009 on 2012-08-04
Thanks Barakatax, it great to get a reply:)

I entered all the commands, changing the device id, and it seemed to complete in the terminal, including the gedit prompts. However, the computer is still not finding or connecting to the network. I haven't tried unplugging then replugging the usb modem yet. 

I closed the terminal window after completing the commands, although I was warned that the terminal was still running the operation. Does this mean I need to enter all the scripts again next time I want to try to connect?

---

### Post by anoe on 2012-08-21
Hi, i am right now in Bali, and yesterday i got a Telkomsel Flash High Speed Wireless Broadban usb modem. I brought my notebook (asus eee pc901) to the shop to be sure the modem i'd got would work well with my ubuntu 12.04. In the beggining it connected but it was really slow. Then they did something to the card or the modem (they said the umts was not activated, or st like that) and now it's working smoothly.

So what we did is connect the device, add a new mobile broadband connection, select indonesia, telkomsel, and the plan we selected was based on volume.

with that it is working for me with no problems (except the filtering to certain webs that i guess they are forbidden here in indonesia).

xxx

---

