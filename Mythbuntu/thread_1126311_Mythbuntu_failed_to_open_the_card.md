---
title: "Mythbuntu failed to open the card"
date: 2009-04-15
forum: Mythbuntu
---

### Post by simon72post on 2009-04-15
Hi 

Please can someone help?

I have a computer running mythbuntu. It has been running mythbuntu fine for a few months.

Recently our local TV (south England) transmitter changed frequency. 

So I have had to re-scan my TV channels.

But whenever I try to rescan the channels I get the message "Failed to open the card"

I have tried removing the card and setting it up again in the set up screens, but this hasn't helped.

The card is detected but I am unable to scan for channels.

The DVB card I am using is a twinham DVB PCI card.


00:08.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (                     rev 11)
00:08.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11                     )

here are some more details

Settings

General
Ip address 127.0.0.1
Port 6543 status port 6544
Master backend 127.0.0.1
Port 6543
Tv format PAL
VBI none
Channel frequency try-all
Time zone for xmltv none
HD ringbuffer 9400
Backend idle 60
Jobs maximum 1
Job queue check frequency 60
Commercial flagger mythcommflag
Transcoder command mythtranscode

Capture cards

DVB :0
DVB DTV capture card (v3.x)
Device number 0
Signal time out 500
Tuning time out 3000

DisEqc unconnected

Recording option 
Max recordings 1
DVB tuning delay 0

Video source
DVB

Video source name DVB
Listings grabber transmitted guide only (eit)
Channel frequency table try-all

Input connections
DVB:0 (DVBinput) ->DVB

Channel editor
(new channel)
Video source (all)

Channel scanner
Video source DVB
Input [DVB :0] (dDVBInput)
Scan type Failed to open the card

Transport editor
&#8220;failed to prob a capture card connected to this transport&#8217;s video source. Please make sure the backend is not running


Please can someone let me know what I can do to solve the problem? Or is there a way to completely reset the mythtv database. So I can set up the TV card from scratch.

---

### Post by AlecJ on 2009-04-15
What happends after a shut down (plug removed for a min) and reboot?

I have the same with a USB type DVB-tcard, A Jap reset normally does the trick

---

### Post by simon72post on 2009-04-16
Hi 

I tried that.

But it didn't solve the problem.

---

### Post by AlecJ on 2009-04-16
Try building a new Video source called EIT set to transmitted eit guide, link your card to it and scan from there, if that works. The next thing to do would be to delete the video source, (which is out of date).

---

### Post by simon72post on 2009-05-12
Hi 

thanks for the response.
Sorry for the late reply. Very busy at the moment.

Anyway.

I deleted the video source and built a new EIT.
and It still didnt work same error.
so I deleted the DVB card and set it up again.

But still no change. when I go to scan for channels.
I get

Video: Source (blank)
Input: [DVB:0] (DVBinput)
Scan type: Failed to open the card 

If I try to continue I get the message.
Programmer error, see console

when I go to close and exit the setup pages.
I get a message card 1 (type DVBinput) is set to start on channel please add, which does not exist.

as I only have the one card installed which is DVB 0.
I am thinking the set up has got messed up and thinks there are 2 cards.

do you have any more ideas I can try.

You said the video source was out of date. How would I update it.

---

### Post by adamjseed on 2009-05-25
Just to add to this...

I have exactly the same problem with no solution (Yet)..

simon72post, I have noticed you have not set the DisEqc... Im not too sure myself to what this is but I have a feeling that it needs to correspond to your dish type, I have a quad LNB so I have set a switch with 4 ports and set the first port as a default LNB. This stopped the console error:
DiSEqcDevTree, Warning:: No Device Tree for cardid X.

That said I am in the same situation – unable to scan for channals. 

In the console, when i scan for channels i get the error:
FE_GET_INFO ioctl Failed (/dev/dvb/adapter0/frontend0)

I did get my card working on Kaffeine but when I install mythv it stops working (the tv icon goes). If i remove mythv it then works again leading me to believe that there may be some permissions problem. 


Someone please help :)

---

