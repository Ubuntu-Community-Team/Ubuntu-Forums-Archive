---
title: "Capture card not recognized after 9.10 upgrade"
date: 2009-11-06
forum: Mythbuntu
---

### Post by sawbuck on 2009-11-06
Hope someone can help.  I'm not linux fluent but have been getting to know MythTV and more recently a little of Ubuntu but I still get into plenty of confusing spots.

I had been using 9.04 for several weeks with good success and just today upgraded to 9.10.  Now I'm in trouble.  My Hauppage HVR 1600 capture card whcih was easily recognized and usable as a:

DVB DTV Capture card (V3.x)  (it said it was a SamsungS5H1409 QAM.Subtype ATSC)

I was able to get full usage after learning the CX18 quirks with Nvidia, XVmc etc bit now in 9.10 the card is not recognised as anything.

I read suggestions in a posting here titled " hvr-1600 difficulties " indicating the following would set up the right drivers:

   sudo apt-get install mercurial
   hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
   cd v4l-dvb
   sudo make
   sudo make install

But I had no such luck.  No options are recognized.  When I run dmesg | grep cx18, I get this:

[   11.302881] cx18:  Start initialization, version 1.0.1
[   11.302953] cx18-0: Initializing card #0
[   11.302958] cx18-0: Autodetected Hauppauge card
[   11.303547] cx18 0000:02:0d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   11.303561] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   11.307543] cx18-0: cx23418 revision 01010000 (B)
[   11.546817] cx18-0: Autodetected Hauppauge HVR-1600
[   [COLOR=Red]11.546820] cx18-0: VBI is not yet supported[/COLOR]
[   12.364859] tuner 1-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   12.364927] cs5345 0-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   12.474545] cx18-0: Disabled encoder IDX device
[   12.474724] cx18-0: Registered device video0 for encoder MPEG (2 MB)
[   12.474729] DVB: registering new adapter (cx18)
[   12.975194] cx18-0: DVB Frontend registered
[   12.975312] cx18-0: Registered device video32 for encoder YUV (2 MB)
[   12.975420] cx18-0: Registered device video24 for encoder PCM audio (1 MB)
[   12.975425] cx18-0: Initialized card #0: Hauppauge HVR-1600
[   13.002586] cx18:  End initialization
[   13.076470] cx18 0000:02:0d.0: firmware: requesting v4l-cx23418-apu.fw
[   13.695616] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   14.192052] cx18 0000:02:0d.0: firmware: requesting v4l-cx23418-cpu.fw
[   14.387515] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   14.393833] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   14.588120] cx18 0000:02:0d.0: firmware: requesting v4l-cx23418-apu.fw
[   15.200083] cx18 0000:02:0d.0: firmware: requesting v4l-cx23418-cpu.fw
[   15.530041] cx18 0000:02:0d.0: firmware: requesting v4l-cx23418-dig.fw
[   15.924948] cx18-0: loaded v4l-cx23418-dig.fw firmware (16382 bytes)

I assume hte driver install effort didn't work based on the red highlighted text above.

Where did I go wrong?  Please help....

---

### Post by sawbuck on 2009-11-06
Update:

