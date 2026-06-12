---
title: "Microsoft VX-1000 Webcam/Mic"
date: 2010-06-23
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kyleabaker on 2010-06-23
When I first installed Ubuntu 10.10 to test, my VX-1000 webcam and microphone were both working (finally), but now the microphone is not working again.

Is anyone else having similar problems? I've tried getting the mic to work again, but I'm unsure of what to do or where to look. The mic never once worked for me in other versions of Ubuntu, so I'm hopeful that it will be working with Ubuntu 10.10...finally.

Any helpful ideas?

---

### Post by kyleabaker on 2010-07-04
Any tips on what to look for or change?

I just tested again and here are my results (in order of testing):

1. Tested "Sound Recorder" and webcam mic worked properly.
2. Tested "Cheese Webcam Booth" and video worked while microphone did not.
3. Tested "Sound Recorder" again and mic didn't work.

Any idea what would cause this to happen?

---

### Post by aviramof on 2010-07-04
I too have the same webcam in lucid the microphone didn't worked but here it does work for me even now so it's not an update or anything check maybe is set on mute try installing gnome-alsa-mixer and check there or just reinstall maverick.

---

### Post by kyleabaker on 2010-07-04
> **aviramof said:**
> I too have the same webcam in lucid the microphone didn't worked but here it does work for me even now so it's not an update or anything check maybe is set on mute try installing gnome-alsa-mixer and check there or just reinstall maverick.

I wonder if this could be another 32-bit/64-bit anomaly. I know there have been issues with this webcam on 64-bit versions of Ubuntu and that is what I'm testing in. Which are you using?

Also, I've installed gnome-alsamixer and am still wandering through the settings and controls. There is a Mic control that was set to Mute and Rec, but I unmuted it and still couldn't hear any sound from it.

This is what gnome-alsamixer looked like before changing any settings:


Is there another control that I should look for to find the mic that is attached to the webcam?

---

### Post by ranch hand on 2010-07-04
You better take a look at the check boxes at the bottom right.  There are switches there for mics.  They may not help but the unmuting will do no good with out the right switches selected.

---

### Post by aviramof on 2010-07-05
> **kyleabaker said:**
> I wonder if this could be another 32-bit/64-bit anomaly. I know there have been issues with this webcam on 64-bit versions of Ubuntu and that is what I'm testing in. Which are you using?

I am using the 32 bit version my computer only have 2GB of memory with no option to expend it so despite the fact that my processor is 64 bit i choose to use the 32 bit version 
of all the operating system that i use and in most cases it's also more stable then 64 bit operating system as you can see in your own case.

64 bit is the future yes but i think it would take a few more years before it would fully be able to replace the 32 bit version development wise that is.

---

### Post by kyleabaker on 2010-07-05
> **ranch hand said:**
> You better take a look at the check boxes at the bottom right.  There are switches there for mics.  They may not help but the unmuting will do no good with out the right switches selected.

Most of those give errors like this in the terminal window, so afaik they are useless for me.
> ** (gnome-alsamixer:13953): WARNING **: gam_toggle_set_state (). No idea what to do for mixer element "Channel Mode"!

** (gnome-alsamixer:13953): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Channel Mode"!

The ones that don't give errors (that are not already checked in the screenshot) are Mic Boost (+20dB), Mic Front Input, Mix, Mix Mono and Duplicate Front.

Since this mic will be coming through webcam I don't think Mic Front Input or Duplicate Front are related to the problem, but I could easily be wrong.

Testing the mic out after changing these settings and I'm still getting no sound through the Mic.

---

### Post by kyleabaker on 2010-07-05
Another thing, The GNOME ALSA Mixer shows those two tabs, Realtek ALC850 rev 0 and USB Mixer. The Realtek tab is the audio stuff built into my motherboard afaik. I can't tell what the USB Mixer is for cause it doesn't seem to have any video settings like a webcam would have.


I saw a post a long time ago that detailed how to check the sound settings directly from the terminal for this device. It didn't solve anything then, but maybe it will help now if I can dig it back up...

---

### Post by kyleabaker on 2010-07-05
I've unplugged my webcam and reattached it to verify that it is reset and works again without restarting the entire computer. It does work again.

