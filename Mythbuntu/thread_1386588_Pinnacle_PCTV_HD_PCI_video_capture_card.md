---
title: "Pinnacle PCTV HD PCI video capture card"
date: 2010-01-20
forum: Mythbuntu
---

### Post by linuxhippy on 2010-01-20
I just bought a Pinnacle PCTV HD PCI video capture card and installed it into a Mythbuntu 9.10 box that's set up to be a backend and frontend.  In the backend setup I see 2 choices in Capture Card Setup that have Pinnacle as the probed card...these are:

Analog V4L capture card
MJPEG capture card

When I go into Input Connections for each of these I cannot scan my us-cable channels.  What am I doing wrong?

---

### Post by linuxhippy on 2010-01-21
I read that this Pinnacle card is compatible with mythtv.  I cannot get it to pick up unencrypted cable.  Has anybody here used a Pinnacle card?  How do I configure it?

---

### Post by Colonelguf on 2010-01-22
I have the Pinnacle 800i card, I think that is the same as you have. I set up the analog v4l side and then in the channel scan screen I just clicked the "Fetch channels" button and it downloaded the analog cable channels from Schedules Direct. The digital tuner has to be set for DVB tuner, not MJPEG, then scan for channels.

---

### Post by linuxhippy on 2010-01-22
> **Colonelguf said:**
> I have the Pinnacle 800i card, I think that is the same as you have. I set up the analog v4l side and then in the channel scan screen I just clicked the "Fetch channels" button and it downloaded the analog cable channels from Schedules Direct. The digital tuner has to be set for DVB tuner, not MJPEG, then scan for channels.

The analog setting did it!  what do you mean about the DVB tuner?  There's a card for DVB but that didn't come up with the Pinnacle 800i module.

---

### Post by Colonelguf on 2010-01-26
> **linuxhippy said:**
> The analog setting did it!  what do you mean about the DVB tuner?  There's a card for DVB but that didn't come up with the Pinnacle 800i module.
It doesn't say Pinnacle in the card setup. IIRC it said Samsung something.

---

### Post by linuxhippy on 2010-01-26
I don't get samsung either.  I'm in the backend capture card setup.  The only card type that has DVB is this:

DVB DTV capture card 3.x

Is that it?  There's 2 submenus after that for configuration.

---

### Post by Colonelguf on 2010-01-27
Ok, I am sitting in front of the TV
Yes, the Card Type says DVB DTV capture card (v3.x)
Frontend ID: Samsung S5H1409 QAM/Subtype: ATSC
Under Recorder options check "Open DVB card on demand" or the analog won't work
Did you get the analog audio working?

---

### Post by linuxhippy on 2010-01-27
> **Colonelguf said:**
> Ok, I am sitting in front of the TV
Yes, the Card Type says DVB DTV capture card (v3.x)
Frontend ID: Samsung S5H1409 QAM/Subtype: ATSC
Under Recorder options check "Open DVB card on demand" or the analog won't work
Did you get the analog audio working?

had the audio working...I had to set it to 48000 on the scaling in the backend.  Now I'm re-installing mythbuntu 9.10 because I switched graphics cards (NVIDIA 64 bit to ATI 32 bit since my mobo is 32 bit) and now mythbuntu won't let me log in.

I have to set my capture card up AGAIN (this is like the 15th time in a week).  So, I'll try to get it working digital this time.

---

### Post by linuxhippy on 2010-01-27
I now see that it probed Samsung.  I cannot lock onto any channels with the DVB capture card.  I went back to the analog card and it couldn't probe anything.  So I removed all capture devices from my pc and then added the analog (it then said pinnacle again).  I think I'm stuck with an analog signal.  My cable is just the basic air channels.

---

### Post by Colonelguf on 2010-01-29
> **linuxhippy said:**
> I now see that it probed Samsung.  I cannot lock onto any channels with the DVB capture card.  I went back to the analog card and it couldn't probe anything.  So I removed all capture devices from my pc and then added the analog (it then said pinnacle again).  I think I'm stuck with an analog signal.  My cable is just the basic air channels.
You do have to scan with the DVB side of the card. It is necessary to have a really strong, clean cable signal for digital.

---

### Post by linuxhippy on 2010-01-29
Good to know that my card is indeed digital.  I think my cable is only analog, though.  I cannot get any of the QAM256 cable stations.  Looks like I should call Comcast.

---

