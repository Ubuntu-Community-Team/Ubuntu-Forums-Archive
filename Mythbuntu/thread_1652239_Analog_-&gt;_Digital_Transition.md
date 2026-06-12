---
title: "Analog -&gt; Digital Transition"
date: 2010-12-24
forum: Mythbuntu
---

### Post by Rayn on 2010-12-24
Comcast in my area is sending out DTAs and saying they will no longer carry analog signals on their lines (going to QAM? I'm not saavy). 

I've been using my Myth system in large part as a DVR (SD, I don't need or care about HD) for years using my two beloved tuners:
PVR-150
PVR-250

One of them has a port for an IR widget which I use to control Myth (0.23.1) as well as a couple external players.  I don't watch TV using MythTV.

Now, I don't think I can make my PVRs read QAM signals so I guess I'm SOL on not changing anything.... so I'm wondering if someone could give me some advice on the least painful way to have the system work with QAM signals (and still have an IR port)

It seems like everytime I poke the system something breaks somewhere so any advice would be super appreciated.

---

### Post by newlinux on 2010-12-24
You could use your pvr-x50s with the DTAs. You'd plug the output of the DTA into the PVR-x50s and then use an IR blaster to change channels on the DTA from myth.

Other than that, you'd need to get QAM capable cards, but they will only be able to tune unencrypted QAM channels, so you'd want to check and see if those channels are worth it to you or not.

---

### Post by ian dobson on 2010-12-24
Hi,

If you want to keep your tuners, why not pick up a settop box with a s-Video output that you can feed into the PVR.

Mythtv can control a IR-Blaster that send IR signals to the settop box to change channels.

Regards
Ian Dobson

---

### Post by Rayn on 2010-12-24
My concern over IR blaster based solutions is the DTA IRs function on the same frequency (which is also my cable set top box frequency) so unless I could build black boxes for each of these IR -> DTA units, everytime someone changed the cable channel it would mess with recordings (would happen frequently) (I know very little about IR blasters so I will start my research here and see what this means - maybe they have a unit that goes USB -> DTA IR1, DTA IR2, that would be convenient)

I have Comcast in CT, and my understanding is non-encrypted QAM content is being reduced to basically nothing so my initial hope I could upgrade to QAM capable cards looks unattainable.

Thanks for pointing me in the right direction to do further research.

---

### Post by LowSky on 2010-12-24
if you want to get all you channels and want to get around encryption the best option is the haupaughe hd pvr

---

### Post by efball3 on 2010-12-24
> **Rayn said:**
> 

I have Comcast in CT, and my understanding is non-encrypted QAM content is being reduced to basically nothing so my initial hope I could upgrade to QAM capable cards looks unattainable.

Thanks for pointing me in the right direction to do further research.

I have comcast cable and the broadcast channels are not encrypted. I can get abc, nbc, cbs, pbs, fox, and a few other stations, all in HD unencrypted 256QAM.  

I'm using the dvico fusionhdtv7 dual express card.  It can record two HD stations at once with minimal CPU load.

---

### Post by ian dobson on 2010-12-24
Hi,

I help a friend setup a simple mythtv system and used a IR-blaster that we just taped onto the front of the settop box using abit if sticky tape. So a problem with switching the wrong tuner is solved with a lowtec solution.

My solution might not be the best, it's just one. Another would be to use a HD-Runner (hd pvr)? (I think that's what their called), or maybe a PCI/usb tuner that supports QAM.

Regards
Ian Dobson

---

### Post by newlinux on 2010-12-24
> **Rayn said:**
> My concern over IR blaster based solutions is the DTA IRs function on the same frequency (which is also my cable set top box frequency) so unless I could build black boxes for each of these IR -> DTA units, everytime someone changed the cable channel it would mess with recordings (would happen frequently) (I know very little about IR blasters so I will start my research here and see what this means - maybe they have a unit that goes USB -> DTA IR1, DTA IR2, that would be convenient)

I have Comcast in CT, and my understanding is non-encrypted QAM content is being reduced to basically nothing so my initial hope I could upgrade to QAM capable cards looks unattainable.

Thanks for pointing me in the right direction to do further research.

IR is line of site, so you should be able to isolate the IR signal somehow with a conveniently angled or placed ir blaster

> **efball3 said:**
> I have comcast cable and the broadcast channels are not encrypted. I can get abc, nbc, cbs, pbs, fox, and a few other stations, all in HD unencrypted 256QAM.  

I'm using the dvico fusionhdtv7 dual express card.  It can record two HD stations at once with minimal CPU load.

What channels are encrypted and unencrypted often vary greatly from one place to another, even with the same provider. In general, you should be able to count on the locals, but not much else. You can check what has been reported at:

[http://www.silicondust.com/support/channels/](http://www.silicondust.com/support/channels/)


I too use an Hauppage HD-PVR, but if you aren't interested in HD it's overkill and not worth it. Just use the composite, RF, or S-video capture (depending on what model PVR-x50 you have) on the cards you already have.

---

### Post by Rayn on 2010-12-25
Hm, the HD PVR has many attractive features I might be interested in -- but it only has one ir blaster that can control one device?

I have to read up on this thing, its expensive, but I'm not confident I could rig up an ir blaster system with my 2 PVR cards and then still control my Mythbox with the IR receiver on one of the PVRs.  That's a lot of lirc running around.  Maybe its less complicated than it appears.

---

### Post by Senkoboy on 2010-12-25
Our cable made the switch this year, ( Suddenlink).  I used a ATI HDTVWonder to pick up the unencrypted QAM channels. Still use my PVR 150 to pick up my VCR if needed and the few basic analog channels left on cable.

---

### Post by Rayn on 2010-12-26
So, if I hook up the DTAs to the coax input of my PVRs ... and enable the IR blaster and set up to them both ... does it matter that the signal is QAM?  Are the cards still usable at all or will they need to be upgraded to QAM cards?

The DTA coax (it has no other outputs) would come from cable in and go to PVR coax cable in.

---

### Post by newlinux on 2010-12-27
> **Rayn said:**
> So, if I hook up the DTAs to the coax input of my PVRs ... and enable the IR blaster and set up to them both ... does it matter that the signal is QAM?  Are the cards still usable at all or will they need to be upgraded to QAM cards?

The DTA coax (it has no other outputs) would come from cable in and go to PVR coax cable in.

No it doesn't matter. Your DTA's would be tuning the QAM signal. You'd be capturing the already unencrypted analog stream via RF from your DTA, same as your TV would if it were hooked up to your DTA. You'd set the PVR-x50s to tune channel 3 or 4 (whatever the DTAs are set to output on) on it's RF input and use IR blasters to change the channel on the DTAs...

The cable in (from wall) should go to DTA in. The DTA out (RF/Coax) would go to the PVR coax in and all would work.

---

