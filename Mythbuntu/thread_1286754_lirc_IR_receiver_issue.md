---
title: "lirc IR receiver issue"
date: 2009-10-09
forum: Mythbuntu
---

### Post by ohzopants on 2009-10-09
This is in no way Myth related, but I decided to post here because I assume that's where the highest concentration of lirc users are to be found.

So here's my issue: I use xbmc to watch videos and I *had* lirc working just fine with my MCE remote (using the mceusb2 module).  Then, on Tuesday, the light on the recevier will not turn off and it does not respond to any key presses on the remote.

I've done the usual googling and forum searching, but I've come up empty handed...

Some places suggested that it might have to do with the order in which USB devices are initialized and which port you are using, but that hasn't changed on my setup.

Unplugging the receiver, stopping lirc, rmmod and modprobe lirc and restarting lirc doesn't help.

dpkg-reconfigure lirc doesn't help either.

My htpc runs an up to date Jaunty (I think the only update I've done since it worked was wget, and I highly doubt that's related).  I installed lirc on my laptop which runs karmic beta and irw worked as expected; so it's not a hardware issue.

Any ideas?

---

### Post by belly917 on 2009-10-09
I sometimes have this problem, but it is never as permanent as it seems to be for you.

For me it only becomes unresponsive during the boot process.  It will not work again until I do one of the following:
[LIST]
[*]Unplug the device, replug the device and restart lirc
[*]Reboot
[/LIST]
Even then it might not reset and I might have to try multiple times.  When it was really being stubborn, leaving the computer off and the USB receiver unplugged for ~10 minutes fixed it.

Lately is hasn't been an issue, as I think the "stuck" MCE2usb receiver is caused by IR signals received during the device's initialization.  So I try to make sure that no IR happens while my mythfrontend is booting.

I don't know if this is much of a help, I just thought I'd share what worked for me.

---

### Post by igoddard on 2009-10-10
> **ohzopants said:**
> This is in no way Myth related, but I decided to post here because I assume that's where the highest concentration of lirc users are to be found.

So here's my issue: I use xbmc to watch videos and I *had* lirc working just fine with my MCE remote (using the mceusb2 module).  Then, on Tuesday, the light on the recevier will not turn off and it does not respond to any key presses on the remote.

I've done the usual googling and forum searching, but I've come up empty handed...

Some places suggested that it might have to do with the order in which USB devices are initialized and which port you are using, but that hasn't changed on my setup.

Unplugging the receiver, stopping lirc, rmmod and modprobe lirc and restarting lirc doesn't help.

dpkg-reconfigure lirc doesn't help either.

My htpc runs an up to date Jaunty (I think the only update I've done since it worked was wget, and I highly doubt that's related).  I installed lirc on my laptop which runs karmic beta and irw worked as expected; so it's not a hardware issue.

Any ideas?

I know you're not using the Hauppauge but check the instructions about setting up the udev rule here: [HTML]http://ubuntuforums.org/showthread.php?t=1140411[/HTML]

You'd need to look through /var/log/messages to see what string replaces "IR-receiver inside an USB DVB receiver".  That would ensure that the USB initialisation order isn't affecting you.

---

### Post by ohzopants on 2009-10-13
Thanks for all the suggestions, but nothing has worked yet.
I've got a bunch of other things going on right now, and I'm planning on a clean install of Karmic soon so I guess I'll just hope that it fixes itself during the upgrade.

---

### Post by ohzopants on 2009-10-16
I played around with it some more:
I read some other people had problems with interference from their TV or sound systems and that was not my issue.

I've tried with the receiver connected to every USB port I have and that didn't work either.

This is really driving me nuts... for the longest time I was ok with using my wireless keyboard to control xbmc but now that I'm used to the remote it's really annoying to have to go back to the keyboard method.

Any other ideas?  Anyone?

---

### Post by igoddard on 2009-10-16
Just a thought - have you checked the transmitter?

Quick tip for checking IR transmitters: a digital camera often has sensitivity in the IR.  Point one at the LED and see if you can see it light up when you press a button in the remote.

---

### Post by ljw1 on 2009-10-21
I am having exactly the same issues. The remote was working and now it is not. All of the setup instructions I have found have given no workable solution. Reconfiguring has not helped and dmesg says that the remote is detected and the correct module is loaded but nothing happens. One problem that I have noticed is that sometimes after a cold boot when I type irw to find out if the remote is going to work it gives a no interface error, but even when it does connect there is no output. It is most annoying not having a remote working on my htpc now when I did nothing to break it. Any further suggestions would be most appreciated.

---

### Post by ohzopants on 2009-10-21
> **igoddard said:**
> Just a thought - have you checked the transmitter?

Quick tip for checking IR transmitters: a digital camera often has sensitivity in the IR.  Point one at the LED and see if you can see it light up when you press a button in the remote.

That is a fantastically geeky and awesome trick I never knew!  Thanks.

But, unfortunately, I can clearly see the signal from the remote on my camera's display when I press any button.

ljw1, I still haven't solved the issue but if (when?) I do I will post my solution here.  Can I ask you to do the same if you figure it out first?

---

### Post by belly917 on 2009-10-21
It happened again this past Sunday morning.  After 2 reboots, the receiver was still stuck on.  When I was rebooting for the 3rd time, I covered the receiver with my hand to prevent the reception of any stray IR signals as it initialized.  During this time the receiving light was off, but as soon as I removed my hand, the light was stuck on again.  Queue mental image of someone playing peek-a-boo with their IR receiver - that was me for a minute or 2.

Next, I isolated the receiver again and tested my remote from a close range.  It worked fine.

Finally, I tried to locate the source of the IR interference and after moving around the room, it disappeared and didn't come back.

Has anyone else having this problem ruled out IR interference?

---

### Post by ohzopants on 2009-10-21
I tried the "peek-a-boo" thing too... glad I'm not the only one who felt sort of silly doing it.

I've unplugged everything else in the room to rule out interference.

---

### Post by leemauger on 2009-11-12
Hi

I have similar strange things going on with OpenSuse and lirc with my Philips SRM5100 MCE remote.

I ran mode2 and found it was spitting out endless streams of data without me pressing the buttons...

When I covered the receiver they stopped, so it was getting interference from somewhere. I found that I needed to shield the receiver from my plasma TV to stop the noise. So TV's (plasma in particular in my case) seem to cause IR noise... I have a cheap Soniq 42 inch plasma.

I just moved the receiver down in front of my receiver and hey presto no noise :)

However, I still need to get irw to work... don't think the codes are being recognised even though I've downloaded the right SRM5100 lirc.conf. Will keep trying.

Thought you guys might find this interesting. Not like it is logical to turn off your TV when trying out your remote!!

---

### Post by leemauger on 2009-11-13
Sorted my Philips SRM5100 remote with lirc on Suse :)

It turns out there are some duff lirc.conf files floating about for this remote. I found the one here works

[http://lirc.sourceforge.net/remotes/philips/](http://lirc.sourceforge.net/remotes/philips/)

You need to make sure you have the lines 

  toggle_bit_mask 0x8000
  rc6_mask    0x100000000
Otherwise mode2 will spit out codes but irw will not report anything :(

I picked up my duff file from here [http://lircconfig.commandir.com/lircd.conf/?viewremote=904](http://lircconfig.commandir.com/lircd.conf/?viewremote=904)

DON'T USE THAT ONE!

Otherwise all good. Nice remote, is a bit sensitive to IR noise from TV though, just put it to the side / on top and it's fine.

Hope this helps.

Lee

---

