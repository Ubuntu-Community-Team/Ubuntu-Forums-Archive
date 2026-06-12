---
title: "Error finding Channels"
date: 2010-11-23
forum: Mythbuntu
---

### Post by adamjseed on 2010-11-23
Hello,

I could really do with some help, I have been trying to get this to work for ages now.

I have a NOVA HD-S2 card which I have last month had working in a mythbuntu 10.10 install. My problem was that my remote front end was not working as it was ubuntu 10.04. So I decided to down grade my mythbuntu server to 10.04. 

My issue is that I cant find any channels and I read about every problem across the internet but to no solution. I even tried to install 10.10 again but I now cant get that to work so I guess I could do with some help identifying what I doing wrong here. 

Here is where I am at:

Install Mythbuntu 10.04
Installed the new firmware ([http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000))
```
wget http://www.hauppauge.de/software/mce/88x_2_122_26109_WHQL.zip
unzip -jo 88x_2_122_26109_WHQL.zip Driver88/hcw88bda**.sys
sudo dd if=hcw88bda.sys of=/lib/firmware/dvb-fe-cx24116-1.22.82.0.fw skip=75504 bs=1 count=32501
sudo ln -s /lib/firmware/dvb-fe-cx24116-1.22.82.0.fw /lib/firmware/dvb-fe-cx24116.fw
```
Then to test:
```
sudo dmesg | grep cx24116
[  751.323004] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[  751.323016] cx88-mpeg driver manager 0000:13:00.2: firmware: requesting dvb-fe-cx24116.fw
[  751.348051] cx24116_firmware_ondemand: Waiting for firmware upload(2)...
[  756.436335] cx24116_load_firmware: FW version 1.22.82.0
[  756.436342] cx24116_firmware_ondemand: Firmware upload complete
```

Which I think shows my firmware is getting uploaded correctly. 

I then tried scanning for channels using 
```
scan -x0 /usr/share/dvb/dvb-s/Astra-28.2E | tee channels.conf
```

Which found a whole range of channels.

I now moved on to setting up Mythtv backend with the following settings:
-----------------------------------General config
Local Backend: 192.168.1.xxx
Master Backend: 192.168.1.xxx
TV Format: PAL
Channel Frequency Tables: Europe-West	
-----------------------------------Capture Card
Card Type: DVB DTV capture card (v3.x)
deseqc = LNB Europe(Universal)
-----------------------------------Video Source
Video Source Name: VS1
Lister Grabber: Transmitted Guide Only (EIT)
Channel Frequency Table: Europe West
----------------------------------Input connectors
Scan Type: Full(Tuned)
Freq: 10714000
Polarity: Horizontal
Symbol rate: 22000000
Mod Sys: DVB-S
FEC: 5/6
Modulation: QPSK
Inversion: leave at auto
Rolloff: leave at 0.35

When I hit next is the error I get

Failed to find any channels.

As I say I have had this card working last month but I cant set it back up. Can anyone help me?

---

### Post by adamjseed on 2010-11-26
Has anyone got any ideas on where I can begin to start to debug this?

---

### Post by nickrout on 2010-11-26
are you sure your lnb values are right?

try FEC auto?

---

### Post by adamjseed on 2010-11-26
Thanks for the reply nickrout.

I tried FEC to auto but to no effect

I think your on to something with the LNB. It is the only element of the whole set-up I am unsure about. I have a standard uk SKY dish pointing at astra. As far as I know it is a single LNB and I have configured it as universal Europe. 

Any suggestions on the configuration of this?

---

### Post by nickrout on 2010-11-26
I found this:

[http://www.gossamer-threads.com/lists/mythtv/users/290575](http://www.gossamer-threads.com/lists/mythtv/users/290575)

but couldn't find anything specific about what sort of LNB sky uses in the UK

---

### Post by adamjseed on 2010-11-28
I have tried a few settings now with the LNB but still getting no channels found. Any other ideas?

---

### Post by bance on 2010-11-29
You have to make sure the LNB setting saves...... Sometimes I had to set it three or four times before it would stick.

Hope this helps,

Steve.

I mean in the card set up dseq section

---

