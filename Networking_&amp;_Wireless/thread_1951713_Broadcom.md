---
title: "Broadcom"
date: 2012-04-03
forum: Networking &amp; Wireless
---

### Post by xworld on 2012-04-03
I dual booted my pc with ubuntu 10.04 and win7 and everything went great. Just one problem, no internet. It couldn't find any networks. I've looked around for quite awhile and nothing seems to work. I have a broadcom wifi adapter and I've heard of many troubles with this and 10.04. Stranger still even when I plug in an ethernet cable it still reads that there are no networks available. Any ideas?

---

### Post by wildmanne39 on 2012-04-03
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by xworld on 2012-04-03
Thanks. Ok here it is
```
                                  ubuntu@ubuntu:~$ cat /etc/lsb-release; uname -a  
 DISTRIB_ID=Ubuntu  
 DISTRIB_RELEASE=10.04  
 DISTRIB_CODENAME=lucid  
 DISTRIB_DESCRIPTION=&quot;Ubuntu 10.04.4 LTS&quot;  
 Linux ubuntu 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:13:04 UTC 2012 i686 GNU/Linux  
 ubuntu@ubuntu:~$ lspci -nnk | grep -iA2 net  
 02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)  
 03:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1083] (rev c0)  
 ubuntu@ubuntu:~$ lsusb  
 Bus 002 Device 003: ID 0781:556c SanDisk Corp.  
 Bus 002 Device 002: ID 8087:0024   
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 001 Device 003: ID 058f:a014 Alcor Micro Corp.  
 Bus 001 Device 002: ID 8087:0024   
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 ubuntu@ubuntu:~$ iwconfig  
 lo        no wireless extensions.  
 

 ubuntu@ubuntu:~$ rfkill list all  
 ubuntu@ubuntu:~$ lsmod  
 Module                  Size  Used by  
 dm_crypt               11331  0  
 snd_hda_codec_realtek   203440  1  
 binfmt_misc             6587  1  
 ppdev                   5259  0  
 lp                      7028  0  
 parport                32635  2 ppdev,lp  
 snd_hda_intel          22069  2  
 snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel  
 snd_hwdep               5412  1 snd_hda_codec  
 snd_pcm_oss            35308  0  
 snd_mixer_oss          13746  1 snd_pcm_oss  
 snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss  
 snd_seq_dummy           1338  0  
 snd_seq_oss            26722  0  
 snd_seq_midi            4557  0  
 snd_rawmidi            19056  1 snd_seq_midi  
 snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi  
 snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event  
 snd_timer              19130  2 snd_pcm,snd_seq  
 snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq  
 snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 uvcvideo               57438  0  
 psmouse                63677  0  
 videodev               34425  1 uvcvideo  
 soundcore               6620  1 snd  
 v4l1_compat            13251  2 uvcvideo,videodev  
 snd_page_alloc          7076  2 snd_hda_intel,snd_pcm  
 serio_raw               3978  0  
 squashfs               20744  1  
 aufs                  149050  1  
 nls_iso8859_1           3249  1  
 nls_cp437               4919  1  
 vfat                    8933  1  
 fat                    47767  1 vfat  
 dm_raid45              81647  0  
 xor                    15028  1 dm_raid45  
 usb_storage            40033  1  
 fbcon                  35102  71  
 tileblit                1999  1 fbcon  
 font                    7557  1 fbcon  
 bitblit                 4707  1 fbcon  
 softcursor              1189  1 bitblit 
 video                  17375  0  
 output                  1871  1 video  
 ahci                   32680  1  
 vga16fb                11385  1  
 vgastate                8961  1 vga16fb 
 ubuntu@ubuntu:~$  
 
```  -bump-Pretty desperate for an answer I've done alot of research on this and so far only found that broadcom and lucid lynx don't mix. Hence why I joined this forum. I'm calling on the experts here. Seems like wildmanne39 knew where this was going. Anyone help?

---

### Post by wildmanne39 on 2012-04-03
Hi, first broadcom is not a bad card you have to install the drivers for it like you do most others.

Second you do not have a broadcom you have a realtek card so please run these commands one line at a time with a wired internet connection, I am not sure how to get the driver without a connection:
```
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
```
then unplug wired connection and reboot.
Thanks

---

### Post by xworld on 2012-04-03
I would but one of the things that is confusing me is that I can't get a connection even with a hard plugin. No wired OR wireless connections. I can't imagine why this is happening

---

### Post by wildmanne39 on 2012-04-03
Hi, the driver for your wired connection is not included in 10.04 either, I just looked it up.

Do you have a cell phone you can tether to your computer?

You could just upgrade to 11.10 then your wired will work for sure.
Thanks

---

### Post by xworld on 2012-04-03
I'm running 11.10 currently and have a liveusb with 10.04 on it. I want to get 10.04 to work but I guess I should ask this: Once the new LTS comes out does the old one stop getting updates. And, how dramatically does it affect you when your system stops getting updates.  In other words, is it even worth trying to get 10.04 to work with 12.04 coming out the end of this month?

---

### Post by wildmanne39 on 2012-04-03
Hi, I personally would just wait for 12.04 because it has the classic mode also that looks almost exactly like 10.04 and it will have the latest updated packages like for firefox and all other applications.

