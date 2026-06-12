---
title: "Hauppauge NOVA-T 500 I2C errors (again...)"
date: 2009-03-31
forum: Mythbuntu
---

### Post by oct on 2009-03-31
Hi all

I know it sounds like a duplicate threat, but all previous posts seem to have been solved, although I continue with the problems.

I've been using Mythbuntu since 7.210 release. I installed the Nova-T 500 fllowing the wiki, and using 1.10 firmware. Later I upgraded to 8.04, did the updates and, a 4 weeks ago, reinstalled the Nova-t using the latest V4L drivers and 1.20 firmware.

From what I read, the disconnect issue had gon with kernel version 2.6.24-16, but I'm using the 2.6.24-23 and the I2C errors are still there. They appear randomly and, when happen, I have to completely power off and remove the power chord to have the card working again. 

I also tried to add a delay to the tuning process as explained as a solution to someone, with bo luck.

Can anybody help me solve this problem, please? Am I doing something wrong? I attach the syslog output of the last freeze.

Thanks

Oct


Mar 30 21:48:53 HTPC kernel: [  132.866291] irq 17: nobody cared (try booting with the "irqpoll" option)
Mar 30 21:48:53 HTPC kernel: [  132.866300] Pid: 0, comm: swapper Tainted: P        2.6.24-23-generic #1
Mar 30 21:48:53 HTPC kernel: [  132.866329]  [__report_bad_irq+0x24/0x80] __report_bad_irq+0x24/0x80
Mar 30 21:48:53 HTPC kernel: [  132.866350]  [note_interrupt+0x27b/0x2c0] note_interrupt+0x27b/0x2c0
Mar 30 21:48:53 HTPC kernel: [  132.866371]  [<e089fccb>] usb_hcd_irq+0x2b/0x60 [usbcore]
Mar 30 21:48:53 HTPC kernel: [  132.866397]  [handle_IRQ_event+0x30/0x60] handle_IRQ_event+0x30/0x60
Mar 30 21:48:53 HTPC kernel: [  132.866413]  [handle_fasteoi_irq+0x86/0xe0] handle_fasteoi_irq+0x86/0xe0
Mar 30 21:48:53 HTPC kernel: [  132.866429]  [do_IRQ+0x3b/0x70] do_IRQ+0x3b/0x70
Mar 30 21:48:53 HTPC kernel: [  132.866455]  [common_interrupt+0x23/0x30] common_interrupt+0x23/0x30
Mar 30 21:48:53 HTPC kernel: [  132.866462]  [default_idle+0x0/0x60] default_idle+0x0/0x60
Mar 30 21:48:53 HTPC kernel: [  132.866492]  [native_safe_halt+0x2/0x10] native_safe_halt+0x2/0x10
Mar 30 21:48:53 HTPC kernel: [  132.866504]  [default_idle+0x3c/0x60] default_idle+0x3c/0x60
Mar 30 21:48:53 HTPC kernel: [  132.866508]  [cpu_idle+0x45/0xd0] cpu_idle+0x45/0xd0
Mar 30 21:48:53 HTPC kernel: [  132.866521]  [start_kernel+0x31f/0x3b0] start_kernel+0x31f/0x3b0
Mar 30 21:48:53 HTPC kernel: [  132.866530]  [unknown_bootoption+0x0/0x1e0] unknown_bootoption+0x0/0x1e0
Mar 30 21:48:53 HTPC kernel: [  132.866562]  =======================
Mar 30 21:48:53 HTPC kernel: [  132.866564] handlers:
Mar 30 21:48:53 HTPC kernel: [  132.866566] [<e089fca0>] (usb_hcd_irq+0x0/0x60 [usbcore])
Mar 30 21:48:53 HTPC kernel: [  132.866584] [<e089fca0>] (usb_hcd_irq+0x0/0x60 [usbcore])
Mar 30 21:48:53 HTPC kernel: [  132.866600] Disabling IRQ #17
Mar 30 21:48:55 HTPC kernel: [  134.421448] mt2060 I2C write failed (len=2)
Mar 30 21:48:55 HTPC kernel: [  134.421458] mt2060 I2C write failed (len=6)
Mar 30 21:48:55 HTPC kernel: [  134.421463] mt2060 I2C read failed
Mar 30 21:48:55 HTPC kernel: [  134.426794] mt2060 I2C read failed
Mar 30 21:48:55 HTPC kernel: [  134.434797] mt2060 I2C read failed
Mar 30 21:48:55 HTPC kernel: [  134.442769] mt2060 I2C read failed
Mar 30 21:48:55 HTPC kernel: [  134.450753] mt2060 I2C read failed
Mar 30 21:48:55 HTPC kernel: [  134.458738] mt2060 I2C read failed
Mar 30 21:48:55 HTPC kernel: [  134.466728] mt2060 I2C read failed
Mar 30 21:48:55 HTPC kernel: [  134.474730] mt2060 I2C read failed
Mar 30 21:48:55 HTPC kernel: [  134.482704] mt2060 I2C read failed
Mar 30 21:48:55 HTPC kernel: [  134.490684] mt2060 I2C read failed
Mar 30 21:48:55 HTPC kernel: [  134.647602] dvb-usb: could not submit URB no. 0 - get them all back
Mar 30 21:48:55 HTPC kernel: [  134.647615] dvb-usb: error while enabling fifo.
Mar 30 21:49:33 HTPC kernel: [  172.575840] dvb-usb: error while stopping stream.
Mar 30 21:49:44 HTPC kernel: [  183.433775] dvb-usb: could not submit URB no. 0 - get them all back
Mar 30 21:49:44 HTPC kernel: [  183.433790] dvb-usb: error while enabling fifo.

