---
title: "Mythbuntu &amp; WinTV Nova-T PCI"
date: 2008-09-30
forum: Mythbuntu
---

### Post by knowledene on 2008-09-30
I'm new to Linux & trying to learn fast. Having just installed Mythbuntu 8.04 MythTV Version: 0.21, I have a problem scanning channels. 

The card is an old one - a WinTV Nova-T PCI with a Philips SAA7146 chip.

The scan goes through but with a signal strength of up to 18% but there are no channels. 

lspci -v shows 
01.09.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01) 
Subsystem: Technotrend Systemtechnik GmbH Technotrend-Budget/Hauppauge WinTV-NOVA-T DVB card 
Flags: bus master, medium devsel, latency 32, IRQ 21 
Memory at df001000 (32-bit, non-prefetchable) [size=512] 

Part of dmesg is:- 
[66.503306] ACPI: PCI Interrupt 0000:01:09.p[A] -> Link [APC2] -> GSI 17 (level,high) -> IRQ21 
[66.503362] saa7146: found saa7146 @ mem f8a40000 (revision 1, irq 21) (0x13c2,0x1005). 
[66.503372] saa7146 (0): dma buffer size 192512 
[66.503375] DVB: registering new adapter (TT-Budget/WinTV-NOVA-T PCI) 
[66.539100] adapter has MAC addr - 00:d0:5c:20:40:7d 
[66.611956] nvidia: module license 'NVIDIA' taints kernel. 
[66.965488] DVB: registering frontend 0 (LSI L64781 DVB-T)... 
............... etc 
[142.102958] DVB: frontend frequency limits undefined - fix driver 
[142.103120] DVB: frontend frequency limits undefined - fix driver 
[142.103198] DVB: frontend frequency limits undefined - fix driver 
............... etc 

$ sudo nano /etc/modprobe - shows it is empty 
$ sudo nano /etc/modprobe.d/options - has the following:- 
# Enable double-buffering so gstreamer et. al. work 
options quickcam compatible=2 
# Default hostap to managed mode 
options hostap_pci iw_mode=2 
options hostap_cs iw_mode=2 

Now I am stuck & haven't a clue what to do next. I've spent a lot of time searching the forums to get so far. 
Can anyone advise please?

---

### Post by SiHa on 2008-09-30
Now this might be a silly question, and feel free to shoot me down...

Have you got the card type correctly identified in the backend setup?

(This is from memory, so I might be a bit hazy on the details...)

When you go into the card definition screen, I think the default option that comes up is "V4L Tuner..." or something, and a device string is reported in the box below. This leads you to think the card has been correctly detected. Only thing is this is an analogue card, and it's scanning for analogue channels which a DVB card will have difficulty picking up!
The card type should be something like "DVB capture card V1.x"

When you go to the channel scan if the system is just scanning Europe-West (or wherever you are...), then you definitely have an anlogue card defined. You should be asked to select which country you are in (in my case UK).

HTH

Simon

---

### Post by stevanbt on 2008-09-30
Hi,
It may be worth checking out [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php) and [http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI)

Signal strength will be reduced unless you add

```
options dvb-usb-dib0700 force_lna_activation=1
```

to

```
/etc/modprobe.d/options
```

Hope this helps, Steve.

---

### Post by SiHa on 2008-09-30
I think this is a single-tuner WINTV card. They don't have the LNA.

---

### Post by knowledene on 2008-10-01
Many thanks for the replies - I'm still trying!

I think SIHa is right, Stevanbt's suggestion hasn't changed anything.
Also It _seems_ the card is identified correctly (as DVB DTV capture card (v3.x)), although options on the channel frequency table are 'europe west' and 'default' does this suggest that it's still coming over as an analogue card?

