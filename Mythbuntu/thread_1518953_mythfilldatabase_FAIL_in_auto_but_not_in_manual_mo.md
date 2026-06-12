---
title: "mythfilldatabase FAIL in auto but not in manual mode"
date: 2010-06-27
forum: Mythbuntu
---

### Post by dibuntux on 2010-06-27
So, now  mythfilldatabase will FAIL in auto (standard settings that worked since last week) but not in manual mode: when you enter Mythbuntu control center and exit it will ask if you want to run mythfilldatabase, I say yes and it completes the fill of all my channels.

I'm using XMLTV (wiki.xmltv.org) with tv_grab_it, and its status is reported to fail since 2010-02-25, but I had not any problem since last week 

This is the error Mythtv reports in backend status:

Last mythfilldatabase run started on 2010-06-26 04:29 and ended on 2010-06-26 04:29. FAILED: xmltv returned error code 512.
There's guide data until 2010-07-04 02:45 (7 days). 

I remember when tv_grab_it was not working I had to manually patch it using the code some fellow italian developed. But in that case was just not working - now it works just manually.

Any Ideas? TIA, Dave

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

### Post by guyverix on 2010-06-28
> **dibuntux said:**
> 
Last mythfilldatabase run started on 2010-06-26 04:29 and ended on 2010-06-26 04:29. FAILED: xmltv returned error code 512.
There's guide data until 2010-07-04 02:45 (7 days). 


Perhaps this is related to your problem?
[http://ubuntuforums.org/showthread.php?t=624517](http://ubuntuforums.org/showthread.php?t=624517)

From that post: The backend runs as the 'mythtv' user. The frontend runs as the user you have created.
That might be why you are having problems.  They have a fix in the thread.

---

### Post by dibuntux on 2010-06-28
I have a file log where I put ALL mods I do to my mythtv system... this was the first entry!

Thanks for reminding me of the solutions below: 



Re: [SOLVED] mythfilldatabase error code 512?
Code:

cd /home/mythtv/.mythtv
sudo ln -s /home/<your_user_name>/.mythtv/au.xmltv

In my case instead of au.xmltv it was Antenna.xmltv

Make sure, if you copy the code example, you replace with the correct name for your xmltv file.

Regards, Steve

---

