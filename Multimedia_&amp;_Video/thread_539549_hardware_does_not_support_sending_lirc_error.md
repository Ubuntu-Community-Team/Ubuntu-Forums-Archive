---
title: "hardware does not support sending lirc error"
date: 2007-08-31
forum: Multimedia &amp; Video
---

### Post by awesomo on 2007-08-31
Hi all,

So I followed the guide on installing and configuring lirc, and am running into problems. When I use the command```
irsend SEND_ONCE blaster POWEROFF
``` i get the following message ```
irsend: command failed: SEND_ONCE blaster POWEROFF
irsend: hardware does not support sending

```

The only part of the guide that I didn't follow is the hardware.conf file; instead of MODULES="lirc_pvr150" I used MODULES="lirc_i2c". When I loaded the pvr150 module I got an error message saying ```
cannot find remote "blaster"
```. For inforamtion's sake I am using the hauppauge wintv pvr 150 with the on card irblaster.

---

### Post by awesomo on 2007-08-31
Alright, so after playing around and searching the internet I have a few questions. IF I need to use my ir blaster to change channels, which module should I load i2c or pvr150?

---

### Post by dannyboy79 on 2007-09-27
can anyone answer this, I too am having this issue trying to change channels for a sa3250hd because I can't get either the internal channel changer over firewire to work nor the external channel changing script. so the last resort is serial ir blasting and I can't even get this working. All I want to be able to do is use my pvr-350 and record the s-video output frmo the STB to the s-video input on the pvr-350. Please help. I am using Feisty and followed the fesity lirc guide.

---

### Post by RoyalPro on 2007-10-15
> **awesomo said:**
> Hi all,

The only part of the guide that I didn't follow is the hardware.conf file; instead of MODULES="lirc_pvr150" I used MODULES="lirc_i2c". When I loaded the pvr150 module I got an error message saying ```
cannot find remote "blaster"
```. For inforamtion's sake I am using the hauppauge wintv pvr 150 with the on card irblaster.

I am having the same problem as you about it not supporting sending and I am about to make my MODULES="lirc_dev lirc_i2c" look like this MODULES="lirc_dev lirc_i2c lirc_pvr150".
About the part of your problem after you changed it to just "lirc_pvr150" and getting the no remote error.  Did you add anything like this to your /etc/lircd.conf & /etc/lirc/lircd.conf (for some reason I have 2?)```
begin remote

  name          blaster
  bits          32
  flags         RAW_CODES
  eps           0
  aeps          0
  plead         0
  gap           333333
  repeat_bit    0
  begin raw_codes
  name RED
  1048586
 end raw_codes
end remote

```

The below is a message I posted to another forum.
I am using Ubuntu  Gutsy kernel version 2.6.22-14-generic.  I have lirc-0.8.3-CVS-pvr150.tar.bz2 installed (I think).  I had to install the Ubuntu version first then the 8.3 version to get the remote to work.  I have the firmware haup-ir-blaster.bin in /lib/firmware/2.6.22-14-generic.  I have add to my lircd.conf
 begin remote:
  name          blaster
  bits          32
  flags         RAW_CODES
  eps           0
  aeps          0
  plead         0
  gap           333333
  repeat_bit    0
  begin raw_codes
  name RED
  1048586
 end raw_codes
end remote
When I try and test it with irsend,I get the errors below.

eric@umc:~$ irsend SEND_ONCE blaster RED
irsend: command failed: SEND_ONCE blaster RED
irsend: hardware does not support sending

eric@umc:~$ irsend SEND_ONCE blaster POWER
irsend: command failed: SEND_ONCE blaster POWER
irsend: hardware does not support sending

Any help would be great and if you need any more info let me know.

---

### Post by RoyalPro on 2007-10-15
After changing to MODULES="lirc_dev lirc_i2c lirc_pvr150" my remote stopped working even as it did before.  I then tried with MODULES="lirc_i2c lirc_pvr150" and still nothing. Then I tried MODULES="lirc_pvr150 lirc_i2c" to see if the order had anything to do with it it and it does.  Now my remote works like it used to and the light on the blaster is now flashing when I do a ```
eric@umc:~$ irsend SEND_ONCE blaster RED
``` with no errors.
I don't have it changing anything on my General Instruments cable box yet because it has a huge list of codes to go though manually and I hope that one of them works but so far so good.  Gave me a much hope that it will be working today.

---

