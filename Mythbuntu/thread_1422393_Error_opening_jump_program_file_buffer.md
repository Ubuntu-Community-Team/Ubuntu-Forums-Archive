---
title: "Error opening jump program file buffer"
date: 2010-03-05
forum: Mythbuntu
---

### Post by dibuntux on 2010-03-05
With Mythbuntu 9.10 AMD64, I'm always getting this 
"Error opening jump program file buffer" when starting Live TV. It was not so with 9.04 (MythTV 0.21, I know...)...

My first tuner is a DVB-S Skystar2, connected to 2 LNB, I've been using for years with Myth. The error comes out only when the last watched channel is on Astra sat, like CNN or BBC. Myth says "partial lock", if I'm fast enough, I just switch to the next channel ON THE SAME MULTIPLEX, and it will lock normally. If I change multiplex, or satellite (other input), at random I've to repeat this procedure. If I do not, Myth exit LiveTV with the dreaded "Error opening jump program file buffer".
This does not happen with DVB-T on my Nova T-500.

I know many people are experiencing this problem, and all of them did not have it on 9.04. I'm using the update PPA, but until now nothing changed.

Any Ideas? Just wait for 10.04 and myth 0.23? TIA

Mythbuntu 9.10 AMD64
Gigabyte GA-M720
Athlon X2 4800+
Nvidia 9400GT 1GB
WD Sata2 CaviarGreen
Skystar 2 DVB-s
Nova T-500 dual DVB-T
Denon AVR 1610 connected with SPDIF
Optoma HD700x on DVI

---

### Post by singedwings on 2010-03-05
I have a skystar2 but I have not suffered your problem. How did you tune the channels?

---

### Post by colinnwn on 2010-03-05
It doesn't happen to me on analog PVR-150. But I finally got my digital HVR-1250 working somewhat, and I am getting this error intermittently as I try to map my digital channels to the correct station in Schedules Direct.

Digital MythTV has been a PITA transitioning to. It has been almost 2 years since I bought my upgraded hardware and started trying, and I still don't have it working satisfactorily.

Edit - Ut oh... The digital card won't open at all, even if I close the FE and restart, I still get the same error before it can tune/lock any digital station. The ship is going down Captain!

---

### Post by dibuntux on 2010-03-07
I scan using the usual:

scan -a 0 -s 1 -x 0 -t 1 /usr/share/dvb/dvb-s/Astra-19.2E > astra.conf

to generate a .conf file, then imported in myth setup.

---

### Post by singedwings on 2010-03-14
If I used a .conf file to scan the channels I could not get any guide data, do you? So I had to persist with the myth scanner until I got all the way through the scan without it crashing.

So far I have not experienced your problem and I am wondering whether the scanning method is a contributing factor.

---

### Post by blueskies1977 on 2010-04-28
I don't think this is anything to do with Mythbackend. I have a fully functioning backend with two front ends. One of the frontends has this problem and the other doesn't.

For reference it is the frontend running mythbuntu which has the problem. The frontend running kubuntu is fine

---

### Post by colin-nz on 2010-05-09
Just reading some other posts trying to solve this for my setup...

They were referring to the need of having the front end and back end times synced... even out by a minute can cause issues... something about it occurring when the program guide changes to another program...

Might explain why one front end of yours had the error and the other didn't?

Have not tested for my setup yet...

Regards

---

### Post by barrylumpkin on 2010-06-19
I have the same intermittent problem with frontend/backend on the same computer. :neutral:

---

### Post by Tonyr63 on 2010-09-01
Hi

I Have tis problem with 0.23 and Ubuntu 10.04 and have found so many similar reports however NO SOLUTIONS.

What do we do to resolve this error which is leaving Mythtv dead in the water?

What does this error mean and what is causing it?

---

### Post by mech259 on 2010-09-02
My Mythtv will work for a bit til I change channels a couple of times. The backend and frontend are on the same machine. It will eventually brown out and lock the machine up.I am running a  Hauppage HVR-2250 Digital with dual tuners on Ubuntu 10.04. Have tried to look on the Mythtv wiki to no avail yet. 1 piece of info, the wiki says it might overwriiten the Nvidia drivers and to reinstall theirs. Anyone find anything yet?

---

### Post by Altino on 2010-09-22
Indeed, I'm experimenting a similar problem. I use mythtv-backend and frontend in different computers. I used to use backend with Ubuntu Server 8.04 LTS 64 bit, with no problem at all.

My DVB-S card is Skystar 2, rev 2.6d, decoding from Hotbird.

Since I installed Ubuntu Server 10.04 LTS problems started appearing. I can scan channels correctly using w_scan. The skystar card is correctly read by kernel (anlysing both lspci and dmesg). However, when I try to setup my mythtv-backend I throws up an error, saying that cannot get skystar model (but can detect that is a DVB-S card is there)... very strange...

Now, I'm considering downgrad the mythtv-backend version but I've no idea if it will gonna work.

---

### Post by ChilledWort on 2010-09-26
I've had this problem recently with my first install of MythTV.  I have an HDHomeRun as my tuner with a basic comcast input.  This seems to happen when channels stop working or never worked and you try to tune them.

What I did to fix this was enter the backend setup (System->Preferences->MythTV Backend Setup) and Navigate to option 4. "Input Connections".  I select the tuner that LiveTV is currently trying to use at startup and in the options page there is a field called "Starting Channel".  This seems to change with use and always stays on the last channel tuned before exit.  I change this to a channel I know works and I'm good to go.

---

### Post by ChilledWort on 2010-09-26
I've had this problem recently with my first install of MythTV.  I have an HDHomeRun as my tuner with a basic comcast input.  This seems to happen when channels stop working or never worked and you try to tune them.

What I did to fix this was enter the backend setup (System->Preferences->MythTV Backend Setup) and Navigate to option 4. "Input Connections".  I select the tuner that LiveTV is currently trying to use at startup and in the options page there is a field called "Starting Channel".  This seems to change with use and always stays on the last channel tuned before exit.  I change this to a channel I know works and I'm good to go.

---

### Post by ChilledWort on 2010-09-26
I've had this problem recently with my first install of MythTV.  I have an HDHomeRun as my tuner with a basic comcast input.  This seems to happen when channels stop working or never worked and you try to tune them.

What I did to fix this was enter the backend setup (System->Preferences->MythTV Backend Setup) and Navigate to option 4. "Input Connections".  I select the tuner that LiveTV is currently trying to use at startup and in the options page there is a field called "Starting Channel".  This seems to change with use and always stays on the last channel tuned before exit.  I change this to a channel I know works and I'm good to go.

---

