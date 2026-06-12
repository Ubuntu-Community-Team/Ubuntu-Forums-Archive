---
title: "Deciding on best HDTV capture for new system"
date: 2008-01-24
forum: Mythbuntu
---

### Post by timg11 on 2008-01-24
I'm preparing to build my first MythTV system, based on Mythbuntu. I have looked at the list of supported capture cards and am trying to decide between the DViCO FusionHDTV5 Gold and the pcHDTV HD-5500.

Can anyone give any details about how these work with Mythbuntu. I am primarily interested in over the air HDTV reception (ATSC). I may be able to use QAM if there are any unencrypted HDTV channels on the cable. NTSC capture is not a requirement.

Please let me know what you think of these two capture cards (or others if I have missed another good option)

Thanks!

---

### Post by newlinux on 2008-01-24
They are both fine. You won't notice much a difference between the two - digital cards simply capture the transport stream with no encoding whatsoever. Both are well supported. Personally I prefer the Kworld ATSC 110/115 because it is cheaper. You may need to load some firmware once, but then after that it works as good as any other digital ATSC/QAM capture card. There are a number of other cards you could consider (Avermedia A180, Dvico fusion 5 lite). The Avermedia can't capture NTSC, but the others can (though this is probably not important in your case).

If all you want is OTA ATSC you might want to look into cheap used Air2pc cards of ebay for $20-$40 bucks. They don't do QAM though.

I personally have used Kworld ATSC 110, pchdtv 5500, dvico fusion 5 lite, and avermedia A180. No real difference once they are setup for me. I ended up selling my pchdtv 5500 and buying two KWorld ATSC 110s for the money.

---

### Post by ubnewbie2 on 2008-01-24
> **newlinux said:**
> They are both fine. You won't notice much a difference between the two - digital cards simply capture the transport stream with no encoding whatsoever.


I agree.  Quality of the recording is dependent on what the TV station is transmitting.

The only thing I have read is that some DVB cards require better(higher) signal levels than others, iow some are more sensitive.  If you reception is poor, then this may make a difference.  I use Leadtek DVB100T cards and they are said to be not so sensitive - but I have no problems with them now my TV antenna and coax feed from it are all up to scratch.

---

### Post by timg11 on 2008-01-25
Thanks for the info, newlinux,

The KWorld ATSC 115 sounds nice, and is lower cost. However, on the Mythbuntu wiki pages <https://help.ubuntu.com/community/MythTV/Install/Gutsy/Tuners>, it is not mentioned. The 110 is mentioned, but says "needs firmware", and refers to a page at mythtv.org. On that page there is a lot of detailed, kernel specific configuration information. Does all that apply to Mythbuntu 7.10?  There is also a comment that the remote does not work with MythTV. 

Do you have the ATSC 110 or the 115? Is it fully functional (ATSC HD and remote control) under Mythbuntu?

---

### Post by newlinux on 2008-01-25
I have the atsc 110 but many here have the atsc 115. There are full threads on setting it up. It behaves almost exactly the same as the 110 and Avermedia A180.

All you need to do is get the firmware:
```
sudo aptitude install linux-source
cd /usr/src
sudo tar xvjf linux-source-[INSERT YOUR KERNEL HERE- just do an ls].tar.bz2
cd linux-source-[INSERT YOUR KERNEL VERSION]/Documentation/dvb
sudo perl get_dvb_firmware nxt2004
sudo cp dvb-fe-nxt2004.fw /lib/firmware/
```

And load the module properly:
1. Add the following lines to /etc/modprobe.d/kworld_atsc_115
Code:

```
alias char-major-81 videodev 
alias char-major-81-0 saa7134 
options saa7134 card=90

```
2. Then edit  /etc/modules to add:
Code:
```

saa7134 
saa7134-dvb
saa7134-alsa


```

Reboot and you're ready. In the next ubuntu release It will be supported out of the box and none of this will be necessary.

As far as the remote goes, I think it requires a kernel patch, and I don't know how well it works. I use a different remote for myth so I don't use the Kworld remote and don't know much about how well it does work with the kernel patch.

---

### Post by timg11 on 2008-04-17
Has anybody verified that the ATSC 110 and 115 are now supported "out of the box" with Mythbuntu 8.04?
Does Mythbuntu 8.04 still need a kernel patch to support the remote?

---

### Post by poke4christ on 2008-04-17
I'm in the process of building my first box (had to send back a bad shuttle box) and I've had the HDHomerun for a little bit now.  I've only used it over the network, but it worked very well.  It actually ended up very good for me becuase it doesn't eat up my two card slots (my box only has two).  It is more expensive than some, but I think it is woth the price.  I hope it works as well when my system is up and running.

---

### Post by colinnwn on 2008-05-03
"I personally have used Kworld ATSC 110, pchdtv 5500, dvico fusion 5 lite"

Sorry to hijack, but can you share how you got the Dvico working?  It isn't working for me.
[http://ubuntuforums.org/showthread.php?t=779913](http://ubuntuforums.org/showthread.php?t=779913)

Thanks.

---

