---
title: "Sound card problems - ATI Technologies Inc IXP SB400 AC'97 Audio Controller"
date: 2007-02-19
forum: Multimedia &amp; Video
---

### Post by vinay.v on 2007-02-19
Hi,

   I have a Foxconn motherboard with inbuilt sound card. The "lspci -v" command shows my sound card to be "ATI Technologies Inc IXP SB400 AC'97 Audio Controller".
Although this sound card is listed as supported in ALSA homepage, I haven't been able to make it work on any linux distribution (not just Ubuntu).

Ubuntu recognises my sound card & loads the proper "snd-atiixp" driver for it. 
But, "aplay -l" says no soundcards found. "lspci -v" shows my soundcard. "lsmod" indicates that snd-atiixp driver is loaded. Even if I do a "modprobe snd-atiixp", I still don't get the sound. 

Most of the posts in different online forums for my sound card suggest that tuning the alsamixer (turning off external amplifier to be exact) solves issues for most people. But when I run the "alsamixer" command, I get an error saying "alsamixer: function snd_ctl_open failed for default: No such device". I cannot open any mixer for that matter alsamixer, amixer, kmix, etc. If I try to do anything related to sound, it says soundcard not found or not configured.

I did download the latest alsa drivers from the alsa website & compiled them as per instructions for my specific sound card. But the problem remains the same. One thing I noted was that almost all linux distributions were able to recognise my sound card properly & load the correct snd-atiixp driver, but there is always no sound. I can't open the mixer in any of them (Same error as above).

When Ubuntu booted up, one strange thing I noticed was that I got an error stating - 
"AC'97 2 access is not valid [0xffffffff], removing mixer."
I think this is the reason why sound doesn't work even if the proper (snd-atiixp) driver is loaded.

Another error I notice during booting up is "PCI: unable to allocate resource area 3" or something like that. I don't know whether that has something to do with sound.

My computer configuration - Pentium D 2.8 GHz Dualcore processor, FoxConn motherboard with built in ATI IXP SB400 AC'97 sound card, built in LAN port, etc., 512 MB DDR2 RAM, 256MB nVidia GeForce 6600 graphics card.

Just FYI, I bought this computer a week ago. I didn't want to install windoze on it. But I did install it (for a couple of minutes only) & tested that sound works properly on windoze after installing the drivers from the motherboard CD.

Any help to get the sound card working on linux would be appreciated. 

Thanks in advance,
Vinay V

---

### Post by ephraim on 2007-02-22
Hey,

I have the same sound card and had problems for the last couple months. Tried just about everything. However, only two things have solved it for me, but I'm still a newbie and don't know much so this may be absolutely worthless to you.

One of my problems was that the snd-atiixp-modem was loading with the snd-atiixp and crowding it out. I don't understand the nitty gritty of this totally, but it appears that the modem and sound card are on the same chip and they don't co-exist very well with Alsa. So, my solution was to blacklist the modem so that it simply doesn't enter into the mix. I don't use the modem anyway.

To do this, open up terminal.

sudo gedit /etc/modprobe.d/blacklist

at bottom of list, type...

#get rid of snd-atiixp-modem
snd-atiixp-modem

then save.


However, I also had to do the following little tweak, excerpted from the following webpage....

[http://www.beginningubuntu.com/dapper_tips.html#Sound_on_my_weird_notebook](http://www.beginningubuntu.com/dapper_tips.html#Sound_on_my_weird_notebook)

"My notebook is possibly the most Linux-incompatible machine that's ever been made. Here's a tip: Don't buy an Asus A6R. It's one of the worst notebooks I've ever owned. 
      Sound didn't work straight off. The notebook has an IXP SB400 AC'97 Audio Controller, according to Ubuntu's Device Manager. If you've got the same sound card, and want to get it working, you need to do two things. 
      (1) Double-click the speaker icon in Ubuntu's system tray and click Edit -> Preferences in the Volume Control window that appears. In the list, look for the Master Surround entry, and put a checkbox in it. Then look for External Amplifier and put a check in it. Click the Close button then click the Switches tab in the Volume Control window. Remove the check against External Amplifier. 
      (2) Then click the Playback tab and click the Speaker icon beneath the Master Surround slider, so that it's no longer muted. Then adjust the slider. Playback some audio and you should find everything now works. Basically, the Master Surround slider is now your volume slider. Weird, but true. To make the system tray applet use the Master Surround to control the volume, right-click the system tray speaker icon, select Preferences, and select Master Surround in the list. "


And so now I have sound. I hope it helps you as well.

Best wishes,
Ephraim:)

