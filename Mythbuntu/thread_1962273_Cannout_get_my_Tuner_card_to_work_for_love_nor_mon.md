---
title: "Cannout get my Tuner card to work for love nor money"
date: 2012-04-20
forum: Mythbuntu
---

### Post by Weidbrewer on 2012-04-20
Every few years and versions of Ubuntu/Myth, I decide that I've just been too darn happy day-to-day and decide to try and actually use the two TV tuners I have.  My wife is going to be on the news tonight, and I really wanted to record it in a format I can save (unlike my Comcast DVR.)  So, once again, I decided that I would punish myself and jump into this again.

I'm trying to set up my Hauppauge 1600.  When I first tried it, no channels were detected, no matter what frequency I tried.  I then tried the installation and firmware [instructions here]("http://www.mythtv.org/wiki/Hauppauge_HVR-1600#Installation_Guide").  Now, not only do I still not have a working card, but now it's not even being detected by Myth at all!!!

The step that says:

```
    Verify that everything was installed correctly. Expect the following (probably more): 

 dmesg | grep cx18
 [    8.651532] cx18:  Start initialization, version 1.0.1
 [    8.651572] cx18-0: Initializing card #0
 [    8.651575] cx18-0: Autodetected Hauppauge card
 [   23.555603] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
 [   24.227119] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
 [   25.651060] cx18-0: loaded v4l-cx23418-dig.fw firmware (16382 bytes)

```

does not yield anything at all:

```
me@computer:~$ dmesg | grep cx18
me@computer:~$ 
```


Can anyone help at all?  I realize that I won't be able to get the recording I want to tonight, but after 4-5 years of using Myth, I'd like to use the PVR functionality of it!

Myth version:  0.25
Ubuntu: 10.04
Both fully patched.

\For sanity, this is the last attempt.  After this, if it doesn't work, I sell my cards so that I'm never tempted again. :)

---

### Post by BicyclerBoy on 2012-04-20
Does it show up detected as hardware?
lspci

Driver load errors?
dmesg | grep malloc

Did you see there are multiple types..
kernel in 10.04.4 may not have support for the later ones because it is at 2.26.32
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600)

Check your tuner PCI ids ..should they be supported (according to LinuxTV) ?

Backport kernel is an option..

---

### Post by Weidbrewer on 2012-04-21
Okay, lots of stuff to answer.  Let's see how well I score:

Yes, it is detecting the cards (the Hauppauge and a PCHDTV 5500):
```
03:07.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
03:07.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
03:07.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
03:07.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
03:08.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder

```

Nothing on the driver errors:

```
me@computer:~$ dmesg | grep malloc
me@computer:~$
```

The card version I have is the 74541 (Model 1183) (Jeez...had this thing for three years, according to my invoice...I've used it for maybe 10 hours in that time...)

It *should* be compatible, as it worked under 8.10-10.04 before.  (Had it semi working on a previous install until I got some unpleasantness and never set it up again the next time I did a fresh install.)  It was also recognized by Myth earlier this evening before I monkeyed with it to get it to detect some channels.  (Also, yes, I double-checked to make sure the cable was connected to it... :) )

Thanks for taking the time.  Hopefully I was able to provide the info you were looking for.

---

### Post by BicyclerBoy on 2012-04-21
Scroll thru' your dmesg output for anything about v4l & firmware..

Do you have the non-free firmware package installed ?
Are you using 64bit ?

After a cold restart, the dmesg output should indicate the tuner card is found in cold start & then firmware is loaded..

---

### Post by klc5555 on 2012-04-21
Your older 1183 model 1600 card should work perfectly for QAM, even on 10.04's ancient kernel and old cx18 module.

Your blank dmesg output for the cx18 indicates that the module may not have been loaded. You can check the output of lsmod just to be sure that it isn't loaded.

Assuming that it isn't, you might try loading the module by hand: 
```

sudo modprobe cx18

```

And see whether this gives you any errors. If not, you can check whether dmesg or lsmod output indicate the module has loaded. Dmesg should also indicate the firware has loaded, but this card uses the firmware only for analog, not for QAM

If the cx18 module appears to have loaded, then likely mythtv's backend setup will now be able to detect the 1600's QAM tuner as some sort of Samsung make, and we can proceed from there.

As an aside, there is a frequent issue with the cx18 not being able to load when the proprietary NVidia module has already loaded (and vice/versa) because of insufficient vmalloc space set up. If this turns out to have afflicted you, them vmalloc will likely need to be icreased to 128m or even 256m to get both to load simultaneously. A frequent but easily fixed problem with these drivers.

---

