---
title: "Mythbuntu Configuration for DVDs &amp; music only"
date: 2008-03-27
forum: Mythbuntu
---

### Post by RustyWyatt on 2008-03-27
Hi Folks,

I have a few very basic questions.  I want to use Mythbuntu to archive, manage and play my DVDs and music from my iTunes library. I watch very little TV and over-the-air broadcasts are just fine for me.

I have been cleaning up an old desktop P4 2.4 GHz and am researching a new video card so it seems like this hardware should easily meet or exceed my basic hardware needs (I have 340 gig on board and a terabyte of NAS for storage starters).

I have read as much as I can find on the web but, not being a TV person, I'm confused about a number of issues.  My questions are:

1 – If I only want copy my DVDs and watch them via my PC, do I need a “tuner card”?

2 – If I do not have a tuner card, how do I operate a remote controller?

3 – If I do not have a tuner card how do I hook up my TV?

4 -  Given the coming change to digital TV, can I buy a digital TV tuner card today that will meet my needs today and that will make me sort of future proof?

4 - For me needs, is it important to have a hardware encoder solution?

5 – If a tuner card is “cable ready” or “satellite ready” will also meet my basic over-the-air broadcasts needs?

All info Greatly Appreciated!

Thanks,
Tom

---

### Post by process91 on 2008-03-28
*phew* OK let me see if I can address your questions.

1. - If you don't plan on watching TV through the computer then you do not need a tuner card.

2. - Assuming by "remote control" you wouldn't be satisfied with a wireless keyboard, then I would try out the [RS232 IR Receiver]("http://www.irblaster.info/receiver.html"). Get the one with the cable, it's $18.95.

3 - The tuner card actually never hooks the computer to the TV, it just allows you to connect a cable wire (or antenna) to the computer. You'll need a video card with an S-Video connection if you have an old TV, or you'll need a newer TV with a VGA connection.

4 - No. Not really. The best HD tuner on the market (imho) is the [HD Home-Run]("http://mythtv.org/wiki/index.php/Silicondust_HDHomeRun"), but most cable providers (or at least Comcast) require you to have one of their own HD boxes to decode the signal. I do get some free ones, because the FCC has seen it wise to require standards like NBC, CBS, and ABC to be broadcast unencoded however the rest are unattainable without hooking into the Comcast box (i.e. firewire) and in general causing a huge mess.
[Note: If this is not the case and someone has a better way to get HD from Comcast into MythTV, please PM me!]

4 (again) - No. See 1 for why you don't need a tuner in the first place. If you choose to get a tuner, do please get a hardware encoding tuner, they offer much better performance and are generally only $20-40 more.

5 - If all you want is OTA broadcast cable grab the [Hauppauge PVR-150]("http://mythtv.org/wiki/index.php/Hauppauge_PVR-150"). It's a decent card, very easy to configure (basically plug-and-play for MythTV) and optionally can include a remote + IR blaster!

Disclaimer: Although I have worked extensively with MythTV, I only started a year ago and would not consider myself an expert. The above statements are only my own opinion, and do not represent the opinion of MythTV or its subsidiaries. Results may vary. Consult your doctor if symptoms progress further.

---

### Post by RustyWyatt on 2008-03-28
Howdy Process91,

Thanks for your detailed reply it was a big help!

I have spent sometime researching replacement video cards for my 1997 system and it's a good thing I did... I have an AGP video slot and I learned a lot I didn't know.

Anyway, today I ordered a "ASUS N7600GS SILENT/HTD/256M GeForce 7600GS 256MB" replacement video card and as you noted it will provide all of my PC to TV/screen interface needs.

I put off ordering a tuner card for the time being as I assume that I can add one at any time to a functioning system. The HD Home-Run certainly looks promising!

As soon a my new video card and upgraded "silent" fans arrive, I'll start the initial installation process... Oh Boy! 

Expert or not, your reply was very timely and helpful! So, Thanks again!!

Tom

---

