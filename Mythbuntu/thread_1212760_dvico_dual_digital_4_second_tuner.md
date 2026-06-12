---
title: "dvico dual digital 4 second tuner"
date: 2009-07-14
forum: Mythbuntu
---

### Post by spleblem on 2009-07-14
hey 
i have had my dvico dual digital 4 tuner card working for awhile now and finally just got the remote to work, now i have tried to enable the second tuner on the card to work but it does not pick up any signals
does anyone know how to fix this?
thanks

---

### Post by spleblem on 2009-07-19
bump
anyone?

---

### Post by ian dobson on 2009-07-19
Hi,

I don't know your card but maybe you need to manually load the driver module twice or there might be a option you need to set to get the driver to find the second tuner.

When you do a ls /dev/dvb* what do you see? For me with 2 DVB cards installed I see adapter0  adapter1.

What messages to you see in dmesg?

What devices are listed in lspci?

Regards
Ian Dobson

---

### Post by chipppy on 2009-07-19
Good Morning

What rev of Mythbuntu are you using?
I have 9.04 and this specific card (see spec's as part of autosign below).  This card worked automagic, but I use a Wii remote so I dont know anything about the remote.

As to the 2 tuners.
Have you setup the two tuners under video cards as part of the 6 initial setup steps?  You need to setup 2 cards card 0 and card 1.

Also there is a very good but long HOW TO: for this card by a dude named something like 'ooby-fiesty' look at the HOW TO:s sticky at the start of this forum.  It is old (has been updated) and there is a lot of Q&A's in the thread.  It will take some reading but I an certian your answer is in there.

Come back here is you need more help.

Cheers
chipppy

---

### Post by spleblem on 2009-07-19
hey guys thanks for the replys
the card is a rev2
i have set the card up as a second tuner under video cards, i have card0 and card1.
when i run ls /dev/dvb i also get adapter0 adapter1 
but still when i try and scan for channels with the second tuner it times out.

---

### Post by ian dobson on 2009-07-20
Hi,

Does the channel scan work for the first tuner?

maybe try using wscan or tzap to scan then import the channels.conf file into mythtv.

Regards
Ian Dobson

---

### Post by spleblem on 2009-07-20
yea the first tuner works fine
not to sure how to import the file

---

### Post by ian dobson on 2009-07-20
Hi,

As both tuners get the same signal, they should be in the same video input group. If you already have all the channels for tuner 1 working then they should work just the same for tuner 2.

What messages to you see in syslog/dmesg?

Regards
Ian Dobson

---

### Post by chipppy on 2009-07-21
Good Morning

In backed setup 

==> 2. Capture cards 
You should have 
[DVB:0]
[DVB:1]

==> 3. Viedo Sources 
You should have created something here with the info for your areas DVB-T frequency table.  I am in Perth Australia so mine is called FTA-Oz and it uses the Perth Frequency Table

--> 4. Input Connections
You should now have
[DVB:0] (DVBInput)-> FTA-Oz     
[DVB:1] (DVBInput)-> FTA-Oz

(remember that the FTA-Oz is what I named it in 3. Video Sources)

==> 5. Channel editor
Edit all your channels and fix up the missing logo's.

If this is all good then you should have a working system.  
Please tell me what parts are not setup like this or if it is all setup like this.

Cheers
chipppy

---

### Post by chipppy on 2009-07-27
Good Afternoon

Found the other Divco thread for you

[]("http://ubuntuforums.org/showthread.php?t=616103")

Read through this thread and post on it if required.  Hope it helps.

Cheers
chipppy

---

### Post by spleblem on 2009-08-03
have had to do a full reinstall because of other errors occuring
so it took me a few days to set everything up again
still having the same problem
yes chippy my setup does look like your post
when watching tv and i try to change tuners i get this message

"you should have gotten a channel lock by now, you can continue to wait for a signal, or you can change the signal with up or down, change video source (y), inputs (c) etc."

when in tuner card setup for second tuner i try and scan for channels at it times out, no signal

---

### Post by spleblem on 2009-08-04
*bump*
anyone?

---

### Post by spleblem on 2009-08-10
Does anyone know how to fix this??

---

### Post by spleblem on 2009-08-29
I have searched and searched but can still find no fix for this
its really starting to be a problem having only one available tuner 
does anyone have any idea of the problem or what i could search for to find an answer?

---

### Post by nasha on 2009-08-29
I have had similar issues on two different DD4's regarding the second tuner. In both cases i replaced the tuner and called it hardware failure. I'm a Hauppauge man now :)

