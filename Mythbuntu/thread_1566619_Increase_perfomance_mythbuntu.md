---
title: "Increase perfomance mythbuntu"
date: 2010-09-02
forum: Mythbuntu
---

### Post by Techmanm on 2010-09-02
I have mytbuntu running now but live tv is a bit stuttering (forgive my bad english) and mythbuntu reacts slow on the remote.

What can i do to increase de performance.

(Running 10.04).

Thanks

Marco

---

### Post by LowSky on 2010-09-02
if liveTV is stuttering you need to change profile under TV setting on te frontend

What kind of equipment you are using can be a factor too. Video playback can be very demanding of resources.

---

### Post by agamotto on 2010-09-03
> **Techmanm said:**
> I have mytbuntu running now but live tv is a bit stuttering (forgive my bad english) and mythbuntu reacts slow on the remote.

What can i do to increase de performance.

(Running 10.04).

Thanks

Marco

1. Go into the Frontend settings, Playback, and change the profile to something like normal or cpu --.  See if this helps.  The slow reaction of the menus and such may be due to your theme not being drawn in Open GL instead of Qt.  Frontend settings, Appearance, when you get to the theme section, make sure that it is being drawn in Open GL.  Otherwise, choose a fairly simple theme, such as retro or Mythbuntu (old).

Your English is fine, by the way!

---

### Post by Techmanm on 2010-09-12
> **agamotto said:**
> 1. Go into the Frontend settings, Playback, and change the profile to something like normal or cpu --.  See if this helps.  The slow reaction of the menus and such may be due to your theme not being drawn in Open GL instead of Qt.  Frontend settings, Appearance, when you get to the theme section, make sure that it is being drawn in Open GL.  Otherwise, choose a fairly simple theme, such as retro or Mythbuntu (old).

Your English is fine, by the way!

I have changed the profile but it doesn't make a difference.
When i'm at the desktop of mythbuntu and start mythtv it also takes about 20 secondes before something happens.

---

### Post by ozybushwalker on 2010-09-12
As previously stated:
> **LowSky said:**
> 
Video playback can be very demanding of resources.

Maybe you have too much other stuff running on the box, maybe too little RAM. Maybe you can offload some video processing to the video card (some types of Nvidia video cards). Maybe you would get better results from using lower resolution video.

Maybe you have separate front-end and back-end and not enough network bandwidth (or too large a latency) between them.

Lots of possibilities. Some more information about your system would help.

---

### Post by frego on 2010-09-12
System specs would be nice.  But no matter how fast a machine, a bad hard drive will cause huge delays.  Check dmesg and see if there any errors.  Also you might check /var/log/messages for anything out of the ordinary.

---

### Post by Techmanm on 2010-09-13
> **frego said:**
> System specs would be nice.  But no matter how fast a machine, a bad hard drive will cause huge delays.  Check dmesg and see if there any errors.  Also you might check /var/log/messages for anything out of the ordinary.

Here are my specs:

Behuizing  Antec  Veris Media Fusion Remote (zilver) 
Moederbord  Gigabyte  GA-MA78GPM-DS2H 
Processor  AMD  Athlon X2 5200+ 
Koeling  Scythe  Ninja Mini 
Voeding  Coolermaster  Real Power M 520W Modular 
Harddisk  Samsung  Sata II 1TB 32MB 
TV kaart  Hauppauge  HVR-4000 
DVD brander  Samsung  S223 Sata brander 
Videokaart  Asus  Radeon EAH3650 Silent / HTDI/512M 
Geheugen  Kingston  KVR800D2N5K2 

I know the motherboard also has an HDMI output but my TV still needs an S-video signal. Thats the reason i bought the asus.

I'm running mythbuntu 10.04. Backend and frontend are on the same machine. The machine also runs a LAMP server and sabnzb+.

Is this to much??

In webmin the CPU load averages says:
0.42 (1 min) 0.43 (5 mins) 0.33 (15 mins)

---

### Post by uncle hammy on 2010-09-13
Your specs are certainly adequate.  However, the ATI card could be your problem, NVidia cards are strongly recommended for MythTV.  I have never had much joy with ATI cards in Myth boxes.

---

### Post by alien878 on 2010-09-14
I agree with Hammy that your video card is probably weak piece.  However, I wouldn't expect it to have problems just with the menus or even SD.

Before you replace the card, you might check a few things:
[LIST]
[*]Check "top" to see if there is anything unexpected using up CPU time.
[*]Try tweaking some of the settings in the Appearance section of the frontend setup.  A few of them will affect performance (ex. "Use OpenGL").
[*]Try a lower screen resolution.  Sometimes the highest available has performance issues.
[/LIST]

---

### Post by LowSky on 2010-09-14
Your video card is fine. The newer ATI models work decently. I used one for a while before I upgraded to a Nvidia 460GTX. The only issue is they cannot use VDPAU, so the processor is doing a bit more work than it would if you used a Nvidia card. That would effect the menus, just playback.

Too much network traffic and hard drive access could be the real issue. Espcially if the same hard drive is being used to host the server and record/stream television.

---

### Post by Techmanm on 2010-09-14
> **LowSky said:**
> Your video card is fine. The newer ATI models work decently. I used one for a while before I upgraded to a Nvidia 460GTX. The only issue is they cannot use VDPAU, so the processor is doing a bit more work than it would if you used a Nvidia card. That would effect the menus, just playback.

Too much network traffic and hard drive access could be the real issue. Espcially if the same hard drive is being used to host the server and record/stream television.

Would it become better when i use the onboard video output on a new LCD TV :D ?

@Lowsky: The server and the recordings are done on the same HD.

What kan i do best, use a small HD for hosting the OS and an other for putting the files on or does this not make a difference.

---

### Post by joshoekstra on 2010-09-14
What you could do is use top on the machine to see what it's doing, iotop would be handy as well.
I'm guessing that you have 2GB of memory? I've also seen sabnzb trash machines a lot, try switching it of to test, it causes a lot of load.
As long as your recording aren't damaged your diskperformance should be fine, I've been running my backend-server on the same disk as recording for years and only had problems when stressing the machine a lot with other tasks than mythtv...

---

