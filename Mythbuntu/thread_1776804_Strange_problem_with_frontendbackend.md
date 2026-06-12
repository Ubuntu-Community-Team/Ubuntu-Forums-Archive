---
title: "Strange problem with frontend/backend"
date: 2011-06-06
forum: Mythbuntu
---

### Post by mattshaw on 2011-06-06
Hi Guys

I have a fully functional frontend/backend combo on one box (in the lounge), Mythbuntu 10.04 with 0.23 fixes. I thought I would reuse some of of my other tuner cards in a new secondary frontend/backend. I have set up a dvb-t tuner in the loft backend, and can watch live tv on the loft frontend. I can schedule recordings, and watch recordings on the lounge frontend, but cannot watch Live TV on the lounge frontend when I switch input to the tuner on the loft backend.

I can only watch live tv on the loft box itself. I have NFS mounted the /myth/tv directory, and all is setup fine

Can anyone please help ????

I still have 3 further tuners to try and setup on the loft backend

---

### Post by mattshaw on 2011-06-06
Further to the above, when I try to switch input to the tuner on the loft backend, I get a black screen, which can only be reset by restarting the gdm. It is very strange that I can schedule and watch recordings on the loft tuner, but not watch live tv.

Thanks in advance for any help

Matt Shaw

matt at shagshaw dot com

---

### Post by ian dobson on 2011-06-06
Hi,

What do you see in the frontend logs (/var/log/mythtv/)?

It sounds alot like a timing problem. Buffering/transfering data over the network takes maybe 1-2seconds longer than from local which could be enough to cause the frontend to timeout.

Regards
Ian Dobson

---

### Post by mattshaw on 2011-06-07
Hi

Thanks for your response Ian

When I go into LiveTV on the lounge frontend it starts with the local dvbt tuner. The first 2 lines below show me changing to bbc1 on the local tuner, I then try to switch input to the remote tuner in the loft. Here is the entry from the mythfrontend.log :


2011-06-07 20:34:55.830 ProgramInfo(): Updated pathname '':'' -> '1001_20110607203455.mpg'
2011-06-07 20:34:55.831 ProgramInfo(): Updated pathname '':'' -> '1001_20110607203455.mpg'
2011-06-07 20:34:55.873 msg: On known multiplex...
2011-06-07 20:34:56.932 NVP(0): Forcing decode extra audio option on (Video method requires it).
2011-06-07 20:34:59.358 AFD: Opened codec 0xaced1fa0, id(MPEG2VIDEO) type(Video)
2011-06-07 20:34:59.358 AFD: codec MP2 has 2 channels
2011-06-07 20:34:59.358 AFD: Opened codec 0xad62c070, id(MP2) type(Audio)
2011-06-07 20:34:59.358 AFD: codec MP2 has 1 channels
2011-06-07 20:34:59.358 AFD: Opened codec 0xb14db5f0, id(MP2) type(Audio)
2011-06-07 20:34:59.358 AFD: Opened codec 0xacec94c0, id(DVB_SUBTITLE) type(Subtitle)
2011-06-07 20:34:59.595 WriteAudio: buffer underrun
2011-06-07 20:34:59.641 NVP(0): prebuffering pause
2011-06-07 20:34:59.642 NVP(0): prebuffering pause
2011-06-07 20:34:59.643 NVP(0): prebuffering pause
Unknown ResidentProgram SBI
2011-06-07 20:35:28.232 MythContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2011-06-07 20:35:28.233 Using protocol version 23056
2011-06-07 20:35:28.262 ProgramInfo(): Updated pathname '':'' -> '1001_20110607203455.mpg'
Starting mythfrontend.real..
2011-06-07 20:36:00.930 mythfrontend version: branches/release-0-23-fixes [26863] [www.mythtv.org](www.mythtv.org)
2011-06-07 20:36:00.930 Using runtime prefix = /usr
2011-06-07 20:36:00.931 Using configuration directory = /home/matt/.mythtv
2011-06-07 20:36:00.931 MediaRenderer::HttpServer Create Error
2011-06-07 20:36:08.277 TV Error: StartRecorder() -- timed out waiting for recorder to start
2011-06-07 20:36:08.277 TV Error: LiveTV not successfully started

Any ideas ????

---

### Post by ian dobson on 2011-06-07
Hi,

Yep, it looks like a timeout. Maybe try increasing the tuning timeout for yout tuners, through mythtv-setup.

Note: I don't use the LiveTV function in Mythtv as it's not the most stable function.

Regards
Ian Dobson

---

### Post by mattshaw on 2011-06-08
Thanks again Ian
 
I did see that setting last night, and I did think about changing it. I think it is set to 5 minutes ????    Should I increase or decrease this value ???
 
thanx in advance

---

### Post by ian dobson on 2011-06-08
Hi,

I imagine it's 5seconds. Maybe try kist increasing it to 10,restart backend and test. If it doesn't work increase and repeat. 

I wouldn't go much higher than about 30 seconds.

Regards
Ian Dobson

---