---

### Post by JugeHuge on 2009-03-31
Continue using 1.10 firmware..

---

### Post by utar on 2009-03-31
I have the same issue after a warm reboot with the latest v4l drivers.  However it works fine after a cold boot.  Can you try a cold boot and see if that works?

[Edit: Now read your post again and see that it works with a cold boot.  JugeHuge's suggestion would be worth a go, I know when I upgraded my drivers these wanted 1.20 so I downloaded and installed it.  Never though this could be what was causing the problems . . .]

---

### Post by oct on 2009-03-31
Yes, a cold boot always solves it, but only until the new crash. Also, I don't think it's related to the firmware, because I already had the problem with 1.10. I can give it a test, though, now that I'm using the latest v4l drivers.

What seem strange to me is that before the I2C errors, there are a couple of messages about irq17 error that finish disabling irq17. Is it possible that my disconnect problem is related to IRQ's instead of the kernel bug solved in 2.6.24-16? Here's my cat /proc/interrupts output:

           CPU0       
  0:        150   IO-APIC-edge      timer
  1:         10   IO-APIC-edge      i8042
  4:          6   IO-APIC-edge    
  6:          5   IO-APIC-edge      floppy
  7:          0   IO-APIC-edge      parport0
  8:          7   IO-APIC-edge      rtc
  9:          0   IO-APIC-fasteoi   acpi
 12:        114   IO-APIC-edge      i8042
 14:      74292   IO-APIC-edge      libata
 15:     468834   IO-APIC-edge      libata
 16:     353965   IO-APIC-fasteoi   uhci_hcd:usb1, uhci_hcd:usb4, nvidia
 17:     573881   IO-APIC-fasteoi   uhci_hcd:usb2, ehci_hcd:usb8
 18:     591316   IO-APIC-fasteoi   uhci_hcd:usb3, uhci_hcd:usb6, libata
 19:     190310   IO-APIC-fasteoi   uhci_hcd:usb5, Intel ICH5
 20:          2   IO-APIC-fasteoi   ehci_hcd:usb7
 21:       2066   IO-APIC-fasteoi   eth0
 22:      44425   IO-APIC-fasteoi   0000:02:00.0
NMI:          0   Non-maskable interrupts
LOC:    6872444   Local timer interrupts
RES:          0   Rescheduling interrupts
CAL:          0   function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
SPU:          0   Spurious interrupts
ERR:          0
MIS:          0

Searching my dmesg it seems that usb8 is the Nova-t (or at least the remote control on the Nova-T) and usb2 is the volume knob of my Antec Fusion case. Is it possible to force interupts so the Nova-T uses a different one?

Thank you

Oct

---

### Post by utar on 2009-03-31
Have you tried disabling EIT scanning on the second tuner as well as adding a delay (say 150ms) to each tuner?

---

### Post by oct on 2009-04-02
Yes, I disabled EIT scanning and put a delay on the tuning process, but nothing happened. Anyway, these problems were fixed in latest kernels + 1.20 firmware, as I read here

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500")

As I mention before, I think that with my configuration the Nova-T should be stable, so I'm worried by the previous "Disabling IRQ 17" error.

Thanks

Oct

---

### Post by rts on 2009-08-21
I am having this exact same problem with the same tuner.  I followed all the same advice.  I am running an up-to-date Mythbuntu 9.04:

...
[  112.696013] mt2060 I2C read failed
[  112.920366] dvb-usb: could not submit URB no. 0 - get them all back
[  112.920373] dvb-usb: error while enabling fifo.
[  438.296039] mt2060 I2C write failed (len=2)
[  438.296050] mt2060 I2C write failed (len=6)
[  438.296057] mt2060 I2C read failed
...

Only a cold boot brings the card back to life.

I am using the 1.20 firmware.

I had been using this card with Mythbuntu 8.10 + 1.20 firmware and upgraded v4l drivers (changeset:   11783:0018ed9bbca3) and it was very stable.  Since upgrading to 9.04 I get the above dvb message every day (or less).


Linux mythbuntu 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux

dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.

---

### Post by tonycollinet on 2009-08-30
Another one here - just to add the weight of evidence.

Every 2 or 3 days I get a lockup that only a cold restart can eliminate. Get the same i2c errors reported.

Also running 9.04, and I have updated to the latest v4l drivers (to fix a remote problem)

Everything I've read so far states that these errors have been fixed - but obviously this is a new bug, or a recurrence of the old one.

I have NOT yet tried the EIT disable, or the tuner delay - will give those a go, and report back.

---

### Post by Vitani on 2009-08-31
Same here, was all fine in Mythbuntu 8.1, but 9.04 is a no go. I've just changed by Capture Cards to open on demand to see if that works, and also disabled the EIT scan on the second tuner. I shall report back if I make any progress.

---

### Post by nasha on 2009-09-01
Hi Guys,

Just thought i'd put in my two cents worth regarding my recent I2C issues.

I was experiencing I2C errors with the Hauppauge HVR-2200, in much the same fashion  (I2C read/write errors & IRQ conflicts), except mine were permanent. I got into contact with the author of the driver (Steve Toth), and after many hours remotely logged in, he made some changes to the driver, and everything was working perfectly.

So the conclusion i would draw is a driver issue, for some reason specific to your card (as was mine. The author had never seen anything like it from the HVR-2200). Doesn't offer much help, but maybe opens an avenue to resolution.

Also i would stick with the 1.10 fw, as the 1.20 has known issues.

Cheers,
Nasha

---

### Post by rts on 2009-09-01
> **nasha said:**
> 
Also i would stick with the 1.10 fw, as the 1.20 has known issues.


1.10 had other issues for me.  Oh well.

---

### Post by a_lamaison on 2009-09-05
I don't have much to add but thought I'd post to show this problem isn't all that rare.  Same setup as most: Ubuntu 9.04, 1.20 firmware, latest v4l drivers.  EIT is disabled.  I tried it with a delay of several *thousand* milliseconds and still gave me I2C errors.

---

### Post by alrcan on 2009-09-16
Just to add I have the same problem, something is very broken in mythbuntu with these tuners.

---

### Post by akaihola on 2009-09-27
Same problem here with Mythbuntu Karmic Alpha 6.

The most convincing explanation I've seen is [here]("http://www.mail-archive.com/linux-media@vger.kernel.org/msg08331.html").

Right now I'm trying to make Karmic run with a 2.6.27-14 kernel (from Intrepid updates) which is known to behave well with this tuner card.

---

### Post by giac0m0 on 2009-10-16
> **akaihola said:**
> 
Right now I'm trying to make Karmic run with a 2.6.27-14 kernel (from Intrepid updates) which is known to behave well with this tuner card.

Hi - I'm also having exactly the same issue in London with 9.04 - could you post a quick review of how you tried to install the 2.6.27 kernel onto 9.04 and issues you had?

Thanks!

---

### Post by tobycatlin on 2009-10-30
i found this thread having had issues finding channels after a full reinstall. I reverted to 1.10 firmware and i think it has found some channels. Shame i had hoped reinstalling would fix the missed recording problems.

would it be wise to drop the nova-t 500 for something else? if so whats the most reliable card for a ubuntu mythtv combo? I bought this one because it was in the compat list

---

### Post by SiHa on 2009-10-31
I've just done clean install of 9.10, and my Nova-T 500 seems stable for the moment, no I2C errors that I can see so far (touch wood).
Probably a dumb question, did you enable the LNA? The procedure is very slightly different, now - the file is options.conf (think it was just 'options' before?.

See GUIGuy's 1st post here:

[http://ubuntuforums.org/showthread.php?t=1294067&highlight=options.conf](http://ubuntuforums.org/showthread.php?t=1294067&highlight=options.conf)

---

### Post by SiHa on 2009-11-01
Spoke to soon.
I2C errors abound.

Will try reverting to 1.10 fw later today.

---

### Post by Neon Dusk on 2009-11-01
Do these errors only appear after the system has been active for a length of time? Once they happen does it kill the card until a restart?

I've been using the Nova-T 500 since 8.04 and have never noticed a problem. The only things I may of done differently (apart from enabling the lna) is :- 

Disabling the Nova remote control
```

options dvb_usb disable_rc_polling=1

```

Disabling the active EIT scanning. On Freeview since the epg is broadcast on all Muxs as long as you're making regular recordings active EIT scanning isn't needed.

The system is also set-up for ACPIWake so it's usually switches off if it's not recording. Although it may be on for a few days at a time if I'm using it for big downloads.

---

### Post by utar on 2009-11-01
Neon Dusk - are you running 9.10?  I've thinking of upgrading my 8.04 install and threads like this one makes me think I shouldn't!



Utar

---

### Post by SiHa on 2009-11-01
> **Neon Dusk said:**
> Do these errors only appear after the system has been active for a length of time? Once they happen does it kill the card until a restart?

**I've been using the Nova-T 500 since 8.04** and have never noticed a problem. The only things I may of done differently (apart from enabling the lna) is :- 

Disabling the Nova remote control
```

options dvb_usb disable_rc_polling=1

```

Disabling the active EIT scanning. On Freeview since the epg is broadcast on all Muxs as long as you're making regular recordings active EIT scanning isn't needed.

The system is also set-up for ACPIWake so it's usually switches off if it's not recording. Although it may be on for a few days at a time if I'm using it for big downloads.

Yes, so have I, with **no** tweaks at all. AFAIK, the disable active scan thing was fixed prior to 8.04.

The one reason I have not upgraded until now, is the I2C problems that everyone reports since 8.10, (with updated V4L drivers). Unfortunately 0.22 meant I had no real alternative.

Anyway, yesterday, I got these arrors after the system had been up for about three hours, so even the daily shutdown wouldn't keep it in check.

---

### Post by Neon Dusk on 2009-11-01
> **utar said:**
> Neon Dusk - are you running 9.10?  I've thinking of upgrading my 8.04 install and threads like this one makes me think I shouldn't!


I've been running 9.10 for a couple of weeks (the beta and then I've upgraded the release version a couple of days ago)

---

### Post by Neon Dusk on 2009-11-01
@SiHa

Do you use the Nova IR receiver? If you don't have you tried disabling it?

---

### Post by utar on 2009-11-01
@SiHa

I'm not clear from reading your post if you have tried disabling eit scanning?

On 8.04 I had to disable eit scanning on one tuner and increase to tuning delay on both tuners to 150ms to stop the card from falling over.  From my experience the active scan problem was not fixed in 8.04.

It may be worth a go if rolling back to fw 1.10 doesn't work.



Utar

---

### Post by SiHa on 2009-11-01
> **utar said:**
> @SiHa

I'm not clear from reading your post if you have tried disabling eit scanning?

On 8.04 I had to disable eit scanning on one tuner and increase to tuning delay on both tuners to 150ms to stop the card from falling over.  From my experience the active scan problem was not fixed in 8.04.

It may be worth a go if rolling back to fw 1.10 doesn't work.
Utar

Sorry, I've got Active EIT enabled on one tuner, and tuning delay at 175ms, simply because that's what I had in 8.04.

If it continues to fall over after , I'll have a go at disabling the EIT altogether, then the remote, as I use a homebrew serial receiver.

@NeonDusk - Sorry, just read your last post, thanks for the suggestions about both these last points, will try them.

---

### Post by metu71 on 2009-11-10
Hi,

I had a break with my MythTV project, but a week ago I installed MythBuntu 9.10 from LiveCD. First I want to say that making system work has become much easier, no exhausting hacking here and there, thanks to everyone involved for that.

I installed the system on VIA EPIA ML-5000 (if I remember it correctly), 1GB of RAM is enough (it runs also with 512MB, but uses swap a lot). I have Hauppauge Nova-t 500 PCI in the system.

I could see problems from the very first moment after finishing configuration. I2C errors with mt2060 came in few hours after restart. When this happened, I lost both tuners and restart was needed. Restarting mythtv-backend did not help. MythTV frontend is showing status "Partial Lock" and no video can be seen.

Firmware used for the DVB-T card is 1.20 and kernel has not been modified by myself. Now I cannot remember if it has been updated by update_manager.

I tried set options for the LNA, rc_polling and disabled EIT scanning. This helps for the problem.
First I had it running for 6 hours without problems with previous settings and then I tried enabling EIT scan for one of the tuners with 500ms delay. After that it didn't take half an hour until the problem came again.
Then I disabled EIT scan again and problem disappeared.

I can live with the workaround, but it is annoying not to have free hands with the features...;)

---

### Post by SiHa on 2009-11-10
For me, the 1.10 fw did the trick...

---

### Post by giac0m0 on 2009-11-10
> **metu71 said:**
> Hi,

Firmware used for the DVB-T card is 1.20 and kernel has not been modified by myself. Now I cannot remember if it has been updated by update_manager.

I tried set options for the LNA, rc_polling and disabled EIT scanning. This helps for the problem.  First I had it running for 6 hours without problems with previous settings and then I tried enabling EIT scan for one of the tuners with 500ms delay. After that it didn't take half an hour until the problem came again.

Then I disabled EIT scan again and problem disappeared.


Hi there, 

I've been having similar problems and it was driving me crazy. The usual culprits of the MT errors in the logs are:

[LIST]
[*]Bad signal
[*]Not including the LNA and rc_polling in the config for kernal extensions
[*]The backend putting in multiple card entries (possible bug)
[*]EIT scanning set with a too low tuning delay
[/LIST]
I'm using 9.04 with the latest updates to the kernel.  I was following this bug on the kernel:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/397696](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/397696)

but following the points below my EIT issues dissapeared which makes me think my problem was multiple card entries in my database.

I had bad signal and replaced the cabling to my antenna, using a signal strength meter to prove to myself there was no issue!

I added the kernel commands to for the Low Noise amplification and the rc_polling for the remote to "dvb-usb-dib0700.conf"

Using PhpMyAdmin I went into the card table of the database and deleted all the cards stored there.  I noticed that there was an extra row (three, instead of the two on-board tuner cards).  You could use the setup options to delete all capture cards on the host and all cards.  I again used PhpMyAdmin to check the correct number of cards were entered.

I did a cold reboot to reload the 1.20 firmware and checked everything was okay with: 

```
dmesg | grep -i dvb
```Then I added both cards and disabled the EIT scanning from both.  I enabled the EIT listings source and did a scan for channels.

Then I enabled a single tuners EIT with a 1000ms delay and watched the EIT data populate the mythweb.

---

### Post by metu71 on 2009-11-10
I checked tuner list. There were 8 card, probably because i have set maximum number of recordings as 4 for both tuners.
I removed capture cards from MythTV setup and noticed in phpmyadmin that all cards were removed. Then I recreated capture cards with mythtv setup and phpmyadmin showed same 8 cards in database.
I had all the settings for the cards as previously, but now I enabled active EIT scan for one of the tuners and set 1000ms delay for that. Active EIT scan was disabled for the other tuner and delay was left value 0.

Now the system has been running without problems for 8 hours. I don't know what seems to have fixed it. Was it the extra long delay (500ms -> 1000ms) or re-creating capture cards. I'll try to find the time for studying this more, but now I feel that I need to wait and see how long problems stay away.

Thank you guys for support. BTW, phpmyadmin is excellent tool!

---

### Post by watkin5 on 2009-11-15
I have the same problem ...```
[   29.755956] usbcore: deregistering interface driver dvb_usb_dib0700
[   29.766379] dib0700: loaded with support for 9 different device-types
[   29.767916] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
[   29.767929] usb 2-1: firmware: requesting dvb-usb-dib0700-1.20.fw
[   29.792897] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[   30.441144] dib0700: firmware started successfully.
[   30.928488] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   30.948049] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   30.948124] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   30.948709] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   31.070137] DVB: registering adapter 0 frontend 0 (DiBcom 3000MC/P)...
[   31.210661] MT2060: successfully identified (IF1 = 1229)
[   31.720749] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   31.721087] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   31.727700] DVB: registering adapter 1 frontend 0 (DiBcom 3000MC/P)...
[   31.749378] MT2060: successfully identified (IF1 = 1217)
[   32.329418] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[   32.329769] usbcore: registered new interface driver dvb_usb_dib0700

...

[ 1742.604242] dvb-usb: error while enabling fifo.
[ 1767.668192] dvb-usb: error while stopping stream.

```

I have a completely fresh install of mythtv on karmic. I have disabled active EIT on both tuners and set a delay of 175 ms. I'm using the default 1.20 firmware.

I can trigger the problem at any time, by going to the program guide and setting two programs, on different multiplexes, to record now. At best I'll get 10 seconds before I see the fifo error. I don't get a problem when using only one of the tuners.

I've had the same problem on Intrepid, and Jaunty.

---

### Post by giac0m0 on 2009-11-15
Looks like your irq error is unrelated:

[http://bugzilla.kernel.org/show_bug.cgi?id=11398](http://bugzilla.kernel.org/show_bug.cgi?id=11398)

Have you tried two seperate tuning delays?  I have mine set to 500ms and 1000ms each.  Have you set the maximum recordings for each card to 1 and checked the database to see if more then two cards are there?

---

### Post by watkin5 on 2009-11-15
> **giac0m0 said:**
> 
Have you tried two seperate tuning delays?  I have mine set to 500ms and 1000ms each.  Have you set the maximum recordings for each card to 1 and checked the database to see if more then two cards are there?
I have only two cards listed in mythconverg, it is set for only one recording per card. I'll try your tuning delays next chance I get.

Thanks, Rob

---

### Post by anton610 on 2009-11-17
Hello, I've the same problem with the nova-t 500
 
are there any news for a workaround?
 
Thanks Anton

---

### Post by Al_Vampyre on 2009-11-17
I have 2 Nova T 500's in my frontend, running 9.10 and 1.20fw, I have the usbcore suspend, disable rc polling, and lna activated in my conf. I have also set one tuner on each card to Active EIT scan and set a tuning delay on all four tuners.

Belet and braces approach seems to be working!

---

### Post by anton610 on 2009-11-18
Hello,

how do i suspend the usbcore,

and how do i enable on one tuner the eit, do i have to make two videosources?

thank you very much!

Regard Anton

---

### Post by Al_Vampyre on 2009-11-18
> **anton610 said:**
> Hello,

how do i suspend the usbcore,

and how do i enable on one tuner the eit, do i have to make two videosources?

thank you very much!

Regard Anton

I have 3 lines in my /etc/modprobe.d/options.conf

options dvb-usb-dib0700 force_lna_activation=1 
*(forces the LNA on the card)*
options usbcore autosuspend=-1
*(prevents the usb on the card going into suspend)*
options dvb_usb disable_rc_polling=1
*(stops the card polling for remote input - do not use if your using the remote that came with the card - I use a seperate MCE remote)*

You can add these in by using **sudo mousepad /etc/modprobe.d/options.conf**

The card options are in the backend setup

Each card sets up with two tuners, I have enabled the check box 'Use card for Active EIT scan' on the first tuner but not on the second.

In Recording options set the tuning delay to 150ms for each tuner.

Hope that helps!

---

### Post by anton610 on 2009-11-19
hello,

thank you very much!!

i think it helps!

regards

---

### Post by tobycatlin on 2009-12-04
I am running a single nova-t 500 on Ubuntu 9.10 Karmic Koala
I am using the 1.20fw firmware
I have disabled eit on both cards and added a 500ms delay to one and 1000ms to the other
I have disabled the remote and usbcore
I have enabled the lna

My card tuned and worked for a bit then the old  mt2060 I2C read failed and won't work again until i do a cold boot. 

Any other ideas on what i can do?

thanks in advance

---

### Post by utar on 2009-12-04
The nova seems to be a awkward card, for some people it works great, for other people it doesn't.

I have read posts that some people have more luck with 1.1fw, perhaps you could give that a go.


Utar

---

### Post by watkin5 on 2009-12-04
> **tobycatlin said:**
> I am running a single nova-t 500 on Ubuntu 9.10 Karmic Koala
I am using the 1.20fw firmware
I have disabled eit on both cards and added a 500ms delay to one and 1000ms to the other
I have disabled the remote and usbcore
I have enabled the lna

My card tuned and worked for a bit then the old  mt2060 I2C read failed and won't work again until i do a cold boot. 

Any other ideas on what i can do?

thanks in advance

You're not alone. I think there are a few of use with poor quality Nova T cards from Hauppauge.

If I set both tuners to start recording I immediately get a 
dvb-usb: error while enabling fifo 

I have to disable a tuner to avoid this problem.

I plan to wait for a HD DVB tuner to become available as an excuse to ditch the Nova T.

---

### Post by bh@magentaretail.com.au on 2009-12-04
I'm running 9.04 with a Hauppauge TD-500 card.  By disabling EIT on the second tuner, setting the DVB tuning delay to 150ms on tuner with EIT enabled, and 0 on the tuner with EIT disabled, the card seems to be absolutely reliable.

But!  I get recording conflicts when trying to record two overlapping shows via the program guide, even though with two tuners this should be possible.  If I schedule one show manually then it works.  I'm GUESSING this is because the second tuner has no program guide information and therefore cannot record shows by program guide???

I've tried setting cross source EIT in backend general settings, but this doesn't seem to have helped.  

Is there a solution to this??

Is it possible to view the program guide information by tuner - this would prove (or disprove) my theory??

Thanks!

---

### Post by watkin5 on 2009-12-04
Have you give both tuners the same priority?

---

### Post by bh@magentaretail.com.au on 2009-12-04
Yes:  Under input connections, both inputs have "input priority" of 0.

---

### Post by SiHa on 2009-12-05
This is one of my biggest bugbears with Myth. It doesn't seem to be intelligent enough to use different tuners for overlapping recordings. You can force it to use a specific tuner in the schedule options of the recording setup, so you can set the overlapping recordings to use different tuners.

It's not exactly a pretty solution, but it works.

---

