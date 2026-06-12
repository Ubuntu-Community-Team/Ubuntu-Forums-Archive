---
title: "Mythbuntu and WinTV-HVR-1800"
date: 2013-11-01
forum: Mythbuntu
---

### Post by shiman6 on 2013-11-01
I've tried to use this TV card back on linux kernel 2, i believe on ubuntu 10.04, but it was such a hassle i gave up and just used Windows 7. 

Now that it's been a few years, and everything's updated and changed quite a bit, would it be easier getting this card to work on the new kernel and ubuntu versions? how would i go about getting this card to work with mythbuntu, complicated or not?

---

### Post by agamotto on 2013-12-05
Yes, the 1800 is much easier to use now.  I have been using one sucessfully for at least 3 years now.  Install Mythbuntu 12.x, and it should auto-detect for you.

---

### Post by shiman6 on 2014-02-06
How did you get yours to work? I'm hitting a brick wall with MythTV, it wont even see it.

---

### Post by tuat2 on 2014-02-07
I no longer use this card, but referring to this page [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1800](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1800) you might need to compile the driver and download the firmware if it doesn't run out of the box.

From experience, I can tell, that it's mostly the firmware. Like for my WinTV Nova HD S2, Ubuntu ships a firmware, which is either broken or only works with another revisioin of the card. So I'd try to install the firmware first.

---

### Post by shiman6 on 2014-02-07
I have all the drivers available, however for some reason V4L DVB isnt an option on Mythtv setup, and that's the only way i know how to get it to work.

---

### Post by tuat2 on 2014-02-07
Are you able to use the card with another application? Did you check the related log output using dmesg?

---

### Post by shiman6 on 2014-02-07
Dmesg reports no errors, VLC says permission error for some reason. I have yet to try tvtime, but i dont want to load too many graphical apps onto the system as it's an ubuntu server install.

---

### Post by tuat2 on 2014-02-07
No idea what causes the permission error here... But there is "apt-get purge" to get rid of those apps after testing. ;)

My next step would be to check the output of "dmesg | grep -i dvb" and whether there is a device in "/dev/dvb/". But I never had a permission issue. :(

And I'd check "lsmod" whether the (I believe) cx23885 driver is loaded.

---

### Post by waterhead on 2014-02-15
Check to see if it is uploading the firmware, with this command:

```
dmesg | grep firmware
```

---

### Post by agamotto on 2014-02-20
> **shiman6 said:**
> I have all the drivers available, however for some reason V4L DVB isnt an option on Mythtv setup, and that's the only way i know how to get it to work.

You shouldn't need V4L DVB for it at all.  I am running Mythbuntu 12.04.3, mythtv libs v27, and it comes up as an ATSC DVB card in the capture card setup.  Perhaps if you change your repositories to v27(which is the current), some of these problems with settle out.  It will also help in the setup if you turn off the EIT scan in the three boxes asking about SEQ header timeouts and such.

---

### Post by waterhead on 2014-02-20
> **shiman6 said:**
> I have all the drivers available, however for some reason V4L DVB isnt an option on Mythtv setup, and that's the only way i know how to get it to work.

V4L is for SD (Standard Definition) analog video tuners, and DVB is is for digital tuners (HD). Your card could have both, but they are set up seperately.

> **agamotto said:**
> You shouldn't need V4L DVB for it at all.  I am running Mythbuntu 12.04.3, mythtv libs v27, and it comes up as an ATSC DVB card in the capture card setup.  Perhaps if you change your repositories to v27(which is the current), some of these problems with settle out.  It will also help in the setup if you turn off the EIT scan in the three boxes asking about SEQ header timeouts and such.

The version of MythTV should make no difference in the tuner working. The EIT is needed if you are receiving OTA broadcasts, and want the OTA schedule information.

For the analog, you should have a device node named /dev/video0.

For the digital, you should have /dev/dvb/adapter0

If these are not present, the card is not being initialized. Please post the output of dmesg that I had asked for (if you are still following this thread).

---

