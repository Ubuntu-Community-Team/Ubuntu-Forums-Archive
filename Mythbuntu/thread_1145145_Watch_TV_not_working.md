---
title: "Watch TV not working"
date: 2009-05-01
forum: Mythbuntu
---

### Post by Cons on 2009-05-01
Hello everyone, 
I did not get the tv running at my Mythbuntu. I am using Technotrend S2-3200 (budget), Mythbuntu 9.04 and kernel 2.6.29! I changed the kernel to get the tv card running and I successfully checked it with xine (xine -g stdin://mpeg2 < /dev/dvb/adapter0/dvr0). 
I followed this ([http://www.mythtv.org/wiki/User_Manual:Setting_up_DVB-S_for_satellite](http://www.mythtv.org/wiki/User_Manual:Setting_up_DVB-S_for_satellite)) instruction and added programs to my mythtv. When I go to "Watch TV" the screen simply keeps black. 

Any hints?
Thank you for your help. 
Cons 
-------------------
mythtv-common:
  Installiert: 0.21.0+fixes19961-0ubuntu8
  Kandidat: 0.21.0+fixes19961-0ubuntu8
  Versions-Tabelle:
 *** 0.21.0+fixes19961-0ubuntu8 0
        500 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) jaunty/multiverse Packages
        100 /var/lib/dpkg/status

at the end of the mythfrontend.log: 
2009-05-01 17:27:09.866 NVP: Prebuffer wait timed out 10 times.
2009-05-01 17:27:11.977 NVP: Prebuffer wait timed out 10 times.

---

### Post by AlecJ on 2009-05-01
> **Cons said:**
> 
I followed this ([http://www.mythtv.org/wiki/User_Manual:Setting_up_DVB-S_for_satellite](http://www.mythtv.org/wiki/User_Manual:Setting_up_DVB-S_for_satellite)) instruction and added programs to my mythtv. When I go to "Watch TV" the screen simply keeps black. 


Do you get the on-screen display?
Did you search for channels and fill the data base?
If your in the UK I have a list of channels that may help you.

---

### Post by Cons on 2009-05-02
Hello AlecJ, 
thank you for your answer. 
> Do you get the on-screen display?
Did you search for channels and fill the data base?
I successfully searched for channels and I can in the frontend switch between these channels. The screen simply keeps black. Do I need anything else because my card TT S2-3200 is a budget card? 
Kind regards 
Cons

---

### Post by AlecJ on 2009-05-02
So you have channels and you get the on screen display telling you that the tuner has locked on?
Is there any sound?
What happends in the guide do you get a list of programs.
As you get video with Xine this, to me, sounds more like a frontend issue with the display card, is there a remote front end PC on the network able to view the backend?

---

### Post by Cons on 2009-05-03
Hi AlecJ, 
I don't get a sound but this is a system problem (no sound at all) and I got the channel list. I do not have a remote front end. 
I tried so long and finally I failed. I do not see any way get it running. I checked kaffeine and this seems to run, even the HD stuff. 
Thank you for your help AlecJ

---

