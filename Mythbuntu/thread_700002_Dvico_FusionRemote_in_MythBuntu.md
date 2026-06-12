---
title: "Dvico FusionRemote in MythBuntu"
date: 2008-02-17
forum: Mythbuntu
---

### Post by nasha on 2008-02-17
Hi Guys,
Having issues getting my remote working. Tuner card is Dvico Dual Digital 4.  I've tried following:
[http://ubuntuforums.org/archive/index.php/t-616103.html](http://ubuntuforums.org/archive/index.php/t-616103.html)
But i get an error attempting to run the first CVS command (not due to the poor syntax of commands in the link).
Anyone have a link to another tutorial, or prepared to help me get this set up?
Any advice would be much appreciated

Regards,
Nasha

---

### Post by NotMyName on 2008-02-18
Hi Nasha

Which type of remote do you have? 

I far as I know there are 3 distinct types of remote control supplied with the card. 2 x MCE types and 1 non-MCE type. 
I suspect you have the later (like I do). The instructions you were following only apply to the MCE type. I eventually got my non-mce one working but it wasn't easy. If you can you post a small photo of your remote I can direct you to the correct instructions for that model.

---

### Post by nasha on 2008-02-18
Here's a link to my remote: [http://lirc.sourceforge.net/remotes/dvico/FusionRemote.jpg](http://lirc.sourceforge.net/remotes/dvico/FusionRemote.jpg)
Thanks for any help you can provide :)

---

### Post by NotMyName on 2008-02-18
> **nasha said:**
> Here's a link to my remote: [http://lirc.sourceforge.net/remotes/dvico/FusionRemote.jpg](http://lirc.sourceforge.net/remotes/dvico/FusionRemote.jpg)
Thanks for any help you can provide :)

Yep that's the one, exactly the same as mine.
I have a working lircc setup I can give you when I get home tonight.

What stage are you at now?
In a terminal run
dmesg|grep DVB

Do you get a line similar to this;
"input: IR-receiver inside an USB DVB receiver as /class/input/input5"

If you do then irw in a terminal and press a few keys.
Do you get command names or codes or nothing at all?

---

### Post by nasha on 2008-02-18
Im at the stage where i've done little to nothing concerning the remote setup, because i had no idea where to start.

Strangely, dmesg doesnt output anything regarding the IR reciever... I say strangely because a day or two ago it was telling me there wasn't one connected :/

If i dmesg|grep IR on the last line i get 'cxusb: No IR reciver detected on this device.'

---

### Post by NotMyName on 2008-02-18
> **nasha said:**
> Im at the stage where i've done little to nothing concerning the remote setup, because i had no idea where to start.

Strangely, dmesg doesnt output anything regarding the IR reciever... I say strangely because a day or two ago it was telling me there wasn't one connected :/

If i dmesg|grep IR on the last line i get 'cxusb: No IR reciver detected on this device.'

Please run dmesg|grep DVB and post the result.
When I run that command I get the following.

jeff@htpc1:~/myconfs$ dmesg|grep DVB
[   54.007293] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4' in warm state.
[   54.038445] DVB: registering new adapter (DViCO FusionHDTV DVB-T Dual Digital 4)
[   54.268606] DVB: registering frontend 0 (Zarlink ZL10353 DVB-T)...
[   54.402453] input: IR-receiver inside an USB DVB receiver as /class/input/input5
[   54.402536] dvb-usb: DViCO FusionHDTV DVB-T Dual Digital 4 successfully initialized and connected.
[   54.402544] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4' in warm state.
[   54.433755] DVB: registering new adapter (DViCO FusionHDTV DVB-T Dual Digital 4)
[   54.479554] DVB: registering frontend 1 (Zarlink ZL10353 DVB-T)...
[   54.480177] dvb-usb: DViCO FusionHDTV DVB-T Dual Digital 4 successfully initialized and connected.

---

### Post by nasha on 2008-02-18
dmesg|grep DVB output:

