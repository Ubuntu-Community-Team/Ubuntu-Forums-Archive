---
title: "Hauppauge WinTV-NOVA-T-500 Problems"
date: 2009-10-18
forum: Mythbuntu
---

### Post by GuiGuy on 2009-10-18
I'm trying to set up a new install for MythBuntu 9.10 using the same hardware driving a working 9.04 system. The tuner card is a [Hauppauge WinTV-NOVA-T-500]("http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500#Forcing_the_activation_of_LNAs_.28Low_Noise_Amplifier.29")

I definitely need to have the LAN (Low Noise Amplifier) turned on to get sufficient signal for a lock. The following did the trick under MythBuntu 9.04

> 
In /etc/modprobe.d/options add:
options dvb_usb_dib0700 force_lna_activation=1

and then 

sudo modprobe dvb_usb_dib0700 
 

This didn't work under 9.10. I then changed /etc/modprobe.d/options to /etc/modprobe.d/options.conf as suggested by the modprobe warning. 

Again, no luck. 

Can anyone help?

---

### Post by AJ1000 on 2009-10-19
I have it working, but with a lot of trial and error. I think you need to have it as dvb-usb-dib0700.conf as well with the following:

options dvb-usb-dib0700 force_lna_activation=1

(which is exactly the same as my options.conf file).

I assume you are using the follwoing to test that the card goes to the warm state:

dmesg|grep -i dvb

---

### Post by GuiGuy on 2009-10-19
> **AJ1000 said:**
> 
I assume you are using the follwoing to test that the card goes to the warm state:

dmesg|grep -i dvb

Yes, I did and it failed. However, after a COLD restart it came good. As I read it there seems to be intermittent issue with the card that is usually resolved by a complete power down and restart. 

Anyway, it seems right now although I am currently [locked out ]("http://ubuntuforums.org/showthread.php?t=1295570")of the system and it's starting to look like a complete re-install :(

---

### Post by AJ1000 on 2009-10-20
I always cold restart, so I did not realise this. Sorry about you being locked out.

Good luck with the reinstallation.

---

### Post by Zeedok on 2009-10-24
> **GuiGuy said:**
> I'm trying to set up a new install for MythBuntu 9.10 using the same hardware driving a working 9.04 system. The tuner card is a [Hauppauge WinTV-NOVA-T-500]("http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500#Forcing_the_activation_of_LNAs_.28Low_Noise_Amplifier.29")

I definitely need to have the LAN (Low Noise Amplifier) turned on to get sufficient signal for a lock. The following did the trick under MythBuntu 9.04

 

This didn't work under 9.10. I then changed /etc/modprobe.d/options to /etc/modprobe.d/options.conf as suggested by the modprobe warning. 

Again, no luck. 

Can anyone help?

I'm having the same problem with 9.10.  An Hauppage Nova-T-500, which worked fine under 9.04.  I will try these instructions, but I just wanted to check - the options.conf file doesn't currently exist.  Can that be right?  It's a clean install . . .

Also, do you mean that the file has to be called dvb-usb-dib0700.conf and it needs to be in the /etc/modprobe.d/ directory??

Thanks

---

### Post by GuiGuy on 2009-10-24
> **Zeedok said:**
> I'm having the same problem with 9.10.  An Hauppage Nova-T-500, which worked fine under 9.04.  I will try these instructions, but I just wanted to check - the options.conf file doesn't currently exist.  Can that be right?  It's a clean install . . .

Just create it. I've since observed that it doesn't matter if it's options.conf or plain "options". But, assuming MythBuntu, 

sudo mousepad /etc/modprobe.d/options.conf 

will be best to future proof it. Note that mousepad will create the file if it doesn't exist.

Then add the line into the options.conf file. 

options dvb_usb_dib0700 force_lna_activation=1

and save. 

> 
Also, do you mean that the file has to be called dvb-usb-dib0700.conf and it needs to be in the /etc/modprobe.d/ directory??


No, just do

sudo modprobe dvb_usb_dib0700 

You shouldn't get any errors or warnings. 

I found that after this I had to shut the PC down (power off). Wait a couple of seconds and restart. Indicated signal levels should now be a bit higher. 

Cheers

---

### Post by Zeedok on 2009-10-24
OK, well I followed your instructions, putting that line into /etc/modprobe.d/options.conf, then I ran the command at the CLI and rebooted . . . Still no luck.

Maybe I should check that your problem was EXACTLY the same as mine . . . My automatic tuning has picked up most or all of my stations - the signal levels are on the whole OK, but the bit error reads as 65555 or whatever the maximum amount it on every channel (even those that the tuner can lock onto).  One channel won't lock even though the Myth interface reports signal 99%.

I am using Mythbuntu 9.10. None of the hardware has changed.  I don't know what software modules are included but I either need the low noise amplifier or a filter or something.

Any other suggestions?

---

### Post by AJ1000 on 2009-10-24
What does

dmesg | grep -i dvb 

show?

---

### Post by GuiGuy on 2009-10-24
> **Zeedok said:**
> OK, well I followed your instructions, putting that line into /etc/modprobe.d/options.conf, then I ran the command at the CLI and rebooted . . . Still no luck.

Any other suggestions?

I am in a bad reception area that receives signals from two directions. Invariably when  I scan for signals it's the lesser one  the tuners latch onto. My solution now to scan on specific frequencies, ie I enter the frequencies and some other details for each transponder I want.

