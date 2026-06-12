---
title: "Avermedia Help"
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by jjasonj on 2007-11-05
I've just bought a AverTV DVB-T Volar X, which to be honest i bought from Maplins as it was half price:)

Only problem is there seems to be no drivers for it, i think the chipset is a815 but can only find the drivers for the a800


When i do dsmeg in Terminal it does list the card but i dont think its actually working.

Ive also downloaded tvtime, Kaffeine and MythTV but all seem to say "No Signal"

Any help would be great \\:D/\\:D/)

---

### Post by jjasonj on 2007-11-06
I have today recieved an e-mail from Avermedia stating as the TV card is very new they might release some drivers for it!!! Good news for anyone who might want/buy this card in the future:):guitar:

---

### Post by alkan on 2007-12-07
Hello! You know some of the drivers from the A815? In LinuxTV seems not leave anything, no?

Greetings!

---

### Post by mfraser on 2007-12-19
I purchased the AverMedia DVB-T Volar X today believing that it would work on Linux, but it turns out it doesn't. Have contacted AverMedia to see if they are any closer to releasing drivers, otherwise it means buying the older one based on the A800 chipset.

I also note that under the FAQs on Maplin's website it states:

Q) Is it linux compatible? - Arran
A) Works fine with Fedora Core 6 and Myth TV (cannot confirm any other distributions)

---

### Post by jjasonj on 2007-12-23
Hi guys, my Avermedia device is still sat in the drawer waiting for drivers:(
i wonder if anyone will ever do the drivers for the device?????

I have tried it on Mythtv believing it might have some sort of drivers but it still doesnt work

---

### Post by mfraser on 2007-12-28
I gave up with trying to get the AverTV DVB-T Volar X working with Kubuntu 7.10 so I returned it to Maplin and paid the extra £5 for a AverTV DVB-T Volar (A808 firmware) which after downloading one file ([http://www.mythtv.org/wiki/index.php/AVerTV_DVB-T_Volar](http://www.mythtv.org/wiki/index.php/AVerTV_DVB-T_Volar)) it works perfectly.:)

---

### Post by anubis1306 on 2008-01-21
Hi guys,  I thought I'd resurrect this thread because I feel as though I've got close to getting this working but need some help. Of course, I may be nowhere near getting it working...

kernel 2.6.23.14

modules:
dvb-usb-dib0700
dib7000*
dib3000*
usbcore
ehci-hcd

Place dvb-dib0700-usb-01.fw (apologies that may not be exactly correct) in /lib/firmware. Also try /lib/`uname -a | gawk '{print $3}'`/firmware if that doesn't work.

Edit /usr/src/linux-2.6.23.14/drivers/media/dvb/dvb-usb/dvb_usb_ids.h.
Replace the *_VOLAR_2 value with 0xa815.

When I plug in the stick, I get drivers registered. I should get the firmware loaded. What I actually get is:

dib0700: firmware dowload failed at 7 with -22.

I've tried changing the VOLAR line to other values. I've tried convincing the driver that it's a different DiB0700 device. None of this works. The driver reads "AverTV ... VOLAR" directly from the device. The product code is a815. The string and the value must match in order for it to try to load the firmware. Placing a different device in the if(Avermedia) part of the driver doesn't even yield the failed to download firmware message.

Sorry, the next bit is from memory and I can't remember the exact files, but they're in dvb-usb or further up in the usb chain.

The -22 comes from the error code EINVAL. It's returned by usb_bulk_msg(), which is called from dib0700_download_firmware().

ret = usb_bulk_msg(...);

if(ret < 0 ) printk(firmware failed at %d with %d, pos, ret);

usb_bulk_msg() contains the calls:

ep = (usb_pipe_in(pipe) ? udev->ep_in : udev->ep_out)[usb_pipeendpoint(pipe)];

In other words,  select the input pipeline then the endpoint of that array.
ep_in and ep_out are defined as arrays: ep_in[16], ep_out[16];

In my case, usb_pipeendpoint(pipe) returns 1. pipe is a very large but valid unsigned int. It should be expected to be large because it's created with bit shifting calls, e.g. i << 15.

if(!ep || (other condition) )
{return EINVAL;}

So, this is where the -22 originates and is because ep == NULL. I've printed out all of the ep_in[] addresses and they are not all NULL. However, selecting a different one does not change the error. The 'other condition' does not fail BTW.

This post is long enough without me posting debug. However, if anyone has any clues and thinks it will help, I'll do so.


Hope I haven't wasted my time typing all that! Cheers.

---

### Post by mike sumner on 2008-03-01
Hi guys, I bought a volar a 815 a couple weeks ago as I got the impression from the avermedia website that linux drivers were available. Apparently, they are not, for this model, but they have promised to look into it. Try emailing these guys if you are waiting for a driver:
[email]Alex.Ho@avermedia.com[/email]
[email]Betty.Cheng@avermedia.com[/email]
[email]Chris.Chen@avermedia.com[/email]

Cheers, Mike

---

