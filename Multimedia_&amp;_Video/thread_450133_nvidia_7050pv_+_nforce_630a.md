---
title: "nvidia 7050pv + nforce 630a"
date: 2007-05-21
forum: Multimedia &amp; Video
---

### Post by baekster on 2007-05-21
does anyone have it?  does it even work on ubuntu?  let me know if anyone got it to work.

---

### Post by vikramsharma on 2007-05-21
> **baekster said:**
> does anyone have it?  does it even work on ubuntu?  let me know if anyone got it to work.
 
I don't have the Nvidia card, but have you tried using the "Restricted Drivers Manager".  In case you haven't, "Restricted Drivers Manager" can be found in System->Administration_>Restricted Drivers Manager.  Hope this helps.

---

### Post by baekster on 2007-05-21
Well...actually I don't have the board yet...trying to make some purchase decisions.  :)  If there is a driver for it somewhere, I won't have any problem using modprobe and /etc/modules and /etc/X11/xorg.conf and such to get it working...

---

### Post by penquissciguy on 2007-05-21
I just put together my new system using the Biostar TForce 7050PV board.  I'm running feisty on it with a few issues.  I haven't managed to get the nvidia driver configured correctly yet.  I installed the nvidia closed-source driver using the restricted drivers manager and rebooted, but the system locks at a blank screen during bootup.  I switched back to the vesa driver for now.  The ethernet onboard is working fine, as is the one PATA channel (haven't got any SATA drives installed yet).  I think this board will work out nicely once I figure out how to iron out the wrinkles.

Ken

---

### Post by penquissciguy on 2007-05-30
> **penquissciguy said:**
> I just put together my new system using the Biostar TForce 7050PV board.  I'm running feisty on it with a few issues.  I haven't managed to get the nvidia driver configured correctly yet.  I installed the nvidia closed-source driver using the restricted drivers manager and rebooted, but the system locks at a blank screen during bootup.  I switched back to the vesa driver for now.  The ethernet onboard is working fine, as is the one PATA channel (haven't got any SATA drives installed yet).  I think this board will work out nicely once I figure out how to iron out the wrinkles.

Ken

After a conversation at nvnews with an nvidia employee, I now know that the 7050pv is not yet supported in linux by the nvidia driver.  The best estimate I could get for when this support will be added was "later this summer".  

Ken

---

### Post by miguelitu on 2007-07-04
just bought the biostar tf7025-m2.

but i havent tested the gpu drivers yet, cause my ethernet is not working with ubuntu. in winxp, it worked.

anyone have a suggestion?


EDIT:

okay, find the driver for the ethernet.

working now :]

---

### Post by mtnhuck on 2007-07-13
I have been having some problems using the 7050PV. I tried installing the latest driver from nVidia but the video performance was unacceptable. I was getting nearly 40% CPU usage on a 3800+ just from moving a terminal window around.  I guess next time I should go for a motherboard that has been around for a little longer. I may try Ubuntu on this machine again but not for a bit. FYI SATA hard drives work fine but the DVD burner I got was not supported. Ethernet/audio etc all worked but I have not tried the HDMI. Cheers
Huck

---

### Post by miguelitu on 2007-07-22
well, ive installed the nvidia and seems to be working fine.

used these twos how-to:

[http://www.nvnews.net/vbulletin/showthread.php?t=94072](http://www.nvnews.net/vbulletin/showthread.php?t=94072)

[http://ubuntuforums.org/showthread.php?t=497284](http://ubuntuforums.org/showthread.php?t=497284)

---

and the ethernet driver is here(there's a readme with instructions inside)

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)

cheers o/

---

