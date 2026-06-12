---
title: "Easy way to determine which is failing: my wifi card or the access point?"
date: 2013-03-12
forum: Networking &amp; Wireless
---

### Post by kerryhall on 2013-03-12
Let's say I'm connected to an AP at a coffee shop. My connection seems to drop randomly. The coffee shop staff insist the problem must be with my wifi card, but I say no, it must be with the AP. Is it possible to collect any sort of data from dmesg or logs on my machine in order to be certain, one way or the other?

Thanks!

---

### Post by kerryhall on 2013-03-18
Any thoughts on this?

---

### Post by varunendra on 2013-03-18
> **kerryhall said:**
> Let's say I'm connected to an AP at a coffee shop. My connection seems to drop randomly. The coffee shop staff insist the problem must be with my wifi card, but I say no, it must be with the AP. Is it possible to collect any sort of data from dmesg or logs on my machine in order to be certain, one way or the other?

Linux drivers still have problems with n-channel or WPA/WPA2 mixed mode encryption. So if that's the case, the problem is at your side.

There are usually hints to the problem in dmesg logs. Look for the lines that say something about wlan, or its drivers (are often more than one working as a group). Also take a look at **iwconfig, iwlist scan**.

Alternatively, just download the 'Wireless Script' from the link in my signature and run it when having problem in connecting. Post back its contents or its pastebin link for analysis.

---

### Post by kerryhall on 2013-03-31
I'm seeing messages in dmesg that reference my wireless card, but I don't know if the "disconnected" (or similar) messages are the result of my wireless card screwing up somehow, or the access point dropping the connection. Does that make sense?

How do I tell if the output from dmesg is a result of an internal wireless problem, or an external one?

---

### Post by ahallubuntu on 2013-03-31
~

---

### Post by kerryhall on 2013-04-04
Ok, I was trying to simplify the problem for the purposes of this thread, but sounds like I should provide as much data as possible.

I'm currently having this issue with three different computers, all with different wireless cards. I have all three connected to my home access point, but I have tried two of em at coffee shops and such. Let me just start with one of them for now. Here is the output:

[http://pastebin.com/1DkfSzVq](http://pastebin.com/1DkfSzVq)

---

### Post by kerryhall on 2013-04-04
This card will drop my connection for about 20 seconds sometimes, it will say "disconnected" and then "connected" but other times the connection will drop for around 2-5 minutes, and request the AP password multiple times.

Here is some sample output of dmesg:

[http://pastebin.com/5ASGbZ68](http://pastebin.com/5ASGbZ68)

---

### Post by matt_symes on 2013-04-04
Hi 

> **kerryhall said:**
> Ok, I was trying to simplify the problem for the purposes of this thread, but sounds like I should provide as much data as possible.

Always provide as much detail as possible or you will get substandard advice.

As for the device you have talked about then take a look at this thread.

[http://comments.gmane.org/gmane.linux.kernel.wireless.general/92203](http://comments.gmane.org/gmane.linux.kernel.wireless.general/92203)

Same driver you are using and may well be the same card.

No idea about your other machines though.

Kind regards

---

### Post by kerryhall on 2013-04-05
Good call :) 

My problem is that I think about an issue, and then try and generalize it. ie, rather than asking for help about this specific card, I originally asked for help about the general case (how to tell if it's my card or the AP). Of course, the general case is much more difficult. :D Thanks!

---

### Post by matt_symes on 2013-04-05
Hi

> Always provide as much detail as possible or you will get substandard advice.

I want to rewrite this comment because, after re-reading it, it's not exactly what i meant.

So for the record...

> Always provide as much detail as possible or you will get only very general advice.

@OP. Did that thread help you in any way ?

Kind regards

---

### Post by varunendra on 2013-04-06
@ kerryhall,

I didn't take a thorough look at the thread matt_symes linked to, but for the system from which you posted the outputs (one with atheros AR9170 card, carl9170 driver), please try -
```
echo "options carl9170 nohwcrypt=Y" | sudo tee /etc/modprobe.d/carl9170.conf
```

The above will write an option file for the driver that will disable hardware based encryption on it (will force it to software encryption). It will take effect after a restart, or -
```
sudo modprobe -rfv carl9170
sudo modprobe -v carl9170
```

Try and let us know if it helps. There should be no harm in leaving the file even if it does not help, but if you wish, you can always remove it with -
```
sudo rm /etc/modprobe.d/carl9170.conf
```

---

