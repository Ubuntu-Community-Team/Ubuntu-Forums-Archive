---
title: "Avermedia avertv volar black hd"
date: 2009-06-10
forum: Multimedia Software
---

### Post by huskerdu on 2009-06-10
Hi, i get this tv-tuner and i can't make it work properly.

The exactly model is this:

[http://www.avermedia.com/avertv/Product/ProductDetail.aspx?Id=460&device=2](http://www.avermedia.com/avertv/Product/ProductDetail.aspx?Id=460&device=2)

This is the lsusb output:

```

Bus 002 Device 002: ID 07ca:850a AVerMedia Technologies, Inc.

```

And this is my kernel.log:

```

dvb-usb: found a 'AverMedia AVerTV Volar Black HD (A850)' in warm state.
dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
DVB: registering new adapter (AverMedia AVerTV Volar Black HD (A850))
af9013: firmware version:4.65.0
DVB: registering adapter 0 frontend 0 (Afatech AF9013 DVB-T)...

```

One interesting thing, is, according what i've read, that it's an af9015, not an af9013 ?

Probed almost everything, lot of firmwares, lot of mercurial repositories in linuxtv and nothing goes.

Any help, please?

---

### Post by huskerdu on 2009-06-11
Solved.

This is the how-to.

1.- Download fron linuxtv the last version.

> hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd v4l-dvb
make
sudo make install

2.- Delete (rename?) the firmware dvb-usb-af9015.fw in /lib/firmware and put this one:

> [http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/](http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/)

And watch Disney channel with me-tv. :D

---

### Post by orduek on 2009-08-06
Hi,
I bought the same usb dongle but can't make it work using your instructions.
When trying VLC it says unable to open dvb://

With mythtv it seems to recognize it but finding no channels.
after installing the newest me-tv it seems I can't use it because the gtk is to old.

any suggestions?

---

### Post by sucotronic on 2009-08-25
Thank you **huskerdu** the instructions worked for me. Now I've to find wich program is the best suitable for this card.

---

### Post by sucotronic on 2009-10-26
Finally the program I've found more comfortable is Kaffeine:

[[IMG]http://img39.imageshack.us/img39/4821/pantallazo5telecincorep.th.png[/IMG]](http://img39.imageshack.us/i/pantallazo5telecincorep.png/)

---

### Post by Eisdiele on 2009-11-05
Hey,
since updating the kernel the tv-stick doesn't work anymore. Do you have the same problem, or is there a new firmware anywhere? My actual kernel is 2.6.31 so would be nice to know if I changed anything else or if it's no more supported...

Thanks a lot
Fabian

btw thanks again to huskerdu until now it worked really fine..

---

### Post by sucotronic on 2009-11-28
Hello Eisdiele, I've now Ubuntu 9.10 Karmic with kernel 2.6.31-14-generic and the tuner works out-of-the-box with the firwmare installed through the "Hardware controllers" app

---

### Post by SiNDAKiT on 2012-06-02
Just wanted to say this is an old topic but it helped my out :)

Thanks huskerdu

---

### Post by nothingspecial on 2012-06-02
[IMG]http://img696.imageshack.us/img696/7058/necrov.png[/IMG]

---