Following the instructions on [http://parker1.co.uk/mythtv_dvb.php](http://parker1.co.uk/mythtv_dvb.php) I get as far as &#8220;Watch Some TV&#8221; (ie scanning channels) and get the error message 

Failed to open /dev/dvb/adapter0/frontend : Device or resource busy

Does this mean that I don't have the right firmware for the card?
How can I check this?
And can I scan channels outside of Mythbuntu?

I am determined to eventually get it going, but am spending a lot of time looking & trying things. I feel that I'm perhaps missing one simple step through lack of knowledge.

Thanks once again for your replies. If you have any more suggestions.....!

Terry

---

### Post by stevanbt on 2008-10-01
Apologies for getting the wrong card...

---

### Post by knowledene on 2008-10-01
No problem.... Thanks for giving me the parker1.co.uk site. I've still to work through it & understand it. 
If you have any other suggestions I would be very grateful.

Terry

---

### Post by SiHa on 2008-10-01
> **knowledene said:**
> Also It _seems_ the card is identified correctly (as DVB DTV capture card (v3.x)), although options on the channel frequency table are 'europe west' and 'default' does this suggest that it's still coming over as an analogue card?


If it's identified as '**DVB DTV capture card (v3.x))**' then that's correct.  When you finally scan for channels though, it should then ask you to select your country. 

Have you tried running the backend setup from scratch. Delete all capture cards, inputs and video sources an start again.

**Important** When you associate a card to an input (or video source - I can never remember which way round it is) it's vitally important to give it a name (eg Freeview?). If you don't, it appears in the list of available inputs as a blank line, (which I don't think you can select). I'm wondering if you have a legacy entry defined as an analogue card that has a name, and your DVB option that doesn't?

I know this can happen. It happened to me when I was first setting up Myth.

Otherwise, I'm stumped I'm afraid.

Ooh, just thought. When you define the card, there is a button 'recording options' or something similar. Select that, and there should be a 'tuning timeout' box. Try winding that up to 150ms or more. As your card is older, I guess it stands to reason that it might take longer to acquire a channel lock.

Cheers, Simon

BTW - The Parker1 site has loads of really useful information. Well worth a look.

---

### Post by knowledene on 2008-10-02
Thanks Simon for your help. 

I've deleted everything on the backend and started again.
The Scan Configuration Screen defaults to "United Kingdom".
On the "Recording Options", I've changed the Tuning Delay to 200ms.

Still no joy. I'm coming to the conclusion that the card is not suitable, even though it works ok in XP.
Time to give it a rest I think, buy another card, & try again later!!

Thanks again
Terry

---

### Post by SiHa on 2008-10-02
I know there was a problem with kernel support of a different Philips chipset, so maybe as you say this one just isn't compatible with Ubuntu. Shame

One last thing, I notice in the logfile there's a 'Nvidia taints kernel' line. Don't suppose you've tried disabling the proprietary Nvidia drivers if you're using them??

---

### Post by eddypolak on 2008-10-02
I have success with a WinTV Nova T 500. I did not have to do anything special to make it work with Mythbuntu 8.04. 'Europe West' and 'default' are what I have too.

No one so far has suggested that your signal might be too low at only[I]up to[I] 18%. When I scan for channels I can see a scrolling display in the background. It reports (fleetingly!) each channel and what it finds there if anything. Do you see that? As far as I can recall I saw some channels were rejected due to too low a signal. I assume these were from remote transmitters. I did get all the ones I expected though and these were at least 50% strength.

---

### Post by eddypolak on 2008-10-03
A correction ... I rescanned channels to check my previous post. In fact channels are either found or there is reported 'no signal'. There is no 'low signal' error as I previously stated.

---

### Post by j.dibble on 2009-05-11
HI,  I'm getting this exact same problem as originally reported in this thread.  Extremely annoying!  I was running fine with ubuntu 7 and this tv card for about 1.5yrs with mythtv. fantastic, and now it appears to be broken after installing jaunty.

i don't think its anything to do with settings on mythtv as one poster replied, i think its to do explicitly with the driver itself.  i think this chipset is particuarly old.

has anyone got any ideas?  did the original poster get it fixed? i don't walk to folk out for a new card just because of some stupid bug.

---

### Post by j.dibble on 2009-06-25
Ok, I can give an update for the benefit of any other users suffering similar pains.  In the end I had to use the scan utility which comes with the dvb-apps package.  This seems to generate the channels.conf file ok.  then you import them into mythtv backend.  works after that.  

still got trouble with the display slightly - the text and picture are slightly blurred/fuzzy but its still actually better quality than the tv build in tuner. 

w_scan still doesn't work.  kaffeine did work. its nice to have mythtv back again!

---

