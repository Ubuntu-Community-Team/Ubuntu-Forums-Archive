---
title: "HP Pavilion Wireless Enable/Disable Button 11.04"
date: 2011-05-11
forum: Networking &amp; Wireless
---

### Post by SpaceMaster on 2011-05-11
I've had a host of problems since upgrading to 11.04 Natty Narwhal, so let's deal with these 1 at a time.

I've got a Hewlett-Packard Pavilion G60 laptop.  Next to the power button is a handy wireless on/off button.  This has always worked well with previous editions (9.04,through 10.10).  first press toggles the wireless off, second press toggles it on.

Not so in 11.04.  The toggle off works great, first time.  But, it will not toggle back on.  Not after any number of tries, not after restarting, not after booting into other OS's (9.10 and Vista) re-enabling it there and then booting back into Narwhal.  to further complicate the issue, this feature bypass the network manager, so toggling the wireless off by the switch leaves me showing no wireless adapter in the network manager.  I also restarted, switched from Unity to a Gnome session, but the issue still persists.

As my only network options are wireless, this has become a substantial inconvenience.
----
EDIT: so the network util is actually saying "wireless disabled by hardware switch".  Also noticed it I enable it in 9.10, reboot to 11.04 (where I inevitably fail to re-enable it), then reboot into 9.10, it will initially be disabled.  The key difference is in 9.10 I have the ability to enable wifi using the hardware button.  It seems that 11.04 is remembering that wireless is disabled between boots.  Is there a place it might be storing this value?  If so, I may be able simply to set the value as enabled, since toggling that silly button isn't working.
-----
EDIT 2:
found this thread:["Wireless disabled by hardware switch" bug? - Natty]("http://ubuntuforums.org/showthread.php?t=1753072")
seems to be a similar issue.  I'll be following how that one develops, too.

---

### Post by SpaceMaster on 2011-05-13
Problem Solved!

But... and of course there's a but, the solution I used is only good under a specific set of circumstances.  So here goes:

Firstly, on my laptop I have Ubuntu 11.04, Ubuntu 9.10 (in case something - say wireless - breaks in 11.04), and (*shudder*) Windows Vista.

Secondly, it turns out that on HP Pavilions, since the "switch" is more of a software switch linked to dedicated button next to the power button, it behaves a little differently.  It turns out that this switch has 3 states: "Disabled", "Enabled but off", and "Enabled & on".

  Hitting the button once switches it from "Enabled & on" to "Disabled".  In previous editions (9.10), a second hit restores it to the "Enabled & on" state.  But, in 11.04, a second strike seems to restore it only to "Enabled but off" state, and hitting the button an odd number of times (ex 1, 3, you know the odd numbers) puts the switch into a "Disabled" state.  This is what hung me up, because no matters how many times I hit it in 11.04, it always either went to "Disabled" or "Enabled but off," which both show on the network util on the launcher as "Wireless disabled at hardware switch."  Strangely, even though I could both enable and use wireless in 9.10, it would revert to "Disabled" at each boot, rendering 11.04 useless as far as networking goes (which I still can't explain why).

Then it struck me.  I had kept Vista on the machine because it came with it, and in Vista there is an "HP Wireless Assistant" utility.  It is in this program I discovered that the switch indeed controls 3, not 2 states of the wireless.  Once in that program, I used the button to switch wireless mode from "Disabled" to "Enabled but off," and then use the program to set wireless to "Enabled & on."  Once clicking OK and restarting, wireless was restored in 11.04.

----------------

One more kink in the solution.  It seems as long as I use the hardware switch to re-enable the wireless in the same session, everything works as it should.  I only run into the problem if I shut down the computer with the wireless still disabled.
So, lesson learned, "don't touch the red button," at least not the one with the wireless logo.

---

### Post by XProgrammer on 2011-05-17
Thanks @ SpaceMaster. 

Fixing it via Vista HP Wireless Assistant helped me.

---

### Post by Khalaris on 2011-05-31
Thanks, SpaceMaster. Your info about the 3 states helped me solve the problem. I have an HP Elitebook, so I don't know how similar the buttons are... I have one (touch) button that controls both bluetooth and wifi. After keeping it pressed for a few seconds instead of just toggling it normally I could finally check "Enable wireless" in the network panel applet and that solved it.

---

### Post by lenooh on 2011-10-07
I had a similar problem on a HP ProBook 4730s (Ubuntu 11.10., Oneiric Beta 2).

Everything worked out of the box (wired, wireless, bluetooth), until I pressed the button for wireless switching:
wireless became disabled by hardware and there was no way to enable it, no matter how many times I pressed it. Changing the BIOS settings did not enable it.

So the solution that worked for me was:
- enable the LAN/WLAN switch in BIOS
- boot to Ubuntu, plug a LAN cable, wait a few seconds then unplug the LAN cable
- wireless should now be enabled by hardware switch (although it says device not ready)
- restart and it works

Have fun!

(same answer as [http://ubuntuforums.org/showthread.php?p=11318336#post11318336](http://ubuntuforums.org/showthread.php?p=11318336#post11318336))

---

### Post by Robyn-Hoodridge on 2011-10-08
I've got an ASUS running Natty. Controls seem to work fine. The selection in ubuntu between "enable wireless" and not works. Well it displays a tick or not, unfortunately i can't test whether the wireless toggles between functional and not. And the hardware button does exactly the same thing. But the hardware indicator (LED) stays on no matter what. I have a sneaky suspicion that, like SpaceMaster and others, the wireless has three settings. But is only toggling between [on and enabled] and [on but disabled]. Now i don't know for sure whether this means it's emitting or using power when it's disabled. But let's say it is and that i want to have it not be doing these things standardly. Does anyone know how to properly dis-enact the wireless?
Cheers

---

### Post by Carl7145 on 2012-03-14
Hello I am having a similar problem. I am using my hp pavillion dv4000 don't tell me its old because I already know that. The thing is the wireless switch on the top of the keyboard dosen't do anything. I am running Ubuntu 11.10. Plz help I have made no changes to the internal parts or anything. Plz help.

---

### Post by lenooh on 2012-03-20
> **Carl7145 said:**
> Hello I am having a similar problem. I am using my hp pavillion dv4000 don't tell me its old because I already know that. The thing is the wireless switch on the top of the keyboard dosen't do anything. I am running Ubuntu 11.10. Plz help I have made no changes to the internal parts or anything. Plz help.
You forgot to say if your wireless is working.
If it is, I wouldn't care about the switch.
If it's not, check your bios settings first (or you could do that anyway). See if there's an option for the switch or something similar.

---

### Post by ogranadino on 2012-05-19
Well the solution is here.
Remove the file NetworkManager.conf (weirds configs use to store there)

sudo rm  /etc/NetworkManager/NetworkManager.conf

Then do

sudo rfkill unblock all
rfkill list all

:guitar:

Thats all.
Works for me, now the on/off switch works.

---

### Post by whitemagicwoman on 2012-08-23
This issue is plaguing me as well.  Since I upgraded to 11.04 (now I have installed 12.04 but the problem persists) my HP Pavilion dv4 doesn't seem to know the wireless adapter is there.  I did the BIOS reset, I tried installing b43-fwcutter, I tried pressing the button several times.  

I also tried 

 sudo rm  /etc/NetworkManager/NetworkManager.conf

etc as listed above.  Nothing doing.  Networking is enabled.

Further suggestions?

---

### Post by turqoisehex on 2012-09-02
Thanks, worked for me on dv2700! I also did:

sudo apt-get install b43-fwcutter bcmwl-kernel-source

After doing that and the above solution, then restarting, its working great! :popcorn:

---