---

### Post by vinay.v on 2007-02-23
First of all, thank you Ephraim for taking time to reply to my post & trying to help me.

I did try blacklisting the "snd-atiixp-modem" module. But that still doesn't solve the problem. The scenario isn't changed one bit!
Even after blacklisting the modem module, the aplay -l says "aplay: device_list:222: no soundcards found...".
Even though lspci lists my sound card correctly & the lsmod command shows me that snd-atiixp driver for my sound card is loaded, the system doesn't even recognise the existance of sound card. For e.g. alsamixer command results in "alsamixer: function snd_ctl_open failed for default: No such device". Trying to open the volume control from the task bar results in "No volume control GStreamer plugins and/or devices found".

I have ordered for an additional sound card. It's a Creative Sound Blaster 5.1 Live PCI card. I did research a little bit in a few linux forums to find out that this card works out of the box for most linux distributions. Hopefully that will help me get sound out of my computer (the issue with my on-board sound card will still not be solved though).

---

### Post by Peter Grant on 2007-05-22
Thankyou Ephraim!! Fantastic!! I followed all that you suggested and my Asus A6R laptop now has sound. I had just today tried Mandriva Spring and it also had no sound. This may be a fix for a general problem.

---

### Post by BinaryMadman on 2007-07-31
Ephraim, you rock!  This worked for me as well. :)  I was having problems with getting audio to work with Flash, in general really - and this fixed it!

---

### Post by andy_6590 on 2007-08-09
I followed these instructions.

"(1) Double-click the speaker icon in Ubuntu's system tray and click Edit -> Preferences in the Volume Control window that appears. In the list, look for the Master Surround entry, and put a checkbox in it. Then look for External Amplifier and put a check in it. Click the Close button then click the Switches tab in the Volume Control window. Remove the check against External Amplifier.
(2) Then click the Playback tab and click the Speaker icon beneath the Master Surround slider, so that it's no longer muted. Then adjust the slider. Playback some audio and you should find everything now works. Basically, the Master Surround slider is now your volume slider. Weird, but true. To make the system tray applet use the Master Surround to control the volume, right-click the system tray speaker icon, select Preferences, and select Master Surround in the list. "

But I went into System> Preferences> Sound, because it wouldn't let me double click like in the instructions. I got a window open with 3 Tabs Devices, Sounds and System beep. I can't find the Master Surround entry. but all the playbacks are set to Autodetect and the sound capture is ALSA - Advanced Linux Sound Architecture. I tried to test them but it just closed the window and did nothing.

Thanks.

Visit my other thread for information.