This time, I watched updates in the System Log Viewer and this is what the output was:
> Jul  5 16:49:52 kyleabaker-desktop kernel: [104818.122525] usb 2-1: new full speed USB device using ohci_hcd and address 5
Jul  5 16:49:53 kyleabaker-desktop kernel: [104818.349087] gspca: probing 045e:00f7
Jul  5 16:49:53 kyleabaker-desktop kernel: [104818.361046] sonixj: Sonix chip id: 11
Jul  5 16:49:53 kyleabaker-desktop kernel: [104818.367105] input: sonixj as /devices/pci0000:00/0000:00:02.0/usb2/2-1/input/input5
Jul  5 16:49:53 kyleabaker-desktop kernel: [104818.367172] gspca: video0 created
Jul  5 16:49:53 kyleabaker-desktop kernel: [104818.367174] gspca: found int in endpoint: 0x83, buffer_len=1, interval=100
Jul  5 16:49:53 kyleabaker-desktop kernel: [104818.367235] gspca: probing 045e:00f7
Jul  5 16:53:35 kyleabaker-desktop kernel: [105040.981955] gspca: found int in endpoint: 0x83, buffer_len=1, interval=100
Jul  5 16:53:37 kyleabaker-desktop kernel: [105042.537923] ohci_hcd 0000:00:02.0: leak ed ffff88003796e370 (#81) state 2
Jul  5 16:53:37 kyleabaker-desktop kernel: [105042.537957] gspca: found int in endpoint: 0x83, buffer_len=1, interval=100
Jul  5 16:53:37 kyleabaker-desktop kernel: [105042.537960] gspca: bandwidth not wide enough - trying again
Jul  5 16:53:37 kyleabaker-desktop kernel: [105042.564943] gspca: found int in endpoint: 0x83, buffer_len=1, interval=100
Jul  5 16:54:08 kyleabaker-desktop kernel: [105073.800352] gspca: found int in endpoint: 0x83, buffer_len=1, interval=100

Notice there are two events in that log. The one that is at 16:49 is reattaching the webcam. I checked with sound recorder and it is working great initially.

The second one, at 16:53, is when I open Cheese to test audio and video together. So something here is breaking the mic until the usb device is removed and reattached.

Does anyone know what this gspca output means or how I might fix it?

---

### Post by kyleabaker on 2010-07-07
I've been communicating with, Jean-François Moine <http://moinejf.free.fr>, who is currently the maintainer of this driver. Here is some information I've gathered so far..

> The problem is known. I have no fix yet, ...

> The video and audio don't work at the same time because the video is
opened before the audio and it takes all the USB bandwidth.

The problem is in the main gspca.c, not in sonixj.c. It may fixed using
a lower alternate setting. To check it, you may add the following lines:

       if (dev->config->desc.bNumInterfaces != 1)
               gspca_dev->nbalt -= 1;
after
       gspca_dev->nbalt = intf->num_altsetting;
in the function gspca_dev_probe() of gspca.c.

If it still does not work, change "-= 1" to "-= 2" or "-= 3" (there are
8 alternate settings in your webcam).

For a correct fix, the exact video bandwidth shall be calculated and I
could not find yet time enough to do the job and people to test it...

If anyone wants to take a stab at this, you just need to download the latest v4l-dvb from here:
[http://linuxtv.org/hg/v4l-dvb/archive/tip.zip](http://linuxtv.org/hg/v4l-dvb/archive/tip.zip)

...make the changes he specified above and compile.

The file that needs to be edited can be found (after extracting the zip) at:
v4l-dvb-*/linux/drivers/media/video/gspca/gspca.c

I'm unable to get this to compile, with an Error 2 stopping the make script. If anyone else has success let me know what you may have done differently!

If we can get this working then I'm sure we can get the patch pushed in soon so everything works by default.

EDIT:
You can actually get the GSPCA drivers only and compile those from:
[http://linuxtv.org/hg/~hgoede/gspca/archive/tip.zip](http://linuxtv.org/hg/~hgoede/gspca/archive/tip.zip)

---

### Post by Ron_ on 2010-07-07
My (64bit Karmic) system log is telling me something different:

Jul  6 10:34:25 home-ubuntu kernel: [   26.325632] Linux video capture interface: v2.00
Jul  6 10:34:25 home-ubuntu kernel: [   26.378774] gspca: main v2.6.0 registered
Jul  6 10:34:25 home-ubuntu kernel: [   26.392592] gspca: probing 045e:00f7
Jul  6 10:34:25 home-ubuntu kernel: [   26.403544] sonixj: Sonix chip id: 11
Jul  6 10:34:25 home-ubuntu kernel: [   26.410349] gspca: probe ok
Jul  6 10:34:25 home-ubuntu kernel: [   26.410359] gspca: probing 045e:00f7
Jul  6 10:34:25 home-ubuntu kernel: [   26.410368] gspca: probing 045e:00f7
Jul  6 10:34:25 home-ubuntu kernel: [   26.410384] usbcore: registered new interface driver sonixj
Jul  6 10:34:25 home-ubuntu kernel: [   26.410386] sonixj: registered

Bandwidth seems not to be a symptom, so I did not try to edit gspca.c.  Still no mic.

btw... I notice that new ALSA drivers for 2.6.31, 2.6.34, 2.6.35 have failed to build for months.  See [https://launchpad.net/~ubuntu-audio-dev/+archive/ppa]("https://launchpad.net/%7Eubuntu-audio-dev/+archive/ppa") .  I held out hope that the fix might be there.

---

### Post by kyleabaker on 2010-07-07
> **Ron_ said:**
> Bandwidth seems not to be a symptom, so I did not try to edit gspca.c.  Still no mic.

btw... I notice that new ALSA drivers for 2.6.31, 2.6.34, 2.6.35 have failed to build for weeks.  See [https://launchpad.net/~ubuntu-audio-dev/+archive/ppa]("https://launchpad.net/%7Eubuntu-audio-dev/+archive/ppa") .  I held out hope that the fix might be there.

Does your mic work at all? Mine works with sound recorder if I've not opened Cheese to activate the webcam yet. After I start Cheese, the mic stops working.

Try rebooting **or** running these command, then testing sound recorder (make sure the usb mic is selected in sound preferences):
```
sudo rmmod gspca_sonixj
sudo modprobe gspca_sonixj
```

---

### Post by Ron_ on 2010-07-07
VX-1000 mic has never worked since the day I plugged it in.  I usually start with Gnome Sound Recorder.  Failing that, I often try Skype and Cheese.

Following your advice (*i.e.* 2 commands), I just produced the first sound I have ever obtained from Gnome Sound Recorder.  Many thanks.  What does this mean?

---

### Post by kyleabaker on 2010-07-07
> **Ron_ said:**
> VX-1000 mic has never worked since the day I plugged it in.  I usually start with Gnome Sound Recorder.  Failing that, I often try Skype and Cheese.

Following your advice (*i.e.* 2 commands), I just produced the first sound I have ever obtained from Gnome Sound Recorder.  Many thanks.  What does this mean?

This just restarts the drivers for your webcam, so its like rebooting and trying sound recorder first.

Unplug your camera, then plug it back in (make sure to select mic in sound preferences again). Now open Cheese, then open a terminal and type "dmesg | tail" with no quotes. Paste the output here. I'm curious to see what Cheese actually causes to happen.

---

### Post by Ron_ on 2010-07-07
Okay.  Just to confirm: starting the camera (in Cheese or Skype) kills the mic every time.

I've discovered that the results of {rmmod, modprobe} are not always reproduceable.  I rebooted and tried recording.  No mic (as expected.)  Issued 2 commands.  No mic.  Fiddled with Cheese, Audacious, Alsa Mixer, Sound Prefs.... After much effort, finally got the mic back.  Not sure what did it.  {rmmod, modprobe} seems to work only following some other condition.

Here is the result of your most recent suggestion.  With all the other variables, I wanted to try it immediately after getting the mic to work, so I did not unplug it.   I launched Cheese immediately after listening to the playback from Gnome Sound Recorder.
[ 5774.111132] sonixj: deregistered
[ 5776.923083] gspca: probing 045e:00f7
[ 5776.933840] sonixj: Sonix chip id: 11
[ 5776.939917] gspca: probe ok
[ 5776.939947] usbcore: registered new interface driver sonixj
[ 5776.939952] sonixj: registered
[ 6029.359110] gspca: usb_submit_urb [0] err -28
[ 6029.383165] ohci_hcd 0000:00:02.0: leak ed ffff8800b1d7a320 (#81) state 2
[ 6033.669931] gspca: usb_submit_urb [0] err -28
[ 6033.692988] ohci_hcd 0000:00:02.0: leak ed ffff8800b1d7a370 (#81) state 2
Is this helpful at all?

---

### Post by kyleabaker on 2010-07-07
Yes. I've seen this one in mine:
> ohci_hcd 0000:00:02.0: leak ed ffff8800b1d7a320 (#81) state 2

But the usb_submit_urb is new to me:
> gspca: usb_submit_urb [0] err -28

I never seem to get a probe ok message, not sure why not, but the camera works fine and the mic works until the camera is initialized.

---

### Post by Ron_ on 2010-07-07
Following up, I unplugged the Webcam and replugged it in.
In Sound Prefs, selected the device.
Tried Sound Recorder.  No mic.
{rmmod, modprobe}
Tried Sound Recorder.  Mic worked.
Cheese
dmesg .... Same as before.
[ 8415.992122] sonixj: deregistered
[ 8420.601619] gspca: probing 045e:00f7
[ 8420.612238] sonixj: Sonix chip id: 11
[ 8420.618306] gspca: probe ok
[ 8420.618334] usbcore: registered new interface driver sonixj
[ 8420.618338] sonixj: registered
[ 8458.808548] gspca: usb_submit_urb [0] err -28
[ 8458.832604] ohci_hcd 0000:00:02.0: leak ed ffff8800b1d7a3c0 (#81) state 2
[ 8463.198393] gspca: usb_submit_urb [0] err -28
[ 8463.222443] ohci_hcd 0000:00:02.0: leak ed ffff8800b1d7a410 (#81) state 2

Thanks for the help.

btw... I just confirmed the following driver behavior.  Unless you unplug/replug, the mic is unresponsive to all commands except the following sequence:
cheese
sudo rmmod gspca_sonixj
sudo modprobe gspca_sonixj

That is, starting the camera is a necessary step, even though it apparently breaks the audio driver.  Only then can sonixj be fixed.

---

### Post by kyleabaker on 2010-07-08
Jean-Francois sent me a reply suggesting I test the Webcam GSPCA drivers from his website and they are smaller and easier to install and test.
[http://moinejf.free.fr/](http://moinejf.free.fr/)

Here are my results from testing his suggested changes (what I sent through the mailing list). Warning, this is long but useful for narrowing down the issue.

```
Okay, now I've exhausted the quick fixes that you've suggested and
have come to a new conclusion.

Without modifying the value in "gspca_dev->nbalt" the drivers will
report "bandwidth not wide enough - trying again". Modifying this
value to subtract between 1 and 8 seems to eliminate this bandwidth
error.

However, the results ultimately stay the same as before where there is
video and no audio for decreasing "gspca_dev->nbalt" from 0-5.

Video input stops working after decreasing by 6-8 while still breaking
the audio input, except for decreasing  by 8 where the video breaks
and audio remains...due to a "no transfer endpoint found" message.

My conclusion, reducing "gspca_dev->nbalt" by values 1-5 apparently
fix the bandwidth issue and don't alter the video input. However, they
also do not correct the issue where the microphone breaks and becomes
disabled.

Below is a log that I kept of each test, compiling the changes,
rebooting, testing and recording, then repeating for each decrement.

-------------------------------------

gspca_dev->nbalt -= 0; /* or same as no change */

	Initial startup (audio works)
		$ dmesg | grep "gspca"
		[   21.268018] gspca: main v2.9.0 registered
		[   21.268850] gspca-2.9.50: probing 045e:00f7
		[   21.285392] gspca-2.9.50: video0 created
		[   21.285395] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100
		[   21.285413] gspca-2.9.50: 045e:00f7 bad interface 1
		[   21.285419] gspca-2.9.50: 045e:00f7 bad interface 2

	Started Cheese (video works, no audio)
		$ dmesg | grep "gspca"
		[   21.268018] gspca: main v2.9.0 registered
		[   21.268850] gspca-2.9.50: probing 045e:00f7
		[   21.285392] gspca-2.9.50: video0 created
		[   21.285395] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100
		[   21.285413] gspca-2.9.50: 045e:00f7 bad interface 1
		[   21.285419] gspca-2.9.50: 045e:00f7 bad interface 2
		[  158.861671] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100
		[  160.405694] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100
		[  160.405698] gspca-2.9.50: bandwidth not wide enough - trying again
		[  160.434684] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100
		[  175.635876] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100

gspca_dev->nbalt -= 1;

	Initial startup (audio works)
		$ dmesg | grep "gspca"
		[   21.905722] gspca: main v2.9.0 registered
		[   21.915236] gspca-2.9.50: probing 045e:00f7
		[   21.931505] gspca-2.9.50: video0 created
		[   21.931508] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100
		[   21.931528] gspca-2.9.50: 045e:00f7 bad interface 1
		[   21.931536] gspca-2.9.50: 045e:00f7 bad interface 2

	Started Cheese (video works, no audio)
		$ dmesg | grep "gspca"
		[   21.905722] gspca: main v2.9.0 registered
		[   21.915236] gspca-2.9.50: probing 045e:00f7
		[   21.931505] gspca-2.9.50: video0 created
		[   21.931508] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100
		[   21.931528] gspca-2.9.50: 045e:00f7 bad interface 1
		[   21.931536] gspca-2.9.50: 045e:00f7 bad interface 2
		[  188.170963] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100
		[  188.170963] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100

gspca_dev->nbalt -= 2;

	Initial startup (audio works)
		$ dmesg | grep "gspca"
		[   22.463556] gspca: main v2.9.0 registered
		[   22.466506] gspca-2.9.50: probing 045e:00f7
		[   22.483436] gspca-2.9.50: video0 created
		[   22.483438] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100
		[   22.483458] gspca-2.9.50: 045e:00f7 bad interface 1
		[   22.483465] gspca-2.9.50: 045e:00f7 bad interface 2

	Started Cheese (video works, no audio)
		$ dmesg | grep "gspca"
		[   22.463556] gspca: main v2.9.0 registered
		[   22.466506] gspca-2.9.50: probing 045e:00f7
		[   22.483436] gspca-2.9.50: video0 created
		[   22.483438] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100
		[   22.483458] gspca-2.9.50: 045e:00f7 bad interface 1
		[   22.483465] gspca-2.9.50: 045e:00f7 bad interface 2
		[  139.718647] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100
		[  147.487578] gspca-2.9.50: frame overflow 234239 > 233472
		[  158.147090] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100

gspca_dev->nbalt -= 3;

	Initial startup (audio works)
		$ dmesg | grep "gspca"
		[   21.295529] gspca: main v2.9.0 registered
		[   21.296266] gspca-2.9.50: probing 045e:00f7
		[   21.321505] gspca-2.9.50: video0 created
		[   21.321508] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100
		[   21.321528] gspca-2.9.50: 045e:00f7 bad interface 1
		[   21.321536] gspca-2.9.50: 045e:00f7 bad interface 2

	Started Cheese (video works, no audio)
		$ dmesg | grep "gspca"
		[   21.295529] gspca: main v2.9.0 registered
		[   21.296266] gspca-2.9.50: probing 045e:00f7
		[   21.321505] gspca-2.9.50: video0 created
		[   21.321508] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100
		[   21.321528] gspca-2.9.50: 045e:00f7 bad interface 1
		[   21.321536] gspca-2.9.50: 045e:00f7 bad interface 2
		[  130.140725] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100
		[  138.444830] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100

gspca_dev->nbalt -= 4;

	Initial startup (audio works)
		$ dmesg | grep "gspca"
		[   21.775525] gspca: main v2.9.0 registered
		[   21.776456] gspca-2.9.50: probing 045e:00f7
		[   21.793435] gspca-2.9.50: video0 created
		[   21.793438] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100
		[   21.793455] gspca-2.9.50: 045e:00f7 bad interface 1
		[   21.793463] gspca-2.9.50: 045e:00f7 bad interface 2

	Started Cheese (video works, no audio)
		$ dmesg | grep "gspca"
		[   21.775525] gspca: main v2.9.0 registered
		[   21.776456] gspca-2.9.50: probing 045e:00f7
		[   21.793435] gspca-2.9.50: video0 created
		[   21.793438] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100
		[   21.793455] gspca-2.9.50: 045e:00f7 bad interface 1
		[   21.793463] gspca-2.9.50: 045e:00f7 bad interface 2
		[  102.566613] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100
		[  107.669128] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100

gspca_dev->nbalt -= 5;

	Initial startup (audio works)
		$ dmesg | grep "gspca"
		[   21.150636] gspca: main v2.9.0 registered
		[   21.151538] gspca-2.9.50: probing 045e:00f7
		[   21.174690] gspca-2.9.50: video0 created
		[   21.174692] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100
		[   21.174710] gspca-2.9.50: 045e:00f7 bad interface 1
		[   21.174717] gspca-2.9.50: 045e:00f7 bad interface 2

	Started Cheese (video works, no audio)
		$ dmesg | grep "gspca"
		[   21.150636] gspca: main v2.9.0 registered
		[   21.151538] gspca-2.9.50: probing 045e:00f7
		[   21.174690] gspca-2.9.50: video0 created
		[   21.174692] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100
		[   21.174710] gspca-2.9.50: 045e:00f7 bad interface 1
		[   21.174717] gspca-2.9.50: 045e:00f7 bad interface 2
		[  103.857992] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100
		[  108.318804] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100

gspca_dev->nbalt -= 6;

	Initial startup (audio works)
		$ dmesg | grep "gspca"
		[   21.719670] gspca: main v2.9.0 registered
		[   21.720735] gspca-2.9.50: probing 045e:00f7
		[   21.741407] gspca-2.9.50: video0 created
		[   21.741409] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100
		[   21.741425] gspca-2.9.50: 045e:00f7 bad interface 1
		[   21.741433] gspca-2.9.50: 045e:00f7 bad interface 2

	Started Cheese (no video, no audio)
		$ dmesg | grep "gspca"
		[   21.719670] gspca: main v2.9.0 registered
		[   21.720735] gspca-2.9.50: probing 045e:00f7
		[   21.741407] gspca-2.9.50: video0 created
		[   21.741409] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100
		[   21.741425] gspca-2.9.50: 045e:00f7 bad interface 1
		[   21.741433] gspca-2.9.50: 045e:00f7 bad interface 2
		[   86.749179] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100
		[   98.646330] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100

gspca_dev->nbalt -= 7;

	Initial startup (audio works)
		$ dmesg | grep "gspca"
		[   21.911549] gspca: main v2.9.0 registered
		[   21.912648] gspca-2.9.50: probing 045e:00f7
		[   21.934429] gspca-2.9.50: video0 created
		[   21.934431] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100
		[   21.934452] gspca-2.9.50: 045e:00f7 bad interface 1
		[   21.934460] gspca-2.9.50: 045e:00f7 bad interface 2

	Started Cheese (no video, no audio)
		$ dmesg | grep "gspca"
		[   21.911549] gspca: main v2.9.0 registered
		[   21.912648] gspca-2.9.50: probing 045e:00f7
		[   21.934429] gspca-2.9.50: video0 created
		[   21.934431] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100
		[   21.934452] gspca-2.9.50: 045e:00f7 bad interface 1
		[   21.934460] gspca-2.9.50: 045e:00f7 bad interface 2
		[  108.513126] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100
		[  121.592828] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100

gspca_dev->nbalt -= 8;

	Initial startup (audio works)
		$ dmesg | grep "gspca"
		[   21.215610] gspca: main v2.9.0 registered
		[   21.217198] gspca-2.9.50: probing 045e:00f7
		[   21.233435] gspca-2.9.50: video0 created
		[   21.233437] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100
		[   21.233459] gspca-2.9.50: 045e:00f7 bad interface 1
		[   21.233467] gspca-2.9.50: 045e:00f7 bad interface 2

	Started Cheese (no video, audio works)
		$ dmesg | grep "gspca"
		[   21.215610] gspca: main v2.9.0 registered
		[   21.217198] gspca-2.9.50: probing 045e:00f7
		[   21.233435] gspca-2.9.50: video0 created
		[   21.233437] gspca-2.9.50: found int in endpoint: 0x83, buffer_len=1, interval=100
		[   21.233459] gspca-2.9.50: 045e:00f7 bad interface 1
		[   21.233467] gspca-2.9.50: 045e:00f7 bad interface 2
		[   85.830434] gspca: no transfer endpoint found

-------------------------------------

The point of breaking the microphone appears to be at the same
instance that the second "found int in endpoint: 0x83, buffer_len=1,
interval=100" occurs. This is in the alloc_and_submit_int_urb()
function in gspca.c.
```

I'd like to find a way to run a trace on alloc_and_submit_int_urb() to see why I'm getting these "found int in endpoint: 0x83, buffer_len=1,
interval=100" errors.

@Ron_
Your error "gspca: usb_submit_urb [0] err -28" occurs only ~4 code lines before the bandwidth error that I was getting in the function called "gspca_init_transfer" (file: gspca.c), so they may be related.

The microphone breakage is likely initiated in this function...

---

### Post by kyleabaker on 2010-07-09
> **Ron_ said:**
> Jul  6 10:34:25 home-ubuntu kernel: [   26.378774] gspca: main v2.6.0 registered
It looks like you're using a much older version right now and I think most of the output such as the bandwidth output messages are fairly new in order to help debug.

I'm starting to familiarize myself a little with the code and how it works, but still haven't made any breakthroughs. I'm hoping Jean-Francois will be able to figure out how to fix this mic error soon, cause its been driving me crazy for a year now.

Another thing I noticed is that when you first start the camera, if you watch the Input level meter in Sound Preferences, the mic appears to get a strong input just before its disabled. I'm not sure why.

---

### Post by kyleabaker on 2010-07-12
We have found the problem and I've put a patch together. If everyone experiencing the problem with the microphone can test this, please do. I'd like to know if this works with VX-1000 and VX-3000 webcams (not sure if the VX-3000 had mic issues, but if it does try this patch).

[LIST=1]
[*]Download my patched GSPCA: [gspca-2.9.51-vx1000-patch-20100712.zip](http://www.kyleabaker.com/downloads/ubuntu/gspca/gspca-2.9.51-vx1000-patch-20100712.zip)

[*]Extract the zip file on your Desktop (so you have the folder “gspca-2.9.51-vx1000-patch-20100712&#8243;).
[*]Open a terminal window and enter the following commands:
cd Desktop/gspca-2.9.51-vx1000-patch-20100712/
make
sudo make install
[*]Reboot your computer and test your webcam in an application such as Cheese (which can easily be found in the Ubuntu Software Center).
[/LIST]

Make sure that when you start your webcam in Cheese that the microphone continues to work. You can verify this in the Sound Preferences window if you click on the Input tab (make sure you have selected “LifeCam VX-1000&#8243;  as your input device).

You can find more [details explaining this patch]("http://kyleabaker.com/2010/07/12/microsoft-lifecam-vx-1000-linux-gspca-patch/") in my blog if you'd like, but please post results here.

---

### Post by Ron_ on 2010-07-12
Kyle,

You did it, buddy!  I got voice and picture for the first time in Skype.  Gnome Sound Recorder also worked.  You da' man!

For whatever reason, I had to tinker around a bit at first.  Had to fix input volume.  Also ran {rmmod, modprobe}, though I'm not sure I had to.

I will continue to exercise the system for a few days.  I'll let you know if any dubious behaviors emerge.

Many thanks.  (Any chance you'd like to help get my linmodem or my DVD burner working? ([http://swiss.ubuntuforums.org/showthread.php?t=1327809&page=2](http://swiss.ubuntuforums.org/showthread.php?t=1327809&page=2) )](*,)

(Just kidding.)  Thanks again.

---

### Post by kyleabaker on 2010-07-12
> **Ron_ said:**
> Kyle,

You did it, buddy!  I got voice and picture for the first time in Skype.  Gnome Sound Recorder also worked.  You da' man!

For whatever reason, I had to tinker around a bit at first.  Had to fix input volume.  Also ran {rmmod, modprobe}, though I'm not sure I had to.

I will continue to exercise the system for a few days.  I'll let you know if any dubious behaviors emerge.

Many thanks.  (Any chance you'd like to help get my linmodem or my DVD burner working? ([http://swiss.ubuntuforums.org/showthread.php?t=1327809&page=2](http://swiss.ubuntuforums.org/showthread.php?t=1327809&page=2) )](*,)

(Just kidding.)  Thanks again.

Awesome. I've been looking through the driver code for a week now, hehe.

If the audio stopped working at some point before and you hadn't restored the input to LifeCam then on reboot it won't be selected by default. Now that its not being cut off, it should be automatically selected upon reboots (unless you unplug the device of course).

If you get a chance to try at some point. Test that upon reboot that the mic is still selected and try the device without {rmmod, modprobe} now. I haven't had to use it, but that may be a problem unrelated to this patch.

Glad to hear its working now though. I have a few more edits to make, but I think this patch will be merged with GSPCA and into the kernel before too long if there are no regressions. :D

---

### Post by Ron_ on 2010-07-12
Yup.

I did reboot (again) and the mic was there right away for Sound Recorder.  Launched Cheese.  Relaunched Sound Recorder.  No probs.  Ran Skype.  Got voice and picture with no further ado.

Two observations.  I did not have to restore the input device in Sound Prefs either time.  Last time, though, I think it changed its name to "USB Analog Mono."  Now it's back to Lifecam VX-1000 Analog Mono."  In both cases, it was already selected.  (As I mentioned before, volume needed to be re-max'd in ALSA Mixer after the first reboot, but by the second reboot it stuck.)

In Cheese, I had to play with video saturation for the first time in memory.  Can't be sure that this is related, though.

---

### Post by Mr Roboto on 2010-07-12
Working for me too.  Legendary!  Looking forward to seeing this in the mainline kernel tree.

Well done, mate!

---

### Post by kyleabaker on 2010-07-13
The GSPCA maintainer has merged these changes into GSPCA 2.9.52, which means it should now be included in all future releases as well. Hopefully GSPCA 2.9.52+ is merged with the Linux kernel before the final kernel that Ubuntu 10.10 ships with.

You can find his version as well as future GSPCA updates on his web site:
[http://moinejf.free.fr/](http://moinejf.free.fr/)

I'm now marking this thread as solved as well, but if you have any other problems relating to this driver or webcam feel free to continue the thread.

---

### Post by pikmaster on 2010-07-16
Hi kyleabaker.
I cannot compile your patch on Ubuntu 9.04 Jaunty Jackalope

jola@komputer-Joli:~/Download$ ls 
Makefile  README  build  crebuildir.sh  
gspca-2.9.51-vx1000-patch-20100712.zip

jola@komputer-Joli:~/Download$ uname -a
Linux komputer-Joli 2.6.28-19-generic #61-Ubuntu SMP Wed May 26 23:35:15 UTC 2010 i686 GNU/Linux


jola@komputer-Joli:~/Download$ make
make -C /lib/modules/2.6.28-19-generic/build M=/home/jola/Download/build modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-19-generic'
  CC [M]  /home/jola/Download/build/gspca.o
In file included from /home/jola/Download/build/gspca.h:2,
                 from /home/jola/Download/build/gspca.c:42:
/home/jola/Download/build/gspca.h.orig:84: warning: 'struct v4l2_dbg_register' declared inside parameter list
/home/jola/Download/build/gspca.h.orig:84: warning: its scope is only this definition or declaration, which is probably not what you want
/home/jola/Download/build/gspca.h.orig:86: warning: 'struct v4l2_dbg_chip_ident' declared inside parameter list
/home/jola/Download/build/gspca.c: In function 'gspca_is_compressed':
/home/jola/Download/build/gspca.c:493: error: 'V4L2_PIX_FMT_MR97310A' undeclared (first use in this function)
/home/jola/Download/build/gspca.c:493: error: (Each undeclared identifier is reported only once
/home/jola/Download/build/gspca.c:493: error: for each function it appears in.)
/home/jola/Download/build/gspca.c: At top level:
/home/jola/Download/build/gspca.c:965: warning: 'struct v4l2_dbg_chip_ident' declared inside parameter list
/home/jola/Download/build/gspca.c: In function 'vidioc_g_chip_ident':
/home/jola/Download/build/gspca.c:977: warning: passing argument 2 of 'gspca_dev->sd_desc->get_chip_ident' from incompatible pointer type
/home/jola/Download/build/gspca.c: In function 'dev_mmap':
/home/jola/Download/build/gspca.c:1783: warning: assignment discards qualifiers from pointer target type
/home/jola/Download/build/gspca.c: At top level:
/home/jola/Download/build/gspca.c:2093: error: variable 'dev_fops' has initializer but incomplete type
/home/jola/Download/build/gspca.c:2094: error: unknown field 'owner' specified in initializer
/home/jola/Download/build/gspca.c:2094: warning: excess elements in struct initializer
/home/jola/Download/build/gspca.c:2094: warning: (near initialization for 'dev_fops')
/home/jola/Download/build/gspca.c:2095: error: unknown field 'open' specified in initializer
/home/jola/Download/build/gspca.c:2095: warning: excess elements in struct initializer
/home/jola/Download/build/gspca.c:2095: warning: (near initialization for 'dev_fops')
/home/jola/Download/build/gspca.c:2096: error: unknown field 'release' specified in initializer
/home/jola/Download/build/gspca.c:2096: warning: excess elements in struct initializer
/home/jola/Download/build/gspca.c:2096: warning: (near initialization for 'dev_fops')
/home/jola/Download/build/gspca.c:2097: error: unknown field 'read' specified in initializer
/home/jola/Download/build/gspca.c:2097: warning: excess elements in struct initializer
/home/jola/Download/build/gspca.c:2097: warning: (near initialization for 'dev_fops')
/home/jola/Download/build/gspca.c:2098: error: unknown field 'mmap' specified in initializer
/home/jola/Download/build/gspca.c:2098: warning: excess elements in struct initializer
/home/jola/Download/build/gspca.c:2098: warning: (near initialization for 'dev_fops')
/home/jola/Download/build/gspca.c:2099: error: unknown field 'unlocked_ioctl' specified in initializer
/home/jola/Download/build/gspca.c:2099: warning: excess elements in struct initializer
/home/jola/Download/build/gspca.c:2099: warning: (near initialization for 'dev_fops')
/home/jola/Download/build/gspca.c:2100: error: unknown field 'poll' specified in initializer
/home/jola/Download/build/gspca.c:2100: warning: excess elements in struct initializer
/home/jola/Download/build/gspca.c:2100: warning: (near initialization for 'dev_fops')
/home/jola/Download/build/gspca.c:2129: error: unknown field 'vidioc_enum_framesizes' specified in initializer
/home/jola/Download/build/gspca.c:2129: warning: initialization from incompatible pointer type
/home/jola/Download/build/gspca.c:2130: error: unknown field 'vidioc_enum_frameintervals' specified in initializer
/home/jola/Download/build/gspca.c:2130: warning: initialization from incompatible pointer type
/home/jola/Download/build/gspca.c:2135: warning: initialization from incompatible pointer type
/home/jola/Download/build/gspca.c:2140: warning: initialization from incompatible pointer type
make[2]: *** [/home/jola/Download/build/gspca.o] Error 1
make[1]: *** [_module_/home/jola/Download/build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-19-generic'
make: *** [modules] Error 2

---

### Post by pikmaster on 2010-07-17
OK, I managed to solve the problem, by taking the source code from 
[http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2)

The version I downloaded was v4l-dvb-9652f85e688a.tar.bz2

Then I replaced the **v4l-dvb-9652f85e688a/v4l/sonixj.c** file in the archive with the **sonixj.c** file from kyleabaker's patch ([http://www.kyleabaker.com/downloads/ubuntu/gspca/gspca-2.9.51-vx1000-patch-20100712.zip](http://www.kyleabaker.com/downloads/ubuntu/gspca/gspca-2.9.51-vx1000-patch-20100712.zip))

Then I compiled the v4l-dvb source:
```
cd v4l-dvb-9652f85e688a
make
sudo make install
```

Now you either need to **reboot** *or* remove and load the new modules for VX-1000:
```
modprobe -vr gspca_sonixj
```

After that, the only adjustment I had to do, was Skype. For video, you need to create a wrapper script */usr/local/bin/skype*:
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype "$@"
```

For audio, Skype had the PulseAudio server set for recording device, but was not recording anything (gnome audio recorder was able to select different capture source). To fix that, start Skype and launch the test call.
While test call is running (recording) run **pavucontrol** from terminal.
Go to "recording tab", click Move Stream to "USB camera - USB Audio".

Done, both video and audio are now working.

---

### Post by executorvs on 2010-07-27
I have a vx-3000 at home. I'll try the patch today and get back to you.

---

### Post by kyleabaker on 2010-07-27
> **executorvs said:**
> I have a vx-3000 at home. I'll try the patch today and get back to you.

My patch has been worked into the maintainers code, and his code is updated regularly, so just download his and try it (currently GSPCA 2.10.2) from:
[http://moinejf.free.fr/](http://moinejf.free.fr/)

Then run the usual...
make
sudo make install
reboot

Thanks! I've been curious to see if this patch fixed the vx-3000!

---

### Post by kyleabaker on 2010-07-31
> **executorvs said:**
> I have a vx-3000 at home. I'll try the patch today and get back to you.

Were you ever able to test the latest drivers to see if the patch fixes the vx-3000?

---

### Post by zoso375 on 2010-08-11
> **kyleabaker said:**
> We have found the problem and I've put a patch together. If everyone experiencing the problem with the microphone can test this, please do. I'd like to know if this works with VX-1000 and VX-3000 webcams (not sure if the VX-3000 had mic issues, but if it does try this patch).

[LIST=1]
[*]Download my patched GSPCA: [gspca-2.9.51-vx1000-patch-20100712.zip](http://www.kyleabaker.com/downloads/ubuntu/gspca/gspca-2.9.51-vx1000-patch-20100712.zip)

[*]Extract the zip file on your Desktop (so you have the folder “gspca-2.9.51-vx1000-patch-20100712&#8243;).
[*]Open a terminal window and enter the following commands:
cd Desktop/gspca-2.9.51-vx1000-patch-20100712/
make
sudo make install
[*]Reboot your computer and test your webcam in an application such as Cheese (which can easily be found in the Ubuntu Software Center).
[/LIST]

Make sure that when you start your webcam in Cheese that the microphone continues to work. You can verify this in the Sound Preferences window if you click on the Input tab (make sure you have selected “LifeCam VX-1000&#8243;  as your input device).

You can find more [details explaining this patch]("http://kyleabaker.com/2010/07/12/microsoft-lifecam-vx-1000-linux-gspca-patch/") in my blog if you'd like, but please post results here.

My two cents: this worked like a charm, unbelievably.  I've been trying to get this webcam working since Jaunty, at least.  You're a lifesaver.

---

### Post by Liametc on 2010-08-12
i think i love you

---

### Post by Ron_ on 2010-08-28
FALSE ALARM.  (Sorry.  All of this is true, but rebooting after patching brought back the sound.)

Hey, Kyle.  This baby stopped working for me again.  I think the reason was an "upgrade" in 2.6.31.  I repeated the 20100712 patch, make, make install, sudo rmmod gspca_sonixj.  On sudo modprobe gspca_sonixj I got...
FATAL:  Error inserting gspca_sonixj (/lib/modules/2.6.31-22-generic/kernel/drivers/media/video/gspca/gspca_sonixj.ko): Unknown symbol in module, or unknown parameter (see dmesg).

dmesg follows.  Any advice?

> 
[49595.551851] gspca_sonixj: disagrees about version of symbol gspca_frame_add
[49595.551857] gspca_sonixj: Unknown symbol gspca_frame_add
[49595.552637] gspca_sonixj: disagrees about version of symbol gspca_dev_probe
[49595.552641] gspca_sonixj: Unknown symbol gspca_dev_probe


---

### Post by kyleabaker on 2010-08-29
> **Ron_ said:**
> FALSE ALARM.  (Sorry.  All of this is true, but rebooting after patching brought back the sound.)

Hey, Kyle.  This baby stopped working for me again.  I think the reason was an "upgrade" in 2.6.31.  I repeated the 20100712 patch, make, make install, sudo rmmod gspca_sonixj.  On sudo modprobe gspca_sonixj I got...
FATAL:  Error inserting gspca_sonixj (/lib/modules/2.6.31-22-generic/kernel/drivers/media/video/gspca/gspca_sonixj.ko): Unknown symbol in module, or unknown parameter (see dmesg).

dmesg follows.  Any advice?

I'm glad you got it working, but you shouldn't be using my patched version anymore. My patch has already been worked into the official GSPCA as I [mentioned before]("http://ubuntuforums.org/showpost.php?p=9586191&postcount=25").

Everyone should be testing with the official GSPCA since it will continue to be maintained and include more fixes over time. My patched version is far outdated already. ;)

**Download the latest GSPCA here:**
[http://moinejf.free.fr/](http://moinejf.free.fr/)

---

### Post by Ron_ on 2010-08-29
Thanks, Kyle.

As a newbie, (not a tester), I was sorta hoping the patch would be stable until it (or its latest version) is merged with the Linux kernel.  (Thought it might even have been included in the most recent upgrade.)  I guess every strategy comes with its own risks.

---

### Post by tmoney68 on 2010-09-14
Just installed the patch and it works great with a vx-3000!!!!

---

### Post by shoeheight on 2010-10-06
> **kyleabaker said:**
> We have found the problem and I've put a patch together. If everyone experiencing the problem with the microphone can test this, please do. I'd like to know if this works with VX-1000 and VX-3000 webcams (not sure if the VX-3000 had mic issues, but if it does try this patch).

[LIST=1]
[*]Download my patched GSPCA: [gspca-2.9.51-vx1000-patch-20100712.zip](http://www.kyleabaker.com/downloads/ubuntu/gspca/gspca-2.9.51-vx1000-patch-20100712.zip)

[*]Extract the zip file on your Desktop (so you have the folder “gspca-2.9.51-vx1000-patch-20100712&#8243;).
[*]Open a terminal window and enter the following commands:
cd Desktop/gspca-2.9.51-vx1000-patch-20100712/
make
sudo make install
[*]Reboot your computer and test your webcam in an application such as Cheese (which can easily be found in the Ubuntu Software Center).
[/LIST]

Make sure that when you start your webcam in Cheese that the microphone continues to work. You can verify this in the Sound Preferences window if you click on the Input tab (make sure you have selected “LifeCam VX-1000&#8243;  as your input device).

You can find more [details explaining this patch]("http://kyleabaker.com/2010/07/12/microsoft-lifecam-vx-1000-linux-gspca-patch/") in my blog if you'd like, but please post results here.

Thanks for your help...solved my issues

---

