---
title: "Quick start help please-UK based Nova-t-500 on 9.10"
date: 2009-11-01
forum: Mythbuntu
---

### Post by djsbriscoe on 2009-11-01
Hi,
Could someone please help me get my Mythtv set up properly? I'm UK based and I've just installed Mythbuntu 9.10 on my standalone machine.
It has a Nova-t-500 dual dvb-t tuner installed.
The Mythbuntu installation went well. I just need to know what I should do next?
Are there any basic tests I can do or terminal commands I can issue to check for basic functionality?
Is there a step by step guide available for newbies like myself?
Any help appreciated, Thanks.

David.

---

### Post by Al_Vampyre on 2009-11-01
My first step is always to try and watch TV after I have done the channel scan, at least that way I know my other half can watch TV even if nothing else works!!

---

### Post by djsbriscoe on 2009-11-01
Hi,
How do I do a channel scan? Most instructions I've read cover a service based in the USA.
Is there anything different I should do?
Thanks.

---

### Post by SiHa on 2009-11-01
First you need to enable the onboard LNA (Low Noise Aplifier)to give you sufficient signal strength even after beinng split over two tuners.

See guiguy's first post [here](http://ubuntuforums.org/showthread.php?t=1294067&highlight=options.conf) to create an options.conf file.

Then you need to run mythtv backend setup (from the system menu).

**Setup a Capture Card:**
New Capture Card 
Adapter0 -> Card type DVB DTV Capture Card (v3.x) - Frontend ID should report DiBcom3000 MC/P. 
Under Recording options, you might want to change max recordings to 1. Theoretically you can record more than 1 per mux, but it's been known to cause problems.
Increase Tuning Delay to 175ms
Come back out of recording options and finish.

Do the same for adapter1

**Create a Video Source:**
New Video Source
Give it a name (I use Freeview;))
If you're hapy with 8 days guide data, chage listings grabber to 'Transmitted Guide Only (EIT)'
Leave Channel Frequency Table at default
Finish

