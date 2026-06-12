---
title: "Multiple commands sent from remote"
date: 2011-02-15
forum: Mythbuntu
---

### Post by lviperz on 2011-02-15
I have searched through here as well as the mythtv mailing list and tried all tips related to my problem. But I'm still at a complete loss as to the multiple commands being sent from my remote.

Here is what I have. A clean install of mythbuntu 10.10, not an upgrade. I have a hauppauge pvr-250 installed using the remote with it. I have the grey remote that is programmed in to a harmony 880.

LIRC is running and the remote functions on all buttons but I get the multiple commands as many have seen.

I have edited my lircrc (.lirc/mythtv) file to try a delay of 1 or 2 but that didn't help. Repeat is already set to 0.
I edited the conf file referenced in /etc/lirc/lircd.conf (include "/usr/share/lirc/extras/more_remotes/hauppauge/lircd.conf.hauppauge") and removed all other remotes referenced so that only the hauppauge_350 remained.

I've restarted lirc after every change and I've even rebooted the system just to make sure. But I still have the problem.

I've ran irw and watched as I press the buttons and I can see the duplicates. I'm lost. I've even set the delay on the harmony longer in hopes of fixing the problem. I've even pulled out the actual grey remote and I get the same duplicate commands.

Anyone have any other idea what else to look for or try?

---

### Post by mr_luksom on 2011-02-16
When you say duplicates, you mean duplicates of the same message in irw?

I get the same thing, but it does not interfere with mythtv operation. If I set repeat to 0 in lircd.conf, one keypress is one action. I do use a homebrew serial reliever though, not hauppaugge equipment.

I personally enabled repeat, I found it made myth easier to use.

---

### Post by AlecJ on 2011-02-16
> **lviperz said:**
> I have searched through here as well as the mythtv mailing list and tried all tips related to my problem. But I'm still at a complete loss as to the multiple commands being sent from my remote.

Here is what I have. A clean install of mythbuntu 10.10, not an upgrade. I have a hauppauge pvr-250 installed using the remote with it. I have the grey remote that is programmed in to a harmony 880.

LIRC is running and the remote functions on all buttons but I get the multiple commands as many have seen.

I have edited my lircrc (.lirc/mythtv) file to try a delay of 1 or 2 but that didn't help. Repeat is already set to 0.
I edited the conf file referenced in /etc/lirc/lircd.conf (include "/usr/share/lirc/extras/more_remotes/hauppauge/lircd.conf.hauppauge") and removed all other remotes referenced so that only the hauppauge_350 remained.

I've restarted lirc after every change and I've even rebooted the system just to make sure. But I still have the problem.

I've ran irw and watched as I press the buttons and I can see the duplicates. I'm lost. I've even set the delay on the harmony longer in hopes of fixing the problem. I've even pulled out the actual grey remote and I get the same duplicate commands.

Anyone have any other idea what else to look for or try?


The problem your trying to fix is hardware, no amount of playing will cure this fault.


The best thing I ever did was to dump this remote, buy a Microsoft MCE remote and USB receiver. The key is the USB Receiver, it must be MCE, there are a lot of types that make the remote into a keyboard and wow thats not fun.

It was has totally transformed the way myth works, had ours for 3 years now, you can also train the power button to operate the TV on/off.

---

### Post by AlecJ on 2011-02-16
They have changed a bit in 3 years, but this is the sort of thing

[http://www.mythtv.org/wiki/MCE_Remote](http://www.mythtv.org/wiki/MCE_Remote)

[https://www.amazon.co.uk/Anyware-HA-IR01SV-Multimedia-control-infrared/dp/B00123UGWQ/ref=sr_1_6?ie=UTF8&qid=1297862985&sr=8-6]("http://cgi.ebay.co.uk/Emachines-Universal-MCE-Remote-Control-USB-Receiver-/140512298353?pt=UK_Collectables_InputDevices_RL&hash=item20b72f8571")[]("http://cgi.ebay.co.uk/HP-Backlit-MCE-Remote-Control-TV-CBL-DVD-AUX-Learning-/140512298083?pt=UK_Collectables_InputDevices_RL&hash=item20b72f8463")

---

### Post by lviperz on 2011-02-16
> **mr_luksom said:**
> When you say duplicates, you mean duplicates of the same message in irw?

I get the same thing, but it does not interfere with mythtv operation. If I set repeat to 0 in lircd.conf, one keypress is one action. I do use a homebrew serial reliever though, not hauppaugge equipment.

I personally enabled repeat, I found it made myth easier to use.

What I mean by duplicates is, for example, when I press the up or down button while in the menus of mythtv, the selection will sometimes jump twice. Press the button once and it should move once, but sometimes it will move twice. This will also happen with the back (esc) button as well as the ok (enter) buttons.

When I run irw I can see the single button press will sometimes result in what looks like multiple key presses. 

As stated in my op, I have searched and there are many people who are experiencing the same problem that seems to have only appeared since lirc is now included in the kernel. Not only in mythbuntu/ubuntu 10.10, but fc14 as well.

I have the same tuner/remote setup in another box running 10.04 and it works correctly. So I don't think it is a hardware issue unless the latest kernel no onger supports my hardware. But the remote works out of the box but with the multiple keystroke/button problem.

There was another post here where Ian Dobson stated he simply removed the extra defined remotes from the conf file and that solved his problem. I have tried that without any luck. I was hoping someone else has the same or similar hardware who did finally fix or found a work around to the problem.

---

### Post by ian dobson on 2011-02-16
Hi,

what happens if you delete the include in the conf file then reboot. Does irw see anything? Could you use irrecord (irecord) to create a new configuration file.

Are you sure you only have one remote configuration file included in your conf?

Regards
Ian Dobson

---

### Post by lviperz on 2011-02-16
> **ian dobson said:**
> Hi,

what happens if you delete the include in the conf file then reboot. Does irw see anything? Could you use irrecord (irecord) to create a new configuration file.

Are you sure you only have one remote configuration file included in your conf?

Regards
Ian Dobson

I'm sure I only have one included file, but I did not try removing the included file. Or trying irrecord to make a new file. This was all from a fresh install.

When I get home tonight I will remove the included file, reboot and see what I get. I did try stopping lirc but then the remote didn't work at al, as expected. I also tried removing the button mappings for the arrow keys to see if maybe something else might have been running and interpreting the buttons, but that just resulted in the arrows keys not working at all.

If I can't get this figured out, due to the WAF, I will look at the mce usb. I've found some on ebay but they are generic. Anyone ever use those hootoo mce remotes?

---

