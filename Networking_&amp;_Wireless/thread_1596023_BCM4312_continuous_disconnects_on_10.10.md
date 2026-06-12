---
title: "BCM4312 continuous disconnects on 10.10"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by hypetech on 2010-10-13
Hi all.  I'm running Ubuntu 10.10 on a Dell Inspiron 1545 using the Broadcom BCM4312 wireless adapter.  I was using 10.04 since its release without any wireless issues, then I upgraded to 10.10.  After upgrading, my wireless will disconnect and reconnect every 20 minutes or so.  This happens at any location that I am connected to wireless.  I also tried a fresh install of 10.10 and the problem still exists.

I have found, by accident, that if I leave open the Seesmic Desktop Air application, my wireless will not disconnect.  I'm not really sure if/how that's relevant, but it makes me think it's some sort of idle timeout/power saving issue, but Seesmic seems to be the only application that makes it behave that I have found.

I've looked around and seen that some people are having trouble getting wireless to work on 10.10 altogether, but I haven't been able to find anything that seems like they are having the same issue I am.  Any assistance or advice would be much appreciated.  Thanks.

---

### Post by influxor on 2010-10-18
Not sure if this helps.
I have the Exact same model of Dell laptop and wireless hardware that you listed and I have had the exact same problem you described upgrading from 10.04.1 LTS to 10.10.

What fixed the issue for me was to stop running and uninstall the Screenlets App. 
In 10.04 i used the sensors and watermark sensors screenlet to display sensor information on the desktop. When i stopped using these my wireless dropping and occasional graphic lockups in the gui have ceased to occur.

I can't say if this is any help for you as you might not even use the sceenlets app.

I also removed some usb modem controller drivers that I do not use, and in system bios I turned off Fn emulation for external keyboards. I do not use bluetooth and disabled that in bios for now as well.
I only saw any real improvement when not using Screenlets in 10.10.  
I hope you can find a solution that works for your system. good luck!

---

### Post by hypetech on 2010-10-18
> **influxor said:**
> Not sure if this helps.
I have the Exact same model of Dell laptop and wireless hardware that you listed and I have had the exact same problem you described upgrading from 10.04.1 LTS to 10.10.

What fixed the issue for me was to stop running and uninstall the Screenlets App. 
In 10.04 i used the sensors and watermark sensors screenlet to display sensor information on the desktop. When i stopped using these my wireless dropping and occasional graphic lockups in the gui have ceased to occur.

I can't say if this is any help for you as you might not even use the sceenlets app.

I also removed some usb modem controller drivers that I do not use, and in system bios I turned off Fn emulation for external keyboards. I do not use bluetooth and disabled that in bios for now as well.
I only saw any real improvement when not using Screenlets in 10.10.  
I hope you can find a solution that works for your system. good luck!

Unfortunately I don't even have screenlets installed :(  However, keeping Seesmic open all the time is providing me with a stable connection, and I lose it very soon after closing Seesmic, so I've at least got a semi-working solution :(

---

### Post by magic9418 on 2010-10-18
I too have this problem...running a macbook 4,1.
On the fresh install it worked for a while and then stopped.  Now it will not use my WPA properly; have tried to remove and reapply the drivers to no avail.

Thanks

---

### Post by johnnytm on 2010-10-18
Curious to know what driver you used for wireless. I have the same laptop and have been running absolutely flawless since installing 10.10. does it continue to happen even if you are activley using the laptop? or is only on waking up?

---

### Post by magic9418 on 2010-10-19
for me I am using the stock STA driver from a fresh boot.

---

### Post by influxor on 2010-10-23
just an update to my earlier reply:

what i suggested trying a few posts before did not end up working.
wicd would not help either.
so i tried something new and think i might have had success in stabilizing the wireless finally but will need to let it run a few days to test.

what i did-

plugged into the router on wired , Uninstalled network-manager  and  network-manager-gnome. Then Reboot the computer and Boot the Live CD of 10.04.LTS and run it in live cd mode. open up Synaptic Package Manager and search for network-manager, network-manager-gnome.  it will list the 10.04.Lts versions, mark those for re-installation and then search for one required dependency 10.10 does not have: libgnome-bluetooth7 and mark to reinstall. 
Hit apply but on the pop-up menu choose "download files only" and ok. 
I copied those downloaded packages from /var/cache/apt/archives to an SDcard.
close out synaptic.

Reboot as normal (10.10 off harddrive for me) and installed  libgnome-bluetooth7 network-manager and network-manager-gnome in Ubuntu 10.10 from the10.04.Lts versions on the SDcard and so far it has not disconnected. I need more time to test it. Careful not to let the updater update network-manager-gnome and network-manager for now so i can use the version from 10.04 for now. so far so good (1 day on wireless and no disconnects at this time).
i had ended up rolling back to the older version in that manner as i had uninstalled network-manager-gnome and tried Wicd and could not connect at all with that one.


UPDATE: after more testing i find this also did not totally fix the issue but may have made it more stable as i had fewer disconnects. Still not a fix for me at this time.


FINAL UPDATE:  OK i think i may have found it!  for me on my system it was the pulseaudio sound server. i had to remove the pulse audio server, leaving 3 library files behind and replaced the volume mixer with Gnome ALSA mixer.  now all is very stable for me using the 10.10 networking and other little problems disappeared!  so look into messing with pulseaudio's server might help you also.  good luck!

---

