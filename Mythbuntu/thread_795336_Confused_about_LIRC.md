---
title: "Confused about LIRC"
date: 2008-05-15
forum: Mythbuntu
---

### Post by Salla101 on 2008-05-15
Sorry for my ignorance, I am just trying to get my head around all this stuff.

I have a PVR-350 using the remote that came with it.  When I had 7.10 installed it worked fine by simply selecting it on the backend config.  Now I am using (total new install) 8.04 I can not get it to work.  I have searched for days and found nothing to might explain any steps needed to get it to work.  I thought it would be as simple as 7.10 but not so much.

Also, I have made a cable that goes from the db9 serial on the PC to my RCA DRD420RE.  I assume I can change the channels on the STB with the Hauppague remote?  I also wonder if I have something programed to record when I a sleeping, will the Mythbuntu change the channel on the STB to capture my show?

Thanks!

---

### Post by gfowler on 2008-05-15
> **Salla101 said:**
> Sorry for my ignorance, I am just trying to get my head around all this stuff.

I have a PVR-350 using the remote that came with it.  When I had 7.10 installed it worked fine by simply selecting it on the backend config.  Now I am using (total new install) 8.04 I can not get it to work.  I have searched for days and found nothing to might explain any steps needed to get it to work.  I thought it would be as simple as 7.10 but not so much.

Also, I have made a cable that goes from the db9 serial on the PC to my RCA DRD420RE.  I assume I can change the channels on the STB with the Hauppague remote?  I also wonder if I have something programed to record when I a sleeping, will the Mythbuntu change the channel on the STB to capture my show?

Thanks!

You should be able to go to the Mythbuntu Control Centre from Application System.  Select Infrared Devices, a check box for 'Enable Remote Control', select the Hauppauge WinTV from the drop down box, select Apply.  The script should do the rest and you should have a working remote, or at least I did.  To check that the remote is sending codes and box is getting them go to a command line and type 'irw' (without single quotes).  Press some keys on the remote and you should see codes displayed.  If so do a Control-C to get back to the the command line.  If no codes are displayed you have troubles :), then you are at 'checking batteries, ir receiver connection, note: if you short the outside barrel of the ir-receiver plug to the computer chassis because of a mal-aligned card install it won't work, hours of hair pulling here).  Good luck

Can't help you on your particular transmitter issue as I don't have such a STB.

Jerry

---

### Post by Salla101 on 2008-05-15
> **gfowler said:**
> You should be able to go to the Mythbuntu Control Centre from Application System.  Select Infrared Devices, a check box for 'Enable Remote Control', select the Hauppauge WinTV from the drop down box, select Apply.  The script should do the rest and you should have a working remote, or at least I did.  To check that the remote is sending codes and box is getting them go to a command line and type 'irw' (without single quotes).  Press some keys on the remote and you should see codes displayed.  If so do a Control-C to get back to the the command line.  If no codes are displayed you have troubles :), then you are at 'checking batteries, ir receiver connection, note: if you short the outside barrel of the ir-receiver plug to the computer chassis because of a mal-aligned card install it won't work, hours of hair pulling here).  Good luck

Can't help you on your particular transmitter issue as I don't have such a STB.

Jerry

I do not have Hauppauge WinTV as an option.  I have listed the following Hauppage DVB's, HVR-1100 HVR-1300, Nova-T 500 and TV card.  I have selected TV Card which seems to be incorrect.

When I issue the command irw from command line I get a *connection refused*.

---

### Post by gfowler on 2008-05-15
> **Salla101 said:**
> I do not have Hauppauge WinTV as an option.  I have listed the following Hauppage DVB's, HVR-1100 HVR-1300, Nova-T 500 and TV card.  I have selected TV Card which seems to be incorrect.

When I issue the command irw from command line I get a *connection refused*.

Sorry, that's what I get for not using a net, you selected the correct card, Hauppauge TV Card. Take a look at ls -l /dev/lirc* and post the results.  There should be something like /dev/lirc0, maybe a /dev/lirc1 and a daemon /dev/lircd.  You can direct irw /dev/lircd or irw /dev/lircd1 if you have two  daemons from a remote and transmitter configured.  

Jerry

---

### Post by wolfster101 on 2008-05-20
> **gfowler said:**
> Sorry, that's what I get for not using a net, you selected the correct card, Hauppauge TV Card. Take a look at ls -l /dev/lirc* and post the results.  There should be something like /dev/lirc0, maybe a /dev/lirc1 and a daemon /dev/lircd.  You can direct irw /dev/lircd or irw /dev/lircd1 if you have two  daemons from a remote and transmitter configured.  

Jerry

Thanks Gfowler,  I will try this when I get home.  
BTW, I am Salla101 as well.  Had some issues with a password and account lock out...Anyway this is the main account.

Thanks again!

---