### Post by nasha on 2009-05-26
Have you checked that the cards firware have been correctly loaded by the kernel? I dont know the specifics for your card, but "dmesg | grep DVB" and "dmesg | grep dvb" should give you some indication. Post it here if your not sure what to look for.

---

### Post by adamjseed on 2009-05-26
Hi nasha, Thanks for the reply...

Im quite new to linux/ubuntu so i really could use your help.

here is the output of the commands:

dmesg | grep DVB
[   12.541504] cx88[0]: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69,autodetected], frontend(s): 1
[   12.782567] tveeprom 1-0050: TV standards ATSC/DVB Digital (eeprom 0x80)
[   12.945560] cx88[0]/2: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69]
[   12.945564] cx88[0]/2: cx2388x based DVB/ATSC card
[   13.029133] DVB: registering new adapter (cx88[0])
[   13.029138] DVB: registering adapter 0 frontend 0 (Conexant CX24116/CX24118)...

dmesg | grep dvb
[   12.945553] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[   12.945556] cx88/2: registering cx8802 driver, type: dvb access: shared
[   41.853205] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[   41.853211] cx8800 0000:04:02.0: firmware: requesting dvb-fe-cx24116.fw


im not too sure what they mean...
I installed my card via the instructions:
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000)

Regards

Adam

---

### Post by pju123 on 2009-05-29
> **adamjseed said:**
> Just to add to this...

I have exactly the same problem with no solution (Yet)..

simon72post, I have noticed you have not set the DisEqc... Im not too sure myself to what this is but I have a feeling that it needs to correspond to your dish type, I have a quad LNB so I have set a switch with 4 ports and set the first port as a default LNB. This stopped the console error:
DiSEqcDevTree, Warning:: No Device Tree for cardid X.

That said I am in the same situation – unable to scan for channals. 

In the console, when i scan for channels i get the error:
FE_GET_INFO ioctl Failed (/dev/dvb/adapter0/frontend0)

I did get my card working on Kaffeine but when I install mythv it stops working (the tv icon goes). If i remove mythv it then works again leading me to believe that there may be some permissions problem. 


Someone please help :)

