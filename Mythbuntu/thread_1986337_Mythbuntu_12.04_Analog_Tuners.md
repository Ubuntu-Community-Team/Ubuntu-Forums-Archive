---
title: "Mythbuntu 12.04 Analog Tuners"
date: 2012-05-24
forum: Mythbuntu
---

### Post by jlp_engineer on 2012-05-24
I must say it is nice to be back using Mythbuntu - sort of.  Let me explain.  I started out years ago using some PVR-150's in a combined BE/FE system with version 8.04.  Years go by, some things happen, and I recently began piecing together a more elaborate system, with separate FE's, and six tuners (analog and digital) split between a master BE and a slave BE. When I loaded 11.10, my P4 systems locked at boot, so I used 11.04 and everything went smoothly until I tried to watch analog channels and particularly change from one analog channel to another.  

So then I switched to LinHES for a while, until I ran into the same problem once I enabled VBI closed captions.  I then found out that the default settings for MPEG-2 encoder cards (horizontal and vertical resolutions) were set incorrectly.  By then 12.04 came out so I went back and reloaded my Master BE with the three digital tuners and my Slave BE with my three PVR150's, and found that I no longer got distorted video on my analog channels after correcting the invalid settings for the recording profiles.  

But now, when I moved to add a remote FE, I found that the digital channels are working, but when I switched to an analog tuner I get a blank screen and the FE is unresponsive.  I tried one of the FE's on the BE or SBE (can't remember) and it did the same thing.  

NOTE: I have six tuners total between the MBE and the SBE, but for some reason the status screen shows 9 tuners, with three unavailable.  

I am hoping I just have a setting wrong somewhere, but I don't know where to start looking.  Has anyone else run into this sort of problem?  Any suggestions?

TIA

---

### Post by nickrout on 2012-05-25
Make sure you started the SBE after the MBE.

Look at your logs.

As to number of tuners, which are duplicated? which are unavailable? Are your digital tuners set up with two virtual tuners per physical tuner (I think thats the default, digital TV can record multiple shows from the same multiplex).

The more I think about it the more it sounds like the 6 available tuners are the 3 digital tuners, each as 2 virtual tuners (3x2=6) and the 3 analogue are "unavailable" due to some problem with the SBE not being recognised. Restart the SBE backend service (sudo service mythtv-backend restart)(the "linux way")  or simply reboot it (the "windows way").

---

### Post by jlp_engineer on 2012-05-25
New information.

When I use the frontend on the SBE, the one with the analog tuners, this works as expected.  I can switch back and forth between the digital tuners and the analog ones, and there are no problems. 

The problem comes when I use the Frontend on the Master Backend that has the digital tuners in it.  When I fire up the FE on the MBE and watch LiveTV, I get a channel from one of the digital tuners.  So far, so good. But when I switch to one of the analog tuners, the FE becomes unresponsive.  I then went to one of my remote frontends, and fired up LiveTV, and one of the digital tuners came up and displayed a channel normally.  I then went to switch to one of the analog tuners on the Slave Backend, and this FE also becomes unresponsive.  ](*,)

OK, so the FE on the SBE works with all tuners (digital and analog), but the FE on the MBE and the remote FE don't (digital only). :confused: Also, I took another look at the tuner list on the status page, and all tuners are listed as available, contrary to my first posting.  And I expect that you are right Nick, that the "extra" tuners listed are multiplex streams (2 per tuner) from the digital cards.  That makes sense, but is not a clear way of displaying this on the status page - no matter.

I took a look at the FE log on the remote FE and it claims that the MBE (I assume master) is not responding, yet the IP address for the MBE is missing.  This just keeps getting better and better.  :-k

I will post the relevant portion of that log on PasteBin and then post the link here.

Here is the remote FE log: [http://pastebin.com/KLZGEEWM](http://pastebin.com/KLZGEEWM)

---

### Post by Lester_Burnham on 2012-05-26
Hi,

Is your recording location set the same as the master backend on the slave backend?
/var/lib/mythtv/recordings/ if default.

Lester

---

### Post by nickrout on 2012-05-26
On the SBE run mythtv-setup and go to 1.General. What are the two ip addresses set to?

---

### Post by Lester_Burnham on 2012-05-26
> **nickrout said:**
> On the SBE run mythtv-setup and go to 1.General. What are the two ip addresses set to?

Hi,

I would've thought the IP's in there would be OK, because of the OP's statement above.
> When I use the frontend on the SBE, the one with the analog tuners, this works as expected. I can switch back and forth between the digital tuners and the analog ones, and there are no problems. 

Makes my suggestion above look doubtfull too.
Do the analogue settings on the master back end need to be set correctly, even though the tuners are on the slave?

Lester

---

### Post by nickrout on 2012-05-26
> **Lester_Burnham said:**
> Hi,

I would've thought the IP's in there would be OK, because of the OP's statement above.Let's let him answer for himself :)> 


Makes my suggestion above look doubtfull too.
Do the analogue settings on the master back end need to be set correctly, even though the tuners are on the slave?

LesterNo, the tuner only needs to be set up on the backend it actually sits on.

---

### Post by jlp_engineer on 2012-05-26
> **Lester_Burnham said:**
> Hi,

Is your recording location set the same as the master backend on the slave backend?
/var/lib/mythtv/recordings/ if default.

Lester

There are no settings at all in the Storage Groups on the SBE, so that must be it.  Should the folders be setup on the SBE in the same folder structure as the MBE???  Do the folders on the MBE need to be NFS mounted to the SBE, or should that happen automatically? Do the recordings and LiveTV created on the slave get transported to the master backend via MythTV protocols, if the local folder structure is not remotely mounted from the MBE?

Lester - You rock!  :guitar:

---

### Post by jlp_engineer on 2012-05-26
> **nickrout said:**
> On the SBE run mythtv-setup and go to 1.General. What are the two ip addresses set to?

On the slave, the Local Backend IP is set to 127.0.0.1, and the Master Backend is set to 192.168.1.100 (which is the MBE system). The IP of the slave is 192.168.1.110.

Should the IP for the Local Backend be set to an actual IP address, or is the local loop back OK in this configuration?

Thanks :-)

---

### Post by jlp_engineer on 2012-05-27
And the answer is ........

I created all the storage groups and pointed them to the already existing folders on the slave, but no dice on LiveTV for the remote FE's. :-k

I then changed the IP address of the Local Backend on the slave to an actual IP, using the IP address of the slave system, and that worked.  Now all my remote Frontends are happy. \\:D/ 

Thanks Lester and Nick !!!

Have a beer on me fellas...  =D>

---

### Post by nickrout on 2012-05-27
> **jlp_engineer said:**
> And the answer is ........

I created all the storage groups and pointed them to the already existing folders on the slave, but no dice on LiveTV for the remote FE's. :-k

I then changed the IP address of the Local Backend on the slave to an actual IP, using the IP address of the slave system, and that worked.  Now all my remote Frontends are happy. \\:D/ 

Thanks Lester and Nick !!!

Have a beer on me fellas...  =D>

Suspected that was it, that's why I asked :)

I still don't understand SG's when you have more than backend, but there are details here [http://www.mythtv.org/wiki/Storage_Groups](http://www.mythtv.org/wiki/Storage_Groups)

---

### Post by Lester_Burnham on 2012-05-28
After reading that storage group info, it sounds like most of the stuff I told you was wrong or shouldn't be required. 
I'm more confused than ever after reading that! I think it needs to be dumbed down even more :)

I'll just stick to a master backend only.

Lester

---

