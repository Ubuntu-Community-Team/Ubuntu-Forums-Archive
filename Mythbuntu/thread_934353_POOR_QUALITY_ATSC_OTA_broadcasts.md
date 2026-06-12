---
title: "POOR QUALITY ATSC OTA broadcasts"
date: 2008-09-30
forum: Mythbuntu
---

### Post by stevecartermo on 2008-09-30
Hello .. I am using Mythbuntu 8.04 and a Pinnacle ATSC HDTV USB tuner.

When the system is working well I would watch commercials in HD, but ... My reception here in Toronto varies.. with the signal level of various stations fluctuating between 0 and over 60 %. When the signal is strong the recordings are great and worth watching, If the signal is less than around 50% the program will have alot of sound and image dropouts and the myth frontend can even freeze while watching it. Anyone have a way to tell MYTHTV not to record if the signal level is below a threshold, or is there a way of testing a recording ... short of watching it for any quality problems.

Thanks

Steve

---

### Post by novellahub on 2008-09-30
I believe you can use live tv to tune to a channel and use the either F7 or ALT-F7 (I am going from memory) to bring up the signal strength meter.  Then adjust your antenna to get better reception.

---

### Post by stevecartermo on 2008-09-30
Thanks for the idea ... but my reception strength varies throughout the day. It isually stronger at night than during the day. I was looking for a way that mythtv could check the signal strength before it starts recording.

---

### Post by agamotto on 2008-09-30
> **stevecartermo said:**
> Hello .. I am using Mythbuntu 8.04 and a Pinnacle ATSC HDTV USB tuner.

When the system is working well I would watch commercials in HD, but ... My reception here in Toronto varies.. with the signal level of various stations fluctuating between 0 and over 60 %. When the signal is strong the recordings are great and worth watching, If the signal is less than around 50% the program will have alot of sound and image dropouts and the myth frontend can even freeze while watching it. Anyone have a way to tell MYTHTV not to record if the signal level is below a threshold, or is there a way of testing a recording ... short of watching it for any quality problems.

     Nope, unfortunately you have discovered the big problem with digital... all or nothing signal.  Where I live, I had to get an amplified antenna designed for 65mi range to keep the channels within 20mi tuned in with a stable lock.  Otherwise, I would have the same problem you are having now.

I don't know if this helps, but at least it answers part of your question/s.

---

### Post by foxbuntu on 2008-09-30
--OR--

If you have cable tv service you could juse use the QAM signal and avoid this all together

---

### Post by novellahub on 2008-10-01
stevecartermo -

How far away are you from the broadcast tower?  I am 27 miles from my location and use an amplified directional antenna. I am getting at least 95% signal strength from all my channels.

**[{antenna link}](http://mythic.tv/product_info.php?cPath=21_30&products_id=63&osCsid=f49d585282ba798c843bde8c1f69b19d)**

Here is a website where you can find where your broadcast towers are by entering your latitude / longitude for the Toronto area (You can find that via google maps):

**[{stations link}](http://www.2150.com/broadcast/default.asp?latitude=43%2E642500&longitude=%2D79%2E387500&magnetic_north=10%2E5&range=40&sort=channel&show_expired=False&show_construction=False&show_analog=False&show_low_power=False&action=Show+Stations)**

If you are looking for a new antenna, Monoprice.com has a few antennas as well.

**[{monoprice.com}](http://www.monoprice.com/products/subdepartment.asp?c_id=109&cp_id=10901)**

---

### Post by stevecartermo on 2008-10-01
95 % signal strength thats impressive.. I am about 30 miles from the transmitter, ... So it looks like I need a new antenna.

Thanks for your input.

---

### Post by agamotto on 2008-10-08
> **foxbuntu said:**
> --OR--

If you have cable tv service you could juse use the QAM signal and avoid this all together

You presume that the local cable company is putting the HD signals out unscrambled and/or on the same channels.  I have Mediacom in my area, and even with my Toshiba HD telly manufactured 3/08, the channels for the HD 'pass-through' change, seemingly at random.  WQPT is on 117-3 one week, 98-4 another, and one local channel even disappears on occasion.  I called Mediacom to ask about this, and the 'technical specialist' had no idea what QAM was...  I called again later, similar response.  When I told them that I want to disconnect, a service manager admitted that they have been having this problem with other customers and the only 'solution' is to rent a digital cable box for those local HD stations.

I picked up this month's Consumer Reports to find out that in the review of DTV boxes for older tvs, they mention that Comcast (I think) customers have been telling them the local HD are scrambled and the solution is to rent an HD box to watch them.

According to Consumer Reports, this just happens to be illegal.

I have already created a complaint with the FCC and the Ill. State's Attny. General, as I think this is what Mediacom is attempting to do in my area to force people into higher-cost packages.

---

### Post by dsbw on 2008-11-09
> **foxbuntu said:**
> --OR--

If you have cable tv service you could juse use the QAM signal and avoid this all together

The other presumption made is that the quality is as good. My OTA HD signals are often better than what comes over the cable.

---

### Post by non-poster on 2009-02-17
hdtvprimer.com is a great site for OTA/antenna info.  You might just need to spend a few bucks on some RG6 and a directional antenna.

---

### Post by Caps18 on 2009-02-17
avsforums would have information on your local area channels.  But, I agree with the directional antenna idea.  And there are a few good home-made antenna designs out there that would help you pick up stations from far away.  Try to make the RG6 cable as short as possible, but still getting the best line of site to the tower.  

Or, in my case, just moving the antenna 1 foot to the left made all the difference.

There are some settings in MythTV (mythbuntu 7.10) that let you set a minimum signal strength threshold to record as well.  But, you never want it to miss a show.

Weather (including clouds) can effect your signal strength as well, so keep that in mind to test in various conditions.

---

### Post by allene222 on 2009-02-18
You can get one of the 7-59 antennas made for the DTV stations.  You might need a preamp if the cable is long.  Using good cable (I use RG-6)is important and no splitters unless you have an amplifier.  That said, I have used the pinnacle usb tuners and they are not very good compared to either the air2pc tuner or the hdhr one.

Some folks around here, about 30 miles from the TX recommend this one:
[http://www.amazon.com/Channel-Master-2016-Mid-range-outdoor/dp/B0018BZJNS](http://www.amazon.com/Channel-Master-2016-Mid-range-outdoor/dp/B0018BZJNS)



Allen

---