Exactly the same here. :(

---

### Post by Triptol on 2009-05-29
Me too. I did have another thread with no results either.

Did anyone here fix the problem?

---

### Post by Neon Dusk on 2009-05-30
@adamjseed

What does 'dmesg | grep cx24116' return?

---

### Post by adamjseed on 2009-05-30
Thanks for any help Neon Dusk,

dmesg | grep cx24116 = 
[   41.853205] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[   41.853211] cx8800 0000:04:02.0: firmware: requesting dvb-fe-cx24116.fw
[   41.962320] cx24116_firmware_ondemand: Waiting for firmware upload(2)...
[   47.068695] cx24116_load_firmware: FW version 1.22.82.0
[   47.068708] cx24116_firmware_ondemand: Firmware upload complete

Triptol,
Shame about no replys, hopefully we can get it resolved in here. Out of intrest what dvb card do you have?

---

### Post by Neon Dusk on 2009-05-30
It looks like it's detected the card and loaded the firmware ok.

Are you trying to pickup Freesat channels with the card? If you are then can you try :-
Stop the mythtv-backend
sudo /etc/init.d/mythtv-backend stop

Do a scan for channels
scan -x0 /usr/share/doc/dvb-utils/examples/scan/dvb-s/Astra-28.2E | tee channels.conf

In Jaunty this should be 
scan -x0 /usr/share/dvb/dvb-s/Astra-28.2E | tee channels.conf

---

### Post by adamjseed on 2009-05-30
Neon Dusk,

My card works fine in Kaffeine, i can scan and view channels. When i install mythtv Kaffeine stops to work. The option to view tv does not appear. i dont know if *means* anything.

And let me just say thanks for the help Neon. ive been trying to get this to work for over a month now :|

i have attached the output of 
scan -x0 /usr/share/dvb/dvb-s/Astra-28.2E | tee channels.conf:
(i did stop it after a minute, if you need the full output please let me know)

It looks like it is picking up channels...

---

### Post by Neon Dusk on 2009-05-30
So in Kaffeine even with mythtv-backend stopped you lose the TV functionality (mythtv-backend will lock the card if it's running).

You should be able to use the generated channels.conf file directly in mythtv see [http://parker1.co.uk/mythtv_freesat.php](http://parker1.co.uk/mythtv_freesat.php)

Also for most people with just a single satellite dish (even if it's a quad LNB) DiSEqC should be set to 'Universal (Europe)'

---

### Post by adamjseed on 2009-05-30
Neon, Just checked, if i stop the backend i CAN then use Kaffeine.

I am just running the "scan -x0 /usr/share/dvb/dvb-s/Astra-28.2E | tee channels.conf" now which will take 20 mins or so... ill try useing that file rather than the scanning in mythtv and post back when im done.

Again thanks for the help

---

### Post by adamjseed on 2009-05-30
Neon, this is where i run into the "Failed to open the card"


i am unable to import the channels.conf or even scan for that matter. See the screen shot attached

anymore ideas?

---

### Post by Neon Dusk on 2009-05-30
You said before that you set DiSEqC as a switch with 4 inputs. Did you delete this and set DiSEqC to be a LNB then Universal Europe?

if that doesn't work then I would delete all the video sources, delete all capture cards and start the mythbackend setup again from the start using the guide that I linked to.

---

### Post by adamjseed on 2009-05-30
Yes, actually i did delete everything and set it up word for word on that guide and still get the error.

---

### Post by Neon Dusk on 2009-05-30
If you start mythtv-setup from the console do you get any further error messages?

Also what does 'ls -al /dev/dvb/adapter0/' return?

Edit: On my system I get 
```

crw-rw----+ 1 root video 212, 132 2009-05-29 15:53 demux0
crw-rw----+ 1 root video 212, 133 2009-05-29 15:53 dvr0
crw-rw----+ 1 root video 212, 131 2009-05-29 15:53 frontend0
crw-rw----+ 1 root video 212, 135 2009-05-29 15:53 net0

```

Also the mythtv user should be part of the video group

```

cat /etc/group | grep video
video:x:44:mythtv

```

---

### Post by adamjseed on 2009-05-30
Neon

ls -al /dev/dvb/adapter0/
returns
total 0
drwxrwxrwx  2 root root     120 2009-05-25 16:51 .
drwxr-xr-x  3 root root      60 2009-05-25 16:51 ..
crw-rw----+ 1 root video 212, 1 2009-05-25 16:51 demux0
crw-rw----+ 1 root video 212, 2 2009-05-25 16:51 dvr0
crwxrwxrwx+ 1 root video 212, 0 2009-05-25 16:51 frontend0
crw-rw----+ 1 root video 212, 3 2009-05-25 16:51 net0


attached is a screenshot of the mythtv terminal

---

### Post by Neon Dusk on 2009-05-30
The permissions are different from what I get (see my updated previous post)

Can you check the video group membership
```

cat /etc/group | grep video
video:x:44:mythtv

```


Also you could try mythtv-setup as root to see if you still get the same error

```

sudo /etc/init.d/mythtv-backend stop
sudo mythtv-setup.real

```

---

### Post by adamjseed on 2009-05-30
neon

Here are the results:
cat /etc/group | grep video
```
video:x:44:mythtv
```


I still get the "Failed to open the card" if i:
sudo /etc/init.d/mythtv-backend stop
sudo mythtv-setup.real

i think the differences in permissions was due to me chmod 777 the frontend0 file...

---

### Post by Neon Dusk on 2009-05-30
Sorry I'm almost out of ideas.

In the Capture Card Setup screen does it correctly identify the card as 'Conexant CX24116/CX24118 Subtype DVB-S'?

Running
```

sudo /etc/init.d/mythtv-backend stop
mythtv-setup.real -v most

```

may give more debug info.

What version of mythtv are you running?
```
dpkg -s mythtv | grep Version
```

It's it's an older version then updating to latest 0.21-fixes version may be worthwhile.

---

### Post by adamjseed on 2009-05-30
neon, 

the frontend id: 'Conexant CX24116/CX24118 Subtype DVB-S'

And the version is:
Version: 0.21.0+fixes19961-0ubuntu8

i recently did a fresh install

---

### Post by Neon Dusk on 2009-05-30
Is it Mythbuntu 9.04 (Jaunty) that you're using?

When setting up the card did you install the Kernel / v4l-dvb driver using the instructions at [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000)? As Jaunty has kernel 2.6.28 this isn't needed the card should work out of the box (you just need to get a new dvb-fe-cx24116.fw firmware file as the one in Jaunty is corrupt)

---

### Post by adamjseed on 2009-05-30
is is 9.04 im using and that was the website i followed, however i think i did install the v4l-dvb drivers as per the instructions on that site... will that cause problems?

---

### Post by Neon Dusk on 2009-05-30
I'm not sure but everything else we have checked looks fine.

---

### Post by adamjseed on 2009-05-30
ok neon, ill have a go tomorrow - maybe try a reinstall... thanks for you help!!!!!! and check back tomorrow night. ill try and let you know whats happened..

---

### Post by adamjseed on 2009-05-31
Well.....

I did a fresh install... didnt install v4l drivers and now i get passed "Failed to open the card".... 

For other people with the problem the only thing i did differently was to have the card in the pc while i installed ubuntu. (Prev i put the card in while ubuntu was already installed)

Neon, thanks again for the help.... its people like you who keep this community going.

Now.... im still haveing problems actually scaning for channels. 

if i choose
1) Full Scan (Tuned)
i get the error "Error parsing parameters
2) import channels.conf
(i have made the file) it goes to the scan screen but noting happens
3) Full scan of existing transports 
i get the error "Error tuning to transporter"
4) Existing transport scan
it goes to the scan screen but noting happens

