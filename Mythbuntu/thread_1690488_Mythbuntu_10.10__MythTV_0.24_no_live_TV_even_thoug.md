---
title: "Mythbuntu 10.10 / MythTV 0.24: no live TV even though channel scan successful"
date: 2011-02-18
forum: Mythbuntu
---

### Post by floh-511 on 2011-02-18
Having got my capture card working, I scanned for channels and though everything would be fine.
However, upon choosing LiveTV, the frontend will say "Please wait" and then kick me back to the start page.

I have two things I think might be connected with this:
1. When I run backend setup, it keeps telling me that capture cards 3 and 4 have not been set with a starting channel. I deleted the capture cards a few times during my hardware setup trials, and even though only two show up now, I still get this message.

If this is a probable issue, how do I delete cards 3 and 4 manually from what config file?

2. My second capture input is not connected to an LNB right now (second cable needs to be set up)

Could that be it or is it something else entirely?

---

### Post by newlinux on 2011-02-18
Could also be a playback problem. Would help to see your logs (frontend and backend). Also, do you have proper start channels setup on your the tuners you have setup? Might be worth it to choose delete all cards on all hosts and set them up again.

How many capture cards do you have and what are they?

---

### Post by floh-511 on 2011-02-22
I have one card with two inputs, set up as dvb-0 and dvb-1 and connected to video sources 0 and 1.
The card is a linux4media cineS2 (digital devices based).

Channel scan successful, I have set up the two devices I can see in the backend with an existing startup channel from the scan.

However the devices 3 and 4 which shouldnt´t exist anymore are still there even though I have deleted all devices (twice). Those have NOT got starting channels of course (where would I define them?), and the backend points this out on exit (I always say "no I know what I am doing" even though I don´t, of course).

I´m almost at the point where I would like to do a clean install, but that would mean losing everything else: My XBMC setup most of all.

Therefore I would still prefer to delete those entries manually in some config file (don´t know if that´s possible).

I will post some logs tonight, not at my Mythbuntu machine right now.

---

### Post by tgm4883 on 2011-02-22
> **floh-511 said:**
> I have one card with two inputs, set up as dvb-0 and dvb-1 and connected to video sources 0 and 1.
The card is a linux4media cineS2 (digital devices based).

Channel scan successful, I have set up the two devices I can see in the backend with an existing startup channel from the scan.

However the devices 3 and 4 which shouldnt´t exist anymore are still there even though I have deleted all devices (twice). Those have NOT got starting channels of course (where would I define them?), and the backend points this out on exit (I always say "no I know what I am doing" even though I don´t, of course).

I´m almost at the point where I would like to do a clean install, but that would mean losing everything else: My XBMC setup most of all.

Therefore I would still prefer to delete those entries manually in some config file (don´t know if that´s possible).

I will post some logs tonight, not at my Mythbuntu machine right now.

Since you have a tuner with two inputs, sounds like multirec is causing tuners 3 and 4

---

### Post by newlinux on 2011-02-22
> **floh-511 said:**
> I have one card with two inputs, set up as dvb-0 and dvb-1 and connected to video sources 0 and 1.
The card is a linux4media cineS2 (digital devices based).

Channel scan successful, I have set up the two devices I can see in the backend with an existing startup channel from the scan.

However the devices 3 and 4 which shouldnt´t exist anymore are still there even though I have deleted all devices (twice). Those have NOT got starting channels of course (where would I define them?), and the backend points this out on exit (I always say "no I know what I am doing" even though I don´t, of course).

I´m almost at the point where I would like to do a clean install, but that would mean losing everything else: My XBMC setup most of all.

Therefore I would still prefer to delete those entries manually in some config file (don´t know if that´s possible).

I will post some logs tonight, not at my Mythbuntu machine right now.

yes, as mentioned, more than likely mult-record is causing you to have tuners 3 and 4. By default with multi-record each tuner results in 2 encoders.

The start channel is likely your problem, as the backend setup is telling you. Will know for sure with your logs, but if your start channels don't exist, livetv won't work because the first channel it tunes to doesn't exist and fails.

You set the starting channel in the backend setup, I don't remember exactly where, but somewhere in the input connection I think. If you look around you'll find it - you need to set these to channels that exist and you know you can properly tune.

---

### Post by floh-511 on 2011-02-24
My logs:
[http://mythbuntu.pastebin.com/0czBjW8t](http://mythbuntu.pastebin.com/0czBjW8t)
I used Mythbuntu Log Grabber, first time so no idea if that is OK. I checked frontend and backend log collection.

I do know where to set up the starting channel. Are you saying that I should delete one of my capture cards and 3 and 4 will disappear? That is easy to try.
I thought two inputs would mean I would need two capture cards.

---

### Post by floh-511 on 2011-02-24
well that was easy. With one capture card it works.
However, I have LiveTV now but sound only works on non-HD channels. Anyone know where that comes from?

Digital Sound via S/PDIF works well with everything else (VLC Player, XBMC, non-HD channels in MythTV).

---

