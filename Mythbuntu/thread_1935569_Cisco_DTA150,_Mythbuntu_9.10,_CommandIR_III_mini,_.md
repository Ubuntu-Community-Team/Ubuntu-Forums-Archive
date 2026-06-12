---
title: "Cisco DTA150, Mythbuntu 9.10, CommandIR III mini, external channel change command"
date: 2012-03-04
forum: Mythbuntu
---

### Post by dominique_emond on 2012-03-04
Hi everyone,

I just spent 2 days getting CommandIR III mini working with my Mythbuntu 9.10 , and two ROGERS CABLE issued
Cisco DTA150 devices (digital to analog converter) which each connect to an analog video tuner (recording) card
that I use to record TV shows.

I have a front end which connects to a separate backend. Only my backend does the recording.

I did not need to use LIRC codes etc.  I just used commandir_record  to record each numeric button (0-9) and stored them
in separate files : e.g.  cicso_0 , ... cisco_9 etc

I tested each file using : e.g. (for changing to channel 30 on emitter 1)  commandir_send -d200 -e1 cisco_3 cisco_0 

SOmetimes you need to re-record a particular digit because it is wonky.
(By the way, remove the mouse IR receiver when recording button codes. Instead aim your cisco remote
downwards (1cm away) from the lonely  =)) light  completely opposite to power light  C-  )

I tailored my OWN channel changing script which only takes in ONE parameter (e.g. the channel number)
instead of 4 parameters that the example has.

put your channel change script in /usr/local/bin , as well as the cisco_n  files .

In mythtv backend setup, in the 'external channel change command', specify entire path to this .sh file

Test out your script from that location.

My output script creates a file telling me what parameter was passed to what script at what time. I specify an
absolute path to this file in /home/mythtv  (since the myth backend uses this id when running)... not your current userid you may be playing with now.

I then noticed that my script WAS being called by mythtv  for recordings and when I was browsing live tv on my frontend.
BUT... the channels weren't changing.  I turned on  mythtv-backend -v all , to look at any errors.

I noticed that WHATEVER was calling my script could not resolved my cisco_n files even though they were beside my
channel change scripts.  So in my last ditch effort, I fully qualified their path with /usr/local/bin/cisco_n .

THIS completed the adventure!! I can change channels using my streamzap (previously configured 2 years ago) to change channels in Watch Live TV on my frontend, my backend gets the request from frontend, and executes my change script, which tells commandir to change the channel.  ALSO when a recording needs to take place, mythtv backend calls the script for the particular card, changes the channel, and recordings starts on proper channel.

As a side benefit, my two output files: /home/mythtv/passed_channel_emitter1.txt and *_emitter2.txt can always be referenced as a debugging tool, should I need it in the future.

I have placed  my recorded cisco button files, and readme.txt, and required .deb files (libusb stuff for mythbuntu 9.04 (i actually used these for 9.10), and change scripts etc on DROPBOX



[http://dl.dropbox.com/u/27797280/cisco_dta_150/cisco_dta150_commandIRIIIMini_Stuff.tar](http://dl.dropbox.com/u/27797280/cisco_dta_150/cisco_dta150_commandIRIIIMini_Stuff.tar)

[http://dl.dropbox.com/u/27797280/cisco_dta_150/cisco_dta_150_remote_codes.tar](http://dl.dropbox.com/u/27797280/cisco_dta_150/cisco_dta_150_remote_codes.tar)



I hope this helps someone.

---

### Post by codehopper on 2012-03-08
dominique_emond, thanks very much for your post.  

What tv cards/equipment are you using under linux?  

I currently have the hauppauge 2250 but there are no linux drivers for the analogue tuner side, so I am looking for a card that has reliable linux support with ir blaster output to control the dta50.

Thanks

---

### Post by dominique_emond on 2012-03-16
Backend:

Hauppauge WinTV-HVR1600 Dual TV Tuner
Hauppage PVR150
Seagate Barracuda 7200.12 500GB Hard Drive
Samsung TS-H663B DVDRW Drive
StarTech.com PCIe 10/100/1000 Ethernet Card
Centon 1024MB PC6400 DDR2
Biostar TA780G M2+ Motherboard & AMD Athlon 64 X2 5200+ Processor Bundle



Front end:

Old Compaq desktop
EVGA GeForce 8600 GT 512MB PCIe - SLI Ready
(For front end so I can connect to TV)

Mythbuntu 9.10

Bought these supplies 2 years ago I believe.

---

