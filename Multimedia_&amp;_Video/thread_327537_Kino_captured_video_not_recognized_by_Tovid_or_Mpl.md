---
title: "Kino captured video not recognized by Tovid or Mplayer"
date: 2006-12-29
forum: Multimedia &amp; Video
---

### Post by Ohmn on 2006-12-29
Hi, I am trying to come back to Linux after about 2 years. The reason I gave it up was we bought a camcorder for xmas a while back and I wanted to be able to dump camcorder video and then burn it to DVD. Lets just say it was way simpler in windows.

But with the programs Kino and Tovid, I had a lot of hope I could do what I wanted in Linux and take back a box for Linux :) Miraculously, I got both installed. I went to burn the .avi file with tovid but tovid aborted the process, seemed like some problem with the video. I tried to play it with mplayer and it would not work. The format I captured originally with Kino was AVI type 1. Tovid and mplayer could not handle it but Totem movie player could. In fact, totem played the captured video in AVI type 1 flawlessly. But that does not help me burn it to DVD.

So I tried some sample captures with Kino in both AVI type 2 and RAW DV. Neither of these would work in mplayer or tovid.  Isn't tovid supposed to work with Kino? 

I know this is the video forum but to prevent multiple posts by myself I also have two other questions. When I need to get r/w permissions for /dev/raw1394 I use the following:

chmod a+rw /dev/raw1394

But the permission goes away when I re-log. Assuming my account name is "Hal", how do I change this to make it permenant?

My final question revolves around my being able to browse XP NTFS partitions in my Ubuntu 6.1 user account but I am not able to r/w to them. How do I give my ubuntu user account "Hal" r/w privilages to hda1 and hdb1? Thanks

---

### Post by Unterseeboot_234 on 2006-12-29
Say, I finally got Kino working as 64-bit. Get rid of your raw1394. Do a Synaptic Add/Remove --> advanced, look for raw1394. You'll get results for libraw1394. But first read this link


[http://ubuntuforums.org/showthread.p...hlight=raw1394]("http://ubuntuforums.org/showthread.p...hlight=raw1394")

Your other problems involve Codecs. Be sure you have the Automatix2. Kino wants dv1394 as its device in dev/ to run the buttons in the Capture/Export feature.

And, I'm a noob on Linux. I'm pretty sure FAT32 and ext3 give the least pain for hybrid files between WIN and linux.

I'll watch this thread. I have to do some more investigating on my Kino install. As it is, I've got too many windows open at the moment with other things cooking. It does take the camera hooked up to verify the connections and links are working.

==============

Okay, because I have the Codecs, because I started Kino from a terminal console, because I have the Sony HandyCam hooked up via firewire and turned to VCR mode -- I have /dev/dv1394 in my /dev folder. It wasn't always like that. I used the above link from the forums to discover gscanbus. That program kept me on the right install path. I suppose, because I have the source for Ubuntu Drake and libraw1394, ubuntu on its own built the kernel patch that loads on boot, I NEVER see raw1394. Within Kino --> Capture tab, I had to go Edit --> Preferences, 1394 device tab and change the device filename from dv1394/0 to dv1394-0. When I did that little change, the buttons to control the camera lit up. If you look inside /dev folder with Kino running, you will have dv1394 in /dev. Go back to /dev after you turn everything off and there is no dv1394 in /dev. Kino put it there. You may have to build libsampler for sound (see [http://www.linux1394.org/](http://www.linux1394.org/) ). That's me on 64-bit. Things may be easier for 32-bit. I used the Synaptic download of Kino. IMHO Kino had to do it this way because of all the different hardware configurations possible.

---

### Post by meng on 2006-12-29
Re: user privileges:
IIRC /dev/raw1394 belongs to group video (but you can check this by:
ls -l /dev/raw1394
One way would be to add user Hal to the group video.

---

### Post by Ohmn on 2006-12-29
> **meng said:**
> Re: user privileges:
IIRC /dev/raw1394 belongs to group video (but you can check this by:
ls -l /dev/raw1394
One way would be to add user Hal to the group video.

It belongs to root in my ununtu 6.10 install. Since I dont want to add "hal" to root I still have a problem heh.

>  Say, I finally got Kino working as 64-bit. Get rid of your raw1394. Do a Synaptic Add/Remove --> advanced, look for raw1394. You'll get results for libraw1394. But first read this link


[http://ubuntuforums.org/showthread.p...hlight=raw1394](http://ubuntuforums.org/showthread.p...hlight=raw1394). 

The link took me to the forum index. So unsure if I should uninstall raw1394 since I have not read the link first.

---

### Post by Unterseeboot_234 on 2006-12-30
You are correct, the link does go back to the main forums page. I'm including it again (I think I am anyway).


[http://ubuntuforums.org/showthread.php?t=56468]("http://ubuntuforums.org/showthread.php?t=56468")

Hey for whatever reason I cannot paste a link like I normally can. Maybe because the posting is from 2005. If this doesn't work, search the forums for--

**ubuntu & sony handycam**
look down the list for the user **finkoisti**

I'm Dapper. Shouldn't make any difference. Use the Synaptic libraw1394 for the raw1394, that will take care of the permissions thing AND safeguard the backdoor of your ubuntu 1394eee vurnerability a little better. Then, to use Kino, follow the rest of that posted thread. I swear, I was going around and around trying to install raw1394eee until I found that old thread (2005). The thread should be the HowTo. The one in the Wiki, the dude gives up, says Kino cannot connect the camera. I'll keep watching this thread.:D

---

### Post by Ohmn on 2006-12-31
[QUOTE] I'm Dapper. Shouldn't make any difference. Use the Synaptic libraw1394 for the raw1394, that will take care of the permissions thing AND safeguard the backdoor of your ubuntu 1394eee vurnerability a little better [/QUOTE}

Probably a good idea. But for right now, I need to be able to play the video I capture with Kino with mplayer. If I can, then I can use tovid to burn it to DVD. I have messed around with DeeVee and it seems to be hit or miss as well. 

I installed automatix and all the codecs for mplayer.  I have gone into mplayer->preferences->codecs and tried about every video and audio codec included and it still does not work. I get the following message:

"Error opening/initializing the selected video_out (-vo) device. I get the same error message when I try to play a DVD in mplayer. Real does nto seem to open them either. Only totem is successfully opening the .avi files from Kino and DVDs. But I need mplayer to work or I can't use Tovid.

---

### Post by ddennedy on 2007-01-07
If you do not need a menu on your DVD, you can just create the DVD image from within Kino by choosing Export/MPEG, provided you have mjpegtools and dvdauthor packages installed. Even if you do want to make menus, you can at least export DVD compliant MPEG-2 files from within Kino and use them with another DVD authoring tool.

---