[   28.151288] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4' in warm state.
[   28.182716] DVB: registering new adapter (DViCO FusionHDTV DVB-T Dual Digital 4)
[   28.363469] DVB: registering frontend 0 (Zarlink ZL10353 DVB-T)...
[   28.430930] dvb-usb: DViCO FusionHDTV DVB-T Dual Digital 4 successfully initialized and connected.
[   28.430952] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4' in warm state.
[   28.462183] DVB: registering new adapter (DViCO FusionHDTV DVB-T Dual Digital 4)
[   28.511390] DVB: registering frontend 1 (Zarlink ZL10353 DVB-T)...
[   28.512130] dvb-usb: DViCO FusionHDTV DVB-T Dual Digital 4 successfully initialized and connected.

---

### Post by NotMyName on 2008-02-19
> **nasha said:**
> dmesg|grep DVB output:

[   28.151288] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4' in warm state.
[   28.182716] DVB: registering new adapter (DViCO FusionHDTV DVB-T Dual Digital 4)
[   28.363469] DVB: registering frontend 0 (Zarlink ZL10353 DVB-T)...
[   28.430930] dvb-usb: DViCO FusionHDTV DVB-T Dual Digital 4 successfully initialized and connected.
[   28.430952] dvb-usb: found a 'DViCO FusionHDTV DVB-T Dual Digital 4' in warm state.
[   28.462183] DVB: registering new adapter (DViCO FusionHDTV DVB-T Dual Digital 4)
[   28.511390] DVB: registering frontend 1 (Zarlink ZL10353 DVB-T)...
[   28.512130] dvb-usb: DViCO FusionHDTV DVB-T Dual Digital 4 successfully initialized and connected.

So far so good. It looks like you already have the v4l-dvb updates needed for the card.
What needs to happen is for the firmware to be loaded for the remote control to be found.

