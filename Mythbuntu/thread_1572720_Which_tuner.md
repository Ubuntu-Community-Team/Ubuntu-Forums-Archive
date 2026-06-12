---
title: "Which tuner?"
date: 2010-09-11
forum: Mythbuntu
---

### Post by badger_fruit on 2010-09-11
Hello everyone. 

I have 2 x PCI TV-Cards in my Myth TV Server; both Hauppage NOVA T500's. One is a "dual head" and the other a single head (it was a hand-me-down).

**In myth-web > back-end status, it tells me there are 6 tuners, how do I know which tuner is associated with which physical card??**

I am having issues with tuners 1 and 2 so need to know which card they're associated with to narrow down the search for the problem!

Thanks for any ideas!

---

### Post by ian dobson on 2010-09-12
Hi,

The only way to see which "virtual tuner" is connected to which actuall tuner is through the mysql database.

If you download the MythTV checker script from my website, I've just added the code to dump the tuner number to the code:-

```

[OK].Found 2 video sources
[OK].Videosource 2 'digital' has a EPG source defined (tv_grab_ch_search)
[OK].Videosource 3 'itgate' has a EPG source defined (/bin/true)
[OK].Videoinput 2 has 4 card inputs defined
[OK].Videoinput 3 has 2 card inputs defined
[--].Checking start channel for each cardinput
[--].Checking channel change script for each cardinput
[--].Cardinput (5) has a channel change script defined '/data/bin/itgate-changea.sh'
[OK].Channel change script '/data/bin/itgate-changea.sh' the permissions 0777 (rwx rwx rwx) owner (id) group (id)
[--].Cardinput (6) has a channel change script defined '/data/bin/itgate-changeb.sh'
[OK].Channel change script '/data/bin/itgate-changeb.sh' the permissions 0777 (rwx rwx rwx) owner (id) group (id)
[OK].All InputCards are linked to a videosource
[OK].Videosource 2 has 56 visible and 75 invisible channels defined
[OK].Videosource 3 has 16 visible and 0 invisible channels defined
[OK].cardinput 1 type DVB exists as device (/dev/dvb/adapter0/frontend0), file permissions are 0660 (rw- rw- ---) owner (root) group (video)
[OK].cardinput 2 type DVB exists as device (/dev/dvb/adapter0/frontend0), file permissions are 0660 (rw- rw- ---) owner (root) group (video)
[OK].cardinput 3 type DVB exists as device (/dev/dvb/adapter1/frontend0), file permissions are 0660 (rw- rw- ---) owner (root) group (video)
[OK].cardinput 4 type DVB exists as device (/dev/dvb/adapter1/frontend0), file permissions are 0660 (rw- rw- ---) owner (root) group (video)
[OK].cardinput 5 type FREEBOX got 1412 bytes from web page (M3U) file 'http://localhost/itgate1.m3u'
[OK].cardinput 5 has 16 Channels defined in m3u file
[OK].cardinput 6 type FREEBOX got 1413 bytes from web page (M3U) file 'http://localhost/itgate2.m3u'
[OK].cardinput 6 has 16 Channels defined in m3u file
[OK].All channels have a valid videosource
[OK].All dtv_multiplex channels have a valid videosource
[OK].All channel entries have a valid dtv_multiplex
[OK].All dtv_multiplex entries have a valid channel
[OK].All EPG entries have a valid channel
[OK].Found 3 storage groups for 'alpha2'

```

Hope this helps.

Regards
Ian Dobson

---

### Post by badger_fruit on 2010-09-14
Hi Ian
Thanks for the prompt reply; I tried your script and it showed me which tuner was related to which input.  I have gone into Myth back-end and de-allocated the tuner from the input source.  
 
Now I know which tuner definition it is in Myth, **how do I determine which physical card it is?**
 
The setup is as attached, a single aerial feeds into a 4-way booster which feeds into three tv inputs on two physical cards (booster socket 1 --> Nova T500, booster socket 2 --> Nova T500D port 0 and booster socket 3 -->Nova T500D port 1).

---

### Post by AKADAP on 2010-09-14
> **badger_fruit said:**
> Hi Ian
Thanks for the prompt reply; I tried your script and it showed me which tuner was related to which input.  I have gone into Myth back-end and de-allocated the tuner from the input source.  
 
Now I know which tuner definition it is in Myth, **how do I determine which physical card it is?**
 
The setup is as attached, a single aerial feeds into a 4-way booster which feeds into three tv inputs on two physical cards (booster socket 1 --> Nova T500, booster socket 2 --> Nova T500D port 0 and booster socket 3 -->Nova T500D port 1).

Tune Live TV to a channel (hit the 'm' key on your keyboard to bring up a menu, on the change input page, the input that does not show up in the list is the one you are using). Disconnect the cable to the card you think you are using. if the live TV stops, you know that you are correct as to which card you were using.

---

