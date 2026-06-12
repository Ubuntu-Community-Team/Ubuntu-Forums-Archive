---
title: "Myth DVB-T scan is a mess!"
date: 2009-06-16
forum: Mythbuntu
---

### Post by dibuntux on 2009-06-16
OK, after more than 2 years using mythbuntu, since 7.10, and I LOVE IT, I can say that scan for DVB-T is really a mess.

We just switch off analog TV here in Italy (partially on same regions) , so the DTV signal is very good.
I now have a STB unit that receives everything.
My PC with an Hauppauge HVR1110 gets everything using VLC, Kaffeine, scan, etc.

It is just Myth that cannot lock on to some channels without a reason.

Following is some previous post of my nightmare.

Can someone help? TIA
Dave

I either get no lock or partial lock, with a very strong signal (>60%) and BE of 65535.

Also tuning was never fixed. I have to scan for country using France, since providing direct freq. info or a channel.conf from scan does not work.



 partial lock - sometimes - on one DVB-T network
I really cannot trace this out. I can lock to all networks but one, RAI (national gov. tv in Italy).

Sometimes it works, sometimes it does not. I tried with an amplifier, and signal passed from 61% to 64%, but it is not dependent on % signal; other netowrks work with just 58%.

I get the signal % at 64, partial lock and BE 65535 and the window that tells you "you should have got a signal lock by now..."


using scan, i get a lock on all networks, which BTW are transmitted from a repeater in the same location, but on the RAI networks I get

Warning: filter timeout pid 0x0011

Other days, it just works. I tried with longer timeouts, but it is the same.

Any suggestions?

My system: Mythbuntu 8.10
Athlon 1700+ 512MB SDRAM PC133
Nvidia 5200 256 MB
Hauppauge HVR 1110 DV-T
SkyStar 2.6 DVB-S

---

### Post by ian dobson on 2009-06-16
Hi,

Sounds as if the DVB stream for that one channel is screwed up. The problem is not at your end, rather the transmitter is not sending a 100% conform DVB stream.

Maybe you could try using wscan to scan your channels then import the channels.conf file into mythtv.

Note: I had lots of problems with the MythTV scanner for my DVB-C system. Even though I have a signal strength of over 80% on all channels the myth scanner only ever found afew channels.

Regards
Ian Dobson

---

### Post by dibuntux on 2009-06-17
Ian, thank you for responding. The problem does not appear on one channel, but on entire multiplexes! I cannot lock  on all channel of RAI (National italian tv, member of the DVB committee) MUX B... but I can lock on RAI MUX A. I cannot lock on all channel on Mediaset (a multinational broadcaster) MUX A, but it works on all channels on Mediaset MUX B. I cannot lock on MUX TIMB1 (Telecom italia media broadcast, also a multinational) who also re-bradcasts BBC and France24, but can lock on MUX TIMB2...
and so on. So half the channels work and the other half does not.

But they ALL lock if I use VLC, Kaffeine, scan, so the problem is just with MythTV. They also work fine with a normal STB tuner.

And no, I cannot import a channel.conf scan because it does not work with DVB-T; it does perfectly with DVB-S.
This is a known problem since version 7.10 - 

Importing channel.conf does not work with DVB-T, like tuning directly. You can only scan for the preset countries.

I agree with you - something transmitted by the mux just confuse mythtv and generate partial or no lock. Sometimes I watched those channels for weeks, then one day they are not visible anymore - and it is not a matter of signal strenght.

But this is definitely a mythtv problem, since all other programs work fine (even Hauppage TV on Windows).

Any ideas? TIA

---

### Post by ian dobson on 2009-06-17
Hi,

Why not just download and compile wscan yourself. It's not that hard and the instructions on the web page are easy to follow.

wscan can scan all the frequencies looking for a valid DVB signal and the streams contained and can write the info to a channels.conf file that you can import into mythtv/use as a starting point for the scan.

I've used wscan with dvb-c and dvb-t with ubuntu 7.10 - 8.10 without any problems. Maybe the packaged version is screwed up?

The problem is that the MythTV channel scanner isn't the most intelligent/it doesn't handle stream errors/non-conform streams that well. one thing to try is to increase the tuner tuning timeout. For my DVB-c card I found that between 700ms-1500ms was the best value for me.

Regards
Ian Dobson

---

### Post by Triptol on 2009-06-17
There are some threads about DVB-T tuning. My idea at the moment is that it is broken in mythtv-setup (you can search on unable to open card).

My solution for the problem was phpmyadmin on the webserver and enter the channel numbers myself. Now this is not something I can recommend, but if you know what I am talking about it might be something for you as well.