**Creat an Input Connection**
Select Adapter 0
Give it a name if you like, I give it a name that references the adapter number (Freeview0), so I can see what tuner I'm using in case of problems.
Video Source -> The one you just defined
Quick Tuning -> I use LiveTV only (Can't remember why)

Repeat for Adapter 1

**Scan for channels! **
Check the 'Only Free' box.
Scan Type -> Full Scan
Country -> United Kingdom

Hopefully it will now scan for about 10 minutes and report about 50 channels.

When prompted, automatically import all channels, as it will number them for you. Manually you have to number them yourself.

**Arrange Channels and Download Icons**
Channel Editor
Sort Mode : Channel Number
You can go through all the channels toggling the 'Visible' box for the ones you don't want. Not sure if there is a quicker way to do this bit.
Icon Download should pul in all the channel icons.

That should be it.

Exit from the setup, and you'll be asked if you want to run mythfilldatabase, say 'yes', and it's populate the database with your channels.

Hopefully you will now be able to fire up the frontend, and watch TV.

Unfortunately, there is a known issue with the version of the firmware (v1.20) for this card, that ships with 9.10. If you find it's bombing out, and only a **cold** reboot will fix it (check /var/log/syslog for I2C read/write errors), post back here.

---

### Post by djsbriscoe on 2009-11-01
SiHa,
Thanks, just what I was looking for.
Hope there's no problems with I2C comms as I've switched to Linux to avoid a Microsoft XP IRQ bug Microsoft wont fix.
I'll post back if any more problems.

---

### Post by SiHa on 2009-11-01
I've just today reverted back to the 1.10 firmware to hopefully rid myself of the errors. Fingers Crossed!

---

### Post by djsbriscoe on 2009-11-01
Hi,
How did you do that? Is the process described anywhere?

---

### Post by SiHa on 2009-11-01
Unfortunately not exactly 'Described'. There's load of people saying 'I reverted back to 1.10', but nobody actually saying how they did it.

Here's what I did, there's a file called /lib/firmware/dvb-usb-dib0700-1.20.fw and it needs to be replaced by  ...-1.10.fw.

This can be downloaded from [http://www.wi-bw.tfh-wildau.de/~pboe...ib0700-1.10.fw](http://www.wi-bw.tfh-wildau.de/~pboe...ib0700-1.10.fw), thankfully I still had my 8.04 install so I just copied it from there.

Now here's the bodge (I think), the system still looks for 1.20, so you have to fool it by renaming the old file to ...1.20.fw.bak and the new one to ...1.20

Then you'll need to do a cold boot. Power down, and remove all power from the PC so that the the cards will properly power down. Wait for 10 mins or so and reboot. Hopefully the card will now load the new firmware.

```
dmesg | grep dvb
```Should spit out a dozen lines or so, one of which should be telling you that a DVB card has been found in a cold state, and one saying that the firmware has been loaded.

If you get this, then you're home and dry.

---

### Post by djsbriscoe on 2009-11-02
Hi,
I've got as far as scanning the channels but it is unable to find any.
I suspect that the LNA is not turning on properly.
The options.conf file has been created 
but I'm confused about the command line.
Should it read

options dvb-usb-dib0700 force_lna_activation=1

or

options dvb_usb_dib0700 force_lna_activation=1 

Also is there a command for shuting down the mythtv backend fully so that I can use the dvb_apps utilities to test the tuners?

Thanks.

---

### Post by Al_Vampyre on 2009-11-02
> **djsbriscoe said:**
> Hi,

Should it read

options dvb-usb-dib0700 force_lna_activation=1

or

options dvb_usb_dib0700 force_lna_activation=1 

Also is there a command for shuting down the mythtv backend fully so that I can use the dvb_apps utilities to test the tuners?

Thanks.

It's the first one if my memory is working this afternoon (I'm at work!)

killall mythbackend in Terminal should do just that.

---

### Post by SiHa on 2009-11-02
Yes, definitely the first.

Also, when you say it's not finding any. Have you actually let a scan complete?

I noticed when re-installing 9.10 at the weekend, all I get is 'Timed Out' messages, but it still does find them. From memory, signal strength reports about 60-70% during the scan.

Finally, no I2C errors since the fw downgrade yesterday. Fingers crossed.

---

### Post by tonycollinet on 2009-11-02
This is the howto I followed to get my Nova T working properley
[http://ubuntuforums.org/showthread.php?t=1140411&highlight=nova+t+500+remote](http://ubuntuforums.org/showthread.php?t=1140411&highlight=nova+t+500+remote)


I also needed to install updated drivers to get the remote to work - you may or may not need to do this....
[http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

---

### Post by SiHa on 2009-11-02
Well. I'm properly confused now.

I'm not convinced my LNA is actually being turned on. I'm getting major pixellation and sound dropouts on my DVB-T channels BBC-HD on the DVB-S card is fine.

So I had a look at /etc/modprobe.d/options on my old 8.04 install HDD, and the line (which definitely worked, I got no channels without) is:```
options dvb_usb_dib0700 force_lna_activation=1 
```But all the how-to's I've seen recently, including the first one in Tonycollinet's post have:```
options dvb-usb-dib0700 force_lna_activation=1 
```
Now since the 8.04 install, I've increased the gain on my main aerial amp, and I'm wondering if the signal is now good enough to get a successful scan without the LNA activated, but not really to watch.

I'm going to try the version from my old install, and see what happens.

Out of interest, does anyone know how I can check if options.conf is actually being parsed and acted on?

---

### Post by utar on 2009-11-02
My understanding if that "dvb_usb_dib0700" and "dvb-usb-dib0700" are inter changable.  I'm sure I found this in the man page but can find it at the moment:

You can check if the lna is activated by:

more /sys/module/dvb_usb_dib0700/parameters/force_lna_activation

If you get "1" then it is activated.

How is the 1.1 fw going btw, any tunders dropping out?

[Edit: you may want to double check the frequencies myth is using.  I know when I did a full retune once myth decided to use some multiplexes from the wrong transmitter, and hence some channels had a poor signal.  I used [http://www.medionsupport.com/phpbb2/channels.php](http://www.medionsupport.com/phpbb2/channels.php) to find out the right frequencies]



Utar

---

### Post by SiHa on 2009-11-02
Thanks, I tried that and got a '1' so it's activated so, why the pixellation I wonder? Also I notice that a recording from last night is perfect, so it may only affect LiveTV, and that makes absolutely no sense at all! Will have to investigate further.

On a lighter note though, I've not had any I2C errors since reverting to 1.10 yesterday afternoon. I'm going to (cautiously) say it's worked. I'll definitely post back if they return...

---

### Post by djsbriscoe on 2009-11-03
Hi,
I've tuned the channels and can watch TV.
I initially tried v1.0 firmware in /lib/firmware but dmesg reported that firmware could not be loaded. It seems that something is requesting v2.0 only. Can I simply rename the v1.0 firmware file as v2.0 to fool the loader or is it more complicated than that.
Now,how do I activate the remote control? Is this something to do with lirc and if so how do I set things up properly?
Thanks for everyones help so far.

---

### Post by SiHa on 2009-11-03
I'm sure there's a 'proper' way of doing it, but I just renamed it to v1.20 (not v2.0 btw).

The remote *should* work OOB, after configuring through Mythbuntu Control Centre. I say 'Should' because I did see a post by Superm1 (I think) saying something like the LIRC_I2C module doesn't work in 9.10, not sure if that will affect this remote. I use homebrew serial receivers so I can't comment.

---

