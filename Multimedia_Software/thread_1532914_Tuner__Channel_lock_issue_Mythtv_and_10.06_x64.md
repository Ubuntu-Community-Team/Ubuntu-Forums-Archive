---
title: "Tuner / Channel lock issue Mythtv and 10.06 x64"
date: 2010-07-17
forum: Multimedia Software
---

### Post by Waderider on 2010-07-17
This issue seemed started after a retune following a new aerial for my Mythtv system. I've been tearing my hair out for days:cry:

I'm running Mythtv .23 on 10.04 64 bit, backend and frontend on the same machine. The tuner card is a Hauppauge Nova-T 500 with dual tuners. Here's the problem - I capture the card twice, as device number /dev/dvb/adapter0/frontend0 and /dev/dvb/adapter1/frontend0, but use just one video source. I think this worked before. When I scan for channels for adapter one, all is well and all channels can be accessed. When I go on to tune adapter two the channel scan appears to go well, but I then can't get a channel lock on most channels (most transports I guess) although some still work.

What am I doing wrong? What is the correct setup procedure for accessing both tuners? 

Note the segfault error message below - is that relevant? Don't think it used to appear.

jeff@jeff-desktop:~$ dmesg | egrep "dvb|v4l|dvb-usb|ic2|mt2060|error"
[    0.041148] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[   10.833965] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   10.834043] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   12.876698] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   13.528658] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[   13.528820] usbcore: registered new interface driver dvb_usb_dib0700
[   83.364676] evolution-data-[2175]: segfault at a ip 00007fdb5524573a sp 00007fdb49160260 error 4 in libc-2.11.1.so[7fdb551ce000+17a000]

Also, in case it helps, I have the following .conf file created for the tuner card:

options dvb-usb-dib0700 force_lna_activation=1
options usbcore autosuspend=-1
options dvb_usb disable_rc_polling=1

Thanks for any help.

---

### Post by Waderider on 2010-07-19
I'll give this a wee bump as I'm still tearing my hair out.

To confirm, it doesn't matter what way I proceed. As soon as I set up the second tuner I am unable to lock to most channels.

---

### Post by mukulakivi on 2010-12-27
I have mythtv 0.23, ubuntu 10.10 and the same tuner card and my problem was like yours. At first, I could watch my TV normally (I could change to any channel as well) and after I changed to another input I got the partial lock all the time - no matter which channel I try?!? Then I changed the frontend setting (I have Finnish versio, but I think english path is as follows:
Settings-TV settings-General:
I checked the 'let live-TV change scheduled programs'

After that I haven't got any partial lock at all, but tomorrow maybe it appear again;-)

(and right before I changed mythtv-setup so that it uses 1000 ms for timeout to change channel, but I think it had no effect. I had before 500 ms and it have worked before well.)

---

### Post by mukulakivi on 2010-12-27
Sorry, This worked just until next recordings and the recording size was zero lenght. Hopeless, this kind of system!!!

---

### Post by BicyclerBoy on 2010-12-28
The name of the .conf file controlling the tuner card changed *buntu 10.04 AFAIK.
The possible .conf file names are options.conf  dvb.conf  dvb-usb-dib0700.conf.

There is an error in the above text for the .conf file
options dvb_usb disable-rc-polling=1

note the underscore (_) & the minus (-) symbols

note: I have not used the autosuspend keyword  & (-1) seems wrong.

The nova-T-500 needs a tuning delay & AFAIK a possibly different tuning delay for each tuner. I use 300ms & 425ms.
Note: this 300ms is not time-out but tuner delay...

Stop moaning because it's free & works fantastic most of the time & for most people.
I have been using myth nova-t-500 for >2yrs.

---

### Post by mukulakivi on 2010-12-29
> **BicyclerBoy said:**
> The name of the .conf file controlling the tuner card changed *buntu 10.04 AFAIK.
The possible .conf file names are options.conf  dvb.conf  dvb-usb-dib0700.conf.

There is an error in the above text for the .conf file
options dvb_usb disable-rc-polling=1

note the underscore (_) & the minus (-) symbols


First of all, my Ubuntu seems to be 10.04

I didn't found any options.conf, dvb.conf or dvb-usb-dib0700.conf file. I try to find it by search *.conf file which would include 'polling' or 'dvb_usb' but no result.

I think I found the link related for this:
[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500#Disabling_the_remote_control_sensor](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500#Disabling_the_remote_control_sensor)

(And the next question is why I haven't such file...)

> The nova-T-500 needs a tuning delay & AFAIK a possibly different tuning delay for each tuner. I use 300ms & 425ms.
Note: this 300ms is not time-out but tuner delay...


I'll try this too.

---

### Post by BicyclerBoy on 2010-12-31
Just a note about the underscore & minus symbol in the string constants of *.conf file...
The mythtv info states "disable-rc-polling"  & the linuxTV states "disable_rc_polling".

The changes of this control file name from options to options.conf etc occurred about *buntu 9.10

It also seems that values of [-1, 0, 1] are possible but exactly what they are is not so clear.
Historically (-1) is true in signed integer data type, (1) is true in unsigned integer...

Your linuxTV link is out-dated info..
The filename of options  file is now named "options.conf"  it should be name.conf where name could be options dvb or ...
My nova-t-500 does not work without the lna activated.

---