Anyway, what's your output of dmesg|grep DVB and dmesg|grep dvb ?
Just want to make sure the driver is succesfully loading.

Have you attempted to record two programs at once, or tried to watch live TV using the 2nd tuner? As a poster said earlier, you only need to scan channels with one tuner. Does Myth recognise two tuners?

---

### Post by spleblem on 2009-08-30
here is the output for those two

```
root@media-desktop:~# dmesg|grep DVB
[    9.164441] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4 (rev 2)' in warm state.
[    9.195750] DVB: registering new adapter (DViCO FusionHDTV DVB-T Dual Digital 4 (rev 2))
[    9.388894] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[    9.543115] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:08.0/0000:01:06.2/usb3/3-1/input/input6
[    9.552569] dvb-usb: DViCO FusionHDTV DVB-T Dual Digital 4 (rev 2) successfully initialized and connected.
[    9.552581] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4 (rev 2)' in warm state.
[    9.583818] DVB: registering new adapter (DViCO FusionHDTV DVB-T Dual Digital 4 (rev 2))
[    9.746825] DVB: registering adapter 1 frontend 0 (DiBcom 7000PC)...
[    9.899294] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:08.0/0000:01:06.2/usb3/3-2/input/input7
[    9.900627] dvb-usb: DViCO FusionHDTV DVB-T Dual Digital 4 (rev 2) successfully initialized and connected.
```

```
root@media-desktop:~# dmesg|grep dvb
[    9.164441] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4 (rev 2)' in warm state.
[    9.164672] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[    9.552566] dvb-usb: schedule remote query interval to 100 msecs.
[    9.552569] dvb-usb: DViCO FusionHDTV DVB-T Dual Digital 4 (rev 2) successfully initialized and connected.
[    9.552581] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4 (rev 2)' in warm state.
[    9.552702] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[    9.900622] dvb-usb: schedule remote query interval to 100 msecs.
[    9.900627] dvb-usb: DViCO FusionHDTV DVB-T Dual Digital 4 (rev 2) successfully initialized and connected.
[    9.900649] usbcore: registered new interface driver dvb_usb_cxusb
```

yes i have tried to use the second tuner and i get the error that i said before
"you should have gotten a channel lock by now, you can continue to wait for a signal, or you can change the signal with up or down, change video source (y), inputs (c) etc."

thanks for any help

---

### Post by spleblem on 2009-09-06
** bump **

---

### Post by gvw on 2009-09-11
I get exactly the same error on my Dvico Dual Digital - at the moment only one tuner works whereas a few weeks or months ago, both worked. Have not been watching a lot of tv so not sure when it dropped out. Since you and I are getting the same error, sounds like software issue caused by a kernel upgrade and not a hardware failure.  I have Rev1 and I do not think this is an unknown issue.

I will scrub and reinstall the firmware and drivers etc and let you know how it turns out

---

### Post by spleblem on 2009-09-12
ok sounds good.
let me know if you what you find out

---

### Post by spleblem on 2009-10-23
anyone?
please i really would like to get my second tuner to work?!!!
thanks

---

### Post by gnewt0n on 2009-11-01
> **spleblem said:**
> anyone?
please i really would like to get my second tuner to work?!!!
thanks

Hi spleblem,

You say you've done a recent re-install - did you take all subsequent upgrades too?

I had a similar issue with recent Ubuntu 9.04 kernels (64 bit AMD) where the second tuner on my (I think V1) card stopped working, and have had to 'freeze' myself on a particular kernel. I'll post again with the details, as I can't access the system from where I am now.

So - a number of possible differences and not exactly the same problem, but I think if you have a few older kernels to try in your grub menu, give that a go.

Here's a pic of the remote that came with my card:
[IMG]http://home.exetel.com.au/newtons/FusionREMOTE-tiny.jpg[/IMG]

Cheers,
Greg |;^)

---

