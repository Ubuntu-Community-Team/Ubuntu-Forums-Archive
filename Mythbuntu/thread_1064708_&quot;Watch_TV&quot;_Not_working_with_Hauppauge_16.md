---
title: "&quot;Watch TV&quot; Not working with Hauppauge 1600"
date: 2009-02-09
forum: Mythbuntu
---

### Post by insanity54 on 2009-02-09
I'm using Mythbuntu 4.10 64-bit. I have a Hauppauge 1600 and 1250. Ubuntu doesn't see the 1250. Ubuntu does sees the 1600 and I followed the installation guide for the 1600 on the mythbuntu wiki.

"Watch TV" in mythtv doesn't work. I get a quick black screen then it goes back to the menu. Scanning for channels works perfectly, but I have never been able to view tv through mythbuntu.

I have never been able to add the 1600 to the correct type of source. I am only able to add it to MPEG2 and Analog V4L. Half the time, (seems random) when trying to add it as MPEG2, it shows, "Failed to open" When I attempt to add the 1600 to the correct type (DVB DTV capture card (v 3.x)) It says "Samsung S5H1409 QUAM Subtype...(can't see the whole thing)" in the probed info. It seems like it's not the right card (I don't have any Samsung cards) Adding the samsung card shows does not work either. 

here is my mythbuntu log:
[http://mythbuntu.pastebin.com/f6cdfe5d1](http://mythbuntu.pastebin.com/f6cdfe5d1)

Someone point me in the right direction on how to get either of my tuner cards to work with DTV?

---

### Post by klc5555 on 2009-02-09
> **insanity54 said:**
> I'm using Mythbuntu 4.10 64-bit. I have a Hauppauge 1600 and 1250. Ubuntu doesn't see the 1250. Ubuntu does sees the 1600 and I followed the installation guide for the 1600 on the mythbuntu wiki.

"Watch TV" in mythtv doesn't work. I get a quick black screen then it goes back to the menu. Scanning for channels works perfectly, but I have never been able to view tv through mythbuntu.

I have never been able to add the 1600 to the correct type of source. I am only able to add it to MPEG2 and Analog V4L. Half the time, (seems random) when trying to add it as MPEG2, it shows, "Failed to open" When I attempt to add the 1600 to the correct type (DVB DTV capture card (v 3.x)) It says "Samsung S5H1409 QUAM Subtype...(can't see the whole thing)" in the probed info. It seems like it's not the right card (I don't have any Samsung cards) Adding the samsung card shows does not work either. 

