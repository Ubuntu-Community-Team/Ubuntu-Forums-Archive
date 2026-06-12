---
title: "Will this work for a frontend and backend?"
date: 2010-01-21
forum: Mythbuntu
---

### Post by nelsonba on 2010-01-21
Just looking to capture OTA HD and operate as a DVR.

HD Homerun
[http://www.amazon.com/SiliconDust-HDHomeRun-HDHR-US-Definition-Television/dp/B0010Y414Q/ref=sr_1_1?ie=UTF8&s=pc&qid=1264134006&sr=1-1](http://www.amazon.com/SiliconDust-HDHomeRun-HDHR-US-Definition-Television/dp/B0010Y414Q/ref=sr_1_1?ie=UTF8&s=pc&qid=1264134006&sr=1-1)

Revo 1600
[]("http://ubuntuforums.org/showthread.php?t=934824&highlight=eee")[http://www.amazon.com/Acer-AspireRevo-AR1600-U910H-Desktop-Windows/dp/B002O3W44Q%3FSubscriptionId%3DAKIAJASE6HSSVXTNREYQ%26tag%3Dsmtfx1-20%26linkCode%3Dxm2%26camp%3D2025%26creative%3D165953%26creativeASIN%3DB002O3W44Q](http://www.amazon.com/Acer-AspireRevo-AR1600-U910H-Desktop-Windows/dp/B002O3W44Q%3FSubscriptionId%3DAKIAJASE6HSSVXTNREYQ%26tag%3Dsmtfx1-20%26linkCode%3Dxm2%26camp%3D2025%26creative%3D165953%26creativeASIN%3DB002O3W44Q)

Extra RAM to run VDPAU
[http://www.amazon.com/Crucial-Technology-CT12864AC800-PC2-6400-Unbuffered/dp/B001258CR0/ref=pd_sim_pc_1](http://www.amazon.com/Crucial-Technology-CT12864AC800-PC2-6400-Unbuffered/dp/B001258CR0/ref=pd_sim_pc_1)

Remote
Recommendations?

Extra storage as needed.

I would also like to be able to play flash content from Hulu/Youtube etc...  With flash 10.1 will this be possible?

Thanks!

---

### Post by zorro07 on 2010-01-22
will make a good frontend, but asking a bit much to backend as well!

even if it had the dual core atom.  better to have a beefier backend.

hope that helps

i have a asrock 330 ion system set up as a frontend its really good!

bye

---

### Post by nelsonba on 2010-01-22
[SIZE=3][FONT=Calibri]For just OTA isn’t the backend essentially just hosting files?  I thought backends could be pretty minimal.[/FONT][/SIZE]

---

### Post by LowSky on 2010-01-22
I think your confused, you think a backend is just a file server, while it doesn that function it also handles all encoding, streaming and recording. Try to do all that on a Atom based machine and your loooking for trouble.

Now you don't need a Core i7 or a core i5, but you do ned some extra juiuce if you play to multitask. You need a processor with over 2GHZ of power for HD a cheaper end dual-core would do the trick easily

take a look at this

[http://www.mythtv.org/wiki/Hardware_Requirements](http://www.mythtv.org/wiki/Hardware_Requirements)
[http://www.mythtv.org/wiki/Hardware_Requirements#Performance_issues](http://www.mythtv.org/wiki/Hardware_Requirements#Performance_issues)

playing flash wont be an issue, Im running hulu desktop  on m yPC all the time, works fine.

---

### Post by falconindy on 2010-01-22
> **nelsonba said:**
> Extra RAM to run VDPAU
[http://www.amazon.com/Crucial-Technology-CT12864AC800-PC2-6400-Unbuffered/dp/B001258CR0/ref=pd_sim_pc_1](http://www.amazon.com/Crucial-Technology-CT12864AC800-PC2-6400-Unbuffered/dp/B001258CR0/ref=pd_sim_pc_1)
RAM is irrelevant when talking about VDPAU. The whole point of it is that you're passing off jobs to your GPU that your CPU would normally be doing (mainly decoding). Adding more RAM to your system will have zero effect.

---

### Post by nelsonba on 2010-01-22
> **LowSky said:**
> I think your confused, you think a backend is just a file server, while it doesn that function it also handles all encoding, streaming and recording. Try to do all that on a Atom based machine and your loooking for trouble.
 
Now you don't need a Core i7 or a core i5, but you do ned some extra juiuce if you play to multitask. You need a processor with over 2GHZ of power for HD a cheaper end dual-core would do the trick easily
 
take a look at this
 
[http://www.mythtv.org/wiki/Hardware_Requirements](http://www.mythtv.org/wiki/Hardware_Requirements)
[http://www.mythtv.org/wiki/Hardware_Requirements#Performance_issues](http://www.mythtv.org/wiki/Hardware_Requirements#Performance_issues)
 
playing flash wont be an issue, Im running hulu desktop on m yPC all the time, works fine.
 
[SIZE=3][FONT=Calibri]What if I’m just doing OTA capture without encoding anything?  (Leaving it as MPEG2) Wouldn’t it just be copying the data to a disk?  Does that use up a lot of resources?[/FONT][/SIZE]

---

### Post by sk8er3810 on 2010-01-22
@LowSky
> playing flash wont be an issue, Im running hulu desktop on m yPC all the time, works fine. 

What CPU? What resolution? Fullscreen?  Hulu in windowed mode appears to be watchable;  I am unable to play Hulu full screen.  Even on my Athlon 64 2.4Ghz Flash performance sucks.

As for Flash 10.1
[http://ubuntuforums.org/showthread.php?t=1387164](http://ubuntuforums.org/showthread.php?t=1387164)

---

### Post by LowSky on 2010-01-22
Phenom x4 B50 (aka Phenom x2 550 unlocked cores.) @ 3.1Ghz.

Resolution is 1366×768 on a 37" LCD. Playback can be a bit rough during high movement scenes but is generely watchable

On a Atom based machine running high def will be an issue, becaus eit really can't, but Hulu can be set to lower definitions to help playback.

---

### Post by nelsonba on 2010-01-22
How about something like this?  My house is set up so I could put this in a storage room, run HDMI through the wall to the TV and use an RF remote to control it.

[http://microcenter.com/single_product_results.phtml?product_id=0326277](http://microcenter.com/single_product_results.phtml?product_id=0326277)

Can I get away with recording two HD shows at once while playing back another?

How about accessing this from another TV using the Nevo 1600 as a frontend?

Could I watch two shows (one on each TV) while recording two shows?

---

### Post by williammanda on 2010-01-22
> **nelsonba said:**
> How about something like this?  My house is set up so I could put this in a storage room, run HDMI through the wall to the TV and use an RF remote to control it.

[http://microcenter.com/single_product_results.phtml?product_id=0326277](http://microcenter.com/single_product_results.phtml?product_id=0326277)

1. Can I get away with recording two HD shows at once while playing back another?

2. How about accessing this from another TV using the Nevo 1600 as a frontend?

3. Could I watch two shows (one on each TV) while recording two shows?

1. Yes you can with the homerun or any dual tuner or multiple single tuners.
2. Yes you can.
3. Yes you can. You can watch tv on any frontend, no matter how many.
The key here is that you need a backend that will do all this. You will need at a minimum for a backend a core 2 duo and the memory (at least 2GB) and a large enough hard drive (I use a TB drive) to do this. You need to think of this in this way. The backend is the manager and the frontends are the employees. The backend is doing several things at once and the frontend is only doing one task. Hope this helps!

---

### Post by nelsonba on 2010-01-22
I realize that 320GB doesn't get me very far, but I can always add storage.  The pc I linked to in my previous post has a dual core 2.4 GHz Athlon 64 X2.  Is it important to have a Core 2 Duo instead?  I could always build something, but it doesn't seem like I'd save much money given the clearance/refurb/used deals that are out there.  This seemed like a pretty good bang for the buck deal if it's enough to accomplish what I'm trying to do.

---

### Post by williammanda on 2010-01-22
The point is for you to have a adequate backend. You need to determine that. I have a core 2 quad 9300 and 4 GB ram for a backend and several frontends. Ypu need to determine what you need,

---