[http://ubuntuforums.org/showthread.php?t=521226](http://ubuntuforums.org/showthread.php?t=521226)

---

### Post by BinaryMadman on 2007-08-13
I forgot to mention in the earlier post that the fix only worked more reliably when I entered:

#get rid of snd-atiixp-modem
blacklist snd-atiixp-modem

rather than just:

#get rid of snd-atiixp-modem
snd-atiixp-modem

---

### Post by sheds on 2007-10-08
Hey there guys.

I've been following these instructions to solve my sound card problem. I am not seeing the sound card anywhere.

Just got a quick question here: do i have to perform something else after putting the entry in the blacklist? You know like modprobe or restart the machine?

Thanks in advance for the help.

---

### Post by jargoman on 2007-10-08
yes you would have to reboot once you blacklisted a module. Or you could remove the module with

$ sudo rmmod snd-atiixp-modem

I would recommend rebooting anyway just to be sure.

---

### Post by sheds on 2007-10-09
Ok, i restated the computer, but got the same problem.

Nonetheless, i followed an manual to get sound going in ubuntu, my case, kubuntu.

I first killed ESD with killall esd, but no processes where running with esd.

The lsof /dev/dsp and lsof /dev/snd/* gave no output, so that's fine.

I then tweaked /etc/esound/esd.conf as the manual suggested.
```
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
```

I still get no sound. So, after performing all these steps, i believe my problem is that there is no sound card detected. The manual suggests that when posting for help on the forums, i should include the output of the command 'lsmod | grep snd':
```
snd_atiixp             19852  0
snd_ac97_codec         96672  1 snd_atiixp
snd_ac97_bus            2432  1 snd_ac97_codec
snd_pcm_oss            46080  0
snd_mixer_oss          18560  1 snd_pcm_oss
snd_pcm                80520  3 snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd                    55428  6 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9952  1 snd
snd_page_alloc         10504  2 snd_atiixp,snd_pcm
```

Hope that someone can help me out and that the preceding information is enough. I will gladly post some more information that you require.

Thanks in advance for the help.

---

### Post by notxperienced on 2007-10-11
Etwas spät aber vielleicht hilft es:

in /etc/modprobe.d/options:

# for soundchip snd_atiixp
options snd-atiixp ac97_codec=0

eintragen und neu starten. Das hat hier geholfen. Sound geht seither.

---

### Post by notxperienced on 2007-10-11
Sorry, now in english:

add to /etc/modprobe.d/options the line(s)

# for soundchip snd_atiixp
options snd-atiixp ac97_codec=0

and restart the system. Hope it helps.

---

### Post by redffs on 2007-11-14
oh, my dear notxperienced, I can't love you more!!!!
You solved my problem which is there since the 1st time I install ubuntu, that is about more than 1 year ago!!!
But would you please exlain more about why this solved my problem???

Vielen Dank im Voraus.

Regards,
redffs

---

### Post by notxperienced on 2007-12-10
Hi redffs,

option ac97_codec=0 avoids the probing of the codec.
Take a look at 'modinfo snd_atiixp', that prints 'parm: ac97_codec:Specify codec instead of probing. (int)' - these means, we force the kernel with ac97_codec=0 to take the first codec. Why the probing does not work? Good question, I can't explain you that, sorry.

---

### Post by crackerdog2 on 2007-12-10
> **notxperienced said:**
> Hi redffs,

option ac97_codec=0 avoids the probing of the codec.
Take a look at 'modinfo snd_atiixp', that prints 'parm: ac97_codec:Specify codec instead of probing. (int)' - these means, we force the kernel with ac97_codec=0 to take the first codec. Why the probing does not work? Good question, I can't explain you that, sorry.

I have tried what you have said and still cannot get any sound, except for when the computer first boots up. I have all the same symptoms, but nothing seems to work.

From lspci -v:

[FONT="Courier New"]00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (
rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 309b
        Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
        Memory at c0003400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>[/FONT]

And from lsmod | grep snd:
[FONT="Courier New"]snd_rtctimer            5216  1 
snd_atiixp_modem       19468  2 
snd_seq_dummy           5380  0 
snd_seq_oss            36864  0 
snd_seq_midi           11008  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_atiixp             24084  5 
snd_ac97_codec        122200  2 snd_atiixp_modem,snd_atiixp
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
ac97_bus                4096  1 snd_ac97_codec
snd_pcm_oss            50048  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_seq                62496  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm                94344  8 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_timer              27272  3 snd_rtctimer,snd_seq,snd_pcm
snd                    69288  22 snd_atiixp_modem,snd_seq_oss,snd_rawmidi,snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_seq_device,snd_pcm,snd_timer
soundcore              10272  1 snd
snd_page_alloc         12560  3 snd_atiixp_modem,snd_atiixp,snd_pcm[/FONT]

Any help would be appreciated.

---

### Post by notxperienced on 2007-12-11
Does the soundcard appear with 'cat /proc/asound/cards' ? Did you tried to blacklist the snd_atiixp_modem module? I don't have a notebook with the sb400 chip.

---

### Post by crackerdog2 on 2007-12-11
> **notxperienced said:**
> Does the soundcard appear with 'cat /proc/asound/cards' ? Did you tried to blacklist the snd_atiixp_modem module? I don't have a notebook with the sb400 chip.

Here is what cat /proc/asound/cards gives me:
```
 0 [IXP            ]: ATIIXP - ATI IXP
                      ATI IXP rev 2 with unknown codec at 0xc0003400, irq 17
 1 [Modem          ]: ATIIXP-MODEM - ATI IXP Modem
                      ATI IXP Modem rev 2 at 0xc0003800, irq 17
```
I have just now tried blacklisting it and that still does not work even after reboot. All I get is the initial sound from Ubuntu bringing up the login page.

---

### Post by notxperienced on 2007-12-12
Hi, the soundcard is recognized. The problem seems to be the 'unknown codec at 0x...' Did you try another value, e.g. options snd-atiixp ac97_codec=1 ? You hear the initial sound. That's strange, are the mixer settings after starting the windowmanager o.k? Do you hear the sound when you try the sound settings from the system menu?

---

### Post by crackerdog2 on 2007-12-12
> **notxperienced said:**
> Hi, the soundcard is recognized. The problem seems to be the 'unknown codec at 0x...' Did you try another value, e.g. options snd-atiixp ac97_codec=1 ? You hear the initial sound. That's strange, are the mixer settings after starting the windowmanager o.k? Do you hear the sound when you try the sound settings from the system menu?

I tried setting the codec=1 and when I rebooted I didnt get any sound. When I try various sounds from the sound settings I also did not receive any sound. I did this prior to even coming across this thread. Now with the codec set to 1 my mixer does not show anything.

Now with codec=1 xmms comes back with an error when I try to play it saying that it canno open audio device /dev/dsp: No such file or directory.

Since setting snd-atiixp ac97_codec does not seem to be helping, I am removing that.

---

### Post by perfesser on 2008-03-02
> **ephraim said:**
> Hey,

<snip>


However, I also had to do the following little tweak, excerpted from the following webpage....

[http://www.beginningubuntu.com/dapper_tips.html#Sound_on_my_weird_notebook](http://www.beginningubuntu.com/dapper_tips.html#Sound_on_my_weird_notebook)

"My notebook is possibly the most Linux-incompatible machine that's ever been made. Here's a tip: Don't buy an Asus A6R. It's one of the worst notebooks I've ever owned. 
      Sound didn't work straight off. The notebook has an IXP SB400 AC'97 Audio Controller, according to Ubuntu's Device Manager. If you've got the same sound card, and want to get it working, you need to do two things. 
      (1) Double-click the speaker icon in Ubuntu's system tray and click Edit -> Preferences in the Volume Control window that appears. In the list, look for the Master Surround entry, and put a checkbox in it. Then look for External Amplifier and put a check in it. Click the Close button then click the Switches tab in the Volume Control window. Remove the check against External Amplifier. 
      (2) Then click the Playback tab and click the Speaker icon beneath the Master Surround slider, so that it's no longer muted. Then adjust the slider. Playback some audio and you should find everything now works. Basically, the Master Surround slider is now your volume slider. Weird, but true. To make the system tray applet use the Master Surround to control the volume, right-click the system tray speaker icon, select Preferences, and select Master Surround in the list. "


And so now I have sound. I hope it helps you as well.

Best wishes,
Ephraim:)

Ephraim, U Rock!
This also worked for an ACER 5920 laptop with an Intel HDA snd device.  Realtek ALC888.
I pulled my hair out on this one for two days.  Ubuntu 6.06 had sound but 7.10 did not.

Thanks a bunch!
~perf.

---

### Post by Nuclear Doughnut on 2008-03-20
Thank you so much... I've been wrestling with this problem for some time.

I'm running a Gateway Mx7527

---

### Post by blackest_knight on 2008-05-19
> **notxperienced said:**
> Sorry, now in english:

add to /etc/modprobe.d/options the line(s)

# for soundchip snd_atiixp
options snd-atiixp ac97_codec=0

and restart the system. Hope it helps.

absolutely brilliant thank you
I had given up on alsa and was trying oss drivers which do work its just so many aps do not use oss drivers.

---

### Post by ~Phoenix~ on 2008-06-14
i tried everything here but i still get no sound :cry: the card is recognized...if you want any information tell me :)

---

