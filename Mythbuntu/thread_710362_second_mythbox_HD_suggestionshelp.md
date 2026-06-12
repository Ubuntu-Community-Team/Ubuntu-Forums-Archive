---
title: "second mythbox HD suggestions/help?"
date: 2008-02-28
forum: Mythbuntu
---

### Post by elj4176 on 2008-02-28
First I'll say that I have been using myth for over a year now with an old dell p4, 512MB, pvr-350  and directv to a projector in the basement with good results. I do not have the hdtv package from directv but plan to add it at some point this year. I recently switched to mythbuntu and had no problems getting it setup. I'm not sure I get any OTA HD in my location either.

I recently bought an hdtv and have a series 2 tivo hooked to it and directv in the main tv watching room. My idea is to replace the non-hd tivo with a shiny new HDmythbox. I see the kworld cards are popular and they can be bought fairly inexpensively and are easy to setup. I would also have to get a mobo with dvi out or an nvidia card with dvi/hdmi out right? Suggestions?
Would a core duo get the job done for HD? I'm not worried about the non-HD since I know the system will be able to handle it. I see a couple of mobo/proc combos online for cheap at tigerdirect.

Is it easy to add a slave BE? Would I be able to watch recordings from either one at either place? If I add a second BE will the recordings be stored there or on the master BE? 
Would it be easier to keep the two mythboxes separate? Kinda like the tivo and mythbox are now except I could connect to either mythbox from a FE only machine.

Lots of questions. Sorry! Thanks for any info/advice you can give.
Don't bang on me for the Tivo - I got that before I ever heard of mythtv with the lifetime data and the wife acceptance factor is high.

---

### Post by tgm4883 on 2008-02-28
My Core 2 Duo E6300 plays HD fine.  Setting up a second backend is easy, you just need the master BE address and db password, you also need to enable the mysql service on the backend (in MCC), and set the master backend to use the non localhost ip (in mythtv-setup)

The slave will record to it's own hard drive, but both systems recordings will be available to both systems.

Don't keep them seperate, it defeats the purpose of having an awesome mythtv network

---

### Post by elj4176 on 2008-02-28
That sounds easy enough. I just hadn't read many posts about muliple BE setups. 

Any hardware suggestions (kworld/mobo/nvidia hdmi)? The kworld 110 or 115 looks like it would get it done and Nvidia cards with dvi are cheap enough. Maybe I'll skip the mobo dvi/hdmi.

Edit:
purchased the kworld 115. now for the rest. I have a Dell sc440 sitting around that I can use until I get a htpc case so maybe a video card with hdmi out is my next item.
Would this get it done for mobo and cpu:

PCChips A13G+ v3.0 Motherboard CPU Bundle - AMD Athlon 64 3500+ Processor 2.20GHz OEM, 1GB PC4200 DDR2 533MHz Memory

---

### Post by newlinux on 2008-02-28
i can playback HD on my P4 2.6. Any dual core can playback HD mpeg2s....

I had a 3500+ playing back HD without XvMC. High CPU usage, however but it played back fine. Given the price of lowend amd dual cores, I'd get a dual core if I were you. You don't have to... but the prices are worth it. My primary HD boxes are X2 4200 and X2 3800. No problems whatsover....

only recommendations are go inexpensive with the video card, stick with nvidia. Integrated video (I have a 6150) works fine. I personally wouldn't pay extra for HDMI. DVI is fine.

---

### Post by elj4176 on 2008-02-29
Well - it looks like I'll be building an SD mythbox wit hthe kworld card. I know the OTA analog stream will stop at some point but I'm not going to use the OTA anyway. The kworld 115 should still capture whatever I send it from my directv box (non-HD) so at worst I add another mythbox to the network and at best I get 1 or 2 OTA HD channels for a year or so. 
For the price of the card and the related hardware it is worth it. I'll be surprised if there isn't a way to capture the HD from the directv box (or cable company) by the time the OTA analog is gone.

---

### Post by newlinux on 2008-02-29
> **elj4176 said:**
> Well - it looks like I'll be building an SD mythbox wit hthe kworld card. I know the OTA analog stream will stop at some point but I'm not going to use the OTA anyway. The kworld 115 should still capture whatever I send it from my directv box (non-HD) so at worst I add another mythbox to the network and at best I get 1 or 2 OTA HD channels for a year or so. 
For the price of the card and the related hardware it is worth it. I'll be surprised if there isn't a way to capture the HD from the directv box (or cable company) by the time the OTA analog is gone.

Don't count on being able to capture HD from US satellite companies. They simply don't want you too. The only way you'll probably be able to do it anytime soon is to capture the analog HD stream from the component out, which requires a fast processer, fast bus, very fast disk access  and tons of disk space, given the high bit stream (we are talking 1 hour is approximately 700GB uncompressed). Real time compression would probably require dedicated hardware encoding, and those cards are expensive and use propietary compression, which means you'd need to use their software to view the capture... However, I heard hauppage is coming out with an affordable solution for component capture...

This is one reason HDMI was adopted. You'd have to break HDCP to capture the already compressed digital stream from HDMI. This is why more and more devices (think Blu-Ray and HD-DVD and upconverting DVD players) only send their highest resolutions through HDMI, and not their component outputs... DirecTV will probably follow suit. Right now, you basically need to hack your satellite box to get HD out of it that you can use with other devices. I'd be surprised if this changes by next year...

There already is a way to do this from cable boxes. Use the firewire connection. But that is controlled by the 5c copy protection settings.

---

