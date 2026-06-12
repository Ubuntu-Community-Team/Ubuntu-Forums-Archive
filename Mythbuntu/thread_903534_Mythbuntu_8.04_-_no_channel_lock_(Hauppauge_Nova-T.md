---
title: "Mythbuntu 8.04 - no channel lock (Hauppauge Nova-T Stick USB)"
date: 2008-08-28
forum: Mythbuntu
---

### Post by kabufzk on 2008-08-28
Hi all!

I just jump right to my problem: I wasted hours and hours setting up a mythtv-backend (the only master-backend) with mythbuntu 8.04. Right now the only hardware i use is a DVB-T Hauppauge WinTV Nova-T Stick([link]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-Stick"))

The stick works out of the box, i can see the device with *lsusb* and *dmesg* shows me that the firmware has been successfully loaded onto the stick and it is registered and in warm state. 

```

user@mythtv-backend:~$ lsusb
Bus 004 Device 003: ID 2040:7050 Hauppauge Hauppauge Nova-T Stick
```

```

user@mythtv-backend:~$ dmesg | grep dvb
[   28.265844] dvb-usb: found a 'Hauppauge Nova-T Stick' in cold state, will try to load a firmware
[   29.789066] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
[   30.493473] dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
[   30.493551] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   31.384340] dvb-usb: schedule remote query interval to 150 msecs.
[   31.384349] dvb-usb: Hauppauge Nova-T Stick successfully initialized and connected.
[   31.384543] usbcore: registered new interface driver dvb_usb_dib0700

```

I can add the device in the mythtv-backend, create a new input-connection, everything works smoothly. The channel-scanner does only find 3 of the 6 channels available, but using a *channels.conf* (scanned on the same machine with the commandline-tool *scan*) reveals all channels. Then i set up the storage-directories, ran mythfilldatabase and was happy to get everything running with no problems...BUT:

When i start the frontend on the same machine (i want to use a remote frontend, but first of course i test it on the local machine) and select *Watch TV* the screen stays black for a few seconds and then presenting me the following mesage: *You should have gotten a channel lock by now. You can continue to wait for a signal ...* Below it says *Signal 0% | BE 65535 | (1__) No Lock* EIT-Information is also not available. This is the same for all 6 channels!

The stick is confirmed to work. I can use kaffeine to watch all of the 6 channels (it finds only the same 3 channels found by mythtv, but using a channels.dvb i can view all the 6). The command-line tool *scan* finds all 6 channels. I even installed an active outdoor antenna outside on a wall, because i live in an area where an outdoor-antenna is recommended (no roof-antenna, just outdoor). Signal is not the best, but kaffeine can deal with it (it shows 40-50% signal strength). can this be a problem for mythtv?

what i tried to resolve the problem:

- fresh install and applying all patches and new kernel from ubuntu repositories with *apt-get* -> NO EFFECT
- compile and install the newest drivers from v4l (*hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)*) -> NO EFFECT
- use the newest firmware suggested [here]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-Stick") -> NO EFFECT

Around 5 re-installs later i don't know what to try anymore. Does SOMEBODY have ANY suggestion to point me to a solution?

THANK YOU IN ADVANCE!:KS

---

### Post by gattopi on 2008-09-03
I have the error 
dvb-usb: no frontend was attached by 'Hauppauge Nova-T Stick'

I try 1000 solution and not work.

Help me Please:(

---

### Post by Hark on 2008-12-28
I also own a Hauppauge Nova-T Stick USB. Worked perfectly in Mythbuntu 7.10, but I have the same problems as you now. In Xine I can watch TV, in MythTV I get nothing more than the message "You should have gotten a channel lock by now" etc.

---

### Post by joho500 on 2009-02-15
Do you have a solution to this problem? I have the same problem with a Technotrend T-1500. I think I read somewhere that Mythtv has a problem with finding/storing the right frequencies, but I can't find it.

Cheers,

Joost

---