cd /lib/firmware
    wget [http://www.linuxtv.org/downloads/firmware/dvb-usb-bluebird-01.fw](http://www.linuxtv.org/downloads/firmware/dvb-usb-bluebird-01.fw)
    wget [http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/xc3028-dvico-au-01.fw](http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/xc3028-dvico-au-01.fw)
    wget [http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/dvb-usb-bluebird-02.fw](http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/dvb-usb-bluebird-02.fw)

Unplug and replug the IR receiver.
Run dmesg|grep DVB again and see if the IR receiver is listed.

---

### Post by nasha on 2008-02-19
I already have those files in /lib/firmware from when i followed the guide i mentioned in my first post...

Just deleted them, and retrieved them again just incase something went wrong. Still nothing in dmesg

---

### Post by NotMyName on 2008-02-19
> **nasha said:**
> I already have those files in /lib/firmware from when i followed the guide i mentioned in my first post...

Just deleted them, and retrieved them again just incase something went wrong. Still nothing in dmesg

Is the are the firmware files dated 15/12/2007?
I'm leaving work now but I've found the original instructions I followed.
Have a look at Chris Pascoe's page here
[http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/](http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/)

I followed the instructions dated 2007/11/12. After doing this I just needed to update my lircd.conf and lircc files and it all worked. I can provide copies of those when I get home.

---

### Post by nasha on 2008-02-19
Files were downloaded from Chris Pascoe, using the link you provided. Files aren't dated 15/12/2007, but the post where they came from is.
The instructions under 11/12/2007 say that the patches are no longer needed:
2007/11/12:

Last night, I convinced my friend with the FusionHDTV Dual Digital 4 board to temporarily swap theirs with my Dual Digital 2, and within a few hours I had the IR remote control working on it.

Update 2007/12/28: The code to make the Dual Digitla 4 IR remote control work, together with the new xc3028 driver support, has been integrated into the main v4l-dvb tree. You will need to download the newer firmware files linked from the 2007/12/15 entry, above, before you will be able to tune.

Would greatly appreciate a copy of those files, that is if i can manage to get the damn receiver going :/

---

### Post by NotMyName on 2008-02-19
> **nasha said:**
> Files were downloaded from Chris Pascoe, using the link you provided. Files aren't dated 15/12/2007, but the post where they came from is.
The instructions under 11/12/2007 say that the patches are no longer needed:
2007/11/12:

Last night, I convinced my friend with the FusionHDTV Dual Digital 4 board to temporarily swap theirs with my Dual Digital 2, and within a few hours I had the IR remote control working on it.

Update 2007/12/28: The code to make the Dual Digitla 4 IR remote control work, together with the new xc3028 driver support, has been integrated into the main v4l-dvb tree. You will need to download the newer firmware files linked from the 2007/12/15 entry, above, before you will be able to tune.

Would greatly appreciate a copy of those files, that is if i can manage to get the damn receiver going :/

I did it before that merge happened.

So the complete steps with that merge in mind are

hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd v4l-dvb
make
sudo make install

Then you need firmware
This is for Australia (I forgot to ask where you are based)
cd /lib/firmware
wget [http://www.linuxtv.org/downloads/firmware/dvb-usb-bluebird-01.fw](http://www.linuxtv.org/downloads/firmware/dvb-usb-bluebird-01.fw)
wget [http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/xc3028-dvico-au-01.fw](http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/xc3028-dvico-au-01.fw)
wget [http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/dvb-usb-bluebird-02.fw](http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/dvb-usb-bluebird-02.fw)

reboot

At this point all being well you should be able to see the 
"input: IR-receiver inside an USB DVB receiver as /class/input/inputX"
when you do dmesg|grep DVB.

If it appears then you're 99% there. If it's not then you need to investigate why the USB device is not being loaded. run dmesg and look for any error messages. If it does appear then it's time to edit your lirc.conf, hardware.conf and lircc files to work with this remote.
I found the Lircd.conf, hardware.conf and lircc files that work with this remote at
[http://www.mythtv.org/wiki/index.php/DViCO_FusionHDTV_DVB-T_Dual_Digital_Installation](http://www.mythtv.org/wiki/index.php/DViCO_FusionHDTV_DVB-T_Dual_Digital_Installation)
Just edit the hardware.conf file to match the input4 or 5 or whatever was shown for your remote.
Once this is done restart lirc by opening a terminal window and typing in /etc/init.d/lirc restart.
The restart the irexec daemon with irexec -d.
Then run irw and press some buttons on the remote.
You should see the remote name and command names appear in the terminal.

Best of luck.

---

### Post by nasha on 2008-02-19
Ive done all those steps to get the IR going. All redo them again, just to be sure and with a bit of luck it will resolve the issue.
If not, im lost! Thanks again for all your help!

---

### Post by nasha on 2008-02-19
Went through:
hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd v4l-dvb
make
sudo make install

Then you need firmware
This is for Australia (I forgot to ask where you are based)
cd /lib/firmware
wget [http://www.linuxtv.org/downloads/fir...bluebird-01.fw](http://www.linuxtv.org/downloads/fir...bluebird-01.fw)
wget [http://www.itee.uq.edu.au/~chrisp/Li...dvico-au-01.fw](http://www.itee.uq.edu.au/~chrisp/Li...dvico-au-01.fw)
wget [http://www.itee.uq.edu.au/~chrisp/Li...bluebird-02.fw](http://www.itee.uq.edu.au/~chrisp/Li...bluebird-02.fw)

reboot

No change to the output of dmesg|grep DVB. Something clearly hates me and doesnt want me to have a working remote lol

---

### Post by NotMyName on 2008-02-19
> **nasha said:**
> Went through:
hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
cd v4l-dvb
make
sudo make install

Then you need firmware
This is for Australia (I forgot to ask where you are based)
cd /lib/firmware
wget [http://www.linuxtv.org/downloads/fir...bluebird-01.fw](http://www.linuxtv.org/downloads/fir...bluebird-01.fw)
wget [http://www.itee.uq.edu.au/~chrisp/Li...dvico-au-01.fw](http://www.itee.uq.edu.au/~chrisp/Li...dvico-au-01.fw)
wget [http://www.itee.uq.edu.au/~chrisp/Li...bluebird-02.fw](http://www.itee.uq.edu.au/~chrisp/Li...bluebird-02.fw)

reboot

No change to the output of dmesg|grep DVB. Something clearly hates me and doesnt want me to have a working remote lol

I feel for you. It took me nearly a week to get it all going properly so I know how you feel. As someone once suggested to me "you always have the option of buying a standard MCE remote and using that".

But if you feel like nutting it out try doing the commands below and comparing your results with mine. See if some modules have not loaded.

jeff@htpc1:~$ lsmod|grep usb
dvb_usb_cxusb          26884  14
dvb_usb                23052  1 dvb_usb_cxusb
dvb_core               80668  1 dvb_usb
i2c_core               26112  4 tuner_xc2028,zl10353,dvb_usb,nvidia
usbhid                 29536  0
hid                    28928  1 usbhid
usbcore               138632  10 zd1211rw,dvb_usb_cxusb,dvb_usb,xpad,lirc_imon,usbhid,ehci_hcd,uhci_hcd

jeff@htpc1:~$ lsmod|grep dvb
dvb_usb_cxusb          26884  14
dvb_usb                23052  1 dvb_usb_cxusb
dvb_core               80668  1 dvb_usb
i2c_core               26112  4 tuner_xc2028,zl10353,dvb_usb,nvidia
usbcore               138632  10 zd1211rw,dvb_usb_cxusb,dvb_usb,xpad,lirc_imon,usbhid,ehci_hcd,uhci_hcd

---

### Post by nasha on 2008-02-19
Here's my output. It seems some things arent getting loaded :s

nasha@MythTV:~$ lsmod|grep usb
usb_storage            73024  0 
ide_core              116804  1 usb_storage
usbhid                 29536  0 
libusual               18448  1 usb_storage
hid                    28928  1 usbhid
dvb_usb_cxusb          26884  23 
dvb_usb                23052  1 dvb_usb_cxusb
dvb_core               80668  1 dvb_usb
i2c_core               26112  3 tuner_xc2028,zl10353,dvb_usb
scsi_mod              147084  6 sbp2,usb_storage,sg,sd_mod,sr_mod,libata
usbcore               138632  8 usb_storage,usbhid,libusual,dvb_usb_cxusb,dvb_usb,ehci_hcd,uhci_hcd

nasha@MythTV:~$ lsmod|grep dvb
dvb_usb_cxusb          26884  23 
dvb_usb                23052  1 dvb_usb_cxusb
dvb_core               80668  1 dvb_usb
i2c_core               26112  3 tuner_xc2028,zl10353,dvb_usb
usbcore               138632  8 usb_storage,usbhid,libusual,dvb_usb_cxusb,dvb_usb,ehci_hcd,uhci_hcd

---

### Post by NotMyName on 2008-02-19
> **nasha said:**
> Here's my output. It seems some things arent getting loaded :s

nasha@MythTV:~$ lsmod|grep usb
usb_storage            73024  0 
ide_core              116804  1 usb_storage
usbhid                 29536  0 
libusual               18448  1 usb_storage
hid                    28928  1 usbhid
dvb_usb_cxusb          26884  23 
dvb_usb                23052  1 dvb_usb_cxusb
dvb_core               80668  1 dvb_usb
i2c_core               26112  3 tuner_xc2028,zl10353,dvb_usb
scsi_mod              147084  6 sbp2,usb_storage,sg,sd_mod,sr_mod,libata
usbcore               138632  8 usb_storage,usbhid,libusual,dvb_usb_cxusb,dvb_usb,ehci_hcd,uhci_hcd

nasha@MythTV:~$ lsmod|grep dvb
dvb_usb_cxusb          26884  23 
dvb_usb                23052  1 dvb_usb_cxusb
dvb_core               80668  1 dvb_usb
i2c_core               26112  3 tuner_xc2028,zl10353,dvb_usb
usbcore               138632  8 usb_storage,usbhid,libusual,dvb_usb_cxusb,dvb_usb,ehci_hcd,uhci_hcd

lirc_imon not loading could be a problem.
You can try
sudo modprobe lirc_dev
sudo modprobe lirc_imon

see what happens and then check the logs. I suspect that something has gone wrong when you did the v4l-dvb make and install causing lirc to not load the driver.

This page has a fairly simple explanation of the process
[https://help.ubuntu.com/community/DViCO_Dual_Digital_4](https://help.ubuntu.com/community/DViCO_Dual_Digital_4)

Other than that you may need someone with more experience of Linux internals than me. 

Sorry I can't be of more help.

---

