---
title: "Upgrading to 11.04 from 10.10 - Using new install"
date: 2011-10-08
forum: Mythbuntu
---

### Post by bleve on 2011-10-08
Hi all,

I am upgrading from 10.10 but decided to backup the database and my  recordings and do a clean install.  This is because I want to add a  Hauppauge HD PVR into my configuration.  I had attempted to add this  into the existing 10.10 install and got everything to work except the IR  blaster.  So I decided to start over.

So what I would like to ask about is what would be the best order to do  things.  I currently have two PVR-350 cards in the MB and added the HD  PVR external device to it.  So when I reinstall, would it be best to  just add everything in at once when configuring the backend or should I  do the PVR-350 cards first or the HD PVR first?  

Any tips would be greatly appreciated.  

-bleve

---

### Post by nickrout on 2011-10-09
> **bleve said:**
> Hi all,

I am upgrading from 10.10 but decided to backup the database and my  recordings and do a clean install.  This is because I want to add a  Hauppauge HD PVR into my configuration.  I had attempted to add this  into the existing 10.10 install and got everything to work except the IR  blaster.  So I decided to start over.

So what I would like to ask about is what would be the best order to do  things.  I currently have two PVR-350 cards in the MB and added the HD  PVR external device to it.  So when I reinstall, would it be best to  just add everything in at once when configuring the backend or should I  do the PVR-350 cards first or the HD PVR first?  

Any tips would be greatly appreciated.  

-bleve

When you reinstall, restore your database. Then in mythtv-setup delete all tuners and start afresh. Put the tuner that you want to prefer for recording (probably the hdpvr to prefer HD recordings) first and then the pvr-350s.

---

### Post by bleve on 2011-10-09
Thanks Nick.  I did the fresh install and created two sources.   One for regular cable plugged into my two PVR-350 cards and one for digital cable.  I have not configured the HD-PVR yet, so it is not added but I can see that it is found via "dmesg".  Over the next day or so I need to work on my lircrc to get the PVR-350 remote working again since it now uses a different module with different key names.  

After that I will attempt to tackle the HD-PVR. 

Thanks,

-Bennett

---

### Post by nickrout on 2011-10-09
> **bleve said:**
> Thanks Nick.  I did the fresh install and created two sources.   One for regular cable plugged into my two PVR-350 cards and one for digital cable.  I have not configured the HD-PVR yet, so it is not added but I can see that it is found via "dmesg".  Over the next day or so I need to work on my lircrc to get the PVR-350 remote working again since it now uses a different module with different key names.  

After that I will attempt to tackle the HD-PVR. 

Thanks,

-Bennettyes but you will need to delete all tuners and add them back in a different order if you want to prefer the HDPVR for recordings.

Don't worry you don't need to delete your sources, just connect them as usual. Deleting the tuners does not delete the sources.

---

### Post by bleve on 2011-10-10
Yes, I usually just set the recording priority in the myth backend setup.  I just hope the HD PVR setup is not too complicated.  lirc has changed for the PVR-350 so it looks like some key names need to be changed, so as I said I will tackle that first.  

I would actually prefer if the channels < 100 were recorded by the PVR-350 cards and the HD and digital content recorded by HD PVR so I will setup up my second source to be channels > 100.  This should also chose them to pick the correct tuners.  

Thanks

---