If you do, please make sure you get the references setup correctly.

---

### Post by dibuntux on 2009-06-18
Ian, thank you again for helping, but no, it does not work.

1) I got wscan and generated a scan file. It finds all channels ok.
2) the file imports fine in Kaffeine, that also finds all channels and let you organize & filter them in an elegant way (as it should be in 2009...)
3) in myth the file gives "Failed to decode channels.conf"
4) if I use scan (who also find all channels just fine) to generate the channels.conf file, the file is imported ok, but I get timeout - no signal on all transponders.

So, I'm at the same point as my first message. Myth is a jewel and I love it - but scan is mess in general and NOT working for DVB-T.

Why cannot the nice folks at myth just copy the Kaffeine system? It is Open Source... they do not have to invent it.

Any more ideas? TIA

---

### Post by ian dobson on 2009-06-18
Hi,

Have you tried w_scan with the -X  option so that it creates a tzap file which mythtv can import. The "Failed to decode channels.conf" sounds like you didn't use the -X option.


Regards
Ian Dobson

---

### Post by dibuntux on 2009-06-19
Thank you Ian...Ooops, I used -x instead of -X (capital)...anyway, does not work either. The file is now recognized by myth, but produce the same results as scan: 
timeout scanning - no signal.

If I scan from myth setup using a variety of country (france, spain, germany & UK), I can find most of the channels - but then they DO NOT WORK - always partial or no lock.

So, if there is something not standard it is myth. I live in Rome, where millions of DVB-T decoders and TV with integrated decoders work with those channels, kaffeine, VLC and all other programs work with those channels on my HW. Just myth... so sad...

Any more ideas? TIA
Dave

---

### Post by ian dobson on 2009-06-19
Hi,

Maybe try increasing the tuning timeout abit, in mythsetup tuners.

MythTV tunes to a channel, waits this defined time and expects a perfect data stream to be comming from the tuner card, and if not it just fails. Try setting this value to maybe 1500ms and see if that helps.

Regards
Ian Dobson

ps. Don't give up, when MythTV works it's wonderful, I've not seen a commercial for weeks. OK my wife complains that the pee breaks are missing but that's a small price to pay. :D

---

### Post by dibuntux on 2009-06-20
Ian, thanks again. Already tried with different timeouts. I have it at 1500 for signal and 3000 for tuning - the same, no lock. Something in the stream just fools myth in same way.

I will not give up, but waiting for something to happen or a new idea.

Thank you anyway.

---

### Post by dibuntux on 2009-06-23
Ian, just increased timeout to signal 2000 and 4000 for tuning. Nothing, either partial or no lock.

But I deleted all channels again, with a fresh start of the system, and loaded the channels.conf file generated with w_scan -X: I was now able to get all channels on board.

Then the result is the same, partial or no lock on most channels, but some works. The strange is that some channles are transmitted on more than one multiplex: on one they do not work and on the other they do work. Really odd.

Still, they all work with Kaffeine or VLC... so sad...

---

### Post by dibuntux on 2009-07-27
Ehi, is it possible that I'm the only one with this?

I came back after one month, upgraded all files, and I'm exactly at the same point...

How comes that MythTV does not work were VLC and other programs just work... ON THE SAME HARDWARE...

Please, anyone with a new idea? TIA:(

---

### Post by utar on 2009-07-27
Can you post the backend and frontend logs when you are trying to tune to a channel and when you are performing a channel scan in mythbackend (just rescan one multiplex which isn't working).  That may give some clues.

---

### Post by My Name on 2009-07-28
Have you tried modifying the Frequencies for each multiplex?
I have to do this in London.
The scan would create frequencies like 569888888
This would not tune in to any channels on this multiplex, but if I round the number up to 570000000 it works perfectly.
I found these correct frequencies when I tested my DVB stick in windows.
Have a look...

---

### Post by dibuntux on 2009-07-29
Utar, Myname, thanks for your help. I will try to post the logs as soon as I can. But, besides the scan, which IS a mess in Mythtv, the real problem is locking on to channels.
Using wscan, I found a way to scan the multiplexes, if you see previous posts, but the problem of locking on channels that Myth recognize is the one.
Frequencies are OK, since when they started the switch over to all digital TV here, the signal strength is the highest. The problem is that most of the channels just give partial lock or no lock! Same exacts frequencies tune perfectly with VLC, Kaffeine or any other DVB linux program... it is just myth... 

...aaargh, I had to manually program a recording of LOST on DVB satellite to overcome the lack of DVB-T...

I'm not at home - I will let you know... in the meantime, thanks again for helping!
Dave

---