10.04 is supported until April 2013 but all the packages will be the old packages like firefox is 11.0 in 11.10 right now but I believe it is 3.6 in 10.04, so the only new updates for 10.04 is for security.
Thanks

---

### Post by bkratz on 2012-04-03
> **wildmanne39 said:**
> Hi, I personally would just wait for 12.04 because it has the classic mode also that looks almost exactly like 10.04 and it will have the latest updated packages like for firefox and all other applications.

10.04 is supported until April 2013 but all the packages will be the old packages like firefox is 11.0 in 11.10 right now but I believe it is 3.6 in 10.04, so the only new updates for 10.04 is for security.
Thanks


@Wildmann-- I tried 12.04 classic and it is not quite "almost exactly" like 10.04.  Similar yes. Anyway, my 10.04 is using firefox 11.0 which was updated from the update manager.
Going to get another year out of 10.04!

---

### Post by troymius on 2012-04-03
This may seem like a stupid comment but did you restart your router? I have this problem sometimes, like once a month, and resetting my router fixes it. It only happens under Linux though which puzzles me.

---

### Post by xworld on 2012-04-04
So if I ran these commands ```
sudo add-apt-repository ppa:lexical/hwe-wireless sudo apt-get update sudo apt-get install rtl8192ce-dkms
```  from 11.10 would I be able to get the driver when I run 10.04?

---

### Post by wildmanne39 on 2012-04-04
Hi, no you have to be able to do it from 10.04. I will ask a friend if there is a way to get the driver without internet access.
Thanks

---

### Post by xworld on 2012-04-04
I'd appreciate that. I refuse to believe that there's nothing I can do and that I'm just not allowed to use Lucid Lynx on this computer.  Thanks a bunch

---

### Post by bkratz on 2012-04-04
> **wildmanne39 said:**
> Hi, no you have to be able to do it from 10.04. I will ask a friend if there is a way to get the driver without internet access.
Thanks



Wildmanne, would this help, it has a .deb file?

[https://launchpad.net/~lexical/+archive/hwe-wireless/+build/1854980]("https://launchpad.net/%7Elexical/+archive/hwe-wireless/+build/1854980")

---

### Post by wildmanne39 on 2012-04-04
Hi, I have been doing more research and I found a link with directions for installing the ethernet driver using the cd and the driver and a patch for it is at this link also.
[http://ubuntuforums.org/showthread.php?t=1722614](http://ubuntuforums.org/showthread.php?t=1722614)
Thanks

---

### Post by wildmanne39 on 2012-04-04
Hi bkrats, > Wildmanne, would this help, it has a .deb file?I am not sure I think it may be the same file I wanted him to add but he has no ehternet connection either, but I found a link that chili555 helped get a guys internet going in 10.04 using this driver without internet access, but it is a lot more difficult.
Thanks

---

### Post by xworld on 2012-04-04
Hello, the link you provided looks promising but the person that he helped seemed to have different system specs. How do I know what packages to download? Do I just download the same ones?

---

### Post by wildmanne39 on 2012-04-04
Hi, you need linux-headers, matching your running kernel, build-essential, patch. follow the directions in post 22.

After you have installed them download the 2 files in post 26.

You can type:
```
uname -r
```
to see what kernel headers you need to install.
Thanks

---

### Post by xworld on 2012-04-04
I'm really sorry. I hate to be so helpless, but I went to the link in post 22 and I can't locate either patch or my kernel headers.  Also when I search Maverick I don't find anything. Surely I'm confused or missing something. I know I need kernel header 2.6.32-38 generic, but I can't find it. I assume I'm supposed to be searching for all these things under lucid distribution right?  Again sorry

---

### Post by wildmanne39 on 2012-04-04
Hi, here is the exact page that the kernel headers and build essentials are on.
[http://packages.ubuntu.com/lucid/devel/](http://packages.ubuntu.com/lucid/devel/)

Pay attention to the dependency requirements for build essential that are listed in post 22 and in the link I just gave you.

It looks like patch is installed be default in 10.04.

You will put these files on an usb stick then onto ubuntu.

I have never got packages from here before and tried to install them so just follow the directions carefully.

You will install the patch using the directions from post 14 so you will need to look at it as well as 22 and maybe some other posts as well.
Thanks

---

### Post by xworld on 2012-04-04
I installed all the packages, except for one in build-essential which didn't work. And I downloaded the two files in post number 26 but I don't know what to do with them. I went into 10.04 and opened synaptic package manager and reinstalled build-essential. All packages are installed including patch and the proper linux headers. Now I'm not sure where to go from here. You say I have to download and install the 2 files from post 26? I'm not sure how to apply them.

---

### Post by wildmanne39 on 2012-04-05
What errors did you get when you tried to install build essentials because you can go no further until you have it installed.
Thanks

---

### Post by xworld on 2012-04-05
Build-essentials is completely installed. I tried install again through synaptic after I got the error and it worked. Now all packages are successfully installed. Not sure where to go from here

---

### Post by wildmanne39 on 2012-04-05
Hi, if you have every thing installed then go to post 14 of that link I gave you and follow the directions for installing the patch and driver, they are both included in that post.
Thanks

---

### Post by xworld on 2012-04-05
I am not able to open the driver file. I get this error:

```
gzip: stdin: decompression OK. trailing garbage ignored
tar: child returned status 2
exiting with failure status due to previous errors
```

I am able to open the patch file however

---

