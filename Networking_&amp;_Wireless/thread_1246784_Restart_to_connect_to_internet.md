---
title: "Restart to connect to internet"
date: 2009-08-22
forum: Networking &amp; Wireless
---

### Post by chavon20 on 2009-08-22
I have recently updated my Ubuntu from Hardy to Jaunty.  I've never had any problems connecting to my wireless network in the past (on Hardy); however on Jaunty my laptop won't connect in the first instance.

The network manager applet appears - with the bars but a little red cross which obviously means the laptop is not connected.  When I restart my laptop I'm connected to the internet almost immediately.

Has anyone experienced this on a wireless network with Jaunty or otherwise?  Seems very odd to me that it won't start from a cold boot but will from a warm boot...  Thanks!

---

### Post by dk06 on 2009-08-22
> **chavon20 said:**
> I have recently updated my Ubuntu from Hardy to Jaunty. I've never had any problems connecting to my wireless network in the past (on Hardy); however on Jaunty my laptop won't connect in the first instance.

The network manager applet appears - with the bars but a little red cross which obviously means the laptop is not connected. When I restart my laptop I'm connected to the internet almost immediately.

Has anyone experienced this on a wireless network with Jaunty or otherwise? Seems very odd to me that it won't start from a cold boot but will from a warm boot... Thanks!

Try updating your computer first.

I've had issues w/the network manager & keyrings before but nothing like you're describing....if you want to try reinstalling the network manager through the 'Synaptic Package Manager' it may be an easy fix (just right click it and say 'reinstall')
[U]
If you are having authentication issues,[/U]
go into your home folder & press **[ctrl] + [H]** *(shows hidden folders)* ...from there check inside your '.gnome2' folder, inside there > 'keyrings' folder, then inside there move the keyring files onto your desktop.
Then try to connect, put in the passphrase then make your new keyring password....if those don't fix it, I'm not sure what to tell you, upgrades can be challenging sometimes.

Hope this helps

---

### Post by chavon20 on 2009-08-22
Thanks for this dk06, I'll give this a go... :)

---

### Post by oboedad55 on 2009-08-22
> **chavon20 said:**
> Thanks for this dk06, I'll give this a go... :)

I had this same problem on my Acer laptop. First I left click to select the wireless I want, then right click and pick "edit connection" and make sure under the wireless part that "connect automatically" is checked. That may help.

Jon

---