Another solution might be to use a second tuner card, if you have access to one, for the scanning stage.  If you're not clear what I mean, let me know and I'll write a step by step. Assuming you have access to another tuner card, of course.

Sorry I can't be of more help than that.

---

### Post by AJ1000 on 2009-10-24
Zeedok,

Check out here:

[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

especially the

'Testing The DVB Card' section

Hope it helps. I have had nova t 500 working for a week now on 9.10, and have gone through the pain you are experiencing, so I understand your frustration.

AJ1000

---

### Post by GuiGuy on 2009-10-24
> **AJ1000 said:**
> What does

dmesg | grep -i dvb 

show?

That won't show if the LNA is on, will it?

---

### Post by GuiGuy on 2009-10-24
> **AJ1000 said:**
> 

[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)


That leads to 
[http://www.mythtv.org/wiki/Index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/Index.php/Hauppauge_WinTV_Nova-T_500_PCI)

which used to be a reasonable guide but has now been deleted!!?? :confused:

Why would they delete or not archive wiki articles?

---

### Post by AJ1000 on 2009-10-24
Go here for the guide (I used firefox for this). Google stil has it cached

[http://209.85.229.132/search?q=cache:g0nu023wAKcJ:www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI+mythtv+pci+nova+t+500&cd=1&hl=en&ct=clnk&gl=uk&client=firefox-a](http://209.85.229.132/search?q=cache:g0nu023wAKcJ:www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI+mythtv+pci+nova+t+500&cd=1&hl=en&ct=clnk&gl=uk&client=firefox-a)

or search google for

mythtv pci nova t 500

In answer to the

dmesg | grep -i dvb

question .. yes it does show it is active because it is in the warm state (fourth line down) rather than cold state. This is what my output looks like for the command:

owner@owner-desktop:~$ dmesg | grep -i dvb
[    9.951182] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
[    9.951191] usb 2-1: firmware: requesting dvb-usb-dib0700-1.20.fw
[   10.158176] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[   10.900137] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[   10.900248] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   10.901926] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   11.025370] DVB: registering adapter 0 frontend 0 (DiBcom 3000MC/P)...
[   11.726718] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   11.727123] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[   11.736224] DVB: registering adapter 1 frontend 0 (DiBcom 3000MC/P)...
[   12.553802] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:08.0/0000:01:06.2/usb2/2-1/input/input5
[   12.553875] dvb-usb: schedule remote query interval to 50 msecs.
[   12.553881] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[   12.554111] usbcore: registered new interface driver dvb_usb_dib0700

---

### Post by GuiGuy on 2009-10-24
> **AJ1000 said:**
> 
question .. yes it does show it is active because it is in the warm state (fourth line down) rather than cold state. 

Sorry, I meant that it wouldn't show if the Low Noise Amplifier is on. By default it is usually set to off. 

BTW, there is a wiki page. Looks like it's been re-done and the old one was deleted. 

[http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI]("http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI")

As I hinted earlier, I can't actually scan for channels using the card. I had to use one of the others. However, the T-500 seems to be working for me although indicated signal levels are lower than what they should be.

---

### Post by AJ1000 on 2009-10-24
Did you do the 'Testing the DVB card' section from the Parker website?

---

### Post by GuiGuy on 2009-10-24
> **Zeedok said:**
> 
Any other suggestions?

If you get really stuck with this I'd suggest the myth-users mailing list. There is a high degree of expertise there. 

[http://mythtv.org/cgi-bin/mailman/listinfo/mythtv-users]("http://mythtv.org/cgi-bin/mailman/listinfo/mythtv-users")

---

### Post by Kaibosh on 2009-11-03
I was having an issue with the LNA as well - and specifically "Where do I put the option to enable LNA?" since I setup a fresh 9.10 install (was previously 8.10)..

After several rebuilds, and everything SEEMING to work ok except never being able to get a signal lock (so it appearing that LNA wasn't enabled), I tried creating /etc/modprobe.d/dvb-usb-dib0700.conf and putting the LNA activation in there I finally got Signal Locks..

So, for me putting it in /etc/modprobe.d/options.conf did nothing at all.
Renaming /etc/modprobe.d/options.conf to /etc/modprobe.d/dvb-usb-dib0700.conf followed by a reboot and everything was peachy..

---

### Post by moorsey on 2009-11-08
AHHHH, thank you thank you!!!!!!!!!!!!

This solved my problem, more specifically, Kaibosh's suggestion to name the config file "dvb-usb-dib0700.conf" worked

A reboot did not work for me, had to shutdown then power on, unless it was just coincidence.

There were no useful Google hits for the error message I was getting, so to try and get people to this post, I will put some more info here

I was doing all the same stuff in mythtv backend that I was on my previuous myth install, the only difference being this was Ubuntu 9.10, previous was 9.04

When scanning for channels, I just kept getting the error:

"Failed to find any channels"

In the terminal in the background, there was errors about not being able to find cardid devices and was also saying no DiSEqC defined or similar.

Adding this config file and now picking up 69 Freeview channels no problems!

Thanks again for this

---

### Post by johnw230873 on 2009-11-09
Just want to confirm this has worked for me as well BUT I would also like to point out that 

THE FILES DON'T EXIST BY DEFAULT YOU NEED TO CREATE THEM.


It took me a few hours to figure this out;) with installing - reinstalling

I now seem to have a problem where not all my sub channels are being found eg when multiple TV Stations are broadcasting on the same freq (Channel) I'm not picking up all the TV stations.

Any ideas or anyone else heard of this?

---

