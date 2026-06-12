---
title: "No video on tv after restart"
date: 2014-09-11
forum: Mythbuntu
---

### Post by prosmart on 2014-09-11
Greetings

I have my Mythbuntu 14.04 box connected to a 42" new TV by HDMI.

Everything works and everything is awesome!

Except for when I turn the TV off at night and switch it back on the next morning - then it says "no signal".

Then, the only way I can get it show anything is by rebooting the box. Interestingly, when I ssh in from another machine on the network and do a "sudo shutdown -r now" I almost immediately (i.e. before the reboot) see the TV come back to life.

Is this an HDMI issue? Happy to switch cables and port type if it is but I'd like to get a resolution to this problem if possible.

TIA

Nigel

---

### Post by khPWXxF on 2014-09-11
This bug is real a pain.  I can fill in some of the details but it's a tortuous story and if you (or anyone else) can take it further please do so because I'm still struggling.  I'm using Mythbuntu 14.04 64 bit on AMD platform.  I have on-board Nvidia 8300.  Standard 311 drivers were totally unstable but 304 are better (but not as good as the 295 with Mythbubtu 12.04 though). 

Our issue is described here:

[http://www.gossamer-threads.com/lists/mythtv/users/570769](http://www.gossamer-threads.com/lists/mythtv/users/570769)
 
It's been decided that newer drivers no longer need an xorg.conf, but this condition is an exception.
  
Create a configuration file /etc/X11/xorg.conf with nvidia-xconfig if it isn't there already.

then edit the file and add to the "Device" section: 
Option "UseHotplugEvents" "false" 

I ignored any references to the CustomEDID option.

That fixed it for me initially, BUT....

Unfortunately, xorg.conf has a habit of vanishing and being renamed xorg.conf.09092014 (or whatever the date is).   Creation date in the directory (ls -l xorg.conf.09092014) is not updated so matching with logs is difficult.

Mine vanished on 8/8/2014 during a period of very intermittent power to the whole area.  It failed again on Tuesday (stable power) this week - I've copied the Tuesday logs but not yet examined them in great detail.

The renaming is described here:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1307546](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1307546)

Seemingly the presence of file /var/ubuntu-drivers-common/last_gfx_boot should prevent the renaming but it's clearly a fragile mechanism.

I've tried chmod 444 xorg.conf but that hasn't prevented deletion.  

I thought the file: /var/lib/dpkg/info/nvidia-prime.postrm to be culprit so I added a tracing mechanism to it.  The trace did not take place on Tuesday so I believe it is exonerated.

You might like to take a copy of a good xorg.conf when you have one.

I think the answer might be to create xorg.conf at every reboot pending a real understanding of the problem but not entirely sure where to do that.

Hope this takes you a few steps along the road, but if you can expand/correct it PLEASE report back here. I really want high WAF with no more debates about the merits of Sky plus!! 

Best wishes
Phil

---

### Post by SeijiSensei on 2014-09-11
You can mark a file "immutable" with "sudo chattr +i /path/to/file".  Such files cannot be deleted or modified even by root.  This is typically an extreme solution, but perhaps the right one for you.  To change an immutable file, you must first turn off the immutable bit with "chattr -i".

---

### Post by kenmollerup on 2014-09-11
No your tv just dosn't remember to change HDMI input, so try to change input to tv on remote, or learn to shutdown your Mythbox before turning off your tv.
Same thing happens if you turn off your DVD player after your tv, tv hangs on a downed HDMI port.

---

### Post by tristone2 on 2014-09-11
Not sure what kernel version and VGA card you are running with. I used to have similar problem but later figured it out.

Initially I had i3 530 onboard HD graphics and everything was fine on Ubuntu 10.04. Later got a new box with ivy bridge on Ubuntu 12.04 and it started to happen. I hooked up the box to an AVR and then to the TV. If I turn the TV off and wait for a few minutes the TV will shutdown the HDMI and after that when I turn the TV back on there will be no input anymore. 

Later I discovered I need to trigger an 'HDMI hotplug event'. This can be done by unplugging the HDMI cable and then plugging it back in. This was not good enough so I went on checking. Then I found if I switch to a text console by pressing Ctrl-Alt-F1 and then switch back to graphics console the event would be triggered. This way I wouldn't have to unplug cable. But that was considered a 'bug' and after a few kernel updates (I remember somewhere in 3.12.x) this was eventually fixed.

Then one day I discovered if I press the input switch on AVR remote to switch it to another source, say, HDMI2, and then switch back to my HTPC on HDMI1, the event is again triggered and I have the picture back. I have been using this trick ever since.

The tricky part about HDMI is, first it involves a handshake, during which both sides of the cable will try to tell each other who they are and what capabilities they have. For devices like AVR, they will act as a hub/switch of HDMI so they will even attempt to intercept and change the handshake info, resulting in strange behaviors. When the TV is off, the AVR is still connected and will send some strange display info to HTPC. If it does not send new info when TV is back on, the HTPC won't know about the changed hence X.org won't reconfigure itself for the output. And that's how you get the blank screen.

---

### Post by khPWXxF on 2014-09-11
Thanks for the suggestion of 'immutability'.  Sounds a good solution.
Phil

---

### Post by prosmart on 2014-09-12
Thanks for all the input - much appreciated.

N/

---

### Post by prosmart on 2014-09-12
> **kenmollerup said:**
> No your tv just dosn't remember to change HDMI input, so try to change input to tv on remote, or learn to shutdown your Mythbox before turning off your tv.
Same thing happens if you turn off your DVD player after your tv, tv hangs on a downed HDMI port.


That would work if the box was in fact going to be powered off but then I wouldn't have this problem would I :)

N/

---

### Post by prosmart on 2014-09-12
Interesting update.

Tried CTL-ALT to another tty and all was fine (1 thru 6). but CTL-ALT-F7 brought me back to "no signal".

Tried to connect and disconnect the hdmi cable to the same port on the TV - got nothing.

Killed xscreensaver (just in case) - different.

Think I may have to dump the HDMI and try digital output.

Any thoughts?

Tried to connect and disconnect the hdmi cable to a different port on the TV - got nothing.

---

### Post by Elfy on 2014-09-12
> **prosmart said:**
> Couldn't delete this post - where is the "delete" button?

There isn't one ;)

If you need something like that use the Report Post button.

---