Any ideas how to scan for the channels?

---

### Post by Neon Dusk on 2009-05-31
It looks like you're one step closer :)

Did you replace the dvb-fe-cx24116.fw firmware file?

---

### Post by adamjseed on 2009-05-31
yes, 
 
```
dmesg | grep cx24116
```
returns:
[  163.773294] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[  163.773301] i2c-adapter i2c-1: firmware: requesting dvb-fe-cx24116.fw
[  163.821819] cx24116_firmware_ondemand: Waiting for firmware upload(2)...
[  168.920638] cx24116_load_firmware: FW version 1.22.82.0
[  168.920649] cx24116_firmware_ondemand: Firmware upload complete

---

### Post by Neon Dusk on 2009-05-31
Can you try going to Full Scan (Tuned) and entering the following 
```

Frequentcy: 10714000
Polarity: Horizontal
Symbol Rate 22000000

FEC: Auto
Inversion: Auto

```

This should pick Channel 4, Film 4 etc.. the transponder details are detailed at [http://www.flysat.com/28east.php](http://www.flysat.com/28east.php)

---

### Post by adamjseed on 2009-05-31
neon,

Tried thoes settings, i didn't get the error "Error parsing parameters"

but it said Scanning.... but did noting

---

### Post by Neon Dusk on 2009-05-31
Can you double check that the DiSEqC settings are 

Type: LNB
LNB Preset: Universal (Europe)

---

### Post by adamjseed on 2009-05-31
neon, You have done it!!!!!!

Thank you soo much for persevering with me.

I definitely owe you a few beers :) (well if you are from the uk and heading to nottingham anytime soon)

I was sure i set the lnb.... but it wasnt set. 

Im using the import channels.conf. which is running now... ill let you know how i get on.

---

### Post by Neon Dusk on 2009-05-31
Glad it's finally working :D.

---

### Post by mgarl10024 on 2009-06-01
Hi,

I was wrestling with the same problem on Friday.
I would go into Mythtv-setup, select "Scan For Channels" and would get the "Failed to open the card".

A small workaround I discovered - 

1) exit back to the main mythtv-setup window
2) start tzap running (tzap -r "BBC ONE" for example).  You'll have to alt+tab to a terminal window to do this.
3) go back into the channel setup menu - mine now doesn't say "Failed to open the card" any more.
4) Flip back to the terminal window and stop tzap
5) Select scan for channels which should now work.

Sounds like a bug to me.

Incidentally, MythTv still failed to find all the channels (it got 90% of them), so I still ended up creating a channels.conf separately, then importing it in.

Hope that helps,

MG

---

