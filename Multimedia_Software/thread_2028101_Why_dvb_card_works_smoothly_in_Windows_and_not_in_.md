---
title: "Why dvb card works smoothly in Windows and not in Ubuntu 12.04?"
date: 2012-07-17
forum: Multimedia Software
---

### Post by mzcl-mn on 2012-07-17
Hi!

I have an Asus My Cinema-U3000Hybrid card.

It works flawlessly in windows...

In Ubuntu 12.04 x86_64 I get pixelizations, sound lags and other distortions.

Can anyone lend a hand?

Regards.

---

### Post by mzcl-mn on 2012-07-19
Hello.

Isn't anyone willing to lend a hand?

](*,)

---

### Post by Whovian on 2012-07-19
Could either be that the card is not fully supported. Two you are missing a driver. Possibly the third could be a error on boot up. Try this out
```
dmesg | less
```Or look for the error log files to see if it booted correctly.(imo those could be it I maybe be wrong though)

---

### Post by BicyclerBoy on 2012-07-20
This model ?
[http://www.linuxtv.org/wiki/index.php/ASUS](http://www.linuxtv.org/wiki/index.php/ASUS)
[http://www.linuxtv.org/wiki/index.php/ASUS_My_Cinema-U3000_Mini](http://www.linuxtv.org/wiki/index.php/ASUS_My_Cinema-U3000_Mini)

---

### Post by mzcl-mn on 2012-07-23
> **BicyclerBoy said:**
> This model ?
[http://www.linuxtv.org/wiki/index.php/ASUS](http://www.linuxtv.org/wiki/index.php/ASUS)
[http://www.linuxtv.org/wiki/index.php/ASUS_My_Cinema-U3000_Mini](http://www.linuxtv.org/wiki/index.php/ASUS_My_Cinema-U3000_Mini)


Hi,

I've followed both links but the issue still remains.


@Whovian: I also have tried those commands.

After the device is connected, I get this:

```
[15008.768069] usb 2-4: new high-speed USB device number 10 using ehci_hcd
[15008.900965] usb 2-4: New USB device found, idVendor=0b05, idProduct=1736
[15008.900977] usb 2-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[15008.900984] usb 2-4: Product: U3000 Hybrid
[15008.900991] usb 2-4: Manufacturer: ASUSTeK
[15008.900997] usb 2-4: SerialNumber: 3930000062
[15008.902203] dvb-usb: found a 'Asus My Cinema-U3000Hybrid' in cold state, will try to load a firmware
[15008.951924] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[15009.167327] dib0700: firmware started successfully.
[15009.668251] dvb-usb: found a 'Asus My Cinema-U3000Hybrid' in warm state.
[15009.668428] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[15009.668611] DVB: registering new adapter (Asus My Cinema-U3000Hybrid)
[15009.919225] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[15009.919446] xc2028 6-0061: creating new instance
[15009.919453] xc2028 6-0061: type set to XCeive xc2028/xc3028 tuner
[15009.919470] Registered IR keymap rc-dib0700-rc5
[15009.919710] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/rc/rc5/input16
[15009.920270] rc5: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/rc/rc5
[15009.920456] dvb-usb: schedule remote query interval to 50 msecs.
[15009.920465] dvb-usb: Asus My Cinema-U3000Hybrid successfully initialized and connected.

```

After/during the operation of the device I get (lots of) these by repeating the commands: ```
dmesg | less
```

```
[15630.102657] xc2028 6-0061: Loading firmware for type=D2620 DTV8 (208), id 0000000000000000.
[15630.107503] dib0700: stk7700ph_xc3028_callback: unknown command 2, arg 0
[15630.107503] 
[15630.112375] dib0700: stk7700ph_xc3028_callback: unknown command 2, arg 0
[15630.112375] 
[15630.116513] dib0700: stk7700ph_xc3028_callback: unknown command 2, arg 0
[15630.116513] 
[15630.124507] dib0700: stk7700ph_xc3028_callback: unknown command 2, arg 0
[15630.124507] 
[15630.132508] dib0700: stk7700ph_xc3028_callback: unknown command 2, arg 0
[15630.132508] 
[15630.140879] dib0700: stk7700ph_xc3028_callback: unknown command 2, arg 0
[15630.140879] 
[15630.145011] dib0700: stk7700ph_xc3028_callback: unknown command 2, arg 0
[15630.145011] 
[15630.149128] dib0700: stk7700ph_xc3028_callback: unknown command 2, arg 0
[15630.149128] 
[15630.157152] dib0700: stk7700ph_xc3028_callback: unknown command 2, arg 0
[15630.157152] 
[15630.161250] dib0700: stk7700ph_xc3028_callback: unknown command 2, arg 0
[15630.161250] 
[15630.167375] dib0700: stk7700ph_xc3028_callback: unknown command 2, arg 0
[15630.167375] 
[15630.171754] dib0700: stk7700ph_xc3028_callback: unknown command 2, arg 0
[15630.171754] 
[15630.179767] dib0700: stk7700ph_xc3028_callback: unknown command 2, arg 0
[15630.179767] 
[15630.183887] dib0700: stk7700ph_xc3028_callback: unknown command 2, arg 0
[15630.183887] 
[15630.187999] dib0700: stk7700ph_xc3028_callback: unknown command 2, arg 0
[15630.187999] 
[15630.194894] dib0700: stk7700ph_xc3028_callback: unknown command 2, arg 0
[15630.194894] 
[15630.199000] dib0700: stk7700ph_xc3028_callback: unknown command 2, arg 0
[15630.199000] 
[15630.203144] dib0700: stk7700ph_xc3028_callback: unknown command 2, arg 0
[15630.203144] 
[15630.207504] dib0700: stk7700ph_xc3028_callback: unknown command 2, arg 0
[15630.207504] 
[15630.212398] dib0700: stk7700ph_xc3028_callback: unknown command 2, arg 0
[15630.212398] 
[15630.212412] xc2028 6-0061: Loading SCODE for type=DTV7 DTV78 DTV8 DIBCOM52 CHINA SCODE HAS_IF_5400 (65000380), id 0000000000000000.

```

Any ideas if this has anything to do with my issues and if that's true, on how to solve them?



Finally,  thank you all for the interest shown so far!

Regards.

---

### Post by BicyclerBoy on 2012-07-23
Long shot..

The errors you have could be IR polling or just unimportant..
If you can live without IR remote (or use another) .. make a file called /etc/modprobe.d/dvb.conf.
stick this in the file:
options dvb_usb disable_rc_polling=1

Ubuntu requires this to get the new modules options into boot image:
sudo update-initramfs -u

**But are** you sure there is any problem with the tuner card/stick ?

You can use "cat" to copy a stream (e.g. /dev/dvb/adapter0/dvr0) to a file (after tuning)..then try play the file with ffplay or VLC or mplayer.

---

### Post by mzcl-mn on 2012-07-24
> **BicyclerBoy said:**
> Long shot..

The errors you have could be IR polling or just unimportant..
If you can live without IR remote (or use another) .. make a file called /etc/modprobe.d/dvb.conf.
stick this in the file:
options dvb_usb disable_rc_polling=1

Ubuntu requires this to get the new modules options into boot image:
sudo update-initramfs -u

**But are** you sure there is any problem with the tuner card/stick ?

You can use "cat" to copy a stream (e.g. /dev/dvb/adapter0/dvr0) to a file (after tuning)..then try play the file with ffplay or VLC or mplayer.


Hello, and thanks.

I guess there's no problem with the tuner. It works with windows ( :( ).

I am going to try your recommendations on a fresh install of ubuntu 12.04 x86_64 then I'll come back to report.

Thanks again.

---

### Post by mzcl-mn on 2012-07-25
Hello, so I did a fresh install and followed ByciclerBoy hint.

a while after logging into the system I plug the device in, and issue dmesg on the command line,

here's what I get:

```
[  168.280125] usb 2-3: new high-speed USB device number 3 using ehci_hcd
[  168.602323] IR NEC protocol handler initialized
[  168.698600] dib0700: loaded with support for 21 different device-types
[  168.698839] dvb-usb: found a 'Asus My Cinema-U3000Hybrid' in cold state, will try to load a firmware
[  168.705126] IR RC5(x) protocol handler initialized
[  168.714618] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[  168.723747] IR RC6 protocol handler initialized
[  168.728065] IR JVC protocol handler initialized
[  168.732030] IR Sony protocol handler initialized
[  168.736550] IR MCE Keyboard/mouse protocol handler initialized
[  168.741172] lirc_dev: IR Remote Control driver registered, major 249 
[  168.742688] IR LIRC bridge handler initialized
[  168.925195] dib0700: firmware started successfully.
[  169.428436] dvb-usb: found a 'Asus My Cinema-U3000Hybrid' in warm state.
[  169.428606] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  169.428759] DVB: registering new adapter (Asus My Cinema-U3000Hybrid)
[  169.685683] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[  169.741626] xc2028 6-0061: creating new instance
[  169.741635] xc2028 6-0061: type set to XCeive xc2028/xc3028 tuner
[  169.741645] dvb-usb: Asus My Cinema-U3000Hybrid successfully initialized and connected.
[  169.742410] usbcore: registered new interface driver dvb_usb_dib0700

```


when I issue---> tzap "RTP 1" (again at the command prompt) I get readings like these:


```
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
reading channels from file '/home/cris/.tzap/channels.conf'
tuning to 754000000 Hz
video pid 0x0100, audio pid 0x0101
status 1f | signal a72f | snr 00b6 | ber 001fffff | unc 00000012 | FE_HAS_LOCK
status 1f | signal a65c | snr 00aa | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a696 | snr 00ac | ber 00001f40 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a6c5 | snr 00aa | ber 00002560 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a6e6 | snr 00aa | ber 000013a0 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a6e4 | snr 00aa | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a6fb | snr 00a8 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a704 | snr 00b0 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a72b | snr 00aa | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a706 | snr 00a7 | ber 00003680 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a741 | snr 00a9 | ber 00000b80 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a730 | snr 00ac | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a6e3 | snr 00aa | ber 00000000 | unc 00000006 | FE_HAS_LOCK
status 1f | signal a73d | snr 00b1 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a752 | snr 00af | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a770 | snr 00a7 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a761 | snr 00a9 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a78c | snr 00ab | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a773 | snr 00a8 | ber 00001bb0 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a7ba | snr 00ac | ber 00000060 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a7e1 | snr 00ac | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a79d | snr 00a9 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a7c5 | snr 00a9 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a7c4 | snr 00af | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a7df | snr 00ad | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a7de | snr 00ac | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a7dc | snr 00af | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a803 | snr 00ab | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a81c | snr 00ab | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a80d | snr 00ad | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a80a | snr 00ac | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a808 | snr 00ab | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a81f | snr 00a5 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a7f6 | snr 00a9 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a840 | snr 00ab | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a848 | snr 00a7 | ber 00000000 | unc 00000012 | FE_HAS_LOCK
status 1f | signal a825 | snr 00ae | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a851 | snr 00a9 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a845 | snr 00ac | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a858 | snr 00ab | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a81a | snr 00ae | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal a868 | snr 00a8 | ber 00000050 | unc 0000000c | FE_HAS_LOCK

```


If I do dmesg then I get the same

```
"dib0700: stk7700ph_xc3028_callback: unknown command 2, arg 0"
```

errors again.



How can I be sure the rc options were indeed loaded?


Thanks.

---

### Post by BicyclerBoy on 2012-07-25
Rem: it was a long shot..
The actual module options will be viewable in the /proc filesystem (somewhere)..

To see the possible options (not actual in use):
modinfo dvb-usb

With the card tuned in one terminal with tzap..open another terminal & run
ffplay -f v4l2 -i /dev/video0
or
cat /dev/video0 > sample.mpg
and then play file with VLC or mplayer.

---

### Post by mzcl-mn on 2012-07-26
Hello BicyclerBoy,

Thanks again for all the help you have been giving up until now.

I really appreciate it.


When you suggested to use tzap to tune in i did the following:

first:

```
tzap -r  "TVI"
```

and on another terminal I tried several things:

```
cat /dev/dvb/adapter0/dvr0 > testvideo.mpg
```

and also 

```
mplayer /dev/dvb/adapter0/dvr0
```


I could see image (but no sound... :(

Besides, the image continues with issues... :(


I used the above devices because there does not seem to be any /dev/video0 on the system...

Regards

---

### Post by Merrattic on 2012-07-26
Do you get the same behaviour when the stick is plugged in before you boot the PC?

My dvb stick (not the same one) needs to be plugged in before boot to activate properly.....

---

### Post by mzcl-mn on 2012-07-27
Yes Merrattic, it's the same behavior.

After a while tuning in, the distortions begin.

What I find odd is that in the beginning there are practically none.

But as the time goes, they become more and more apparent and disturbing.

---

### Post by mzcl-mn on 2012-07-27
> **BicyclerBoy said:**
> Rem: it was a long shot..
The actual module options will be viewable in the /proc filesystem (somewhere)..

To see the possible options (not actual in use):
modinfo dvb-usb

With the card tuned in one terminal with tzap..open another terminal & run
ffplay -f v4l2 -i /dev/video0
or
cat /dev/video0 > sample.mpg
and then play file with VLC or mplayer.

Hello BicyclerBoy.

I have been busy with this issue, so I've googled around and found an utility for checking out kernel modules called *systools* (which is available on the **sysfsutils** package for our Ubuntu).

Well I've issued

```
systool -v -m dvb_usb | less
```

after having installed that **sysfsutils** package and I got this

```
Module = "dvb_usb"

  Attributes:
    initstate           = "live"
    refcnt              = "1"
    srcversion          = "C87BB12D300C227ECC94997"
    uevent              = <store method only>
    version             = "1.0"

  Parameters:
    debug               = "0"
    disable_rc_polling  = "1"
    force_pid_filter_usage= "0"

  Sections:
    .bss                = "0x0000000000000000"
    .gnu.linkonce.this_module= "0x0000000000000000"
    .note.gnu.build-id  = "0x0000000000000000"
    .rodata             = "0x0000000000000000"
    .rodata.str1.1      = "0x0000000000000000"
    .rodata.str1.8      = "0x0000000000000000"
    .smp_locks          = "0x0000000000000000"
    .strtab             = "0x0000000000000000"
    .symtab             = "0x0000000000000000"
    .text               = "0x0000000000000000"
    __kcrctab           = "0x0000000000000000"
    __ksymtab           = "0x0000000000000000"
    __ksymtab_strings   = "0x0000000000000000"
    __mcount_loc        = "0x0000000000000000"
    __param             = "0x0000000000000000"


```
Does this mean that the rc polling option is set?


I also found out that there is another module for handling  **dvb_usb** on my particular hardware setting (and I am not so sure if that module should be the one to tweak for the rc polling) which is *_dvb_usb_dib0700_*

I am going to check what settings are there to be set on that module with your suggested modinfo command and if there is one available for rc polling. Maybe it's on this module that this setting must be made. What do you think?

You may ask why am I doing this assumption, well it's because on the above section from the dvb_usb module, the field __param has a zero value which makes think that the option for rc polling was not entirely accepted).

Regards!

---

### Post by BicyclerBoy on 2012-08-03
Looks like it is set..

Can check here as well:
cat /sys/module/dvb_usb/parameters/disable_rc_polling

ls -al  /sys/module/dvb_usb_dib0700/parameters/

This could be the complete list ?? else look into the source code.
[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500#dvb_usb_dib0700](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500#dvb_usb_dib0700)

---

### Post by mzcl-mn on 2012-08-03
Hello BicyclerBoy;

Thank-you once more for all your help.

Will check-out those hints and then I'll report back.

Regards

---

### Post by mzcl-mn on 2012-08-16
Hello,

I've took a break from this project.

That is why it has taken me so long to post this update.

Also I have decided to try out another device.


The device is an AVerTV Volar Green HD, and its ID is 07ca:a835

It doesn't have support yet but with a little googling I've found out instructions on how to make it work:

[http://mauriziosiagri.wordpress.com/tag/07caa835/#ubuntu12](http://mauriziosiagri.wordpress.com/tag/07caa835/#ubuntu12)

So now one of the most important stages of my project is covered out.

I am still looking for a solution for the Asus device that I had... but that must be postponed.

For the project to be completed I think that maybe I should seek help on some other subforum because it is related to networking.

The purpose of all this endeavor is to stream dvb on local network. I can confirm that streaming from server works but up to a certain point.

If I use vlc as a server software, and stream for instance one dvb channel with http settings, I sucessfully tune to it on the client pc at another address on the lan.

But, if I use some other protocol, for instance "rtp/mpeg ts" and stream it to some multicast address, I can only get distortions on the client side.

I think that my router can handle IGMP. But I am not absolutely sure that it is set correctly.

So... That's about it! I am stuck...

Thanks for any pointers!

---

### Post by elvis_ef on 2012-10-15
I have the same problem on my Ubuntu 12.04 (had it also on 11.04 and 11.10). I think it's related to a lack of packets in a system or something like that. I was working with it and the system was starting up successfully. I can't remember what kind of small things I did, and suddenly I have this problem and my ubuntu desktop can't run. The X server is stopping and the console is coming up. Need to login with the pass, and then when I run "startx" it shows desktop but without gnome-panel (only icons are visible) and any title bars on windows. Hmm... weird... Do not know what to do with it. When this message shows up while starting ubuntu: "dib0700: stk7700ph_xc3028_callback: unknown command 2, arg 0" I can't do anything. It's full of rows from up to down the screen and it lasts about 5/6 seconds and then stops. But to login in the same console terminal (tty1) I need to press ALT+F2 for a while and then press ALT+F1 again, to come back to the previous terminal to see login and pass options. While booting it just shows all the messages, then messages disappear and... I should see login and pass screen (lightdm) but... it comes back to the console with another messages and then....  this message from up to down... eh : /

What this would be? I have "firmware non-free" installed (it's in the ppa / installing by Synaptic). Maybe I did something wrong and some of the packages cannot live without other ones? Cause earlier even if this problem with "dib0700: stk...." was, I could normally run the system. Now I can't...

Any suggestions? Maybe I should reinstall some packages like Xorg server or ubuntu-desktop metapackage?...

My system: Ubuntu Desktop 12.04 with Lightdm desktop environment. Hmm.. Could it be related to that I have Gnome Fallback and Mate installed on this system together? It can interfere with themselves... anyway how to solve the problem with this line of Dib0700?

Thanks in advance for any suggestion.

----------------------------------------------------------------------------------

**Edit: **Ok, the problem that I couldn't see lightdm was that I removed "unity-greeter" package (found it out in lightdm logs), doesn't matter Im using Gnome Fallback though... (weird..) But the problem with dib0700 persists..

---