I looked at the text that scrolled by after "make" command completed following the commands to build the v4l drivers:   hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
                cd v4l-dvb

   and this is in the scrolled text after the make command:
                 File not found: /lib/modules/2.6.28-11-generic/build/.config at ./scripts/make_kconfig.pl line 32, 
                 <IN> line 4.
                 make[1]: *** No rule to make target `.myconfig', needed by `config-compat.h'.  Stop.
                 make[1]: Leaving directory `/home/frank/v4l-dvb/v4l'
                 make: *** [all] Error 2

I assume that is a huge problem and susequent efforts to install were meaningless.

Anyway, I reinstalled Mythtv using the Synaptic Package Manager and it came back with a "successful" message.  

No matter, I still have no card recognition.

Am I faced with a totally wipeout and clean install?

---

### Post by sawbuck on 2009-11-08
Being a relative forum dummy I don't know how tio put a "solved" tag on this but since I might be the only one with an interest in this thread it probably goes up as "who cares?" anyway,  

However,  I was unsuccessful in finding ANY way of adding the capture card that worked previously so I downloaded the 9.10 Mythbuntu img , burned it to CD, and did a fresh install - 3 times.  I couldn't get a clean first boot the first couple of times.  

(I have to admit I still haven't read all the release notes for 9,10.)

Found out - after a lot of head-banging - the menu.lst file I modified in previous versions isn't used.  Since I have an EVGA 6200 (NVIDIA) graphics card combined with Hauppauge HVR 1600 capture card, on 9.04 and prior installations, I had to alter the menu.lst fie adding "vmalloc=256m" to use the reccommended NVIDIA drivers. 

I selected the restricted driver option during 9.10 setup which didn't allow the it to complete the first boot.  The "vmalloc=" can be added it to a similar appearing line in /boot/grub/grub.cfg.  After that, first boot completes and doesn't continue thrashing at startup.

Still have't checked all the features previousl uysed but Live TV, recording, and viewing of both seems OK.

---

### Post by xinix on 2009-11-08
> **sawbuck said:**
> Update:
                 File not found: /lib/modules/2.6.28-11-generic/build/.config at ./scripts/make_kconfig.pl line 32, 

Were you using the headers or are you trying to use the kernel source?  Also could link to the post with the instruction you are following.  The first line in your error makes me think that you don't have the headers or kernel source properly installed.

If you read that line, you will see that it is being directed to the **2.6.28-11** kernel source or headers.  The kernel version in Karmic is **2.6.31-xx**.   Did you try completely removing the folder with the driver source and try again?  Another possibility is that you were using the same driver source you used before doing the upgrade.  This can lead to having build configs that point to old headers.

I was in the middle of responding when you posted your 'who cares' response.  By the looks of it you got the driver working on a fresh install.  Sometimes it takes a day or two to get a response on the forum.

---

### Post by sawbuck on 2009-11-10
> **xinix said:**
> Were you using the headers or are you trying to use the kernel source?  Also could link to the post with the instruction you are following.  The first line in your error makes me think that you don't have the headers or kernel source properly installed.

If you read that line, you will see that it is being directed to the **2.6.28-11** kernel source or headers.  The kernel version in Karmic is **2.6.31-xx**.   Did you try completely removing the folder with the driver source and try again?  Another possibility is that you were using the same driver source you used before doing the upgrade.  This can lead to having build configs that point to old headers.

I was in the middle of responding when you posted your 'who cares' response.  By the looks of it you got the driver working on a fresh install.  Sometimes it takes a day or two to get a response on the forum.

xinix,

Thanks for suggestions.  Wasn't sure where to go or what to try other than a fresh install.  However, I DID keep the old install available and bootable so do go back to it as time permits to see if I can learn anything and perhaps (wishful thinking here) find a solution.   So your input was appreciated.  I am using Firefox from the "upgraded" boot at the moment and am pulling info from this boot.

The instructions I followed - and referenced results earlier - were from the "Installation -> Drivers" section of this pointer:

[http://www.mythtv.org/wiki/Hauppauge_HVR-1600#Firmware](http://www.mythtv.org/wiki/Hauppauge_HVR-1600#Firmware)

I had located it from a responder to one of the threads in this forum relating to HVR 1600 (as my card is).  That apparently was intended to get up the analog side for use on the card.  

Once I had the fresh install going on another disk, and since my interest was OTA ATSC (US broadcast is my source )continued search found reference to this:

[http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers#Retrieving_the_Latest_V4L-DVB_Source_Code](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers#Retrieving_the_Latest_V4L-DVB_Source_Code)

which (to my limited understanding) looks similar but does say it sets up ATSC.

Anyway, I tried that and after following the steps exactly I ran make and get this result:

make -C /v4l-dvb/v4l 
make[1]: Entering directory `/v4l-dvb/v4l'
Updating/Creating .config
Preparing to compile for kernel version 2.6.28
[COLOR=Red]File not found: /lib/modules/2.6.28-11-generic/build/.config at ./scripts/make_kconfig.pl line 32, <IN> line 4.
make[1]: *** No rule to make target `.myconfig', needed by `config-compat.h'.  Stop.
[/COLOR]make[1]: Leaving directory `/v4l-dvb/v4l'
make: *** [all] Error 2

Once again, it is looking for 2,6,28-11 kernel.

When I look in my /lib/modules   directory, I find these folders:

2.6.28-11-generic  2.6.31-14-generic

My grub boot loader has the option of booting from either but 28-11 boots into the "upgraded" 9.04 -> 9.10 disk and the 31-14 boots to the "fresh" 9.10 disk.  They are installed on separate disks, configured as primary and secondary in the PC bios.

Only 2.6.31-14 directory has a "buil;d" directory so it is easy for me to see why the error appears.  Since I upgraded 9.04, which had a kernel 2.6.28-11, to 9.10 (which has the 2.6,31-14 kernel) is there anyway of using the driver build process to enable the HVR 1600 capture card?   If the answer is no, I'll be happy to forget this and go to the fresh installed version.  If there is a way, I'd like to learn it in case the experience is need ed in the future,

Again, if your read this, thanks for the interest.  Any suggestions on how to get the drivers complled or downloaded or any other way for this installation to recognize the capture card?

---

### Post by xinix on 2009-11-11
It sounds like the "upgraded 9.04" didn't completely upgrade things.  It should appear in grub with the new kernel number.  I think the first hurdle in this case is figuring out what kernel you are actually booting when you choose the upgraded version.  Boot into the upgraded, not the clean install, version and type this command:
```
uname -r
```
It will tell you what kernel is loaded.  It should be the current Karmic kernel.  If it isn't then we need to get that bit working before we can try to get the driver installed.

---

### Post by sawbuck on 2009-12-08
> **xinix said:**
> It sounds like the "upgraded 9.04" didn't completely upgrade things.  It should appear in grub with the new kernel number.  I think the first hurdle in this case is figuring out what kernel you are actually booting when you choose the upgraded version.  Boot into the upgraded, not the clean install, version and type this command:
```
uname -r
```It will tell you what kernel is loaded.  It should be the current Karmic kernel.  If it isn't then we need to get that bit working before we can try to get the driver installed.

xinix,

Sad to say, somewhere in my fumbling back then I'd screwed up that installation on the 2nd disk and ended up having to format the whole thing to ext4.  I do appreciate your help trying to bail me out.  I really need to be able to spend more time with this box to begin to understand ubuntu/mythbuntu a LOT better.  With snow flying here in New England and bitter cold on its way I hope to be able to cozy up to the system and get finally get acquainted.  Since the original problem, I've had a few glitches of other nature to research and seek help on and didn't get back to this thread to respond until today.  However, it ain't likely I get more than a few hours a week to address each problem so it will be a SLOW process......

---

