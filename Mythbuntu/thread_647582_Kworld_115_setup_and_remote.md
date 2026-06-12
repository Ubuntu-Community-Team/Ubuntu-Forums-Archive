---
title: "Kworld 115 setup and remote"
date: 2007-12-22
forum: Mythbuntu
---

### Post by airiox on 2007-12-22
Setting up my mythubuntu box now. I am am pretty much a linux noob with only using suse the past few months off and on. 

What I need is to get my capture card installed (Kworld ATSC 115) and its remote.

My question is can anyone explain how to install the capture card and how to install the remote. Mythbunutu comes with lirc installed but I am not sure if my remote is on the list, if it is can you tell me which one.

Also I have the mythtv wiki up for the atsc 110 but I have no clue what it is saying.
Could anyone simplify the instructions for how to do it just on mythbuntu.

[http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110](http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110)

Thanks

---

### Post by airiox on 2007-12-24
The real problem is the first part.

# cd /[kernel source directory]/Documentation/dvb/
# perl get_dvb_firmware nxt2004

Can anyone tell me how to find out or tell me the path of [kernel source directory]

Thanks.

---

### Post by newlinux on 2007-12-24
For me (and this was in edgy) I downloaded this from the V4L site, and then cd' into the unzipped directory directory structure of the download and ran it from there. It didn't come on my Edgy system that I know of... IIRC. I don't know if it does or doesn't in Gutsy.  It's been over a year... But basically all you need to do is  download  that firmware file and put it in /lib/firmware.

You can see if the file or perl script exist on your system by doing:

```

slocate get_dvb_firmware
slocate nxt2004

```
This will give you the path to them if they are on your system in a place that it is indexed.
If you can't find them then you probably need to download them.

---

### Post by thecoolcat on 2007-12-25
> **airiox said:**
> The real problem is the first part.

# cd /[kernel source directory]/Documentation/dvb/
# perl get_dvb_firmware nxt2004

Can anyone tell me how to find out or tell me the path of [kernel source directory]

Thanks.

You can also download this script from here:
[https://help.ubuntu.com/community/MythTV_Feisty_hardware_list](https://help.ubuntu.com/community/MythTV_Feisty_hardware_list)
(under ATI cards.)

I haven't got the remote and analog to work yet. See this thread for details:
[http://ubuntuforums.org/showthread.php?t=643415](http://ubuntuforums.org/showthread.php?t=643415)

---

