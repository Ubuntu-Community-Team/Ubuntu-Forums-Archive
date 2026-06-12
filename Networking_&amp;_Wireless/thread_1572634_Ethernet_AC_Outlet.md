---
title: "Ethernet AC Outlet"
date: 2010-09-11
forum: Networking &amp; Wireless
---

### Post by Scott. on 2010-09-11
Since it seems that it will take a while for Linux to get reliable wireless, I've been looking at that Ethernet AC Outlet as a possible solution.  I'm  hoping it's an all hardware solution (my ethernet works fine).  However the vendors, if they list any OS at all, never list Linux.  Has anyone had any experience with these?

---

### Post by slooksterpsv on 2010-09-11
As long as there's no software to install you should be good. All it should do is transmit the ethernet information over your power-lines in your house - from point A to point B. I've been looking into getting one of these so I can run my work's ip phone out of my bedroom.

Overall, if you're still concerned, you may want to look at getting another wireless router, linking access points and connecting through said router.

---

### Post by BkkBonanza on 2010-09-11
> **Scott. said:**
> Since it seems that it will take a while for Linux to get reliable wireless

Huh? My wireless works perfectly reliably... and always has for years now. This is just a nonsense statement.

---

### Post by slooksterpsv on 2010-09-11
> **BkkBonaza said:**
> Huh? My wireless works perfectly reliably... and always has for years now. This is just a nonsense statement.

My brand new laptop, Gateway NV53 (which I bought back in February) didn't work on 9.10 - wireless kept dropping constantly. In 10.04, works flawlessly, better than Windows too.

Every computer is different, and it's not a nonsense statement, it's legit. There may not be reliable drivers for his wireless adapter, which is why he stated until Linux gets reliable wireless.

---

### Post by BkkBonanza on 2010-09-11
So he means "until HE gets reliable wireless", then because it's not "Linux" that has NO reliable wireless...

---

### Post by Scott. on 2010-09-11
> **slooksterpsv said:**
> As long as there's no software to install you should be good. All it should do is transmit the ethernet information over your power-lines in your house - from point A to point B. I've been looking into getting one of these so I can run my work's ip phone out of my bedroom.

Overall, if you're still concerned, you may want to look at getting another wireless router, linking access points and connecting through said router.
Thanks.  I do have an old 801.11b router and repeater (access point).  I may get back to you if I have trouble with it

---

### Post by Scott. on 2010-09-11
> **BkkBonaza said:**
> Huh? My wireless works perfectly reliably... and always has for years now. This is just a nonsense statement.
Tell me how.  I know a lot of folks who've had trouble getting the Broadcom (Dell) 1390 Minicard to work.  I've tried Linux drivers and Windows w/ ndiswrapper.  I also tried a NetGear WG111v3 USB.  It recognized the USB by name, but the drivers it loaded were wacked.  I was a Hardware & Software engineer for IBM for 7 years.  Unfortunately - no Linux experience, but a lot of network experience.  Do you have any idea what I might be doing wrong?

---

### Post by apmcd47 on 2010-09-11
> **Scott. said:**
> Since it seems that it will take a while for Linux to get reliable wireless, I've been looking at that Ethernet AC Outlet as a possible solution.  I'm  hoping it's an all hardware solution (my ethernet works fine).  However the vendors, if they list any OS at all, never list Linux.  Has anyone had any experience with these?

I'm using a "New Link" brand double unit set (ie two units) between my cable modem and router with no apparent problem. Looking at the manual on the CD-ROM it seems that software is only needed if more than two devices are in use.

No, I haven't connected a Linux machine directly to the adapters.

Note that it has to be connected directly to the mains. Than means
[LIST]
[*]In a socket by itself (no multi-socket adapters);
[*]Sockets used by the adapters should be on the ring, not a spur;
[*]No extension leads.
[/LIST]
It does however work in a twin-socket mains outlet.

Andrew

---

### Post by DjSesso on 2010-09-11
If you arent playing any games on the powerline adapters you will be fine. other then that its kinda slow.

I have a mini card that on my precision laptop that doesnt work well with the b43 but works perfectly on the wl driver. People just need to use the right driver.

---

### Post by Scott. on 2010-09-11
> **BkkBonaza said:**
> So he means "until HE gets reliable wireless", then because it's not "Linux" that has NO reliable wireless...
This conversation is going down a dead end.  I apologize to all those offended by my statement about Linux's wireless support.  However, please note, my situation (based on reading on this forum) I'm not the only one.  But yes, I made the statement based strictly on my experience.

---

### Post by Scott. on 2010-09-11
> **DjSesso said:**
> If you arent playing any games on the powerline adapters you will be fine. other then that its kinda slow.

I have a mini card that on my precision laptop that doesnt work well with the b43 but works perfectly on the wl driver. People just need to use the right driver.
I tried the wl driver.  No luck the first few times. Card wasn't recognized.  I'll give it another try off a clean install.  Are you using the 1390?

---