here is my mythbuntu log:
[http://mythbuntu.pastebin.com/f6cdfe5d1](http://mythbuntu.pastebin.com/f6cdfe5d1)

Someone point me in the right direction on how to get either of my tuner cards to work with DTV?

Your 1600 QAM tuner is registering correctly (as Samsung), and your experience with the analog is normal --Myth frequently only allows you to add the analog half as v4l (which won't work), but after you save this, then you can re-enter the card configuration and change the analog to the correct mpeg2 and save again.

You say that your scans are working. So that after the scans (digital & analog) you're finding stations (with channel lock and tables), and thereafter, after proceeding to the end of the configuring inputs menu and exiting, the found channels can be seen in the Channel Editor (no sense actually editing them at this stage). When you exit the Channel Editor, you need to then  set up at least one directory as your Default Storage Group in "Storage Groups" and then, upon exiting Storage Groups and "escaping" from the backend setup menu, you have to be sure that mythfilldatabase runs successfully, otherwise none of your hardware settings nor channels nor directories will get saved to the database.

Now there is no real thing as LiveTV in Mythtv --everything that the tuners tune is recorded to the Default Storage directories and you are then watching that recording some 4 to 30 seconds later. 

So when Mythtv tries to tune "LiveTV" and kicks you back to the main menu, the  usual culprit is that the user "mythtv" doesn't have proper read-write permissions to one or more of the directories in the Default group. Each directory in the Default group must have its owner and group set to "mythtv" (not "root" or your username), and the permissions on each of these directories should be set to 775, 776, or (maybe) 777. If one storage directory in the group doesn't measure up, Myth kicks you out.

---

### Post by insanity54 on 2009-02-10
You sir... Are a genious!

I've spent about a week on this project trying to get it running myself, but I never could! 

You were right, The problem was with the permissions and user of the storage directories. I had three storage directories set up. livetv, default, and db. I ran the following commands in the terminal:

```

sudo chmod 775 livetv
sudo chmod 775 default
sudo chmod 775 db

sudo chown mythtv:mythtv livetv
sudo chown mythtv:mythtv db
sudo chown mythtv:mythtv default

```

Another problem was with the input connections. I figured this out by looking in the mythtv backend logs. It gave me an error, "ChannelBase(1) Error: InitializeInputs(): Could not get inputs for the capturecard. Perhaps you have forgotten to bind video sources to your car's inputs?" I had set them up before, but I had neglected to redo them after I had deleted all my capture cards to start fresh.

After that, I am able to see analog tv. The digital side is just giving me constant black for about ten seconds before it bounces back to the menu. I guess I'll have to mess around with that some more. Any ideas on that?

---

### Post by klc5555 on 2009-02-10
> **insanity54 said:**
>  The digital side is just giving me constant black for about ten seconds before it bounces back to the menu. I guess I'll have to mess around with that some more. Any ideas on that?

Your digital with the 1600 may just suck. I use 3 different models of dvb-capable tuners: pchdtv5500, the haupauge 1600, and one of the newer-style cheap AverMedia A180s (where they've removed all the obsolete analog hardware). Whereas the 5500 and the A180 catch all my 21 available clear QAM stations, with signal-strength in the 96%-99% range, my 1600 has never, ever, been able to find more than 7. And to do that, I needed to put a little Motorola broadband amp on it; without the amp the 1600 could only find 2 stations. Scanning in Mythtv with the 1600 always produces signal strength readings of 1% or less. After fiddling with the 1600 for a month or two, I decided to use it as an analog-only tuner, since that was the primary function I had purchased it for.

That being said, the digital half of the 1600 works accepably for some people. Yours is presumably one of the QAM models, not one of the VSB-only ones. (The only way to know for sure is to check the sticker on the tuner-module itself --the box and documentation are no help.) If scanning on this card in Mythtv in "Input Connections" is not producing acceptable results, then you will likely have better results using the command-line "scan" tool that is supplied with "dvb-apps" at linuxtv.org.  The basic use of the tool set is described here: 

[http://www.mythtv.org/wiki/Adding_Digital_Cable_Channels_(For_ATSC/QAM_Tuner_Cards_--_USA/Canada](http://www.mythtv.org/wiki/Adding_Digital_Cable_Channels_(For_ATSC/QAM_Tuner_Cards_--_USA/Canada))
 
In running the utility, you redirect its output to a text file that you can call "channels.conf"

./scan atsc/us-Cable-Standard-center-frequencies-QAM256 > channels.conf

And, assuming that the utility eventually found some channels and the file channels.conf is not blank, you can have Myth load this "channels.conf" rather than perform a "full scan" in the Input Connections setup for the dvb tuner. Then, the Channel Editor phase of the setup proceeds as usual.

If your 1600 gives you a significantly different subset of QAM stations than any other dvb tuner you have, but you wish to continue using the dvb side of the 1600, you may wish to configure a special Video Source in the backend setup just for the dvb 1600 alone, so that when Mythtv is assigning shows to dvb tuners for scheduled recordings, it will assign to the 1600 only things on channels it can see, rather than on channels it can't see. 

Good luck! Hope your 1600 ends up working better than mine! :)

---

### Post by insanity54 on 2009-02-13
Hmm, well I guess I've got some tinkering to do. Thank you very very very much for your help!

---

