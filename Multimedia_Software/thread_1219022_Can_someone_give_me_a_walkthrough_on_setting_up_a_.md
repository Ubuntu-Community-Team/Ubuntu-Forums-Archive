---
title: "Can someone give me a walkthrough on setting up a TV tuner?"
date: 2009-07-21
forum: Multimedia Software
---

### Post by NinjaNumberNine on 2009-07-21
Hi, I have a Kworld ATSC 120, also called KWorld PlusTV HD PCI 120. I have the manual right [[COLOR=Red]_HERE_[/COLOR]]("http://www.mythtv.org/wiki/Kworld_ATSC_120"), but the step by step is utterly confusing. I need someone to help me through each or the steps in that guide-(I think they would work if I knew what I was doing.)  I don't even know how to find if I have the latest Linux kernel!     :D

Thanks,


  NinjaNumberNine

---

### Post by NinjaNumberNine on 2009-07-21
Anybody?

---

### Post by newlinux on 2009-07-22
It would help if you told us specifically at each step what questions you have or what you don't understand. you can find out what kernel you are running by typing:

```

uname -r

```

at a command prompt.

If you are running Ibex as your information says you should probably be fine.
[http://www.linuxtv.org/wiki/index.php/KWorld_ATSC_120](http://www.linuxtv.org/wiki/index.php/KWorld_ATSC_120) says you need a kernel 2.6.26 or later (I'd follow those instructions instead of the ones you linked, which seem to assume you are running a kernel that doesn't support the ATSC 120).

also, to modify the files in the tutorial will need to add "sudo" in front of the "nano" command.

---

### Post by NinjaNumberNine on 2009-07-22
It says that I have Linux kernel 2.6.28-11-generic.

So I guess I can skip that step?

---

### Post by NinjaNumberNine on 2009-07-22
My problem really is with the driver installation.
I cannot find a way to extract the .sys driver file-
and when i did some research, It seems like some 
guy named Markus wasen't sponsoring the drivers anymore,
and the person who reported this said that for those
that had the files, hang on to them, cause they might not be able 
to get them again.

I may be wrong, though.

This is the command list...
 
# In order to use, you need to:
#       1) Download the windows driver with something like:
#               wget                [http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip](http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip)
#       2) Extract the file hcw85bda.sys from the zip into the current dir:
#               unzip -j HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip Driver85/hcw85bda.sys
#       3) run the script:
#               ./extract_xc3028.pl
#       4) copy the generated file:
#               cp xc3028-v27.fw /lib/firmware


The first two steps work fine, but on the third, ```
./extract_xc3028.pl
```
It says that the file or directory is not found!

P.S. Everywhere I read seems to require a /usr/src directory. I dont have one.:confused:

---

### Post by newlinux on 2009-07-22
you should have a /usr/src/ directory, but you can complete the steps without doing that method. What may be confusing is that they are giving you two ways to extract the firmware, download the script and use it on the .sys file, or you can find the perl script in /usr/src/linux-source-2.6.28/Documentation/video4linux/. To get that script from that location you would need to do

```

sudo apt-get install linux-source

```

and then untar the linux-source tarball. If all that sounds like more than you want to do, then all you have to do is the following:

1. Create a working directory. how about ~/drivers
```

mkdir ~/drivers

```

2. Download: [http://linuxtv.org/hg/v4l-dvb/raw-file/6477aa1782d5/linux/Documentation/video4linux/extract_xc3028.pl](http://linuxtv.org/hg/v4l-dvb/raw-file/6477aa1782d5/linux/Documentation/video4linux/extract_xc3028.pl) into the ~/drivers directory.

3. extract the hcw85bda.sys file from the zip and save it in ~/drivers

4. ```

cd ~/drivers
perl extract_xc3028.pl hcw85bda.sys
sudo cp xc3028-v27.fw /lib/firmware/
```

---

### Post by newlinux on 2009-07-22
Then you should be able to skip to step 3 in the linuxtv wiki...

Keep in mind I don't have this card, but this is my interpretation of the directions.

---

### Post by NinjaNumberNine on 2009-07-22
Okay, I'll give that a try. Thanks!

---

### Post by NinjaNumberNine on 2009-07-22
> you should have a /usr/src/ directory
Hey, wait! I installed kubuntu 9.04 and now I have a /usr/src directory!:D

---

### Post by NinjaNumberNine on 2009-07-22
Sorry for all the confusion. Anyway, I now have the hcw85bda.sys file in "drivers" but I do have the /usr/src/ folder.

---

### Post by NinjaNumberNine on 2009-07-22
How do you get to this? the manual says I need to but I could not find that option in Ubuntu or Kubuntu.:shock:
>  Device Drivers  ---> 
   Multimedia devices  --->
     <M> Video For Linux
     <M> DVB for Linux
     [*] Video capture adapters (NEW)  --->
         [*]   Autoselect pertinent encoders/decoders and other helper chips
         <M>   Conexant 2388x (bt878 successor) support
         <M>     Conexant 2388x DMA audio support
         <M>     DVB/ATSC Support for cx2388x based TV cards
     [*] DVB/ATSC adapters (NEW)  --->
     [*]   Customise the frontend modules to build
         Customise DVB Frontends  --->
            <M> Samsung S5H1409 based
 The guide says 2 disable the "video for linux" and "DVB for linux" trees.

---

### Post by newlinux on 2009-07-22
> **NinjaNumberNine said:**
> How do you get to this? the manual says I need to but I could not find that option in Ubuntu or Kubuntu.:shock:

 The guide says 2 disable the "video for linux" and "DVB for linux" trees.

Okay. Have you put the file xc3028-v27.fw in /lib/firmware?

according to [http://www.linuxtv.org/wiki/index.php/KWorld_ATSC_120](http://www.linuxtv.org/wiki/index.php/KWorld_ATSC_120) with the kernel you are running you can skip the kernel modification and skip straight to step 3, where you setup the drivers.

This thread may elso help...
[http://ubuntuforums.org/showthread.php?t=944931](http://ubuntuforums.org/showthread.php?t=944931)
According to this, you should use underscores instead of hyphens in the module names.

---

### Post by NinjaNumberNine on 2009-07-22
I dont understand. How can I get the xc3028-v27.fw???
I cant find where in the process I get that file!

---

### Post by newlinux on 2009-07-22
> **NinjaNumberNine said:**
> I dont understand. How can I get the xc3028-v27.fw???
I cant find where in the process I get that file!
It's the 4th step in the instructions I sent you above. (make sure you've done the second step)

---

### Post by NinjaNumberNine on 2009-07-22
please excuse my stupidity, but i cant seem to understand the instructions...

---

### Post by newlinux on 2009-07-22
> **NinjaNumberNine said:**
> please excuse my stupidity, but i cant seem to understand the instructions...

Judging by that screenshot, you haven't done step #2 in my instructions yet (download the extract_xc3028.pl file into the ~/drivers directory). Just click on the link I provided and save the file to ~/drivers and then run the commands from step 4.

---

### Post by NinjaNumberNine on 2009-07-22
I do have the extract_xc3028.pl file, but I cant figure how to extract it.

---

### Post by newlinux on 2009-07-22
where did you save the file to? what does:
```

ls ~/drivers

```
return?

You can't just run it unless you make it executable. otherwise you have to run it like I said in the instructions above (**perl** extract_xc3028.pl xc3028-v27.fw)

---

### Post by NinjaNumberNine on 2009-07-22
```
halstan@Victory:~$ cd ~/drivers
halstan@Victory:~/drivers$ cd /home/halstan/drivers
halstan@Victory:~/drivers$ perl extract_xc3028.pl hcw85bda.sys
md5sum: hcw85bda.sys: No such file or directory
Hash of extracted file does not match (found , expected 0e44dbf63bb0169d57446aec21881ff2!
halstan@Victory:~/drivers$

```

And thats what I get for the perl extract_xc3028.pl hcw85bda.sys.:roll:

---

### Post by newlinux on 2009-07-22
again, what does

ls ~/drivers

return?

actually, might be better to do

ls -l ~/drivers

---

### Post by NinjaNumberNine on 2009-07-22
> where did you save the file to? what does:
 

```
ls ~/drivers
```
return?

...```
halstan@Victory:~$ ls ~/drivers
extract_xc3028.pl
halstan@Victory:~$
```

> You can't just run it unless you make it executable

hadn't thought of that :mrgreen:

```
halstan@Victory:~$  ls -l ~/drivers
total 24
-rwxr-xr-x 1 halstan halstan 24285 2009-07-22 10:22 extract_xc3028.pl
halstan@Victory:~$
```

---

### Post by newlinux on 2009-07-22
Attached is the file - I just downloaded and extracted it. Ungzip it and then copy it to your /lib/firmware directory and make sure

---

### Post by newlinux on 2009-07-22
> **NinjaNumberNine said:**
> ...```
halstan@Victory:~$ ls ~/drivers
extract_xc3028.pl
halstan@Victory:~$
```


hadn't thought of that :mrgreen:

```
halstan@Victory:~$  ls -l ~/drivers
total 24
-rwxr-xr-x 1 halstan halstan 24285 2009-07-22 10:22 extract_xc3028.pl
halstan@Victory:~$
```

the problem is that you don't have the windows driver (xxx.sys) file in that directory. You were supposed to save it there...

---

### Post by NinjaNumberNine on 2009-07-22
> Unzip it and then copy it to your /lib/firmware directory
Okay, got that done.
> and make sure
make sure what?
> the problem is that you don't have the windows driver (xxx.sys) file in that directory. You were supposed to save it there
what windows driver?
you mean the hcw85bda.sys?

---

### Post by NinjaNumberNine on 2009-07-22
> what windows driver?
 you mean the hcw85bda.sys?
Never mind, I see what you had meant- I put the windows driver and the x...
one in the same folder and typed the pearl command, and it said "firmwares generated."

---

### Post by newlinux on 2009-07-22
sorry that line got cutoff make sure the firmware file is there by doing:

ls /lib/firmware/

You should see the firmware file there...

Then you can proceed to step 3 in the instructions on linuxtv (and read the other thread I posted about the hyphen/underscore issue)

---

### Post by NinjaNumberNine on 2009-07-22
Yup, the firmware's there, and I'm proceeding to Lab #3
:-D                   :-D                     :-D                       :-D

---

### Post by NinjaNumberNine on 2009-07-22
New problem- I edited the blacklists to digital but when I rebooted there was an error message: [B]KDE detected that one or more internal sound devices were removed.
Do you want KDE to permanently forget about these devices?
This is the list of devices KDE thinks can be removed:
Capture: Conexant CX8801 (CX88 Digital[/B])"
I clicked no, but when I loaded xawtv I got the following error:
```
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.28-11-generic)
xinerama 0: 1280x1024+0+0
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available

```

---

### Post by NinjaNumberNine on 2009-07-22
Should I try analogue?

---

### Post by newlinux on 2009-07-22
can you post the contents of your /etc/rc.local and /etc/modprobe.d/blacklist-misc files?

---

### Post by NinjaNumberNine on 2009-07-22
rc.local:
```
#!/bin/sh -e
#
# rc.local
# mv /etc/modprobe.d/blacklist-misc /root
  modprobe cx8800
  modprobe cx88-alsa
  cp /root/blacklist-misc /etc/modprobe.d
# # Make sure that the script will "exit 0" on success or any other
# value on error.
## In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

```
and the blacklist-misc
```
  blacklist cx8800
  blacklist cx88-alsa
```

---

### Post by NinjaNumberNine on 2009-07-22
-can you tell that my card's video output has the same motto I do?
(avoid being seen. seen, avoid being captured. captured, avoid being held)

---

### Post by newlinux on 2009-07-22
Your files aren't as the instructions said.

in your rc.local file
# mv /etc/modprobe.d/blacklist-misc /root

should be

mv /etc/modprobe.d/blacklist-misc /root

(without the #)
and /etc/modprobe.d/blacklist-misc should contain
```

blacklist cx8800
blacklist cx8802
blacklist cx88_alsa
blacklist cx88_dvb

```

If you want this to be digital that rc.local should contain
```

  mv /etc/modprobe.d/blacklist-misc /root
  modprobe cx88_dvb
  cp /root/blacklist-misc /etc/modprobe.d

```

instead of what you have.
**Note I've replaced the hyphens with underscores, as the previous thread I referenced suggested.**

Reboot. If it doesn't work, post the output of

```

lsmod | grep cx88

```

and the contents of the above two files

---

### Post by newlinux on 2009-07-22
BTW, to test the digital side you can't use xawtv. You need to use Mythtv (do you have that setup), or something like mplayer. You'll need to scan for channels first. If you don't know how to do that outside of myth, I can dig up the instructions

---

### Post by NinjaNumberNine on 2009-07-22
> in your rc.local file
 # mv /etc/modprobe.d/blacklist-misc /root
Oops, I messed up... I thought you meant to type ```
mv /etc/modprobe.d/blacklist-misc /root
``` in terminal.. now the backlist-misc file is gone :shock:
Which card type should I pick in card setup (mythtv)
assuming I have digital signal?

---

### Post by NinjaNumberNine on 2009-07-22
lsmod | grep cx88:
```
root@Victory:/home/halstan# lsmod | grep cx88
cx88_alsa              18824  1
cx8800                 38148  0
compat_ioctl32          9344  1 cx8800
cx88_dvb               29444  0
cx88_vp3054_i2c        10624  1 cx88_dvb
v4l2_common            20992  2 cx8800,tuner
snd_pcm                82948  3 cx88_alsa,snd_hda_intel,snd_pcm_oss
cx8802                 24068  1 cx88_dvb
cx88xx                 79272  4 cx88_alsa,cx8800,cx88_dvb,cx8802
videodev               41600  3 cx8800,tuner,cx88xx
ir_common              52228  1 cx88xx
i2c_algo_bit           14084  2 cx88_vp3054_i2c,cx88xx
tveeprom               20100  1 cx88xx
videobuf_dvb           15236  3 cx88_dvb,cx8802,cx88xx
dvb_core               92032  2 cx88_dvb,videobuf_dvb
snd                    62628  16 cx88_alsa,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
btcx_risc              13064  4 cx88_alsa,cx8800,cx8802,cx88xx
videobuf_dma_sg        20484  5 cx88_alsa,cx8800,cx88_dvb,cx8802,cx88xx
videobuf_core          26500  5 cx8800,cx8802,cx88xx,videobuf_dvb,videobuf_dma_sg
root@Victory:/home/halstan#
```

---

### Post by NinjaNumberNine on 2009-07-22
I will be gone for about four days- stick around, please! [-o<

---

### Post by newlinux on 2009-07-23
I don't think the contents of your /etc/modprobe.d/blacklist-misc file is right. make sure your rc.local and blacklist-misc are as specified in earlier posts.

The lsmod output you gave indicates the proper modules aren't being blacklisted (they are loaded, which they shouldn't be).

You shouldn't see:
 cx8800
 cx8802
 cx88_alsa

in the output of lsmod for digital setup. You should see cx88_dvb.

In myth you should choose a DVB card. but you're system isn't ready to test that yet based on your lsmod results.

---

### Post by NinjaNumberNine on 2009-07-28
Okay, I am back now.

Fire away!

---

### Post by newlinux on 2009-07-28
> **NinjaNumberNine said:**
> Okay, I am back now.

Fire away!

see my prior post...

---

### Post by NinjaNumberNine on 2009-07-28
This is my rc.local file:
```
#!/bin/sh -e
#
# rc.local
#  mv /etc/modprobe.d/blacklist-misc /root
  modprobe cx88_dvb
  cp /root/blacklist-misc /etc/modprobe.d
# # Make sure that the script will "exit 0" on success or any other
# value on error.
## In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0


```


What I want to know is, where SPECIFICALLY in this file do I put the > ```
mv /etc/modprobe.d/blacklist-misc /root
```

---

### Post by newlinux on 2009-07-28
> **NinjaNumberNine said:**
> This is my rc.local file:
```
#!/bin/sh -e
#
# rc.local
#  mv /etc/modprobe.d/blacklist-misc /root
  modprobe cx88_dvb
  cp /root/blacklist-misc /etc/modprobe.d
# # Make sure that the script will "exit 0" on success or any other
# value on error.
## In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0


```


What I want to know is, where SPECIFICALLY in this file do I put the
You already have it in the file. You just need to remove the # in front of it (which makes the line ignored). This is what I mentioned earlier. Correct that and make sure the contents of /etc/modprobe.d/blacklist-misc are correct and post them here. Then reboot and give me the result of the lsmod command I mentioned earlier.

---

### Post by NinjaNumberNine on 2009-07-28
Okay, the rc.local file is set up.

The contents of  /etc/modprobe.d/blacklist-misc are as follows:
```
blacklist cx8800
blacklist cx8802
blacklist cx88_alsa
blacklist cx88_dvb

```

---

### Post by NinjaNumberNine on 2009-07-28
lsmod:
```
halstan@Victory:~$ lsmod
Module                  Size  Used by
s5h1409                17028  1      
cx88_dvb               29444  0      
cx88_vp3054_i2c        10624  1 cx88_dvb
tuner_xc2028           28976  2         
tuner                  32836  0         
v4l2_common            20992  1 tuner   
cx8802                 24068  1 cx88_dvb
cx88xx                 79272  2 cx88_dvb,cx8802
videodev               41600  2 tuner,cx88xx   
v4l1_compat            21764  1 videodev       
ir_common              52228  1 cx88xx         
i2c_algo_bit           14084  2 cx88_vp3054_i2c,cx88xx
tveeprom               20100  1 cx88xx                
btcx_risc              13064  2 cx8802,cx88xx         
videobuf_dvb           15236  3 cx88_dvb,cx8802,cx88xx
videobuf_dma_sg        20484  3 cx88_dvb,cx8802,cx88xx
videobuf_core          26500  4 cx8802,cx88xx,videobuf_dvb,videobuf_dma_sg
dvb_core               92032  2 cx88_dvb,videobuf_dvb                     
i915                   65540  2                                           
drm                    96296  3 i915                                      
bridge                 56340  0                                           
stp                    10500  1 bridge                                    
bnep                   20224  2                                           
nfsd                  227756  13                                          
lockd                  74156  1 nfsd                                      
nfs_acl                11136  1 nfsd                                      
auth_rpcgss            42144  1 nfsd                                      
sunrpc                195424  13 nfsd,lockd,nfs_acl,auth_rpcgss           
exportfs               12544  1 nfsd                                      
video                  25360  0                                           
output                 11008  1 video                                     
input_polldev          11912  0                                           
lp                     17156  0                                           
snd_hda_intel         435636  2                                           
snd_pcm_oss            46336  0
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0
snd_seq_oss            37760  0
snd_seq_midi           14336  0
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
iTCO_wdt               19108  0
iTCO_vendor_support    11652  1 iTCO_wdt
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
psmouse                61972  0
ppdev                  15620  0
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13316  0
intel_agp              34108  1
agpgart                42696  3 drm,intel_agp
pcspkr                 10496  0
parport_pc             40100  1
parport                42220  3 lp,ppdev,parport_pc
snd                    62628  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
usb_storage            82880  0
e100                   41740  0
mii                    13312  1 e100
fbcon                  46112  0
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```
lsmod | grep cx88:

```
halstan@Victory:~$ lsmod | grep cx88
cx88_dvb               29444  0
cx88_vp3054_i2c        10624  1 cx88_dvb
cx8802                 24068  1 cx88_dvb
cx88xx                 79272  2 cx88_dvb,cx8802
videodev               41600  2 tuner,cx88xx
ir_common              52228  1 cx88xx
i2c_algo_bit           14084  2 cx88_vp3054_i2c,cx88xx
tveeprom               20100  1 cx88xx
btcx_risc              13064  2 cx8802,cx88xx
videobuf_dvb           15236  3 cx88_dvb,cx8802,cx88xx
videobuf_dma_sg        20484  3 cx88_dvb,cx8802,cx88xx
videobuf_core          26500  4 cx8802,cx88xx,videobuf_dvb,videobuf_dma_sg
dvb_core               92032  2 cx88_dvb,videobuf_dvb
halstan@Victory:~$

```
sudo nano /etc/modprobe.d/blacklist-misc
```
blacklist cx8800
blacklist cx8802
blacklist cx88_alsa
blacklist cx88_dvb
```

rc.local
```
#!/bin/sh -e
#
# rc.local
  mv /etc/modprobe.d/blacklist-misc /root
  modprobe cx88_dvb
  cp /root/blacklist-misc /etc/modprobe.d
# Make sure that the script will "exit 0" on success or any other
# value on error.
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0


```

---

### Post by NinjaNumberNine on 2009-07-28
Back again...

---

### Post by NinjaNumberNine on 2009-07-29
Now, I dont know how to best test the card...
This is what I get with 'DVB-DTV capture card (v3.x)' in MythBackend:

---

### Post by newlinux on 2009-07-29
That looks fine. Samsung S5H1409 is the digital demodulator used for this card. Are you familiar with myth at all? you will want to complete this page, setup a video source and scan for channels using QAM (if you have digital cable connected) or ATSC 8vsb (if you have an antenna connected to the card). Make sure to let the scan complete fully. It may take a while. Do you know what stations you should get?

Is myth the application you plan on using with this card? If not, I'd recommend you test with mplayer and scan. There are a lot more variables to getting myth right.

---

### Post by NinjaNumberNine on 2009-07-29
> Is myth the application you plan on using with this card?
Well, if it works, MythTV would be great. The problem is, when I choose DVB-DTV, the only "choose video source" options in channel scanner are "none" and "unassigned. How do you "scan using QAM"?

> I'd recommend you test with mplayer and scan

I dont even know how to load my card in mplayer, but at this point, I would be glad to get anything to work.

---

### Post by NinjaNumberNine on 2009-07-29
Oh, and will Xine work with digital too?

---

### Post by newlinux on 2009-07-29
> **NinjaNumberNine said:**
> Well, if it works, MythTV would be great. The problem is, when I choose DVB-DTV, the only "choose video source" options in channel scanner are "none" and "unassigned. How do you "scan using QAM"?



I dont even know how to load my card in mplayer, but at this point, I would be glad to get anything to work.

You have to create the video source first, then assign it to an input, then scan. So you probably haven't created any video sources. you might want to look at the mythtv user manual or a guide to setting it up. Plenty out there about backend setup


I don't have time now to write up instructions, but you can search these forums for using the "scan" utility and creating a "channels.conf" file and using that with mplayer dvb:// or kaffiene. I think xine can too.

---

### Post by NinjaNumberNine on 2009-07-29
Now the capture card menu shows this!

Is the ERROR_OPEN important?

---

### Post by NinjaNumberNine on 2009-07-29
I have to get this card working within two days or my dad is going to say > You are wasting your time- Cant even get a signal. MythTV really is a myth...
And I will have to stop working on it...

---

### Post by newlinux on 2009-07-29
> **NinjaNumberNine said:**
> I have to get this card working within two days or my dad is going to say 
And I will have to stop working on it...

I think you should have gotten a card that works out of the box then... You really should get the card working (I recommend mplayer and scan) before complicating things with myth setup. Your problem isn't getting myth to work. It's getting the card to work.

What have you changed since this screen showed the right thing? Also, if you were interested in doing myth, you should have posted this thread in the mythbuntu section.

---

### Post by NinjaNumberNine on 2009-07-30
> Also, if you were interested in doing myth, you should have posted this thread in the mythbuntu section.
Well, its like I said. I want any TV program that works.
 > You should have posted this thread in the mythbuntu section.But I don't have Mythbuntu.

---

### Post by NinjaNumberNine on 2009-07-30
I would be very thankful if you could show me how to do an mplayer channel scan.

---

### Post by NinjaNumberNine on 2009-07-30
> A card that works out of the box
Easy to say, but I could not find any. I am sure there are some out there, but I want one that is ATSC/NTSC compatible. If you know one like that that is very easy to set up AND costs around $50, let me know, please.

---

### Post by NinjaNumberNine on 2009-07-30
Okay, kill me if you like, but I just reinstalled Kubuntu 9.04. :cry:
I will go through everything I have learned in this thread and try to get back to the part where I could successfully scan channels in MythTV. (I did get to that, and it found all my channels, but when I ran the frontend and hit "Watch TV," it showed a black screen and the program went unresponsive.) (And yes, I had picked a steady starting channel)
Anyway, please notify me if anything I do is wrong. I am going to post the steps as I make them.

  Thanks sincerely,

          NinjaNumberNine

---

### Post by xc3RnbFO8P on 2009-07-30
Try **Kaffeine** 
in Synaptic Package Manager

---

### Post by newlinux on 2009-07-30
> **NinjaNumberNine said:**
> Well, its like I said. I want any TV program that works.
 But I don't have Mythbuntu.

The forum is for ubuntu users who install myth, not just those who install the mythbuntu variant of ubuntu on their machine.

> **NinjaNumberNine said:**
> I would be very thankful if you could show me how to do an mplayer channel scan.
If you are scanning for QAM stations, make sure no other applications are using the tuner, like mythbackend (and make sure the proper modules are loaded (and not the ones that shouldn't be loaded) 

```

sudo apt-get install dvb-utils
mkdir ~/.azap
scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-Cable-Standard-center-frequencies-QAM256 > ~/.azap/channels.conf

```
This scan will take a while. verify there are channels in your channels.conf file that you just created.

```

ln -s ~/.azap/channels.conf ~/.mplayer/
mplayer dvb://  -cache 8192

```

MPlayer should start playing the first channel listed in your channels.conf. You should be able to move through your channels.conf list by using h (next channel) and k (previous channel) on your keyboard. When switching between channels, the video window will shut/close, but you will see in the console that you launched MPlayer from that the next channel you are attempting to view is queueing up before the next video window is opened up, displaying the next channel. If one of the channels has something wrong with it, MPlayer will appear to be hung (nothing happening or some error reported in the console output), but just hit ctrl-c to terminate. Alternatively, you can pass the names of the channels themselves (e.g.):
```

mplayer dvb://ABC-DT -cache 8192

```
where ABC-DT is a channel name in your ~/.mplayer/channels.conf file.

> **NinjaNumberNine said:**
> Easy to say, but I could not find any. I am sure there are some out there, but I want one that is ATSC/NTSC compatible. If you know one like that that is very easy to set up AND costs around $50, let me know, please.

Check my hardware in my signature. Not a single card cost me more than $50 (I only buy on sale), and the only thing on current kernels I have to do to get any of them to work is put the firmware file in the right place and/or load the proper module.  And I only have to do this once - works every boot after that. The Dvico worked out of the box. All but the PVR-150 do ATSC/QAM and. the Kworld do ATSC/QAM/NTSC, as does the dvico. You might have a harder time finding those cards now as they are older.

The Pinacle 800i and Hauppage HVR-1800 (PCIe) don't require as much to get working either, for most and both support ATSC/QAM/NTSC. Still the HVR-1600 shouldn't be too hard to get working, if you accurately follow the instructions.

> **NinjaNumberNine said:**
> Okay, kill me if you like, but I just reinstalled Kubuntu 9.04. :cry:
I will go through everything I have learned in this thread and try to get back to the part where I could successfully scan channels in MythTV. (I did get to that, and it found all my channels, but when I ran the frontend and hit "Watch TV," it showed a black screen and the program went unresponsive.) (And yes, I had picked a steady starting channel)
Anyway, please notify me if anything I do is wrong. I am going to post the steps as I make them.

  Thanks sincerely,

          NinjaNumberNine
You probably just didn't have your playback profiles configured properly. You'd need to look in your mythfrontend.log to get more info. Try changing that setting in the frontend. Playback configuration in myth is another story. What hardware are you running (specifically CPU and GPU)?

---

### Post by newlinux on 2009-07-30
> **Ringi said:**
> Try **Kaffeine** 
in Synaptic Package Manager

Last I checked, Kaffeine can play digital stations, but doesn't scan for QAM or ATSC, so you still have to create a channels.conf file and convert it to KAffeine's format.

---

### Post by NinjaNumberNine on 2009-07-30
> Not a single card cost me more than $50 (I only buy on sale)
Now the Kworld 110 is not even available and the Kworld 115 (nearly identical chipset) is $89 or higher.

---

### Post by NinjaNumberNine on 2009-07-30
> Quote:
 Originally Posted by NinjaNumberNine View Post 
Well, its like I said. I want any TV program that works.
 But I don't have Mythbuntu.
The forum is for ubuntu users who install myth, not just those who install the mythbuntu variant of ubuntu on their machine.
 
 
Quote:
 Originally Posted by NinjaNumberNine View Post 
I would be very thankful if you could show me how to do an mplayer channel scan.
If you are scanning for QAM stations, make sure no other applications are using the tuner, like mythbackend (and make sure the proper modules are loaded (and not the ones that shouldn't be loaded) 
 
 
Code:
sudo apt-get install dvb-utils
mkdir ~/.azap
scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-Cable-Standard-center-frequencies-QAM256 > ~/.azap/channels.conf
This scan will take a while. verify there are channels in your channels.conf file that you just created.
 
 
Code:
ln -s ~/.azap/channels.conf ~/.mplayer/
mplayer dvb://  -cache 8192
MPlayer should start playing the first channel listed in your channels.conf. You should be able to move through your channels.conf list by using h (next channel) and k (previous channel) on your keyboard. When switching between channels, the video window will shut/close, but you will see in the console that you launched MPlayer from that the next channel you are attempting to view is queueing up before the next video window is opened up, displaying the next channel. If one of the channels has something wrong with it, MPlayer will appear to be hung (nothing happening or some error reported in the console output), but just hit ctrl-c to terminate. Alternatively, you can pass the names of the channels themselves (e.g.):
 
Code:
mplayer dvb://ABC-DT -cache 8192
where ABC-DT is a channel name in your ~/.mplayer/channels.conf file.
 
 
Quote:
 Originally Posted by NinjaNumberNine View Post 
Easy to say, but I could not find any. I am sure there are some out there, but I want one that is ATSC/NTSC compatible. If you know one like that that is very easy to set up AND costs around $50, let me know, please.
Check my hardware in my signature. Not a single card cost me more than $50 (I only buy on sale), and the only thing on current kernels I have to do to get any of them to work is put the firmware file in the right place and/or load the proper module. And I only have to do this once - works every boot after that. The Dvico worked out of the box. All but the PVR-150 do ATSC/QAM and. the Kworld do ATSC/QAM/NTSC, as does the dvico. You might have a harder time finding those cards now as they are older.
 
 The Pinacle 800i and Hauppage HVR-1800 (PCIe) don't require as much to get working either, for most and both support ATSC/QAM/NTSC. Still the HVR-1600 shouldn't be too hard to get working, if you accurately follow the instructions.
 
 
Quote:
 Originally Posted by NinjaNumberNine View Post 
Okay, kill me if you like, but I just reinstalled Kubuntu 9.04. 
 I will go through everything I have learned in this thread and try to get back to the part where I could successfully scan channels in MythTV. (I did get to that, and it found all my channels, but when I ran the frontend and hit "Watch TV," it showed a black screen and the program went unresponsive.) (And yes, I had picked a steady starting channel)
 Anyway, please notify me if anything I do is wrong. I am going to post the steps as I make them.
 
 Thanks sincerely,
 
 NinjaNumberNine
You probably just didn't have your playback profiles configured properly. You'd need to look in your mythfrontend.log to get more info. Try changing that setting in the frontend. Playback configuration in myth is another story. What hardware are you running (specifically CPU and GPU)?
Thanks for replies- but now I am going to be all mixed up. I am still trying to get back to the previous setup. I'll ask more questions when I get there.

---

### Post by newlinux on 2009-07-30
> **NinjaNumberNine said:**
> Now the Kworld 110 is not even available and the Kworld 115 (nearly identical chipset) is $89 or higher.

As I said, you'll have a harder time finding them now, but you can definitely find the 115 for less than $89 (and you can certainly get the pinnacle 800i for less than that). The kind of deals I got mine on where like this:

[http://www.techbargains.com/news_displayItem.cfm/126577](http://www.techbargains.com/news_displayItem.cfm/126577)

unfortunately, that's long since expired.

I paid less than $40 for most of my cards. If price is really important to you, you'll find or wait for the sales. There's always ebay if you trust that...

[http://cgi.ebay.com/Kworld-ATSC-110-TV-tuner-with-Firefly-remote-HDTV-ready_W0QQitemZ180389430432QQcmdZViewItemQQptZPCC_Video_TV_Cards?hash=item2a000c44a0&_trksid=p3286.c0.m14](http://cgi.ebay.com/Kworld-ATSC-110-TV-tuner-with-Firefly-remote-HDTV-ready_W0QQitemZ180389430432QQcmdZViewItemQQptZPCC_Video_TV_Cards?hash=item2a000c44a0&_trksid=p3286.c0.m14)

If time is more than issue, then you are stuck, I guess.

---

### Post by newlinux on 2009-07-30
> **NinjaNumberNine said:**
> Thanks for replies- but now I am going to be all mixed up. I am still trying to get back to the previous setup. I'll ask more questions when I get there.

I think I've provided all the information you need to use the card. Hopefully it will work. 

If you end up using myth and have myth problems, you'll probably want to post in the mythbuntu forums

---

### Post by NinjaNumberNine on 2009-07-30
> The kind of deals I got mine on where like this:
 
 [http://www.techbargains.com/news_displayItem.cfm/126577](http://www.techbargains.com/news_displayItem.cfm/126577)
WOW I wish that was still around!

> I think I've provided all the information you need to use the card.
Does that mean you're leaving? :icon_frown:

---

### Post by newlinux on 2009-07-30
> **NinjaNumberNine said:**
> WOW I wish that was still around!


Does that mean you're leaving? :icon_frown:
No... I like to help when I have time. I'll still be around.

---

### Post by NinjaNumberNine on 2009-07-30
Okay, I installed the firmware and configured the rc.local and blacklist-misc files, so now I should be ready to do a channel scan in mplayer; this is what happens.
```
halstan@Victory:~$ sudo apt-get install dvb-utils
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  dvb-apps
The following NEW packages will be installed:
  dvb-apps dvb-utils
0 upgraded, 2 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 696kB of archives.
After this operation, 6210kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com jaunty/universe dvb-apps 1.1.1+rev1207-4 [687kB]
Get:2 http://us.archive.ubuntu.com jaunty/universe dvb-utils 1.1.1+rev1207-4 [9156B]
Fetched 696kB in 19s (36.1kB/s)
Selecting previously deselected package dvb-apps.
(Reading database ... 113445 files and directories currently installed.)
Unpacking dvb-apps (from .../dvb-apps_1.1.1+rev1207-4_i386.deb) ...
Selecting previously deselected package dvb-utils.
Unpacking dvb-utils (from .../dvb-utils_1.1.1+rev1207-4_all.deb) ...
Setting up mythexport (2.0-0ubuntu1) ...
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
dpkg: error processing mythexport (--configure):
 subprocess post-installation script returned error exit status 1
Setting up dvb-apps (1.1.1+rev1207-4) ...

Setting up dvb-utils (1.1.1+rev1207-4) ...
Errors were encountered while processing:
 mythexport
E: Sub-process /usr/bin/dpkg returned an error code (1)
halstan@Victory:~$ mkdir ~/.azap
halstan@Victory:~$ scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-Cable-Standard-center-frequencies-QAM256 > ~/.azap/channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/atsc/us-Cable-Standard-center-frequencies-QAM256
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
ERROR: cannot open '/usr/share/doc/dvb-utils/examples/scan/atsc/us-Cable-Standard-center-frequencies-QAM256': 2 No such file or directory
ERROR: initial tuning failed
dumping lists (0 services)
Done.
halstan@Victory:~$

```
Does that tell you anything?

-Anyway now I will try with MythTV...

---

### Post by NinjaNumberNine on 2009-07-30
Okay, apparently the only thing that works for me is QAM-64 to scan for channels. (see the attachment) but somehow, the channel scan left out about 20 channels.  :confused: :confused:

---

### Post by NinjaNumberNine on 2009-07-30
Something weird is going on. Now, when I load the Frontend, on certain channels I hear music! The strange thing is, I don't have any channels with just music- I think that the channels are radio frequencies!

---

### Post by NinjaNumberNine on 2009-07-30
after flipping through five black screen channels (with radio music) the following happens:


Also, (see screenshot #2,) the only options are different varieties of NTSC, SECAM, and PAL. 
No options for ATSC:confused:

(By the way, I did had it set on NTSC. I accidentally changed it to PAL-60 while getting the screenshot, so that's why it shows that in the attachment)

I'll be back tomorrow...

---

### Post by newlinux on 2009-07-30
> **NinjaNumberNine said:**
> Okay, I installed the firmware and configured the rc.local and blacklist-misc files, so now I should be ready to do a channel scan in mplayer; this is what happens.
```
halstan@Victory:~$ sudo apt-get install dvb-utils
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  dvb-apps
The following NEW packages will be installed:
  dvb-apps dvb-utils
0 upgraded, 2 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 696kB of archives.
After this operation, 6210kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com jaunty/universe dvb-apps 1.1.1+rev1207-4 [687kB]
Get:2 http://us.archive.ubuntu.com jaunty/universe dvb-utils 1.1.1+rev1207-4 [9156B]
Fetched 696kB in 19s (36.1kB/s)
Selecting previously deselected package dvb-apps.
(Reading database ... 113445 files and directories currently installed.)
Unpacking dvb-apps (from .../dvb-apps_1.1.1+rev1207-4_i386.deb) ...
Selecting previously deselected package dvb-utils.
Unpacking dvb-utils (from .../dvb-utils_1.1.1+rev1207-4_all.deb) ...
Setting up mythexport (2.0-0ubuntu1) ...
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
dpkg: error processing mythexport (--configure):
 subprocess post-installation script returned error exit status 1
Setting up dvb-apps (1.1.1+rev1207-4) ...

Setting up dvb-utils (1.1.1+rev1207-4) ...
Errors were encountered while processing:
 mythexport
E: Sub-process /usr/bin/dpkg returned an error code (1)
halstan@Victory:~$ mkdir ~/.azap
halstan@Victory:~$ scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-Cable-Standard-center-frequencies-QAM256 > ~/.azap/channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/atsc/us-Cable-Standard-center-frequencies-QAM256
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
ERROR: cannot open '/usr/share/doc/dvb-utils/examples/scan/atsc/us-Cable-Standard-center-frequencies-QAM256': 2 No such file or directory
ERROR: initial tuning failed
dumping lists (0 services)
Done.
halstan@Victory:~$

```
Does that tell you anything?

-Anyway now I will try with MythTV...

looks like something is wrong with your package management. I don't think everything was installed right. Did you try installing mythexport earlier? If dvb-utils doesn't install right, you won't have the files you need to scan with... or maybe they put them in a different location now...

---

### Post by newlinux on 2009-07-30
> **NinjaNumberNine said:**
> Okay, apparently the only thing that works for me is QAM-64 to scan for channels. (see the attachment) but somehow, the channel scan left out about 20 channels.  :confused: :confused:

the channels left out are probably QAM-256 (where I live almost all the stations are QAM-256 and only 4 are QAM-64 - but this can vary). Did you do a full QAM-256 and QAM-64 (not high or low).

---

### Post by newlinux on 2009-07-30
> **NinjaNumberNine said:**
> Something weird is going on. Now, when I load the Frontend, on certain channels I hear music! The strange thing is, I don't have any channels with just music- I think that the channels are radio frequencies!

Most cable providers have a bunch of music only  channels (mine does and it rebroadcast local radio stations too). These are usually unencrypted so that's probably what you've got.

---

### Post by newlinux on 2009-07-30
> **NinjaNumberNine said:**
> after flipping through five black screen channels (with radio music) the following happens:


Also, (see screenshot #2,) the only options are different varieties of NTSC, SECAM, and PAL. 
No options for ATSC:confused:

(By the way, I did had it set on NTSC. I accidentally changed it to PAL-60 while getting the screenshot, so that's why it shows that in the attachment)

I'll be back tomorrow...

This means you found a video channel. As I mentioned earlier, you probably have bad playback settings for your hardware, so stations that actually show video probably will fail. I can't help you with that until you answer the questions I asked you about your GPU and CPU. you will probably want to look in your logs. Also, the only things you should be scanning for is QAM. Your problem with displaying video isn't tuning, it's playback (which is why it's easier test the card with mplayer). You need to get your playback settings right.

Also if you are in the U.S. your tv format (this is different from what you are tuning) should be NTSC

---

### Post by newlinux on 2009-07-30
> **newlinux said:**
> the channels left out are probably QAM-256 (where I live almost all the stations are QAM-256 and only 4 are QAM-64 - but this can vary). Did you do a full QAM-256 and QAM-64 (not high or low).

You also may need to look into using QAM-HRC and/or QAM-IRC tuning as well...

you might want to go to [http://www.silicondust.com/hdhomerun/channels_us](http://www.silicondust.com/hdhomerun/channels_us) to see what channels you should be getting qam256 and qam64, etc. Make sure to select the right provider.

---

### Post by xc3RnbFO8P on 2009-07-31
> **NinjaNumberNine said:**
> Something weird is going on. Now, when I load the Frontend, on certain channels I hear music! The strange thing is, I don't have any channels with just music- I think that the channels are radio frequencies!

Don't you need a Cable TV De-Scambler to see Cable TV, how do you connect to the cable?

---

### Post by newlinux on 2009-07-31
> **Ringi said:**
> Don't you need a Cable TV De-Scambler to see Cable TV, how do you connect to the cable?
Most U.S. providers make at least some of the channels available via analog (unscrambled - usually just basic channels) and via unencrypted QAM (in my case, all the basic channels are available in addition to the HD versions of the local stations). What is available may vary, but almost all cable providers at least make the locals and HD locals available via unencrypted QAM. You don't need any box or anything (I actually don't have a cable box) to tune unencrypted QAM stations or unscrambled analog stations. just connect the coax directly from the wall to the tuner.

---

### Post by NinjaNumberNine on 2009-07-31
thanks for all the posts- that will hold me for a while!

---

### Post by NinjaNumberNine on 2009-07-31
> 1: looks like something is wrong with your package management. I don't think everything was installed right. 2: Did you try installing mythexport earlier? 3:If dvb-utils doesn't install right, you won't have the files you need to scan with... or maybe they put them in a different location now...
1: Sorry, I left out something. I had just had a package manager crash, (I was installing a little game, nothing important) and when I tried to run the "install dvb-utils" it said there were errors and I needed to run "dpkg-configure" (or something like that, I am just typing these from memory)
so I ran that, it seemed to go okay, an then I got what you saw earlier.

2: Yes, actually I did. I searched myth in Package Manager (like synaptic) and installed all the things that sounded like accessories, and mythexport was one of them.

3: could I try installing it through the Package Manager (adept)?

---

### Post by NinjaNumberNine on 2009-07-31
Ok, I ran all this. Does it sound any better?

```
halstan@Victory:~$ **dpkg --configure -a**
dpkg: requested operation requires superuser privilege
halstan@Victory:~$ **sudo su  **                          
[sudo] password for halstan:                          
root@Victory:/home/halstan# **dpkg --configure -a       **
Setting up mythexport (2.0-0ubuntu1) ...              
Enter password:                                       
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
dpkg: error processing mythexport (--configure):                                   
 subprocess post-installation script returned error exit status 1                  
Errors were encountered while processing:                                          
 mythexport                                                                        
root@Victory:/home/halstan# **sudo aptitude purge mythexport**
Reading package lists... Done                             
Building dependency tree                                  
Reading state information... Done                         
Initializing package states... Done                       
Writing extended state information... Done                
The following packages will be REMOVED:                   
  mythexport{p}                                           
0 packages upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
Need to get 0B of archives. After unpacking 283kB will be freed.       
Do you want to continue? [Y/n/?] y                                     
Writing extended state information... Done                             
(Reading database ... 114732 files and directories currently installed.)
Removing mythexport ...                                                 
 * Reloading web server config apache2                                                                                                         apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName                                 
                                                                                                                                        [ OK ] 
 * Stopping MythExport Daemon: mythexport                                                                                                      No /usr/bin/perl found running; none killed.                                                                                                   
                                                                                                                                        [ OK ] 
Purging configuration files for mythexport ...                                                                                                 
rm: cannot remove `/var/www/.mythtv': Is a directory                                                                                           
dpkg: error processing mythexport (--purge):                                                                                                   
 subprocess post-removal script returned error exit status 1                                                                                   
Processing triggers for man-db ...                                                                                                             
Errors were encountered while processing:
 mythexport
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done

root@Victory:/home/halstan# **dpkg --configure -a**
root@Victory:/home/halstan# **sudo apt-get install dvb-utils**
Reading package lists... Done
Building dependency tree
Reading state information... Done
dvb-utils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
root@Victory:/home/halstan# **sudo apt-get remove dvb-utils**
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  dvb-utils
0 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
After this operation, 45.1kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 114695 files and directories currently installed.)
Removing dvb-utils ...
root@Victory:/home/halstan#** sudo apt-get install dvb-utils**
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  dvb-utils
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 0B/9156B of archives.
After this operation, 45.1kB of additional disk space will be used.
Selecting previously deselected package dvb-utils.
(Reading database ... 114692 files and directories currently installed.)
Unpacking dvb-utils (from .../dvb-utils_1.1.1+rev1207-4_all.deb) ...
Setting up dvb-utils (1.1.1+rev1207-4) ...
root@Victory:/home/halstan#

```


Does it sound like dvb-utils is installed right now?

---

### Post by NinjaNumberNine on 2009-07-31
I dont get it. In May our cable company started giving digital signal, so shouldn't I choose ATSC?

---

### Post by NinjaNumberNine on 2009-07-31
I think I will try setting up the rc.local for analog tv.

---

### Post by newlinux on 2009-07-31
> **NinjaNumberNine said:**
> I dont get it. In May our cable company started giving digital signal, so shouldn't I choose ATSC?

Not where it asks for TV format in the general settings of mythtv-setup. This field isn't for the type of signal your tuning.

And yes, it seems dvb-utils is installed correctly. Why are you giving up on digital? You were able to scan for and tune channels. You need to get your playback working (and you haven't answered the questions I need you to answer to help you with that). I wouldn't switch unless what you ultimately want to record and view are analog channels. you should stay with the type of signal you plan on using.

---

### Post by NinjaNumberNine on 2009-07-31
> you should stay with the type of signal you plan on using.
If you say so... But I want something that works! If you think we can get digital to work, I will keep trying.

---

### Post by NinjaNumberNine on 2009-07-31
You mean:
>  I can't help you with that until you answer the questions I asked you about your GPU and CPU.
You never asked any questions that I know of.

---

### Post by NinjaNumberNine on 2009-07-31
By the way, analog works fine in mythtv and tvtime. I can see video and hear audio- but the quality is horrible. I would like to continue with digital, (I just wanted analog as a backup plan.)
I have the rc.local and blacklist-misc files reconfigured for digital again.

---

### Post by newlinux on 2009-07-31
> **NinjaNumberNine said:**
> You mean:

You never asked any questions that I know of.

I have asked you multiple times about your GPU/CPU, playback settings and logs. Look back or search through the thread. If you don't read what I write to help you or answer my questions I can't help you anymore.

---

### Post by NinjaNumberNine on 2009-07-31
Are you feeling irritated?:shock:

---

### Post by newlinux on 2009-07-31
> **NinjaNumberNine said:**
> If you say so... But I want something that works! If you think we can get digital to work, I will keep trying.
You already had digital tuning working. I gave you suggestions for getting more channels in your scan which I never heard anything back from you about. The problem you had was with your playback - which is probably why your analog pictures looked bad. I've said this multpile times in this thread. I can't say for sure because you haven't said anything about your mythfrontend logs, your playback settings, or your hardware, that I have asked about more than once. I've asked other things in this thread and given suggestions and instructions that you haven't even responded to that would have helped you and I've had to explain things multiple times - which leads me to believe you aren't paying good attention to what I'm writing, and I think my help is being wasted.

---

### Post by newlinux on 2009-07-31
> **NinjaNumberNine said:**
> Are you feeling irritated?:shock:

annoyed is a better word. Seems to me that if you wanted help, you'd pay attention when you got it instead telling me I didn't write what I did, or asking me questions I've already answered in this thread, or ignoring what I've written.

---

### Post by NinjaNumberNine on 2009-07-31
I fully apologize. I did not mean it like it sounded, I had just overlooked that question. I did find it, and now I am working on it.

---

### Post by NinjaNumberNine on 2009-07-31
> I can't say for sure because you haven't said anything about your mythfrontend logs, your playback settings, or your hardware
As for that, I dont even know where the mythfrontend log **is**, I dont know which playback settings you want, and I dont have a device manager to find the gpus and cpus and such. 

[SIZE="7"]AND...[/SIZE] 
I am a complete Linux nOOb. I have used Windows all my life, and now everyone expects me to know stuff about linux that I have never even heard of.
> and I think my help is being wasted.
maybe you're right...
But I am definitely learning a lot..

---

### Post by NinjaNumberNine on 2009-07-31
> Thanks that was informative
what, newlinux's posts?

---

### Post by newlinux on 2009-07-31
> **NinjaNumberNine said:**
> As for that, I dont even know where the mythfrontend log **is**, I dont know which playback settings you want, and I dont have a device manager to find the gpus and cpus and such. 
that's all fine. But up until now you didn't even acknowledge that I asked the questions, so how could I help you get the answer? If you had addressed these, you wouldn't be having as much problems and I'd be able to help you more. Also, you still haven't  addressed/responded to some questions and suggestions. 

There is a hardware manager application, but I don't remember how you get to it in KDE. Can't you look up the specs of the computer you have? I would assume if you built it yourself you'd know the specs. If not, post the output of:

```

lspci -v

```
and
```

cat /proc/cpuinfo | grep -i model

```

Mythfrontend log  (and mythbackend) is at
/var/log/mythtv

if you are running mythfrontend from the menu. If you run it commandline you can specify where it logs to by doing:
```

mythfrontend -l name_of_log_file

```
Which you would easily find out if you went to the mythbuntu forums and searched. You need to post it from a time when you got the video display error when trying to tune a channel. 

>  
I am a complete Linux nOOb. I have used Windows all my life, and now everyone expects me to know stuff about linux that I have never even heard of.

maybe you're right...
But I am definitely learning a lot..

If you are a noobie, all the more reason to pay close attention to the help you receive. I don't expect anything but you actually read and respond to what I write. I'm not everyone, I'm just me. I've helped plenty of noobies before and have been one myself, so I don't expect much. But if you can't figure out how to do or find out what I've asked the you have to at least tell me. I don't know what you know how to do.

---

### Post by newlinux on 2009-07-31
Questions:

1. What CPU/GPU (gave you a way to tell already)
2. what are you playback settings? In mythfrontend you can get to them by going to Utilities/Setup->Setup>TV Settings->Playback (or something like that -I'm not at a myth terminal so I don't know from memory) It's on the second or third page or something of those playback settings.
3. What scans have you done? I recommended a full scan (not high or low) on QAM-64, QAM-256, HRC and IRC. I also recommended you go to [http://www.silicondust.com/hdhomerun/channels_us](http://www.silicondust.com/hdhomerun/channels_us) and see what stations you are supposed to get in your area (hopefully your area has information). Make sure to choose the right provider and look at the right signal type (QAM). I still haven't heard back on this. And not doing this has nothing to do with being a noobie or windows user.
4. Are you currently setup for digital or analog in your rc.local?
5. what does:
```

find / -name '*QAM*' 2>/dev/null

```
return?

---

### Post by NinjaNumberNine on 2009-07-31
I did not build the computer, somebody gave it to me. Here is the lspci output:

```
halstan@Victory:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
        Subsystem: Gateway 2000 Device 7201                                         
        Flags: bus master, fast devsel, latency 0                                   
        Capabilities: <access denied>                                               
        Kernel driver in use: agpgart-intel                                         
        Kernel modules: intel-agp                                                   

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
        Subsystem: Gateway 2000 Device 7201                                                           
        Flags: bus master, fast devsel, latency 0, IRQ 16                                             
        Memory at 73100000 (32-bit, non-prefetchable) [size=512K]                                     
        I/O ports at 20e0 [size=8]                                                                    
        Memory at 60000000 (32-bit, prefetchable) [size=256M]                                         
        Memory at 73180000 (32-bit, non-prefetchable) [size=256K]                                     
        Capabilities: <access denied>                                                                 
        Kernel modules: intelfb                                                                       

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Gateway 2000 Device 7201                                                           
        Flags: bus master, fast devsel, latency 0, IRQ 22                                             
        Memory at 731c0000 (64-bit, non-prefetchable) [size=16K]                                      
        Capabilities: <access denied>                                                                 
        Kernel driver in use: HDA Intel                                                               
        Kernel modules: snd-hda-intel                                                                 

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
        Flags: bus master, fast devsel, latency 0                                     
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0                  
        Capabilities: <access denied>                                                 
        Kernel driver in use: pcieport-driver                                         
        Kernel modules: shpchp                                                        

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
        Flags: bus master, fast devsel, latency 0                                     
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0                  
        Capabilities: <access denied>                                                 
        Kernel driver in use: pcieport-driver                                         
        Kernel modules: shpchp                                                        

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)                                                         
        Flags: bus master, fast devsel, latency 0                                                                                              
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0                                                                           
        Capabilities: <access denied>                                                                                                          
        Kernel driver in use: pcieport-driver                                                                                                  
        Kernel modules: shpchp                                                                                                                 

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
        Subsystem: Gateway 2000 Device 7201                                                   
        Flags: bus master, medium devsel, latency 0, IRQ 23                                   
        I/O ports at 2080 [size=32]                                                           
        Kernel driver in use: uhci_hcd                                                        

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
        Subsystem: Gateway 2000 Device 7201                                                   
        Flags: bus master, medium devsel, latency 0, IRQ 19                                   
        I/O ports at 2060 [size=32]                                                           
        Kernel driver in use: uhci_hcd                                                        

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
        Subsystem: Gateway 2000 Device 7201                                                   
        Flags: bus master, medium devsel, latency 0, IRQ 18                                   
        I/O ports at 2040 [size=32]                                                           
        Kernel driver in use: uhci_hcd                                                        

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
        Subsystem: Gateway 2000 Device 7201                                                   
        Flags: bus master, medium devsel, latency 0, IRQ 16                                   
        I/O ports at 2020 [size=32]                                                           
        Kernel driver in use: uhci_hcd                                                        

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20)
        Subsystem: Gateway 2000 Device 7201                                                              
        Flags: bus master, medium devsel, latency 0, IRQ 23                                              
        Memory at 731c4000 (32-bit, non-prefetchable) [size=1K]                                          
        Capabilities: <access denied>                                                                    
        Kernel driver in use: ehci_hcd                                                                   

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01)
        Flags: bus master, fast devsel, latency 0                           
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=32       
        I/O behind bridge: 00001000-00001fff                                
        Memory behind bridge: 70000000-730fffff                             
        Capabilities: <access denied>                                       

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
        Subsystem: Gateway 2000 Device 7201                                                 
        Flags: bus master, medium devsel, latency 0                                         
        Capabilities: <access denied>                                                       
        Kernel modules: iTCO_wdt, intel-rng                                                 

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Gateway 2000 Device 7201                                                                          
        Flags: bus master, medium devsel, latency 0, IRQ 18                                                          
        I/O ports at 01f0 [size=8]                                                                                   
        I/O ports at 03f4 [size=1]                                                                                   
        I/O ports at 0170 [size=8]                                                                                   
        I/O ports at 0374 [size=1]                                                                                   
        I/O ports at 20b0 [size=16]                                                                                  
        Kernel driver in use: ata_piix                                                                               

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Gateway 2000 Device 7201                                                                                                
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19                                                                         
        I/O ports at 20c8 [size=8]                                                                                                         
        I/O ports at 20ec [size=4]                                                                                                         
        I/O ports at 20c0 [size=8]                                                                                                         
        I/O ports at 20e8 [size=4]                                                                                                         
        I/O ports at 20a0 [size=16]                                                                                                        
        Capabilities: <access denied>                                                                                                      
        Kernel driver in use: ata_piix                                                                                                     

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
        Subsystem: Gateway 2000 Device 7201                                    
        Flags: medium devsel, IRQ 11                                           
        I/O ports at 2000 [size=32]
        Kernel modules: i2c-i801

04:04.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
        Subsystem: KWorld Computer Co. Ltd. Device 08c1
        Flags: bus master, medium devsel, latency 32, IRQ 18
        Memory at 72000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>
        Kernel driver in use: cx8800
        Kernel modules: cx8800

04:04.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
        Subsystem: KWorld Computer Co. Ltd. Device 08c1
        Flags: bus master, medium devsel, latency 32, IRQ 18
        Memory at 71000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>
        Kernel driver in use: cx88_audio
        Kernel modules: cx88-alsa

04:04.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
        Subsystem: KWorld Computer Co. Ltd. Device 08c1
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at 70000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>
        Kernel modules: cx8802

04:05.0 Communication controller: Conexant Systems, Inc. Device 2f40
        Subsystem: Conexant Systems, Inc. Device 2000
        Flags: bus master, fast Back2Back, medium devsel, latency 32, IRQ 10
        Memory at 73000000 (32-bit, non-prefetchable) [size=64K]
        I/O ports at 1040 [size=8]
        Capabilities: <access denied>

04:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)
        Subsystem: Gateway 2000 Device 7201
        Flags: bus master, medium devsel, latency 32, IRQ 20
        Memory at 73010000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 1000 [size=64]
        Capabilities: <access denied>
        Kernel driver in use: e100
        Kernel modules: e100

halstan@Victory:~$

```
and
```
halstan@Victory:~$ cat /proc/cpuinfo | grep -i model
model           : 6
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz
model           : 6
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz
halstan@Victory:~$
```


What do you mean? > ```
mythfrontend -l name_of_log_file
``` Do you want me to type |the directory that I want the log file| in place of |name_of_log_file|?
> But if you can't figure out how to do or find out what I've asked the you have to ** at least tell me**.

Okay, but you might regret saying that... :-D

---

### Post by NinjaNumberNine on 2009-07-31
>  I also recommended you go to [http://www.silicondust.com/hdhomerun/channels_us](http://www.silicondust.com/hdhomerun/channels_us) and see what stations you are supposed to get in your area
I did that but all I get is a jumbled page of channel numbers. Do you want me to post that page?

```
US:71913  Digital Antenna: Hot Springs, AR, 71913 458391  8vsb 545000000 26 3 26.1 KVTHDT   8vsb 207000000 12 1 11.1 KTHVDT 1920x1080i 16:9 13411389 13355685 13145340   8vsb 207000000 12 2 11.2 KTHVDT2 704x480i 4:3 13447543 13429414 13421207   8vsb 581000000 32 3 4.1 KARKDT 1920x1080i 16:9 13421915 13416742 13174260   8vsb 653000000 44 3 42.1 KARZDT 1280x720p 16:9 13457593 13438512 13398197   8vsb 605000000 36 3 36.1 KKAPDT 704x480i 4:3 13352666   8vsb 569000000 30 3 16.1 KLRTDT 1280x720p 16:9 13448680 13261279 13141235   8vsb 569000000 30 4 16.2 KLRTDT2 352x480i 4:3 13465419 13452310 13442366   8vsb 623000000 39 3 38.1 KASNDT 1920x1080i 16:9 13256336 13217846 13049228   8vsb 177000000 7 3 2.1 KETSDT 1280x720p 16:9 13464338 13334364 13178140   8vsb 177000000 7 4 2.2 KETSDT2 704x480i 4:3 13303804 13281934 13280938   8vsb 177000000 7 5 2.3 KETSDT3 704x480i 4:3 13364251 13022871 13006440   8vsb 177000000 7 6 2.4 KETSDT4 640x480i 4:3 13415674 13112812 12986347   8vsb 521000000 22 3 7.1 KATVDT 1280x720p 16:9 13406255 13401988 13367989   8vsb 521000000 22 4 7.2 KATVDT2 704x480i 4:3 13467082 13423125 13392629   8vsb 533000000 24 3 25.1 KVTNDT 704x480i 4:3 13270292 13194307 13149266    Digital Cable: Conway, AR, 72034 461760  qam256 99000000 96 10  KTHVDT2 704x480i 4:3 13310503 13142407   qam256 465000000 64 5  MCGLD 704x480p 4:3 13467291 13346454 13226816   qam256 465000000 64 6  MCRBC 704x480p 4:3 13467908 13467854 13143529   qam256 465000000 64 8  MCREG 704x480p 4:3 13467934 13256759 13133680   qam256 465000000 64 10  ksla 704x480p 4:3 13467786 13467040 13465888   qam256 465000000 64 13  MCTJM 704x480p 4:3 13467822 13467527 13389772   qam256 465000000 64 15  MCRAP 704x480p 4:3 13468445 13302468 13211610   qam256 465000000 64 17  MCRBS 704x480p 4:3 13467898 13418869 13296008   qam256 465000000 64 19  MCMET 704x480p 4:3 13468481 13466159 13384701   qam256 465000000 64 20  MCROK 704x480p 4:3 13468054 13468029 13467826   qam256 465000000 64 21  MCRRK 704x480p 4:3 13468065 13467234 13223198   qam256 465000000 64 23  MCSRK 704x480p 4:3 13467774 13466518 13465864   qam256 465000000 64 25  MCSSC 704x480p 4:3 13467398 13467081 13424362   qam256 465000000 64 27  MCTOT 704x480p 4:3 13467756 13467140 13140355   qam256 465000000 64 29  MCMIX 704x480p 4:3 13468152 13466810 13466596   qam256 465000000 64 30  MCSJZ 704x480p 4:3 13467856 13467540 13466855   qam256 465000000 64 31  MCJAZ 704x480p 4:3 13295107 13235001 13186138   qam256 465000000 64 32  MCCMP 704x480p 4:3 13467110 13466442 13466249   qam256 465000000 64 34  MCLTC 704x480p 4:3 13468288 13467420 13466429   qam256 465000000 64 35  MCSEA 704x480p 4:3 13468012 13467993 13132316   qam256 465000000 64 36  MCTDC 704x480p 4:3 13468096 13382278 13248271   qam256 465000000 64 37  MCTRC 704x480p 4:3 13468026 13466759 13122563   qam256 465000000 64 40  MCSWG 704x480p 4:3 13468259 13375540 13331859   qam256 465000000 64 41  MCPLT 704x480p 4:3 13468269 13467378 13453930   qam256 465000000 64 42  MCTRP 704x480p 4:3 13467930 13467553 13466357   qam256 465000000 64 43  MCPRT 704x480p 4:3 13468469 13466420 13321054   qam256 465000000 64 44  MCURB 704x480p 4:3 13467848 13403084 13193814   qam256 465000000 64 47  MCPHT 704x480p 4:3 13467019 13466875 13392165   qam256 465000000 64 49  MCMEX 704x480p 4:3 13454672 13397135 13263899   qam256 465000000 64 50  MCROM 704x480p 4:3 13468267 13406020 13365983   qam256 489000000 68 3  KARKDT 1920x1080i 16:9 13234953   qam256 555000000 79 28     qam256 627000000 91 1  KTHVDT   qam256 627000000 91 5  KATVDT 1280x720p 16:9 13328228 13169101 13158022   qam256 633000000 92 4   352x480i 4:3 13353790 13246236   qam256 669000000 103 55     qam256 711000000 110 162   1280x720p 16:9 13375996   qam256 717000000 111 166  KAFTDT (AETN HD) 1280x720p 16:9 13459887 13368795 13280412   qam256 795000000 124 1
```

(i don't know why it just shows a tiny bar that you have to move sideways on)

---

### Post by NinjaNumberNine on 2009-07-31
> 1. What CPU/GPU?
model           : 6
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz
> 2. what are you playback settings?
See attachment 1 (I dont know if these are the ones you want)
> 3. What scans have you done?
I have done all the possible combinations. QAM 256 does not give any channels. The only successful one is QAM-64, and like I said, it only gives 3/4 of the available channels.
> 4. Are you currently setup for digital or analog in your rc.local? I changed back to digital.
> 5. what does:```
 find / -name '*QAM*' 2>/dev/null
```
return? ```
halstan@Victory:~$ find / -name '*QAM*' 2>/dev/null
/usr/share/dvb/atsc/us-Cable-IRC-center-frequencies-QAM256
/usr/share/dvb/atsc/us-Cable-EIA-542-IRC-center_frequencies-QAM256
/usr/share/dvb/atsc/us-Cable-Standard-center-frequencies-QAM256
/usr/share/dvb/atsc/us-Cable-HRC-center-frequencies-QAM256
/usr/share/dvb/atsc/us-Cable-EIA-542-HRC-center-frequencies-QAM256
halstan@Victory:~$
```

---

### Post by newlinux on 2009-07-31
Okay. from what you've sent, you have an intel GPU and P4 3.2Ghz. That hardware should be able to play anything from your scans, so that is good. Do you have the intel proprietary driver installed for graphics processing (don't know if that is the default or not in Jaunty.

You live in zip code 71913? Is that near Conway, AZ. The page comes up fine for me (but it is for Conway). It gives me a listing of all the channels you can expect to get in a scan (if you get the same channels as conway).

for the mythfrontend command if you want the log file to be in your homedirectory do:
```

mythfrontend -l ~/mythfrontend.log

```

I recommend you change your playback profile to CPU++ not CPU+ and try again to go through your channels. You may need to install the intel proprietary video driver for good playback.

---

### Post by newlinux on 2009-07-31
I want to try tuning using mplayer again, now that I know you have the file available on your system (if changing to CPU++ doesn't work). This is to hopefully take the playback issue out of the picture. You should already have  dvb-utils installed, so I'll just modify my previous post

```

sudo /etc/init.d/mythtv-backend stop
mkdir ~/.azap
scan /usr/share/dvb/atsc/us-Cable-Standard-center-frequencies-QAM256 > ~/.azap/channels.conf

```
This scan will take a while. verify there are channels in your channels.conf file that you just created.

```

ln -s ~/.azap/channels.conf ~/.mplayer/
mplayer dvb://  -cache 8192

```

MPlayer should start playing the first channel listed in your channels.conf. You should be able to move through your channels.conf list by using h (next channel) and k (previous channel) on your keyboard. When switching between channels, the video window will shut/close, but you will see in the console that you launched MPlayer from that the next channel you are attempting to view is queueing up before the next video window is opened up, displaying the next channel. If one of the channels has something wrong with it, MPlayer will appear to be hung (nothing happening or some error reported in the console output), but just hit ctrl-c to terminate. Alternatively, you can pass the names of the channels themselves (e.g.):
```

mplayer dvb://ABC-DT -cache 8192

```
where ABC-DT is a channel name in your ~/.mplayer/channels.conf file.


When you are done playing with mplayer you can restart mythbackend by doing:

```
 sudo /etc/init.d/mythtv-backend start 
```

---

### Post by newlinux on 2009-07-31
also, how do you know what channels are available via unencrypted QAM?

---

### Post by newlinux on 2009-07-31
> **NinjaNumberNine said:**
> 

```
US:71913  Digital Antenna: Hot Springs, AR, 71913 458391  8vsb 545000000 26 3 26.1 KVTHDT   8vsb 207000000 12 1 11.1 KTHVDT 1920x1080i 16:9 13411389 13355685 13145340   8vsb 207000000 12 2 11.2 KTHVDT2 704x480i 4:3 13447543 13429414 13421207   8vsb 581000000 32 3 4.1 KARKDT 1920x1080i 16:9 13421915 13416742 13174260   8vsb 653000000 44 3 42.1 KARZDT 1280x720p 16:9 13457593 13438512 13398197   8vsb 605000000 36 3 36.1 KKAPDT 704x480i 4:3 13352666   8vsb 569000000 30 3 16.1 KLRTDT 1280x720p 16:9 13448680 13261279 13141235   8vsb 569000000 30 4 16.2 KLRTDT2 352x480i 4:3 13465419 13452310 13442366   8vsb 623000000 39 3 38.1 KASNDT 1920x1080i 16:9 13256336 13217846 13049228   8vsb 177000000 7 3 2.1 KETSDT 1280x720p 16:9 13464338 13334364 13178140   8vsb 177000000 7 4 2.2 KETSDT2 704x480i 4:3 13303804 13281934 13280938   8vsb 177000000 7 5 2.3 KETSDT3 704x480i 4:3 13364251 13022871 13006440   8vsb 177000000 7 6 2.4 KETSDT4 640x480i 4:3 13415674 13112812 12986347   8vsb 521000000 22 3 7.1 KATVDT 1280x720p 16:9 13406255 13401988 13367989   8vsb 521000000 22 4 7.2 KATVDT2 704x480i 4:3 13467082 13423125 13392629   8vsb 533000000 24 3 25.1 KVTNDT 704x480i 4:3 13270292 13194307 13149266    Digital Cable: Conway, AR, 72034 461760  qam256 99000000 96 10  KTHVDT2 704x480i 4:3 13310503 13142407   qam256 465000000 64 5  MCGLD 704x480p 4:3 13467291 13346454 13226816   qam256 465000000 64 6  MCRBC 704x480p 4:3 13467908 13467854 13143529   qam256 465000000 64 8  MCREG 704x480p 4:3 13467934 13256759 13133680   qam256 465000000 64 10  ksla 704x480p 4:3 13467786 13467040 13465888   qam256 465000000 64 13  MCTJM 704x480p 4:3 13467822 13467527 13389772   qam256 465000000 64 15  MCRAP 704x480p 4:3 13468445 13302468 13211610   qam256 465000000 64 17  MCRBS 704x480p 4:3 13467898 13418869 13296008   qam256 465000000 64 19  MCMET 704x480p 4:3 13468481 13466159 13384701   qam256 465000000 64 20  MCROK 704x480p 4:3 13468054 13468029 13467826   qam256 465000000 64 21  MCRRK 704x480p 4:3 13468065 13467234 13223198   qam256 465000000 64 23  MCSRK 704x480p 4:3 13467774 13466518 13465864   qam256 465000000 64 25  MCSSC 704x480p 4:3 13467398 13467081 13424362   qam256 465000000 64 27  MCTOT 704x480p 4:3 13467756 13467140 13140355   qam256 465000000 64 29  MCMIX 704x480p 4:3 13468152 13466810 13466596   qam256 465000000 64 30  MCSJZ 704x480p 4:3 13467856 13467540 13466855   qam256 465000000 64 31  MCJAZ 704x480p 4:3 13295107 13235001 13186138   qam256 465000000 64 32  MCCMP 704x480p 4:3 13467110 13466442 13466249   qam256 465000000 64 34  MCLTC 704x480p 4:3 13468288 13467420 13466429   qam256 465000000 64 35  MCSEA 704x480p 4:3 13468012 13467993 13132316   qam256 465000000 64 36  MCTDC 704x480p 4:3 13468096 13382278 13248271   qam256 465000000 64 37  MCTRC 704x480p 4:3 13468026 13466759 13122563   qam256 465000000 64 40  MCSWG 704x480p 4:3 13468259 13375540 13331859   qam256 465000000 64 41  MCPLT 704x480p 4:3 13468269 13467378 13453930   qam256 465000000 64 42  MCTRP 704x480p 4:3 13467930 13467553 13466357   qam256 465000000 64 43  MCPRT 704x480p 4:3 13468469 13466420 13321054   qam256 465000000 64 44  MCURB 704x480p 4:3 13467848 13403084 13193814   qam256 465000000 64 47  MCPHT 704x480p 4:3 13467019 13466875 13392165   qam256 465000000 64 49  MCMEX 704x480p 4:3 13454672 13397135 13263899   qam256 465000000 64 50  MCROM 704x480p 4:3 13468267 13406020 13365983   qam256 489000000 68 3  KARKDT 1920x1080i 16:9 13234953   qam256 555000000 79 28     qam256 627000000 91 1  KTHVDT   qam256 627000000 91 5  KATVDT 1280x720p 16:9 13328228 13169101 13158022   qam256 633000000 92 4   352x480i 4:3 13353790 13246236   qam256 669000000 103 55     qam256 711000000 110 162   1280x720p 16:9 13375996   qam256 717000000 111 166  KAFTDT (AETN HD) 1280x720p 16:9 13459887 13368795 13280412   qam256 795000000 124 1
```

(i don't know why it just shows a tiny bar that you have to move sideways on)

The ones that have qam256 in front of them are the ones others in that zip code say you can tune with a digital tuner. The ones that have 8VSB in front of them are for OTA antennas.

---

### Post by NinjaNumberNine on 2009-07-31
> You live in zip code 71913? Is that near Conway, AZ?
No. I do live in 71913, but in Hot Springs, Arkansas. I don't know how that got mixed up. Even the report I gave you shows Hot Springs, AR in the first line.

---

### Post by NinjaNumberNine on 2009-07-31
> You may need to install the intel proprietary video driver for good playback.
In proprietary drivers it says "there are no proprietary drivers in use." and there are none available. I guess the intel proprietary is the default.

---

### Post by newlinux on 2009-07-31
> **NinjaNumberNine said:**
> No. I do live in 71913, but in Hot Springs, Arkansas. I don't know how that got mixed up. Even the report I gave you shows Hot Springs, AR in the first line.

Sorry I meant conway, AR - that's the closes place to you it has data for  QAM (not 8vsb - look further in your line and you'll see what I'm talking about - the only part you should car about is the part after Digital cable, since you aren't trying to tune OTA stations).

---

### Post by NinjaNumberNine on 2009-07-31
> also, how do **you know** what channels are available via unencrypted QAM?
I do?

---

### Post by NinjaNumberNine on 2009-07-31
by the way, I am running the mplayer scan right now (I have not tried myth with cpu++ yet)
these are the relatively discouraging results so far:
```
halstan@Victory:~$ scan /usr/share/dvb/atsc/us-Cable-Standard-center-frequencies-QAM256 > ~/.azap/channels.conf                                                                           
scanning /usr/share/dvb/atsc/us-Cable-Standard-center-frequencies-QAM256                     
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'                           
>>> tune to: 57000000:QAM_256                                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 57000000:QAM_256 (tuning failed)                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 63000000:QAM_256                                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 63000000:QAM_256 (tuning failed)                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 69000000:QAM_256                                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 69000000:QAM_256 (tuning failed)                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 79000000:QAM_256                                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 79000000:QAM_256 (tuning failed)                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 85000000:QAM_256                                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 85000000:QAM_256 (tuning failed)                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 177000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 177000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 183000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 183000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 189000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 189000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 195000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 195000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 201000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 201000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 207000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 207000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 213000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 213000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 123012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 123012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 129012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 129012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 135012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 135012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 141000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 141000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 147000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 147000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 153000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 153000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 159000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 159000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 165000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 165000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 171000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 171000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 219000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 219000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 225000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 225000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 231012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 231012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 237012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 237012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 243012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 243012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 249012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 249012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 255012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 255012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 261012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 261012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 267012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 267012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 273012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 273012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 279012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 279012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 285012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 285012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 291012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 291012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 297012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 297012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 303012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 303012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 309012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 309012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 315012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 315012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 321012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 321012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 327012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 327012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 333025000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 333025000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 339012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 339012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 345012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 345012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 351012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 351012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 357012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 357012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 363012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 363012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 369012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 369012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 375012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 375012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 381012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 381012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 387012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 387012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 393012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 393012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 399012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 399012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 405000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 405000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 411000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 411000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 417000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 417000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 423000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 423000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 429000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 429000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 435000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 435000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 441000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 441000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 447000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 447000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 453000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 453000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 459000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 459000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 465000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 465000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 471000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 471000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 477000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 477000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 483000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 483000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 489000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 489000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 495000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 495000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 501000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 501000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 507000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 507000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 513000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 513000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 519000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 519000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 525000000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 525000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 531000000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 531000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 537000000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 537000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 543000000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 543000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 549000000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 549000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 555000000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 555000000:QAM_256 (tuning failed)


```

---

### Post by newlinux on 2009-07-31
> **NinjaNumberNine said:**
> I do?

You said you were only getting 3/4 of your channels in the scan. That implies you know what channels you should be getting
> **NinjaNumberNine said:**
> by the way, I am running the mplayer scan right now (I have not tried myth with cpu++ yet)
these are the relatively discouraging results so far:
```
halstan@Victory:~$ scan /usr/share/dvb/atsc/us-Cable-Standard-center-frequencies-QAM256 > ~/.azap/channels.conf                                                                           
scanning /usr/share/dvb/atsc/us-Cable-Standard-center-frequencies-QAM256                     
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'                           
>>> tune to: 57000000:QAM_256                                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 57000000:QAM_256 (tuning failed)                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 63000000:QAM_256                                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 63000000:QAM_256 (tuning failed)                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 69000000:QAM_256                                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 69000000:QAM_256 (tuning failed)                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 79000000:QAM_256                                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 79000000:QAM_256 (tuning failed)                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 85000000:QAM_256                                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 85000000:QAM_256 (tuning failed)                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 177000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 177000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 183000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 183000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 189000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 189000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 195000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 195000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 201000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 201000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 207000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 207000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 213000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 213000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 123012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 123012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 129012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 129012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 135012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 135012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 141000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 141000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 147000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 147000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 153000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 153000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 159000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 159000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 165000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 165000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 171000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 171000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 219000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 219000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 225000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 225000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 231012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 231012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 237012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 237012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 243012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 243012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 249012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 249012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 255012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 255012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 261012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 261012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 267012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 267012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 273012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 273012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 279012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 279012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 285012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 285012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 291012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 291012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 297012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 297012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 303012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 303012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 309012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 309012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 315012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 315012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 321012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 321012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 327012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 327012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 333025000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 333025000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 339012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 339012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 345012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 345012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 351012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 351012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 357012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 357012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 363012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 363012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 369012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 369012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 375012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 375012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 381012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 381012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 387012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 387012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 393012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 393012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 399012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 399012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 405000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 405000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 411000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 411000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 417000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 417000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 423000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 423000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 429000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 429000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 435000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 435000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 441000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 441000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 447000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 447000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 453000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 453000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 459000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 459000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 465000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 465000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 471000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 471000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 477000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 477000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 483000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 483000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 489000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 489000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 495000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 495000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 501000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 501000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 507000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 507000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 513000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 513000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 519000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 519000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 525000000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 525000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 531000000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 531000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 537000000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 537000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 543000000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 543000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 549000000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 549000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 555000000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 555000000:QAM_256 (tuning failed)


```

believe it or not, that's normal. There are a whole bunch of encrypted channels (PPV, Premium, etc. etc.) that tuning will fail for.

---

### Post by NinjaNumberNine on 2009-07-31
> You said you were only getting 3/4 of your channels in the scan. That implies you know what channels you should be getting
Oh, yeah. I have a normal TV too, and I get channels 2 through about 70

(it was the smallest cable package available)

---

### Post by NinjaNumberNine on 2009-07-31
> believe it or not, that's normal. 

I suppose this is normal too? :mrgreen:
```
halstan@Victory:~$ scan /usr/share/dvb/atsc/us-Cable-Standard-center-frequencies-QAM256 > ~/.azap/channels.conf                                                                           
scanning /usr/share/dvb/atsc/us-Cable-Standard-center-frequencies-QAM256                     
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'                           
>>> tune to: 57000000:QAM_256                                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 57000000:QAM_256 (tuning failed)                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 63000000:QAM_256                                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 63000000:QAM_256 (tuning failed)                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 69000000:QAM_256                                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 69000000:QAM_256 (tuning failed)                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 79000000:QAM_256                                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 79000000:QAM_256 (tuning failed)                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 85000000:QAM_256                                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 85000000:QAM_256 (tuning failed)                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 177000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 177000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 183000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 183000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 189000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 189000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 195000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 195000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 201000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 201000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 207000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 207000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 213000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 213000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 123012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 123012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 129012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 129012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 135012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 135012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 141000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 141000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 147000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 147000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 153000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 153000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 159000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 159000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 165000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 165000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 171000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 171000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 219000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 219000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 225000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 225000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 231012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 231012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 237012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 237012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 243012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 243012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 249012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 249012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 255012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 255012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 261012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 261012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 267012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 267012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 273012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 273012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 279012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 279012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 285012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 285012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 291012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 291012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 297012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 297012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 303012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 303012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 309012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 309012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 315012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 315012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 321012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 321012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 327012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 327012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 333025000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 333025000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 339012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 339012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 345012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 345012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 351012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 351012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 357012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 357012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 363012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 363012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 369012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 369012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 375012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 375012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 381012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 381012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 387012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 387012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 393012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 393012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 399012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 399012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 405000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 405000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 411000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 411000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 417000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 417000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 423000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 423000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 429000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 429000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 435000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 435000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 441000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 441000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 447000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 447000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 453000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 453000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 459000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 459000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 465000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 465000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 471000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 471000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 477000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 477000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 483000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 483000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 489000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 489000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 495000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 495000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 501000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 501000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 507000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 507000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 513000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 513000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 519000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 519000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 525000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 525000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 531000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 531000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 537000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 537000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 543000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 543000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 549000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 549000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 555000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 555000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 561000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 561000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 567000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 567000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 573000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 573000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 579000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 579000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 585000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 585000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 591000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 591000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 597000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 597000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 603000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 603000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 609000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 609000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 615000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 615000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 621000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 621000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 627000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 627000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 633000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 633000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 639000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 639000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 645000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 645000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 93000000:QAM_256                                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 93000000:QAM_256 (tuning failed)                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 99000000:QAM_256                                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 99000000:QAM_256 (tuning failed)                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 105000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 105000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 111025000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 111025000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 117025000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 117025000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 651000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 651000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 657000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 657000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 663000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 663000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 669000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 669000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 675000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 675000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 681000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 681000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 687000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 687000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 693000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 693000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 699000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 699000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 705000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 705000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 711000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 711000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 717000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 717000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 723000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 723000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 729000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 729000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 735000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 735000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 741000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 741000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 747000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 747000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 753000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 753000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 759000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 759000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 765000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 765000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 771000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 771000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 777000000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 777000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 783000000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 783000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 789000000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 789000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 795000000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 795000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 801000000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 801000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.
halstan@Victory:~$

```

---

### Post by newlinux on 2009-07-31
> **NinjaNumberNine said:**
> Oh, yeah. I have a normal TV too, and I get channels 2 through about 70

(it was the smallest cable package available)

Those are probably analog channels (do you use a box, or do you tune them directly with your tV? does your TV have a digital tuner?. It doesn't tell you what's available via digital.

> **NinjaNumberNine said:**
> I suppose this is normal too? :mrgreen:
```
halstan@Victory:~$ scan /usr/share/dvb/atsc/us-Cable-Standard-center-frequencies-QAM256 > ~/.azap/channels.conf                                                                           
scanning /usr/share/dvb/atsc/us-Cable-Standard-center-frequencies-QAM256                     
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'                           
>>> tune to: 57000000:QAM_256                                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 57000000:QAM_256 (tuning failed)                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 63000000:QAM_256                                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 63000000:QAM_256 (tuning failed)                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 69000000:QAM_256                                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 69000000:QAM_256 (tuning failed)                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 79000000:QAM_256                                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 79000000:QAM_256 (tuning failed)                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 85000000:QAM_256                                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 85000000:QAM_256 (tuning failed)                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 177000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 177000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 183000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 183000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 189000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 189000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 195000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 195000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 201000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 201000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 207000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 207000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 213000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 213000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 123012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 123012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 129012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 129012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 135012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 135012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 141000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 141000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 147000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 147000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 153000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 153000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 159000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 159000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 165000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 165000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 171000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 171000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 219000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 219000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 225000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 225000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 231012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 231012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 237012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 237012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 243012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 243012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 249012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 249012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 255012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 255012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 261012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 261012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 267012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 267012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 273012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 273012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 279012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 279012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 285012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 285012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 291012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 291012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 297012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 297012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 303012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 303012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 309012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 309012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 315012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 315012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 321012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 321012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 327012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 327012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 333025000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 333025000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 339012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 339012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 345012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 345012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 351012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 351012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 357012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 357012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 363012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 363012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 369012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 369012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 375012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 375012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 381012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 381012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 387012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 387012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 393012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 393012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 399012500:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 399012500:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 405000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 405000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 411000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 411000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 417000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 417000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 423000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 423000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 429000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 429000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 435000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 435000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 441000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 441000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 447000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 447000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 453000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 453000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 459000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 459000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 465000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 465000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 471000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 471000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 477000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 477000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 483000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 483000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 489000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 489000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 495000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 495000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 501000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 501000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 507000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 507000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 513000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 513000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 519000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 519000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 525000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 525000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 531000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 531000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 537000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 537000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 543000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 543000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 549000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 549000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 555000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 555000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 561000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 561000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 567000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 567000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 573000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 573000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 579000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 579000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 585000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 585000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 591000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 591000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 597000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 597000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 603000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 603000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 609000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 609000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 615000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 615000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 621000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 621000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 627000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 627000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 633000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 633000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 639000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 639000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 645000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 645000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 93000000:QAM_256                                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 93000000:QAM_256 (tuning failed)                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 99000000:QAM_256                                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 99000000:QAM_256 (tuning failed)                                                
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 105000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 105000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 111025000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 111025000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 117025000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 117025000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 651000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 651000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 657000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 657000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 663000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 663000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 669000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 669000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 675000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 675000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 681000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 681000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 687000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 687000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 693000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 693000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 699000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 699000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 705000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 705000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 711000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 711000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 717000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 717000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 723000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 723000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 729000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 729000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 735000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 735000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 741000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 741000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 747000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 747000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 753000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 753000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 759000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 759000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 765000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 765000000:QAM_256 (tuning failed)                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 771000000:QAM_256                                                               
WARNING: >>> tuning failed!!!                                                                
>>> tune to: 771000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 777000000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 777000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 783000000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 783000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 789000000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 789000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 795000000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 795000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 801000000:QAM_256
WARNING: >>> tuning failed!!!
>>> tune to: 801000000:QAM_256 (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.
halstan@Victory:~$

```

Follow the rest of the instructions I gave you. The next step will tell you if it found anything...

---

### Post by NinjaNumberNine on 2009-07-31
> Those are probably analog channels (do you use a box, or do you tune them directly with your tV? does your TV have a digital tuner?. It doesn't tell you what's available via digital.
Um, it's my dads TV. I'm just 14 anyway, I wouldn't know...
As far as I do know, we get nothing but digital signal now.

---

### Post by NinjaNumberNine on 2009-07-31
Here's the rest of the mplayer channel scan steps:
```
halstan@Victory:~$ ln -s ~/.azap/channels.conf ~/.mplayer/
halstan@Victory:~$ mplayer dvb://  -cache 8192
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.20GHz (Family: 15, Model: 6, Stepping: 5)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvb://.
UNKNOWN TUNER TYPE
DVB CONFIGURATION IS EMPTY, exit
Failed to open dvb://.


Exiting... (End of file)
halstan@Victory:~$








```

---

### Post by newlinux on 2009-07-31
The next step was to check and see if there was anything in the channels.conf file. Looks like there's not, so that scan didn't pick up anything. 

Just to be sure, what does:
```

ls -l ~/.azap

```
and
```

ls -l ~/.mplayer

```
return?


You might want to try some of the other QAM scan files, or go back and try mythtv (with CPU++). It seems you don't have a QAM-64 scan file based on what you sent me earlier. 

Is the cable plugged directly into the tV or to a cable box? Doesn't really matter that much for what we are trying to do, so you can ignore that question.

Can you do:

```

 cat /var/log/Xorg.0.log | grep -i driver

```
I want to see which driver you are using for video

---

### Post by NinjaNumberNine on 2009-07-31
> Just to be sure, what does:
 ```
ls -l ~/.azap
```
```
halstan@Victory:~$ ls -l ~/.azap
total 0
-rw-r--r-- 1 halstan halstan 0 2009-07-31 15:50 channels.conf
halstan@Victory:~$

```
> ls -l ~/.mplayer
```
halstan@Victory:~$ ls -l ~/.mplayer
total 12
lrwxrwxrwx 1 halstan halstan   33 2009-07-31 15:58 channels.conf -> /home/halstan/.azap/channels.conf
-rw-r--r-- 1 halstan halstan   44 2009-07-31 12:11 config
-rw-r--r-- 1 halstan halstan 2598 2009-07-31 14:59 gui.conf
-rw-r--r-- 1 halstan halstan    0 2009-07-31 14:59 gui.history
-rw-r--r-- 1 halstan halstan  104 2009-07-31 14:59 gui.pl
-rw-r--r-- 1 halstan halstan    0 2009-07-31 14:59 gui.url
halstan@Victory:~$

```

> Is the cable plugged directly into the tV or to a cable box? Doesn't really matter that much for what we are trying to do, so you can ignore that question.

Yes, its plugged straight to the TV. (I guess that means it has a built-in tuner?)

> Can you do:
```
 cat /var/log/Xorg.0.log | grep -i driver
```

```
halstan@Victory:~$ cat /var/log/Xorg.0.log | grep -i driver
        X.Org Video Driver: 5.0
        X.Org XInput driver : 4.0
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by thedrivers
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        ABI class: X.Org Video Driver, version 5.0
        ABI class: X.Org Video Driver, version 5.0
(II) [drm] loaded kernel module for "i915" driver.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) EXA(0): Driver registered support for the following operations:
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 4.0
halstan@Victory:~$

```

---

### Post by NinjaNumberNine on 2009-07-31
Oh, and almost forgot. When I ran ```
xawtv -noxv & sox -w -r 48000 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp

``` it brought up xawTV and started playing clear TV! 
Then, as usual, I had to go click on the "contrast" button and I managed to get it all the way to the right- now I don't know how to get it back so all I see is colorful static..:cry:

---

### Post by newlinux on 2009-07-31
> **NinjaNumberNine said:**
> Oh, and almost forgot. When I ran ```
xawtv -noxv & sox -w -r 48000 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp

``` it brought up xawTV and started playing clear TV! 
Then, as usual, I had to go click on the "contrast" button and I managed to get it all the way to the right- now I don't know how to get it back so all I see is colorful static..:cry:

Is that when you had the card configured for analog? If you have it configured for digital now, it might not work. Not sure if xaw supports digital (maybe it does now, I haven't used that program in a while). I fit does work for digital, that confirms your problem in myth is playback related. On the flip side, if your card is currently configured for analog (or not properly configured for digital) that would explain why the scan you performed earlier failed to lock any channels.
what does 
```
lsmod | grep cx88
```
 return?

Yeah, your channels.conf file is empty, so it didn't get any locks in the scan. 
Yeah if it straight plugged in to the TV it has a tuner. Whether or not it is digital capable depends on the model.

Looks like you have the i915 intel driver, which should be okay.

have you tried the CPU++ playback profile and gone through the channels in mythtv? If it doesn't work, then post the log from when it errored out. 

But first we need to make sure you are in proper digital mode.

---

### Post by NinjaNumberNine on 2009-07-31
halstan@Victory:~$ lsmod | grep cx88
cx88_dvb               29444  1
cx88_vp3054_i2c        10624  1 cx88_dvb
cx88_alsa              18824  2
snd_pcm                82948  3 snd_hda_intel,cx88_alsa,snd_pcm_oss
cx8800                 38148  0
cx8802                 24068  1 cx88_dvb
cx88xx                 79272  4 cx88_dvb,cx88_alsa,cx8800,cx8802
ir_common              52228  1 cx88xx
i2c_algo_bit           14084  2 cx88_vp3054_i2c,cx88xx
videobuf_dvb           15236  3 cx88_dvb,cx8802,cx88xx
dvb_core               92032  2 cx88_dvb,videobuf_dvb
videodev               41600  3 tuner,cx8800,cx88xx
compat_ioctl32          9344  1 cx8800
v4l2_common            20992  2 tuner,cx8800
tveeprom               20100  1 cx88xx
videobuf_dma_sg        20484  5 cx88_dvb,cx88_alsa,cx8800,cx8802,cx88xx
btcx_risc              13064  4 cx88_alsa,cx8800,cx8802,cx88xx
videobuf_core          26500  5 cx8800,cx8802,cx88xx,videobuf_dvb,videobuf_dma_sg
snd                    62628  22 snd_hda_intel,cx88_alsa,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
halstan@Victory:~$

---

### Post by NinjaNumberNine on 2009-07-31
That is the strange thing. I don't think xawtv supports digital either and my rc.local looks like this:
```
#!/bin/sh -e
#
# rc.local
#
# Th#!/bin/sh -e
#
# rc.local
  mv /etc/modprobe.d/blacklist-misc /root
  modprobe cx88_dvb
  modprobe cx88_alsa
  cp /root/blacklist-misc /etc/modprobe.d mv /etc/modprobe.d/blacklist-misc /root
# # Make sure that the script will "exit 0" on success or any other
# value on error.
## In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0


```
Last time I tried Digital, (before I set up analog) the  |modprobe cx88_dvb 
&  modprobe cx88_alsa| had hyphens instead of underscores.

Is my rc.local as it should be?

---

### Post by NinjaNumberNine on 2009-07-31
Can you give me a graphical step by step (i.e. tell me which button to press) to setup digital in Myth? All I have done so far is add the new capture card as DVB-DTV. The next step, Creating a video source, is what confuses me. To get the listings, I have to have an account with SchedulesDirect, which costs money.  What should I do now? I am in the "Create new video source" screen.

---

### Post by newlinux on 2009-07-31
> **NinjaNumberNine said:**
> That is the strange thing. I don't think xawtv supports digital either and my rc.local looks like this:
```
#!/bin/sh -e
#
# rc.local
#
# Th#!/bin/sh -e
#
# rc.local
  mv /etc/modprobe.d/blacklist-misc /root
  modprobe cx88_dvb
  modprobe cx88_alsa
  cp /root/blacklist-misc /etc/modprobe.d mv /etc/modprobe.d/blacklist-misc /root
# # Make sure that the script will "exit 0" on success or any other
# value on error.
## In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0


```
Last time I tried Digital, (before I set up analog) the  |modprobe cx88_dvb 
&  modprobe cx88_alsa| had hyphens instead of underscores.

Is my rc.local as it should be?

No. Take out the cx88_alsa. see the second page of this thread or the link. Then reboot. make sure your blacklist-misc file is correct to. This is why you shouldn't switch back and forth - you are throwing too many variables in there at once to troubleshoot effectively. Just my opinion....

and this line
 cp /root/blacklist-misc /etc/modprobe.d mv /etc/modprobe.d/blacklist-misc /root

should be
 cp /root/blacklist-misc /etc/modprobe.d

---

### Post by newlinux on 2009-07-31
> **NinjaNumberNine said:**
> Can you give me a graphical step by step (i.e. tell me which button to press) to setup digital in Myth? All I have done so far is add the new capture card as DVB-DTV. The next step, Creating a video source, is what confuses me. To get the listings, I have to have an account with SchedulesDirect, which costs money.  What should I do now? I am in the "Create new video source" screen.

There are already guides out there you can use.

[http://www.mythtv.org/wiki/User_Manual:MythTV_structure](http://www.mythtv.org/wiki/User_Manual:MythTV_structure) is the official documentation. There are other guides out there too.

None of this will work now until you have your card set up right for digital. Once it is, leave it alone if you want to play with digital... I'd try the scan again with mplayer once you have it set up correctly. make sure mythbackend isn't running when you do it.

---

### Post by NinjaNumberNine on 2009-07-31
> Once you have your card set up right for digital
> Once it is set up
> once you have it set up correctly
Ok, tell me what to post here. I don't know if I am set up right or not. I would assume so, though. the rc.local file is like you specified, exept I was not sure what you meant "Take out the cx88_alsa." Do you mean just take out the line and don't replace it?

---

### Post by NinjaNumberNine on 2009-07-31
> There are already guides out there you can use.
 
 [http://www.mythtv.org/wiki/User_Manual:MythTV_structure](http://www.mythtv.org/wiki/User_Manual:MythTV_structure) is the official documentation. There are other guides out there too.
 
I already read that, but I still come up with the same thing: Do I have to have a SchedulesDirect account to have digital TV?

---

### Post by NinjaNumberNine on 2009-07-31
> I'd try the scan again with mplayer once you have it set up correctly.
I want to do that, but there are no channels in the "channels.conf" file after I scan.

---

### Post by newlinux on 2009-07-31
> **NinjaNumberNine said:**
> Ok, tell me what to post here. I don't know if I am set up right or not. I would assume so, though. the rc.local file is like you specified, exept I was not sure what you meant "Take out the cx88_alsa." Do you mean just take out the line and don't replace it?

Yes. As I said before (again you aren't paying attention to what I've written) go back to the second page of this thread. I tell you there what the files should look like. After you have rebooted post the results of ```
 lsmod | grep cx88 
``` and the contents of the files I mentioned in the post where I told you these files were wrong.
> **NinjaNumberNine said:**
> I already read that, but I still come up with the same thing: Do I have to have a SchedulesDirect account to have digital TV?
No. You've already scanned and tuned stations (although they had no video) before without one, so you've already done it without schedules direct. Why do you think you need it now? It's only for guide information.

> **NinjaNumberNine said:**
> I want to do that, but there are no channels in the "channels.conf" file after I scan.
Yes, but one of the reasons it may not have worked is that you didn't properly change your files back to make the card work for digital. So when you do, you need to run through all those steps again, and in addition try the other QAM scan files that came up from the find command I had you run to generate them.

Good luck.

---

### Post by NinjaNumberNine on 2009-07-31
> (again you aren't paying attention to what I've written) go back to the second page of this thread.
Do you have your browser set on ten results per page? I ran a search on page two and there was nothing there named rc.local.

-Oh, well it does not matter. I will remove the alsa line and reboot...

---

### Post by newlinux on 2009-07-31
> **NinjaNumberNine said:**
> Do you have your browser set on ten results per page? I ran a search on page two and there was nothing there named rc.local.

-Oh, well it does not matter. I will remove the alsa line and reboot...

20 posts per page. It does matter to me. Point being, your question has been answered in this thread (more than once).  Your question has also been answered in the link you posted in this thread (as I mentioned before too). Yet, you ask again... Try searching the thread. I also told you to make sure the other file was right before rebooting...

---

### Post by NinjaNumberNine on 2009-07-31
> It's only for guide information.
Oh, thats good. I thought maybe that was a service that gave a list of all the channels and their frequencies. Last time I used EPG, which requires no account.

---

### Post by NinjaNumberNine on 2009-07-31
> 20 posts per page. It does matter to me. Point being, your question has been answered in this thread (more than once). Your question has also been answered in the link you posted in this thread (as I mentioned before too). Yet, you ask again... Try searching the thread. I also told you to make sure the other file was right before rebooting...I am awed by your persistence! OK, I was wrong. What do you want?

My rc.local:
 ```
#!/bin/sh -e
#
# rc.local
  mv /etc/modprobe.d/blacklist-misc /root
  modprobe cx88_dvb
  cp /root/blacklist-misc /etc/modprobe.d
# # Make sure that the script will "exit 0" on success or any other
# value on error.
## In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0


```My blacklist-misc:


```

blacklist cx8800
blacklist cx8802
blacklist cx88_alsa
blacklist cx88_dvb

```lsmod on reboot:
```
halstan@Victory:~$  lsmod | grep cx88
cx88_dvb               29444  0
cx88_vp3054_i2c        10624  1 cx88_dvb
cx8802                 24068  1 cx88_dvb
cx88xx                 79272  2 cx88_dvb,cx8802
videodev               41600  2 tuner,cx88xx
ir_common              52228  1 cx88xx
i2c_algo_bit           14084  2 cx88_vp3054_i2c,cx88xx
tveeprom               20100  1 cx88xx
btcx_risc              13064  2 cx8802,cx88xx
videobuf_dvb           15236  3 cx88_dvb,cx8802,cx88xx
videobuf_dma_sg        20484  3 cx88_dvb,cx8802,cx88xx
videobuf_core          26500  4 cx8802,cx88xx,videobuf_dvb,videobuf_dma_sg
dvb_core               92032  2 cx88_dvb,videobuf_dvb
halstan@Victory:~$
```

---

### Post by NinjaNumberNine on 2009-08-01
Is there a way to run a 64-QAM channel scan for mplayer?
In Myth I have it set up so that it finds all my channels, everything is setup for digital, etc...

...[SIZE=2]But[/SIZE] with all that in mythfrontend it just flashes the screen when I hit "Watch TV." :D

---

### Post by buddy_t on 2009-10-09
**Pinnacle PCTV HD pci card(800i**I, no sound in any App.  Works in TVTIME with the command in terminal  arecord -D hw:1,0 -f dat | aplay . However sound does not match video and if you close terminal sound turns off.  Since this easy command turns on sound is there an easy fix to make it work without running the command and video and sound to match? I am a newbie to Ubuntu. Thank you

---

### Post by NinjaNumberNine on 2009-10-10
-Kind of wondering why you posted that here? But OK, I'll try to help. :)

Could you tell me if you're trying to use the digital or analog side please?

---

